---
title: "How to restrick the USB Access"
date: 2011-03-22
forum: General Help
---

### Post by suresh_vandiyur on 2011-03-22
Hi,

I want restrict pen drives and usb Hard disk for the normal users because i restrict the USB port means the usb mouse and usb keyboard may work or not.
How to do this. please Help Me.

Thank you,

Regards,
Suresh

---

### Post by An Sanct on 2011-03-22
There are several ways to [disable USB storage]("http://www.cyberciti.biz/faq/linux-disable-modprobe-loading-of-usb-storage-driver/") as noted in the link and will not change the way other USB devices work (mouse, keyboard, sound, webcam, ...).

---

### Post by suresh_vandiyur on 2011-03-22
> **An Sanct said:**
> There are several ways to [disable USB storage]("http://www.cyberciti.biz/faq/linux-disable-modprobe-loading-of-usb-storage-driver/") as noted in the link and will not change the way other USB devices work (mouse, keyboard, sound, webcam, ...).

Ok. it will not affect the usb mouse and keyboard?. how to re enable USB devices. it will not affect the root users?..

Thank you,

Regards,
Suresh

---

### Post by suresh_vandiyur on 2011-03-22
> **suresh_vandiyur said:**
> Ok. it will not affect the usb mouse and keyboard?. how to re enable USB devices. it will not affect the root users?..

Thank you,

Regards,
Suresh

How to re enable the usb ports

Thank you,

Regards,
Suresh

---

### Post by satish_j on 2011-03-22
You can re-enable usb access by simply moving the *usb-storage.ko* back to kernel path
or
removing the *nousb* from grub config file
It is mentioned in the link given by An Sanct

---

