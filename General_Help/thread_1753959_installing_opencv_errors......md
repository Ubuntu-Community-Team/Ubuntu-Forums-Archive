---
title: "installing opencv errors....."
date: 2011-05-09
forum: General Help
---

### Post by kinderen on 2011-05-09
hi everyone,
i have been trying to install opencv, after run ./configure i ran the make file. after running the make check command I got this message:
```
Making check in cxcore
make[1]: Entering directory `/home/vincent/opencv-1.1.0/cxcore'
Making check in src
make[2]: Entering directory `/home/vincent/opencv-1.1.0/cxcore/src'
/bin/bash ../../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../.. -I. -I../../cxcore/include -I../..  -DNDEBUG  -Wall -fno-rtti -pipe -O3 -g -march=i686 -ffast-math -fomit-frame-pointer  -msse2   -MT cxalloc.lo -MD -MP -MF .deps/cxalloc.Tpo -c -o cxalloc.lo cxalloc.cpp
 g++ -DHAVE_CONFIG_H -I. -I../.. -I. -I../../cxcore/include -I../.. -DNDEBUG -Wall -fno-rtti -pipe -O3 -g -march=i686 -ffast-math -fomit-frame-pointer -msse2 -MT cxalloc.lo -MD -MP -MF .deps/cxalloc.Tpo -c cxalloc.cpp  -fPIC -DPIC -o .libs/cxalloc.o
In file included from _cxcore.h:60:0,
                 from cxalloc.cpp:42:
../../cxcore/include/cxmisc.h:133:6: error: #elif with no expression
make[2]: *** [cxalloc.lo] Error 1
make[2]: Leaving directory `/home/vincent/opencv-1.1.0/cxcore/src'
make[1]: *** [check-recursive] Error 1
make[1]: Leaving directory `/home/vincent/opencv-1.1.0/cxcore'
make: *** [check-recursive] Error 1

```what does this mean and what can i do about it? please help...

thanks vince....

---

