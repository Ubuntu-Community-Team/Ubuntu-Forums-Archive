---
title: "Screen blanks after 10 minutes"
date: 2011-07-19
forum: General Help
---

### Post by chrisp3047 on 2011-07-19
Hi all,

Since upgrading to 11.04, my screen goes blank if I am not active for 10 mins. This is really annoying if I'm sat on the sofa watching a movie through the computer!

The screensaver is set to 1 hour and the power management settings are set to 'never'. I never had this problem with the previous Ubuntu version. I'm on a desktop rather than a laptop.

Does anyone have any ideas??

Many thanks for all suggestions.

---

### Post by jerrrys on 2011-07-20
you seem to have the screensaver set right, but this still sounds like the problem to me.  next time you watch a movie,  before you watch,  open a terminal and enter:

killall gnome-screensaver

and watch your movie and see what happens...

---

