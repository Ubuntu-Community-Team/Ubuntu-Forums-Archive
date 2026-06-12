---
title: "Mplayer/xmms/GLIB Problem..."
date: 2006-04-09
forum: General Help
---

### Post by ahwei on 2006-04-09
I just want to install the Mplayer in order to watch my .avi movies. One leads to another depencies problem. 

First I have to clear a list of depencies when installing the Mplayer

- libfaad2.0
- libdirectfb-0.9-22
- libggi2 (>=1.2.0.5)
- libglib1.2 (>=1.2.0)
- libgtk1.2 (>=1.2.10-4)
- libjack0.80.0-0 (>=0.99.0)
- libmad0
- libungif4g
.
.
.
the list grows. I managed to 'clear' all the depencies (spent hours on it) using combination methods of google search + manual download + dpkg install + Synaptic.... and now left only one:

mplayer-386:
 Depends: xmms (>=1.2.10+cvs20050209) but it is not installable

OK. Did the same routine search again and got the source code download. Run the ./configure after tar and the result: 

ahwei@ahwei:~$ cd xmms-1.2.10
ahwei@ahwei:~/xmms-1.2.10$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for prefix by checking for xmms... no
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking whether byte ordering is bigendian... no
checking for inline... inline
checking for an ANSI C-conforming const... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking whether -lc should be explicitly linked in... no
creating libtool
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for glib-config... no
checking for GLIB - version >= 1.2.2... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

Oh my. One create another. Starting to feel annoyed. Managed to find out the  archieve tag gz "glib-1.2.10.tar.gz" run the ./configure again, all passed and starting to make and the make install. And you guess it, another problem occurs: 

.
.
.
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D _REENTRANT -c gstrfuncs.c  -fPIC -DPIC -o .libs/gstrfuncs.lo
gstrfuncs.c: In function 'g_printf_string_upper_bound':
gstrfuncs.c:870: error: syntax error before string constant
gstrfuncs.c:1037: error: syntax error before string constant
gstrfuncs.c:1080: error: syntax error before string constant
gstrfuncs.c:1111: error: syntax error before string constant
gstrfuncs.c: In function 'g_strdown':
gstrfuncs.c:1139: warning: pointer targets in assignment differ in signedness
gstrfuncs.c: In function 'g_strup':
gstrfuncs.c:1155: warning: pointer targets in assignment differ in signedness
gstrfuncs.c: In function 'g_strchug':
gstrfuncs.c:1314: warning: pointer targets in assignment differ in signedness
gstrfuncs.c:1317: warning: pointer targets in passing argument 1 of 'strlen' dif fer in signedness
make[2]: *** [gstrfuncs.lo] Error 1
make[2]: Leaving directory `/home/ahwei/glib-1.2.10'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ahwei/glib-1.2.10'
make: *** [all-recursive-am] Error 2

ahwei@ahwei:~/glib-1.2.10$ make install
Making install in .
make[1]: Entering directory `/home/ahwei/glib-1.2.10'
/bin/sh ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN= g_log_domain_glib     -g -O2 -Wall  -D_REENTRANT -c gstrfuncs.c
rm -f .libs/gstrfuncs.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D _REENTRANT -c gstrfuncs.c  -fPIC -DPIC -o .libs/gstrfuncs.lo
gstrfuncs.c: In function 'g_printf_string_upper_bound':
gstrfuncs.c:870: error: syntax error before string constant
gstrfuncs.c:1037: error: syntax error before string constant
gstrfuncs.c:1080: error: syntax error before string constant
gstrfuncs.c:1111: error: syntax error before string constant
gstrfuncs.c: In function 'g_strdown':
gstrfuncs.c:1139: warning: pointer targets in assignment differ in signedness
gstrfuncs.c: In function 'g_strup':
gstrfuncs.c:1155: warning: pointer targets in assignment differ in signedness
gstrfuncs.c: In function 'g_strchug':
gstrfuncs.c:1314: warning: pointer targets in assignment differ in signedness
gstrfuncs.c:1317: warning: pointer targets in passing argument 1 of 'strlen' dif fer in signedness
make[1]: *** [gstrfuncs.lo] Error 1
make[1]: Leaving directory `/home/ahwei/glib-1.2.10'
make: *** [install-recursive] Error 1


Now I am stucked. Anyone can help me before I giving up my ubuntu to becaue of this.... 


I am using Ubuntu 5.10 Breezy.

---

### Post by nanotube on 2006-04-10
ehrm... why are you installing all this from source?
if you just used apt-get, or sytaptic, to get the packages from the repositories, they would automatically pull all the dependencies!
now... i dont know what you have or have not yet installed... but i bet if you just try opening up synaptic package manager, searching for "mplayer", and installing the mplayer-386 package, everything will install and work. try it.

---

### Post by ahwei on 2006-04-10
I tried.. but it always said the package not available, for example I was trying to install the xmms: 

root@ahwei:/etc/apt# apt-get -f install xmms
Reading package lists... Done
Building dependency tree... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate
root@ahwei:/etc/apt#

Below is my sources.list, not sure if I missed out anything. I am now in Singapore... 

## Uncomment the following two lines to fetch updated software from the network
## deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
## deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
## deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
## deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Backports
## deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports main universe multiverse restricted
## deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted

I am quite noob, thus I appreciate if anyone can give me some advice... :mrgreen:

---

### Post by ahwei on 2006-04-10
Copy the sources.list an able to run the update now. Now I can watch .avi and .wmv extension. 

Thanks anyway

---

