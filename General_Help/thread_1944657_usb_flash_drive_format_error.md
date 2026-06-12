---
title: "usb flash drive format error"
date: 2012-03-21
forum: General Help
---

### Post by yisong on 2012-03-21
Hi, I have a problem with a 16gb usb flash drive. The problem arose after trying to install a version of ubuntu (version Qbuntu, ubuntu 10.04 modified by University of Barcelona faculty of chemistry), but the installation failed. then i tried to format the usb in ubuntu and this failed with message "_Error creating file system: helper exited with exit code 1: Error calling fsync (2) on / dev/sdc1: Input / output error_". then i tried to format it in windows and failed again with the classic error "disk is write protected" and then i tried many solutions (regedit-writeprotect /, usbwp /, ..) but none worked. the usb has lever , and as I am a newbie with ubuntu, i dont know what to do. if anyone have any solution please reply. Thank you.:confused:

---

### Post by ajgreeny on 2012-03-21
Try again with gparted either by installing it in your installation of Qbuntu or from a live CD, but rather than just trying to make a new partition, first write a new partition table from the Device menu of gparted.

That should wipe the disk completely clean leaving unallocated space where you can then make a new partition.

---

### Post by yisong on 2012-03-21
> **ajgreeny said:**
> Try again with gparted either by installing it in your installation of Qbuntu or from a live CD, but rather than just trying to make a new partition, first write a new partition table from the Device menu of gparted.

That should wipe the disk completely clean leaving unallocated space where you can then make a new partition.

Thanks for the fast reply,
i tried to wipe out the disk installing from a live CD but it failed with message "_org.freedesktop.UDisks.Error.Failed: Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sdc: Input/output error_" and "_S'ha produït una excepció no controlada: [Errno 30] Read-only file system: '/media/YiS 16GB/casper_' (means an uncotrolled exception occurred):frown:

---

