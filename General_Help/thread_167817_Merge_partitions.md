---
title: "Merge partitions"
date: 2006-04-29
forum: General Help
---

### Post by TheTux on 2006-04-29
Hello guys..

my ubuntu partition is now only has 600 mb of free space...i only has 1 partition for ubuntu..no separated /home partition...so now i think i want to make a home partition and add some space to my root partition...i have 2gb of free space that i extracted from my windows partition...i've  attached my gparted screenshot

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=8854&stc=1&d=1146311804[/IMG]

and this is my fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        4334    19454715    f  W95 Ext'd (LBA)
/dev/hda3            4335        4831     3992152+  83  Linux
/dev/hda4            4832        4864      265072+  82  Linux swap / Solaris
/dev/hda5            1913        4079    17406396    7  HPFS/NTFS

the hda1 is my windows partition.hda3 is my ubuntu partition.hda5 is my windows backup files and installers...i dont want to remove my windows(hda1) and windows backup(hda5) partitions...so how do i merge the free 2gb of space into my ubuntu partition?

hda1(windows),hda3(ubuntu)and hda4(linux swap) are primary partitions.others in extended partition

is there anyway to do this without reinstalling windows or ubuntu?i need both ;D

if the question is not clear please tell me...i'm sorry my english is not very good

---

### Post by olsonar on 2006-04-29
Well, you can't do it from within ubuntu, since you'd have to unmount the ubuntu partition to edit it, but thats where the partitioning tools are. If you have partitioning software in windows, just use that. If not, I think the ubuntu live cds have gparted on them, so that should work, but I'm not certain.

---

