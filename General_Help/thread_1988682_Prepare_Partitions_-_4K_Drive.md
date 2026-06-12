---
title: "Prepare Partitions - 4K Drive"
date: 2012-05-28
forum: General Help
---

### Post by PierreRobiquet on 2012-05-28
Hello,

I've just purchased a Seagate Momentus XT 750GB drive, which features the 4k sector sizes. I wish to install Windows 7 and dual boot with either Ubuntu or Lubuntu, but I'm wondering what would be the best way to partition the drive?

I would typically launch gparted and do the partitioning myself, e.g. creating the NTFS file system for Windows and the ext4 and swap for the Linux install however is there anything special that needs to be done to ensure it aligns with the new sector format? I'll use the version of gparted that's included in Ubuntu 12.04 but I can also burn a gparted live CD if needed.

---

### Post by steevp on 2012-05-28
Recent versions of Gparted use MiB alignment by default, which is fine for 4K disks.

The version in 12.04 is fine.

---

