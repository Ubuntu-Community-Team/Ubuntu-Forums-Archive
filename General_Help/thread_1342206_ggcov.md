---
title: "ggcov"
date: 2009-11-30
forum: General Help
---

### Post by aSteve on 2009-11-30
I've installed ggcov, and when I try to run it:

--
$ ggcov
ggcov: error while loading shared libraries: libbfd-2.19.51.20090515.so: cannot open shared object file: No such file or directory
$ locate libbfd
/usr/lib/libbfd-2.20.so
$
--

I've found this bug report...

[https://bugs.launchpad.net/ubuntu/+source/ggcov/+bug/40367](https://bugs.launchpad.net/ubuntu/+source/ggcov/+bug/40367)

I tried to follow Phil M's suggestion to rebuild from source - but failed with this error:

--
filename.c: In function 'char* file_make_absolute_to(const char*, const char*)':
filename.c:192: error: invalid conversion from 'const char*' to 'char*'
make[4]: *** [filename.o] Error 1
make[4]: Leaving directory `/tmp/ggcov-0.8/build-tree/ggcov-0.8/src'
---

I notice that the bug is marked 'triaged' - but, given the time this bug has been known, suspect that there must be some work-around that "works"... It seems an awfully long time for a package in the "Ubuntu Software Centre" to simply not work.

Any suggestions?  Is there an easy way to install the elder libbfd?  Any other 'quick fix'?

---

### Post by LuisIbanez on 2009-12-12
Just to report that I see the same problem in my Ubuntu 9.10

ggcov
ggcov: error while loading shared libraries: libbfd-2.19.51.20090515.so: cannot open shared object file: No such file or directory

---

