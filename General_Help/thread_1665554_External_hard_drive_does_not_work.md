---
title: "External hard drive does not work"
date: 2011-01-12
forum: General Help
---

### Post by Varian Roy on 2011-01-12
My computer is an HP dv6000. I just installed ubuntu on my laptop but am having a hard time trying to see my external hard drive. I know there's a way to go and install some stuff via the terminal but I'm unsure as to how. Please help!

---

### Post by TeoBigusGeekus on 2011-01-12
Can you post us the output of
```
sudo fdisk -l
```
(-L)

---

### Post by deserthowler on 2011-01-12
Go to one of the menu bars ... the one you want to put the indicator on ... and right click on an empty space on the bar.  Then click on **Add to Panel** and a list will appear.  Find **DiskMounter** and add that to the panel.  It should show the unmounted drives on your computer.

Earl

---

