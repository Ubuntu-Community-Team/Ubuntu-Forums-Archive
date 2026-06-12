---
title: "Lock screen wont work"
date: 2010-02-21
forum: General Help
---

### Post by illbashu on 2010-02-21
Lock screen button does nothing, is there a way to fix this?

---

### Post by NightwishFan on 2010-02-21
Try disabling Compiz, and see if that helps. The only issue I have with locking the screen is that sometimes it wont work if a menu has focus.

---

### Post by raktarok on 2010-02-21
Please have a look at this thread. Hope this solves your problem.

[http://ubuntuforums.org/showthread.php?t=1315471](http://ubuntuforums.org/showthread.php?t=1315471)

---

### Post by illbashu on 2010-02-21
The lock button itself seems to be broken :/ it works when I manually do it by typing in

```
gnome-screensaver-command --lock
```

---

### Post by raktarok on 2010-02-21
What you can do now is make a launcher using that command, and then pin it to the panel. Just right click the panel, go to custom launcher, and then make the launcher. This should serve as a suitable alternative.

I don't know what is wrong with the lock button though, sorry.

---

### Post by W.Y.N.F.S on 2010-03-03
same problem. after update lock screen button does not work, and monitor turns off automatically but i don`t want it to. Now I can`t find where this setting was changed.

---

### Post by johndoe32102002 on 2010-07-08
The Lock Screen button does nothing in Ubuntu 10.04.  Even running the command in terminal fails:
gnome-screensaver-command --lock
** Message: Screensaver is not running!

---

### Post by johndoe32102002 on 2010-07-08
Try this in terminal:
sudo apt-get install libxxf86misc1

This fixed the locking mechanism for me.

---

