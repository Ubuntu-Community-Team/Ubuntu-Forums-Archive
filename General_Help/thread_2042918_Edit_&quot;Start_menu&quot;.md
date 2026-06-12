---
title: "Edit &quot;Start menu&quot;"
date: 2012-08-15
forum: General Help
---

### Post by skittelsen on 2012-08-15
I have an entry at the top of the menu that is NOT listed in the editor. How can I remove or hide this entry? (Hamradio)

---

### Post by Toz on 2012-08-15
It comes from the extra-xdg-menus package which is installed alongside any one of a number of applications including:
```
$ apt-cache rdepends extra-xdg-menus 
extra-xdg-menus
Reverse Depends:
  arduino
  eagle
  xlog
  pcb-common
  kicad
  gwave
  glfer
  gerbv
  geda-gschem
  geda-gattrib
  fldigi
  arduino

```

Do you have a file called "hamradio.menu" in your ~/.config/menus/application-merged directory? If so, delete it.

Otherwise, the main file exists in /etc/xdg/menus/applications-merged. Using sudo, rename it:
```
sudo mv /etc/xdg/menus/applications-merged/hamradio.menu /etc/xdg/menus/applications-merged/hamradio.menu.BAK
```

You might have to log out and back in again for it to take effect.

---

### Post by skittelsen on 2012-08-16
Thanks, that worked.
I didn't find a copy of the file in the first directory you listed, but in the second one. After renaming it, it was removed from the main menu.

---

