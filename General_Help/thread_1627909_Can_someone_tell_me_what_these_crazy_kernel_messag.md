---
title: "Can someone tell me what these crazy kernel messages are?"
date: 2010-11-22
forum: General Help
---

### Post by victoitor on 2010-11-22
Some background. My system has been crashing consistently since I upgraded to 10.10. I have downloaded 10.04 and I was ready to downgrade as there would be no trace of what made my system crash.

Recently I was reading about the new kernel patch and I did the procedure described here: [http://haineault.com/blog/144/](http://haineault.com/blog/144/)

As I was testing the results, my computer seemed to crash again, but this time the mouse kept moving and the keyboard did not stop responding so I waited. At some point, my system returned to normal. After that, I checked my messages file in the system log and I found some crazy lines relating to some kernel panic. Does anyone know what the hell is it?

--------
```

Nov 22 01:06:26 toobaka kernel: [   21.704260] type=1400 audit(1290398786.699:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1033 comm="apparmor_parser"
Nov 22 01:07:34 toobaka kernel: [   89.888832] lo: Disabled Privacy Extensions
Nov 22 01:22:51 toobaka pulseaudio[1502]: asyncq.c: q overrun, queuing locally
Nov 22 01:23:03 toobaka pulseaudio[1502]: last message repeated 9 times
Nov 22 01:22:56 toobaka pulseaudio[2143]: pid.c: Stale PID file, overwriting.
Nov 22 01:34:05 toobaka kernel: [ 1680.372129] ionice        D f6157c24     0  2257   1802 0x00000000
Nov 22 01:34:05 toobaka kernel: [ 1680.372139]  f6157c34 00200086 00000002 f6157c24 00000008 c05d89e0 c08c3700 c08c3700
Nov 22 01:34:05 toobaka kernel: [ 1680.372155]  07985037 0000015e c08c3700 c08c3700 07963ad8 0000015e 00000000 c08c3700
Nov 22 01:34:05 toobaka kernel: [ 1680.372170]  c08c3700 f710e580 00000001 f710e580 c1c08700 f6157c80 f6157c44 c05c6ec1
Nov 22 01:34:05 toobaka kernel: [ 1680.372185] Call Trace:
Nov 22 01:34:05 toobaka kernel: [ 1680.372202]  [<c05c6ec1>] io_schedule+0x61/0xa0
Nov 22 01:34:05 toobaka kernel: [ 1680.372211]  [<c023d628>] sync_buffer+0x38/0x40
Nov 22 01:34:05 toobaka kernel: [ 1680.372219]  [<c05c768d>] __wait_on_bit+0x4d/0x70
Nov 22 01:34:05 toobaka kernel: [ 1680.372225]  [<c023d5f0>] ? sync_buffer+0x0/0x40
Nov 22 01:34:05 toobaka kernel: [ 1680.372232]  [<c023d5f0>] ? sync_buffer+0x0/0x40
Nov 22 01:34:05 toobaka kernel: [ 1680.372240]  [<c05c775b>] out_of_line_wait_on_bit+0xab/0xc0
Nov 22 01:34:05 toobaka kernel: [ 1680.372249]  [<c0165e60>] ? wake_bit_function+0x0/0x50
Nov 22 01:34:05 toobaka kernel: [ 1680.372256]  [<c023d5ee>] __wait_on_buffer+0x2e/0x30
Nov 22 01:34:05 toobaka kernel: [ 1680.372264]  [<c0277a93>] wait_on_buffer+0x23/0x30
Nov 22 01:34:05 toobaka kernel: [ 1680.372272]  [<c027900e>] __ext3_get_inode_loc+0x23e/0x2d0
Nov 22 01:34:05 toobaka kernel: [ 1680.372281]  [<c022dde5>] ? get_new_inode_fast+0xe5/0x110
Nov 22 01:34:05 toobaka kernel: [ 1680.372288]  [<c027b7ff>] ext3_iget+0x5f/0x400
Nov 22 01:34:05 toobaka kernel: [ 1680.372295]  [<c022ad32>] ? __d_lookup+0x102/0x110
Nov 22 01:34:05 toobaka kernel: [ 1680.372302]  [<c027ec37>] ext3_lookup+0x87/0x100
Nov 22 01:34:05 toobaka kernel: [ 1680.372309]  [<c05c8bdd>] ? _raw_spin_lock+0xd/0x10
Nov 22 01:34:05 toobaka kernel: [ 1680.372316]  [<c022b797>] ? d_alloc+0x117/0x170
Nov 22 01:34:05 toobaka kernel: [ 1680.372324]  [<c022317b>] do_lookup+0x15b/0x1c0
Nov 22 01:34:05 toobaka kernel: [ 1680.372332]  [<c022361d>] do_last+0x24d/0x3a0
Nov 22 01:34:05 toobaka kernel: [ 1680.372339]  [<c02251bd>] do_filp_open+0x19d/0x4c0
Nov 22 01:34:05 toobaka kernel: [ 1680.372347]  [<c021d9e2>] ? get_arg_page+0x52/0xb0
Nov 22 01:34:05 toobaka kernel: [ 1680.372355]  [<c035a39d>] ? _copy_from_user+0x3d/0x130
Nov 22 01:34:05 toobaka kernel: [ 1680.372363]  [<c021f337>] open_exec+0x37/0x130
Nov 22 01:34:05 toobaka kernel: [ 1680.372372]  [<c0253384>] load_script+0x1f4/0x260
Nov 22 01:34:05 toobaka kernel: [ 1680.372380]  [<c01f4c85>] ? get_user_pages+0x55/0x70
Nov 22 01:34:05 toobaka kernel: [ 1680.372387]  [<c021d9e2>] ? get_arg_page+0x52/0xb0
Nov 22 01:34:05 toobaka kernel: [ 1680.372395]  [<c0253190>] ? load_script+0x0/0x260
Nov 22 01:34:05 toobaka kernel: [ 1680.372402]  [<c021f0ed>] search_binary_handler+0xcd/0x2e0
Nov 22 01:34:05 toobaka kernel: [ 1680.372408]  [<c021dbac>] ? copy_strings+0x16c/0x180
Nov 22 01:34:05 toobaka kernel: [ 1680.372416]  [<c021f623>] do_execve+0x1f3/0x2c0
Nov 22 01:34:05 toobaka kernel: [ 1680.372432]  [<c035a1aa>] ? strncpy_from_user+0x3a/0x70
Nov 22 01:34:05 toobaka kernel: [ 1680.372437]  [<c0109d97>] sys_execve+0x37/0x70
Nov 22 01:34:05 toobaka kernel: [ 1680.372441]  [<c010316e>] ptregs_execve+0x12/0x18
Nov 22 01:34:05 toobaka kernel: [ 1680.372445]  [<c05c9114>] ? syscall_call+0x7/0xb
Nov 22 01:36:05 toobaka kernel: [ 1800.372276] gnome-panel   D f4b99e04     0  1506   1435 0x00000000
Nov 22 01:36:05 toobaka kernel: [ 1800.372287]  f4b99e14 00200086 00000002 f4b99e04 f6aafa00 c05d89e0 c08c3700 c08c3700
Nov 22 01:36:05 toobaka kernel: [ 1800.372303]  8a5a7bc1 00000172 c08c3700 c08c3700 8a56df7c 00000172 00000000 c08c3700
Nov 22 01:36:05 toobaka kernel: [ 1800.372317]  c08c3700 f5d8bf70 00000001 f6fb0714 f6fb0718 ffffffff f4b99e40 c05c7ae6
Nov 22 01:36:05 toobaka kernel: [ 1800.372332] Call Trace:
Nov 22 01:36:05 toobaka kernel: [ 1800.372350]  [<c05c7ae6>] __mutex_lock_slowpath+0xd6/0x140
Nov 22 01:36:05 toobaka kernel: [ 1800.372358]  [<c05c79f5>] mutex_lock+0x25/0x40
Nov 22 01:36:05 toobaka kernel: [ 1800.372368]  [<c02230d7>] do_lookup+0xb7/0x1c0
Nov 22 01:36:05 toobaka kernel: [ 1800.372376]  [<c0223be4>] link_path_walk+0x3e4/0x890
Nov 22 01:36:05 toobaka kernel: [ 1800.372384]  [<c02241b1>] path_walk+0x51/0xc0
Nov 22 01:36:05 toobaka kernel: [ 1800.372391]  [<c0224339>] do_path_lookup+0x59/0x90
Nov 22 01:36:05 toobaka kernel: [ 1800.372399]  [<c0224e81>] user_path_at+0x41/0x80
Nov 22 01:36:05 toobaka kernel: [ 1800.372408]  [<c0328e1a>] ? aa_alloc_task_context+0x2a/0xb0
Nov 22 01:36:05 toobaka kernel: [ 1800.372415]  [<c0328dc3>] ? aa_dup_task_context+0x33/0x60
Nov 22 01:36:05 toobaka kernel: [ 1800.372423]  [<c032deb6>] ? apparmor_cred_prepare+0x36/0x50
Nov 22 01:36:05 toobaka kernel: [ 1800.372433]  [<c0302c85>] ? security_prepare_creds+0x15/0x20
Nov 22 01:36:05 toobaka kernel: [ 1800.372441]  [<c016c612>] ? prepare_creds+0x82/0xb0
Nov 22 01:36:05 toobaka kernel: [ 1800.372450]  [<c0217772>] sys_faccessat+0xa2/0x190
Nov 22 01:36:05 toobaka kernel: [ 1800.372457]  [<c0217885>] sys_access+0x25/0x30
Nov 22 01:36:05 toobaka kernel: [ 1800.372465]  [<c05c9114>] syscall_call+0x7/0xb
Nov 22 01:36:05 toobaka kernel: [ 1800.372472]  [<c05c007b>] ? print_cpu_info+0x15/0x129
Nov 22 01:36:05 toobaka kernel: [ 1800.372479]  [<c05c0000>] ? cpu_init+0x207/0x249
Nov 22 01:36:05 toobaka kernel: [ 1800.372689] ionice        D f6157c24     0  2257   1802 0x00000000
Nov 22 01:36:05 toobaka kernel: [ 1800.372698]  f6157c34 00200086 00000002 f6157c24 00000008 c05d89e0 c08c3700 c08c3700
Nov 22 01:36:05 toobaka kernel: [ 1800.372713]  07985037 0000015e c08c3700 c08c3700 07963ad8 0000015e 00000000 c08c3700
Nov 22 01:36:05 toobaka kernel: [ 1800.372727]  c08c3700 f710e580 00000001 f710e580 c1c08700 f6157c80 f6157c44 c05c6ec1
Nov 22 01:36:05 toobaka kernel: [ 1800.372742] Call Trace:
Nov 22 01:36:05 toobaka kernel: [ 1800.372750]  [<c05c6ec1>] io_schedule+0x61/0xa0
Nov 22 01:36:05 toobaka kernel: [ 1800.372758]  [<c023d628>] sync_buffer+0x38/0x40
Nov 22 01:36:05 toobaka kernel: [ 1800.372765]  [<c05c768d>] __wait_on_bit+0x4d/0x70
Nov 22 01:36:05 toobaka kernel: [ 1800.372772]  [<c023d5f0>] ? sync_buffer+0x0/0x40
Nov 22 01:36:05 toobaka kernel: [ 1800.372778]  [<c023d5f0>] ? sync_buffer+0x0/0x40
Nov 22 01:36:05 toobaka kernel: [ 1800.372785]  [<c05c775b>] out_of_line_wait_on_bit+0xab/0xc0
Nov 22 01:36:05 toobaka kernel: [ 1800.372794]  [<c0165e60>] ? wake_bit_function+0x0/0x50
Nov 22 01:36:05 toobaka kernel: [ 1800.372801]  [<c023d5ee>] __wait_on_buffer+0x2e/0x30
Nov 22 01:36:05 toobaka kernel: [ 1800.372808]  [<c0277a93>] wait_on_buffer+0x23/0x30
Nov 22 01:36:05 toobaka kernel: [ 1800.372816]  [<c027900e>] __ext3_get_inode_loc+0x23e/0x2d0
Nov 22 01:36:05 toobaka kernel: [ 1800.372824]  [<c022dde5>] ? get_new_inode_fast+0xe5/0x110
Nov 22 01:36:05 toobaka kernel: [ 1800.372831]  [<c027b7ff>] ext3_iget+0x5f/0x400
Nov 22 01:36:05 toobaka kernel: [ 1800.372838]  [<c022ad32>] ? __d_lookup+0x102/0x110
Nov 22 01:36:05 toobaka kernel: [ 1800.372846]  [<c027ec37>] ext3_lookup+0x87/0x100
Nov 22 01:36:05 toobaka kernel: [ 1800.372852]  [<c05c8bdd>] ? _raw_spin_lock+0xd/0x10
Nov 22 01:36:05 toobaka kernel: [ 1800.372858]  [<c022b797>] ? d_alloc+0x117/0x170
Nov 22 01:36:05 toobaka kernel: [ 1800.372866]  [<c022317b>] do_lookup+0x15b/0x1c0
Nov 22 01:36:05 toobaka kernel: [ 1800.372873]  [<c022361d>] do_last+0x24d/0x3a0
Nov 22 01:36:05 toobaka kernel: [ 1800.372881]  [<c02251bd>] do_filp_open+0x19d/0x4c0
Nov 22 01:36:05 toobaka kernel: [ 1800.372889]  [<c021d9e2>] ? get_arg_page+0x52/0xb0
Nov 22 01:36:05 toobaka kernel: [ 1800.372896]  [<c035a39d>] ? _copy_from_user+0x3d/0x130
Nov 22 01:36:05 toobaka kernel: [ 1800.372904]  [<c021f337>] open_exec+0x37/0x130
Nov 22 01:36:05 toobaka kernel: [ 1800.372912]  [<c0253384>] load_script+0x1f4/0x260
Nov 22 01:36:05 toobaka kernel: [ 1800.372921]  [<c01f4c85>] ? get_user_pages+0x55/0x70
Nov 22 01:36:05 toobaka kernel: [ 1800.372928]  [<c021d9e2>] ? get_arg_page+0x52/0xb0
Nov 22 01:36:05 toobaka kernel: [ 1800.372935]  [<c0253190>] ? load_script+0x0/0x260
Nov 22 01:36:05 toobaka kernel: [ 1800.372942]  [<c021f0ed>] search_binary_handler+0xcd/0x2e0
Nov 22 01:36:05 toobaka kernel: [ 1800.372948]  [<c021dbac>] ? copy_strings+0x16c/0x180
Nov 22 01:36:05 toobaka kernel: [ 1800.372956]  [<c021f623>] do_execve+0x1f3/0x2c0
Nov 22 01:36:05 toobaka kernel: [ 1800.372962]  [<c035a1aa>] ? strncpy_from_user+0x3a/0x70
Nov 22 01:36:05 toobaka kernel: [ 1800.372971]  [<c0109d97>] sys_execve+0x37/0x70
Nov 22 01:36:05 toobaka kernel: [ 1800.372978]  [<c010316e>] ptregs_execve+0x12/0x18
Nov 22 01:36:05 toobaka kernel: [ 1800.372985]  [<c05c9114>] ? syscall_call+0x7/0xb
Nov 22 01:36:05 toobaka kernel: [ 1800.373183] metacity      D ed011de4     0  2263   1499 0x00000000
Nov 22 01:36:05 toobaka kernel: [ 1800.373192]  ed011df4 00000086 00000002 ed011de4 f6aafa00 c05d89e0 c08c3700 c08c3700
Nov 22 01:36:05 toobaka kernel: [ 1800.373207]  90e80522 0000016e c08c3700 c08c3700 90df609b 0000016e 00000000 c08c3700
Nov 22 01:36:05 toobaka kernel: [ 1800.373221]  c08c3700 f5d10000 00000001 f6fb0714 f6fb0718 ffffffff ed011e20 c05c7ae6
Nov 22 01:36:05 toobaka kernel: [ 1800.373236] Call Trace:
Nov 22 01:36:05 toobaka kernel: [ 1800.373244]  [<c05c7ae6>] __mutex_lock_slowpath+0xd6/0x140
Nov 22 01:36:05 toobaka kernel: [ 1800.373252]  [<c05c79f5>] mutex_lock+0x25/0x40
Nov 22 01:36:05 toobaka kernel: [ 1800.373259]  [<c02230d7>] do_lookup+0xb7/0x1c0
Nov 22 01:36:05 toobaka kernel: [ 1800.373267]  [<c022361d>] do_last+0x24d/0x3a0
Nov 22 01:36:05 toobaka kernel: [ 1800.373274]  [<c02251bd>] do_filp_open+0x19d/0x4c0
Nov 22 01:36:05 toobaka kernel: [ 1800.373283]  [<c0328dc3>] ? aa_dup_task_context+0x33/0x60
Nov 22 01:36:05 toobaka kernel: [ 1800.373290]  [<c032deb6>] ? apparmor_cred_prepare+0x36/0x50
Nov 22 01:36:05 toobaka kernel: [ 1800.373299]  [<c0302c85>] ? security_prepare_creds+0x15/0x20
Nov 22 01:36:05 toobaka kernel: [ 1800.373306]  [<c021f337>] open_exec+0x37/0x130
Nov 22 01:36:05 toobaka kernel: [ 1800.373313]  [<c021dcf3>] ? check_unsafe_exec+0x43/0xe0
Nov 22 01:36:05 toobaka kernel: [ 1800.373320]  [<c021f4ec>] do_execve+0xbc/0x2c0
Nov 22 01:36:05 toobaka kernel: [ 1800.373327]  [<c035a1aa>] ? strncpy_from_user+0x3a/0x70
Nov 22 01:36:05 toobaka kernel: [ 1800.373335]  [<c0109d97>] sys_execve+0x37/0x70
Nov 22 01:36:05 toobaka kernel: [ 1800.373341]  [<c010316e>] ptregs_execve+0x12/0x18
Nov 22 01:36:05 toobaka kernel: [ 1800.373348]  [<c05c9114>] ? syscall_call+0x7/0xb
Nov 22 01:36:05 toobaka kernel: [ 1800.373355]  [<c05c0000>] ? cpu_init+0x207/0x249
Nov 22 01:36:05 toobaka kernel: [ 1800.373542] which         D ef83fdbc     0  2264   1978 0x00000000
Nov 22 01:36:05 toobaka kernel: [ 1800.373550]  ef83fdcc 00000086 00000002 ef83fdbc f6aafa00 c05d89e0 c08c3700 c08c3700
Nov 22 01:36:05 toobaka kernel: [ 1800.373565]  ed5f57b9 00000177 c08c3700 c08c3700 ed5166be 00000177 00000000 c08c3700
Nov 22 01:36:05 toobaka kernel: [ 1800.373579]  c08c3700 f5d13f70 00000001 f6fb0714 f6fb0718 ffffffff ef83fdf8 c05c7ae6
Nov 22 01:36:05 toobaka kernel: [ 1800.373594] Call Trace:
Nov 22 01:36:05 toobaka kernel: [ 1800.373602]  [<c05c7ae6>] __mutex_lock_slowpath+0xd6/0x140
Nov 22 01:36:05 toobaka kernel: [ 1800.373610]  [<c05c79f5>] mutex_lock+0x25/0x40
Nov 22 01:36:05 toobaka kernel: [ 1800.373617]  [<c02230d7>] do_lookup+0xb7/0x1c0
Nov 22 01:36:05 toobaka kernel: [ 1800.373625]  [<c0223be4>] link_path_walk+0x3e4/0x890
Nov 22 01:36:05 toobaka kernel: [ 1800.373633]  [<c01d99c2>] ? find_get_page+0x22/0xa0
Nov 22 01:36:05 toobaka kernel: [ 1800.373640]  [<c02241b1>] path_walk+0x51/0xc0
Nov 22 01:36:05 toobaka kernel: [ 1800.373648]  [<c0224339>] do_path_lookup+0x59/0x90
Nov 22 01:36:05 toobaka kernel: [ 1800.373655]  [<c0224e81>] user_path_at+0x41/0x80
Nov 22 01:36:05 toobaka kernel: [ 1800.373662]  [<c01f4536>] ? handle_mm_fault+0x146/0x400
Nov 22 01:36:05 toobaka kernel: [ 1800.373669]  [<c021c9da>] vfs_fstatat+0x3a/0x70
Nov 22 01:36:05 toobaka kernel: [ 1800.373677]  [<c05cc46d>] ? do_page_fault+0x1cd/0x440
Nov 22 01:36:05 toobaka kernel: [ 1800.373684]  [<c021cb30>] vfs_stat+0x20/0x30
Nov 22 01:36:05 toobaka kernel: [ 1800.373690]  [<c021cb59>] sys_stat64+0x19/0x30
Nov 22 01:36:05 toobaka kernel: [ 1800.373698]  [<c0218e85>] ? vfs_read+0x125/0x190
Nov 22 01:36:05 toobaka kernel: [ 1800.373705]  [<c0218490>] ? do_sync_read+0x0/0xe0
Nov 22 01:36:05 toobaka kernel: [ 1800.373712]  [<c0218f32>] ? sys_read+0x42/0x70
Nov 22 01:36:05 toobaka kernel: [ 1800.373719]  [<c05c9114>] syscall_call+0x7/0xb
Nov 22 01:40:05 toobaka kernel: [ 2040.372129] apt-check     D f6157ddc     0  2257   1802 0x00000000
Nov 22 01:40:05 toobaka kernel: [ 2040.372140]  f6157dec 00200086 00000002 f6157ddc c0279b70 c05d89e0 c08c3700 c08c3700
Nov 22 01:40:05 toobaka kernel: [ 2040.372155]  aaab07f2 000001ae c08c3700 c08c3700 aaa7fc86 000001ae 00000000 c08c3700
Nov 22 01:40:05 toobaka kernel: [ 2040.372170]  c08c3700 f710e580 00000001 f710e580 c1c08700 f6157e38 f6157dfc c05c6ec1
Nov 22 01:40:05 toobaka kernel: [ 2040.372193] Call Trace:
Nov 22 01:40:05 toobaka kernel: [ 2040.372206]  [<c0279b70>] ? ext3_get_block+0x0/0x100
Nov 22 01:40:05 toobaka kernel: [ 2040.372215]  [<c05c6ec1>] io_schedule+0x61/0xa0
Nov 22 01:40:05 toobaka kernel: [ 2040.372221]  [<c01d9c4d>] sync_page+0x3d/0x50
Nov 22 01:40:05 toobaka kernel: [ 2040.372227]  [<c05c7537>] __wait_on_bit_lock+0x47/0x90
Nov 22 01:40:05 toobaka kernel: [ 2040.372232]  [<c0278580>] ? ext3_readpages+0x0/0x20
Nov 22 01:40:05 toobaka kernel: [ 2040.372237]  [<c01d9c10>] ? sync_page+0x0/0x50
Nov 22 01:40:05 toobaka kernel: [ 2040.372242]  [<c01d9bde>] __lock_page+0x7e/0x90
Nov 22 01:40:05 toobaka kernel: [ 2040.372249]  [<c0165e60>] ? wake_bit_function+0x0/0x50
Nov 22 01:40:05 toobaka kernel: [ 2040.372254]  [<c01db296>] find_lock_page+0x56/0x70
Nov 22 01:40:05 toobaka kernel: [ 2040.372259]  [<c01db4f9>] filemap_fault+0x199/0x400
Nov 22 01:40:05 toobaka kernel: [ 2040.372266]  [<c01f2570>] __do_fault+0x40/0x570
Nov 22 01:40:05 toobaka kernel: [ 2040.372271]  [<c01f4536>] handle_mm_fault+0x146/0x400
Nov 22 01:40:05 toobaka kernel: [ 2040.372278]  [<c05cc3e6>] do_page_fault+0x146/0x440
Nov 22 01:40:05 toobaka kernel: [ 2040.372284]  [<c01f8efb>] ? sys_mmap_pgoff+0x12b/0x1c0
Nov 22 01:40:05 toobaka kernel: [ 2040.372290]  [<c05cc2a0>] ? do_page_fault+0x0/0x440
Nov 22 01:40:05 toobaka kernel: [ 2040.372295]  [<c05c9817>] error_code+0x73/0x78
Nov 22 01:40:05 toobaka kernel: [ 2040.372307] lsb_release   D 00000000     0  2293   2288 0x00000000
Nov 22 01:40:05 toobaka kernel: [ 2040.372314]  ed143e00 00000086 f6273f70 00000000 f7138000 c0132d1d c08c3700 c08c3700
Nov 22 01:40:05 toobaka kernel: [ 2040.372325]  d355ff47 000001ae c08c3700 c08c3700 00000000 000001ae 00000000 c08c3700
Nov 22 01:40:05 toobaka kernel: [ 2040.372336]  c08c3700 f6273f70 01345000 f6273f70 c1c08700 ed143e4c ed143e10 c05c6ec1
Nov 22 01:40:05 toobaka kernel: [ 2040.372346] Call Trace:
Nov 22 01:40:05 toobaka kernel: [ 2040.372352]  [<c0132d1d>] ? kmap_atomic_prot+0xcd/0xf0
Nov 22 01:40:05 toobaka kernel: [ 2040.372359]  [<c05c6ec1>] io_schedule+0x61/0xa0
Nov 22 01:40:05 toobaka kernel: [ 2040.372364]  [<c01d9c4d>] sync_page+0x3d/0x50
Nov 22 01:40:05 toobaka kernel: [ 2040.372369]  [<c05c7537>] __wait_on_bit_lock+0x47/0x90
Nov 22 01:40:05 toobaka kernel: [ 2040.372376]  [<c03536e4>] ? prio_tree_remove+0x94/0xe0
Nov 22 01:40:05 toobaka kernel: [ 2040.372381]  [<c01d9c10>] ? sync_page+0x0/0x50
Nov 22 01:40:05 toobaka kernel: [ 2040.372386]  [<c01d9bde>] __lock_page+0x7e/0x90
Nov 22 01:40:05 toobaka kernel: [ 2040.372391]  [<c0165e60>] ? wake_bit_function+0x0/0x50
Nov 22 01:40:05 toobaka kernel: [ 2040.372396]  [<c01db6f1>] filemap_fault+0x391/0x400
Nov 22 01:40:05 toobaka kernel: [ 2040.372401]  [<c01f24c9>] ? free_pgtables+0xb9/0xf0
Nov 22 01:40:05 toobaka kernel: [ 2040.372406]  [<c01f2570>] __do_fault+0x40/0x570
Nov 22 01:40:05 toobaka kernel: [ 2040.372412]  [<c01f67f0>] ? __vma_link_file+0x40/0x70
Nov 22 01:40:05 toobaka kernel: [ 2040.372417]  [<c01f4536>] handle_mm_fault+0x146/0x400
Nov 22 01:40:05 toobaka kernel: [ 2040.372423]  [<c05cc3e6>] do_page_fault+0x146/0x440
Nov 22 01:40:05 toobaka kernel: [ 2040.372428]  [<c01f8efb>] ? sys_mmap_pgoff+0x12b/0x1c0
Nov 22 01:40:05 toobaka kernel: [ 2040.372434]  [<c05cc2a0>] ? do_page_fault+0x0/0x440
Nov 22 01:40:05 toobaka kernel: [ 2040.372439]  [<c05c9817>] error_code+0x73/0x78
Nov 22 01:42:05 toobaka kernel: [ 2160.372111] apt-check     D f6157ddc     0  2257   1802 0x00000000
Nov 22 01:42:05 toobaka kernel: [ 2160.372121]  f6157dec 00200086 00000002 f6157ddc c0279b70 c05d89e0 c08c3700 c08c3700
Nov 22 01:42:05 toobaka kernel: [ 2160.372137]  aaab07f2 000001ae c08c3700 c08c3700 aaa7fc86 000001ae 00000000 c08c3700
Nov 22 01:42:05 toobaka kernel: [ 2160.372152]  c08c3700 f710e580 00000001 f710e580 c1c08700 f6157e38 f6157dfc c05c6ec1
Nov 22 01:42:05 toobaka kernel: [ 2160.372167] Call Trace:
Nov 22 01:42:05 toobaka kernel: [ 2160.372191]  [<c0279b70>] ? ext3_get_block+0x0/0x100
Nov 22 01:42:05 toobaka kernel: [ 2160.372200]  [<c05c6ec1>] io_schedule+0x61/0xa0
Nov 22 01:42:05 toobaka kernel: [ 2160.372206]  [<c01d9c4d>] sync_page+0x3d/0x50
Nov 22 01:42:05 toobaka kernel: [ 2160.372212]  [<c05c7537>] __wait_on_bit_lock+0x47/0x90
Nov 22 01:42:05 toobaka kernel: [ 2160.372217]  [<c0278580>] ? ext3_readpages+0x0/0x20
Nov 22 01:42:05 toobaka kernel: [ 2160.372222]  [<c01d9c10>] ? sync_page+0x0/0x50
Nov 22 01:42:05 toobaka kernel: [ 2160.372227]  [<c01d9bde>] __lock_page+0x7e/0x90
Nov 22 01:42:05 toobaka kernel: [ 2160.372234]  [<c0165e60>] ? wake_bit_function+0x0/0x50
Nov 22 01:42:05 toobaka kernel: [ 2160.372240]  [<c01db296>] find_lock_page+0x56/0x70
Nov 22 01:42:05 toobaka kernel: [ 2160.372245]  [<c01db4f9>] filemap_fault+0x199/0x400
Nov 22 01:42:05 toobaka kernel: [ 2160.372251]  [<c01f2570>] __do_fault+0x40/0x570
Nov 22 01:42:05 toobaka kernel: [ 2160.372257]  [<c01f4536>] handle_mm_fault+0x146/0x400
Nov 22 01:42:05 toobaka kernel: [ 2160.372263]  [<c05cc3e6>] do_page_fault+0x146/0x440
Nov 22 01:42:05 toobaka kernel: [ 2160.372270]  [<c01f8efb>] ? sys_mmap_pgoff+0x12b/0x1c0
Nov 22 01:42:05 toobaka kernel: [ 2160.372275]  [<c05cc2a0>] ? do_page_fault+0x0/0x440
Nov 22 01:42:05 toobaka kernel: [ 2160.372280]  [<c05c9817>] error_code+0x73/0x78
Nov 22 01:42:05 toobaka kernel: [ 2160.372292] lsb_release   D 00000000     0  2293   2288 0x00000000
Nov 22 01:42:05 toobaka kernel: [ 2160.372299]  ed143e00 00000086 f6273f70 00000000 f7138000 c0132d1d c08c3700 c08c3700
Nov 22 01:42:05 toobaka kernel: [ 2160.372310]  d355ff47 000001ae c08c3700 c08c3700 00000000 000001ae 00000000 c08c3700
Nov 22 01:42:05 toobaka kernel: [ 2160.372321]  c08c3700 f6273f70 01345000 f6273f70 c1c08700 ed143e4c ed143e10 c05c6ec1
Nov 22 01:42:05 toobaka kernel: [ 2160.372331] Call Trace:
Nov 22 01:42:05 toobaka kernel: [ 2160.372337]  [<c0132d1d>] ? kmap_atomic_prot+0xcd/0xf0
Nov 22 01:42:05 toobaka kernel: [ 2160.372344]  [<c05c6ec1>] io_schedule+0x61/0xa0
Nov 22 01:42:05 toobaka kernel: [ 2160.372348]  [<c01d9c4d>] sync_page+0x3d/0x50
Nov 22 01:42:05 toobaka kernel: [ 2160.372361]  [<c05c7537>] __wait_on_bit_lock+0x47/0x90
Nov 22 01:42:05 toobaka kernel: [ 2160.372367]  [<c03536e4>] ? prio_tree_remove+0x94/0xe0
Nov 22 01:42:05 toobaka kernel: [ 2160.372372]  [<c01d9c10>] ? sync_page+0x0/0x50
Nov 22 01:42:05 toobaka kernel: [ 2160.372377]  [<c01d9bde>] __lock_page+0x7e/0x90
Nov 22 01:42:05 toobaka kernel: [ 2160.372383]  [<c0165e60>] ? wake_bit_function+0x0/0x50
Nov 22 01:42:05 toobaka kernel: [ 2160.372388]  [<c01db6f1>] filemap_fault+0x391/0x400
Nov 22 01:42:05 toobaka kernel: [ 2160.372393]  [<c01f24c9>] ? free_pgtables+0xb9/0xf0
Nov 22 01:42:05 toobaka kernel: [ 2160.372398]  [<c01f2570>] __do_fault+0x40/0x570
Nov 22 01:42:05 toobaka kernel: [ 2160.372403]  [<c01f67f0>] ? __vma_link_file+0x40/0x70
Nov 22 01:42:05 toobaka kernel: [ 2160.372408]  [<c01f4536>] handle_mm_fault+0x146/0x400
Nov 22 01:42:05 toobaka kernel: [ 2160.372414]  [<c05cc3e6>] do_page_fault+0x146/0x440
Nov 22 01:42:05 toobaka kernel: [ 2160.372420]  [<c01f8efb>] ? sys_mmap_pgoff+0x12b/0x1c0
Nov 22 01:42:05 toobaka kernel: [ 2160.372426]  [<c05cc2a0>] ? do_page_fault+0x0/0x440
Nov 22 01:42:05 toobaka kernel: [ 2160.372431]  [<c05c9817>] error_code+0x73/0x78
Nov 22 01:44:05 toobaka kernel: [ 2280.372080] apt-check     D f6157ddc     0  2257   1802 0x00000000
Nov 22 01:44:05 toobaka kernel: [ 2280.372086]  f6157dec 00200086 00000002 f6157ddc c0279b70 c05d89e0 c08c3700 c08c3700
Nov 22 01:44:05 toobaka kernel: [ 2280.372094]  aaab07f2 000001ae c08c3700 c08c3700 aaa7fc86 000001ae 00000000 c08c3700
Nov 22 01:44:05 toobaka kernel: [ 2280.372103]  c08c3700 f710e580 00000001 f710e580 c1c08700 f6157e38 f6157dfc c05c6ec1
Nov 22 01:44:05 toobaka kernel: [ 2280.372111] Call Trace:
Nov 22 01:44:05 toobaka kernel: [ 2280.372121]  [<c0279b70>] ? ext3_get_block+0x0/0x100
Nov 22 01:44:05 toobaka kernel: [ 2280.372128]  [<c05c6ec1>] io_schedule+0x61/0xa0
Nov 22 01:44:05 toobaka kernel: [ 2280.372132]  [<c01d9c4d>] sync_page+0x3d/0x50
Nov 22 01:44:05 toobaka kernel: [ 2280.372137]  [<c05c7537>] __wait_on_bit_lock+0x47/0x90
Nov 22 01:44:05 toobaka kernel: [ 2280.372141]  [<c0278580>] ? ext3_readpages+0x0/0x20
Nov 22 01:44:05 toobaka kernel: [ 2280.372144]  [<c01d9c10>] ? sync_page+0x0/0x50
Nov 22 01:44:05 toobaka kernel: [ 2280.372148]  [<c01d9bde>] __lock_page+0x7e/0x90
Nov 22 01:44:05 toobaka kernel: [ 2280.372153]  [<c0165e60>] ? wake_bit_function+0x0/0x50
Nov 22 01:44:05 toobaka kernel: [ 2280.372157]  [<c01db296>] find_lock_page+0x56/0x70
Nov 22 01:44:05 toobaka kernel: [ 2280.372161]  [<c01db4f9>] filemap_fault+0x199/0x400
Nov 22 01:44:05 toobaka kernel: [ 2280.372166]  [<c01f2570>] __do_fault+0x40/0x570
Nov 22 01:44:05 toobaka kernel: [ 2280.372170]  [<c01f4536>] handle_mm_fault+0x146/0x400
Nov 22 01:44:05 toobaka kernel: [ 2280.372175]  [<c05cc3e6>] do_page_fault+0x146/0x440
Nov 22 01:44:05 toobaka kernel: [ 2280.372180]  [<c01f8efb>] ? sys_mmap_pgoff+0x12b/0x1c0
Nov 22 01:44:05 toobaka kernel: [ 2280.372184]  [<c05cc2a0>] ? do_page_fault+0x0/0x440
Nov 22 01:44:05 toobaka kernel: [ 2280.372188]  [<c05c9817>] error_code+0x73/0x78

```

---

### Post by wilee-nilee on 2010-11-22
Look in my signature and follow how to put code tags at the beginning and end of all that text. It will likely get you help sooner if any is available.;)

