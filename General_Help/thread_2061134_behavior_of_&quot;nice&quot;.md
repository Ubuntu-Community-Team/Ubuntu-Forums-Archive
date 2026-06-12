---
title: "behavior of &quot;nice&quot;"
date: 2012-09-21
forum: General Help
---

### Post by thk on 2012-09-21
I am testing some heavy loads on a server to see if I can get some processes to back off using "nice". The machine has 16 virtual cores. It appears that setting a high nice value has no effect on scheduling. Running eg "nice -n 20 stress -c 64; stress -c 64" launches 128 processes. Using htop, I see no difference between niced and regular processes. I checked the value of ignore_nice_load in /sys and it is 0. On systems I have used in the past, I could see the niced processes drop down to nearly 0 cpu usage. Its not happening on Ubuntu. Anyone know what is going on?

---

### Post by Doug S on 2012-09-21
I can not answer your question, I do not know what is going on. However, I can confirm on two 12.04 servers "nice" appears to have no effect, just as you described. Further, on my 10.10 server, "nice" behaves as expected, such that when severly loaded the "nice" tasks get very little CPU time.
 
By the way, nice only goes to 19, although it seems to clamp it at that value if one asks for a higher number (meaning less favorable scheduling).
 
Edit: I found [this]("http://serverfault.com/questions/405092/nice-level-not-working-on-linux") , but when I tried setting "/proc/sys/kernel/sched_autogroup_enabled" to 0 it made no difference.
Edit: Correction: it does work, see posting #7 below.

---

### Post by thk on 2012-09-22
After a bit of searching, I figured it out. It turns out that if a program is connected to a tty, its priority is not influenced by nice. If you background them however, you will see the correct behavior.

Unfortunately, this behavior interacts with the gridengine batch system. Jobs submitted to gridengine appear similarly not to be influenced by nice, which is exactly what you do not want for long running batch jobs. I think it is because gridengine redirects stdin/stdout and so the job appears to be interactive to the system when it is not.

Bummer. This 'feature' was not well thought through.

---

### Post by dcstar on 2012-09-22
> **thk said:**
> After a bit of searching, I figured it out. It turns out that if a program is connected to a tty, its priority is not influenced by nice. If you background them however, you will see the correct behavior.

Unfortunately, this behavior interacts with the gridengine batch system. Jobs submitted to gridengine appear similarly not to be influenced by nice, which is exactly what you do not want for long running batch jobs. I think it is because gridengine redirects stdin/stdout and so the job appears to be interactive to the system when it is not.

Bummer. This 'feature' was not well thought through.

Try launching another shell with a nice value and run them in that shell.

---

### Post by thk on 2012-09-22
> **dcstar said:**
> Try launching another shell with a nice value and run them in that shell.

