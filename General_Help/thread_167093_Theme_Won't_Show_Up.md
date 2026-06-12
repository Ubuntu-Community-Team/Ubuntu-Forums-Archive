---
title: "Theme Won't Show Up"
date: 2006-04-27
forum: General Help
---

### Post by Harold P on 2006-04-27
This is my input/output.

[B]
harold@ubuntu:~/Desktop/lipstik-2.2$ ls
acinclude.m4  ChangeLog        configure.in.in     lipstik.spec   README
aclocal.m4    config.h.in      COPYING             Makefile.am    stamp-h.in
admin         configure        INSTALL             Makefile.dist  style
AUTHORS       configure.files  lipstik.SlackBuild  Makefile.in    subdirs
BUGS          configure.in     lipstik.slack-desc  NEWS           TODO
harold@ubuntu:~/Desktop/lipstik-2.2$ --prefix=`kde-config --prefix
>
harold@ubuntu:~/Desktop/lipstik-2.2$ ./configure --prefix=`kde-config --prefix
>
harold@ubuntu:~/Desktop/lipstik-2.2$ ./configure --prefix=`kde-config --prefix
>
harold@ubuntu:~/Desktop/lipstik-2.2$ ./configure --prefix=`kde-config --prefix`
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as requested)
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
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wnon-virtual-dtor... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
checking whether g++ supports -Wl,--no-undefined... yes
checking whether g++ supports -Wl,--allow-shlib-undefined... yes
not using lib directory suffix
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking if C++ programs can be compiled... yes
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
checking sys/bitypes.h usability... yes
checking sys/bitypes.h presence... yes
checking for sys/bitypes.h... yes
checking for poll in -lpoll... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking if res_init is available... yes
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for dlopen in -ldl... (cached) yes
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
checking for X... libraries /usr/X11R6/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for perl... /usr/bin/perl
checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
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
checking for mcopidl... /usr/bin/mcopidl
checking for artsc-config... /usr/bin/artsc-config
checking for meinproc... /usr/bin/meinproc
checking for kconfig_compiler... /usr/bin/kconfig_compiler
checking for dcopidlng... /usr/bin/dcopidlng
checking for xmllint... /usr/bin/xmllint
checking if style should be compiled... yes
configure: creating ./config.status
fast creating Makefile
fast creating style/Makefile
fast creating style/config/Makefile
config.pl: fast created 3 file(s).
config.status: creating config.h
config.status: executing depfiles commands

Good - your configure finished. Start make now

harold@ubuntu:~/Desktop/lipstik-2.2$ make
make  all-recursive
make[1]: Entering directory `/home/harold/Desktop/lipstik-2.2'
Making all in style
make[2]: Entering directory `/home/harold/Desktop/lipstik-2.2/style'
Making all in config
make[3]: Entering directory `/home/harold/Desktop/lipstik-2.2/style/config'
/usr/share/qt3/bin/moc ./lipstikconf.h -o lipstikconf.moc
if /bin/sh ../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT lipstikconf.lo -MD -MP -MF ".deps/lipstikconf.Tpo" -c -o lipstikconf.lo lipstikconf.cpp; \
then mv -f ".deps/lipstikconf.Tpo" ".deps/lipstikconf.Plo"; else rm -f ".deps/lipstikconf.Tpo"; exit 1; fi
/usr/share/qt3/include/private/qucom_p.h:69: warning: 'struct QUBuffer' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:77: warning: 'struct QUType' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:104: warning: 'struct QUType_Null' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:287: warning: 'struct QUType_enum' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:307: warning: 'struct QUType_ptr' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:326: warning: 'struct QUType_iface' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:345: warning: 'struct QUType_idisp' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:364: warning: 'struct QUType_bool' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:383: warning: 'struct QUType_int' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:403: warning: 'struct QUType_double' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:423: warning: 'struct QUType_charstar' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:444: warning: 'struct QUType_QString' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:65: warning: 'struct QUType_QVariant' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:87: warning: 'struct QUType_varptr' has virtual functions but non-virtual destructor
/bin/sh ../../libtool --silent --tag=CXX --mode=link g++  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common    -o kstyle_lipstik_config.la -rpath /usr/lib/kde3 -L/usr/X11R6/lib -L/usr/share/qt3/lib -L/usr/lib  -avoid-version -module -no-undefined -Wl,--no-undefined -Wl,--allow-shlib-undefined -R /usr/lib -R /usr/share/qt3/lib -R /usr/X11R6/lib  -module lipstikconf.lo -lkdeui
make[3]: Leaving directory `/home/harold/Desktop/lipstik-2.2/style/config'
make[3]: Entering directory `/home/harold/Desktop/lipstik-2.2/style'
/usr/share/qt3/bin/moc ./lipstik.h -o lipstik.moc
if /bin/sh ../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -DQT_PLUGIN -MT lipstik.lo -MD -MP -MF ".deps/lipstik.Tpo" -c -o lipstik.lo lipstik.cpp; \
then mv -f ".deps/lipstik.Tpo" ".deps/lipstik.Plo"; else rm -f ".deps/lipstik.Tpo"; exit 1; fi
/usr/share/qt3/include/private/qucom_p.h:69: warning: 'struct QUBuffer' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:77: warning: 'struct QUType' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:104: warning: 'struct QUType_Null' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:287: warning: 'struct QUType_enum' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:307: warning: 'struct QUType_ptr' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:326: warning: 'struct QUType_iface' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:345: warning: 'struct QUType_idisp' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:364: warning: 'struct QUType_bool' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:383: warning: 'struct QUType_int' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:403: warning: 'struct QUType_double' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:423: warning: 'struct QUType_charstar' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:444: warning: 'struct QUType_QString' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:65: warning: 'struct QUType_QVariant' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:87: warning: 'struct QUType_varptr' has virtual functions but non-virtual destructor
if /bin/sh ../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -DQT_PLUGIN -MT misc.lo -MD -MP -MF ".deps/misc.Tpo" -c -o misc.lo misc.cpp; \
then mv -f ".deps/misc.Tpo" ".deps/misc.Plo"; else rm -f ".deps/misc.Tpo"; exit 1; fi
/bin/sh ../libtool --silent --tag=CXX --mode=link g++  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -DQT_PLUGIN   -o lipstik.la -rpath /usr/lib/kde3/plugins/styles -L/usr/X11R6/lib -L/usr/share/qt3/lib -L/usr/lib  -avoid-version -module -no-undefined -Wl,--no-undefined -Wl,--allow-shlib-undefined -R /usr/lib -R /usr/share/qt3/lib -R /usr/X11R6/lib  -module lipstik.lo misc.lo -lkdefx
make[3]: Leaving directory `/home/harold/Desktop/lipstik-2.2/style'
make[2]: Leaving directory `/home/harold/Desktop/lipstik-2.2/style'
make[2]: Entering directory `/home/harold/Desktop/lipstik-2.2'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/harold/Desktop/lipstik-2.2'
make[1]: Leaving directory `/home/harold/Desktop/lipstik-2.2'
harold@ubuntu:~/Desktop/lipstik-2.2$ sudo make install
Password:
Making install in style
make[1]: Entering directory `/home/harold/Desktop/lipstik-2.2/style'
Making install in config
make[2]: Entering directory `/home/harold/Desktop/lipstik-2.2/style/config'
make[3]: Entering directory `/home/harold/Desktop/lipstik-2.2/style/config'
test -z "/usr/lib/kde3" || mkdir -p -- "/usr/lib/kde3"
 /bin/sh ../../libtool --silent --mode=install /usr/bin/install -c -p  'kstyle_lipstik_config.la' '/usr/lib/kde3/kstyle_lipstik_config.la'
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kde3
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/harold/Desktop/lipstik-2.2/style/config'
make[2]: Leaving directory `/home/harold/Desktop/lipstik-2.2/style/config'
make[2]: Entering directory `/home/harold/Desktop/lipstik-2.2/style'
make[3]: Entering directory `/home/harold/Desktop/lipstik-2.2/style'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/apps/kdisplay/color-schemes" || mkdir -p -- "/usr/share/apps/kdisplay/color-schemes"
 /usr/bin/install -c -p -m 644 'lipstikstandard.kcsrc' '/usr/share/apps/kdisplay/color-schemes/lipstikstandard.kcsrc'
 /usr/bin/install -c -p -m 644 'lipstikwhite.kcsrc' '/usr/share/apps/kdisplay/color-schemes/lipstikwhite.kcsrc'
 /usr/bin/install -c -p -m 644 'lipstiknoble.kcsrc' '/usr/share/apps/kdisplay/color-schemes/lipstiknoble.kcsrc'
