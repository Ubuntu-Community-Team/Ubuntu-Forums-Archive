---
title: "Update initramfs on PXE server"
date: 2010-10-26
forum: General Help
---

### Post by chipperuga on 2010-10-26
After copying a filesystem to be used as an image on a PXE server, is it possible to update that image's initramfs on the PXE server?

On PXE server, I added several ethernet modules/drivers to the following file:
/nfsroot/etc/initramfs-tools/modules

Before the changes will take effect, I need to run:
```
$ sudo update-initramfs -u
```

---

### Post by chipperuga on 2010-10-26
Use chroot?

```
**campuslife@pxedus**t:~$ sudo chroot /nfsroot/
[sudo] password for campuslife: 
**root@pxedust**:/# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
```

---

