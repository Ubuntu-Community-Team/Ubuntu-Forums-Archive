---
title: "Cinepaint: Compile Fail!"
date: 2011-03-09
forum: General Help
---

### Post by ari_d on 2011-03-09
After two days of installing dependencies and troubleshooting, I finally got Cinepaint 0.22-1 to configure without error. However I cannot compile beyond this stage. 'Make' always results in: make: 

*** No targets.  Stop.

I'm fairly new at compiling but know my way around the terminal, so I'm lost. Please point me in the right direction.

Here's what I'm getting:

```
ari@chadbook:~/Desktop/cinepaint-0.22-1$ ./configure --enable-pygimp --enable-gtk2 --disable-print
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether build environment is sane... yes
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking whether ln -s works... yes
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
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
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether byte ordering is bigendian... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking whether time.h and sys/time.h may both be included... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/times.h usability... yes
checking sys/times.h presence... yes
checking for sys/times.h... yes
checking for unistd.h... (cached) yes
checking for pid_t... yes
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for working alloca.h... yes
checking for alloca... yes

PKG_CONFIG_PATH =

checking fd_set and sys/select... yes
checking for yywrap in -lfl... yes
checking for pthread_create in -lpthread... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking for Gtk2... (version 2.22.0) yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  ca cs da de el en_GB es fi fr ga gl hu hr it ja ko lt nl nn no pl pt pt_BR ro ru sk sl sv tr uk zh_CN zh_TW
checking for TIFF support... checking for TIFFOpen in -ltiff... yes
checking tiff.h usability... yes
checking tiff.h presence... yes
checking for tiff.h... yes
checking tiffio.h usability... yes
checking tiffio.h presence... yes
checking for tiffio.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking for OpenEXR... (version 1.6.1) yes
checking for JPEG support... checking for jinit_memory_mgr in -ljpeg... yes
checking for gzsetparams in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking for libpng... (version 1.2.44) yes
checking for pkg-config... /usr/bin/pkg-config
checking for lcms >= 1.16... yes (version 1.18)
checking for XmuClientWindow in -lXmu... yes
checking X11/Xmu/WinUtil.h usability... yes
checking X11/Xmu/WinUtil.h presence... yes
checking for X11/Xmu/WinUtil.h... yes
checking for oyranos-config... /usr/bin/oyranos-config
checking for fltk-config... /usr/local/bin/fltk-config
checking sys/ipc.h usability... yes
checking sys/ipc.h presence... yes
checking for sys/ipc.h... yes
checking sys/shm.h usability... yes
checking sys/shm.h presence... yes
checking for sys/shm.h... yes
checking whether shmctl IPC_RMID allowes subsequent attaches... yes
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking for python... /usr/bin/python
checking for Python prefix... /usr
checking for Python exec-prefix... /usr
checking for Python version... python2.6
checking for Python header files... 
checking for Python library... -L/usr/lib/python2.6/config
checking fltk dependend plug-ins ... yes "bracketing_to_hdr" "collect" "pdf"
checking thread dependend plug-ins ... yes "icc_examin"
checking flex dependend plug-ins ... yes "iol"
checking for rpm... no
configure: creating ./config.status
config.status: creating Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating user_install
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating gimprc
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating gimprc_user
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating cinepainttool
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating cinepaint-gtk.pc
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating cinepaint.spec
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating lib/version.h
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating lib/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating lib/wire/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating lib/fl_i18n/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating libgimp/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating libgimp/gimpintl.h
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating libhalf/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/blur/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/bmp/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/bracketing_to_hdr/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/bracketing_to_hdr/br_core/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/bracketing_to_hdr/FL_adds/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/bracketing_to_hdr/gui/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/bracketing_to_hdr/jhead/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/cineon/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/collect/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/compose/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/dbbrowser/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/decompose/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/dicom/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/edge/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/fits/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/gauss_rle/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/gbr/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/gifload/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/hdr/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/icc_examin/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/iff/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/iol/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/iol/examples/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/jpeg/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/mblur/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/median/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/minimum/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/noisify/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/openexr/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/pic/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/pdf/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/png/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/pnm/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/print/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/psd/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/psd_save/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/pygimp/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/pygimp/doc/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/pygimp/plug-ins/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/script-fu/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/script-fu/scripts/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/rawphoto/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/retinex/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/rotate/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/screenshot/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/sgi/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/sharpen/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/snoise/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/sobel/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/spread/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/tga/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/tiff/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/unsharp/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/xwd/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating po/Makefile.in
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating po-plug-ins/Makefile.in
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating po-plug-ins/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating po-script-fu/Makefile.in
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating po-script-fu/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating app/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating app/depth/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating data/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating data/brushes/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating data/curves/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating data/gradients/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating data/palettes/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating data/patterns/Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command
config.status: creating lib/config.h
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing default commands
configure: configuring in plug-ins/icc_examin/icc_examin
configure: running /bin/bash './configure' --prefix=/usr/local  '--enable-pygimp' '--enable-gtk2' '--disable-print' --cache-file=/dev/null --srcdir=.

################################################################
#                                                              #
        Welcome to ICC Examin Version 0.43 configurator
#                                                              #
#                       Configuration                          #

Linux system            detected
Ubuntu 10.10
32-bit system           detected
Oyranos 0.1.9           detected
littleCMS 1.18          detected
X11                     detected
X VidMode extension     detected
X Xinerama              detected
libXpm is available
libXext is available
FTGL      2.1.3~rc5         detected
FLTK 1.3.0              detected
rm: cannot remove `fltk_test': No such file or directory
PNG 1.2.44               detected
libdl is available

                        detected
