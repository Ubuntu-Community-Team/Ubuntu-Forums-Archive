---
title: "udev rules for cryptsetup"
date: 2011-01-17
forum: General Help
---

### Post by v1nny on 2011-01-17
I use external e-sata disks, encrypted, for off-site backups. To ease their use, I created a udev rule to automatically setup the device mapper (dm) device to be ready to be mounted. Here is the rule I am using:

/etc/udev/rules.d/cryptsetup.rules:
```

ACTION=="add", ENV{ID_FS_TYPE}=="crypto_LUKS", RUN+="/sbin/start cryptdisks-udev DEVNAME=/dev/disk/by-uuid/$env{ID_FS_UUID_ENC}"

```

Since the disk (by-uuid) is listed in the crypttab, this actually works surprisingly well. In my setup I don't have to worry about mounting the disk as I handle that automatically in my backup script.

Ideally, I'd like a similar udev rule to automatically remove the dm device when the disk drive is removed. I've tried several things, but at this point it looks like I'm going to have to write a script, to be called by udev (like above, but ACTION="remove"), that iterates over all the dm devices to check to see if the device uses the device being removed.

Does anyone know, or can think, of a better way to handle the device removal?

Thanks.

---

