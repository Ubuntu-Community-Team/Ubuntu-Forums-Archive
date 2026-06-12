---
title: "repairing from another system"
date: 2006-03-07
forum: General Help
---

### Post by steve196 on 2006-03-07
At the moment my Ubuntu system sees 1kb sized "ghost" partitions, and I do not dare to boot it, since I fear, an imperfect interpretation of partition tables could lead to severe data loss (the error seems to be systematic. The setup CD doesn´t display those fake partitions, but gives the others numbers, as if a partition were left out, like 1,2,4,5).
My question is: Where in the configuration can the error be, and how can I fix it, without using a configuration tool (which would require me to boot the faulty system first, which I don´t want to do).

---

### Post by el3ktro on 2006-03-07
I don't know exatly what you mean. You say your Ubuntu install sees "ghost" partitions, but you don't want to boot it because of that. But when you don't boot it, how do you know that this system which you don't boot sees those "ghost" partitions?

Can you post the output of a command etc. which shows us these partitions?

Tom

---

### Post by steve196 on 2006-03-07
I had installed the system, booted into it and wanted to cuhange the way partitions are mounted (in the bootup I saw ntfs partitions mounted rw, which is wrong). In the partition manager (or whatever you name it) I saw the 1 kb sized partitions (one for each disk). They were mounted. I did not dare to access them. I immediately exited the system after I saw that.
Since someone else had solved the same problem by formatting the linux partition and reinstalling, I tried to do that. In the partitioner from the install program I saw the odd partition numbering and aborted install.

---

### Post by Mustard on 2006-03-07
If you booted up with a live CD you might be able to retrieve your critical data, and save it on some external storage medium ie CD, DVD, USB drive or second hard drive.  After doing that you could repartition and reinstall.  A live CD like Kanotix might do the trick.

Getting the live CD would entail using someone elses computer, internet connection and CD/DVD burner.

I'm not exactly sure from your description what you are seeing either, but if you think you have a problem then perhaps its time to backup now and start from scratch.

---

### Post by Ocxic on 2006-03-07
I'd say boot your system, It's already been booted once, and i doubt you have to worry about data loss, and check what fdisk -l /dev/hd??  says about your harddrives and post the output.

---

### Post by steve196 on 2006-03-07
Thank you.
fdisk has something unusual to say. I do not know what that means though. I have two Hds with four partitions each and a third one with one partition. All are fat, fat32 or ntfs except one reiser and one swap. The partitions are interpreted correctly by win2k
> Password:

Disk /dev/hda1: 2146 MB, 2146765824 bytes
255 heads, 63 sectors/track, 260 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/hda1p1   ?      116388      126889    84344761   69  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(68, 13, 10) logical=(116387, 225, 36)
Partition 1 has different physical/logical endings:
     phys=(288, 115, 43) logical=(126888, 82, 1)
Partition 1 does not end on cylinder boundary.
/dev/hda1p2   ?      105915      222310   934940732+  73  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(105914, 175, 47)
Partition 2 has different physical/logical endings:
     phys=(366, 32, 33) logical=(222309, 108, 57)
Partition 2 does not end on cylinder boundary.
/dev/hda1p3   ?           1           1           0   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(0, 40, 54)
Partition 3 has different physical/logical endings:
     phys=(372, 97, 50) logical=(0, 40, 53)
Partition 3 does not end on cylinder boundary.
/dev/hda1p4               1      213826  1717556736    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(213825, 235, 42)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/hda2: 1044 MB, 1044610560 bytes
255 heads, 63 sectors/track, 127 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/hda2p1   ?      105945      207378   814758329+  74  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 36) logical=(105944, 131, 12)
Partition 1 has different physical/logical endings:
     phys=(366, 104, 37) logical=(207377, 59, 61)
Partition 1 does not end on cylinder boundary.
/dev/hda2p2   ?       82801      116350   269488144   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(107, 121, 32) logical=(82800, 34, 51)
Partition 2 has different physical/logical endings:
     phys=(10, 121, 13) logical=(116349, 218, 61)
Partition 2 does not end on cylinder boundary.
/dev/hda2p3   ?       33551      120595   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(33550, 137, 11)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(120594, 153, 54)
Partition 3 does not end on cylinder boundary.
/dev/hda2p4   ?      243387      243391       32672   bb  Boot Wizard hidden
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(65, 1, 0) logical=(243386, 212, 25)
Partition 4 has different physical/logical endings:
     phys=(128, 0, 7) logical=(243390, 229, 37)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/hda3: 888 MB, 888330240 bytes
