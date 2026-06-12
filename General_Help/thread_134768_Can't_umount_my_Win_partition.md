---
title: "Can't umount my Win partition"
date: 2006-02-22
forum: General Help
---

### Post by Fred Doolie on 2006-02-22
Here is my fstab

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
/dev/hda1	/media/Windows	ntfs     nls=utf8,ro,user,umask=0222	0  0

When the system comes up (Gnome) the two parttions on my external drive and my win partition show up as drive icons on the desktop. Inserting a CD will also show an icon. I can right-click and choose umount for anything. All will cleanly unmount except the Win partition. I'm refused permission to unmount the Windows drive. 

If I plug in my little external USB HDD it also shows. When I choose unmount the icon goes away but I get an error that it couldn't eject the media. 

How can this be fixed?

---

### Post by carlosqueso on 2006-02-22
It's more than likely a permissions thing.  Open a terminal and type ```
sudo umount hda1
``` to unmount it.

---

### Post by aysiu on 2006-02-22
[QUOTE=Fred Doolie]
When the system comes up (Gnome) the two parttions on my external drive and my win partition show up as drive icons on the desktop. Inserting a CD will also show an icon. I can right-click and choose umount for anything. All will cleanly unmount except the Win partition. I'm refused permission to unmount the Windows drive. [/quote] If you don't want it to mount, change this line in your /etc/fstab ```
/dev/hda1 /media/Windows ntfs nls=utf8,ro,user,umask=0222 0 0
``` to this one ```
#/dev/hda1 /media/Windows ntfs nls=utf8,ro,user,umask=0222 0 0
```

> 
If I plug in my little external USB HDD it also shows. When I choose unmount the icon goes away but I get an error that it couldn't eject the media. 

How can this be fixed? That's a bug that's supposedly fixed as of Dapper Flight 3, but it'll remain a bug in Breezy (incidentally, it wasn't a bug in Hoary).

---

### Post by Fred Doolie on 2006-02-22
[QUOTE=carlosqueso]It's more than likely a permissions thing.  Open a terminal and type ```
sudo umount hda1
``` to unmount it.[/QUOTE]

Thanks. I put that in a launcher and it works fine.  I wonder why I can't use the regular unmount option that works on the other drives.

---

### Post by carlosqueso on 2006-02-22
NTFS drives just don't seem to get along terribly well with linux machines.   I had similar problems to you and just got REALLY used to the terminal.

---

### Post by Zalbor on 2006-02-22
[QUOTE=Fred Doolie]Thanks. I put that in a launcher and it works fine.  I wonder why I can't use the regular unmount option that works on the other drives.[/QUOTE]
I don't know exactly how it works, but CDs etc get mounted with user permissions while other partitions (like the NTFS one) are mounted with root permissions and therefore need sudo to unmount. That's why it doesn't simply work.
By the way, if you want to use a launcher for it, use gksudo instead of sudo. With regular sudo it can't ask for your password unless it's in a terminal, so it won't always work.

---

