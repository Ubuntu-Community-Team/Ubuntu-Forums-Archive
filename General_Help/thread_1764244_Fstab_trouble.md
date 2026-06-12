---
title: "Fstab trouble"
date: 2011-05-21
forum: General Help
---

### Post by And6ate9 on 2011-05-21
I am trying to make an fstab to load up my drive at start up but I am having some trouble. Can someone look over this for me?

```
# /etc/fstab: static file system information. 
# 
# Use 'blkid -o value -s UUID' to print the universally unique identifier 
# for a device; this may be used with UUID= as a more robust way to name 
# devices that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    nodev,noexec,nosuid 0       0 
# / was on /dev/sda7 during installation 
UUID=11e7c59f-bd20-428e-98f9-3bdc4bf19eb7 /               ext4    errors=remount-ro 0       1 
# /home was on /dev/sda8 during installation 
UUID=8272225d-e443-47e8-b9d4-796a0f247873 /home           ext4    defaults        0       2 
/dev/sda3       none            swap    sw              0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#
# Here my my fstab 
#
# /dev/sda2 
#/dev/sda2  /media/zGrubboot ext3   defaults,relatime  0      2 
#
# /dev/sda11 
/dev/sda11  /media/ntfsshare ntfs-3g unmask=000,uid=1000,gid=1000,auto,rw,users,locale=en_US.utf8 0 0
#
# /dev/sdc1 
/dev/sdc1  /media/mediashare ntfs-3g unmask=000,uid=1000,gid=1000,auto,rw,users,locale=en_US.utf8 0 0
#
#/dev/sdc2 
/dev/sdc2  /media/backup01 ntfs-3g unmask=000,uid=1000,gid=1000,auto,rw,users,locale=en_US.utf8 0 0
#
#/dev/sdb1 
/dev/sdb1  /media/backup02 ntfs-3g unmask=000,uid=1000,gid=1000,auto,rw,users,locale=en_US.utf8 0 0
#
# This enables usb in Virtualbox in Jaunty 9.04 and above 
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0 
```

---

### Post by Plueonic on 2011-05-21
> **And6ate9 said:**
> 
```

# /dev/sda11 
/dev/sda11  /media/ntfsshare ntfs-3g [COLOR=Red]unmask[/COLOR]=000,uid=1000,gid=1000,auto,rw,users,locale=en_US.utf8 0 0
```
You probably meant to use [COLOR=Red]umask[/COLOR].. so replace them and see if running  *sudo mount -a* gives any error messages.

---

### Post by And6ate9 on 2011-05-21
Oh, I feel so embarrassed. 
But, grub can seem to load the kernel. I guess I have to try addling line by line.

---

