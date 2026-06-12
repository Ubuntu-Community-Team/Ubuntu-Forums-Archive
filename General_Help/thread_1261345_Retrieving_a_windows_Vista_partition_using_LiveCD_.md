---
title: "Retrieving a windows Vista partition using LiveCD Ubuntu"
date: 2009-09-08
forum: General Help
---

### Post by beginner's love on 2009-09-08
Hi,
I tried with a friend to retrieve the windows Vista partition of my laptop (lost administrator and user account passwords) using live CD Ubuntu but this is what happened...
- I dont see the windows partition initially but after some obscure commands on the terminal written by my friend we detect a partition NTFS in dev/sda2
- we try to mount it but there a message like this:
a NTFS signature is missing. Failed to mount dev/sda2: Invalid argument. The device doesnt have a valid NTFS. May be you selected the wrong device ? or the whole disk instead of a partition...
What should I do from now on???
:P:):(:confused::guitar:

---

### Post by P4man on 2009-09-08
Im guessing those "obscure" commands weren't quite what they needed to be and possibly made things worse :s

You could try testdisk:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by beginner's love on 2009-09-14
> **P4man said:**
> Im guessing those "obscure" commands weren't quite what they needed to be and possibly made things worse :s

You could try testdisk:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Hi P4man,
I will try to use it but has not too much knowlege about it, could you help me step by step?
BL

---

### Post by P4man on 2009-09-14
Im hardly an expert myself. But these might help:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

