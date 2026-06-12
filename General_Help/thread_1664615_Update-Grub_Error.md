---
title: "Update-Grub Error"
date: 2011-01-11
forum: General Help
---

### Post by NMZmaster on 2011-01-11
Yesterday I did a clean install of Ubuntu and made a few changes to /etc/default/grub to set the countdown timer to 0 and hide the grub menu.  After running sudo update-grub, these worked as intended.

Today, I wanted to try to fix grub's resolution (it looked like 640x480 whereas my previous install used my full resolution of 1680x1050), and couldn't figure out how.  I tried setting some things but they did nothing, so I reverted them back to default values.  After running update-grub, I was hit with the following message:


Generating grub.cfg ...
.: 27: Can't open /grub/grub-mkconfig_lib


Now I can't run update-grub at all, regardless of reboots or running grub-install.  Google returned nothing that looked relevant; does anyone have a clue about this?

---

### Post by Habitual on 2011-01-11
Please have a look at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

