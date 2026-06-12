---
title: "Automatic mounting issue"
date: 2010-05-16
forum: General Help
---

### Post by aparigraha on 2010-05-16
I got some problems with Kubuntu wanting to mount drives that are already mounted at boot through **fstab**.

I always mount the drives through UUID or Label. And the mounting always works, UUID or Label doesn't matter. The problem appears after login, where i get six popup windows asking for my password to mount the six already mounted drives.

Six new directories (sda1, sda2, sdb1......) have already been created automatically in the /media directory.


How do I get rid of this annoying thing?

Here's my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc  nodev,noexec,nosuid  0  0  
/dev/sdc1                                  /              ext4  errors=remount-ro    0  1  
# /home was on /dev/sdc3 during installation
UUID=1d95253f-3593-40ef-9523-11e9efb38fa1  /home          ext4  defaults             0  2  
# swap was on /dev/sdc4 during installation
UUID=6bcd17dd-c8e4-49f7-9b86-d07202b4e867  none           swap  sw                   0  0  
#LABEL=Ext                               /media/Ext  ext3  user,auto            0  0  
#LABEL=BACK                               /media/Back  vfat  user,auto            0  0  
#LABEL=sto                                 /media/sto    ext3  user,auto            0  0  
#LABEL=tor                               /media/tor  ext3  users            0  0  
#LABEL=320                                  /media/320     ext3  users            0  0  
#LABEL=stuff                                /media/stuff   ext3  users            0  0  
```

Thx

---

### Post by aparigraha on 2010-05-17
**EDIT**

This solved it, even though I'm not dealing with "removable media".

System settings -> Advanced -> Removable  Devices

Uncheck "Mount all removable media at login".

---

