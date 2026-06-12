---
title: "so ehm... Cinepaint?"
date: 2010-05-03
forum: General Help
---

### Post by rasmus91 on 2010-05-03
Hi There

Ever since i found out that there was something called cinepaint i've tried to install it. On their website it says that the debian version currently isn't stable, and therefore not released.

I've tried their own CVS file, and costum files. Nothing so far works.

Any idea how to install?
(A guide would be fantastic)

---

### Post by Surrogard on 2010-05-28
I got it to run, and it wasn't that complicated.
There is a shell-script on their site doing almost everything thats needed.
[http://cinepaint.cvs.sourceforge.net/viewvc/*checkout*/cinepaint/cinepaint-project/cinepaint/ubuntu-cvs.sh?content-type=text/plain](http://cinepaint.cvs.sourceforge.net/viewvc/*checkout*/cinepaint/cinepaint-project/cinepaint/ubuntu-cvs.sh?content-type=text/plain)
But this script wasnt correct for me and a security threat was in it too.
Setting the LD_LIBRARY_PATH is not good, the better way is (after cvs checkout):
```
export LDFLAGS="-R/usr/local/lib"
./configure
make
sudo make install
```In the script the path set is "/usr/lib/local" what might work for other distributions or be an error.

---

### Post by eagle416 on 2010-06-17
Could you please clarify your instructions? where do I insert the code? there's no "CVS Checkout" in your link.

I still get "command: cinepaint not found"

---

### Post by cogvos on 2010-07-17
You know this package is proving to be a pain. Someone must have been able to get it to work. I can't and I guess quite a few others can't either (?).

Following the above I checked out the cvs. But the script falls over at the 
sh autogen.sh point as autogen,sh does not exist in the current dir. Downloading the source from the web fails as well with a problem in the configure (below).

I am guessing there is an error in the configure script which is causing all those sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command lines but have no idea how to fix it.

So please anyone have you managed to get this thing working and if so how?

,/configure output.

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
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
checking for f95... f95
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether f95 accepts -g... yes
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
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for f95 option to produce PIC... -fPIC
checking if f95 PIC flag -fPIC works... yes
checking if f95 supports -c -o file.o... yes
checking whether the f95 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
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
checking for glib-config... /usr/bin/glib-config
checking for inline definition in glibconfig.h... no
checking for inline... inline
checking for gtk-config... /usr/bin/gtk-config
checking for GTK - version >= 1.2.8... yes
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
checking for libpng... (version 1.2.37) yes
checking for pkg-config... /usr/bin/pkg-config
checking for lcms >= 1.16... yes (version 1.18)
checking for XmuClientWindow in -lXmu... yes
checking X11/Xmu/WinUtil.h usability... yes
checking X11/Xmu/WinUtil.h presence... yes
checking for X11/Xmu/WinUtil.h... yes
checking for pkg-config... /usr/bin/pkg-config
try gutenprintui
checking for gutenprint >= 5.0.0... Package gutenprintui was not found in the pkg-config search path.
Perhaps you should add the directory containing `gutenprintui.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gutenprintui' found
expr: syntax error
configure: WARNING:
*** libgutenprint version  is too old or not available.
*** You need at least version 5.0.0 .
configure: WARNING:
*** Check for libgutenprint failed. Try setting the PKG_CONFIG_PATH variable.
*** You may download it from
*** [http://gutenprint.sourceforge.net/](http://gutenprint.sourceforge.net/) . Take an developers release.
*** They are numberd beginning with 5.0.0 .
*** You can build without printing support by passing
*** --disable-print to configure (but you won't be able to print then).
checking for oyranos-config... /usr/local/bin/oyranos-config
checking for fltk-config... /usr/bin/fltk-config
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
checking for Python header files... -I/usr/include/python2.6 -I/usr/lib/python2.6/config
checking for Python library... -L/usr/lib/python2.6/config
checking fltk dependend plug-ins ... yes "bracketing_to_hdr" "collect" "pdf"
checking thread dependend plug-ins ... yes "icc_examin"
checking flex dependend plug-ins ... yes "iol"
checking for rpm... no
configure: creating ./config.status
config.status: creating Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating user_install
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating gimprc
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating gimprc_user
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating cinepainttool
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating cinepaint-gtk.pc
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating cinepaint.spec
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating lib/version.h
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating lib/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating lib/wire/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating lib/fl_i18n/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating libgimp/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating libgimp/gimpintl.h
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating libhalf/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/blur/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/bmp/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/bracketing_to_hdr/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/bracketing_to_hdr/br_core/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/bracketing_to_hdr/FL_adds/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/bracketing_to_hdr/gui/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/bracketing_to_hdr/jhead/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/cineon/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/collect/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/compose/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/dbbrowser/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/decompose/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/dicom/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/edge/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/fits/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/gauss_rle/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/gbr/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/gifload/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/hdr/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/icc_examin/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/iff/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/iol/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/iol/examples/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/jpeg/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/mblur/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/median/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/minimum/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/noisify/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/openexr/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/pic/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/pdf/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/png/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/pnm/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/print/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/psd/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/psd_save/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/pygimp/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/pygimp/doc/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/pygimp/plug-ins/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/script-fu/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/script-fu/scripts/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/rawphoto/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/retinex/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/rotate/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/screenshot/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/sgi/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/sharpen/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/snoise/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/sobel/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/spread/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/tga/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/tiff/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/unsharp/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating plug-ins/xwd/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating po/Makefile.in
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating po-plug-ins/Makefile.in
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating po-plug-ins/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating po-script-fu/Makefile.in
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating po-script-fu/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating app/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating app/depth/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating data/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating data/brushes/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating data/curves/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating data/gradients/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating data/palettes/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating data/patterns/Makefile
sed: file ./confstatpokZqC/subs-4.sed line 33: unterminated `s' command
config.status: creating lib/config.h
config.status: lib/config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing default commands
configure: configuring in plug-ins/icc_examin/icc_examin
configure: running /bin/bash './configure' --prefix=/usr/local  --cache-file=/dev/null --srcdir=.

################################################################
#                                                              #
        Welcome to ICC Examin Version 0.43 configurator
#                                                              #
#                       Configuration                          #

Linux system            detected
Ubuntu 9.10
32-bit system           detected
Oyranos 0.1.9           detected
littleCMS 1.18          detected
X11                     detected
X VidMode extension     detected
X Xinerama              detected
libXpm is available
libXext is available
FTGL      2.1.3~rc5         detected
FLTK 1.1.9              detected
PNG 1.2.37               detected
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
   Gtk1 toolkit                 yes    1.2.10
   DnD support                  yes    X11/Xmu
   littleCMS                    yes    lcms 1.18
   Oyranos                      yes    oyranos 0.1.9

Plug-ins with external dependencies:
   Python plug-in:              no
   OpenEXR plug-in:             yes    OpenEXR 1.6.1
   Tiff plug-in:                yes
   PNG plug-in:                 yes    libpng 1.2.37
   Jpeg plug-in:                yes
   Print plug-in:               no
   FLTK dependent plug-ins:     yes    bracketing_to_hdr collect pdf
   Thread dependent plug-ins:   yes    icc_examin
   Flex dependent plug-ins:     yes    iol
=================================================================

Now type 'make' and 'make install' / 'make rpm' to build the package and 
install. The unix command is 'cinepaint'.

---

### Post by rasmus91 on 2010-10-01
It would actually be very nice if this was working... is Robin Rowe actually still working on it?

---

### Post by szr4321 on 2010-12-14
Just in case someone is still interested in this: for the source tar ball (without the CVS script which I couldn't find unfortunately) I made a small patch, see [http://lglinux.blogspot.com/2010/12/compiling-cinepaint-on-ubuntu-maverick.html]("http://lglinux.blogspot.com/2010/12/compiling-cinepaint-on-ubuntu-maverick.html").

---

### Post by Hanginon on 2011-02-28
Thanks szr4321 for the patch - I've now got Cinepaint 0.22-1 running on Ubuntu Maverick.

Two questions (for anyone) -

I can't find a source for 0.25 (or is 0.22-1 and 0.25 really the same thing?).

The configure script you have disables printing - reason for that?

---

### Post by n.l.o on 2011-03-02
> **Hanginon said:**
> The configure script you have disables printing - reason for that?

If you install gutenprint you can remove it, just did

```
sudo apt-get install gcc automake g++ libfltk1.1-dev libgtk2.0-dev zlib1g-dev libjpeg62-dev libpng12-dev libtiff4-dev libopenexr-dev libxpm-dev libgutenprint-dev libgutenprintui2-dev liblcms1-dev pkg-config ftgl-dev libxmu-dev libxxf86vm-dev flex python-dev libtool
```

before (from [http://ubuntuforums.org/archive/index.php/t-806010.html](http://ubuntuforums.org/archive/index.php/t-806010.html) comment by disx).
and most of the dependencies are met.

running make at the moment, keeping my fingers crossed...

EDIT: got a recursive error when running checkinstall after make. dunno why, giving up for now... (configure & make works fine though)

---

### Post by Hanginon on 2011-03-02
Well, I did 0.22-1 again with the following (I already had Gutenprint dependencies - I use it in GIMP) -

> ./configure --prefix=`pwd`/install --enable-gtk2

Yes, it prints, but with all kinds of error messages like -
GTK_IS_WIDGET(failed)
GTK_IS_TOGGLE_BUTTON

---

### Post by Hanginon on 2011-03-02
Well, I think I have answered my own question. In order for Cinepaint to run under Ubuntu Maverick, it has to be built with GTK2. In order for it to print (without posting errors) it has to be built with GTK. Catch 22. Basically, Cinepaint needs to be reprogrammed.

Where is Robin Rowe, or is Cinepaint 0.25 (if I ever find it) different??

---

### Post by Hanginon on 2011-04-02
Four weeks and absolutely nothing.

Can ANYONE answer the following -

Is Robin Rowe a real person?
Do they really care about CinePaint?
Are we just going to get thrown a small bone every 6 months to peak our interest?

Please reference the following (and note the date)
[http://www.cinepaint.org/](http://www.cinepaint.org/)

I guess the term "next weekend" is NOT what I am used to.

---

### Post by babygenius55 on 2011-10-02
Not sure if anyone got this working or not...   here's a newer version that fails when checking for "loyranos".  [http://www.oyranos.org/scm?p=cinepaint.git;a=summary](http://www.oyranos.org/scm?p=cinepaint.git;a=summary)  I think I will bother to make a sym link for every one one at a time when I wake up.  It's sill y that there isn't any HDR editor openly available for ubuntu.  If anyone gets this working please let me know.

---

