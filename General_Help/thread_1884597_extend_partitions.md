---
title: "extend partitions"
date: 2011-11-21
forum: General Help
---

### Post by SE7EN-LOCSTA on 2011-11-21
i need to extend my storage partition, and i have reinstalled an os and gave it less space this time. now i am left with 6gb of free space that i cannot seem to do anything with. windows will not let me do anything with this free space (except give it back to windows-where i took it from in the first place). i am not sure how to go about this in ubuntu. i have apparently reached my limit for partitions on this drive, so cant just make a new one. disk utility shows me this order for my partitions.
1.system reserved
2.windows7
*3.free - taken from win7
4.storage
5.extended
  a. ubuntu
  b. swap
  c. backtrack

i need to take what is free on (3) and add it to (4). i dont have a harddrive large enough to move the files from 4, delete it and merge 3+4 together. is it possible to extend this, or should i just give that space back to windows?

---

### Post by coffeecat on 2011-11-21
If what you are calling 2 and 4 are primary partitions with free space between them (what you call 3), then it is possible to enlarge "4" to include the free space, so long as partition "4" and free-space "3" are contiguous.

**However**, it is strongly recommended not to do this unless you have backed up the data on partition "4" onto a separate medium. Such resizing usually goes OK. Occasionally it goes horribly wrong and you must have your data backed-up.

Also - your numbering does not follow the conventions for partition numbers. So that we can be sure we're talking about the same thing, open a terminal and post the output of:

```
sudo fdisk -lu
sudo blkid
```

---

### Post by jjex22 on 2011-11-21
> **SE7EN-LOCSTA said:**
> 
1.system reserved
2.windows7
*3.free - taken from win7
4.storage
5.extended
  a. ubuntu
  b. swap
  c. backtrack



I agree - back up first, if possible create a disk image using something like clonezilla - it makes fixing a lot easier! you really shouldn't have any problem extending the 3rd partition using gparted - but I usually find it's best to do big jobs like this from a gparted live cd - I do get less errors than from in an os - also apply each job one at a time - it rarely goes wrong but let's be honest safer than sorry! 

Personally I'd move the data partition inside the extended partition so it doesn't take up a primary slot, but this is a big job and you will almost certainly have to repair grub/whatever bootloader you are using after the move, so may not be worth it, but it's always an option - If you have no intention of adding a windows/osx/bsd then it isn't worth the hassle - and to be honest the next time windows makes you reinstall it, you can just get rid of that irritating back up partition in the installation options - I do it, so can confirm it doesn't affect windows at all - but deleting it from a current install will.

---

### Post by SE7EN-LOCSTA on 2011-11-21
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a31a071

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   110798847    55296000    7  HPFS/NTFS/exFAT
/dev/sda3       123090030   438889779   157899875    7  HPFS/NTFS/exFAT
/dev/sda4       438890494   488396799    24753153    5  Extended
/dev/sda5       438890496   462327807    11718656   83  Linux
/dev/sda6       462329856   468187135     2928640   82  Linux swap / Solaris
/dev/sda7       468189184   488396799    10103808   83  Linux

Disk /dev/sdc: 512 MB, 512229376 bytes
9 heads, 8 sectors/track, 13895 cylinders, total 1000448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1             233     1000447      500107+   6  FAT16
-----------------------------------------------------------------------------
/dev/sda1: LABEL="System Reserved" UUID="5E4E98174E97E655" TYPE="ntfs" 
/dev/sda2: LABEL="WIN7" UUID="2A46A62446A5F0AD" TYPE="ntfs" 
/dev/sda3: LABEL="STORAGE" UUID="3A89F6353F1573DC" TYPE="ntfs" 
/dev/sda5: UUID="fe787738-38b6-4ea0-8019-15d15e8f9069" TYPE="ext4" 
/dev/sda6: UUID="db3ac0e1-85d5-469f-918d-bec375a70148" TYPE="swap" 
/dev/sda7: LABEL="BACKTRACK" UUID="5a56bb26-3a39-4ac6-a60f-d349cd382faf" TYPE="ext4" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="FLASH512MB" UUID="049A-F620" TYPE="vfat"
------------------------------------------------------
the free space is between sda2-sda3 - i reinstalled windows with a smaller partition than last time-, and i would like to extend it to sda3 "STORAGE"

---

### Post by jjex22 on 2011-11-21
Awesome, that confirms it you've got 
ntfs
ntfs
free space
ntfs
extended.

So increasing the 3rd partition to the left as it would be displayed in gparted is completely possible,and very easy, although time consuming. However the program will move every sector, not just add some free space, so it is absolutely essential that you back up before you do this as this increases the chance of errors. Again, I recommend using a [live gparted cd]("http://gparted.sourceforge.net/livecd.php"), not doing it from the OS, also using a graphical partitioner like gparted reduces the chance of errors as you can see a representation of what's going on.

---

### Post by coffeecat on 2011-11-21
Just to add to what jjex22 said, your partition sizes are as follows:

sda1 - 105MB
sda2 - 56.6GB
free space - 6.3GB
sda3 - 161.7GB
sda4 (extended partition) - 25.3GB

As jjex22 says, resizing a partition to the left takes a very long time, and you really must backup all data first.

---

### Post by SE7EN-LOCSTA on 2011-11-21
ok, thank you guys very much. i do not have enough space to backup my storage partition [it is the backup], so i will just give that space back to windows, as i dont want to risk losing the info. i think i was using the wrong program to try to resize (disk utiility) to begin with, and windows wasnt helpful with what i was trying to do. thanks again.

---

### Post by coffeecat on 2011-11-21
> **SE7EN-LOCSTA said:**
> ok, thank you guys very much. i do not have enough space to backup my storage partition [it is the backup],

@SE7EN-LOCSTA, some food for thought for you. Your storage partition is on the same physical drive as your other partitions. This is not effective backup. If the drive failed - drives can fail catastrophically and suddenly - you would lose all your data. Your personal files are more valuable than the cost of the physical media on which they are stored. You need a separate external drive to use as backup - or more than one.

Over the years I have seen many threads on this forum where people have irretrievably lost personal files because they did not have backups on physically separate media. Please don't let yourself be one of them.

---

