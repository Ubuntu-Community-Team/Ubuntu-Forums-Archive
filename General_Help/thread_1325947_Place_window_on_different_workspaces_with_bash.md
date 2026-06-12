---
title: "Place window on different workspaces with bash?"
date: 2009-11-13
forum: General Help
---

### Post by valros on 2009-11-13
For pure entertainment value, is there a way move a window from process id x to workspace y using something such as bash? Compiz is the window manager if that matters.

---

### Post by diesch on 2009-11-14
Have a look at wmctrl (not installed by default).

---

### Post by valros on 2009-11-14
In this same experiment, I run into the problem of multiple tasks, so is there a way to, from within bash, run a script in another session?

---

### Post by Agent ME on 2009-11-14
You mean like backgrounding some process? If you run a command with an '&' at the end, it runs it in the background, leaving it running while you're at the terminal ("gedit &"). You can the type % followed by its job number to put focus on it (likely to be "%1" for first thing, etc).
Ctrl+Z will stop the currently running process and bring you to terminal. Typing "%<job number> &" will continue it in the background.

---

### Post by valros on 2009-11-15
Adding the ampersand didn't background the process, the process was still running in that terminal.

---

### Post by MaxIBoy on 2009-11-15
Have a look at a program called "devilspie." I think this can do what you want.


By the way, you need "&disown" instead of "&". If you close the terminal, the process doeesn't get killed. If you want to suppress the output, do something like this:
```
command 2>&1 >/dev/null &disown
```
The "2>&1" sends standard error "2" into standard output "1" so that both error messages and normal output will be redirected together into /dev/null, which is where all unwanted data goes to die.

---

