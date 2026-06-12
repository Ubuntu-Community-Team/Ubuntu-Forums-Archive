---
title: "need help with script for gnome-teminal"
date: 2009-11-08
forum: General Help
---

### Post by WoAnerges on 2009-11-08
i need a scrit like that:

```

gnome-terminal
cd /home/roooot/program/
./program_run -ParameterForProram1 -ParameterForProgram2 -ParameterForProgramn

```
but it openes a new empty terminal and openes program that is hiden.
i need to correct this script so then
it will:
cd to needed dir -> open terminal -> run program in opened terminal.

thank you for reply!

---

### Post by WoAnerges on 2009-11-08
searching for life forms!! Earth, do you copy? (::::

---

### Post by munky99999 on 2009-11-08
> but it openes a new empty terminal and openes program that is hiden.
Well if you execute the say bash script with this in it. The gnome-terminal command opens new terminal. That terminal wont be used. Anything after that likely wont be executed neither. At least I'm pretty sure any command after gnome-terminal isnt going to be run.

My question. Why not simply make a shortcut launcher for this?

---

### Post by dje on 2009-11-08
```
gnome-terminal -x *command*
```
found from:
```
man gnome-terminal
```

---

### Post by WoAnerges on 2009-11-08
> **dje said:**
> ```
gnome-terminal -x *command*
```
found from:
```
man gnome-terminal
```

yes! it work's! ;)

thank you! now i know new command: "man"
^_^

---