Good idea. I will try that. I was submitting binaries to gridengine, but if I submit a shell script, perhaps processes spawned from the evoked shell script will honor the nice value (since they are running from a shell that gridengine exec'd with a low priority).

---

### Post by thk on 2012-09-22
It just gets stranger.

I tried launching a large number of

schedtool -B -n 20 -e bash -c stress -c 1

jobs with gridengine and then at the command line launched a bunch of

stress -c 1

jobs. The batched gridengine processes show nice = 19, but do not yield to the jobs launched from the command line. In fact they are getting higher priority than the un-niced jobs from the command line. htop clearly shows the gridengine jobs monopolizing the cpu percentage at the expense of the command line jobs. Weird.

---

### Post by Doug S on 2012-09-22
Correction to my posting #2 above: That method for making "nice" work the way it used to does work, one just has to open the session (in my case a new putty session, pts) after changing "/proc/sys/kernel/sched_autogroup_enabled" to 0.
When I wrote yesterday, I had used the same sessions that were already open for my "before" test. Today, I made a new putty connection and the "nice" stuff got very little CPU time if I used the new putty connection.
 
Example output from top for the two settings:```
With /proc/sys/kernel/sched_autogroup_enabled 1:
 
top - 07:56:51 up 13:42,  4 users,  load average: 7.76, 7.17, 8.10
Tasks: 162 total,  24 running, 138 sleeping,   0 stopped,   0 zombie
Cpu(s): 48.6%us,  0.0%sy, 51.4%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   7956412k total,  1447376k used,  6509036k free,   562040k buffers
Swap:  8294396k total,        0k used,  8294396k free,   404004k cached
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5727 doug      39  19  4156   88    0 R   35  0.0   0:05.42 waiter
 5717 doug      20   0  4156   92    0 R   35  0.0   0:11.90 waiter
 5723 doug      39  19  4156   88    0 R   34  0.0   0:05.70 waiter
 5725 doug      39  19  4156   88    0 R   34  0.0   0:05.62 waiter
 5731 doug      39  19  4156   88    0 R   34  0.0   0:05.34 waiter
 5732 doug      39  19  4156   88    0 R   34  0.0   0:05.42 waiter
 5712 doug      20   0  4156   92    0 R   34  0.0   0:12.15 waiter
 5711 doug      20   0  4156   92    0 R   34  0.0   0:12.53 waiter
 5719 doug      20   0  4156   92    0 R   34  0.0   0:11.92 waiter
 5724 doug      39  19  4156   88    0 R   34  0.0   0:05.79 waiter
 5728 doug      39  19  4156   88    0 R   34  0.0   0:05.34 waiter
 5733 doug      39  19  4156   88    0 R   34  0.0   0:05.35 waiter
 5708 doug      20   0  4156   92    0 R   33  0.0   0:12.28 waiter
 5710 doug      20   0  4156   92    0 R   33  0.0   0:12.10 waiter
 5713 doug      20   0  4156   92    0 R   33  0.0   0:12.33 waiter
 5714 doug      20   0  4156   92    0 R   33  0.0   0:12.25 waiter
 5726 doug      39  19  4156   88    0 R   33  0.0   0:05.47 waiter
 5730 doug      39  19  4156   88    0 R   33  0.0   0:05.50 waiter
 5716 doug      20   0  4156   92    0 R   33  0.0   0:12.12 waiter
 5734 doug      39  19  4156   88    0 R   33  0.0   0:05.23 waiter
 5715 doug      20   0  4156   92    0 R   32  0.0   0:11.85 waiter
 5729 doug      39  19  4156   88    0 S   32  0.0   0:05.36 waiter
 5718 doug      20   0  4156   92    0 R   32  0.0   0:11.96 waiter
 5709 doug      20   0  4156   92    0 R   31  0.0   0:12.24 waiter
 5720 doug      20   0 17332 1344  960 R    0  0.0   0:00.03 top
    1 root      20   0 24464 2428 1344 S    0  0.0   0:01.39 init
 
With /proc/sys/kernel/sched_autogroup_enabled 0:
 
top - 08:00:13 up 13:46,  4 users,  load average: 12.27, 11.26, 9.70
Tasks: 162 total,  25 running, 137 sleeping,   0 stopped,   0 zombie
Cpu(s): 91.5%us,  0.0%sy,  8.5%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   7956412k total,  1447360k used,  6509052k free,   562160k buffers
Swap:  8294396k total,        0k used,  8294396k free,   404004k cached
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6002 doug      20   0  4156   88    0 R   66  0.0   0:08.84 waiter
 5996 doug      20   0  4156   88    0 R   65  0.0   0:08.88 waiter
 5991 doug      20   0  4156   88    0 R   64  0.0   0:09.80 waiter
 5995 doug      20   0  4156   88    0 R   64  0.0   0:09.61 waiter
 5998 doug      20   0  4156   88    0 R   62  0.0   0:08.90 waiter
 5992 doug      20   0  4156   88    0 R   61  0.0   0:09.60 waiter
 5999 doug      20   0  4156   88    0 R   61  0.0   0:08.94 waiter
 5993 doug      20   0  4156   88    0 R   60  0.0   0:09.11 waiter
 6000 doug      20   0  4156   88    0 R   60  0.0   0:09.08 waiter
 5994 doug      20   0  4156   88    0 R   56  0.0   0:09.04 waiter
 5997 doug      20   0  4156   88    0 R   55  0.0   0:08.69 waiter
 6001 doug      20   0  4156   88    0 R   54  0.0   0:08.93 waiter
 5988 doug      39  19  4156   92    0 R    9  0.0   0:05.76 waiter
 5978 doug      39  19  4156   92    0 R    8  0.0   0:06.42 waiter
 5983 doug      39  19  4156   92    0 R    7  0.0   0:06.30 waiter
 5985 doug      39  19  4156   92    0 R    7  0.0   0:05.88 waiter
 5989 doug      39  19  4156   92    0 R    6  0.0   0:05.52 waiter
 5979 doug      39  19  4156   92    0 R    6  0.0   0:06.46 waiter
 5980 doug      39  19  4156   92    0 R    6  0.0   0:06.15 waiter
 5982 doug      39  19  4156   92    0 R    5  0.0   0:05.93 waiter
 5981 doug      39  19  4156   92    0 R    5  0.0   0:06.04 waiter
 5987 doug      39  19  4156   92    0 R    5  0.0   0:05.87 waiter
 5984 doug      39  19  4156   92    0 R    3  0.0   0:05.94 waiter
 5986 doug      39  19  4156   92    0 R    3  0.0   0:05.82 waiter
    1 root      20   0 24464 2428 1344 S    0  0.0   0:01.39 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
```As a side note, I have never figured out how to modify /proc/sys setting from the command line, so I make a script to do it and run it as sudo. Examples:```
doug@s15:~/temp$ cat enable_nice
#! /bin/bash
cat /proc/sys/kernel/sched_autogroup_enabled
echo 0 > /proc/sys/kernel/sched_autogroup_enabled
cat /proc/sys/kernel/sched_autogroup_enabled
doug@s15:~/temp$
doug@s15:~/temp$ cat disable_nice
#! /bin/bash
cat /proc/sys/kernel/sched_autogroup_enabled
echo 1 > /proc/sys/kernel/sched_autogroup_enabled
cat /proc/sys/kernel/sched_autogroup_enabled
doug@s15:~/temp$
doug@s15:~/temp$ sudo ./disable_nice
[sudo] password for doug:
0
1
doug@s15:~/temp$

```

---

### Post by thk on 2012-09-22
Yes, that helps. At least now gridengine jobs appear to share equal time with non-gridengine jobs, regardless of nice level. They wont go to low cpu usage, but that's better than dominating other jobs.

---

### Post by thk on 2012-09-22
> **Doug S said:**
> As a side note, I have never figured out how to modify /proc/sys setting from the command line, so I make a script to do it and run it as sudo.

```
sudo sysctl kernel.sched_autogroup_enabled=0
```

will set it one time or

```
kernel.sched_autogroup_enabled = 0
```

in /etc/sysctl.d/50-disable-autogroup.conf so that it will get set on reboot.

---

### Post by Doug S on 2012-09-22
thk, thanks for that.
 
On my system there seems to be a side effect of messing with "/proc/sys/kernel/sched_autogroup_enabled" where the system crashes when I try to re-boot. I have repeated it several times now.
 
Edit: [Launchpad bug report ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1055222")about the crash senario.

---

