---
title: "Grub - Boot Windows Too"
date: 2012-06-16
forum: General Help
---

### Post by robertlankford on 2012-06-16
This is probably the simpliest thing in the world.  I have Ubuntu 12/04 installed on a hard drive (/dev/sdb).  I am booting from this hard drive into Ubuntu.

I have also added another hard drive to my system that has Windows 7 on it.  It is located at /dev/sda1.  

How can I set up Grub (know nothing about it) so that I can choose which hard drive to boot from?

---

### Post by drs305 on 2012-06-16
> **robertlankford said:**
> This is probably the simpliest thing in the world.  I have Ubuntu 12/04 installed on a hard drive (/dev/sdb).  I am booting from this hard drive into Ubuntu.

I have also added another hard drive to my system that has Windows 7 on it.  It is located at /dev/sda1.  

How can I set up Grub (know nothing about it) so that I can choose which hard drive to boot from?

From your Ubuntu OS just run the following from a terminal:
```
sudo update-grub
```

That should allow GRUB to find Windows and add it to the boot menu.

If it doesn't, try installing and running Boot Repair. See the link in my signature line.

---

