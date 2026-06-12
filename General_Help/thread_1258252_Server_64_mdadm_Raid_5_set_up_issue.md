---
title: "Server 64 mdadm Raid 5 set up issue"
date: 2009-09-04
forum: General Help
---

### Post by RPMouton on 2009-09-04
Hey Folks,

OK, I have searched and experimented but haven't been able to make mdadm work to set up a raid 5 array.

I have the OS installed on dev/sda and installed 3 more drives sdb, sdc and  sdd

I have tried issuing the mdadm command with the drives partitioned and formatted, not partitioned and partitioned and not formatted.  In all cases I get the following :

```
roger@Phubuntu:/dev$ sudo mdadm --create /dev/md0 --level=raid5 --force /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: no raid-disks specified.
```What am I doing wrong?

Thanks in advance,

---

### Post by tgrimley on 2009-09-05
> **RPMouton said:**
> Hey Folks,

OK, I have searched and experimented but haven't been able to make mdadm work to set up a raid 5 array.

I have the OS installed on dev/sda and installed 3 more drives sdb, sdc and  sdd

I have tried issuing the mdadm command with the drives partitioned and formatted, not partitioned and partitioned and not formatted.  In all cases I get the following :

```
roger@Phubuntu:/dev$ sudo mdadm --create /dev/md0 --level=raid5 --force /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: no raid-disks specified.
```What am I doing wrong?

Thanks in advance,



You dont have the command formatted correctly.  Also, you'll DEFINITELY want to partition the drive so you know it is easier to determine it has a RAID partition on it.

then, you should be doing

```
roger@Phubuntu:/dev$ sudo mdadm --create /dev/md0 --level=raid5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1
```

---

### Post by RPMouton on 2009-09-06
> **tgrimley said:**
> You dont have the command formatted correctly.  Also, you'll DEFINITELY want to partition the drive so you know it is easier to determine it has a RAID partition on it.

then, you should be doing

```
roger@Phubuntu:/dev$ sudo mdadm --create /dev/md0 --level=raid5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1
```


Thanks much,

I will try this out when I get back in town and report back.

regards,

---

