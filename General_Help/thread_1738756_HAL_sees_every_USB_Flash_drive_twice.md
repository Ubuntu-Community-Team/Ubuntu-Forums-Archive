---
title: "HAL sees every USB Flash drive twice"
date: 2011-04-25
forum: General Help
---

### Post by GdV87 on 2011-04-25
Hello everybody;
I've recently upgraded from Ubuntu 8.04 to 10.04. My problem is that now HAL sees every USB Flash drive twice. This behavior is specific of USB Flash drives and USB-pluggable Hard Disks, since it doesn't involve CDs or other USB-pluggable devices as printers.
As you can see from the attached output of 'lshal' command, the USB Flash drive named "pendrive" (containing one partition) is listed twice with the same volume uuid.
I've attached also the configuration files of HAL: "preferences.fdi" from "/etc/hal/fdi/policy" and "hal.conf" from "/etc/dbus-1/system.d/".
Could someone help me?
Thank you in advance.

GdV87

---

