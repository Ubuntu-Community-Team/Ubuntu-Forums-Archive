---
title: "Grub editing - What do I edit?"
date: 2011-12-27
forum: General Help
---

### Post by davethewave83 on 2011-12-27
I used the startup disk creator to create a USB startup disk. When Grub is booting it flips an error "vesamenu.c32: Not a COM32R image
boot:" 

when I type "live" and enter, it loads fine. 

I'd like to edit the startup disks startup files to automatically type "live" for me being how I don't know what this error means, or how to correct it otherwise. 

which file would I need to edit?

[solved] i had to edit the linuxsys.cfg and replace the default vesamenu.c32
with default live. it boots now without my intervention

---

