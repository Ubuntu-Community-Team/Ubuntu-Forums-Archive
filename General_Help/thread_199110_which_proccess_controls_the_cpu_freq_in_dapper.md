---
title: "which proccess controls the cpu freq in dapper?"
date: 2006-06-18
forum: General Help
---

### Post by shdgrao on 2006-06-18
Hi!

Since I installed the latest updates from dapper I can't understand how the system controls the cpu speed. I had always controlled that with powernowd but now it doesn't work as he used to. First of all, is the same if I have powernowd installed and running or not, it seems to be another process controlling the CPU speed but I don't know which one it is. Does anyone know who controls the cpu speed in dapper? I would like to come back to powernowd but I suppose that first of all I have to disable the other program that is controlling my cpu rightnow to let powernowd do his work.

---

### Post by oscar on 2006-06-18
I'm not sure if this is exactly what you are looking for but you can change the frequency from the panel:
Right click on it and go "Add to Panel..." select "CPU Frequency Scaling Monitor". Now in a terminal go:
```
sudo chmod +s /usr/bin/cpufreq-selector
``` and you can select the frequency you want.

---

### Post by caserio on 2006-06-18
Hi, 

[Powernowd]("https://launchpad.net/distros/ubuntu/+source/powernowd/0.97-1ubuntu1") controls the cpu speed.

Did you tweak some system services ?

Did you try cpufreqd ?

---

