---
title: "Can't login to X / Gnome after fiddling with Nautilus"
date: 2010-10-15
forum: General Help
---

### Post by anandamide on 2010-10-15
Haha, I borked my 10.10 upgrade less than an hour after installing it! Love it.

Was following the tips [here]("http://www.omgubuntu.co.uk/2010/10/10-things-to-do-after-installing-ubuntu-10-10-maverick-meerkat/") and installing Nautilus-elementary. After a reboot panel failed to initialize, no desktop shortcuts, and both CPUs were chugging away at 60-90%. Puzzled, I ran htop and for the life of me cannot remember what I saw.

Surmising there was a problem with Nautilus I decided to uninstall / reinstall it (I've never been one for nuance). This got me chucked from the X11 session and I've been unable to get back past gdm since then.

I've uninstalled the Nautilus-Elementary PPA and am now on basic Nautilus, still no luck.

Nothing unusual in /var/log/Xorg.0.log or /var/log/dmesg when I attempt to log in.

---

### Post by anandamide on 2010-10-15
Fixed it - found exactly the solution [here]("http://ubuntuforums.org/showthread.php?t=1432580").

---

