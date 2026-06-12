---
title: "Can't mount USB Storage Devices"
date: 2010-05-04
forum: General Help
---

### Post by Darkness Des on 2010-05-04
Whenever I plug in a Flash Drive, External Hard Drive, or anything else remotely related to storage through a USB port, nothing happens. Ubuntu doesn't recognize that it is there, only when I run LSUSB can I see it, and I can't get anything to mount. This is a problem for me, as I back up to an external Hard Drive frequently. Does anybody have a solution?

---

### Post by garvinrick4 on 2010-05-04
> **Darkness Des said:**
> Whenever I plug in a Flash Drive, External Hard Drive, or anything else remotely related to storage through a USB port, nothing happens. Ubuntu doesn't recognize that it is there, only when I run LSUSB can I see it, and I can't get anything to mount. This is a problem for me, as I back up to an external Hard Drive frequently. Does anybody have a solution?Yes, first hit Alt and F2 at same time
and type gconf-editor in box and click run. When Configuration editor opens go to Apps to
nautilus to Preferences and check boxes to open your media.

Next I will give you 2 small pieces of code, open a terminal and put them in one at a time
and copy and paste the results here and I will tell you how to open media if you want from
command line for cases like this. 

sudo fdisk -l  (small L)

sudo blkid  (small L second letter)

Have your media plugged into your machine when you run these commands.

---

### Post by Darkness Des on 2010-05-10
Edit:
I updated, although none of them had ANYTHING to do with media, it mysteriously started working again. Thank you for your help.

---

