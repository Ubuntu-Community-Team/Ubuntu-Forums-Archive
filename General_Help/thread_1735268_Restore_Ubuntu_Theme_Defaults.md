---
title: "Restore Ubuntu Theme Defaults"
date: 2011-04-21
forum: General Help
---

### Post by JPS913 on 2011-04-21
Hi:

I installed the Elegant Gnome theme/package and I uninstalled it after about a week of use. Even after reverting back to the ambiance theme, or other themes, I've noticed that some elements of the Elegant Gnome theme have remained (e.g. the panel color and icons in Chrome or after right clicking and the system font). Please see the attached screenshots for examples.

Is there a way to restore the Gnome defaults or Ubuntu system defaults so that everything is as it should be? Thanks

---

### Post by TeoBigusGeekus on 2011-04-21
The manually installed themes should be stored in ~/.themes
Try to rename the folder to something like ~/.themes_messed_up, log out and then in and post back with the result.

---

### Post by JPS913 on 2011-04-21
Hey man, I ran some more google searches for ways to reset the Gnome/Ubuntu theme defaults and I believe this worked.

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

I didn't notice the change immediately, but after logging in and out I noticed that my desktop was basically set back to the way it would be after a fresh install. All my programs are still there, but the panels and theme were all reset.

Thanks for the tip though. I will save it for another time should this method not work again.

---

