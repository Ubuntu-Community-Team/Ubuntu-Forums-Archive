---
title: "Write protection on  a USB flash drive"
date: 2012-10-10
forum: General Help
---

### Post by fauhid on 2012-10-10
how do i remove write proctection on a usb flash drive in ubuntu 12.10 using either commands or graphical user interface

---

### Post by cbanakis on 2012-10-10
Maybe try to delete the partition using disk utility, then reformat?

There is not a hardware lock switch on the flash drive, is there?

---

### Post by cbanakis on 2012-10-10
or maybe...

```
sudo hdparm -r0 /dev/sdb
```Assuming your flash drive is sbd.

I think you can confirm which device is your flash drive by typing
```
fdisk -l
```

If its not obvious, you can run fdisk -l with and without the flash drive connected, then see whats listed with it connected that is not listed when it is not connected.

If that makes sense.

---

