---
title: "ntfs partition dead"
date: 2006-02-03
forum: General Help
---

### Post by matva on 2006-02-03
my windows xp partition is dead, and i have a seperate ntfs partition that i'd like to be able to write to. Is it possible to format the partition from within ubuntu, or do i have to boot up into a partition manager? Or maybe there is a way to write to a NTFS partition that i don't know about. I'd rather that.

---

### Post by TechSonic on 2006-02-03
NTFS partitions can only be read and copied when in ubuntu.  If you need windows, try installing it on a FAT32 Partition, thus giving you the ability to write to it.  NTFS is an unstable/insecure partition table is very easy to damage if you attempt to write to it under Linux.

---

