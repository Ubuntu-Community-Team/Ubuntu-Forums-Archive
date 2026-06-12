---
title: "Secondary drive mount problem"
date: 2011-05-05
forum: General Help
---

### Post by megabuffen on 2011-05-05
I have a server with two hard drives. I just backed up all my data to the secondary drive, formatted the primary one, and installed Ubuntu 11.04 Server on the primary one.

The problem is, whenever the secondary hard drive is installed, Ubuntu says that it cannot mount /boot due to "unsupported options". If I physically disconnect the secondary drive, it starts up just fine, without any error messages.

Is there any way that I can connect the secondary hard drive without these problems? I don't want to format it as it would destroy the entire backup...:confused:

---

### Post by megabuffen on 2011-05-05
I had this feeling there was something wrong with the disk connections so i swapped the IDE cables, and it started working again. Would be interesting though to know why it couldn't mount /boot.

---

### Post by oldfred on 2011-05-05
You mention IDE. Were you using cable select with the newer 80 wire cables and jumpers set to cable select on drive. Or using the older 40 wire cables and setting jumpers to master & slave on drive. Old verisons only boot from primary master, so jumper settings are important on which drive boots. 

SATA is totally controlled by BIOS, no jumpers, much easier. I was getting to the point I could not see to plug those little jumpers in anyway.

---

### Post by megabuffen on 2011-05-06
That would be 40-pin IDE. I think the drives were set to cable select as I have been using them for some time with only one drive per IDE cable, but I should check it out next time i physically visit the server. It seemed though that the BIOS was at least able to boot the drive in both cases.

---

### Post by oldfred on 2011-05-06
If the BIOS/motherboard is new enough to support SATA it then has the capability to choose boot in BIOS. It is the old BIOS that only were IDE that only booted primary master.

But jumpers and 40/80 wire cables are important. If you have two 40 wire cables you then are using primary & secondary master, not master and slave on one wire.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

