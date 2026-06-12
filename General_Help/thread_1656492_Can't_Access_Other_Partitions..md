---
title: "Can't Access Other Partitions."
date: 2010-12-31
forum: General Help
---

### Post by asrockw7 on 2010-12-31
Hi, I am completely new to the whole Linux scene and I am currently using Xubuntu after i used Ubuntu and Kubuntu. So far, i'm preferring it over both. The only problem is I can't access my other partitions. I have my Windows partition and another partition just for storage and such, and I can't access it. I can't even see them using the default File Manager of Xubuntu. I've downloaded Dolphin to try and somehow work it out, and i do see them now but i still can't access them.

Xubuntu 10.10, if it means anything.

Also, I do have Xubuntu on a separate partition alone.

---

### Post by Brandon Williams on 2010-12-31
Are the partitions in question present in your /etc/fstab file? If not, then you will first want to create mount points (for example, 'sudo mkdir /mnt/windows' and/or 'sudo mkdir /mnt/data'). Then test mount the partitions (for example, 'sudo mount /dev/sdaX /mnt/windows' or 'sudo mount /dev/sdaY /mnt/data', where X and Y represent the partition numbers for the windows and data partitions). If this works, then you can use sudo to edit your /etc/fstab files to get your system to automount the partitions on boot. The lines would look something like this:```
/dev/sdaX /mnt/windows auto defaults 0 0
/dev/sdaY /mnt/data auto defaults 0 0
```

If this is unclear or doesn't work for you, please provide more specific information about the partitions and the content of your /etc/fstab file so we can give more specific help.

---

