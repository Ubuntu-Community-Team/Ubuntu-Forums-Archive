---
title: "Error while compiling snort.."
date: 2010-03-03
forum: General Help
---

### Post by karthick87 on 2010-03-03
I get an error while compiling snort..Wats the problem?

```
karthick@Learners-desktop:~$ cd /home/karthick/Desktop/snort-2.8.5.3
karthick@Learners-desktop:~/Desktop/snort-2.8.5.3$ ./configure -enable-dynamicplugin --with-mysql
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking dependency style of g++... none
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
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
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
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ranlib... (cached) ranlib
checking whether byte ordering is bigendian... no
checking for bison... no
checking for yacc... no
checking for flex... no
checking for strings.h... (cached) yes
checking for string.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking for inttypes.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking for floor in -lm... yes
checking for ceil in -lm... yes
checking for inet_ntoa in -lnsl... yes
checking for socket in -lsocket... no
checking whether printf must be declared... no
checking whether fprintf must be declared... no
checking whether syslog must be declared... no
checking whether puts must be declared... no
checking whether fputs must be declared... no
checking whether fputc must be declared... no
checking whether fopen must be declared... no
checking whether fclose must be declared... no
checking whether fwrite must be declared... no
checking whether fflush must be declared... no
checking whether getopt must be declared... no
checking whether bzero must be declared... no
checking whether bcopy must be declared... no
checking whether memset must be declared... no
checking whether strtol must be declared... no
checking whether strcasecmp must be declared... no
checking whether strncasecmp must be declared... no
checking whether strerror must be declared... no
checking whether perror must be declared... no
checking whether socket must be declared... no
checking whether sendto must be declared... no
checking whether vsnprintf must be declared... no
checking whether snprintf must be declared... no
checking whether strtoul must be declared... no
checking for snprintf... yes
checking for strlcpy... no
checking for strlcat... no
checking for strerror... yes
checking for vswprintf... yes
checking for wprintf... yes
checking for char... yes
checking size of char... 1
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long int... yes
checking size of long int... 4
checking for long long int... yes
checking size of long long int... 8
checking for unsigned int... yes
checking size of unsigned int... 4
checking for unsigned long int... yes
checking size of unsigned long int... 4
checking for unsigned long long int... yes
checking size of unsigned long long int... 8
checking for u_int8_t... yes
checking for u_int16_t... yes
checking for u_int32_t... yes
checking for u_int64_t... yes
checking for uint8_t... yes
checking for uint16_t... yes
checking for uint32_t... yes
checking for uint64_t... yes
checking for int8_t... yes
checking for int16_t... yes
checking for int32_t... yes
checking for int64_t... yes
checking for INADDR_NONE... yes
checking for __FUNCTION__... yes
checking for pcap_datalink in -lpcap... no
checking pfring.h usability... no
checking pfring.h presence... no
checking for pfring.h... no
checking for pfring_open in -lpfring... no
checking for pfring_open in -lpcap... no

   ERROR!  Libpcap library/headers (libpcap.a (or .so)/pcap.h)
   not found, go get it from http://www.tcpdump.org
   or use the --with-libpcap-* options, if you have it installed
   in unusual place.  Also check if your libpcap depends on another
   shared library that may be installed in an unusual place
```

---

### Post by sisco311 on 2010-03-03
You have to install the build dependencies:
```
sudo apt-get build-dep snort
```

---

### Post by latgarf on 2010-03-05
I had the same problem, which I solved by installing the 
**libpcap0.8-dev **
packet via Synaptic.

However, now the next problem appeared:

checking for INADDR_NONE... yes
checking for __FUNCTION__... yes
checking for pcap_datalink in -lpcap... yes
checking for sparc... no
checking for mysql... 

**********************************************
  ERROR: unable to find mysql headers (mysql.h)
  checked in the following places
        /usr
        /usr/include
        /usr/include/mysql
        /usr/mysql
        /usr/mysql/include
        /usr/local
        /usr/local/include
        /usr/local/include/mysql
        /usr/local/mysql
        /usr/local/mysql/include
**********************************************

---

### Post by sisco311 on 2010-03-05
> **latgarf said:**
> I had the same problem, which I solved by installing the 
**libpcap0.8-dev **
packet via Synaptic.

However, now the next problem appeared:

checking for INADDR_NONE... yes
checking for __FUNCTION__... yes
checking for pcap_datalink in -lpcap... yes
checking for sparc... no
checking for mysql... 

**********************************************
  ERROR: unable to find mysql headers (mysql.h)
  checked in the following places
        /usr
        /usr/include
        /usr/include/mysql
        /usr/mysql
        /usr/mysql/include
        /usr/local
        /usr/local/include
        /usr/local/include/mysql
        /usr/local/mysql
        /usr/local/mysql/include
**********************************************

You must install libmysqlclient15-dev, but you need other dependencies as well.

Go to System -> Administration -> Software Sources and make sure that the *Source code* check box is selected.

Then run:
```
sudo apt-get build-dep snort
```to download the dependencies.

---

