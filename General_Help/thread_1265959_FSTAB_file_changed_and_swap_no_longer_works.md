---
title: "FSTAB file changed and swap no longer works"
date: 2009-09-14
forum: General Help
---

### Post by sevenflo on 2009-09-14
Hey guys,

I originally installed Ubuntu and it had the whole hard drive. I decided to change my drive to a larger one. I configured it as below in partitions.jpg. 

I backed up my system using this tar method: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Then I reinstalled Ubuntu on the new drive. I decided to put the system on ext4 and have my /home on ext3. 

After reinstalling the system, I untarred the backup. Things came back the way they were except for a few things. One of them being my swap space is no longer available and I cannot hibernate. Just in case these are important, I'll write the two other issues I noticed (not a big deal). 

1. I had the linux server kernel installed, now it's not. I had it for PAE supprt (4gb ram). And yes I'm aware 64-bit ubuntu solves the trick, I just don't have time to reinstall my system from scratch. 
2. Songbird doesn't open. 
3. SWAP space is unavailable.

The first two don't matter as I hear Ubuntu 9.10 will support PAE and Songbird I'll just reinstall.

Here is what my system tells me:

_**fdisk:**_

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

**_fdisk -l:_**

/dev/sda1   *           1        3647    29294496   83  Linux
/dev/sda2            3648       60801   459089505    5  Extended
/dev/sda5            3648       27962   195310206   83  Linux
/dev/sda6           54723       60801    48829536    b  W95 FAT32
/dev/sda7           27963       29421    11719386   82  Linux swap / Solaris

_**/etc/fstab:**_

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=f14c97f8-fb32-459c-9f75-0c109a26ddaa /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6ac6ba37-3bd8-4bd1-a50f-43bf40e226b3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Lastly, in the attached image gparted.jpg, is the current layout of my system + an interestin message.

1. How can I set the system back to use the partitions I assigned in partitions.JPG ?
2. Is my system (with the exception of SWAP) being used the way I want it? It says the gparted tells me the ext4 partition is not mounted. But I wanted Ubuntu to be installed and boot off of that partition

Note: The extra partitions, I don't want mounted automatically. They're fine as they are.

Thanks!
If you need any more info, just let me know.

---

### Post by carl4926 on 2009-09-14
# out the current entry for swap and try

```
/dev/sda7 swap                 swap       defaults              0 0
```

---

### Post by sevenflo on 2009-09-14
Thanks Carl4926, it worked!

I'll mark it as SOLVED but should I do anything for my / to get that exclamation and WARNING out o gparted? 

John

---

