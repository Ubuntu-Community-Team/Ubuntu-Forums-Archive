---
title: "Cairo Dock Problems"
date: 2009-08-05
forum: General Help
---

### Post by epic concept on 2009-08-05
I installed cairo dock but when I try to launch it from the Terminal using cairo-dock it gives the following error   warning : (cairo-dock.c:main:414) couldn't create directory /home/christian/.config/cairo-dock   How do I fix that? BTW I don't have compiz installed I'm running Gnome if that matters.

---

### Post by fabounet on 2009-08-06
a permission issue ?
try sudo chmod -R 777 ~/.config/cairo-dock
how did you install it ?

---

