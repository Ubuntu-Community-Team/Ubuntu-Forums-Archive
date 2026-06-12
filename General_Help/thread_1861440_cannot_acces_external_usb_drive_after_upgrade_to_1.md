---
title: "cannot acces external usb drive after upgrade to 11.10"
date: 2011-10-15
forum: General Help
---

### Post by johnnyslogan on 2011-10-15
Hello,

I can no longer acces my external usb-harddrive, after I upgraded to Ubuntu 11.10. I can acces it with one user, though, but not from my primary user-account. I get acces denied. Also Samba seems to not be able to acces the drive any longer. 

The drive is automounted using /etc/usbmount/usbmount.conf and the file system is NTFS. Again, the drive does mount, and I'm able to acces it from one user account, but not from anywhere else. 

cat /etc/mtab gives me:

```
/dev/sdc1 /media/FreeAgent\040Drive fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
```

Any help is much appreciated.

---

### Post by alswar on 2011-10-16
Hi, I have the same problem.
Logged in as a user, then swapped to a different user and I can't use my external harddrive.
I tried to mount it manually but it's saying is already mounted:

sudo mount /dev/sdf1
mount: /dev/sdf1 already mounted or /media/FreeAgent Drive busy
mount: according to mtab, /dev/sdf1 is already mounted on /media/FreeAgent Drive

Mine wasn't an upgrade, but installation from scratch.

---

### Post by kend650 on 2011-10-21
I am having the same problem.  When either my WD MyBook or Maxtor One Touch are connected via USB, the system won't boot.  If I plug either one in after boot, neither gets mounted or recognized.  They both worked fine with 11.04, and that's where my backups are, and now I can't get to them.

What is going on here??????

---

### Post by johnnyslogan on 2011-10-22
Just a quick update: Reinstalled 11.10 and have 'hard'-mounted usb-drive in fstab. So far no access-problems this way.

---

