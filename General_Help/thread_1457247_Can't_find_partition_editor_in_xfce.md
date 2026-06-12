---
title: "Can't find partition editor in xfce"
date: 2010-04-18
forum: General Help
---

### Post by drreed on 2010-04-18
unetbootin can't recognize my usb stick for some reason. Last night I made a bootable win98 stick to test it (from freeBSD) and it worked. Today I want to try unetbootin to install Fedora 12 LXDE on that stick, but unetbootin says it can't find the stick, try formatting it to fat32. Other tutorials say to use gparted for this. I can't find gparted, and I don't have a systems>administration menu.

---

### Post by Kai Summers on 2010-04-18
gparted can be found [here]("http://gparted.sourceforge.net/").

---

### Post by klemes on 2010-04-18
Simply install it by typing:

sudo apt-get install gparted

in a console.

---

### Post by sisco311 on 2010-04-18
GParted is in the repositories, click [here]("apt://gparted") to install it or run:
```
sudo apt-get install gparted
```

---

### Post by drreed on 2010-04-18
> **klemes said:**
> Simply install it by typing:

sudo apt-get install gparted

in a console.


I was afraid it would install a lot of other gnome related stuff. I was hoping there was an alternative for xfce. However, it didn't do that thankfully, and the usb is formatted

---

