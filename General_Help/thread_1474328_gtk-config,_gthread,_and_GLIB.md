---
title: "gtk-config, gthread, and GLIB"
date: 2010-05-05
forum: General Help
---

### Post by mugetsu37 on 2010-05-05
Alright, so I'm trying to install GDAM on my system, and... I didn't expect it to be this much of a project.

First off, I need to compile it from source, this would not be a problem if it was updated, but the project seems to have been abandoned for the time being. As such, ./configure requires gtk-config. However, as of gtk-2.0, gtk-config has been deprecated in favor of pkg-config. There go a few hours to looking through code and mailing lists. Okay, so I figure I can just trick ./configure into *thinking* it's looking at gtk-config: one mv command later I have a gtk-config, back to ./configure... and get this:

```

checking for GTK - version >= 1.2.5... Package gthread was not found in the pkg-config search path.
Perhaps you should add the directory containing `gthread.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gthread' found
Package gthread was not found in the pkg-config search path.
Perhaps you should add the directory containing `gthread.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gthread' found
no
*** Could not run GTK test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK was incorrectly installed
*** or that you have moved GTK since it was installed. In the latter case, you
*** may want to edit the gtk-config script: /usr/bin/gtk-config
configure: error: Cannot find Gtk - gtk-config missing from path?

```**the reason it references pkg-config (or what I can find, at least) is the ./configure grabs the first word from the script for it's name. Weird, but not the point.

Alright, so did a find for gthread... no dice. Looked it up, it has to do with program threading. So, I move on to my other solution to try: try installing Gtk+-1.2 or earlier somewhere on the computer, see if that's easier. Tracked one down, extract, ./configure, now I need GLIB, the precursor to gtk-config.

But that's okay, I dove right in, took another few hours, found out that I just have to change a few prefixes and enabled some switches, namely: --with-glib=/usr/share/glib-2.0/, which tells ./configure to look for the current version of GLIB. The system type check was giving me some errors too; I decided to ignore them for now. So here we go, ./configure:

```

~/Desktop/gtk+-1.2.10$ sudo ./configure --with-glib=/usr/share/glib-2.0/ --enable-glibtest=no
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking host system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for ranlib... (cached) ranlib
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking whether ln -s works... (cached) yes
loading cache ./config.cache within ltconfig
ltconfig: you must specify a host type if you use `--no-verify'
Try `ltconfig --help' for more information.
checking for object suffix... o
checking for executable suffix... (cached) no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions ... no
checking if gcc static flag -static works... -static
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking command to parse /usr/bin/nm -B output... ok
checking how to hardcode library paths into programs... immediate
checking for /usr/bin/ld option to reload object files... -r
checking dynamic linker characteristics... no
checking if libtool supports shared libraries... no
checking whether to build shared libraries... no
checking whether to build static libraries... yes
checking for objdir... .libs
creating libtool
loading cache ./config.cache
checking whether to enable maintainer-specific portions of Makefiles... no
checking host system type... i686-pc-linux-gnu
checking whether build environment is sane... yes
checking for gcc... (cached) gcc
checking whether the C compiler (gcc -g -O2 ) works... yes
checking whether the C compiler (gcc -g -O2 ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for POSIXized ISC... no
checking for gcc option to accept ANSI C... none needed
checking for a BSD compatible install... /usr/bin/install -c
checking whether make sets ${MAKE}... (cached) yes
checking for gawk... gawk
checking for perl5... no
checking for perl... perl
checking for indent... no
checking whether make is GNU Make... yes
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for working const... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for unistd.h... yes
checking for getpagesize... yes
checking for working mmap... yes
checking for argz.h... yes
checking for limits.h... yes
checking for locale.h... yes
checking for nl_types.h... yes
checking for malloc.h... yes
checking for string.h... yes
checking for unistd.h... (cached) yes
checking for sys/param.h... yes
checking for getcwd... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for strchr... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for stpcpy... yes
checking for LC_MESSAGES... yes
checking whether NLS is requested... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  az ca cs da de el es et eu fi fr ga gl hr hu it ja ko lt nl no nn pl pt pt_BR ro ru sk sl sp sr sv tr uk vi wa zh_CN.GB2312 zh_TW.Big5
checking for extra flags to get ANSI library prototypes... none needed
checking for extra flags for POSIX compliance... none needed
configure: error: GLIB directory (/usr/share/glib-2.0/) not present or not configured

```But this really makes no sense to me. I checked the log, right after the POSIX test there are only two lines:
configure: In function 'main':
configure:4173: warning: unused variable 'dir'
again, no sense to me. I guess I'll fiddle with it again in a while, but until then, anyone have any ideas?

---

