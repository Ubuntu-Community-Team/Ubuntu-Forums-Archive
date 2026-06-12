---
title: "embedded sys of ARM"
date: 2012-03-24
forum: General Help
---

### Post by rocket42 on 2012-03-24
2 every one.
I am developing an embedded system of ARM using Ubuntu kernel-3.2.11
when i configure binutils-2.9 package then it appear the following error:
I underlined the following error:
[COLOR=Magenta][I][COLOR=Red]Configuring for a i686-pc-linux-gnu host.
Created "Makefile" in /home/control-project/build-tools/build-binutils using "mt-frag"
Configuring libiberty...
Appending ../../binutils-2.9/libiberty/config/../../config/mh-x86pic to xhost-mkfrag
xhost-mkfrag is unchanged
Linked "alloca-conf.h" to "../../binutils-2.9/libiberty/alloca-norm.h".
Created "Makefile" in /home/control-project/build-tools/build-binutils/libiberty using "xhost-mkfrag"
Configuring opcodes...
loading cache ../config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for ar... (cached) ar
checking for ranlib... (cached) ranlib
checking for ranlib... (cached) ranlib
checking for gcc... (cached) gcc
checking whether the C compiler (gcc -g -O2 ) works... yes
checking whether the C compiler (gcc -g -O2 ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking whether ln -s works... (cached) yes
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... -static
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking command to parse /usr/bin/nm -B output... yes
checking how to hardcode library paths into programs... immediate
checking for /usr/bin/ld option to reload object files... -r
checking dynamic linker characteristics... Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
checking for objdir... .libs
creating libtool
checking whether to enable maintainer-specific portions of Makefiles... no
checking for Cygwin32 environment... (cached) no
checking for Mingw32 environment... (cached) no
checking for executable suffix... (cached) no
checking for gcc... (cached) gcc
checking whether the C compiler (gcc -g -O2 ) works... yes
checking whether the C compiler (gcc -g -O2 ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking for stdlib.h... (cached) yes
creating ./config.status
creating Makefile
creating config.h
config.h is unchanged
Configuring bfd...
loading cache ../config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for gcc... (cached) gcc
checking whether the C compiler (gcc -g -O2 ) works... yes
checking whether the C compiler (gcc -g -O2 ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for POSIXized ISC... no
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for ar... (cached) ar
checking for ranlib... (cached) ranlib
checking for ranlib... (cached) ranlib
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking whether ln -s works... (cached) yes
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... -static
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking command to parse /usr/bin/nm -B output... yes
checking how to hardcode library paths into programs... immediate
checking for /usr/bin/ld option to reload object files... -r
checking dynamic linker characteristics... Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
checking for objdir... .libs
creating libtool
checking whether to enable maintainer-specific portions of Makefiles... no
checking for Cygwin32 environment... (cached) no
checking for Mingw32 environment... (cached) no
checking for executable suffix... (cached) no
checking for gcc... (cached) gcc
checking whether the C compiler (gcc -g -O2 ) works... yes
checking whether the C compiler (gcc -g -O2 ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for stddef.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for time.h... (cached) yes
checking for unistd.h... (cached) yes
checking for fcntl.h... (cached) yes
checking for sys/file.h... (cached) yes
checking for sys/time.h... (cached) yes
checking whether time.h and sys/time.h may both be included... (cached) yes
checking for fcntl... (cached) yes
checking for getpagesize... (cached) yes
checking for setitimer... (cached) yes
checking for sysconf... (cached) yes
checking for fdopen... (cached) yes
checking whether strstr must be declared... (cached) no
checking whether malloc must be declared... (cached) no
checking whether realloc must be declared... (cached) no
checking whether free must be declared... (cached) no
checking whether getenv must be declared... (cached) no
checking for sys/procfs.h... yes
checking for unistd.h... (cached) yes
checking for getpagesize... (cached) yes
checking for working mmap... (cached) yes
checking for madvise... (cached) yes
checking for mprotect... (cached) yes
updating cache ../config.cache
creating ./config.status
creating Makefile
creating doc/Makefile
creating bfd-in3.h
creating config.h
Configuring binutils...
loading cache ../config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for ranlib... (cached) ranlib
checking for gcc... (cached) gcc
checking whether the C compiler (gcc -g -O2 ) works... yes
checking whether the C compiler (gcc -g -O2 ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking whether ln -s works... (cached) yes
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... -static
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking command to parse /usr/bin/nm -B output... yes
checking how to hardcode library paths into programs... immediate
checking for /usr/bin/ld option to reload object files... -r
checking dynamic linker characteristics... Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for objdir... .libs
creating libtool
checking for gcc... (cached) gcc
checking whether the C compiler (gcc -g -O2 ) works... yes
checking whether the C compiler (gcc -g -O2 ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for bison... no
checking for byacc... no
checking for flex... lex
checking for yywrap in -ll... no
checking how to run the C preprocessor... (cached) gcc -E
_c_[/COLOR][COLOR=Red][U]hecking lex output file root... ../../binutils-2.9/binutils/configure: 1: lex: not found
configure: error: cannot find output from lex; giving up
Configure in /home/control-project/build-tools/build-binutils/binutils failed, exiting.[/U]
[COLOR=Black]pleased to help me.
thanks in advance!
[/COLOR][/COLOR][/I][/COLOR]

---

