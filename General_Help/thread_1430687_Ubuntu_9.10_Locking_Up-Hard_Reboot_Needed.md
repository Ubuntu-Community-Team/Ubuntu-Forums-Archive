---
title: "Ubuntu 9.10 Locking Up-Hard Reboot Needed"
date: 2010-03-15
forum: General Help
---

### Post by oracle5 on 2010-03-15
Using Ubuntu 9.10 with the 2.6.31-20-generic kernel on a Thinkpad R61i and have been having random lockups lately. Most of them occur when the system is left unattended such as overnight but every once in a while it will occur when I'm using the machine. Its a complete lockup where I have to hard reboot. Pushing the caps lock doesn't make the caps lock indicator light come on nor will the mouse move in the times when it locked up while I was using it. 

Below is from my kern.log around the time of the latest event. The same set of messages gets repeated over and over for about 20 minutes until all the logs stop. It makes me suspect its something to do with the Intel graphics card but that's about all I know.

> Mar 15 01:53:57 thinkpad kernel: [35160.752592] INFO: task i915/1:370 blocked for more than 120 seconds.
Mar 15 01:53:57 thinkpad kernel: [35160.752599] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Mar 15 01:53:57 thinkpad kernel: [35160.752604] i915/1        D 0000000000000000     0   370      2 0x00000000
Mar 15 01:53:57 thinkpad kernel: [35160.752613]  ffff88007960fd70 0000000000000046 0000000000000000 0000000000015880
Mar 15 01:53:57 thinkpad kernel: [35160.752623]  ffff8800798c47c0 0000000000015880 0000000000015880 0000000000015880
Mar 15 01:53:57 thinkpad kernel: [35160.752631]  0000000000015880 ffff8800798c47c0 0000000000015880 0000000000015880
Mar 15 01:53:57 thinkpad kernel: [35160.752639] Call Trace:
Mar 15 01:53:57 thinkpad kernel: [35160.752654]  [<ffffffff8152bbb7>] __mutex_lock_slowpath+0xd7/0x160
Mar 15 01:53:57 thinkpad kernel: [35160.752661]  [<ffffffff8152bab6>] mutex_lock+0x26/0x50
Mar 15 01:53:57 thinkpad kernel: [35160.752701]  [<ffffffffa007f788>] i915_gem_retire_work_handler+0x38/0x90 [i915]
Mar 15 01:53:57 thinkpad kernel: [35160.752724]  [<ffffffffa007f750>] ? i915_gem_retire_work_handler+0x0/0x90 [i915]
Mar 15 01:53:57 thinkpad kernel: [35160.752733]  [<ffffffff81073705>] run_workqueue+0x95/0x170
Mar 15 01:53:57 thinkpad kernel: [35160.752741]  [<ffffffff81073884>] worker_thread+0xa4/0x120
Mar 15 01:53:57 thinkpad kernel: [35160.752749]  [<ffffffff81078a30>] ? autoremove_wake_function+0x0/0x40
Mar 15 01:53:57 thinkpad kernel: [35160.752756]  [<ffffffff810737e0>] ? worker_thread+0x0/0x120
Mar 15 01:53:57 thinkpad kernel: [35160.752762]  [<ffffffff81078646>] kthread+0xa6/0xb0
Mar 15 01:53:57 thinkpad kernel: [35160.752770]  [<ffffffff8101312a>] child_rip+0xa/0x20
Mar 15 01:53:57 thinkpad kernel: [35160.752776]  [<ffffffff810785a0>] ? kthread+0x0/0xb0
Mar 15 01:53:57 thinkpad kernel: [35160.752782]  [<ffffffff81013120>] ? child_rip+0x0/0x20


Any suggestions on how to fix this problem would be greatly appreciated.

Thanks,
oracle5

---

### Post by dcstar on 2010-03-15
> **oracle5 said:**
> Using Ubuntu 9.10 with the 2.6.31-20-generic kernel on a Thinkpad R61i and have been having random lockups lately.
.........
Any suggestions on how to fix this problem would be greatly appreciated.

Thanks,
oracle5

Monitor CPU and MB temps.

---

### Post by rnerwein on 2010-03-16
hi
pardon me, but the messages in syslog looks for me as a fake for a well known bug. 
have a look what task it wich blocked ( pid see lockfile ).
ciao

---

### Post by oracle5 on 2010-03-16
Temps are not doing anything weird since that was what I first suspected when I was having problems originally. 

I think I've come up with somewhat of a solution though. I turned off the option for the screen to be powered off except when shutting down obviously and I have not had any more lock ups. Not really the best solution but at least its working.

---

