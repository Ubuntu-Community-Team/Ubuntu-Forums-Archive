---
title: "Epson stylus photo rx580; can't print"
date: 2010-06-09
forum: General Help
---

### Post by Mr Nemo on 2010-06-09
I'm trying to set up this printer with my Ubuntu OS (Lucid), but it doesn't seem to be working. I'm trying to install the driver for the printer but I keep getting:

```
eiven@eiven-laptop:~/Desktop/pipslite-1.4.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for lt_dlinit in -lltdl... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for an ANSI C-conforming const... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking which extension is used for loadable modules... .so
checking which variable specifies run-time library path... LD_LIBRARY_PATH
checking for the default library search path... /lib /usr/lib /usr/lib/mesa /usr/lib32/mesa /usr/lib32/alsa-lib /usr/lib/alsa-lib /usr/local/lib /lib/x86_64-linux-gnu /usr/lib/x86_64-linux-gnu 
checking for objdir... .libs
checking whether libtool supports -dlopen/-dlpreopen... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen in -ldl... (cached) yes
checking for dlerror... yes
checking for _ prefix in compiled symbols... no
checking whether deplibs are loaded by dlopen... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking for error_t... yes
checking for argz_append... yes
checking for argz_create_sep... yes
checking for argz_insert... yes
checking for argz_next... yes
checking for argz_stringify... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for unistd.h... (cached) yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking dld.h usability... no
checking dld.h presence... no
checking for dld.h... no
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking for string.h... (cached) yes
checking for strchr... yes
checking for strrchr... yes
checking for memcpy... yes
checking for memmove... yes
checking for strcmp... yes
checking for closedir... yes
checking for opendir... yes
checking for readdir... yes
checking for cups-config... yes
checking for pthread_create in -lpthread... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... yes
checking for ANSI C header files... (cached) yes
checking for dirent.h that defines DIR... (cached) yes
checking for library containing opendir... (cached) none required
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for strerror in -lcposix... no
checking for an ANSI C-conforming const... (cached) yes
checking for off_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for pid_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking whether gcc needs -traditional... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking return type of signal handlers... void
checking for alarm... yes
checking for gettimeofday... yes
checking for memset... yes
checking for mkfifo... yes
checking for select... yes
checking for socket... yes
checking for strcspn... yes
checking for strstr... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking for shared library run path origin... done
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for atoll... yes
checking for _exit... yes
checking for ftime... yes
checking for getexecname... no
checking for getc_unlocked... yes
checking for getpagesize... yes
checking for getpid... yes
checking for lltostr... no
checking for madvise... yes
checking for mkstemp... yes
checking for _NSGetExecutablePath... no
checking for _pclose... no
checking for pclose... yes
checking for poll... yes
checking for _popen... no
checking for popen... yes
checking for pread... yes
checking for pwrite... yes
checking for putc_unlocked... yes
checking for raise... yes
checking for rand_r... yes
checking for readlink... yes
checking for realpath... yes
checking for select... (cached) yes
checking for seekdir... yes
checking for sigemptyset... yes
checking for sigaction... yes
checking for strerror... yes
checking for strlcat... no
checking for strlcpy... no
checking for strtoll... yes
checking for sysconf... yes
checking for tempnam... yes
checking for times... yes
checking for telldir... yes
checking for ulltostr... no
checking for vsprintf... yes
checking for vsnprintf... yes
checking sys/times.h usability... yes
checking sys/times.h presence... yes
checking for sys/times.h... yes
checking for sys/types.h... (cached) yes
checking whether pread is declared... no
checking whether pwrite is declared... no
checking whether strlcpy is declared... no
checking whether vsnprintf is declared... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating lib/Makefile
config.status: creating lib-l2/Makefile
config.status: creating src/Makefile
config.status: creating src/filter-l2/Makefile
config.status: creating daemon/Makefile
config.status: creating daemon/rc/Makefile
config.status: creating status-monitor/Makefile
config.status: creating layout_script/Makefile
config.status: creating pixmaps/Makefile
config.status: creating ppd/Makefile
config.status: creating po/Makefile.in
config.status: WARNING:  po/Makefile.in.in seems to ignore the --datarootdir setting
config.status: creating setup/Makefile
config.status: creating makeinstall/Makefile
config.status: creating pipslite.spec
config.status: creating config.h
config.status: config.h is unchanged
config.status: creating src/filter-l2/magick/magick_config.h
config.status: src/filter-l2/magick/magick_config.h is unchanged
config.status: creating src/filter-l2/magick/magick_config_api.h
config.status: src/filter-l2/magick/magick_config_api.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
eiven@eiven-laptop:~/Desktop/pipslite-1.4.0$ make
make  all-recursive
make[1]: Entering directory `/home/eiven/Desktop/pipslite-1.4.0'
Making all in lib
make[2]: Entering directory `/home/eiven/Desktop/pipslite-1.4.0/lib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/eiven/Desktop/pipslite-1.4.0/lib'
Making all in lib-l2
make[2]: Entering directory `/home/eiven/Desktop/pipslite-1.4.0/lib-l2'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/eiven/Desktop/pipslite-1.4.0/lib-l2'
Making all in src
make[2]: Entering directory `/home/eiven/Desktop/pipslite-1.4.0/src'
Making all in filter-l2
make[3]: Entering directory `/home/eiven/Desktop/pipslite-1.4.0/src/filter-l2'
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../src/filter-l2/magick    -DCUPS_FILTER_PATH=\"/usr/local/lib/cups/filter\" -I../../lib-l2 -I../../src/filter-l2/ -g -O2 -Wall -MT l2filter.o -MD -MP -MF .deps/l2filter.Tpo -c -o l2filter.o l2filter.c
l2filter.c:45:25: error: cups/raster.h: No such file or directory
l2filter.c:68: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
l2filter.c:76: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
l2filter.c: In function &#8216;main&#8217;:
l2filter.c:125: error: &#8216;cups_raster_t&#8217; undeclared (first use in this function)
l2filter.c:125: error: (Each undeclared identifier is reported only once
l2filter.c:125: error: for each function it appears in.)
l2filter.c:125: error: &#8216;cups_ras&#8217; undeclared (first use in this function)
l2filter.c:126: error: &#8216;cups_page_header_t&#8217; undeclared (first use in this function)
l2filter.c:126: error: expected &#8216;;&#8217; before &#8216;header&#8217;
l2filter.c:137: error: &#8216;header&#8217; undeclared (first use in this function)
l2filter.c:188: warning: implicit declaration of function &#8216;cupsRasterOpen&#8217;
l2filter.c:188: error: &#8216;CUPS_RASTER_READ&#8217; undeclared (first use in this function)
l2filter.c:201: warning: implicit declaration of function &#8216;cupsRasterReadHeader&#8217;
l2filter.c:204: warning: implicit declaration of function &#8216;convert_cups_to_jpeg_1st&#8217;
l2filter.c:228: warning: implicit declaration of function &#8216;resize_jpeg&#8217;
l2filter.c:252: warning: implicit declaration of function &#8216;cupsRasterClose&#8217;
l2filter.c: At top level:
l2filter.c:779: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
l2filter.c:1202: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
make[3]: *** [l2filter.o] Error 1
make[3]: Leaving directory `/home/eiven/Desktop/pipslite-1.4.0/src/filter-l2'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/eiven/Desktop/pipslite-1.4.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/eiven/Desktop/pipslite-1.4.0'
make: *** [all] Error 2

```

