---
title: "Stop mounting internal disks in /media"
date: 2010-10-07
forum: General Help
---

### Post by twins on 2010-10-07
Hi

I want my usb disks to automount in /media as usual, but I don't want the internal partitions to be mounted there. The internal partitions are my business, and I'd like to install it ONLY where I want. I can disable the automount, but then the usb disks will not mount.
Can anyone help me, please?
Btw, I run 10.04.

thanks

twins

---

### Post by nevius on 2010-10-07
> **twins said:**
> Hi

I want my usb disks to automount in /media as usual, but I don't want the internal partitions to be mounted there. The internal partitions are my business, and I'd like to install it ONLY where I want. I can disable the automount, but then the usb disks will not mount.
Can anyone help me, please?
Btw, I run 10.04.

thanks

twins

You can change the mount point in /etc/fstab, but before editing your fstab, do the following:

1) back it up
2) read the documentation:[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by twins on 2010-10-07
> **nevius said:**
> You can change the mount point in /etc/fstab, but before editing your fstab, do the following:

1) back it up
2) read the documentation:[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Thanks.
I already changed my fstab. I already monted my partitions precisely where I want. What is still missing is to get rid of the /media mountpoints.
/media automounts are not in fstab. Btw, what is the file that configures automount?

twins

---

### Post by Morbius1 on 2010-10-07
Then unmount them:
```
 sudo umount /media/whatever
```
They shouldn't be permanent mountpoints.

---

