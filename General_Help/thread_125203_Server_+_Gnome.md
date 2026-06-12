---
title: "Server + Gnome"
date: 2006-02-03
forum: General Help
---

### Post by Ubuntuud on 2006-02-03
Hi, I want to reinstall ubuntu, but I was wondering if I could do a server install and then install gnome, just like you install xubuntu.
If you want to know why, I don't need all the auto installed programs an packages.
And if it is possible, what are essential (or just nice) packages? Thanks.

---

### Post by moephan on 2006-02-03
Wouldn't it be easier just to use synaptic to remove the installed programs that you don't want? 

If that doesn't suit, you could look at the packages that the package "ubuntu-desktop" depends on and pickout the ones in there that you think you want, and then use apt-get to install them.

Cheers, Rick

---

### Post by carlosqueso on 2006-02-03
```
sudo apt-get install gnome
``` will probably give you everything you need.   Then you can always poke around in synaptic or apt-cache to get anythings else you need.  A more minimal install of gnome would be ```
sudo apt-get install gnome-desktop-environment
```

---

