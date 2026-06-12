---
title: "Weird RAID5 expansion issue"
date: 2011-09-23
forum: General Help
---

### Post by GuiGuy on 2011-09-23
Hi all,

I had a 3 X 2T WD (same batch) RAID5 setup using mdadm. The array was reported as having 3.7T of storage available, which seemed correct.

When the free space of the array got to ~600G remaining, I decided to ad another 2T (WD, same type, different batch) to the array. [_I used this thread as my guide_]("http://ubuntuforums.org/showthread.php?t=517282").Despite my apprehension (I always expect anything I do in a shell to end in tears), everything seemed to go well. After 30 hours of rebuilding the array came up to ~6T indicated. 

However, free space has remained at ~600G. IN other words, despite adding and seemingly integrating an extra 2T into the array, **available free space did not increase**. Conversely, total available space is indicated as having increased significantly.

Can any one enlighten me?

Thanks

---

