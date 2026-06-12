---
title: "Lost xserver and gui...and hope."
date: 2011-11-24
forum: General Help
---

### Post by Alexalad on 2011-11-24
Lately, I've had some issues with the xorg process using 100% of my cpu. So I ended the processes (obviously, in hindsight, it was an incredibly stupid thing to do). As soon as I ended it, my screen went black and turned into a fullscreen terminal. I rebooted a few times, and only have a fullscreen terminal, now. I used the "apt-get remove xserver-xorg" then "apt-get install xserver-xorg".
This outputs "Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"

Startx outputs: 


xauth: /home/*username*/.Xauthority not writable, changes will be ignored
xauth: error in locking authority file /home/user/.Xauthority

exec: 3: /usr/bin/X: not found
giving up.
xinit: no such file or directory (errno 2): unable to connect to X server
xinit: no such process (errno 3): server error.
xauth: error in locking authority file /home/user/.Xauthority

Sudo startx gives the same output.

---

### Post by wolfen69 on 2011-11-24
Try
```
sudo apt-get install xorg
```
you don't need to do *sudo startx*, just *startx*

---

### Post by Alexalad on 2011-11-24
That output a long list of 'failed to fetch' items followed by:
Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

