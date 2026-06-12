---
title: "Touchpanel Support in Ubuntu"
date: 2006-03-13
forum: General Help
---

### Post by VinnyC on 2006-03-13
Greetings Ubuntu. As this is my first post let me start by saying thank you very much for such a great linux distribution. It looks like with the release of Dapper, Linux finally has the chance to become mainstream.

Now for why i'm posting today, I have recently had a bad experience trying to get touchpanels to work with ubuntu. Although there seems to be some xorg drivers for the various brands of touchpanels, I still can't seem to find one that will work correctly. In my possesion is a Redradio Relaytouch screen and a Xenarc 7" LCD touchscreen. Both of these and several other brands use the popular eGalax driver. 

Recently eGalax posted a driver on their website for ubuntu, however like the drivers for the other linux distributions on their site, they do not compile in ubuntu. They all fail in about the same place, the driver called tkusb. From what I can understand this is a kernel driver for the touchpanel.

Here is the error I get:
```


make[1]: Leaving directory `/home/cliqk/touchkit/diag'
make[1]: Entering directory `/home/cliqk/touchkit/usb'
make -C /lib/modules/2.6.15-17-386/build SUBDIRS=/home/cliqk/touchkit/usb module s
make[2]: Entering directory `/usr/src/linux-source-2.6.15-17'
  CC [M]  /home/cliqk/touchkit/usb/tkusb.o
/home/cliqk/touchkit/usb/tkusb.c: In function 'write_tscreen':
/home/cliqk/touchkit/usb/tkusb.c:359: warning: implicit declaration of function 'verify_area'
/home/cliqk/touchkit/usb/tkusb.c:371: warning: ignoring return value of 'copy_fr om_user', declared with attribute warn_unused_result
/home/cliqk/touchkit/usb/tkusb.c:406: warning: ignoring return value of 'copy_fr om_user', declared with attribute warn_unused_result
/home/cliqk/touchkit/usb/tkusb.c:412: warning: ignoring return value of 'copy_fr om_user', declared with attribute warn_unused_result
/home/cliqk/touchkit/usb/tkusb.c: In function 'read_tscreen':
/home/cliqk/touchkit/usb/tkusb.c:481: warning: ignoring return value of 'copy_to _user', declared with attribute warn_unused_result
/home/cliqk/touchkit/usb/tkusb.c:490: warning: ignoring return value of 'copy_to _user', declared with attribute warn_unused_result
/home/cliqk/touchkit/usb/tkusb.c: At top level:
/home/cliqk/touchkit/usb/tkusb.c:593: error: unknown field 'mode' specified in i nitializer
make[3]: *** [/home/cliqk/touchkit/usb/tkusb.o] Error 1
make[2]: *** [_module_/home/cliqk/touchkit/usb] Error 2
make[2]: Leaving directory `/usr/src/linux-source-2.6.15-17'
make[1]: *** [build_module] Error 2
make[1]: Leaving directory `/home/cliqk/touchkit/usb'
make: *** [all] Error 1

