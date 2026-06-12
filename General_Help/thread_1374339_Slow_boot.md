---
title: "Slow boot"
date: 2010-01-06
forum: General Help
---

### Post by syncmasterpt on 2010-01-06
Hi:

I have an Asus P6T motherboard with an I7 920 processor and an ATI 4870, and I'm having the following problem with the latest Kubuntu 9.10 and Kernel 2.6.31-17-generic 64bits.

At boot time, the splash screen of Kubuntu start ok, then disapears, and I only have a blinking cursor for a long while (aprx 15s).

The logs show this jump in time:

Jan  6 22:39:09 kecortex kernel: [   12.868777] type=1505 audit(1262817520.449:9): operation="profile_load" pid=574 name=/usr/sbin/tcpdump
Jan  6 22:39:09 kecortex kernel: [   18.288733] usplash:448 freeing invalid memtype ffffffffd0000000-ffffffffd1000000
Jan  6 22:39:09 kecortex kernel: [   31.015910] udev: starting version 147
Jan  6 22:39:09 kecortex kernel: [   31.068780] Adding 2000052k swap on /dev/sdb7.  Priority:-1 extents:1 across:2000052k
Jan  6 22:39:09 kecortex kernel: [   31.264778] Bluetooth: Generic Bluetooth USB driver ver 0.5
Jan  6 22:39:09 kecortex kernel: [   31.264829] usbcore: registered new interface driver btusb

as it can be seen, the boot stops between 18s until 31s... 

Any ideas?

Thanks!

---

### Post by syncmasterpt on 2010-01-07
Ok.

The delay is due to apparmor loading.

Disabling apparmor eliminates the delay.

---

