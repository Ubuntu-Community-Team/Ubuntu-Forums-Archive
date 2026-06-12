---
title: "cpulimit on i7 2600k"
date: 2011-12-14
forum: General Help
---

### Post by hg088 on 2011-12-14
hi

im trying to limit a process to 50% of the total cpu but when i do:

```
cpulimit -p 123 -l 50
```the process just uses like 6%

this is because when a process uses all the cpu, top shows 800%

so according to the cpulimit page i should write something like

```
cpulimit -p 123 -l 400
```in order to use 50% of my cpu

but, cpu limit doesn't allow me to set limits higher than 100%

---

### Post by 3Miro on 2011-12-14
i7 CPUs come with 4 physical cores with hyper-threading, which means that you have 8 logical cores and that is what Linux sees and reports. If you see something like 800%, this means that a process is taking all the power from all 8 cores.

Your command can limit a single-core process to use only 50% of one core. You should look for a way to limit the process to 100% on 4 cores, basically limit the number of threads the program would use. If the program is written in OpenMP there is a way to do that in the code and there may be a way to do that as an environment variable.
 
Also, note that some tools like Lxtasks reports all cores as 100%. This a process that takes only 1/8 cores would be reported as 12.5%. If you are using half of one core, then you are using 6%. Somehow the "cpulimit -p 123 -l 50" makes your program go to single-core mode.

---

