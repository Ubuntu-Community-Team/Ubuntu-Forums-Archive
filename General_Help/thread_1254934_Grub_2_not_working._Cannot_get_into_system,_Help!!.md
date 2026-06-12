---
title: "Grub 2 not working. Cannot get into system, Help!!!"
date: 2009-08-31
forum: General Help
---

### Post by jac0117 on 2009-08-31
I was trying to upgrade from Intrepid to Jaunty and used the upgrade CD. While upgrading I got an error saying that GRUB could not be installed. It gave me the option to install GRUB 2 instead. I did, but now every time I get to the GRUB 2 screen and try to start Ubuntu I get the following error:

Error 12: Unrecognized device list

I booted with a live CD and restored GRUB Legacy, but when I reboot I still get GRUB 2 and keep getting the same error.

Anybody knows how to fix this?

Thanks for any help.

---

### Post by P4man on 2009-09-01
perhaps you can try changing (or deleting) device.map in /(yourharddisk)/boot/grub from a live cd.

That said, dont expect too much help on grub2 here. Few use it, even fewer know anything about it :s

---

### Post by 1ronlung on 2009-09-01
Normally I'd advise [www.supergrubdisk.org](www.supergrubdisk.org)

Not sure if it's compatible with grub2, but should overwrite it with grub1

---

