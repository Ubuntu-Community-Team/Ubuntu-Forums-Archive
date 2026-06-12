---
title: "Kricketscoreboard"
date: 2010-02-05
forum: General Help
---

### Post by lammergeir on 2010-02-05
Hi, I'm trying to install Kricketscoreboard and I get the following in terminal: 

checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
appending configuration tag "GCJ" to libtool
checking if gcj supports -fno-rtti -fno-exceptions... (cached) no
checking for gcj option to produce PIC... -fPIC
checking if gcj PIC flag -fPIC works... no
checking if gcj supports -c -o file.o... no
checking whether the gcj linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... socklen_t
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking for poll in -lpoll... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking if res_init is available... yes
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for dlopen in -ldl... yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking sizeof size_t == sizeof unsigned long... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... libraries /usr/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking if Qt compiles without flags... yes
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... libraries /usr/lib, headers /usr/include/kde
checking if UIC has KDE plugins available... yes
checking for KDE paths... defaults
checking for dcopidl... /usr/bin/dcopidl
checking for dcopidl2cpp... /usr/bin/dcopidl2cpp
checking for mcopidl... not found
configure: error: The important program mcopidl was not found!
Please check whether you installed aRts correctly.

terry@terry-desktop:~/Desktop/kricketscoreboard-1.1$ ^C
terry@terry-desktop:~/Desktop/kricketscoreboard-1.1$ ./configure --without-arts checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wnon-virtual-dtor... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
not using lib directory suffix
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... 
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
checking for egrep... grep -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... no
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
appending configuration tag "GCJ" to libtool
checking if gcj supports -fno-rtti -fno-exceptions... (cached) no
checking for gcj option to produce PIC... -fPIC
checking if gcj PIC flag -fPIC works... no
checking if gcj supports -c -o file.o... no
checking whether the gcj linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... socklen_t
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking for poll in -lpoll... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking if res_init is available... yes
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for dlopen in -ldl... yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking sizeof size_t == sizeof unsigned long... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... libraries /usr/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking if Qt compiles without flags... yes
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... libraries /usr/lib, headers /usr/include/kde
checking if UIC has KDE plugins available... yes
checking for KDE paths... defaults
checking for dcopidl... /usr/bin/dcopidl
checking for dcopidl2cpp... /usr/bin/dcopidl2cpp
checking for kde-config... /usr/bin/kde-config
checking for meinproc... /usr/bin/meinproc
checking whether byte ordering is bigendian... no
checking for MAXPATHLEN... 4096
checking if doc should be compiled... yes
checking if kricketscoreboard should be compiled... yes
checking if po should be compiled... yes
configure: creating ./config.status
fast creating Makefile
fast creating doc/Makefile
fast creating doc/en/Makefile
fast creating kricketscoreboard/Makefile
fast creating po/Makefile
config.status: creating config.h
config.status: executing depfiles commands

Good - your configure finished. Start make now

terry@terry-desktop:~/Desktop/kricketscoreboard-1.1$ make
cd . && /bin/bash ./config.status Makefile 
fast creating Makefile
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: Entering directory `/home/terry/Desktop/kricketscoreboard-1.1'
Making all in doc
make[2]: Entering directory `/home/terry/Desktop/kricketscoreboard-1.1/doc'
cd .. && /bin/bash ./config.status doc/Makefile 
fast creating doc/Makefile
make[2]: Leaving directory `/home/terry/Desktop/kricketscoreboard-1.1/doc'
make[2]: Entering directory `/home/terry/Desktop/kricketscoreboard-1.1/doc'
Making all in en
make[3]: Entering directory `/home/terry/Desktop/kricketscoreboard-1.1/doc/en'
cd ../.. && /bin/bash ./config.status doc/en/Makefile 
fast creating doc/en/Makefile
make[3]: Leaving directory `/home/terry/Desktop/kricketscoreboard-1.1/doc/en'
make[3]: Entering directory `/home/terry/Desktop/kricketscoreboard-1.1/doc/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/terry/Desktop/kricketscoreboard-1.1/doc/en'
make[3]: Entering directory `/home/terry/Desktop/kricketscoreboard-1.1/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/terry/Desktop/kricketscoreboard-1.1/doc'
make[2]: Leaving directory `/home/terry/Desktop/kricketscoreboard-1.1/doc'
Making all in kricketscoreboard
make[2]: Entering directory `/home/terry/Desktop/kricketscoreboard-1.1/kricketscoreboard'
cd .. && /bin/bash ./config.status kricketscoreboard/Makefile depfiles
fast creating kricketscoreboard/Makefile
config.status: executing depfiles commands
make[2]: Leaving directory `/home/terry/Desktop/kricketscoreboard-1.1/kricketscoreboard'
make[2]: Entering directory `/home/terry/Desktop/kricketscoreboard-1.1/kricketscoreboard'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.  -I/usr/include/kde -I/usr/share/qt3/include -I.  -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT printoptions.o -MD -MP -MF ".deps/printoptions.Tpo" \
	  -c -o printoptions.o `test -f 'printoptions.cpp' || echo './'`printoptions.cpp; \
	then mv -f ".deps/printoptions.Tpo" ".deps/printoptions.Po"; \
	else rm -f ".deps/printoptions.Tpo"; exit 1; \
	fi
