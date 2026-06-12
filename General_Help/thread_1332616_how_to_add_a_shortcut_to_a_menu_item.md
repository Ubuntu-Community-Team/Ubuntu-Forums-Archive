---
title: "how to add a shortcut to a menu item"
date: 2009-11-20
forum: General Help
---

### Post by poikiloid on 2009-11-20
for example, I am using the finance program Gnucash, and want to be able to add shortcut "Cntrl+B" to select the item "Blank Transaction" under the Actions menu.

i realize i can do "Alt+A" then "B" to select it, but that's another key to push every time and i am used OSX where I can assign a keyboard shortcut to any menu item.

anyone know how in ubuntu?

thanks!

---

### Post by adaucourt on 2009-11-20
> **how to add a shortcut to a menu item**
 for example, I am using the finance program Gnucash, and want to be able to add shortcut "Cntrl+B" to select the item "Blank Transaction" under the Actions menu.

i realize i can do "Alt+A" then "B" to select it, but that's another key to push every time and i am used OSX where I can assign a keyboard shortcut to any menu item.

anyone know how in ubuntu?

thanks! 	

System-->Preferences-->Keyboard Shortcuts-->Add

---

### Post by iiretepii on 2009-11-20
> **adaucourt said:**
> System-->Preferences-->Keyboard Shortcuts-->Add

You can also use Compizconfig Settings Manager.

---

### Post by P4man on 2009-11-20
Have you guys read the OP question? Neither approach would work like that, at least i dont see how. If im wrong please elaborate how you would make a shortcut to a specific app's menu item...

---

### Post by diesch on 2009-11-20
Use gconf-editor to set */desktop/gnome/interface/can_change_accels* to true. Then select the menu item you want and press the desired shortcut. Use <DEL> to remove a shortcut.

---

### Post by poikiloid on 2009-11-20
> **diesch said:**
> Use gconf-editor to set */desktop/gnome/interface/can_change_accels* to true. Then select the menu item you want and press the desired shortcut. Use <DEL> to remove a shortcut.

that worked, Diesch. 
thanks!
for anyone else, to clarify: after changing the setting in gconf-editor: hover your mouse pointer over the menu item (or navigate to it with keyboard) and while it is highlighted, push the key combo you want for its shortcut.
and on the specific example i gave, Cntl+B won't work for some reason. But Cntl+Shift+B does, and other things do. I settled on Cntl+Z.

---

### Post by P4man on 2009-11-20
> **diesch said:**
> Use gconf-editor to set */desktop/gnome/interface/can_change_accels* to true. Then select the menu item you want and press the desired shortcut. Use <DEL> to remove a shortcut.

Thats an awesome trick!

---

