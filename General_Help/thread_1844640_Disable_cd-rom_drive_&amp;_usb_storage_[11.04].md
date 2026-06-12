---
title: "Disable cd-rom drive &amp; usb storage [11.04]"
date: 2011-09-15
forum: General Help
---

### Post by Fabien88 on 2011-09-15
Hi,

I didn't manage to disable Cdrom drive/usb storage on Ubuntu 11.04.

Here are my failed attempts : 
Removing user from groups cdrom and plugdev
Deleting file /lib/modules/$(uname -r)/kernel/drivers/usb/storage/usb-storage.ko

Blacklisting usb storage : echo 'blacklist usb_storage' >> /etc/modprobe.d/blacklist.conf

None of these solutions work.

Moreover, cdrom auto mount while /etc/fstab does not contain any 
 link to the cdrom driver...
Anyone else know a solution to this problem ?
Thank you for your help.

---

