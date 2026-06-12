---
title: "Ubuntu 10.04 RAM - buffers/cache problem."
date: 2010-10-05
forum: General Help
---

### Post by Andrea9 on 2010-10-05
Hi to all, (sorry for my english!)

If Skype, Thunderbird, Firefox running and I start virtualmachine with VirtualBox (XP 1.5 GB RAM dedicated) my system kill some processes (VirtualBox, Skype, ecc.).

this is "free -m" when the system kill processes

```
                  total       used       free     shared    buffers     cached
Mem:          3023       2943         80          0          0       1518
-/+ buffers/cache:       1424       1598
```why buffer/cache is not cleaned instead of kill any processes?

And this is syslog in /var/log/

```
Oct  5 08:55:01 NB-A9 pulseaudio[1667]: ratelimit.c: 565 events suppressed
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814433] gnome-settings- invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814442] gnome-settings- cpuset=/ mems_allowed=0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814450] Pid: 1630, comm: gnome-settings- Tainted: P           2.6.32-25-generic #44-Ubuntu
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814455] Call Trace:
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814469]  [<c01cd4f4>] oom_kill_process+0xa4/0x2b0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814477]  [<c01cdb69>] ? select_bad_process+0xa9/0xe0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814484]  [<c01cdbf1>] __out_of_memory+0x51/0xa0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814491]  [<c01cdc98>] out_of_memory+0x58/0xb0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814498]  [<c01d04a7>] __alloc_pages_slowpath+0x407/0x4a0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814507]  [<c01d067a>] __alloc_pages_nodemask+0x13a/0x170
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814515]  [<c01d2c3a>] __do_page_cache_readahead+0xea/0x200
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814523]  [<c01d2d76>] ra_submit+0x26/0x30
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814529]  [<c01ccdec>] filemap_fault+0x3dc/0x410
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814537]  [<c01e5360>] __do_fault+0x40/0x490
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814544]  [<c01e6f69>] handle_mm_fault+0x139/0x390
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814553]  [<c058f72d>] do_page_fault+0x10d/0x3a0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814561]  [<c058f620>] ? do_page_fault+0x0/0x3a0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814567]  [<c058d623>] error_code+0x73/0x80
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814572] Mem-Info:
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814576] DMA per-cpu:
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814581] CPU    0: hi:    0, btch:   1 usd:   0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814586] CPU    1: hi:    0, btch:   1 usd:   0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814589] Normal per-cpu:
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814594] CPU    0: hi:  186, btch:  31 usd: 130
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814599] CPU    1: hi:  186, btch:  31 usd: 182
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814602] HighMem per-cpu:
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814607] CPU    0: hi:  186, btch:  31 usd: 107
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814611] CPU    1: hi:  186, btch:  31 usd: 165
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814621] active_anon:91587 inactive_anon:387431 isolated_anon:0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814623]  active_file:438 inactive_file:515 isolated_file:0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814625]  unevictable:8 dirty:0 writeback:3 unstable:0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814627]  free:20490 slab_reclaimable:1968 slab_unreclaimable:3493
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814630]  mapped:257375 shmem:387745 pagetables:1751 bounce:0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814642] DMA free:8528kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15852kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:8kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814652] lowmem_reserve[]: 0 865 3030 3030
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814670] Normal free:72936kB min:3728kB low:4660kB high:5592kB active_anon:9400kB inactive_anon:44252kB active_file:752kB inactive_file:924kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:0kB mapped:671564kB shmem:44276kB slab_reclaimable:7872kB slab_unreclaimable:13964kB kernel_stack:2576kB pagetables:848kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:2400 all_unreclaimable? yes
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814680] lowmem_reserve[]: 0 0 17326 17326
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814698] HighMem free:496kB min:512kB low:2844kB high:5176kB active_anon:356948kB inactive_anon:1505472kB active_file:1000kB inactive_file:1136kB unevictable:32kB isolated(anon):0kB isolated(file):0kB present:2217744kB mlocked:32kB dirty:0kB writeback:12kB mapped:357936kB shmem:1506704kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:6156kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:3232 all_unreclaimable? yes
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814709] lowmem_reserve[]: 0 0 0 0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814718] DMA: 6*4kB 5*8kB 5*16kB 6*32kB 4*64kB 2*128kB 4*256kB 1*512kB 2*1024kB 2*2048kB 0*4096kB = 8528kB
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814741] Normal: 372*4kB 765*8kB 599*16kB 316*32kB 215*64kB 133*128kB 36*256kB 3*512kB 0*1024kB 0*2048kB 1*4096kB = 72936kB
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814764] HighMem: 102*4kB 11*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 496kB
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814786] 388772 total pagecache pages
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814790] 0 pages in swap cache
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814794] Swap cache stats: add 0, delete 0, find 0/0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814798] Free swap  = 0kB
Oct  5 08:55:08 NB-A9 kernel: [ 2644.814801] Total swap = 0kB
Oct  5 08:55:08 NB-A9 kernel: [ 2644.826473] 786128 pages RAM
Oct  5 08:55:08 NB-A9 kernel: [ 2644.826477] 558802 pages HighMem
Oct  5 08:55:08 NB-A9 kernel: [ 2644.826481] 266254 pages reserved
Oct  5 08:55:08 NB-A9 kernel: [ 2644.826485] 11977 pages shared
Oct  5 08:55:08 NB-A9 kernel: [ 2644.826488] 494590 pages non-shared
Oct  5 08:55:08 NB-A9 kernel: [ 2644.826494] Out of memory: kill process 2679 (run-mozilla.sh) score 517772 or a child
Oct  5 08:55:08 NB-A9 kernel: [ 2644.826502] Killed process 2683 (firefox-bin)
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880685] mysqld invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880693] mysqld cpuset=/ mems_allowed=0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880701] Pid: 1249, comm: mysqld Tainted: P           2.6.32-25-generic #44-Ubuntu
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880706] Call Trace:
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880719]  [<c01cd4f4>] oom_kill_process+0xa4/0x2b0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880728]  [<c01cdb69>] ? select_bad_process+0xa9/0xe0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880735]  [<c01cdbf1>] __out_of_memory+0x51/0xa0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880742]  [<c01cdc98>] out_of_memory+0x58/0xb0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880749]  [<c01d04a7>] __alloc_pages_slowpath+0x407/0x4a0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880757]  [<c01d067a>] __alloc_pages_nodemask+0x13a/0x170
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880766]  [<c01d2c3a>] __do_page_cache_readahead+0xea/0x200
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880774]  [<c01d2d76>] ra_submit+0x26/0x30
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880780]  [<c01ccdec>] filemap_fault+0x3dc/0x410
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880788]  [<c01e5360>] __do_fault+0x40/0x490
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880795]  [<c01e6f69>] handle_mm_fault+0x139/0x390
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880804]  [<c058f72d>] do_page_fault+0x10d/0x3a0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880812]  [<c0219232>] ? sys_select+0x42/0xc0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880819]  [<c058f620>] ? do_page_fault+0x0/0x3a0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880826]  [<c058d623>] error_code+0x73/0x80
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880830] Mem-Info:
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880834] DMA per-cpu:
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880839] CPU    0: hi:    0, btch:   1 usd:   0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880843] CPU    1: hi:    0, btch:   1 usd:   0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880847] Normal per-cpu:
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880852] CPU    0: hi:  186, btch:  31 usd:  95
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880857] CPU    1: hi:  186, btch:  31 usd: 168
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880860] HighMem per-cpu:
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880865] CPU    0: hi:  186, btch:  31 usd: 107
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880870] CPU    1: hi:  186, btch:  31 usd: 165
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880879] active_anon:91587 inactive_anon:387431 isolated_anon:0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880881]  active_file:449 inactive_file:574 isolated_file:0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880883]  unevictable:8 dirty:0 writeback:3 unstable:0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880885]  free:20525 slab_reclaimable:1968 slab_unreclaimable:3493
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880888]  mapped:257375 shmem:387745 pagetables:1751 bounce:0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880900] DMA free:8528kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15852kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:8kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880909] lowmem_reserve[]: 0 865 3030 3030
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880928] Normal free:73076kB min:3728kB low:4660kB high:5592kB active_anon:9400kB inactive_anon:44252kB active_file:796kB inactive_file:1012kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:0kB mapped:671564kB shmem:44276kB slab_reclaimable:7872kB slab_unreclaimable:13964kB kernel_stack:2576kB pagetables:848kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:832 all_unreclaimable? no
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880938] lowmem_reserve[]: 0 0 17326 17326
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880956] HighMem free:496kB min:512kB low:2844kB high:5176kB active_anon:356948kB inactive_anon:1505472kB active_file:1000kB inactive_file:1284kB unevictable:32kB isolated(anon):0kB isolated(file):0kB present:2217744kB mlocked:32kB dirty:0kB writeback:12kB mapped:357936kB shmem:1506704kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:6156kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:3232 all_unreclaimable? yes
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880967] lowmem_reserve[]: 0 0 0 0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880976] DMA: 6*4kB 5*8kB 5*16kB 6*32kB 4*64kB 2*128kB 4*256kB 1*512kB 2*1024kB 2*2048kB 0*4096kB = 8528kB
Oct  5 08:55:08 NB-A9 kernel: [ 2644.880999] Normal: 401*4kB 776*8kB 599*16kB 317*32kB 215*64kB 133*128kB 36*256kB 3*512kB 0*1024kB 0*2048kB 1*4096kB = 73172kB
Oct  5 08:55:08 NB-A9 kernel: [ 2644.881026] HighMem: 102*4kB 11*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 496kB
Oct  5 08:55:08 NB-A9 kernel: [ 2644.881049] 388772 total pagecache pages
Oct  5 08:55:08 NB-A9 kernel: [ 2644.881052] 0 pages in swap cache
Oct  5 08:55:08 NB-A9 kernel: [ 2644.881057] Swap cache stats: add 0, delete 0, find 0/0
Oct  5 08:55:08 NB-A9 kernel: [ 2644.881060] Free swap  = 0kB
Oct  5 08:55:08 NB-A9 kernel: [ 2644.881064] Total swap = 0kB
Oct  5 08:55:08 NB-A9 kernel: [ 2644.892519] 786128 pages RAM
Oct  5 08:55:08 NB-A9 kernel: [ 2644.892523] 558802 pages HighMem
Oct  5 08:55:08 NB-A9 kernel: [ 2644.892526] 266254 pages reserved
Oct  5 08:55:08 NB-A9 kernel: [ 2644.892529] 11959 pages shared
Oct  5 08:55:08 NB-A9 kernel: [ 2644.892532] 494637 pages non-shared
Oct  5 08:55:08 NB-A9 kernel: [ 2644.892539] Out of memory: kill process 2722 (VirtualBox) score 307383 or a child
Oct  5 08:55:08 NB-A9 kernel: [ 2644.892545] Killed process 2722 (VirtualBox)
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055408] udisks-daemon invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055416] udisks-daemon cpuset=/ mems_allowed=0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055423] Pid: 1809, comm: udisks-daemon Tainted: P           2.6.32-25-generic #44-Ubuntu
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055428] Call Trace:
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055441]  [<c01cd4f4>] oom_kill_process+0xa4/0x2b0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055449]  [<c01cdb69>] ? select_bad_process+0xa9/0xe0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055456]  [<c01cdbf1>] __out_of_memory+0x51/0xa0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055463]  [<c01cdc98>] out_of_memory+0x58/0xb0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055470]  [<c01d04a7>] __alloc_pages_slowpath+0x407/0x4a0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055479]  [<c01d067a>] __alloc_pages_nodemask+0x13a/0x170
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055487]  [<c01d2c3a>] __do_page_cache_readahead+0xea/0x200
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055495]  [<c01d2d76>] ra_submit+0x26/0x30
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055502]  [<c01ccdec>] filemap_fault+0x3dc/0x410
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055508]  [<c0215482>] ? do_filp_open+0x4d2/0x990
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055516]  [<c01e5360>] __do_fault+0x40/0x490
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055523]  [<c01e6f69>] handle_mm_fault+0x139/0x390
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055532]  [<c058f72d>] do_page_fault+0x10d/0x3a0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055540]  [<c058f620>] ? do_page_fault+0x0/0x3a0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055546]  [<c058d623>] error_code+0x73/0x80
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055553]  [<c0590000>] ? show_kprobe_addr+0x30/0x100
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055558] Mem-Info:
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055561] DMA per-cpu:
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055566] CPU    0: hi:    0, btch:   1 usd:   0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055571] CPU    1: hi:    0, btch:   1 usd:   0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055574] Normal per-cpu:
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055579] CPU    0: hi:  186, btch:  31 usd:  63
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055584] CPU    1: hi:  186, btch:  31 usd: 168
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055587] HighMem per-cpu:
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055591] CPU    0: hi:  186, btch:  31 usd: 107
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055596] CPU    1: hi:  186, btch:  31 usd: 165
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055606] active_anon:91588 inactive_anon:387431 isolated_anon:0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055608]  active_file:454 inactive_file:645 isolated_file:0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055610]  unevictable:8 dirty:1 writeback:0 unstable:0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055612]  free:20513 slab_reclaimable:1960 slab_unreclaimable:3493
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055614]  mapped:257362 shmem:387745 pagetables:1751 bounce:0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055626] DMA free:8528kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15852kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:8kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055636] lowmem_reserve[]: 0 865 3030 3030
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055654] Normal free:73028kB min:3728kB low:4660kB high:5592kB active_anon:9400kB inactive_anon:44252kB active_file:744kB inactive_file:1344kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:4kB writeback:0kB mapped:671524kB shmem:44276kB slab_reclaimable:7840kB slab_unreclaimable:13964kB kernel_stack:2376kB pagetables:848kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:768 all_unreclaimable? no
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055665] lowmem_reserve[]: 0 0 17326 17326
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055682] HighMem free:496kB min:512kB low:2844kB high:5176kB active_anon:356952kB inactive_anon:1505472kB active_file:1072kB inactive_file:1236kB unevictable:32kB isolated(anon):0kB isolated(file):0kB present:2217744kB mlocked:32kB dirty:0kB writeback:0kB mapped:357924kB shmem:1506704kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:6156kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:3232 all_unreclaimable? yes
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055693] lowmem_reserve[]: 0 0 0 0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055702] DMA: 6*4kB 5*8kB 5*16kB 6*32kB 4*64kB 2*128kB 4*256kB 1*512kB 2*1024kB 2*2048kB 0*4096kB = 8528kB
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055725] Normal: 367*4kB 775*8kB 599*16kB 317*32kB 215*64kB 133*128kB 36*256kB 3*512kB 0*1024kB 0*2048kB 1*4096kB = 73028kB
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055748] HighMem: 102*4kB 11*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 496kB
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055770] 388842 total pagecache pages
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055773] 0 pages in swap cache
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055778] Swap cache stats: add 0, delete 0, find 0/0
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055781] Free swap  = 0kB
Oct  5 08:55:08 NB-A9 kernel: [ 2645.055784] Total swap = 0kB
Oct  5 08:55:08 NB-A9 kernel: [ 2645.067368] 786128 pages RAM
Oct  5 08:55:08 NB-A9 kernel: [ 2645.067373] 558802 pages HighMem
Oct  5 08:55:08 NB-A9 kernel: [ 2645.067376] 266254 pages reserved
Oct  5 08:55:08 NB-A9 kernel: [ 2645.067379] 11981 pages shared
Oct  5 08:55:08 NB-A9 kernel: [ 2645.067382] 494704 pages non-shared
Oct  5 08:55:08 NB-A9 kernel: [ 2645.067389] Out of memory: kill process 2703 (skype-wrapper) score 227861 or a child
Oct  5 08:55:08 NB-A9 kernel: [ 2645.067395] Killed process 2704 (skype)
Oct  5 08:55:08 NB-A9 kernel: [ 2646.721091] device eth0 left promiscuous mode
```I use this system and this configuration for months and I've never had any problems so far.

