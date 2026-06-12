---
title: "Looking for an application"
date: 2011-12-20
forum: General Help
---

### Post by ChimeraMica on 2011-12-20
Hey, nothing complicated. I'm just wondering if there's an application that could find the underlying process in the same way that xkill works to kill applications. I tried a Google search but it's hard to look things like this up. Thank you in advance.

---

### Post by yetiman64 on 2011-12-20
```
man ps
``` For info on "ps", it will list processes running. You can get various info with it by using the switches shown in the man page for it. For example "ps -A" will give a list of all processes running. Btw, ps is a terminal application only (no gui).

---

### Post by ChimeraMica on 2011-12-20
Well yes, I know about ps. I'm looking for something that's to ps what xkill is to kill. This is nice for finding out what process an application is associated with.

---

### Post by yetiman64 on 2011-12-20
> **ChimeraMica said:**
> Well yes, I know about ps. I'm looking for something that's to ps what xkill is to kill. This is nice for finding out what process an application is associated with.Ah, you're looking for a gui app. System Monitor maybe? (you may need to set it up in the preferences to show info you specifically require).

---

### Post by ChimeraMica on 2011-12-20
Yes, a gui application. I want to be able to roll over an application's window, similar to a function in process explorer (procexp.exe) in sysinternals for windows, and have it tell me which process it is, or highlight it in, say, gnome-system-monitor.

---

