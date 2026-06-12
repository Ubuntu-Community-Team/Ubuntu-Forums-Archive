---
title: "Mounting NTFS partitions read-only on the 9.10 LiveCD"
date: 2010-03-10
forum: General Help
---

### Post by ronchi on 2010-03-10
I'm using the 9.10 (32-bit) LiveCD to examine machines having Windows partitions.  I want to be able to say that the hard disk was not tampered with in any way, and that means mounting the partition read-only (e.g., sudo mount -t ntfs -r ... sudo mount -t ntfs -o ro ...).

When I use the mount command on the LiveCD for a non-NTFS partition (e.g., a Linux partition), using mount -t auto -r ... works just fine, and the partition is mounted with read and execute (rx) but not write privileges.  Wonderful.  No problem.

However, when I mount an NTFS partition, no matter whether I have the -r; -o ro,force, in the mount command, the partition is still mounted read-write, and not read only.  I've play around with the mount command on an NTFS partition, but to no avail.  No matter what I do with the mount command, the NTFS partition is always mounted read-write.  

Why is it on the LiveCD that when mounting an NTFS partition, it mounts with write privileges even when you're expressly telling the system not to do so?  More to the point, is there something that I can do with the LiveCD image (i.e., a custom LiveCD image) to prevent an NFTS partition from mounting with read-write privileges?

---

### Post by dcstar on 2010-03-10
> **ronchi said:**
> I'm using the 9.10 (32-bit) LiveCD to examine machines having Windows partitions.  I want to be able to say that the hard disk was not tampered with in any way, and that means mounting the partition read-only (e.g., sudo mount -t ntfs -r ... sudo mount -t ntfs -o ro ...).

When I use the mount command on the LiveCD for a non-NTFS partition (e.g., a Linux partition), using mount -t auto -r ... works just fine, and the partition is mounted with read and execute (rx) but not write privileges.  Wonderful.  No problem.

However, when I mount an NTFS partition, no matter whether I have the -r; -o ro,force, in the mount command, the partition is still mounted read-write, and not read only.  I've play around with the mount command on an NTFS partition, but to no avail.  No matter what I do with the mount command, the NTFS partition is always mounted read-write.  

Why is it on the LiveCD that when mounting an NTFS partition, it mounts with write privileges even when you're expressly telling the system not to do so?  More to the point, is there something that I can do with the LiveCD image (i.e., a custom LiveCD image) to prevent an NFTS partition from mounting with read-write privileges?

Not **all** mount commands apply to **all** filesystems, you will have to read the exact commands available for NTFS filesystems and try to use them.

---

