---
title: "How to install f4l"
date: 2011-07-22
forum: General Help
---

### Post by kexanie on 2011-07-22
Now I've got a f4l-0.2.1.tar.bz2 from [http://f4l.sourceforge.net/](http://f4l.sourceforge.net/)
When I extract it,and enter the directory "f4l-0.2.1".
I type this:
```
cd f4l-0.2.1
```however ,when input
```
./configure
```it shows
```
bash: ./configure: No such file or directory
```when
```
make
```shows
```

cd src/flagStonePort/transform-cxx-bsd/transform/ && make -f Makefile 
make[1]: Entering directory `/home/kexanie/Desktop/f4l-0.2.1/src/flagStonePort/transform-cxx-bsd/transform'
g++ -c -pipe -g -fPIC -w -D_REENTRANT -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o FSButtonEvent.o FSButtonEvent.cpp
In file included from FSButtonEvent.h:34:0,
                 from FSButtonEvent.cpp:22:
FSVector.h:35:17: fatal error: new.h: No such file or directory
compilation terminated.
make[1]: *** [FSButtonEvent.o] Error 1
make[1]: Leaving directory `/home/kexanie/Desktop/f4l-0.2.1/src/flagStonePort/transform-cxx-bsd/transform'
make: *** [sub-src-flagStonePort-transform-cxx-bsd-transform-make_default] Error 2

```what does "new.h: No such file or directory" means ?
Could anybody tell me why ?
or show me how to install a flash editor in Ubuntu 

P.S. "kexanie" is my user name.and I extract it to Desktop

---

### Post by cryptictalk on 2011-10-15
Hi,

I dont know how to fix this but I am having the same issue.

I have downloaded the source tar-ball from SourceForge, extracted and when I run 'make' within the source directory I get the same error.

The file "FSVector.h" is including the file "new.h" but it does not exist (I have checked the entire source tree, its no where...)

Does anyone have any advice ideas how we can go about fixing this?

---