In file included from /usr/share/qt3/include/qwindowdefs.h:47,
                 from /usr/share/qt3/include/qwidget.h:45,
                 from printoptions.h:19,
                 from printoptions.cpp:16:
/usr/share/qt3/include/qstring.h: In member function ‘char QChar::latin1() const’:
/usr/share/qt3/include/qstring.h:197: warning: conversion to ‘char’ from ‘int’ may alter its value
/usr/share/qt3/include/qstring.h: In member function ‘void QChar::setCell(uchar)’:
/usr/share/qt3/include/qstring.h:222: warning: conversion to ‘ushort’ from ‘int’ may alter its value
/usr/share/qt3/include/qstring.h: In member function ‘void QChar::setRow(uchar)’:
/usr/share/qt3/include/qstring.h:223: warning: conversion to ‘ushort’ from ‘int’ may alter its value
/usr/share/qt3/include/qstring.h: In constructor ‘QChar::QChar(uchar, uchar)’:
/usr/share/qt3/include/qstring.h:267: warning: conversion to ‘ushort’ from ‘int’ may alter its value
/usr/share/qt3/include/qstring.h: In constructor ‘QStringData::QStringData(QChar*, uint, uint)’:
/usr/share/qt3/include/qstring.h:365: warning: conversion to ‘unsigned int:30’ from ‘uint’ may alter its value
/usr/share/qt3/include/qstring.h:365: warning: conversion to ‘unsigned int:30’ from ‘uint’ may alter its value
In file included from /usr/share/qt3/include/qobject.h:48,
                 from /usr/share/qt3/include/qwidget.h:46,
                 from printoptions.h:19,
                 from printoptions.cpp:16:
/usr/share/qt3/include/qevent.h: In constructor ‘QContextMenuEvent::QContextMenuEvent(QContextMenuEvent::Reason, const QPoint&, const QPoint&, int)’:
/usr/share/qt3/include/qevent.h:432: warning: conversion to ‘unsigned char’ from ‘uint’ may alter its value
/usr/share/qt3/include/qevent.h: In member function ‘void QDropEvent::setAction(QDropEvent::Action)’:
/usr/share/qt3/include/qevent.h:523: warning: conversion to ‘unsigned char’ from ‘uint’ may alter its value
In file included from player.h:22,
                 from team.h:22,
                 from match.h:24,
                 from printoptions.h:34,
                 from printoptions.cpp:16:
batsman.h: At global scope:
batsman.h:36: warning: type qualifiers ignored on function return type
batsman.h:37: warning: type qualifiers ignored on function return type
batsman.h:40: warning: type qualifiers ignored on function return type
batsman.h:41: warning: type qualifiers ignored on function return type
batsman.h:42: warning: type qualifiers ignored on function return type
batsman.h:43: warning: type qualifiers ignored on function return type
In file included from match.h:27,
                 from printoptions.h:34,
                 from printoptions.cpp:16:
innings.h:42: warning: type qualifiers ignored on function return type
innings.h: In member function ‘float Innings::getRunRate() const’:
innings.h:44: warning: conversion to ‘float’ from ‘double’ may alter its value
In file included from runratestats.h:30,
                 from mainform.h:33,
                 from printoptions.h:37,
                 from printoptions.cpp:16:
graphwidget.h: In member function ‘void graphWidget::setScale(int, int)’:
graphwidget.h:73: warning: conversion to ‘float’ from ‘int’ may alter its value
graphwidget.h:73: warning: conversion to ‘float’ from ‘int’ may alter its value
graphwidget.h: In member function ‘void graphWidget::setMaxXY(int, int)’:
graphwidget.h:74: warning: conversion to ‘float’ from ‘int’ may alter its value
graphwidget.h:74: warning: conversion to ‘float’ from ‘int’ may alter its value
printoptions.cpp: In member function ‘void printOptions::printWidget(QWidget*, QPainter&)’:
printoptions.cpp:281: error: ‘floor’ was not declared in this scope
make[2]: *** [printoptions.o] Error 1
make[2]: Leaving directory `/home/terry/Desktop/kricketscoreboard-1.1/kricketscoreboard'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/terry/Desktop/kricketscoreboard-1.1'
make: *** [all] Error 2
terry@terry-desktop:~/Desktop/kricketscoreboard-1.1$ sudo make install
[sudo] password for terry: 
Making install in doc
make[1]: Entering directory `/home/terry/Desktop/kricketscoreboard-1.1/doc'
Making install in en
make[2]: Entering directory `/home/terry/Desktop/kricketscoreboard-1.1/doc/en'
make[3]: Entering directory `/home/terry/Desktop/kricketscoreboard-1.1/doc/en'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/terry/Desktop/kricketscoreboard-1.1/doc/en'
make[2]: Leaving directory `/home/terry/Desktop/kricketscoreboard-1.1/doc/en'
make[2]: Entering directory `/home/terry/Desktop/kricketscoreboard-1.1/doc'
make[3]: Entering directory `/home/terry/Desktop/kricketscoreboard-1.1/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/terry/Desktop/kricketscoreboard-1.1/doc'
make[2]: Leaving directory `/home/terry/Desktop/kricketscoreboard-1.1/doc'
make[1]: Leaving directory `/home/terry/Desktop/kricketscoreboard-1.1/doc'
Making install in kricketscoreboard
make[1]: Entering directory `/home/terry/Desktop/kricketscoreboard-1.1/kricketscoreboard'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.  -I/usr/include/kde -I/usr/share/qt3/include -I.  -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT printoptions.o -MD -MP -MF ".deps/printoptions.Tpo" \
	  -c -o printoptions.o `test -f 'printoptions.cpp' || echo './'`printoptions.cpp; \
	then mv -f ".deps/printoptions.Tpo" ".deps/printoptions.Po"; \
	else rm -f ".deps/printoptions.Tpo"; exit 1; \
	fi
