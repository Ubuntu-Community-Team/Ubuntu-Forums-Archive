---
title: "Don't know what to do after installing new hard drive"
date: 2009-07-13
forum: General Help
---

### Post by jon64 on 2009-07-13
I just bought a new hard drive for my ubuntu server because my old 750gb hard drive is starting to get full. But after installing the new hard drive into my server i realized i didn't know what to do after that :( I've tried searching around the forums for a tutorial for partitioning and giving permissions to the drive but i haven't found anything helpful. If someone could help me pretty soon id greatly appreciate it :p

---

### Post by zipperback on 2009-07-13
> **jon64 said:**
> I just bought a new hard drive for my ubuntu server because my old 750gb hard drive is starting to get full. But after installing the new hard drive into my server i realized i didn't know what to do after that :( I've tried searching around the forums for a tutorial for partitioning and giving permissions to the drive but i haven't found anything helpful. If someone could help me pretty soon id greatly appreciate it :p


A quick search of google found thousands of pages.
[http://www.google.com/#hl=en&q=how+do+I+add+additional+hard+drives+under+linux&aq=f&oq=&aqi=&fp=KxYPMM6r3XA](http://www.google.com/#hl=en&q=how+do+I+add+additional+hard+drives+under+linux&aq=f&oq=&aqi=&fp=KxYPMM6r3XA)


You didn't provide any specifics about your current system or how it is configured, but you might find LVM (Logical Volume Manager) to be pretty helpful for your system.

[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

Could you please tell us the specifics of your current configuration?

- zipperback
:popcorn:

---

### Post by sanemanmad on 2009-07-13
is the drive already mounted?
you can use ```
parted
```to format. First you should identify the drive in the terminal.

```
fdisk -l
```
then ```
ls -l /dev/disk/by-uuid
``` obtain the uuid for the drive and edit ```
/etc/fstab
``` with this information.

---

### Post by jon64 on 2009-07-13
**This is what i get when i sudo fdisk -l in terminal. I also have a second 1TB drive in my server. But i want to keep it unallocated for now.**

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xccda9c4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       89700   720515218+  83  Linux
/dev/sda2           89701       91201    12056782+   5  Extended
/dev/sda5           89701       91201    12056751   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009a56b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

**and this is what i have in my fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=daaa3e8c-b69c-4081-a4fe-70b004b0570b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f0f35ac6-b4f4-427a-b68e-4c5ac74108a6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /media/newstorage ext3 defaults 0 0

---

### Post by sanemanmad on 2009-07-14
So all you to do now is ```
ls -l /dev/disk/by-uuid|grep sdc
``` and that is the uuid used in fstab (Hint copy the other line already in there and swap uuid and mnt location) > (change / to /mnt/something). However before you can do that, create a partition using parted. ```
apt-get parted
```. man pages are really useful for this tool. Good Luck!

---

