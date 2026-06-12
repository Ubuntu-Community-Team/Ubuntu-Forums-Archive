---
title: "Xterm with commands from terminal"
date: 2011-10-17
forum: General Help
---

### Post by xtremesupremacy3 on 2011-10-17
Hey,

I'm working on a really nice piece of software, but I kinda hit a wall at the final part of it.

I need an xterm session to be run with commands from within the program.

Like for instance, to start Xterm on it's own I would type ```
((xterm &)&)
```

That will run an independant xterm and not require me to finish the xterm session before I can carry on with my program. But here is where I hit the brick wall:

I need it to carry out a certain command, say apt-get install.
What I want it to do is to open an xterm process together with the apt-get command but all not interfere with the rest of the program.
Technically speaking, I can create a bash script and tell it to run that, but that's too quick and dirty.

Anyone able to lend me some advice?

Thanks
Arthur

---

### Post by xtremesupremacy3 on 2011-10-17
I worked it out, and for those who need it in the future, this is what to do:

Let's say you want to start a new xterm session with apt-get install abc from within a terminal and not let the terminal you launched it from be dependant on the closure of the xterm session...ie. That the terminal does not wait for xterm to be finished before you can carry on working in it.

```
((xterm -e "sudo apt-get install abc" &)&)
```

What this does is run the xterm externally and run the command in quotes with it.

Arthur

---

