---
title: "&quot;nice&quot; causing increased CPU time even in the absence of a load"
date: 2010-09-10
forum: General Help
---

### Post by rbpember on 2010-09-10
I've just noticed that "nicing" long running computationally intensive, I/O unintensive, single-threaded executables on my system increases the CPU run time of those executables (as reported by /usr/bin/time as well as by wall clock) by a factor of 2-3 even in the absence of any load, i.e., "top" tells me that my program is getting 100% of a CPU. For example:

--------------------
%coot 248: /usr/bin/time -p ./a.out > out
real 97.47
user 85.64
sys 0.94
%coot 249: nice +4 /usr/bin/time -p ./a.out > out
real 248.31
user 231.94
sys 1.68
%coot 250:
----------------------

My system is running Ubuntu 7.10. If I run the same executable on two other machines I have access to -- one running Fedora 5 and the other Ubuntu 9.10 --  I don't see any discrepancy between the runtimes using nice and not using nice.

This behavior is executable independent, compiler dependent, and language dependent -- I'm seeing it across the board. I'm assuming I've somehow configured my system to behave this way, but I have no idea what I may have done. Also, this was the first time I'd ever done timing runs with "nice" (actually, "at"), so I'm not sure how long my system's been configured (if configured is the right word) this way.


Any suggestions?

---

### Post by dcstar on 2010-09-11
> **rbpember said:**
> I've just noticed that "nicing" long running computationally intensive, I/O unintensive, single-threaded executables on my system increases the CPU run time of those executables
..........
This behavior is executable independent, compiler dependent, and language dependent -- I'm seeing it across the board. I'm assuming I've somehow configured my system to behave this way, but I have no idea what I may have done. Also, this was the first time I'd ever done timing runs with "nice" (actually, "at"), so I'm not sure how long my system's been configured (if configured is the right word) this way.


Any suggestions?

Yes, decide if you want niced processors to be ignored by the CPU throttling or not.

I specifically have my BOINC processes set not to crank up my CPU speed because they are run with nice, so they take longer than on a system which runs the CPU at 100% because of niced processes.

---

### Post by rbpember on 2010-09-13
Thanks! I wasn't sure what you meant by "boinc" but googling 

"cpu throttling" ubuntu 7.10

pointed me to 

[http://ubuntuforums.org/showthread.php?t=762842](http://ubuntuforums.org/showthread.php?t=762842)

I was unfamiliar with the term "throttling", otherwise I would have gotten there earlier.

For me

sudo /etc/init.d/powernowd stop

did the trick.

---

### Post by dcstar on 2010-09-14
> **rbpember said:**
> 
..........
sudo /etc/init.d/powernowd stop

did the trick.
This will show you the simple option to put into /etc/default/powernowd that would have "fixed" the issue without stopping an useful process:
```
man powernowd
```

---

### Post by rbpember on 2010-09-21
Thanks for the suggestion, but for the life of me I can't figure out how
to get powernowd to do what I want, namely, have "nice" make no 
difference to my execution time in the absence of a load if powernowd is
active.

I looked at the man page. The only options my version has that could 
possibly be relevant are:

-n     Include nice'd processes in calculations.
-m     Modes of operation, 0 = SINE, 1 = AGGRESSIVE (default), 2 PASSIVE, 
       3 = LEAPS
-s     Frequency step in kHz (default = 100000)
-p     Polling frequency in msecs (default = 1000)
-u     CPU usage upper limit percentage [0 .. 100, default 80]
-l     CPU usage lower limit percentage [0 .. 100, default 20]

Recall the data I have are:

1) If powernowd is "stopped", "nice" and "no-nice" makes no difference 
   to my execution time.

2) if powernowd is "started", "no-nice" runs at the same speed as case 1, 
   but "niced" runs significantly slower

3) in all cases, "top" reports 100% CPU utilization (of the single
   threaded process)

I initially had no /etc/default/powerenowd, i.e., running with the 
whatever defaults powernowd intrinsically uses, I saw the behavior 
described above.

I tried:

OPTIONS="-n"
       ="-s 1000000"
       ="-u 100 -l 100"
       ="-u 2 -l 1"
       ="-u 100 -l 100 -s 1000000"
       ="-m 2"
       ="-m 3"
       ="-m 0"

In all cases, a "niced" process ran much slower if powernowd was active.

What am I missing or doing wrong? For what it's worth, I am running the powernowd that came with Ubuntu 7.10, which is version 0.97. Acc'g to

[http://www.deater.net/john/powernowd.html](http://www.deater.net/john/powernowd.html)

there shouldn't be any significant difference between what I have and version 1.00

---

