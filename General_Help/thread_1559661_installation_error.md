---
title: "installation error"
date: 2010-08-23
forum: General Help
---

### Post by chips24 on 2010-08-23
where can i find this package and what does it do?
 "mktime"
how do i find the functioning program when i am done?

I would like to understand what its doing here...
sorry about the misleading title, i thought there was a problem, but i guess my patience was getting the best of me...

please move this thread, i thought there was a problem, but there wasn't.

caleb@caleb-laptop:~$ cd '/home/caleb/Downloads/povray-3.6.1'
caleb@caleb-laptop:~/Downloads/povray-3.6.1$ ./configure COMPILED_BY="Caleb Hubbell<calebgordon24@gmail.com>"

===============================================================================
Configure POV-Ray version 3.6.1
===============================================================================

This is an unofficial version compiled by:
 Caleb Hubbell<calebgordon24@gmail.com>
The POV-Ray Team(tm) is not responsible for supporting this version.

Environment
-----------
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether $C_INCLUDE_PATH contains the "." path... no
checking whether $CPLUS_INCLUDE_PATH contains the "." path... no

Programs
--------
checking for egrep... grep -E
checking for style of include used by make... GNU
checking for g++... g++
checking for C++ compiler default output... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g++ version... 4.4.3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for ranlib... ranlib

Language constructs and functions
---------------------------------
checking whether to link with cygwin DLL... no
checking whether time.h and sys/time.h may both be included... yes
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
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for int... yes
checking size of int... 4
checking for long int... yes
checking size of long int... 4
checking for size_t... (cached) yes
checking size of size_t... 4
checking for float... yes
checking size of float... 4
checking for working memcmp... yes
checking return type of signal handlers... void
checking for vsnprintf... yes
checking for getcwd... yes
checking for readlink... yes
checking for gettimeofday... yes

Libraries
---------
checking whether to enable static linking... no
checking for sin in -lm... yes
checking for asinh... yes
checking for vga_init in -lvga... no
configure: SVGAlib display will be disabled
checking for X... no
configure: X Window display will be disabled
checking for installed supporting libraries... yes
checking for library containing zlibVersion... no
configure: zlib will be built and statically linked to POV-Ray
checking for libpng... forced by libz
configure: libpng will be built and statically linked to POV-Ray
checking for library containing jpeg_std_error... no
configure: libjpeg will be built and statically linked to POV-Ray
checking for libtiff... forced by libz
configure: libtiff will be built and statically linked to POV-Ray

Compiling
---------
checking whether to enable pipes for communications... yes
checking whether g++ accepts -pipe... yes
checking whether gcc accepts -pipe... yes
checking whether g++ accepts -Wno-multichar... yes
checking whether to enable I/O restrictions... yes
checking whether to enable debugging... no
checking whether to enable profiling... no
checking whether to enable stripping... no
checking whether to enable optimizations... yes
checking whether g++ accepts -O3... yes
checking whether gcc accepts -O3... yes
checking whether g++ accepts -msse... yes
checking whether gcc accepts -msse... yes
checking whether g++ accepts -mfpmath=sse... yes
checking whether gcc accepts -mfpmath=sse... yes
checking whether g++ accepts -msse2... yes
checking whether gcc accepts -msse2... yes
checking whether g++ accepts -march=i686 -mtune=i686... yes
checking whether gcc accepts -march=i686 -mtune=i686... yes
checking whether g++ accepts -malign-double... yes
checking whether gcc accepts -malign-double... yes
checking whether g++ accepts -minline-all-stringops... yes
checking whether gcc accepts -minline-all-stringops... yes

Makefiles
---------
configure: creating ./config.status
config.status: creating Makefile
config.status: creating libraries/Makefile
config.status: creating source/base/Makefile
config.status: creating source/frontend/Makefile
config.status: creating source/Makefile
config.status: creating unix/Makefile
config.status: creating conf.h
config.status: executing depfiles commands
config.status: executing config.log commands

Supporting libraries
--------------------
configure: configuring in libraries/zlib
configure: running /bin/bash './configure.gnu' --prefix=/usr/local  'COMPILED_BY=Caleb Hubbell<calebgordon24@gmail.com>' --cache-file=/dev/null --srcdir=.
configure.gnu: configuring zlib 1.2.1
configure.gnu: running ./configure --srcdir=. --cache-file=/dev/null  --prefix=/usr/local
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking utime.h usability... yes
checking utime.h presence... yes
checking for utime.h... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for error_at_line... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking whether time.h and sys/time.h may both be included... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for alarm... yes
checking for working mktime... no
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking whether utime accepts a null argument... yes
checking for vprintf... yes
checking for _doprnt... no
checking for memset... yes
checking for mkdir... yes
checking for munmap... yes
checking for strdup... yes
checking for strerror... yes
checking for strrchr... yes
checking for utime... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h

