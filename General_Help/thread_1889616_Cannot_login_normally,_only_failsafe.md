---
title: "Cannot login normally, only failsafe"
date: 2011-12-01
forum: General Help
---

### Post by Deer Hunter on 2011-12-01
Hello all,

I'm running Ubuntu 10.04, and just recently, I lost the ability to log into Ubuntu normally, only the failsafe mode works.

When I start up the machine, it brings me to the login screen. If I try to login normally, it looks as though it wants to proceed, and flashes the desktop for a second, and then back up comes the login screen again.

This is a very unexpected development, as I have not had any such problems on this computer before. Can anybody help me figure out what's going on here?

Thanks in advance.

Deer Hunter

---

### Post by Deer Hunter on 2011-12-02
Bump for viewability.

---

### Post by Habitual on 2011-12-02
Get to the login screen and switch to Console using Ctrl-Alt-F1 and login as your usual self, then issue these commands...
```

mv .config .config.org
mv .gconf .gconf.org
exit

```
Ctrl-Alt-F7 I believe gets you back to the gui login window.
...try again.

NOTE0: If unsuccessful, we put the .config and .gconf directories back.
NOTE1: This WILL reset your gnome desktop to default values.

---

### Post by Deer Hunter on 2011-12-03
Thank you sir, that seems to have done the trick. Case closed.

---