System:
Ubuntu 10.04 32-bit, 3 GB RAM, Core2 T5550.

regards

Andrea

---

### Post by searchfgold6789 on 2010-10-05
Maybe your system is complaining of not having enough memory..

---

### Post by CharlesA on 2010-10-05
It sounds like you are pushing it over the limit of memory you have free.

Does the same thing happen if you reduce the VM's memory to 1GB (or 512MB)?

---

### Post by Andrea9 on 2010-10-05
> **CharlesA said:**
> It sounds like you are pushing it over the limit of memory you have free.

Does the same thing happen if you reduce the VM's memory to 1GB (or 512MB)?

Ok, but buffer/cache is not "free" memory? And why for months and I've never had any problems whit same configuration?


If I reduce VM's memory to 1GB and i run Skype, firefox, ecc. my hard disk starts to work and I am forced to kill some processes or the system is not usable. The mouse is slow.

---

### Post by CharlesA on 2010-10-05
Buffers and cache are "free" memory, since the kernel will swap it out as it's needed.

It really sounds like a hardware problem tbh.

Have you run memtest86+ on the host machine overnight?

---

### Post by Andrea9 on 2010-10-05
> **CharlesA said:**
> Buffers and cache are "free" memory, since the kernel will swap it out as it's needed.

It really sounds like a hardware problem tbh.

