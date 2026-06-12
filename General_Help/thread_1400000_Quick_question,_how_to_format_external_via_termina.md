---
title: "Quick question, how to format external via terminal"
date: 2010-02-06
forum: General Help
---

### Post by altjx on 2010-02-06
i know there's tools like gparted, but if i have an external HD, how do i format it?

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x086f8f0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3907    31382946   83  Linux
/dev/sda2            3908       38913   281185695    5  Extended
/dev/sda5           37604       38913    10522543+  82  Linux swap / Solaris
/dev/sda6            3908       36299   260188677   83  Linux
/dev/sda7           36300       37603    10474348+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e836ce1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS

```

I want to format the /dev/sdd disk, which is 500GB, if you can, can you show me how to format it as fat32 and ntfs? i'd like to keep both in memory

---

### Post by nothingspecial on 2010-02-06
> **altjx said:**
> i know there's tools like gparted, but if i have an external HD, how do i format it?

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x086f8f0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3907    31382946   83  Linux
/dev/sda2            3908       38913   281185695    5  Extended
/dev/sda5           37604       38913    10522543+  82  Linux swap / Solaris
/dev/sda6            3908       36299   260188677   83  Linux
/dev/sda7           36300       37603    10474348+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e836ce1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS

```

I want to format the /dev/sdd disk, which is 500GB, if you can, can you show me how to format it as fat32 and ntfs? i'd like to keep both in memory

Unmount it

for fat32

```
sudo mkfs -t vfat /dev/sdd1
```

for ntfs change vfat for ntfs

---

### Post by altjx on 2010-02-06
> **nothingspecial said:**
> Unmount it

for fat32

```
sudo mkfs -t vfat /dev/sdd1
```for ntfs change vfat for ntfs

Thanks =)

---

