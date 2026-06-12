---
title: "don't see flash disk which plugged in runtime"
date: 2010-08-22
forum: General Help
---

### Post by Sanjarbek on 2010-08-22
I am using Ubuntu 9.10 Desktop.
My problem is when I plug in flash disk in computer in runtime system don't automatically mount partions. There isn't any new files in /dev which I could be mount.
What cause it? Before everything was working.

Thanks

---

### Post by martin_legion on 2010-08-23
Try pluggin the flash drive in a different slot. After pluggin it type 
```
dmesg | grep SCSI
```
and look for something like:
```
[27454.113114] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[27454.113549] sd 7:0:0:1: [sdd] Attached SCSI removable disk
```
You can also try the command "mount" alone to see all the mounted devices on the system and their mount points.

---

