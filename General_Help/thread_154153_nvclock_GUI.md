---
title: "nvclock GUI"
date: 2006-04-02
forum: General Help
---

### Post by Zer0d on 2006-04-02
When i install nvclock 0.8d i only get the command line version, but i have X installed and so on... Configure output:

```

checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for library containing getopt_long... none required
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.4.0... checking for X... no
checking QTDIR... *** Can't find qt header/library directories, you can fix this using two ways depending on your system:
*** - set QTDIR or use -with-qtdir=DIR option
*** - use --with-qt-includes=DIR or --with-qt-libraries=DIR to set the include/library directory
configure: no X Window System found
configure: creating ./config.status
config.status: creating src/Makefile
config.status: creating src/backend/Makefile
config.status: creating src/nvcontrol/Makefile
config.status: creating src/qt/Makefile
config.status: creating src/gtk/Makefile
config.status: creating Makefile
config.status: creating config.h
config.status: executing default-1 commands

NVClock build summary:
----------------------
- Commandline version enabled
- NV-CONROL support disabled
- GTK2 GUI disabled
- QT GUI disabled


```
What do i install so the configuration script finds my X system... Or how do i install the needed packages?

---

### Post by David Corrales on 2006-04-02
You probably need to install the **dev** (development) versions of some packages. Those contain the necessary headers needed to compile against said libraries.

---

### Post by Zer0d on 2006-04-03
Installed xorg and some gtk2 development packages and now it works :D

---

### Post by beto310 on 2006-11-06
[http://packages.ubuntulinux.org/dapper/x11/nvclock-gtk](http://packages.ubuntulinux.org/dapper/x11/nvclock-gtk) check each package to see if -dev is installed

---

