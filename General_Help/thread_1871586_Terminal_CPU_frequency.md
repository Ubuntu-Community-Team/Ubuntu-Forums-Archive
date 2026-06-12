---
title: "Terminal CPU frequency"
date: 2011-10-29
forum: General Help
---

### Post by aleczandru on 2011-10-29
Hi I am new to Ubuntu and a profesor asked me how can i check the frequency on a CPU threw the terminal.Naturaly beying knew to the OS I dident knew.He also told me to check for the real frequency and for the one used by the manufacturers on there catalog magazines

Can someone pls tell me how this can be done with Ubuntu Terminal?

---

### Post by mcduck on 2011-10-29
This will tell you info about your processor(s), including the frequency they are running.

```
cat /proc/cpuinfo
```

(The frequency is the one the CPU is using *at the moment*, not the max speed. So if you want to know how fast CPU you have you should give it some work to do before running the command to make it step to full speed instead of power saving mode.)

---

