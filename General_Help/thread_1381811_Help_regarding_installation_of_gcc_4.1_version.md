---
title: "Help regarding installation of gcc 4.1 version"
date: 2010-01-15
forum: General Help
---

### Post by Scholar1987 on 2010-01-15
Hi,

  Can anyone please help me with the steps to install gcc 4.1 version on Ubuntu 9..10. Actually Ubuntu 9.10 version supports gcc 4.4.1

but I want to install gcc 4.1.x version 

Thank you

With regards,
Scofield

---

### Post by mc4man on 2010-01-15
Your free to install the 4.1 gcc, g++ from synaptic or apt-get

---

### Post by Scholar1987 on 2010-01-15
thanks for the reply...

I just want to get the command to install the version of gcc 4.1.x

actually I used this command

$sudo apt-get install gcc-4.1.1

it installed gcc-4.1.1 and gcc-4.1.1-base but when I try to checkout gcc version by giving this command gcc -v it is giving "the package is not installed". wat is the problem?

Is that Ubuntu 9.10 does not support gcc 4.1.1

Please help me out

---

### Post by mc4man on 2010-01-15
> actually I used this command

$sudo apt-get install gcc-4.1.1
Not sure how that actually worked as that isn't the package(s) name, more like
```
sudo apt-get install gcc-4.1 g++-4.1
```
Ex.
> doug@doug-laptop:~$ sudo apt-get install gcc-4.1 g++-4.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  casper libdiscover2 mplayer-skins libdc1394-22-dev squashfs-tools xresprobe
  discover user-setup localechooser-data libraw1394-dev discover-data
  mplayer-nogui discover1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cpp-4.1 gcc-4.1-base libstdc++6-4.1-dev
Suggested packages:
  gcc-4.1-locales g++-4.1-multilib gcc-4.1-doc gcc-4.1-multilib
  libmudflap0-dev libstdc++6-4.1-doc
The following NEW packages will be installed:
  cpp-4.1 g++-4.1 gcc-4.1 gcc-4.1-base libstdc++6-4.1-dev
[0 upgraded, 5 newly installed, 0 to remove and 4 not upgraded.


> giving this command gcc -v it is giving "the package is not installed"

Should return this (proposed is ..4ubuntu9, simile is 8
> doug@doug-laptop:~$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu8' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 

> Is that Ubuntu 9.10 does not support gcc 4.1.1

Well it does, though to use gcc-4.1.X you'll need to specify in a manner appropriate to the source you're building, your 'system default' gcc is 4.4.X and will remain so

EX.
> doug@doug-laptop:~$ gcc-4.1 -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --with-tune=generic --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20080704 (prerelease) (Ubuntu 4.1.2-27ubuntu1)



The only source I have on hand is mplayer and while I wouldn't use 4.1 to show it can be used (several ways to set, some are (in terms of this source and in general
> doug@doug-laptop:~/mplayer1$ export CC=gcc-4.1 
doug@doug-laptop:~/mplayer1$ ./configure
Checking for gcc-4.1 version ... 4.1.3 
Detected operating system: Linux
Detected host architecture: i386
Checking for host cc ... gcc-4.1

or 
> doug@doug-laptop:~/mplayer1$ CC=gcc-4.1 ./configure
Checking for gcc-4.1 version ... 4.1.3 
Detected operating system: Linux
Detected host architecture: i386
Checking for host cc ... gcc-4.1 
ect., ect.

---

### Post by Scholar1987 on 2010-01-16
**Hey I have all these warnings. i am unable to understand wat r these... There are many such warnings during installation. Does this warning mean that Ns-2 does not work**
 
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘ReadImage’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:855: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:921: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:946: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:951: warning: conversion to ‘short unsigned int’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:952: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:981: warning: conversion to ‘char’ from ‘unsigned char’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:982: warning: conversion to ‘char’ from ‘unsigned char’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:983: warning: conversion to ‘char’ from ‘unsigned char’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:985: warning: conversion to ‘char’ from ‘unsigned char’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘GetCode’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1088: warning: conversion to ‘unsigned int’ from ‘int’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1098: warning: conversion to ‘unsigned int’ from ‘int’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1098: warning: conversion to ‘int’ from ‘unsigned int’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘Mread’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1160: warning: conversion to ‘int’ from ‘size_t’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1163: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘CommonWriteGIF’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1482: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1542: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘ReadValue’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1643: warning: conversion to ‘unsigned int’ from ‘int’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1652: warning: conversion to ‘int’ from ‘unsigned int’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘write_block’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1794: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘output’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1826: warning: conversion to ‘unsigned int’ from ‘int’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘rl_flush_clearorrep’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1985: warning: conversion to ‘int’ from ‘unsigned int’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘rl_flush_withtable’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:2012: warning: conversion to ‘int’ from ‘unsigned int’ may change the sign of the result

---

