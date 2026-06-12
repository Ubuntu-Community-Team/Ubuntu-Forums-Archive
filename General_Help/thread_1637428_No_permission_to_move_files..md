---
title: "No permission to move files."
date: 2010-12-04
forum: General Help
---

### Post by drazelian on 2010-12-04
Im trying to move some files from my desktop to /usr/share/ProjectM
Project M is a visualization program, and Im trying to move some presets I downloaded there. 

The error I get is 
```
There was an error moving the file into /usr/share/projectM/presets.
Error moving file: Permission denied
```I am logged in as administrator, why can't I move these files?

---

### Post by drazelian on 2010-12-04
bump

---

### Post by Frogs Hair on 2010-12-04
To open nautilus as root , type   gksudo nautilus   in the terminal.

---

### Post by matt_symes on 2010-12-04
Hi

Press Alt F2 and type 

gksudo nautilus

to open nautilus as root. Close as soon as you have finished moving the files.

Kind regards

---

### Post by drazelian on 2010-12-04
worked perfect! Thanks!

---

### Post by karthick87 on 2010-12-04
Mark this thread as [COLOR=Red][SOLVED][/COLOR]

---

### Post by bookcrazy on 2011-02-13
Worked perfectly! Thanks a million.

---

### Post by linuxsyst on 2011-02-13
[SIZE="4"]Please Mark The Thread As (Solved)[/SIZE]
At (Thread Tools)

---

