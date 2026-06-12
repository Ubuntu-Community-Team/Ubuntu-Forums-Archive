---
title: "Got Grub Error 21, Now Can't See Ubuntu Drive"
date: 2009-11-05
forum: General Help
---

### Post by ram2008 on 2009-11-05
[SIZE="3"]This morning when I tried to boot my computer, instead of getting the usual menu, I got a message that said "Grub loading, please wait", then after that "Error 21".  I booted with a Live CD and opened a terminal and typed "fdisk -l".  The print out shows all partitions and/or drives except sdc1, the Ubuntu drive.  Is there a way to recover from this or do I have to re-install?[/SIZE]

---

### Post by Crafty Kisses on 2009-11-05
Can you post the results of the following?
```
fdisk -l
cat /etc/fstab
```
I'm aware you already looked at your disk setup but I would like to see it. Usually you can solve this issue by reinstalling GRUB.

---

### Post by ram2008 on 2009-11-05
[SIZE="3"]Hi Crafty,

Thanks for responding to my post.  Here is the result from the cat command:

roy@roy-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=49ab0690-e10c-4b41-980f-57d028a3c1d5 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=a23595c5-bd05-4db6-b163-52df58fd6560 none            swap    sw              0       0
# swap was on /dev/sdc6 during installation
UUID=0d83b057-b512-47a0-bb34-4a953f0c71ae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
roy@roy-desktop:~$ 


Here is the print out from "fdisk -l":

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x010f7430

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3077    24715971    7  HPFS/NTFS
/dev/sda2            3078       14555    92197035    f  W95 Ext'd (LBA)
/dev/sda3           14556       14592      297202+   7  HPFS/NTFS
/dev/sda5            3078        3625     4401778+   7  HPFS/NTFS
/dev/sda6            3626        9072    43752996    7  HPFS/NTFS
/dev/sda7            9073       14555    44042166    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13b48afa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 180.0 GB, 180045766656 bytes
255 heads, 63 sectors/track, 21889 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc94dc94

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       21563   173204766   83  Linux
/dev/sdc2           21564       21889     2618595    5  Extended
/dev/sdc5           21564       21867     2441848+  82  Linux swap / Solaris
/dev/sdc6           21868       21889      176683+  82  Linux swap / Solaris

Disk /dev/sdf: 1004 MB, 1004535808 bytes
7 heads, 38 sectors/track, 7375 cylinders
Units = cylinders of 266 * 512 = 136192 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        7376      980864+   6  FAT16
roy@roy-desktop:~$ 

You'll notice that the Ubuntu drive, sdc1, now shows up.  This happened a few hours ago.  I had booted from my USB drive and when I exited from that, much to my surprise, it booted to 9.04 as always.  Even though I'm back in 9.04, not everything is right.  I can't write to any of my NTFS drives which I normally do routinely.  It seems to me that either the OS is totally screwed up or there's a serious problem with the hard drive.  At this point I'm inclined to just accept the loss of data and replace the hard drive.  The system is not reliable in its present configuration. This is the second time this week that I've had trouble booting and getting the Grub Error 21.  The first time I ran a "fsck" and that seemed to have fixed something but obviously not permanently.[/SIZE]

---

### Post by ranch hand on 2009-11-05
Why do you think that the drive is going bad?

---

