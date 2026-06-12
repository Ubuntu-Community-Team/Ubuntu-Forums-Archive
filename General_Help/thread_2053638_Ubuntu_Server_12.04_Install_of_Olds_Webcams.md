---
title: "Ubuntu Server 12.04 Install of Olds Webcams"
date: 2012-09-05
forum: General Help
---

### Post by Myke974 on 2012-09-05
Hey There !
I'm going to use 1 PC with Ubuntu Server 12.04 LTS x64
and 1 PC under windows with firefox + chrome brownsers.
I have 2 olds welcam : 1 in usb 1 i think and one cheap -10$ ebay
I have some few died laptop around : will it be possible to take off their webcams and re-use them onto server ?
I plug the first Webcam in ubuntu PC and I check the 8 last lines of syslog with:
tail -n 8 /var/log/syslog
```
Sep  6 02:17:01 house-server CRON[28578]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  6 02:23:25 house-server kernel: [ 4649.152015] usb 1-1: new high-speed USB device number 2 using ehci_hcd
Sep  6 02:23:25 house-server kernel: [ 4649.296445] Linux video capture interface: v2.00
Sep  6 02:23:25 house-server kernel: [ 4649.300611] gspca_main: v2.14.0 registered
Sep  6 02:23:25 house-server kernel: [ 4649.301301] gspca_main: sn9c20x-2.14.0 probing 0c45:6242
Sep  6 02:23:25 house-server kernel: [ 4649.321806] gspca_sn9c20x: MT9M111 sensor detected
Sep  6 02:23:25 house-server kernel: [ 4649.321864] input: sn9c20x as /devices/pci0000:00/0000:00:0b.1/usb1/1-1/input/input5
Sep  6 02:23:25 house-server kernel: [ 4649.321986] usbcore: registered new interface driver sn9c20x
```Did i see usb 1.1 :?: :-k
now i make a
dir /dev/video*
```
/dev/video0
```Now time to test the webcam : I'm going to search internet about ffmpeg or something like that.
All help is Welcome ):P
#Myke974

---

