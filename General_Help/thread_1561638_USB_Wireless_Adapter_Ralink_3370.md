---
title: "USB Wireless Adapter: Ralink 3370"
date: 2010-08-26
forum: General Help
---

### Post by tew88 on 2010-08-26
My USB Wireless Adapter is not recognised when I boot into Ubuntu 10.04. It's installed and running on a Windows 7 install.

Any suggestions?

```
~$ lsusb

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 047d:2048 Kensington 
Bus 003 Device 002: ID 045e:00b4 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 148f:3370 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by tew88 on 2010-08-27
Bump.

Any takers? I'm really struggling with this one.

---

### Post by Toast2120 on 2010-08-30
Bought the same adapter, lol. No idea. I'll post something if I get somewhere.

---

### Post by ilowman on 2010-09-03
I got one of these today, mainly because it said it was Linux compatible. As far as I can see no module is being loaded for it. I guess this is the driver:

[http://cateee.net/lkddb/web-lkddb/RT2800USB.html](http://cateee.net/lkddb/web-lkddb/RT2800USB.html)

but
> 
Known issues: - support for RT2870 chips doesn't work with 802.11n APs yet -** support for RT3070 chips is non-functional at the moment**

so  it doesn't look good. :(

There is a driver included on the cd that came with it but I can't compile it because I have packages missing and no internet access to install them.....

There's also a post here about it:

[http://georgia.ubuntuforums.org/showthread.php?p=9634554](http://georgia.ubuntuforums.org/showthread.php?p=9634554)

but doing what was suggested there didn't help me.


Edit:
I managed to get online by connecting through my netbook. I installed build-essential and tried making the driver supplied on the disk but just get a lot of errors in the source code. The driver it's trying to build is rt3370sta.

---

### Post by Miragej on 2010-10-04
Hey guys, 
I bought the little white wireless N dongle from 7dayshop the other day, not sure if you guys have the same one?

Anyway, I'm having the same problem, just wondering if anyone has got it working yet?

---

### Post by ilowman on 2011-04-10
I finally got this working using ndiswrapper and the windows drivers after seeing this page:

[http://masendav.wordpress.com/2010/10/03/getting-rt3370-usb-wifi-adapter-to-work-in-linux/](http://masendav.wordpress.com/2010/10/03/getting-rt3370-usb-wifi-adapter-to-work-in-linux/)

I had to edit ntoskrnl.c like it says and compile ndiswrapper but now it seems to be working perfectly. :D

---

### Post by lesser on 2011-06-16
I'm now using a stable staging driver (rt5370sta) for this device. I've had no issues and a sensitive reception. Info is in [this post]("http://ubuntuforums.org/showthread.php?t=1748136&page=3").

---

### Post by ilowman on 2011-08-04
> **lesser said:**
> I'm now using a stable staging driver (rt5370sta) for this device. I've had no issues and a sensitive reception. Info is in [this post]("http://ubuntuforums.org/showthread.php?t=1748136&page=3").

Excellent. I just downloaded version 2.5.0.2 of the Ralink driver, added the "MODULE_LICENSE("GPL");" line and complied with wpa_supplicant support and now have a working stick without having to use ndiswrapper. :)
It also works through WICD although NetworkManager doesn't seem to recognize it.

---

