---
title: "Swap Mounts on Desktop"
date: 2006-06-30
forum: General Help
---

### Post by OffHand on 2006-06-30
Weird.... my swap partition auto mounts on my desktop although the mount point is set to none.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
#/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda9       /media/data     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda8       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Am I missing something?

---

### Post by taurus on 2006-06-30
That's how it works...:rolleyes:

---

### Post by OffHand on 2006-06-30
[QUOTE=taurus]That's how it works...:rolleyes:[/QUOTE]
I appreciate your reply but it doesn't help much.
And it it is not how it should work.

---

### Post by taurus on 2006-06-30
What do you mean that is not how it should work?  What should it be?  There is no mount point for swap partition...  #-o

---

### Post by OffHand on 2006-07-01
[QUOTE=taurus]What do you mean that is not how it should work?  What should it be?  There is no mount point for swap partition...  #-o[/QUOTE]
Sorry for the late reply but I had to crash. t was 4 am. 
If the mount point  is set to 'none' or if I comment it out with # it shouldn't automaticly mount, right?

---

### Post by detgar on 2006-07-01
[QUOTE=subsonic_shadow]...my swap partition auto mounts on my desktop...
[/QUOTE]
Do you mean that you see an icon on your desktop representing your swap partition? If so, that is most certainly weird.

My swap line in fstab looks the same:

> /dev/sda2       none            swap    sw              0       0

---

### Post by OffHand on 2006-07-01
[QUOTE=detgar]Do you mean that you see an icon on your desktop representing your swap partition? If so, that is most certainly weird.

My swap line in fstab looks the same:[/QUOTE]
That is correct. I got an icon on my desktop representing my swap partition. It's even in my gnome menu.

---

### Post by OffHand on 2006-07-02
bump

---