---

### Post by dcstar on 2010-11-22
> **victoitor said:**
> Some background. My system has been crashing consistently since I upgraded to 10.10. I have downloaded 10.04 and I was ready to downgrade as there would be no trace of what made my system crash.

Recently I was reading about the new kernel patch and I did the procedure described here: [http://haineault.com/blog/144/](http://haineault.com/blog/144/)
.........

That patch clearly has **nothing** to do with crashing systems, it is a performance response patch. Why on earth stuff around with things that are totally irrelevant to the problem you have?

---

### Post by victoitor on 2010-11-22
> **dcstar said:**
> That patch clearly has **nothing** to do with crashing systems, it is a performance response patch. Why on earth stuff around with things that are totally irrelevant to the problem you have?

I've been having a huge amount of problems with 10.10. Constant crashing is not the only one. I was messing around with this patch because of two reasons. First, I was about to torch 10.10 from my machine, so why not play around with it before I did so? The second reason is that I always felt the linux scheduler was really bad and suffered from interactivity problems. When I saw how easy it was to install this fix, I just had to do it.

---

### Post by dcstar on 2010-11-23
> **victoitor said:**
> I've been having a huge amount of problems with 10.10. Constant crashing is not the only one. I was messing around with this patch because of two reasons. First, I was about to torch 10.10 from my machine, so why not play around with it before I did so? The second reason is that I always felt the linux scheduler was really bad and suffered from interactivity problems. When I saw how easy it was to install this fix, I just had to do it.

You risk "muddying the waters" of trying to find your underlying problem by trying to address one particular symptom.

If your system crashes constantly you should do things like boot to memtest and run tests for hours on end to prove that the hardware is stable.

The Linux scheduler works fine in the vast majority of installs, it is only in that small percentage of installs with the disk I/O issue that this patch seems to help (and I have found it very effective for this specific issue).

---

### Post by victoitor on 2010-11-23
> **dcstar said:**
> You risk "muddying the waters" of trying to find your underlying problem by trying to address one particular symptom.

If your system crashes constantly you should do things like boot to memtest and run tests for hours on end to prove that the hardware is stable.

The Linux scheduler works fine in the vast majority of installs, it is only in that small percentage of installs with the disk I/O issue that this patch seems to help (and I have found it very effective for this specific issue).

I've run the memtest already for hours on end. I kept thinking it was a hardware issue until I noticed many other people complaining of the same problem. My mom's computer is also suffering with so many problems as soon as she upgraded to 10.10.

By the way, I didn't know of this IO issue. Do you have a link where I can read more about it?

---

