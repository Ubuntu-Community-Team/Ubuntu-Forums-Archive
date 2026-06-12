---
title: "how to install grub on my separate partition?"
date: 2011-10-18
forum: General Help
---

### Post by Helen84 on 2011-10-18
i have made a partition layout with ubuntu and windows and some extra partitions i created spare to use for operating systems later on. I made a special partition on /dev/sda5 that i want to use just for a grub boot manager to manage all my other operating systems. At the moment my pc boots from the grub installed with the ubuntu10.10 on /dev/dsa6.

how can i set my pc to install grub on /dev/sda5 "grub dedicated" to handle all the other operating systems now and the future. at the moment i have not formatted it just labelled it. i have gparted installed so i can format it as ext2 or ext4? 

root@helen-ubuntu:~# fdisk -ls

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8cdd4106

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS **<-WINDOWS 7 **
/dev/sda2              13       25510   204800000    7  HPFS/NTFS <**-WINDOWS 7 **
/dev/sda3           25510      121602   771857409    5  Extended
/dev/sda5           25510       25574      512000   83  Linux **<GRUB DEDICATED**
/dev/sda6           25574       51070   204800000   83  Linux **<-UBUNTU-10.10**
/dev/sda7           51070       52090     8192000   82  Linux swap / Solaris
/dev/sda8           52090       53365    10240000   83  Linux **<-NOTHING YET**
/dev/sda9           53365       54640    10240000   83  Linux **<-NOTHING YET **
root@helen-ubuntu:~#

---

### Post by oldfred on 2011-10-18
You can do that, I used to with grub legacy and only kinda do it with grub2. 

One of the main advantages of grub2 is its os-prober that finds and adds boot stanzas to your grub.cfg file so you can boot all installs.

If you have a grub only partition you will have to manually add boot stanzas. If you know boot stanzas you can easily add them, but most users do not. I started by adding a stanza to 40_custom and now turn off os-prober most of the time and just use my own 40_custom for my other installs.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

If you just want to try other installs you can even boot directly from the grub partition.
This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

I have a ISO boot stanzas in my boot and grub2 installs in USB flash drives with FAT32, NTFS and Linux formats.

---

