---
title: "random desktop freezes in karmic"
date: 2009-11-03
forum: General Help
---

### Post by cesera on 2009-11-03
I recently bought an old Dell Inspiron 1100 from a friend. It now runs Ubuntu Karmic, which generally works well, except seemingly random desktop freezes.
Every so often the whole desktop stops responding (I can move the mouse pointer, but do nothing with it. The keyboard seems frozen as well, at least I cannot use CTRL+ALT+F? to switch to a terminal session.)
 
 
I have run memtest86+ to see if that was the problem, but that all seems fine.
For what it worth the machine has 1GB RAM, 40GB hdd and an intel graphics card.
 
 
If anyone can tell me where to even start looking that would be helpful. I did search the forums for this problem and have come across a few threads, but none of the were particularly helpful.

---

### Post by P4man on 2009-11-03
can you look in /var/log/messages if you see any errors around the time of the freezes ? Are you using desktop effects, and if so, does turning them off eliminate the problem?

---

### Post by .kev on 2009-11-03
Same here, freshly upgraded Jaunty>Karmic, Intel 945GC, system freezes quickly after gdm login.
If I let gdm alone I can work in ttys as usual, no freeze.
Creating a new user didn't solve the issue.
Hard drive/memory are ok.
When the freeze occurs the keyboard and mouse do not respond but I can ssh.

Here's what I get in /var/log/kern.log :
The last line before trying to start my session :
```

[   55.780104] type=1505 audit(1257248121.939:21): operation="profile_replace" pid=1208 name=/usr/sbin/tcpdump
```Next to this line, this is wherre the session hangs :
```
[  600.920064] INFO: task i915/2:278 blocked for more than 120 seconds.
[  600.920073] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  600.920080] i915/2        D c08145c0     0   278      2 0x00000000
[  600.920090]  f64fff04 00000046 00000000 c08145c0 f6a39bb8 c08145c0 cd113e9a 00000069
[  600.920106]  c08145c0 c08145c0 f6a39bb8 c08145c0 cd112de7 00000069 c08145c0 f6a42e00
[  600.920120]  f6a39920 f68f1814 f68f1818 ffffffff f64fff30 c056f776 f7089920 f68f181c
[  600.920134] Call Trace:
[  600.920150]  [<c056f776>] __mutex_lock_slowpath+0xc6/0x130
[  600.920158]  [<c056f690>] mutex_lock+0x20/0x40
[  600.920195]  [<f824ec0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
[  600.920206]  [<c0157a7e>] run_workqueue+0x6e/0x140
[  600.920236]  [<f824ebe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
[  600.920245]  [<c0157bd8>] worker_thread+0x88/0xe0
[  600.920254]  [<c015c280>] ? autoremove_wake_function+0x0/0x40
[  600.920262]  [<c0157b50>] ? worker_thread+0x0/0xe0
[  600.920269]  [<c015bf8c>] kthread+0x7c/0x90
[  600.920276]  [<c015bf10>] ? kthread+0x0/0x90
[  600.920285]  [<c0104007>] kernel_thread_helper+0x7/0x10
[  600.920316] INFO: task Xorg:995 blocked for more than 120 seconds.
[  600.920321] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  600.920327] Xorg          D c08145c0     0   995      1 0x00400004
[  600.920336]  f61f1e28 00003086 00100100 c08145c0 f61b6718 c08145c0 92d192ac 00000069
[  600.920350]  c08145c0 c08145c0 f61b6718 c08145c0 92d09700 00000069 c08145c0 f60e21c0
[  600.920364]  f61b6480 f68f1814 f68f1818 ffffffff f61f1e54 c056f776 00000000 f68f181c
[  600.920378] Call Trace:
[  600.920386]  [<c056f776>] __mutex_lock_slowpath+0xc6/0x130
[  600.920394]  [<c056f690>] mutex_lock+0x20/0x40
[  600.920423]  [<f824ee8b>] i915_gem_throttle_ioctl+0x2b/0x70 [i915]
[  600.920462]  [<f81466c0>] drm_ioctl+0x180/0x360 [drm]
[  600.920494]  [<f824ee60>] ? i915_gem_throttle_ioctl+0x0/0x70 [i915]
[  600.920504]  [<c01e72bc>] ? do_sync_read+0xbc/0x100
[  600.920513]  [<c0127c38>] ? default_spin_lock_flags+0x8/0x10
[  600.920521]  [<c05707da>] ? _spin_lock_irqsave+0x2a/0x40
[  600.920530]  [<c015f405>] ? __remove_hrtimer+0x25/0x70
[  600.920538]  [<c015fc63>] ? hrtimer_try_to_cancel+0x33/0x80
[  600.920547]  [<c014947e>] ? do_setitimer+0x23e/0x300
[  600.920562]  [<c01f4cf3>] vfs_ioctl+0x73/0x90
[  600.920570]  [<c01f4fc1>] do_vfs_ioctl+0x71/0x310
[  600.920577]  [<c014957b>] ? sys_setitimer+0x3b/0x90
[  600.920585]  [<c01f52bf>] sys_ioctl+0x5f/0x80
[  600.920592]  [<c010336c>] syscall_call+0x7/0xb
```And 120s later, guess what :
```
[  720.920064] INFO: task i915/2:278 blocked for more than 120 seconds.
*... et caetera.*
```So here it is, clearly related to xorg-driver-video-intel / kernel 2.6.31-14

I tried to reinstall/reconfigure/purge+reinstall it, no success.

Maybe I should try a clean install, just to check...

Any ideas? Is there a PPA with a patched version?

edit: oh I forgot to try with disabled desktop effects. brb

---

### Post by P4man on 2009-11-03
.kev, your bug seems to be this one:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/451518](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/451518)

---

### Post by .kev on 2009-11-03
Yes, it is, thanks :) I'll do my next posts in the bug thread.

Everything works OK without compiz though, so I'll disable it until this issue is fixed.

---