```

I have unpacked all kernel sources to /usr/src/

Then I ran 'make oldconfig' to get my settings. Then I even tried compiling the kernel by just typing 'make'. After waiting several hours the kernel was finished compiling successfully, but still no help with the touch driver.

You can download the drivers for yourself here:
[http://www.egalax.com/eg/drivers.htm](http://www.egalax.com/eg/drivers.htm)

Let me know if you have any better luck compiling. There is a part in the instructions which is very confusing. Perhaps, I've missed a step here... It says:
> 
3.2) change the directory to /touchkit then type make all
The touchKit driver will be rebuild. ( Some packages must be
installed and well configured ).

--

I have also discovered that ubuntu comes with a driver called touchkitusb. Is is possible that this is conflicting with the egalax provided tksub? If that is the case what good is a touchpanel driver with no calibration utility? Why doesn't Ubuntu or xorg have it's own calibration utility?

I would greatly appreciate it if someone could tell me if I am doing something wrong here or if the egalax driver is just busted.

Thanks for reading,
-VinnyC

---

### Post by LuisC-SM on 2006-03-25
Hi VinnyC

I've read this post the day I got nstalled eGalax TouchScreen on my box, but I was sure I will answer it ASA I finished installing it on Fedora Core 4 and Linspire 5.0 (So far from that :( ).
I could run it in Ubuntu Breezy and Linspire 5.0. On FC4 I had problems compiling the kernel sources, in fact, the only information provided in forums lead you to the release notes. So I quit (I'm not a programmer nor deeloper).
Going back to the main point, what I did last week was to install firs the packages you need (Then it worked like a charm, now I must be missing something 'cause I 'had to reformat my HD, later I tell u).
Before installing the Ubuntu version the manual says you need:
make, gcc, Tcl/Tk, glibc-devel, kernel-sources and xfree86-devel.
What I installed from synaptic was:
gcc
gcc3.4
g++
Tcl8.4 & Tcl8.4-dev
Tk8.4 & Tk8.4-dev
linux-kernel-2.6.12-10-386 (in my case)
xlibs-dev
x-dev

and the problem was to find glibc-devel.... because is a RPM package and this manual was written for Mandrake 8.x-9.x and RedHat 7.x-8.x.
So what I did was install a lot of libraries I cannot remember and whick aren't anymore in the cache files due to a problem when trying to install Mandrake hosed my box and after 10 hours I could get my HD back.
But I remember I installed some extrange libraries that pulled some other (dependencies), so here is all the libraries I installed and at the end you will see my compiling results.
> Instaló los paquetes siguientes:
binutils (2.16.1-2ubuntu6)
debconf-utils (1.4.56ubuntu2)
debhelper (4.9.5ubuntu1)
cpp-3.4 (3.4.4-6ubuntu8.1)
g++-3.4 (3.4.4-6ubuntu8.1)
gcc (4:4.0.1-3)
gcc-3.4 (3.4.4-6ubuntu8.1)
gcc-3.4-base (3.4.4-6ubuntu8.1)
gcc-4.0 (4.0.1-4ubuntu9)
libc6-dev (2.3.5-1ubuntu12.5.10.1)
libstdc++6-dev (3.4.4-6ubuntu8.1)
linux-kernel-headers (2.6.11.2-0ubuntu13)
libice-dev (1:6.3.5-4)
libsm-dev (1:6.0.4-4)
libx11-dev (1:6.2.1+cvs.20050722-8)
libxau-dev (1:0.1.2-2)
libxext-dev (1:6.4.3-3)
libxi-dev (1:1.3.0-2)
libxmu-dev (1:6.2.3-5)
libxmu-headers (1:6.2.3-5)
libxmuu-dev (1:6.2.3-5)
libxpm-dev (1:3.5.2-5)
libxrandr-dev (1:1.0.2-2)
libxt-dev (1:0.99.0+cvs.20050803-3)
libxtrap-dev (1:3.0.0-3)
libxtst-dev (1:1.13.0-2)
libxv-dev (1:2.2.0+cvs.20050712-3)
x-dev (6.8.99.15+cvs.20050722-1)
x11proto-core-dev (6.8.99.15+cvs.20050722-1)
x11proto-input-dev (1.3-1)
x11proto-kb-dev (1.0+cvs.20050817-1)
x11proto-randr-dev (1.1-1)
x11proto-record-dev (1.13-1)
x11proto-trap-dev (3.4-1)
x11proto-video-dev (2.2+cvs.20050712-1)
x11proto-xext-dev (6.9.99.0-1)
xlibs-dev (6.8.2-77)
xlibs-static-dev (6.8.2-77)
zlib1g-dev (1:1.2.3-3ubuntu4)
linux-source-2.6.12 (2.6.12-10.30)
build-essential (11.1)
g++ (4:4.0.1-3)
g++-4.0 (4.0.1-4ubuntu9)
kernel-package (9.001ubuntu5)
libaudio-dev (1.7-2ubuntu2)
libexpat1-dev (1.95.8-3)
libfontconfig1-dev (2.3.2-1ubuntu4)
libfreetype6-dev (2.1.7-2.4ubuntu1)
libgl1-mesa-dev (6.3.2-0ubuntu6breezy1)
libglu1-mesa-dev (6.3.2-0ubuntu6breezy1)
libjpeg62-dev (6b-10)
liblcms1-dev (1.13-1)
libmng-dev (1.0.8-1)
libncurses5-dev (5.4-9ubuntu4)
libpng12-dev (1.2.8rel-1ubuntu3)
libqt3-headers (3:3.3.4-8ubuntu5)
libqt3-mt (3:3.3.4-8ubuntu5)
libqt3-mt-dev (3:3.3.4-8ubuntu5)
libstdc++6-4.0-dev (4.0.1-4ubuntu9)
libxcursor-dev (1.1.4-0ubuntu5)
libxft-dev (2.1.7-1ubuntu5)
libxinerama-dev (1:1.1.0+cvs.20050821-1)
libxrender-dev (1:0.9.0-1)
qt3-dev-tools (3:3.3.4-8ubuntu5)
x11proto-gl-dev (1.4+cvs.20050524-5)
x11proto-render-dev (1:0.9.0-1)
x11proto-xinerama-dev (1.1-1)
tcl8.4-dev (8.4.9-1)
tk8.4-dev (8.4.9-1build1)
libdb4.2++-dev (4.2.52-19ubuntu4)
libdb4.2++c2 (4.2.52-19ubuntu4)
libdb4.2-dev (4.2.52-19ubuntu4)
libuclibc-dev (0.9.26-cvs20040816-5.1)
libuclibc0 (0.9.26-cvs20040816-5.1)
cpp-3.3 (1:3.3.6-8ubuntu1)
g++-3.3 (1:3.3.6-8ubuntu1)
gcc-3.3 (1:3.3.6-8ubuntu1)
libstdc++5-3.3-dev (1:3.3.6-8ubuntu1)
libusb-dev (2:0.1.10a-17ubuntu1)
linux-headers-2.6.12-10 (2.6.12-10.30)
linux-headers-2.6.12-10-386 (2.6.12-10.30)
dpkg-dev (1.13.10ubuntu4)
Of course u don't need all thouse libraries but I was so confused that I did not know what to install even when I made a lot of hours of research (I could say that more than 70 hours of research.

Results from compiling in $HOME/touchkit/include (I have a USB touchscreen so there must be made the first compilation with "make new".

> jose@kiosko-01:~/touchkit/include$ make new
rm -f configSTR.h configSTR.mak configINT.h configINT.mak touch.tcl
tclsh ../utility/tcl2h.tcl configSTR.tcl > configSTR.h
tclsh ../utility/tcl2mak.tcl configSTR.tcl > configSTR.mak
tclsh ../utility/tcl2h.tcl configINT.tcl > configINT.h
tclsh ../utility/tcl2mak.tcl configINT.tcl > configINT.mak
tclsh ../utility/ini2tcl.tcl touch.ini > touch.tcl
jose@kiosko-01:~/touchkit/include$

cd .. and "make all"
>  Building modules, stage 2.
  MODPOST
  LD [M]  /home/jose/touchkit/usb/tkusb.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: Leaving directory `/home/jose/touchkit/usb'
