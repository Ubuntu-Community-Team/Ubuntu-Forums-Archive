---
title: "SuperPen Graphics Tablet on Ubuntu?"
date: 2009-08-04
forum: General Help
---

### Post by RobFS1 on 2009-08-04
I was wondering if there was a way that I could use the SuperPen Graphics Tablet, like the one sold on ThinkGeek at [http://www.thinkgeek.com/computing/keyboards-mice/5ede/]("http://www.thinkgeek.com/computing/keyboards-mice/5ede/") on Ubuntu 8.04. Thanks

---

### Post by Favux on 2009-08-04
Hi RobFS1,

You should be able to get it set up.  It looks like it's a rebranded UC-Logic tablet.  So at least the wizardpen driver should work.  See:

[https://help.ubuntu.com/community/TabletSetupWizardpenHardy173](https://help.ubuntu.com/community/TabletSetupWizardpenHardy173)

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

Hope this was helpful.

---

### Post by RobFS1 on 2009-08-05
Thanks So Much! I will try it when it gets here and get back to you.

---

### Post by RobFS1 on 2009-08-06
Can you help me with this?

```
rob@Rob:~$ wget http://www.kubuntu.dk/wizardpen/wizardpen-0.6.0.2.tar.gz
--10:50:59--  http://www.kubuntu.dk/wizardpen/wizardpen-0.6.0.2.tar.gz
           => `wizardpen-0.6.0.2.tar.gz'
Resolving www.kubuntu.dk... \212.97.132.151
Connecting to www.kubuntu.dk|212.97.132.151|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 645,572 (630K) [application/x-gzip]

100%[====================================>] 645,572      202.02K/s    ETA 00:00

10:51:02 (201.39 KB/s) - `wizardpen-0.6.0.2.tar.gz' saved [645572/645572]

rob@Rob:~$ tar -xvf wizardpen-0.6.0.2.tar.gz
wizardpen-0.6.0.2/
wizardpen-0.6.0.2/config.log
wizardpen-0.6.0.2/stamp-h1
wizardpen-0.6.0.2/Makefile.am
wizardpen-0.6.0.2/configure
wizardpen-0.6.0.2/configure.ac
wizardpen-0.6.0.2/libtool
wizardpen-0.6.0.2/ltmain.sh
wizardpen-0.6.0.2/copying
wizardpen-0.6.0.2/autogen.sh
wizardpen-0.6.0.2/config.h
wizardpen-0.6.0.2/Makefile
wizardpen-0.6.0.2/config.status
wizardpen-0.6.0.2/config.sub
wizardpen-0.6.0.2/install-sh
wizardpen-0.6.0.2/depcomp
wizardpen-0.6.0.2/config.h.in
wizardpen-0.6.0.2/config.guess
wizardpen-0.6.0.2/Makefile.in
wizardpen-0.6.0.2/missing
wizardpen-0.6.0.2/aclocal.m4
wizardpen-0.6.0.2/autom4te.cache/
wizardpen-0.6.0.2/man/
wizardpen-0.6.0.2/calibrate/
wizardpen-0.6.0.2/src/
wizardpen-0.6.0.2/autom4te.cache/output.0
wizardpen-0.6.0.2/autom4te.cache/requests
wizardpen-0.6.0.2/autom4te.cache/traces.0
wizardpen-0.6.0.2/man/wizardpen.4
wizardpen-0.6.0.2/man/Makefile.am
wizardpen-0.6.0.2/man/Makefile
wizardpen-0.6.0.2/man/wizardpen.man
wizardpen-0.6.0.2/man/Makefile.in
wizardpen-0.6.0.2/calibrate/install
wizardpen-0.6.0.2/calibrate/ChangeLog
wizardpen-0.6.0.2/calibrate/readme
wizardpen-0.6.0.2/calibrate/copying
wizardpen-0.6.0.2/calibrate/wizardpen-calibrate.c
wizardpen-0.6.0.2/calibrate/Makefile
wizardpen-0.6.0.2/calibrate/wizardpen-calibrate
wizardpen-0.6.0.2/src/wizardpen_drv.la
wizardpen-0.6.0.2/src/Makefile.am
wizardpen-0.6.0.2/src/wizardpen.lo
wizardpen-0.6.0.2/src/Makefile
wizardpen-0.6.0.2/src/wizardpen.c
wizardpen-0.6.0.2/src/wizardpen.h
wizardpen-0.6.0.2/src/Makefile.in
wizardpen-0.6.0.2/src/.deps/
wizardpen-0.6.0.2/src/.libs/
wizardpen-0.6.0.2/src/.deps/wizardpen.Plo
wizardpen-0.6.0.2/src/.libs/wizardpen_drv.la
wizardpen-0.6.0.2/src/.libs/wizardpen_drv.so
wizardpen-0.6.0.2/src/.libs/wizardpen.o
wizardpen-0.6.0.2/src/.libs/wizardpen_drv.lai
rob@Rob:~$ cd wizardpen-0.6.0.2
rob@Rob:~/wizardpen-0.6.0.2$ ./configure --with-xorg-module-dir=/usr/lib/xorg/modules
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking if RANDR is defined... no
checking if XINPUT is defined... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... configure: error: Package requirements (xorg-server >= 1.0.99.901 xproto ) were not met:

No package 'xorg-server' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

rob@Rob:~/wizardpen-0.6.0.2$ make
make  all-recursive
make[1]: Entering directory `/home/rob/wizardpen-0.6.0.2'
Making all in src
make[2]: Entering directory `/home/rob/wizardpen-0.6.0.2/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1    -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c -o wizardpen.lo wizardpen.c
 gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1 -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c wizardpen.c  -fPIC -DPIC -o .libs/wizardpen.o
In file included from wizardpen.c:28:
../config.h:4:25: error: xorg-server.h: No such file or directory
wizardpen.c:50:18: error: misc.h: No such file or directory
wizardpen.c:51:18: error: xf86.h: No such file or directory
wizardpen.c:55:25: error: xf86_OSproc.h: No such file or directory
wizardpen.c:56:18: error: xisb.h: No such file or directory
wizardpen.c:57:24: error: xf86Xinput.h: No such file or directory
wizardpen.c:58:22: error: exevents.h: No such file or directory
wizardpen.c:59:24: error: xf86Module.h: No such file or directory
In file included from wizardpen.c:76:
wizardpen.h:74: error: expected specifier-qualifier-list before 'XISBuffer'
wizardpen.h:105: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceControl'
wizardpen.h:106: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceOn'
wizardpen.h:107: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceOff'
wizardpen.h:108: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceClose'
wizardpen.h:109: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceInit'
wizardpen.h:110: warning: parameter names (without types) in function declaration
wizardpen.h:111: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ConvertProc'
wizardpen.h:112: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ReverseConvertProc'
wizardpen.h:113: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'QueryHardware'
wizardpen.h:115: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenGetPacket'
wizardpen.h:116: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenPreInit'
wizardpen.h:118: warning: parameter names (without types) in function declaration
wizardpen.h:119: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'USBQueryHardware'
wizardpen.h:121: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenAutoDevProbe'
wizardpen.c:92: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'InputDriverRec'
wizardpen.c: In function 'IsUSBLine':
wizardpen.c:179: error: 'X_PROBED' undeclared (first use in this function)
wizardpen.c:179: error: (Each undeclared identifier is reported only once
wizardpen.c:179: error: for each function it appears in.)
wizardpen.c: At top level:
wizardpen.c:196: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'fd_query_wizardpen'
wizardpen.c:216: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenAutoDevProbe'
wizardpen.c:336: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenPreInit'
wizardpen.c:500: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceControl'
wizardpen.c:527: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceOn'
wizardpen.c:571: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceOff'
wizardpen.c:596: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceClose'
wizardpen.c:606: error: expected ')' before 'dev'
wizardpen.c:614: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceInit'
wizardpen.c:716: error: expected ')' before 'local'
wizardpen.c:885: error: expected ')' before 'local'
wizardpen.c:895: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ConvertProc'
wizardpen.c:920: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ReverseConvertProc'
wizardpen.c:938: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'QueryHardware'
wizardpen.c:984: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'USBQueryHardware'
wizardpen.c: In function 'NewPacket':
wizardpen.c:1033: error: 'struct <anonymous>' has no member named 'packeti'
wizardpen.c: At top level:
wizardpen.c:1037: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenGetPacket'
make[2]: *** [wizardpen.lo] Error 1
make[2]: Leaving directory `/home/rob/wizardpen-0.6.0.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rob/wizardpen-0.6.0.2'
make: *** [all] Error 2
rob@Rob:~/wizardpen-0.6.0.2$ sudo make install
Making install in src
make[1]: Entering directory `/home/rob/wizardpen-0.6.0.2/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1    -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c -o wizardpen.lo wizardpen.c
 gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1 -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c wizardpen.c  -fPIC -DPIC -o .libs/wizardpen.o
In file included from wizardpen.c:28:
../config.h:4:25: error: xorg-server.h: No such file or directory
wizardpen.c:50:18: error: misc.h: No such file or directory
wizardpen.c:51:18: error: xf86.h: No such file or directory
wizardpen.c:55:25: error: xf86_OSproc.h: No such file or directory
wizardpen.c:56:18: error: xisb.h: No such file or directory
wizardpen.c:57:24: error: xf86Xinput.h: No such file or directory
wizardpen.c:58:22: error: exevents.h: No such file or directory
wizardpen.c:59:24: error: xf86Module.h: No such file or directory
In file included from wizardpen.c:76:
wizardpen.h:74: error: expected specifier-qualifier-list before 'XISBuffer'
wizardpen.h:105: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceControl'
wizardpen.h:106: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceOn'
wizardpen.h:107: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceOff'
wizardpen.h:108: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceClose'
wizardpen.h:109: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceInit'
wizardpen.h:110: warning: parameter names (without types) in function declaration
wizardpen.h:111: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ConvertProc'
wizardpen.h:112: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ReverseConvertProc'
wizardpen.h:113: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'QueryHardware'
wizardpen.h:115: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenGetPacket'
wizardpen.h:116: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenPreInit'
wizardpen.h:118: warning: parameter names (without types) in function declaration
wizardpen.h:119: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'USBQueryHardware'
wizardpen.h:121: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenAutoDevProbe'
wizardpen.c:92: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'InputDriverRec'
wizardpen.c: In function 'IsUSBLine':
wizardpen.c:179: error: 'X_PROBED' undeclared (first use in this function)
wizardpen.c:179: error: (Each undeclared identifier is reported only once
wizardpen.c:179: error: for each function it appears in.)
wizardpen.c: At top level:
wizardpen.c:196: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'fd_query_wizardpen'
wizardpen.c:216: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenAutoDevProbe'
wizardpen.c:336: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenPreInit'
wizardpen.c:500: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceControl'
wizardpen.c:527: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceOn'
wizardpen.c:571: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceOff'
wizardpen.c:596: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceClose'
wizardpen.c:606: error: expected ')' before 'dev'
wizardpen.c:614: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceInit'
wizardpen.c:716: error: expected ')' before 'local'
wizardpen.c:885: error: expected ')' before 'local'
wizardpen.c:895: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ConvertProc'
wizardpen.c:920: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ReverseConvertProc'
wizardpen.c:938: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'QueryHardware'
wizardpen.c:984: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'USBQueryHardware'
wizardpen.c: In function 'NewPacket':
wizardpen.c:1033: error: 'struct <anonymous>' has no member named 'packeti'
wizardpen.c: At top level:
wizardpen.c:1037: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenGetPacket'
make[1]: *** [wizardpen.lo] Error 1
make[1]: Leaving directory `/home/rob/wizardpen-0.6.0.2/src'
make: *** [install-recursive] Error 1

```

---

### Post by Favux on 2009-08-06
Hi RobFS1,

You are using Hardy correct?  I think the problem is it's looking for a newer Xserver.  I think Hardy's is 1.4, Intrepid 1.5, and Jaunty's is 1.6.  So it looks like this wizardpen driver (the newest?) is for Jaunty (and Intrepid?).  You need to find one for Hardy.

---

### Post by RobFS1 on 2009-08-07
It says on the page though, 

General information

This guide is based on *ubuntu 8.04 (Hardy Heron) after Xorg version 1.7.3.


# Oh, and by the way, my tablet came (obviously) and it's make and model is:

Manhattan Graphics Tablet; Model 174572

---

### Post by Favux on 2009-08-07
Hi RobFS1,

Well it's saying:
```
checking for XORG... configure: error: Package requirements (xorg-server >= 1.0.99.901 xproto ) were not met:

No package 'xorg-server' found
```
And then the rest of the errors look like it's complaining about not finding xserver-xorg.  Actually that may be a typo in the config file somewhere:
```
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
```
I think it means xorg-xserver and it's backwards.  Try searching in Synaptic Package Manager "xserver-xorg" and you'll find "xserver-xorg-core".

But according to this that's the right wizardpen driver version:  [http://digitalbluewave.blogspot.com/2009/03/wizardpen-ubuntu-904-and-everchanging.html](http://digitalbluewave.blogspot.com/2009/03/wizardpen-ubuntu-904-and-everchanging.html)

---

### Post by Favux on 2009-08-07
Hi RobFS1,

Did you do this part?:
```
sudo aptitude install xutils libx11-dev libxext-dev build-essential xautomation xinput xserver-xorg-dev
```
Made sure you got the entire line?  From Option 2 here:  [http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html)

---

### Post by RobFS1 on 2009-08-07
This is the output of that.


```
 sudo aptitude install xutils libx11-dev libxext-dev build-essential xautomation xinput xserver-xorg-dev
[sudo] password for rob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for xinput
Couldn't find any package whose name or description matched "xserver-xorg-dev"
No candidate version found for xinput
Couldn't find any package whose name or description matched "xserver-xorg-dev"
The following packages are BROKEN:
  g++ g++-4.3 libstdc++6-4.3-dev 
The following NEW packages will be installed:
  build-essential 
1 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/5527kB of archives. After unpacking 19.1MB will be used.
The following packages have unmet dependencies:
  libstdc++6-4.3-dev: Depends: gcc-4.3-base (= 4.3.3-5ubuntu4) which is a virtual package.
                      Depends: libstdc++6 (>= 4.3.3-5ubuntu4) but 4.2.4-1ubuntu4 is installed.
  g++-4.3: Depends: gcc-4.3-base (= 4.3.3-5ubuntu4) which is a virtual package.
           Depends: gcc-4.3 (= 4.3.3-5ubuntu4) which is a virtual package.
           Depends: libc6 (>= 2.8) but 2.7-10ubuntu4 is installed.
  g++: Depends: cpp (>= 4:4.3.3-1ubuntu1) but 4:4.2.3-1ubuntu6 is installed.
       Depends: gcc (>= 4:4.3.3-1ubuntu1) but 4:4.2.3-1ubuntu6 is installed.
       Depends: gcc-4.3 (>= 4.3.3-1) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
g++

Keep the following packages at their current version:
build-essential [Not Installed]
g++-4.3 [Not Installed]
libstdc++6-4.3-dev [Not Installed]

Score is -9794


```

---

### Post by RobFS1 on 2009-08-07
```
~/wizardpen-0.6.0.2$ ./configure --with-xorg-module-dir=/usr/lib/xorg/modules
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
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
checking for g++... no
checking for c++... no
checking for gpp... gpp
checking whether we are using the GNU C++ compiler... no
checking whether gpp accepts -g... no
checking dependency style of gpp... none
checking how to run the C++ preprocessor... /lib/cpp
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking whether the gpp linker (/usr/bin/ld) supports shared libraries... yes
libtool.m4: error: problem compiling CXX test program
checking for gpp option to produce PIC... 
checking if gpp static flag  works... yes
checking if gpp supports -c -o file.o... no
checking whether the gpp linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... unsupported
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking if RANDR is defined... no
checking if XINPUT is defined... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... configure: error: Package requirements (xorg-server >= 1.0.99.901 xproto ) were not met:

No package 'xorg-server' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

```
 make
make  all-recursive
make[1]: Entering directory `/home/rob/wizardpen-0.6.0.2'
Making all in src
make[2]: Entering directory `/home/rob/wizardpen-0.6.0.2/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1    -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c -o wizardpen.lo wizardpen.c
 gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1 -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c wizardpen.c  -fPIC -DPIC -o .libs/wizardpen.o
In file included from wizardpen.c:28:
../config.h:4:25: error: xorg-server.h: No such file or directory
wizardpen.c:50:18: error: misc.h: No such file or directory
wizardpen.c:51:18: error: xf86.h: No such file or directory
wizardpen.c:55:25: error: xf86_OSproc.h: No such file or directory
wizardpen.c:56:18: error: xisb.h: No such file or directory
wizardpen.c:57:24: error: xf86Xinput.h: No such file or directory
wizardpen.c:58:22: error: exevents.h: No such file or directory
wizardpen.c:59:24: error: xf86Module.h: No such file or directory
In file included from wizardpen.c:76:
wizardpen.h:74: error: expected specifier-qualifier-list before 'XISBuffer'
wizardpen.h:105: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceControl'
wizardpen.h:106: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceOn'
wizardpen.h:107: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceOff'
wizardpen.h:108: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceClose'
wizardpen.h:109: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceInit'
wizardpen.h:110: warning: parameter names (without types) in function declaration
wizardpen.h:111: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ConvertProc'
wizardpen.h:112: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ReverseConvertProc'
wizardpen.h:113: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'QueryHardware'
wizardpen.h:115: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenGetPacket'
wizardpen.h:116: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenPreInit'
wizardpen.h:118: warning: parameter names (without types) in function declaration
wizardpen.h:119: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'USBQueryHardware'
wizardpen.h:121: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenAutoDevProbe'
wizardpen.c:92: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'InputDriverRec'
wizardpen.c: In function 'IsUSBLine':
wizardpen.c:179: error: 'X_PROBED' undeclared (first use in this function)
wizardpen.c:179: error: (Each undeclared identifier is reported only once
wizardpen.c:179: error: for each function it appears in.)
wizardpen.c: At top level:
wizardpen.c:196: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'fd_query_wizardpen'
wizardpen.c:216: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenAutoDevProbe'
wizardpen.c:336: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenPreInit'
wizardpen.c:500: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceControl'
wizardpen.c:527: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceOn'
wizardpen.c:571: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceOff'
wizardpen.c:596: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceClose'
wizardpen.c:606: error: expected ')' before 'dev'
wizardpen.c:614: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceInit'
wizardpen.c:716: error: expected ')' before 'local'
wizardpen.c:885: error: expected ')' before 'local'
wizardpen.c:895: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ConvertProc'
wizardpen.c:920: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ReverseConvertProc'
wizardpen.c:938: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'QueryHardware'
wizardpen.c:984: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'USBQueryHardware'
wizardpen.c: In function 'NewPacket':
wizardpen.c:1033: error: 'struct <anonymous>' has no member named 'packeti'
wizardpen.c: At top level:
wizardpen.c:1037: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenGetPacket'
make[2]: *** [wizardpen.lo] Error 1
make[2]: Leaving directory `/home/rob/wizardpen-0.6.0.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rob/wizardpen-0.6.0.2'
make: *** [all] Error 2

```

```
 sudo make install
[sudo] password for rob: 
Making install in src
make[1]: Entering directory `/home/rob/wizardpen-0.6.0.2/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1    -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c -o wizardpen.lo wizardpen.c
 gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1 -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c wizardpen.c  -fPIC -DPIC -o .libs/wizardpen.o
In file included from wizardpen.c:28:
../config.h:4:25: error: xorg-server.h: No such file or directory
wizardpen.c:50:18: error: misc.h: No such file or directory
wizardpen.c:51:18: error: xf86.h: No such file or directory
wizardpen.c:55:25: error: xf86_OSproc.h: No such file or directory
wizardpen.c:56:18: error: xisb.h: No such file or directory
wizardpen.c:57:24: error: xf86Xinput.h: No such file or directory
wizardpen.c:58:22: error: exevents.h: No such file or directory
wizardpen.c:59:24: error: xf86Module.h: No such file or directory
In file included from wizardpen.c:76:
wizardpen.h:74: error: expected specifier-qualifier-list before 'XISBuffer'
wizardpen.h:105: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceControl'
wizardpen.h:106: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceOn'
wizardpen.h:107: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceOff'
wizardpen.h:108: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceClose'
wizardpen.h:109: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceInit'
wizardpen.h:110: warning: parameter names (without types) in function declaration
wizardpen.h:111: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ConvertProc'
wizardpen.h:112: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ReverseConvertProc'
wizardpen.h:113: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'QueryHardware'
wizardpen.h:115: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenGetPacket'
wizardpen.h:116: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenPreInit'
wizardpen.h:118: warning: parameter names (without types) in function declaration
wizardpen.h:119: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'USBQueryHardware'
wizardpen.h:121: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenAutoDevProbe'
wizardpen.c:92: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'InputDriverRec'
wizardpen.c: In function 'IsUSBLine':
wizardpen.c:179: error: 'X_PROBED' undeclared (first use in this function)
wizardpen.c:179: error: (Each undeclared identifier is reported only once
wizardpen.c:179: error: for each function it appears in.)
wizardpen.c: At top level:
wizardpen.c:196: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'fd_query_wizardpen'
wizardpen.c:216: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenAutoDevProbe'
wizardpen.c:336: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenPreInit'
wizardpen.c:500: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceControl'
wizardpen.c:527: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceOn'
wizardpen.c:571: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceOff'
wizardpen.c:596: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceClose'
wizardpen.c:606: error: expected ')' before 'dev'
wizardpen.c:614: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'DeviceInit'
wizardpen.c:716: error: expected ')' before 'local'
wizardpen.c:885: error: expected ')' before 'local'
wizardpen.c:895: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ConvertProc'
wizardpen.c:920: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ReverseConvertProc'
wizardpen.c:938: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'QueryHardware'
wizardpen.c:984: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'USBQueryHardware'
wizardpen.c: In function 'NewPacket':
wizardpen.c:1033: error: 'struct <anonymous>' has no member named 'packeti'
wizardpen.c: At top level:
wizardpen.c:1037: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'WizardPenGetPacket'
make[1]: *** [wizardpen.lo] Error 1
make[1]: Leaving directory `/home/rob/wizardpen-0.6.0.2/src'
make: *** [install-recursive] Error 1



```

---

### Post by Favux on 2009-08-07
Hi RobFS1,

You can't compile without build-essential, and apparently you don't have that installed.  So let's start with that.
```
sudo apt-get update

sudo apt-get install build-essential

sudo apt-get upgrade

```
And see where that gets us.

---

### Post by RobFS1 on 2009-08-07
```
 sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.3.1) but it is not going to be installed
E: Broken packages
```

---

### Post by Favux on 2009-08-07
Hi RobFS1,

Wow!  I don't know what's going on.  Something not good obviously.  What happens when you run System>Administration>Update Manager?

---

### Post by RobFS1 on 2009-08-07
It says that i dont have any updates to install...

---

### Post by Favux on 2009-08-07
Hi RobFS1,

OK, try going into Synaptic Package Manager.  Search 'build-essential'.  Is it installed?  If so tell it to reinstall.  Or try to install it if it isn't there.

---

### Post by RobFS1 on 2009-08-08
This is what it says when i try to do that: see attached screenshot.

---

### Post by Favux on 2009-08-08
Alright, what happens if you search 'g++' in Synaptic.  It's the GNU C++ compiler.  You need it to compile.  See if it will install, if it isn't.

---

### Post by RobFS1 on 2009-08-08
this is what it says: see the screenshot

---

### Post by Favux on 2009-08-08
Hi RobFS1,

I don't know why this is happening.  It should just install what you are asking and pull in the dependencies itself.  Or if things are messed up it should be talking about a corrupt package cache or something.  In Administration>Software Sources do you have at least main, universe, restricted, and multiverse selected?  With say Server from United States or something?

---

### Post by RobFS1 on 2009-08-08
Yes i have all of those things selected.

---

### Post by Favux on 2009-08-08
Go into Software Sources, it will ask for your password, and in the Ubuntu Software see what's selected (boxes checked).

---

### Post by RobFS1 on 2009-08-08
All of the prior stated boxes are selected.

---

### Post by Favux on 2009-08-08
Hi RobFS1,

How long have you had Hardy installed?  Have you spent a lot of time configuring it?

I'm asking because I have no clue what's wrong.  It seems like you have a corrupt install.  How big a deal would a reinstall be?  Maybe download and burn a new iso (at low speed)?

It's probably an over reaction but we've spent enough time dinking around going no where that you could have burned the iso and reinstalled by now.  I'm worried we'll keep wasting your time.

Or you could post on the Install & Upgrade forum or whatever and ask for help.

---