Have you run memtest86+ on the host machine overnight?

I've run memtest86+ on the host machine in this morning without errors. :(

---

### Post by plucky on 2010-10-05
You have no swap partition.

Did you remove it?
Or 
Was that how you set up your system?

Try adding one and see if that helps
Post output of ```
sudo fdisk -l
cat /etc/fstab
sudo blkid
```

---

### Post by Andrea9 on 2010-10-05
> **plucky said:**
> You have no swap partition.
Did you remove it?
Or 
Was that how you set up your system?


**I have never had swap partition.**

But _in this momen_t i have created swap on SD Card with
[I]sudo mkswap -f /dev/mmcblk0
sudo swapon /dev/mmcblk0[/I]
for resolve this problem at the moment, and now

_free -m_
```
             total       used       free     shared    buffers     cached
Mem:          3023       2928         94          0         31        877
-/+ buffers/cache:       2019       1004
Swap:         1938       1046        891
```


> **plucky said:**
> 
Try adding one and see if that helps
Post output of ```
sudo fdisk -l
cat /etc/fstab
sudo blkid
```

_sudo fdisk -l_
```
Disco /dev/sda: 250.1 GB, 250059350016 byte
Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               2       28893   232074990    f  W95 Esteso (LBA)
/dev/sda2   *       28894       30401    12113010    7  HPFS/NTFS
/dev/sda5               2        6079    48821503+   7  HPFS/NTFS
/dev/sda6            6080       13374    58597056   83  Linux
/dev/sda7           13375       28893   124656336   83  Linux
```_cat /etc/fstab_
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=925c497f-d993-4edf-b794-8710aa7a0ccf /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=69645ecf-ac94-4866-a87d-99af212ace27 /home           ext4    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```_sudo blkid_```
/dev/sda2: LABEL="HP_RECOVERY" UUID="2C88743C8874071C" TYPE="ntfs" 
/dev/sda5: LABEL="XP" UUID="483494023493F164" TYPE="ntfs" 
/dev/sda6: UUID="925c497f-d993-4edf-b794-8710aa7a0ccf" TYPE="ext4" 
/dev/sda7: UUID="69645ecf-ac94-4866-a87d-99af212ace27" TYPE="ext4" 
/dev/mmcblk0: UUID="b6b6160a-8011-435d-85fb-700e127bfd5f" TYPE="swap" 
```[I]


thanks for help
[/I]

---

### Post by Andrea9 on 2010-10-06
Who uses the RAM? And the buffer / cache?

free -m
```

             total       used       free     shared    buffers     cached
