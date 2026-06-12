---
title: "Webcam not working on Clevo D901C"
date: 2011-03-17
forum: General Help
---

### Post by pasoleatis on 2011-03-17
Yet another webcam problem. I am using Uuntu 10.04 on my computer, a D901C laptop. According to this site the driver is already included in the kernel:

[http://linuxlaptopwiki.net/wiki/Talk:Clevo_D901C#Webcam_driver_.28Ali_m5602.29](http://linuxlaptopwiki.net/wiki/Talk:Clevo_D901C#Webcam_driver_.28Ali_m5602.29)

a simple search gave 

:~$ locate gspca_m5602
/lib/modules/2.6.32-21-generic/kernel/drivers/media/video/gspca/m5602/gspca_m5602.ko
/lib/modules/2.6.32-28-generic/kernel/drivers/media/video/gspca/m5602/gspca_m5602.ko
/lib/modules/2.6.32-29-generic/kernel/drivers/media/video/gspca/m5602/gspca_m5602.ko
/lib/modules/2.6.32-30-generic/kernel/drivers/media/video/gspca/m5602/gspca_m5602.ko
cva@GuGu:~$ 

So there is something there. Cheese and guvcview do not find any device. What do I have to do to make my webcam work? 

Best regards,

Pasoleatis

---

### Post by no2498 on 2011-03-18
open a terminal type webcam click enter
should load a cam grabber
after installed
in  the terminal type lsusb click enter
do you see the cam in the list

in a terminal type dmesg click enter
did it find the cam

retry your programs

---

### Post by pasoleatis on 2011-03-18
> **no2498 said:**
> open a terminal type webcam click enter
should load a cam grabber
after installed
in  the terminal type lsusb click enter
do you see the cam in the list

in a terminal type dmesg click enter
did it find the cam

retry your programs

Thank you for your reply. 

Here is what I get:

 webcam
reading config file: /home/cva/.webcamrc
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no grabber device available
cva@GuGu:~$ 

:~$ lsusb 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c03f Logitech, Inc. UltraX Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 174f:6d51 Syntek 2.0Mpixel Web Cam - Eurocom D900C
Bus 002 Device 003: ID 04fc:0c25 Sunplus Technology Co., Ltd SATALink SPIF225A
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
cva@GuGu:~$ 

The webcam is called Syntek, Though the chipset is ali_m...

One if the messages is:

[559927.921905] Linux video capture interface: v2.00
[559927.935990] gspca: main v2.7.0 registered
[559927.954238] usbcore: registered new interface driver ALi m5602
[559927.954270] ALi m5602: registered


The webcam is on but it is not detected by the programs.

---

### Post by no2498 on 2011-03-19
[http://www.qbik.ch/usb/devices/search_res.php?pattern=cam](http://www.qbik.ch/usb/devices/search_res.php?pattern=cam)

thats a list of cams 

this is what i put in google

174f:6d51 Syntek 2.0Mpixel Web Cam - Eurocom D900C


odd this did not load a grabber

in a terminal type dmesg click enter
did it find the cam

does it connect using fire wire

try using camorama

or if you use 32 bit try wxcam

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

you can get it in a deb file

---

### Post by no2498 on 2011-03-19
open a terminal type gstreamer-properties click enter
click video
try v4l and v4l2
use the bottom test button for each 1
you may try a different plugin

---

### Post by pasoleatis on 2011-03-19
I get the message "can't to indentify device /dev/video0".

---

### Post by pasoleatis on 2011-03-20
Well I guess it is hopeless. Thisa should be the driver, but it does not compile. [http://www.qbik.ch/usb/devices/showdev.php?id=4346](http://www.qbik.ch/usb/devices/showdev.php?id=4346)

```

/Syntek/stk11xx-2.1.0$ make -f Makefile.standalone clean
make -C /lib/modules/2.6.32-30-generic/build SUBDIRS=/home/cva/Downloads/Syntek/stk11xx-2.1.0 clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-30-generic'
  CLEAN   /home/cva/Downloads/Syntek/stk11xx-2.1.0/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-30-generic'
cva@GuGu:~/Downloads/Syntek/stk11xx-2.1.0$ make -f Makefile.standalone
make -C /lib/modules/2.6.32-30-generic/build SUBDIRS=/home/cva/Downloads/Syntek/stk11xx-2.1.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-30-generic'
  CC [M]  /home/cva/Downloads/Syntek/stk11xx-2.1.0/stk11xx-usb.o
  CC [M]  /home/cva/Downloads/Syntek/stk11xx-2.1.0/stk11xx-v4l.o
/home/cva/Downloads/Syntek/stk11xx-2.1.0/stk11xx-v4l.c:1737: error: unknown field &#8216;compat_ioctl&#8217; specified in initializer
/home/cva/Downloads/Syntek/stk11xx-2.1.0/stk11xx-v4l.c:1737: error: &#8216;v4l_compat_ioctl32&#8217; undeclared here (not in a function)
make[2]: *** [/home/cva/Downloads/Syntek/stk11xx-2.1.0/stk11xx-v4l.o] Error 1
make[1]: *** [_module_/home/cva/Downloads/Syntek/stk11xx-2.1.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-30-generic'
make: *** [driver] Error 2

```

My machine is made by Clevo and they only  support windows. I am now running a virtual machine with windows just  to have skype with webcam. It is not so bad I got the license for free from work and my machine is a quad core with 8GB of RAM so it can run it, , but I would  rather not use windowst at all. On some other threads, somebody suggested to  go spend 15 bucks on a new webcam which has drivers on linux and not to  spend anymore time. I guess that is a good advice, but I am not sure how  to check that the webcam I want to buy would work on linux. Could you  give me some suggestions about model which work on Ubuntu?

---

