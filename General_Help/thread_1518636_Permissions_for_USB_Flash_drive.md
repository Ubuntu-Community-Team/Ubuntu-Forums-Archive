---
title: "Permissions for USB Flash drive"
date: 2010-06-26
forum: General Help
---

### Post by axmukher on 2010-06-26
When I plug in the USB flash drive, it automounts as device /dev/sdc1 at mount point /media/usb0. The problem with this mount is that the permissions are set to root, so I cannot write to it.

Now, if I use the System > Administration > Disk Utility and first unmount the disk, then mount it again, then this time round it automounts the device as /dev/sdb1 at mount point /media/DISKNAME with the permissions reset correctly to the user logged in.

Is there any way I can correct the automount behavior?

---

### Post by supergrav on 2010-06-26
Have a look here: [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)[]("https://help.ubuntu.com/community/Mount/USB") .

---

