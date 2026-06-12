---
title: "This is driving me crazy please help!"
date: 2010-05-15
forum: General Help
---

### Post by unbuntunewb on 2010-05-15
In using unbuntu 10.4 I am absolutely clueless on this. I accidentally erased my "panel" and now I cannot minimize windows however they remain open. I have a down arrow, an X and a - on the top of my pages

when I hit the - the page disappears but still stays active, example im on youtube and I hit that expecting to minimize but the page closes and I cannot retrieve it but whatever I was viewing continues to play. when I hit the down arrow the page just kinda shuffles to a different side of the screen and is basically useless.

PLEASE HELP, im so frustrated. 

thank you!

---

### Post by mhgsys on 2010-05-15
open a terminal and type:
```
gconftool-2 --recursive-unset /apps/panel
```
and restart gdm after that

in console (Ctrl+Alt+f1 ,f2, f3, etc) 
log in with your username and password 
type;

```
sudo /etc/init.d/gdm stop
```
```
sudo /etc/init.d/gdm start

```

---

### Post by unbuntunewb on 2010-05-15
What is GDM? I must stress that I have zero knowledge on the operating system outside of firefox

---

### Post by Leinarcane on 2010-05-15
GDM is the GNOME Display Manager, a graphical login program.

Here's some links to help you learn Linux and Ubuntu, that should help you along.
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)
[http://www.ubuntu.com/training/e-learning/desktop](http://www.ubuntu.com/training/e-learning/desktop)
[http://ubuntuclips.org/](http://ubuntuclips.org/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
[http://www.linux.org/lessons/](http://www.linux.org/lessons/)
[http://linuxreviews.org/beginner/](http://linuxreviews.org/beginner/)

---

### Post by Sin@Sin-Sacrifice on 2010-05-15
Shortcut = ```
sudo service gdm restart
```

---

