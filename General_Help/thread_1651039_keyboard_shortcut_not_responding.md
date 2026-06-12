---
title: "keyboard shortcut not responding"
date: 2010-12-22
forum: General Help
---

### Post by jack_the_lad on 2010-12-22
Hello,

I am experiencing problems with keyboard shortcuts. It started to happen after I installed gnome shell and switched back to gdk. the most annoying part is that every single keyboard shortcut works except the most used one AKA "run a terminal":p 

first I thought it had something to do with shortcuts in compiz but no. I changed the keyboard shortcut for "run a terminal" to something wild like CTRL+SHIFT+ALT+N and it still doesn't work. That command is not doing anything... Can i add my custom commands to keyboard shortcuts and how? How to fix this?

---

### Post by jack_the_lad on 2010-12-22
solved this with xbindkeys.

type in the following command

```
sudo apt-get install xbindkeys xbindkeys-config && xbindkeys --defaults > /home/hrvoje/.xbindkeysrc && xbindkeys-config
```

then add new shortcut for gnome-terminal, it should work

---

