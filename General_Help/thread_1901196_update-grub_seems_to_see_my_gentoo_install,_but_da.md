---
title: "update-grub seems to see my gentoo install, but dan richter's Grub Customizer doesn't"
date: 2011-12-28
forum: General Help
---

### Post by sirspazzolot on 2011-12-28
I can boot it manually just fine 
```
>set root=(hd0,8)
>linux /boot/gentoo-linux-3.0.6
>boot
```
but how do I get the entry to actually appear in my grub menu? the osprober seems to see the gentoo install when I run update-grub but there is no mention of it in the grub gui thing and it's not in the boot menu.

should I manually edit something? thanks in advance!

---

### Post by sirspazzolot on 2011-12-28
buuuuh. turns out the stuff in /etc/grub.d/ is really easy. just edited 40_custom, put the three lines between brackets and preceded that with menuentry "gentoo loonix ololol"

solved.

---

