---
title: "Can't Start R Commander"
date: 2011-05-27
forum: General Help
---

### Post by myrdos on 2011-05-27
When I try to run R Commander, the window pops up but is unresponsive. Nothing will respond to clicks, and there's nothing to do but Ctrl-C it.

```
r --interactive
library(Rcmdr)
Loading required package: tcltk
Loading Tcl/Tk interface ... done
Loading required package: grDevices
Loading required package: utils
Loading required package: car
Loading required package: stats
Loading required package: graphics
Loading required package: MASS
Loading required package: nnet
Loading required package: survival
Loading required package: splines

Rcmdr Version 1.6-2


Attaching package: 'Rcmdr'


The following object(s) are masked from 'package:tcltk':

    tclvalue
```

I tried installing the more recent packages from here: [http://cran.r-project.org/bin/linux/ubuntu](http://cran.r-project.org/bin/linux/ubuntu), with the same result except that the following also appears in the console:
```

The following object(s) are masked from 'package:stats':

    nobs
```

Does anyone know how to work around this?

---

### Post by rg4w on 2011-05-27
Have you tried installing from the Ubuntu Software Center?  The first time I installed R Commander I did it manually and it was a lot of work.  When I got my newer laptop I discovered it was in the USC, and it installed well, taking care of all of the dependencies for me.

---

### Post by myrdos on 2011-05-28
Yes, I installed everything from the Ubuntu repositories. Although I can't say that package r-cran-rcmdr has all the dependencies it needs, specifically it complains that leaps, Hmisc and aplpack are missing.

---

### Post by sanderd17 on 2011-05-28
Not a solution, but an alternative: The R-plugin for gedit. It works quite well.

---

