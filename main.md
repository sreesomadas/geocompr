
--- 
title: 'Geocomputation with R'
author:
- Robin Lovelace
- Jakub Nowosad
date: '2017-08-16'
knit: bookdown::render_book
site: bookdown::bookdown_site
documentclass: book
bibliography:
  - refs.bib
  - packages.bib
biblio-style: apalike
link-citations: yes
description: "Forthcoming book on geographical data with R."
github-repo: "Robinlovelace/geocompr"
url: 'http\://robinlovelace.net/geocompr'
---



# Welcome {-}

Welcome to **geocompr**, the [website](http://robinlovelace.net/geocompr) of our forthcoming book with [CRC Press](https://www.crcpress.com/Chapman--HallCRC-The-R-Series/book-series/CRCTHERSER).

## Development {-}

Inspired by the **bookdown** [R package](https://github.com/rstudio/bookdown) we are developing this book in the open.
We decided to make the book open source to encourage contributions, ensure reproducibility and provide access to the material as it evolves.

We're developing the book in 3 main phases.
We're in phase 1 and focussed on the first 5 main chapters, which we aim to be complete by September.
Drafts of other chapters will be added to this website as the project progresses.

The latest version is hosted at [robinlovelace.net/geocompr](http://robinlovelace.net/geocompr).
This website is kept up-to-date thanks to Travis, a continuous integration (CI) service.
Travis automatically rebuilds the book and finds bugs by reporting the 'build status' after every update.
Currently the build is:

[![Build Status](https://travis-ci.org/Robinlovelace/geocompr.svg?branch=master)](https://travis-ci.org/Robinlovelace/geocompr) 

The version of the book you are reading now was built on 2017-08-16 and was built on [Travis](https://travis-ci.org/Robinlovelace/geocompr).
**bookdown** makes editing a book as easy as editing a wiki.
To do so, just click on the 'edit me' icon highlighted in the image below.
Which-ever chapter you are looking at, this will take you to the source [R Markdown](http://rmarkdown.rstudio.com/) file hosted on GitHub. If you have a GitHub account, you'll be able to make changes there and submit a pull request. If you do not, it's time to [sign-up](https://github.com/)! 

[![](figures/editme.png)](https://github.com/Robinlovelace/geocompr/edit/master/index.Rmd)

To raise an issue about the book's content (e.g. code not running) or make a feature request, check-out the [issue tracker](https://github.com/Robinlovelace/geocompr/issues).

## Reproducibility {-}

To reproduce the book, you need a recent version of [R](https://cran.r-project.org/) and up-to-date packages.
The following code should install the required packages:


```r
if(!require(devtools)) {
  install.packages("devtools")
}
devtools::install_github("robinlovelace/geocompr")
```

To build the book locally, clone or [download](https://github.com/Robinlovelace/geocompr/archive/master.zip) the repo and run the following line from the [project](https://github.com/Robinlovelace/geocompr/blob/master/geocompr.Rproj)'s root directory:


```r
bookdown::render_book("index.Rmd") # to build the book
browseURL("_book/index.html") # to view it
```

For further details see the book's GitHub page at [Robinlovelace/geocompr](https://github.com/Robinlovelace/geocompr#geocomputation-with-r).

<!-- ## Acknowledgements {-} -->
<!-- add list of people who helped with this book -->

<!--chapter:end:index.Rmd-->


# Introduction {#intro}

This book is about harnessing the power of modern computers to *do things* with geographic data.
It teaches a range of spatial skills, including: reading, writing and manipulating geographic data; making static and interactive maps; and modeling geographic phenomena.
By demonstrating how various spatial operations can be linked, in the reproducible 'code chunks' that intersperse the prose, the book also shows how these skills support a transparent and thus scientific workflow.
Learning how to use the wealth of geospatial 'tools' this computational approach enables can be exciting and liberating.
However, it is even more liberating to create new tools.
By the end of the book you should be able to create new tools in the form of shareable R functions.

Over the last few decades a huge amount of work has gone into developing open source software for handling geographic data (see [foss4g.org](http://foss4g.org/)).
This means that spatial data analysis is no longer the preserve of those who can afford expensive programs, and the hardware to run them.
Anyone can now download high performance spatial libraries on their computer.
However, despite the growth of geospatial software that is *open source*, much of it remains *inaccessible*, in a form that is scriptable and therefore easily reproducible and 'computational'.
Open source Geographic Information Systems (GIS) such as QGIS (see [qgis.org](http://qgis.org/en/site/)) have greatly reduced the 'barrier to entry', but the emphasis of such programs on a Graphical User Interface (GUI) can discourage reproducibility and an emphasis on the code that the Geocomputational approach requires, as discussed in Chapter 13.

A major aim of this book is to make geographical data analysis more accessible as part of a reproducible workflow.
R is a flexible language that allows access to many spatial software libraries (see section \@ref(why-geocomputation-with-r)).
Before going into the details of the software, however, it is worth taking a step back and thinking about what we mean by geocomputation.

## What is geocomputation?

Geocomputation is a relatively young field with a ~30 year history, dating back to the first conference on the subject in 1996.^[The conference took place at the University of Leeds, where one of the authors (Robin) is currently based and where the 21^st^ GeoComputation was hosted in 2017 (see
[geocomputation.org](http://www.geocomputation.org/)).
]
<!-- todo: which chapters? -->
What distinguishes geocomputation from the older quantitative geography, is its emphasis on "creative and experimental" GIS applications [@longley_geocomputation:_1998].
Additionally, it is also about developing new, research-driven methods [@openshaw_geocomputation_2000]:

> GeoComputation is about using the various different types of geodata and about
developing relevant geo-tools within the overall context of a 'scientific'
approach.

But geocomputation and this book teach more than just methods and code: they are about *doing*
"practical work that is beneficial or useful" [@openshaw_geocomputation_2000].
Of course, reading this book will give you a solid *knowledge* of geocomputational methods, and how to use them via the reproducible examples implemented in the code chunks in each chapter.
But there is much more.
This book aims to teach how to do geocomputation rather than just to think about it.
Hence, you should be also able to apply the learned methods and mastered skills to real-world data, for evidence-based analysis in your own areas of interest.
Moreover, throughout the book we encourage you to make geographic research more reproducible, scientific and socially beneficial. 

This book is also part of the movement towards Geographical Information Science (GDS), a more recent concept which incorporates elements of 'data science' into GIS.
Like Geocomputation, GSD can be defined in terms of its relation with GIS, some of which are outlined in Table \@ref(tab:gdsl).
The focus on reproducibility and a command-line interface in this book is aligned with GDS.


Table: (\#tab:gdsl)Differences in emphasis between the fields of Geographic Information Systems (GIS) and Geographic Data Science (GDS).

Attribute          GIS                        GDS                              
-----------------  -------------------------  ---------------------------------
Home disciplines   Geography                  Geography, Computing, Statistics 
Software focus     Graphical User Interface   Code                             
Reproduciblility   Minimal                    Maximal                          

While embracing recent developments in the field, we also wanted to pay respects to the wider field of Geography, with its 2000 history [@roller_eratosthenes_2010], and the narrower field of *Geographic Information System* (GIS) [@neteler_open_2008].
Geography has played an important role in explaining and influencing humanity's relationship with the natural
world^[A good example of this is Alexander von Humboldt's travels to South America, which laid the foundations for physical and plant geography [@wulf_invention_2015].
]
and this book aims to contribute to this so-called 'Geographic Tradition' [@livingstone_geographical_1992].
GIS has become almost synonymous with handling spatial data on a computer, and provides a basis for excellent open source tools which can be accessed from R, as we will see in Chapter 13.
<!--
todo - add this reference to end of previous line:
(\@ref(gis)).
-->

The book's links to older disciplines were reflected in suggested titles for the book: *Geography with R* and *R for GIS*.
Each has advantages.
The former conveys the message that it comprises much more than just spatial data: 
non-spatial attribute data are inevitably interwoven with geometry data, and Geography is about more than where something is on the map.
The latter communicates that this is a book about using R as a GIS, to perform spatial operations on *geographic data* [@bivand_applied_2013].
However, the term GIS conveys some connotations (see Table \@ref(tab:gdsl)) which simply fail to communicate one of R's greatest strengths:
its console-based ability to seamlessly switch between geographic and non-geographic data processing, modeling and visualization tasks.
By contrast, the term geocomputation implies reproducible and creative programming.
Of course, (geocomputational) algorithms are powerful tools that can become highly complex.
However, all algorithms are composed of smaller parts.
By teaching you its foundations and underlying structure, we aim to empower you to create your own innovative solutions to geographic data problems.

## Why Geocomputation with R?

Early geographers used a variety of tools including rulers, compasses and sextants to advance knowledge about the world. 
However, until John Harrison invented the marine chronometer in the 18th century it had been impossible to determine the exact longitude at sea ('the longitude problem').
Prior to his invention ships followed for centuries a line of constant latitude making each journey much longer, more expensive and often also more dangerous.
Nowadays this seems unimaginable with every smartphone having a GPS receiver at its disposal.
And there are a multitude of other sensors measuring the world in real-time (satellites, radar, autonomous cars, citizens, etc.).
For instance, an autonomous car could create 100 GB or more per day (see e.g., this [article](https://www.economist.com/news/science-and-technology/21696925-building-highly-detailed-maps-robotic-vehicles-autonomous-cars-reality)).
Equally, earth observation data (satellite imagery) has become so big that it is impossible to analyze the corresponding data with a single computer (see [http://r-spatial.org/2016/11/29/openeo.html](http://r-spatial.org/2016/11/29/openeo.html)).
Hence, we need computational power, software and related tools to handle and extract the most interesting patterns of this ever-increasing amount of (geo-)data.
(Geo-)Databases help with data management, storing and querying such large amounts of data.
Through interfaces we can access subsets of these data for further analysis, information extraction and visualization.
In this book we treat R as a 'tool for the trade' for the latter.

R is a multi-platform, open source language for statistical computing and graphics ([https://www.r-project.org/](https://www.r-project.org/)).
With a wide range of packages R also supports advanced geospatial statistics, modeling and visualization.^[The integrated development environment (IDE) [RStudio](https://www.rstudio.com/) deserves mention here from a user perspective as it has made the interactive use of R more accessible].
At its core R is an object-oriented, [functional programming language](http://adv-r.had.co.nz/Functional-programming.html) [@wickham_advanced_2014], and was specifically designed as an interactive interface to other software [@chambers_extending_2016]. 
The latter also includes many 'bridges' to a treasure trove of GIS software, geolibraries and functions.
<!--
todo - add this reference to end of previous line:
(\@ref(gis)).
-->
It is thus ideal for quickly creating 'geo-tools', without needing to master lower level languages (compared to R) such as C, FORTRAN and Java (see section \@ref(software-for-geocomputation)). 
This can feel like breaking free from the metaphorical 'glass ceiling' imposed by GUI-based proprietary geographic information systems (see Table \@ref(tab:gdsl) for a definition of GUI).
What is more, advanced users might even extend R with the power of other languages (e.g., C++ through **Rcpp** or Python through **reticulate**; see also section \@ref(software-for-geocomputation)).

An example showing R's flexibility with regard to geographic software development is its support for generating interactive maps thanks to **leaflet** [@R-leaflet].
The packages **tmap** and **mapview** [@R-tmap; @R-mapview] are built on and extend **leaflet**.
These packages help overcome the criticism that R has "limited interactive [plotting] facilities" [@bivand_applied_2013]. 
The code below illustrates this by generating Figure \@ref(fig:interactive).




```r
library(leaflet)
popup = c("Robin", "Jakub")
leaflet() %>%
  addProviderTiles("NASAGIBS.ViirsEarthAtNight2012") %>% 
  addAwesomeMarkers(lng = c(-3, 23), lat = c(52, 53), popup = popup)
```

<div class="figure" style="text-align: center">
preserve5e7b10bfb25611a9
<p class="caption">(\#fig:interactive)World at night imagery from NASA overlaid by the authors' approximate home locations to illustrate interactive mapping with R.</p>
</div>

It would have been difficult to produce Figure \@ref(fig:interactive) using R a few years ago, let alone embed the results in an interactive html page (the interactive version can be viewed at [robinlovelace.net/geocompr](http://robinlovelace.net/geocompr/intro.html)).
This illustrates R's flexibility and how, thanks to developments such as **knitr** and **leaflet**, it can be used as an interface to other software, a theme that will recur throughout this book.
The use of R code, therefore, enables teaching geocomputation with reference to reproducible examples such as that provided in \@ref(fig:interactive) rather than abstract concepts.

## Software for geocomputation

R is a powerful tool for geocomptation.
However, other languages can be used and it is useful to be aware of these for historical context and to help understand the wider open source geospatial programming ecosystem, of which R is a part.
With this motivation in mind the section briefly introduces the languages [C++](https://isocpp.org/), [Java](https://www.oracle.com/java/index.html) and [Python](https://www.python.org/) for geocomputation, with reference to R.

A natural choice for geocomputation would be C++ since major GIS packages (e.g., [GDAL](http://www.gdal.org/), [QGIS](www.qgis.org), [GRASS](https://grass.osgeo.org/), [SAGA](www.saga-gis.org), and even [ArcGIS](https://www.arcgis.com/)) often rely in great parts on it.
This is because well-written C++ can be blazzingly fast, which makes it a good choice for performance-critical applications such as the processing of large spatial data.
Usually, people find it harder to learn than Python or R.
It is also likely that you have to invest a lot of time to code things that are readily available in R.
Therefore, we would recommend to learn R, and subsequently to learn C++ through **Rcpp** if a need for performance optimization arises.
Subsequently, you could even implement geoalgorithms you are missing from the most common desktop GIS with the help of **Rcpp**^[Though, in that case we would recommend to contribute the C++ code to one of the open-source GIS packages since this would make the geoalgorithm available to a wider audience.
In turn, you could access the GIS software via one of the available R-GIS interfaces. <!--(\@ref(gis))]-->].

Java is another important (and versatile) language used in GIScience.
For example, the open-source desktop GIS [gvSig](http://www.gvsig.com/en/products/gvsig-desktop), [OpenJump](http://openjump.org/) and [uDig](http://udig.refractions.net/) are written in Java.
There are also many open source add-on libraries available for Java, including [GeoTools](http://docs.geotools.org/) and the [Java Topology Suite](https://www.locationtech.org/projects/technology.jts).^[Please note, that GEOS is a C++ port of the Java Topology Suite.]
Furthermore, many server-based applications use Java including among others [Geoserver/Geonode](http://geonode.org/), [deegree](http://www.deegree.org/) and [52°North WPS](http://52north.org/communities/geoprocessing/wps/).

Java's object-oriented syntax is similar to C++, however, its memory management is much simpler.
Still, it is rather unforgiving regarding class, object and variable declarations forcing you to think about a well-designed programming structure.
This is especially useful in large projects with thousands of lines of codes placed in numerous files.
Following the *write once, run anywhere* principle, Java is platform-independent (which is unusual for a compiled programming language).
Overall, Java's compiled language has an excellent performance on large-scale systems making it a suitable candidate for complex architecture projects such as programming a desktop GIS.
However, Java is probably less suitable for statistical modeling and visualization compared to Python or R.
First and foremost, though you can do data science with Java [@brzustowicz_data_2017], Java offers much fewer statistical libraries especially when compared with R.
Secondly, interpreted languages (such as R and Python) are often easier to write (at the prize of lower performance) than compiled languages (such as Java and C++).
Moreover, interpreted languages allow a faster and interactive (line-by-line) code implementation.
Finally, R's native support of data types such as data frames and matrices is especially advantageous when it comes to analyzing data.

Lastly, we will introduce Python for geocomputation
Many people believe that R and Python are battling for supremacy in the field of data science.
This is accompanied by a partly offensive as much as often rather subjective discussion on what to learn or what to use.
We believe that both languages have their merits, and in the end it is about doing geocomputation and communicating the corresponding results regardless of the chosen software.
Moreover, both languages are object-oriented, and have lots of further things in common.
Learning one language should give you a headstart when choosing to learn the other as well.
R's major advantage is that statisticians wrote hundreds of statistical packages (unmatched by Python) explicitly for other statisticians.
By contrast, Python's major advantage is that it is (unlike R) a multi-purpose language thereby bringing together people from diverse fields which also explains Python's bigger user base compared to R's.
So if you like Python better or you think it better suits your needs (for example because you are also interested in web and GUI development), go for it.
In fact, we often advise our students to start with Python just because the major GIS software packages provide Python libraries that lets the user access its geoalgorithms from the Python command line^[`grass.script` for GRASS (https://grasswiki.osgeo.org/wiki/GRASS_and_Python), `saga-python` for SAGA-GIS (http://saga-python.readthedocs.io/en/latest/), `processing` for QGIS and `arcpy` for ArcGIS.
].
However, when the teaching moves on to statistical geoprocessing and spatial predictive modeling we guide them towards R where they can take advantage of the concepts already learned through Python.
Nevertheless, you can also use Python for the most common statistical learning techniques (though R tends to be more on the bleeding edge regarding new statistical development including those in the geostatistical community).
In addition, Python also offers excellent support for spatial data analysis and manipulation (see packages **osgeo**, **Shapely**, **NumPy**, **osgeo**, **PyGeoProcessing**). 
We refer you to @garrard_geoprocessing_2013 for an introduction to geoprocessing with Python.

## R's spatial ecosystem

Before cracking-on with the action, a few introductory remarks are needed to explain the approach taken here and provide context.
<!-- paragraphs (with references to chapters in the book): -->
<!-- 1. this book focus -> sf + raster/stars + leaflet/mapview (the recent state of spatial R); the history of R spatial is way longer -->

There are many ways to handle spatial data in R, with dozens of packages in the area.^[An overview of R's spatial ecosystem can be found in the CRAN Task View on the Analysis of Spatial Data
(see [cran.r-project.org/web/views/Spatial.html](https://cran.r-project.org/web/views/Spatial.html)).]
In this book we endeavor to teach the state-of-the-art in the field whilst ensuring that the methods are future-proof.
Like many areas of software development, R's spatial ecosystem is rapidly evolving.
Because R is open source, these developments can easily build on previous work, by 'standing on the shoulders of giants', as Isaac Newton put it in [1675](http://digitallibrary.hsp.org/index.php/Detail/Object/Show/object_id/9285).
This approach is advantageous because it encourages collaboration and avoids 'reinventing the wheel'.
The package **sf** (covered in Chapter \@ref(spatial-class)), for example, builds on its predecessor **sp**.

A surge in development time (and interest) in 'R-Geo' has followed the award of a grant by the R Consortium for the development of support for Simple Features, an open-source standard and model to store and access vector geometries. 
This resulted in the **sf** package (covered in \@ref(intro-sf)).
Multiple places reflect the immense interest in **sf**. This is especially true for the [R-sig-Geo Archives](https://stat.ethz.ch/pipermail/r-sig-geo/), a long-standing open access email list containing much R-spatial wisdom accumulated over the years.
Many posts on the list now discuss **sf** and related packages, suggesting that R's spatial software developers are using the package and, therefore, it is here to stay.

We even propose that the release of **sf** heralds a new era for spatial data analysis and geocomputation in R.
This era ^[We refrain from labeling it the **geoverse** with any seriousness awaiting a better name!] clearly has the wind in its sails, and is set to dominate future developments in R's spatial ecosystem for years to come.
So time invested in learning the 'new ways' of handling spatial data and, hopefully, reading this book, is well spent!

<div class="figure" style="text-align: center">
<img src="figures/spatial-package-growth.png" alt="The popularity of spatial packages in R. The y-axis shows the average number of downloads, within a 30-day rolling window, of R's top 5 spatial packages, defined as those with the highest number of downloads within the last 30 days." width="1050" />
<p class="caption">(\#fig:cranlogs)The popularity of spatial packages in R. The y-axis shows the average number of downloads, within a 30-day rolling window, of R's top 5 spatial packages, defined as those with the highest number of downloads within the last 30 days.</p>
</div>

It is noteworthy that shifts in the wider R community, as exemplified by the data processing package **dplyr** (released in [2014](https://cran.r-project.org/src/contrib/Archive/dplyr/)) influenced shifts in R's spatial ecosystem. 
Alongside other packages that have a shared style and emphasis on 'tidy data' (including e.g., **ggplot2**), **dplyr** was placed in the **tidyverse** 'metapackage' in late [2016](https://cran.r-project.org/src/contrib/Archive/tidyverse/).
The **tidyverse** approach, with its focus on long-form data and fast, intuitively named functions, has become immensely popular.
This has led to a demand for 'tidy spatial data' which has been partly met by **sf** and other approaches such as the GitHub package [**tabularaster**](https://hypertidy.github.io/tabularaster/).
An obvious feature of the **tidyverse** is the tendency for packages to work in harmony.
Although an equivalent **geoverse** is presently missing, there is an on-going discussion of harmonizing R's many spatial packages.^[
See the [r-spatial](https://github.com/r-spatial/) organisation and conversations in the [discussion](https://github.com/r-spatial/discuss/issues/11) repo for more on this.
] and a growing number of actively developed packages which are designed to work in harmony with **sf** (Table \@ref(tab:revdep)) and 


Table: (\#tab:revdep)The top 5 most downloaded packages that depend on sf, in terms of average number of downloads per day over the previous month. As of 2017-08-12 there are 24 packages which import sf.

package      Downloads
----------  ----------
plotly            1672
leaflet            464
mapview            193
geojsonio          172
tigris              90

## R's spatial history

There are many benefits of using recent packages such as **sf**, with the caveat that they are generally less stable than mature packages such as its predecessor, the **sp**-package.

The saying "if you live on the cutting edge you risk getting hurt" captures this well, meaning that older packages may be more appropriate for applications requiring stability and backwards-compatibility with other mature packages.
Another reason for knowing about the history of geocomputation with R is that there is a wealth of functions, use-cases and teaching material written using older packages in R's spatial ecosystem, which can still be useful today if you know where to look.

The beginnings of spatial capabilities in R are closely connected with its predecessor - the S language [@bivand_implementing_2000].
The 1990s saw the development of numerous S scripts and a handful of packages for spatial statistics.
Some of these, including **spatial**, **sgeostat** and **splancs**, eventually became R packages [@rowlingson_splancs:_1993; @rowlingson_splancs:_2017;@venables_modern_2002; @university_sgeostat:_2016].

Volume 1/2 of R News (the predecessor of The R Journal) contained an overview of spatial statistical software in R at the time, much of which was based on previous code written for S/S-PLUS [@ripley_spatial_2001].
This overview described packages for spatial smoothing and interpolation (e.g., **akima**, **spatial**, **sgeostat** and **geoR**) and point pattern analysis [**splancs** and **spatstat**; @akima_akima:_2016; @rowlingson_splancs:_2017; @jr_geor:_2016].
<!-- there is something wrong with the citation: Jr and Diggle 2016 (@jr_geor:_2016)-->
While all these are still available on CRAN, **spatstat** stands out among them, as it remains dominant in the field of spatial point pattern analysis [@baddeley_spatial_2015].

The following R News issue (Volume 1/3) put spatial packages in the spotlight again, with an introduction to **splancs** and a commentary on future prospects regarding spatial statistics [@bivand_more_2001].
Additionally, the issue introduced two packages for testing spatial autocorrelation that eventually became part of **spdep** [@bivand_spdep:_2017].
Notably, the commentary mentions the need for standardization of spatial interfaces, efficient mechanisms for exchanging data with GIS, and handling of spatial metadata such as coordinate reference systems (CRS).

**maptools** [written by Nicholas Lewin-Koh; @bivand_maptools:_2017] is another important package from this time.
Initially, **maptools** just contained a wrapper around [shapelib](http://shapelib.maptools.org/), and permitted the reading of ESRI Shapefiles into geometry nested lists. 
The corresponding and nowadays obsolete S3 class called "Map" stored this list alongside an attribute data frame. 
The work on the "Map" class representation was nevertheless important since it directly fed into **sp** prior to its publication on CRAN.

In 2003, Hornik et al. [-@hornik_approaches_2003] published an extended review of spatial packages. 
Around this time the development of R's spatial capabilities increasingly supported interfaces to external libraries, especially to GDAL and PROJ.4.
These interfaces facilitated geographic data I/O (covered in chapter \@ref(read-write)) and CRS transformations, respectively.
@hornik_approaches_2003 proposed a spatial data class system, including support for points, lines, polygons and grids based on GDAL's support for a wide range of spatial data formats.
All these ideas contributed to the packages **rgdal** and **sp**, which became the foundational packages for spatial data analysis with R [@bivand_applied_2013].

**rgdal** provided GDAL bindings for R which greatly extended R's spatial capabilities in terms of access to previously unavailable spatial data formats.
Initially, Tim Keitt released it in 2003 with support for raster drivers.
But soon, **rgdal** also enabled storing information about coordinate reference system (building on top of the PROJ.4 library), allowed map projections, datum transformations and OGR vector reading. 
Many of these additional capabilities were thanks to Barry Rowlingson who folded them into the **rgdal** codebase in March 2006.^[A presentation at the 2003 DSC conference in Vienna gives the background as he saw it then [@rowlingson03]; see also his announcement of the **Rmap** package on [R-help](https://stat.ethz.ch/pipermail/r-help/2003-January/028413.html) in early 2003.]

**sp**, released in 2005, overcame R's inability to distinguish spatial and non-spatial objects.
It grew from a [workshop](http://spatial.nhh.no/meetings/vienna/index.html) before, and a session at the 2003 DSC conference in Vienna, gathering input from most interested package developers. 
At the same time, [sourceforge](https://sourceforge.net/) was chosen for development collaboration (migrated to [R-Forge](https://r-forge.r-project.org) five years later) and the [R-sig-geo mailing list](https://stat.ethz.ch/mailman/listinfo/r-sig-geo) was started.

Prior to 2005, spatial coordinates were generally treated as any other number. 
This changed with **sp** as it provided generic classes and methods for spatial data.
The sophisticated class system supported points, lines, polygons and grids, with and without attribute data. 

<!--???-->
<!-- points, multipoints, pixels, full grid, line, lines, spatial lines, polygon, polygons, spatial polygons -->
Making use of the S4 class system, **sp** stores each piece of 'spatially specific' information (such as bounding box, coordinate reference system, attribute table) in slots, which are accessible via the `@` symbol.
For instance, **sp**-classes store attribute data in the `data` slot as a `data.frame`.
This enables non-spatial data operations to work alongside spatial operations (covered in chapters \@ref(attr) and \@ref(spatial-data-operations), respectively).
Additionally, **sp** implemented generic methods for spatial data types for well-known functions such as `summary()` and `plot()` .

In the following, **sp** classes rapidly became the go-to standard for spatial data in R, resulting in a proliferation of packages that depended on it from around 20 in 2008 and over 100 in 2013 [@bivand_applied_2013].
Now more than 200 packages rely on **sp**, making it an important part of the R ecosystem. 
<!-- https://github.com/Robinlovelace/geocompr/issues/58 -->
<!-- https://github.com/edzer/sfr/issues/387#issuecomment-308949140 -->

Prominent R packages using **sp** include: **gstat**, for spatial and spatio-temporal geostatistics; **geosphere**, for spherical trigonometry; and **adehabitat** used for the analysis of habitat selection by animals [@R-gstat; @calenge_package_2006; @hijmans_geosphere:_2016].

While **rgdal** and **sp** solved many spatial issues, R was still lacking geometry calculation abilities.
Therefore, Colin Rundel started to develop a package that interfaces GEOS, an open-source geometry library, during a Google Summer of Coding project in 2010.
The resulting **rgeos** package [first released in 2010; @R-rgeos] brought geometry calculations to R by allowing functions and operators from the GEOS library to manipulate **sp** objects.
Another limitation of **sp** was its limited support of raster data.
The **raster**-package [first released in 2010; @R-raster] overcame this by providing a `raster` class and functions for creating, reading and writing raster data.
A key feature of **raster** is its ability to work with data sets that are too large to fit into the main memory (RAM), thereby overcoming one of R's major limitations when working on raster data.^[The
**raster** package also provided tools for raster algebra, general raster functions and the development of more additional raster functions.]

In parallel with or partly even preceding the development of spatial classes and methods came the support for R as an interface to dedicated GIS software.
The **GRASS** package [@bivand_using_2000] and follow-on packages **spgrass6** and **rgrass7** (for GRASS GIS 6 and 7, respectively) were prominent examples in this direction [@bivand_spgrass6:_2016;@bivand_rgrass7:_2016].
Other examples of bridges between R and GIS include **RSAGA** [@R-RSAGA, first published in 2008], **ArcGIS** [@brenning_arcgis_2012, first published in 2008], and **RQGIS** [@R-RQGIS, first published in 2016].
<!-- ADD THIS LATTER -->
<!-- More information about interfaces between R and GIS software could be find in \@ref(gis). -->

Map making was not a focus of R's early spatial capabilities.
But soon **sp** provided methods for advanced map making using both the base and lattice plotting system. 
Despite this, a demand for the layered grammar of graphics was growing especially after the release of **ggplot2** in 2007.
**ggmap** extended **ggplot2**'s spatial capabilities [@kahle_ggmap:_2013].
However, its main purpose was the easy access of several APIs to automatically download map tiles (among others, Google Maps and OpenStreetmap) and subsequent plotting of these as a basemap. 
<!--Additionally, *ggmap** lets you use (mainly Google's) geocoding and routing services.-->
Though **ggmap** facilitated map-making with **ggplot2**, one main limitation remained.
To make spatial data work with the **ggplot2** system, one needed to `fortify` spatial objects.
Basically, this means, you need to combine the coordinates and attribute slots of a spatial class object into one data frame.
While this works well in the case of points, it duplicates the same information over and over again in the case of polygons, since each coordinate (vertex) of a polygon receives the attribute data of the polygon.
This is especially disadvantageous if you need to deal with tens of thousands of polygons.
With the introduction of simple features to R this limitation disappears, and it seems likely that this will make **ggplot2** the standard tool for the visualization of vector data. 
This might be different regarding the visualization of raster data. Raster visualization methods received a boost with the release of **rasterVis** [@lamigueiro_displaying_2014] which builds on top of the lattice system.
More recently, new packages aim at easing the creation of complex, high-quality maps with minimal code.
The **tmap** package (released in 2014) might serve as an archetype for this kind of development [@R-tmap].
It facilitates the user-friendly creation of thematic maps with an intuitive command-line interface (see also [**mapmisc**](https://cran.r-project.org/package=mapmisc)) . 
<!-- ADD THIS LATTER -->
<!-- CITE the paper Tennekes, M. (2017) tmap: Thematic Maps in R. Forthcoming in the Journal
of Statistical Software http://von-tijn.nl/tijn/research/presentations/tmap_user2017.pdf-->
**tmap** is a sophisticated yet user friendly mapping package which works in harmony with the **leaflet** package (released in 2015) for interactive map making [@R-leaflet]. 
Similarly, the **mapview** package builds also on top of **leaflet** [@R-mapview] for interactive mapping based on **sp** or **sf** objects. **mapview** allows the access of a wide range of background maps, scale bars and more.

However, it is noteworthy that among all the recent developments described above, the support for simple features [**sf**; @R-sf] has been without doubt the most important evolution in R's spatial ecosystem.
Naturally, this is the reason why we will describe **sf** in detail in Chapter \@ref(spatial-class).

<!-- ## How to read this book -->

## Exercises

1. Think about the terms 'GIS', 'GDS' and 'Geocomputation' described above. Which is your favorite, and why?

2. Provide three reasons for using a scriptable language such as R for geocomputation instead of using an established GIS program such as QGIS.

3. Name two advantages and two disadvantages of using mature packages compared with 'cutting edge' packages for spatial data (for example **sp** vs **sf**).


<!--chapter:end:01-introduction.Rmd-->


# Geographic data in R {#spatial-class}

## Prerequisites {-}

This is the first practical chapter of book and therefore has software requirements.
We assume you have a recent version of R installed on your computer and are comfortable using it at the command line, e.g. via an integrated development environment (IDE) such as RStudio (recommended).
R/RStudio works on all major operating systems and can be installed and set-up in a few minutes on most modern computers, as described in [section 2.3](https://csgillespie.github.io/efficientR/set-up.html#r-version) and [section 2.5](https://csgillespie.github.io/efficientR/set-up.html#rstudio) of @gillespie_efficient_2016 (other guides are available).

If you are not a regular R user is worth taking time to ensure that you have an efficient R workflow because this will make the subsequent worked examples easier to run on your own computer, e.g. as part of an RStudio '[project](https://csgillespie.github.io/efficientR/set-up.html#project-management)' such as that provided in the root directory of the [`geocompr`](https://github.com/Robinlovelace/geocompr) GitHub repository.
We recommend getting up-to-speed with the language, with reference to resources such as @gillespie_efficient_2016, @grolemund_r_2016, and online interactive guides such as that provided by [DataCamp](https://www.datacamp.com/courses/free-introduction-to-r), before proceeding with the chapter.

* * *

After R is installed and set-up, packages which extend R must be installed and loaded for it to handle spatial data.
On Mac and Linux operating systems there are a few additional requirements: see the [README](https://github.com/r-spatial/sf) of the **sf** package for instructions.
The **sf**, **raster**, and **spData** packages used in this chapter can be installed and loaded with the following commands:


```r
install.packages("sf")
install.packages("raster")
install.packages("spData")
library(sf)
library(raster)
library(spData)
```

This chapter will provide brief explanations of both the fundamental geographic data types: vector and raster.
A brief abstract description is provided of each before moving quickly to their implementation in R packages designed specifically for handling them.
Both are vital to the sciences, although which will be of most use will largely depend on your discipline:

- Because human settlements and boundaries tend to be complex with precise borders defined by legal systems, vector data tends to dominate in the social sciences.
- In environmental sciences, by contrast, raster data tend to dominate due to its links to remote sensing.

However, there is a substantial level of overlap:
ecologists and demographers, for example, commonly use both vector and raster geographical data types.
We therefore strongly recommend learning about each type of data before proceeding to understand how to manipulate them in subsequent chapters.

## Vector data

Vector data are based on points that are located on a Cartesian (or geographic) coordinate system.
Each point in vector data is typically described by two numbers representing distance from the $origin$ along the $x$ (horizontal) and $y$ (vertical) axis in Euclidean space.^[In 3 dimensional coordinate systems three numbers are needed for each of the three axes, $x$, $y$ and $z$.]
In mathematical notation these points are typically represented as numbers separated by commas and enclosed by a pair of brackets: 
$(1, 3)$ for example, represents a point located one unit to the right and three units above the origin.
There is clear link between these vector points and the `vector` class in R.
The following line of code, for example, creates a 2 dimensional vector:


```r
p = vector(mode = "numeric", length = 2)
```

More commonly one would read-in data with functions such as `read_csv()` from the **tidyverse** or `read_sf()` from the **sf** package, covered in chapter \@ref(read-write).
To generate new data (e.g. for testing), one would more commonly use the command `c()` (think of 'c' for 'combine'), as illustrated
below:^[Other methods for generating numbers include with the `seq()` function (short for 'sequence') for generating regular sequences or `runif()`, `rnorm()` and other functions generating random numbers following some kind of probability distribution.
The **mapedit** package can be used to create spatial data manually on an interactive map.
]


```r
p = c(1, 3)
```

Now this can be plotted in Cartesian space, as illustrated in figure \@ref(fig:cartesian):


```r
plot(p[1], p[2], xlim =  c(0, 5), ylim = c(0, 5))
```

<div class="figure" style="text-align: center">
<img src="figures/cartesian-1.png" alt="Illustration of vector point data in base R." width="576" />
<p class="caption">(\#fig:cartesian)Illustration of vector point data in base R.</p>
</div>

Generally vector datasets have a high level of precision (but not necessarily accuracy as we will see in \@ref(units)).
Raster datasets, by contrast, use cells that break the surface up into a cells of constant size (*resolution*). Rasters therefore aggregate spatially specific features to a given resolution resulting in small features being blurred or lost in raster datasets.
<!-- todo: add figure(s) showing raster data and blurring? -->
This book uses **sf** and **raster** packages to work with vector data and raster datasets respectively.

### An introduction to simple features {#intro-sf}

Simple features is an open standard developed and endorsed by the Open Geospatial Consortium ([OGC](http://portal.opengeospatial.org/files/?artifact_id=25355)) to represent a wide range of geographical information.
It is a hierarchical data model that simplifies geographic data by condensing a complex range of geographic forms into a single geometry class.
Only 7 out of 68 possible types of simple feature are currently used in the vast majority of GIS operations (Figure \@ref(fig:sf-ogc)).
All of these are fully supported (with plotting methods etc) in the R package **sf** [@R-sf].^[
The full OGC standard includes rather exotic geometry types including 'surface' and 'curve' geometry types, which currently have limited application in real world applications.
All 68 types can be represented in R, although (at the time of writing) all methods, such as plotting, are only supported for the 7 types that are used.
]

<div class="figure" style="text-align: center">
<img src="figures/sf-classes.png" alt="The subset of the Simple Features class hierarchy supported by sf. Figure based on the Open Geospatial Consortium document [06-103r4](http://www.opengeospatial.org/standards/sfa)." width="100%" />
<p class="caption">(\#fig:sf-ogc)The subset of the Simple Features class hierarchy supported by sf. Figure based on the Open Geospatial Consortium document [06-103r4](http://www.opengeospatial.org/standards/sfa).</p>
</div>

**sf** can represent all common vector geometry types (raster data classes are not supported by **sf**): points, lines, polygons and their respective 'multi' versions (which group together features of the same type into a single feature).
**sf** also supports geometry collections, which can contain multiple geometry types in a single feature.
Given the breadth of geographic data forms, it may come as a surprise that a class system to support all of them is provided in a single package, which can be installed from CRAN:^[The
development version, which may contain new features, can be installed with `devtools::install_github("r-spatial/sf").`
]
**sf** incorporates the functionality of the 3 main packages of the **sp** paradigm (**sp** [@R-sp] for the class system, **rgdal** [@R-rgdal] for reading and writing data, **rgeos** [@R-rgeos] for spatial operations undertaken by GEOS) in a single, cohesive whole.
This is well-documented in **sf**'s [vignettes](http://cran.rstudio.com/package=sf):


```r
vignette("sf1") # for an introduction to the package
vignette("sf2") # for reading, writing and converting Simple Features
vignette("sf3") # for manipulating Simple Features
```

As the first vignette explains, simple feature objects in R are stored in a data frame, with geographic data occupying special column, a 'list-column'. This column is usually named 'geom' or 'geometry'.
A 'real world' example is loaded by the **spData** package, which loads the `world` object:


```r
library(spData)
data("world")
```

In the above code **spData** silently loaded the `world` dataset (and many other spatial datasets - see [the spData website](https://nowosad.github.io/spData/) for a full list).
The dataset contains spatial and non-spatial information, as shown by the function `names()`, which reports the column headings in data frames. 
This can be seen as the final column name of `world`:


```r
names(world)
#>  [1] "iso_a2"    "name_long" "continent" "region_un" "subregion"
#>  [6] "type"      "area_km2"  "pop"       "lifeExp"   "gdpPercap"
#> [11] "geom"
```

It is the contents of this modest-looking `geom` column that gives `sf` objects their spatial powers.
It's actually a list-column, containing all the coordinates needed to plot the result as a map using the `plot()` method, the results of which are presented in Figure \@ref(fig:world-all).


```r
library(sf) # must be loaded to plot sf objects
#> Linking to GEOS 3.5.0, GDAL 2.1.0, proj.4 4.8.0
plot(world)
#> Warning: plotting the first 9 out of 10 attributes; use max.plot = 10 to
#> plot all
```

<div class="figure" style="text-align: center">
<img src="figures/world-all-1.png" alt="A spatial plot of the world using the sf package, with a facet for each attribute." width="576" />
<p class="caption">(\#fig:world-all)A spatial plot of the world using the sf package, with a facet for each attribute.</p>
</div>

Note that instead of creating a single map, as most GIS programs would, the `plot()` command has created multiple maps, one for each variable in the `world` datasets.
This behavior can be useful for exploring the spatial distribution of different variables and is discussed further in \@ref(basic-map) below.

Being able to treat spatial objects as regular data frames with spatial powers has many advantages, especially if you are already used to working with data frames.
The commonly used `summary()` function, for example, provides a useful overview of the variables within the `world` object, but prefixed with some information about the object's spatial component:


```r
summary(world["lifeExp"])
#>     lifeExp                geom    
#>  Min.   :48.9   MULTIPOLYGON :177  
#>  1st Qu.:64.3   epsg:4326    :  0  
#>  Median :72.8   +proj=long...:  0  
#>  Mean   :70.6                      
#>  3rd Qu.:77.1                      
#>  Max.   :83.6                      
#>  NA's   :9
```

The result provides a quick summary of both the non-spatial and spatial data contained in `world`: the average life expectancy is 73 years (ranging from less than 50 to more than 80 years) across all countries, and these are represented by `MULTIPOLYGON`s, allowing many polygons per country (this is needed for countries with many islands such as Indonesia and Greece). 

<!-- TODO: cross-reference section covering CRSs. -->

Note that by appending `["lifeExp"]` onto the object name in the previous code chunk, only the relevant column was summarized.
We explore such 'attribute operations' in Chapter \@ref(attr).
First, it's worth taking a look at the basic behavior and contents of this simple feature object, which can usefully be thought of as a '**S**patial data**F**rame).

`sf` objects are easy to subset.
The code below shows its first 2 rows and 3 columns.
The output shows 2 major differences compared with a regular `data.frame`: the inclusion of additional geographic data (`geometry type`, `dimension`, `bbox` and CRS information - `epsg (SRID)`, `proj4string`), and the presence of final `geometry` column:


```r
world[1:2, 1:3]
#> Simple feature collection with 2 features and 3 fields
#> geometry type:  MULTIPOLYGON
#> dimension:      XY
#> bbox:           xmin: 11.6401 ymin: -17.93064 xmax: 75.15803 ymax: 38.48628
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#>   iso_a2   name_long continent                           geom
#> 1     AF Afghanistan      Asia MULTIPOLYGON(((61.210817091...
#> 2     AO      Angola    Africa MULTIPOLYGON(((16.326528354...
```

All this may seem rather complex, especially for a class system that is supposed to be simple.
However, there are good reasons for organizing things this way and using **sf**.

<!-- It's a `MULTIPOLYGON` with 177 features and a geographical (longitude/latidue) coordinate reference system (CRS) with an EPSG code of `4326`. -->

### Why Simple Features?

There are many advantages of **sf** over **sp**, including:

- Faster reading and writing of data (more than 10 times faster in some cases)
- Better plotting performance
- **sf** objects can be treated as dataframes in most operations
- **sf** functions can be combined using `%>%` operator and works well with the [tidyverse](http://tidyverse.org/) collection of R packages
- **sf** function names are relatively consistent and intuitive (all begin with `st_`) compared with the function names and syntax of the **sp**, **rgdal** and **rgeos** packages that it supersedes.

A broader advantage is that simple features are so well-supported by other software products, not least PostGIS, which has heavily influenced the design of **sf**.

A disadvantage you should be aware of, however, is that **sf** is not *feature complete* and that it continues to evolve.
The transition from **sp** to **sf** will likely take many years, and many spatial packages may never switch.
Even if you discover spatial data with R through the **sf** package, it is still worth at least being aware of **sp** classes, even if you rarely use them for everyday geospatial tasks.

Fortunately it is easy to translate between **sp** and **sf** using the `as()` function: 


```r
library(sp)
world_sp = as(object = world, Class = "Spatial")
```

### Basic map making {#basic-map}

Basic maps in **sf** can be created quickly with the base `plot()` function. Unlike **sp**, however, **sf** by default creates a faceted plot, one sub-plot for each variable, as illustrated in the left-hand image in Figure \@ref(fig:sfplot). 


```r
plot(world[3:4])
plot(world["pop"])
```

<div class="figure" style="text-align: center">
<img src="figures/sfplot-1.png" alt="Plotting with sf, with multiple variables (left) and a single variable (right)." width="49%" /><img src="figures/sfplot-2.png" alt="Plotting with sf, with multiple variables (left) and a single variable (right)." width="49%" />
<p class="caption">(\#fig:sfplot)Plotting with sf, with multiple variables (left) and a single variable (right).</p>
</div>

As with **sp**, you can add layers to your maps created with `plot()`, with the argument `add = TRUE`.^[In
fact, when you `plot()` an **sf** object, R is calling `sf:::plot.sf()` behind the scenes.
`plot()` is a generic method that behaves differently depending on the class of object being plotted.]
To illustrate this, and prepare for content covered in chapters \@ref(attr) and \@ref(spatial-data-operations) on attribute and spatial data operations, we will subset and combine countries in the `world` object, to create a single object that represents Asia:


```r
asia = world[world$continent == "Asia", ]
asia = st_union(asia)
```

We can now plot the Asian continent over a map of the world.
Note, however, that this only works if the initial plot has only 1 layer:


```r
plot(world["pop"])
plot(asia, add = TRUE, col = "red")
```

<img src="figures/asia-1.png" width="50%" style="display: block; margin: auto;" />

This can be very useful for quickly checking the geographic correspondence between two or more layers: 
the `plot()` function is fast to execute and requires few lines of code, but does not create interactive maps with a wide range of options.
For more advanced map making we recommend using a dedicated visualization package such as **tmap**, **ggplot2**, **mapview**, or **leaflet**.
<!-- TODO: cross reference advanced mapping chapter -->

<!-- 
- plot() function 
- map export 
-->

<!-- Maybe show also somewhere that `world[0]` produces only a plot of the geometry which is rather useful if you do not want to plot a specific attribute. This way, you can for example dismiss the col = "white"-argument in your Nigeria example. -->



#### Further work

**sf** makes R data objects more closely aligned to the data model used in GDAL and GEOS, in theory making spatial data operations faster.
The work here provides a taste of the way **sf** operates but there is much more to learn (see Chapter \@ref(spatial-data-operations)). And there is also a wealth of information in the highly recommended vignettes of the package.

As a final exercise, we'll see one way of how to do a spatial overlay in **sf**. First, we convert the countries of the world into centroids, and then subset those in Asia. Finally, the `summary`-command tells us how many centroids (countries) are part of Asia (43) and how many are not (134).


```r
world_centroids = st_centroid(world)
#> Warning in st_centroid.sfc(st_geometry(x)): st_centroid does not give
#> correct centroids for longitude/latitude data
sel_asia = st_intersects(world_centroids, asia, sparse = FALSE)
#> although coordinates are longitude/latitude, it is assumed that they are planar
summary(sel_asia)
#>      V1         
#>  Mode :logical  
#>  FALSE:134      
#>  TRUE :43
```

Note: another way of achieving the same result is with a GEOS function for identifying spatial overlay, which we'll cover in more detail in Chapter \@ref(spatial-data-operations).

**sf**'s `plot()` function builds on base plotting methods, allowing access to its many optional arguments (see `?plot`).
This provides powerful but not necessarily intuitive functionality, as illustrated by the variable circle sizes generated by the `cex` argument (see Figure \@ref(fig:africa), generated by the code below).


```r
plot(world["continent"])
plot(world_centroids, add = TRUE, cex = world$pop / 1e8, lwd = 3)
```

<div class="figure" style="text-align: center">
<img src="figures/africa-1.png" alt="Centroids representing country population, diameter being proportional to population." width="576" />
<p class="caption">(\#fig:africa)Centroids representing country population, diameter being proportional to population.</p>
</div>

<!-- More appropriate for subsequent chapters. -->
<!-- This shows that there are 43 countries in Asia -->
<!-- We can check if they are the same countries as follows: -->

<!-- ```{r} -->
<!-- africa_centroids2 = world_centroids[sel_africa,] -->
<!-- identical(africa_centroids, africa_centroids2) -->
<!-- ``` -->

### Simple feature classes {#sf_classes}

To understand new data formats in depth, it often helps to generate them for first principles.
This section walks through vector spatial classes step-by-step, from the elementary simple feature geometry to simple feature objects, with class `sf`, representing complex spatial data.
Before describing each geometry type that the **sf** package supports it is worth taking a step back to understand the building blocks of `sf` objects. 
As stated in section \@ref(intro-sf), simple features are simply dataframes with at least one special column that makes it spatial.
These spatial columns are often called `geom` or `geometry` and can be like non-spatial columns: `world$geom` refers to the spatial element of the `world` object described above.
These geometry columns are 'list columns' of class `sfc`: they are simple feature collections.
In turn, `sfc` objects are composed of one or more objects of class `sfg`: simple feature geometries.

To understand how the spatial components of simple features work, it is vital to understand simple feature geometries.
For this reason we cover each type currently supported `sfg` in the next sections before moving to describe how they can be combined to form `sfc` and eventually full `sf` objects.

#### Simple feature geometry types {#geometry}

<!-- This section demonstrates how the full range of geometry types supported by the **sf** package can be created, combined and plotted. -->
Geometries are the basic building blocks of simple features.
Simple features could be represented as one of the 17 geometry types using the **sf** package.
In this chapter we will focus on seven, the most commonly used, simple features types: `POINT`, `LINESTRING`, `POLYGON`, `MULTIPOINT`, `MULTILINESTRING`, `MULTIPOLYGON` and `GEOMETRYCOLLECTION`.<!--FIG-->
The whole list of possible feature types could be found in [the PostGIS manual ](http://postgis.net/docs/using_postgis_dbmanagement.html).

Simple features, outside of an R environment, could be represented in one of two ways, ether as a well-known binary (WKB) or well-known text (WKT). 
Well-known binary (WKB) representations are usually hexadecimal strings, which are used to transfer and store geometry objects in databases.
Well-known text (WKT), on the other hand, is a text markup description of simple features. 
Both formats are exchangeable, therefore we would focus only on the well-known text (WKT) representation.

All of the geometry types are built of points. 
Each point could be described as coordinates in a 2D, 3D or 4D space:

- X and Y coordinates represent location of points. It could be either easting and northing or longitude and latitude.
- A Z coordinate denotes altitude.
- An M coordinate ("measure") allows to represent some measure associated to the point, but not the whole feature. 
This coordinate could be a time of measurement, information who measured this point or what's the error of measurement.

As a result, four possible types of points exist - XY (two-dimensional), XYZ (three-dimensional containing altitude), XYM (three-dimensional containing measure) and XYZM (four-dimensional).
They could be easily describes as a well-known text:

- XY - `POINT (5 2)`
- XYZ - `POINT (5 2 3)`
- XYM - `POINTM (5 2 1)`
- XYZM - `POINT (5 2 3 1)`

<img src="figures/point-1.png" width="576" style="display: block; margin: auto;" />

A linestring is represented by a sequence of points with linear interpolation between points, for example:

- `LINESTRING (1 5, 4 4, 4 1, 2 2, 3 2)`

<img src="figures/linestring-1.png" width="576" style="display: block; margin: auto;" />

Linestring cannot have self intersecting line part.
In other words, lines shouldn't pass through the same point twice (except for the endpoint).

A polygon is a sequence of points, where the first and last point have the same coordinates. 
Similarly to linestring, polygon needs to create a non-self intersecting ring.
By the definition, polygon has one exterior boundary (outer ring) and zero or more interior boundaries (inner ring).
These interior boundaries are often known as holes.

- Zero interior boundaries (holes) - `POLYGON ((1 5, 2 2, 4 1, 4 4, 1 5))`

<img src="figures/polygon-1.png" width="576" style="display: block; margin: auto;" />

- One hole - `POLYGON ((1 5, 4 4, 4 1, 2 2, 1 5), (2 4, 3 4, 3 3, 2 3, 2 4))`

<img src="figures/polygon_hole-1.png" width="576" style="display: block; margin: auto;" />

The next three geometry types are the sets of previous ones: a multipoint is a set of points, multilinestring is a set strings and multipolygon is a set of polygons:

- Multipoint - `MULTIPOINT (5 2, 1 3, 3 4, 3 2)`
- Multistring - `MULTILINESTRING ((1 5, 4 4, 4 1, 2 2, 3 2), (1 2, 2 4))`
- Multipolygon - `MULTIPOLYGON ((1 5, 4 4, 4 1, 2 2, 1 5), (0 2, 1 2, 1 3, 0 3, 0 2))`

<img src="figures/multis-1.png" width="576" style="display: block; margin: auto;" />

A geometry collection is the most heterogeneous type.
It could consists of a set of any geometry types previously mentioned, for example:

- Geometry collection - `GEOMETRYCOLLECTION (MULTIPOINT (5 2, 1 3, 3 4, 3 2), LINESTRING (1 5, 4 4, 4 1, 2 2, 3 2)))`

<img src="figures/geom_collection-1.png" width="576" style="display: block; margin: auto;" />

#### Simple feature geometry (sfg) objects {#sfg}

Simple feature geometry types are represented in R by objects of a `sfg` class. 
A `sfg` object is a geometry of a single feature - a point, linestring, polygon, multipoint, multilinestring, multipolygon or geometry collection.

Usually you don't need to create geometries on your own. 
In most cases, geometries are read from spatial files.
However, a set of function to create simple feature geometry objects (`sfg`) exists in R and could be used in special cases.
The names of these functions are simple and consistent, as they start with a `st_`  prefix and end with name of geometry types in lowercase letters:

- A point - `st_point()`
- A linestring - `st_linestring()`
- A polygon - `st_polygon()`
- A multipoint - `st_multipoint()`
- A multilinestring - `st_multilinestring()`
- A multipolygon - `st_multipolygon()`
- A geometry collection - `st_geometrycollection()`

In R, `sfg` objects are represented by three native data types:

1. A numeric vector - a single point
2. A matrix - a set of points, where each row contains a point - a multipoint or linestring
3. A list - any other set, e.g. a multilinestring or geometry collection

To create point objects, we could use the `st_point()` function:


```r
# note that we use a numeric vector for points
st_point(c(5, 2)) # XY point
#> POINT(5 2)
st_point(c(5, 2, 3)) # XYZ point
#> POINTZ(5 2 3)
st_point(c(5, 2, 1), dim = "XYM") # XYM point
#> POINTM(5 2 1)
st_point(c(5, 2, 3, 1)) # XYZM point
#> POINTZM(5 2 3 1)
```

XY, XYZ and XYZM types of points are automatically created based on the length of a numeric vector. 
Only the XYM type needs to be specified using a `dim` argument.

Multipoint and linestring objects are created based on a matrix using `st_multipoint()` and `st_linestring()` functions:


```r
# the rbind function simplify creation of matrices
## MULTIPOINT
multipoint_matrix = rbind(c(5, 2), c(1, 3), c(3, 4), c(3, 2))
st_multipoint(multipoint_matrix)
#> MULTIPOINT(5 2, 1 3, 3 4, 3 2)

## LINESTRING
linestring_matrix = rbind(c(1, 5), c(4, 4), c(4, 1), c(2, 2), c(3, 2))
st_linestring(linestring_matrix)
#> LINESTRING(1 5, 4 4, 4 1, 2 2, 3 2)
```

The rest of objects are represented by lists:


```r
## POLYGON
polygon_list = list(rbind(c(1, 5), c(2, 2), c(4, 1), c(4, 4), c(1, 5)))
st_polygon(polygon_list)
#> POLYGON((1 5, 2 2, 4 1, 4 4, 1 5))
```


```r
## POLYGON with a hole
polygon_border = rbind(c(1, 5), c(2, 2), c(4, 1), c(4, 4), c(1, 5))
polygon_hole = rbind(c(2, 4), c(3, 4), c(3, 3), c(2, 3), c(2, 4))
polygon_with_hole_list = list(polygon_border, polygon_hole)
st_polygon(polygon_with_hole_list)
#> POLYGON((1 5, 2 2, 4 1, 4 4, 1 5), (2 4, 3 4, 3 3, 2 3, 2 4))
```


```r
## MULTILINESTRING
multilinestring_list = list(rbind(c(1, 5), c(4, 4), c(4, 1), c(2, 2), c(3, 2)), 
                            rbind(c(1, 2), c(2, 4)))
st_multilinestring((multilinestring_list))
#> MULTILINESTRING((1 5, 4 4, 4 1, 2 2, 3 2), (1 2, 2 4))
```


```r
## MULTIPOLYGON
multipolygon_list = list(list(rbind(c(1, 5), c(2, 2), c(4, 1), c(4, 4), c(1, 5))),
                         list(rbind(c(0, 2), c(1, 2), c(1, 3), c(0, 3), c(0, 2))))
st_multipolygon(multipolygon_list)
#> MULTIPOLYGON(((1 5, 2 2, 4 1, 4 4, 1 5)), ((0 2, 1 2, 1 3, 0 3, 0 2)))
```


```r
## GEMETRYCOLLECTION
gemetrycollection_list = list(st_multipoint(multipoint_matrix),
                              st_linestring(linestring_matrix))
st_geometrycollection(gemetrycollection_list)
#> GEOMETRYCOLLECTION(MULTIPOINT(5 2, 1 3, 3 4, 3 2), LINESTRING(1 5, 4 4, 4 1, 2 2, 3 2))
```

<!-- table -->
<!-- figure - image/fig1.jpg -->
<!-- they are interconnected - points could create mulitpoints or lines; -->
<!-- lines could create mutlilines or polygons, etc. -->
<!-- https://r-spatial.github.io/sf/articles/sf1.html -->

#### Simple feature collections {#sfc}

One `sfg` object contains only a single simple feature geometry. 
A simple feature collection (`sfc`) is a list of `sfg` objects with information about a coordinate reference system.
The `st_sfc()` function can be used to create `sfc` objects, as illustrated in the code below, which combines two simple features of a point type into a single feature:


```r
# sfc POINT
point1 = st_point(c(5, 2))
point2 = st_point(c(1, 3))
st_sfc(point1, point2)
#> Geometry set for 2 features 
#> geometry type:  POINT
#> dimension:      XY
#> bbox:           xmin: 1 ymin: 2 xmax: 5 ymax: 3
#> epsg (SRID):    NA
#> proj4string:    NA
#> POINT(5 2)
#> POINT(1 3)
```

In most cases, an `sfc` object contains objects of identical geometry type.
Therefore, when we combine `sfg` objects of a polygon type we would get `sfc` of a polygon type, and a collection of multilinestring would result into `sfc` of a multilinestring type:


```r
# sfc POLYGON
polygon_list1 = list(rbind(c(1, 5), c(2, 2), c(4, 1), c(4, 4), c(1, 5)))
polygon1 = st_polygon(polygon_list)
polygon_list2 = list(rbind(c(0, 2), c(1, 2), c(1, 3), c(0, 3), c(0, 2)))
polygon2 = st_polygon(polygon_list2)
st_sfc(polygon1, polygon2)
#> Geometry set for 2 features 
#> geometry type:  POLYGON
#> dimension:      XY
#> bbox:           xmin: 0 ymin: 1 xmax: 4 ymax: 5
#> epsg (SRID):    NA
#> proj4string:    NA
#> POLYGON((1 5, 2 2, 4 1, 4 4, 1 5))
#> POLYGON((0 2, 1 2, 1 3, 0 3, 0 2))
```


```r
# sfc MULTILINESTRING
multilinestring_list1 = list(rbind(c(1, 5), c(4, 4), c(4, 1), c(2, 2), c(3, 2)), 
                            rbind(c(1, 2), c(2, 4)))
multilinestring1 = st_multilinestring((multilinestring_list1))
multilinestring_list2 = list(rbind(c(2, 9), c(7, 9), c(5, 6), c(4, 7), c(2, 7)), 
                            rbind(c(1, 7), c(3, 8)))
multilinestring2 = st_multilinestring((multilinestring_list2))
st_sfc(multilinestring1, multilinestring2)
#> Geometry set for 2 features 
#> geometry type:  MULTILINESTRING
#> dimension:      XY
#> bbox:           xmin: 1 ymin: 1 xmax: 7 ymax: 9
#> epsg (SRID):    NA
#> proj4string:    NA
#> MULTILINESTRING((1 5, 4 4, 4 1, 2 2, 3 2), (1 2...
#> MULTILINESTRING((2 9, 7 9, 5 6, 4 7, 2 7), (1 7...
```

It is possible to create a `sfc` object from `sfg` objects with different geometry types.
This new object would have a "geometry" geometry type:


```r
# sfc GEOMETRY
st_sfc(point1, multilinestring1)
#> Geometry set for 2 features 
#> geometry type:  GEOMETRY
#> dimension:      XY
#> bbox:           xmin: 1 ymin: 1 xmax: 5 ymax: 5
#> epsg (SRID):    NA
#> proj4string:    NA
#> POINT(5 2)
#> MULTILINESTRING((1 5, 4 4, 4 1, 2 2, 3 2), (1 2...
```

<!-- if you want to use it - st_cast() to a proper geometry type -->
<!-- or st_is to select only one geometry type -->
<!-- http://r-spatial.org/r/2017/01/12/newssf.html -->
<!-- methods(class = "sfc") -->

The simple feature collection objects could have more information about spatial data than just geometries.
It is possible to store coordinate reference systems (CRS) in them.
<!-- What's CRS -->
CRS can be represented by `epsg (SRID)` and `proj4string` attributes.
The default value of `epsg (SRID)` and `proj4string` is `NA` (*Not Available*), which is used when the CRS is unknown:


```r
st_sfc(point1, point2)
#> Geometry set for 2 features 
#> geometry type:  POINT
#> dimension:      XY
#> bbox:           xmin: 1 ymin: 2 xmax: 5 ymax: 3
#> epsg (SRID):    NA
#> proj4string:    NA
#> POINT(5 2)
#> POINT(1 3)
```

The `sfc` object could have `NA` values in both attributes or have an actual value for one or two CRS attributes.
Importantly, all geometries in the `sfc` objects must have the same CRS. 

We can add coordinate reference system as a `crs` argument of `st_sfc()`. 
This argument could accept either an integer with the `epsg` code or character with `proj4string`.

For example, we can set the WGS 84 using either its epsg code (`4326`) or its `proj4string` definition (`"+proj=longlat +datum=WGS84 +no_defs"`):


```r
# EPSG definition
st_sfc(point1, point2, crs = 4326)
#> Geometry set for 2 features 
#> geometry type:  POINT
#> dimension:      XY
#> bbox:           xmin: 1 ymin: 2 xmax: 5 ymax: 3
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#> POINT(5 2)
#> POINT(1 3)
```


```r
# PROJ4STRING definition
st_sfc(point1, point2, crs = "+proj=longlat +datum=WGS84 +no_defs")
#> Geometry set for 2 features 
#> geometry type:  POINT
#> dimension:      XY
#> bbox:           xmin: 1 ymin: 2 xmax: 5 ymax: 3
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#> POINT(5 2)
#> POINT(1 3)
```

Both of these approaches have advantages and disadvantages. 
An `epsg` code is usually shorter and therefore easier to remember. 
The code also refers to only one, well-defined coordinate reference system. 
It could be, however, considered a limitation of `epsg`, as it is not flexible.
On the hand, a `proj4string` definition is longer - it could specify many different parameters, such as projection type, datum and ellipsoid. 
This makes `proj4string` more complicated, but also allows to create many different projections and modify existing ones.
`proj4string` is also supported by the PROJ.4 software (and therefore by the `sf` package), which enables transformations between different projections.

`epsg` always points to a particular CRS.
This property makes possible for PROJ.4 to convert `epsg` into corresponding `proj4string`.
For example, we can set the UTM Zone 11N projection with `epsg` code `2955`:


```r
st_sfc(point1, point2, crs = 2955)
#> Geometry set for 2 features 
#> geometry type:  POINT
#> dimension:      XY
#> bbox:           xmin: 1 ymin: 2 xmax: 5 ymax: 3
#> epsg (SRID):    2955
#> proj4string:    +proj=utm +zone=11 +ellps=GRS80 +towgs84=0,0,0,0,0,0,0 +units=m +no_defs
#> POINT(5 2)
#> POINT(1 3)
```

As you can see above, the `proj4string` definition was automatically added.
Now we can try to set the CRS using `proj4string`:


```r
st_sfc(point1, point2, crs = "+proj=utm +zone=11 +ellps=GRS80 +towgs84=0,0,0,0,0,0,0 +units=m +no_defs")
#> Geometry set for 2 features 
#> geometry type:  POINT
#> dimension:      XY
#> bbox:           xmin: 1 ymin: 2 xmax: 5 ymax: 3
#> epsg (SRID):    NA
#> proj4string:    +proj=utm +zone=11 +ellps=GRS80 +towgs84=0,0,0,0,0,0,0 +units=m +no_defs
#> POINT(5 2)
#> POINT(1 3)
```

The above result doesn't contain `epsg`. 
This is due the fact that no general method for conversion from `proj4string` to `epsg` exists.

<!-- precision -->
<!-- plots can be made -->

#### Simple feature objects {#sf}

Most of the time, geometries are related to a set of attributes. 
These attributes could represent the name of the geometry, measured value, group to which the geometry belongs, and many more.
For example, we measured a temperature of 25°C on the Trafalgar Square in London on June 21^th^ 2017. 
This can be described not only by its coordinates and temperature value, but also by the name of the point, the date of the measurement, it's category (city or village), or if the measurement was made using an automatic station.

The simple feature class, `sf`, is a combination of an attribute table (`data.frame`) and simple feature geometry collection (`sfc`).
Simple features are created using the `st_sf()` function:


```r
# sfg objects
london_point = st_point(c(0.1, 51.5))
ruan_point = st_point(c(-9, 53))

# sfc object
our_geometry = st_sfc(london_point, ruan_point, crs = 4326)

# data.frame object
our_attributes = data.frame(name = c("London", "Ruan"),
                            temperature = c(25, 13),
                            date = c(as.Date("2017-06-21"), as.Date("2017-06-22")),
                            category = c("city", "village"),
                            automatic = c(FALSE, TRUE))

# sf object
sf_points = st_sf(our_attributes, geometry = our_geometry)
```

The above example illustrates the components of `sf` objects. 
Firstly, simple feature geometry (`sfg`) objects are defined using coordinates.
These objects are combined into a simple feature collection (`sfc`).
The `sfc` also stores the information about coordinate reference system.
`data.frame` is created, where each row corresponds to one geometry feature.
Finally, the attribute table and `sfc` object are tied together using the `st_sf()` function.


```r
sf_points
#> Simple feature collection with 2 features and 5 fields
#> geometry type:  POINT
#> dimension:      XY
#> bbox:           xmin: -9 ymin: 51.5 xmax: 0.1 ymax: 53
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#>     name temperature       date category automatic        geometry
#> 1 London          25 2017-06-21     city     FALSE POINT(0.1 51.5)
#> 2   Ruan          13 2017-06-22  village      TRUE    POINT(-9 53)
```

The resulting object has two classes - `sf` and `data.frame`:


```r
class(sf_points)
#> [1] "sf"         "data.frame"
```

The result shows that `sf` objects actually have two classes, `sf` and `data.frame`.
Simple features are simply data frames (square tables), but with spatial attributes (usually stored in a special `geom` list-column in the data frame).
This duality is central to the concept of simple features:
most of the time a `sf` can be treated as and behaves like a `data.frame`.
Simple features are, in essence, data frames with a spatial extension.

<!-- methods -->
<!-- methods(class = "sf") -->
<!-- plots -->
<!-- https://r-spatial.github.io/sf/articles/sf1.html#how-attributes-relate-to-geometries -->

## Raster data

<!-- what is raster ?? -->

### An introduction to raster

Raster objects in R are supported by the **raster** package. 
It provides an extensive set of functions to create, read, processed and write of raster datasets.
Beside the general raster data manipulation, **raster** provides many low level functions that can be used to create and develop new concepts. **raster** also supports work on large raster datasets that are stored on a hard drive, but are too large to fit into memory. 
Instead of recreating the whole file in RAM, this package extracts information about the structure of the dataset, such as a number of rows and columns, spatial extent and the name of the file.
When manipulating this dataset, values are read and processed in a small chunk and written either to a specified file on a disk or temporary file.

The **raster** package provides three main classes of objects - `RasterLayer`, `RasterBrick` and `RasterStack`. 
We would refer to all of them as `Raster*`.

<!-- we should replace it with our own dataset -->
<!-- example dataset from spData -->

```r
library(raster)
#> Loading required package: sp
raster_filepath = system.file("external/test.grd", package="raster")
new_raster = raster(raster_filepath)
```

The `Raster*` objects store three types of information: spatial, non-spatial and metadata.
All of them could be shown by just typing the name of the object: 


```r
new_raster
#> class       : RasterLayer 
#> dimensions  : 115, 80, 9200  (nrow, ncol, ncell)
#> resolution  : 40, 40  (x, y)
#> extent      : 178400, 181600, 329400, 334000  (xmin, xmax, ymin, ymax)
#> coord. ref. : +init=epsg:28992 +towgs84=565.237,50.0087,465.658,-0.406857,0.350733,-1.87035,4.0812 +proj=sterea +lat_0=52.15616055555555 +lon_0=5.38763888888889 +k=0.9999079 +x_0=155000 +y_0=463000 +ellps=bessel +units=m +no_defs 
#> data source : /home/travis/R/Library/raster/external/test.grd 
#> names       : test 
#> values      : 128, 1806  (min, max)
```

Raster's spatial properties are expressed as the dimensions (number of rows, number of columns, number of cells and number of layers for multilayer objects), extent and coordinate reference system of the data.


```r
# the dimensions (number of rows, number of columns, number of cells)
dim(new_raster)
#> [1] 115  80   1
```


```r
# the spatial extent
extent(new_raster)
#> class       : Extent 
#> xmin        : 178400 
#> xmax        : 181600 
#> ymin        : 329400 
#> ymax        : 334000
```


```r
# the coordinate reference system
crs(new_raster)
#> CRS arguments:
#>  +init=epsg:28992
#> +towgs84=565.237,50.0087,465.658,-0.406857,0.350733,-1.87035,4.0812
#> +proj=sterea +lat_0=52.15616055555555 +lon_0=5.38763888888889
#> +k=0.9999079 +x_0=155000 +y_0=463000 +ellps=bessel +units=m
#> +no_defs
```

Unlike the **sf** package, **raster** only use the `proj4string` representation of the coordinate reference system.

Values of the cells are the only non-spatial information in the `Raster*` object.
They could be summarized and plotted using the base R functions, such as `summary()` and `hist()`.


```r
# the numerical summary of the data
summary(new_raster)
#>         test
#> Min.     128
#> 1st Qu.  293
#> Median   371
#> 3rd Qu.  500
#> Max.    1806
#> NA's    6097
```


```r
# the histogram of the values
hist(new_raster)
```

<img src="figures/unnamed-chunk-39-1.png" width="576" style="display: block; margin: auto;" />

`getValues()` can be used to extract the values as a numerical vector.


```r
new_raster_values = getValues(new_raster)
head(new_raster_values)
#> [1] NA NA NA NA NA NA
```

The new vector, `new_raster_values`, could be an input for many statistical operations.

Metadata in `Raster*` include, for example a class of the object, path to the source of the data and names of the layers.


```r
# the object class
class(new_raster)
#> [1] "RasterLayer"
#> attr(,"package")
#> [1] "raster"
```


```r
# the file path to the data source
filename(new_raster)
#> [1] "/home/travis/R/Library/raster/external/test.grd"
```


```r
# the names of layer in the `Raster*` object
names(new_raster)
#> [1] "test"
```

Sometimes it could be important to know if the values of the files are in RAM or on disk using the `inMemory()` function:


```r
inMemory(new_raster)
#> [1] FALSE
```

The full list of the **raster** function could be found using `help(package = "raster", topic = "raster-package")`.

### Basic map making

Just as in the **sf** package, basic raster maps can be created with the `plot()` function.


```r
plot(new_raster)
```

<img src="figures/unnamed-chunk-45-1.png" width="576" style="display: block; margin: auto;" />

<!-- more advanced options - rasterVis, tmap, mapview, leaflet -->
<!-- combining raster with vector for a plot -->
<!-- TODO: cross reference advanced mapping chapter -->

### Raster classes

`RasterLayer` represents the simplest raster object, consisting of only one layer and store information about a number of rows and columns, spatial object extent and coordinate reference system used. 
<!-- CRS as proj4 -->
This raster class could store raster values in a RAM memory or only point to a file on hard drive that holds the values.

Object of the `RasterLayer` class is created by the `raster()` function:
<!-- explanation that this function can do many more things -->
<!-- how to add crs -->
<!-- how to add values -->


```r
library(raster)
r = raster() # creation of an empty RasterLayer object
r
#> class       : RasterLayer 
#> dimensions  : 180, 360, 64800  (nrow, ncol, ncell)
#> resolution  : 1, 1  (x, y)
#> extent      : -180, 180, -90, 90  (xmin, xmax, ymin, ymax)
#> coord. ref. : +proj=longlat +datum=WGS84 +ellps=WGS84 +towgs84=0,0,0
```


```r
# creation of the RasterLayer object with a given number of columns and rows, and extent
r1 = raster(ncol = 101, nrow = 77, xmn = 0, xmx = 101, ymn = 0, ymx = 77)
r1
#> class       : RasterLayer 
#> dimensions  : 77, 101, 7777  (nrow, ncol, ncell)
#> resolution  : 1, 1  (x, y)
#> extent      : 0, 101, 0, 77  (xmin, xmax, ymin, ymax)
#> coord. ref. : +proj=longlat +datum=WGS84 +ellps=WGS84 +towgs84=0,0,0
values(r1) = sample(1:ncell(r1)) # adding random values to the new raster object
```

Two additional classes, `RasterBrick` and `RasterStack` are used when dealing with multiple layers.
These two classes differ in terms of a number of supported files, type of representation and processing speed.

A `RasterBrick` contain multiple layers of raster data, which refer to only a single, mutlilayer file.
<!-- ... -->
<!-- (such as mulitspectral satellite images). -->

`RasterBrick` objects are created using the `brick()` function. 
This function usually takes a filename to a multilayer raster file.
However, it is also possible to provide a `Raster*` object, `array`, and a few more.
All of possible formats could be found on the help file - `?brick`.
<!-- should we use this example or have our own multilayer dataset? -->

```r
multilayer_raster_filepath = system.file("external/rlogo.grd", package="raster")
r_brick = brick(multilayer_raster_filepath)
r_brick
#> class       : RasterBrick 
#> dimensions  : 77, 101, 7777, 3  (nrow, ncol, ncell, nlayers)
#> resolution  : 1, 1  (x, y)
#> extent      : 0, 101, 0, 77  (xmin, xmax, ymin, ymax)
#> coord. ref. : +proj=merc +datum=WGS84 +ellps=WGS84 +towgs84=0,0,0 
#> data source : /home/travis/R/Library/raster/external/rlogo.grd 
#> names       : red, green, blue 
#> min values  :   0,     0,    0 
#> max values  : 255,   255,  255
```

The `nlayers` function helps to get the number of layers in a `Raster*` object:


```r
nlayers(r_brick)
#> [1] 3
```

A `RasterStack` is a list of `RasterLayer` objects with the same extent and resolution. 
It can be created based on a group of object from many sources - different files, another bands in a multi-band file and `RasterLayer` objects created in R. 


```r
raster_on_disk = raster(multilayer_raster_filepath, layer = 1)
raster_in_memory = raster(xmn = 0, xmx = 101, ymn = 0, ymx = 77, res = 1)
values(raster_in_memory) = sample(1:ncell(raster_in_memory))
crs(raster_in_memory) = crs(raster_on_disk)
```


```r
r_stack <- stack(raster_in_memory, raster_on_disk)
r_stack
#> class       : RasterStack 
#> dimensions  : 77, 101, 7777, 2  (nrow, ncol, ncell, nlayers)
#> resolution  : 1, 1  (x, y)
#> extent      : 0, 101, 0, 77  (xmin, xmax, ymin, ymax)
#> coord. ref. : +proj=merc +datum=WGS84 +ellps=WGS84 +towgs84=0,0,0 
#> names       : layer,  red 
#> min values  :     1,    0 
#> max values  :  7777,  255
```

Due to its properties, `RasterBrick` objects should be processed in a shorter time than `RasterStack`.
Additionally, operations on `RasterBrick` and `RasterStack` objects will typically return `RasterBrick`.
On the other hand, `RasterStack` give more flexibility, as a single object could be related to data stored in a memory and on disk in the same time.
`RasterBrick` objects could be stored only in a memory or on disk.

## Coordinate Reference Systems

This section is work in progress.

Despite the differences between vector and raster spatial data types, they are united by shared concepts intrinsic to spatial data. Perhaps the most important of these is Coordinate Reference System (CRS), which defines how the spatial elements of the data relate to the surface of the Earth (or other body).

In **sf** the CRS of an object can be retrieved and set using `st_crs()` and `st_set_crs()` respectively:


```r
old_crs = st_crs(sf_points) # get CRS
old_crs # print CRS
#> $epsg
#> [1] 4326
#> 
#> $proj4string
#> [1] "+proj=longlat +datum=WGS84 +no_defs"
#> 
#> attr(,"class")
#> [1] "crs"
sf_points = st_set_crs(sf_points, 27700) # set CRS
#> Warning: st_crs<- : replacing crs does not reproject data; use st_transform
#> for that
```

Note the warning emitted after the CRS for `sf_points` was set to `27700`.
This is a good thing: we have imposed a spatial reference onto data without knowing what that means.
To discover what the 'magic number' `27700` means, we can retrieve the CRS again (see Chapter \@ref(coord) for more on CRSs):


```r
st_crs(sf_points)
#> $epsg
#> [1] 27700
#> 
#> $proj4string
#> [1] "+proj=tmerc +lat_0=49 +lon_0=-2 +k=0.9996012717 +x_0=400000 +y_0=-100000 +ellps=airy +towgs84=446.448,-125.157,542.06,0.15,0.247,0.842,-20.489 +units=m +no_defs"
#> 
#> attr(,"class")
#> [1] "crs"
```

## Units

<!-- https://cran.r-project.org/web/packages/units/vignettes/measurement_units_in_R.html -->
The final thing to say about `sf` objects in this chapter is that they have units.
This is advantageous because it prevents confusion caused by the fact that different CRSs use different units (most use meters, some use feet).
Furthermore, it also provides information on dimensionality, as illustrated by calculating the area of Nigeria:


```r
nigeria = world[world$name_long == "Nigeria", ]
```


```r
st_area(nigeria)
#> 9.05e+11 m^2
```

The result, as expected, is in units of square meters (m^2^), representing 2 dimensional space, and that Nigeria is a large country!
To translate the huge number into a more digestible size, it is tempting to divide the results by a million (the number of square meters in a square kilometer):


```r
st_area(nigeria) / 1e6
#> 905072 m^2
```

However, the result is incorrectly given in the same units.
The solution is to set the units with the **units** package:


```r
units::set_units(st_area(nigeria), km^2)
#> 905072 km^2
```

<!-- Something about when units are not set: -->
<!-- ```{r} -->
<!-- st_distance(sf_point1, sf_point2) -->
<!-- ``` -->

<!-- ## Precision -->

## Exercises

1. What does the summary of the `geometry` column tell us about the `world` dataset, in terms of:

- The geometry type?
- How many countries there are?
- The coordinate reference system (CRS)?

2. Using **sf**'s `plot()` command, create a map of Nigeria in context, building on the code that creates and plots Asia above (see Figure \@ref(fig:nigeria) for an example of what this could look like). 

- Hint: this used the `lwd`, `main` and `col` arguments of `plot()`. 
- Bonus: make the country boundaries a dotted grey line.
- Hint: `border` is an additional argument of `plot()` for **sf** objects.

3. Exercise 3 <!--missing title-->

- What does the `lwd` argument do in the `plot()` code that generates Figure \@ref(fig:africa). 
- Perform the same operations and map making for another continent of your choice.
- Bonus: Download some global geographic data and add attribute variables assigning them to the continents of the world.

<!--chapter:end:02-spatial-data.Rmd-->


# Attribute data operations {#attr}

## Prerequisites {-}

- This chapter requires the packages **tidyverse** and **sf**:


```r
library(sf)
library(tidyverse)
```

- We will also make use of the `world` and `worldbank_df` data sets. Note that loading the **spData** package automatically attaches these data sets to your global environment:


```r
library(spData)
```

## Introduction

Attribute data is non-spatial information associated with geographic (geometry) data.
A bus station, for example, could be represented by a field containing its name (attribute data), associated with its latitude and longitude position (geometry data).
Simple features, described in the previous chapter, store attribute data in a data frame, with each column corresponding to a variable (such as 'name') and each row to one observation (such as an individual bus station).
In addition, a special column, usually named `geom` or `geometry`, stores the geometry data of **sf** objects.
For a bus station, that would likely be a single point representing its coordinate of the bus station.
By contrast, a line or a polygon consist of multiple points.
Still, these points only correspond to one row in the attribute table.
This works since **sf** stores the geometry in the form of a list. 
The list elements correspond to the number of observations in the attribute table.
But each list element can contain more than one coordinate if required or even another list as it is the case for polygons with holes (see previous sections).
This structure enables multiple columns to represent a range of attributes for thousands of features (one row per feature).

This chapter focuses on non-geographical operations such as subsetting, aggregating or joining attribute data. 
Note that the corresponding functions also have a geographical equivalent.
Sometimes you can even use the same functions for attribute and spatial operations.
This is, for example, the case for subsetting as base R's `[` and tidyverse's `filter()` let you also subset spatial data based on the spatial extent of another spatial object (see Chapter \@ref(spatial-data-operations)).
That is, the skills you learn here are cross-transferable which is also why this chapter lays the foundation for the next chapter (Chapter \@ref(spatial-data-operations)) which extends the here presented methods to the spatial world.

As outlined in Chapter \@ref(spatial-class), **sf** provided support for simple features in R and made them work with generic R functions such as `plot()` and `summary()` (as can be seen by executing `methods("summary")` and/or `methods("plot")`).

The reliable `data.frame` (and modifications to it such as the `tibble` class used in the tidyverse) is the basis for data analysis in R.
Extending this system to work with spatial data has many advantages. 
The most important one is that the accumulated know-how in the R community for handling data frames can be transferred to geographic attribute data.

Before proceeding to perform various attribute operations on a dataset, let's explore its structure.
To find out more about the structure of our use case dataset `world`, we use base R functions for working with tabular data such as `nrow()` and `ncol()`:


```r
dim(world) # it is a 2 dimensional object, with rows and columns
#> [1] 177  11
nrow(world) # how many rows?
#> [1] 177
ncol(world) # how many columns?
#> [1] 11
```

Our dataset contains ten non-geographical columns (and one geometry list-column) with almost 200 rows representing the world's countries.

Extracting the attribute data of an `sf` object is the same as removing its geometry:


```r
world_df = st_set_geometry(world, NULL)
class(world_df)
#> [1] "data.frame"
```

This can be useful if the geometry column causes problems, e.g., by occupying large amounts of RAM, or to focus the attention on the attribute data.
For most cases, however, there is no harm in keeping the geometry column because non-spatial data operations on `sf` objects act only on the attribute data.
For this reason, being good at working with attribute data of spatial objects is the same as being proficient at handling data frames in R.
For many applications, **dplyr** offers the most effective and most intuitive approach of working with data frames, as we will see in the next
section.^[
Unlike objects of class `Spatial` of the **sp** package, `sf` objects are also compatible with the **tidyverse** packages **dplyr** and **ggplot2**.
The former provides fast and powerful functions for data manipulation (see [Section 6.7](https://csgillespie.github.io/efficientR/data-carpentry.html#data-processing-with-data.table) of @gillespie_efficient_2016), and the latter provides powerful plotting capabilities.
]
This chapter focuses on **dplyr** because of its intuitive function names and ability to perform multiple chained operations using the pipe operator.

## Attribute subsetting

Because simple feature objects are also data frames (run `class(world)`to verify), you can use a wide range of functions (from base R and other packages) for subsetting them.
Base R subsetting functions include `[`, `subset()` and  `$`.
**dplyr** subsetting functions include `select()`, `filter()`, and `pull()`.
Both sets of functions preserve the spatial components of the data.

The `[` operator can subset both rows and columns. 
You use indices to specify the elements you wish to extract from an object, e.g., `object[i, j]` with `i` and `j` representing rows and columns.
<!-- you can also use `[`(world, 1:6, 1) -->
The indices can be either numeric, indicating position, or character strings, indicating row or column names.
Leaving `i` or `j` empty, simply returns all rows or columns.
For instance, `object[1:5, ]` returns the first five rows and all columns.
Below, we demonstrate how to use base R subsetting (results not shown - try running this on your own computer to check the output is as expected):


```r
world[1:6, ] # subset rows by position
```


```r
world[, 1:3] # subset columns by position
```


```r
world[, c("name_long", "lifeExp")] # subset columns by name
```

The `[` subsetting operator also accepts `logical` vectors consisting of `TRUE` and `FALSE` elements.
The following code chunk, for example, creates a new object, `small_countries`, which only contains nations whose surface area is smaller than 100,000 km^2^:


```r
sel_area = world$area_km2 < 10000
summary(sel_area)
#>    Mode   FALSE    TRUE 
#> logical     170       7
small_countries = world[sel_area, ]
```

Note that we created the intermediary `sel_object`, a logical vector, for illustration purposes, and to show that only seven countries match our query.
A more concise command, that omits the intermediary object, generates the same result:


```r
small_countries = world[world$area_km2 < 10000, ]
```

Another the base R function `subset()` provides yet another way to achieve the same result:


```r
small_countries = subset(world, area_km2 < 10000)
```

You can use the `$` operator to select a specific variable by its name. The result is a vector:


```r
world$name_long
```

<!-- , after the package has been loaded: [or - it is a part of tidyverse] -->
Base R functions are essential, and we recommend that you have a working knowledge of them.
However, **dplyr** often makes working with data frames easier.
Moreover, **dplyr** is usually much faster than base R since it makes use of C++ in the background. 
This comes in especially handy when working with large data sets.
As a special bonus, **dplyr** is compatible with `sf` objects.
The main **dplyr** subsetting functions are `select()`, `slice()`, `filter()` and `pull()`.

The `select()` function selects columns by name or position.
For example, you could select only two columns, `name_long` and `pop`, with the following command:


```r
world1 = select(world, name_long, pop)
head(world1, n = 2)
#> Simple feature collection with 2 features and 2 fields
#> geometry type:  MULTIPOLYGON
#> dimension:      XY
#> bbox:           xmin: 11.6401 ymin: -17.93064 xmax: 75.15803 ymax: 38.48628
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#>     name_long      pop                           geom
#> 1 Afghanistan 31627506 MULTIPOLYGON(((61.210817091...
#> 2      Angola 24227524 MULTIPOLYGON(((16.326528354...
```

`select()` also allows subsetting of a range of columns with the help of the `:` operator: 


```r
# all columns between name_long and pop (inclusive)
world2 = select(world, name_long:pop)
head(world2, n = 2)
```

Omit specific columns with the `-` operator:


```r
# all columns except subregion and area_km2 (inclusive)
world3 = select(world, -subregion, -area_km2)
head(world3, n = 2)
```

Conveniently, `select()` lets you subset and rename columns at the same time, for example:


```r
world4 = select(world, name_long, population = pop)
head(world4, n = 2)
#> Simple feature collection with 2 features and 2 fields
#> geometry type:  MULTIPOLYGON
#> dimension:      XY
#> bbox:           xmin: 11.6401 ymin: -17.93064 xmax: 75.15803 ymax: 38.48628
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#>     name_long population                           geom
#> 1 Afghanistan   31627506 MULTIPOLYGON(((61.210817091...
#> 2      Angola   24227524 MULTIPOLYGON(((16.326528354...
```

This is more concise than the base R equivalent:


```r
world5 = world[, c("name_long", "pop")] # subset columns by name
names(world5)[2] = "population" # rename column manually
```

The `select()` function works with a number of special functions that help with more advanced subsetting operations such as `contains()`, `starts_with()` and `num_range()`. 
Find out more about the details on the function's help page - `?select`.

`slice()` is the row-equivalent of `select()`.
The following code chunk, for example, selects the 3^rd^ to 5^th^ rows:


```r
slice(world, 3:5)
```

`filter()` is **dplyr**'s equivalent of base R's `subset()` function.
It keeps only rows matching given criteria, e.g., only countries with a very high average of life expectancy:


```r
# only countries with a life expectation larger than 82 years
world6 = filter(world, lifeExp > 82)
```

The standard set of comparison operators can be used in the `filter()` function: 


Symbol   Name                  
-------  ----------------------
`==`     Equal to              
`!=`     Not equal to          
`>`      Greater than          
`>=`     Greater than or equal 
`<`      Less than             
`<=`     Less than or equal    
`&`      And                   
|        Or                    
`!`      Not                   

<!-- describe these: ==, !=, >, >=, <, <=, &, | -->
<!-- add warning about = vs == -->
<!-- add info about combination of &, |, ! -->

Finally, we would like to introduce the special *pipe* operator (` %>% `) of the **magrittr** package.
The *pipe* operator feeds ('pipes forward') the output of one function into the first argument of the next function.
Combining many functions together with pipes is called *chaining* or *piping*.
For example, let us first take the `world` dataset, then let us select the two columns named `name_long` and `continent`, and then we just would like to return the first five rows.


```r
world %>%
  select(name_long, continent) %>%
  slice(1:5)
#> Simple feature collection with 5 features and 2 fields
#> geometry type:  MULTIPOLYGON
#> dimension:      XY
#> bbox:           xmin: -180 ymin: -90 xmax: 180 ymax: 83.64513
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#> # A tibble: 5 x 3
#>              name_long continent              geom
#>                  <chr>     <chr>  <simple_feature>
#> 1          Afghanistan      Asia <MULTIPOLYGON...>
#> 2               Angola    Africa <MULTIPOLYGON...>
#> 3              Albania    Europe <MULTIPOLYGON...>
#> 4 United Arab Emirates      Asia <MULTIPOLYGON...>
#> # ... with 1 more rows
```

The pipe operator supports an intuitive data analysis workflow.
It allows operations to be written in a clear order, line-by-line and from left to right (as with most languages), avoiding 'nesting', whereby one function is burried inside another (without pipes the code in the previous chunk would be written as `slice(select(world, name_long, continent), 1:5)` which is harder for most people to read, write and understand).
Another advantage over the nesting approach is that you can easily comment out certain parts of a pipe.
**dplyr** works especially well with the pipe operator because its fundamental functions (or 'verbs', like `select()`) expect a data frame object as input and also return one.^[If you want **dplyr** to return a vector, use `pull`.]

## Attribute data aggregation 

<!-- https://github.com/ropenscilabs/skimr ?? -->

<!-- As demonstrated in chapter \@ref(spatial-class), `summary()` provides a quick summary of the spatial and non-spatial components of spatial objects.
Enter the following command for an overview of the `world` object and all its variables (result not shown):


```r
summary(world)
```

This function is useful when using R interactively, but lacks flexibility and should not be used to create new objects.-->
The **dplyr** equivalent is `summarize()`, which returns summary statistics of groups and variables defined by the user.
The following code, for example, calculates the total population and number of all countries in the world:


```r
# customized data summary
world_summary = world %>% 
  summarize(pop = sum(pop, na.rm = TRUE), country_n = n())
world_summary
#> Simple feature collection with 1 feature and 2 fields
#> geometry type:  MULTIPOLYGON
#> dimension:      XY
#> bbox:           xmin: -180 ymin: -90 xmax: 180 ymax: 83.64513
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#>        pop country_n                           geom
#> 1 7.21e+09       177 MULTIPOLYGON(((-159.2081835...
```

The new object, `world_summary`, is an aggregation of all 177 world's countries.
It consists of one row and two columns. 
The `pop =` and `country_n =` created the names of the two columns, while the `sum()`- and `n()`-function actually did the aggregation.
The first function added up all inhabitants, while the latter simply counted the number of rows. 
 
You can use a wide range of functions within `summarize()` for aggregation and summary purposes.
Type `?summarize` for a list with useful functions and more information.

`summarize()` becomes even more powerful when combined with `group_by()`, which allows simultaneous aggregate/summary operations *per group*, analogous to the base R function `aggregate()`.
The following code chunk calculates the total population and number of countries *per continent* (see Chapter 5 of [R for Data Science](http://r4ds.had.co.nz/transform.html#grouped-summaries-with-summarize) for a more detailed overview of `summarize()`):


```r
# data summary by groups
world_continents = world %>% 
  group_by(continent) %>% 
  summarize(pop = sum(pop, na.rm = TRUE), country_n = n())
world_continents
#> Simple feature collection with 8 features and 3 fields
#> geometry type:  GEOMETRY
#> dimension:      XY
#> bbox:           xmin: -180 ymin: -90 xmax: 180 ymax: 83.64513
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#> # A tibble: 8 x 4
#>    continent      pop country_n              geom
#>        <chr>    <dbl>     <int>  <simple_feature>
#> 1     Africa 1.15e+09        51 <MULTIPOLYGON...>
#> 2 Antarctica 0.00e+00         1 <MULTIPOLYGON...>
#> 3       Asia 4.31e+09        47 <MULTIPOLYGON...>
#> 4     Europe 7.39e+08        39 <MULTIPOLYGON...>
#> # ... with 4 more rows
```

`sf` objects are well-integrated with the **tidyverse**, as illustrated by the fact that the aggregated objects preserve the geometry of the original `world` object.
What is more, under the hood `sf` is already doing a spatial aggregation of polygon data which is known as 'dissolving polygons' in the GIS world - an operation we will explain in more detail in the the next chapter.
This means that summaries of the world's continents can be plotted spatially, as illustrated below, which generates a plot of population by continent (note that borders between countries have largely been removed):


```r
plot(world_continents["pop"])
```

<div class="figure" style="text-align: center">
<img src="figures/continent-pop-1.png" alt="Geographic representation of attribute aggregation by continent: total population by continent generated by `summarize()`." width="576" />
<p class="caption">(\#fig:continent-pop)Geographic representation of attribute aggregation by continent: total population by continent generated by `summarize()`.</p>
</div>

Using the base R function `aggregate()` you can obtain the same result with a slightly different syntax: you have to indicate the grouping variable as a `list`-object:


```r
ag_var = list(world$continent)
world_continents2 = aggregate(world["pop"], by = ag_var, FUN = sum, na.rm = TRUE)
```

<!-- Todo (optional): add exercise exploring similarities/differences with `world_continents`? -->

<!-- should it stay or should it go (?) aka should we present the arrange function?: -->
<!-- Jannes: I would suggest to leave the arrange function as an exercise to the reader. -->

<!-- ```{r} -->
<!-- # sort variables -->
<!-- ## by name -->
<!-- world_continents %>%  -->
<!--   arrange(continent) -->
<!-- ## by population (in descending order) -->
<!-- world_continents %>%  -->
<!--   arrange(-pop) -->
<!-- ``` -->

## Attribute data joining 

<!-- https://github.com/dgrtwo/fuzzyjoin -->
<!-- http://r4ds.had.co.nz/relational-data.html -->
<!-- non-unique keys -->

Combining data from different sources is one of the most common tasks in data preparation. 
Joins are methods to combine pair of tables based on a shared key variable.
The **dplyr** package has a set of verbs to easily join `data.frames` - `left_join()`, `right_join()`,  `inner_join()`, `full_join`, `semi_join()` and `anti_join()`.
The function names follow SQL naming conventions, and @grolemund_r_2016 explain these functions thoroughly in the Relational data chapter in the book R for Data Science .

Working with spatial data, however, usually involves a connection between spatial data (`sf` objects) and tables (`data.frame` objects).
Fortunately, the **sf** package has all of the **dplyr** join functions adapted to work with `sf` objects.
The only important difference between combining two `data.frames` and combining `sf` and `data.frame` objects is the special `sf` column storing the geometry information.
Therefore, the result of data joins can be either an `sf` or `data.frame` object.

The easiest way to understand the concept of joins is to show how they work with a smaller dataset. 
We will use an `sf` object `north_america` with country codes (`iso_a2`), names and geometries, as well as a `data.frame` object `wb_north_america` containing information about urban population and unemployment for three countries.
It is important to add that the first object contains data about Canada, Greenland and the United States and the second one about Canada, Mexico and the United States:


```r
north_america = world %>%
  filter(subregion == "Northern America") %>%
  select(iso_a2, name_long)
north_america
#> Simple feature collection with 3 features and 2 fields
#> geometry type:  MULTIPOLYGON
#> dimension:      XY
#> bbox:           xmin: -171.7911 ymin: 18.91619 xmax: -12.20855 ymax: 83.64513
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#>   iso_a2     name_long                           geom
#> 1     CA        Canada MULTIPOLYGON(((-63.6645 46....
#> 2     GL     Greenland MULTIPOLYGON(((-46.76379 82...
#> 3     US United States MULTIPOLYGON(((-155.54211 1...
```


```r
plot(north_america[0])
```

<img src="figures/unnamed-chunk-27-1.png" width="576" style="display: block; margin: auto;" />


```r
wb_north_america = worldbank_df %>% 
  filter(name %in% c("Canada", "Mexico", "United States")) %>%
  select(name, iso_a2, urban_pop, unemploy = unemployment)

wb_north_america
#>            name iso_a2 urban_pop unemploy
#> 1        Canada     CA  29022137     6.91
#> 2        Mexico     MX  99018446     5.25
#> 3 United States     US 259740511     6.17
```

In this book, we focus on spatial data. 
Most of the following join examples will have a `sf` object as the first argument and a `data.frame` object as the second argument which results in a new `sf` object.
However, the reverse order is also possible and will give you back a `data.frame` object.
This is mostly beyond the scope of this book, but we encourage you to try it.

### Left joins

The left join is the most often used type of joins.
The `left_join()` returns all observations from the left object (`north_america`) and the matched observations from the right object (`wb_north_america`). 
In cases, like `Greenland`, absent in the right object, `NA` values will show up.

To join two objects we need to specify a key.
This is a variable (or a set of variables) that uniquely identifies each observation (row). 
The `by` argument of **dplyr**'s join functions lets you identify the key variable. 
In simple cases, a single, unique variable exist in both objects like the `iso_a2` column in our example:


```r
left_join1 = north_america %>% 
  left_join(wb_north_america, by = "iso_a2")
left_join1
#> Simple feature collection with 3 features and 5 fields
#> geometry type:  MULTIPOLYGON
#> dimension:      XY
#> bbox:           xmin: -171.7911 ymin: 18.91619 xmax: -12.20855 ymax: 83.64513
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#>   iso_a2     name_long          name urban_pop unemploy
#> 1     CA        Canada        Canada  29022137     6.91
#> 2     GL     Greenland          <NA>        NA       NA
#> 3     US United States United States 259740511     6.17
#>                             geom
#> 1 MULTIPOLYGON(((-63.6645 46....
#> 2 MULTIPOLYGON(((-46.76379 82...
#> 3 MULTIPOLYGON(((-155.54211 1...
```

It is also possible to join objects by different variables.
Both of the datasets have variables with names of countries, but they are named differently.
The `north_america` has a `name_long` column and the `wb_north_america` has a `name` column.
In these cases, we can use a named vector to specify the connection, e.g. `c("name_long" = "name")`:


```r
left_join2 = north_america %>% 
  left_join(wb_north_america, by = c("name_long" = "name"))
left_join2
#> Simple feature collection with 3 features and 5 fields
#> geometry type:  MULTIPOLYGON
#> dimension:      XY
#> bbox:           xmin: -171.7911 ymin: 18.91619 xmax: -12.20855 ymax: 83.64513
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#>   iso_a2.x     name_long iso_a2.y urban_pop unemploy
#> 1       CA        Canada       CA  29022137     6.91
#> 2       GL     Greenland     <NA>        NA       NA
#> 3       US United States       US 259740511     6.17
#>                             geom
#> 1 MULTIPOLYGON(((-63.6645 46....
#> 2 MULTIPOLYGON(((-46.76379 82...
#> 3 MULTIPOLYGON(((-155.54211 1...
```

The new object `left_join2`, however, contains two duplicated variables - `iso_a2.x` and `iso_a2.y` because both of the input tables possessed a variable named `iso_a2`.
To solve this problem we should specify all the keys:


```r
left_join3 = north_america %>% 
  left_join(wb_north_america, by = c("iso_a2", "name_long" = "name"))
left_join3
#> Simple feature collection with 3 features and 4 fields
#> geometry type:  MULTIPOLYGON
#> dimension:      XY
#> bbox:           xmin: -171.7911 ymin: 18.91619 xmax: -12.20855 ymax: 83.64513
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#>   iso_a2     name_long urban_pop unemploy                           geom
#> 1     CA        Canada  29022137     6.91 MULTIPOLYGON(((-63.6645 46....
#> 2     GL     Greenland        NA       NA MULTIPOLYGON(((-46.76379 82...
#> 3     US United States 259740511     6.17 MULTIPOLYGON(((-155.54211 1...
```

It is also possible to use our objects in the reverse order, where a `data.frame` object is the first argument and a `sf` object is the second argument.
This would keep the geometry column but drop the `sf` class, and result in a `data.frame` object.


```r
# keeps the geom column, but drops the sf class
left_join4 = wb_north_america %>%
  left_join(north_america, by = c("iso_a2"))
left_join4
#>            name iso_a2 urban_pop unemploy     name_long
#> 1        Canada     CA  29022137     6.91        Canada
#> 2        Mexico     MX  99018446     5.25          <NA>
#> 3 United States     US 259740511     6.17 United States
#>                             geom
#> 1 MULTIPOLYGON(((-63.6645 46....
#> 2                           NULL
#> 3 MULTIPOLYGON(((-155.54211 1...
class(left_join4)
#> [1] "data.frame"
```

`left_join4` has only one class - `data.frame`, however it is possible to add spatial `sf` class using the `st_as_sf()` function: 


```r
left_join4_sf = st_as_sf(left_join4)
left_join4_sf
#> Simple feature collection with 3 features and 5 fields (with 1 geometry empty)
#> geometry type:  MULTIPOLYGON
#> dimension:      XY
#> bbox:           xmin: -171.7911 ymin: 18.91619 xmax: -12.20855 ymax: 83.64513
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#>            name iso_a2 urban_pop unemploy     name_long
#> 1        Canada     CA  29022137     6.91        Canada
#> 2        Mexico     MX  99018446     5.25          <NA>
#> 3 United States     US 259740511     6.17 United States
#>                             geom
#> 1 MULTIPOLYGON(((-63.6645 46....
#> 2                 MULTIPOLYGON()
#> 3 MULTIPOLYGON(((-155.54211 1...
class(left_join4_sf)
#> [1] "sf"         "data.frame"
```

On the other hand, it is also possible to remove the geometry column of `left_join4` using base R functions or `dplyr`.
Here, this is this simple because the geometry column is just another `data.frame` column and no longer the sticky geometry column of an `sf` object (see also Chapter \@ref(spatial-class)):


```r
# base R
left_join4_df = subset(left_join4, select = -geom)
# or dplyr
left_join4_df = left_join4 %>% select(-geom)
left_join4_df
#>            name iso_a2 urban_pop unemploy     name_long
#> 1        Canada     CA  29022137     6.91        Canada
#> 2        Mexico     MX  99018446     5.25          <NA>
#> 3 United States     US 259740511     6.17 United States
class(left_join4_df)
#> [1] "data.frame"
```

### Right joins

`right_join()` keeps all observations from the second object (`wb_north_america` in this case) but preserves the `sf` class from the left object (`north_america`).


```r
right_join1 = north_america %>% 
  right_join(wb_north_america, by = c("iso_a2", "name_long" = "name"))
right_join1
#> Simple feature collection with 3 features and 4 fields (with 1 geometry empty)
#> geometry type:  MULTIPOLYGON
#> dimension:      XY
#> bbox:           xmin: -171.7911 ymin: 18.91619 xmax: -52.6481 ymax: 83.23324
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#>   iso_a2     name_long urban_pop unemploy                           geom
#> 1     CA        Canada  29022137     6.91 MULTIPOLYGON(((-63.6645 46....
#> 2     MX        Mexico  99018446     5.25                 MULTIPOLYGON()
#> 3     US United States 259740511     6.17 MULTIPOLYGON(((-155.54211 1...
```

The output shows that the result, `right_join1`, has information about Mexico, but drops information about Greenland.
Furthermore, our right object, as a `data.frame`, doesn't have a geometry representation of Mexico.
As a result, the `right_join1` object contains only non-spatial data of Mexico.
It could be easily illustrated using the `plot` function:


```r
plot(right_join1[0]) # Canada and United States only
```

<img src="figures/unnamed-chunk-36-1.png" width="576" style="display: block; margin: auto;" />

### Inner joins

The `inner_join()` keeps only observations from the left object (`north_america`) where there are matching observations in the right object (`wb_north_america`). 
Additionally, all columns from the left and right object are kept:


```r
inner_join1 = north_america %>% 
  inner_join(wb_north_america, by = c("iso_a2", "name_long" = "name"))
inner_join1
#> Simple feature collection with 2 features and 4 fields
#> geometry type:  MULTIPOLYGON
#> dimension:      XY
#> bbox:           xmin: -171.7911 ymin: 18.91619 xmax: -52.6481 ymax: 83.23324
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#>   iso_a2     name_long urban_pop unemploy                           geom
#> 1     CA        Canada  29022137     6.91 MULTIPOLYGON(((-63.6645 46....
#> 2     US United States 259740511     6.17 MULTIPOLYGON(((-155.54211 1...
```

### Semi joins

The `semi_join()` is very similar to the `inner_join()`. 
It also keeps only observations from the left object (`north_america`) where there are matching observations in the right object, but keeping just columns from the left one:
<!-- filtering? -->


```r
semi_join1 = north_america %>% 
  semi_join(wb_north_america, by = "iso_a2")
semi_join1
#> Simple feature collection with 2 features and 2 fields
#> geometry type:  MULTIPOLYGON
#> dimension:      XY
#> bbox:           xmin: -171.7911 ymin: 18.91619 xmax: -52.6481 ymax: 83.23324
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#>   iso_a2     name_long                           geom
#> 1     CA        Canada MULTIPOLYGON(((-63.6645 46....
#> 2     US United States MULTIPOLYGON(((-155.54211 1...
```

### Anti joins

The `anti_join()` returns all rows from the left object that are not matching observations in the right object.
Only columns from the right object are kept:


```r
anti_join1 = north_america %>% 
  anti_join(wb_north_america, by = "iso_a2")
anti_join1
#> Simple feature collection with 1 feature and 2 fields
#> geometry type:  MULTIPOLYGON
#> dimension:      XY
#> bbox:           xmin: -73.297 ymin: 60.03676 xmax: -12.20855 ymax: 83.64513
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#>   iso_a2 name_long                           geom
#> 1     GL Greenland MULTIPOLYGON(((-46.76379 82...
```


```r
plot(anti_join1[0])
```

<img src="figures/unnamed-chunk-40-1.png" width="576" style="display: block; margin: auto;" />

### Full joins

The `full_join()` returns all rows and all columns from both the left and right object. 
It also puts `NA` in cases where there are not matching values and returns an empty geometry for cases that only exist in the right object:


```r
full_join1 = north_america %>% 
  full_join(wb_north_america, by = "iso_a2")
full_join1
#> Simple feature collection with 4 features and 5 fields (with 1 geometry empty)
#> geometry type:  MULTIPOLYGON
#> dimension:      XY
#> bbox:           xmin: -171.7911 ymin: 18.91619 xmax: -12.20855 ymax: 83.64513
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
#>   iso_a2     name_long          name urban_pop unemploy
#> 1     CA        Canada        Canada  29022137     6.91
#> 2     GL     Greenland          <NA>        NA       NA
#> 3     US United States United States 259740511     6.17
#> 4     MX          <NA>        Mexico  99018446     5.25
#>                             geom
#> 1 MULTIPOLYGON(((-63.6645 46....
#> 2 MULTIPOLYGON(((-46.76379 82...
#> 3 MULTIPOLYGON(((-155.54211 1...
#> 4                 MULTIPOLYGON()
```

## Attribute data creation
<!-- lubridate? -->

Often, we would like to create a new column based on already existing columns.
For example, we want to calculate population density for each country.
For this we need to divide a population column, here `pop`, by an area column , here `area_km2` with unit area in square km.
Using base R, we can type:


```r
data("world")
world_new = world # do not overwrite our original data
world_new$pop_dens = world_new$pop / world_new$area_km2
```

Alternatively, we can use one of **dplyr** functions - `mutate()` or `transmute()`.
`mutate()` adds new columns at the penultimate position in the `sf` object (the last one is reserved for the geometry):


```r
world %>% 
  mutate(pop_dens = pop / area_km2)
```

The difference between `mutate()` and `transmute()` is that the latter skips all other existing columns (except for the sticky geometry column):


```r
world %>% 
  transmute(pop_dens = pop / area_km2)
```

Existing columns could be also paste together using `unite()`. 
For example, we want to stick together `continent` and `region_un` columns into a new `con_reg` column.
We could specify a separator to use between values and if input columns should be removed:


```r
world_unite = world %>%
  unite(con_reg, continent:region_un, sep = ":", remove = TRUE)
```

The `separate()` function is the complement of the `unite()` function.
Its role is to split one column into multiple columns using either a regular expression or character position.


```r
world_separate = world_unite %>% 
  separate(con_reg, c("continent", "region_un"), sep = ":")
```



Two helper functions, `rename()` and `set_names` can be used to change columns names.
The first one, `rename()` replace an old name with a new one.
For example, we want to change a name of column from `name_long` to `name`:


```r
world %>% 
  rename(name = name_long)
```

`set_names` can be used to change names of many columns. 
In this function, we do not need to provide old names: 


```r
new_names = c("ISO_A2", "Name", "Continent", "Region", "Subregion", 
              "Country_type", "Area_in_km2", "Population", "Life_Expectancy",
              "GDP_per_capita", "geom")
world %>% 
  set_names(new_names)
```

## Removing spatial information
<!-- Shouln't that be part of chapter 2-->

It is important to note that the attribute data operations preserve the geometry of the simple features.
As mentioned at the outset of the chapter, however, it can be useful to remove the geometry.
In the case of the `world` dataset, this can be done using
`st_set_geometry()`^[Note that
`st_geometry(world_st) = NULL`
also works to remove the geometry from `world` but overwrites the original object.
].


```r
world_data = world %>% st_set_geometry(NULL)
class(world_data)
#> [1] "data.frame"
```

## Exercises

For these exercises we’ll use the `us_states` and `us_states_df` datasets from the **spData** package:


```r
library(spData)
data("us_states")
data("us_states_df")
```

`us_states` is a spatial object (of class `sf`), containing geometry and a few attributes (including name, region, area, and population) of states within the contiguous United States.
`us_states_df` is a data frame (of class `data.frame`) containing the name and additional variables (including median income and poverty level, for years 2010 and 2015) of US states, including Alaska, Hawaii and Puerto Rico.
The data comes from the US Census Bureau, and is documented in `?us_states` and `?us_states_df`.

<!-- Attribute subsetting -->
1. Create a new object called `us_states_name` that contains only the `NAME` column from the `us_states` object. 
What is the class of the new object? <!--why there is a "sf" part? -->
2. Select columns from the `us_states` object which contain population data.
Obtain the same result using a different command (bonus: try to find 3 ways of obtaining the same result).
Hint: try to use helper functions, such as `contains` or `starts_with` from **dplyr** (see `?contains`).
3. Find all states with the following characteristics (bonus find *and* plot them):
- Belongs to the Midwest region
- Belongs to the West region, has an area below 250,000 km^2^ *and* 20015 population greater than 5,000,000 residents (hint: you may need to use the function `units::set_units()` or `as.numeric()`)
- Belongs to the South region, had an area larger than 150,000 km^2^ or total population in 2015 larger than 7,000,000 residents
<!-- Attribute aggregation -->
4. What was the total population in 2015 in the `us_states` dataset? What was the minimum and maximum total population in 2015?
5. How many states are there in each region?
6. What was the minimum and maximum total population in 2015 in each region? What was the total population in 2015 in each region?
<!-- Attribute joining -->
7. Add variables from `us_states_df` to `us_states` and create a new object called `us_states_stats`. What function did you use and why? Which variable is the key in the both datasets? What is the class of a new object?
8. `us_states_df` has two more variables than `us_states`. How you can find them?
<!-- Attribute creation -->
9. What was the population density in 2015 in each state? What was the population density in 2010 in each state?
10. How much has population density changed between 2010 and 2015 in each state? Calculate the change in percentages and map them.
11. Change the columns names in `us_states` to lowercase. (Hint: helper functions - `tolower()` and `colnames()` may help).
<!-- Mixed exercises -->
<!-- combination of use of select, mutate, group_by, summarize, etc  -->
12. Using `us_states` and `us_states_df` create a new object called `us_states_sel`. The new object should have only two variables - `median_income_15` and `geometry`. Change the name of the `median_income_15` column to `Income`.
13. Calculate the change in median income between 2010 and 2015 for each state. Bonus: what was the minimum, average and maximum median income in 2015 for each region? What is the region with the largest increase of the median income?

<!--chapter:end:03-attribute-operations.Rmd-->


# Spatial data operations

## Prerequisites {-}

- This chapter requires **tidyverse**, **sf**, **units**, and **spData** packages:


```r
library(sf)
library(tidyverse)
library(units)
```

- You must have loaded the `world` data from the **spData** package:


```r
library(spData)
```

## Introduction

<!-- references to the previos chapter -->
<!-- short description to the next sections -->
<!-- should be done after the first draft of the next sections -->
<!-- Note about that datasets should have the same projections -->

## Spatial subsetting

Spatial subsetting is the process of selecting only those features of a spatial object that in some way *intersect* with another spatial object.
Note that 'intersect' in this context has a precise meaning:
if `y` is used to subset features in a 'target' object of `x`, any features in `x` that touch, overlap or are within features in `y` will be selected.
Intersect is the default operation for spatial subsetting but others can be used using the `op =`
argument.^[Interested
readers can see this default value of `op` set in the first line of the function call by entering its long-form name into the console: 
`` sf:::`[.sf` ``
]

There are 9 well-defined operations that can be used for spatial subsetting, covered in section \@ref(topological-relations).
This may seem daunting but the good news is that you do not have to learn all of them separately:
after you understand how to spatially subset objects that *intersect* another (via `st_intersects()`) it is easy to subset based on other types of spatial operation such as `st_touches()`, `st_crosses()` and `st_within()`.
For this reason now we focus only pn one of the spatial subsetting operations.
We use `st_intersects()` instead of any of the others not only because it the default when subsetting with `[`,
but also `st_intersects()` is useful as a 'catch all' that identifies all types of spatial relations.

In general terms, spatial subsetting is simply the spatial equivalent of *attribute subsetting*.
However, to do spatial subsetting *two spatial objects are needed* the spatial relation between which is to be established.
As with attribute subsetting, spatial subsetting is a *binary operation*: an object is either selected or not.
As in section \@ref(attribute-subsetting), we start with base methods before describing how to do it in the **tidyverse**.
<!-- todo: link to non-binary links, e.g. area-weighted spatial interpolation -->

<!-- ### Spatial subsetting in base R -->

Attribute subsetting in base R is done with the `[` operator and passing into the square brackets a vector of class `integer` (whole numbers) or `logical` (a vector of `TRUE`s and `FALSE`s).
This means `world[1:6,]` subsets the first 6 countries of the world and that `world[world$area_km2 < 10000,]` returns the subset of countries that have a small surface area.
For this chapter we will use countries in Africa, which can be generated using this method as
follows:^[Recall
that we can also subset simple features using the `filter()` function, e.g. with `filter(world, continent == "Africa")`]


```r
africa_wgs = world[world$subregion == "Western Africa", ]
```

To further set-up the input data, we will reproject the data to the coordinate reference system (CRS) 32630 (it's EPSG code, explained in Chapter 6):


```r
africa = st_transform(africa_wgs, crs = 32630) 
```

*Spatial* subsetting in base R use the same method as attribute subsetting, except *another spatial object* is placed inside the square brackets in the place of an `integer` or `logical` vector.
This is a concise and consistent syntax, as shown in the next code chunk.
Let's test it with a hypothetical scenario: we want to subset all countries within 20 degrees of the point where the equator (where latitude = 0 degrees) intersects the prime meridian (longitude = 0 degrees), as illustrated in Figure \@ref(fig:globe).
The subsetting object is created below.
Note that this must have the same CRS as the target object (set with the `crs` argument):


```r
center = st_sf(st_sfc(st_point(c(0, 0)), crs = 4326))
buff = st_buffer(x = center, dist = 20)
buff = st_transform(buff, 32630)
```

<div class="figure" style="text-align: center">
<img src="figures/globe.png" alt="Hypothetical subsetting scenario: select all countries which intersect with a circle of 20 degrees in radius around planet Earth. Figure created with the **[globe](https://cran.r-project.org/package=globe)** package." width="250" />
<p class="caption">(\#fig:globe)Hypothetical subsetting scenario: select all countries which intersect with a circle of 20 degrees in radius around planet Earth. Figure created with the **[globe](https://cran.r-project.org/package=globe)** package.</p>
</div>

The data to be subset, or 'target layer', is the `africa` created above, which has a projected CRS (`32630`).
Now that the input data is set-up, the spatial subsetting operation is a single, concise command:


```r
africa_buff = africa[buff,]
```

Note that the command emits a message: about assuming `planar coordinates`.
This is because spatial operations (especially distance and area calculations) cannot be assumed to be accurate in a geographic (longitude/latitude) CRS.
In this case there is a clear justification: the data is close to the equator where there is least distortion caused by the curvature of the earth, and the example illustrates the method, which would more usually be used on pojected ('planar') data.
In any case, the spatial subsetting clearly worked.
As illustrated by Figure \@ref(fig:buffeq), only countries which spatially intersect with the giant circle are returned:


```r
plot(africa_buff["pop"])
plot(buff, add = TRUE)
```

<div class="figure" style="text-align: center">
<img src="figures/buffeq-1.png" alt="Subset of the `africa` data selected based on their intersection with a circle 20 degrees in radius with a center point at 0 degrees longitude and 0 degrees latitude." width="576" />
<p class="caption">(\#fig:buffeq)Subset of the `africa` data selected based on their intersection with a circle 20 degrees in radius with a center point at 0 degrees longitude and 0 degrees latitude.</p>
</div>

Note that countries that only just touch the giant circle are selected such as the large country at the north of plot (Algeria).
`st_relates()` includes countries that only touch (but are not within or overlapping with) the selection object.
Other spatial subsetting operations such as `st_within()` are more conservative, as shown in section \@ref(topological-relations).

Before we progress to explore the differences between different spatial subsetting operations, it is worth seeing alternative ways to acheive the same result,
to deepen understanding of what is going on 'under the hood' (vital for developing advanced geocomputation applications).
The second way to reproduce the subsetting operation illustrated in Figure \@ref(fig:buffeq) simply involves expanding the operation over 2 lines:


```r
sel_buff = st_intersects(x = africa, y = buff, sparse = FALSE)
africa_buff2 = africa[sel_buff, ]
```

The third way is essentially the same as the second, but uses the `filter()` function introduced in section \@ref(attribute-subsetting), forming the foundations of a 'tidy' spatial data analysis workflow.
If you already use **dplyr** for data manipulation, this way should seem familiar:


```r
africa_buff3 = africa %>%
  filter(st_intersects(x = ., y = buff, sparse = FALSE))
```

How can we be sure that the results obtained through the 4 subsetting operations demonstrated above?
We can test them as follows:


```r
identical(x = africa_buff, y = africa_buff2)
#> [1] TRUE
identical(x = africa_buff, y = africa_buff3)
#> [1] FALSE
```

The reason that the third spatially subset object (`africa_buff3`) is not identical is that **dplyr** changes the row names:


```r
head(row.names(africa_buff))
#> [1] "14" "15" "32" "60" "61" "62"
head(row.names(africa_buff3))
#> [1] "1" "2" "3" "4" "5" "6"
```

If the row names are re-set, the objects become identical:


```r
attr(africa_buff3, "row.names") = attr(x = africa_buff, "row.names")
identical(africa_buff, africa_buff3)
#> [1] TRUE
```


### Note {-}

This discarding of row names is not something that is specific to spatial
data:^[**dplyr** discards row names by design.
For further discussion of this decision, and some controversy, see the (closed) issue [#366](https://github.com/tidyverse/dplyr/issues/366) in the package's issue tracker.]


```r
row.names(africa[africa$subregion == "Northern Europe",])
#> character(0)
row.names(filter(africa, subregion == "Northern Europe"))
#> character(0)
```

## Spatial data aggregation 

Like attribute data aggregation, covered in section \@ref(attribute-data-aggregation), spatial data aggregation is a way of *condensing* data.
Aggregated data show some statistic about a variable (typically mean average or total) in relation to some kind of *grouping variable*. 
For attribute data aggregation the grouping variable is another variable, typically one with few unique values relative to the number of rows.
The `continent` variable in the `world` dataset is a good example:
there are only 8 unique continents but 177 countries.
In section \@ref(attribute-data-aggregation) the aggregation process condensed the `world` dataset down into only 8 rows and an aggregated `pop` variable representing the total population per continent (see Figure \@ref(fig:continent-pop)).

Spatial data aggregation is the same conceptually but uses a *spatial* grouping object:
the *output* is the same, in terms of number of rows/features and geometry, as the *grouping object*, but with new variables corresponding to the input dataset.
As with spatial subsetting, spatial aggregation operations work by extending existing functions.
Since mid-2017 (with the release of **sf** `0.5-3`) the base R function `aggregate()` works with a spatial object as a grouping variable.

Building on the example presented the previous section (\@ref(spatial-subsetting)), we demonstrate this by aggregating the population of countries that intersect with the buffer represented by the circular `buff` object created in the previous section.


```r
buff_agg = aggregate(x = africa["pop"], by = buff, FUN = sum)
```

The result, `buff_agg`, is a spatial object with the same geometry as `by` (the circular buffer in this case) but with an additional variable, `pop` reporting summary statistics for all features in `x` that intersect with `by` (the total population of the countries that touch the buffer in this case).
Plotting the result (with `plot(buff_agg)`) shows that the operation does not really make sense:
Figure \@ref(fig:buff-agg) shows a population of over half a billion people mostly located in a giant circle floating off the west coast of Africa!  

<div class="figure" style="text-align: center">
<img src="figures/buff-agg-1.png" alt="Result of spatial aggregation showing the total population of countries that intersect with a large circle whose center lies at 0 degrees longitude and latituge" width="576" />
<p class="caption">(\#fig:buff-agg)Result of spatial aggregation showing the total population of countries that intersect with a large circle whose center lies at 0 degrees longitude and latituge</p>
</div>

The results of the spatial aggregation exercise presented in Figure \@ref(fig:buff-agg) are unrealistic for three reasons:

- People do not live in the sea (the geometry of the aggregating object is not appropriate for the geometry target object).
- This method would 'double count' countries whose borders cross aggregating polygons when multiple, spatially contiguous, features are used as the aggregating object.
- It is wrong to assume that all the people living in countries that *touch* the buffer reside *within* it (the default spatial operator `st_intersects()` is too 'greedy'). The most extreme example of this is Algeria, the most northerly country selected:
the spatial aggregation operation assumes that all 39 million Algerian citizens reside in the tiny southerly tip that is within the circular buffer.

A number of methods can be used to overcome these issues, which result in unrealistically high population attributed to the circular buffer illustrated in Figure \@ref(fig:buff-agg).
The simplest of these is to convert the country polygons into points representing their *geographic centroids* before aggregation.
<!-- Todo: reference section where we demonstrate geographic centroid generation -->
This would ensure that any spatially contiguous aggregating object covering the target object (the Earth in this case) would result in the same total: there would be no double counting.
The estimated total population residing within the study area would be more realistic if geographic centroids were used.
(The centroid of Algeria, for example, is far outside the aggregating buffer.)
Except in cases where the number of target features per aggregating feature is very large, or where the aggregating object is *spatially congruent* with the target (covered in section \@ref(spatial-congruence-and-areal-interpolation)), using centroids can also lead to errors due to boundary effects:
imagine a buffer that covers a large area but contains no centroids.
These issues can be tackled when aggregating areal target data with areal interpolation.

### Spatial congruence and areal interpolation

Spatial congruence is an important concept when interpreting the results of spatial aggregation and other operations.
An *aggregating object* object (which we will refer to as `y`, representing the buffer object in the previous section) is *congruent* with the target object `x`, corresponding to the first argument of `aggregate()` in the previous section, if the two objects have shared borders:
no feature in `x` overlaps one or more features in `y`.
*Incongruent* objects, by contrast do not share common borders [@qiu_development_2012].
This is the case illustrated in Figure \@ref(fig:buff-agg), where the borders of the countries in the 'target' object bear no relation to, and frequently cross, the outline of the aggregating buffer.

This is problematic if one wants to convert from type of *areal* unit that is incongruent with another, as illustrated in Figure \@ref(fig:areal-example).
Areal interpolation resolves this problem.
A number of methods have been developed to for the task, all of which start from the following constraint, succinctly described in a classic paper on the subject [@tobler_smooth_1979]:
"that the original [target] data arrive packaged in discrete  collection regions."

<div class="figure" style="text-align: center">
<img src="figures/areal-example-1.png" alt="Illustration of congruent (left) and incongruent (right) areal units." width="576" />
<p class="caption">(\#fig:areal-example)Illustration of congruent (left) and incongruent (right) areal units.</p>
</div>

The simplest useful method for spatial interpolation is *area weighted* spatial interpolation.
This is implemented in `st_interpolate_aw()`, as demonstrated below:


```r
buff_agg_aw = st_interpolate_aw(x = africa["pop"], to = buff, extensive = TRUE)
#> Warning in st_interpolate_aw(x = africa["pop"], to = buff, extensive =
#> TRUE): st_interpolate_aw assumes attributes are constant over areas of x
```

<!-- - `aggregate.sf()` - aggregate an sf object, possibly union-ing geometries -->
<!-- - disaggregation?? `st_cast()` - https://github.com/edzer/sfr/wiki/migrating -->
<!-- - `group_by()` + `summarise()` - potential errors -->
<!-- - ? generalization **rmapsharper** - https://github.com/ateucher/rmapshaper -->
<!-- `st_union` -->

## Spatial data joining 

<!-- e.g. two point's datasets (non-overlapping) -->
<!-- e.g. two point's datasets (overlapping) -->
<!-- ? topological problems of joining lines/polygons? -->
<!-- joining different types (e.g. points + polygons = geometry) -> save as GPKG? -->
<!-- `merge()`; `st_interpolate_aw()` -->

## Spatial data creation

<!-- where should "area" example be? in this or the previous chapter? -->
<!-- `st_centroid()` -->
<!-- `st_buffer()` -->
<!-- http://r-spatial.org//r/2017/06/09/mapedit_0-2-0.html -->


```r
# add a new column
africa$area = set_units(st_area(africa), value = km^2)
africa$pop_density = africa$pop / africa$area

# OR
africa = africa %>%
        mutate(area = set_units(st_area(.), value = km^2)) %>%
        mutate(pop_density = pop / area)
```

Note that this has created a attributes for the area and population density variables:


```r
attributes(africa$area)
#> $units
#> $numerator
#> [1] "km" "km"
#> 
#> $denominator
#> character(0)
#> 
#> attr(,"class")
#> [1] "symbolic_units"
#> 
#> $class
#> [1] "units"
attributes(africa$pop_density)
#> $units
#> $numerator
#> character(0)
#> 
#> $denominator
#> [1] "km" "km"
#> 
#> attr(,"class")
#> [1] "symbolic_units"
#> 
#> $class
#> [1] "units"
```

These can be set to `NULL` as follows:


```r
attributes(africa$area) = NULL
attributes(africa$pop_density) = NULL
```

<!-- ## Spatial data transformation -->
<!-- changes classes; polygonize, etc-->

### Topological relations

<!-- http://lin-ear-th-inking.blogspot.com/2007/06/subtleties-of-ogc-covers-spatial.html -->
<!-- https://edzer.github.io/sfr/articles/sf3.html -->
<!-- https://github.com/edzer/sfr/wiki/migrating#relevant-commands-exported-by-rgeos -->
<!-- Relations and inverse relations -->
<!-- http://desktop.arcgis.com/en/arcmap/latest/extensions/data-reviewer/types-of-spatial-relationships-that-can-be-validated.htm -->
<!-- Topological relations: + difference between datatypes -->
<!-- ?geos_binary_pred -->
<!-- Distance relations -->
<!-- Subset (1) points in polygons <-> (2) -->


```r
a1 = st_polygon(list(rbind(c(-1, -1), c(1, -1), c(1, 1), c(-1, -1))))
a2 = st_polygon(list(rbind(c(2, 0), c(2, 2), c(3, 2), c(3, 0), c(2, 0))))
a = st_sfc(a1, a2)

b1 = a1 * 0.5
b2 = a2 * 0.4 + c(1, 0.5)
b = st_sfc(b1, b2)

l1 = st_linestring(x = matrix(c(0, 3, -1, 1), , 2))
l2 = st_linestring(x = matrix(c(-1, -1, -0.5, 1), , 2))
l = st_sfc(l1, l2)

p = st_multipoint(x = matrix(c(0.5, 1, -1, 0, 1, 0.5), , 2))

plot(a, border = "red", axes = TRUE)
plot(b, border = "green", add = TRUE)
plot(l, add = TRUE)
plot(p, add = TRUE)
```

<img src="figures/unnamed-chunk-19-1.png" width="576" style="display: block; margin: auto;" />

Equals:
<!-- https://postgis.net/docs/ST_Equals.html -->


```r
st_equals(a, b, sparse = FALSE)
```

Contains:
<!-- https://postgis.net/docs/ST_Contains.html -->
<!-- https://postgis.net/docs/ST_ContainsProperly.html -->


```r
st_contains(a, b, sparse = FALSE)
st_contains_properly(a, b, sparse = FALSE)
```

Covers:
<!-- https://postgis.net/docs/ST_Covers.html -->
<!-- https://postgis.net/docs/ST_CoveredBy.html -->


```r
st_covers(a, b, sparse = FALSE)
st_covered_by(a, b, sparse = FALSE)
```

Within:
<!-- https://postgis.net/docs/ST_Within.html -->


```r
st_within(a, b, sparse = FALSE)
```

Overlaps:
<!-- https://postgis.net/docs/ST_Overlaps.html -->


```r
st_overlaps(a, b, sparse = FALSE)
```

Intersects:
<!-- https://postgis.net/docs/ST_Intersects.html -->


```r
st_intersects(a, b, sparse = FALSE)
```

Disjoint:
<!-- https://postgis.net/docs/ST_Disjoint.html -->


```r
st_disjoint(a, b, sparse = FALSE)
```

Touches:
<!-- https://postgis.net/docs/ST_Touches.html -->


```r
st_touches(a, b, sparse = FALSE)
```

Crosses:
<!-- https://postgis.net/docs/ST_Crosses.html -->


```r
st_crosses(a, b, sparse = FALSE)
```

DE9-IM - https://en.wikipedia.org/wiki/DE-9IM
<!-- https://edzer.github.io/sfr/reference/st_relate.html -->


```r
st_relate(a, b, sparse = FALSE)
```

<!-- examples (points/polygons) -->
<!-- examples (points/lines) -->
<!-- examples (lines/polygons) -->

### Distance relations


```r
st_distance(a, b)
```

### Spatial clipping

Spatial clipping is a form of spatial subsetting that involves changes to the `geometry` columns of at least some of the affected features.

Clipping can only apply to features more complex than points: 
lines, polygons and their 'multi' equivalents.
To illustrate the concept we will start with a simple example:
two overlapping circles with a centrepoint 1 unit away from each other and radius of 1:


```r
b = st_sfc(st_point(c(0, 1)), st_point(c(1, 1))) # create 2 points
b = st_buffer(b, dist = 1) # convert points to circles
l = c("x", "y")
plot(b)
text(x = c(-0.5, 1.5), y = 1, labels = l) # add text
```

<div class="figure" style="text-align: center">
<img src="figures/points-1.png" alt="Overlapping circles." width="576" />
<p class="caption">(\#fig:points)Overlapping circles.</p>
</div>

Imagine you want to select not one circle or the other, but the space covered by both `x` *and* `y`.
This can be done using the function `st_intersection()`, illustrated using objects named `x` and `y` which represent the left and right-hand circles:


```r
x = b[1]
y = b[2]
x_and_y = st_intersection(x, y)
plot(b)
plot(x_and_y, col = "lightgrey", add = TRUE) # color intersecting area
```

<img src="figures/unnamed-chunk-31-1.png" width="576" style="display: block; margin: auto;" />

The subsequent code chunk demonstrate how this works for all combinations of the 'venn' diagram representing `x` and `y`, inspired by [Figure 5.1](http://r4ds.had.co.nz/transform.html#logical-operators) of the book R for Data Science [@grolemund_r_2016].
<!-- Todo: reference r4ds -->

<div class="figure" style="text-align: center">
<img src="figures/venn-clip-1.png" alt="Spatial equivalents of logical operators" width="576" />
<p class="caption">(\#fig:venn-clip)Spatial equivalents of logical operators</p>
</div>

To illustrate the relationship between subsetting and clipping spatial data, we will subset points that cover the bounding box of the circles `x` and `y` in Figure \@ref(fig:venn-clip).
Some points will be inside just one circle, some will be inside both and some will be inside neither.
To generate the points will use a function not yet covered in this book, `st_sample()`.

There are two different ways to subset points that fit into combinations of the circles: via clipping and logical operators.
But first we must generate some points.
We will use the *simple random* sampling strategy to sample from a box representing the extent of `x` and `y`, using the code below to generate the situation plotted in Figure \@ref(fig:venn-subset):


```r
bb = st_bbox(st_union(x, y))
pmat = matrix(c(bb[c(1, 2, 3, 2, 3, 4, 1, 4, 1, 2)]), ncol = 2, byrow = TRUE)
box = st_polygon(list(pmat))
set.seed(2017)
p = st_sample(x = box, size = 10)
plot(box)
plot(x, add = T)
plot(y, add = T)
plot(p, add = T)
text(x = c(-0.5, 1.5), y = 1, labels = l)
```

<div class="figure" style="text-align: center">
<img src="figures/venn-subset-1.png" alt="Randomly distributed points within the bounding box enclosing circles x and y." width="576" />
<p class="caption">(\#fig:venn-subset)Randomly distributed points within the bounding box enclosing circles x and y.</p>
</div>



### Exercises

1. Write code that subsets points that are contained within `x` *and* `y` (illustrated by the plot in the 2^nd^ row and the 1^st^ column in Figure \@ref(fig:venn-clip)).
- Create a randomly located point with the command `st_point()` (refer back to section \@ref(sfg) to see how to create spatial data 'from scratch').
2. Write code that uses functions `aggregate()` and `st_buffer()` to answers the following question: What proportion of the world's population lives in countries that intersect a circle with a 10 degree radius of the intersection between the equator and the [9^th^ meridian](https://en.wikipedia.org/wiki/9th_meridian_east)? (Advanced challenge: find the point with the highest number of people within a 10 degree radius.)


```r
center9 = st_sf(st_sfc(st_point(c(-9, 0)), crs = 4326))
buff9 = st_buffer(center9, dist = 10)
#> Warning in st_buffer.sfc(st_geometry(x), dist, nQuadSegs): st_buffer does
#> not correctly buffer longitude/latitude data, dist needs to be in decimal
#> degrees.
agg9 = aggregate(world["pop"], buff9, FUN = sum)
#> although coordinates are longitude/latitude, it is assumed that they are planar
agg9$pop / sum(world$pop, na.rm = TRUE)
#> [1] 0.00998
```

3. Assuming that people are evenly distributed across countries, estimate the population living *within* the circle created to answer the previous question.


```r
interp9 = st_interpolate_aw(x = world["pop"], to = buff9, extensive = TRUE)
#> Warning in st_interpolate_aw(x = world["pop"], to = buff9, extensive =
#> TRUE): st_interpolate_aw assumes attributes are constant over areas of x
```

<!-- TODO? create a series of polygons distributed evenly over the surface of the Earth and clip them. -->

<!-- ```{r} -->
<!-- set.seed(2018) -->
<!-- blob_points = st_sample(x = world, size = 2) -->
<!-- blobs = st_buffer(x = blob_points, dist = 1) -->
<!-- plot(blobs) -->
<!-- ``` -->

<!--chapter:end:04-spatial-operations.Rmd-->


# Geographic data I/O {#read-write}

The previous chapters provided an overview of spatial data classes in R, with a focus on simple features.
This chapter is about getting spatial data onto your computer and then, perhaps after processing it with techniques described in this book, back out to the world.
<!-- Not sure if this is the place for the following two sentences... Or if so, some kind of link is missing.-->
We include a section (\@ref(visual-outputs)) on visualization because outputting data in a human (not just computer) readable format enables non-programmers to benefit from your work.
If your aim is to use geocomputation to improve the world, e.g. by encouraging evidence-based policies, this final stage is vital.

I/O is short for "input/output" which means, in plain English, "reading and writing data".
We use the acronym instead of plain English not to confuse you or to make chapter names short, but because that's the term used in computer science and it is useful to think of data import and export from a computing perspective.^[
Concepts such as computational efficiency, hard disk space and 'idempotence' are useful when thinking about reading and writing geographic datasets, which can become large and difficult to handle.
Loading/saving data is yet another way of saying the same thing.
]
<!-- todo: check we mention computational efficiency, disk-space and 'idempotence' -->

<!-- Old intro to this chapter - can we salvage anything from this? -->
<!-- Reading, writing and plotting are 3 of the most important initial stages in geocomputation. -->
<!-- If you cannot load your data, it's not even worth starting. -->
<!-- If you cannot write your processed data, it will make it hard to collaborate with others. -->
<!-- Furthermore, an often-overlooked issue is that if you cannot create visuals of your spatial data, it will be hard to understand. -->
<!-- For this reason this introductory chapter also has a section on basic map making. -->

## Data Input (I)

To efficiently read data into R, it helps to have an understanding of what happens 'under the hood'.
Executing commands such as `sf::st_read()` (the main function we use for loading spatial data, from the **sf** package) or `readr::read_csv()` silently sets off a chain of events that loads objects.
<!-- I would suggest to avoid confusion. readr::read_csv cannot load spatial objects. Since you write "happens under the hood", I would also expect a bit more detail on "silently sets off a chain of events". -->
"Loading" in this context means loading the data into R or, more precisely, assigning objects to your workspace, stored in RAM accessible from the `.GlobalEnv` of your current R session.
<!-- What is your understanding of workspace? Or what is the difference between workspace and the global environment here?-->
<!-- coud add a footnote here mentioning `.GlobalEnv` -->

Spatial data comes in a wide variety of file formats, and **sf** is able to handle most of them <!-- is that right? --> via its `st_read()` command.
Behind the scenes it uses GDAL, which supports the import of a very wide range of spatial data formats.
The first argument of `st_read()` is `file`, which should be a text string or an object containing a single text string:


```r
library(sf)
#> Linking to GEOS 3.5.0, GDAL 2.1.0, proj.4 4.8.0
f = system.file("shapes/world.gpkg", package = "spData")
world = st_read(f)
#> Reading layer `wrld.gpkg' from data source `/home/travis/R/Library/spData/shapes/world.gpkg' using driver `GPKG'
#> Simple feature collection with 177 features and 10 fields
#> geometry type:  MULTIPOLYGON
#> dimension:      XY
#> bbox:           xmin: -180 ymin: -90 xmax: 180 ymax: 83.64513
#> epsg (SRID):    4326
#> proj4string:    +proj=longlat +datum=WGS84 +no_defs
```

**Tip**: `read_sf()` and `write_sf()` can be used as easy-to-remember alternatives to `st_read()` and `st_write()`.
Remember they hide information about the data source and overwrite existing data, though.

A major advantage of **sf** is that it is fast.
To demonstrate this, we will use a function to compare `st_read` with its **sp** equivalent, `rgdal::readOGR`:


```r
bench_read = function(file, n) {
  m = microbenchmark(times = n,
                     rgdal::readOGR(f),
                     st_read(f)
  )
  mean(m$time[1:n]) / mean(m$time[(n + 1):(n * 2)])
}
```

This function takes as arguments an input file (`file`) and a number of times to run each command (`n`) and returns how many times faster `st_read()` is than `readOGR()`.
Let's run the benchmark for the `world.gpkg` file represented by the object `f`:
<!-- We as illustrated in the benchmark below: -->


```r
library(microbenchmark)
read_world_gpkg = bench_read(file = f, n = 5)
```


```r
read_world_gpkg
#> [1] 2.33
```

The results demonstrate that **sf** was around 2 times faster than **rgdal** at reading-in the world countries shapefile.
The relative performance of `st_read()` compared with other functions will vary depending on file format and the nature of the data.
To illustrate this point, we performed the same operation on a geojson file and found a greater speed saving:


```r
f = system.file("shapes/cycle_hire_osm.geojson", package = "spData")
read_lnd_geojson = bench_read(file = f, n = 5)
```


```r
read_lnd_geojson
#> [1] 3.43
```

In this case **sf** was around 3 times faster than **rgdal**.

To find out which data formats **sf** supports, run `st_drivers()`. Here, we show only the first two drivers:


```r
sf_drivers = st_drivers()
head(sf_drivers, n = 2)
#>          name                  long_name write  copy is_raster is_vector
#> PCIDSK PCIDSK       PCIDSK Database File  TRUE FALSE      TRUE      TRUE
#> netCDF netCDF Network Common Data Format  TRUE  TRUE      TRUE      TRUE
```

## Data output (O)



The counterpart of `st_read()` is `st_write()`.
It allows to write **sf** objects to a wide range of geographic vector file formats, including the most common ones such as `.geojson`, `.shp` and `.gpkg`.
Based on the file name `st_write()` decides automatically which driver to use. How fast the writing process is depends also on the driver:
<!-- Is this comparison here necessary, or shouldn't we instead focus on the automatic driver selection? -->


```r
system.time(st_write(world, "world.geojson", quiet = TRUE))
#>    user  system elapsed 
#>   0.064   0.000   0.064
system.time(st_write(world, "world.shp", quiet = TRUE)) 
#>    user  system elapsed 
#>   0.048   0.000   0.049
system.time(st_write(world, "world.gpkg", quiet = TRUE))
#>    user  system elapsed 
#>   0.016   0.016   0.032
```



<!-- ```{r} -->
<!-- st_write(obj = world, dsn = "world.gpkg") -->
<!-- ``` -->

**Note**: if you try to write to the same data source again, the function will fail.
<!-- Why are you creating a modified version? Could you not use the same object again to demonstrate that overwriting will fail? -->
This is demonstrated in the code below for a modified version of the world in which the population doubles in all countries (don't worry about the **dplyr** code for now, this is covered in Chapter \@ref(attr)):


```r
world_mod = dplyr::mutate(world, pop = pop * 2)
```




```r
st_write(obj = world_mod, dsn = "world.gpkg")
##   GDAL Error 1: Layer world.gpkg already exists, CreateLayer failed.
## Use the layer creation option OVERWRITE=YES to replace it.
```

The error message (only partly reproduced above) provides some information as to why the function failed.
The `GDAL Error 1` statement makes clear that the failure occurred at the GDAL level.
Additionally, the suggestion to use `OVERWRITE=YES` provides a clue how to fix the problem.
However, this is a GDAL option, and not a `st_write()` argument.
Luckily, `st_write` provides a `layer_options` argument through which we can pass driver-dependent options:


```r
st_write(obj = world_mod, dsn = "world.gpkg", layer_options = "OVERWRITE=YES")
```

Another solution is to use the `st_write()` argument `delete_layer`. Setting it to `TRUE` deletes already existing layers in the data source before the function attempts to write (note there is also a `delete_dsn` argument):


```r
st_write(obj = world_mod, dsn = "world.gpkg", delete_layer = TRUE)
```

You can achieve the same with `write_sf()` since it is equivalent to (technically an *alias* for) `st_write()`, except that its defaults for `delete_layer` and `quiet` is `TRUE`.
This enables spatial data to be overwritten more concisely, and with less output going to screen:
<!-- What does this mean: overwritten more concisely? -->




```r
write_sf(obj = world_mod, dsn = "world.gpkg")
```

<!-- Is the file.remove()-part important? -->
A blunter way to update file-based geographic data sources such as `.gpkg` files is to simply delete them.
This is not generally recommended, as it will not work for multi-file data sources such as `.shp` files:


```r
file.remove("world.gpkg")
```

## File formats

<!-- don't use shp -->

## Visual outputs

## Exercises

1. Name three differences between `write_sf()` and the more well-known function `st_write()`.

1. What are the default arguments of `read_sf()` and `write_sf()` that enable two of these differences?

<!-- ## Vector -->

<!-- 
- sf package 
- st_drivers
- st_read, read_sf
- st_write, write_sf
- text files 
- WKT, WKB, sp (st_as_sf)
-->

<!-- ## Raster -->

<!-- 
- raster package 
- raster
-->

<!--chapter:end:05-read-write-plot.Rmd-->


# References

<!--chapter:end:references.Rmd-->
