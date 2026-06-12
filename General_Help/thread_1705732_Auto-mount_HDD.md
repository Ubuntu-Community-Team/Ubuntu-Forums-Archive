---
title: "Auto-mount HDD"
date: 2011-03-12
forum: General Help
---

### Post by Rythyminside on 2011-03-12
Newbie here,

Is there a way to auto mount partitions or SATA HDDs on startup, using 10.10?

I have no problems reading the drives.

---

### Post by coffeecat on 2011-03-12
You need to edit /etc/fstab. Have a look here:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you have NTFS partitions, you may come across a utility in the repos called ntfs-config. My advice - steer clear of it. On occasion it can do some really unfortunate things. It's safer to learn how to edit fstab yourself.

If you need help, post the output of these commands:

```
sudo fdisk -lu
sudo blkid
```And mention which partitions you want mounted.

---

