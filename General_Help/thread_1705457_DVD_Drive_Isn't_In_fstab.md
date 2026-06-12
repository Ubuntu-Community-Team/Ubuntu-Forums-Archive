---
title: "DVD Drive Isn't In fstab"
date: 2011-03-12
forum: General Help
---

### Post by Mark76 on 2011-03-12
Does anyone know why this should be so?

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=97605117-f926-4e1d-abc9-513b8f4c2614 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=dc7cb0a1-2747-47fb-9c61-46e4d836b55d none            swap    sw              0   

DVD drive is sr0 in devices

---

### Post by oldos2er on 2011-03-12
Which version of Ubuntu are you using? I think this is normal behavior in 10.10, not sure about earlier versions.

Is your DVD drive working ok?

---

### Post by psusi on 2011-03-12
It doesn't need to be.

---

### Post by Mark76 on 2011-03-12
> **oldos2er said:**
> Which version of Ubuntu are you using? I think this is normal behavior in 10.10, not sure about earlier versions.

Is your DVD drive working ok?

Yes it is. And I have 10.10.

I'm mostly concerned because I can't unmount mounted CD-Rs. I have to eject them without unmounting.

---

