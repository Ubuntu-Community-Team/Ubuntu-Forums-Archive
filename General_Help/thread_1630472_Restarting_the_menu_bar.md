---
title: "Restarting the menu bar"
date: 2010-11-25
forum: General Help
---

### Post by ntg on 2010-11-25
ok, I m adding this here for future reference cause I lost a long time googling and found no answer to my (solved) problem.

(Notes if you ve lost your menu bar it might be for some other reason, but these will help)
- Alt-F2 will run any program. Use it to run xterm.
- do a ```
ps aux | grep gnome
```to see if your panel is there
- try a ```
gnome-panel --restart
```, amybe you ll get lucky
I was not, it appears the gnome panel was running ok, but my xconf was messed up (was messing with updates), so the screen display was wrong and it was running somewhere in outer space. 
In this case try using ```
gnome-display-properties
``` to set it right. I had to ask for same image in all monitors.

---

