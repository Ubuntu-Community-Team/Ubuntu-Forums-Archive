---
title: "navigate to drives using 'cd' command"
date: 2011-07-26
forum: General Help
---

### Post by love_linux1 on 2011-07-26
suppose i have 2 hdsk partitions.

1)File system: 40GB (ext4) : system, home, swap, boot, tmp, fat32_windows
2)Xyz: 40GB (ntfs) : other partion cöntaining files.

Terminal:
user@xy-desktop$

now what to do to goto 'xyz' drive(ntfs) and access files?

---

### Post by 13east on 2011-07-26
Depends on where you have "xyz" mounted.

Two common options are to have it mounted to either ```
/mnt
``` or ```
/media
```.  So the command with respect to above mount points would be:

```
cd /mnt/xyz
cd /media/xyz
```

---

### Post by seawolf167 on 2011-07-26
As said previously, it depends on the mounted name of the partition as well as the mount point. You can see all the mounted items on your computer by typing in

```
mount
```

If you item isn't on the list, you will need to mount it before you can access it

```
man mount
```

else, you can simply "cd" to the directory where the partition/drive is mounted

```
cd /path/to/folder
```

just replace /path/to/folder with its mount point and name (as a common example, see the previous poster's commands at the bottom of the post)

---

### Post by AlphaLexman on 2011-07-26
Also, see...
[https://help.ubuntu.com/community/Mount]("https://help.ubuntu.com/community/Mount")

---

### Post by ajgreeny on 2011-07-26
Don't forget that though you speak of disks, ubuntu and all linux distros will see partitions.  With regard to mounting partitions it can be extremely helpful to give labels to all partitions on all disks.  That way even usb disks are mounted at the same mount point at all times, even if attached in a different order.  If not labelled they will be mounted as /media/disk1, /media/disk2, etc etc and not always the same number, which can be very confusing.

---

