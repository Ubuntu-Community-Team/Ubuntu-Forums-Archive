---
title: "Directional keys in the terminal"
date: 2009-08-09
forum: General Help
---

### Post by amcavoy on 2009-08-09
In the terminal, I tried to use the "up" directional key to display the last command I typed, but this just returned "^[[A".  How do I accomplish this task?

---

### Post by Post Monkeh on 2009-08-09
it'll do that if you hit up while the terminal is executing a command. Do you get that if you open a terminal and press up before anything else?

---

### Post by amcavoy on 2009-08-09
This only happens when I am running a program (PARI, in this case).  When running a program, is there a way to overcome this (or, perhaps another key that will give me the last command typed)?

---

### Post by Post Monkeh on 2009-08-09
> **amcavoy said:**
> This only happens when I am running a program (PARI, in this case).  When running a program, is there a way to overcome this (or, perhaps another key that will give me the last command typed)?
That is standard behavior then. You can only use the up key to initiate the last command when you can actually issue a command (which you can't do when another process  is running) i don't know if there's another way to retrieve the last commands other than by opening a second terminal window, but it won't contain commands issued in the current terminal window until it's closed.

---

### Post by wojox on 2009-08-09
You would have to check man ie 
```
man pari
```
When you start a program like that in a shell you leave the shell and enter the program and on exit you drop back into the shell. Then you can use the up arrow.

---

