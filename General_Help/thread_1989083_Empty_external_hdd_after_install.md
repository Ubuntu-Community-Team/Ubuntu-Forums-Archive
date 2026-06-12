---
title: "Empty external hdd after install"
date: 2012-05-28
forum: General Help
---

### Post by Marzata on 2012-05-28
After a fresh (Xubuntu 12.04 LTS) install we found our backup (WD Elements 1.5 TB) hdd shown as empty. We have not deleted / formatted / partitioned it. The disk by default has FAT32 file system. Any idea for a fix? Thank you!

---

### Post by dino99 on 2012-05-28
open synaptic (or your package manager) then install ntfs-3g to be able to work with fat32

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by Marzata on 2012-05-28
The disk is detected but somehow shown as an empty. See below: 

```
do@re:~$ df -HT
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdc1      vfat      1.5T   50k  1.5T   1% /media/E195-1230

```

---

### Post by Old_Grey_Wolf on 2012-05-28
Is that disk shared with Microsoft Windows? If it is run chdsk from Windows. Then see if Ubuntu can read it.

---

