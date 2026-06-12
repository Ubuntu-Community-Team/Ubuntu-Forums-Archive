---
title: "Multiple ATLAS binaries"
date: 2010-12-10
forum: General Help
---

### Post by akats on 2010-12-10
Hi,

I installed the package libatlas3gf-amd64sse3 on my system, as it best fits my hardware.  However, when I tried installing python-opencv, it insisted that I install libatlas3gf-base , so now both of these packages are on my computer.  They install their files into different directories, like 
/usr/lib/atlas-amd64sse3/atlas/libblas.so.3gf vs.
/usr/lib/atlas-base/atlas/libblas.so.3gf

I don't understand why OpenCV insists on the base version -- does anyone?  More importantly, how do I know and ensure that all the other packages, like numpy are using the optimized version?  All of this is on meerkat.

Thanks!

Anatoliy

---

