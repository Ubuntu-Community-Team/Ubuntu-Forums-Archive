---
title: "gconf-editor: more than 10 custom commands?"
date: 2009-08-29
forum: General Help
---

### Post by billdotson on 2009-08-29
Is there a way to have more than 10 custom commands? This should really be possible by default (idea for Ubuntu 9.10 anyone?)

---

### Post by billdotson on 2009-09-01
guess not

---

### Post by enli on 2009-09-01
By default on Ubuntu 9.04 Gnome 2.26.1 I see that there are 12 custom commands. It is possible to have more commands but honestly I don't know what is the limit.

I created new string keys, named them command_13 and run_command_13 and the shortcut worked. So the answer is yes, you can have more than 10 custom commands.

It didn't work with compiz enabled as it supports only 12 commands from CCSM > commands.

**EDIT:** I had to disable compiz by "metacity --replace" to test above.

---

### Post by kerry_s on 2009-09-01
why use gconf-editor to do your shortcuts? you need to look through your preferences menu, theres a tool for keyboard shortcuts.

---

### Post by enli on 2009-09-03
Thats true. But I didn't see any point in creating 10 shortcuts to verify this. Instead I just created two keys - much easier!

---

