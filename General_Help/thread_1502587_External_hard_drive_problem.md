---
title: "External hard drive problem"
date: 2010-06-05
forum: General Help
---

### Post by lesath on 2010-06-05
Lately I've been having ridiculous computer issues. Long story short, I was forced to create a LiveUSB stick of 10.04 in order to back up my hard drive and do a clean install of Ubuntu. In order to back up my hard drive, I tried to use GParted on the LiveUSB to make an ext4 partition in my external drive, so that I could make one large .tar file of my home folder. This gave me several errors and didn't work, I would assume due to the LiveUSB being generally crap (everything was crashing and I couldn't install my wireless drivers, among other things) but the drive continued to function, so I finally just copied and pasted my entire home folder to the drive, installed, 10.04, and rebooted my computer. Now the external drive will not mount and when I attempt to check it, I get the error: "FAT32 root dir starts with a bad cluster!" A friend tells me that I basically have no chance of recovering my files without paying for expensive data recovery specialists, but I have literally no money at the moment. [I]

Please please please [/I]spare me the lectures about backing up before you attempt to partition. I cannot have infinite backups and I was aware of the risk I was taking; all I want to know is if there's any way to get my files back.

---

### Post by bodhi.zazen on 2010-06-05
you can try fsck

fsck -y /dev/sdb1

where /dev/sdb1 is your FAT partition.

---

### Post by lesath on 2010-06-05
Never mind, because I ignorantly followed someone's instructions, despite not really knowing what I was doing, the disk is now unusable and my data unrecoverable. Thanks anyway.

---

### Post by harrisonk on 2010-06-05
Try testdisk ```
 sudo apt-get install testdisk 
``` it is a terminal app that recovered my data.

Harrison

---

