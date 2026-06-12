---
title: "Can't use any packaging management program?"
date: 2009-10-13
forum: General Help
---

### Post by ErikEhlert on 2009-10-13
For some reason, as soon as I start my computer. if I try tp use just about any way to install packages or update them, KPackageManager, GDebi,terminal, they all give me different errors saying another package management program is open causing a problem, I even go into System Activity to close any processes running, I don't know if there is a program open I am unaware about, or if the system thinks something is open. I attempted re-booting, but the program is still "open"...

---

### Post by wojox on 2009-10-13
Run this in the terminal and post the results back out:

```
top -b -n 1 > top.out
```

top.out will show up in your home directory.

---

