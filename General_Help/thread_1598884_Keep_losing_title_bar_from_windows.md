---
title: "Keep losing title bar from windows"
date: 2010-10-17
forum: General Help
---

### Post by b9k9kiwi on 2010-10-17
Every now and then (that is two or three times a day) the title bar (the one with the exit/minimise/maximise icons on it) disappears from all open windows and any I subsequently open.

The only way to get it back is to reboot.

Not critical, but a nuisance.

Any advice or fix would be appreciated.

Ubuntu 10.10
Fresh install, nVidia drivers activated.

---

### Post by b9k9kiwi on 2010-10-17
Naughty me - I didn't first check if there were other threads on this issue, and there are.

Hope that there is a fix/fixes in them.

Thanks for looking.

---

### Post by Geraba on 2011-01-16
I'm also often having this problem. Is there a fix to it yet? Or is there a simple way to fix it without rebooting or using Ctrl+Alt+Backspace (like killing gnome-window or something)?

---

### Post by stinkeye on 2011-01-16
> **Geraba said:**
> I'm also often having this problem. Is there a fix to it yet? Or is there a simple way to fix it without rebooting or using Ctrl+Alt+Backspace (like killing gnome-window or something)?
For compiz...
alt+F2 and run
```
gtk-window-decorator --replace
```

---

### Post by Geraba on 2011-01-19
> **stinkeye said:**
> For compiz...
alt+F2 and run
```
gtk-window-decorator --replace
```

Thanks, that worked like a charm!
I would like to know... how did you manage to figure that command out? I tried to kill gtk-window-decorator when that happened, but it didn't work...

---

### Post by stinkeye on 2011-01-19
> **Geraba said:**
> Thanks, that worked like a charm!
I would like to know... how did you manage to figure that command out? I tried to kill gtk-window-decorator when that happened, but it didn't work...

If you look in ccsm in the Window Decoration plugin, you'll see this is the command to load the window decorator for compiz.

If you were using emerald as the decorator the command would be **emerald --replace**

Install fusion-icon for a switching menu.
```
sudo apt-get install fusion-icon
```

---

