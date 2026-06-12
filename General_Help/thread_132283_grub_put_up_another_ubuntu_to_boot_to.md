---
title: "grub put up another ubuntu to boot to"
date: 2006-02-18
forum: General Help
---

### Post by KansasJoe on 2006-02-18
I just installed ubuntu after fighting a few debootstrapper errors and nvidia configures but finally got it to work after a couple of hours...here's my problem now - i did synaptic update and all of a sudden there's two ubuntu's and two ubuntu recoveries to boot to instead of the one of each that there should be....don't think it's a big problem just need to know how to get rid of the extra one that came up...thanx

---

### Post by cotcot on 2006-02-18
With the synaptic update you update the kernel. The second ubuntu in the grub menu is the new kernel. This is normal. There is no functional need to change something.

If you do not like to see it in you can uninstall the old kernel or delete the old kernel boot entries in the grub menu (/boot/grub/menu.lst). Be carefull in doing this.

---

