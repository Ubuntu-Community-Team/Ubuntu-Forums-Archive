---
title: "How to set up USB internet device."
date: 2009-09-20
forum: General Help
---

### Post by fatigue on 2009-09-20
I bought a USB internet device called COMVIQ

Does anyone know how to set this up in Ubuntu?

This USB thing has exe setup and you can install program in windows.
So I tried this setup.exe in wine but it doesn't work.

Ubuntu recognize this device as USB wireless too but I don't know how to set this up.
Thank you for your help

---

### Post by fatigue on 2009-09-22
does anyone know?

---

### Post by P4man on 2009-09-22
Im guessing you are talking about a 3G USB dongle (internet over GSM) ?

If so, find out what type of dongle it is exactly. open a terminal and type:
```
lsusb
```
copy/paste the output here. 

A lot of 3G dongles just work out of the box (configure your connection by right clicking network manager > edit connections > mobile broadband) but some may need some tweaking or may not work at all.

---

### Post by fatigue on 2009-09-28
```
Bus 008 Device 004: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0461:4d42 Primax Electronics, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Here is my usbs
Does anyone recognize?

Thank you for help

---

### Post by P4man on 2009-09-28
The first line is your modem. Its a huawei E1750, and I found this thread:
[http://ubuntuforums.org/showthread.php?t=1246293](http://ubuntuforums.org/showthread.php?t=1246293)

I suggest you post in there and ask eeBus how he managed to get it working, but I must warn you, it will not be easy. You're unlucky as most huawei modems work out of the box.

---

