---
title: "Data Loss when enabling Trim on SSD?"
date: 2010-11-14
forum: General Help
---

### Post by shimoda on 2010-11-14
Hi!

I'm a little worried because I can't enable Trim in my SSD Drive. It's a Kingston SSDNow V 64Gb.
It's cheap and fast, I'm happy with it, but enabling Trim only gives me problems...! :(

I'm in Ubuntu 10.04 with Kernel 2.6.32... With wiper.sh all seems to go well, but in short time appear something... For example, the last time I tried it, the system booted more slowly and appeared strange errors in Xorg.log...

I tried newer kernels with the discard option, but there are also errors...:Always is the same... After enabling Trim, if I try to backup the drive (with clonezilla), errors appear doing the backup... 

Hdparm tells me that the drive is Trim capable...

Anyone with this drive or with ideas? :confused:
I'm sad because I don't know what can I try to do now...!

---

### Post by zaphod777 on 2010-11-16
> **shimoda said:**
> Hi!

I'm a little worried because I can't enable Trim in my SSD Drive. It's a Kingston SSDNow V 64Gb.
It's cheap and fast, I'm happy with it, but enabling Trim only gives me problems...! :(

I'm in Ubuntu 10.04 with Kernel 2.6.32... With wiper.sh all seems to go well, but in short time appear something... For example, the last time I tried it, the system booted more slowly and appeared strange errors in Xorg.log...

I tried newer kernels with the discard option, but there are also errors...:Always is the same... After enabling Trim, if I try to backup the drive (with clonezilla), errors appear doing the backup... 

Hdparm tells me that the drive is Trim capable...

Anyone with this drive or with ideas? :confused:
I'm sad because I don't know what can I try to do now...!
can you post the results of 

cat "/etc/fstab" when you have trim enabled?

---

### Post by shimoda on 2010-11-17
Now I'm testing wiper.sh in Kernel 2.6.32 and I don't have kernel-trim...

My fstab is:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=bfa9fd3d-ed49-4c1c-8bf0-e90e6c60abe0 /               ext4    noatime,errors=remount-ro 0       1

/dev/disk/by-uuid/54614a54-701e-43e7-b5c1-c5d7c2ab300f /media/Taller                       ext4    rw,users,noexec        0 0
/dev/disk/by-uuid/19a5b063-f6cf-4320-93c5-3d6b2b52e3bc /media/Dades                       ext4    rw,owner        0 0
/dev/disk/by-uuid/c784e461-59cc-4949-8bb3-c46bf6787e22 /media/Gigs                       ext4    rw,users        0 0
/dev/disk/by-uuid/9ab97371-3eb4-4473-b4e5-0afb9050dff4 /media/Calaix                       ext4    rw,owner       0 0

# swap was on /dev/sdb2 during installation
UUID=918e1cfd-0b44-4afa-8c29-9707c4d8b137 none            swap    sw              0       0
```

In my test with newer Kernels (33 & 35) I added the discard option:
> UUID=bfa9fd3d-ed49-4c1c-8bf0-e90e6c60abe0 /               ext4    noatime,discard,errors=remount-ro 0       1

I don't know what could be wrong!!

---

