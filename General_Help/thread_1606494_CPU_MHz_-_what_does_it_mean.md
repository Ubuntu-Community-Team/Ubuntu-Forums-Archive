---
title: "CPU MHz - what does it mean?"
date: 2010-10-26
forum: General Help
---

### Post by sim085 on 2010-10-26
Hello, doing a quick search on the Internet I found out that to get the CPU information I need to use the command;

```
cat /proc/cpuinfo
```

Here I get CPU MHz is equal to **1000.000**. However what does this mean? That the CPU is currently running at 1000MHz or that it can run up to 1000MHz? I am asking this because when I switch the computer I get the message (on start-up) that *"CPU clock frequency is 200MHz"*. In Bios I can change this up to 455MHz. Therefore I do not know if the CPU (which should be able to run up to 1GHz) is running at 1000MHz or at just 200MHz!

---

### Post by psusi on 2010-10-26
The cpu is running at 1 GHz, 200 MHz is the front side bus frequency.

---

### Post by sim085 on 2010-10-26
> **psusi said:**
> The cpu is running at 1 GHz, 200 MHz is the front side bus frequency.

I know strictly speaking it is not a linux/ubuntu question; but why would I need to change the front side bus frequency? What I noted was that when I increased this, bios also told me that DDR speed would increase.

---

### Post by psusi on 2010-10-26
> **sim085 said:**
> I know strictly speaking it is not a linux/ubuntu question; but why would I need to change the front side bus frequency? What I noted was that when I increased this, bios also told me that DDR speed would increase.

If you want to overclock.

---

### Post by efflandt on 2010-10-26
CPU MHz in cpuinfo is your current CPU speed.  However, depending upon your CPU, that usually changes dynamically based on load.  For example I think my 3.2 GHz i5 is 2 cores with hyperthreading which appears to be 4 cpus.  Under light load it is cruising at 1.2 GHz:

**grep MHz /proc/cpuinfo**
cpu MHz        : 1200.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000

Under heavier load, that automatically increases:

**grep MHz /proc/cpuinfo**
cpu MHz        : 3201.000
cpu MHz        : 1333.000
cpu MHz        : 3201.000
cpu MHz        : 1200.000

---

