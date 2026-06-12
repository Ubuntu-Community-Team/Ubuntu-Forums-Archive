---
title: "Ctrl+Alt+F4"
date: 2010-04-06
forum: General Help
---

### Post by crazyamerican on 2010-04-06
I accidentally pushed control while trying to exit a window (with ALT+F4), and I was dropped into a command shell. Is there anyway to get the normal Ubuntu desktop and such up and running again without restarting?

---

### Post by -humanaut- on 2010-04-06
yeah login to the console do ```
 sudo init 3 
``` then ```
sudo startx
```

---

### Post by mikewhatever on 2010-04-06
Yes, ctrl+alt+7.:)

*sudo startx* should not work, since x is already running.

---

### Post by nem75 on 2010-04-06
> **crazyamerican said:**
> I accidentally pushed control while trying to exit a window (with ALT+F4), and I was dropped into a command shell. Is there anyway to get the normal Ubuntu desktop and such up and running again without restarting?

It is still running. Just hit Alt+F7 and you're back in the graphical terminal where Gnome is running.

> yeah login to the console do
```

 sudo init 3

```
then
```

sudo startx

```

Umm ... no, please don't do that.

---

### Post by -humanaut- on 2010-04-06
oh yeah you shouldn't sudo startx . opps...

---

### Post by nem75 on 2010-04-06
No need to init 3 either. As was said, Gnome is still running in tty7 if you've accidentally switched to a text terminal. ;)

---

