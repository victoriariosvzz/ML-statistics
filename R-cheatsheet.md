---
title: "Notes: R cheatsheet"
author: "Victoria Ríos"
date: "5/2/2021"
output: html_document
---



# Package required

```r
#install.packages("ISLR")
library(ISLR)
```

```
## 
## Attaching package: 'ISLR'
```

```
## The following object is masked _by_ '.GlobalEnv':
## 
##     Auto
```

```r
library(MASS)
```

# Basics

##Vectors

```r
x <- c(1,3,2,6) # Vector
x
```

```
## [1] 1 3 2 6
```

```r
y <- c(1,3,5,2) # vector
y
```

```
## [1] 1 3 5 2
```

```r
x + y # addition of vectors
```

```
## [1] 2 6 7 8
```

##Objects saved

```r
ls() # to check all the objects saved at the moment
```

```
## [1] "A"         "Auto"      "cylinders" "f"         "fa"       
## [6] "x"         "y"
```

```r
rm(x,y) # to remove specific objects (variables)

rm(list = ls()) # to remov all the objects saved
```
##Matrix

```r
x <- matrix(data = c(1,2,3,4), nrow = 2, ncol = 2)
x
```

```
##      [,1] [,2]
## [1,]    1    3
## [2,]    2    4
```

```r
y <- matrix(data = c(1,2,3,4), nrow = 2, ncol = 2, byrow = TRUE) # to order it by rows
y
```

```
##      [,1] [,2]
## [1,]    1    2
## [2,]    3    4
```

```r
sqrt(x)
```

```
##          [,1]     [,2]
## [1,] 1.000000 1.732051
## [2,] 1.414214 2.000000
```

```r
x^2
```

```
##      [,1] [,2]
## [1,]    1    9
## [2,]    4   16
```

## Random numbers
The **rnorm()** function generates a vector of random normal variables, with first argument n the sample size. Each time we call this function, we will get a different answer.

```r
x <- rnorm(n = 50) # random number, sample size = 50
y <- x + rnorm(n = 50, mean = 50, sd = .1)

cor(x,y) # we find the correlation of both variables
```

```
## [1] 0.995529
```
Sometimes we want our code to reproduce the exact same set of random numbers; we can use the **set.seed()** function to do this. The set.seed() function takes an (arbitrary) integer argument.

```r
set.seed(1303)
rnorm(50)
```

```
##  [1] -1.1439763145  1.3421293656  2.1853904757  0.5363925179
##  [5]  0.0631929665  0.5022344825 -0.0004167247  0.5658198405
##  [9] -0.5725226890 -1.1102250073 -0.0486871234 -0.6956562176
## [13]  0.8289174803  0.2066528551 -0.2356745091 -0.5563104914
## [17] -0.3647543571  0.8623550343 -0.6307715354  0.3136021252
## [21] -0.9314953177  0.8238676185  0.5233707021  0.7069214120
## [25]  0.4202043256 -0.2690521547 -1.5103172999 -0.6902124766
## [29] -0.1434719524 -1.0135274099  1.5732737361  0.0127465055
## [33]  0.8726470499  0.4220661905 -0.0188157917  2.6157489689
## [37] -0.6931401748 -0.2663217810 -0.7206364412  1.3677342065
## [41]  0.2640073322  0.6321868074 -1.3306509858  0.0268888182
## [45]  1.0406363208  1.3120237985 -0.0300020767 -0.2500257125
## [49]  0.0234144857  1.6598706557
```
## Mean and variance

```r
set.seed (3)
y=rnorm (100)

mean(y)
```

```
## [1] 0.01103557
```

```r
var(y)
```

```
## [1] 0.7328675
```

```r
sqrt(var(y))
```

```
## [1] 0.8560768
```

```r
sd(y)
```

```
## [1] 0.8560768
```
# Graphics

```r
x=rnorm (100)
y=rnorm (100)
plot(x,y)
```

![plot of chunk unnamed-chunk-75](figure/unnamed-chunk-75-1.png)

```r
plot(x,y, xlab=" this is the x-axis", ylab=" this is the y-axis", main=" Plot of X vs Y")
```

![plot of chunk unnamed-chunk-75](figure/unnamed-chunk-75-2.png)

We will often want to save the output of an R plot. The command that we use to do this will depend on the file type that we would like to create.

