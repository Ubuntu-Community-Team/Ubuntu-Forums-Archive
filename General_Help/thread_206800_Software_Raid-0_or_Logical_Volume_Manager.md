---
title: "Software Raid-0 or Logical Volume Manager???"
date: 2006-06-30
forum: General Help
---

### Post by darkhatter on 2006-06-30
I have a old computer with a lot of small hard drives, and I want to know which one is going to give me the best speed.

the computer I have can run kde at a useable speed.

---

### Post by thingy on 2006-06-30
> Logical volume management provides a higher-level view of the disk storage on a computer system than the traditional view of disks and partitions. This gives the system administrator much more flexibility in allocating storage to applications and users.

Storage volumes created under the control of the logical volume manager can be resized and moved around almost at will, although this may need some upgrading of file system tools.

The logical volume manager also allows management of storage volumes in user-defined groups, allowing the system administrator to deal with sensibly named volume groups such as "development" and "sales" rather than physical disk names such as "sda" and "sdb".

LVM = No performance benefits. You have admin benefits however.

Raid 0 = Striping will not give you any performance increases unless you are doing *VERY* large amounts of I/O.

That was prob. not what you wanted to hear, but if you are simply using that machine as a desktop or a low usage file server, then just use LVM to catenate the disks and provide storage space to your other machines.

jin

---

### Post by darkhatter on 2006-06-30
its ok, I'm going to be using it as a storage/desktop so I guess I'll just stick with raid-0
thanks :smile:

---

