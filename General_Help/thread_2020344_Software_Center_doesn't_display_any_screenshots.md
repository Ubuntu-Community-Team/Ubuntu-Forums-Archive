---
title: "Software Center doesn't display any screenshots"
date: 2012-07-08
forum: General Help
---

### Post by moljac024 on 2012-07-08
I don't think I ever saw screenshots in the software center. It always says "No screenshot available". Note that I am aware that not all packages have screenshots, but I don't see ANY screenshots, even for packages I am sure that have them (i have checked screenshots.ubuntu.com, for instance)

In the past I have used Xubuntu, but now I installed 12.04 from the network install minimal iso and I am not using any desktop environment.

Can this be due to me not using GNOME? Maybe it requires a component of gnome that isn't a dependency to display screenshots?

---

### Post by krustenBrot on 2012-07-08
> I ever saw screenshots in the software center......
>  and I am not using any desktop environment.

Excuse me but how do you open up the software-center without using **any **desktop environment?

---

### Post by krustenBrot on 2012-07-08
Addition: You can check dependencies by installing **apt-rdepends**

typing **apt-rdepends software-center | grep gnome** into a terminal gives the following ouptut:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
  Depends: gnome-icon-theme
  Depends: policykit-1-gnome
  Depends: libgnome-menu-3-0 (>= 3.2.0.1)
libgnome-menu-3-0
  Depends: libsoup-gnome2.4-1 (>= 2.27.4)
libsoup-gnome2.4-1
  Depends: libgnome-keyring0 (>= 2.20.3)
libgnome-keyring0
  Depends: libgnome-keyring-common (= 3.2.2-2)
libgnome-keyring-common
gnome-icon-theme
  Depends: gnome-icon-theme-full
gnome-icon-theme-full
  Depends: gnome-icon-theme (= 3.4.0-0ubuntu1)
  Depends: gnome-icon-theme
  Depends: gnome-keyring
gnome-keyring
policykit-1-gnome

```

So it does depend on some gnome packages / but they should have been installed when installing the software center

---

### Post by moljac024 on 2012-07-08
> **krustenBrot said:**
> .....

Excuse me but how do you open up the software-center without using **any **desktop environment?

Because right now i'm just using a window manager, awesome to be precise.

---

