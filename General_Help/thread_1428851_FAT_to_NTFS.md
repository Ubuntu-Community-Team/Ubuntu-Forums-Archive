---
title: "FAT to NTFS"
date: 2010-03-13
forum: General Help
---

### Post by nischalinn on 2010-03-13
How to convert FAT file system to NTFS file system via Ubuntu,are there any commands to do this task?

---

### Post by srs5694 on 2010-03-13
I don't know of any in-place FAT-to-NTFS conversion utility for Linux. Such an option might be supported by some Windows utilities, but I've never looked into it. AFAIK, the only way to do this in Linux would be to:


[list=1]
[*]Mount the FAT partition
[*]Create a backup, say using tar, or just copy the files to another directory using cp
[*]Unmount the FAT partition
[*]Convert the FAT partition to NTFS, either by using GNU Parted or one of its GUI brethren or by using mkfs.ntfs and then changing the partition type code using fdisk
[*]Mount the NTFS (formerly FAT) partition
[*]Extract the backup into the new NTFS partition
[/list]

---

### Post by TitanusEramius on 2010-03-13
I agree.
In Linux I don't think there is another way to do it, but I know Windows have the tools needed to convert FAT to NTFS:
[http://technet.microsoft.com/en-us/library/bb456984.aspx](http://technet.microsoft.com/en-us/library/bb456984.aspx) (sorry for linking to Microsoft by the way :icon_frown: )

---

