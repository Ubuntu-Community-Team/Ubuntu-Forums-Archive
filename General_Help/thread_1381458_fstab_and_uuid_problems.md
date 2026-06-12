---
title: "fstab and uuid problems"
date: 2010-01-14
forum: General Help
---

### Post by James- on 2010-01-14
I'm trying to specify my usb key to mount in /media/Kingston with certain options, but when I do add the UUID line to my /etc/fstab I get two devices:
16 GB File System
Kingston
I have created the directory /media/Kingston

When I click on Kingston the first time it says a timeout error, a second time and it says /dev/sdb1 is already mounted(it mounts the 16GB File System on my desktop..)

here is my fstab:
```

proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=5457a33f-656e-4d57-8c77-8de798b08ec8 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=33dd70df-2d5a-4ca3-93f3-79ee62478cc4 /home           ext4    defaults        0       2
/dev/sda5       none            swap    sw              0       0
UUID=51d20e2f-9a93-4dfe-9d91-05fca4f34c35 /media/Kingston ext4 data=writeback,noauto,errors=remount-ro,noatime,nodiratime,user 0 0

```

*EDIT*
seems ubuntu doesn't like/ignores UUIDs
I hard coded /dev/sdb1 instead of the UUID and it works as it's suppose to

---

