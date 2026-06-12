---
title: "Unmount main HDD for FSArchiver Restore"
date: 2011-03-15
forum: General Help
---

### Post by ondemanddesign on 2011-03-15
I need to unmount my primary partition /dev/sda1/ to perform a FSArchiver restore, however when I try to umount the partition it tells me I can't unmount a partition that is in use, how do I fix this?

```
fsarchiver restfs /mnt/backup/gentoo-rootfs.fsa id=0,dest=/dev/sda1
```

---

### Post by deadite66 on 2011-03-16
You have to boot from a separate device, a livecd like sysresccd will suffice it has fsarchiver installed.

[http://www.sysresccd.org](http://www.sysresccd.org)

---

### Post by ondemanddesign on 2011-03-16
> **deadite66 said:**
> You have to boot from a separate device, a livecd like sysresccd will suffice it has fsarchiver installed.

[http://www.sysresccd.org](http://www.sysresccd.org)

Awesome, used sysresccd, transfered the FSArchiver file over through rsync over the network, used df -h and fdisk -l to find out which hard drive to restore the .fsa file to. Worked great, thanks.

---