test -z "/usr/lib/kde3/plugins/styles" || mkdir -p -- "/usr/lib/kde3/plugins/styles"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c -p  'lipstik.la' '/usr/lib/kde3/plugins/styles/lipstik.la'
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kde3/plugins/styles
test -z "/usr/share/apps/kstyle/themes" || mkdir -p -- "/usr/share/apps/kstyle/themes"
 /usr/bin/install -c -p -m 644 'lipstik.themerc' '/usr/share/apps/kstyle/themes/lipstik.themerc'
make[3]: Leaving directory `/home/harold/Desktop/lipstik-2.2/style'
make[2]: Leaving directory `/home/harold/Desktop/lipstik-2.2/style'
make[1]: Leaving directory `/home/harold/Desktop/lipstik-2.2/style'
make[1]: Entering directory `/home/harold/Desktop/lipstik-2.2'
make[2]: Entering directory `/home/harold/Desktop/lipstik-2.2'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/harold/Desktop/lipstik-2.2'
make[1]: Leaving directory `/home/harold/Desktop/lipstik-2.2'
harold@ubuntu:~/Desktop/lipstik-2.2$     
[/B]
I think I've done everything right, correct? It's not showing up in kthememanager. Any help?


Thanks,
hp

---

### Post by ComplexNumber on 2006-04-27
its not a theme. its a style. look in styles instead.

---

### Post by Harold P on 2006-04-27
Oops... :oops:

