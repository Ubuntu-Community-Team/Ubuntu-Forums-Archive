---
title: "Removing extents or converting to ext3   ?"
date: 2009-12-05
forum: General Help
---

### Post by rwt911 on 2009-12-05
I am wanting to view my files on my ubuntu partition from my windows partition. Currently the ubuntu partition has a ext4 partition with extents enabled. 

If I understand correctly the only way to view ext4 partitions from a windows partition is by disabling extents or downgrading to ext2/3.

What ways could I do either without disrupting nt of my data?

If it matters I am using ubuntu 9.10.

Thanks

---

### Post by rwt911 on 2009-12-06
Bump...;)

---

### Post by fluffman86 on 2009-12-06
Linux has excellent NTFS support.  Put all of the data you want to share on an NTFS partition, but don't switch from EXT4.  Ext4 way faster than ext3.  I couldn't give it up now.  :)

---

