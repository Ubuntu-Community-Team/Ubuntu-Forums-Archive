---
title: "dd"
date: 2010-09-11
forum: General Help
---

### Post by Begin_learn on 2010-09-11
i have a pen drive that has two mp3 files.i am unable to delete the files as they appear again and again..............how can i format the drivee using dd command

---

### Post by HermanAB on 2010-09-11
Something like this:

Plug drive in, then look at the kernel messages:
dmesg

Figure out the name of the device, probably /dev/sdb

Format it with:
mkfs.vfat /dev/sdb1

BTW, there is probably a format utility elsewhere in the system - either in the Tools menu or in a Nautilus context menu.

---

### Post by Sam Fallow on 2010-09-11
I suspect that if you didn't 'unmount' the pen drive these two files will continue to appear.

Try deleting them on a windows machine. Always pays to unmount usb devices.

---