```r
pdf("Figure.pdf ")
plot(x,y,col ="green")
dev.off() # indicates R we are done creating the plot
```

```
## RStudioGD 
##         2
```
## Sequence of numbers

```r
x <- seq(1,10)
x
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10
```

```r
x <- 1:10
x
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10
```

```r
x <- seq(-pi, pi, length = 50)
x
```

```
##  [1] -3.14159265 -3.01336438 -2.88513611 -2.75690784 -2.62867957
##  [6] -2.50045130 -2.37222302 -2.24399475 -2.11576648 -1.98753821
## [11] -1.85930994 -1.73108167 -1.60285339 -1.47462512 -1.34639685
## [16] -1.21816858 -1.08994031 -0.96171204 -0.83348377 -0.70525549
## [21] -0.57702722 -0.44879895 -0.32057068 -0.19234241 -0.06411414
## [26]  0.06411414  0.19234241  0.32057068  0.44879895  0.57702722
## [31]  0.70525549  0.83348377  0.96171204  1.08994031  1.21816858
## [36]  1.34639685  1.47462512  1.60285339  1.73108167  1.85930994
## [41]  1.98753821  2.11576648  2.24399475  2.37222302  2.50045130
## [46]  2.62867957  2.75690784  2.88513611  3.01336438  3.14159265
```

## Plotting 3D data: contour()
We will now create some more sophisticated plots. The contour() function produces a contour plot in order to represent three-dimensional data; contour plot it is like a topographical map. It takes three arguments:
1. A vector of the x values (the first dimension),
2. A vector of the y values (the second dimension), and
3. A matrix whose elements correspond to the z value (the third dimension) for each pair of (x,y) coordinates.

```r
y <- x
f <- outer(x,y,function (x,y)cos(y)/(1+x^2))
contour (x,y,f)
contour (x,y,f,nlevels =45, add=T)
```

![plot of chunk unnamed-chunk-78](figure/unnamed-chunk-78-1.png)

```r
fa <- (f-t(f))/2
contour (x,y,fa,nlevels =15)
```

![plot of chunk unnamed-chunk-78](figure/unnamed-chunk-78-2.png)
## 3D color coded plot: image()
The image() function works the same way as contour(), except that it image() produces a color-coded plot whose colors depend on the z value, known as **heatmap**.

```r
y <- x
f <- outer(x,y,function (x,y)cos(y)/(1+x^2))
image (x,y,f)
image (x,y,f, add=T)
```

![plot of chunk unnamed-chunk-79](figure/unnamed-chunk-79-1.png)

```r
fa <- (f-t(f))/2
image (x,y,fa)
```

![plot of chunk unnamed-chunk-79](figure/unnamed-chunk-79-2.png)
## 3D plot view angle controlled: persp()
lternatively, persp() can be used to produce a three-dimensional plot. The arguments theta and phi control the angles at which the plot is viewed.

```r
image(x,y,fa)
```

![plot of chunk unnamed-chunk-80](figure/unnamed-chunk-80-1.png)

```r
persp(x,y,fa)
```

![plot of chunk unnamed-chunk-80](figure/unnamed-chunk-80-2.png)

```r
persp(x,y,fa ,theta =30)
```

![plot of chunk unnamed-chunk-80](figure/unnamed-chunk-80-3.png)

```r
persp(x,y,fa ,theta =30, phi =20)
```

![plot of chunk unnamed-chunk-80](figure/unnamed-chunk-80-4.png)

```r
persp(x,y,fa ,theta =30, phi =70)
```

![plot of chunk unnamed-chunk-80](figure/unnamed-chunk-80-5.png)

```r
persp(x,y,fa ,theta =30, phi =40)
```

![plot of chunk unnamed-chunk-80](figure/unnamed-chunk-80-6.png)

# Data

## Indexing data

```r
A <- matrix (1:16 ,4 ,4)

A[c(1,3) ,c(2,4)] # Seleccionando las filas 1 y 3, con las columnas 2 y 4.
```

```
##      [,1] [,2]
## [1,]    5   13
## [2,]    7   15
```

```r
A[1:3 ,2:4]
```

```
##      [,1] [,2] [,3]
## [1,]    5    9   13
## [2,]    6   10   14
## [3,]    7   11   15
```

```r
A[-c(1,3) ,] # Keep everything, except rows 1 and 3
```

```
##      [,1] [,2] [,3] [,4]
## [1,]    2    6   10   14
## [2,]    4    8   12   16
```

