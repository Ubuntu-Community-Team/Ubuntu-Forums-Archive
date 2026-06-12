---
title: "Partitioning method for Ubuntu 10.10"
date: 2011-03-25
forum: General Help
---

### Post by xosman on 2011-03-25
Greetings,

I have a question regarding partitioning method for Ubuntu.
Originally I had two partitions C 80GB (Win 7) and D about 160GB (my personal data) both NTFS. What I've done, through Windows 7's Disk Management tool I shrunk partition D and created unallocated space of 23 GB on the drive. Then, I divided this space on two partitions one 20GB (as /) and another one 3GB (as swap) and I formatted them in NTFS.
After this operation I started installing Ubuntu 10.10 and I reformatted both of them for 20GB using ext4 file system assigning it as / mount point and 3GB as swap.

My question is does it really matter where I created these partitions? Are they equivalent to if I created them during Ubuntu installation (using free space instead)?

Thanks for your viewpoints.

Best regards,
Osman.

---

### Post by lithopsian on 2011-03-25
Yes, you'll be fine.

---

### Post by xosman on 2011-03-25
Thanks very much for the reply!

Below/above is my screenshot from diskpart. Is this configuration OK, I mean type of partitions. Btw what does it mean 'offset'?

Thanks a lot again!

---

### Post by oldfred on 2011-03-25
I am not familiar with windows, but the offset looks like the start point on the drive.

You do have to be careful creating partitions with Windows. If you create more than 4, it does not use the common extended partition and create logicals, but converts from basic to dynamic or a Logical volume system that is proprietary to windows and not compatible with anything including some windows tools. Yours looks just fine.

Better to use windows tools for Windows and Linux tools for Linux, except sometimes you can use Linux tools to fix Windows but never vice-versa.

---

### Post by xosman on 2011-03-26
Thanks very much for explanation and conclusion!

All the Best,
Osman.

---

