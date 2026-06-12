---
title: "Startup Manager does not configure Grub with correct default kernel selected."
date: 2011-12-23
forum: General Help
---

### Post by 73ckn797 on 2011-12-23
Running 10.04 and 11.10 (gnome shell Classic).
Using startup manager to reset default kernel. There are 2 11.10 kernels and 4 10.04 kernels listed. The first 2 are for 11.10 and the others are 10.04. I select the latest (37) 10.04 kernel but startup manager selects 4 lines down for kernel 35 recovery mode.

I do not find any bug reports on Launch Pad. I can neither find a way to submit a report.

Any suggestions?

I could edit the Grub config but have not pursued that at this point.

---

### Post by Mahkoe on 2011-12-23
My first suggestion would be to apt-get purge bootup-manager then apt-get install it, but if that doesn't work, just just apt-get purge all the grub packages to remove the configuration files, and apt-get remove bootup-manager, then install the grub packages, and grub-install /dev/sda (or whichever one your disk is). I'm sure it wouldn't be too hard to mess around with the grub configuration without bootup-manager.

Cheers

---

### Post by 73ckn797 on 2011-12-24
I edited /etc/default/grub. It listed the default as 8 when I wanted 6.
Also uninstalled startup-manager from 11.10.

---

