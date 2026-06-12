---
title: "start ubuntu 9.10 without x"
date: 2010-04-15
forum: General Help
---

### Post by false_chicken on 2010-04-15
How can I start ubuntu without x starting? I would like to have x not start by default.

---

### Post by darolu on 2010-04-15
You need to remove (or move to a backup file) the gdm.conf file from your init:
```
$ cd /etc/init/
:/etc/init$ sudo mv gdm.conf gdm.conf-disabled
```
To restore it, simply move the file back:
```
:/etc/init$ sudo mv gdm.conf-disabled gdm.conf
```

---

### Post by melrokz on 2010-04-15
Fine, I'm just curious, what will happen if u do not start x?

---

### Post by false_chicken on 2010-04-15
Thanks:)

---

### Post by wojox on 2010-04-15
> **melrokz said:**
> Fine, I'm just curious, what will happen if u do not start x?

You will be staring at a terminal.

---

### Post by darolu on 2010-04-15
> **melrokz said:**
> Fine, I'm just curious, what will happen if u do not start x?

Press Ctrl+Alt+F1 (ctrl+alt+f7 brings you back) and that's what you would see when you turn the computer on; you log in with your regular username and password and start using your computer; to start the graphical interface run:
```
$ startx
```
[quote=false_chicken]Thanks:D[/quote]
No problem, Debian and Debian based (like Ubuntu) distros are kinda tricky since they start at runlevel 2 by default yet have all services (including X) running, runlevel 2,3,4 and 5 have the exact same services opposed to most distros that start X at init 5.

---

### Post by false_chicken on 2010-04-15
Another quick question. How can i disable the pulsing splash screen when ubuntu is loading? I like to see the text and messages that I see when some other distros are loading.

---

