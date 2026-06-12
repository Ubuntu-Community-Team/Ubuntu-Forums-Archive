---
title: "can't install Updates"
date: 2009-09-01
forum: General Help
---

### Post by Kello125 on 2009-09-01
So i try to install the updates and it tells me i don't have enough space on '/'

How can i fix this?

---

### Post by Kello125 on 2009-09-01
bump

---

### Post by tuxxy on 2009-09-01
It seems your filesystem is full, did you check your drives/partitions, use df in the terminal for info.

---

### Post by drs305 on 2009-09-01
Run this and post the results:
```

df -H

```

If your / is full, you might look at this guide to resizing a / partition if you know why you are out of space:
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

If it is full and it only 2.3-2.5GB following a new installation side by side with Windows:
[2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")

If you don't know why it is full:
[Disk Space Problems & Solutions]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by Kello125 on 2009-09-01
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by drs305 on 2009-09-01
> **Kello125 said:**
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Have you run the command as the error message suggests:
```
sudo dpkg --configure -a
```
It will ask for your password. You won't see it as you type. When finished typing it, hit ENTER. 
If you get error messages, please post them for us.

Then
```

sudo apt-get update
sudo apt-get upgrade

```

---

