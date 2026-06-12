---
title: "sauerbraten occasionally freezing on ubuntu 10.10"
date: 2011-02-24
forum: General Help
---

### Post by jazzerit on 2011-02-24
hi guys, I've got the justice edition of sauerbraten, from the tarball on their website (though I didn't have to compile it). Occasionally, when I run it on multiplayer, a map will freeze it. I can't get to a tty unless I first type alt+sysrq+r to release keyboard control from x. Then, I can do ps aux | grep sauer to find it's pid to kill, yet it still gives nothing on x. I then kill all kde things, do sudo service gdm stop and sudo service gdm start, which gets me back to a usable desktop, but weird things will go wrong, like fonts will be the wrong colour. So, to get it back to normal, I have to restart. Is there any way (preferably without actually killing x) of getting my screen back without restarting? I have an integrated intel graphics card, and sauerbraten normally runs at an allright speed. I doubt that's the problem, but I may be wrong. Any ideas welcome. Thanks!
EDIT:
just in case there is any confusion, I'm running the normal version of ubuntu, but with kde as well as gnome. This is why I stop the gdm service, but talk abou kde.

---

### Post by jazzerit on 2011-02-26
bump

---

### Post by jazzerit on 2011-02-28
bump

---

### Post by jazzerit on 2011-03-11
bump

---

### Post by ankspo71 on 2011-03-16
Hi,
Have you tried suspending KDE's 3D effects before playing Sauerbraten? Alt+Shift+F12 toggles toggles KDE's 3D effects on and off. 
Hope this helps.

---

### Post by jazzerit on 2011-03-16
> **ankspo71 said:**
> Hi,
Have you tried suspending KDE's 3D effects before playing Sauerbraten? Alt+Shift+F12 toggles toggles KDE's 3D effects on and off. 
Hope this helps.
thanks- I'll try that next time I boot into KDE.

---

### Post by jazzerit on 2011-05-28
ok, after an update it hasn't been freezing there, rather it's been freezing right after I load it. I can reload X with ctrl+alt+k, though.

---

