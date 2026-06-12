---
title: "high memory use, all processes sleeping"
date: 2010-02-01
forum: General Help
---

### Post by paulnn on 2010-02-01
Hi,

I'm using Ubuntu 9.10 and my kernel is 2.6.31-17-generic.

Soon after I boot up my memory usage is much higher than normal, around 33% with only firefox running, where it would usually be around 10-15%. I think the processor is running more than normal and the system seems slower in general, sometimes the memory usage climbs to the point where i have to reboot.

In System-monitor, all processes are listed as 'sleeping' (including Firefox which i'm using to write this now) and it says "poll_schedule_timeout" in the "waiting channel" column for most processes.

Is anyone having the same problem? Any ideas what's causing it?

thanks.

---

### Post by leeds_shrew on 2010-02-01
Q1: yes, Q2: no. Have suspicions around CheckGmail and flash player though. Do you have CheckGmail?

---

### Post by paulnn on 2010-02-01
I don't have checkgmail; don't think it's flashplayer either - a restart used to fix this for me but now each time i boot up system monitor shows this straight away, before i launch any processes myself.

Apart from system_monitor, the one process that isn't marked 'poll_schedule_timeout" is gfvs-fuse-daemon, it's marked as "futex_wait_queue_me". 

From google it looks like some people have had similar problems but no fixes or ideas.

---

### Post by paulnn on 2010-02-02
Anyone got an idea on this? From the moment i boot the gvfs-fuse-daemon process says 'futex_wait_queue_me', which in think means it's in deadlock.

Ubuntu 9.10 and my kernel is 2.6.31-17-generic.

---

### Post by GrowMap on 2010-02-02
I have the same issue with the same release. FireFox grays out and sometimes recovers and sometimes does not. When that happens FireFox process says 'futex_wait_queue_me'. 

I too am getting "gvfs-fuse-daemon process says 'futex_wait_queue_me'" from the moment I boot up now; however, I don't believe that was happening when I first started experiencing the FireFox issues. 

Just now Pidgin grayed out and recovered and I recall Ubuntu wanted to ditch Pidgin for some reason. Could that be related? 

Any guidance on how to resolve this issue would be greatly appreciated.

---

### Post by colinjones on 2010-02-02
I'm having the same issue (karmic, x64), eventually my machine grinds to a halt without a reboot, swapping constantly. console-kit-daemon, the gnome authentication and polkitd seem to eat all the memory, although even when they are low (just after reboot) the baseline is still higher than I would expect.

posted in several threads about this, no ideas as yet... but there seem to be others with the same issue. Logged a bug with freedesktop upstream on consolekit but no real response there yet either.

---

### Post by wojox on 2010-02-02
gvfs is the virtual file system, usually used to mount network shares. Anyone doing that?

---

### Post by paulnn on 2010-02-03
I am not mounting network drives. I think gvfs now mounts local external devices as well as network drives - But even with no usb devices mounted or connected it's still deadlocked as soon as i boot up (futex_wait indicates a deadlock as far as i know)

I also tried removing practically everything from the (long) list of default startup applications, to no avail, so empathy, evolution, bluetooth manager, network manager, seahorse daemon (?!), and visual assitance  are not culprits.

I am out of ideas - is it possible to remove gvfs or is it a vital system component? According to synaptic loads of applications depend on it.

---

### Post by Shark_AtK12 on 2010-02-03
I have had the same problem and after doing some researching, i found this to be an issue with 2.6.31-17. Here is a link that may help, there are also some other good topics linked in there.
[http://ubuntuforums.org/showthread.php?t=1344897](http://ubuntuforums.org/showthread.php?t=1344897)
 
I haven't researched it too much as i haven't had time but After rebooting my PC twice in a row, doing a free -m my usage is down to 200mb. You can try going back to the .14 kernel.

---

### Post by colinjones on 2010-02-03
has anybody tried -18?

---

### Post by L8erG8er on 2010-04-28
I know this reply is way later, but I'm using -20, and still see gvfs in futex_wait.

---

### Post by kioan on 2010-06-08
The problem remains... 
I have ```
2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
``` and this problem is driving me crazy... :mad:


The output of 
```
ps -elf | grep poll_s| wc -l
ps -elf | grep futex_| wc -l
```
shows 91 processes with poll_schedule_timeout wait channel and 10 on futex_wait_queue_me

---

