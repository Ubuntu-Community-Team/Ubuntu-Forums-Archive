---
title: "Unable to remove kernel after failure of update"
date: 2009-10-29
forum: General Help
---

### Post by wikikie on 2009-10-29
Dear all,

Recently, I tried to update my Ubuntu 8.10 to 9.04.
Due to unknown reasons, the update seems to be unsuccessful.
After that, every time when I run the update manager, the following message appears:

[COLOR=Blue]The following packages will be REMOVED:
  linux-restricted-modules-2.6.27-7-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2220kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 149650 files and directories currently installed.)
Removing linux-restricted-modules-2.6.27-7-generic ...
rmdir: failed to remove `/lib/modules/2.6.27-7-generic/volatile/': No such file or directory
FATAL: Could not open '/boot/System.map-2.6.27-7-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
Cannot find /lib/modules/2.6.27-7-generic
update-initramfs: failed for /boot/initrd.img-2.6.27-7-generic
dpkg: error processing linux-restricted-modules-2.6.27-7-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-restricted-modules-2.6.27-7-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]


Does anyone have any idea of what shall I do (my recent kernel is _2.6.27.2-ma1_)?
Thank you very much.

Wik

---

