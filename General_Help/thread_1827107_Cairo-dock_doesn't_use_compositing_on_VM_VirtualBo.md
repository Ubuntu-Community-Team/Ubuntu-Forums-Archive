---
title: "Cairo-dock doesn't use compositing on VM VirtualBox"
date: 2011-08-17
forum: General Help
---

### Post by VMuser289 on 2011-08-17
When I start GLX-Dock, it was surrounded by a black box. GLX-dock, for whatever reason, will not use compositing, even though I know compositing works, and is enabled. My graphics card is a NVIDIA GeForce 8500GT. I have 3D acceleration enabled, as well as guest additions driver on. My host is Windows 7 Home, and my guest OS is Ubuntu 10.10. Is it Cairo dock acting up, or is compiz doing something? I wouldn't want to use fake compositing, because it gets ugly.


Thank you in advance.

---

### Post by MG&amp;TL on 2011-08-17
IDK, but if it helps, it don't work on mine either. 

You realise that the graphics card doesn't seem to be the same card in the VM? I don't have to install a driver for my pc, (on Vbox) even though I usually have to... Just a quick gotcha, you say you know compositing works...is that on windows or on the VM? Compiz should have compositing enabled by default, so I'm guessing you're falling back to metacity.

[http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/]("http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/")

---

### Post by VMuser289 on 2011-08-17
Let me see if that works... I know Cairo dock primarily uses compiz, but it might also use metacity for compositing.

---

### Post by VMuser289 on 2011-08-17
Eh, already have it enabled on metacity, as well as compiz. I do know I  use the desktop cube and I tried docky, so it is probably cairo dock's  fault.:neutral:

---

