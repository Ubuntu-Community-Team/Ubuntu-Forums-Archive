---
title: "Lost menu icons on upgrade"
date: 2009-11-06
forum: General Help
---

### Post by Fraoch on 2009-11-06
The 9.04 - 9.10 upgrade was the most painless ever.  I even managed to do it remotely because my video card is having hardware issues...

The only problem is that I appear to have lost a lot of menu icons.  These are built-in Ubuntu entries like Preferences - Administration - Help and Support, etc.  See screenshot.

The menu items still work, it's just that the icons are gone.

Any idea how to fix it?

Thank you.

---

### Post by pjbgravely on 2009-11-06
No icons on my fresh install, just in the sub menus, probably it is either how it was designed or a common bug.

Paul

---

### Post by P4man on 2009-11-06
open gconf-editor and browse to /desktop/gnone/interface
Check "menus have icons"

or in system > preferences > appearance > interface
check  show icons in menus

its not a bug Its the result of a decision made by gnome 
If you;re interested in learning why:
edit: wrong link
cant find the long explanation. The short one from gnome release notes:
> 
GNOME menus and buttons have been standardised across all applications to not display icons by default. Menu items with dynamic objects, including applications, files or bookmarks, and devices are the exception and can display an icon. This change will standardise the look and feel of menus and present a cleaner interface to users.
[http://library.gnome.org/misc/release-notes/2.28/](http://library.gnome.org/misc/release-notes/2.28/)

---

### Post by Fraoch on 2009-11-06
Thank you very much!

> **P4man said:**
> open gconf-editor and browse to /desktop/gnone/interface
Check "menus have icons"

This didn't have an immediate effect, I guess you need to restart X.

> or in system > preferences > appearance > interface
check  show icons in menus

Now this did have an immediate effect!  Thanks!

> its not a bug Its the result of a decision made by gnome 
If you;re interested in learning why:
edit: wrong link
cant find the long explanation. The short one from gnome release notes:

[http://library.gnome.org/misc/release-notes/2.28/](http://library.gnome.org/misc/release-notes/2.28/)

Huh.  It just looked wrong, given the nice visual makeover the rest of the icons got.

Thanks again.

---

### Post by P4man on 2009-11-06
Both work instantly and they enable/disable each other. Its the same checkbox, no restart required. You must have clicked the wrong one but hey its solved so who cares :)

---

