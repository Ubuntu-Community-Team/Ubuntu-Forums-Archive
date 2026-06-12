---
title: "Any commands needed in Grub after resizing partition?"
date: 2009-10-26
forum: General Help
---

### Post by [=Vion=] on 2009-10-26
I need to resize my ext3 partition of ubuntu Jaunty Jackalope but Im not sure if I will need to reconfigure the GRUB loader to recognize my new sized partition. For example if I resize and am using LILo then I would need to run sbin/lilo.....

---

### Post by drs305 on 2009-10-26
> **'[=Vion=] said:**
> I need to resize my ext3 partition of ubuntu Jaunty Jackalope but Im not sure if I will need to reconfigure the GRUB loader to recognize my new sized partition. For example if I resize and am using LILo then I would need to run sbin/lilo.....

Unless the UUID changes you won't need to do anything. It shouldn't change for a resizing.

However, after you finish the resizing and before you reboot, you can check the UUIDs with the following commands:
```

sudo blkid -c /dev/null
cat /etc/fstab
cat /boot/grub/menu.lst

```

If the / UUID and the one in menu.lst or fstab don't match, make sure to change the menu.lst/fstab entries before rebooting.

---

