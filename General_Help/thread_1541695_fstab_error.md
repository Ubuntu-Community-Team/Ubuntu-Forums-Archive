---
title: "fstab error"
date: 2010-07-29
forum: General Help
---

### Post by shelly13 on 2010-07-29
hi all, 
i have installed ubuntu server 10.04 over my windows xp system and after installation it is not allowing me to perform any filr related operations. not even new file/directory creation. It gives "Read Only File System" error.
I have tried fsck command and it gives me error in /etc/fstab.
I am new to linux..can anybody give me any solution?
It is urgent.

---

### Post by ajgreeny on 2010-07-29
Post the output of ```
cat /etc/fstab
``` and ```
sudo blkid
```and we may be able to help more.

---

### Post by shelly13 on 2010-07-30
i have seen etc/fstab, but its totally currepted and give symbolic output..

---

### Post by prodigy_ on 2010-07-30
If /etc/fstab is indeed corrupt, you'll need to recover it manually, because without it your OS won't be able to boot. This file lists all file systems that must be automatically mounted at boot time, including root (/) file system.

An simple example of working /etc/fstab:
```
# / was on /dev/sdc1 during installation
UUID=6b5610c4-6774-4080-bd76-72be7b3fad70 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc3 during installation
UUID=774bd8b2-6c42-4687-9a70-4dcfdf614473 none            swap    sw              0       0
```

---

If you're not sure which partition should be the root file system, you can try to use the Boot Info Script from my sig. It provides a lot of diagnostic info.

---

### Post by ajgreeny on 2010-07-30
OK, let's see the output now of the ```
sudo blkid
``` and ```
sudo fdisk -l
``` from terminal in a live CD, and we should be able to put together an /etc/fstab file that will work for you.

---

