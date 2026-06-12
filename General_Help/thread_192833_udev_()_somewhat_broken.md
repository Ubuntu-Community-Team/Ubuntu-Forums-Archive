---
title: "udev (?) somewhat broken?"
date: 2006-06-09
forum: General Help
---

### Post by deb2006 on 2006-06-09
Under "Places / Computer" I have the following entries:
- all my partitions
- a single "Filesystem" entry
- one CD icon altho I have two 

Something's (udev?) gotta be terribly broken there ...
But wait! I guess it cannot be udev because I can access the 2nd CD-ROM device.

---

### Post by mlind on 2006-06-09
create new mount point on your /media folder for your 2nd cd
and add it on /etc/fstab. The first device should on /etc/fstab already.

---

### Post by deb2006 on 2006-06-09
Nope, that doesn't work. It seems as if Nautilus' view is independent of /etc/fstab. There always remains _one_ CD/RW-icon no matter what I do (delete all CD-RW entries or add another CD-RW entry). 
This really sucks. Why do I have icons for all my partitions? This is crap since Nautilus' view should be comparable to that of bash. In bash there is a root directory - the same should be applied to Nautilus. Why Nautilus shows only one CD-RW icon instead of two - hell, I don't know. And it's not that the 2nd CD-RW didn't work. It works perfectly.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               xfs     defaults        0       1
/dev/sda1       /boot           ext2    defaults        0       2
/dev/sdb1       /home           xfs     defaults        0       2
/dev/sda2       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by mlind on 2006-06-09
Did you create a /media/cdrom1 directory ?
then try command **sudo /etc/init.d/dbus restart**

/edit
I'm not sure if it was dbus afterall, I restarted udev also 
and then did *killall nautilus gnome-panel* after that devices on nautilus
view were refreshed.

---

### Post by mlind on 2006-06-09
I don't know how udev is supposed to work, but when it's first time started by
kernel boot process, /sys/ folder is populated by different devices.

After this do 
```

sudo umount -a  

```

followed by 
```

sudo mount -a

```

/sys/ is now empty. Is this normal or should the same devices appear back?

---

### Post by ozgur on 2006-06-15
Check this thread:

[http://ubuntuforums.org/showthread.php?t=197468](http://ubuntuforums.org/showthread.php?t=197468)

---

