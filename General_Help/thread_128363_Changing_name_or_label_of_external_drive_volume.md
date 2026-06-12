---
title: "Changing name or label of external drive volume?"
date: 2006-02-11
forum: General Help
---

### Post by annsachd on 2006-02-11
I've formatted an external USB drive with Gparted to use as a backup for files. When the drive is turned on it shows up on the desktop as "6.0 GB Volume." It works fine.

Is there a way to change this name so that when it shows up on the desktop it would read "File Backup"?

I noticed that in /media it shows up as "usbdisk".

Thanks for the help.

---

### Post by annsachd on 2006-02-11
Any ideas?

---

### Post by dcstar on 2006-02-11
[QUOTE=annsachd]I've formatted an external USB drive with Gparted to use as a backup for files. When the drive is turned on it shows up on the desktop as "6.0 GB Volume." It works fine.

Is there a way to change this name so that when it shows up on the desktop it would read "File Backup"?

I noticed that in /media it shows up as "usbdisk".

Thanks for the help.[/QUOTE]
e2label for ext2 filesystems, mlabel for ms-dos ones (mtools package).

[http://ubuntuforums.org/showthread.php?t=65830](http://ubuntuforums.org/showthread.php?t=65830)

---

### Post by annsachd on 2006-02-11
Thank you for the software hint and the link. Without the link I wouldn't have been able to get it all straight. My external now has a nice new name.

---

