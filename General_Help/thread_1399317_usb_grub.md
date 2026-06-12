---
title: "usb grub"
date: 2010-02-05
forum: General Help
---

### Post by ample on 2010-02-05
i installed grub 1.97 on a usb using:
```
grub-install --no-floppy --root-directory=/mnt/sdb1 /dev/sdb
```
which worked fine. the only problem is that on startup, grub looks for grub.cfg instead of menu.lst, and it drops me into the grub command line. so i ran:
```
grub-mkconfig -o /mnt/sdb1/boot/grub/grub.cfg
```
oddly, it did not create the output file i specified. and it also created grub.cfg based on the boot options of my computer.  so my question is: is it possible to convert a menu.lst into a grub.cfg (a command other than grub-mkconfig that is able to specify an input file as well as an output file)?

btw, since the grub.cfg is so similar to the menu.lst, i was able to simply replace the kernel and initrd lines in grub.cfg with the ones in menu.lst with minor tweaks(changing "kernel" to "linux") and the usb grub menu boots fine now. however, this question is for future reference, since replacing all the kernel and initrd lines for 8 boot choices was a major pain that i do not want to repeat.

---

