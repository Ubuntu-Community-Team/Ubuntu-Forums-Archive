---
title: "/media has 2 My Book entries after Lucid upgrade"
date: 2010-05-02
forum: General Help
---

### Post by evolmachine on 2010-05-02
/media has 2 similar entries for my external hard drive after I upgraded from Karmic to Lucid. One reads "My Book" and the other "My Book_".  "My Book" is owned by root and I can't access it.  Unfortunately all my shortcuts and programs previously linked to this hard drive are complaining they don't have permission to access the drive (mediatomb and deluge, mostly).

How can I get rid of the extra "My Book_" and reclaim "My Book"?

---

### Post by evolmachine on 2010-05-02
also, trying to unmount the second partition of the external hard drive "WD Smartware" gives the error

Unable to unmount WD SmartWare
umount: /media/cdrom2 mount disagrees with the fstab

I have no idea what that means.

---

### Post by evolmachine on 2010-05-02
I managed to muddle through "chown" to get access to "My Book".  after unplugging my external drive "My Book" is still there, however "My Book_" has disappeared (logically).  I can't unmount "My Book".  I can't delete it.  It's completely empty and shows 19.2Gb of free space!  WTF?!

I tried editing /etc/fstab but I have no idea what it all means...

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=a8d5b318-7151-4860-9105-2def109eb202 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=2ccfd9b5-e2a7-4d84-94ce-51883a21b82a none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

any help would be greatly appreciated.

---

### Post by lunatico on 2010-05-29
Yeah this just happened to me today that I upgraded from 9.10 to 10.04.
I'll start looking for a solution and when I find it I'll post.
Did you ever found a solution?

---

### Post by lunatico on 2010-05-29
OK, found the solution.

[LIST=1]
[*]Unplug your USB hard drive (former My Book)
[*]Open a terminal window and type:
[*]sudo nautilus /media
[*]Delete the 'My Book' folder
[*]Close your windows
[*]Plug you USB hard drive again
[/LIST]

Hope it helps.

---

### Post by Desabrir on 2010-09-30
I have the same problem, except it only happens with my external usb DVD drive. I have no problems with my usb HDD. 

> **lunatico said:**
> OK, found the solution.

[LIST=1]
[*]Unplug your USB hard drive (former My Book)
[*]Open a terminal window and type:
[*]sudo nautilus /media
[*]Delete the 'My Book' folder
[*]Close your windows
[*]Plug you USB hard drive again
[/LIST]

Hope it helps.

Did this, well tried, and I got an error about it being busy.

---

### Post by lunatico on 2010-10-01
> **Desabrir said:**
> Did this, well tried, and I got an error about it being busy.

That's very strange. Are you sure you unplugged the DVD drive first?

---

