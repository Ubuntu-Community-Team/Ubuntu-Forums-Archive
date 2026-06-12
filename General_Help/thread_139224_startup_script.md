---
title: "startup script"
date: 2006-03-03
forum: General Help
---

### Post by specialboy on 2006-03-03
I am currantly having to mount some of my drives manually and I would like to make a sript to do this and have it run at startup.  I don't how to make a script though let alone run it at start up.

To mount my drives I have to type

sudo mount -t vfat /dev/hde1 /media/fat1
sudo mount -t vfat /dev/hdf1 /media/fat2

---

### Post by halfvolle melk on 2006-03-03
You can edit /etc/fstab. Open a terminal and type:
```
sudo gedit /etc/fstab
```
Mine looks like this:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd1       /mnt/d          ext2    user            0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by keeb on 2006-03-03
you're going to want to update your /etc/fstab file..

with

```
  /dev/hde1  /media/fat1 vfat  umask=000 0 0
  /dev/hdf1 /media/fat2 vfat umask=000 0 0
```

if you just want read only access and..

```

  /dev/hde1  /media/fat1 vfat  uid=<your userid> 0 0
  /dev/hdf1 /media/fat2 vfat uid=<your userid> 0 0
```

that will make you the OWNER of the files on mount.. :D

good luck!

---

### Post by specialboy on 2006-03-04
Had a go at editing my fstab but not having any luck thus far:(.  I know other people have been having trouble with their disks showing up and stuff so I shall see what I can see... Cheers!

---

### Post by specialboy on 2006-03-04
Wait a sec.   :D I wasn't really paying attention when I edited the fstab.  I kept the <> around my username heh heh.

Now I find my drives have mounted as they are visible in the folder I mounted them in but they are still not able to show up in the computer or on the desktop (they never could mind) But I think this is another problem.  Once again Cheers!

---

### Post by cbudden on 2006-03-04
Now this could be called a "feature", but try removing the leading / from the drives you added in fstab, as this made them show on the desktop for me.

---

