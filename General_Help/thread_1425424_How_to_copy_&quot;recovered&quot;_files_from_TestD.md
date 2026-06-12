---
title: "How to copy &quot;recovered&quot; files from TestDisk?"
date: 2010-03-09
forum: General Help
---

### Post by ushpiy on 2010-03-09
Hello!

My one partition while resizing in GParted had died and now as in the process to recover data from it, I have loaded Parted Magic on my USB drive and am booting off it and through Testdisk I do the process and come to the part where I am presented with my files (which were in the dead partition).
I understand that I can't copy the files back to another partition on the same drive, thus I am using my USB to copy some important things from the dead partition using Testdisk but when I select the option to copy, am presented with where to copy and when I select the desired place, it says the files are copied but when I boot of a (real) OS and try to view the files on the USB they aren't there.

So I hope you guys understood my problem and would help me recover the data.

Thanks
Heres the output of "fdisk -l" if it helps:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd694ae23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391    7  HPFS/NTFS
/dev/sda2              14        6540    52428127+   7  HPFS/NTFS
/dev/sda3            6541       58190   414878625    5  Extended
/dev/sda4   *       58191       60801    20972857+  af  HFS / HFS+
/dev/sda5            6541       32039   204816097    7  HPFS/NTFS
/dev/sda6           40611       43221    20972826   af  HFS / HFS+
/dev/sda7           43222       58190   120238461    7  HPFS/NTFS

Disk /dev/sdb: 7969 MB, 7969177600 bytes
221 heads, 20 sectors/track, 3521 cylinders
Units = cylinders of 4420 * 512 = 2263040 bytes
Disk identifier: 0x0000feab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2        3522     7778304    b  W95 FAT32

```
where sdb1 is my USB drive and sda5 is the dead partition.

Thanks!

---

### Post by Herman on 2010-03-09
:confused: Probably there are people here who want to help you but I'm sorry, I have to tell you that your post just doesn't make any sense. 
Can you try to write it again and be careful to get your story explained more accurately and correctly please?

TestDisk is not a file recovery program, it's for recovering lost partitions or fixing the partition table. PhotoRec can recover lost files if the file system has been destroyed, but it doesn't show you your files. You can choose what kind of file you would like PhotoRec to search for each time though. Also, if you have Parted Magic in a USB you probably need to mount your other file system before you can copy anything to it, maybe you're copying files to the LiveCD operating system? (I'm guessing it's some kind of 'persistence' install in the USB drive). 

Maybe if you try to explain again somebody will be able to help? :D

EDIT: Unless TestDisk has changed a lot since last time I used it a couple of weeks ago and I'm out of date.

---

### Post by ushpiy on 2010-03-10
Thanks but I believe I have managed to solve the issue myself.

---

