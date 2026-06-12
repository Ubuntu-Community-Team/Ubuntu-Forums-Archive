---
title: "Problems with usb pen drive."
date: 2006-02-09
forum: General Help
---

### Post by chuckbennett1961 on 2006-02-09
I have a usb pin drive that was formated under Windows 2000 and it was formated with fat16, and that is what I want.  Now I need configure it with one  partition and am having problems with it.  Can some one give me step by step instructions on how to partition this thing with out loosing fat16.  I'll keep looking my self and if it find an answer I'll post it.

Thank you.

---

### Post by chuckbennett1961 on 2006-02-10
Just some added information.  These generic pin drives came blank.  I mean blank.  No partition or anything.  I just wanted to give you all just a little more information.

---

### Post by chuckbennett1961 on 2006-02-16
I found someone that knows how to partition a pin drive with  fat16 and make it look like a dos partition.  (Remember these pen drives were blank when new)

Frist thing to do is ls /dev/sd* to find out what it is called 
returned /dev/sda
fdisk /dev/sda
command (m for help):p
((you get a bunch of junk back)))

command (m for help):d
Partition number (1-4)1

command (m for help):d
Partition number (1-4)2

command (m for help):d
Partition number (1-4)3

command (m for help):d
Partition number (1-4)4

command (m for help):p

Command (m for help): p

Disk /dev/sda: 129 MB, 129499136 bytes
4 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 248 * 512 = 126976 bytes

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-1019, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-1019, default 1019): 
Using default value 1019

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 6
Changed system type of partition 1 to 6 (FAT16)

Command (m for help): p

Disk /dev/sda: 129 MB, 129499136 bytes
4 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 248 * 512 = 126976 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019      126325    6  FAT16

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.
Syncing disks.

mkdosfs /dev/sda1

remove pen drive.

---

### Post by chuckbennett1961 on 2006-02-16
replace the :p with first the :
and then a p.  It seems the configuration of the forum is to take these two characters and make them a smiley.  Sorry.

---

