---
title: "Can't write to disk?!"
date: 2009-08-15
forum: General Help
---

### Post by PwnCakes193 on 2009-08-15
Randomly my USB Hard drive can't be written to. It says this
"There was an error creating the directory in /media/disk.
Error creating directory: Read-only file system"

What do I do to fix this?

---

### Post by harry2006 on 2009-08-15
> **PwnCakes193 said:**
> Randomly my USB Hard drive can't be written to. It says this
"There was an error creating the directory in /media/disk.
Error creating directory: Read-only file system"

What do I do to fix this?
looks your stick got mounted as Readonly file sys...try unmounting and then mounting using sudo with write permission...it shud work...

---

### Post by PwnCakes193 on 2009-08-15
> **harry2006 said:**
> looks your stick got mounted as Readonly file sys...try unmounting and then mounting using sudo with write permission...it shud work...

How would I do that?

---

### Post by Crafty Kisses on 2009-08-15
> **PwnCakes193 said:**
> How would I do that?
Depending on what the drives mount point is, you can find this out by running as root:
```
fdisk -l
```
You should be able to run:
```
mount -o remount, -rw /dev/sdb1
```
Remember I'm just guessing the mount point is** /dev/sdb1**.

---

### Post by PwnCakes193 on 2009-08-15
> **Codename said:**
> Depending on what the drives mount point is, you can find this out by running as root:
```
fdisk -l
```
You should be able to run:
```
mount -o remount, -rw /dev/sdb1
```
Remember I'm just guessing the mount point is** /dev/sdb1**.

How do I run as root, is it sudo?

---

### Post by running_rabbit07 on 2009-08-15
> **PwnCakes193 said:**
> How do I run as root, is it sudo?

Yes

I hit the up folder button so that I can right-click on the drive and click properties, the click the permissions tab and give myself permission, but that doesn't work in every situation.

---

### Post by PwnCakes193 on 2009-08-15
I run it as sudo and all I get is another line saying:
tom@tom-laptop:~$ sudo mount -o remount, -rw /dev/sda5
tom@tom-laptop:~$

---

### Post by running_rabbit07 on 2009-08-15
After doing that try opening the drive.

---

### Post by PwnCakes193 on 2009-08-15
Nope, now there is a lock symbol on each of my folders.

---

### Post by Crafty Kisses on 2009-08-16
Post your **fstab**, you can run in the terminal as root:
```
cat /etc/fstab
```

---

### Post by olbaldy77 on 2009-08-27
I am having the same problem and this is what happens when I run **sudo cat /etc/fstab**

> olbaldy@olbaldy-desktop:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c9f31395-a8a5-46a6-b3a9-3bc054b30820 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2a70dabe-3757-4345-8299-9a95af239fd8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

The disk I'm having the problem with is /dev/sdb1

---

### Post by Crafty Kisses on 2009-09-20
> **olbaldy77 said:**
> I am having the same problem and this is what happens when I run **sudo cat /etc/fstab**



The disk I'm having the problem with is /dev/sdb1

Have you tried running the command I previously stated? 
```
mount -o remount,rw /dev/sdb1
```
Then try to mount the drive and try to write to it.

---

### Post by hydn79 on 2012-11-09
> **PwnCakes193 said:**
> How do I run as root, is it sudo?

This works. thx

---

