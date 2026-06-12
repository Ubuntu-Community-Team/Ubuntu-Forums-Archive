---
title: "Ubuntu and windows 7 in the same partition?!"
date: 2011-11-01
forum: General Help
---

### Post by wilix on 2011-11-01
Hi every one,
I really need your help to overcome the following problem:
In fact I have decided to install ubuntu 11.10 64 bit few days ago, but since I was a beginner, I had to do a lot to finally install it...I have followed all the necessary steps, but at the end I was astonished when I have realized that Ubuntu and W7 shared the same partition ( home) , in fact I have created new partitions : to be more clear : one i called it HOME another / and a SWAP partition...So where was my mistake? I would appreciate any suggestion a remark from you!
ps: Now ubuntu works perfectly but windows 7 can't be loaded ( doesn't boot if i may say since It request froom me at the beginning to repare but i tried and it didn't work, same message again and again)

---

### Post by tartalo on 2011-11-01
If you go to a terminal and write the following, what's the output?
```
sudo fdisk -l
```
and
```
df -h
```

---

### Post by Mark Phelps on 2011-11-01
The only way that Ubuntu and Windows 7 can share the same partition is if you installed using Wubi -- since it creates a file known as root.disk, and that can exist inside a Winows 7 OS partition.

Normal Ubuntu installs, to their own separate partitions, can not be done to NTFS (what Windows 7 uses) partitions.

---

### Post by techvish81 on 2011-11-01
TOM And JERRY:lolflag:

---

