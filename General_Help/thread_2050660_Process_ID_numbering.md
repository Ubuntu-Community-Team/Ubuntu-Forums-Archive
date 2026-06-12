---
title: "Process ID numbering"
date: 2012-08-31
forum: General Help
---

### Post by pokerbirch on 2012-08-31
I have a VPS server on which I run a number of Python scripts and have a minor annoyance with how the processes are numbered. For instance, a script which has been running since boot might be PID 825, whereas a recently started script might be PID 2855 (or much higher). I realise that the PIDs are selected sequentially by the OS/Kernel, but am wondering why lower numbers are not being re-used if they are free? It just seems like a waste of several thousand perfectly useable numbers to me. Is there any way to "reset" the count or force PID re-use without re-booting?

```
  PID TTY      STAT   TIME COMMAND
  825 ?        S     81:59 python pnl/manager.pyc --server
 2849 ?        S      0:04 python vb/manager.pyc uk --server
 2870 ?        S      0:00 sshd: birchy@pts/1
 2871 pts/1    Ss     0:00 -bash
 2876 pts/1    R+     0:00 ps x

```

---

### Post by dcstar on 2012-09-01
> **pokerbirch said:**
> I have a VPS server on which I run a number of Python scripts and have a minor annoyance with how the processes are numbered. For instance, a script which has been running since boot might be PID 825, whereas a recently started script might be PID 2855 (or much higher). I realise that the PIDs are selected sequentially by the OS/Kernel, but am wondering why lower numbers are not being re-used if they are free? **It just seems like a waste of several thousand perfectly useable numbers to me.** Is there any way to "reset" the count or force PID re-use without re-booting?
.........

This is a joke, right?

---

### Post by pokerbirch on 2012-09-01
> **dcstar said:**
> This is a joke, right?It was tongue in cheek, yes.

I just wonder why the PIDs don't follow conventional logic and re-use the lowest "free" id. That is assuming that the PID becomes available when a process is closed? Or maybe it doesn't?

---

### Post by Doug S on 2012-09-01
Free PID numbers are re-used. However, only when the cycle repeats. I believe the code exection is more efficient for the way it is done, and minimizing operating system overhead is a priority for the kernel. Example (simple program, called from a script in a loop):```
.
.
.
Elapsed:   0.01 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 32756
Elapsed:   0.00 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 32757
Elapsed:   0.01 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 32758
Elapsed:   0.01 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 32759
Elapsed:   0.00 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 32760
Elapsed:   0.01 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 32761
Elapsed:   0.01 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 32762
Elapsed:   0.00 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 32763
Elapsed:   0.01 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 32764
Elapsed:   0.01 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 32765
Elapsed:   0.00 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 32766
Elapsed:   0.01 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 32767
Elapsed:   0.01 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 300
Elapsed:   0.01 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 301
Elapsed:   0.01 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 302
Elapsed:   0.00 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 303
Elapsed:   0.01 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 304
Elapsed:   0.01 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 305
Elapsed:   0.00 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 306
Elapsed:   0.01 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 307
Elapsed:   0.01 s.  user cpu:      0.00 s.  sys cpu:      0.00 s.  pid = 308
.
.
.
```

---

### Post by pokerbirch on 2012-09-01
So the PIDs are basically a 16-bit integer array which returns to the lowest available number when it hits the upper limit? Makes sense now as it will be working sequentially rather than attempting to search the array every time it needs a new PID.

---

### Post by dcstar on 2012-09-01
> **pokerbirch said:**
> It was tongue in cheek, yes.

I just wonder why the PIDs don't follow conventional logic and re-use the lowest "free" id. That is assuming that the PID becomes available when a process is closed? Or maybe it doesn't?

Processes can die unexpectedly or be terminated leaving orphans, and other processes may have previously recorded that once valid PID and then try to use/end/kill that PID.

If a PID was immediately reused then the chances of another process incorrectly using that PID is far, far greater then allowing the PID list to grow and wrap.

Like so many things in Unix/Linux there are very good reasons for them being that way, but unfortunately too many people "decide" that they know better and want to change things. Your "tongue in cheek" question is far too similar to the many posts you can see in forums like this when dolts decide that a perfectly working system is just not good enough for them and they go and muck up things to fit their view of the world.

---

