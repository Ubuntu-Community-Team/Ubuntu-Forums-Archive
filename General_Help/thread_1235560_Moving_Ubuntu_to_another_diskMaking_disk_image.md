---
title: "Moving Ubuntu to another disk/Making disk image"
date: 2009-08-09
forum: General Help
---

### Post by mookie3three on 2009-08-09
Hi Guys,

I have UNR installed on an SD card and want to move it to a new card, but I can't seem to find a good way to move the entire image as is. Currently the disk is listed as 3 partitions, one ext3, an extended and a Linux_swap. I have tried to use Partimage but it will only let me do one partition at a time and I'm not 100% sure where it is saving it as it doesn't allow you to browse the file system. I have tried Clonezilla but it only allowed be to back up the EXT3 partition and when I tried to restore it, it said the partition table was wrong.

So for example the disk is listed as sdb, and the partitions are sdb1, sdb2 and sdb5. So I want make and image of sdb, rather than sdb 1,2 etc.

Can someone please help me with a way to do this, or an alternative method to achieve the same thing.

Thanks

---

### Post by mookie3three on 2009-08-11
Any help with this one guys?

Would I be able to just do a fresh install and then re-image the EXT3 partition over the top?

---

### Post by Barafu Albino Cheetah on 2009-08-11
Whatever way you do, you will have to reinstall bootloader. And, if you will reinstall botloader, you may copy it any way.  I've just yesterday moved my linux I'm answering you with. Always use the same simple thing
```
sudo rsync --exclude=/proc --exclude=/sys --exclude=/media -aHv / /newdestination
```
Don't try to copy /proc, as there are some virtual infinite files.

---

### Post by mookie3three on 2009-08-12
Thanks for that but I can't seem to get it to work using that command. But I did manage to image it using CLonezilla, and realised the reason it wasn't working was that the new SD card was 1mb smaller than the one. Anyway it works but doesn't report the partitions correctly, but I will try again using another config.

---

