---
title: "Unity 2d mistake"
date: 2011-11-02
forum: General Help
---

### Post by elite4seth on 2011-11-02
I just installed xubuntu onto a partition of my macbook, i looked up a "what to do when you first boot linux" site sincei im just getting started and it tole me to run
**sudo apt-get update**[B]
sudo apt-get install unity-2d


[/B]in the terminal and i was stupid enough not to read it first. It's supposed to change my desktop ( i think) to Unity 2d? But i think i just want to stick with what it originally had 10 minutes ago. my terminal window is open right now with 

IDconfig deferred processing now taking place
Mymacbook~$



Thanks in advance!

---

### Post by infinitybot on 2011-11-02
You can remove unity by
```
sudo apt-get purge unity-2d
```

---

### Post by elite4seth on 2011-11-02
Thank you! im gonna do alot more reading =]

---

### Post by Vaphell on 2011-11-02
you could leave unity-2d with no problem. At the login screen you click that cog icon and choose the desktop environment to be used for your session.

---

### Post by 3rdalbum on 2011-11-02
Merely installing Unity 2D won't do much. You would have to explicitly choose it at the login screen. On Ubuntu you can have both Unities, XFCE, KDE, LXDE and both Gnome 3 shell/fallback simultaneously installed, and just switch between them at the login screen.

---

