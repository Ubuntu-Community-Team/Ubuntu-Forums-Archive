---
title: "ubuntu and xubuntu 9.10 broadcom wl"
date: 2009-11-15
forum: General Help
---

### Post by timremy on 2009-11-15
hello

i tried ubuntu and xubuntu 9.10. i have run 8.10 and 9.04 from my

amd proc on my hp presario v3000 and they worked. when i tried

ubuntu or xubuntu 9.10, it seems that no wifi is detected. does ubuntu 

and xubuntu 9.10 have the broadcom wl driver? 

can someone help.

thank you

timremy

---

### Post by Brandon Williams on 2009-11-17
The driver is there, but it doesn't get installed with a clean install. After the install, you can apt-get install bwmwl-kernel-source to get the driver back. [Here](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/443185) is a related bug report.

---

### Post by CaKiwi on 2009-11-17
I had the same problem and post #1 in this thread fixed it

[http://ubuntuforums.org/showthread.php?t=1305906](http://ubuntuforums.org/showthread.php?t=1305906)

---

