---
title: "How can you see what's going on in the background while using GUI?"
date: 2010-04-22
forum: General Help
---

### Post by thony971 on 2010-04-22
Hey,

I would like to know what's going on underneath the GUI, is there a tool for me to see what's going on at the command line while using the GUI?

---

### Post by Lepy on 2010-04-22
Launch the program from a terminal, possibly with a -v or --verbose

---

### Post by Calcipher on 2010-04-22
I'm not quite sure I understand what you are asking for, do you want a list of processes running?  If this is the case you can run the Ubuntu task manager (System Menu->Administration->System Monitor) or, from the command line, you can run the command "top" (or watch -n 5 ps -ef).

---

### Post by Ravernomina on 2010-04-22
> **thony971 said:**
> Hey,

I would like to know what's going on underneath the GUI, is there a tool for me to see what's going on at the command line while using the GUI?
 
To see whats running in the background fully use this command
```
top
```

To see what a program is doing while running do this
```
PROGRAMLAUNCHNAME -v
```

gl:D

---

