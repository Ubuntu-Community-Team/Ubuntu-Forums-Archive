---
title: "Ubuntu 9.10 going into infinite disk check without starting"
date: 2010-05-02
forum: General Help
---

### Post by devosion on 2010-05-02
Hi folks I really need help with this. I put together a pc with a gigabyte ga-x58-ud3r, seriously don't use this mobo, and during the short time my two drives were installed on this board I was unable to load windows in any form, and secondly my ubuntu installation on the second drive seems to have been corrupted. About after a day having the ubuntu drive installed on the board it began giving me errors unable to read the drive, and checking the disk repeatedly. Having changed the bios to read the sata ports from ide, and ahci I was unable to find a setting that allowed the drive to be read properly without any issues. Upon migrating back to the old box I am finding I am having the exact same issue again. I am stuck in an infinite drive check and upon the second time I am asked to try another mount the screen stays black with a cursor. I booted up Ubuntu with the live cd and see all my contents of the disc looking fine, but im not sure how I can recover the drive without deleting over 500gb of important files. Please assist. :(

---

### Post by devosion on 2010-05-03
Bumpa for assistance.

---

### Post by v1ad on 2010-05-03
Bios Update for sure. had that with the same board. bios update makes it perfect.

---

### Post by devosion on 2010-05-03
Well I updated the bios of the board to F5, but im still getting the case where ubuntu will not mount and goes into a series of drive checks until I arrive to a black screen. 

The error I get is:

> 
init: mountall main process (542) terminated with status 2


When I press Ctrl+D to run a recovery shell it goes to a black screen with cursor and doesn't do anything from that point.

---

### Post by devosion on 2010-05-03
So I went ahead and burned ubuntu 10.04 to disk and used the livecd to check the drive that im having problems with. I open up the disk utility and have it check the partitions on the drive. It finds my root partition doing just fine, but my home partition it states is not clean. It doesn't look like disk utility fixes the problem though, because I run check filesystem again and it returns the same message. I really need to retain the information on this drive. Is there another utility I can use to fix this? Or will installing 10.04 over 9.10 fix the problem? Please assist.

---

### Post by devosion on 2010-05-03
bumpa again

---

