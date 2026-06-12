---
title: "Keyboard layout changes no longer working"
date: 2011-11-16
forum: General Help
---

### Post by dave0109 on 2011-11-16
After I installed the system, I modified the keyboard map settings in /usr/share/X11/xkb/symbols/gb, which I do for every release I install.  I tend to modify the "extd" set to add a few other accented characters that I use.

Originally, it all worked (as I recall), but not today and I can't understand why.

If I go to the Settings Manager -> Keyboard -> Layout, I have the 'Use system defaults' checked, and in the greyed out section below, the layout has the right name, that is, it matches the "name[Group1]" in the symbols file.  Yet the extra key maps I added don't work.

I notice that there were a few new language-pack-* updates installed at the weekend as well as some gconf stuff.  May be related.

Any ideas on how to fix?

---

### Post by dave0109 on 2011-11-19
Strange, if I go to the Settings Manager -> Keyboard -> Layout, and then uncheck the 'Use system defaults' option and logout/login, the keyboard settings are then what I would expect.

So why isn't the system picking up the settings in the symbols file then set to 'Use system defaults'?

---

