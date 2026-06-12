---
title: "how to change ownership and permissions for USB flash drive ?"
date: 2012-06-03
forum: General Help
---

### Post by raymondvillain on 2012-06-03
Running 64 bit Ubuntu 12.04

Formatted a 2 gig USB flash drive to NTFS so kid could use it at home on Ubuntu and at school on windows.

Now he can't access it.

I can access it, but I can't change any permissions.

I've tried "gksudo nautilus" from a terminal but right clicking on the drive and going through the procedure to change permissions doesn't work.

Also tried "sudo chown username:username /media/"name of flash drive" to no avail.

Can I put a line in my /etc/fstab file to fix this?  If so, what should it say?

What to do?

---

### Post by sam_delta on 2012-06-03
you should go for FAT format for a usb drive if you want compatiblity, it will even work in mac.
if you need ntfs for some reason, try using the -R option , something like this:
```
sudo chown user:user /media/name_of_drive -R
sudo chmod 777 user:user /media/name_of_drive -R
```
sam

---

### Post by idoitprone on 2012-06-03
> **sam_delta said:**
> you should go for FAT format for a usb drive if you want compatiblity, it will even work in mac.
if you need ntfs for some reason, try using the -R option , something like this:
```
sudo chown user:user /media/name_of_drive -R
sudo chmod 777 user:user /media/name_of_drive -R
```sam

i dont think it would work because both fat32 and ntfs creates permission upon mount. If you want to change permissions, just remount it with the correct permissions

---

### Post by raymondvillain on 2012-06-04
Many thanks, sam_delta and idoitprone.

How do I "remount" it with correct permissions?  This sounds promising.

---

### Post by sdowney717 on 2012-06-04
have you tried gparted?
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by raymondvillain on 2012-06-04
sdowney717 suggested using gparted.  I had a go at it, but can't see how gparted can change permissions.  I did use gparted to unmount the device, but what to do then?

---

### Post by idoitprone on 2012-06-04
> **raymondvillain said:**
> sdowney717 suggested using gparted.  I had a go at it, but can't see how gparted can change permissions.  I did use gparted to unmount the device, but what to do then?

use root to umount it

then remout it with your user

---

