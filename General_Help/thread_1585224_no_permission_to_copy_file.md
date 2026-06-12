---
title: "no permission to copy file"
date: 2010-09-30
forum: General Help
---

### Post by tigs6969 on 2010-09-30
looked through the forum but no help
anyway my hd is 1.5tb western digital, just installed it 
did sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11661    93666951   83  Linux
/dev/sda2           11662       12161     4016250    5  Extended
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00057ad5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001    b  W95 FAT32

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5a5aacc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60149   483146811    7  HPFS/NTFS
/dev/sdc2           60150       60801     5237190    5  Extended
/dev/sdc5           60476       60779     2441848+  83  Linux
/dev/sdc6           60780       60801      176683+  82  Linux swap / Solaris
/dev/sdc7           60150       60453     2441817   83  Linux
/dev/sdc8           60454       60475      176683+  82  Linux swap / Solaris

its the 2nd one on the list

god knows why but the name of it in media is 6e0d6076-3916-4b5b-8e73-f8cabcde6218
i did  chown -R cuddles /media/6e0d6076-3916-4b5b-8e73-f8cabcde6218 
but  chown: cannot read directory `/media/6e0d6076-3916-4b5b-8e73-f8cabcde6218/lost+found': Permission denied
any help?

---

### Post by tigs6969 on 2010-09-30
actually forget this whole topic i forgot to write sudo before chown :confused::confused::confused::confused: idiot i am its working :D

---

### Post by mattgyver83 on 2010-09-30
> 
god knows why but the name of it in media is 6e0d6076-3916-4b5b-8e73-f8cabcde6218

Glad you figured it out, just an FYI that strange number is the UUID, The Universal Unique Identifier of that drive.  I believe if it had a label it would be mounted by its label, if you manually mount it to a specific mountpoint it can have whatever name you want :)

---

### Post by andrewthomas on 2010-09-30
You can easily set a label for a partition using

System > Administration > Disk Utility

Then select drive and Edit Filesystem Label

---

