---
title: "gzip using 90% of CPU yet it's not loaded"
date: 2010-02-03
forum: General Help
---

### Post by ozguitarplayer on 2010-02-03
Hi,
At times I notice that my CPU is working hard and I open terminal and enter #top which shows me that gzip is running and using 90% or more or the CPU this remains the same after I close all applications and the only thing left open is terminal.
The only way I have found so far is to reboot the system.

Anyone got any suggestions as to what my be causing this?

---

### Post by lloyd_b on 2010-02-03
> **ozguitarplayer said:**
> Hi,
At times I notice that my CPU is working hard and I open terminal and enter #top which shows me that gzip is running and using 90% or more or the CPU this remains the same after I close all applications and the only thing left open is terminal.
The only way I have found so far is to reboot the system.

Anyone got any suggestions as to what my be causing this?

At a guess, it's the "logrotate" command (it keeps log files from filling up the disk).  As part of its function, it uses 'gzip' to compress older log files to save space.

It's being run automatically by cron, I believe on a once-a-day basis.

Have you tried just letting it run?  It may that by rebooting before it's finished you are creating even more work for it...

Lloyd B.

---

### Post by ozguitarplayer on 2010-02-03
Thanks, I'll try letting it run and see how it goes, I guess I was wondering about it as it has only been happening this past couple of weeks.

---

### Post by ozguitarplayer on 2010-02-04
Back again, 
I have let it run and it goes for hours before I get fed up and reboot. If it was compressing files surely it wouldn't take 3-4 hours without finishing and use 90%+ of CPU.
It has only just started happening and I have been using Jaunty Jackalope since it's release in April 09.

---

### Post by lloyd_b on 2010-02-04
> **ozguitarplayer said:**
> Back again, 
I have let it run and it goes for hours before I get fed up and reboot. If it was compressing files surely it wouldn't take 3-4 hours without finishing and use 90%+ of CPU.
It has only just started happening and I have been using Jaunty Jackalope since it's release in April 09.

I'd say it's time to get some more info about that gzip process.  After running 'top', press the 'c' key to turn on the information about the command (this shows the command and all of its options).  Note that much of the info probably won't fit on the screen, in which cast hit the "f" key and turn off any fields you don't need to see (I'd say leave PID and CPU fields, but turn off the rest).

If possible, could you post the results of that, so we can see exactly what command is running?  It sounds like it's stuck in a loop of some sort, but without any idea as to what it's processing it's impossible to tell exactly what it's getting stuck on.

Lloyd B.

---

### Post by ozguitarplayer on 2010-02-04
Thanks for that, I'll have to wait till the next time gzip starts running on it own, then I'll do as you suggest and get back to you.

---

### Post by ozguitarplayer on 2010-02-05
Hi again,
This is the output of c & f

```
root@MasterJack:/home/nigel# top

top - 07:27:24 up 34 min,  2 users,  load average: 1.61, 1.50, 1.07
Tasks: 142 total,   1 running, 141 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.4%us,  2.5%sy, 41.8%ni, 39.0%id,  6.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2051596k total,  1999108k used,    52488k free,    12612k buffers
Swap:        0k total,        0k used,        0k free,  1578844k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                               
 4487 root      39  19  2024  664  288 S   95  0.0  14:52.41 gzip                                                  
 2785 root      20   0  324m  40m 9544 S   16  2.0   2:42.70 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0
 4959 root      20   0 49492  36m  22m S    4  1.8   0:16.66 /usr/sbin/synaptic --hide-main-window --non-interactiv
 3413 nigel     20   0  321m  98m  19m S    2  4.9   5:01.57 /opt/firefox/firefox-bin                              
   32 root      15  -5     0    0    0 S    1  0.0   0:04.35 [kswapd0]                                             
 3201 nigel     20   0 39636  16m 7720 S    0  0.8   0:06.27 gnome-panel                                           
 3213 nigel     20   0 26676 8596 5360 S    0  0.4   0:00.89 update-notifier --startup-delay=60                    
 4486 root      39  19 15132  12m  704 D    0  0.6   0:11.46 tar -czS -C / --no-recursion --ignore-failed-read --nu
 4969 root      20   0  5236 1984 1684 S    0  0.1   0:00.73 /usr/lib/apt/methods/http                             
    1 root      20   0  3084 1752  432 S    0  0.1   0:01.41 /sbin/init                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 [kthreadd]                                            
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 [migration/0]                                         
    4 root      15  -5     0    0    0 S    0  0.0   0:00.11 [ksoftirqd/0]                                         
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 [watchdog/0]                                          
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 [migration/1]                                         
    7 root      15  -5     0    0    0 S    0  0.0   0:00.14 [ksoftirqd/1]                                         
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 [watchdog/1]                                          
Current Fields:  AEHIOQTWKNMbcdfgjplrsuvyzX  for window 1:Def
Toggle fields via field letter, type any other key to return 

* A: PID        = Process Id                               u: nFLT       = Page Fault count
* E: USER       = User Name                                v: nDRT       = Dirty Pages count
* H: PR         = Priority                                 y: WCHAN      = Sleeping in Function
* I: NI         = Nice value                               z: Flags      = Task Flags <sched.h>
* O: VIRT       = Virtual Image (kb)                     * X: COMMAND    = Command name/line
* Q: RES        = Resident size (kb)
* T: SHR        = Shared Mem size (kb)                   Flags field:
* W: S          = Process Status                           0x00000001  PF_ALIGNWARN
* K: %CPU       = CPU usage                                0x00000002  PF_STARTING
* N: %MEM       = Memory usage (RES)                       0x00000004  PF_EXITING
* M: TIME+      = CPU Time, hundredths                     0x00000040  PF_FORKNOEXEC
  b: PPID       = Parent Process Pid                       0x00000100  PF_SUPERPRIV
  c: RUSER      = Real user name                           0x00000200  PF_DUMPCORE
  d: UID        = User Id                                  0x00000400  PF_SIGNALED
  f: GROUP      = Group Name                               0x00000800  PF_MEMALLOC
  g: TTY        = Controlling Tty                          0x00002000  PF_FREE_PAGES (2.5)
  j: P          = Last used cpu (SMP)                      0x00008000  debug flag (2.5)
  p: SWAP       = Swapped size (kb)                        0x00024000  special threads (2.5)
  l: TIME       = CPU Time                                 0x001D0000  special states (2.5)
  r: CODE       = Code size (kb)                           0x00100000  PF_USEDFPU (thru 2.4)
  s: DATA       = Data+Stack size (kb)

```

---

### Post by daqron on 2010-12-13
Is this possibly the system backup process (do you have auto backups configured)? I'm pretty sure that's what is going on on my system. I have an i7 processor and tons of RAM but gzip running at 100% for > 1 hour was bringing the system to its knees. Evidently the backup config doesn't bother to throttle the process for smooth background execution.

In any case, check out [cpulimit]("http://www.ubuntugeek.com/cpulimit-limit-the-cpu-usage-of-a-process.html"). If it is indeed backup, or logrotate, or something else you don't want to cancel, cpulimit will at least keep its CPU usage at bay.

---