255 heads, 63 sectors/track, 108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/hda3p1   ?      116388      126889    84344761   69  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(68, 13, 10) logical=(116387, 225, 36)
Partition 1 has different physical/logical endings:
     phys=(288, 115, 43) logical=(126888, 82, 1)
Partition 1 does not end on cylinder boundary.
/dev/hda3p2   ?      105915      222310   934940732+  73  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(105914, 175, 47)
Partition 2 has different physical/logical endings:
     phys=(366, 32, 33) logical=(222309, 108, 57)
Partition 2 does not end on cylinder boundary.
/dev/hda3p3   ?           1           1           0   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(0, 40, 54)
Partition 3 has different physical/logical endings:
     phys=(372, 97, 50) logical=(0, 40, 53)
Partition 3 does not end on cylinder boundary.
/dev/hda3p4          179626      179629       26207+   0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(179625, 87, 47)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(179628, 154, 45)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/hda5: 245.9 GB, 245976966144 bytes
255 heads, 63 sectors/track, 29904 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/hda5p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/hda5p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hda5p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/hda5p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/hdc1: 5066 MB, 5066740224 bytes
16 heads, 63 sectors/track, 9817 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

     Device Boot      Start         End      Blocks   Id  System

Disk /dev/hdc3: 320 MB, 320785920 bytes
16 heads, 63 sectors/track, 621 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Disk /dev/hdc3 doesn't contain a valid partition table

Disk /dev/hdc4: 68.2 GB, 68261598720 bytes
16 heads, 63 sectors/track, 132265 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/hdc4p1   ?     1920663     3757825   925929529+  68  Unknown
Partition 1 does not end on cylinder boundary.
/dev/hdc4p2   ?     1319628     1854326   269488144   79  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hdc4p3   ?      534712     1921977   699181456   53  OnTrack DM6 Aux3
Partition 3 does not end on cylinder boundary.
/dev/hdc4p4   ?     1383560     1383581       10668+  49  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/hdc5: 6374 MB, 6374559744 bytes
16 heads, 63 sectors/track, 12351 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/hdc5p1   ?      216399     1904881   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/hdc5p2   ?      723265     1262922   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hdc5p3   ?      167316      167316           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/hdc5p4         2671568     2671619       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/hdd1: 160.0 GB, 160039240704 bytes
255 heads, 63 sectors/track, 19456 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/hdd1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/hdd1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hdd1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/hdd1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


---

### Post by steve196 on 2006-03-07
Okay, that was wrong. It treated the partitions as disks. I tried the same command again with just one '?' and it came up with something more reasonable.
> Password:

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         261     2096451    6  FAT16
/dev/hda2             262         388     1020127+   6  FAT16
/dev/hda3             389         496      867510    b  W95 FAT32
/dev/hda4             497       30401   240211912+   5  Extended
/dev/hda5             497       30401   240211881    7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         616     4947988+  83  Linux
/dev/hdc2             617        1391     6225187+   f  W95 Ext'd (LBA)
/dev/hdc3            1392        1430      313267+  82  Linux swap / Solaris
/dev/hdc4            1431        9729    66661717+   c  W95 FAT32 (LBA)
/dev/hdc5             617        1391     6225156    7  HPFS/NTFS

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       19457   156288321    7  HPFS/NTFS


Still there is one nonexisting partition on each of two HDs and it shares space with a legitimate one.

---

### Post by Ocxic on 2006-03-07
did you just do an install of ubuntu?? do you have a different boot loader then Grub/lilo??

this looks to me like some bootloader has modified the partitons of your disks possibly to make sense of an unknown partiton, or your partitioner smucked something. 
It's only one kiloyte as you say, possibly the reserve sector of your hard disk scince it is at the end and there can only be 4 primary partitons this says your have five which is not right.
All of your partitons line up correctly and filesystems are detected correctly if that is how you've formatted the disks.
If your system has been like this for a while and you havent notice any file corruption, disk read or i/o errors, or a noticable decrese in hard disk performance, you shouldn't have to worry, but try not to go near the perticular partiton. get back to me on those questions and we'll see whats up.

---

### Post by steve196 on 2006-03-08
For Ubuntu install I only formatted the Linux partition. I have lilo on the linux partition and NTloader (the thing that comes with win2k) as boot manager. I did not change the partitioning. There is no exotic type of partition and afaik the partition tables are standard too. I have used those partitions as they are under win2k for years without issues.

---

### Post by Ocxic on 2006-03-08
It's got to be ntbootloader doing something witht he partiton tables and installing linux and foramtting a partiton could have brought a small bug to the surface, but like i said if all seems well you shouldn't have to worry. where are they mounted for your system? the answer will allow me to decide if it's safe to remove the partiton from the table and fix averyhting so it goes back to normal.

---

