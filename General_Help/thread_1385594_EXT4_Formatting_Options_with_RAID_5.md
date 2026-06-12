---
title: "EXT4 Formatting Options with RAID 5"
date: 2010-01-19
forum: General Help
---

### Post by pentas on 2010-01-19
Getting ready to format my 5-disk RAID5 array with ext4 for use as a home file server.  My current setup is using mdadm with a chunk size of 4 KB.

When using mke2fs, does anyone have any recommended options for optimally meshing the file system layout with the RAID5 layout?  (For example, 4 KB chunk size on the raid, so 4 KB block size on the file system?)

Thanks!

---

