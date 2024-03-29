# Learning R for Wildlife


This document compiles R resources that I recommend. R is not the most
straightforward programming language, and different styles of R code can appear
drastically different. Almost every style will look quite different from more 
conventional programming languages like C or Python. 

Given that, it is easy to head down the wrong path in R. The resources I list 
here are largely chosen to avoid those pitfalls. 

<base target="_top"/>
_________________

## Basics

Do you want to learn R?

If you have little to no coding experience and want to get started, or are 
new to R and data processing, chapter 1 of this online book is great:

__Statistical Inference via Data Science__
https://moderndive.com/1-getting-started.html

__Tips on learning to code__
https://moderndive.com/1-getting-started.html#tips-code


<!-- > ^learning to code goes much smoother ... when you are working on a particular project, like analyzing data that you are interested in and that is important to you.^ -->

If are familiar with general coding principles, or have even coded in old school 
base R extensively, but are new to tidy R or data science with R, 
[Hadley's](https://github.com/hadley) book is the definitive 
guide to analyzing data with R. It's also great for more experienced coders as
a guide to organizing the data analysis work flow. 

__R for Data Science__
https://r4ds.had.co.nz/index.html


Both of these resources are listed on the 
[tidyverse](https://www.tidyverse.org/learn/) website.

Once you've started using these, you'll quickly need more reference info on 
tidyverse tools. Thankfully, these are extremely well documented with vignettes
and examples. Many of the most commonly used data manipulation functions come
from the package `dplyr`:

__Introduction to dplyr__ 
https://dplyr.tidyverse.org/articles/dplyr.html

You'll also want to plot data, and hence learn `ggplot2`:

__Learning ggplot2__ 
https://ggplot2.tidyverse.org/#learning-ggplot2

If you want to get started plotting quickly, you can find what you need here:

__R Graphics Cookbook__ 
https://r-graphics.org/


Now that you're writing code, you are aren't going to want to stop and read 
books every time you need to look up how to do something. I don't even know how 
to read anymore. One of the best things
about modern R tools are the cheat sheets. Here is a centralized collection:

__RStudio Cheatsheets__ 
https://www.rstudio.com/resources/cheatsheets/

_________________

## Style 

Writing code is not just about building a machine that processes data. 
Especially for scientific data analysis, code is also a precise description 
of your methodology. If others can read it, they can learn exactly what you did 
with your data. The challenge is making your code readable. 

This is a major motivation behind using tidy data and tidyverse functions, but
these won't save you from writing unreadable code. You have infinite choices in 
naming and formatting things. For legibility and consistency, try to adhere to:

__The tidyverse style guide__ 
https://style.tidyverse.org/

_________________

## Statistics

Do you want to get some basic descriptive statistics (mean, variance, etc)?
Do you want to make some plots or fit a basic model?

__R for Data Science__, again, has you covered.

- [Ch 7  Exploratory Data Analysis](https://r4ds.had.co.nz/exploratory-data-analysis.html)
- [Ch 22 Modeling](https://r4ds.had.co.nz/model-intro.html)

Do you want to model your data for legit scientific use? 
Understand linear or logistic regression?
Use (and actually understand) generalized additive models? 

By far the best resource for statistical data analysis I've ever seen is 
[Cosma Shalizi's](http://bactra.org/): 

__Advanced Data Analysis from an Elementary Point of View__
https://www.stat.cmu.edu/~cshalizi/ADAfaEPoV/

Most texts either focus on the principles and theory of statistics, or the 
nitty gritty of data analysis code. This book is about theory while
also demonstrating things with actual R code and plots. The one 
downside is that it uses base R instead of tidyverse stuff. However, once you
are familiar with tidyverse stuff it is not hard to go between the two. The 
largest difference is in the base `plot` versus the tidy `ggplot`.

Some of the content in this book is probably not of interest. I certainly
haven't made it through the whole thing. 
So I'll highlight some sections I've found particularly useful here: 

- 1.1   _Regression: Predicting and Relating Quantitative Features_
- 2.4   _Linear Regression Is Not the Philosopher’s Stone_
- 3     _Model Evaluation_
- 8     _Additive Models_
- 12    _Generalized Linear Models and Generalized Additive Models_
  
I think if you were to work through that whole book you would have a better 
statistics education than the majority of professional data scientists.
  
_________________

## Spatial Data

Do you want to make maps? Do spatial statistics? Explore movements?

Spatial data comes in two forms: Vector and Raster. 
  
  - Vector: This is data associated with precise coordinates. Think points, 
  lines, gps fixes, roads. 
  - Raster: This is gridded data that is mapped to a spatial surface. The data
  is in images, and each pixel of that image covers a general area rather than 
  precise coordinates. Think satellite imagery or elevation models.
  
For vector data, you will want to use `sf`:

__Simple Features for R__
https://r-spatial.github.io/sf/

This is an R package, not a book. However, like many good R packages, it has
excellent documentation in the _Articles_ or _vignettes_. 

`sf` is at the heart of all the code I've written to process telemetry data. 
I can't recommend it enough, and [Edzer](https://github.com/edzer) is the most
responsive developer I've encountered. 

For more info on how to use `sf`:    

__Spatial Analysis with R__
https://chiajung-yeh.github.io/Spatial-Analysis/

This text by [Yeh Chia Jung](https://github.com/chiajung-yeh) looks nice. 
It's basically an in-depth demo using the `sf` package. 
It illustrates how to use `ggplot` in combination with spatial data, and also 
explains what goes into making data spatial. 


For raster data, the corresponding package is `stars`:

__Spatiotemporal Arrays: Raster and Vector Datacubes__
(https://r-spatial.github.io/stars/)

However, this is a younger package and has a strong competitor in 
[`terra`](https://rspatial.org/terra/pkg/index.html), which I haven't used but I
know is popular.

More info: 

The underlying libraries driving all of these spatial data tools come from 
[Open Geospatial Consortium](https://www.osgeo.org/partners/ogc/).
These tools, like [GDAL](https://gdal.org/) and [PROJ](https://proj.org/) also
power software like [QGIS](https://www.qgis.org/en/site/) and 
[PostGIS](https://postgis.net/). 

The good thing about that is that it's easy to exchange data between any of 
these tools, and often an analysis done in one can be easily replicated in 
another. For example, I've often done something using the QGIS graphical 
interface, and then once I've figured out what I wanted, copied the steps over
into R or Python using the same underlying GDAL library. 

Unfortunately, ESRI does its own thing and often doesn't play well with OGC 
tools. 


_________________  
  
## Advanced R topics
  
At some point writing tidy R code you are going to get frustrated and feel
limited with what you can do. Most likely you will then start trying to write
Python using R, with for loops and such. This can work but will also get
really messy, and if you choose this path, you will regret ever using R 
because things would have been easier and faster had you started with Python. 

Fortunately there is another path, and once again Hadley is there to guide us:

__Advanced R__
https://adv-r.hadley.nz/

You may want to publish your code as a tool to be used by others for purposes 
beyond your particular use case and data. In this case, you should make an R 
package. Personally, I'm new at that and don't have much experience, but this
book is guiding me through the process:

__R Packages__
https://r-pkgs.org/index.html

_________________

## RMarkdown

This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.
  
For more info on how to write R Markdown and do really fancy stuff with it:

__R Markdown: The Definitive Guide__
https://bookdown.org/yihui/rmarkdown/
  
_________________

Source: https://github.com/rgzn/r_guides