Mem:          3023       1608       1414          0         57        415
-/+ buffers/cache:       1135       1887
Swap:         1938       1502        436


```

top

```
Tasks: 155 total,   1 running, 154 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  0.7%sy,  0.0%ni, 97.2%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   3095756k total,  1605004k used,  1490752k free,    57716k buffers
Swap:  1985016k total,  1538128k used,   446888k free,   409104k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
10386 root      20   0 54608  42m  12m S    3  1.4   0:06.76 Xorg               
10595 andrea    20   0  118m  13m  10m S    1  0.5   0:00.61 gnome-terminal     
10627 andrea    20   0  312m  68m  26m S    1  2.3   0:06.12 firefox-bin        
 1628 andrea     9 -11 94876 4700 3224 S    0  0.2   0:08.11 pulseaudio         
10519 andrea    20   0 96816  11m 9392 S    0  0.4   0:00.96 metacity           
10536 andrea    20   0 16952 2360 1960 S    0  0.1   0:00.01 gvfs-afc-volume    
10557 andrea    20   0 32180  13m  10m S    0  0.4   0:00.24 clock-applet       
    1 root      20   0  2812 1144  628 S    0  0.0   0:00.73 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:02.10 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    9 root      20   0     0    0    0 S    0  0.0   0:00.31 events/0           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root      20   0     0    0    0 S    0  0.0   0:00.02 netns              
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr          
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                 
   17 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers        
   18 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default        
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   21 root      20   0     0    0    0 S    0  0.0   0:03.67 kblockd/0          
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpid             
   24 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
   25 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug      
   26 root      20   0     0    0    0 S    0  0.0   0:02.02 ata/0              
   28 root      20   0     0    0    0 S    0  0.0   0:00.00 ata_aux            
   29 root      20   0     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd      
   30 root      20   0     0    0    0 S    0  0.0   0:00.00 khubd              
   31 root      20   0     0    0    0 S    0  0.0   0:00.40 kseriod            
   32 root      20   0     0    0    0 S    0  0.0   0:00.00 kmmcd              
   35 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd         
   36 root      20   0     0    0    0 S    0  0.0   0:33.11 kswapd0            
   37 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd               
   38 root      20   0     0    0    0 S    0  0.0   0:00.00 aio/0              
   40 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea    
   41 root      20   0     0    0    0 S    0  0.0   0:00.00 crypto/0           
   55 root      20   0     0    0    0 S    0  0.0   0:06.94 scsi_eh_0          
   56 root      20   0     0    0    0 S    0  0.0   0:00.02 scsi_eh_1          
   60 root      20   0     0    0    0 S    0  0.0   0:00.00 kstriped           
   61 root      20   0     0    0    0 S    0  0.0   0:00.00 kmpathd/0          
   63 root      20   0     0    0    0 S    0  0.0   0:00.00 kmpath_handlerd   
