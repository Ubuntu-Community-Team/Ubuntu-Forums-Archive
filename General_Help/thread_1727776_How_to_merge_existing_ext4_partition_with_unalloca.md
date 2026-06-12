---
title: "How to merge existing ext4 partition with unallocated space"
date: 2011-04-12
forum: General Help
---

### Post by piyush.kansalx on 2011-04-12
Hi,

Referring to below screen-shot, can you please suggest how can I merge the unallocated space of 8.13GiB in the existing ext4 partition (/dev/sdb5).

---

### Post by Hedgehog1 on 2011-04-12
You will not be 'merging', you will be 'resizing' a partition to also use the empty space next to it.

In case you want to make /dev/sdb5 bigger, you will first need to move/resize /dev/sdb2 (the extended partition it lives in) and then move/resize /dev/sdb5.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-12
=dupe= I have never done that before...

---