./configure seems to work and I keep getting stuck at make...

---

### Post by Mr Nemo on 2010-06-12
bump?

---

### Post by chayzer on 2010-06-12
How about the .ppd from:
[http://avasys.jp/eng/linux_driver/]("http://avasys.jp/eng/linux_driver/")

---

### Post by Mr Nemo on 2010-06-12
I can't find anything about a .ppd

---

### Post by chayzer on 2010-06-12
Looks like they have a .deb file for you. Give that a shot or the .ppd file can be found in the source tar.gz in the ppd folder

---

### Post by Mr Nemo on 2010-06-12
the only .deb file I found was for 32 bit, which doesnt install correctly even when forced. I found a proper file for the scanner, but that's not my main concern. Ill try looking for the .ppd file again...

**I found a ppd folder in the source file, but what can I do with that?

---

### Post by chayzer on 2010-06-12
System->Administration->Printing

When you add a new printer there should be an option in there a couple steps in to use .ppd file

I'm also assuming you tried the gutenprint driver?

---

### Post by Mr Nemo on 2010-06-12
I have not tried the gutenprint driver, I will look into that. Back in a few with results.

**Gutenprint driver is not working. A bunch of errors that i don't understand, but it says cups/raster.h doesnt exist

**I dunno what I did or didn't do, but now my computer is recognizing the printer... any thoughts why? Did gutenprint driver install regardless of the errors? Im confused...  Thanks for your help Chayzer.

---

