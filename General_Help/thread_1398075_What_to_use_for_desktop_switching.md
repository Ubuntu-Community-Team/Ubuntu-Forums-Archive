---
title: "What to use for desktop switching"
date: 2010-02-04
forum: General Help
---

### Post by filip007 on 2010-02-04
What to use for desktop switching like ALT+TAB?

I just install Unknown Horizons and the game froze but desktop still working "keyboard lights" is there any way to swtich to desktop or call System Monitor to close not working apps.
[http://www.unknown-horizons.org/site/](http://www.unknown-horizons.org/site/)

---

### Post by kellemes on 2010-02-04
> **filip007 said:**
> What to use for desktop switching like ALT+TAB?

I just install Unknown Horizons and the game froze but desktop still working "keyboard lights" is there any way to swtich to desktop or call System Monitor to close not working apps.
[http://www.unknown-horizons.org/site/](http://www.unknown-horizons.org/site/)

Switch to other terminal.. for example..
Ctrl-Alt-F1
Now you can kill an application like so..
```
killall <appname>
```
Use **top** to find the application that you want to murder.. even better is **htop**, have to install it first.


By the way.. have you tried xkill?
ALT-F2, start xkill at the commandwindow, the mousecursor will change to a skull that will murder a window at touch.

---

### Post by filip007 on 2010-02-04
What is the root password for Ubuntu if any, i like to use reboot option or to get back inside os, startx is not doing anything?

---

### Post by 3rdalbum on 2010-02-04
Press Control-Alt-F7 to get back to your desktop.

Also, if you get blinking keyboard lights, then that indicates a kernel panic, and the only thing you can do is reboot.

---

### Post by kellemes on 2010-02-04
> **3rdalbum said:**
> Press Control-Alt-F7 to get back to your desktop.

Indeed, sorry I forgot to mention.

---

### Post by kantu on 2010-02-04
btw to get to root type ```
sudo su
```

---

### Post by filip007 on 2010-02-04
Thanks lads i better write this down...

CTRL+ALT+F1 for Term
killall (appname)
CTRL+ALT+F7 switch back to desktop
or 
sudo su 
reboot

PS: Is there a list for all running apps, how do i call it?


My MSI G31 board boot so fast so i probably go the faster way with reboot if i get stuck some day ;)

---

### Post by kellemes on 2010-02-04
> **filip007 said:**
> Thanks lads i better write this down...

CTRL+F1 for Term
killall (appname)
CTRL+F7 switch back to desktop
or 
sudo su 
reboot

My MSI G31 board boot so fast so i probably go the faster way with reboot if i get stuck some day ;)

Ctrl-ALT-Fkey

---

### Post by filip007 on 2010-02-04
Fixed already :popcorn:

---

