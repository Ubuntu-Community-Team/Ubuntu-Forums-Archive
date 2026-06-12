---
title: "Why does the oom-killer run? I have plenty of swap..."
date: 2010-02-23
forum: General Help
---

### Post by janerikdahlin on 2010-02-23
Ever since I upgraded to Karmic I've had problems with processes that just die when the machine is under a heavy load. Digging through the logs I found that the oom-killer was the culprit. In desperation I sacrificed a disk partition and added it as swap, but that didn't help. As you can see in the log, I still had 33946176kB free swap when the oom-killer was invoked.

Why is the oom-killer invoked and what can I do to stop it?

Any help appreciated.

```

Feb 23 16:10:58 dalburk kernel: [1223639.929720] rhythmbox invoked oom-killer: gfp_mask=0x44d0, order=2, oomkilladj=0
Feb 23 16:11:00 dalburk kernel: [1223639.929724] rhythmbox cpuset=/ mems_allowed=0
Feb 23 16:11:00 dalburk kernel: [1223639.929728] Pid: 1343, comm: rhythmbox Tainted: P         C 2.6.31-19-generic #56-Ubuntu
Feb 23 16:11:00 dalburk kernel: [1223639.929730] Call Trace:
Feb 23 16:11:00 dalburk kernel: [1223639.929739]  [<c01b594f>] oom_kill_process+0x9f/0x250
Feb 23 16:11:00 dalburk kernel: [1223639.929742]  [<c01b5f5e>] ? select_bad_process+0xbe/0xf0
Feb 23 16:11:00 dalburk kernel: [1223639.929745]  [<c01b5fe1>] __out_of_memory+0x51/0xa0
Feb 23 16:11:00 dalburk kernel: [1223639.929748]  [<c01b6083>] out_of_memory+0x53/0xb0
Feb 23 16:11:00 dalburk kernel: [1223639.929751]  [<c01b834e>] __alloc_pages_slowpath+0x42e/0x480
Feb 23 16:11:00 dalburk kernel: [1223639.929754]  [<c01b84af>] __alloc_pages_nodemask+0x10f/0x120
Feb 23 16:11:00 dalburk kernel: [1223639.929758]  [<c01b8507>] __get_free_pages+0x17/0x30
Feb 23 16:11:00 dalburk kernel: [1223639.929762]  [<c01e08d8>] __kmalloc_track_caller+0xd8/0x180
Feb 23 16:11:00 dalburk kernel: [1223639.929766]  [<c049410d>] ? __alloc_skb+0x2d/0x130
Feb 23 16:11:00 dalburk kernel: [1223639.929769]  [<c04905ce>] ? sock_alloc_send_pskb+0x14e/0x270
Feb 23 16:11:00 dalburk kernel: [1223639.929771]  [<c049412d>] __alloc_skb+0x4d/0x130
Feb 23 16:11:00 dalburk kernel: [1223639.929774]  [<c04905ce>] sock_alloc_send_pskb+0x14e/0x270
Feb 23 16:11:00 dalburk kernel: [1223639.929778]  [<c0490708>] sock_alloc_send_skb+0x18/0x20
Feb 23 16:11:00 dalburk kernel: [1223639.929782]  [<c050e2d6>] unix_stream_sendmsg+0x236/0x380
Feb 23 16:11:00 dalburk kernel: [1223639.929785]  [<c04829b4>] ? aa_cred_policy+0x14/0x30
Feb 23 16:11:00 dalburk kernel: [1223639.929788]  [<c048f25b>] sock_aio_write+0x10b/0x120
Feb 23 16:11:00 dalburk kernel: [1223639.929792]  [<c01e7735>] do_sync_readv_writev+0xb5/0xf0
Feb 23 16:11:00 dalburk kernel: [1223639.929796]  [<c013d319>] ? enqueue_entity+0xc9/0x140
Feb 23 16:11:00 dalburk kernel: [1223639.929800]  [<c015c0f0>] ? autoremove_wake_function+0x0/0x40
Feb 23 16:11:00 dalburk kernel: [1223639.929805]  [<c02c81ef>] ? security_file_permission+0xf/0x20
Feb 23 16:11:00 dalburk kernel: [1223639.929808]  [<c01e79cf>] ? rw_verify_area+0x5f/0xe0
Feb 23 16:11:00 dalburk kernel: [1223639.929811]  [<c01e7e18>] ? rw_copy_check_uvector+0x78/0xf0
Feb 23 16:11:00 dalburk kernel: [1223639.929814]  [<c01e877c>] do_readv_writev+0x9c/0x1c0
Feb 23 16:11:00 dalburk kernel: [1223639.929816]  [<c048f150>] ? sock_aio_write+0x0/0x120
Feb 23 16:11:00 dalburk kernel: [1223639.929820]  [<c015fdd3>] ? hrtimer_interrupt+0x183/0x210
Feb 23 16:11:00 dalburk kernel: [1223639.929823]  [<c01e88e5>] vfs_writev+0x45/0x60
Feb 23 16:11:00 dalburk kernel: [1223639.929826]  [<c01e89ed>] sys_writev+0x3d/0xa0
Feb 23 16:11:00 dalburk kernel: [1223639.929829]  [<c010336c>] syscall_call+0x7/0xb
Feb 23 16:11:00 dalburk kernel: [1223639.929831] Mem-Info:
Feb 23 16:11:00 dalburk kernel: [1223639.929832] DMA per-cpu:
Feb 23 16:11:00 dalburk kernel: [1223639.929834] CPU    0: hi:    0, btch:   1 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223639.929836] CPU    1: hi:    0, btch:   1 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223639.929838] CPU    2: hi:    0, btch:   1 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223639.929840] CPU    3: hi:    0, btch:   1 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223639.929841] Normal per-cpu:
Feb 23 16:11:00 dalburk kernel: [1223639.929843] CPU    0: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223639.929845] CPU    1: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223639.929847] CPU    2: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223639.929849] CPU    3: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223639.929850] HighMem per-cpu:
Feb 23 16:11:00 dalburk kernel: [1223639.929852] CPU    0: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223639.929854] CPU    1: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223639.929856] CPU    2: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223639.929857] CPU    3: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223639.929861] Active_anon:211446 active_file:34553 inactive_anon:102677
Feb 23 16:11:00 dalburk kernel: [1223639.929862]  inactive_file:267012 unevictable:42862 dirty:298 writeback:11 unstable:0
Feb 23 16:11:00 dalburk kernel: [1223639.929863]  free:34735 slab:43770 mapped:56338 pagetables:2031 bounce:0
Feb 23 16:11:00 dalburk kernel: [1223639.929867] DMA free:3488kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:20kB inactive_file:0kB unevictable:0kB present:15852kB pages_scanned:0 all_unreclaimable? no
Feb 23 16:11:00 dalburk kernel: [1223639.929869] lowmem_reserve[]: 0 865 3523 3523
Feb 23 16:11:00 dalburk kernel: [1223639.929875] Normal free:42024kB min:3728kB low:4660kB high:5592kB active_anon:8kB inactive_anon:36kB active_file:288kB inactive_file:1152kB unevictable:74780kB present:885944kB pages_scanned:0 all_unreclaimable? no
Feb 23 16:11:00 dalburk kernel: [1223639.929877] lowmem_reserve[]: 0 0 21270 21270
Feb 23 16:11:00 dalburk kernel: [1223639.929883] HighMem free:93428kB min:512kB low:3376kB high:6240kB active_anon:845776kB inactive_anon:410672kB active_file:137904kB inactive_file:1066896kB unevictable:96668kB present:2722564kB pages_scanned:0 all_unreclaimable? no
Feb 23 16:11:00 dalburk kernel: [1223639.929886] lowmem_reserve[]: 0 0 0 0
Feb 23 16:11:00 dalburk kernel: [1223639.929890] DMA: 9*4kB 45*8kB 31*16kB 12*32kB 1*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 3516kB
Feb 23 16:11:00 dalburk kernel: [1223639.929899] Normal: 10419*4kB 51*8kB 8*16kB 0*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 42276kB
Feb 23 16:11:00 dalburk kernel: [1223639.929908] HighMem: 588*4kB 90*8kB 4404*16kB 606*32kB 8*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 93440kB
Feb 23 16:11:00 dalburk kernel: [1223639.929917] 329412 total pagecache pages
Feb 23 16:11:00 dalburk kernel: [1223639.929919] 12936 pages in swap cache
Feb 23 16:11:00 dalburk kernel: [1223639.929921] Swap cache stats: add 18900032, delete 18887096, find 2623219/3507137
Feb 23 16:11:00 dalburk kernel: [1223639.929923] Free swap  = 33946176kB
Feb 23 16:11:00 dalburk kernel: [1223639.929924] Total swap = 34178176kB
Feb 23 16:11:00 dalburk kernel: [1223639.939328] 913327 pages RAM
Feb 23 16:11:00 dalburk kernel: [1223639.939331] 686001 pages HighMem
Feb 23 16:11:00 dalburk kernel: [1223639.939333] 34428 pages reserved
Feb 23 16:11:00 dalburk kernel: [1223639.939334] 270468 pages shared
Feb 23 16:11:00 dalburk kernel: [1223639.939335] 614074 pages non-shared
Feb 23 16:11:00 dalburk kernel: [1223639.939338] Out of memory: kill process 19735 (VBoxSVC) score 2136105 or a child
Feb 23 16:11:00 dalburk kernel: [1223639.939389] Killed process 19776 (VirtualBox)
Feb 23 16:11:00 dalburk kernel: [1223640.048034] device eth0 left promiscuous mode
Feb 23 16:11:00 dalburk kernel: [1223641.265911] rsyslogd invoked oom-killer: gfp_mask=0xd0, order=1, oomkilladj=0
Feb 23 16:11:00 dalburk kernel: [1223641.265917] rsyslogd cpuset=/ mems_allowed=0
Feb 23 16:11:00 dalburk kernel: [1223641.265922] Pid: 1034, comm: rsyslogd Tainted: P         C 2.6.31-19-generic #56-Ubuntu
Feb 23 16:11:00 dalburk kernel: [1223641.265926] Call Trace:
Feb 23 16:11:00 dalburk kernel: [1223641.265936]  [<c01b594f>] oom_kill_process+0x9f/0x250
Feb 23 16:11:00 dalburk kernel: [1223641.265941]  [<c01b5f5e>] ? select_bad_process+0xbe/0xf0
Feb 23 16:11:00 dalburk kernel: [1223641.265945]  [<c01b5fe1>] __out_of_memory+0x51/0xa0
Feb 23 16:11:00 dalburk kernel: [1223641.265950]  [<c01b6083>] out_of_memory+0x53/0xb0
Feb 23 16:11:00 dalburk kernel: [1223641.265954]  [<c01b834e>] __alloc_pages_slowpath+0x42e/0x480
Feb 23 16:11:00 dalburk kernel: [1223641.265959]  [<c01b84af>] __alloc_pages_nodemask+0x10f/0x120
Feb 23 16:11:00 dalburk kernel: [1223641.265964]  [<c01b8507>] __get_free_pages+0x17/0x30
Feb 23 16:11:00 dalburk kernel: [1223641.265969]  [<c0142b60>] dup_task_struct+0x40/0xe0
Feb 23 16:11:00 dalburk kernel: [1223641.265974]  [<c0143918>] copy_process+0x68/0xcb0
Feb 23 16:11:00 dalburk kernel: [1223641.265978]  [<c01446de>] do_fork+0x7e/0x3a0
Feb 23 16:11:00 dalburk kernel: [1223641.265984]  [<c057344b>] ? do_page_fault+0x19b/0x380
Feb 23 16:11:00 dalburk kernel: [1223641.265988]  [<c0101a94>] sys_clone+0x34/0x40
Feb 23 16:11:00 dalburk kernel: [1223641.265993]  [<c010336c>] syscall_call+0x7/0xb
Feb 23 16:11:00 dalburk kernel: [1223641.265996] Mem-Info:
Feb 23 16:11:00 dalburk kernel: [1223641.265998] DMA per-cpu:
Feb 23 16:11:00 dalburk kernel: [1223641.266001] CPU    0: hi:    0, btch:   1 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.266003] CPU    1: hi:    0, btch:   1 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.266006] CPU    2: hi:    0, btch:   1 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.266009] CPU    3: hi:    0, btch:   1 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.266011] Normal per-cpu:
Feb 23 16:11:00 dalburk kernel: [1223641.266013] CPU    0: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.266016] CPU    1: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.266019] CPU    2: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.266022] CPU    3: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.266024] HighMem per-cpu:
Feb 23 16:11:00 dalburk kernel: [1223641.266026] CPU    0: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.266029] CPU    1: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.266032] CPU    2: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.266034] CPU    3: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.266040] Active_anon:210621 active_file:34530 inactive_anon:98277
Feb 23 16:11:00 dalburk kernel: [1223641.266041]  inactive_file:270653 unevictable:42862 dirty:76 writeback:48 unstable:0
Feb 23 16:11:00 dalburk kernel: [1223641.266043]  free:35994 slab:44277 mapped:35396 pagetables:1829 bounce:0
Feb 23 16:11:00 dalburk kernel: [1223641.266048] DMA free:3492kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:20kB inactive_file:0kB unevictable:0kB present:15852kB pages_scanned:0 all_unreclaimable? no
Feb 23 16:11:00 dalburk kernel: [1223641.266052] lowmem_reserve[]: 0 865 3523 3523
Feb 23 16:11:00 dalburk kernel: [1223641.266061] Normal free:41152kB min:3728kB low:4660kB high:5592kB active_anon:8kB inactive_anon:36kB active_file:196kB inactive_file:96kB unevictable:74780kB present:885944kB pages_scanned:0 all_unreclaimable? no
Feb 23 16:11:00 dalburk kernel: [1223641.266065] lowmem_reserve[]: 0 0 21270 21270
Feb 23 16:11:00 dalburk kernel: [1223641.266073] HighMem free:99332kB min:512kB low:3376kB high:6240kB active_anon:842476kB inactive_anon:393072kB active_file:137904kB inactive_file:1082516kB unevictable:96668kB present:2722564kB pages_scanned:0 all_unreclaimable? no
Feb 23 16:11:00 dalburk kernel: [1223641.266078] lowmem_reserve[]: 0 0 0 0
Feb 23 16:11:00 dalburk kernel: [1223641.266083] DMA: 9*4kB 45*8kB 31*16kB 11*32kB 1*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 3484kB
Feb 23 16:11:00 dalburk kernel: [1223641.266097] Normal: 10285*4kB 18*8kB 8*16kB 0*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 41476kB
Feb 23 16:11:00 dalburk kernel: [1223641.266111] HighMem: 680*4kB 773*8kB 4405*16kB 606*32kB 8*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 99288kB
Feb 23 16:11:00 dalburk kernel: [1223641.266124] 332820 total pagecache pages
Feb 23 16:11:00 dalburk kernel: [1223641.266127] 12631 pages in swap cache
Feb 23 16:11:00 dalburk kernel: [1223641.266130] Swap cache stats: add 18900220, delete 18887589, find 2623245/3507213
Feb 23 16:11:00 dalburk kernel: [1223641.266133] Free swap  = 33957044kB
Feb 23 16:11:00 dalburk kernel: [1223641.266135] Total swap = 34178176kB
Feb 23 16:11:00 dalburk kernel: [1223641.277082] 913327 pages RAM
Feb 23 16:11:00 dalburk kernel: [1223641.277086] 686001 pages HighMem
Feb 23 16:11:00 dalburk kernel: [1223641.277088] 34428 pages reserved
Feb 23 16:11:00 dalburk kernel: [1223641.277091] 104470 pages shared
Feb 23 16:11:00 dalburk kernel: [1223641.277093] 777621 pages non-shared
Feb 23 16:11:00 dalburk kernel: [1223641.277097] Out of memory: kill process 3475 (run-mozilla.sh) score 178478 or a child
Feb 23 16:11:00 dalburk kernel: [1223641.277153] Killed process 3480 (thunderbird-bin)
Feb 23 16:11:00 dalburk kernel: [1223641.394564] rsyslogd invoked oom-killer: gfp_mask=0xd0, order=1, oomkilladj=0
Feb 23 16:11:00 dalburk kernel: [1223641.394568] rsyslogd cpuset=/ mems_allowed=0
Feb 23 16:11:00 dalburk kernel: [1223641.394572] Pid: 1034, comm: rsyslogd Tainted: P         C 2.6.31-19-generic #56-Ubuntu
Feb 23 16:11:00 dalburk kernel: [1223641.394574] Call Trace:
Feb 23 16:11:00 dalburk kernel: [1223641.394582]  [<c01b594f>] oom_kill_process+0x9f/0x250
Feb 23 16:11:00 dalburk kernel: [1223641.394586]  [<c01b5f5e>] ? select_bad_process+0xbe/0xf0
Feb 23 16:11:00 dalburk kernel: [1223641.394589]  [<c01b5fe1>] __out_of_memory+0x51/0xa0
Feb 23 16:11:00 dalburk kernel: [1223641.394592]  [<c01b6083>] out_of_memory+0x53/0xb0
Feb 23 16:11:00 dalburk kernel: [1223641.394595]  [<c01b834e>] __alloc_pages_slowpath+0x42e/0x480
Feb 23 16:11:00 dalburk kernel: [1223641.394598]  [<c01b84af>] __alloc_pages_nodemask+0x10f/0x120
Feb 23 16:11:00 dalburk kernel: [1223641.394601]  [<c01b8507>] __get_free_pages+0x17/0x30
Feb 23 16:11:00 dalburk kernel: [1223641.394605]  [<c0142b60>] dup_task_struct+0x40/0xe0
Feb 23 16:11:00 dalburk kernel: [1223641.394608]  [<c0143918>] copy_process+0x68/0xcb0
Feb 23 16:11:00 dalburk kernel: [1223641.394611]  [<c01446de>] do_fork+0x7e/0x3a0
Feb 23 16:11:00 dalburk kernel: [1223641.394616]  [<c057344b>] ? do_page_fault+0x19b/0x380
Feb 23 16:11:00 dalburk kernel: [1223641.394618]  [<c0101a94>] sys_clone+0x34/0x40
Feb 23 16:11:00 dalburk kernel: [1223641.394621]  [<c010336c>] syscall_call+0x7/0xb
Feb 23 16:11:00 dalburk kernel: [1223641.394623] Mem-Info:
Feb 23 16:11:00 dalburk kernel: [1223641.394625] DMA per-cpu:
Feb 23 16:11:00 dalburk kernel: [1223641.394627] CPU    0: hi:    0, btch:   1 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.394629] CPU    1: hi:    0, btch:   1 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.394631] CPU    2: hi:    0, btch:   1 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.394632] CPU    3: hi:    0, btch:   1 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.394634] Normal per-cpu:
Feb 23 16:11:00 dalburk kernel: [1223641.394635] CPU    0: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.394637] CPU    1: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.394639] CPU    2: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.394641] CPU    3: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.394643] HighMem per-cpu:
Feb 23 16:11:00 dalburk kernel: [1223641.394644] CPU    0: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.394646] CPU    1: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.394648] CPU    2: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.394650] CPU    3: hi:  186, btch:  31 usd:   0
Feb 23 16:11:00 dalburk kernel: [1223641.394653] Active_anon:206111 active_file:34498 inactive_anon:98332
Feb 23 16:11:00 dalburk kernel: [1223641.394654]  inactive_file:270923 unevictable:42862 dirty:76 writeback:85 unstable:0
Feb 23 16:11:00 dalburk kernel: [1223641.394655]  free:40304 slab:44252 mapped:32481 pagetables:1774 bounce:0
Feb 23 16:11:00 dalburk kernel: [1223641.394659] DMA free:3492kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:20kB inactive_file:0kB unevictable:0kB present:15852kB pages_scanned:0 all_unreclaimable? no


```

---

