---
title: "Using Ubuntu live to restore Windows OS partition"
date: 2012-03-05
forum: General Help
---

### Post by yamanoorsai on 2012-03-05
I am trying to using Ubuntu Live to restore windows partitions. I am able to restore the windows OS if I use NTFS file partition.

I am not able to restore the OS if I use FAT 32 file formats. The partitions that I am creating are FAT32(LBA) partitions. I am using the mkfs.vfat -F32 command to format them. After copying the files, they are supposed to enter the active partition and launch an automated installation process. The partitions are not being recognised as bootable ones. Can any one point out where am I going wrong?

P.S I am also writing the MBR according to the operating system using the ms-sys command.

---

### Post by Mark Phelps on 2012-03-05
> **yamanoorsai said:**
> ...Can any one point out where am I going wrong?

Yes ... Win7 requires NTFS; it won't intall or run in FAT32 partitions.

---

### Post by yamanoorsai on 2012-03-05
I am attempting this for Windows XP

---

