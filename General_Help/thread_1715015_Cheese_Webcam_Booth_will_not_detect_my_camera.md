---
title: "Cheese Webcam Booth will not detect my camera"
date: 2011-03-26
forum: General Help
---

### Post by linuxuser12345 on 2011-03-26
Hi, I am using Ubuntu 10.10 Desktop Edition, 64-bit, and my camera is a Samsung Digital Camcorder, Model # SC-MX10/XAA.
I try to use it in the Cheese Webcam Booth with the camera set to the  "PC Camera" mode for USB, and Cheese does not detect my camera. What  should I do to fix this problem??

---

### Post by Bucky Ball on 2011-03-26
Is your machine recognising the camera? With it plugged in and switched on open a terminal and paste this in:

```
lsusb
```Can you see it there in the output of you connected usb devices?

---

### Post by linuxuser12345 on 2011-03-26
Yes, I can see it:

jeb@Kitchen-PC:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 04e8:120f Samsung Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jeb@Kitchen-PC:~$

Cheese Webcam Booth is still not recognising it, though. : /

---

### Post by BigCityCat on 2011-03-26
try this webcam program. Search for it in synaptic.

Guvcview

---

### Post by linuxuser12345 on 2011-03-26
Okay, I got Guvcview installed and it _***still***_ doesn't work... : /

---

### Post by BigCityCat on 2011-03-26
do you have ubuntu-restricted-extras installed? If not install that. Do you have the mediubuntu ppa installed? If not go here and complete the steps provided.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by linuxuser12345 on 2011-03-26
Is there a way I can install that one file I need from the restricted extras without installing the rest? I don't want all that stuff that the full restricted extras package comes with

---

### Post by BigCityCat on 2011-03-26
If/Once you have mediubuntu installed. Try installing the non free codecs.

> sudo apt-get install non-free-codecs

I'm not an expert. I'm just rying to help.

---

### Post by BigCityCat on 2011-03-26
> **linuxuser12345 said:**
> Is there a way I can install that one file I need from the restricted extras without installing the rest? I don't want all that stuff that the full restricted extras package comes with

Above my expertise. Try installing gstreamer.

---

### Post by linuxuser12345 on 2011-03-26
What type of Gstreamer plugin set should I get? I already have the ffmpeg video plugin set

---

### Post by BigCityCat on 2011-03-26
Here is the ubuntu troubleshooting guide.

[https://help.ubuntu.com/community/Webcam/Troubleshooting](https://help.ubuntu.com/community/Webcam/Troubleshooting)

---

### Post by BigCityCat on 2011-03-26
> **linuxuser12345 said:**
> What type of Gstreamer plugin set should I get? I already have the ffmpeg video plugin set

Try installing these.

install the gstreamer0.10-ffmpeg, gstreamer0.10-plugins-bad, gstreamer0.10-plugins-ugly

---

### Post by no2498 on 2011-03-26
this comes from the cheese help FAQ'S


open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin try setting it to outo

---

### Post by Bucky Ball on 2011-03-26
Just checkes gstreamer-properties and mine is using v4l2 faultlessly if that's any help. Maybe that will work for you too.

---

### Post by linuxuser12345 on 2011-03-26
> **Bucky Ball said:**
> Just checkes gstreamer-properties and mine is using v4l2 faultlessly if that's any help. Maybe that will work for you too.
How do I do that?

---

### Post by Bucky Ball on 2011-03-26
As no2498 mentioned:

-open a terminal
-type gstreamer-properties
-click enter

In other words, Applications>Accessories>Terminal then paste this in:

```
gstreamer-properties
```Click the 'Video' tab and check what you are using. For 'Default Output' I have 'Autodetect.

For Default Input I have 'Video for Linux 2 (v412)'.

---

