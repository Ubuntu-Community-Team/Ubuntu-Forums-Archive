---
title: "Hard Drive Problem"
date: 2010-01-22
forum: General Help
---

### Post by kermit99911 on 2010-01-22
How can I format my HD to be used with Windows again ? I installed Ubuntu on the disk, and opted to use the whole disk. Since then I have obtained another (bigger) disk and installed XP with Ubuntu 9.1 running within XP. I would like to use my original disk for data storage, but windows doesn't even see it, so I'm at a loss of how to proceed.. Can anyone help me ?

---

### Post by chayzer on 2010-01-22
Either in windows, under control panel -> Administrative tools There should be a section about storage on the left, your disk will show up as unknown or something along those lines, you have to delete that partition and make a new partition.

In ubuntu, use gparted and format the disk at NTFS or VFAT/FAT32 and your windows will be able to see it.

There is also something called ext2 IFS for windows which will allow you to see all your linux partitions in windows.

---

### Post by kermit99911 on 2010-01-22
Thanks Chayzer.. I have tried the Admin Tools/Disk Management, it is not showing. I have the HD in an external caddy. When I plugged it in to a USB Port Windows reported Unknown Device, couldn't find a driver, so its no wonder its not showing.. Could you please explain about using GPARTED in Ubuntu ? I'll give that a try

---

### Post by chayzer on 2010-01-22
```
sudo apt-get install gparted
sudo gparted
```

It's a pretty easy program to use, you should be able to figure it out from there. Good luck!

---

### Post by kermit99911 on 2010-01-22
Thanks ... I'll let you know what happens !

---

### Post by kermit99911 on 2010-01-23
Chayzer.. Tried the sudo gparted as you suggested. Ubuntu told me that the installation failed! tried a couple of times, after computer resets. However, searching around in "system/Admin" menu I found an entry for displaying Disk Properties. In this item it displayed all the attached HDs and their properties, AND with drop-down menus allowing alterations to these properties. So, picked the disk, selected NTFS, clicked apply, rebooted into Windows and Eureka! the disk was recognised, but needed formatting before I could use it. Well done to Ubuntu v9.1 .. and thanks to you for pointing me in the right direction.

---

### Post by howefield on 2010-01-23
> **chayzer said:**
> ```
sudo apt-get install gparted
sudo gparted
```

Gaining elevated rights with graphical applications should be done with gksudo, not sudo.

Also, gparted shouldn't need starting with elevated rights in the first place.

---

### Post by howefield on 2010-01-23
> **kermit99911 said:**
> How can I format my HD to be used with Windows again ?

Boot with the Ubuntu Live CD to the desktop, and load gparted from there (it is included on the live disk). Might be the quickest way given you are having problems otherwise.

Make sure you format the correct disk ;)

---

### Post by kermit99911 on 2010-01-25
Thanx all ..

---

