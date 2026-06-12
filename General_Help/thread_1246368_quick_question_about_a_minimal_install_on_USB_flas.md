---
title: "quick question about a minimal install on USB flash drive"
date: 2009-08-21
forum: General Help
---

### Post by sarith on 2009-08-21
EDIT: This should probably be moved to the Installation section of the forums (sorry!)

So I recently picked up a mini-ITX board ([http://www.newegg.com/Product/Product.aspx?Item=N82E16813500027](http://www.newegg.com/Product/Product.aspx?Item=N82E16813500027)) which I'm really excited to get a minimal install of Ubuntu going on to serve as a server / set top media center.

Anyway, here's my dilemma (and I'm pretty sure I'm just misunderstanding the exact install process):

Basically, I want to have the entire minimal installation of Ubuntu running on a USB flash drive.  The set top box itself will have no moving parts whatsoever (i.e. there is no hard drive, optical drive, etc).  Now in order to install TO this USB flash drive, can I use another computer (i.e. my Macbook Pro), boot from the minimal CD, install to the flash drive, then just unplug the USB flash from my Macbook and plug it right into my other box (bootable and ready to go)?

I understand the 'boot from usb' route that would allow me to use a USB key in lieu of a CD -- but I need to *install* TO a USB key.

As a side note, I've got a pretty decent amount of experience on linux and bsd systems, so don't hesitate to get technical on me at all. Any help would be greatly appreciated.

Thanks so much!
S

---

### Post by cwaidelich on 2009-08-21
I dont understand correctly: you want a LiveUSB with Ubuntu? If u have a running Ubuntu you can always do: System -> Install Ubuntu on USB.

(It has worked for me)

[You can also look here.]("http://www.google.com/search?source=ig&hl=en&rlz=1G1GGLQ_DECO336&=&q=ubuntu+on+usb&btnG=Google-Suche&meta=lr%3D&aq=0s&oq=ubuntu+in+usb")

---

### Post by sarith on 2009-08-21
Well my major question is, when installing onto a usb (doing a minimal install) -- does the installer *only* install hardware driver information, etc. for the singular machine that both the installation CD and flash drive are plugged into during install?  

The idea is that I'll be transporting this USB key to another computer (where it is essential that any and all device drivers for the motherboard function properly).  Basically, I need to create a LiveUSB (yes) but I have no way of doing it *on* the system I'll eventually be using it with (dedicated).

Am I just totally misunderstanding the hierarchy of installation?

Thanks a bunch,
s

---

### Post by cwaidelich on 2009-08-21
I have never had trouble with my live usb stick actually. I use it mostly to grab files from Windows Clients that dont boot anymore and to use GParted to format their HDD again. I created it on my ubuntu laptop (5 month ago, and used it in a least 6 laptops + pcs).

This is actually the [best software]("http://unetbootin.sourceforge.net/") in my opinion to create LiveUSBs (supports many Distros).

---

### Post by earthpigg on 2009-08-21
> **sarith said:**
> does the installer *only* install hardware driver information, etc. for the singular machine that both the installation CD and flash drive are plugged into during install?

no, it installs the stuff needed to *detect* hardware on the machine you plug it into automatically - assuming the basic architecture (x86, etc) remains the same.

if its a home computer and not PowerPC, then x86 will work with it. x86 is also known as "32-bit intel" or other things similar.

---

