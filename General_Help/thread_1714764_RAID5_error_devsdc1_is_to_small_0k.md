---
title: "RAID5 error: /dev/sdc1 is to small: 0k"
date: 2011-03-25
forum: General Help
---

### Post by JaizEdelmann on 2011-03-25
Hey guys i've just triede setting up my new raid with 4 discs however it wont let me create the raid, any ideas?

Running my harddrives through a

> Promise SATA300 TX4 interface/controller

Thats my create command:
```
sudo mdadm --create --verbose /dev/md0 --level=5 \
   --raid-devices=4 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1

```

Error msg
> mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: /dev/sdc1 is too small: 0K
mdadm: create aborted


if i try and do
```
sudo fdisk /dev/sdc
```
and tjek partitions with 
```
p
```
i get
```
/dev/sdc1               1      243201  1953512001   fd  Linux raid autodetect
```

I've setup all my 4 drives with 1 primary parition and set the Hexcode to FD (Linux raid autodetect) and written the tabels to the disks.

Fdisk -l

>    Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90a3cf5b

> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x026198bd


>   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6320ada9


---

### Post by JaizEdelmann on 2011-03-25
Apprently the kernal did not register the changes in the tabels so i did a

> sudo partprobe and resulted in raid array successfully creating! :)

---

