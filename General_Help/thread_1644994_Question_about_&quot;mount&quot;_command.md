---
title: "Question about &quot;mount&quot; command"
date: 2010-12-14
forum: General Help
---

### Post by e24ohm on 2010-12-14
Folks:
I have been mounting my usb flash drive as followed:

**df -T**
To find the type and location of my flash drive.

**sudo mount /dev/sdb1 /mnt/usb**
To mount the flash drive to /mnt/usb; however, I am not useing the **-t** switch to specify the partion type, which happens to be vfat and I have no problem mounting.

In addition, my other drive is FuseBlk, which I am not sure what that means; however, I also have no issue mounting this drive.

Question. Is it important to speicfy the partition type when mounting?

---

