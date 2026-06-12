---
title: "wicd-curses crashes on &quot;from wicd import dbusmanager&quot;"
date: 2010-12-10
forum: General Help
---

### Post by LuniTux on 2010-12-10
Hello,

I am trying to create a minimal fully functional non-gui ubuntu 9.10 machine. I am finding programs here and there that I can use without a gui such as htop and gpm. The problem is with wicd. when I run
```

sudo wicd-client

Traceback (most recent call last):
  File "/usr/share/wicd/wicd-curses.py", line 52, in <module>
    from wicd import dbusmanager
  File "/usr/share/wicd/dbusmanager.py", line 93, in <module>
    DBUS_MANAGER = DBusManager()
  File "/usr/share/wicd/dbusmanager.py", line 57, in __init__
    self._bus = dbus.SystemBus()
...

```

Similar error for **wicd-curses**. All the errors seem to be based on **from wicd import dbusmanager**. Am I missing a python add-on for wicd?

---