configure: configuring in libraries/png
configure: running /bin/bash './configure.gnu' --prefix=/usr/local  'COMPILED_BY=Caleb Hubbell<calebgordon24@gmail.com>' --cache-file=/dev/null --srcdir=.
configure.gnu: configuring libpng 1.2.5
configure.gnu: running ./configure --srcdir=. --cache-file=/dev/null  --prefix=/usr/local
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working strtod... yes
checking for memset... yes
checking for pow... no
checking for strrchr... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h

configure: configuring in libraries/jpeg
configure: running /bin/bash './configure.gnu' --prefix=/usr/local  'COMPILED_BY=Caleb Hubbell<calebgordon24@gmail.com>' --cache-file=/dev/null --srcdir=.
configure.gnu: configuring libjpeg 6b
configure.gnu: running ./configure --srcdir=. --cache-file=/dev/null  --prefix=/usr/local
checking for gcc... gcc
checking whether the C compiler (gcc  -pipe -O3 -msse -mfpmath=sse -msse2 -march=i686 -mtune=i686 -malign-double -minline-all-stringops  ) works... yes
checking whether the C compiler (gcc  -pipe -O3 -msse -mfpmath=sse -msse2 -march=i686 -mtune=i686 -malign-double -minline-all-stringops  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking how to run the C preprocessor... gcc -E
checking for function prototypes... yes
checking for stddef.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for size_t... yes
checking for type unsigned char... yes
checking for type unsigned short... yes
checking for type void... yes
checking for working const... yes
checking for inline... __inline__
checking for broken incomplete types... ok
checking for short external names... ok
checking to see if char is signed... yes
checking to see if right shift is signed... yes
checking to see if fopen accepts b spec... yes
checking for a BSD compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking libjpeg version number... 62
creating ./config.status
creating Makefile
creating jconfig.h
configure.gnu: editing Makefile

configure: configuring in libraries/tiff
configure: running /bin/bash './configure.gnu' --prefix=/usr/local  'COMPILED_BY=Caleb Hubbell<calebgordon24@gmail.com>' --cache-file=/dev/null --srcdir=.
configure.gnu: configuring libtiff 3.6.1
configure.gnu: running ./configure --noninteractive --with-DSO=no  --prefix=/usr/local    --srcdir=.

Configuring TIFF Software v3.6.1

If configure does the wrong thing, check the file config.log for
information that may help you understand what went wrong.

Reading site-wide parameters from ./config.site.
Fee, fie, foe, this smells like a i686-pc-linux-gnu system.
Using /usr/bin/gcc for a C compiler (use -with-CC=compilername to override).
Using -I.././../jpeg -I.././../zlib  to get the appropriate compilation environment.
Using " -pipe -O3 -msse -mfpmath=sse -msse2 -march=i686 -mtune=i686 -malign-double -minline-all-stringops  " for C compiler options.
Using /usr/bin/make to configure the software.
Defaulting MACHDEPLIBS to -lm.

Creating libtiff/port.h with necessary definitions.
... using MSB2LSB bit order for your i686 cpu
... using little-endian byte order for your i686 cpu
... O_RDONLY is in <fcntl.h>
... using double for promoted floating point parameters
... enabling use of inline functions
Done creating libtiff/port.h.

Checking system libraries for functionality to emulate.
Done checking system libraries.

Checking for Dynamic Shared Object (DSO) support.
Done checking for DSO support.

Selecting programs used during installation.
Looks like mv supports the -f option to force a move.
Looks like /bin/ln supports the -s option to create a symbolic link.
Done selecting programs.

Selecting default TIFF configuration parameters.

Looks like manual pages go in /usr/local/man.
Looks like manual pages should be installed with bsd-source-cat.

Creating Makefile from ./Makefile.in
Creating libtiff/Makefile from ./libtiff/Makefile.in
Creating man/Makefile from ./man/Makefile.in
Creating tools/Makefile from ./tools/Makefile.in
Creating port/install.sh from ./port/install.sh.in
Done.

configure.gnu: editing libtiff/Makefile


===============================================================================
POV-Ray 3.6.1 has been configured with the following features:
  I/O restrictions: enabled
  X Window display: disabled
  SVGAlib display : disabled

Type 'make' to build, and 'make install' to install all files in the hierarchy
/usr/local
===============================================================================

caleb@caleb-laptop:~/Downloads/povray-3.6.1$

---

