---
title: "Pre-downloading a Ubuntu hardware driver?"
date: 2011-03-31
forum: General Help
---

### Post by Mercenary(FH) on 2011-03-31
Ok this is sort of a weird request, Im on wireless and there is an Ubuntu driver for my wireless card (WN311T PCI-Wireless N adapter for netgear)

However....to get it I obviously have to be connected to the internet (which I can on my windows computer)

is there any way to like.....download the driver on windows and then like Install it on my Ubuntu partition (computer is a dual boot)

Thaks

---

### Post by bodhi.zazen on 2011-03-31
You can download anything you like, store it on a flash drive or somewhere on your windows partition, and then transfer it to Ubuntu.

Do you have some kind of a guide on how to get the driver working ? Sometimes with wireless this involves compiling a custom kernel, sometimes applying a patch.

---

### Post by Mercenary(FH) on 2011-04-01
Well basically it just said to download one of the 3rd party drivers that pop up (Like restricted drivers?)

But I don't know where you would even find them at...

---

### Post by bodhi.zazen on 2011-04-01
If it is a deb in the Ubuntu repostiories, search here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

If not, google search for "Ubuntu" (or linux) and your wireless card.

---

### Post by tredegar on 2011-04-01
It looks like support for that device is already in the kernel (it is on 10.04).

I think it uses the **ar9170usb** module.

So plug it in and see what happens. Wait a moment. Type **sudo iwconfig** and see if it is listed.

If not, try adding the module it needs with **sudo modprobe ar9170usb**
Re-plug it, then see if it is listed and usable.

If it is still not working, we need to know what its USB ID is.
**lsusb** without the device, and then **lsusb** after it has been plugged in (check for the newly added device) will help you work out what it is.

---

