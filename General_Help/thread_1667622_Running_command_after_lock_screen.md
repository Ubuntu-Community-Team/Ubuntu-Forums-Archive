---
title: "Running command after lock screen"
date: 2011-01-15
forum: General Help
---

### Post by echogene on 2011-01-15
So I have a script that runs from 'Startup Applications'.  That works fine.  However, I also want it to run after I unlock a locked screen such as after suspend or a screensaver.  I have mod3+t as a shortcut to it, but it would be nice if I could get it to run automatically.

---

### Post by necrosymbiont on 2011-02-17
I'm bumping this because I also would like to know how to make a command run after I unlock the screen.

(I would like to use purple-remote to set my Pidgin status to Away when I lock the screen and Available when I unlock...)

---

### Post by necrosymbiont on 2011-02-17
Okay, figured it out. Use a while-loop like so:

```
while [ "`gnome-screensaver-command --query | head -1`" = "The screensaver is active" ]; do
sleep 4
done

# Put here some commands to run after unlocking...
```

---

### Post by bolomas on 2012-07-12
I found better solution:
[http://unix.stackexchange.com/questions/28181/run-script-on-screen-lock-unlock](http://unix.stackexchange.com/questions/28181/run-script-on-screen-lock-unlock)

---

