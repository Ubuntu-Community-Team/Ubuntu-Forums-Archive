---
title: "why no getty?"
date: 2010-11-18
forum: General Help
---

### Post by gregwm on 2010-11-18
lubuntu lucid is installed on both my desktop and my lappy.  mostly everything works.  the installs were via netboot, then apt-get for more stuff, notably lubuntu-desktop, et al.

the lappy is no doubt suffering because it lost power before the netboot completed.  grub never got installed, but no problem, i still have hardy in another partition, and i put an entry for lucid in that grub.

/sbin/getty and /etc/default/console-setup are present and identical on both the desktop and the laptop.  so what could be missing on the laptop that keeps the gettys from getting launched?

---

