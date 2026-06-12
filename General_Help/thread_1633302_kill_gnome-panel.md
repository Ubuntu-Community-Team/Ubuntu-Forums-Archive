---
title: "kill gnome-panel"
date: 2010-11-29
forum: General Help
---

### Post by shoot2kill on 2010-11-29
Hi, i have recently configured my install to use only AWN for the launchers/panels and was wondering how i can remove the last gnome-panel?

each gnome-panel can be deleted by right click and delete, but the last one has this grayed out.

i have tried running 'killall gnome-panel' in terminal, but it either reopens itself straight away or doesnt even kill the process.

i am wanting to stop the process from running on system start up, and have seen a couple of threads mention to change this in the sessions preferences but i am running 10.10 and dont see that option in the preferences menu.

Thanks

---

### Post by Verbeck on 2010-11-29
open  gconf-editor(alt+F2)
 navigate to desktop>gnome>session>required_components>panel and change *gnome-panel *to *avant-window-navigator*

---

### Post by shoot2kill on 2010-11-29
i saw somewhere that said to change the 'gnome-panel' to '' but didnt work. will give a reboot now to try this.

---

### Post by shoot2kill on 2010-11-29
nope, still got an annoying panel! :(

---

### Post by Verbeck on 2010-11-29
still cant delete it?

---

### Post by shoot2kill on 2010-11-29
no, the delete button is greyed out when its the last panel. and it still loads on startup

---

### Post by wojox on 2010-11-29
Look here [Remove ALL Gnome Panels]("http://ubuntuforums.org/showthread.php?t=1444461&page=1")

---

### Post by shoot2kill on 2010-11-29
thanks alot pal. that link worked great. dont know how i missed it first.

---

