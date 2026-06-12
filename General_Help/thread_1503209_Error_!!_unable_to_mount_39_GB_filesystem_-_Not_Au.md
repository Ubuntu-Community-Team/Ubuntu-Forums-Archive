---
title: "Error !! unable to mount 39 GB filesystem - Not Authorized !!"
date: 2010-06-06
forum: General Help
---

### Post by finalfantasy1st on 2010-06-06
[IMG]http://img180.imageshack.us/img180/879/computerfilebrowser001.png[/IMG]


i can't access to my volumes in Ubuntu 10.4

how can i fix this problem plzzz?

---

### Post by finalfantasy1st on 2010-06-06
the output of 
"sudo fdisk -l" from terminal is :

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x62665524

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3219    25856586    7  HPFS/NTFS
/dev/sda2            3220       19458   130433400    f  W95 Ext'd (LBA)
/dev/sda5            3220        7968    38146311    7  HPFS/NTFS
/dev/sda6            7969       12717    38146311    7  HPFS/NTFS
/dev/sda7           12718       17466    38146311    7  HPFS/NTFS
/dev/sda8           17467       19209    13993984   83  Linux
/dev/sda9           19209       19458     1998848   82  Linux swap / Solaris

```

---

### Post by finalfantasy1st on 2010-06-06
Solved:P

---

### Post by Leppie on 2010-06-06
would be nice for others who face the same issue if you posted your solution ;)

---

### Post by finalfantasy1st on 2010-06-07
> **Leppie said:**
> would be nice for others who face the same issue if you posted your solution ;)

ok

To solve this problem do the following :

1 - you must create folders in this path
```
 /media
```to make them "mount points"
note 1 : click "alt + F2" and write "gksudo nautilus" to be able to add the folders in this path
note 2 : make sure to rename this folders to c_drive, d_drive, ... etc.

2 - install "MountManager" from ubuntu software center

3 - go to system >> administration >> MountManager

4 - from "MountManager" choose the volumes you want to mount then add mount point - the folders that you created previously - and apply this settings from : partition >> apply

5 - done :)

---

### Post by dcstar on 2010-06-07
> **finalfantasy1st said:**
> Solved:P

Really?, the thread is not marked as such.

---

### Post by dcstar on 2010-06-07
> **finalfantasy1st said:**
> ok

To solve this problem do the following :

1 - you must create folders in this path
```
 **/media**
```to make them "mount points"
........

No, you must** not** create anything in that folder, **/media** is a **system folder** for removable media.

Create a folder that is not related to any system folders for any permanent mounts.

---

### Post by finalfantasy1st on 2010-06-07
> **dcstar said:**
> Really?, the thread is not marked as such.

yes:)

i will mark it now

---

### Post by finalfantasy1st on 2010-06-07
> **dcstar said:**
> No, you must** not** create anything in that folder, **/media** is a **system folder** for removable media.

Create a folder that is not related to any system folders for any permanent mounts.

why you must** not** create anything in that folder?? :confused: even if **/media** is a **system folder** for removable media.

it's works for me :)

---

### Post by Leppie on 2010-06-07
> **finalfantasy1st said:**
> why you must** not** create anything in that folder?? :confused: even if **/media** is a **system folder** for removable media.
/media is the folder where the system puts automagically mounted devices/partitions. if there's already mountpoints in this folder, automount may encounter conflicts.

---

### Post by finalfantasy1st on 2010-06-07
> **Leppie said:**
> /media is the folder where the system puts automagically mounted devices/partitions. if there's already mountpoints in this folder, automount may encounter conflicts.

Hmmmmmmm

if i faced a problem on this issue i will delete this folders:)

---

