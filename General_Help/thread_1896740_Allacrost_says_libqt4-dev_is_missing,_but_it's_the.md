---
title: "Allacrost says libqt4-dev is missing, but it's there."
date: 2011-12-17
forum: General Help
---

### Post by drmrgd on 2011-12-17
I thought I would check out Hero Allacrost.  I downloaded the most recent version and tried to compile it.  However, I'm getting the following:

```
dave@CygnusX1:~/My Games/allacrost-1.0.2$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking whether to enable -O3 compiler optimization... yes
checking whether to enable debugging... no
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking whether to enable usage of map editor... yes
checking for Qt4 headers... /usr/include/qt4
checking for Qt4 libraries... no
configure: error: in `/home/dave/My Games/allacrost-1.0.2':
configure: error: Qt4 development libraries not found
See `config.log' for more details
dave@CygnusX1:~/My Games/allacrost-1.0.2$ sudo ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking whether to enable -O3 compiler optimization... yes
checking whether to enable debugging... no
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking whether to enable usage of map editor... yes
checking for Qt4 headers... /usr/include/qt4
checking for Qt4 libraries... no
configure: error: in `/home/dave/My Games/allacrost-1.0.2':
configure: error: Qt4 development libraries not found
See `config.log' for more details

```

But, when I check for the Qt4 development libraries, I can see them:

```
dave@CygnusX1:~/My Games/allacrost-0.1.0$ dpkg -s libqt4-dev
Package: libqt4-dev
Status: install ok installed
Priority: optional
Section: libdevel
Installed-Size: 24944
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Architecture: i386
Source: qt4-x11
Version: 4:4.7.4-0ubuntu8
Replaces: libqt4-opengl-dev (<< 4.4.0-2), libqtwebkit-dev (<< 2.0~)
Depends: libqt4-dbus (= 4:4.7.4-0ubuntu8), libqt4-declarative (= 4:4.7.4-0ubuntu8), libqt4-designer (= 4:4.7.4-0ubuntu8), libqt4-help (= 4:4.7.4-0ubuntu8), libqt4-network (= 4:4.7.4-0ubuntu8), libqt4-qt3support (= 4:4.7.4-0ubuntu8), libqt4-script (= 4:4.7.4-0ubuntu8), libqt4-scripttools (= 4:4.7.4-0ubuntu8), libqt4-sql (= 4:4.7.4-0ubuntu8), libqt4-svg (= 4:4.7.4-0ubuntu8), libqt4-test (= 4:4.7.4-0ubuntu8), libqt4-xml (= 4:4.7.4-0ubuntu8), libqt4-xmlpatterns (= 4:4.7.4-0ubuntu8), libqtcore4 (= 4:4.7.4-0ubuntu8), libqtgui4 (= 4:4.7.4-0ubuntu8), qt4-linguist-tools (= 4:4.7.4-0ubuntu8), qt4-qmake (= 4:4.7.4-0ubuntu8), libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.1.1), zlib1g (>= 1:1.1.4)
Recommends: libqt4-opengl-dev (= 4:4.7.4-0ubuntu8), libqtwebkit-dev (>= 2.0~)
Suggests: libmysqlclient-dev, libpq-dev, libsqlite3-dev, qt4-dev-tools, qt4-doc, unixodbc-dev
Breaks: libqt4-opengl-dev (<< 4.4.0-2), libqtwebkit-dev (<< 2.0~)
Description: Qt 4 development files
 Qt is a cross-platform C++ application framework. Qt's primary feature
 is its rich set of widgets that provide standard GUI functionality.
 .
 This package contains the header development files and development programs
 used for building Qt 4 applications.
Homepage: http://qt.nokia.com/
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>

```

Not sure how to proceed with this one.  Checking the config.log as suggested just basically shows the same thing.  Not sure what I'm missing here.  Any advice on what I need to install to get this working?

---

### Post by lechien73 on 2011-12-17
Hero of Allacrost also uses libqt4-opengl-dev, so maybe those libraries are missing?

---

### Post by drmrgd on 2011-12-17
> **lechien73 said:**
> Hero of Allacrost also uses libqt4-opengl-dev, so maybe those libraries are missing?

Thanks for the help.  I did already check, though, and those libraries seem to be there.  Any other ideas perhaps?

---