```thanks

---

### Post by CharlesA on 2010-10-06
> **Andrea9 said:**
> Who uses the RAM? And the buffer / cache?

Cache is memory used for disk caching.

Check [here]("http://www.linuxatemyram.com/") for more info.

---

### Post by Andrea9 on 2010-10-06
> **CharlesA said:**
> Cache is memory used for disk caching.

Check [here]("http://www.linuxatemyram.com/") for more info.

Ok, but

             > 
                             _______________total        used       free     shared    buffers     cached 
Mem:__________                            3023       1608       1414          0         57        415 
-/+ buffers/cache:               _[COLOR=Red]**____ 1135**[/COLOR]_       1887 
Swap:_________                            1938        _**[COLOR=Red]1502[/COLOR]**_        436
is used, right?

Only firefox running... (see "top" in my previus post)

thanks

---

### Post by CharlesA on 2010-10-06
The whole X enironment uses a fair amount of memory.

As for the swap file, I don't have why it's almost 100% used.

---

### Post by psusi on 2010-10-06
Reboot?

---

### Post by Andrea9 on 2010-10-06
> **psusi said:**
> Reboot?

work. 

But now can you read my first post in this thread? :)

---

### Post by psusi on 2010-10-06
What do you mean "work"?  Did it work?  And I did read the first post and concluded that you were trying to use all of your ram up, so the memory hogging process was killed.

---

### Post by Andrea9 on 2010-10-06
(Sorry for my englis)

If I reboot, the system at start it's ok. I have used same configuration (running WM with 1.5GB RAM, skype, firefox, thunderbird,OpenOffice) for months without any problem. (without partition swap, never)

Recently my system start to kill processes.

My questions:

Why buffer/cache is not released if necessary?
Why the system insted to release buffer/cache kill processes?


I've run memtest for 1 hour without errors. I have to execute ram test  for more hours?


thanks :wink:

---

### Post by psusi on 2010-10-06
That was your first question, and the answer to that was that you were using up all of your ram, even after almost all of the cache was freed.  Now your question is why is it using so much ram when you don't really have anything running.  My question is, does it still use that much ram after you reboot?

---

### Post by Andrea9 on 2010-10-06
> **psusi said:**
> That was your first question, and the answer to that was that you were using up all of your ram, even after **almost all of the cache was freed**.


Nearly 1 GB is still busy from buffer/cache...

> **psusi said:**
> 
Now your question is why is it using so much ram when you don't really have anything running.  My question is, does it still use that much ram after you reboot?
After reboot it's ok.

thanks

---

### Post by psusi on 2010-10-07
> **Andrea9 said:**
> Nearly 1 GB is still busy from buffer/cache...

That is because you aren't using it.  When you fire up the virtual machine that asks for 1.5 gb, you still didn't have that much even with the cache freed, hence why it was killed.

> **Andrea9 said:**
> 
After reboot it's ok.

thanks

There is a bug with ureadahead in lucid.  After you update some packages, the next reboot ureadahead will profile the boot to speed up subsequent boots.  After profiling, it does not free the memory it used, so you need to reboot again to get it back.

---

### Post by soldier1st on 2010-10-07
1.5GB os memory is too much for a VM. between 512MB to 1GB max is all it needs(depending on the os) and if you put more it could end up slowing the vm down(depends on os)

---

### Post by Andrea9 on 2010-10-10
> **psusi said:**
> That is because you aren't using it.  When you fire up the virtual machine that asks for 1.5 gb, you still didn't have that much even with the cache freed, hence why it was killed.

I'm sorry but I'm not able to explain.

_**System 3GB RAM, NO SWAP**_

At system start (I've started only firefox):

free -m
```
total       used       free     shared    buffers     cached
Mem:          3023        660       2362          0         90        310
-/+ buffers/cache:        259       2763
Swap:            0          0          0

