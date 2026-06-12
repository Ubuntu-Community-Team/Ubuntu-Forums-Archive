---
title: "usb mouse stopped working"
date: 2009-08-12
forum: General Help
---

### Post by Jaco.csm on 2009-08-12
My usb mouse stopped working for no apparent reason, and without me installing any other software/update between the time that it last worked and when it stopped working. It was working the one minute and then it just died. The touchpad still works but can't get the mouse to work. I tried a different usb mouse but still no luck. Restart also didn't help. It does pick up a usb flash drive though but then it keeps mounting and unmounting it, and there is power on the mouse (laser light is on).

I have a sony vaio aw vgn-aw17gu/q (RAID) with ubuntu 9.04 alternative cd installed and it worked perfictly until now. Any ideas?

---

### Post by P4man on 2009-08-12
if you plug the mouse in, does it show up in the list when you run

```
lsusb
```

?

---

### Post by Jaco.csm on 2009-08-14
yes. I think it has less to do with the mouse and more to do with the usb. do a mouse get mounted? if yes then maybe the same thing happens to it then to the flash ( get mounted and then unmounted and then mounted agen...) ?

here is wat i get with lsusb

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 044e:3017 Alps Electric Co., Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:183e Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:1000  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by matthewbpt on 2009-08-14
hmmm, what happens to other usb devices when plugging them in, do they work?

---

### Post by Jaco.csm on 2009-08-14
it started working just as randomly as when it stopped working.:P it is as if lsusb fixed it but I do not think lsusb can do that. Maybe it was the restart but restart did not work yesterday.

thanks for the reply:guitar:

---

### Post by Jaco.csm on 2009-08-14
I do not know I just tried the flash and it is fixed now.

---

### Post by P4man on 2009-08-14
hmm..
first thought would be to go into the bios, and check the setting for "legacy USB support" or something along those lines. Change it from on to off (or vice versa)

Also this might help:

[http://ubuntuforums.org/showthread.php?t=1137797](http://ubuntuforums.org/showthread.php?t=1137797)

I know this guy is having keyboard problems, but I saw it referenced in another thread where someone claimed it solved his mouse problem.

---

