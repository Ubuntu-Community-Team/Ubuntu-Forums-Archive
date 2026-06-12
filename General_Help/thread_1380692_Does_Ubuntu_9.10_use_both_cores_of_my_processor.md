---
title: "Does Ubuntu 9.10 use both cores of my processor?"
date: 2010-01-13
forum: General Help
---

### Post by manco on 2010-01-13
Just a quick question:

It was easy to check in Windows, but I just wanted to know if there's a way to check if Ubuntu is utilizing both cores of my processor (Pentium Core 2 Duo).

Thanks

---

### Post by iponeverything on 2010-01-13
run "htop"

install it with:

```
sudo apt-get install htop
```

---

### Post by lavinog on 2010-01-13
It is supposed to:
go to system>adminstration>system monitor
click the resources tab
you should see a cpu graph with cpu1 and cpu2

---

### Post by manco on 2010-01-13
> **lavinog said:**
> It is supposed to:
go to system>adminstration>system monitor
click the resources tab
you should see a cpu graph with cpu1 and cpu2
Yup, System Monitor shows CPU1 and CPU2;

Thanks!

---

### Post by iponeverything on 2010-01-14
> **lavinog said:**
> It is supposed to:
go to system>adminstration>system monitor
click the resources tab
you should see a cpu graph with cpu1 and cpu2

My only problem with system monitor is that it has such a high cpu utilization all by itself..

---

### Post by lavinog on 2010-01-14
> **iponeverything said:**
> My only problem with system monitor is that it has such a high cpu utilization all by itself..

Yes,  I think it is a feature to ensure your cpu is working ;)
I prefer htop myself.
I wish they would revert back to the old system monitor that didn't focus on pretty graphs so much.

---

### Post by llama320 on 2010-01-14
To get a whole bunch more info about your CPUs you might try the cpufrequtils package
```
sudo apt-get install cpufrequtils
```
After that (you may need to reboot) call
```
cpufreq-info
```

---

### Post by blackened on 2010-01-14
> **manco said:**
> Just a quick question:

It was easy to check in Windows, but I just wanted to know if there's a way to check if Ubuntu is utilizing both cores of my processor (Pentium Core 2 Duo).

Thanks

As an aside: Pentium and Core 2 are two different lines of Intel processors. Hence you have either a Pentium (1, 2, 3, 4, M, or D) or a Core 2 (Solo, Duo, Quad, or Extreme), but not both at once in the same machine.

---

### Post by manco on 2010-01-14
> **blackened said:**
> As an aside: Pentium and Core 2 are two different lines of Intel processors. Hence you have either a Pentium (1, 2, 3, 4, M, or D) or a Core 2 (Solo, Duo, Quad, or Extreme), but not both at once in the same machine.
Duly noted.

I guess I just assumed it had "Pentium" in the name somewhere.

It's an Intel Core 2 Duo processor then ;)

---

### Post by Matt_Johnson on 2010-01-14
it should

---

