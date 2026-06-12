---
title: "Chrome causing suspend problems"
date: 2010-02-18
forum: General Help
---

### Post by ToeBee on 2010-02-18
I have a Dell mini 10v running 9.10 netbook remix. I tried installing Chrome and fell in love with how fast it is on this low power machine. It is the only browser where Wave is really usable (well as usable as Wave can be at all...)

But I am pretty sure that Chrome is somehow breaking suspend. After a day or two of using Chrome I can no longer suspend. When I try, it starts shutting things down (network manager disconnects, input stops being accepted, etc) but the screen never turns off and after 10 seconds or so everything wakes back up and keeps running. I intentionally did NOT fire up Chrome for a week and suspend continued working all week long. A day or two after I started using Chrome again, suspend broke. I realize this isn't exactly hard evidence that Chrome is the culprit but it's the best theory I have at the moment. 

It should be noted that once suspend is broken, even if I exit Chrome, it does not fix itself. Logging out doesn't fix it either. I have to reboot to get suspend working again. Obviously for a netbook, this is quite annoying.

I will include excerpts from syslog when it fails but they seems like pretty generic messages. I would attach all of the logs from a failed suspend but it is far beyond the 18KB limit for text attachments. **Mainly I'm just wondering if anyone else has noticed suspend problems while using Chrome.** Googling has not turned up much on the subject.

Basically it is a bunch of messages that look like the following. I'm guessing there is a repeat for each running process:

```
console-kit-d D c08145c0     0   845      1 0x00000000
 f4337eac 00000082 f4204000 c08145c0 f4325a88 c08145c0 38100712 00003e8e
 c08145c0 c08145c0 f4325a88 c08145c0 00000001 00003e8e c08145c0 ef562540
 f43257f0 00000000 00000002 f4337f7c f4337ebc c0163725 f4337fb4 f4337efc
Call Trace:
 [<c0163725>] refrigerator+0xc5/0x110
 [<c0153e26>] get_signal_to_deliver+0x46/0x2a0
 [<c05711c7>] ? unlock_kernel+0x27/0x30
 [<c010304b>] do_signal+0x6b/0x160
 [<c012d12b>] ? kunmap_atomic+0x5b/0x70
 [<c03888c0>] ? vt_ioctl+0x0/0x1560
 [<c03803c7>] ? tty_ioctl+0x77/0x620
 [<c0380350>] ? tty_ioctl+0x0/0x620
 [<c01f536c>] ? vfs_ioctl+0x1c/0x90
 [<c01f5691>] ? do_vfs_ioctl+0x71/0x310
 [<c057344b>] ? do_page_fault+0x19b/0x380
 [<c010318d>] do_notify_resume+0x4d/0x60
 [<c0103448>] work_notifysig+0x13/0x1b

```

Then when that is all over, it is followed by this which, once again, looks like pretty generic debugging information.
```
 Sched Debug Version: v0.09, 2.6.31-19-generic #56-Ubuntu
 now at 68800580.419206 msecs
   .jiffies                                 : 17125145
   .sysctl_sched_latency                    : 40.000000
   .sysctl_sched_min_granularity            : 8.000000
   .sysctl_sched_wakeup_granularity         : 10.000000
   .sysctl_sched_child_runs_first           : 0.000001
   .sysctl_sched_features                   : 113916

 cpu#0, 1596.210 MHz
   .nr_running                    : 1
   .load                          : 1024
   .nr_switches                   : 29402722
   .nr_load_updates               : 6856056
   .nr_uninterruptible            : 4294966612
   .next_balance                  : 17.125159
   .curr->pid                     : 16022
   .clock                         : 68800580.012041
   .cpu_load[0]                   : 1024
   .cpu_load[1]                   : 1024
   .cpu_load[2]                   : 1024
   .cpu_load[3]                   : 1024
   .cpu_load[4]                   : 1024
   .yld_count                     : 1534844
   .sched_switch                  : 0
   .sched_count                   : 32026509
   .sched_goidle                  : 11131918
   .ttwu_count                    : 19054294
   .ttwu_local                    : 17742223
   .bkl_count                     : 164575

 cfs_rq[0]:/
   .exec_clock                    : 9894888.137834
   .MIN_vruntime                  : 0.000001
   .min_vruntime                  : 12719339.150054
   .max_vruntime                  : 0.000001
   .spread                        : 0.000000
   .spread0                       : 0.000000
   .nr_running                    : 1
   .load                          : 1024
   .nr_spread_over                : 803
   .shares                        : 0

 rt_rq[0]:/
   .rt_nr_running                 : 0
   .rt_throttled                  : 0
   .rt_time                       : 0.000000
   .rt_runtime                    : 950.000000

 runnable tasks:
             task   PID         tree-key  switches  prio     exec-runtime         sum-exec        sum-sleep
 ----------------------------------------------------------------------------------------------------------
 R     pm-suspend 16022  12719339.150054        86   120  12719339.150054     20069.145033      1627.409391 /

 cpu#1, 1596.210 MHz
   .nr_running                    : 0
   .load                          : 0
   .nr_switches                   : 25618530
   .nr_load_updates               : 7340261
   .nr_uninterruptible            : 685
   .next_balance                  : 17.125145
   .curr->pid                     : 0
   .clock                         : 68800577.025200
   .cpu_load[0]                   : 0
   .cpu_load[1]                   : 0
   .cpu_load[2]                   : 0
   .cpu_load[3]                   : 0
   .cpu_load[4]                   : 0
   .yld_count                     : 1227998
   .sched_switch                  : 0
   .sched_count                   : 28256996
   .sched_goidle                  : 9896899
   .ttwu_count                    : 16748751
   .ttwu_local                    : 15279392
   .bkl_count                     : 95410

 cfs_rq[1]:/
   .exec_clock                    : 9329795.468156
   .MIN_vruntime                  : 0.000001
   .min_vruntime                  : 11284157.426748
   .max_vruntime                  : 0.000001
   .spread                        : 0.000000
   .spread0                       : -1435181.723306
   .nr_running                    : 0
   .load                          : 0
   .nr_spread_over                : 1368
   .shares                        : 0

 rt_rq[1]:/
   .rt_nr_running                 : 0
   .rt_throttled                  : 0
   .rt_time                       : 0.000000
   .rt_runtime                    : 950.000000

 runnable tasks:
             task   PID         tree-key  switches  prio     exec-runtime         sum-exec        sum-sleep
 ----------------------------------------------------------------------------------------------------------


 Restarting tasks ... done.
 r8169: eth0: link up

```

---

