---
title: "How to get X running after ctl+alt+F1"
date: 2011-06-16
forum: General Help
---

### Post by dagoss on 2011-06-16
I have this habit of trying to switch desktops by using ctrl+alt+F1 (or F2 or whatever desktop I'm trying to go to) instead of ctl+alt+left/right. So when I do this and get dropped to CLI, is it possible to get back to the X session I had running? If not to that session, what's the proper way to kill X before bringing it back up?

---

### Post by coldraven on 2011-06-16
Ctrl+Alt+F7 should do it. Works for me in 10.10

---

### Post by mcduck on 2011-06-16
Yep, Ctrl-Alt-F1 to F6 are used for virtual terminals, while Ctrl-Alt-F7 and forward are the running desktop sessions.

---

### Post by nothingspecial on 2011-06-16
Some times you have to press Ctrl-Alt-F8. I think that might be if you restart gdm though.

---

### Post by seawolf167 on 2011-06-16
FYI: if you do have to drop to tty1 because of a graphics problem or something the way to start the x server or restart gdm is below

```
startx
sudo service gdm start|restart|stop
```

---

### Post by dagoss on 2011-06-16
Thanks! That's exactly what I needed to know. Now whenever I try to switch desktops and drop to tty1, I would curse profusely!

---

### Post by Slim Odds on 2011-06-16
Restarting the X server for this reason is a very bad idea. Especially if you had any applications running in the GUI before you went to the CLI. Using Ctrl-Alt-F7 is the way to go.

---

