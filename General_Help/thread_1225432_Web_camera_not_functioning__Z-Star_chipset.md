---
title: "Web camera not functioning:  Z-Star chipset"
date: 2009-07-28
forum: General Help
---

### Post by s.fox on 2009-07-28
Hello,

I have the following web camera:

```
Bus 003 Device 002: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam
```Whenever I try and use it with skype its detected but just displays green static.  Cheese just outputs a grey box.  After some research I came across [this]("http://www.qbik.ch/usb/devices/showdev.php?id=3049") thread on another forum which says that the web camera is now supported by the spca5xx driver.  

What is odd is that I have this installed already.  Can anyone advise me on what to do next?  

Many thanks, 

Silver Fox

---

### Post by s.fox on 2009-08-01
3 day bump :)

---

### Post by eldragon on 2009-08-01
this has been discussed to death. a small search wouldnt kill you.

start skype with
```

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

```

or its ubuntu equivalent (aka find where v4l1compat.so is)

---

### Post by Arup on 2009-08-01
> **Silver_fox_ said:**
> Hello,

I have the following web camera:

```
Bus 003 Device 002: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam
```Whenever I try and use it with skype its detected but just displays green static.  Cheese just outputs a grey box.  After some research I came across [this]("http://www.qbik.ch/usb/devices/showdev.php?id=3049") thread on another forum which says that the web camera is now supported by the spca5xx driver.  

What is odd is that I have this installed already.  Can anyone advise me on what to do next?  

Many thanks, 

Silver Fox


You have to blacklist zc0301 in /modules/blacklist.d for gspca to load right. This problem doesn't happen in Jaunty where it loads the right driver model from the kernel.

---

### Post by W4l0ck on 2009-08-01
> **Silver_fox_ said:**
> Hello,

I have the following web camera:

```
Bus 003 Device 002: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam
```Whenever I try and use it with skype its detected but just displays green static.  Cheese just outputs a grey box.  After some research I came across [this]("http://www.qbik.ch/usb/devices/showdev.php?id=3049") thread on another forum which says that the web camera is now supported by the spca5xx driver.  

What is odd is that I have this installed already.  Can anyone advise me on what to do next?  

Many thanks, 

Silver Fox

if it is designed for Windows it will only run in windows, usually with webcams and cameras and such, you have to install some things first.

---

