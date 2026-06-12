---
title: "I have a sony webbie HD camera and ubuntu."
date: 2009-10-20
forum: General Help
---

### Post by dbzkid on 2009-10-20
I wanted to know if that would work on my Ubuntu as a webcam, it works on xp but sadly not on vista and I cant get it to work on my Ubuntu either. anyone else have this problem.

The camera model is MHS-CM1

Thanks
-Kevin

---

### Post by TicTac52 on 2010-03-22
^BUMP^
I have a Sony MHS-PM1 and Ubuntu, and the computer doesn't detect the webcam, either. I can switch the camera to mass-media-storage mode and the computer detects it, but nothing when it's on webcam mode. I've tried using apps that are for  webcam, too, and it says that there's no webcam.
Seriously, how canI get Ubuntu to acknowledge my webcam.
(PS - I'm not very Ubuntu savvy)

---

### Post by no2498 on 2010-03-22
try this
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1
make sure the cam is on same way as with windows

if you use a fire wire im not sure if cheese or ekiga softphone will see it

but if it comes on in the gstreamer-properties you have hope

hope this helps you 2

---

### Post by TicTac52 on 2010-03-23
Nothin' but rubbish. I guess you don't want to get a Sony MHS-PM1 if you want a camera AND a webcam for ubuntu. Thanks anyway, mate ;)

---

### Post by no2498 on 2010-03-23
if you seen any thing in the bottom test window
you have some thing to work with

have you been to the cam makers web site and ask if they have a driver that will work on/with ubuntu


lsusb in a terminal will tell you if the computer see the cam
cam plugged in
cam unplugged 

see what changes

---

### Post by TicTac52 on 2010-03-24
Ok, when I do the tests, it says:
 - Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'.
 and
 - Video for Linux (v4l): Device "/dev/video0" does not exist.
When I do the "Test Input" it just shows bars and black and white fuzz in the bottom right corner

I don't use firewire, just a usb.

When I put gstreamer-properties into a terminal, it shows: 

```
leon@fletcher:~$ gstreamer-properties
/home/leon/.themes/Dust Cold/gtk-2.0/gtkrc:739: error: unexpected identifier `nautilus', expected character `='
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(463): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src3:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline1/GstV4lSrc:v4lsrc2]
```I put lsusb into the terminal. The first time without the webcam pugged in, the second time, it was plugged in.

```
leon@fletcher:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 002 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
leon@fletcher:~$ lsusb
Bus 001 Device 002: ID 054c:03bc Sony Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 002 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```I didn't go to the site and ask about a driver.
Sorry, I'm really kind of a n00b with Ubuntu.

---

### Post by brittanie on 2010-09-13
Any luck yet? I have a webbie hd also. Sony does not seem to have a driver for linux, but I am going to try to use WINE and run the XP drivers. wish me luck!

---

### Post by Barnbrat on 2012-02-14
After 3 years, have we found any solutions?  I also have a Sony Webbie HD.

---

