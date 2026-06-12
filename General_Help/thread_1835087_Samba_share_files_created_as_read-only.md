---
title: "Samba share files created as read-only"
date: 2011-08-28
forum: General Help
---

### Post by arbulus on 2011-08-28
On my Ubuntu Natty box, I am using fstab to mount a samba share from my wife's Mac running OS X Snow Leopard. I have it shared from there with full read and write permission for my user. On my Ubuntu box, I can read files, create files and even delete files on that share, but when I create a file, it becomes read-only, so I cannot edit a file I just created on the share. 

Here is my /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ced5b74f-b49b-44ac-ba45-db35e4c3ffda /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda6 during installation
UUID=2f9be5ac-24bd-492d-bb23-83bf255e14e2 none            swap    sw              0       0
//10.0.1.200/storage	/home/dave/storage	cifs	credentials=/home/dave/.smbcredentials,dir_mode=0777,file_mode=0777	0	0
//10.0.1.200/storagebackup	/home/dave/storagebackup	cifs	credentials=/home/dave/.smbcredentials,dir_mode=0777,file_mode=0777	0	0
```

Does anyone have any idea why this might be doing this?

---

### Post by arbulus on 2011-08-28
I figured it out. I added uid=1000 to the fstab line and it solved my problem.

---

