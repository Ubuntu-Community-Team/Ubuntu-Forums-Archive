---
title: "Java Gui for R (JGR) in Karmic Koala?"
date: 2009-11-18
forum: General Help
---

### Post by inkhorn on 2009-11-18
Hi All,

I followed the instructions on [http://rosuda.org/JGR/linux.shtml](http://rosuda.org/JGR/linux.shtml) to install JGR on my machine that runs Karmic Koala.  However, every time I go into R to type "install.packages('JGR')", I get a message saying that JGR is not available.  Anybody else having this problem?

Inkhorn

---

### Post by MKS on 2009-11-18
I'm having exactly the same issue. Might be something to do with the CRAN repository, but I *did* have JGR working under Jaunty.

---

### Post by johannesS on 2009-11-20
Hi
I had the same problem on an openSuse system.
I could resolve it by updating R-base and R-base-devel to the newest stable version (2.10.xy)

Then, install.packages("JGR") etc. worked fine. 

Possibly that has to do with rJava dependencies. 

Cheers
Johannes

---

