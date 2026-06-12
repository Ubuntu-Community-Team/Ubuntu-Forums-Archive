---
title: "breezy 3 finger salute how ?"
date: 2006-01-30
forum: General Help
---

### Post by rfruth on 2006-01-30
Every now & then I have a run away program - how can I stop it short of using the reset switch or a power cycle, in Windows there is the good ole three finger salute (Ctrl-Alt-Del) and the Mac has a force quit keyboard short-cut what about Breezy ? (the other day it was a program in the terminal, I saw no way to gracefully exit and the mouse was 'stuck' inside the terminal box ((I couldn't close the window)) and there were no other programs running (so no Alt-Tab) what to do :confused:

---

### Post by kaamos on 2006-01-30
You can just about always press ctrl+alt+F1 and kill processes from there. To kill xmms:
```
killall xmms
```
If you don't know the name of the app you can use the command
```
top
```
or
```
top -u *username*
```
and press "q" and enter the prosess number (pid). The latter command lists only processes started by you.

I think I saw a howto on the forums how to make gnome-system-monitor to open with ctrl+alt+del. Try searching.

---

### Post by Horndog on 2006-01-30
If the Desktop freezes for me, I Ctrl+Alt+F2 to the main prompt and log in and just type "reboot" or "shutdown". It is not a good thing to hit the reset button with any NIX OS.

---

### Post by kaamos on 2006-01-30
But because it is a nix os, there is no need to reboot! :) If your desktop is totally frozen, you can restart the xserver with
```
sudo /etc/init.d/gdm restart
```

---

### Post by C J Pro on 2006-01-30
If the desktop freezes, I find Ctrl+Alt+Backspace useful.

---

### Post by Horndog on 2006-01-30
[QUOTE=kaamos]But because it is a nix os, there is no need to reboot! :) If your desktop is totally frozen, you can restart the xserver with
```
sudo /etc/init.d/gdm restart
```[/QUOTE]

That's good :) But being an old dog with "CRS" disease It is sometimes faster to reboot rather than look for that command.

---

### Post by o_fortuna on 2006-01-30
[QUOTE=rfruth]Every now & then I have a run away program - how can I stop it short of using the reset switch or a power cycle, in Windows there is the good ole three finger salute (Ctrl-Alt-Del) and the Mac has a force quit keyboard short-cut what about Breezy ? (the other day it was a program in the terminal, I saw no way to gracefully exit and the mouse was 'stuck' inside the terminal box ((I couldn't close the window)) and there were no other programs running (so no Alt-Tab) what to do :confused:[/QUOTE]
Also, if you have a terminal process that seems stuck, hit Ctrl and C (the letter key) at the same time. That stops the currently running terminal program.

---

### Post by rfruth on 2006-01-30
Thank U all ! Some of the stuff I had heard of (ctrl+alt+F1, ctrl break. ctrl C)  and some was new to me (top -u username) look out world I've got a handle on things :cool:

---

### Post by ronmarley1 on 2006-01-30
Automatix will conifgure Ctrl-Alt-Del to open the gnome System Monitor (and do a bunch pof other cool stuff!).  Get it here--->[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

---

