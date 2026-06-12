---
title: "Error encountered with kernel compilation."
date: 2006-02-23
forum: General Help
---

### Post by genyue on 2006-02-23
Hi,
 
 I'm new to kernel compilation, and fairly new to Linux (been playing with it for about a month and have a rough idea of how it works).
         
 Anyway, I've managed to compiled a kernel, build the modules, and make an 'initrd' image (yes, all done successfully).
 
 -
 Here are the configurations (Grub) for booting Kubuntu with the kernel:
 ```

title   Kubuntu kernel test
root   (hd0,0)
kernel   /bzImage-2.6.12 root=/dev/sda6 ro
initrd   /initrd-2.6.12.img
boot
 
```
 -
 
 Oh yeah, I have placed "System.map-2.6.12" in the same directory with the kernel and initrd as well.
 
 As for my partition setup:
         
 /dev/sda1 <-- mounted to "/boot" (ext3 filesystem)
 /dev/sda6 <-- installation for Kubuntu, mounted as "/" (reiser filesystem)

When the kernel try to load the modules, ".../lib/modules/2.6.12/modules.dep not found..." was printed as the error message, and 'kernel panic' after that.

The file "modules.dep" is assured to be existing in that directory by myself (which is at /dev/sda6). I even tried to copy the folder to my /boot folder, but it still doesn't detect "modules.dep".
 
 I hope enough information is provided, if not, please let me know what other information which is required.

---

