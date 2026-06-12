---
title: "Mounting Options ..."
date: 2006-03-24
forum: General Help
---

### Post by wannabelinuxconvert on 2006-03-24
I'm using fstab to mount a FUSE filesystem to two seperate mount points in /media/

When the first one mounts, an drive icon appears on the desktop and I can use it like any other partition I have, double click it and Nautilus opens up etc.

But when I mount the second one, no icon appears on the desktop, I can how ever access it through the icon in the 'computer' folder, and if I go directly into the folder in /media/.

To add to this strange'ness ... if I umount the first drive, I expect the drive icon on the desktop to dissappear, but it doesn't, it just changes it's name to the second mounted filesystem, as though one icon had been underneath the other, except this isn't the case as I remounted both and moved the icon around and there's nothing underneath.

Does anyone know why this is happening, or how to make an icon appear per filesystem I mount !?

I have two physical partitions I mount and each one of those has there own icon so I'm really stuck with this at the minute ](*,) 

Cheers

Mic

---

### Post by wannabelinuxconvert on 2006-03-24
No ideas anyone ... I cannot seem to solve this problem !?

Mic

---

### Post by aysiu on 2006-03-24
I guess most people, like me, are confused as to what a "FUSE filesystem" is.

I know NTFS, FAT32, HFS, HFS+, Ext3, Reiserfs, but I've never heard of FUSE.

---

### Post by wannabelinuxconvert on 2006-03-24
FUSE stands for Filesystem in Userspace and details can be found at 

[http://fuse.sourceforge.net/]("http://fuse.sourceforge.net/")

And is used for such things like GmailFS, which I know several people here in forum have either heard of or have had experience's with.

Mic

---

