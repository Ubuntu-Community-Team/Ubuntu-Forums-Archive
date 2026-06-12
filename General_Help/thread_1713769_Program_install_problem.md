---
title: "Program install problem"
date: 2011-03-24
forum: General Help
---

### Post by dwoodyatt on 2011-03-24
I'm trying to install qtstalker-0.36 on Ubuntu 10.10. When I "make" i get the following:
cd lib && make -f Makefile
make[1]: Entering directory `/home/don/Desktop/src/qtstalker-0.36/lib'
g++ -c -pipe -g -ffast-math -Wall -W -O0 -D_REENTRANT -fPIC  -DQT_NO_COMPAT -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_NO_DEBUG -I/usr/share/qt3/mkspecs/default -I. -I/usr/local/include/ta-lib -I/usr/include/qt3 -o QuotePlugin.o QuotePlugin.cpp
In file included from DBIndex.h:27,
                 from QuotePlugin.h:35,
                 from QuotePlugin.cpp:22:
DBBase.h:26: fatal error: db.h: No such file or directory
compilation terminated.
make[1]: *** [QuotePlugin.o] Error 1
make[1]: Leaving directory `/home/don/Desktop/src/qtstalker-0.36/lib'
make: *** [sub-lib] Error 2
_________________________________
I'm new to linux and I don't understand what it is telling me,

---

