---
title: "Wubi - edit grub menu list"
date: 2010-07-05
forum: General Help
---

### Post by Neo23x0 on 2010-07-05
Hi!

I am using Ubuntu 10 on Wubi for quite a long time now without mayor problems. (Upgraded to 10.04)

No - caused by some hardware problems I have to edit the grub boot menu and add "acpi_irq_nobalance" to my kernel boot options.

I can't find a /boot/grub/menu.lst in my Ubuntu installation. 

How do I change boot menu entries permanently?
I read something about grub4dos. Is that the default way?

Thanks for your help

---

### Post by bcbc on 2010-07-05
edit the /etc/default/grub and add it to the line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` then run ```
sudo update grub
```

see the [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) docs for more info. 

PS the menu.lst is grub-legacy. 10.04 uses grub2 so the menu is now /boot/grub/grub.cfg and it's not advisable to edit it directly as it gets automatically regenerated e.g. when you install a kernel update.

---

### Post by Neo23x0 on 2010-07-05
Thanks a lot!

It worked. 
I haven't had the need to check the new grub2 structure and options.

---

