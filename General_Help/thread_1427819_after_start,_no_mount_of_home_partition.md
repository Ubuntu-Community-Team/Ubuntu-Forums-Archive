---
title: "after start, no mount of /home partition"
date: 2010-03-12
forum: General Help
---

### Post by tyoc213 on 2010-03-12
Hi there, I was working OK with my laptop all this time from the launch of 9.10 but now I cant boot to my system...

I mean, more than 2 partitions, 1 for system, 1 for home, one for other archives, and so on.

The problem is that in the startup, mount all cant mount the /home partition Im runing right now from 9.10 live CD

Also, note: edited /etc/fstab and comented the line of /home, then it can run to the X and login, but cant update the archives of Xauthority or some like that because there is no /home/tyoc213 where to modify them... the X session is "usable" in the sense that it display the default back ground, but no bars or meno, no ALT+F2 or ALT+F1, I cant launch nothing... but if I hit the shutdown button the window for select power off, reboot and so on is launch.

---

### Post by srs5694 on 2010-03-12
Something's changed about your /home partition, or perhaps its /etc/fstab entry was edited improperly. It's impossible to know for sure without more information, but the fix is likely to be the same no matter what the cause. All the fixes require you to have *some* method of identifying your partition -- by partition name/number (e.g., /dev/sda5), by UUID, or by name. With that information in hand, you can edit the partition's /etc/fstab entry; change whatever is there now (probably a UUID) to use the new identifiers. For instance, if you know the partition is /dev/sda5, you could change the entry to:

```

/dev/sda5        /home    ext3           noatime        0 2

```

Change "ext3" to the correct filesystem type, if necessary. You can also change other entries for various options. It's probably best to leave whatever you've got now for most fields; just change the first field that identifies the filesystem. If you prefer to use a UUID, as Ubuntu does by default, you can locate it with the blkid command, as in "blkid /dev/sda5". Specify it after a "UUID=" string.

Once this is done, type "mount -a" as root, with /home unmounted, and see if the filesystem mounts. If it does, everything should then work (your X problems are symptoms of the /home filesystem not being mounted). To be 100% sure, reboot.

---

### Post by tyoc213 on 2010-03-14
Hi there, it works, I have watched the /dev/sda# from gparted with the info option... thought it doesnt display the UUID, also I edited /etc/fstab with /dev/sda5 and now Im able to enter again to my sistem... but

> $ blkid /dev/sda5 -v
blkid from util-linux-ng 2.16 (libblkid 2.16.0, 10-Feb-2009)

as you see the command doesnt show the actual UUID, dont know what has happened if it is an error or an HD failure.

---

### Post by srs5694 on 2010-03-15
The "-v" option to blkid just shows the program's version number and then exits. This overrides the normal behavior of displaying information about the filesystem it's fed, so if you want the filesystem's UUID, you must omit the "-v" option.

---