```top

```
top - 11:34:00 up 3 min,  2 users,  load average: 0.65, 0.54, 0.23
Tasks: 167 total,   1 running, 166 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.4%us,  6.4%sy,  0.0%ni, 90.1%id,  1.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   3095756k total,   757084k used,  2338672k free,    92768k buffers
Swap:        0k total,        0k used,        0k free,   388548k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                             
  100 root      20   0  3188 1992  376 S   12  0.1   0:21.16 collector                                                                                                           
 2008 andrea    20   0  364m  91m  27m S    3  3.0   0:16.01 firefox-bin                                                                                                         
 1106 root      20   0 60508  48m  13m S    1  1.6   0:08.29 Xorg                                                                                                                
 1965 andrea    20   0  118m  13m  10m S    1  0.4   0:00.63 gnome-terminal                                                                                                      
 2080 andrea    20   0  2548 1236  924 R    1  0.0   0:00.04 top                                                                                                                 
    1 root      20   0  2808 1720 1220 S    0  0.1   0:00.48 init                                                                                                                
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                            
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                         
    4 root      20   0     0    0    0 S    0  0.0   0:00.17 ksoftirqd/0                                                                                                         
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                          
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                         
    7 root      20   0     0    0    0 S    0  0.0   0:00.01 ksoftirqd/1                                                                                                         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                          
    9 root      20   0     0    0    0 S    0  0.0   0:00.00 events/0                                                                                                            
   10 root      20   0     0    0    0 S    0  0.0   0:00.06 events/1                                                                                                            
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                                              
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                             
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns                                                                                                               
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr                                                                                                           
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                                                                                                                  
   17 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers                                                                                                         
   18 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                                                                         
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                                                       
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                                                                                                       
   21 root      20   0     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                                                                           
   22 root      20   0     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                                           
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                              
   24 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                        
   25 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug                                                                                                       
   26 root      20   0     0    0    0 S    0  0.0   0:00.02 ata/0                                                                                                               
   27 root      20   0     0    0    0 S    0  0.0   0:00.00 ata/1                                                                                                               
   28 root      20   0     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                                             
   29 root      20   0     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                                       
   30 root      20   0     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                               
   31 root      20   0     0    0    0 S    0  0.0   0:00.22 kseriod                                                                                                             
   32 root      20   0     0    0    0 S    0  0.0   0:00.00 kmmcd                                                                                                               
   35 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd                                                                                                          
   36 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                                             
   37 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                                                                                
   38 root      20   0     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                               
   39 root      20   0     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                               
   40 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                                                                                     
   41 root      20   0     0    0    0 S    0  0.0   0:00.00 crypto/0                  
```After Start VM with 1024 GB RAM.

free -m

```
             total       used       free     shared    buffers     cached
Mem:          3023       2935         87          0         47       1346
-/+ buffers/cache:       1541       **1481**
Swap:            0          0          0


