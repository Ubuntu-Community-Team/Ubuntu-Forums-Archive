---
title: "File access from another partition"
date: 2006-02-06
forum: General Help
---

### Post by sjoseph on 2006-02-06
Hello,

I am new to Ubuntu, love it so far, but need help accessing music and photos that I have on another FAT32 partition of the same drive that has the OS installed. Why can't I acceess these through GNOME applications? I can cut and paste from the other partition but this is not what i'm interested in doing. the other partitions don't show up in the app file dir.

thanks in advance.

---

### Post by frodon on 2006-02-06
Maybe your fstab line is wrong, could you post your fstab file here ?
To open it use this command : ```
sudo gedit /etc/fstab
```

---

### Post by linuxden on 2006-02-06
[QUOTE=sjoseph]Hello,

I am new to Ubuntu, love it so far, but need help accessing music and photos that I have on another FAT32 partition of the same drive that has the OS installed. Why can't I acceess these through GNOME applications? I can cut and paste from the other partition but this is not what i'm interested in doing. the other partitions don't show up in the app file dir.

thanks in advance.[/QUOTE]

If you have already mounted your fat partition which by your post looks like it, then the path to access your fat partition is

```
 /media/windows*/ 
```

*windows being whatever dir you created in the mount process...

You can create a shortcut to it in nautilus by opening the windows* directory and adding a bookmark....

---

### Post by cotcot on 2006-02-06
Your fstab should have a line like this : 

/dev/hda1    /media/windows vfat  iocharset=utf8,umask=000  0    0

Suppposing you have created the directory /media/windows and hda1 is the name of the fat partition.

---

### Post by sjoseph on 2006-02-06
my fatsab code is: thanks in advance

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hdb1       /media/hdb1     vfat    defaults        0       0
/dev/hdb5       /media/hdb5     vfat    defaults        0       0
/dev/hdb8       /media/hdb8     vfat    defaults        0       0
/dev/hdb7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by aysiu on 2006-02-06
There's the problem: ```
/dev/hda1 /media/hda1 vfat defaults 0 0
/dev/hdb1 /media/hdb1 vfat defaults 0 0
/dev/hdb5 /media/hdb5 vfat defaults 0 0
/dev/hdb8 /media/hdb8 vfat defaults 0 0
``` Change those to say ```
/dev/hda1 /media/hda1 vfat iocharset=utf8,umask=000 0 0
``` and same for /dev/hdb1, /dev/hb5, etc.

Then reboot your computer.

---

### Post by sjoseph on 2006-02-06
thanks for all your help, I've changed the fatsab code and it's working great. nice to have you all out there.

steve

---

### Post by linuxden on 2006-02-07
[QUOTE=sjoseph]thanks for all your help, I've changed the fatsab code and it's working great. nice to have you all out there.

steve[/QUOTE]


fstab man!! fstab!!! lmao just kidding it stands for "file system table"....

Anyways glad it worked out for ya... The community is great here!!! oh and welcome not sure if i said that in my previous post in  this thread...

So welcome aboard!

---

