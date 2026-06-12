---
title: "making webcams work"
date: 2009-09-27
forum: General Help
---

### Post by starcraftmaster on 2009-09-27
hello i got two web cams
one is a logitech (unknown model)
and a other creative pd1001

none of them work in amsn

do you know how i can get them to work ?

---

### Post by starcraftmaster on 2009-09-28
any one ?

---

### Post by starcraftmaster on 2009-09-30
any one ?:cry:

---

### Post by Giblet5 on 2009-09-30
[This might help]("https://help.ubuntu.com/community/Webcam").

---

### Post by starcraftmaster on 2009-10-01
it seems easycam can do what i want
but it only meant to work on ubuntu 8.04
has any one tried it on ubuntu 9.04

---

### Post by starcraftmaster on 2009-10-01
well i found some thing that may work
the qc-usb driver
but i got no clue how to install it 
this what it says to do :

Installation

This section explains how to compile and install the qc-usb driver for the Linux kernel. For the most current instructions, please read the README that comes with the driver. These instructions explain how to compile the driver as a standalone module, which is the only option at this time because the driver has not (yet) been integrated into the mainline kernel.

The following requirements must be met:
Kernel >= 2.2.18, kernel 2.4.x, or kernel 2.6.x with USB and V4L support. If you are running a version 2.2 kernel, you really need to upgrade to at least 2.4.
Kernel source for the kernel you are running. The symbolic link /lib/modules/`uname -r`/build should point to the source directory.
A working installation of gcc >= 2.95
Download the driver as described in the Download section and type the following to extract the source files (where X.XX is the current version number): 
$ tar zxvf qc-usb-X.XX.tar.gz
Compiling the source should then be a case of simply of cd-ing to the new qc-usb-X.XX directory and executing the following command: 
$ make all
After a few moments the compiler will produce a loadable kernel module (LKM) named quickcam.ko for kernel 2.6.x or quickcam.o for kernel 2.4.x.

If the USB and V4L modules are already loaded, then you can load the module by typing one of the following commands (as root). For a 2.6.x kernel: 
# insmod ./quickcam.ko
Or, for kernel 2.4.x: 
# insmod ./quickcam.o
Once the quickcam module has been successfully loaded, it is time to fire up your favorite V4L application to start viewing pictures from the webcam.

---

### Post by starcraftmaster on 2009-10-02
any one ?

---

### Post by P4man on 2009-10-02
before starting to compile drivers, perhaps you might give us the exact model types. open a terminal and type

```
lsusb
```
(=LSUSB in lowercase)

And copy/paste the output here. That will give all details for your USB devices.

---

### Post by starcraftmaster on 2009-10-02
lsusb
Bus 001 Device 006: ID 046d:0850 Logitech, Inc. QuickCam Web
Bus 001 Device 005: ID 07b2:5101 Motorola BCS, Inc. SurfBoard SB5101 Cable Modem
Bus 001 Device 004: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 001 Device 003: ID 0416:5518 Winbond Electronics Corp. 4-Port Hub
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



and with the creative webcam
Bus 001 Device 007: ID 041e:400d Creative Technology, Ltd WebCam PD1001
Bus 001 Device 005: ID 07b2:5101 Motorola BCS, Inc. SurfBoard SB5101 Cable Modem
Bus 001 Device 004: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 001 Device 003: ID 0416:5518 Winbond Electronics Corp. 4-Port Hub
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by starcraftmaster on 2009-10-03
.

---

### Post by starcraftmaster on 2009-10-04
any one ?

---

