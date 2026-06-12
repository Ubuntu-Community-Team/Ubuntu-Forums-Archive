---
title: "System hangs whenever module is inserted or removed"
date: 2010-06-26
forum: General Help
---

### Post by agent8131 on 2010-06-26
After the updates about a week ago I noticed my system was hanging (screen and mouse frozen, unable to switch desktops, Ctrl+Alt+SysRq+B still reboots) frequently.  Though sometimes the system would not hang but become extremely sluggish and unresponsive.  I've been able to determine that the problems occur whenever a module is added or removed.  I can cause this problem with such commands as:

sudo modprobe aes
sudo rmmod raid0

I've tried multiple kernels but the problem persists.  I've run memtest on the system but no errors have been found.  I wonder if this could be some other sort of hardware problem but I'm suspicious that this began after a set of updates.  I've seen message such as this in the kern.log:

```
Jun 25 22:35:48 localhost kernel: [  240.480059] INFO: task modprobe:2672 blocked for more than 120 seconds.
Jun 25 22:35:48 localhost kernel: [  240.492925] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jun 25 22:35:48 localhost kernel: [  240.506918] modprobe      D 00000000ffffffff     0  2672   2650 0x00000004
Jun 25 22:35:48 localhost kernel: [  240.506929]  ffff880195179cc8 0000000000000086 0000000000015bc0 0000000000015bc0
Jun 25 22:35:48 localhost kernel: [  240.506939]  ffff88019b93b1a0 ffff880195179fd8 0000000000015bc0 ffff88019b93ade0
Jun 25 22:35:48 localhost kernel: [  240.506948]  0000000000015bc0 ffff880195179fd8 0000000000015bc0 ffff88019b93b1a0
Jun 25 22:35:48 localhost kernel: [  240.506956] Call Trace:
Jun 25 22:35:48 localhost kernel: [  240.506974]  [<ffffffff8153f0cd>] schedule_timeout+0x22d/0x300
Jun 25 22:35:48 localhost kernel: [  240.506985]  [<ffffffff812b6f86>] ? rb_erase+0xd6/0x160
Jun 25 22:35:48 localhost kernel: [  240.506995]  [<ffffffff81053980>] ? __dequeue_entity+0x30/0x50
Jun 25 22:35:48 localhost kernel: [  240.507002]  [<ffffffff8153ecfb>] wait_for_common+0xdb/0x170
Jun 25 22:35:48 localhost kernel: [  240.507011]  [<ffffffff8105b180>] ? default_wake_function+0x0/0x20
Jun 25 22:35:48 localhost kernel: [  240.507018]  [<ffffffff8153ee4d>] wait_for_completion+0x1d/0x20
Jun 25 22:35:48 localhost kernel: [  240.507027]  [<ffffffff81080c15>] flush_cpu_workqueue+0x65/0xa0
Jun 25 22:35:48 localhost kernel: [  240.507035]  [<ffffffff81080cd0>] ? wq_barrier_func+0x0/0x20
Jun 25 22:35:48 localhost kernel: [  240.507041]  [<ffffffff81081504>] flush_workqueue+0x54/0x80
Jun 25 22:35:48 localhost kernel: [  240.507050]  [<ffffffff810b64f4>] __stop_machine+0xf4/0x120
Jun 25 22:35:48 localhost kernel: [  240.507058]  [<ffffffff8109b450>] ? __unlink_module+0x0/0x30
Jun 25 22:35:48 localhost kernel: [  240.507065]  [<ffffffff810b674e>] stop_machine+0x3e/0x60
Jun 25 22:35:48 localhost kernel: [  240.507073]  [<ffffffff8109ea90>] free_module+0x30/0x150
Jun 25 22:35:48 localhost kernel: [  240.507081]  [<ffffffff810a1935>] sys_init_module+0x225/0x260
Jun 25 22:35:48 localhost kernel: [  240.507090]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b

```

I'm not sure how to proceed at this point.  I've tried using strace but that was not helpful.  This is becoming a serious problem as I cannot load any encrypted volumes due to the inability to load the aes module.  dpkg is currently in an interrupted state as the system hung when upgrading virtualbox-3.2 when it attempted to remove the modules.  So my system is barely functional and I cannot see any way to fix things.  Suggestions?

---

### Post by dino99 on 2010-06-26
dont know exactly what the problem is, but check the basics:

- is your sources.list only using genuine ubuntu repo and trusted ppa
( if some ppa are used, take care they are still updated)
- look at logs about conflicts
- if some packages have been forced (into synaptic) in the past, these issues might be related to

- clean the system (can use gconf-cleaner, bleachbit)

- ckeck custom config (or use the standard instead)

- is bios can be updated ?

note: the latest kernel 35 work better with raid now

---

### Post by agent8131 on 2010-06-26
The problem was the cgroup-bin package.  I have contributed to the bug report here:

[https://bugs.launchpad.net/ubuntu/+source/libcgroup/+bug/598335](https://bugs.launchpad.net/ubuntu/+source/libcgroup/+bug/598335)

I was attempting to use cgroups to limit memory consumption of certain applications.  It seems like this package is broken in ubuntu and should be avoided.

---

