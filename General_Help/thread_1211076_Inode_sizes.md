---
title: "Inode sizes"
date: 2009-07-12
forum: General Help
---

### Post by spongypants23 on 2009-07-12
So I know that Intrepid uses an inode size of 256 (whatever that means). It appears that Jaunty's default inode size is also 256.

Is there a way to change this to 128 during the formatting process of the installer?

---

### Post by blueridgedog on 2009-07-12
Yes, you can run mke2fs (mkfs.ext3) with an inode option:

```
       -I inode-size
              Specify the size of each inode in bytes.  mke2fs creates 256-byte inodes by default.  In kernels after 2.6.10 and some ear&#8208;
              lier vendor kernels it is possible to utilize inodes larger than 128 bytes to store extended attributes for  improved  per&#8208;
              formance.   The inode-size value must be a power of 2 larger or equal to 128.  The larger the inode-size the more space the
              inode table will consume, and this reduces the usable space in the filesystem and can also negatively  impact  performance.
              Extended  attributes  stored in large inodes are not visible with older kernels, and such filesystems will not be mountable
              with 2.4 kernels at all.  It is not possible to change this value after the filesystem is created.
```

This will erase the drive and reformat it.

Why do you want to change the inode size?

---

### Post by spongypants23 on 2009-07-12
So that I can access the partition from Winows. The ExtIFS doesn't work with 256, apparently.

---

