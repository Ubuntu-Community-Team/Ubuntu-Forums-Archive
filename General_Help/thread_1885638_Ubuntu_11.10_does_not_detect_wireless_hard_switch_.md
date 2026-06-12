---
title: "Ubuntu 11.10 does not detect wireless hard switch status"
date: 2011-11-23
forum: General Help
---

### Post by zhouzian on 2011-11-23
I'm using a ASUS w7j notebook with hardware wireless switch, which controls wifi and bluetooth. From the early version of ubuntu to the newest version, I alwasy encounter the same problem: 
 
When the hardswitch is turned on, system works normally.
When the hardswitch is turned off before power on, system will automatically start wifi and bluetooth. Now the hardswitch status is swapped, which means on is off, and off is on. But it can still control the status of my wireless devices.
 
Is there any way to detect the wireless hardswitch status in the boot process and set the wifi and bt status? I noticed that before booting into the desktop, the wireless devices are already turned on. So I think there might be something in the kernel controls the status.
 
If the problem is solved, I'll switch to ubuntu:P

---

### Post by zhouzian on 2011-11-23
I've searched a lot, but cannot find similar issues.:confused:

---

### Post by oldtimer7777 on 2011-11-23
> **zhouzian said:**
> I've searched a lot, but cannot find similar issues.:confused:

I would review my BIOS settings if I were you, and see if there isn't an option for that in BIOS.

---

### Post by zhouzian on 2011-11-23
I've reviewed the BIOS, but there is no related options...
Currently, I found it is related to asus-laptop kernel module. If I blacklist it, wifi will not automatically start, but I cannot use shortcut keys either. I want to find a way to use the legacy asus_acpi module, which was not in the kernel anymore.

---