Gettext                 detected
translations available: de eo fr
local CinePaint   detected


generated icc_examin.spec from icc_examin.spec.in
prefix =                /usr/local

################################################################
#                       Configuration                          #
prefix          =       /usr/local
exec_prefix     =       /usr/local
bindir          =       /usr/local/bin
sbindir         =       /usr/local/sbin
libdir          =       /usr/local/lib
includedir      =       /usr/local/include
datadir         =       /usr/local/share
mandir          =       /usr/local/share/man
pixmapdir       =       /usr/local/share/pixmaps
desktopdir      =       /usr/local/share/applications
INCL            :       INCL=-I$(includedir) -I/usr/X11R6/include -I. -I/usr/include/g++ -I/usr/include
CFLAGS          =        $(INCL)
CXXFLAGS        =        $(INCL)
LDFLAGS         =        -L.
################################################################



preparing Makefile in ./
preparing Makefile in fl_i18n/
Makefile:14: *** missing separator.  Stop.

=================================================================
              Configuration Results

GTK CinePaint Version 0.22-1


General dependencies:
   Gtk2 toolkit                 yes    2.22.0
   DnD support                  yes    X11/Xmu
   littleCMS                    yes    lcms 1.18
   Oyranos                      yes    oyranos 0.1.9

Plug-ins with external dependencies:
   Python plug-in:              yes    python2.6
   OpenEXR plug-in:             yes    OpenEXR 1.6.1
   Tiff plug-in:                yes
   PNG plug-in:                 yes    libpng 1.2.44
   Jpeg plug-in:                yes
   Print plug-in:               no
   FLTK dependent plug-ins:     yes    bracketing_to_hdr collect pdf
   Thread dependent plug-ins:   yes    icc_examin
   Flex dependent plug-ins:     yes    iol
=================================================================

Now type 'make' and 'make install' / 'make rpm' to build the package and 
install. The unix command is 'cinepaint'.
ari@chadbook:~/Desktop/cinepaint-0.22-1$ make
make: *** No targets.  Stop.
```

Thank you!

---

### Post by anglican on 2011-03-10
> **ari_d said:**
> 

... snip ...

configure: creating ./config.status
config.status: creating Makefile
sed: file ./confstat1Erugb/subs-4.sed line 33: unterminated `s' command

... snip ... 

preparing Makefile in ./
preparing Makefile in fl_i18n/
Makefile:14: *** missing separator.  Stop.

... snip ...

install. The unix command is 'cinepaint'.

ari@chadbook:~/Desktop/cinepaint-0.22-1$ make
make: *** No targets.  Stop.[/CODE]

Thank you!Those sed errors are your problem and the error making a makefile in ./ - configure is **not** running without errors! The Makefiles needed to actually build Cinepaint are not being created correctly hence the make error that you see. Strangely I don't get that error when configuring from the source code file - I downloaded the same version as you have (I'm on Xubuntu 10.04 x86, which may or may not be relevent). I can't compile because of missing dependencies but it seems to configure without the error you're getting. I'd suggest trying to use alien on the many rpm versions that seem to be available and install that instead... or you could try installing from [http://www.getdeb.net/software/cinepaint](http://www.getdeb.net/software/cinepaint).


H

---

