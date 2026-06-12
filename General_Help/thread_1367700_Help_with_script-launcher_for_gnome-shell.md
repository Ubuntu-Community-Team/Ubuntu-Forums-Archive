---
title: "Help with script-launcher for gnome-shell"
date: 2009-12-29
forum: General Help
---

### Post by bruno9779 on 2009-12-29
I have been trying to make a launcher to enable/disable gnome-shell.
To achieve this I have made a script to check if gnome-shell is running:

```
#!/bin/bash
SERVICE='gnome-shell'

if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    debugexit
else
    gnome-shell --replace
fi
```

Activating gnome-shell when is not found works fine.
Exiting doesn't because "debugexit" should be typed in the Alt+F2 prompt.

Any ideas?

---

### Post by bruno9779 on 2009-12-30
bump

anyone?

---

### Post by Greenwidth on 2009-12-30
er.. not much help, but it works for me (substituting firefox).

---

### Post by Johnny B on 2009-12-30
what is debugexit?
that line should read: "exec killall gnome-shell"

---

### Post by bruno9779 on 2009-12-30
frome gnome-shell documentation, debugexit in alt+f2 prompt closes gracefully gnome-shell, it avoids some apps to break when going back to GDM.

---

### Post by bruno9779 on 2009-12-30
In fact, I have just tried "exec killall" and while it obviously shuts down gnome-shell, it does not restore GDM, and I am now in broken DE, gotta restart x

---

### Post by bruno9779 on 2009-12-30
bump

---

