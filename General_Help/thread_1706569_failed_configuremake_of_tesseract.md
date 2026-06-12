---
title: "failed configure/make of tesseract"
date: 2011-03-14
forum: General Help
---

### Post by chris1497 on 2011-03-14
Seems it failed because I am missing a header file called allheaders.h.  What is this and where do I get it?  Thanks in advance.

Here is the output of the configure and make commands:

/var/tmp/tesseract-ocr-read-only$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking --enable-graphics argument... yes
checking for cl.exe... no
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking how to run the C++ preprocessor... g++ -E
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/var/tmp/tesseract-ocr-read-only/config/missing: Unknown `--run' option
Try `/var/tmp/tesseract-ocr-read-only/config/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking dependency style of g++... gcc3
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether byte ordering is bigendian... no
checking for deflate in -lz... yes
checking for png_read_png in -lpng... yes
checking for jpeg_read_scanlines in -ljpeg... yes
checking for sem_init in -lpthread... yes
checking for ANSI C header files... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking sys/ipc.h usability... yes
checking sys/ipc.h presence... yes
checking for sys/ipc.h... yes
checking sys/shm.h usability... yes
checking sys/shm.h presence... yes
checking for sys/shm.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking allheaders.h usability... no
checking allheaders.h presence... no
checking for allheaders.h... no
checking for stdbool.h that conforms to C99... yes
checking for _Bool... no
checking whether #! works in shell scripts... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for wchar_t... yes
checking for long long int... yes
checking for mbstate_t... yes
checking for size_t... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/param.h... yes
checking for getpagesize... yes
checking for working mmap... yes
checking for pid_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for strerror... yes
checking for vsnprintf... yes
checking for gethostname... yes
checking for strchr... yes
checking for memcpy... yes
checking for acos... yes
checking for asin... yes
checking for Leffler libtiff library... checking linking with -ltiff... ok
setting LIBTIFF_CFLAGS=
setting LIBTIFF_LIBS=-ltiff
configure: creating ./config.status
config.status: creating Makefile
config.status: creating api/Makefile
config.status: creating ccmain/Makefile
config.status: creating ccstruct/Makefile
config.status: creating ccutil/Makefile
config.status: creating classify/Makefile
config.status: creating cube/Makefile
config.status: creating cutil/Makefile
config.status: creating dict/Makefile
config.status: creating image/Makefile
config.status: creating neural_networks/runtime/Makefile
config.status: creating textord/Makefile
config.status: creating viewer/Makefile
config.status: creating wordrec/Makefile
config.status: creating training/Makefile
config.status: creating tessdata/Makefile
config.status: creating tessdata/configs/Makefile
config.status: creating tessdata/tessconfigs/Makefile
config.status: creating testing/Makefile
config.status: creating java/Makefile
config.status: creating java/com/Makefile
config.status: creating java/com/google/Makefile
config.status: creating java/com/google/scrollview/Makefile
config.status: creating java/com/google/scrollview/events/Makefile
config.status: creating java/com/google/scrollview/ui/Makefile
config.status: creating config_auto.h
config.status: config_auto.h is unchanged
config.status: executing libtool commands
config.status: executing depfiles commands

Configuration is done.
You can now build tesseract by running:

% make

/var/tmp/tesseract-ocr-read-only$ make
make  all-recursive
make[1]: Entering directory `/var/tmp/tesseract-ocr-read-only'
Making all in ccstruct
make[2]: Entering directory `/var/tmp/tesseract-ocr-read-only/ccstruct'
make[3]: Entering directory `/var/tmp/tesseract-ocr-read-only/ccstruct'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I..  -I../ccutil -I../cutil -I../image -I../viewer   -g -O2 -MT coutln.lo -MD -MP -MF .deps/coutln.Tpo -c -o coutln.lo coutln.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I.. -I../ccutil -I../cutil -I../image -I../viewer -g -O2 -MT coutln.lo -MD -MP -MF .deps/coutln.Tpo -c coutln.cpp  -fPIC -DPIC -o .libs/coutln.o
coutln.cpp:26: fatal error: allheaders.h: No such file or directory
compilation terminated.
make[3]: *** [coutln.lo] Error 1
make[3]: Leaving directory `/var/tmp/tesseract-ocr-read-only/ccstruct'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/var/tmp/tesseract-ocr-read-only/ccstruct'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/tmp/tesseract-ocr-read-only'
make: *** [all] Error 2

---

### Post by kittkatt on 2011-03-14
[https://code.google.com/p/tesseract-ocr/wiki/TesseractSvnInstallation](https://code.google.com/p/tesseract-ocr/wiki/TesseractSvnInstallation)

From reading the comment it looks like someone messed up a commit.  The workaround suggested was to check out another revision for the time being.

---

