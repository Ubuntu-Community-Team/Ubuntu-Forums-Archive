---
title: "A darn frustrated idiot"
date: 2009-12-28
forum: General Help
---

### Post by csbright on 2009-12-28
Alrigth, I am sure this is a simple solution, so take it easy on me boys. 

I am very new to ubuntu, I have some  how installed XCFE desktop and now do not know, how the heck to get rid of it. I can not find any sort of theme manager and do not know where the heck it went so side ways. That's what I get for mindlessly poking around on a saturday afternoon listening to the football game. So can someone please tell me now to change desktops. 

Many thanks 
CS

---

### Post by Mahngiel on 2009-12-28
XCFE is a desktop environment.  If you downloaded it, you ought to still have the default programs

enter a terminal and type
'gconf-editor'

that will pull up the configuration editor.  follow this list on the menu tree:

Dektop > Gnome > Session > Require_Components

there should be three keys, filemanager, panel, and windowmanager

if you want to go back to stock gnome:
change the 'values' of:
filemanager to nautilus
panel to gnome-panel
windowmanager 'metacity'.

then reboot

---

