---
title: "8gb Flash Drive stuck at 3.8gb Capacity"
date: 2010-09-25
forum: General Help
---

### Post by MrNickDanger on 2010-09-25
I have an 8gb sandisk cruzer flash drive that I wanted to remove the U3 software from. I used with this: 
[http://www.softpedia.com/get/Tweak/Uninstallers/U3-Launchpad-Removal-Tool.shtml](http://www.softpedia.com/get/Tweak/Uninstallers/U3-Launchpad-Removal-Tool.shtml)
and ran it on my windows machine because wine didn't work for it
but after it removed U3 my card only had 3.8gb. Is there any way to restore it back to 8gigs?

I've already tried reformatting with the disk utility and it just doesn't give me the option to format higher than 3.8gb.

suggestions?

---

### Post by srs5694 on 2010-09-25
Please post the output of "sudo fdisk -l /dev/sdb" (or whatever the device file is for the flash drive, if it's not /dev/sdb). Please post the output between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string to improve legibility.

---

### Post by hrickh on 2010-09-25
Your best bet is to use GParted (it's in the Ubuntu repository, if it's not already installed).

From there (as root), you can unmount the drive, then remove the fat32 partition that is most likely taking up the majority of the space.

Then you can reallocate the entire flash drive to a single 8G partition. Technically, you can resize partitions, but frankly, if you want the entire USB drive as one partition, just get ride of existing partition, then create a new single partition.

R.
==

---

### Post by Miyavix3 on 2010-09-25
[http://en.wikipedia.org/wiki/File_Allocation_Table](http://en.wikipedia.org/wiki/File_Allocation_Table)

As you can see, the max file space is 4GB. So we can assume that your flash drive got formatted to FAT.

Reformat to FAT32 (or FAT16 if you really want to) using gparted. It should be in the repositories if you don't already have it.

---

### Post by dcstar on 2010-09-26
Use **gparted** to write a new Partition Table to the device, then add whatever partitions you want.

---

