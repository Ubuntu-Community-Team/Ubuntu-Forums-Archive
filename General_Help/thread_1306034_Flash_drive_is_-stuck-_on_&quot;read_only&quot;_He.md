---
title: "Flash drive is -stuck- on &quot;read only&quot; Help!"
date: 2009-10-30
forum: General Help
---

### Post by oxf on 2009-10-30
Please could someone help me ASAP on this.

I'm trying to copy some PDF files to a usb flash drive. (Kingston 8GB). It wont let me as it's saying the flash is a "read only file system" I've tried changing the permissions for the flash using root but it wont let and shows the "locked" symbol. How do I resolve this?

Many thanks!

---

### Post by razy60 on 2009-10-30
Hi is there a slider on the side to unlock it?

When and where was it last used


Raz

---

### Post by oxf on 2009-10-30
> **razy60 said:**
> Hi is there a slider on the side to unlock it?

When and where was it last used


Raz

No there's no lock/unlock slider on it! I was using it yesterday and copied files from Ubuntu to it just fine. My partners used it in windows last night and say she's not done anything except save a couple of files to it! I'm stumped

---

### Post by John Bean on 2009-10-30
Perhaps it has some errors on it and is mounted r/o as a result. You could do a disk check and see what happens.

---

### Post by razy60 on 2009-10-30
It may not have been unmounted/ejected from windows properly?
Failing that have you looked at it in partition manager, try changing settings there.
One other thing if the files your partner saved need a password or there is some sort of encryption on it such as u3 it needs to be unlocked there first, and i am sure you can only do that in windows

Raz

---

### Post by linux-hack on 2009-10-30
you can change the mount option to rw (read, write) in the fstab or mount it manualy with :
```
sudo mount -t -o rw,user,auto,unhide FILESYSTEM dev/USBKEY /mnt/MYKEY
```

---

### Post by oxf on 2009-11-01
Well thanks guys...filed for future reference. Was in a hurry for a deadline so resorted to Windows, copy files, and formated the flash. No longer a problem. So who knows...?

---

