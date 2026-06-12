---
title: "gst-jpeg2000-1.0.0 error"
date: 2006-04-25
forum: General Help
---

### Post by cosmoshell on 2006-04-25
root@ubuntu:~# cd /home/god/Desktop/gst-jpeg2000-1.0.0
root@ubuntu:/home/god/Desktop/gst-jpeg2000-1.0.0# ./configure configure: configuring gst-jpeg2000 for release
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for pkg-config... yes
checking for pkg-config... /usr/bin/pkg-config
checking for   gstreamer-0.8 >= 0.8   gstreamer-control-0.8 >= 0.8... yes
checking GST_CFLAGS... -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -pthread -I/usr/include/gstreamer-0.8 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2
checking GST_LIBS... -Wl,--export-dynamic -pthread -lgstcontrol-0.8 -lgstreamer-0.8 -lgobject-2.0 -lgmodule-2.0 -ldl -lgthread-2.0 -lxml2 -lz -lm -lglib-2.0
checking for gstreamer-libs-0.8 >= 0.8... configure: no GStreamer plugin libs found
configure: creating ./config.status
config.status: creating gst-j2k.apspec
config.status: creating Makefile
config.status: creating src/Makefile
config.status: executing depfiles commands
root@ubuntu:/home/god/Desktop/gst-jpeg2000-1.0.0# make
Making all in src
make[1]: Entering directory `/home/god/Desktop/gst-jpeg2000-1.0.0/src'
if /bin/sh ../libtool --mode=compile --tag=CC gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DGST_PLUGIN_VERSION=\"1.0.0\" -DGST_PLUGIN_VERSION_RELEASE=\"1\" -DPACKAGE=\"gst-jpeg2000\" -DVERSION=\"1.0.0\" -DPACKAGE=\"gst-jpeg2000\" -DVERSION=\"1.0.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -I. -I.     -I/include -g -O2 -MT libgstjpeg2000_la-gstj2k.lo -MD -MP -MF ".deps/libgstjpeg2000_la-gstj2k.Tpo" -c -o libgstjpeg2000_la-gstj2k.lo `test -f 'gstj2k.c' || echo './'`gstj2k.c; \
        then mv -f ".deps/libgstjpeg2000_la-gstj2k.Tpo" ".deps/libgstjpeg2000_la-gstj2k.Plo"; else rm -f ".deps/libgstjpeg2000_la-gstj2k.Tpo"; exit 1; fi
 gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DGST_PLUGIN_VERSION=\"1.0.0\" -DGST_PLUGIN_VERSION_RELEASE=\"1\" -DPACKAGE=\"gst-jpeg2000\" -DVERSION=\"1.0.0\" -DPACKAGE=\"gst-jpeg2000\" -DVERSION=\"1.0.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I. -I. -I/include -g -O2 -MT libgstjpeg2000_la-gstj2k.lo -MD -MP -MF .deps/libgstjpeg2000_la-gstj2k.Tpo -c gstj2k.c  -fPIC -DPIC -o .libs/libgstjpeg2000_la-gstj2k.o
In file included from gstj2k.c:27:
gstj2kdec.h:26:21: error: gst/gst.h: No such file or directory
In file included from gstj2k.c:27:
gstj2kdec.h:49: error: syntax error before 'GstElement'
gstj2kdec.h:49: warning: no semicolon at end of struct or union
gstj2kdec.h:52: warning: data definition has no type or storage class
gstj2kdec.h:55: error: syntax error before 'width'
gstj2kdec.h:55: warning: data definition has no type or storage class
gstj2kdec.h:56: error: syntax error before 'height'
gstj2kdec.h:56: warning: data definition has no type or storage class
gstj2kdec.h:57: error: syntax error before 'fps'
gstj2kdec.h:57: warning: data definition has no type or storage class
gstj2kdec.h:59: error: syntax error before 'bpp'
gstj2kdec.h:59: warning: data definition has no type or storage class
gstj2kdec.h:60: error: syntax error before 'depth'
gstj2kdec.h:60: warning: data definition has no type or storage class
gstj2kdec.h:61: error: syntax error before 'endianness'
gstj2kdec.h:61: warning: data definition has no type or storage class
gstj2kdec.h:62: error: syntax error before 'red_mask'
gstj2kdec.h:62: warning: data definition has no type or storage class
gstj2kdec.h:63: error: syntax error before 'red_loss'
gstj2kdec.h:63: warning: data definition has no type or storage class
gstj2kdec.h:64: error: syntax error before 'red_shift'
gstj2kdec.h:64: warning: data definition has no type or storage class
gstj2kdec.h:65: error: syntax error before '}' token
gstj2kdec.h:68: error: syntax error before 'GstElementClass'
gstj2kdec.h:68: warning: no semicolon at end of struct or union
gstj2kdec.h:71: error: syntax error before 'gst_jpeg2000dec_get_type'
gstj2kdec.h:71: warning: data definition has no type or storage class
In file included from gstj2k.c:28:
gstj2kenc.h:49: error: syntax error before 'GstElement'
gstj2kenc.h:49: warning: no semicolon at end of struct or union
gstj2kenc.h:52: warning: data definition has no type or storage class
gstj2kenc.h:55: error: syntax error before 'width'
gstj2kenc.h:55: warning: data definition has no type or storage class
gstj2kenc.h:56: error: syntax error before 'height'
gstj2kenc.h:56: warning: data definition has no type or storage class
gstj2kenc.h:57: error: syntax error before 'fps'
gstj2kenc.h:57: warning: data definition has no type or storage class
gstj2kenc.h:59: error: syntax error before 'bpp'
gstj2kenc.h:59: warning: data definition has no type or storage class
gstj2kenc.h:60: error: syntax error before 'depth'
gstj2kenc.h:60: warning: data definition has no type or storage class
gstj2kenc.h:61: error: syntax error before 'endianness'
gstj2kenc.h:61: warning: data definition has no type or storage class
gstj2kenc.h:62: error: syntax error before 'red_mask'
gstj2kenc.h:62: warning: data definition has no type or storage class
gstj2kenc.h:63: error: syntax error before '}' token
gstj2kenc.h:66: error: syntax error before 'GstElementClass'
gstj2kenc.h:66: warning: no semicolon at end of struct or union
gstj2kenc.h:69: error: syntax error before 'gst_jpeg2000enc_get_type'
gstj2kenc.h:69: warning: data definition has no type or storage class
gstj2k.c:32: error: syntax error before 'plugin_init'
gstj2k.c:32: error: syntax error before '*' token
gstj2k.c: In function 'plugin_init':
gstj2k.c:34: error: 'plugin' undeclared (first use in this function)
gstj2k.c:34: error: (Each undeclared identifier is reported only once
gstj2k.c:34: error: for each function it appears in.)
gstj2k.c:34: error: 'GST_RANK_NONE' undeclared (first use in this function)
gstj2k.c:36: error: 'FALSE' undeclared (first use in this function)
gstj2k.c:43: error: 'TRUE' undeclared (first use in this function)
gstj2k.c: At top level:
gstj2k.c:48: error: syntax error before string constant
make[1]: *** [libgstjpeg2000_la-gstj2k.lo] Error 1
make[1]: Leaving directory `/home/god/Desktop/gst-jpeg2000-1.0.0/src'
make: *** [all-recursive] Error 1
root@ubuntu:/home/god/Desktop/gst-jpeg2000-1.0.0#

---

### Post by croak77 on 2006-04-25
Check to see if libgstreamer-plugins0.8-dev is installed? Maybe that will help.

---

### Post by cosmoshell on 2006-04-28
not currently installed

---

