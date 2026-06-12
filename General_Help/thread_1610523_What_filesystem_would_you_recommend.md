---
title: "What filesystem would you recommend?"
date: 2010-10-31
forum: General Help
---

### Post by byb3 on 2010-10-31
At this moment I have 2x1TB (1TB usable) drives in a RAID1 array.  I am thinking about upgrading this with a further 2x2TB (2TB usable) drives in another RAID1 array.  However I would like to be able to address these two arrays as one logical 3TB array.

I've attached a picture of how it looks.  Is this possible?

I've even looked into different filesystems (XFS, NFS, btrfs, Lustre, GlusterFS) but I can't find clear confirmation on the outcome when you have variable sized drives.

---

### Post by dcstar on 2010-11-01
> **byb3 said:**
> At this moment I have 2x1TB (1TB usable) drives in a RAID1 array.  I am thinking about upgrading this with a further 2x2TB (2TB usable) drives in another RAID1 array.  However I would like to be able to address these two arrays as one logical 3TB array.
........
I've even looked into different filesystems (XFS, NFS, btrfs, Lustre, GlusterFS) but I can't find clear confirmation on the outcome when you have variable sized drives.

Filesystems are irrelevant to RAID, filesystems use whatever disk resources are made available, RAID or not:

```
man lvm
```

---

### Post by HiImTye on 2010-11-01
I love how you went to the effort of making a picture

---

