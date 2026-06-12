---
title: "Weird crash somewhere that logs me out of KDE help me create bug report...."
date: 2010-05-06
forum: General Help
---

### Post by kubunut on 2010-05-06
Hey everyone,


Just noticed I left the computer on to download last night, and for the second time I didn´t download anything because KDE logs me out automatically.

How can I find out the cause of this logging out ?

Here is my syslog:

> May  7 00:17:01 my-desktop CRON[2760]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  7 01:17:01 my-desktop CRON[2768]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  7 01:36:45 my-desktop kernel: [26358.364344] python invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
May  7 01:36:47 my-desktop kernel: [26358.364352] python cpuset=/ mems_allowed=0
May  7 01:36:47 my-desktop kernel: [26358.364357] Pid: 1517, comm: python Tainted: P   M       2.6.32-22-generic #33-Ubuntu
May  7 01:36:47 my-desktop kernel: [26358.364360] Call Trace:
May  7 01:36:47 my-desktop kernel: [26358.364372]  [<c01cc814>] oom_kill_process+0xa4/0x2b0
May  7 01:36:47 my-desktop kernel: [26358.364377]  [<c01cce89>] ? select_bad_process+0xa9/0xe0
May  7 01:36:47 my-desktop kernel: [26358.364382]  [<c01ccf11>] __out_of_memory+0x51/0xa0
May  7 01:36:47 my-desktop kernel: [26358.364386]  [<c01ccfb8>] out_of_memory+0x58/0xb0
May  7 01:36:47 my-desktop kernel: [26358.364390]  [<c01cf7c7>] __alloc_pages_slowpath+0x407/0x4a0
May  7 01:36:47 my-desktop kernel: [26358.364395]  [<c01cf99a>] __alloc_pages_nodemask+0x13a/0x170
May  7 01:36:47 my-desktop kernel: [26358.364400]  [<c01d1fda>] __do_page_cache_readahead+0xea/0x200
May  7 01:36:47 my-desktop kernel: [26358.364405]  [<c01d2116>] ra_submit+0x26/0x30
May  7 01:36:47 my-desktop kernel: [26358.364408]  [<c01cc10c>] filemap_fault+0x3dc/0x410
May  7 01:36:47 my-desktop kernel: [26358.364413]  [<c01e4650>] __do_fault+0x40/0x490
May  7 01:36:48 my-desktop kernel: [26358.364419]  [<c01a3673>] ? cpu_quiet_msk+0xb3/0x110
May  7 01:36:48 my-desktop kernel: [26358.364423]  [<c01e6259>] handle_mm_fault+0x139/0x390
May  7 01:36:48 my-desktop kernel: [26358.364430]  [<c058dacd>] do_page_fault+0x10d/0x3a0
May  7 01:36:48 my-desktop kernel: [26358.364435]  [<c02184f2>] ? sys_select+0x42/0xc0
May  7 01:36:48 my-desktop kernel: [26358.364439]  [<c058d9c0>] ? do_page_fault+0x0/0x3a0
May  7 01:36:48 my-desktop kernel: [26358.364443]  [<c058b9c3>] error_code+0x73/0x80
May  7 01:36:48 my-desktop kernel: [26358.364446] Mem-Info:
May  7 01:36:48 my-desktop kernel: [26358.364448] DMA per-cpu:
May  7 01:36:48 my-desktop kernel: [26358.364451] CPU    0: hi:    0, btch:   1 usd:   0
May  7 01:36:48 my-desktop kernel: [26358.364453] Normal per-cpu:
May  7 01:36:48 my-desktop kernel: [26358.364455] CPU    0: hi:  186, btch:  31 usd: 134
May  7 01:36:48 my-desktop kernel: [26358.364457] HighMem per-cpu:
May  7 01:36:48 my-desktop kernel: [26358.364460] CPU    0: hi:  186, btch:  31 usd: 185
May  7 01:36:48 my-desktop kernel: [26358.364466] active_anon:151593 inactive_anon:151567 isolated_anon:0
May  7 01:36:48 my-desktop kernel: [26358.364467]  active_file:201 inactive_file:237 isolated_file:0
May  7 01:36:48 my-desktop kernel: [26358.364469]  unevictable:0 dirty:0 writeback:0 unstable:0
May  7 01:36:48 my-desktop kernel: [26358.364470]  free:5440 slab_reclaimable:1353 slab_unreclaimable:2471
May  7 01:36:48 my-desktop kernel: [26358.364471]  mapped:712 shmem:482 pagetables:2173 bounce:0
May  7 01:36:48 my-desktop kernel: [26358.364480] DMA free:5072kB min:64kB low:80kB high:96kB active_anon:1544kB inactive_anon:1792kB active_file:8kB inactive_file:96kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15804kB mlocked:0kB dirty:0kB writeback:0kB mapped:20kB shmem:0kB slab_reclaimable:4kB slab_unreclaimable:4kB kernel_stack:0kB pagetables:8kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
May  7 01:36:48 my-desktop kernel: [26358.364486] lowmem_reserve[]: 0 865 1254 1254
May  7 01:36:48 my-desktop kernel: [26358.364496] Normal free:16316kB min:3728kB low:4660kB high:5592kB active_anon:414500kB inactive_anon:413932kB active_file:92kB inactive_file:104kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:0kB mapped:384kB shmem:168kB slab_reclaimable:5408kB slab_unreclaimable:9880kB kernel_stack:2000kB pagetables:3960kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:64 all_unreclaimable? no
May  7 01:36:48 my-desktop kernel: [26358.364504] lowmem_reserve[]: 0 0 3111 3111
May  7 01:36:48 my-desktop kernel: [26358.364513] HighMem free:372kB min:388kB low:804kB high:1224kB active_anon:190328kB inactive_anon:190544kB active_file:704kB inactive_file:748kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:398216kB mlocked:0kB dirty:0kB writeback:0kB mapped:2444kB shmem:1760kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:4724kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:1390 all_unreclaimable? no
May  7 01:36:48 my-desktop kernel: [26358.364520] lowmem_reserve[]: 0 0 0 0
May  7 01:36:48 my-desktop kernel: [26358.364524] DMA: 2*4kB 1*8kB 2*16kB 1*32kB 2*64kB 2*128kB 2*256kB 4*512kB 2*1024kB 0*2048kB 0*4096kB = 5072kB
May  7 01:36:48 my-desktop kernel: [26358.364534] Normal: 3073*4kB 3*8kB 0*16kB 1*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 16316kB
May  7 01:36:48 my-desktop kernel: [26358.364545] HighMem: 1*4kB 0*8kB 1*16kB 1*32kB 5*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 372kB
May  7 01:36:48 my-desktop kernel: [26358.364555] 1265 total pagecache pages
May  7 01:36:48 my-desktop kernel: [26358.364557] 335 pages in swap cache
May  7 01:36:48 my-desktop kernel: [26358.364560] Swap cache stats: add 102835, delete 102500, find 134/179
May  7 01:36:48 my-desktop kernel: [26358.364562] Free swap  = 0kB
May  7 01:36:48 my-desktop kernel: [26358.364564] Total swap = 409616kB
May  7 01:36:48 my-desktop kernel: [26358.377501] 327648 pages RAM
May  7 01:36:48 my-desktop kernel: [26358.377503] 100338 pages HighMem
May  7 01:36:48 my-desktop kernel: [26358.377506] 6390 pages reserved
May  7 01:36:48 my-desktop kernel: [26358.377507] 4835 pages shared
May  7 01:36:48 my-desktop kernel: [26358.377509] 313206 pages non-shared
May  7 01:36:48 my-desktop kernel: [26358.377513] Out of memory: kill process 1257 (kdeinit4) score 720377 or a child
May  7 01:36:48 my-desktop kernel: [26358.377518] Killed process 1258 (klauncher)
May  7 01:36:48 my-desktop kernel: [26359.915006] kbluetooth invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
May  7 01:36:48 my-desktop kernel: [26359.915014] kbluetooth cpuset=/ mems_allowed=0
May  7 01:36:48 my-desktop kernel: [26359.915019] Pid: 1466, comm: kbluetooth Tainted: P   M       2.6.32-22-generic #33-Ubuntu
May  7 01:36:48 my-desktop kernel: [26359.915023] Call Trace:
May  7 01:36:48 my-desktop kernel: [26359.915036]  [<c01cc814>] oom_kill_process+0xa4/0x2b0
May  7 01:36:48 my-desktop kernel: [26359.915040]  [<c01cce89>] ? select_bad_process+0xa9/0xe0
May  7 01:36:48 my-desktop kernel: [26359.915045]  [<c01ccf11>] __out_of_memory+0x51/0xa0
May  7 01:36:48 my-desktop kernel: [26359.915049]  [<c01ccfb8>] out_of_memory+0x58/0xb0
May  7 01:36:48 my-desktop kernel: [26359.915053]  [<c01cf7c7>] __alloc_pages_slowpath+0x407/0x4a0
May  7 01:36:48 my-desktop kernel: [26359.915058]  [<c01cf99a>] __alloc_pages_nodemask+0x13a/0x170
May  7 01:36:48 my-desktop kernel: [26359.915064]  [<c01d1fda>] __do_page_cache_readahead+0xea/0x200
May  7 01:36:48 my-desktop kernel: [26359.915068]  [<c01d2116>] ra_submit+0x26/0x30
May  7 01:36:48 my-desktop kernel: [26359.915072]  [<c01cc10c>] filemap_fault+0x3dc/0x410
May  7 01:36:48 my-desktop kernel: [26359.915076]  [<c01e4650>] __do_fault+0x40/0x490
May  7 01:36:48 my-desktop kernel: [26359.915080]  [<c01e6259>] handle_mm_fault+0x139/0x390
May  7 01:36:48 my-desktop kernel: [26359.915088]  [<c058dacd>] do_page_fault+0x10d/0x3a0
May  7 01:36:48 my-desktop kernel: [26359.915092]  [<c058d9c0>] ? do_page_fault+0x0/0x3a0
May  7 01:36:48 my-desktop kernel: [26359.915096]  [<c058b9c3>] error_code+0x73/0x80
May  7 01:36:48 my-desktop kernel: [26359.915099] Mem-Info:
May  7 01:36:48 my-desktop kernel: [26359.915101] DMA per-cpu:
May  7 01:36:48 my-desktop kernel: [26359.915104] CPU    0: hi:    0, btch:   1 usd:   0
May  7 01:36:48 my-desktop kernel: [26359.915106] Normal per-cpu:
May  7 01:36:48 my-desktop kernel: [26359.915108] CPU    0: hi:  186, btch:  31 usd: 163
May  7 01:36:48 my-desktop kernel: [26359.915110] HighMem per-cpu:
May  7 01:36:48 my-desktop kernel: [26359.915113] CPU    0: hi:  186, btch:  31 usd:  69
May  7 01:36:48 my-desktop kernel: [26359.915119] active_anon:151493 inactive_anon:151609 isolated_anon:0
May  7 01:36:48 my-desktop kernel: [26359.915120]  active_file:255 inactive_file:463 isolated_file:0
May  7 01:36:48 my-desktop kernel: [26359.915122]  unevictable:0 dirty:0 writeback:82 unstable:0
May  7 01:36:48 my-desktop kernel: [26359.915123]  free:5399 slab_reclaimable:1352 slab_unreclaimable:2477
May  7 01:36:48 my-desktop kernel: [26359.915125]  mapped:747 shmem:482 pagetables:2129 bounce:0
May  7 01:36:48 my-desktop kernel: [26359.915133] DMA free:5072kB min:64kB low:80kB high:96kB active_anon:1544kB inactive_anon:1792kB active_file:8kB inactive_file:96kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15804kB mlocked:0kB dirty:0kB writeback:0kB mapped:20kB shmem:0kB slab_reclaimable:4kB slab_unreclaimable:4kB kernel_stack:0kB pagetables:8kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
May  7 01:36:48 my-desktop kernel: [26359.915139] lowmem_reserve[]: 0 865 1254 1254
May  7 01:36:48 my-desktop kernel: [26359.915150] Normal free:16152kB min:3728kB low:4660kB high:5592kB active_anon:414120kB inactive_anon:414172kB active_file:256kB inactive_file:288kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:8kB mapped:476kB shmem:168kB slab_reclaimable:5404kB slab_unreclaimable:9904kB kernel_stack:2000kB pagetables:3960kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:1216 all_unreclaimable? no
May  7 01:36:48 my-desktop kernel: [26359.915157] lowmem_reserve[]: 0 0 3111 3111
May  7 01:36:48 my-desktop kernel: [26359.915166] HighMem free:372kB min:388kB low:804kB high:1224kB active_anon:190308kB inactive_anon:190472kB active_file:756kB inactive_file:1468kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:398216kB mlocked:0kB dirty:0kB writeback:320kB mapped:2492kB shmem:1760kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:4548kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:2656 all_unreclaimable? no
May  7 01:36:48 my-desktop kernel: [26359.915174] lowmem_reserve[]: 0 0 0 0
May  7 01:36:48 my-desktop kernel: [26359.915178] DMA: 2*4kB 1*8kB 2*16kB 1*32kB 2*64kB 2*128kB 2*256kB 4*512kB 2*1024kB 0*2048kB 0*4096kB = 5072kB
May  7 01:36:48 my-desktop kernel: [26359.915188] Normal: 3030*4kB 6*8kB 1*16kB 0*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 16152kB
May  7 01:36:48 my-desktop kernel: [26359.915199] HighMem: 1*4kB 0*8kB 1*16kB 1*32kB 5*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 372kB
May  7 01:36:48 my-desktop kernel: [26359.915209] 1695 total pagecache pages
May  7 01:36:48 my-desktop kernel: [26359.915211] 479 pages in swap cache
May  7 01:36:48 my-desktop kernel: [26359.915214] Swap cache stats: add 103004, delete 102525, find 146/202
May  7 01:36:48 my-desktop kernel: [26359.915216] Free swap  = 0kB
May  7 01:36:48 my-desktop kernel: [26359.915218] Total swap = 409616kB
May  7 01:36:48 my-desktop kernel: [26359.928210] 327648 pages RAM
May  7 01:36:48 my-desktop kernel: [26359.928213] 100338 pages HighMem
May  7 01:36:48 my-desktop kernel: [26359.928215] 6390 pages reserved
May  7 01:36:48 my-desktop kernel: [26359.928217] 5102 pages shared
May  7 01:36:48 my-desktop kernel: [26359.928218] 313278 pages non-shared
May  7 01:36:48 my-desktop kernel: [26359.928223] Out of memory: kill process 1257 (kdeinit4) score 714764 or a child
May  7 01:36:48 my-desktop kernel: [26359.928228] Killed process 1357 (ksmserver)
May  7 01:36:48 my-desktop kernel: [26359.987959] kio_file invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
May  7 01:36:48 my-desktop kernel: [26359.987967] kio_file cpuset=/ mems_allowed=0
May  7 01:36:48 my-desktop kernel: [26359.987972] Pid: 2104, comm: kio_file Tainted: P   M       2.6.32-22-generic #33-Ubuntu
May  7 01:36:48 my-desktop kernel: [26359.987975] Call Trace:
May  7 01:36:48 my-desktop kernel: [26359.987988]  [<c01cc814>] oom_kill_process+0xa4/0x2b0
May  7 01:36:48 my-desktop kernel: [26359.987993]  [<c01cce89>] ? select_bad_process+0xa9/0xe0
May  7 01:36:48 my-desktop kernel: [26359.987997]  [<c01ccf11>] __out_of_memory+0x51/0xa0
May  7 01:36:48 my-desktop kernel: [26359.988028]  [<c01ccfb8>] out_of_memory+0x58/0xb0
May  7 01:36:48 my-desktop kernel: [26359.988033]  [<c01cf7c7>] __alloc_pages_slowpath+0x407/0x4a0
May  7 01:36:48 my-desktop kernel: [26359.988038]  [<c01cf99a>] __alloc_pages_nodemask+0x13a/0x170
May  7 01:36:48 my-desktop kernel: [26359.988043]  [<c01d1fda>] __do_page_cache_readahead+0xea/0x200
May  7 01:36:48 my-desktop kernel: [26359.988048]  [<c01d2116>] ra_submit+0x26/0x30
May  7 01:36:48 my-desktop kernel: [26359.988051]  [<c01cc10c>] filemap_fault+0x3dc/0x410
May  7 01:36:48 my-desktop kernel: [26359.988056]  [<c01e4650>] __do_fault+0x40/0x490
May  7 01:36:48 my-desktop kernel: [26359.988060]  [<c01e6259>] handle_mm_fault+0x139/0x390
May  7 01:36:48 my-desktop kernel: [26359.988067]  [<c058dacd>] do_page_fault+0x10d/0x3a0
May  7 01:36:48 my-desktop kernel: [26359.988071]  [<c058d9c0>] ? do_page_fault+0x0/0x3a0
May  7 01:36:48 my-desktop kernel: [26359.988075]  [<c058b9c3>] error_code+0x73/0x80
May  7 01:36:48 my-desktop kernel: [26359.988078] Mem-Info:
May  7 01:36:48 my-desktop kernel: [26359.988080] DMA per-cpu:
May  7 01:36:48 my-desktop kernel: [26359.988083] CPU    0: hi:    0, btch:   1 usd:   0
May  7 01:36:48 my-desktop kernel: [26359.988085] Normal per-cpu:
May  7 01:36:48 my-desktop kernel: [26359.988087] CPU    0: hi:  186, btch:  31 usd: 117
May  7 01:36:48 my-desktop kernel: [26359.988089] HighMem per-cpu:
May  7 01:36:48 my-desktop kernel: [26359.988092] CPU    0: hi:  186, btch:  31 usd:  93
May  7 01:36:48 my-desktop kernel: [26359.988098] active_anon:151493 inactive_anon:151609 isolated_anon:0
May  7 01:36:48 my-desktop kernel: [26359.988099]  active_file:258 inactive_file:476 isolated_file:0
May  7 01:36:48 my-desktop kernel: [26359.988100]  unevictable:0 dirty:0 writeback:82 unstable:0
May  7 01:36:48 my-desktop kernel: [26359.988102]  free:5399 slab_reclaimable:1352 slab_unreclaimable:2477
May  7 01:36:48 my-desktop kernel: [26359.988103]  mapped:767 shmem:482 pagetables:2129 bounce:0
May  7 01:36:48 my-desktop kernel: [26359.988111] DMA free:5072kB min:64kB low:80kB high:96kB active_anon:1544kB inactive_anon:1792kB active_file:8kB inactive_file:96kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15804kB mlocked:0kB dirty:0kB writeback:0kB mapped:20kB shmem:0kB slab_reclaimable:4kB slab_unreclaimable:4kB kernel_stack:0kB pagetables:8kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
May  7 01:36:48 my-desktop kernel: [26359.988118] lowmem_reserve[]: 0 865 1254 1254
May  7 01:36:48 my-desktop kernel: [26359.988128] Normal free:16152kB min:3728kB low:4660kB high:5592kB active_anon:414120kB inactive_anon:414172kB active_file:228kB inactive_file:408kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:8kB mapped:476kB shmem:168kB slab_reclaimable:5404kB slab_unreclaimable:9904kB kernel_stack:2000kB pagetables:3960kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:768 all_unreclaimable? no
May  7 01:36:48 my-desktop kernel: [26359.988136] lowmem_reserve[]: 0 0 3111 3111
May  7 01:36:48 my-desktop kernel: [26359.988145] HighMem free:372kB min:388kB low:804kB high:1224kB active_anon:190308kB inactive_anon:190472kB active_file:796kB inactive_file:1400kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:398216kB mlocked:0kB dirty:0kB writeback:320kB mapped:2572kB shmem:1760kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:4548kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:4320 all_unreclaimable? yes
May  7 01:36:48 my-desktop kernel: [26359.988152] lowmem_reserve[]: 0 0 0 0
May  7 01:36:48 my-desktop kernel: [26359.988156] DMA: 2*4kB 1*8kB 2*16kB 1*32kB 2*64kB 2*128kB 2*256kB 4*512kB 2*1024kB 0*2048kB 0*4096kB = 5072kB
May  7 01:36:48 my-desktop kernel: [26359.988166] Normal: 3024*4kB 9*8kB 1*16kB 0*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 16152kB
May  7 01:36:48 my-desktop kernel: [26359.988176] HighMem: 1*4kB 0*8kB 1*16kB 1*32kB 5*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 372kB
May  7 01:36:48 my-desktop kernel: [26359.988186] 1724 total pagecache pages
May  7 01:36:48 my-desktop kernel: [26359.988188] 487 pages in swap cache
May  7 01:36:48 my-desktop kernel: [26359.988191] Swap cache stats: add 103012, delete 102525, find 146/203
May  7 01:36:48 my-desktop kernel: [26359.988193] Free swap  = 0kB
May  7 01:36:48 my-desktop kernel: [26359.988195] Total swap = 409616kB
May  7 01:36:48 my-desktop kernel: [26360.001045] 327648 pages RAM
May  7 01:36:48 my-desktop kernel: [26360.001048] 100338 pages HighMem
May  7 01:36:48 my-desktop kernel: [26360.001050] 6390 pages reserved
May  7 01:36:48 my-desktop kernel: [26360.001052] 5180 pages shared
May  7 01:36:48 my-desktop kernel: [26360.001053] 313283 pages non-shared
May  7 01:36:48 my-desktop kernel: [26360.001057] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:48 my-desktop kernel: [26360.001063] Killed process 1408 (ksmserver)
May  7 01:36:48 my-desktop kernel: [26360.004283] kio_file invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
May  7 01:36:48 my-desktop kernel: [26360.004290] kio_file cpuset=/ mems_allowed=0
May  7 01:36:48 my-desktop kernel: [26360.004295] Pid: 2104, comm: kio_file Tainted: P   M       2.6.32-22-generic #33-Ubuntu
May  7 01:36:48 my-desktop kernel: [26360.004298] Call Trace:
May  7 01:36:48 my-desktop kernel: [26360.004310]  [<c01cc814>] oom_kill_process+0xa4/0x2b0
May  7 01:36:48 my-desktop kernel: [26360.004314]  [<c01cce89>] ? select_bad_process+0xa9/0xe0
May  7 01:36:48 my-desktop kernel: [26360.004318]  [<c01ccf11>] __out_of_memory+0x51/0xa0
May  7 01:36:48 my-desktop kernel: [26360.004322]  [<c01ccfb8>] out_of_memory+0x58/0xb0
May  7 01:36:48 my-desktop kernel: [26360.004327]  [<c01cf7c7>] __alloc_pages_slowpath+0x407/0x4a0
May  7 01:36:48 my-desktop kernel: [26360.004332]  [<c01cf99a>] __alloc_pages_nodemask+0x13a/0x170
May  7 01:36:48 my-desktop kernel: [26360.004337]  [<c01d1fda>] __do_page_cache_readahead+0xea/0x200
May  7 01:36:48 my-desktop kernel: [26360.004342]  [<c01d2116>] ra_submit+0x26/0x30
May  7 01:36:48 my-desktop kernel: [26360.004345]  [<c01cc10c>] filemap_fault+0x3dc/0x410
May  7 01:36:48 my-desktop kernel: [26360.004350]  [<c01e4650>] __do_fault+0x40/0x490
May  7 01:36:48 my-desktop kernel: [26360.004354]  [<c01e6259>] handle_mm_fault+0x139/0x390
May  7 01:36:48 my-desktop kernel: [26360.004361]  [<c058dacd>] do_page_fault+0x10d/0x3a0
May  7 01:36:48 my-desktop kernel: [26360.004365]  [<c058d9c0>] ? do_page_fault+0x0/0x3a0
May  7 01:36:48 my-desktop kernel: [26360.004369]  [<c058b9c3>] error_code+0x73/0x80
May  7 01:36:48 my-desktop kernel: [26360.004372] Mem-Info:
May  7 01:36:48 my-desktop kernel: [26360.004374] DMA per-cpu:
May  7 01:36:48 my-desktop kernel: [26360.004377] CPU    0: hi:    0, btch:   1 usd:   0
May  7 01:36:49 my-desktop kernel: [26360.004379] Normal per-cpu:
May  7 01:36:49 my-desktop kernel: [26360.004381] CPU    0: hi:  186, btch:  31 usd: 132
May  7 01:36:49 my-desktop kernel: [26360.004383] HighMem per-cpu:
May  7 01:36:49 my-desktop kernel: [26360.004386] CPU    0: hi:  186, btch:  31 usd:  93
May  7 01:36:49 my-desktop kernel: [26360.004392] active_anon:151485 inactive_anon:151617 isolated_anon:0
May  7 01:36:49 my-desktop kernel: [26360.004393]  active_file:267 inactive_file:462 isolated_file:0
May  7 01:36:49 my-desktop kernel: [26360.004395]  unevictable:0 dirty:0 writeback:80 unstable:0
May  7 01:36:49 my-desktop kernel: [26360.004396]  free:5399 slab_reclaimable:1352 slab_unreclaimable:2479
May  7 01:36:49 my-desktop kernel: [26360.004397]  mapped:771 shmem:482 pagetables:2129 bounce:0
May  7 01:36:49 my-desktop kernel: [26360.004406] DMA free:5072kB min:64kB low:80kB high:96kB active_anon:1544kB inactive_anon:1792kB active_file:8kB inactive_file:96kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15804kB mlocked:0kB dirty:0kB writeback:0kB mapped:20kB shmem:0kB slab_reclaimable:4kB slab_unreclaimable:4kB kernel_stack:0kB pagetables:8kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
May  7 01:36:49 my-desktop kernel: [26360.004413] lowmem_reserve[]: 0 865 1254 1254
May  7 01:36:49 my-desktop kernel: [26360.004423] Normal free:16152kB min:3728kB low:4660kB high:5592kB active_anon:414088kB inactive_anon:414204kB active_file:260kB inactive_file:344kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:12kB mapped:496kB shmem:168kB slab_reclaimable:5404kB slab_unreclaimable:9912kB kernel_stack:2000kB pagetables:3960kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:1728 all_unreclaimable? yes
May  7 01:36:49 my-desktop kernel: [26360.004430] lowmem_reserve[]: 0 0 3111 3111
May  7 01:36:49 my-desktop kernel: [26360.004440] HighMem free:372kB min:388kB low:804kB high:1224kB active_anon:190308kB inactive_anon:190472kB active_file:800kB inactive_file:1408kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:398216kB mlocked:0kB dirty:0kB writeback:308kB mapped:2568kB shmem:1760kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:4548kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:4320 all_unreclaimable? yes
May  7 01:36:49 my-desktop kernel: [26360.004447] lowmem_reserve[]: 0 0 0 0
May  7 01:36:49 my-desktop kernel: [26360.004451] DMA: 2*4kB 1*8kB 2*16kB 1*32kB 2*64kB 2*128kB 2*256kB 4*512kB 2*1024kB 0*2048kB 0*4096kB = 5072kB
May  7 01:36:49 my-desktop kernel: [26360.004461] Normal: 3024*4kB 9*8kB 1*16kB 0*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 16152kB
May  7 01:36:49 my-desktop kernel: [26360.004471] HighMem: 1*4kB 0*8kB 1*16kB 1*32kB 5*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 372kB
May  7 01:36:49 my-desktop kernel: [26360.004481] 1704 total pagecache pages
May  7 01:36:49 my-desktop kernel: [26360.004483] 487 pages in swap cache
May  7 01:36:49 my-desktop kernel: [26360.004486] Swap cache stats: add 103012, delete 102525, find 146/203
May  7 01:36:53 my-desktop kernel: [26360.004488] Free swap  = 0kB
May  7 01:36:53 my-desktop kernel: [26360.004490] Total swap = 409616kB
May  7 01:36:53 my-desktop kernel: [26360.017508] 327648 pages RAM
May  7 01:36:53 my-desktop kernel: [26360.017511] 100338 pages HighMem
May  7 01:36:53 my-desktop kernel: [26360.017513] 6390 pages reserved
May  7 01:36:53 my-desktop kernel: [26360.017515] 5180 pages shared
May  7 01:36:53 my-desktop kernel: [26360.017517] 313268 pages non-shared
May  7 01:36:53 my-desktop kernel: [26360.017521] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:53 my-desktop kernel: [26360.017526] Killed process 1408 (ksmserver)
May  7 01:36:53 my-desktop kernel: [26360.020280] kio_file invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
May  7 01:36:53 my-desktop kernel: [26360.020287] kio_file cpuset=/ mems_allowed=0
May  7 01:36:53 my-desktop kernel: [26360.020292] Pid: 2104, comm: kio_file Tainted: P   M       2.6.32-22-generic #33-Ubuntu
May  7 01:36:53 my-desktop kernel: [26360.020295] Call Trace:
May  7 01:36:54 my-desktop kernel: [26360.020306]  [<c01cc814>] oom_kill_process+0xa4/0x2b0
May  7 01:36:54 my-desktop kernel: [26360.020310]  [<c01cce89>] ? select_bad_process+0xa9/0xe0
May  7 01:36:54 my-desktop kernel: [26360.020315]  [<c01ccf11>] __out_of_memory+0x51/0xa0
May  7 01:36:54 my-desktop kernel: [26360.020319]  [<c01ccfb8>] out_of_memory+0x58/0xb0
May  7 01:36:54 my-desktop kernel: [26360.020323]  [<c01cf7c7>] __alloc_pages_slowpath+0x407/0x4a0
May  7 01:36:54 my-desktop kernel: [26360.020328]  [<c01cf99a>] __alloc_pages_nodemask+0x13a/0x170
May  7 01:36:54 my-desktop kernel: [26360.020334]  [<c01d1fda>] __do_page_cache_readahead+0xea/0x200
May  7 01:36:54 my-desktop kernel: [26360.020338]  [<c01d2116>] ra_submit+0x26/0x30
May  7 01:36:54 my-desktop kernel: [26360.020342]  [<c01cc10c>] filemap_fault+0x3dc/0x410
May  7 01:36:54 my-desktop kernel: [26360.020347]  [<c01e4650>] __do_fault+0x40/0x490
May  7 01:36:54 my-desktop kernel: [26360.020351]  [<c01e6259>] handle_mm_fault+0x139/0x390
May  7 01:36:54 my-desktop kernel: [26360.020358]  [<c058dacd>] do_page_fault+0x10d/0x3a0
May  7 01:36:54 my-desktop kernel: [26360.020362]  [<c058d9c0>] ? do_page_fault+0x0/0x3a0
May  7 01:36:54 my-desktop kernel: [26360.020365]  [<c058b9c3>] error_code+0x73/0x80
May  7 01:36:54 my-desktop kernel: [26360.020368] Mem-Info:
May  7 01:36:54 my-desktop kernel: [26360.020371] DMA per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.020373] CPU    0: hi:    0, btch:   1 usd:   0
May  7 01:36:54 my-desktop kernel: [26360.020376] Normal per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.020378] CPU    0: hi:  186, btch:  31 usd: 132
May  7 01:36:54 my-desktop kernel: [26360.020380] HighMem per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.020382] CPU    0: hi:  186, btch:  31 usd:  93
May  7 01:36:54 my-desktop kernel: [26360.020388] active_anon:151485 inactive_anon:151617 isolated_anon:0
May  7 01:36:54 my-desktop kernel: [26360.020390]  active_file:267 inactive_file:462 isolated_file:0
May  7 01:36:54 my-desktop kernel: [26360.020391]  unevictable:0 dirty:0 writeback:80 unstable:0
May  7 01:36:54 my-desktop kernel: [26360.020392]  free:5399 slab_reclaimable:1352 slab_unreclaimable:2479
May  7 01:36:54 my-desktop kernel: [26360.020394]  mapped:771 shmem:482 pagetables:2129 bounce:0
May  7 01:36:54 my-desktop kernel: [26360.020402] DMA free:5072kB min:64kB low:80kB high:96kB active_anon:1544kB inactive_anon:1792kB active_file:8kB inactive_file:96kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15804kB mlocked:0kB dirty:0kB writeback:0kB mapped:20kB shmem:0kB slab_reclaimable:4kB slab_unreclaimable:4kB kernel_stack:0kB pagetables:8kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.020409] lowmem_reserve[]: 0 865 1254 1254
May  7 01:36:54 my-desktop kernel: [26360.020419] Normal free:16152kB min:3728kB low:4660kB high:5592kB active_anon:414088kB inactive_anon:414204kB active_file:260kB inactive_file:344kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:12kB mapped:496kB shmem:168kB slab_reclaimable:5404kB slab_unreclaimable:9912kB kernel_stack:2000kB pagetables:3960kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:1728 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.020427] lowmem_reserve[]: 0 0 3111 3111
May  7 01:36:54 my-desktop kernel: [26360.020436] HighMem free:372kB min:388kB low:804kB high:1224kB active_anon:190308kB inactive_anon:190472kB active_file:800kB inactive_file:1408kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:398216kB mlocked:0kB dirty:0kB writeback:308kB mapped:2568kB shmem:1760kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:4548kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:4320 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.020443] lowmem_reserve[]: 0 0 0 0
May  7 01:36:54 my-desktop kernel: [26360.020447] DMA: 2*4kB 1*8kB 2*16kB 1*32kB 2*64kB 2*128kB 2*256kB 4*512kB 2*1024kB 0*2048kB 0*4096kB = 5072kB
May  7 01:36:54 my-desktop kernel: [26360.020458] Normal: 3024*4kB 9*8kB 1*16kB 0*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 16152kB
May  7 01:36:54 my-desktop kernel: [26360.020468] HighMem: 1*4kB 0*8kB 1*16kB 1*32kB 5*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 372kB
May  7 01:36:54 my-desktop kernel: [26360.020479] 1704 total pagecache pages
May  7 01:36:54 my-desktop kernel: [26360.020481] 487 pages in swap cache
May  7 01:36:54 my-desktop kernel: [26360.020483] Swap cache stats: add 103012, delete 102525, find 146/203
May  7 01:36:54 my-desktop kernel: [26360.020486] Free swap  = 0kB
May  7 01:36:54 my-desktop kernel: [26360.020487] Total swap = 409616kB
May  7 01:36:54 my-desktop kernel: [26360.033741] 327648 pages RAM
May  7 01:36:54 my-desktop kernel: [26360.033744] 100338 pages HighMem
May  7 01:36:54 my-desktop kernel: [26360.033746] 6390 pages reserved
May  7 01:36:54 my-desktop kernel: [26360.033748] 5180 pages shared
May  7 01:36:54 my-desktop kernel: [26360.033749] 313268 pages non-shared
May  7 01:36:54 my-desktop kernel: [26360.033754] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.033759] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.036324] kio_file invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
May  7 01:36:54 my-desktop kernel: [26360.036331] kio_file cpuset=/ mems_allowed=0
May  7 01:36:54 my-desktop kernel: [26360.036336] Pid: 2104, comm: kio_file Tainted: P   M       2.6.32-22-generic #33-Ubuntu
May  7 01:36:54 my-desktop kernel: [26360.036339] Call Trace:
May  7 01:36:54 my-desktop kernel: [26360.036350]  [<c01cc814>] oom_kill_process+0xa4/0x2b0
May  7 01:36:54 my-desktop kernel: [26360.036354]  [<c01cce89>] ? select_bad_process+0xa9/0xe0
May  7 01:36:54 my-desktop kernel: [26360.036359]  [<c01ccf11>] __out_of_memory+0x51/0xa0
May  7 01:36:54 my-desktop kernel: [26360.036363]  [<c01ccfb8>] out_of_memory+0x58/0xb0
May  7 01:36:54 my-desktop kernel: [26360.036367]  [<c01cf7c7>] __alloc_pages_slowpath+0x407/0x4a0
May  7 01:36:54 my-desktop kernel: [26360.036372]  [<c01cf99a>] __alloc_pages_nodemask+0x13a/0x170
May  7 01:36:54 my-desktop kernel: [26360.036377]  [<c01d1fda>] __do_page_cache_readahead+0xea/0x200
May  7 01:36:54 my-desktop kernel: [26360.036382]  [<c01d2116>] ra_submit+0x26/0x30
May  7 01:36:54 my-desktop kernel: [26360.036385]  [<c01cc10c>] filemap_fault+0x3dc/0x410
May  7 01:36:54 my-desktop kernel: [26360.036390]  [<c01e4650>] __do_fault+0x40/0x490
May  7 01:36:54 my-desktop kernel: [26360.036394]  [<c01e6259>] handle_mm_fault+0x139/0x390
May  7 01:36:54 my-desktop kernel: [26360.036401]  [<c058dacd>] do_page_fault+0x10d/0x3a0
May  7 01:36:54 my-desktop kernel: [26360.036405]  [<c058d9c0>] ? do_page_fault+0x0/0x3a0
May  7 01:36:54 my-desktop kernel: [26360.036409]  [<c058b9c3>] error_code+0x73/0x80
May  7 01:36:54 my-desktop kernel: [26360.036412] Mem-Info:
May  7 01:36:54 my-desktop kernel: [26360.036414] DMA per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.036417] CPU    0: hi:    0, btch:   1 usd:   0
May  7 01:36:54 my-desktop kernel: [26360.036419] Normal per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.036422] CPU    0: hi:  186, btch:  31 usd: 132
May  7 01:36:54 my-desktop kernel: [26360.036423] HighMem per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.036426] CPU    0: hi:  186, btch:  31 usd:  93
May  7 01:36:54 my-desktop kernel: [26360.036432] active_anon:151485 inactive_anon:151617 isolated_anon:0
May  7 01:36:54 my-desktop kernel: [26360.036433]  active_file:267 inactive_file:462 isolated_file:0
May  7 01:36:54 my-desktop kernel: [26360.036435]  unevictable:0 dirty:0 writeback:80 unstable:0
May  7 01:36:54 my-desktop kernel: [26360.036436]  free:5399 slab_reclaimable:1352 slab_unreclaimable:2479
May  7 01:36:54 my-desktop kernel: [26360.036437]  mapped:771 shmem:482 pagetables:2129 bounce:0
May  7 01:36:54 my-desktop kernel: [26360.036445] DMA free:5072kB min:64kB low:80kB high:96kB active_anon:1544kB inactive_anon:1792kB active_file:8kB inactive_file:96kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15804kB mlocked:0kB dirty:0kB writeback:0kB mapped:20kB shmem:0kB slab_reclaimable:4kB slab_unreclaimable:4kB kernel_stack:0kB pagetables:8kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.036452] lowmem_reserve[]: 0 865 1254 1254
May  7 01:36:54 my-desktop kernel: [26360.036462] Normal free:16152kB min:3728kB low:4660kB high:5592kB active_anon:414088kB inactive_anon:414204kB active_file:260kB inactive_file:344kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:12kB mapped:496kB shmem:168kB slab_reclaimable:5404kB slab_unreclaimable:9912kB kernel_stack:2000kB pagetables:3960kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:1728 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.036470] lowmem_reserve[]: 0 0 3111 3111
May  7 01:36:54 my-desktop kernel: [26360.036479] HighMem free:372kB min:388kB low:804kB high:1224kB active_anon:190308kB inactive_anon:190472kB active_file:800kB inactive_file:1408kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:398216kB mlocked:0kB dirty:0kB writeback:308kB mapped:2568kB shmem:1760kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:4548kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:4320 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.036486] lowmem_reserve[]: 0 0 0 0
May  7 01:36:54 my-desktop kernel: [26360.036490] DMA: 2*4kB 1*8kB 2*16kB 1*32kB 2*64kB 2*128kB 2*256kB 4*512kB 2*1024kB 0*2048kB 0*4096kB = 5072kB
May  7 01:36:54 my-desktop kernel: [26360.036501] Normal: 3024*4kB 9*8kB 1*16kB 0*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 16152kB
May  7 01:36:54 my-desktop kernel: [26360.036511] HighMem: 1*4kB 0*8kB 1*16kB 1*32kB 5*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 372kB
May  7 01:36:54 my-desktop kernel: [26360.036521] 1704 total pagecache pages
May  7 01:36:54 my-desktop kernel: [26360.036523] 487 pages in swap cache
May  7 01:36:54 my-desktop kernel: [26360.036526] Swap cache stats: add 103012, delete 102525, find 146/203
May  7 01:36:54 my-desktop kernel: [26360.036528] Free swap  = 0kB
May  7 01:36:54 my-desktop kernel: [26360.036530] Total swap = 409616kB
May  7 01:36:54 my-desktop kernel: [26360.049372] 327648 pages RAM
May  7 01:36:54 my-desktop kernel: [26360.049374] 100338 pages HighMem
May  7 01:36:54 my-desktop kernel: [26360.049376] 6390 pages reserved
May  7 01:36:54 my-desktop kernel: [26360.049378] 5192 pages shared
May  7 01:36:54 my-desktop kernel: [26360.049380] 313267 pages non-shared
May  7 01:36:54 my-desktop kernel: [26360.049384] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.049389] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.052334] kio_file invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
May  7 01:36:54 my-desktop kernel: [26360.052341] kio_file cpuset=/ mems_allowed=0
May  7 01:36:54 my-desktop kernel: [26360.052346] Pid: 2104, comm: kio_file Tainted: P   M       2.6.32-22-generic #33-Ubuntu
May  7 01:36:54 my-desktop kernel: [26360.052350] Call Trace:
May  7 01:36:54 my-desktop kernel: [26360.052361]  [<c01cc814>] oom_kill_process+0xa4/0x2b0
May  7 01:36:54 my-desktop kernel: [26360.052365]  [<c01cce89>] ? select_bad_process+0xa9/0xe0
May  7 01:36:54 my-desktop kernel: [26360.052369]  [<c01ccf11>] __out_of_memory+0x51/0xa0
May  7 01:36:54 my-desktop kernel: [26360.052373]  [<c01ccfb8>] out_of_memory+0x58/0xb0
May  7 01:36:54 my-desktop kernel: [26360.052378]  [<c01cf7c7>] __alloc_pages_slowpath+0x407/0x4a0
May  7 01:36:54 my-desktop kernel: [26360.052382]  [<c01cf99a>] __alloc_pages_nodemask+0x13a/0x170
May  7 01:36:54 my-desktop kernel: [26360.052388]  [<c01d1fda>] __do_page_cache_readahead+0xea/0x200
May  7 01:36:54 my-desktop kernel: [26360.052392]  [<c01d2116>] ra_submit+0x26/0x30
May  7 01:36:54 my-desktop kernel: [26360.052396]  [<c01cc10c>] filemap_fault+0x3dc/0x410
May  7 01:36:54 my-desktop kernel: [26360.052401]  [<c01e4650>] __do_fault+0x40/0x490
May  7 01:36:54 my-desktop kernel: [26360.052405]  [<c01e6259>] handle_mm_fault+0x139/0x390
May  7 01:36:54 my-desktop kernel: [26360.052412]  [<c058dacd>] do_page_fault+0x10d/0x3a0
May  7 01:36:54 my-desktop kernel: [26360.052416]  [<c058d9c0>] ? do_page_fault+0x0/0x3a0
May  7 01:36:54 my-desktop kernel: [26360.052419]  [<c058b9c3>] error_code+0x73/0x80
May  7 01:36:54 my-desktop kernel: [26360.052422] Mem-Info:
May  7 01:36:54 my-desktop kernel: [26360.052425] DMA per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.052427] CPU    0: hi:    0, btch:   1 usd:   0
May  7 01:36:54 my-desktop kernel: [26360.052429] Normal per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.052432] CPU    0: hi:  186, btch:  31 usd: 132
May  7 01:36:54 my-desktop kernel: [26360.052433] HighMem per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.052436] CPU    0: hi:  186, btch:  31 usd:  93
May  7 01:36:54 my-desktop kernel: [26360.052442] active_anon:151485 inactive_anon:151617 isolated_anon:0
May  7 01:36:54 my-desktop kernel: [26360.052443]  active_file:267 inactive_file:462 isolated_file:0
May  7 01:36:54 my-desktop kernel: [26360.052445]  unevictable:0 dirty:0 writeback:80 unstable:0
May  7 01:36:54 my-desktop kernel: [26360.052446]  free:5399 slab_reclaimable:1352 slab_unreclaimable:2479
May  7 01:36:54 my-desktop kernel: [26360.052447]  mapped:771 shmem:482 pagetables:2129 bounce:0
May  7 01:36:54 my-desktop kernel: [26360.052455] DMA free:5072kB min:64kB low:80kB high:96kB active_anon:1544kB inactive_anon:1792kB active_file:8kB inactive_file:96kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15804kB mlocked:0kB dirty:0kB writeback:0kB mapped:20kB shmem:0kB slab_reclaimable:4kB slab_unreclaimable:4kB kernel_stack:0kB pagetables:8kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.052462] lowmem_reserve[]: 0 865 1254 1254
May  7 01:36:54 my-desktop kernel: [26360.052472] Normal free:16152kB min:3728kB low:4660kB high:5592kB active_anon:414088kB inactive_anon:414204kB active_file:260kB inactive_file:344kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:12kB mapped:496kB shmem:168kB slab_reclaimable:5404kB slab_unreclaimable:9912kB kernel_stack:2000kB pagetables:3960kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:1728 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.052479] lowmem_reserve[]: 0 0 3111 3111
May  7 01:36:54 my-desktop kernel: [26360.052488] HighMem free:372kB min:388kB low:804kB high:1224kB active_anon:190308kB inactive_anon:190472kB active_file:800kB inactive_file:1408kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:398216kB mlocked:0kB dirty:0kB writeback:308kB mapped:2568kB shmem:1760kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:4548kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:4320 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.052535] lowmem_reserve[]: 0 0 0 0
May  7 01:36:54 my-desktop kernel: [26360.052539] DMA: 2*4kB 1*8kB 2*16kB 1*32kB 2*64kB 2*128kB 2*256kB 4*512kB 2*1024kB 0*2048kB 0*4096kB = 5072kB
May  7 01:36:54 my-desktop kernel: [26360.052550] Normal: 3024*4kB 9*8kB 1*16kB 0*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 16152kB
May  7 01:36:54 my-desktop kernel: [26360.052560] HighMem: 1*4kB 0*8kB 1*16kB 1*32kB 5*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 372kB
May  7 01:36:54 my-desktop kernel: [26360.052570] 1704 total pagecache pages
May  7 01:36:54 my-desktop kernel: [26360.052572] 487 pages in swap cache
May  7 01:36:54 my-desktop kernel: [26360.052575] Swap cache stats: add 103012, delete 102525, find 146/203
May  7 01:36:54 my-desktop kernel: [26360.052577] Free swap  = 0kB
May  7 01:36:54 my-desktop kernel: [26360.052579] Total swap = 409616kB
May  7 01:36:54 my-desktop kernel: [26360.065359] 327648 pages RAM
May  7 01:36:54 my-desktop kernel: [26360.065362] 100338 pages HighMem
May  7 01:36:54 my-desktop kernel: [26360.065363] 6390 pages reserved
May  7 01:36:54 my-desktop kernel: [26360.065365] 5193 pages shared
May  7 01:36:54 my-desktop kernel: [26360.065367] 313267 pages non-shared
May  7 01:36:54 my-desktop kernel: [26360.065370] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.065376] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.068327] kio_file invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
May  7 01:36:54 my-desktop kernel: [26360.068333] kio_file cpuset=/ mems_allowed=0
May  7 01:36:54 my-desktop kernel: [26360.068338] Pid: 2104, comm: kio_file Tainted: P   M       2.6.32-22-generic #33-Ubuntu
May  7 01:36:54 my-desktop kernel: [26360.068341] Call Trace:
May  7 01:36:54 my-desktop kernel: [26360.068352]  [<c01cc814>] oom_kill_process+0xa4/0x2b0
May  7 01:36:54 my-desktop kernel: [26360.068357]  [<c01cce89>] ? select_bad_process+0xa9/0xe0
May  7 01:36:54 my-desktop kernel: [26360.068361]  [<c01ccf11>] __out_of_memory+0x51/0xa0
May  7 01:36:54 my-desktop kernel: [26360.068365]  [<c01ccfb8>] out_of_memory+0x58/0xb0
May  7 01:36:54 my-desktop kernel: [26360.068369]  [<c01cf7c7>] __alloc_pages_slowpath+0x407/0x4a0
May  7 01:36:54 my-desktop kernel: [26360.068374]  [<c01cf99a>] __alloc_pages_nodemask+0x13a/0x170
May  7 01:36:54 my-desktop kernel: [26360.068379]  [<c01d1fda>] __do_page_cache_readahead+0xea/0x200
May  7 01:36:54 my-desktop kernel: [26360.068384]  [<c01d2116>] ra_submit+0x26/0x30
May  7 01:36:54 my-desktop kernel: [26360.068387]  [<c01cc10c>] filemap_fault+0x3dc/0x410
May  7 01:36:54 my-desktop kernel: [26360.068392]  [<c01e4650>] __do_fault+0x40/0x490
May  7 01:36:54 my-desktop kernel: [26360.068396]  [<c01e6259>] handle_mm_fault+0x139/0x390
May  7 01:36:54 my-desktop kernel: [26360.068403]  [<c058dacd>] do_page_fault+0x10d/0x3a0
May  7 01:36:54 my-desktop kernel: [26360.068407]  [<c058d9c0>] ? do_page_fault+0x0/0x3a0
May  7 01:36:54 my-desktop kernel: [26360.068411]  [<c058b9c3>] error_code+0x73/0x80
May  7 01:36:54 my-desktop kernel: [26360.068413] Mem-Info:
May  7 01:36:54 my-desktop kernel: [26360.068416] DMA per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.068418] CPU    0: hi:    0, btch:   1 usd:   0
May  7 01:36:54 my-desktop kernel: [26360.068420] Normal per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.068423] CPU    0: hi:  186, btch:  31 usd: 132
May  7 01:36:54 my-desktop kernel: [26360.068425] HighMem per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.068427] CPU    0: hi:  186, btch:  31 usd:  93
May  7 01:36:54 my-desktop kernel: [26360.068433] active_anon:151485 inactive_anon:151617 isolated_anon:0
May  7 01:36:54 my-desktop kernel: [26360.068434]  active_file:267 inactive_file:462 isolated_file:0
May  7 01:36:54 my-desktop kernel: [26360.068436]  unevictable:0 dirty:0 writeback:80 unstable:0
May  7 01:36:54 my-desktop kernel: [26360.068437]  free:5399 slab_reclaimable:1352 slab_unreclaimable:2479
May  7 01:36:54 my-desktop kernel: [26360.068438]  mapped:771 shmem:482 pagetables:2129 bounce:0
May  7 01:36:54 my-desktop kernel: [26360.068447] DMA free:5072kB min:64kB low:80kB high:96kB active_anon:1544kB inactive_anon:1792kB active_file:8kB inactive_file:96kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15804kB mlocked:0kB dirty:0kB writeback:0kB mapped:20kB shmem:0kB slab_reclaimable:4kB slab_unreclaimable:4kB kernel_stack:0kB pagetables:8kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.068453] lowmem_reserve[]: 0 865 1254 1254
May  7 01:36:54 my-desktop kernel: [26360.068463] Normal free:16152kB min:3728kB low:4660kB high:5592kB active_anon:414088kB inactive_anon:414204kB active_file:260kB inactive_file:344kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:12kB mapped:496kB shmem:168kB slab_reclaimable:5404kB slab_unreclaimable:9912kB kernel_stack:2000kB pagetables:3960kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:1728 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.068471] lowmem_reserve[]: 0 0 3111 3111
May  7 01:36:54 my-desktop kernel: [26360.068480] HighMem free:372kB min:388kB low:804kB high:1224kB active_anon:190308kB inactive_anon:190472kB active_file:800kB inactive_file:1408kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:398216kB mlocked:0kB dirty:0kB writeback:308kB mapped:2568kB shmem:1760kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:4548kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:4320 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.068487] lowmem_reserve[]: 0 0 0 0
May  7 01:36:54 my-desktop kernel: [26360.068491] DMA: 2*4kB 1*8kB 2*16kB 1*32kB 2*64kB 2*128kB 2*256kB 4*512kB 2*1024kB 0*2048kB 0*4096kB = 5072kB
May  7 01:36:54 my-desktop kernel: [26360.068501] Normal: 3024*4kB 9*8kB 1*16kB 0*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 16152kB
May  7 01:36:54 my-desktop kernel: [26360.068511] HighMem: 1*4kB 0*8kB 1*16kB 1*32kB 5*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 372kB
May  7 01:36:54 my-desktop kernel: [26360.068521] 1704 total pagecache pages
May  7 01:36:54 my-desktop kernel: [26360.068523] 487 pages in swap cache
May  7 01:36:54 my-desktop kernel: [26360.068526] Swap cache stats: add 103012, delete 102525, find 146/203
May  7 01:36:54 my-desktop kernel: [26360.068528] Free swap  = 0kB
May  7 01:36:54 my-desktop kernel: [26360.068530] Total swap = 409616kB
May  7 01:36:54 my-desktop kernel: [26360.081501] 327648 pages RAM
May  7 01:36:54 my-desktop kernel: [26360.081503] 100338 pages HighMem
May  7 01:36:54 my-desktop kernel: [26360.081505] 6390 pages reserved
May  7 01:36:54 my-desktop kernel: [26360.081507] 5193 pages shared
May  7 01:36:54 my-desktop kernel: [26360.081509] 313267 pages non-shared
May  7 01:36:54 my-desktop kernel: [26360.081513] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.081518] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.084360] kio_file invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
May  7 01:36:54 my-desktop kernel: [26360.084367] kio_file cpuset=/ mems_allowed=0
May  7 01:36:54 my-desktop kernel: [26360.084372] Pid: 2104, comm: kio_file Tainted: P   M       2.6.32-22-generic #33-Ubuntu
May  7 01:36:54 my-desktop kernel: [26360.084375] Call Trace:
May  7 01:36:54 my-desktop kernel: [26360.084386]  [<c01cc814>] oom_kill_process+0xa4/0x2b0
May  7 01:36:54 my-desktop kernel: [26360.084391]  [<c01cce89>] ? select_bad_process+0xa9/0xe0
May  7 01:36:54 my-desktop kernel: [26360.084395]  [<c01ccf11>] __out_of_memory+0x51/0xa0
May  7 01:36:54 my-desktop kernel: [26360.084399]  [<c01ccfb8>] out_of_memory+0x58/0xb0
May  7 01:36:54 my-desktop kernel: [26360.084403]  [<c01cf7c7>] __alloc_pages_slowpath+0x407/0x4a0
May  7 01:36:54 my-desktop kernel: [26360.084408]  [<c01cf99a>] __alloc_pages_nodemask+0x13a/0x170
May  7 01:36:54 my-desktop kernel: [26360.084414]  [<c01d1fda>] __do_page_cache_readahead+0xea/0x200
May  7 01:36:54 my-desktop kernel: [26360.084418]  [<c01d2116>] ra_submit+0x26/0x30
May  7 01:36:54 my-desktop kernel: [26360.084421]  [<c01cc10c>] filemap_fault+0x3dc/0x410
May  7 01:36:54 my-desktop kernel: [26360.084426]  [<c01e4650>] __do_fault+0x40/0x490
May  7 01:36:54 my-desktop kernel: [26360.084430]  [<c01e6259>] handle_mm_fault+0x139/0x390
May  7 01:36:54 my-desktop kernel: [26360.084437]  [<c058dacd>] do_page_fault+0x10d/0x3a0
May  7 01:36:54 my-desktop kernel: [26360.084441]  [<c058d9c0>] ? do_page_fault+0x0/0x3a0
May  7 01:36:54 my-desktop kernel: [26360.084445]  [<c058b9c3>] error_code+0x73/0x80
May  7 01:36:54 my-desktop kernel: [26360.084448] Mem-Info:
May  7 01:36:54 my-desktop kernel: [26360.084451] DMA per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.084453] CPU    0: hi:    0, btch:   1 usd:   0
May  7 01:36:54 my-desktop kernel: [26360.084455] Normal per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.084458] CPU    0: hi:  186, btch:  31 usd: 132
May  7 01:36:54 my-desktop kernel: [26360.084460] HighMem per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.084462] CPU    0: hi:  186, btch:  31 usd:  93
May  7 01:36:54 my-desktop kernel: [26360.084468] active_anon:151485 inactive_anon:151617 isolated_anon:0
May  7 01:36:54 my-desktop kernel: [26360.084469]  active_file:267 inactive_file:462 isolated_file:0
May  7 01:36:54 my-desktop kernel: [26360.084471]  unevictable:0 dirty:0 writeback:80 unstable:0
May  7 01:36:54 my-desktop kernel: [26360.084472]  free:5399 slab_reclaimable:1352 slab_unreclaimable:2479
May  7 01:36:54 my-desktop kernel: [26360.084473]  mapped:771 shmem:482 pagetables:2129 bounce:0
May  7 01:36:54 my-desktop kernel: [26360.084482] DMA free:5072kB min:64kB low:80kB high:96kB active_anon:1544kB inactive_anon:1792kB active_file:8kB inactive_file:96kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15804kB mlocked:0kB dirty:0kB writeback:0kB mapped:20kB shmem:0kB slab_reclaimable:4kB slab_unreclaimable:4kB kernel_stack:0kB pagetables:8kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.084489] lowmem_reserve[]: 0 865 1254 1254
May  7 01:36:54 my-desktop kernel: [26360.084498] Normal free:16152kB min:3728kB low:4660kB high:5592kB active_anon:414088kB inactive_anon:414204kB active_file:260kB inactive_file:344kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:12kB mapped:496kB shmem:168kB slab_reclaimable:5404kB slab_unreclaimable:9912kB kernel_stack:2000kB pagetables:3960kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:1728 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.084506] lowmem_reserve[]: 0 0 3111 3111
May  7 01:36:54 my-desktop kernel: [26360.084515] HighMem free:372kB min:388kB low:804kB high:1224kB active_anon:190308kB inactive_anon:190472kB active_file:800kB inactive_file:1408kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:398216kB mlocked:0kB dirty:0kB writeback:308kB mapped:2568kB shmem:1760kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:4548kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:4320 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.084523] lowmem_reserve[]: 0 0 0 0
May  7 01:36:54 my-desktop kernel: [26360.084526] DMA: 2*4kB 1*8kB 2*16kB 1*32kB 2*64kB 2*128kB 2*256kB 4*512kB 2*1024kB 0*2048kB 0*4096kB = 5072kB
May  7 01:36:54 my-desktop kernel: [26360.084537] Normal: 3024*4kB 9*8kB 1*16kB 0*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 16152kB
May  7 01:36:54 my-desktop kernel: [26360.084547] HighMem: 1*4kB 0*8kB 1*16kB 1*32kB 5*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 372kB
May  7 01:36:54 my-desktop kernel: [26360.084557] 1704 total pagecache pages
May  7 01:36:54 my-desktop kernel: [26360.084560] 487 pages in swap cache
May  7 01:36:54 my-desktop kernel: [26360.084562] Swap cache stats: add 103012, delete 102525, find 146/203
May  7 01:36:54 my-desktop kernel: [26360.084565] Free swap  = 0kB
May  7 01:36:54 my-desktop kernel: [26360.084566] Total swap = 409616kB
May  7 01:36:54 my-desktop kernel: [26360.097580] 327648 pages RAM
May  7 01:36:54 my-desktop kernel: [26360.097583] 100338 pages HighMem
May  7 01:36:54 my-desktop kernel: [26360.097585] 6390 pages reserved
May  7 01:36:54 my-desktop kernel: [26360.097587] 5201 pages shared
May  7 01:36:54 my-desktop kernel: [26360.097588] 313267 pages non-shared
May  7 01:36:54 my-desktop kernel: [26360.097592] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.097598] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.100380] kio_file invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
May  7 01:36:54 my-desktop kernel: [26360.100387] kio_file cpuset=/ mems_allowed=0
May  7 01:36:54 my-desktop kernel: [26360.100392] Pid: 2104, comm: kio_file Tainted: P   M       2.6.32-22-generic #33-Ubuntu
May  7 01:36:54 my-desktop kernel: [26360.100395] Call Trace:
May  7 01:36:54 my-desktop kernel: [26360.100407]  [<c01cc814>] oom_kill_process+0xa4/0x2b0
May  7 01:36:54 my-desktop kernel: [26360.100411]  [<c01cce89>] ? select_bad_process+0xa9/0xe0
May  7 01:36:54 my-desktop kernel: [26360.100415]  [<c01ccf11>] __out_of_memory+0x51/0xa0
May  7 01:36:54 my-desktop kernel: [26360.100419]  [<c01ccfb8>] out_of_memory+0x58/0xb0
May  7 01:36:54 my-desktop kernel: [26360.100424]  [<c01cf7c7>] __alloc_pages_slowpath+0x407/0x4a0
May  7 01:36:54 my-desktop kernel: [26360.100429]  [<c01cf99a>] __alloc_pages_nodemask+0x13a/0x170
May  7 01:36:54 my-desktop kernel: [26360.100434]  [<c01d1fda>] __do_page_cache_readahead+0xea/0x200
May  7 01:36:54 my-desktop kernel: [26360.100439]  [<c01d2116>] ra_submit+0x26/0x30
May  7 01:36:54 my-desktop kernel: [26360.100442]  [<c01cc10c>] filemap_fault+0x3dc/0x410
May  7 01:36:54 my-desktop kernel: [26360.100447]  [<c01e4650>] __do_fault+0x40/0x490
May  7 01:36:54 my-desktop kernel: [26360.100451]  [<c01e6259>] handle_mm_fault+0x139/0x390
May  7 01:36:54 my-desktop kernel: [26360.100458]  [<c058dacd>] do_page_fault+0x10d/0x3a0
May  7 01:36:54 my-desktop kernel: [26360.100462]  [<c058d9c0>] ? do_page_fault+0x0/0x3a0
May  7 01:36:54 my-desktop kernel: [26360.100466]  [<c058b9c3>] error_code+0x73/0x80
May  7 01:36:54 my-desktop kernel: [26360.100469] Mem-Info:
May  7 01:36:54 my-desktop kernel: [26360.100471] DMA per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.100474] CPU    0: hi:    0, btch:   1 usd:   0
May  7 01:36:54 my-desktop kernel: [26360.100476] Normal per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.100478] CPU    0: hi:  186, btch:  31 usd: 132
May  7 01:36:54 my-desktop kernel: [26360.100480] HighMem per-cpu:
May  7 01:36:54 my-desktop kernel: [26360.100483] CPU    0: hi:  186, btch:  31 usd:  93
May  7 01:36:54 my-desktop kernel: [26360.100488] active_anon:151485 inactive_anon:151617 isolated_anon:0
May  7 01:36:54 my-desktop kernel: [26360.100490]  active_file:267 inactive_file:462 isolated_file:0
May  7 01:36:54 my-desktop kernel: [26360.100491]  unevictable:0 dirty:0 writeback:80 unstable:0
May  7 01:36:54 my-desktop kernel: [26360.100493]  free:5399 slab_reclaimable:1352 slab_unreclaimable:2479
May  7 01:36:54 my-desktop kernel: [26360.100494]  mapped:781 shmem:482 pagetables:2129 bounce:0
May  7 01:36:54 my-desktop kernel: [26360.100502] DMA free:5072kB min:64kB low:80kB high:96kB active_anon:1544kB inactive_anon:1792kB active_file:8kB inactive_file:96kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15804kB mlocked:0kB dirty:0kB writeback:0kB mapped:20kB shmem:0kB slab_reclaimable:4kB slab_unreclaimable:4kB kernel_stack:0kB pagetables:8kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.100509] lowmem_reserve[]: 0 865 1254 1254
May  7 01:36:54 my-desktop kernel: [26360.100519] Normal free:16152kB min:3728kB low:4660kB high:5592kB active_anon:414088kB inactive_anon:414204kB active_file:260kB inactive_file:344kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:12kB mapped:496kB shmem:168kB slab_reclaimable:5404kB slab_unreclaimable:9912kB kernel_stack:2000kB pagetables:3960kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:1728 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.100527] lowmem_reserve[]: 0 0 3111 3111
May  7 01:36:54 my-desktop kernel: [26360.100536] HighMem free:372kB min:388kB low:804kB high:1224kB active_anon:190308kB inactive_anon:190472kB active_file:800kB inactive_file:1408kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:398216kB mlocked:0kB dirty:0kB writeback:308kB mapped:2608kB shmem:1760kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:4548kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:4320 all_unreclaimable? yes
May  7 01:36:54 my-desktop kernel: [26360.100543] lowmem_reserve[]: 0 0 0 0
May  7 01:36:54 my-desktop kernel: [26360.100547] DMA: 2*4kB 1*8kB 2*16kB 1*32kB 2*64kB 2*128kB 2*256kB 4*512kB 2*1024kB 0*2048kB 0*4096kB = 5072kB
May  7 01:36:54 my-desktop kernel: [26360.100558] Normal: 3024*4kB 9*8kB 1*16kB 0*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 16152kB
May  7 01:36:54 my-desktop kernel: [26360.100568] HighMem: 1*4kB 0*8kB 1*16kB 1*32kB 5*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 372kB
May  7 01:36:54 my-desktop kernel: [26360.100578] 1704 total pagecache pages
May  7 01:36:54 my-desktop kernel: [26360.100580] 487 pages in swap cache
May  7 01:36:54 my-desktop kernel: [26360.100583] Swap cache stats: add 103012, delete 102525, find 146/203
May  7 01:36:54 my-desktop kernel: [26360.100585] Free swap  = 0kB
May  7 01:36:54 my-desktop kernel: [26360.100587] Total swap = 409616kB
May  7 01:36:54 my-desktop kernel: [26360.113703] 327648 pages RAM
May  7 01:36:54 my-desktop kernel: [26360.113706] 100338 pages HighMem
May  7 01:36:54 my-desktop kernel: [26360.113708] 6390 pages reserved
May  7 01:36:54 my-desktop kernel: [26360.113710] 5201 pages shared
May  7 01:36:54 my-desktop kernel: [26360.113712] 313267 pages non-shared
May  7 01:36:54 my-desktop kernel: [26360.113716] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.113721] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.116453] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.116459] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.120414] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.120420] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.124447] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.124454] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.128524] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.128530] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.132428] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.132433] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.136426] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.136432] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.142517] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.142525] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.144385] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.144391] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.148283] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.148288] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.152266] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.152271] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.156379] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.156385] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.160298] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.160304] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.164281] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.164286] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.168387] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.168393] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.172314] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.172320] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.176298] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.176303] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.180290] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.180295] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.184366] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.184371] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.188331] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.188336] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.192325] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.192331] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.196365] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.196371] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.200340] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.200345] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.204367] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.204462] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.208360] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.208366] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.212351] Out of memory: kill process 1257 (kdeinit4) score 707338 or a child
May  7 01:36:54 my-desktop kernel: [26360.212356] Killed process 1408 (ksmserver)
May  7 01:36:54 my-desktop kernel: [26360.452193] Out of memory: kill process 1257 (kdeinit4) score 699911 or a child
May  7 01:36:54 my-desktop kernel: [26360.452200] Killed process 1442 (kwrited)
May  7 01:36:54 my-desktop kernel: [26360.684556] Out of memory: kill process 1257 (kdeinit4) score 697925 or a child
May  7 01:36:54 my-desktop kernel: [26360.684563] Killed process 1501 (python)
May  7 01:37:31 my-desktop acpid: client 1079[0:0] has disconnected
May  7 01:37:31 my-desktop acpid: client 1079[0:0] has disconnected
May  7 01:37:31 my-desktop acpid: client connected from 1079[0:0]
May  7 01:37:31 my-desktop acpid: 1 client rule loaded
May  7 01:37:31 my-desktop acpid: client connected from 1079[0:0]
May  7 01:37:31 my-desktop acpid: 1 client rule loaded
May  7 01:37:35 my-desktop kdm_greet[2806]: Cannot load /usr/share/kde4/apps/kdm/faces/.default.face: No such file or directory
May  7 02:17:01 my-desktop CRON[2825]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  7 03:17:01 my-desktop CRON[2833]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  7 04:17:01 my-desktop CRON[2841]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  7 04:38:06 my-desktop kernel: [37240.306902] input: Logitech MX1000 mouse as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1.1/3-1.1:1.0/bluetooth/hci0/hci0:11/input12
May  7 04:38:06 my-desktop kernel: [37240.307434] generic-bluetooth 0005:046D:B003.0006: input,hidraw2: BLUETOOTH HID v43.10 Mouse [Logitech MX1000 mouse] on 00:07:61:43:86:3F
May  7 04:38:25 my-desktop anacron[2988]: Anacron 2.3 started on 2010-05-07
May  7 04:38:25 my-desktop anacron[2988]: Will run job `cron.daily' in 5 min.
May  7 04:38:25 my-desktop anacron[2988]: Jobs will be executed sequentially
May  7 04:38:45 my-desktop python: hp-systray[3065]: error: option -s not recognized
May  7 04:43:25 my-desktop anacron[2988]: Job `cron.daily' started
May  7 04:43:25 my-desktop anacron[3267]: Updated timestamp for job `cron.daily' to 2010-05-07


I run Deluge at night for d/l on the scheduler to d/l between 2-8 am.
At 4:38 am I logged back in to KDE and I left the computer running at about 10 pm on the 6th of May...so is this a KDE error, out of memory ???

Has anybody else experienced this ?



Kubunut

---

### Post by kubunut on 2010-05-07
Update: I noticed that deluge seems to hang sometimes and that the parent process of deluge is kdeinit4 or something which could be the reason....dammit....

---

