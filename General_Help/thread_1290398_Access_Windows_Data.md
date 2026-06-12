---
title: "Access Windows Data"
date: 2009-10-13
forum: General Help
---

### Post by Gliderfm on 2009-10-13
I recently installed Jaunty on a 2nd hard drive. I neglected to let it have access to   my XP, since I didn't think I would need to. Can I go back and do that now that it's installed? Also will it read XP since it's on another drive?
 
Thanx All :)

---

### Post by sisco311 on 2009-10-13
Yes, you can mount ntfs partitions:
[http://psychocats.net/ubuntu/mountwindows]("http://psychocats.net/ubuntu/mountwindows")

---

### Post by Rob_H on 2009-10-13
Yup. First, figure out the identifier of the Windows partition under Linux. To do this, run:

```
sudo fdisk -l
```

Look for an "HPFS/NTFS" partition. Let's say it's **/dev/sda1**. Next, create a mount point directory for it (if necessary) and then mount it like so:

```
sudo mkdir -p /mnt/windows
sudo mount /dev/sda1 /mnt/windows
```

You can now access your Windows partition as **/mnt/windows**. If you want to mount it automatically at boot time, the process is only slightly more involved and requires editing **/etc/fstab**.

---

