---
title: "Shutdown"
date: 2011-08-24
forum: General Help
---

### Post by Gwaro on 2011-08-24
I get the following message always when shutting down: 

'A program is still running,Unknown Not responding.
Waiting for the program to finish. Interrupting the program 
may cause you to lose your work.'

This is even after closing all running programs.What could be this unknown program?

---

### Post by linkageless on 2011-08-24
Hard to know without looking, if you can run up any kind of terminal at this point or failing that immediately before, it would be useful if you could look at output from ps -ef

Might be a bit long but perhaps by process of elimination you could identify it. I suppose you're looking for something that is a child process of your window manager, definitely not with a PPID of 1 or 2

---

### Post by fdrake on 2011-08-24
try to reconstruct the same error and the post the 
```
dmesg
```

---

