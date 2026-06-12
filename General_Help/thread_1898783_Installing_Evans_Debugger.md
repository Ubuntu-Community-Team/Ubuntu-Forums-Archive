---
title: "Installing Evans Debugger"
date: 2011-12-22
forum: General Help
---

### Post by pl4f0rd on 2011-12-22
Hi

I switched from backtrack to lubuntu because backtrack was causing me too many problems.  I have installed all my required tools apart from one.

I am having some difficulty installing evans debugger. I have followed some tutorials online however i am running into problems.

Upon installation i get an error and am unable to figure it out which is below, if any one could shed some light i would be most grateful

```

/usr/local/src/debugger$ make install
cd src/ && make -f Makefile install
make[1]: Entering directory `/usr/local/src/debugger/src'
g++ -c -pipe -ansi -pedantic -W -Wall -Wno-long-long -Wnon-virtual-dtor -fvisibility=hidden -Wstrict-null-sentinel -O2 -Wall -W -D_REENTRANT -DQT_WEBKIT -DDEFAULT_PLUGIN_PATH=/usr/lib/edb/ -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I../../../../share/qt4/mkspecs/linux-g++ -I. -I../../../../include/qt4/QtCore -I../../../../include/qt4/QtGui -I../../../../include/qt4 -Iwidgets -I../include -Iqhexview -Ios/unix -I../include/os/unix -Iedisassm -Ios/unix/linux -I../include/os/unix/linux -Iarch/i386 -I../include/arch/i386 -I.moc/release-shared -I.uic -o .obj/release-shared/Debugger.o Debugger.cpp
In file included from Debugger.cpp:35:0:
../include/Expression.h:24:30: fatal error: boost/function.hpp: No such file or directory
compilation terminated.
make[1]: *** [.obj/release-shared/Debugger.o] Error 1
make[1]: Leaving directory `/usr/local/src/debugger/src'
make: *** [sub-src-install_subtargets-ordered] Error 2


```

Other than this error lubuntu works amazingly well :P

---

### Post by leopardsaga on 2012-04-09
my problem is:
$ qmake
$ make
cd src/ && make -f Makefile 
make[1]: Entering directory `/home/huanghe/Downloads/debugger/src'
g++ -c -pipe -ansi -pedantic -W -Wall -Wno-long-long -Wnon-virtual-dtor -fvisibility=hidden -Wstrict-null-sentinel -ggdb -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_XML_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtXml -I/usr/include/qt4 -Iwidgets -I../include -Iqhexview -Iqjson -Ios/unix -I../include/os/unix -Iedisassm -Ios/unix/linux -I../include/os/unix/linux -Iarch/i386 -I../include/arch/i386 -I.moc/release-shared -I.uic -o .obj/release-shared/ArchProcessor.o arch/i386/ArchProcessor.cpp
arch/i386/ArchProcessor.cpp:33:55: fatal error: boost/math/special_functions/fpclassify.hpp: No such file or directory
compilation terminated.
make[1]: *** [.obj/release-shared/ArchProcessor.o] Error 1
make[1]: Leaving directory `/home/huanghe/Downloads/debugger/src'
make: *** [sub-src-make_default-ordered] Error 2

---

### Post by leopardsaga on 2012-04-09
Before build edb,
run "sudo apt-get install libboost-all-dev",
this will resolve the lib dependencies.

But after installing,
comes with another problem:
edb can't be launched, the information is "segmentation fault"
wish may help you.

---

