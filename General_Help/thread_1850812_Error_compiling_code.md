---
title: "Error compiling code"
date: 2011-09-27
forum: General Help
---

### Post by newbie_country on 2011-09-27
I have downloaded a zip file (lastools.zip) and am attempting to compile it as per the instructions in the README.txt
when running make I get the following error;

cd laslib && make
make[1]: Entering directory `/home/craig/Downloads/lastools/laslib'
cd src && make
make[2]: Entering directory `/home/craig/Downloads/lastools/laslib/src'
g++  -c -O3 -Wall -Wno-deprecated -DNDEBUG -I/usr/include/ -I../inc -I. lasinterval.cpp -o lasinterval.o
lasinterval.cpp:37:22: fatal error: hash_map.h: No such file or directory
compilation terminated.
make[2]: *** [lasinterval.o] Error 1
make[2]: Leaving directory `/home/craig/Downloads/lastools/laslib/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/craig/Downloads/lastools/laslib'
make: *** [all] Error 2

What is wrong (or rather what am I doing wrong)?

I have a "vanilla" install of ubuntu 11.04.

Thanks in advance.

---

### Post by oldos2er on 2011-09-27
> **newbie_country said:**
> I have downloaded a zip file (lastools.zip) and am attempting to compile it as per the instructions in the README.txt
when running make I get the following error;

cd laslib && make
make[1]: Entering directory `/home/craig/Downloads/lastools/laslib'
cd src && make
make[2]: Entering directory `/home/craig/Downloads/lastools/laslib/src'
g++  -c -O3 -Wall -Wno-deprecated -DNDEBUG -I/usr/include/ -I../inc -I. lasinterval.cpp -o lasinterval.o
lasinterval.cpp:37:22: [COLOR="Red"]fatal error: hash_map.h: No such file or directory[/COLOR]
compilation terminated.
make[2]: *** [lasinterval.o] Error 1
make[2]: Leaving directory `/home/craig/Downloads/lastools/laslib/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/craig/Downloads/lastools/laslib'
make: *** [all] Error 2


The text in red is telling you a dependency is needed. I would run ```
ann@ann-Dell-XPS-410:~$ apt-cache search hash_map
libsparsehash-dev - Google's extremely memory-efficient C++ hash_map implementation
sparsehash - memory-efficient C++ hash_map implementation (transition package)
``` then install the package libsparsehash-dev, then retry 'make'.

---

### Post by newbie_country on 2011-09-27
Thanks for the quick response however I still get the same error.

---

### Post by azmyth on 2011-09-29
I'd try installing one of these packages or both to see if thsi will satisfy your dep issue.

libcvc3-2-dev
libginac-dev

---

