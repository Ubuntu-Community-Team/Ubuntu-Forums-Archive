---
title: "Usb data not working on live usb install"
date: 2010-10-08
forum: General Help
---

### Post by altometer on 2010-10-08
So I have a bit of a puzzling pickle.

When running Ubuntu 10.4 from my Kingston 8GB usb stick, I can not read other usb data drives! 

I can verify the USB ports still work because I use a mouse and keyboard. Any help will be greatly appreciated!

EDIT:I re-installed the OS, works now.

---

### Post by P4man on 2010-10-08
odd. Perhaps post the output of

```
sudo fdisk -l
```

and

```
lsusb
```

to see if the USB drives are being recognised and the partitions are visible.

---

### Post by altometer on 2010-10-11
Odder yet, it appears to have corrected itself after applying the newest updates. Thank you for the replay anyway!

---

