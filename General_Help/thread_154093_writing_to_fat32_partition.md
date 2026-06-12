---
title: "writing to fat32 partition"
date: 2006-04-02
forum: General Help
---

### Post by steve196 on 2006-04-02
How do I give an ordinary user write permission to a fat32 partition?

---

### Post by cjazz on 2006-04-02
Edit your /etc/fstab. Under <options> for your fat32 partition, add umask=000.

The line for your fat32 partition might look something like this:

/dev/hda1       /media/hda1     vfat    defaults,umask=000        0       0


You should, of course, substitute your own information for partition name, mount point, etc.

---

### Post by steve196 on 2006-04-02
I wrote that into fstab and unmounted and remounted the partition. Now root sees all permissions enabled, but the other user still doesn´t have them.

---

### Post by rabidphage on 2006-04-02
follow this procedure
```
sudo gedit /etc/fstab
```

comment out the fstab entry relating to your partitions by adding a # before he entry

/dev/hda1       /media/hda1     vfat users,rw,owner,umask=000 0 0

copy paste this once for each harddrive partition and change the device and mount point accordingly. for example /dev/hda2 is the second partition of the drive and /media/hda2 is the mount point.

Save and exit gedit 

remount or reboot.

---

### Post by steve196 on 2006-04-02
Now I can mount and umount without being root, but there is still the same thing with write permissions.

---

### Post by steve196 on 2006-04-03
Problem solved. Complete reboot instead of umount/mount was needed.

---

