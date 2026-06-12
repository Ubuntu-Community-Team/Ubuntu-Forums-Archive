---
title: "Re-sizing Ubuntu drive"
date: 2010-11-16
forum: General Help
---

### Post by nanso_ on 2010-11-16
Hi, 
I installed Ubuntu 9.10 on half of my D drive about a year ago, but realized that I don't really need all the space on the Ubuntu partition. I have Windows Visa Home Premium installed on my C drive. Is there any way to re-size the drive on which I had installed Ubuntu without removing it?
Thank you

---

### Post by Verbeck on 2010-11-16
i don't know whether vista can resize ext partitions, but you could boot from a gparted live cd ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) or a normal ubuntu live and run gparted from system>administration to resize the partition

as always ; backup all important data first

---

### Post by drs305 on 2010-11-16
I wrote this guide for *expanding* the Ubuntu partition, but the principles apply equally for shrinking it. 
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")


I'd recommend any resizing of the Windows partition be done with Windows tools.

---

### Post by HarrisonNapper on 2010-11-16
To reiterate, **back everything up**

Resizing a physical partition with things on it poses risk of losing data.

---

### Post by Lancro on 2010-11-16
I would start from a live cd/usb stick and run gksudo gparted, to shrink it, and leave unallocated space, and then in windows, I will resize windows partition into the unallocated space to fill it, use linux tool for linux partition and windows tools for windows partition.

---

