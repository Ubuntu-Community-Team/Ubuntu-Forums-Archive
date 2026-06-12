---
title: "Using terminal while processing a program"
date: 2010-04-20
forum: General Help
---

### Post by windlove on 2010-04-20
I am totally new to Ubuntu. I hope I can learn from you guys. 

The current question is, sometimes I start a program from terminal, say gedit. The terminal will be recognized as processing, and I cannot use the same terminal for other tasks until I close the gedit.  

So without opening another terminal, how can I use the terminal while processing the program? 

Thank you. 
Fred

---

### Post by MooPi on 2010-04-20
You can open a tab if your using gnome-terminal, or another terminal program called terminator enables multiple windows or tabs.

---

### Post by sisco311 on 2010-04-20
you can stop a precess with Ctrl+z and start it in the background (foreground) with the bg (fg) commmand.

or start it directly in the background:
```
gedit file **&**
```

---

