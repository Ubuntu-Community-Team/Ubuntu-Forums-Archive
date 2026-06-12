---
title: "*-doc packages, what for?"
date: 2011-08-20
forum: General Help
---

### Post by zia.newversion on 2011-08-20
I installed ```
libboost1.40-doc
``` package.
I guess it is documentation.

But if I use ```
man libboost-1.40
``` it doesn't work. How do I read the documentation? Is there a package for that?

---

### Post by Cheesehead on 2011-08-20
> Description: Boost.org libraries documentation
 The Boost web site provides free, peer-reviewed, portable C++ source
 libraries. The emphasis is on libraries which work well with the C++
 Standard Library. One goal is to establish "existing practice" and
 provide reference implementations so that the Boost libraries are
 suitable for eventual standardization. Some of the libraries have
 already been proposed for inclusion in the C++ Standards Committee's
 upcoming C++ Standard Library Technical Report.
 .
 This is documentation for the libboost1.40-dev package in HTML format.
 Some pages point to header files provided in libboost1.40-dev package,
 so it is suggested to install the latter as well.

You're right. HTML files won't work with man.

---

