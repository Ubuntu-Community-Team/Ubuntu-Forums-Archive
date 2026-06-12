---
title: "Ubuntu recognizes HDD, BIOS doesn't"
date: 2012-01-22
forum: General Help
---

### Post by Indulgencijus on 2012-01-22
Hi,

So, my situation is like that:
BIOS allows me to choose HDD as a boot option, but it says that IDE primary master and secondary master (as well as both slaves) are "Not installed".
In Ubuntu it doesn't show HDD on 'Computer', but it does show information about it on 'Disk Utility'.
I was able to install Ubuntu, but Windows does not install, it just says that the Hard drive was not found.

How could I fix that?

Thanks in advance.

---

### Post by bsniadajewski on 2012-01-22
What type of BIOS (phoenix, AMI, etc.).  There may be options in the BIOS setup that will let you tell the BIOS to say there are drives installed.

---

### Post by Indulgencijus on 2012-01-23
I have AMIBIOS, version 3.31a

---

### Post by xyzzyman on 2012-01-23
First step is to reset the BIOS and only change any settings that are absolutely required. Next is to properly jumper your drives, master for the drive at the end of the cable, slave for the one in the middle. Auto-jumpers don't always work with every configuration. If you still have an issue, try each drive individually as master as sometimes a bad drive can mess up the entire IDE chain. It's getting to the age where I almost assume any IDE drive I come across might be failing.

---

### Post by Indulgencijus on 2012-01-23
I don't really understand stuff about jumpers and cables, but I don't think it's the problem.
It occurred when I (almost) accidently removed my old OS (windows) from my drive (before that everything went fine).
I installed ubuntu and chose option to delete everything from drive.
Maybe it has to something with that?

---

### Post by oldfred on 2012-01-23
If you have the older IDE type drives:

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

I changed to SATA as soon as the price dropped to just a few dollars more than PATA (about 6 years ago) as I always had trouble with the tiny little jumpers on the drives and knowing which setting was correct. every drive seems to be different and they did not label them well early on. SATA has no jumpers.

---

