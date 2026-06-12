---
title: "can't configure wireless usb"
date: 2006-06-23
forum: General Help
---

### Post by dannemil on 2006-06-23
I'm running dapper. I got a new Linksys Wireless USB (WUSB54GC). When I do a lsusb, it is apparently recognized because it gives me

Bus 001 Device 008: ID 13b1:0020 Linksys

But there is no indication that any networking processes even know the interface is there. The nm-applet doesn't list any wireless interface at all. I've tried

sudo iwconfig eth1 essid (XXXX)

but I get

SET failed on device eth1 ; No such device.

I also tried this with wlan0 in palce of eth1 with the same result.

The indicator light on the device has never even blinked.

Any help on getting this wireless adaptor installed and configured would be appreciated. I have gone through wireless configuration on my laptop with Ubuntu with a built in wireless device, but no such luck for this usb wireless on another computer.

Wired and tired...

---

### Post by burgermann on 2006-06-26
You should find the solution from this thread:
[http://www.ubuntuforums.org/showthread.php?t=170017&highlight=WUSB54GC](http://www.ubuntuforums.org/showthread.php?t=170017&highlight=WUSB54GC)

It's not difficult if problems occur anyway, just ask :)

---

### Post by aqau on 2006-07-23
If you had problems with the guide posted by burgeman, then follow this one that was specifically written for ubuntu(i wrote it, so let my know how it goes):

[http://www.cicerosonline.com/WUSB54GC/](http://www.cicerosonline.com/WUSB54GC/)

---

