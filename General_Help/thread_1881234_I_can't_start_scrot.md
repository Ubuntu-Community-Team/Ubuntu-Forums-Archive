---
title: "I can't start scrot"
date: 2011-11-15
forum: General Help
---

### Post by wxuyec on 2011-11-15
I want to use scrot to take a screen shot.
but I am tired of start it from bash every time.
so I add an keyboard shortcut of MOD4+j by the gnome-keybinding-properties for
scrot -bs -q 100 '/home/wxuyec/Desktop/%T.png' -e 'eog $f'.
but I found that when I pressed the keys of MOD4+j,
there is nothing happened.
but if I run the command of 
scrot -bs -q 100 '/home/wxuyec/Desktop/%T.png' -e 'eog $f'.
in shell, it does work.
can anybody help me to fix that? Thank you very much.
plus: if I press Alt+F2, and run the same command from there,
it works too.

---

### Post by TeoBigusGeekus on 2011-11-15
Scrot needs to run in a terminal. Change to command to
```
gnome-terminal -e scrot -bs -q 100 '/home/wxuyec/Desktop/%T.png' -e 'eog $f'
```
Change gnome-terminal with whatever terminal you're using.

---

