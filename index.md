---
title       : Predicting the species of an iris
subtitle    : 
author      : John Johnson
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
--- 

## Purpose

* To predict the species of iris given sepal width and length, and petal length and width
* To display the new potential iris along with other measured irises

---

## Using the app

* The app is located at https://randomjohn.shinyapps.io/flower/
* Use the **Plot variables** list boxes to choose the graph

![Plot variables are chosen in list boxes](assets/img/plotvars.PNG)

* Use the sliders to define your new measurement to be classified

![Iris characteristics are chosen with sliders](assets/img/irischar.PNG)

---

## How the prediction is made

The prediction is made through a classification tree. For example, suppose we wanted to classify an iris with sepal length of 3.0 cm, sepal width of 1.5 cm, petal length of 3.0 cm, and petal width of 1.5cm, we would proceed as follows:


```r
library(rpart)
data(iris)
fit <- rpart(Species ~ ., data = iris)
potential <- data.frame(Sepal.Width = 1.5, Sepal.Length = 3, Petal.Width = 1.5, 
    Petal.Length = 3)
as.character(predict(fit, potential, type = "class"))
```

```
## [1] "versicolor"
```


---

## Misclassification

Because of the way classification trees work, a prediction may be different from its apparent neighbors.

![The classification algorithm doesn't always work that well](assets/img/different.PNG)
