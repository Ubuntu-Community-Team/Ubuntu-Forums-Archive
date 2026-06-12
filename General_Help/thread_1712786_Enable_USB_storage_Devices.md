---
title: "Enable USB storage Devices"
date: 2011-03-23
forum: General Help
---

### Post by suresh_vandiyur on 2011-03-23
HI,

[http://www.cyberciti.biz/faq/linux-disable-modprobe-loading-of-usb-storage-driver/](http://www.cyberciti.biz/faq/linux-disable-modprobe-loading-of-usb-storage-driver/)

In the above link am using for the Disable for USB device. how i can re enable the USB devices. please help me


Thank you,

---

### Post by Script Warlock on 2011-03-23
did you ask them how to reverse their method?

---

### Post by suresh_vandiyur on 2011-03-23
> **Script Warlock said:**
> did you ask them how to reverse their method?

mv /root/usb-storage.ko  /lib/modules/$(uname -r)/kernel/drivers/usb/storage/
modprobe usb-storage i hvae tried this command but enabling the usb devices.please help me

Thank you

---

