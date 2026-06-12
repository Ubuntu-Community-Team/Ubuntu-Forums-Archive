---
title: "Calculator source code"
date: 2010-12-23
forum: General Help
---

### Post by sid.mallya on 2010-12-23
I want to know if it is possible to edit the source code of the programs in Linux. Like, take the calculator for instance. If I want to add a user-defined function to it, how can I do it - if I can do it at all ?

In general, where and how can I look at the source code of such programs ?

---

### Post by theasprint on 2010-12-23
Could it be in Ubuntu software Center? 

Just guessing only. But there are a list of installed programs in the Ubuntu software center and I think it is possible to get the source code from there.

---

### Post by anglican on 2010-12-23
> **sid.mallya said:**
> I want to know if it is possible to edit the source code of the programs in Linux. Like, take the calculator for instance. If I want to add a user-defined function to it, how can I do it - if I can do it at all ?

In general, where and how can I look at the source code of such programs ?Source code for just about everything in Ubuntu is available. To get source code you just run:

```
sudo apt-get build-dep $package
```where package = whatever package you want. Then do 
```
 sudo apt-get source $package
```to get the source for that package. However for many programs the code may be part of a large package e.g. xcalc is part of the "x11-apps" package which includes a lot of other programs too, so you may prefer to simply google for the source code and just get the files you need. For example, for xcalc you can find the source at:

[http://xcalc.sourcearchive.com/documentation/1.0.1/main.html](http://xcalc.sourcearchive.com/documentation/1.0.1/main.html)

To find out which package a particular program belongs to, use:

```
dpkg -S /path/to/file
```e.g.

```
dpkg -S /usr/bin/xcalc
```H

---

### Post by sid.mallya on 2010-12-23
Thanks a lot. :)

---

