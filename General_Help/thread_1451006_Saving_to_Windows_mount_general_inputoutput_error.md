---
title: "Saving to Windows mount: general input/output error"
date: 2010-04-09
forum: General Help
---

### Post by mcjohnson on 2010-04-09
Hi all,

I'm having trouble saving changes I make to files that are saved on a Windows partition while in Ubuntu. 

So say File.doc is saved in My Documents in Windows. I boot into Ubuntu, Windows automounts to /media/windowsmnt, I open the file in Open Office Word Processor, and I make some changes. When I try to save, I get the following errors:

'Error saving the document File: General input/output error while accessing /media/windowsmnt/Documents and Settings/My Name/My Documents/File.doc.'

Then that comes up a second time, followed by

'Error saving the document File: General Error. General input/output error.'

Meanwhile, a new file opened in Ubuntu saves to the Windows partition just fine. I'm not sure if it's related, but 'sudo fdisk -l' in Terminal gives me something different than it used to, something about partitions not being in order. Thanks for the help, I appreciate it.

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        6693    53713327+   7  HPFS/NTFS
/dev/sda3            6694        9546    22916722+   5  Extended
/dev/sda5            9363        9546     1477948+  82  Linux swap / Solaris
/dev/sda6            6694        9362    21438679+  83  Linux

Partition table entries are not in disk order
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 1015 MB, 1015021568 bytes
32 heads, 61 sectors/track, 253 cylinders
Units = cylinders of 1952 * 2048 = 3997696 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      398636      983425  2283019262   72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(398635, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(983424, 30, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       86419     1078237  3872056480   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(86418, 26, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1078236, 17, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      957932     1949749  3872056384   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(957931, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1949748, 25, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?     1478321     1478349      110998    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(1478320, 8, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1478348, 22, 13)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

