---
title: "Show Desktop"
date: 2011-10-29
forum: General Help
---

### Post by jim_deadlock on 2011-10-29
Super+d used to clear my desktop but it's stopped working, where can I reset this shortcut (I can't find anything in ccsm)?

---

### Post by jim_deadlock on 2011-10-31
Anyone?

---

### Post by wman on 2011-10-31
System Setting>Keyboard>Shortcut,Maybe there is any misunderstandings in expression,because i am Chinese~~

---

### Post by Frogs Hair on 2011-10-31
Check Keyboard > Shortcuts , if needed you can add a shortcut if the key binding is not being used for something else .

---

### Post by jim_deadlock on 2011-10-31
OK thanks I'm making some progress now... it appears that show desktop has changed to CTRL+ALT+D but when I select it and press SUPER+D (like it used to be) it won't change. I can live with it as it is I suppose but it would be nice to get it back to the old way.

---

### Post by texadactyl on 2012-03-18
Gnome:
[LIST=1]
[*]Launch gconf-editor from command line.
[*]Navigate: > apps > metacity > global_keybindings.
[*]Edit show_desktop.
[*]Change <Ctrl><Alt> to <Super>.
[/LIST]

Test.

---

### Post by jim_deadlock on 2012-03-18
That's great thanks!

---

