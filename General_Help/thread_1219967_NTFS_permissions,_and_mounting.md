---
title: "NTFS permissions, and mounting"
date: 2009-07-22
forum: General Help
---

### Post by bnvdarklord on 2009-07-22
I have two "problems" with my internal NTFS hdd. 

1) When i turn on the pc, the disk is not mounted, and i have to click it in Places to be activated. How can i make it to mount automatically?

2) The disk is owned by root user. I can do whatever i want to the disk except: i don't have a trash(not sure it has to do with permissions), so all files are deleted permanantly, and i cannot change permissions, in properties, as it says i'm not the owner. How can i fix this?

Thanks in advance!:D

---

### Post by masux594 on 2009-07-22
Search before post =P .. read [this thread]("http://ubuntuforums.org/showthread.php?t=802699")..

Sysc, A

---

### Post by GoldenSun on 2009-07-22
> **masux594 said:**
> Search before post =P .. read [this thread]("http://ubuntuforums.org/showthread.php?t=802699")..

Sysc, A

good thread

Also I don't think you can set permissions on a ntfs hd.

---

### Post by Operan on 2009-07-22
> **GoldenSun said:**
> good thread

Also I don't think you can set permissions on a ntfs hd.

You're right! Use FAT32 instead to set permissions correctly.

---

### Post by merlinus on 2009-07-22
If permissions cannot be set correctly on ntfs, then how do you explain all the dual-booting with win2000, xp, vista, and 7, which all use it as their filesystem?

ntfs has a number of advantages over fat32 as well, such as being less prone to fragmenting and handling larger files.

---

### Post by bnvdarklord on 2009-07-22
Thanks for the automount post, i must have missed it...

Regarding permissions in ntfs: If i can't set them, why it says i need to be root to set them?

And i guess i cannot have a trash folder because its ntfs again? Is there any way to convert it to ext3 or 4 w/o formatting ? but i guess not :(

---

### Post by merlinus on 2009-07-22
You cannot permanently change permissions on non-linux partitions unless they are unmounted.  After doing so:

```
gksudo nautilus
```Navigate to the mountpoint and you can change whatever you like, and they will stick.

Usually the permissions are set in /etc/fstab.

And if you want a trashcan, then ext3 or ext4 is the way to go, but you will have to format it as such.

---

### Post by bnvdarklord on 2009-07-22
So i cannot have a trash on ntfs but i can on a fat32... strange... Anyways, it doesn't bother me very much. 
Thanks for your answers. :)

---

### Post by merlinus on 2009-07-22
Actually, I am not certain about trash on ntfs, because my flashdrive is formatted as fat32 and of course has one.

---

