---
title: "Wine Is Stuck!"
date: 2009-11-15
forum: General Help
---

### Post by Bubka3 on 2009-11-15
I cant get rid of wine, I uninstalled it but the menu is still here. Rebooted 2 times now.

PIC
[IMG]http://i443.photobucket.com/albums/qq151/bubka3/winewontleave.png[/IMG]

---

### Post by arnab_das on 2009-11-15
type the following:

"sudo apt-get purge wine"

and then the following

"sudo apt-get autoremove"

from the terminal.

also remove all the remnants of wine:

rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine

---

### Post by Bubka3 on 2009-11-15
still here

---

### Post by Bubka3 on 2009-11-15
nvm, last 5 commands worked

---