```top

```
Cpu(s):  4.6%us,  8.0%sy,  0.5%ni, 85.2%id,  1.5%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   3095756k total,  2762260k used,   333496k free,    94116k buffers
Swap:        0k total,        0k used,        0k free,  1094196k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                             
 2121 andrea    20   0 1451m 1.2g 1.1g S   11 40.9   1:35.49 VirtualBox                                                                                                          
  100 root      20   0  3188 1992  376 S   11  0.1   0:46.34 collector                                                                                                           
 2008 andrea    20   0  364m  92m  27m S    5  3.1   0:27.86 firefox-bin                                                                                                         
 1106 root      20   0 62464  49m  13m S    2  1.6   0:14.33 Xorg                                                                                                                
 1965 andrea    20   0  119m  14m  10m S    1  0.5   0:01.48 gnome-terminal                                                                                                      
   65 root      20   0     0    0    0 S    0  0.0   0:00.31 kondemand/0                                                                                                         
    1 root      20   0  2808 1720 1220 S    0  0.1   0:00.49 init                                                                                                                
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                            
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                         
    4 root      20   0     0    0    0 S    0  0.0   0:00.34 ksoftirqd/0                                                                                                         
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                          
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                         
    7 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1                                                                                                         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                          
    9 root      20   0     0    0    0 S    0  0.0   0:00.02 events/0                                                                                                            
   10 root      20   0     0    0    0 S    0  0.0   0:00.06 events/1                                                                                                            
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                                              
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                             
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns                                                                                                               
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr                                                                                                           
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                                                                                                                  
   17 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers                                                                                                         
   18 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                                                                         
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                                                       
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                                                                                                       
   21 root      20   0     0    0    0 S    0  0.0   0:00.01 kblockd/0                                                                                                           
   22 root      20   0     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                                           
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                              
   24 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                        
   25 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug                                                                                                       
   26 root      20   0     0    0    0 S    0  0.0   0:00.06 ata/0                                                                                                               
   27 root      20   0     0    0    0 S    0  0.0   0:00.02 ata/1                                                                                                               
   28 root      20   0     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                                             
   29 root      20   0     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                                       
   30 root      20   0     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                               
   31 root      20   0     0    0    0 S    0  0.0   0:00.22 kseriod                                                                                                             
   32 root      20   0     0    0    0 S    0  0.0   0:00.00 kmmcd                                                                                                               
   35 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd                                                                                                          
   36 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                                             
   37 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                                                                                
   38 root      20   0     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                               
   39 root      20   0     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                               
   40 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea       
```I've **1481** MB RAM free, right?

Then i can start other programs, OpenOffice, Thunderbird, skype.... right?

free -m

```
             total       used       free     shared    buffers     cached
Mem:          3023       2938         84          0         28       1275
-/+ buffers/cache:       1634       1388
Swap:            0          0          0

```top

```
Tasks: 162 total,   1 running, 161 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.7%us, 10.0%sy,  0.7%ni, 82.5%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   3095756k total,  3009804k used,    85952k free,    29216k buffers
Swap:        0k total,        0k used,        0k free,  1305268k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2121 andrea    20   0 1453m 1.2g 1.1g S   14 41.0   4:22.42 VirtualBox         
  100 root      20   0  3188 1992  376 S   11  0.1   1:33.31 collector          
 1965 andrea    20   0  119m  14m  10m S    4  0.5   0:03.30 gnome-terminal     
 1106 root      20   0 64504  51m  13m S    3  1.7   0:29.69 Xorg               
 2008 andrea    20   0  420m  96m  28m S    3  3.2   0:57.49 firefox-bin        
 1675 andrea    20   0  107m  11m 9924 S    1  0.4   0:02.97 metacity           
 2243 andrea    20   0  199m  57m  21m S    1  1.9   0:03.61 skype              
    4 root      20   0     0    0    0 S    0  0.0   0:00.61 ksoftirqd/0        
   10 root      20   0     0    0    0 S    0  0.0   0:00.07 events/1           
 1075 root      20   0  4836 2228 1900 S    0  0.1   0:00.02 wpa_supplicant     
 2263 andrea    20   0  2548 1228  924 R    0  0.0   0:00.13 top                
    1 root      20   0  2808 1720 1220 S    0  0.1   0:00.49 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.07 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      20   0     0    0    0 S    0  0.0   0:00.03 events/0           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns              
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr          
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                 
   17 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers        
   18 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default        
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/1      
   21 root      20   0     0    0    0 S    0  0.0   0:00.01 kblockd/0          
   22 root      20   0     0    0    0 S    0  0.0   0:00.00 kblockd/1          
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpid             
   24 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
   25 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug      
   26 root      20   0     0    0    0 S    0  0.0   0:00.15 ata/0              
   27 root      20   0     0    0    0 S    0  0.0   0:00.04 ata/1              
   28 root      20   0     0    0    0 S    0  0.0   0:00.00 ata_aux            
   29 root      20   0     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd      
   30 root      20   0     0    0    0 S    0  0.0   0:00.00 khubd              
   31 root      20   0     0    0    0 S    0  0.0   0:00.22 kseriod            
   32 root      20   0     0    0    0 S    0  0.0   0:00.00 kmmcd              
   35 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd    
