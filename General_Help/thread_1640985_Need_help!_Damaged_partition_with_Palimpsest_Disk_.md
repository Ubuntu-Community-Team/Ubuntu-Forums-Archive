---
title: "Need help! Damaged partition with Palimpsest Disk Utility"
date: 2010-12-08
forum: General Help
---

### Post by anticler on 2010-12-08
I have a HDD with OS Win with three partitions NTFS.
I  installed Ubuntu 10.10 on new partition, and I left the old partitions on the disk, because there are a lot of my personal data.

When I was looking for how to mount partitions on startup, I was fortuitously to Palimpsest Disk Utility selecting the checkbox on sda2 as a boot, and apply. But I saw that it was wrong and took the check back. And after this was damaged NTFS on the partition sda2. Windows shows the partition as RAW.

How do I now restore my partition?

---

### Post by srs5694 on 2010-12-08
First, show us the output of "sudo fdisk -lu /dev/sda", preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility. If you're very very lucky, you may be able to change the partition type code and get everything back.

If you're less lucky, you'll have to use Windows utilities, such as CHKDSK or commercial disk utility packages, to recover your data; or you may need to use [PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) or a similar tool to recover individual files. I recommend holding off on using such techniques until you get some feedback on the fdisk output, though.

---

### Post by anticler on 2010-12-08
I connected the drive to windows and run the test in the R-Studio. 
It showed me partition as NTFS and real size of partition. And Error:
[COLOR="DimGray"]Error File System - Unable to open the volume because MFT file is outside disk bound[/COLOR]s

---

