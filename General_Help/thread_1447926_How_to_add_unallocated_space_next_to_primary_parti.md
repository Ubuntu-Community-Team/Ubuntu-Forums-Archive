---
title: "How to add unallocated space next to primary partition to /home logical partition?"
date: 2010-04-06
forum: General Help
---

### Post by bilekbp on 2010-04-06
Hello, I allocated too much space to my primary / partition. I have resized it and shrunk it by 12GB. /home is a logical partition, and using gparted from a LiveCD I can't add any size to it.

Is there anything that will allow me to add the free space to /home, extending the partition?

I don't know anything about LVMs, though someone mentioned this as a possible solution in another thread similar to this question. I have only one physical drive, these are partitions on a single drive.

---

### Post by gzarkadas on 2010-04-06
You will have to first change size to the extended partition that contains /home and then expand /home to the unallocated space inside the extended partition.

---

### Post by john newbuntu on 2010-04-06
I am not sure on how your partition layout is.  But  + 1 to what gzarkadas suggested. But I feel you may have to delete a primary partition to the right of the extended one (if a primary partition exists or have used up all 3 primaries).

It is hard to say if using LVM helps at this point perhaps due to space constraints.  Generally, if you start off with LVM, you get the flexibility to adjust partitions.

One other ugly approach is to create symlinks from sub-directories in /home to a new partition that you will have to create presuming you have additional space(or link back to /home).

Can you afford to have another disk at this point so that you can offload /home to a partition on that disk?

---

### Post by plucky on 2010-04-06
> I have resized it and shrunk it by 12GB. /home is a logical partition, and using gparted from a LiveCD I can't add any size to it.

The Live CD will mount the swap partition which should be in the Extended partition.You have to un-mount the swap partition before you can resize the extended and logical partitions.

Good Luck

---

