---
title: "top, command"
date: 2010-11-22
forum: General Help
---

### Post by Drenriza on 2010-11-22
When looking at top, what does all this mean

load average: 0.45, 0.52, 0.49 
What is this, load of total system resources? such as. CPU, hdd, RAM? or just cpu?

Cpu(s):  5.6%us,  3.0%sy,  0.0%ni, 90.9%id,  0.5%wa,  0.0%hi,  0.0%si,  0.0%st
I have in my machine 2 cores. But where in this do i see the load of these 2 cores. And what is 90.9%ID?

hope somebody can shed a little light on this.
Thanks on advance.

---

### Post by pawhtiobo on 2010-11-22
Hi :)

Install **htop**, its an improved version of **top**, it will show you more information and a diferent layout.

see ya..

---

### Post by lmarmisa on 2010-11-22
The command **man uptime** explains the meaning of load averages:

```

uptime gives a one line display of the following information.  The cur&#8208;
rent time, how long the system has been running,  how  many  users  are
currently  logged  on,  and the system load averages for the past 1, 5,
and 15 minutes.

This is the same information contained in the header line displayed  by
w(1).

System load averages is the average number of processes that are either
in a runnable or uninterruptable state.  A process in a runnable  state
is  either  using the CPU or waiting to use the CPU. A process in unin&#8208;
terruptable state is waiting for some I/O access, eg waiting for  disk.
The  averages  are  taken over the three time intervals.  Load averages
are not normalized for the number of CPUs in a system, so a load  aver&#8208;
age  of 1 means a single CPU system is loaded all the time while on a 4
CPU system it means it was idle 75% of the time.


```The command **man top** explains some detalis about the percentages of loads.

If you wish an alternative to the command top, select System -> Administration -> System Monitor.

---

### Post by Drenriza on 2010-11-22
Im using this command on a server.

Well in the top command im most intersted in the
Cpu(s):  90.9%id
from the output of
Cpu(s):  5.6%us,  3.0%sy,  0.0%ni, 90.9%id,  0.5%wa,  0.0%hi,  0.0%si,  0.0%st.

So far i have tried to isolate that part by
```
top |grep id
```but this gives me the output

Cpu(s): 10.1%us,  3.4%sy,  0.3%ni, 85.2%id,  1.0%wa,  0.0%hi,  0.0%si,  0.0%st
anyone know how i can narrow it down to the id part.

I tried
```
top |grep id | awk '{ print $5 }'
```
but that was a no-go.
Hope you know what i mean.

---

### Post by HermanAB on 2010-11-22
Howdy,

It sounds like you should read the man page:
$ man top

oodles of info and special commands there.

---

### Post by mcduck on 2010-11-22
> **Drenriza said:**
> Im using this command on a server.

Well in the top command im most intersted in the
Cpu(s):  90.9%id
from the output of
Cpu(s):  5.6%us,  3.0%sy,  0.0%ni, 90.9%id,  0.5%wa,  0.0%hi,  0.0%si,  0.0%st.

So far i have tried to isolate that part by
```
top |grep id
```but this gives me the output

Cpu(s): 10.1%us,  3.4%sy,  0.3%ni, 85.2%id,  1.0%wa,  0.0%hi,  0.0%si,  0.0%st
anyone know how i can narrow it down to the id part.

I tried
```
top |grep id | awk '{ print $5 }'
```
but that was a no-go.
Hope you know what i mean.

"id" just means "idle", as in "CPU not doing anything". So, there is no process responsible of it, it's just what's left from all the running processes.

10% CPU load = 90% idle.

---

