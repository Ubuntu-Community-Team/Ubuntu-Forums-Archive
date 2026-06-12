---
title: "nouveau color"
date: 2010-08-02
forum: General Help
---

### Post by Finalfantasykid on 2010-08-02
I would use the nouveau driver but the color hue seems to be slightly off.  Is there any way to adjust the hue for the driver in real time(I don't want to have to change values in Xorg.conf the stop x, restart x and see if it worked).  For example the proprietary nvidia drivers have the color settings in nvidia-settings.

---

### Post by utnubuuser on 2010-08-02
xgamma maybe

>  man xgamma

---

### Post by Finalfantasykid on 2010-08-02
Thanks, I'll experiment with that to find the right setting.

Ok, I found out that the problem is actually firefox.  The colours seem to be a little off while I am using nouveau.  Any ideas for that?

[http://img827.imageshack.us/img827/9651/screenshotnb.png](http://img827.imageshack.us/img827/9651/screenshotnb.png)

Notice the beak of tux

EDIT:  Ok I fixed it.  For anyone having this problem, go to about:config in firefox and change gfx.color_management_mode to "0".  This will fix it.

---

