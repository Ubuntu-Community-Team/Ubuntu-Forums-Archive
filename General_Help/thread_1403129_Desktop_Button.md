---
title: "Desktop Button"
date: 2010-02-09
forum: General Help
---

### Post by jinjin on 2010-02-09
ok so on ubuntu the desktop button returns you to the desktop, but before it does that, it bring up all the windows that are active (including ones that are minimized already).  for ex, if i have  5 windows and i minimized 3 of them and have two on my screen, and i want to return to the desktop by pressing the desktop button, it would bring up all 5 windows. if i press the desktop button again, THEN it will bring me to the desktop.  

this means that to return to the desktop, i have to press the desktop button twice, which is annoying. in windows xp, you only have the press the desktop button once to get back to the desktop because it does not bring back up all the windows and automatically goes to the desktop.

is there any way i could do this with ubuntu so that i only need to press the desktop button once to return to the desktop?

---

### Post by x33a on 2010-02-09
This never happened to me. Maybe a bug?

try it with the shortcut keys, and see if still happens.
```

ctrl-alt-d
```

---

### Post by jinjin on 2010-02-11
still happens, it brings up all the windows first and i have press desktop again for it to go desktop immediately

---

### Post by x33a on 2010-02-11
Just searched around a bit, and it seems compiz has something to do with it.

Take a look here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/236376](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/236376)

Try disabling Desktop effects (if you have them enabled) and see if the problem goes away.

---

