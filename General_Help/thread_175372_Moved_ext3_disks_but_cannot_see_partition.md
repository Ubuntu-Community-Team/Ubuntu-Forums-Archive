---
title: "Moved ext3 disks but cannot see partition"
date: 2006-05-13
forum: General Help
---

### Post by petef on 2006-05-13
Hi guys,

I have two machines on ubuntu the old one had a 2nd 40Gb "slave" drive in it formatted as ext3. I've now put this drive into my new machine but if I do 

fdisk -l 

I get the following 
-------------------------------------------------------------------------
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1216     9767488+  83  Linux
/dev/hda2   *        1217        4783    28651927+  83  Linux
/dev/hda3            4784        4865      658665    5  Extended
/dev/hda5            4784        4865      658633+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Disk /dev/hdb doesn't contain a valid partition table
--------------------------------------------------------------------------
As you can see /dev/hdb the 2nd drive shows as not having a valid partition table. Any ideas ???? 

Thanks in advance 

Pete

---

### Post by dcstar on 2006-05-13
[QUOTE=petef]Hi guys,

I have two machines on ubuntu the old one had a 2nd 40Gb "slave" drive in it formatted as ext3. I've now put this drive into my new machine but if I do 
......
Disk /dev/hdb doesn't contain a valid partition table
--------------------------------------------------------------------------
As you can see /dev/hdb the 2nd drive shows as not having a valid partition table. Any ideas ???? 

Thanks in advance 

Pete[/QUOTE]
The new machine's BIOS is possibly seeing the drive in a different (newer) mode than the old PC, play around with your BIOS settings for the second drive and manually try all the available options to see if that makes a difference.

---

### Post by petef on 2006-05-13
Hi 

Thanks for the reply. I've checked the BIOS already and it's seeing the drive fine ? 

I can put the old master drive in from the other Ubuntu machine and see that but not this one with the media on it ? 

Pete

---

