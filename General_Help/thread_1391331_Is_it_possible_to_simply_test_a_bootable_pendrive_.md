---
title: "Is it possible to simply test a bootable pendrive with qemu?"
date: 2010-01-26
forum: General Help
---

### Post by frenchn00b on 2010-01-26
Hello,

Qemu does only boot  from floppy, img/iso, or ide, cdrom, but not usb? 
is that right?

---

### Post by frenchn00b on 2010-01-28
It seems that it is    possible ...  

> qemu -hda /dev/sda 


this may be but is buggy : qemu -usb -usbdevice <devicename>

---

### Post by falconindy on 2010-01-28
Make an image of the USB drive with dd and boot from that.

```
dd if=/dev/sdxy of=~/flashdrive.img bs=1M
```
Just replace /dev/sdxy with the partition letter/number of your flash drive.

---

### Post by frenchn00b on 2010-01-28
> **falconindy said:**
> Make an image of the USB drive with dd and boot from that.

```
dd if=/dev/sdxy of=~/flashdrive.img bs=1M
```
Just replace /dev/sdxy with the partition letter/number of your flash drive.

nice

---

