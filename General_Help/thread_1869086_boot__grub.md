---
title: "boot / grub"
date: 2011-10-25
forum: General Help
---

### Post by Drenriza on 2011-10-25
Hi all.

On my system /boot/grub/menu.1st i have my timeout to 5 seconds.
But when i boot the system, and ends at the grub menu list. Their is no timeout. So i manually need to select what partition to boot from.

It seams that the /boot/grub/menu.1st is being ignored.
So my question is. How can this be ignored? And how can i do so after the timeout on 5 seconds it will select the default boot partition?

Thanks on advance.
Kind regards.

---

### Post by scania_gti on 2011-10-25
[Boot repair disk]("http://sourceforge.net/p/boot-repair-cd/home/Home/") may help you. You can set timeout, boot priority and repair in boot accident.

---

### Post by mcduck on 2011-10-25
Could you post your menu.lst file here? Perhaps there's some error in the file and that causes the setting to be ignored.

...and also note that it's *menu.lst*, not *menu.1st* (with a small "L", not the number "1" ;))

Edit: you should also run "grub --version" to make sure you really are still using the old Grub 0.97. The later Ubuntu releases are, by default, using Grub2 which doesn't even use the menu.lst file and the timeout is configured in /etc/default/grub instead.

---

