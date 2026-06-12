---
title: "Ubuntu Giving Second HDD &quot;sda&quot; Logical Name"
date: 2009-12-27
forum: General Help
---

### Post by jake1017 on 2009-12-27
I have just put a second IDE HDD in my Ubuntu 9.10 box. Ubuntu has given it the logical name /dev/sda, which was originally my SATA HDD name. My SATA is now called /dev/sdb.

Is there a way to safely swap these names around?


Thanks in advance.

---

### Post by taurus on 2009-12-27
Use the UUID for your harddrives.

```
sudo blkid
```

---

### Post by oldfred on 2009-12-27
We have seen many BIOS that insert the IDE drive as the first drive in mixed SATA & PATA configurations. Some BIOS let you choose drive order, but even though mine does for booting my drive order is set by the order they are plugged into the SATA ports.

You can try editing /boot/grub/device.map, but I do not know.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd

---

