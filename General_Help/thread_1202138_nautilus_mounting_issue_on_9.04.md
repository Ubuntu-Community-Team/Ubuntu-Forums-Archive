---
title: "nautilus mounting issue on 9.04"
date: 2009-07-01
forum: General Help
---

### Post by rampage on 2009-07-01
trying to add "auto" to the mounting option under the volume tab in my HDD properties withing "computer" and after unmounting the drive it will not let me mount it again "invalid mount option when attempting to mount...". I checked fstab and there was no record of that drive being in there at all. Is there a config file that this corresponds to nautilus mount options so I can get rid of that "auto" option I put in there? or is there a way I can get in and change that back to defaults

Thanks very much

---

### Post by colau on 2009-07-01
> **rampage said:**
> trying to add "auto" to the mounting option under the volume tab in my HDD properties withing "computer" and after unmounting the drive it will not let me mount it again "invalid mount option when attempting to mount...". I checked fstab and there was no record of that drive being in there at all. Is there a config file that this corresponds to nautilus mount options so I can get rid of that "auto" option I put in there? or is there a way I can get in and change that back to defaults

Thanks very much
Can you post
```

cat /etc/fstab

```

---

### Post by rampage on 2009-07-01
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=07801b8e-2f0b-4b9d-8892-2bd3160c4638 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=4a0f434d-f4ca-410c-8243-87d4f2b4af3b /home           ext4    relatime        0       2
# swap was on /dev/sda6 during installation
UUID=90a4a236-a191-4d8f-884b-fe9a66555901 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
princess@thequantummachine:~$ 

##########################################################################

does gnome have a seperate config file for mounting when you are using nautilus?

---

### Post by colau on 2009-07-01
Can you post
```

sudo fdisk -l

```

---

### Post by rampage on 2009-07-01
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9077    72910971    7  HPFS/NTFS
/dev/sda2            9078       14593    44307270    5  Extended
/dev/sda5            9078       10322    10000431   83  Linux
/dev/sda6           10323       10541     1759086   82  Linux swap / Solaris
/dev/sda7           10542       14593    32547658+  83  Linux

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a3a401e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19929   160079661    7  HPFS/NTFS

---

### Post by rampage on 2009-07-01
Oh i got it now actually...thanks for your help

I forced it to mount in the terminal and when the drive was mounted I was able to remove the bad options... works great now

---

### Post by redmk2 on 2009-07-01
> **rampage said:**
> ...does gnome have a seperate config file for mounting when you are using nautilus?

Yes.  It is under .gvfs in your home directory.

---

