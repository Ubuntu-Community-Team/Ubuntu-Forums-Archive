---
title: "Nothing will compile"
date: 2006-01-20
forum: General Help
---

### Post by jpfinley on 2006-01-20
Anytime I go through the usual process of:

./configure
make
make install

I never get any farther than the configuration.  I always end up with this error: ```
john@aux:~/Desktop/grubconf-0.5.1$ make
make: *** No targets specified and no makefile found.  Stop.

```

Is there anyone out there who can tell me how to fix this or why this is happening?  I have 'build-essential'.

I have searched [so]("http://ubuntuforums.org/showthread.php?t=119392&highlight=targets+makefile+found") [many]("http://ubuntuforums.org/showthread.php?t=112847&highlight=targets+makefile+found") threads that get to this problem and fizzle out.  Can we solve this thing this time? Please?

---

### Post by Rule on 2006-01-20
you need to install the build-essential package.

---

### Post by jpfinley on 2006-01-20
Like I said, I already have buildiessential.  Synaptic says I have version 11.1 installed.  I also have both depending packages libc6-dev and libc-dev.

---

### Post by Sef on 2006-01-20
> Is there anyone out there who can tell me how to fix this or why this is happening? I have 'build-essential'.

Since you got build-essential, I have a couple of questions for you.

A) Do you untar the package?

B) Do you change to the directory where the submenu where the package has been opened?

From Psychocats.net:

> tar -xvzf obscure-1.0.tar.gz
cd obscure-1.0
./configure
make
sudo make install

