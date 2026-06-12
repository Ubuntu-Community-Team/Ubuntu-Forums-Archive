---
title: "Installing Rosegarden error failed to find X11 header X11/SM/SMlib.h"
date: 2010-05-08
forum: General Help
---

### Post by hansteam on 2010-05-08
After upgrading to 10.04 I tried to reinstall Rosegarden and wound up with the following output when I ran ./configure:

```
chris@chris-laptop:~/Documents/Code/rosegarden-10.02.1$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking how to run the C++ preprocessor... g++ -E
checking for X... libraries , headers 
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking QTDIR... /usr
checking Qt includes... /usr/include/qt4
checking for moc-qt4... /usr/bin/moc-qt4
checking for uic-qt4... /usr/bin/uic-qt4
checking for rcc-qt4... no
checking for rcc... /usr/bin/rcc
checking for lupdate-qt4... /usr/bin/lupdate-qt4
checking for lrelease-qt4... /usr/bin/lrelease-qt4
checking QTLIBDIR... /usr/lib
checking QT_CXXFLAGS... -I/usr/include/qt4/Qt3Support -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtXml -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtCore -I/usr/include/qt4 -DQT3_SUPPORT
checking QT_LIBS... -L/usr/lib -lQt3Support -lQtGui -lQtXml -lQtNetwork -lQtCore
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking ladspa.h usability... yes
checking ladspa.h presence... yes
checking for ladspa.h... yes
checking X11/SM/SMlib.h usability... no
checking X11/SM/SMlib.h presence... no
checking for X11/SM/SMlib.h... no
configure: error: Failed to find required X11 header X11/SM/SMlib.h

```

I tried reinstalling libx11-dev:

```
chris@chris-laptop:~/Documents/Code/rosegarden-10.02.1$ sudo apt-get install libx11-dev
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libx11-dev is already the newest version.
libx11-dev set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

Any ideas?

---

### Post by hansteam on 2010-05-08
OK, so I found the solution to this problem. I simply ran apt-get install smlib-dev I have a new problem:

```
chris@chris-laptop:~/Documents/Code/rosegarden-10.02.1$ sudo make
Rebuilding dependencies file...
make: Nothing to be done for `all'.

```

---

### Post by scotty64 on 2010-05-09
> **hansteam said:**
> OK, so I found the solution to this problem. I simply ran apt-get install smlib-dev I have a new problem:

```
chris@chris-laptop:~/Documents/Code/rosegarden-10.02.1$ sudo make
Rebuilding dependencies file...
make: Nothing to be done for `all'.

```

You have to start over again in order to get a working build:
make clean
./configure
make
sudo make install


And then :guitar: .....

---

### Post by ciacnorris on 2010-08-13
Same problem as above while building Rosegarden 10.04.2 on Ubuntustudio 10.04 64-bit.

But when i run
apt-get install smlib-dev
it says that smlib-dev package doesn't exist.

Any help?

---

### Post by hansteam on 2010-11-29
I'm not sure if this was the case when I originally posted, but I found with my last installation of Ubuntu that Rosegarden is in the repository so you can just:

```
sudo apt-get install rosegarden
```

It will ask you to install some supporting software for extra functionality.

---

### Post by STEELBAS on 2011-07-27
> **ciacnorris said:**
> Same problem as above while building Rosegarden 10.04.2 on Ubuntustudio 10.04 64-bit.

But when i run
apt-get install smlib-dev
it says that smlib-dev package doesn't exist.

Any help?
Just in case anyone else ever has a problem with "configure: error: Failed to find required X11 header X11/SM/SMlib.h", and doesn't want to use the outdated Rosegarden version in the Ubuntu repo: You need to install "libsm-dev", not "smlib-dev".

Sorry for posting old, but this is the best Google result for the problem.

---

