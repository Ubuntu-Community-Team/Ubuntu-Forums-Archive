---
title: "manual install of firestarter not working on ubuntu 11.10"
date: 2012-05-06
forum: General Help
---

### Post by RichFox on 2012-05-06
Hi I'm new to the atempting technical things in linux so please forgive my lack of giving pertinent info.

I am attempting to install firestarter 1.0.3 from a tarball onto my pc running ubuntu 11.10 but am unable to ./congigure.

I appreciate that there are faster and easier ways than manually configuring, making etc - but I wish to be able to do it.

Please see below for data from my terminal:

richard@richard-VGN-NR21M-S:~$ cd source
richard@richard-VGN-NR21M-S:~/source$ dir
firestarter-1.0.3
richard@richard-VGN-NR21M-S:~/source$ cd firestarter-1.0.3
richard@richard-VGN-NR21M-S:~/source/firestarter-1.0.3$ dir
aclocal.m4    COPYING		      INSTALL		   mkinstalldirs
AUTHORS       CREDITS		      install-sh	   NEWS
autogen.sh    fedora.init	      intltool-extract.in  pixmaps
ChangeLog     firestarter.console     intltool-merge.in    po
config.guess  firestarter.desktop     intltool-update.in   README
config.h.in   firestarter.desktop.in  libtool		   scripts
config.log    firestarter.pam	      ltmain.sh		   src
config.sub    firestarter.schemas.in  Makefile.am	   stamp-h.in
configure     firestarter.spec	      Makefile.in	   TODO
configure.in  firestarter.spec.in     missing
richard@richard-VGN-NR21M-S:~/source/firestarter-1.0.3$ ./configure
checking for intltool >= 0.30... 0.31.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler... 
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for gconftool-2... /usr/bin/gconftool-2
checking for pkg-config... /usr/bin/pkg-config
checking for libgnome-2.0 >= 2.0.0
                  libgnomeui-2.0 >= 2.0.0
                  gtk+-2.0 >= 2.4.0
                  gnome-vfs-2.0 >= 2.6.0
		  libglade-2.0 >= 2.3.6... Package libgnome-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnome-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnome-2.0' found Package libgnomeui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomeui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomeui-2.0' found Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found Package gnome-vfs-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gnome-vfs-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gnome-vfs-2.0' found Package libglade-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libglade-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libglade-2.0' found
configure: error: Library requirements (libgnome-2.0 >= 2.0.0
                  libgnomeui-2.0 >= 2.0.0
                  gtk+-2.0 >= 2.4.0
                  gnome-vfs-2.0 >= 2.6.0
		  libglade-2.0 >= 2.3.6) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
richard@richard-VGN-NR21M-S:~/source/firestarter-1.0.3$ 


I also went through the list of all dependencies and attempted to install all except which told me were allready installed.

Thanks in advance for any help.

Rich

---