---

### Post by ComplexNumber on 2006-04-27
so did you find it?

---

### Post by Harold P on 2006-04-27
Yeah. I was misled to think it was a theme because kde-looks has it under Theme/styles. Dumb me! :-# 

Thanks,
Harold

---

### Post by ComplexNumber on 2006-04-27
[quote=Harold P]Yeah. I was misled to think it was a theme because kde-looks has it under Theme/styles. Dumb me! :-# 

Thanks,
Harold[/quote] thats ok :). its an easy mistake to make, and one that many do make. the theme-manager-themes are the actual themes (ie click [here]("http://www.kde-look.org/index.php?xcontentmode=8"). the others you see in the theme/styles section are the style engines). each of those theme manager themes makes use of a  style engine, window decoration, icons, background wallpaper, and colour scheme (and sometimes a screensaver). when you install a theme manager theme, it assumes that you have all the relevant components (ie style, icon, window decoration, etc) already installed. if any one component is missing, it will use the current one (eg the current icons etc)

---

### Post by Harold P on 2006-04-27
[QUOTE=ComplexNumber]thats ok :). its an easy mistake to make, and one that many do make. the theme-manager-themes are the actual themes (ie click [here]("http://www.kde-look.org/index.php?xcontentmode=8"). the others you see in the theme/styles section are the style engines). each of those theme manager themes makes use of a  style engine, window decoration, icons, background wallpaper, and colour scheme (and sometimes a screensaver). when you install a theme manager theme, it assumes that you have all the relevant components (ie style, icon, window decoration, etc) already installed. if any one component is missing, it will use the current one (eg the current icons etc)[/QUOTE]

That REALLY helps clear things up. It was very confusing at first not finding the new theme (even thought it wasn't a theme...). I can't wait to start customizing!

Have a nice day,
Harold

---

### Post by ComplexNumber on 2006-04-27
when you install a theme manager theme, you want to look for the 'kth' file. you can either double click on it to install it, or you can install it via the kde control centre in the theme manger themes section. unfortunately, it often doesn't tell you exactly what components(ie window decorations, style, icons, etc) that it makes use of, so one doesn't always know what components to install before installing the theme manager theme. however, some do. as an example, have a look at [this]("http://www.kde-look.org/content/show.php?content=34396") one called Titianium. if you click on the link to the download and install instructions, it says:

> PREREQUISITES[LIST]
[*]Style: [QtCurve V6]("http://www.kde-look.org/content/show.php?content=5065")
[*]Window Decoration: [Crystal]("http://www.kde-look.org/content/show.php?content=13969")
[*]Icons: [Vista-Inspirate]("http://www.kde-look.org/content/show.php?content=31585")[/LIST] therefore,  you know to install these before installing the theme manager theme so that it looks as it is intended. you already have the crystal icons because kde uses these by default, so there's no need to install them. the style engine and the icons do need installing though.
hope this helps.

---

### Post by linuxa on 2006-05-01
[QUOTE=ComplexNumber]when you install a theme manager theme, you want to look for the 'kth' file. [/QUOTE]

Where do you happen to get your themes from? I'm having a hard time trying to get themes (or conversions of) for Kubuntu that will work with the Theme Manager.

The Ubuntu related downloads for themes off [http://www.kde-look.org](http://www.kde-look.org) seems to be deb's. Is it safe to just ran them?

---

### Post by ComplexNumber on 2006-05-01
[quote=linuxa]Where do you happen to get your themes from? I'm having a hard time trying to get themes (or conversions of) for Kubuntu that will work with the Theme Manager.

The Ubuntu related downloads for themes off [http://www.kde-look.org]("http://www.kde-look.org") seems to be deb's. Is it safe to just ran them?[/quote]
yup, thats where i get mine from. but i install from source (even though half of the kde windecs and  kde style engines simply refuse to compile). if you use kubuntu and they're debs, you can install them from the command lijne by running dpkg (oe something like that).


what do you mean by this because i don't quite understand exactly:
> I'm having a hard time trying to get themes (or conversions of) for Kubuntu that will work with the Theme Manager.
why won't they work and in what way?

---

### Post by linuxa on 2006-05-04
[quote=ComplexNumber]yup, thats where i get mine from. but i install from source (even though half of the kde windecs and  kde style engines simply refuse to compile). if you use kubuntu and they're debs, you can install them from the command lijne by running dpkg (oe something like that).


what do you mean by this because i don't quite understand exactly:
.
why won't they work and in what way?[/quote]

Because they are .debs, the Theme manager won't recognize them as valid input files. I think you were right on the mark with the fact the Theme Manager only accepting .kth files.

I thought about a deb install with dpkg, but was unsure of the results e.g. what happens if it fails and only partially installs. 

Baah, I guess I had wanted the brainless "click next, next, next" window way of installing :P

But yeah, going with a deb is no problem. If it messes up, I'll just restore my default theme using Theme Manager.

---

### Post by linuxa on 2006-05-11
I am curios to know where the themes are stored though?

In other words, without Theme Manager, how would I go about restore a particular theme via the command line?

---

