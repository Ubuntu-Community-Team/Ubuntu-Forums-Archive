---
title: "Trying to get f-spot 0.1.11"
date: 2006-04-09
forum: General Help
---

### Post by Rebeca on 2006-04-09
I was trying to get [f-spot 0.1.11](http://f-spot.org/Download) (It's a tar.bz2 file. Apparently, Dapper users have access to it in synaptic, but it isn't there for Breezy. So, I have f-spot 0.1.3 at the moment.) and I was using some ideas I found at the f-spot mailing list in which a user had tried to do [a similar thing](http://www.archivesat.com/post148172.htm) before, but I'm stuck in one of the last steps - since there seems to be a conflict with the gtk-sharp version I have, and I don't want to mess this up, so I need some ideas on what to do.

Here are the last two commands I used and their results:

```
root@ubuntu:/usr/src/f-spot # cd f-spot-0.1.11
root@ubuntu:/usr/src/f-spot/f-spot-0.1.11 # ./configure; make; make check
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.21... 0.34.1 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
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
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototy pes
checking what language compliance flags to pass to the C compiler...
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... yes (version 2.8.3)
checking for mono... /usr/bin/mono
checking for mcs... /usr/bin/mcs
checking for mono.pc... found
checking for Mono.Data.SqliteClient.dll... found
checking for Mono.Posix.dll... found
checking for System.Runtime.Remoting.dll... found
checking for System.Web.dll... found
checking for System.Web.Services.dll... found
checking pkg-config is at least version 0.9.0... yes
checking for F... configure: error: Package requirements (libgnome-2.0 >= 2.2 li bgnomeui-2.0 >= 2.2 libexif >= 0.5.7 libexif < 0.7.0 gtkhtml-sharp-2.0 >= 2.7 gc onf-sharp-2.0 >= 2.7 glade-sharp-2.0 >= 2.7 gnome-vfs-sharp-2.0 >= 2.7 gtk+-2.0 >= 2.6 mono >= 1.1.7 dbus-sharp >= 0.23) were not met:

Requested 'gtkhtml-sharp-2.0 >= 2.7' but version of Gtkhtml is 2.3.92

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables F_CFLAGS
and F_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `check'.  Stop.
```

Help?

---

### Post by Ramses de Norre on 2006-04-09
sudo apt-get install g77
Then run ./configure again and check which errors remain.

---

### Post by Rebeca on 2006-04-09
ok. I opened terminal and I did as you said, then I opened my other window and runned ./configure again (from root@ubuntu:/usr/src/f-spot/f-spot-0.1.11 #) and I still have the same errors.

```

root@ubuntu:/usr/src/f-spot/f-spot-0.1.11 # ./configure; make; make check
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.21... 0.34.1 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yeschecking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yeschecking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yeschecking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 static flag -static works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yeschecking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler...
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... yes (version 2.8.3)
checking for mono... /usr/bin/mono
checking for mcs... /usr/bin/mcs
checking for mono.pc... found
checking for Mono.Data.SqliteClient.dll... found
checking for Mono.Posix.dll... found
checking for System.Runtime.Remoting.dll... found
checking for System.Web.dll... found
checking for System.Web.Services.dll... found
checking pkg-config is at least version 0.9.0... yes
checking for F... configure: error: Package requirements (libgnome-2.0 >= 2.2 libgnomeui-2.0 >= 2.2 libexif >= 0.5.7 libexif < 0.7.0 gtkhtml-sharp-2.0 >= 2.7 gconf-sharp-2.0 >= 2.7 glade-sharp-2.0 >= 2.7 gnome-vfs-sharp-2.0 >= 2.7 gtk+-2.0>= 2.6 mono >= 1.1.7 dbus-sharp >= 0.23) were not met:

Requested 'gtkhtml-sharp-2.0 >= 2.7' but version of Gtkhtml is 2.3.92

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables F_CFLAGS
and F_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `check'.  Stop.

```

---

### Post by Ramses de Norre on 2006-04-09
sudo apt-get install gtkhtml3.8 libgtkhtml3.8-15 libgtkhtml3.8-dev libgtkhtml-dev gtkhtml

---

### Post by Celerex on 2006-04-09
I was about to say you need to make sure these dependancies are met:

libgnome-2.0 >= 2.2
libgnomeui-2.0 >= 2.2
libexif >= 0.5.7
libexif < 0.7.0
gtkhtml-sharp-2.0 >= 2.7
gconf-sharp-2.0 >= 2.7
glade-sharp-2.0 >= 2.7
gnome-vfs-sharp-2.0 >= 2.7
gtk+-2.0>= 2.6
mono >= 1.1.7
dbus-sharp >= 0.23

and give a possible breakdown of which ones you really do need to install but i think I was beat to the punch.

---

### Post by Rebeca on 2006-04-09
```
[username]@ubuntu:~$ sudo apt-get install gtkhtml3.8 libgtkhtml3.8-15 libgtkhtml3.8-dev libgtkhtml-dev gtkhtml
Password:
Reading package lists... Done
Building dependency tree... Done
gtkhtml3.8 is already the newest version.
libgtkhtml3.8-15 is already the newest version.
The following extra packages will be installed:
  bonobo gconf gdk-imlib1 gdk-imlib1-dev gnome-bin gnome-libs-data imlib-base
  indent libart-dev libart2 libbonobo2 libcapplet1 libdb3-dev libefs1
  libgail-dev libgal-dev libgal23 libgconf11 libgdk-pixbuf-dev
  libgdk-pixbuf-gnome-dev libgdk-pixbuf-gnome2 libghttp1 libglade-gnome0
  libglade-gnome0-dev libglade0 libglade0-dev libglib1.2-dev libgnome-dev
  libgnome32 libgnomeprint-bin libgnomeprint-data libgnomeprint-dev
  libgnomeprint15 libgnomeprint2.2-dev libgnomeprintui2.2-dev libgnomesupport0
  libgnomeui32 libgnorba-dev libgnorba27 libgnorbagtk0 libgtk1.2-dev
  libgtkhtml-data libgtkhtml1.1-3 liboaf0 liborbit-dev liborbit0 libwrap0-dev
  libxml-dev libxml1 oaf
Suggested packages:
  nfs-common imlib-progs gnome-core db3-doc libgail-doc glade libglib1.2-doc
  libgtkxmhtml-dev libzvt-dev gnome-common gsfonts-other libgtk1.2-doc
Recommended packages:
  imlib1 imlib2 libgal-data orbit
The following NEW packages will be installed:
  bonobo gconf gdk-imlib1 gdk-imlib1-dev gnome-bin gnome-libs-data gtkhtml
  imlib-base indent libart-dev libart2 libbonobo2 libcapplet1 libdb3-dev
  libefs1 libgail-dev libgal-dev libgal23 libgconf11 libgdk-pixbuf-dev
  libgdk-pixbuf-gnome-dev libgdk-pixbuf-gnome2 libghttp1 libglade-gnome0
  libglade-gnome0-dev libglade0 libglade0-dev libglib1.2-dev libgnome-dev
  libgnome32 libgnomeprint-bin libgnomeprint-data libgnomeprint-dev
  libgnomeprint15 libgnomeprint2.2-dev libgnomeprintui2.2-dev libgnomesupport0
  libgnomeui32 libgnorba-dev libgnorba27 libgnorbagtk0 libgtk1.2-dev
  libgtkhtml-data libgtkhtml-dev libgtkhtml1.1-3 libgtkhtml3.8-dev liboaf0
  liborbit-dev liborbit0 libwrap0-dev libxml-dev libxml1 oaf
0 upgraded, 53 newly installed, 0 to remove and 0 not upgraded.
Need to get 9857kB of archives.
After unpacking 39.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://security.ubuntu.com breezy-security/main libgdk-pixbuf-gnome2 0.22.0-8ubuntu0.1 [6952B]
Get:2 http://archive.ubuntu.com breezy/main imlib-base 1.9.14-16.2ubuntu4 [120kB]
Get:3 http://security.ubuntu.com breezy-security/main libgdk-pixbuf-dev 0.22.0-8ubuntu0.1 [148kB]
Get:4 http://archive.ubuntu.com breezy/main libglib1.2-dev 1.2.10-10ubuntu1 [156kB]
Get:5 http://security.ubuntu.com breezy-security/main libgdk-pixbuf-gnome-dev 0.22.0-8ubuntu0.1 [7556B]
Get:6 http://archive.ubuntu.com breezy/main libgtk1.2-dev 1.2.10-17build1 [1147kB]
Get:7 http://archive.ubuntu.com breezy/main gdk-imlib1 1.9.14-16.2ubuntu4 [91.8kB]
Get:8 http://archive.ubuntu.com breezy/main libart2 1.4.2-20 [49.3kB]
Get:9 http://archive.ubuntu.com breezy/main libgnomesupport0 1.4.2-20 [25.4kB]
Get:10 http://archive.ubuntu.com breezy/main libgnomeui32 1.4.2-20 [432kB]
Get:11 http://archive.ubuntu.com breezy/main liborbit0 0.5.17-11.1 [179kB]
Get:12 http://archive.ubuntu.com breezy/main libgnorba27 1.4.2-20 [54.3kB]
Get:13 http://archive.ubuntu.com breezy/main libgnorbagtk0 1.4.2-20 [44.4kB]
Get:14 http://archive.ubuntu.com breezy/main gnome-bin 1.4.2-20 [93.1kB]
Get:15 http://archive.ubuntu.com breezy/main gnome-libs-data 1.4.2-20 [60.5kB]
Get:16 http://archive.ubuntu.com breezy/main libgnome32 1.4.2-20 [79.8kB]
Get:17 http://archive.ubuntu.com breezy/main libxml1 1:1.8.17-10 [220kB]
Get:18 http://archive.ubuntu.com breezy/main libgnomeprint-bin 0.37-5 [27.4kB]
Get:19 http://archive.ubuntu.com breezy/main libgnomeprint-data 0.37-5 [210kB]
Get:20 http://archive.ubuntu.com breezy/main libgnomeprint15 0.37-5 [224kB]
Get:21 http://archive.ubuntu.com breezy/main liboaf0 0.6.10-3 [67.8kB]
Get:22 http://archive.ubuntu.com breezy/main oaf 0.6.10-3 [121kB]
Get:23 http://archive.ubuntu.com breezy/main libbonobo2 1.0.22-2.3build1 [308kB]Get:24 http://archive.ubuntu.com breezy/main libefs1 1.0.22-2.3build1 [68.9kB]
Get:25 http://archive.ubuntu.com breezy/main bonobo 1.0.22-2.3build1 [154kB]
Get:26 http://archive.ubuntu.com breezy/main libgconf11 1.0.9-7ubuntu1 [102kB]
Get:27 http://archive.ubuntu.com breezy/main gconf 1.0.9-7ubuntu1 [66.8kB]
Get:28 http://archive.ubuntu.com breezy/main gdk-imlib1-dev 1.9.14-16.2ubuntu4 [75.0kB]
Get:29 http://archive.ubuntu.com breezy/universe libcapplet1 1:1.5.11-7 [46.2kB]Get:30 http://archive.ubuntu.com breezy/main libglade0 1:0.17-3 [58.9kB]
Get:31 http://archive.ubuntu.com breezy/main libglade-gnome0 1:0.17-3 [43.7kB]
Get:32 http://archive.ubuntu.com breezy/universe libgal23 0.24-1.4ubuntu1 [492kB]
Get:33 http://archive.ubuntu.com breezy/universe libghttp1 1.0.9-15 [18.9kB]
Get:34 http://archive.ubuntu.com breezy/universe libgtkhtml1.1-3 1.1.10-4ubuntu1 [252kB]
Get:35 http://archive.ubuntu.com breezy/universe libgtkhtml-data 1.1.10-4ubuntu1 [156kB]
Get:36 http://archive.ubuntu.com breezy/universe gtkhtml 1.1.10-4ubuntu1 [185kB]Get:37 http://archive.ubuntu.com breezy/main indent 2.2.9-6 [102kB]
Get:38 http://archive.ubuntu.com breezy/main libart-dev 1.4.2-20 [46.0kB]
Get:39 http://archive.ubuntu.com breezy/main libdb3-dev 3.2.9-22ubuntu1 [293kB]
Get:40 http://archive.ubuntu.com breezy/main libgail-dev 1.8.5-0ubuntu2 [80.1kB]Get:41 http://archive.ubuntu.com breezy/main libgnorba-dev 1.4.2-20 [35.1kB]
Get:42 http://archive.ubuntu.com breezy/main libwrap0-dev 7.6.dbs-8 [32.5kB]
Get:43 http://archive.ubuntu.com breezy/main liborbit-dev 0.5.17-11.1 [390kB]
Get:44 http://archive.ubuntu.com breezy/main libgnome-dev 1.4.2-20 [570kB]
Get:45 http://archive.ubuntu.com breezy/main libxml-dev 1:1.8.17-10 [372kB]
Get:46 http://archive.ubuntu.com breezy/main libgnomeprint-dev 0.37-5 [265kB]
Get:47 http://archive.ubuntu.com breezy/main libglade0-dev 1:0.17-3 [110kB]
Get:48 http://archive.ubuntu.com breezy/main libglade-gnome0-dev 1:0.17-3 [40.0kB]
Get:49 http://archive.ubuntu.com breezy/universe libgal-dev 0.24-1.4ubuntu1 [738kB]
Get:50 http://archive.ubuntu.com breezy/main libgnomeprint2.2-dev 2.12.1-0ubuntu1 [299kB]
Get:51 http://archive.ubuntu.com breezy/main libgnomeprintui2.2-dev 2.12.1-0ubuntu1 [181kB]
Get:52 http://archive.ubuntu.com breezy/universe libgtkhtml-dev 1.1.10-4ubuntu1 [374kB]
Get:53 http://archive.ubuntu.com breezy/main libgtkhtml3.8-dev 3.8.1-0ubuntu1 [338kB]
Fetched 9857kB in 1m22s (119kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
Selecting previously deselected package imlib-base.
(Reading database ... 82038 files and directories currently installed.)
Unpacking imlib-base (from .../imlib-base_1.9.14-16.2ubuntu4_all.deb) ...
Selecting previously deselected package libglib1.2-dev.
Unpacking libglib1.2-dev (from .../libglib1.2-dev_1.2.10-10ubuntu1_i386.deb) ...Selecting previously deselected package libgtk1.2-dev.
Unpacking libgtk1.2-dev (from .../libgtk1.2-dev_1.2.10-17build1_i386.deb) ...
Selecting previously deselected package gdk-imlib1.
Unpacking gdk-imlib1 (from .../gdk-imlib1_1.9.14-16.2ubuntu4_i386.deb) ...
Selecting previously deselected package libart2.
Unpacking libart2 (from .../libart2_1.4.2-20_i386.deb) ...
Selecting previously deselected package libgnomesupport0.
Unpacking libgnomesupport0 (from .../libgnomesupport0_1.4.2-20_i386.deb) ...
Selecting previously deselected package libgnomeui32.
Unpacking libgnomeui32 (from .../libgnomeui32_1.4.2-20_i386.deb) ...
Selecting previously deselected package liborbit0.
Unpacking liborbit0 (from .../liborbit0_0.5.17-11.1_i386.deb) ...
Selecting previously deselected package libgnorba27.
Unpacking libgnorba27 (from .../libgnorba27_1.4.2-20_i386.deb) ...
Selecting previously deselected package libgnorbagtk0.
Unpacking libgnorbagtk0 (from .../libgnorbagtk0_1.4.2-20_i386.deb) ...
Selecting previously deselected package gnome-bin.
Unpacking gnome-bin (from .../gnome-bin_1.4.2-20_i386.deb) ...
Selecting previously deselected package gnome-libs-data.
Unpacking gnome-libs-data (from .../gnome-libs-data_1.4.2-20_all.deb) ...
Selecting previously deselected package libgnome32.
Unpacking libgnome32 (from .../libgnome32_1.4.2-20_i386.deb) ...
Selecting previously deselected package libxml1.
Unpacking libxml1 (from .../libxml1_1%3a1.8.17-10_i386.deb) ...
Selecting previously deselected package libgnomeprint-bin.
Unpacking libgnomeprint-bin (from .../libgnomeprint-bin_0.37-5_i386.deb) ...
Selecting previously deselected package libgnomeprint-data.
Unpacking libgnomeprint-data (from .../libgnomeprint-data_0.37-5_all.deb) ...
Selecting previously deselected package libgnomeprint15.
Unpacking libgnomeprint15 (from .../libgnomeprint15_0.37-5_i386.deb) ...
Selecting previously deselected package liboaf0.
Unpacking liboaf0 (from .../liboaf0_0.6.10-3_i386.deb) ...
Selecting previously deselected package oaf.
Unpacking oaf (from .../archives/oaf_0.6.10-3_i386.deb) ...
Selecting previously deselected package libbonobo2.
Unpacking libbonobo2 (from .../libbonobo2_1.0.22-2.3build1_i386.deb) ...
Selecting previously deselected package libefs1.
Unpacking libefs1 (from .../libefs1_1.0.22-2.3build1_i386.deb) ...
Selecting previously deselected package bonobo.
Unpacking bonobo (from .../bonobo_1.0.22-2.3build1_i386.deb) ...
Selecting previously deselected package libgconf11.
Unpacking libgconf11 (from .../libgconf11_1.0.9-7ubuntu1_i386.deb) ...
Selecting previously deselected package gconf.
Unpacking gconf (from .../gconf_1.0.9-7ubuntu1_i386.deb) ...
Selecting previously deselected package gdk-imlib1-dev.
Unpacking gdk-imlib1-dev (from .../gdk-imlib1-dev_1.9.14-16.2ubuntu4_i386.deb) ...
Selecting previously deselected package libcapplet1.
Unpacking libcapplet1 (from .../libcapplet1_1%3a1.5.11-7_i386.deb) ...
Selecting previously deselected package libgdk-pixbuf-gnome2.
Unpacking libgdk-pixbuf-gnome2 (from .../libgdk-pixbuf-gnome2_0.22.0-8ubuntu0.1_i386.deb) ...
Selecting previously deselected package libglade0.
Unpacking libglade0 (from .../libglade0_1%3a0.17-3_i386.deb) ...
Selecting previously deselected package libglade-gnome0.
Unpacking libglade-gnome0 (from .../libglade-gnome0_1%3a0.17-3_i386.deb) ...
Selecting previously deselected package libgal23.
Unpacking libgal23 (from .../libgal23_0.24-1.4ubuntu1_i386.deb) ...
Selecting previously deselected package libghttp1.
Unpacking libghttp1 (from .../libghttp1_1.0.9-15_i386.deb) ...
Selecting previously deselected package libgtkhtml1.1-3.
Unpacking libgtkhtml1.1-3 (from .../libgtkhtml1.1-3_1.1.10-4ubuntu1_i386.deb) ...
Selecting previously deselected package libgtkhtml-data.
Unpacking libgtkhtml-data (from .../libgtkhtml-data_1.1.10-4ubuntu1_all.deb) ...Selecting previously deselected package gtkhtml.
Unpacking gtkhtml (from .../gtkhtml_1.1.10-4ubuntu1_i386.deb) ...
Selecting previously deselected package indent.
Unpacking indent (from .../indent_2.2.9-6_i386.deb) ...
Selecting previously deselected package libart-dev.
Unpacking libart-dev (from .../libart-dev_1.4.2-20_i386.deb) ...
Selecting previously deselected package libdb3-dev.
Unpacking libdb3-dev (from .../libdb3-dev_3.2.9-22ubuntu1_i386.deb) ...
Selecting previously deselected package libgail-dev.
Unpacking libgail-dev (from .../libgail-dev_1.8.5-0ubuntu2_i386.deb) ...
Selecting previously deselected package libgnorba-dev.
Unpacking libgnorba-dev (from .../libgnorba-dev_1.4.2-20_i386.deb) ...
Selecting previously deselected package libwrap0-dev.
Unpacking libwrap0-dev (from .../libwrap0-dev_7.6.dbs-8_i386.deb) ...
Selecting previously deselected package liborbit-dev.
Unpacking liborbit-dev (from .../liborbit-dev_0.5.17-11.1_i386.deb) ...
Selecting previously deselected package libgnome-dev.
Unpacking libgnome-dev (from .../libgnome-dev_1.4.2-20_i386.deb) ...
Selecting previously deselected package libgdk-pixbuf-dev.
Unpacking libgdk-pixbuf-dev (from .../libgdk-pixbuf-dev_0.22.0-8ubuntu0.1_i386.deb) ...
Selecting previously deselected package libgdk-pixbuf-gnome-dev.
Unpacking libgdk-pixbuf-gnome-dev (from .../libgdk-pixbuf-gnome-dev_0.22.0-8ubuntu0.1_i386.deb) ...
Selecting previously deselected package libxml-dev.
Unpacking libxml-dev (from .../libxml-dev_1%3a1.8.17-10_i386.deb) ...
Selecting previously deselected package libgnomeprint-dev.
Unpacking libgnomeprint-dev (from .../libgnomeprint-dev_0.37-5_i386.deb) ...
Selecting previously deselected package libglade0-dev.
Unpacking libglade0-dev (from .../libglade0-dev_1%3a0.17-3_i386.deb) ...
Selecting previously deselected package libglade-gnome0-dev.
Unpacking libglade-gnome0-dev (from .../libglade-gnome0-dev_1%3a0.17-3_i386.deb) ...
Selecting previously deselected package libgal-dev.
Unpacking libgal-dev (from .../libgal-dev_0.24-1.4ubuntu1_i386.deb) ...
Selecting previously deselected package libgnomeprint2.2-dev.
Unpacking libgnomeprint2.2-dev (from .../libgnomeprint2.2-dev_2.12.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgnomeprintui2.2-dev.
Unpacking libgnomeprintui2.2-dev (from .../libgnomeprintui2.2-dev_2.12.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgtkhtml-dev.
Unpacking libgtkhtml-dev (from .../libgtkhtml-dev_1.1.10-4ubuntu1_i386.deb) ...
Selecting previously deselected package libgtkhtml3.8-dev.
Unpacking libgtkhtml3.8-dev (from .../libgtkhtml3.8-dev_3.8.1-0ubuntu1_i386.deb) ...
Setting up imlib-base (1.9.14-16.2ubuntu4) ...

Setting up libglib1.2-dev (1.2.10-10ubuntu1) ...
Setting up libgtk1.2-dev (1.2.10-17build1) ...
Setting up gdk-imlib1 (1.9.14-16.2ubuntu4) ...

Setting up libart2 (1.4.2-20) ...

Setting up liborbit0 (0.5.17-11.1) ...

Setting up libgnorbagtk0 (1.4.2-20) ...

Setting up libxml1 (1.8.17-10) ...

Setting up liboaf0 (0.6.10-3) ...

Setting up oaf (0.6.10-3) ...
Setting up libefs1 (1.0.22-2.3build1) ...

Setting up gdk-imlib1-dev (1.9.14-16.2ubuntu4) ...
Setting up libglade0 (0.17-3) ...

Setting up libghttp1 (1.0.9-15) ...

Setting up indent (2.2.9-6) ...

Setting up libart-dev (1.4.2-20) ...
Setting up libdb3-dev (3.2.9-22ubuntu1) ...
Setting up libgail-dev (1.8.5-0ubuntu2) ...
Setting up libwrap0-dev (7.6.dbs-8) ...
Setting up liborbit-dev (0.5.17-11.1) ...

Setting up libgdk-pixbuf-dev (0.22.0-8ubuntu0.1) ...
Setting up libxml-dev (1.8.17-10) ...

Setting up libglade0-dev (0.17-3) ...

Setting up libgnomeprint2.2-dev (2.12.1-0ubuntu1) ...
Setting up libgnomeprintui2.2-dev (2.12.1-0ubuntu1) ...
Setting up libgtkhtml3.8-dev (3.8.1-0ubuntu1) ...
Setting up gconf (1.0.9-7ubuntu1) ...

Setting up libgconf11 (1.0.9-7ubuntu1) ...

Setting up libgtkhtml-data (1.1.10-4ubuntu1) ...
Setting up gnome-libs-data (1.4.2-20) ...

Setting up libgnomesupport0 (1.4.2-20) ...

Setting up libgnome32 (1.4.2-20) ...

Setting up libgnomeui32 (1.4.2-20) ...

Setting up libgnorba27 (1.4.2-20) ...

Setting up gnome-bin (1.4.2-20) ...

Setting up libgnomeprint-bin (0.37-5) ...
Setting up libgnomeprint-data (0.37-5) ...

Setting up libgnomeprint15 (0.37-5) ...
Setting up libbonobo2 (1.0.22-2.3build1) ...

Setting up bonobo (1.0.22-2.3build1) ...
Setting up libcapplet1 (1.5.11-7) ...
Setting up libgdk-pixbuf-gnome2 (0.22.0-8ubuntu0.1) ...
Setting up libglade-gnome0 (0.17-3) ...

Setting up libgal23 (0.24-1.4ubuntu1) ...

Setting up libgtkhtml1.1-3 (1.1.10-4ubuntu1) ...

Setting up gtkhtml (1.1.10-4ubuntu1) ...
Setting up libgnorba-dev (1.4.2-20) ...
Setting up libgnome-dev (1.4.2-20) ...
Setting up libgdk-pixbuf-gnome-dev (0.22.0-8ubuntu0.1) ...
Setting up libgnomeprint-dev (0.37-5) ...
Setting up libglade-gnome0-dev (0.17-3) ...
Setting up libgal-dev (0.24-1.4ubuntu1) ...
Setting up libgtkhtml-dev (1.1.10-4ubuntu1) ...

```

Is that enough information? How do I get libgnome-2.2 (and the other needed things)? (I didn't see libgnome 2.2 in synaptic.)

---

### Post by Celerex on 2006-04-09
well you installed a bunch of stuff. Try the ./configure again

(as a note, when doing this instead of using ./configure ; make ; make install I'd personally using ./configure && make && make install. The && means if a command fails the following commands will not be executed)

---

### Post by Rebeca on 2006-04-09
```

root@ubuntu:/usr/src/f-spot/f-spot-0.1.11 # ./configure && make && make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.21... 0.34.1 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 static flag -static works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler...
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... yes (version 2.8.3)
checking for mono... /usr/bin/mono
checking for mcs... /usr/bin/mcs
checking for mono.pc... found
checking for Mono.Data.SqliteClient.dll... found
checking for Mono.Posix.dll... found
checking for System.Runtime.Remoting.dll... found
checking for System.Web.dll... found
checking for System.Web.Services.dll... found
checking pkg-config is at least version 0.9.0... yes
checking for F... configure: error: Package requirements (libgnome-2.0 >= 2.2 libgnomeui-2.0 >= 2.2 libexif >= 0.5.7 libexif < 0.7.0 gtkhtml-sharp-2.0 >= 2.7 gconf-sharp-2.0 >= 2.7 glade-sharp-2.0 >= 2.7 gnome-vfs-sharp-2.0 >= 2.7 gtk+-2.0 >= 2.6 mono >= 1.1.7 dbus-sharp >= 0.23) were not met:

Requested 'gtkhtml-sharp-2.0 >= 2.7' but version of Gtkhtml is 2.3.92

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables F_CFLAGS
and F_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I still have several dependencies not met.

---

