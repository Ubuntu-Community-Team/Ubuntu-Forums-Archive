---
title: "Start-up guake with multiple terminal windows open"
date: 2012-05-24
forum: General Help
---

### Post by tbretten on 2012-05-24
Is there a way to start-up guake in such a way that there are serveral terminal windows open? It would be nice to be able to pre-name the individual windows and have them execute separate commands/scripts (such as htop, df inside a never endind for loop ...).
I fear I'd have to look into guake's code itself, rather than being able to do it via the .bashrc and would be pleased much to be proven wrong, here... 

Greetings,
tbretten

---

### Post by stinkeye on 2012-05-24
A script something like this as your guake startup command should work.
```
#!/bin/bash
cd $HOME
sleep 15
guake -n1 --rename-tab=htop -e htop &
sleep 1
guake -s0 &
```
**guake -s0** puts the focus back to the first tab.
Comment out if you want htop tab to have focus.

---

