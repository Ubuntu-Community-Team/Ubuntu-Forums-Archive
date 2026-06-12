---
title: "How to find usb stick in terminal?"
date: 2009-10-24
forum: General Help
---

### Post by oxymoron on 2009-10-24
Hi,

What is the command to see where my usb stick is mounted?


Regards

Oxy

---

### Post by geirha on 2009-10-24
If it's mounted, then either of the following commands should show the mountpoint
```
mount
df -h
```

---

### Post by oxymoron on 2009-10-24
hhmmm, it appears it isn't mounted, how does one mount a usb stick in terminal?

---

### Post by frt975 on 2009-10-24
```
sudo mkdir /mount/location/
sudo mount /dev/sdbX /mount/location
```

---

### Post by geirha on 2009-10-24
First, find the correct partition to mount. fdisk should help identify the correct device node.
```
sudo fdisk -l
```

If /dev/sdb is the usb-stick, then the partition containing the filesystem you want to mount will usually be /dev/sdb1. Assuming it is /dev/sdb1, you mount with:

```
sudo mount /dev/sdb1 /mountpoint
```

The mountpoint must exist, and it must be a directory, so make sure it is created first. E.g.:
```
sudo mkdir /mnt/usbstick
sudo mount /deb/sdb1 /mnt/usbstick
ls /mnt/usbstick
```

---

