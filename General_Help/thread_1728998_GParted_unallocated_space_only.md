---
title: "GParted: unallocated space only"
date: 2011-04-14
forum: General Help
---

### Post by trebi on 2011-04-14
Hello,

I have accidentally deleted the first booting parition (Windows 7) with GParted, so then I immediately googled and found an utility *testdisk* which has successfully recovered the parition and it can boot and be seen from linux again. Only Exception is GParded, which sees an unallocated space on whole disk from this point!

I found this post [http://ubuntuforums.org/showpost.php?p=9089174&postcount=11](http://ubuntuforums.org/showpost.php?p=9089174&postcount=11) which looks like solution, but I can't figure he count a number of sectors *978726293*. *500107862016 / 978726293 = 510.978263885* what is near to 512 (sector size), but not equal. So I don't understand the arithmetic.

sudo fdisk -l
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29f629f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3967    31864896    7  HPFS/NTFS
/dev/sda2            3968        9140    41544604+   7  HPFS/NTFS
/dev/sda3            9140       12995    30971904   83  Linux
/dev/sda4           12995       60802   384010609+   f  W95 Ext'd (LBA)
/dev/sda5           12996       60801   384001695    7  HPFS/NTFS

```

sudo sfdisk -d /dev/sda
```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 63729792, Id= 7, bootable
/dev/sda2 : start= 63729855, size= 83089209, Id= 7
/dev/sda3 : start=146819072, size= 61943808, Id=83
/dev/sda4 : start=208762911, size=768021219, Id= f
/dev/sda5 : start=208764675, size=768003390, Id= 7

```

Could someone clarify this for me, or at least solve the GParted issue?

---

### Post by coffeecat on 2011-04-14
If you look here:

> **trebi said:**
> 
sudo fdisk -l
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, [COLOR=Red]60801[/COLOR] cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29f629f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3967    31864896    7  HPFS/NTFS
/dev/sda2            3968        9140    41544604+   7  HPFS/NTFS
/dev/sda3            9140       12995    30971904   83  Linux
/dev/sda4           12995       [COLOR=Red]60802[/COLOR]   384010609+   f  W95 Ext'd (LBA)
/dev/sda5           12996       60801   384001695    7  HPFS/NTFS

```

You'll see that the extended partition is seemingly extending beyond the physical end of the disc. This is a common problem with testdisk and Gparted cannot make sense of this partition table impossibility.

Repeat fdisk, but this time:

```
sudo fdisk -lu
```You need to -u option to get the output in sectors rather than cylinders. You need the sector figures which sfdisk is giving you. The fix is then to use sfdisk to write correct figures back to the partition table or forum member srs5694's utility fixparts.

Here is a useful link (written by srs5694) on how to fix this problem with sfdisk:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

Frustratingly, I've temporarily mislaid the link to his fixparts utility. If you search the forum for "fixparts" in srs5694's posts you'll likely find it. Sorry to leave a loose end but I need to log off now. I'll check in later.

Or srs5694 may happen along himself, in which case you couldn't be in better hands.

---

### Post by srs5694 on 2011-04-14
That was my post. I probably mistyped one of the numbers, or copied the wrong value.

Ignore that solution; it's now much easier with my [FixParts](http://www.rodsbooks.com/fixparts/) utility. You can either download the appropriate fixparts Debian file from [SourceForge](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/fixparts-binaries/) or install the full gptfdisk package for your version of Ubuntu (see the "Downloading GPT fdisk from OBS" section of [this page](http://www.rodsbooks.com/gdisk/download.html)). Then:


[list=1]
[*]Back up your data, or at least your partition table. (Your sfdisk output above backs up your partition table, so save that on another disk.)
[*]Type "sudo fixparts /dev/sda".
[*]In FixParts, type "p" to view your partitions and verify they're all present. The extended partition won't show up, but the logical it contains should. Thus, you should see four partitions, three primaries and one logical. If you don't see all the partitions, type "q" to quit and post back with a cut-and-paste of your FixParts session, along with the output of "sudo fdisk -lu" (note the critical "u").
[*]In FixParts, type "w" to save your partition table.
[/list]


This procedure should fix the problem.

---

### Post by coffeecat on 2011-04-14
The man himself! :)

---

### Post by trebi on 2011-04-14
Definitely The Man, It works! Thanks! Only problem was that extended partition with NTFS, so I had to boot in Windows, run *chkdsk /f* and reboot TWICE :)

---

### Post by ruben2020 on 2012-05-17
I used the fixparts tool and it worked very well!

However, then I couldn't boot up because my Linux boot partition was one of the extended partitions and the boot manager was GRUB. GRUB could not find it any more. I eventually fixed it.

But I propose that after doing the steps given above, do this, if your system is similar to mine. Replace /dev/sda with your harddisk.

```
sudo grub-install --recheck /dev/sda
```

If you've already run into the problem where you can't boot up any more, then boot up with a Ubuntu Live CD, and open Terminal. Assuming your Linux boot partition is /dev/sda5, you should do the following:
```

sudo mkdir /mnt/myhdd
sudo mount /dev/sda5 /mnt/myhdd
sudo grub-install --boot-directory=/mnt/myhdd/boot --recheck /dev/sda
sudo umount /dev/sda5

```

---

### Post by coffeecat on 2012-05-17
Old thread closed.

@ruben2020, the OP has not logged in for nearly a year!

---

