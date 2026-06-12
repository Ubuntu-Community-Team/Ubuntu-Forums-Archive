---
title: "OK, so why batch does not always work?"
date: 2010-05-28
forum: General Help
---

### Post by Mark_Galeck on 2010-05-28
I was trying to understand "batch" command, and I thought perhaps when I am logged in a terminal, in addition to X, there are multiple users, and man page says it is not suitable for multiple users. But then, you could never use batch in a terminal? So not sure...  take a look, at first it works, then it does not.  In this example, I am trying to use "batch" to make (touch) a new file.  And the load is always very low.  

mark@ubuntu:~/foobar$ batch
warning: commands will be executed using /bin/sh
at> touch foobar
at> <EOT>
job 24 at Thu May 27 21:27:00 2010
mark@ubuntu:~/foobar$ ls
foobar
mark@ubuntu:~/foobar$ rm foobar
mark@ubuntu:~/foobar$ ls
mark@ubuntu:~/foobar$ batch
warning: commands will be executed using /bin/sh
at> touch foobar
at> <EOT>
job 25 at Thu May 27 21:27:00 2010
mark@ubuntu:~/foobar$ ls
mark@ubuntu:~/foobar$ uptime
 21:28:10 up  4:06,  2 users,  load average: 0.01, 0.08, 0.16


what is going on??

---

### Post by lavinog on 2010-05-28
I think you need to wait a minute.

---

### Post by jocko on 2010-05-28
You'll probably find the answer in your other thread about the same thing:
> **dcstar said:**
> ... batch only runs when system load is below 1.5, ...

And please don't start new threads when you already have an active thread about the same thing (even if the title of the original thread was misleading).

Edit: Sorry, didn't read the whole first post in this thread. I see you have already considered and probably ruled out the system load thing...
I don't really know anything about batch or uptime, but the loads you see in uptime are averages over the last 1, 5 and 15 minutes, so if you run at a very low load for 58 seconds and then 2 seconds on above 1.5, the average load for the last minute will still be very low, which could mean batch would not run during those two seconds even if the average load looks like it would allow it to run...

---

### Post by Mark_Galeck on 2010-05-28
> **jocko said:**
> 
I don't really know anything about batch or uptime, but the loads you see in uptime are averages over the last 1, 5 and 15 minutes, so if you run at a very low load for 58 seconds and then 2 seconds on above 1.5, the average load for the last minute will still be very low, which could mean batch would not run during those two seconds even if the average load looks like it would allow it to run...

Thank you! Yes I realize these are averages, OK but of course, for the testing purposes, I am not running anything at all (that I know of).  Just typing "batch" in the terminal, as you saw in the pasted session. Nothing else.  At times, the command inside batch (touch) gets executed, at times, does not, sometimes, gets executed later, don't really see any pattern, loads are really light always - nothing else runs.

(Well, maybe this is general Linux or Unix question, not sure, not just Ubuntu behaviour, so maybe I should not post it here?)


Mark

---

### Post by lavinog on 2010-05-28
atd man page might give some insight:
```


       -l      Specifies  a limiting load factor, over which batch jobs should
               not be run, instead of the compile-time choice of 1.5.  For  an
               SMP  system  with  n  CPUs,  you will probably want to set this
               higher than n-1.

       -b      Specify the minimum interval in seconds between  the  start  of
               two batch jobs (60 default).

```

A second job must wait at least 60 seconds before starting regardless of the load.

---

