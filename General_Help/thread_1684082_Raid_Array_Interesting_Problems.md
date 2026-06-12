---
title: "Raid Array Interesting Problems"
date: 2011-02-08
forum: General Help
---

### Post by Barajqial on 2011-02-08
Hey there,
 
So we are getting some interesting problems with a raid array set-up with karmic koala that we use at work for back-ups.  This problem just developed after about a year of the raid functioning perfectly.  The raid starts and mounts itself just fine, and we can copy from the raid with no issues.  While trying to copy to the raid it hangs and one access light on the raid box lights up.  When then have to reboot the system and the same errors continue.  We have tried a new raid box and new tower/mobo/etc the only thing that has worked is a fresh install of 10.04(lts).  It just seems weird that it should all of the sudden fail with no updates, .conf changes, or hardware changes.  None of the logs show anything abnormal, but I can post them here if you would like.
 
Any Ideas
     -Bar

---

### Post by Barajqial on 2011-02-08
Here is a what shows up in dmesg on the server in question...

```
[   29.562539] CPU0 attaching NULL sched-domain.
[   29.562547] CPU1 attaching NULL sched-domain.
[   29.562550] CPU2 attaching NULL sched-domain.
[   29.628829] CPU0 attaching sched-domain:
[   29.628834]  domain 0: span 0-2 level MC
[   29.628837]   groups: 0 1 2
[   29.628846] CPU1 attaching sched-domain:
[   29.628848]  domain 0: span 0-2 level MC
[   29.628851]   groups: 1 2 0
[   29.628855] CPU2 attaching sched-domain:
[   29.628857]  domain 0: span 0-2 level MC
[   29.628860]   groups: 2 0 1
[   36.620046] eth2: no IPv6 routers present
[  206.841197] JBD: barrier-based sync failed on md0-8 - disabling barriers
[  360.372051] INFO: task nautilus:1851 blocked for more than 120 seconds.
[  360.372055] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  360.372059] nautilus      D 0001aac8     0  1851   1634 0x00000000
[  360.372064]  ef039c78 00000082 ef039cc8 0001aac8 00000000 c084b760 f177b5a4 c084b760
[  360.372072]  fe90dac4 00000036 c084b760 c084b760 f177b5a4 c084b760 c084b760 f1799a40
[  360.372078]  fe8f1fb9 00000036 f177b300 f177b300 ef039cac f06bca38 ef039ca4 c058e395
[  360.372084] Call Trace:
[  360.372094]  [<c058e395>] rwsem_down_failed_common+0x75/0x1a0
[  360.372098]  [<c058e50d>] rwsem_down_read_failed+0x1d/0x30
[  360.372102]  [<c058e567>] call_rwsem_down_read_failed+0x7/0x10
[  360.372106]  [<c058dacc>] ? down_read+0x1c/0x20
[  360.372111]  [<c028cbe7>] ext4_get_blocks+0x47/0x2c0
[  360.372116]  [<c02aeeb1>] ? __ext4_handle_dirty_metadata+0x61/0xe0
[  360.372120]  [<c022c915>] ? alloc_buffer_head+0x15/0x40
[  360.372124]  [<c028cfa5>] ext4_da_get_block_prep+0x85/0x120
[  360.372128]  [<c022fc02>] __block_prepare_write+0x152/0x380
[  360.372133]  [<c01cb7dc>] ? add_to_page_cache_lru+0x5c/0x70
[  360.372137]  [<c022ffe3>] block_write_begin+0x53/0xf0
[  360.372140]  [<c028cf20>] ? ext4_da_get_block_prep+0x0/0x120
[  360.372145]  [<c029083e>] ext4_da_write_begin+0x1ce/0x380
[  360.372149]  [<c028cf20>] ? ext4_da_get_block_prep+0x0/0x120
[  360.372154]  [<c01ca390>] pagecache_write_begin+0x40/0x50
[  360.372158]  [<c022a48f>] pipe_to_file+0x8f/0x150
[  360.372163]  [<c02f536e>] ? cap_inode_need_killpriv+0x2e/0x40
[  360.372167]  [<c0228f8c>] splice_from_pipe_feed+0x5c/0x100
[  360.372171]  [<c022a400>] ? pipe_to_file+0x0/0x150
[  360.372175]  [<c022a37b>] generic_file_splice_write+0xbb/0x140
[  360.372179]  [<c01518ab>] ? current_fs_time+0x1b/0x20
[  360.372183]  [<c022a2c0>] ? generic_file_splice_write+0x0/0x140
[  360.372187]  [<c0229f8b>] do_splice_from+0x5b/0x80
[  360.372194]  [<c022a11e>] do_splice+0x16e/0x220
[  360.372198]  [<c022ac3d>] sys_splice+0xad/0xd0
[  360.372202]  [<c01033ec>] syscall_call+0x7/0xb
```

---

### Post by Barajqial on 2011-02-09
Problem appears to have fixed itself.  All copying to and from the raid now woks.  Don't know what changed to make it work all the sudden again.

---

