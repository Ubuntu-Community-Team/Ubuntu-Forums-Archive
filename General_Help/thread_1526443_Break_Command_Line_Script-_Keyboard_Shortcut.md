---
title: "Break Command Line Script- Keyboard Shortcut"
date: 2010-07-08
forum: General Help
---

### Post by kid1000002000 on 2010-07-08
What is the keyboard shortcut to stop and/or pause the command line while it is in the middle of executing a script?

---

### Post by geirha on 2010-07-08
See [http://mywiki.wooledge.org/BashGuide/JobControl](http://mywiki.wooledge.org/BashGuide/JobControl)

---

### Post by colorlessprism on 2010-07-08
Ctrl+C, should interrupt a running script/program from the terminal. sometimes it is necessary to switch to a tty (CTRL+ALT+F2) type: ```
ps aux
```
at the bottom of the processes list should be the process your looking for. it will look somthing like this 
```
tb64      2776 18.3  0.6  45912 12588 ?        Sl   04:09   0:00 gnome-terminal
tb64      2777  0.0  0.0   1984   708 ?        S    04:09   0:00 gnome-pty-helper
tb64      2778 28.5  0.1   5836  3208 pts/0    Ss   04:09   0:00 bash
tb64      2794  0.0  0.0   2712  1068 pts/0    R+   04:09   0:00 ps aux

```
lets say that "gnome-terminal" is the failing process, we would type:
```
 kill 2776
```
if the process is owned by root it will be necessary to use "sudo". when finished you can switch back to your desktop (CTRL+ALT+F7)

---

### Post by kid1000002000 on 2010-07-08
thank you, everyone.

---

