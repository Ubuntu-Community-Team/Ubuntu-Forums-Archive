---
title: "Error when unmounting USB stick"
date: 2010-08-29
forum: General Help
---

### Post by veroslav on 2010-08-29
Hi,

I get the following error each time I try to safely remove the USB stick (by right-clicking on the USB stick icon on the desktop and choosing "Remove safely"):

Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:13.2/usb1/1-1)
SYNCHRONIZE CACHE: synchronize cache(10):  Fixed format, current;  Sense key: Key=9
 Additional sense: Logical unit not ready, cause not reportable
  Info fld=0x0 [0] 
FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: start stop unit: transport: Host_status=0x07 [DID_ERROR]
Driver_status=0x00 [DRIVER_OK, SUGGEST_OK]

FAILED: No such file or directory

It used to work without errors when unmounting the USB from Nautilus window, but now, I get the same error when unmounting from there as well. Is it safe to assume that the stick can be removed even though the error message is displayed? What might be the cause?
Also, I do not have any Nautilus-windows opened nor any applications that are locking any files on the USB stick while removing it.

Thanks.

Kind regards,
Veroslav

---

### Post by veroslav on 2010-08-30
*bump*

---

### Post by veroslav on 2010-09-01
*Last bump*

Appears to be a bug (#551752) but I am just wondering whether it is safe to remove the USB stick after the error message is shown, does anybody knows?

Thank you.

Regards,
Veroslav

---

