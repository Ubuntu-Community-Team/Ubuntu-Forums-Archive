---
title: "In which file can I find the Keyboardshortcuts"
date: 2009-09-12
forum: General Help
---

### Post by murumesch on 2009-09-12
Hi

I'd like to write a script which modifies the keyboart shortcuts. 

Does anyone know in which file you can change the shortcuts?

Murumesch

---

### Post by Brandon Williams on 2009-09-12
Which shortcuts are you looking for? The gnome shortcuts are found in gconf and can be modified from a script using gconftool-2. Other window managers have their shortcuts in other places and are modified using other methods.

---

### Post by pastalavista on 2009-09-12
...

---

### Post by murumesch on 2009-09-13
For example I'd like to create this keyboardshortcut: Ctrl + N   --- creates a new Terminal

I could do it manually with System -> Preferences -> Keyboardshortcuts, but I dlike to do it with a script (a jump-script: the script does all the necassary stuff after a new installation of Ubuntu, i.e.it adds my Alias', Keyboardshortcuts, etc...)

---

### Post by Brandon Williams on 2009-09-13
As I said in my previous message, you can add or remove keyboard shortcuts in gnome with gconftool-2. Open up gconf-editor and explore the keys under /apps/metacity/global_keybindings to start getting a sense of the keys that you would need to add or update.

---

### Post by murumesch on 2009-09-14
Thanks, works just fine! :)

---

