---
title: "usb storage devices don't work, everything else usb does"
date: 2011-01-03
forum: General Help
---

### Post by rahfin on 2011-01-03
After installing Ubuntu, my laptop hasn't been able to open usb storage devices. First was installed 9.4, now running 10.04 and the problem persists.

After turning the computer on and putting usb drive in, dmesg or lsusb doesn't give any indication of a device available. After "sudo modrpobe usb-storage" dmesg gives continuous error reports but lsusb still doesn't show anything.

dmesg.txt (after modprobe usb-storage)
Putting external hd (self-powered) and a usb flash drive stick in and out of usb slot(s). At one point I did 'modprobe hid' and 'modprobe usbhid' but nothing changed.

Everything else than storage devices work perfectly (mouse, bluetooth, camera etc). A weird note: when a device is plugged in lsusb might show the 3 usb slots as empty but add the plugged device as a fourth one.

Thanks in advance!

---

