---
title: "resize2fs: &quot;inode is from a bad block in the inode table&quot;"
date: 2010-07-09
forum: General Help
---

### Post by rhd on 2010-07-09
I was using gparted from a live usb to resize an ext4 partition and it failed while running resize2fs. The error it gave was
```
resize2fs: The inode is from a bad block in the inode table while trying to resize /dev/sda5
please run 'e2fsck -fy /dev/sda5' to fix the filesystem after the aborted resize operation.
```So then I ran e2fsck (without the yes to all option) and tried to resize the partition in gparted again. The resize still failed. 
Output of the fsck:
```
e2fsck 1.41.11 (14-Mar-2010_
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 248005/5922816 files (0.8% non-contiguous), 3120976/23677801 blocks

```The partition boots fine. What could be wrong with my filesystem?:confused:

---

### Post by rhd on 2010-07-09
ker-bump?

---

