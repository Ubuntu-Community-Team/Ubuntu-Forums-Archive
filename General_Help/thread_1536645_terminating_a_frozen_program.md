---
title: "terminating a frozen program"
date: 2010-07-22
forum: General Help
---

### Post by agent_509 on 2010-07-22
I was using a program when it froze, and now all I can do is use hotkeys and access a terminal through quake. How can I terminate this program without restarting?

---

### Post by Vaphell on 2010-07-22
from terminal
**killall <program>**
or
**kill <process_id>** (id can be found with **ps ux**, if it's stubborn and doesn't want to be killed, add **-9** after kill)

---

### Post by techunit on 2010-07-22
> **Vaphell said:**
> from terminal
**killall <program>**
or
**kill <process_id>** (id can be found with **ps ux**, if it's stubborn and doesn't want to be killed, add **-9** after kill)

Yep your right just try to put those is code boxes to make them clearer for people to read and understand...

---

### Post by agent_509 on 2010-07-22
I understood just fine, thanks, (now i just have to figure out how to scroll so that I can see all the ids, I hope i dont have to restart)

---

### Post by agent_509 on 2010-07-22
well crud, it froze up even more and then I couldnt do anything period. As much as I hated to (I was in the middle of building a linuxfromscratch system) I had to restart

---

### Post by Vaphell on 2010-07-22
if you want to limit list of processes you can use redirecting the output to another app

```
ps ux | grep <keyword>
```

**ps ux** spits all the stuff to **grep**, which takes that and shows only lines with <keyword>

---

### Post by Tak11 on 2010-07-22
You can also do it graphically with System -> Administration -> System Monitor

Or add a "Force Quit" button to your task bar Right click it -> add to panel -> Force Quit

---

### Post by PhilGil on 2010-07-22
Yet another way to kill a non-responsive program.

Open a terminal and enter ```
xkill
```After your mouse cursor changes to an "x" then click on the window you'd like to kill.

---

