---
title: "claws under kubuntu Lucid Lynx has an unreadable display"
date: 2011-07-03
forum: General Help
---

### Post by alanjackson on 2011-07-03
I just upgraded to Lucid (yes I'm a little slow), and now Claws is basically unreadable. Everything else seems to be okay. The text gets replaced with black squares on updates, which can be fixed if I scroll up and back, but then if I select anything, it becomes unreadable again. I have attached a picture.

Running Kubuntu Lucid Lynx 2.6.32-32-generic
Nvidia GeForce 6200 TurboCache(TM)
NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
Claws 3.7.9

Just noticed that gvim is also hosed on its display... sigh.

---

### Post by alanjackson on 2011-07-03
Duhhh.... I found the fix. Simply run :

sudo nvidia-xconfig

to "refresh" the xorg.conf file.

---

### Post by alanjackson on 2011-07-03
Spoke too soon. That fixed the gvim issue, but Claws remains a problem.

---

### Post by alanjackson on 2011-07-04
Fixed it by moving to gnome for my desktop from KDE.

---

