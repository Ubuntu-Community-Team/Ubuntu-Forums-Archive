---
title: "No graphics driver in 10.04, help!"
date: 2010-05-01
forum: General Help
---

### Post by MrCloudHands on 2010-05-01
I recently upgraded to Lucid and am having difficulty finding and installing the ATI graphics driver for my machine. When I open Administration > Hardware Drivers, the list is completely empty. I've searched the forums but haven't found a way to get the driver installed. My graphics card is an ATI Radeon X1200 series, and my computer is a Toshiba Satellite A215-S5818. Hope someone with more experience can help me out. Thanks!

---

### Post by MrCloudHands on 2010-05-16
bump

---

### Post by lidex on 2010-05-16
Reference these pages:
Binary:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
Open Source:
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by MrCloudHands on 2010-05-16
Thanks for leading me in the right direction. I tried to purge fglrx as the tutorial stated but got an error each time. Here's what the terminal output was:

```
christian@christian-laptop:~$ sudo apt-get remove --purge xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xorg-driver-fglrx is not installed, so not removed
The following packages will be REMOVED:
  fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 60.0MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 171521 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas why it won't uninstall?

---

### Post by lidex on 2010-05-16
Yeah, it's a bugger. Go here:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver")

---

### Post by mr clark25 on 2010-05-16
i have a very similar graphics card. i have the radeon X1300 pro. (pro meaning that it has 256mb of ram instead of 128mb)

there is no driver for my card, but i get satisfying performance out of it. i have almost all of compiz's settings enabled (it can't handle blur), and i have a really cool 3d desktop cube...

---

### Post by ryan858 on 2010-05-16
The error is basically saying that fglrx wasn't ever installed correctly... This could be why you didn't see it in Hardware Drivers. Though it should have shown up still...

You can try this:

[B]$ sudo apt-get purge fglrx fglrx-dev fglrx-kernel-source xorg-driver-fglrx fglrx-amdcccle fglrx-modaliases
[/B]**$ sudo apt-get install fglrx fglrx-kernel-source  xorg-driver-fglrx fglrx-amdcccle fglrx-modaliases**

This would try to purge all fglrx packages and install them again...

You can also try (after purging fglrx) installing one of the open source drivers, *xserver-xorg-video-radeon*, or *xserver-xorg-video-ati*.

I would go with the proprietary *fglrx* driver first, then the *xserver-xorg-video-radeon* driver, and if that doesn't work, then try the *xserver-xorg-video-ati* driver.

To install *xserver-xorg-video-radeon *or* xserver-xorg-video-ati*, do:

[B]$ sudo apt-get install xserver-xorg-video-radeon
[/B]or
**$ sudo apt-get install xserver-xorg-video-ati**

---

