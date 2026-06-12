---
title: "/boot getting crowded"
date: 2010-02-14
forum: General Help
---

### Post by flyingsliverfin on 2010-02-14
i like to keep my folders cleaned up a bit. I was poking around a bit after i noticced my grub menu had about 10 different old ubuntu kernels (fixed the menu)

anyway, i noticed that my /boot is looking full:
abi-2.6.28-11-generic           memtest86+.bin
abi-2.6.31-14-generic           System.map-2.6.28-11-generic
abi-2.6.31-15-generic           System.map-2.6.31-14-generic
abi-2.6.31-16-generic           System.map-2.6.31-15-generic
abi-2.6.31-17-generic           System.map-2.6.31-16-generic
abi-2.6.31-19-generic           System.map-2.6.31-17-generic
config-2.6.28-11-generic        System.map-2.6.31-19-generic
config-2.6.31-14-generic        vmcoreinfo-2.6.28-11-generic
config-2.6.31-15-generic        vmcoreinfo-2.6.31-14-generic
config-2.6.31-16-generic        vmcoreinfo-2.6.31-15-generic
config-2.6.31-17-generic        vmcoreinfo-2.6.31-16-generic
config-2.6.31-19-generic        vmcoreinfo-2.6.31-17-generic

grub                         
 vmcoreinfo-2.6.31-19-generic
initrd.img-2.6.28-11-generic    vmlinuz-2.6.28-11-generic
initrd.img-2.6.31-14-generic    vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-15-generic    vmlinuz-2.6.31-15-generic
initrd.img-2.6.31-16-generic    vmlinuz-2.6.31-16-generic
initrd.img-2.6.31-17-generic    vmlinuz-2.6.31-17-generic
initrd.img-2.6.31-19-generic    vmlinuz-2.6.31-19-generic

is it safe to delete some of the older versions? (like maybe from .28-11 to .31-16)

---

### Post by darolu on 2010-02-14
Yes it is completely safe, just keep the two latest ones, doesn't hurt to have one back up kernel. Uninstall from synaptic, to be extra safe.

---

### Post by Satoru-san on 2010-02-14
don't rm, mv to your home folder.

And yes, do keep the 2 latest kernels.


But just incase both kernels become broken you have a backup in your home folder.

---

