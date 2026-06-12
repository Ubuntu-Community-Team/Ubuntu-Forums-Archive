---
title: "Stopping A process?"
date: 2006-04-05
forum: General Help
---

### Post by Giffin on 2006-04-05
I just started up the Kubuntu live cd, and when I clicked on network options or something similar, it started searching for something and couldn't find it... and didn't stop searching.  Is there an equivilent to the task manager in kubuntu where I can stop a process if its going on forever?

Giffin

---

### Post by gingermark on 2006-04-05
[QUOTE=Giffin]I just started up the Kubuntu live cd, and when I clicked on network options or something similar, it started searching for something and couldn't find it... and didn't stop searching.  Is there an equivilent to the task manager in kubuntu where I can stop a process if its going on forever?

Giffin[/QUOTE]
I haven't used the live CD but if it's anything like a regular install, then use KSystemGuard. You can kill processes from there.

---

### Post by Randomskk on 2006-04-05
if you know the process name, or a part of it:
```
killall processname
```
If it's a root process / started by root, use sudo first:
```
sudo killall processname
```

---

### Post by dawhoo on 2006-04-05
Type  KSysGuard  into the "Run Command" from the start menu

I asked the same question the other day :D

---

