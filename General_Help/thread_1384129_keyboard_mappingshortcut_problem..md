---
title: "keyboard mapping/shortcut problem."
date: 2010-01-18
forum: General Help
---

### Post by alfonz19 on 2010-01-18
Hi, I've made my own keyboard layout. On xubuntu works well without problems. Layout places ISO_Level3_Shift on key, that in most case generates MENU. The key, which displays popupList and which originates from windows.

This behavior occures not everywhere, but only in few applications - thus there has to be some WRONG library. For example firefox, kate (run under gnome) works ok, gedit or psi does not (while the same psi behave correctly under xubuntu).

So, some ubuntu HAS to catch scancode of that useless key and displaying that useless popuplist instead generating what I've requested for. So does anybody here an idea where to order ubuntu NOT to do that? 

Note: keyboard configuration is OK. If I use xev, then when key is pressed  ISO_Level3_Shift is generated correctly.

EDIT: currently I've walked problem around with 
xmodmap -e 'keycode 135=ISO_Level3_Shift'
but I do not think it's a good idea. Because I'm runnig this command automatically after startup presuming the default keyboard is mine modified one. I still would preffer to correct ubuntu behavior.

---

