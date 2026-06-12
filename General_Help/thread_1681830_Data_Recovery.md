---
title: "Data Recovery"
date: 2011-02-04
forum: General Help
---

### Post by layers on 2011-02-04
Well, to make the long story short, I deleted some folders, and I really need them back. these folders were stored in the same drive where my Ubuntu is installed. Is is possible to use any kind of recovery software, on the filesystem without losing it?

---

### Post by DiSTORT3D on 2011-02-04
Try Testdisk, i used it to restore a disk and recovered 90% of what was lost after the disc gave up on me

---

### Post by layers on 2011-02-04
> **DiSTORT3D said:**
> Try Testdisk, i used it to restore a disk and recovered 90% of what was lost after the disc gave up on me
See, but you used it on a disk that you don't care about, right? (I mean that the program takes it as an empty one, and may cause damage by inspecting it. Right?)

---

### Post by DiSTORT3D on 2011-02-04
Well i did really care about or else i would have thrown it away, anyway you can alway mirror your disk before you do data recovery.

---

### Post by layers on 2011-02-04
> **DiSTORT3D said:**
> Well i did really care about or else i would have thrown it away, anyway you can alway mirror your disk before you do data recovery.
No, no. What I meant is, that I am afraid to lose whatever is now on the disk (the not-lost data).

---

### Post by layers on 2011-02-04
I thought Testdisk is for lost partitions, not for lost files.

---

### Post by layers on 2011-02-05
Ok, so I have testdisk-6.11, but how exactly do I make it find the files, that are in the second partition of my HD?

---

### Post by dino99 on 2011-02-05
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://www.addictivetips.com/ubuntu-linux-tips/how-to-recover-deleted-filesdata-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-recover-deleted-filesdata-in-ubuntu-linux/)

---

### Post by layers on 2011-02-05
> **dino99 said:**
> [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://www.addictivetips.com/ubuntu-linux-tips/how-to-recover-deleted-filesdata-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-recover-deleted-filesdata-in-ubuntu-linux/)
=>```
ibo@ibo-laptop:~$ scalpel /dev/sda2 -o ~/rec
Scalpel version 1.60
Written by Golden G. Richard III, based on Foremost 0.69.
ERROR: You have attempted to use a non-empty output directory. In order
       to maintain forensic soundness, this is not allowed.
Aborting.
```rec is a newly created folder, with nothing in it.

nv, there was audit.txt, which i have no idea where it came from

---

