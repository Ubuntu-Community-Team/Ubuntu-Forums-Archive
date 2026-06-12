---
title: "Tooltips Back to Normal?"
date: 2010-06-13
forum: General Help
---

### Post by Joseph Schwenker on 2010-06-13
I am using the latest Elementary gtk, metacity, and icon themes from the Elementary repository, and I HATE the transparent tooltips.  How can I change them back to how they were in Ubuntu 9.10?  The nice, non-transparent, Mac-like ones?  Additionally, Elementary-Monochrome messes up the Weather applet on my dock.  How can I get the regular, colored weather icons back?

---

### Post by Joseph Schwenker on 2010-06-13
I have found some success by editing /usr/share/themes/elementary/gtk-2.0/gtkrc.  I opened it with gedit running in root, and searched for "tooltip".  For the first listed values, I changed #000 to #FFF.  Then, I changed new-tooltip-style to 0.  I then saved and reapplied the theme.  The tooltips were no longer transparent, and I was able to specify my own color in the Appearance settings.  I'm still trying to figure out how to get rid of the gradient.

---

