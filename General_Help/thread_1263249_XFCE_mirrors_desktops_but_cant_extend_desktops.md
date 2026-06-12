---
title: "XFCE mirrors desktops but cant extend desktops"
date: 2009-09-10
forum: General Help
---

### Post by xjgnsdof on 2009-09-10
I have Ubuntu Server Edition 9.04 (64-bit) with XFCE as the GUI. I connected an external monitor because I use this server for daily tasks and want the benefits of a second desktop.

However, when I go into "Displays," I only have the option to set resolutions and refresh rates. Also, the desktop is always mirrored; I can't choose to extend the desktop to the second monitor. Any ideas?

---

### Post by earthpigg on 2009-09-10
video card?

if nVidia, the solution is as simple as pointing-and-clicking around in the nvidia-settings app and enabling/disabling (can't remember) TwinView.

---

### Post by xjgnsdof on 2009-09-10
lspci returns "Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller" as my video card.

---

### Post by xjgnsdof on 2009-09-12
I have another laptop with an Intel integrated graphics card that allows for extended desktops, but it runs Ubuntu w/ the standard GNOME desktop, not Ubuntu w/ XFCE. Any ideas?

---

### Post by xjgnsdof on 2009-09-12
up

---

### Post by xjgnsdof on 2009-09-12
I switched to GNOME desktop, and I can now extend my desktop to a second display, rather than merely mirror it.

So much for Xubuntu...

---

### Post by earthpigg on 2009-09-12
> **elgilicious said:**
> I switched to GNOME desktop, and I can now extend my desktop to a second display, rather than merely mirror it.

So much for Xubuntu...

gnome stuff frequently works in xfce. have you tried logging back into xfce and running the gnome app that accomplishes the desktop extension?

---

