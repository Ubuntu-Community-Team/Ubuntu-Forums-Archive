---
title: "Installing Ubuntu Minimal from USB Stick"
date: 2011-07-16
forum: General Help
---

### Post by JaizEdelmann on 2011-07-16
We are strugling with installing ubuntu minimal maverik from a usb stick, everytime we have installed we get master boot record on USB instead of our harddrive , what todo?

How do we set master boot record on the harddrive with the ubuntu installation, so we can unplug the .... usb key.

---

### Post by mikewhatever on 2011-07-17
The MBR of a device is usually designated as /dev/sdX (for example - /dev/sda, /dev/sdb, etc). Make sure you select the correct one when installing.
On the second though, it really doesn't matter. If you can boot the newly installed system with the USB stick plugged in, just reinstall grub with the following command:
```
sudo grub-install /dev/sda
```

/dev/sda is usually the hard disk, but you can verify that by running **sudo fdisk -l**.

---

