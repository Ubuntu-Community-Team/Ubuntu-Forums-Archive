---
title: "konqueror, autorun, something..."
date: 2006-05-17
forum: General Help
---

### Post by rbprogrammer on 2006-05-17
ok so i have this external harddrive that i use for just storage.  i have the setup like this:
[INDENT][FONT="Courier New"]connected through usb
150 GB -> two partitions[INDENT]~100 GB ntfs readonly
~50 GB read/write FAT32 (vfat)[/INDENT][/FONT][/INDENT]

so the problem is when i turn on the hard disk, konqueror does this windows like autorun thing and i get three error messages that look like this:
[INDENT][FONT="Courier New"]An error occurred while loading media:/sdb1:
The file or folder media:/sdb1 does not exist.[/FONT][/INDENT]

the same happens for:
[INDENT][FONT="Courier New"]media:/sdb5
[INDENT]and[/INDENT]
media:/sdb2[/FONT][/INDENT]

so what i want to know is if i can stop konqueror from trying to open up those locations, i can still access both filesystems perfectly fine through the mount points in [FONT="Courier New"]/media/[/FONT], but i just want to shut off that feature...

---

### Post by GeneralZod on 2006-05-18
[http://ubuntuforums.org/showthread.php?t=90457&highlight=ivman+konqueror](http://ubuntuforums.org/showthread.php?t=90457&highlight=ivman+konqueror)

Also, make sure your version of KDE is 100% up-to-date, as these silly error messages were fixed for many people by a set of updates a few weeks after release.

---