: '+-----------------------------------+'
: '|  Build-All Complete Successfully  |'
: '+-----------------------------------+'
jose@kiosko-01:~/touchkit$

make install results
> root@kiosko-01:~/touchkit# make install
cat: /tmp/.usb.on: No existe el fichero o el directorio
/bin/sh: line 0: test: too many arguments
(*) Install USB module [/lib/modules/2.6.12-9-386/kernel/drivers/usb/tkusb.ko]
(*) Install USB module [/lib/modules/2.6.12-9-386/kernel/sound/usb/tkusb.ko]
(*) Install USB module [/lib/modules/2.6.12-10-386/kernel/drivers/usb/tkusb.ko]
(*) Install USB module [/lib/modules/2.6.12-10-386/kernel/sound/usb/tkusb.ko]
(*) Install touch panel daemon [/usr/bin/tpaneld]
(*) Install configuration utility [/usr/bin/touchcfg]
(*) Install XFree86 driver [/usr/X11R6/lib/modules/input/touchkit_drv.o]
(*) Generate uninstall script [/usr/bin/uninstall_TouchKit]
(*) Update system starting up script [/etc/init.d/rc.local]
************************** Warning ****************************
** XF86Config-4: File not found
***************************************************************
+--------------------------------------+
|  Installation Complete Successfully  |
+--------------------------------------+

You can think that this is OK... but NOWAY....why?
Firs in the "touchcfg" command (desktop icon also) when I try to aling the screen, the blinking circles dissapear :( and sometimes freezes so theres is some workaround it should be made.
I will steel try to find out more... in the meantime, I would like someone to help me by telling me 2 things....

1. which is the equivalent Debian file of glibc-dev.RPM ???
2. when reffering to kernel-sources... my "uname -r" cmd says: 2.6.12-10-386
so I believe that downloading "linux-source-2.6.12 (2.6.12-10.30), and "un-taring" with "tar --bzip2 -xvf linux-source-2.6.12.tar.bz2"  and by linking with: "ln -s /usr/src/linux-source-2.6.12 /usr/src/linux" is all I must do????

Regards

Luis C. Suárez

PS. I Cannot answer your questions 'cause I don't know where u found the touchkitusb driver

**[COLOR="DarkRed"]Edited:[/COLOR]**
Now is working only by changing to a diferent USB Port :) .. I didn't know I had 2 USB versions in the same MB.

---

