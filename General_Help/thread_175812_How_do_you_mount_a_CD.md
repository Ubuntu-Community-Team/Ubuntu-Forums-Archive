---
title: "How do you mount a CD?"
date: 2006-05-13
forum: General Help
---

### Post by Dakaru on 2006-05-13
Ok So I put my disk in to listen but I dont know how to mount it, can anyone give me the command?

---

### Post by nanotube on 2006-05-13
well, it "should" mount automatically.
since it doesnt, try command
```
mount /media/cdrom0
```
if that doesnt work, take a look at your /etc/fstab file, and look for a line that has cdrom in it. once you find it, check which device it is, you can issue a command
```
mount /dev/hda
```
and that would mount your cdrom (if it is in /dev/hda, as it is for me).

---

### Post by Dakaru on 2006-05-13
[QUOTE=nanotube]well, it "should" mount automatically.
since it doesnt, try command
```
mount /media/cdrom0
```
if that doesnt work, take a look at your /etc/fstab file, and look for a line that has cdrom in it. once you find it, check which device it is, you can issue a command
```
mount /dev/hda
```
and that would mount your cdrom (if it is in /dev/hda, as it is for me).[/QUOTE]
how do you unmount it?

---

### Post by bluevoodoo1 on 2006-05-13
umount /dev/cdrom

where cdrom is the name of your drive

(might need to use sudo, I can't remember)

---

### Post by nanotube on 2006-05-13
[QUOTE=bluevoodoo1]umount /dev/cdrom

where cdrom is the name of your drive

(might need to use sudo, I can't remember)[/QUOTE]
yea, "umount" is right. 
but cdrom usually has option "user" in fstab, so a user can mount/umount it without using sudo.

---

### Post by bluevoodoo1 on 2006-05-13
[QUOTE=nanotube]yea, "umount" is right. 
but cdrom usually has option "user" in fstab, so a user can mount/umount it without using sudo.[/QUOTE]


ah yes of course.

---

