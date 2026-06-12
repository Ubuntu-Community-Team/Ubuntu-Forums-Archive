---
title: "Themes and Menus"
date: 2006-02-24
forum: General Help
---

### Post by newlinuxuser on 2006-02-24
I was wondering if it was possible to make my ubuntu handle abit more like XP, its just that im new to ubuntu and want to make everything familiar - is there a way i can change the ubuntu logo so it says start? thanks in advance

---

### Post by mcduck on 2006-02-24
Sure. First you need a suitable picture for your start-button. Then right-click on the panel, select 'add to panel' and add 'Main Menu' to your panel. Right-click the Menu Bar (the one with Applications/Places/System) and select 'remove from panel'. Now you should have a single-button menu with Ubuntu logo on your panel. Drag it where you want it. 

Then open Configuration Editor (in System tools/Configuration Editor). Browse to apps/panel/objects and find the one that has 'menu-object' as object_type. Now mark the 'use_custom_icon'-checkbox, and type address to your start-button image to the 'custom_icon'-field. The start menu should change instantly. If it doesn't, log out and back again.

---