```In top, I read that 1388 MB RAM are cached, then she's free. right?

If my VM have 1024MB or 1536MB, I'have enough free memory. Now 1388MB, if start my VM with 1536 MB, 1388+1024-1536=876 MB free (about).


Now I stop and restart VM changing the VM RAM from 1024 to 1536:

(Why? Because I had for ever this configuration and this have worked from ever.)

Now, this is free -m -s 2 on loading WM (whit 1536MB RAM)

**Look at start that I've 2422 MB free** and look to _the end_
```
andrea@NB-A9:~$ free -m -s 2
             total       used       free     shared    buffers     cached
Mem:          3023       2002       1020          0         13       1388
-/+ buffers/cache:        600       2422
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2016       1007          0         13       1394
-/+ buffers/cache:        607       2415
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2083        939          0         14       1405
-/+ buffers/cache:        664       2358
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2185        837          0         14       1406
-/+ buffers/cache:        765       2257
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2187        836          0         14       1407
-/+ buffers/cache:        765       2257
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2188        834          0         14       1408
-/+ buffers/cache:        765       2257
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2189        833          0         14       1410
-/+ buffers/cache:        765       2257
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2191        831          0         14       1412
-/+ buffers/cache:        765       2257
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2192        830          0         14       1413
-/+ buffers/cache:        765       2257
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2194        828          0         14       1415
-/+ buffers/cache:        765       2258
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2197        825          0         14       1416
-/+ buffers/cache:        767       2256
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2213        809          0         14       1423
-/+ buffers/cache:        775       2247
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2256        766          0         14       1441
-/+ buffers/cache:        800       2222
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2310        712          0         14       1473
-/+ buffers/cache:        822       2200
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2362        660          0         14       1503
-/+ buffers/cache:        845       2178
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2433        589          0         14       1541
-/+ buffers/cache:        878       2145
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2498        525          0         14       1578
-/+ buffers/cache:        905       2118
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2542        480          0         14       1607
-/+ buffers/cache:        921       2102
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2587        435          0         14       1638
-/+ buffers/cache:        935       2088
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2623        399          0         14       1662
-/+ buffers/cache:        947       2076
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2663        359          0         14       1683
-/+ buffers/cache:        965       2057
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2719        304          0         14       1714
-/+ buffers/cache:        990       2032
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2762        260          0         14       1731
-/+ buffers/cache:       1016       2006
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2851        171          0         14       1776
-/+ buffers/cache:       1060       1962
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2863        159          0         14       1779
-/+ buffers/cache:       1070       1952
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2892        130          0         14       1780
-/+ buffers/cache:       1097       1925
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2936         86          0         11       1691
-/+ buffers/cache:       1233       1789
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2937         85          0          3       1380
-/+ buffers/cache:       1553       1469
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2943         80          0          0       1136
-/+ buffers/cache:       1806       1216
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2895        127          0          0       1155
-/+ buffers/cache:       1739       1283
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2920        102          0          0       1172
-/+ buffers/cache:       1747       1275
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2941         82          0          0       1187
-/+ buffers/cache:       1752       1270
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2943         80          0          1       1168
-/+ buffers/cache:       1773       1249
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2943         80          0          0       1150
-/+ buffers/cache:       1792       1230
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:          3023       2942         80          0          0       1146
-/+ buffers/cache:       1796       [COLOR=Red]**1226**[/COLOR]
Swap:            0          0          0

HERE THE SYSTEM KILL VirtualBox, Skype, Firefox....

             total       used       free     shared    buffers     cached
Mem:          3023       1423       **[COLOR=Blue]1599[/COLOR]**          0          0       1162
-/+ buffers/cache:        260       [COLOR=Red]**2762**[/COLOR]
Swap:            0          0          0


```

Why does the system when he killed processes still had plenty of RAM available? _1226_ MB

After system kill RAM available: 1226 + 1536 = [COLOR=Red]2762[/COLOR]  ... :-o then the loading of VM was completed.


I hope that is clearer now. :)


Thanks,

Andrea

---

### Post by Andrea9 on 2010-10-11
up

---

### Post by Andrea9 on 2010-10-12
I found the problem.

Despite the 7 hours of memtest had not detected anything.

I changed the bench with a 1 GB RAM to 2 GB. (Now  have 4 GB but the system only detects 32-bit 3. Then as before) Now the  system lets me run all the applications together without blocking 1 GB  for buffer / cache and without killing anyone.

So I can say that what the system was not asking too much. It was probably a hardware problem or compatibility.

thanks

Andrea

---

### Post by Andrea9 on 2010-10-12
The problem occurred again. :(

---

### Post by abussuhail on 2010-12-03
try this as root:

$ echo 1 > /proc/sys/vm/drop_caches

---

