---
title: "Help in mounting fat partition"
date: 2010-06-30
forum: General Help
---

### Post by Ubu4moi on 2010-06-30
I have a FAT32 partition on my harddrive with Ubuntu 10.04LTS. Everytime I want to mount it the OS ask me for the password, how can I configure it so I can mount it with out needing to authenticate evreytime?

---

### Post by ajgreeny on 2010-06-30
You can either use an edit to your /etc/fstab file, or you could try adding the **disk mounter** applet to your panel.  I use the latter, or I did for a fat32 windows partition in the past with no problems at all.  I still use it for other ext3 and ext4 partitions from other linux distros.

Automount fat32 at boot by adding this line to /etc/fstab having made the folder first with ```
sudo mkdir /media/fat32
```
Line to add with your own dev name and folder name as you wish.
```
/dev/sdx# /media/fat32 vfat defaults,user,dmask=027,fmask=137 0 0
```

---