[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

Edit:  Possibly build-essential did not install correctly.  So remove and reinstall it.

---

### Post by jpfinley on 2006-01-20
Sef,

I am using that very site as a reference for installing software.  I'm almost positive that my typing is correct.  Here's what I'm doing:
```
john@aux:~$ cd Desktop
john@aux:~/Desktop$ tar -xvzf grubconf-0.5.1.tar.gz
grubconf-0.5.1/
grubconf-0.5.1/Makefile.in
grubconf-0.5.1/README
grubconf-0.5.1/stamp-h.in
grubconf-0.5.1/ABOUT-NLS
grubconf-0.5.1/AUTHORS
grubconf-0.5.1/COPYING
grubconf-0.5.1/ChangeLog
grubconf-0.5.1/INSTALL
grubconf-0.5.1/Makefile.am
grubconf-0.5.1/NEWS
grubconf-0.5.1/TODO
grubconf-0.5.1/acconfig.h
grubconf-0.5.1/acinclude.m4
grubconf-0.5.1/aclocal.m4
grubconf-0.5.1/config.guess
grubconf-0.5.1/config.h.in
grubconf-0.5.1/config.sub
grubconf-0.5.1/configure
grubconf-0.5.1/configure.in
grubconf-0.5.1/grubconf.desktop.in
grubconf-0.5.1/install-sh
grubconf-0.5.1/ltmain.sh
grubconf-0.5.1/missing
grubconf-0.5.1/mkinstalldirs
grubconf-0.5.1/grubconf.8
grubconf-0.5.1/xmldocs.make
grubconf-0.5.1/omf.make
grubconf-0.5.1/intl/
grubconf-0.5.1/intl/ChangeLog
grubconf-0.5.1/intl/Makefile.in
grubconf-0.5.1/intl/config.charset
grubconf-0.5.1/intl/locale.alias
grubconf-0.5.1/intl/ref-add.sin
grubconf-0.5.1/intl/ref-del.sin
grubconf-0.5.1/intl/gettext.h
grubconf-0.5.1/intl/gettextP.h
grubconf-0.5.1/intl/hash-string.h
grubconf-0.5.1/intl/libgnuintl.h
grubconf-0.5.1/intl/libgettext.h
grubconf-0.5.1/intl/loadinfo.h
grubconf-0.5.1/intl/bindtextdom.c
grubconf-0.5.1/intl/dcgettext.c
grubconf-0.5.1/intl/dgettext.c
grubconf-0.5.1/intl/gettext.c
grubconf-0.5.1/intl/finddomain.c
grubconf-0.5.1/intl/loadmsgcat.c
grubconf-0.5.1/intl/localealias.c
grubconf-0.5.1/intl/textdomain.c
grubconf-0.5.1/intl/l10nflist.c
grubconf-0.5.1/intl/explodename.c
grubconf-0.5.1/intl/dcigettext.c
grubconf-0.5.1/intl/dcngettext.c
grubconf-0.5.1/intl/dngettext.c
grubconf-0.5.1/intl/ngettext.c
grubconf-0.5.1/intl/plural.y
grubconf-0.5.1/intl/localcharset.c
grubconf-0.5.1/intl/intl-compat.c
grubconf-0.5.1/intl/plural.c
grubconf-0.5.1/intl/VERSION
grubconf-0.5.1/po/
grubconf-0.5.1/po/ChangeLog
grubconf-0.5.1/po/Makefile.in.in
grubconf-0.5.1/po/POTFILES.in
grubconf-0.5.1/po/grubconf.pot
grubconf-0.5.1/include/
grubconf-0.5.1/include/Makefile.in
grubconf-0.5.1/include/Makefile.am
grubconf-0.5.1/include/callbacks.h
grubconf-0.5.1/include/interface.h
grubconf-0.5.1/include/support.h
grubconf-0.5.1/include/grubconf_global.h
grubconf-0.5.1/include/grubconf_os_list.h
grubconf-0.5.1/include/grubconf_dev.h
grubconf-0.5.1/include/partitioning.h
grubconf-0.5.1/macros/
grubconf-0.5.1/macros/Makefile.in
grubconf-0.5.1/macros/ChangeLog
grubconf-0.5.1/macros/Makefile.am
grubconf-0.5.1/macros/compiler-flags.m4
grubconf-0.5.1/macros/curses.m4
grubconf-0.5.1/macros/gnome-common.m4
grubconf-0.5.1/macros/gnome-cxx-check.m4
grubconf-0.5.1/macros/gnome-gettext.m4
grubconf-0.5.1/macros/gnome-pthread-check.m4
grubconf-0.5.1/macros/gnome-x-checks.m4
grubconf-0.5.1/macros/linger.m4
grubconf-0.5.1/macros/check-utmp.m4
grubconf-0.5.1/macros/gnome-pkgconfig.m4
grubconf-0.5.1/macros/gnome-platform.m4
grubconf-0.5.1/macros/autogen.sh
grubconf-0.5.1/src/
grubconf-0.5.1/src/Makefile.in
grubconf-0.5.1/src/Makefile.am
grubconf-0.5.1/src/main.c
grubconf-0.5.1/src/callbacks.c
grubconf-0.5.1/src/support.c
grubconf-0.5.1/src/interface.c
grubconf-0.5.1/src/grubconf_global.c
grubconf-0.5.1/src/grubconf_os_list.c
grubconf-0.5.1/src/grubconf_dev.c
grubconf-0.5.1/src/partitioning.c
grubconf-0.5.1/pixmaps/
grubconf-0.5.1/pixmaps/Makefile.in
grubconf-0.5.1/pixmaps/Makefile.am
grubconf-0.5.1/pixmaps/grubconf-app.png
grubconf-0.5.1/pixmaps/grubconf.png
grubconf-0.5.1/help/
grubconf-0.5.1/help/Makefile.in
grubconf-0.5.1/help/Makefile.am
grubconf-0.5.1/help/C/
grubconf-0.5.1/help/C/Makefile.in
grubconf-0.5.1/help/C/Makefile.am
grubconf-0.5.1/help/C/legal.xml
grubconf-0.5.1/help/C/grubconf.xml
grubconf-0.5.1/help/C/grubconf-C.omf
grubconf-0.5.1/help/C/figures/
grubconf-0.5.1/help/C/figures/color.png
grubconf-0.5.1/help/C/figures/general.png
grubconf-0.5.1/help/C/figures/os.png
john@aux:~/Desktop$ cd grubconf-0.5.1
john@aux:~/Desktop/grubconf-0.5.1$ ./configure
loading cache ./config.cache
checking for non-GNU ld... /usr/bin/X11/ld
checking if the linker (/usr/bin/X11/ld) is GNU ld... yes
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for strerror in -lcposix... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for Cygwin environment... no
checking for mingw32 environment... no
checking host system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/X11/ld
checking if the linker (/usr/bin/X11/ld) is GNU ld... yes
checking for /usr/bin/X11/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for object suffix... o
checking for executable suffix... no
checking command to parse /usr/bin/nm -B output... ok
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/X11/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for pkg-config... /usr/bin/pkg-config
checking for libgnomeui-2.0 gtk+-2.0... john@aux:~/Desktop/grubconf-0.5.1$ make
make: *** No targets specified and no makefile found.  Stop.

```

---

### Post by mo_x on 2006-01-21
It is often not necessay to compile programs yourself. Try this command:
sudo apt-get install grubconf
If you do want to compile it yourself, did you install development files for gnome and gtk?

---

### Post by jpfinley on 2006-01-21
Thanks, mo x.  Believe me, if I could get away without ever compiling, I would.

That command tells me that it can't find the grubconf package.  Could you please elaborate on the development packages in question?

---

### Post by mo_x on 2006-01-21
I think grubconf is in the universe repository. You need to modify the /etc/apt/sources.list and uncomment the appropriate lines. Then execute the following command:
sudo apt-get update
Now try again the command to install grubconf.
You can also use synaptic to install programs. I think it is in the menu, someting like "Add/Remove Software" (use KDE myself)

---

### Post by jpfinley on 2006-01-21
My sources.list contains universe - I think.  I have attached a copy.

install grubconf still returns the same error.  And I still don't know why I can't compile anything, which, to me is a bigger problem.

---

### Post by slashem on 2006-01-23
You need to install libgnomeui-dev

---

### Post by jpfinley on 2006-01-23
Thanks for the info, slashem!  I will be sure to try this as soon as I get home and report the results.

---

### Post by jpfinley on 2006-01-23
Thanks for the tip! I'm seeing improvement.

./config goes smoothly.

make gives me:```
john@aux:~/Desktop/grubconf-0.5.1$ make
make  all-recursive
make[1]: Entering directory `/home/john/Desktop/grubconf-0.5.1'
Making all in intl
make[2]: Entering directory `/home/john/Desktop/grubconf-0.5.1/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/john/Desktop/grubconf-0.5.1/intl'
Making all in po
make[2]: Entering directory `/home/john/Desktop/grubconf-0.5.1/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/john/Desktop/grubconf-0.5.1/po'
Making all in include
make[2]: Entering directory `/home/john/Desktop/grubconf-0.5.1/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/john/Desktop/grubconf-0.5.1/include'
Making all in macros
make[2]: Entering directory `/home/john/Desktop/grubconf-0.5.1/macros'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/john/Desktop/grubconf-0.5.1/macros'
Making all in src
make[2]: Entering directory `/home/john/Desktop/grubconf-0.5.1/src'
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2 .0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/ gtk-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/libbonob oui-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/inc lude/gnome-keyring-1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/ include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation- 2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/lib/gtk-2.0/include  -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/libxml2      -Wall - Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparenthese s -Wpointer-arith -Wmissing-prototypes   -O1     -g -c main.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2 .0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/ gtk-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/libbonob oui-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/inc lude/gnome-keyring-1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/ include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation- 2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/lib/gtk-2.0/include  -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/libxml2      -Wall - Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparenthese s -Wpointer-arith -Wmissing-prototypes   -O1     -g -c callbacks.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2 .0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/ gtk-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/libbonob oui-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/inc lude/gnome-keyring-1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/ include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation- 2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/lib/gtk-2.0/include  -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/libxml2      -Wall - Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparenthese s -Wpointer-arith -Wmissing-prototypes   -O1     -g -c support.c
support.c: In function ‘my_getline’:
support.c:153: warning: pointer targets in passing argument 2 of ‘getline’ diffe r in signedness
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2 .0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/ gtk-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/libbonob oui-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/inc lude/gnome-keyring-1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/ include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation- 2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/lib/gtk-2.0/include  -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/libxml2      -Wall - Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparenthese s -Wpointer-arith -Wmissing-prototypes   -O1     -g -c interface.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2 .0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/ gtk-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/libbonob oui-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/inc lude/gnome-keyring-1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/ include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation- 2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/lib/gtk-2.0/include  -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/libxml2      -Wall - Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparenthese s -Wpointer-arith -Wmissing-prototypes   -O1     -g -c grubconf_global.c
grubconf_global.c: In function ‘stristr’:
grubconf_global.c:684: warning: pointer targets in assignment differ in signedne ss
grubconf_global.c:692: warning: pointer targets in assignment differ in signedne ss
grubconf_global.c:701: warning: pointer targets in assignment differ in signedne ss
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2 .0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/ gtk-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/libbonob oui-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/inc lude/gnome-keyring-1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/ include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation- 2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/lib/gtk-2.0/include  -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/libxml2      -Wall - Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparenthese s -Wpointer-arith -Wmissing-prototypes   -O1     -g -c grubconf_os_list.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2 .0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/ gtk-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/libbonob oui-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/inc lude/gnome-keyring-1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/ include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation- 2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/lib/gtk-2.0/include  -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/libxml2      -Wall - Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparenthese s -Wpointer-arith -Wmissing-prototypes   -O1     -g -c grubconf_dev.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2 .0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/ gtk-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/libbonob oui-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/inc lude/gnome-keyring-1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/ include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation- 2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/lib/gtk-2.0/include  -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/libxml2      -Wall - Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparenthese s -Wpointer-arith -Wmissing-prototypes   -O1     -g -c partitioning.c
partitioning.c: In function ‘copy_to_part’:
partitioning.c:72: warning: pointer targets in passing argument 1 of ‘copy_to_in t’ differ in signedness
partitioning.c:73: warning: pointer targets in passing argument 1 of ‘copy_to_in t’ differ in signedness
partitioning.c: In function ‘msdos_signature’:
partitioning.c:163: warning: pointer targets in initialization differ in signedn ess
/bin/sh ../libtool --mode=link gcc  -Wall -Wimplicit -Wreturn-type -Wunused -Wsw itch -Wcomment -Wuninitialized -Wparentheses -Wpointer-arith -Wmissing-prototype s        -O1     -g  -o grubconf  main.o callbacks.o support.o interface.o grubc onf_global.o grubconf_os_list.o grubconf_dev.o partitioning.o -Wl,--export-dynam ic -pthread -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnome-keyring -lxml2 -lz -lgno mecanvas-2 -lgnome-2 -lpopt -lart_lgpl_2 -lpangoft2-1.0 -lgnomevfs-2 -lbonobo-2 -lgconf-2 -lbonobo-activation -lORBit-2 -lgthread-2.0 -lgtk-x11-2.0 -lgdk-x11-2. 0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi - lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lXrender -lX11 -lgobject- 2.0 -lgmodule-2.0 -ldl -lglib-2.0
mkdir .libs
gcc -Wall -Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized - Wparentheses -Wpointer-arith -Wmissing-prototypes -O1 -g -o grubconf main.o call backs.o support.o interface.o grubconf_global.o grubconf_os_list.o grubconf_dev. o partitioning.o -Wl,--export-dynamic  /usr/lib/libgnomeui-2.so -L/usr/lib /usr/ lib/libjpeg.so /usr/lib/libbonoboui-2.so -lSM -lICE /usr/lib/libgnome-keyring.so  /usr/lib/libgnomecanvas-2.so /usr/lib/libgnome-2.so /usr/lib/libesd.so /usr/lib /libaudiofile.so /usr/lib/libart_lgpl_2.so /usr/lib/libgnomevfs-2.so /usr/lib/li bxml2.so /usr/lib/libgnutls.so /usr/lib/libtasn1.so /usr/lib/libgcrypt.so -lnsl /usr/lib/libgpg-error.so -lresolv -lrt /usr/lib/libbonobo-2.so /usr/lib/libgconf -2.so /usr/lib/libbonobo-activation.so /usr/lib/libORBitCosNaming-2.so /usr/lib/ libORBit-2.so /usr/lib/libpopt.so /usr/lib/libgthread-2.0.so -lpthread /usr/lib/ libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/lib gdk_pixbuf-2.0.so /usr/lib/libpangocairo-1.0.so /usr/lib/libpangoft2-1.0.so -lXi nerama -lXi -lXrandr -lXext -lXcursor -lXfixes /usr/lib/libpango-1.0.so /usr/lib /libcairo.so -lpng12 -lfontconfig /usr/lib/libfreetype.so -lz -lm -lXrender -lX1 1 /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2. 0.so
make[2]: Leaving directory `/home/john/Desktop/grubconf-0.5.1/src'
Making all in pixmaps
make[2]: Entering directory `/home/john/Desktop/grubconf-0.5.1/pixmaps'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/john/Desktop/grubconf-0.5.1/pixmaps'
Making all in help
make[2]: Entering directory `/home/john/Desktop/grubconf-0.5.1/help'
Making all in C
make[3]: Entering directory `/home/john/Desktop/grubconf-0.5.1/help/C'
for file in grubconf-C.omf; do \
  scrollkeeper-preinstall /usr/share/gnome/help/grubconf/C/grubconf.xml ./$file $file.out; \
done
touch omf_timestamp
make[3]: Leaving directory `/home/john/Desktop/grubconf-0.5.1/help/C'
make[3]: Entering directory `/home/john/Desktop/grubconf-0.5.1/help'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/john/Desktop/grubconf-0.5.1/help'
make[2]: Leaving directory `/home/john/Desktop/grubconf-0.5.1/help'
make[2]: Entering directory `/home/john/Desktop/grubconf-0.5.1'
make[2]: Leaving directory `/home/john/Desktop/grubconf-0.5.1'
make[1]: Leaving directory `/home/john/Desktop/grubconf-0.5.1'
```


and make install gives me:```
john@aux:~/Desktop/grubconf-0.5.1$ make install
Making install in intl
make[1]: Entering directory `/home/john/Desktop/grubconf-0.5.1/intl'
if test "grubconf" = "gettext" \
   && test '' = 'intl-compat.o'; then \
  /bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo  "../.././mkinstalldirs" ;; esac` /usr/lib /usr/include; \
  /usr/bin/install -c -m 644 libintl.h /usr/include/libintl.h; \
  /bin/sh ../libtool --mode=install \
    /usr/bin/install -c -m 644 libintl.a /usr/lib/libintl.a; \
else \
  : ; \
fi
if test 'no' = yes; then \
  /bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo  "../.././mkinstalldirs" ;; esac` /usr/lib; \
  temp=/usr/lib/t-charset.alias; \
  dest=/usr/lib/charset.alias; \
  if test -f /usr/lib/charset.alias; then \
    orig=/usr/lib/charset.alias; \
    sed -f ref-add.sed $orig > $temp; \
    /usr/bin/install -c -m 644 $temp $dest; \
    rm -f $temp; \
  else \
    if test yes = no; then \
      orig=charset.alias; \
      sed -f ref-add.sed $orig > $temp; \
      /usr/bin/install -c -m 644 $temp $dest; \
      rm -f $temp; \
    fi; \
  fi; \
  /bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo  "../.././mkinstalldirs" ;; esac` /usr/share/locale; \
  test -f /usr/share/locale/locale.alias \
    && orig=/usr/share/locale/locale.alias \
    || orig=./locale.alias; \
  temp=/usr/share/locale/t-locale.alias; \
  dest=/usr/share/locale/locale.alias; \
  sed -f ref-add.sed $orig > $temp; \
  /usr/bin/install -c -m 644 $temp $dest; \
  rm -f $temp; \
else \
  : ; \
fi
if test "grubconf" = "gettext"; then \
  /bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo  "../.././mkinstalldirs" ;; esac` /usr/share/gettext/intl; \
  /usr/bin/install -c -m 644 VERSION /usr/share/gettext/intl/VERSION; \
  /usr/bin/install -c -m 644 ChangeLog.inst /usr/share/gettext/intl/ChangeLog; \
  dists="COPYING.LIB-2 COPYING.LIB-2.1 Makefile.in config.charset locale.alias r ef-add.sin ref-del.sin gettext.h gettextP.h hash-string.h libgnuintl.h libgettex t.h loadinfo.h bindtextdom.c dcgettext.c dgettext.c gettext.c finddomain.c loadm sgcat.c localealias.c textdomain.c l10nflist.c explodename.c dcigettext.c dcnget text.c dngettext.c ngettext.c plural.y localcharset.c intl-compat.c"; \
  for file in $dists; do \
    /usr/bin/install -c -m 644 ./$file \
                    /usr/share/gettext/intl/$file; \
  done; \
  chmod a+x /usr/share/gettext/intl/config.charset; \
  dists="plural.c"; \
  for file in $dists; do \
    if test -f $file; then dir=.; else dir=.; fi; \
    /usr/bin/install -c -m 644 $dir/$file \
                    /usr/share/gettext/intl/$file; \
  done; \
  dists="xopen-msg.sed linux-msg.sed po2tbl.sed.in cat-compat.c"; \
  for file in $dists; do \
    rm -f /usr/share/gettext/intl/$file; \
  done; \
else \
  : ; \
fi
make[1]: Leaving directory `/home/john/Desktop/grubconf-0.5.1/intl'
Making install in po
make[1]: Entering directory `/home/john/Desktop/grubconf-0.5.1/po'
/bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo " ../.././mkinstalldirs" ;; esac` /usr/share
/bin/sh: ../.././mkinstalldirs: No such file or directory
make[1]: *** [install-data-yes] Error 127
make[1]: Leaving directory `/home/john/Desktop/grubconf-0.5.1/po'
make: *** [install-recursive] Error 1
john@aux:~/Desktop/grubconf-0.5.1$ 
```

Any idea as to where those errors are originating?

---

### Post by jpfinley on 2006-01-23
Well I must say, I'm very impressed with this forum.  After thinking that the package which I was trying to install was broken, I attempted another program, and the results were beautiful.  Everything just worked like I thought it should.

Thankyou, thankyou, thankyou to all of the people who responded to a newbie 's problem.  I couldn't have done it without this great community.

---

### Post by not_yet on 2006-01-23
try this

sudo make install

---

### Post by jpfinley on 2006-01-23
I still receive the same errors.

---

### Post by slashem on 2006-01-23
I tried and I got those errors too. Anyway, grubconf is compiled in the 'src' directory. Just copy it to /usr/local/bin and you're done.

---

