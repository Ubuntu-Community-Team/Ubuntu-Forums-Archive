---
title: "Empty Hard Drive with 4GB Unavailable"
date: 2010-10-01
forum: General Help
---

### Post by dodle on 2010-10-01
I'm just curious about this, I don't understand exactly how all filesystems work.  I have an empty hard drive formatted to ext4 that shows 4.8GB being unavailable, and the trash is empty.  Why is this?  Attached is a picture to demonstrate.

---

### Post by mikewhatever on 2010-10-01
One of the reasons is reserved space. By default, ext3/ext4 reserve 5% of disk space for whatever system needs. Since yours is likely an external hdd, and probably is not intended for OS installations, reclaiming the 5% should be safe.

```
sudo tune2fs -m 0 /dev/sdXY
```

Check what X and Y are with the **sudo fdisk -l** command.

---

