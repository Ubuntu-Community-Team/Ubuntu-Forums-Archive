---
title: "CPU 3 stuck at nearly 100% - suggestions?"
date: 2010-11-08
forum: General Help
---

### Post by benofoz on 2010-11-08
Dear Ubuntu community,

I recently installed 10.04 and things were going great. Then, all of a sudden my third CPU jumped up to almost 100% usage. Since then I've been experiencing all sorts of slowdowns etc., and my battery time has dropped significantly. I've looked at top and there doesn't seem to be any process that is eating up my computing power. Any suggestions on how to fix this problem?

I'm using a Lenovo X201 with i5 540m processor (with hyperthreading), if that has anything to do with the problem.

Here's my top as of about a minute ago.

```
top - 19:38:21 up 14 min,  2 users,  load average: 0.68, 0.62, 0.40
Tasks: 197 total,   2 running, 195 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.9%us,  1.5%sy,  0.0%ni, 96.5%id,  0.0%wa,  0.1%hi,  0.0%si,  0.0%st
Mem:   3851472k total,  1222652k used,  2628820k free,    75280k buffers
Swap:  2188280k total,        0k used,  2188280k free,   517828k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2676 ben       20   0  166m  59m  18m S    7  1.6   0:36.52 npviewer.bin       
 1048 root      20   0  184m  31m  17m S    5  0.8   0:46.77 Xorg               
 2663 ben       20   0  308m  45m  37m S    3  1.2   0:09.04 chrome             
 2339 ben       20   0  314m  36m 8716 S    1  1.0   0:05.66 compiz             
 2723 ben       20   0  205m  20m  10m S    1  0.5   0:01.39 gnome-terminal     
 2866 ben       20   0  839m  38m  15m S    1  1.0   0:01.82 chrome             
    1 root      20   0 23700 1960 1276 S    0  0.1   0:01.28 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.01 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/2        
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/2     
```

As you can see, CPU 3 is at 96.5% while the others are fine, and no apparent culprit.

Thank you in advance!

---

### Post by TiBaal89 on 2010-11-08
> **benofoz said:**
> As you can see, CPU 3 is at 96.5% while the others are fine, and no apparent culprit.

Hmmm... actually I don't see what you mean.  That appears to indicate your cpu(s) is/are being used rather lightly.  Perhaps one of us is misreading it - can you indicate what portion of that readout makes you think this is occurring?

---

### Post by amauk on 2010-11-08
You're reading the info top displays incorrectly

These numbers are not individual CPU measures,
rather they are per category

```
Cpu(s):  1.9%us,  1.5%sy,  0.0%ni, 96.5%id,  0.0%wa,  0.1%hi,  0.0%si,  0.0%st
```

The numbers mean as follows
1.9% used by user-land processes
1.5% used by system (kernel) processes
0.0% used by user-land processes that have been "niced"
96.5% idle
0.0% of processes are waiting for disk I/O
0.1% of CPU used to process hardware interrupts
0.0% of CPU used to process software interrupts
0.0% of CPU has been "stolen" by the host hypervisor (a virtual machine thing)

---

### Post by TiBaal89 on 2010-11-08
Ah ha!  Yes, that's it... from the top man page:

>    2c. CPU States
       The CPU states are shown in the  Summary  Area.  They  are  always
       shown  as  a  percentage  and are for the time between now and the
       last refresh.

        us  --  User CPU time
          The time the CPU has spent running users'  processes  that  are
          not niced.

        sy  --  System CPU time
          The  time  the  CPU  has  spent running the kernel and its pro&#8208;
          cesses.

        ni  --  Nice CPU time
          The time the CPU has spent running users'  proccess  that  have
          been niced.

        wa  --  iowait
          Amount of time the CPU has been waiting for I/O to complete.

        hi  --  Hardware IRQ
          The  amount  of time the CPU has been servicing hardware inter&#8208;
          rupts.

        si  --  Software Interrupts
          The amount of time the CPU has been servicing  software  inter&#8208;
          rupts.

        st  --  Steal Time
          The  amount  of  CPU  'stolen' from this virtual machine by the
          hypervisor for other tasks (such  as  running  another  virtual
          machine).

---

### Post by benofoz on 2010-11-08
My mistake - I was having the problem and did a restart which seemed to stop it. I assumed the problem would still be occurring and copied the top output without paying attention.

Thank you for the input, regardless of my error.

---

### Post by amauk on 2010-11-08
It was probably npviewer
(which is a wrapper to enable 32bit browser plugins to run on a 64bit system - often used with closed-source plugins like flash)

There are various issues with plugins crashing and causing npviewer to go haywire

If this is indeed the issue, maybe look into the installing the 64bit beta version of flash?

---

### Post by TiBaal89 on 2010-11-08
For future reference, if you'd like to see a breakdown of what's happening on individual cpu's - hit the 'one' key while top is running and it will break that section apart to show each.  Cool feature...

---

