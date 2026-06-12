---
title: "Manually installing a driver... need help"
date: 2012-06-22
forum: General Help
---

### Post by LouisLeRoi on 2012-06-22
Hi,   so I removed XP from a 2004 HP laptop and installed Ubuntu  instead... very impressed.   The only problem is that since Windows has  all the drivers written specifically for it this ati IGP 345m has much  worse image quality and slower scrolling etc etc in ubuntu.   Looking  around the web I red that a few other linux users with the same crap  card from ATI have much better perfomance using  xf86-video-ati-6.7.195.tar.gz   so I downloaded that and extracted and  went to the terminal and did the ./configure thing but it stops abruptly  and this is what I get 

&quot;   > 

aclocal.m4    config.h.in   COPYING    Makefile.am  README.ati        src
ChangeLog     config.sub    depcomp    Makefile.in  README.ati.sgml
compile       configure     install-sh    man         README.r128
config.guess  configure.ac  ltmain.sh    missing      README.r128.sgml
l:~/Downloads/xf86-video-ati-6.7.195$ configure
configure: command not found
:~/Downloads/xf86-video-ati-6.7.195$ sudo configure
[sudo] password for : 
sudo: configure: command not found
:~/Downloads/xf86-video-ati-6.7.195$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
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
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking if XINERAMA is defined... no
checking if RANDR is defined... no
checking if RENDER is defined... no
checking if XV is defined... no
checking if XF86MISC is defined... no
checking if DPMSExtension is defined... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... configure: error: Package requirements (xorg-server >= 1.3 xproto fontsproto ) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'fontsproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
 


how does one go about installing this driver???

---

### Post by pbrane on 2012-06-22
first thing you might do is check out [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=") and have a look at the fglrx-installer. Maybe that will work for you. It would be better to install a deb package.

Second if you want to build from source or the x-swat ppa doesn't work for you then resolve the 
```



No package 'xorg-server' found
No package 'xproto' found
No package 'fontsproto' found


``` issues.

probably you just need to install the dev packages.

Try running these commands in a terminal
```

sudo apt-get install xserver-xorg-dev
sudo apt-get install x11proto-core-dev

```

Not sure about the fontsproto, it may be part of the x11proto-core-dev package.

Also you may be able to install the compiled source using *checkinstall*. You may have to install the package first. But checkinstall will build a deb package from the source and then you can remove the driver easily.

And in case you haven't seen this:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by dino99 on 2012-06-22
[http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-file](http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-file)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by LouisLeRoi on 2012-06-22
thanks pbrane those terminal commands worked but it is asking me for even more stuff:


> checking for /usr/include/xorg/damage.h... yes
checking whether to include DRI support... yes
checking for DRI... configure: error: Package requirements (libdrm >= 2.2 xf86driproto) were not met:

No package 'libdrm' found
No package 'xf86driproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DRI_CFLAGS
and DRI_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details. following a monkey logic I tried your terminal commands again but didn't work:

> lq:~/Downloads/xf86-video-ati-6.7.195$ sudo apt-get install libdrm
[sudo] password for l..s: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libdrm
only now I understand that in order to install the drive you have to compile it first...


 ati cards are a cancer, never again. 

 > **Accelerated 3D support**

 All these Radeon(HD) cards and derivatives have good 3D acceleration support 

R100                        Radeon 7200 RV100                       Radeon 7000(VE), M6, RN50/ES1000 RS100                       Radeon IGP320(M) RV200                       Radeon 7500, M7, FireGL 7800 RS200                       Radeon IGP330(M)/IGP340(M) not really no, I can tell you that for RS200 I get a "driver unknown" and
 2d unity and no hardware acceleration

---

### Post by pbrane on 2012-06-22
you need the -dev files for those libraries. Look in synaptic package manager for the names of the library files and their -dev counterparts.

---

### Post by LouisLeRoi on 2012-06-22
thx again Pbrane, it worked and 'config' made a bunch of new files:

> config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating config.h
config.status: executing depfiles commands
l:~/Downloads/xf86-video-ati-6.7.195$ makefile
makefile: command not found
l:~/Downloads/xf86-video-ati-6.7.195$ sudo makefile
[sudo] password for ls: 
sudo: makefile: command not found
l:~/Downloads/xf86-video-ati-6.7.195$ ./Makefike
bash: ./Makefike: No such file or directory
loq:~/Downloads/xf86-video-ati-6.7.195$ ./Makefile
bash: ./Makefile: Permission denied
 now I'll try to get Makefile to run, somehow, and then it's just 'install' right??

 edit:

 'make' worked and it asked me for even more dev files, like glxint.h and xf86resources.h  

 got tired of installing package after package in synaptics so here's a better way for anyone who just wants to download specific files

>  	sudo apt-get install apt-file sudo apt-file update apt-file search GL/gl.h

---

### Post by QIII on 2012-06-22
ATI cards are not "cancer".

Your card is no longer supported by a current ATI driver and the legacy ATI driver does not work with X server versions after 2008.

You are left with the default open source Radeon driver.  The snippet you quoted is from the Community Help page about the open source Radeon and Gallium3D drivers.

In case you were wondering, Linux support has also been dropped for many older NVIDIA cards.

---

### Post by LouisLeRoi on 2012-06-22
I found that out just before reading your post as 'xf86Resources.h' is not available anywhere in synaptic or apt get...



 ' gcc -DHAVE_CONFIG_H -I. -I. -I.. -fvisibility=hidden -I/usr/include/pixman-1 -I/usr/include/xorg -I/usr/include/libdrm -I/usr/include/X11/dri -g -O2 -Wall -MT atibus.lo -MD -MP -MF .deps/atibus.Tpo -c atibus.c  -fPIC -DPIC -o .libs/atibus.o
In file included from atimach64io.h:37:0,
                 from atibus.c:32:
atistruct.h:62:27: fatal error: xf86Resources.h: No such file or directory
compilation terminated.'


 ati cards are a cancer, this one has been cancer aids and syphilis from day one as I have seen laptops with equal specs that run much better because they have nvidia cards.

 
 Anyway unfortunately gonna have to give up on ubuntu and try some lighter linux or go back to xp (talking about cancers)

---

### Post by QIII on 2012-06-22
When ATI was ATI, Linux was poorly supported.

It is now AMD/ATI and things have changed.  That's part of the reason your chip is now in the trash heap.

If you were an AMD executive, would you want to expend the resources to maintain a mess for products that are old, rare and didn't work well to keep them current for an OS that represents 5% of the market?

The math doesn't work.

---

### Post by LouisLeRoi on 2012-06-22
one more reason for them to pick up all those old drivers and release them open source to the public.

 I can tell you that this 2004 HP laptop, a pentium 4 with 1g of ram is still perfect for browsing the internet, writing emails, mp3, vids etc... this materialism and consumerism of having to constantly upgrading your computer is stupid and there would be a great service for humanity in releasing something like a lightweight linux that runs well in old hardware

---

### Post by pbrane on 2012-06-22
Sorry, I didn't realize that ATI card was no longer supported. I wouldn't have had you install all those dev packages. (Next time I'll check first)

---

### Post by QIII on 2012-06-22
Not to worry.  You were trying to help.

The subject is a bit obscure.

My personal goal on the forum is to have a good answer at least 25% of the time!  :)

---

