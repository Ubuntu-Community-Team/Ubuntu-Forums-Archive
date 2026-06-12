---
title: "Running terminal commands at startup"
date: 2009-09-01
forum: General Help
---

### Post by TheOneHidalgo on 2009-09-01
The system beep when trying to backspace where there is no text and on system shutdown got really annoying, and the only way I can figure out to stop it is to disable the pc speaker by:

sudo modprobe -r pcspkr

The only problem with this is that I have to type the command every time I turn my computer on.  Is there any way I can get this command to auto-execute on startup?

---

### Post by P4man on 2009-09-01
just dont load it at all. Add it to the blacklist:

```
gksudo gedit /etc/modprobe.d/blacklist.conf 
```

---

