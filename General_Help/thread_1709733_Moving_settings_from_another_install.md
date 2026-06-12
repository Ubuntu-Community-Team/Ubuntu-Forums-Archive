---
title: "Moving settings from another install?"
date: 2011-03-18
forum: General Help
---

### Post by RobotGymnast on 2011-03-18
I installed a fresh version of Ubuntu on a computer, but I'd like to copy over my settings from my old installation. Where are settings for Gnome (panels and menus) and other applications (chromium, thunderbird, ktorrent, pidgin, skype, code::blocks, amarok) located?

Thanks for any help!

---

### Post by WorMzy on 2011-03-18
In . folders in your home directory.

e.g. Panel info is stored in

~/.gconf/apps/panel

Press Ctrl+H to show hidden files and folders.

Copying over .gconf, .config and .local will get most of gnome-specific settings, other apps may have their own . folders, like firefox uses .mozilla

---

### Post by RobotGymnast on 2011-03-18
Thanks!
Though, this didn't seem to work for chromium.

---

### Post by lithopsian on 2011-03-18
Should be ~/.config/google-chrome

---

### Post by RobotGymnast on 2011-03-18
Yup, that worked; it turned out to be a permissions issue, because

```

sudo chmod -R me:me *

```

Doesn't catch hidden folders.

---

