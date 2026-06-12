---
title: "Update manager"
date: 2009-07-19
forum: General Help
---

### Post by DeMus on 2009-07-19
Every day the update manager pops up and shows me a long list of Linux kernel updates. Since they are all about 2.6.28 kernel version and I already use the 2.6.30 version I don't want them. How can I erase the listings so the next day I won't see them again? Now I have to unmark them all to be able to install other updates.

---

### Post by cosine352 on 2009-07-19
I will say install them. As Jaunty is tested for kernel 2.6.28. you can boot to 2.6.30 from the boot menu. So it could be helpful if you have any problem with the .30 kernel.

---

### Post by DeMus on 2009-07-19
> **cosine352 said:**
> I will say install them. As Jaunty is tested for kernel 2.6.28. you can boot to 2.6.30 from the boot menu. So it could be helpful if you have any problem with the .30 kernel.

The funny thing is: I have a listing of 2.6.28.11, 2.6.28.12 and 2.6.28.13 in my menu.lst file. See here:

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.30-020630-generic
uuid		29453d7e-da32-4a71-8367-766e1eb3fa0a
kernel		/boot/vmlinuz-2.6.30-020630-generic root=UUID=29453d7e-da32-4a71-8367-766e1eb3fa0a ro quiet splash 
initrd		/boot/initrd.img-2.6.30-020630-generic
quiet

title		Ubuntu 9.04, kernel 2.6.30-020630-generic (recovery mode)
uuid		29453d7e-da32-4a71-8367-766e1eb3fa0a
kernel		/boot/vmlinuz-2.6.30-020630-generic root=UUID=29453d7e-da32-4a71-8367-766e1eb3fa0a ro  single
initrd		/boot/initrd.img-2.6.30-020630-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		29453d7e-da32-4a71-8367-766e1eb3fa0a
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=29453d7e-da32-4a71-8367-766e1eb3fa0a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		29453d7e-da32-4a71-8367-766e1eb3fa0a
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=29453d7e-da32-4a71-8367-766e1eb3fa0a ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		29453d7e-da32-4a71-8367-766e1eb3fa0a
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=29453d7e-da32-4a71-8367-766e1eb3fa0a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		29453d7e-da32-4a71-8367-766e1eb3fa0a
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=29453d7e-da32-4a71-8367-766e1eb3fa0a ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		29453d7e-da32-4a71-8367-766e1eb3fa0a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=29453d7e-da32-4a71-8367-766e1eb3fa0a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		29453d7e-da32-4a71-8367-766e1eb3fa0a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=29453d7e-da32-4a71-8367-766e1eb3fa0a ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		29453d7e-da32-4a71-8367-766e1eb3fa0a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

What will happen to this list, what will happen to the Ubuntu installation I have running right now? Will it still run as normally on 2.6.30? Can I uninstall the ones I don't need? If so, how?
Please help.

---

### Post by bodhi.zazen on 2009-07-19
If you are happy with your current kernel, remove linux-generic and all the 2.6.28.* stuff (headers, kernel, etc).

---

