---
title: "cross compiling software for arm"
date: 2010-09-20
forum: General Help
---

### Post by meg23 on 2010-09-20
I am trying to cross compile a package from source for an embedded arm board, however I am not having much luck creating an arm binary. 

export PATH=/usr/local/arm/4.3.2/bin:$PATH 
export CROSS_COMPILE=arm-none-linux-gnueabi-
./configure --host=arm-linux
make
make install

After running make, this is what I get:

configure: WARNING: If you wanted to set the --build type, don't use --host.
    If a cross compiler is detected then cross compile mode will be used.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for arm-linux-strip... arm-linux-strip
checking build system type... i686-pc-linux-gnu
checking host system type... arm-unknown-linux-gnu
checking for style of include used by make... GNU
checking for arm-linux-gcc... arm-linux-gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... yes
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether arm-linux-gcc accepts -g... yes
checking for arm-linux-gcc option to accept ISO C89... none needed
checking dependency style of arm-linux-gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by arm-linux-gcc... /usr/local/arm/4.3.2/arm-none-linux-gnueabi/bin/ld
checking if the linker (/usr/local/arm/4.3.2/arm-none-linux-gnueabi/bin/ld) is GNU ld... yes
checking for /usr/local/arm/4.3.2/arm-none-linux-gnueabi/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/local/arm/4.3.2/bin/arm-linux-nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... arm-linux-gcc -E
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
checking for arm-linux-g++... arm-linux-g++
checking whether we are using the GNU C++ compiler... yes
checking whether arm-linux-g++ accepts -g... yes
checking dependency style of arm-linux-g++... gcc3
checking how to run the C++ preprocessor... arm-linux-g++ -E
checking for arm-linux-g77... no
checking for arm-linux-xlf... no
checking for arm-linux-f77... no
checking for arm-linux-frt... no
checking for arm-linux-pgf77... no
checking for arm-linux-cf77... no
checking for arm-linux-fort77... no
checking for arm-linux-fl32... no
checking for arm-linux-af77... no
checking for arm-linux-xlf90... no
checking for arm-linux-f90... no
checking for arm-linux-pgf90... no
checking for arm-linux-pghpf... no
checking for arm-linux-epcf90... no
checking for arm-linux-gfortran... no
checking for arm-linux-g95... no
checking for arm-linux-xlf95... no
checking for arm-linux-f95... no
checking for arm-linux-fort... no
checking for arm-linux-ifort... no
checking for arm-linux-ifc... no
checking for arm-linux-efc... no
checking for arm-linux-pgf95... no
checking for arm-linux-lf95... no
checking for arm-linux-ftn... no
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/local/arm/4.3.2/bin/arm-linux-nm -B output from arm-linux-gcc object... ok
checking for objdir... .libs
checking for arm-linux-ar... arm-linux-ar
checking for arm-linux-ranlib... arm-linux-ranlib
checking for arm-linux-strip... (cached) arm-linux-strip
checking if arm-linux-gcc supports -fno-rtti -fno-exceptions... no
checking for arm-linux-gcc option to produce PIC... -fPIC
checking if arm-linux-gcc PIC flag -fPIC works... yes
checking if arm-linux-gcc static flag -static works... yes
checking if arm-linux-gcc supports -c -o file.o... yes
checking whether the arm-linux-gcc linker (/usr/local/arm/4.3.2/arm-none-linux-gnueabi/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by arm-linux-g++... /usr/local/arm/4.3.2/arm-none-linux-gnueabi/bin/ld
checking if the linker (/usr/local/arm/4.3.2/arm-none-linux-gnueabi/bin/ld) is GNU ld... yes
checking whether the arm-linux-g++ linker (/usr/local/arm/4.3.2/arm-none-linux-gnueabi/bin/ld) supports shared libraries... yes
checking for arm-linux-g++ option to produce PIC... -fPIC
checking if arm-linux-g++ PIC flag -fPIC works... yes
checking if arm-linux-g++ static flag -static works... yes
checking if arm-linux-g++ supports -c -o file.o... yes
checking whether the arm-linux-g++ linker (/usr/local/arm/4.3.2/arm-none-linux-gnueabi/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for arm-linux-gcc... (cached) arm-linux-gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether arm-linux-gcc accepts -g... (cached) yes
checking for arm-linux-gcc option to accept ISO C89... (cached) none needed
checking dependency style of arm-linux-gcc... (cached) gcc3
checking dependency style of arm-linux-gcc... gcc3
checking for ecj... no
checking for jikes... no
checking for gcj... no
checking for javac... no
checking for pthread_self in -lthr... no
checking for pthread_self in -lpthread... yes
checking for fmod in -lm... yes
checking for dlopen in -ldl... yes
checking for inflate in -lz... yes
checking for ANSI C header files... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking endian.h usability... yes
checking endian.h presence... yes
checking for endian.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking alloca.h usability... yes
checking alloca.h presence... yes
checking for alloca.h... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... no
checking for gettimeofday... yes
checking for strtol... yes
checking for setlocale... yes
checking for LC_MESSAGES... yes
checking for __thread... yes
checking whether to enable maintainer-specific portions of Makefiles... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/interp/Makefile
config.status: creating src/interp/engine/Makefile
config.status: creating src/arch/Makefile
config.status: creating src/os/Makefile
config.status: creating src/os/linux/Makefile
config.status: creating src/os/darwin/Makefile
config.status: creating src/os/bsd/Makefile
config.status: creating src/os/solaris/Makefile
config.status: creating src/os/solaris/x86/Makefile
config.status: creating src/os/linux/powerpc/Makefile
config.status: creating src/os/linux/arm/Makefile
config.status: creating src/os/linux/i386/Makefile
config.status: creating src/os/linux/x86_64/Makefile
config.status: creating src/os/linux/parisc/Makefile
config.status: creating src/os/linux/mips/Makefile
config.status: creating src/os/darwin/i386/Makefile
config.status: creating src/os/darwin/arm/Makefile
config.status: creating src/os/darwin/powerpc/Makefile
config.status: creating src/os/bsd/powerpc/Makefile
config.status: creating src/os/bsd/arm/Makefile
config.status: creating src/os/bsd/i386/Makefile
config.status: creating src/os/bsd/x86_64/Makefile
config.status: creating src/os/bsd/sparc/Makefile
config.status: creating lib/Makefile
config.status: creating lib/java/Makefile
config.status: creating lib/java/lang/Makefile
config.status: creating lib/jamvm/Makefile
config.status: creating lib/jamvm/java/Makefile
config.status: creating lib/jamvm/java/lang/Makefile
config.status: creating lib/java/lang/reflect/Makefile
config.status: creating lib/java/security/Makefile
config.status: creating lib/gnu/Makefile
config.status: creating lib/sun/reflect/annotation/Makefile
config.status: creating lib/sun/reflect/Makefile
config.status: creating lib/sun/Makefile
config.status: creating lib/gnu/classpath/Makefile
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: linking src/arch/arm.h to src/arch.h
config.status: executing depfiles commands
steve@steve-desktop:~/Desktop/jamvm-1.5.4$ make
Making all in src
make[1]: Entering directory `/home/steve/Desktop/jamvm-1.5.4/src'
make  all-recursive
make[2]: Entering directory `/home/steve/Desktop/jamvm-1.5.4/src'
Making all in os
make[3]: Entering directory `/home/steve/Desktop/jamvm-1.5.4/src/os'
Making all in linux
make[4]: Entering directory `/home/steve/Desktop/jamvm-1.5.4/src/os/linux'
Making all in arm
make[5]: Entering directory `/home/steve/Desktop/jamvm-1.5.4/src/os/linux/arm'
/bin/bash ../../../../libtool --tag=CC   --mode=compile arm-linux-gcc -DHAVE_CONFIG_H -I. -I../../../../src  -I../../../../src   -g -O2 -MT dll_md.lo -MD -MP -MF .deps/dll_md.Tpo -c -o dll_md.lo dll_md.c
 arm-linux-gcc -DHAVE_CONFIG_H -I. -I../../../../src -I../../../../src -g -O2 -MT dll_md.lo -MD -MP -MF .deps/dll_md.Tpo -c dll_md.c  -fPIC -DPIC -o .libs/dll_md.o
Assembler messages:
Fatal error: can't create .libs/dll_md.o: Permission denied
make[5]: *** [dll_md.lo] Error 1
make[5]: Leaving directory `/home/steve/Desktop/jamvm-1.5.4/src/os/linux/arm'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/steve/Desktop/jamvm-1.5.4/src/os/linux'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/steve/Desktop/jamvm-1.5.4/src/os'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/steve/Desktop/jamvm-1.5.4/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/steve/Desktop/jamvm-1.5.4/src'
make: *** [all-recursive] Error 1

Am I on the right path?

---

### Post by rlougher on 2010-09-22
Yes, it's trying to compile the ARM specific parts of JamVM, so it's recognised that you're cross-compiling.  However, when it's trying to create files it's getting permission denied.  You don't have write permission because the directories are owned by somebody else, or there's already files there owned by somebody else which you can't overwrite (e.g. have you tried compiling before as root?).

Try cleaning any old files as root:

sudo make clean

and try make again.  If this fails, do the build as root:

sudo make

Hopefully this should work.

Rob.

---

### Post by rlougher on 2010-09-22
Note, if you're not root, you always need to do

sudo make install

because the files are installed in places not writable by normal users (e.g. /usr/local).

Rob.

---

### Post by rlougher on 2010-09-22
Sorry, another note...

Once installed, you need to copy the files onto your target ARM system.  Make install won't install them onto your target, but will copy the files into the correct place on the host.

JamVM installs by default into /usr/local/jamvm

You need to package this up and install the files into the same place on your target, e.g.:

On the host:

sudo make install
cd /usr/local
sudo tar cvzf jamvm.tgz jamvm

On the target:

cd /usr/local
sudo tar xvzf jamvm.tgz

Rob.

---

