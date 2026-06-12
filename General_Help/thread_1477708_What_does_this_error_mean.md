---
title: "What does this error mean?"
date: 2010-05-09
forum: General Help
---

### Post by Cityscape on 2010-05-09
I have a friend who get this error while trying to install Lucid on his desktop. ```
could not start device/dev/mapper/asr_pictures-no such file or directory
```

He gets this after putting keyboard info in. And Jaunty would install fine on his PC.

What does this error mean? :confused:

---

### Post by Cityscape on 2010-05-09
No one knows what this means?

---

### Post by SPr on 2010-05-09
Has the install CD been checked for errors? There should be a menu item for the check before the Live CD loads.

---

### Post by Cityscape on 2010-05-10
> **SPr said:**
> Has the install CD been checked for errors? There should be a menu item for the check before the Live CD loads.
He has burnt 2 CD's and bought one. They all gave the same error.

---

### Post by captain22275 on 2010-05-10
iam not exactly an expert but i recommend downloading the disc from a different source or borrowing it from someone as it sounds like a corrupt disc to me if not download a 9.10 disc burn it install it then update to 10.04

---

### Post by Mark Phelps on 2010-05-10
It's very unlikely all three disks would be bad ... so, I would first boot from the LiveCD and see what fails.

---

### Post by Cityscape on 2010-05-10
He has burnt the cd with 2 different iso images on 2 different computers and bought one online from OnDisk & all had the same problem. It can't be the CD's.

He had Jaunty and when he tried to upgrade to Karmic it destroyed his system. But I'll tell him to try a Karmic > Lucid upgrade.

---

### Post by oldfred on 2010-05-10
Were these drives ever in a RAID configuration?  If they still are DO NOT do this:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

### Post by Cityscape on 2010-05-11
So is this error Raid related?

---

### Post by oldfred on 2010-05-11
Drives save metadata that can interfer. Only if the drives we in a raid and sometimes when experimenting BIOS setting it may write something. but if drives are still RAID running the commands will destroy the RAID. If not raid running them should not cause any problem. It has worked for a few that forgot they had disks in a raid configuration.

---