```r
dim(A) # shows rows and columns in the matrix
```

```
## [1] 4 4
```
## Loading data
The **read.table()** function is one of the primary ways to do this. The help file read.table() contains details about how to use this function. We can use the function **write.table()** to export data.

Once the data has been loaded, the **fix()** function can be used to view it in a spreadsheet like window.
However, the window must be closed before further R commands can be entered.

```r
Auto <- read.table ("Auto.data", header = TRUE, na.strings = "?")

fix(Auto) # TO observe the data as a spreadsheet
```

## Missing data: na.omit()
There are various ways to deal with the missing data. In this case, only five of the rows contain missing observations, and so we choose to use the na.omit() function to simply remove these rows.

```r
Auto <- na.omit(Auto) #We remove the rows with missing values

dim(Auto)
```

```
## [1] 392   9
```

```r
names(Auto) # we check the variables names
```

```
## [1] "mpg"          "cylinders"    "displacement" "horsepower"  
## [5] "weight"       "acceleration" "year"         "origin"      
## [9] "name"
```
## Additional Graphical and Numerical Summaries
To refer to a variable, we must type the data set and the variable name joined with a $ symbol. Alternatively, we can use the attach() function in
attach() order to tell R to make the variables in this data frame available by name

```r
plot(Auto$cylinders , Auto$mpg )
```

![plot of chunk unnamed-chunk-84](figure/unnamed-chunk-84-1.png)

```r
attach (Auto)
```

```
## The following objects are masked from Auto (pos = 5):
## 
##     acceleration, cylinders, displacement, horsepower,
##     mpg, name, origin, weight, year
```

```
## The following objects are masked from Auto (pos = 6):
## 
##     acceleration, cylinders, displacement, horsepower,
##     mpg, name, origin, weight, year
```

```r
plot(cylinders , mpg)
```

![plot of chunk unnamed-chunk-84](figure/unnamed-chunk-84-2.png)
The as.factor() function converts quantitative variables into qualitative variables.

```r
cylinders =as.factor(cylinders)
```

Plotting

```r
plot(cylinders , mpg)
```

![plot of chunk unnamed-chunk-86](figure/unnamed-chunk-86-1.png)

```r
plot(cylinders , mpg , col ="red ")
```

![plot of chunk unnamed-chunk-86](figure/unnamed-chunk-86-2.png)

```r
plot(cylinders , mpg , col ="red", varwidth =T)
```

![plot of chunk unnamed-chunk-86](figure/unnamed-chunk-86-3.png)

```r
plot(cylinders , mpg , col ="red", varwidth =T,horizontal =T)
```

![plot of chunk unnamed-chunk-86](figure/unnamed-chunk-86-4.png)

```r
plot(cylinders , mpg , col ="red", varwidth =T, xlab=" cylinders ", ylab ="MPG ")
```

![plot of chunk unnamed-chunk-86](figure/unnamed-chunk-86-5.png)
The hist() function can be used to plot a histogram.

```r
hist(mpg)
```

![plot of chunk unnamed-chunk-87](figure/unnamed-chunk-87-1.png)

```r
hist(mpg ,col =2)
```

![plot of chunk unnamed-chunk-87](figure/unnamed-chunk-87-2.png)

```r
hist(mpg ,col =2, breaks =15)
```

![plot of chunk unnamed-chunk-87](figure/unnamed-chunk-87-3.png)
The pairs() function creates a scatterplot matrix i.e. a scatterplot for every pair of variables for any given data set. We can also produce scatterplots matrix for just a subset of the variables.

```r
#pairs(Auto)
pairs(∼ mpg + displacement + as.integer(horsepower) + weight + acceleration , Auto)
```

![plot of chunk unnamed-chunk-88](figure/unnamed-chunk-88-1.png)

## Printing the values on the plot: identify()
In conjunction with the plot() function, identify() provides a useful identify() interactive method for identifying the value for a particular variable for
points on a plot. We pass in three arguments to identify(): the x-axis variable, the y-axis variable, and the variable whose values we would like to see printed for each point.

```r
plot(horsepower,mpg)
identify(x = horsepower,y = mpg, labels = name, n = T)
```

![plot of chunk unnamed-chunk-89](figure/unnamed-chunk-89-1.png)

```
## integer(0)
```

```r
#Now we clic on the point where we want to print the label
```