### Post by Myke974 on 2012-09-05
cat /dev/video0 > ~/test.mpg
I wait 70 seconds and I used CTRL + C 
I got a 8Mo file I couldn't read with VLC ](*,)
Do I need a special codec ?[-(
Outpout of lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:6242 Microdia PC Camera (SN9C201 + MI1310)
```

---

### Post by Myke974 on 2012-09-06
sudo apt-get install ffmpeg
```
Setting up microdia-dkms (2009.01-0ubuntu1~ppa4j) ...
Removing old microdia-2009.01 DKMS files...

------------------------------
Deleting module version: 2009.01
completely from the DKMS tree.
------------------------------
Done.
Loading new microdia-2009.01 DKMS files...

Creating symlink /var/lib/dkms/microdia/2009.01/source ->
                 /usr/src/microdia-2009.01

DKMS: add completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.2.0-29-generic KVER=3.2.0-29-generic src=/var/lib/dkms/microdia/2009.01/build....(bad exit status: 2)
Error! Bad return status for module build on kernel: 3.2.0-29-generic (x86_64)
Consult /var/lib/dkms/microdia/2009.01/build/make.log for more information.
dpkg: error processing microdia-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 microdia-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
```hum errors..let's check
cat /var/lib/dkms/microdia/2009.01/build/make.log
```
DKMS make.log for microdia-2009.01 for kernel 3.2.0-29-generic (x86_64)
Thu Sep  6 21:11:36 RET 2012
make -C /lib/modules/3.2.0-29-generic/build SUBDIRS=/var/lib/dkms/microdia/2009.01/build modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic'
  CC [M]  /var/lib/dkms/microdia/2009.01/build/sn9c20x-usb.o
  CC [M]  /var/lib/dkms/microdia/2009.01/build/sn9c20x-v4l2.o
/var/lib/dkms/microdia/2009.01/build/sn9c20x-v4l2.c: In function ‘v4l_sn9c20x_ioctl’:
/var/lib/dkms/microdia/2009.01/build/sn9c20x-v4l2.c:1322:2: warning: passing argument 1 of ‘video_ioctl2’ from incompatible pointer type [enabled by default]
include/media/v4l2-ioctl.h:326:13: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/var/lib/dkms/microdia/2009.01/build/sn9c20x-v4l2.c:1322:2: warning: passing argument 2 of ‘video_ioctl2’ makes integer from pointer without a cast [enabled by default]
include/media/v4l2-ioctl.h:326:13: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/var/lib/dkms/microdia/2009.01/build/sn9c20x-v4l2.c:1322:2: error: too many arguments to function ‘video_ioctl2’
include/media/v4l2-ioctl.h:326:13: note: declared here
/var/lib/dkms/microdia/2009.01/build/sn9c20x-v4l2.c: In function ‘v4l_sn9c20x_register_video_device’:
/var/lib/dkms/microdia/2009.01/build/sn9c20x-v4l2.c:1376:18: warning: assignment from incompatible pointer type [enabled by default]
/var/lib/dkms/microdia/2009.01/build/sn9c20x-v4l2.c: At top level:
/var/lib/dkms/microdia/2009.01/build/sn9c20x-v4l2.c:1459:2: error: unknown field ‘ioctl’ specified in initializer
/var/lib/dkms/microdia/2009.01/build/sn9c20x-v4l2.c:1459:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/microdia/2009.01/build/sn9c20x-v4l2.c:1459:2: warning: (near initialization for ‘v4l_sn9c20x_fops.open’) [enabled by default]
/var/lib/dkms/microdia/2009.01/build/sn9c20x-v4l2.c:1461:18: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
make[2]: *** [/var/lib/dkms/microdia/2009.01/build/sn9c20x-v4l2.o] Error 1
make[1]: *** [_module_/var/lib/dkms/microdia/2009.01/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'
make: *** [driver] Error 2
```

---

### Post by Myke974 on 2012-09-06
I checked [http://www.ideasonboard.org/uvc/#devices](http://www.ideasonboard.org/uvc/#devices)
for my
ID 0c45:6242 Microdia PC Camera (SN9C201 + MI1310)
and it is not in ! So does that mean it is not supported ?
sudo git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)
```
Cloning into 'microdia'...
```
Let take a look at the new folder now : ls microdia```

Doxyfile   Makefile  omnivision.c  sn9c20x-bridge.c   sn9c20x-dev.c    sn9c20x-sysfs.c
hv7131r.c  micron.c  omnivision.h  sn9c20x-bridge.h   sn9c20x.h        sn9c20x-usb.c
Kconfig    micron.h  README        sn9c20x-debugfs.c  sn9c20x-queue.c  sn9c20x-v4l2.c
```
Ah there is a README File !
> Most video applications do not support the image encoding SN9C20x-based
   webcams offer. Such applications need to have the image stream converted
   for them. This can be done using "libv4l", which is pre-loaded between the
   application and the video resource and translates the image stream into a
   usable format.
   Most distributions offer precompiled packages. If yours does not, the
   sources are available here :
     [http://freshmeat.net/projects/libv4l/](http://freshmeat.net/projects/libv4l/)
sudo apt-get install v4l-utils
```
Get:1 http://re.archive.ubuntu.com/ubuntu/ precise-updates/universe v4l-utils amd64 0.8.6-1ubuntu2 [117 kB]
Fetched 117 kB in 3s (38.9 kB/s)
Selecting previously unselected package v4l-utils.
(Reading database ... 98663 files and directories currently installed.)
Unpacking v4l-utils (from .../v4l-utils_0.8.6-1ubuntu2_amd64.deb) ...
Setting up microdia-dkms (2009.01-0ubuntu1~ppa4j) ...
Removing old microdia-2009.01 DKMS files...

------------------------------
Deleting module version: 2009.01
completely from the DKMS tree.
------------------------------
Done.
Loading new microdia-2009.01 DKMS files...

Creating symlink /var/lib/dkms/microdia/2009.01/source ->
                 /usr/src/microdia-2009.01

DKMS: add completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.2.0-29-generic KVER=3.2.0-29-generic src=/var/lib/dkms/microdia/2009.01/build....(bad exit status: 2)
Error! Bad return status for module build on kernel: 3.2.0-29-generic (x86_64)
Consult /var/lib/dkms/microdia/2009.01/build/make.log for more information.
dpkg: error processing microdia-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up v4l-utils (0.8.6-1ubuntu2) ...
Errors were encountered while processing:
 microdia-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
again this error :o:o
let's try:
cd microdia
make
```
make -C /lib/modules/3.2.0-29-generic/build SUBDIRS=/home/myke974/PKwrk/microdia modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic'
  CC [M]  /home/myke974/PKwrk/microdia/sn9c20x-usb.o
  CC [M]  /home/myke974/PKwrk/microdia/sn9c20x-v4l2.o
  CC [M]  /home/myke974/PKwrk/microdia/sn9c20x-sysfs.o
  CC [M]  /home/myke974/PKwrk/microdia/sn9c20x-dev.o
  CC [M]  /home/myke974/PKwrk/microdia/sn9c20x-queue.o
/home/myke974/PKwrk/microdia/sn9c20x-queue.c:77:28: fatal error: linux/videodev.h: No such file or directory
compilation terminated.
make[2]: *** [/home/myke974/PKwrk/microdia/sn9c20x-queue.o] Error 1
make[1]: *** [_module_/home/myke974/PKwrk/microdia] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'
make: *** [driver] Error 2
```
I can see fatal error linux/videodev.h in sn9c20x-queue.c

---