In file included from /usr/share/qt3/include/qwindowdefs.h:47,
                 from /usr/share/qt3/include/qwidget.h:45,
                 from printoptions.h:19,
                 from printoptions.cpp:16:
/usr/share/qt3/include/qstring.h: In member function ‘char QChar::latin1() const’:
/usr/share/qt3/include/qstring.h:197: warning: conversion to ‘char’ from ‘int’ may alter its value
/usr/share/qt3/include/qstring.h: In member function ‘void QChar::setCell(uchar)’:
/usr/share/qt3/include/qstring.h:222: warning: conversion to ‘ushort’ from ‘int’ may alter its value
/usr/share/qt3/include/qstring.h: In member function ‘void QChar::setRow(uchar)’:
/usr/share/qt3/include/qstring.h:223: warning: conversion to ‘ushort’ from ‘int’ may alter its value
/usr/share/qt3/include/qstring.h: In constructor ‘QChar::QChar(uchar, uchar)’:
/usr/share/qt3/include/qstring.h:267: warning: conversion to ‘ushort’ from ‘int’ may alter its value
/usr/share/qt3/include/qstring.h: In constructor ‘QStringData::QStringData(QChar*, uint, uint)’:
/usr/share/qt3/include/qstring.h:365: warning: conversion to ‘unsigned int:30’ from ‘uint’ may alter its value
/usr/share/qt3/include/qstring.h:365: warning: conversion to ‘unsigned int:30’ from ‘uint’ may alter its value
In file included from /usr/share/qt3/include/qobject.h:48,
                 from /usr/share/qt3/include/qwidget.h:46,
                 from printoptions.h:19,
                 from printoptions.cpp:16:
/usr/share/qt3/include/qevent.h: In constructor ‘QContextMenuEvent::QContextMenuEvent(QContextMenuEvent::Reason, const QPoint&, const QPoint&, int)’:
/usr/share/qt3/include/qevent.h:432: warning: conversion to ‘unsigned char’ from ‘uint’ may alter its value
/usr/share/qt3/include/qevent.h: In member function ‘void QDropEvent::setAction(QDropEvent::Action)’:
/usr/share/qt3/include/qevent.h:523: warning: conversion to ‘unsigned char’ from ‘uint’ may alter its value
In file included from player.h:22,
                 from team.h:22,
                 from match.h:24,
                 from printoptions.h:34,
                 from printoptions.cpp:16:
batsman.h: At global scope:
batsman.h:36: warning: type qualifiers ignored on function return type
batsman.h:37: warning: type qualifiers ignored on function return type
batsman.h:40: warning: type qualifiers ignored on function return type
batsman.h:41: warning: type qualifiers ignored on function return type
batsman.h:42: warning: type qualifiers ignored on function return type
batsman.h:43: warning: type qualifiers ignored on function return type
In file included from match.h:27,
                 from printoptions.h:34,
                 from printoptions.cpp:16:
innings.h:42: warning: type qualifiers ignored on function return type
innings.h: In member function ‘float Innings::getRunRate() const’:
innings.h:44: warning: conversion to ‘float’ from ‘double’ may alter its value
In file included from runratestats.h:30,
                 from mainform.h:33,
                 from printoptions.h:37,
                 from printoptions.cpp:16:
graphwidget.h: In member function ‘void graphWidget::setScale(int, int)’:
graphwidget.h:73: warning: conversion to ‘float’ from ‘int’ may alter its value
graphwidget.h:73: warning: conversion to ‘float’ from ‘int’ may alter its value
graphwidget.h: In member function ‘void graphWidget::setMaxXY(int, int)’:
graphwidget.h:74: warning: conversion to ‘float’ from ‘int’ may alter its value
graphwidget.h:74: warning: conversion to ‘float’ from ‘int’ may alter its value
printoptions.cpp: In member function ‘void printOptions::printWidget(QWidget*, QPainter&)’:
printoptions.cpp:281: error: ‘floor’ was not declared in this scope
make[1]: *** [printoptions.o] Error 1
make[1]: Leaving directory `/home/terry/Desktop/kricketscoreboard-1.1/kricketscoreboard'
make: *** [install-recursive] Error 1
GRateful for any help.

---

