---
title: "allow the process to use a single core processor"
date: 2012-05-03
forum: General Help
---

### Post by sedoyksa on 2012-05-03
Hello have an application that can load the CPU to 400 percent, that is, all the core system at a time. how to set up a process to use only one CPU core
CPU model name: Intel (R) Core (TM) i5 CPU M 450@2.40GHz
Chromium application
  Performance Monitor shows the usage of 400%

---

### Post by jerome1232 on 2012-05-03
AFAIk if the program itself doesn't allow you to control how many threads it uses (chromium is very multithreaded) then there is no external way to control threading. You can however try adjusting the nice value, which will give it a lower cpu priority compared to other processes.

The gui way is to open system monitor, click the processes tab, right click the offending process, and give it a "very low" priority. I am unsure of how much of an affect this will give you so YMMV.

---

### Post by sedoyksa on 2012-05-03
its not a real solution
but i try
thanks

---

### Post by brainwash on 2012-05-03
You can use *taskset* to set the CPU affinity of a process:
```
$ pidof firefox
2039
$ taskset -p -c 2039
pid 2039's current affinity list: 0,1,2,3
$ taskset -p -c 0,1 2039
pid 2039's current affinity list: 0,1,2,3
pid 2039's new affinity list: 0,1
```

This command starts a new Firefox process and runs it on CPU 0:
```
taskset -c 0 /usr/bin/firefox
```

---

### Post by sedoyksa on 2012-05-04
brainwash very nice, thanks

---

