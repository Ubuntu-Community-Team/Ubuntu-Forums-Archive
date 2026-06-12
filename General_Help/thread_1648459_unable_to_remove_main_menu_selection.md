---
title: "unable to remove main menu selection"
date: 2010-12-18
forum: General Help
---

### Post by chaos_efphect on 2010-12-18
I have a fresh install of Ubuntu 10.04 and while i was taking a cisco class installed the cisco packet tracker. i have since finished the class and tired to uninstall the software but the icon is still suck in the main menu under the internet section. it will not let me uncheck it or delete it. i have spend about 2 hours trying to find a simple fix and came up dry. Please any help is welcomed.


PS, i have tired checking the /usr/share/applications/ and the /home/username/.local/share/applications/ with no luck.

---

### Post by Dex73 on 2010-12-18
Have you tried System/Preferences/Main Menu yet?

---

### Post by chaos_efphect on 2010-12-18
Yes i have, i hit delete or try to remove the check and noting happens

---

### Post by Dex73 on 2010-12-18
How was it installed?

---

### Post by Krytarik on 2010-12-19
Try re-building the menu-items-cache, in terminal:
```
sudo rm /usr/share/applications/desktop.*.cache
sudo sh -c "/usr/share/gnome-menus/update-gnome-menus-cache /usr/share/applications/ > /usr/share/applications/desktop.${LANG}.cache"

```

---

