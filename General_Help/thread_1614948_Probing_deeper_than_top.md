---
title: "Probing deeper than top"
date: 2010-11-06
forum: General Help
---

### Post by Rocket J Squirrel on 2010-11-06
I've been reading that Flash chews up cpu cycles and ram, even when browsers are not onscreen or when tabs with Flash objects don't have focus. 

The top command shows the processes that are using the most cpu cycles, but it doesn't reveal what sub-processes in a process are responsible for the usage. For example, top here shows that firefox-bin is presently using 28% of cpu, but doesn't tell me how much of that is Flash, or what other processes running under or within Firefox make up that total. 

Does anyone know whether Linux has a way to show a little more "under the hood" detail than is available through top?

---

### Post by Enigmapond on 2010-11-06
I installed htop and find it relays a lot more information. Top tends to be limited...

---

### Post by ridetheteapot on 2010-11-06
when your using top you can press 'c' to toggle command lines, which will show you what process is running libflashplayer.so (which is useful for chromium, i dont know about firefox) 'H' will toggle showing threads - 
a nice alternative to top is htop, it's easy to configure and real snazzy ;)

EDIT:

oh and try tree mode with htop, that will show you flash vs other firefox subprocesses in a pretty nice way

---

### Post by Rocket J Squirrel on 2010-11-06
Well, here neither top nor htop seem to break out anything recognizable as Flash. I see plenty of firefox-bins, though.

---

### Post by oldos2er on 2010-11-06
In htop, flash in firefox shows up as "/usr/lib/firefox-3.6.12/plugin-container /home/ann/.mozilla/plugins/libflashplayer.so 31072 plugin true"

---

### Post by Rocket J Squirrel on 2010-11-06
Ah. My screen is not wide enough to show all that. All I can see is

/usr/lib/firefox-3.6.12/plugin-container || < edge of screen.

Is there some way to make the display wrap?

---

### Post by Rocket J Squirrel on 2010-11-06
Wait -- never mind. Right arrow key takes me to end of line.

---

### Post by TSJason on 2010-11-08
I like to simply use "ps" for viewing the full output:

```
ps auxSwwf
```

---

### Post by efflandt on 2010-11-08
If you need a wider terminal try Terminal > 132x24 or 134x43 from menus at top of terminal window.

---

