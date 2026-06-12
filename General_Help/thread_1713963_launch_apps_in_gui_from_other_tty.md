---
title: "launch apps in gui from other tty"
date: 2011-03-24
forum: General Help
---

### Post by Siljrath on 2011-03-24
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2626848](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2626848)
theres a thread asking to issue commands to one tty from another, i'd like to know, if there's a way this can be done without screen, and so that you could issue commands to the gui, from other tty.

surely there's a way to do that, right?

---

### Post by ~Plue on 2011-03-24
if X server is already running,
```
DISPLAY=:0 appname
```

---