### Post by starcraftmaster on 2009-10-05
:(

---

### Post by starcraftmaster on 2009-10-07
come on guys:(

does no one know what this means:

Installation

This section explains how to compile and install the qc-usb driver for the Linux kernel. For the most current instructions, please read the README that comes with the driver. These instructions explain how to compile the driver as a standalone module, which is the only option at this time because the driver has not (yet) been integrated into the mainline kernel.

The following requirements must be met:
Kernel >= 2.2.18, kernel 2.4.x, or kernel 2.6.x with USB and V4L support. If you are running a version 2.2 kernel, you really need to upgrade to at least 2.4.
Kernel source for the kernel you are running. The symbolic link /lib/modules/`uname -r`/build should point to the source directory.
A working installation of gcc >= 2.95
Download the driver as described in the Download section and type the following to extract the source files (where X.XX is the current version number): 
$ tar zxvf qc-usb-X.XX.tar.gz
Compiling the source should then be a case of simply of cd-ing to the new qc-usb-X.XX directory and executing the following command: 
$ make all
After a few moments the compiler will produce a loadable kernel module (LKM) named quickcam.ko for kernel 2.6.x or quickcam.o for kernel 2.4.x.

If the USB and V4L modules are already loaded, then you can load the module by typing one of the following commands (as root). For a 2.6.x kernel: 
# insmod ./quickcam.ko
Or, for kernel 2.4.x: 
# insmod ./quickcam.o
Once the quickcam module has been successfully loaded, it is time to fire up your favorite V4L application to start viewing pictures from the webcam.

---

### Post by davidmohammed on 2009-10-07
Hi there,
  I've tried and failed to get my PD1001 working since gutsy (the epcam driver code worked with that kernel)  - the later kernels seem to be incompatible with the old driver code you have found.  In the end, I bought a cheap ebay philips webcam - worked straight-away on Karmic.

---

### Post by davidmohammed on 2009-10-07
... as to the quickcam - looking on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/qc-usb/+bug/213114") it looks like you have to fiddle around with a kernel patch - does work though.

t

---

### Post by starcraftmaster on 2009-10-07
> **davidmohammed said:**
> ... as to the quickcam - looking on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/qc-usb/+bug/213114") it looks like you have to fiddle around with a kernel patch - does work though.

t

could you tell me how i would install and make it work ?

am a totally noob at linux :(

---

### Post by davidmohammed on 2009-10-07
... post #9 in that link showed what the guy did to compile and install - 

looks like the two "patch" files are contained in the zip attachment.  

Reading the last post, if you are using jaunty you will need to alter one of the source files using your favourite text editor (mine is gedit).

---

### Post by starcraftmaster on 2009-10-08
the only zip files there are:qc-usb-patches.zip (1.5 KiB, text/plain)

how would i intall them ?

---

### Post by davidmohammed on 2009-10-08
...  I presume 

from a terminal window
```

mkdir quickcam
```
click on the zip and extract into the quickcam directory
```

sudo -i
apt-get install qc-usb-source qc-usb-utils
cd /usr/src
tar xvfj qc-usb.tar.bz2
cd modules/qc-usb
patch < ~/quickcam/patch1
patch < ~/quickcam/patch2

```

if you are using jaunty make the changes to the source file as described in the final post then
```

make
install
exit

```

Hope this helps - can't test this myself since I dont have a quickcam.

---

### Post by starcraftmaster on 2009-10-10
nope did'nt work
hes the terminal info(saw some errors)

root@PackardBell:~/quickcam# sudo -i
root@PackardBell:~# apt-get install qc-usb-source qc-usb-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
qc-usb-source is already the newest version.
qc-usb-utils is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenal1 libclucene0ldbl librdf0 xchat-common kdebase-runtime-data-common
  libgda3-common libdiscid0 cheese fortunes-min libtagc0 libnotify-bin libapr1
  kde-icons-oxygen fortune-mod libexiv2-5 librasqal1 openoffice.org-l10n-pt-br
  libsoprano4 redland-utils librecode0 tidy docbook-defguide
  openoffice.org-help-pt-br kdelibs5-data cvs oss-compat python-xml
  libtunepimp5 thunar-data imagemagick-doc libgda3-bin libgda3-3 libpq5
  imagemagick exiv2 soprano-daemon kdebase-runtime-data libgdl-1-0 quanta-data
  libsdl-image1.2 libgdl-1-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@PackardBell:~# cd /usr/src
root@PackardBell:/usr/src# tar xvfj qc-usb.tar.bz2
modules/
modules/qc-usb/
modules/qc-usb/debian/
modules/qc-usb/debian/compat
modules/qc-usb/debian/control.modules.in
modules/qc-usb/debian/postinst.modules.in
modules/qc-usb/debian/rules
modules/qc-usb/debian/copyright
modules/qc-usb/debian/changelog
modules/qc-usb/debian/docs
modules/qc-usb/qc-driver.c
modules/qc-usb/qc-formats.c
modules/qc-usb/qc-hdcs.c
modules/qc-usb/qc-memory.c
modules/qc-usb/qc-mjpeg.c
modules/qc-usb/qc-pb0100.c
modules/qc-usb/qc-vv6410.c
modules/qc-usb/qc-memory.h
modules/qc-usb/quickcam.h
modules/qc-usb/videodev2.h
modules/qc-usb/videodevfix.h
modules/qc-usb/Makefile
modules/qc-usb/FAQ
modules/qc-usb/qcweb-info.txt
modules/qc-usb/README.qce
modules/qc-usb/TODO
root@PackardBell:/usr/src# cd modules/qc-usb
root@PackardBell:/usr/src/modules/qc-usb# patch < ~/quickcam/patch1
patching file qc-driver.c
Reversed (or previously applied) patch detected!  Assume -R? [n] 
Apply anyway? [n] 
Skipping patch.
2 out of 2 hunks ignored -- saving rejects to file qc-driver.c.rej
root@PackardBell:/usr/src/modules/qc-usb# patch < ~/quickcam/patch1
patching file qc-driver.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 2554 (offset 26 lines).
Hunk #2 succeeded at 3033 (offset 26 lines).
root@PackardBell:/usr/src/modules/qc-usb# patch < ~/quickcam/patch2
patching file qc-driver.c
Hunk #1 FAILED at 2255.
Hunk #2 FAILED at 2311.
Hunk #3 FAILED at 2383.
Hunk #4 FAILED at 2435.
Hunk #5 FAILED at 2494.
Hunk #6 FAILED at 2530.
Hunk #7 FAILED at 3189.
7 out of 7 hunks FAILED -- saving rejects to file qc-driver.c.rej
root@PackardBell:/usr/src/modules/qc-usb# patch < ~/quickcam/patch2
patching file qc-driver.c
Hunk #1 FAILED at 2255.
Hunk #2 FAILED at 2311.
Hunk #3 FAILED at 2383.
Hunk #4 FAILED at 2435.
Hunk #5 FAILED at 2494.
Hunk #6 FAILED at 2530.
Hunk #7 FAILED at 3189.
7 out of 7 hunks FAILED -- saving rejects to file qc-driver.c.rej
root@PackardBell:/usr/src/modules/qc-usb# make]
-bash: make]: command not found
root@PackardBell:/usr/src/modules/qc-usb# make
make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/usr/src/modules/qc-usb modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /usr/src/modules/qc-usb/qc-driver.o
/usr/src/modules/qc-usb/qc-driver.c: In function &#8216;qc_v4l_ioctl&#8217;:
/usr/src/modules/qc-usb/qc-driver.c:2557: error: &#8216;struct video_device&#8217; has no member named &#8216;type&#8217;
/usr/src/modules/qc-usb/qc-driver.c: At top level:
/usr/src/modules/qc-usb/qc-driver.c:3036: error: unknown field &#8216;type&#8217; specified in initialiser
make[2]: *** [/usr/src/modules/qc-usb/qc-driver.o] Error 1
make[1]: *** [_module_/usr/src/modules/qc-usb] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [all] Error 2
root@PackardBell:/usr/src/modules/qc-usb# install
install: missing file operand
Try `install --help' for more information.
root@PackardBell:/usr/src/modules/qc-usb#

---

### Post by jmdsdf on 2009-11-14
I have pretty much exactly the same two cameras, and have too been thinking about just buying a Linux compatible web cam! I have not been able to get either to work. I have been able to get the qc-usb driver compiled and installed, but it crashes my computer so badly that Alt-Sys-REISUB won't reboot it. Here's how you too can install the driver:

```
~$ su -
~# apt-get install qc-usb-source
~# cd /usr/src
/usr/src# tar xvfj qc-usb.tar.bz2
/usr/src# cd modules/qc-usb/
/usr/src/modules/qc-usb# patch -p1 < kcompat-2.6.30.patch
/usr/src/modules/qc-usb# make clean
/usr/src/modules/qc-usb# make all
/usr/src/modules/qc-usb# make install
```

Plug in the camera, remove the gspca drivers, then:

```
/usr/src/modules/qc-usb# insmod quickcam.ko
```

Download the kcompat patch from [http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/31081f6cd878b6db](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/31081f6cd878b6db) It's the last link.

I can't for the life of me get the epcam driver installed for the PD1001. It works on older kernels, but I think after 2.6.28 I've been out of luck.

---

