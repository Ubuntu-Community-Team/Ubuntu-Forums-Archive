---
title: "turning on usbfs, all usb device not working"
date: 2012-07-10
forum: General Help
---

### Post by h113331pp on 2012-07-10
Hi, all, sorry to ask such an old question, but I have to turn on the usbfs option in kernel in order to use usb redirect function in VMware view client, I googled a lot of threads about usbfs, and got two ways:

1.bind /sys/bus/ or /dev/bus to /proc/bus - this not work, VMware

2.turn on CONFIG_USB_DEVICEFS option the in ubuntu kernel - this make all usb device not working after I replace my kernel(since I use the same config as ubuntu default I don`t need replace the entire kernel module).

I also read some article saying this option not used after 2.6.32, and udev take the job, so is it the reason I broke my usb device function?

---

### Post by h113331pp on 2012-07-11
Sorry, my fault. just make sure 'vmware-view-usb' have the privilege 2755, or the application couldn`t operation any usb device. and new version vmware-view doesn`t need usbfs for usb redirect.

---

