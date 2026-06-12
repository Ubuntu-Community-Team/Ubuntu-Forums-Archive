---
title: "i fear restarting my machine..."
date: 2010-12-09
forum: General Help
---

### Post by jjb945025 on 2010-12-09
(using ver. 10.04-lucid lynx) This is because , at random, Gnome environment will have some kind of problem..leaving me with a black screen, like the terminal but not it,where i can enter my password and thats just about all..there seems to be no way to enter the graphical linux environment.i was forced to wipe the hard drive clean twice because of this and both times i reinstalled lucid lynx.. does anyone know whats going on here? thank you.

---

### Post by Rubi1200 on 2010-12-09
Hi,
what graphics card do you have installed and how much RAM?

Thanks.

---

### Post by WorMzy on 2010-12-09
The black terminal-like screen is a tty. If you get dropped to one at boot time, it's likely because gdm failed to start for some reason. A quick and simple fix would be to just run
```
startx
```
as **_your_** user (*not* as root, e.g. with sudo). That will give you a graphical environment if gdm isn't running, but you won't be able to shut down from it as this method doesn't start a clean consolekit session.

A better solution would be to restart gdm:
```
sudo service gdm restart
```

In the event that gdm crashes again, you should be given an explanation as to *why*, which you can then post here, and we can give you advice on how to fix it.

However, since this happening periodically, I suspect there may be a problem with your harddisk. Can you check the SMART data about it by opening the Disk Utility (Alt+F2, palimpsest, run).

---

