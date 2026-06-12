---
title: "pyusb broken"
date: 2010-09-02
forum: General Help
---

### Post by dld on 2010-09-02
My applications that use pyusb are all broken this morning.  I did a Ubuntu update earlier, without much thought.  I believe  usb-creator-common  and  usb-creator-gtk  were replaced, as well a few python packages.   Any one know of this problem and fixes?
Don

---

### Post by dld on 2010-09-02
Solved!  My  /lib/udev/rules.d$/50-udev-default.rules  file was modified, but I have no idea when or how that happened.

---

