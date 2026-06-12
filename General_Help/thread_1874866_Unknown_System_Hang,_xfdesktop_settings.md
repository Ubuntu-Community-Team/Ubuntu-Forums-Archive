---
title: "Unknown System Hang, xfdesktop settings?"
date: 2011-11-03
forum: General Help
---

### Post by hwttdz on 2011-11-03
Update: Marking as solved, seems to have been related to a cronjob dependent on an sshfs drive hanging.

I'm getting random hangs about every 30 minutes.  I believe this has something to do with 

```
Nov  3 21:37:09 poseidon kernel: [ 4318.139193] INFO: task xfdesktop-setti:22972 blocked for more than 120 seconds.
Nov  3 21:37:09 poseidon kernel: [ 4318.139198] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  3 21:37:09 poseidon kernel: [ 4318.139201] xfdesktop-setti D ffffffff81605120     0 22972   1904 0x00000004
Nov  3 21:37:09 poseidon kernel: [ 4318.139206]  ffff8801af223a58 0000000000000082 ffff8801af2239f8 ffffffff810329b9
Nov  3 21:37:09 poseidon kernel: [ 4318.139211]  ffff8801af223fd8 ffff8801af223fd8 ffff8801af223fd8 0000000000012a40
Nov  3 21:37:09 poseidon kernel: [ 4318.139215]  ffff8801c5981720 ffff8801c2d20000 ffff8801a9aa8e40 ffff8801a9aa8e40
Nov  3 21:37:09 poseidon kernel: [ 4318.139220] Call Trace:
Nov  3 21:37:09 poseidon kernel: [ 4318.139229]  [<ffffffff810329b9>] ? default_spin_lock_flags+0x9/0x10
Nov  3 21:37:09 poseidon kernel: [ 4318.139235]  [<ffffffff8125f805>] request_wait_answer+0x85/0x230
Nov  3 21:37:09 poseidon kernel: [ 4318.139240]  [<ffffffff81081cb0>] ? add_wait_queue+0x60/0x60
Nov  3 21:37:09 poseidon kernel: [ 4318.139244]  [<ffffffff8125fa25>] fuse_request_send+0x75/0xb0
Nov  3 21:37:09 poseidon kernel: [ 4318.139248]  [<ffffffff81264678>] fuse_lookup_name+0x148/0x2b0
Nov  3 21:37:09 poseidon kernel: [ 4318.139252]  [<ffffffff81264830>] fuse_lookup+0x50/0x1d0
Nov  3 21:37:09 poseidon kernel: [ 4318.139258]  [<ffffffff81171ee5>] d_alloc_and_lookup+0x45/0x90
Nov  3 21:37:09 poseidon kernel: [ 4318.139262]  [<ffffffff8117f745>] ? d_lookup+0x35/0x60
Nov  3 21:37:09 poseidon kernel: [ 4318.139266]  [<ffffffff81174116>] do_lookup+0x216/0x2b0
Nov  3 21:37:09 poseidon kernel: [ 4318.139270]  [<ffffffff81175e7c>] path_lookupat+0x11c/0x700
Nov  3 21:37:09 poseidon kernel: [ 4318.139275]  [<ffffffff81094f98>] ? get_futex_value_locked+0x28/0x40
Nov  3 21:37:09 poseidon kernel: [ 4318.139281]  [<ffffffff812f46f7>] ? __strncpy_from_user+0x27/0x60
Nov  3 21:37:09 poseidon kernel: [ 4318.139285]  [<ffffffff81176491>] do_path_lookup+0x31/0xc0
Nov  3 21:37:09 poseidon kernel: [ 4318.139288]  [<ffffffff811723c1>] ? getname_flags+0x51/0xd0
Nov  3 21:37:09 poseidon kernel: [ 4318.139293]  [<ffffffff81176989>] user_path_at+0x59/0xa0
Nov  3 21:37:09 poseidon kernel: [ 4318.139299]  [<ffffffff815e9efe>] ? _raw_spin_lock+0xe/0x20
Nov  3 21:37:09 poseidon kernel: [ 4318.139303]  [<ffffffff81096653>] ? futex_wake+0x113/0x130
Nov  3 21:37:09 poseidon kernel: [ 4318.139307]  [<ffffffff8116bfe4>] vfs_fstatat+0x44/0x70
Nov  3 21:37:09 poseidon kernel: [ 4318.139310]  [<ffffffff8116c02e>] vfs_lstat+0x1e/0x20
Nov  3 21:37:09 poseidon kernel: [ 4318.139313]  [<ffffffff8116c1ca>] sys_newlstat+0x1a/0x40
Nov  3 21:37:09 poseidon kernel: [ 4318.139318]  [<ffffffff815f22c2>] system_call_fastpath+0x16/0x1b
```

Anyone with any ideas?  My machine worked fine until today, and I think I've had 5 now.

Update: I reseated some cables and my uptime is at about 6 hours, so perhaps that did the trick.  Fingers crossed.  Of course I also spent some money on a hard drive thinking that was the most likely cause of failure.

Second update: Reseating the cables did not fix the issue, a few hours after that I disabled a cronjob which apparently depended on an sshfs drive being mounted.  This seems to have fixed the issue (5 days uptime now).  I'm slightly miffed that 1) sshfs would hang like that instead of just saying "mountpoint not connected" or whathaveyou.  2) that the whole os would grind to a halt because what was essentially an scp run by an unprivileged user failed (if root is scp'ing a system file that would be a) stupid, and b) a different story).  Anyways, living with my scripts dir being out of sync between machines at the moment.

---

