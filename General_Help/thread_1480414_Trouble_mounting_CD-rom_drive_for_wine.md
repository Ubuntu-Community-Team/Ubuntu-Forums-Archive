---
title: "Trouble mounting CD-rom drive for wine"
date: 2010-05-11
forum: General Help
---

### Post by JFS85 on 2010-05-11
I recently installed Lucid Lynx (clean install not an upgrade) and everything works fine,
except when I installed wine and tried to mount cd-rom drive for it. I looked for cdrom0 in /media/ but it wasn't there:

```
/media$ ls
My Book
```(My Book is my external hdd)
when I put a cd in the drive it works just fine, I can acces the cd and it appears on my desktop. 

```
/media$ ls
My Book  RT2_PLAT
```RT2_PLAT is the railroad tycoon 2 cd.

Here is my /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdg2 during installation
UUID=b9ebce1f-ef4a-4fef-8706-091e92592db1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdg3 during installation
UUID=1f54ed01-fe43-4ab4-816f-f1a5a4e87617 none            swap    sw              0       0

```

I had an earlier version of Ubuntu (8.10) on the same computer and it work just fine.
I have the 64 bit version of 10.04

---

