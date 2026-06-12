---
title: "How to uninstall Nvidia driver version 195.36.15?"
date: 2010-03-23
forum: General Help
---

### Post by Laxman_prodigy on 2010-03-23
I installed this drivers from Nvidia's site. How to completely remove every traces of this driver?

Please guide me.:)

---

### Post by gradinaruvasile on 2010-03-23
Stop gdm, launch the installer script with sudo and append --uninstall. Then you might remove /etc/X11/xorg.conf if you havent got customised it.

BTW why do you want to uninstall it?

---

### Post by Laxman_prodigy on 2010-03-23
Actually, I don't want to.

I need to install vdpau-enabled packages from "Nvidia Vdpau Team PPA". So just thought to remove this completely since they also have 195 version.

I don't know much; so kinda' nooby thing.:)

---

### Post by Laxman_prodigy on 2010-03-23
[B]"Then you might remove /etc/X11/xorg.conf if you havent got customised it."

[/B]How would I do that?

---

### Post by gradinaruvasile on 2010-03-23
sudo rm /etc/X11/xorg.conf

At the command line.

---

### Post by Laxman_prodigy on 2010-03-23
> **gradinaruvasile said:**
> sudo rm /etc/X11/xorg.conf

At the command line.


Okay, I got it. Thanks:)

---

