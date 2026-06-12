---
title: "Applets mysteriously vanish from panels"
date: 2010-12-12
forum: General Help
---

### Post by zolushka on 2010-12-12
A friend of mine is running Ubuntu 10.04 LTS.

Applets (indicator applet, main menu, etc.) on his top GNOME panel frequently fail to appear when he logs in, and have to be added manually.

What we've tried:
1) Right-click each applet and check "Lock to Panel".
2) In gconf-editor, set "/apps/panel/global/locked_down" to true.

Neither makes the applets stay put.

I'm running Ubuntu 10.04 LTS as well, and have no such problem. Any ideas on how to solve my friend's problem?

Thanks! :)

---

### Post by zolushka on 2010-12-18
Bump?

---

### Post by susema on 2010-12-18
You can reset panel settings;

```
gconftool-2 --recursive-unset /apps/panel
```

Then log out.

---

### Post by zolushka on 2010-12-18
Will try that and let you know if things stay put - thanks! :)

---

