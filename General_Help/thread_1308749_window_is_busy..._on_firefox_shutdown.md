---
title: "window is busy... on firefox shutdown"
date: 2009-10-31
forum: General Help
---

### Post by pickarooney on 2009-10-31
Every time I click on the close button in Firefox I immediately get the message that it's busy or not responding, asking if I want to go ahead with shutting it down. After a couple of seconds it closes anyway. It's a little irritating - why would this message come up straight after clicking close? It could at least give the program a chance to shut down!

Anyone else got this?

---

### Post by Turtle.net on 2009-10-31
I have the same problem, that's why I decided to move to chromium (Epiphany works great also).

---

### Post by lovinglinux on 2009-10-31
It could be an extension executing a script on unload.

Try to start Firefox in safe mode, then close it to see if the problem persists.

```
firefox -safe-mode
```

You could also optimize Firefox databases. See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

