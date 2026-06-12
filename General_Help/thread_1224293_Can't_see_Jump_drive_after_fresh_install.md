---
title: "Can't see Jump drive after fresh install"
date: 2009-07-27
forum: General Help
---

### Post by i-like-knives on 2009-07-27
Just installed Hardy (fresh). The same drive showed up fine on gutsy before.
The jump drive light is on in its dock.
Read media preferences etc and checked google too for issue, but none address if you cannot even see the drive on the computer places. Both CD/DVD drives show with filesystem, so0 ??
Thanks.

---

### Post by ajgreeny on 2009-07-27
This is a usb drive, right? If so plug it in and run in terminal ```
lsusb
```and see if the system can at least see it,  You can also run ```
sudo fdisk -l
``` in terminal again to see that the system sees it properly, and that the partition(s) on it are still intact, and can then try to mount it manually.

Report back the output from those two commands and let's see where we go from there.

---

