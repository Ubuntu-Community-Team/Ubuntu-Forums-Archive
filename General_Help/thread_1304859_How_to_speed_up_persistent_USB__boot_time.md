---
title: "How to speed up persistent USB  boot time"
date: 2009-10-29
forum: General Help
---

### Post by song2 on 2009-10-29
Hi,
I got the brand new Ubuntu 9.10, installed it on an USB stick. Everything works (until now). 
Knowing that I plan to use it only on one computer, do you have any tips to speed-up the boot time? I successfully changed the timeout in "text.cfg" to skip the boot menu part, but my impression is that it still takes a lot of time to boot. The part with the new light-pulsating icon takes about 1 to 2 minutes (1,6 GHz, 3Gb RAM). I think 8.10 booted much faster. 
Is there a way to tell "it" that is the same computer and not to search again to install all the drivers (if "it" does that).
Thanks!

---

### Post by bodhi.zazen on 2009-11-05
Moved from Tips and Tutorials to general help (the tutorials section is not for support questions).

---

### Post by Mighty_Joe on 2009-11-05
> **song2 said:**
> Hi,
I got the brand new Ubuntu 9.10, installed it on an USB stick. Everything works (until now). 


Did you do a "Live CD" install?  They're slow because the "Live CD" is a compressed file system.  It has to be loaded into memory before it can be used.  
Personally, I prefer to do a full install to a flash drive.  It takes more space (2+GB vs. 700Mb), but it's much faster.

---

### Post by woop on 2009-11-14
> **Mighty_Joe said:**
> Did you do a "Live CD" install?  They're slow because the "Live CD" is a compressed file system.  It has to be loaded into memory before it can be used.  
Personally, I prefer to do a full install to a flash drive.  It takes more space (2+GB vs. 700Mb), but it's much faster.

hey, I have live cd install with persistance on flash drive. how did you do the full install to flash drive?any chance of a link to a how to or tutorial

boot time is a little annoying

---

### Post by bodhi.zazen on 2009-11-15
plug in the usb and install Ubuntu as you would normally, use the usb drive as the target for installation, install grub into the usb.

---

### Post by dcstar on 2009-11-15
> **woop said:**
> hey, I have live cd install with persistance on flash drive. how did you do the full install to flash drive?any chance of a link to a how to or tutorial

boot time is a little annoying

The whole point about the USB boot using the Live CD setup is to minimise writes to the active drive - because Solid State Drives still have a finite quantity of write cycles and installing "standard" Ubuntu will push a SSD towards death far quicker than the Live CD setup.

If you want an Ubuntu install designed to minimise wear on a SSD, then try the UNR install. It should be set up to use RAM drives and minimise writes to the installed drive (I hope.....)

---

### Post by bodhi.zazen on 2009-11-15
> **dcstar said:**
> The whole point about the USB boot using the Live CD setup is to minimise writes to the active drive - because Solid State Drives still have a finite quantity of write cycles and installing "standard" Ubuntu will push a SSD towards death far quicker than the Live CD setup.

If you want an Ubuntu install designed to minimise wear on a SSD, then try the UNR install. It should be set up to use RAM drives and minimise writes to the installed drive (I hope.....)

actually you can make many of these tweaks yourself.

The ones I use are here :

[http://blog.bodhizazen.net/linux/netbook-optimization/](http://blog.bodhizazen.net/linux/netbook-optimization/)

everything is in RAM and hardly any wear and tear on the hard drive. I use those settings for netbooks, laptops, and desktops.

---

### Post by autonomy on 2009-11-15
unplug any other devices plugged into the usb interfaces.

---

### Post by Mighty_Joe on 2009-11-16
> **dcstar said:**
> The whole point about the USB boot using the Live CD setup is to minimise writes to the active drive - because Solid State Drives still have a finite quantity of write cycles and installing "standard" Ubuntu will push a SSD towards death far quicker than the Live CD setup.


I think the fragility of flash memory [has been overstated]("http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html")
That said, I take steps to reduce wear similar to the ones posted by bodhi.zazen. I posted a link in [this topic.]("http://ubuntuforums.org/showthread.php?t=1193680")

---

### Post by Grenage on 2009-11-16
The max projected write counts were quite shoddy when the media started making an appearance.  It's progressively improved rapidly, just take a look at Intel's new SSDs.

---

### Post by P4man on 2009-11-16
> **Mighty_Joe said:**
> I think the fragility of flash memory [has been overstated]("http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html")

Thats pretty interesting, but I wonder if its actually correct. We dont know how many spare blocks that drive has. He writes to only 1 block but if the drive wear levelling algorithm spreads that out over 1.000 spares (thats still only 1Mbyte) then he didnt kill just one block, he killed (all) 1.000 spares as well, and his results are pretty much in line with conventional wisdom. 

Having about half a dozen defunct USB sticks here at work, I draw very different conclusions (unless not all thumb drives do wear levelling)

Anyway thumb drives are dirt cheap, so I do normal installs on them as well, but I dont count on those lasting many years. ill check out the tips on how to reduce wear.

---

### Post by Mighty_Joe on 2009-11-16
> **P4man said:**
> Anyway thumb drives are dirt cheap, so I do normal installs on them as well, but I dont count on those lasting many years. ill check out the tips on how to reduce wear.

I keep anything I want to save on a NAS ;)

---

