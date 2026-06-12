---
title: "Processor running at 100 percent"
date: 2011-04-05
forum: General Help
---

### Post by dsmo223 on 2011-04-05
I can't figure out why but my processor is running at 100% on all four cores, and the fan is running at max speed. All I did was double click an a.out file created by g++, and it is running at full speed now. Anybody know why this was caused?

[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by Frogs Hair on 2011-04-05
Open the terminal and enter ```
top
``` this will at least identify the offending process/s.

Did this start after an event such as updates or application installation ? You mentioned opening a file , have you opened it before ?

---

### Post by antaios256 on 2011-04-05
it sounds like the a.out file had some type of error run the code top specified by Frogs Hair to find the offending processes - you can from then kill the processes but if you don't know how to identify which processes are required and which are problems post the output for help

---

### Post by seawolf167 on 2011-04-05
IMO *htop *is better than *top*, but thats just me

```
sudo apt-get install htop
```

Lots of things can cause 100% cpu usage, it seems to me like the most common that I run into is a bad printer driver that slowly eats more and more of the cpu, but you'll be able to see the offending program at the top of the list with *htop/top* and kill it.

---

