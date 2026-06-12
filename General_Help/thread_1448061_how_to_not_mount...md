---
title: "how to not mount.."
date: 2010-04-06
forum: General Help
---

### Post by schwabdale on 2010-04-06
I am booting off a persistent pen drive running Ubuntu 10.04. How do I tell the pen drive O/S to
NOT mount any windows partitions by default? I want to keep the drive from being able to modify
the windows install.

Please help.

---

### Post by -humanaut- on 2010-04-06
You could open a terminal and type ```
 sudo nano /etc/fstab
``` once your in the text file just simply delete the mount points for your windows partition then sudo umount /win/dows that should do it.

---

### Post by schwabdale on 2010-04-06
I am kinda new to linux. What would my Windows mount point look like?

---

### Post by muteXe on 2010-04-06
Something like this would be in your fstab:
```

/dev/hda1       /mnt/WinXP      ntfs-3g      quiet,defaults,locale=en_US.utf8,umask=0	0 0

```

In other words mounting your windows partition (/dev/hda1 in this example) to a location in your filesystem (/mnt/WinXP in this example).

This is the line you need to delete. Make a backup of your fstab first tho, just in case.

---

### Post by schwabdale on 2010-04-06
Thank you very much!

---

### Post by schwabdale on 2010-04-06
I do not have any option in fstab
it looks like this (this is a pendrive)

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0 
/dev/sdb9 swap swap defaults 0 0

---

### Post by dino99 on 2010-04-06
into system -- admin --MountManager you can made your decisions

---

### Post by eriktheblu on 2010-04-06
With a USB boot, my internal HDD does not mount automatically. It's partitions do however show under places.

If your goal is to avoid the temptation to modify the drive (or to avoid modifying it accidentally) you might consider mounting it in such a manner that it is inaccessible. You could edit your FSTAB to mount the drive in a hidden directory (say /.mnt/hd1) then set ownership to root, and permissions to 000 (no permissions).

This would make it very difficult to modify any files.

---

### Post by schwabdale on 2010-04-06
Thanks for all the replies. 
Its the same here. My partitions are showing up under places and my Home folder. 
Now that you mentioned partitions... my goal is to not allow any access to my windows 
partitions. Any ideas? I don't want to see them at all.

---

