---
title: "How do i change mount point of HAL devices?"
date: 2006-03-19
forum: General Help
---

### Post by Nexu on 2006-03-19
How do i change mount point of HAL devices?

EG: instead of /media/usbdisk i want it to mount at /home/Storage/USBdisk

---

### Post by Jucato on 2006-03-19
If it's found in your /etc/fstab, you can simply change the entry there from /media/usbdisk to whatever you want, AFAIK

---

### Post by Nexu on 2006-03-19
I know that, but its not being managed by fstab. It's being mounted by HAL.
Reason i SPECIFIED in the topic "HAL".

---

