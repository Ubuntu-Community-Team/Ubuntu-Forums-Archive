---
title: "Tailing logs - Control the terminal speed"
date: 2009-07-10
forum: General Help
---

### Post by doobiest on 2009-07-10
Does anyone know of a way to watch a log using tail or something tail like, but being able to control the output speed on screen.  Basically backlog/buffer it.  I have some server logs for work that I want to watch basically always. There's to many unknown lines to form a useful grep. I just want this running on an aux. screen and maybe I'll catch something out of the corner of my eye once and a while.

---

### Post by doobiest on 2009-07-10
lol hmm.

tail -f logname|while read line; do echo $line; sleep 1; done

Ya that works, wonder what the memory usage will be like.

Any other ideas though?

---

### Post by t4thfavor on 2009-07-10
watch --interval 10 tail -n 50 log.log

Thats a better way!

---

### Post by geirha on 2009-07-10
Use the pager less.
```
less logfile
```
Hit Shift+F to "tail -f" the logfile, hit Ctrl+C to get back to normal less mode.

---

### Post by doobiest on 2009-07-10
I like the watch solution.  Prior to you replying I ended up doing..

while true; do tail -n 100 log; sleep 10; done

Looks like watch accomplishes the same thing, is easier to execute and is probably more efficient on the system.

Good call on the less example, I remember using it in the past.. I don't know what it is but I just hate less.

---

### Post by LightningCrash on 2009-07-10
I use the KDE File Watcher, it doesn't buffer but it *does* survive logrotates.

I'll test to see if less will survive logrotates in just a second.

ETA: (It doesn't)

---

