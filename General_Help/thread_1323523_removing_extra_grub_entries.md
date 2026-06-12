---
title: "removing extra grub entries"
date: 2009-11-11
forum: General Help
---

### Post by crimius on 2009-11-11
Hi, I'm trying to remove old kernel versions out of my GRUB boot menu, and i see that there should be a file /boot/grub/menu.lst with all the choices, however I don't seem to have it.  any ideas?

---

### Post by fragos on 2009-11-12
If you did a clean install of Ubuntu 9.10 you'll be using GRUB 2 which no longer uses menu.lst. With the original GRUB you could use Synaptic to remove old kernel versions and those would automatically be removed from the boot menu. I'd think that would still work with GRUB 2.

---

