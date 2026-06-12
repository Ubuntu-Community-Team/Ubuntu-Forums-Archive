---
title: "Cannot change file permission"
date: 2009-08-27
forum: General Help
---

### Post by dE_logics on 2009-08-27
I have an NTFS partition...the folder in which it's mounted has a root's ownership but it has permission set for everyone to write on it.

Now...I cannot change the ownership of this folder in which the partition has been mounted...chown own wont work...it works normally (i.e produces no errors and all) but with no effect.

I tired 'open as administrator' from nautilus and tried to change it from the property menu of the folder...but it keeps switching back.

The partition is NTFS and Windows shares it.

---

### Post by cdenley on 2009-08-27
NTFS cannot store Linux permissions.

---

### Post by bodhi.zazen on 2009-08-27
Moved to general help as this is a better location.

You set the ownership and permissions on both FAT and NTFS partitions when you mount them or in /etc/fstab.

See man mount or 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by dE_logics on 2009-08-28
Oh...now I see.

Thanks everyone!

---

### Post by HiImTye on 2009-08-28
you can set the permissions at your mount point, rather than the drive itself

i.e. go to /media/ and right click 'YourDrive' (or whatever you have it called) and set the permissions that way :)

---

