---
title: "Change boot load splash screen 12.04"
date: 2012-05-10
forum: General Help
---

### Post by CrusaderAD on 2012-05-10
I installed xubuntu-desktop on top of my standard ubuntu-desktop and the loading screen changed. Anyone know how to switch it back?

---

### Post by ptrost on 2012-05-10
What you would need to do is:

sudo apt-get remove plymouth-theme-xubuntu*

then reboot and you should see the default ubuntu splash.

---

### Post by CrusaderAD on 2012-05-11
Worked perfect, thanks!

---

