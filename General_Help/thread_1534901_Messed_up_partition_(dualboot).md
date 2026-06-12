---
title: "Messed up partition (dualboot)"
date: 2010-07-20
forum: General Help
---

### Post by Eszty on 2010-07-20
Hello everyone!
I'm a new Ubuntu user and I'm already a fan, but I have a small problem. I wanted to dualboot my laptop with Ubuntu 10.04 and Windows Vista. I already had Vista (and hated it), so I installed Ubuntu. It all went well, until I messed up something with the partitions (in Vista of course..). Then my laptop wouldn't start up and I got an error message ( I don't remember what it was.). So I installed Ubuntu again on another partition and it is all working now (both Ubuntu and Vista). But now I have a partition, of 15 GB I think, that I can't use for anything. I would really want that back. So my question is: Does somebody have an idea how I can fix that? 

Thank you in advance,
Eszty

---

### Post by Irony on 2010-07-20
System > Admin > Disk Utility

Then format the 15GB partition as ext4 (give it a label name) and then mount it as extra storage.

---

### Post by Eszty on 2010-07-20
That's all? Thank you :)

---

### Post by SoFl W on 2010-07-20
Be sure it isn't a 15meg recovery partition.

---

### Post by Eszty on 2010-07-20
How can I know that?
I have 4 volumes: 18GB ext4 (Filesystem, Mounted), 825MB swap space, 15GB ext4 (filesystem, not mounted) and 686MB swap space. Is the swap space the recovery? If so, can I format the one that belongs to the 15GB filesystem?

---

### Post by vicohm on 2010-07-20
Just use disk utility to fix errors and format the partition...I reccommend that if you want to dual boot your laptop with Windows and Ubuntu it is best for you to use wubi whereby ubuntu will be installed just like a program and you can dual boot..I hope the problem is not with the partition table because if so you may have to format the whole hard disk..

---

