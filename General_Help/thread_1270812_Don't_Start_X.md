---
title: "Don't Start X"
date: 2009-09-20
forum: General Help
---

### Post by bconover on 2009-09-20
Okay, well, a while ago I had this all figured out... now I forget again though. Basically, I don't want to run X at startup, or anything graphical (GDM, Gnome). I just want to start up with the command line, and command line login.

I realize I can SWITCH to different levels with Ctrl-Alt-F#, but I want to start in one of these levels, and then be able to manually start X + gnome later if I wished.

There's some file you have to edit and change the runlevel, I forget which one and what commands I'll need to change.

I used to have all this down, but I just need a quick reminder.

I've read some stuff online, and found a file in /etc/event.d called rc-default that might be the answer, however, upon opening it I had no clue which commands to change.

Thanks, this is probably a pretty simple question, and obviously completely possible (since I've done it  before, and from what I recall, fairly painlessly).

---

### Post by jocko on 2009-09-20
To prevent gdm (and x) from starting at boot, run this command:
```
sudo update-rc.d -f gdm remove
```It will remove the links to the init script which starts and stops gdm from all runlevels.

If you decide you want it back:
```
sudo update-rc.d gdm defaults
```And: Ctrl+Alt+Fx does not switch between different runlevels, it just switches between different virtual terminals that are all on the same runlevel (2 by default). To switch to another runlevel, you need to run "sudo init n" (where "n" is 0 (shut down), 1, 2 (default), 3, 4, 5, 6 (reboot) or s (single user mode = root terminal or recovery mode))

---

