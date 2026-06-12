---
title: "System information disabled due to load higher than 1.0"
date: 2011-10-06
forum: General Help
---

### Post by jazzon on 2011-10-06
I occasionallly see this message on a fresh boot and first login to any of my several machines.  Any ideas what it means or what causes it?  I am the only one logged in, and the machine is not reachable to the outside world.

---

### Post by coldraven on 2011-10-06
I downloaded the Ubuntu 10.04 server ready made virtual machine from VirtualBox
[http://virtualboxes.org/images/](http://virtualboxes.org/images/)
It is only for playing with PHP etc. but half the time on bootup I get that message too.
I have no idea why as the server is not connected to anything other than localhost.
Where are the experts? :)

---

### Post by capscrew on 2011-10-06
> **jazzon said:**
> I occasionallly see this message on a fresh boot and first login to any of my several machines.  Any ideas what it means or what causes it?  I am the only one logged in, and the machine is not reachable to the outside world.

This might be informative```
 System load averages is [COLOR="Blue"][B]the average number of processes that are either
       in a runnable or uninterruptable state[/B][/COLOR].  A process in a runnable  state
       is  either  using the CPU or waiting to use the CPU. A process in unin&#8208;
       terruptable state is waiting for some I/O access, eg waiting for  disk.
       The  averages  are  taken over the three time intervals.  Load averages
       are not normalized for the number of CPUs in a system, so [B][COLOR="Red"][B]a load  aver&#8208;
       age  of 1 means a single CPU system is loaded all the time[/B][/COLOR][/B] while on a 4
       CPU system it means it was idle 75% of the time.
```

In a practical sense what the system is telling you is -- *wait I'm busy right now*.

To see a listing of system load use the commands *w* or *top* or (if installed) *htop*.  The last two processes are real time so you can actually watch the load go up if you are watching a video or other  CPU intensive activity.

---

### Post by jazzon on 2011-10-07
LOL...Thanks cap.  So during the boot up the one of the three scan cycles occurs, and the value is stored as > 1.0 so i get that message.  Weird, but understandable now.

---

