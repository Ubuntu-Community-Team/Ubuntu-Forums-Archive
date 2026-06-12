---
title: "Network drivers with no internet connection"
date: 2009-09-11
forum: General Help
---

### Post by rmeske on 2009-09-11
Hi All,

I recently brought a very old laptop out of retirement due to my current one needing repair.  Windows 2000 runs like a slug on it and so I thought I would try Ubuntu 8.04.  After booting with the CD I found it responded much better with Ubuntu.  The only thing keeping me from wiping Windows completely is being able to install network drivers.  The laptop does not have any built in network adapters, so I have been using a USB wireless adapter and a Linksys PC card.  However, they are not installed as part of the default Ubuntu installation.

Is there a way of finding a driver for my network adapters and install them manually?  

Any help would be appreciated.

Ron

---

### Post by P4man on 2009-09-11
Im surprised in more than one way. Ubuntu being snappier than windows 2000? Ubuntu needs at least 512Mb realistically. Windows 2000 should fly with less than half that much. How much ram does the machine have?

Anyway, as to your actual question.. is the linksys PC card an USB adaptor that you need to connect the wifi stick ? Or are both wifi sticks, and neither working?

can you provide the output of

```
lsusb
```

and

```
lspci
```

---

### Post by rmeske on 2009-09-15
The laptop is a Pentium 3 with 512MB of memory.  The reason it is slow, I am guessing, is all the patches over the last 10 years, not to mention the AntiVirus/SPyware/Malware/... software protection that is on it.  I am sure if I formatted the drive and reinstalled W2K, the speed would improve.  So, before I go through all that effort, I thought I would try linux and upon booting from the CD, there was a noticeable difference in response.   So now , I want to do a dual boot and really see how much of a difference there is.

I inserted a 3COM 10/100 PC Card and it was recognized by Ubuntu, so I am good with internet connection now.  I need to take some time to locate the drivers for the USB Belkin wireless adapter as it is not recognized.

I would still like to know if there is a way to download drivers on another computer (including Windows) placing them on a USB Disk or CD and then installing them in Ubuntu.    Thanks for all the help.

---

### Post by 3rdalbum on 2009-09-15
> **rmeske said:**
> I need to take some time to locate the drivers for the USB Belkin wireless adapter as it is not recognized.

This command:

```
lsusb
```

should hopefully tell you (or us) the chipset used in your USB wireless adapter, which with a bit of Google will say how to use the wireless.

> I would still like to know if there is a way to download drivers on another computer (including Windows) placing them on a USB Disk or CD and then installing them in Ubuntu.    Thanks for all the help.

Yes, but drivers on Linux are distributed as source code, not precompiled. This is because Linux runs on different sorts of processors, and a driver compiled for ordinary x86 processors will not work on anything else.

You can do it, but you'll need to either use your internet connection to install build-essential and linux-headers-generic, or download those packages with the other computer (from packages.ubuntu.com).

---

### Post by rmeske on 2009-09-16
The results of lsusb is:

Bus 001 Device 002: ID 0846:4240 NetGear, Inc. WG111 WiFi (v2)
Bus 001 Device 001: ID 0000:0000

---

### Post by P4man on 2009-09-16
are you sure its not working? in top top right notification area, there is a network icon. If you click it don't you get a list with AP's ?

---

### Post by rmeske on 2009-09-18
I started up ubuntu again and when I checked for Wireless connections, there they were.  It was great, I was able to connect wirelessly and everything seemed to be working great.  I stepped away from the computer for a few minutes, came back and the connection was gone.  It was as if the adapter was no longer recognized.  I removed it and reinserted, and then I was see the wireless networks again.

I know it is not the computer, adapter, or network as everything works under Windows 2000 on the laptop with the same adapter and connecting to the same network.

---

