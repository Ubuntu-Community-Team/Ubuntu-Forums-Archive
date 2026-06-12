---
title: "desktop shows /home/user"
date: 2011-08-08
forum: General Help
---

### Post by DrScum on 2011-08-08
I made a new 10.04 install. What I see on the desktop are the contents of /home/<user> and not /home/<user>/desktop as I would expect.

If I create a launcher using the right click > create launcher method the launcher is created in /home/<user>

Is there a way to fix this?

---

### Post by SalHelder on 2011-08-08
Do the following:

1. Install Ubuntu-Tweak

2. Go to Desktop > Preferences of Desktop Icons

3. There see if you have the option "Show content of Home folder in desktop (end session to apply)" checked, if not, check and uncheck.

4. Restart the session.

It should do it.

---

### Post by hyfanious on 2011-08-08
hi
see this file:
```
/home/<user>/.config/user-dirs.dirs
```
be sure that this line is exists:
```
XDG_DESKTOP_DIR="$HOME/Desktop
```

---

### Post by DrScum on 2011-08-08
Thanks for your replies! Editing the /home/<user>/.config/user-dirs.dirs file did it.

---

