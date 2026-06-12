---
title: "Pidgin + Firefox Crash"
date: 2010-05-14
forum: General Help
---

### Post by Lucky75 on 2010-05-14
Hi all,

I've had issues with this for a while, but this is the first time it's pissed me off to post about it. Once in a while, particularly when I'm playing a video in VLC (but not always) my pidgin decides to hang. It seems to mainly be affected when a (MSN) contact  goes offline and I try to interact with the chat window or soemthing. 

Anyway, my cpu stutters for a while, and both pidgin and firefox become unresponsive, and firefox just closes. Any suggestions for what's wrong or how to fix it?

Thanks! (Running 9.10 still)

> 

May 14 19:38:13 my-desktop kernel: [3561362.632373] nautilus invoked oom-killer: gfp_mask=0x201da, order=0, oomkilladj=0
May 14 19:38:14 my-desktop kernel: [3561362.632379] nautilus cpuset=/ mems_allowed=0
May 14 19:38:14 my-desktop kernel: [3561362.632384] Pid: 2635, comm: nautilus Tainted: P           2.6.31-20-generic #58-Ubuntu
May 14 19:38:14 my-desktop kernel: [3561362.632387] Call Trace:
May 14 19:38:14 my-desktop kernel: [3561362.632398]  [<c01b5a2f>] oom_kill_process+0x9f/0x250
May 14 19:38:14 my-desktop kernel: [3561362.632403]  [<c01b603e>] ? select_bad_process+0xbe/0xf0
May 14 19:38:14 my-desktop kernel: [3561362.632408]  [<c01b60c1>] __out_of_memory+0x51/0xa0
May 14 19:38:14 my-desktop kernel: [3561362.632413]  [<c01b6163>] out_of_memory+0x53/0xb0
May 14 19:38:14 my-desktop kernel: [3561362.632417]  [<c01b83f6>] __alloc_pages_slowpath+0x3f6/0x490
May 14 19:38:14 my-desktop kernel: [3561362.632423]  [<c01b859f>] __alloc_pages_nodemask+0x10f/0x120
May 14 19:38:14 my-desktop kernel: [3561362.632428]  [<c01bb052>] __do_page_cache_readahead+0xe2/0x190
May 14 19:38:14 my-desktop kernel: [3561362.632433]  [<c01bb121>] ra_submit+0x21/0x30
May 14 19:38:14 my-desktop kernel: [3561362.632437]  [<c01b2940>] do_sync_mmap_readahead+0x90/0xc0
May 14 19:38:14 my-desktop kernel: [3561362.632442]  [<c01b3c6d>] ? find_get_page+0x1d/0x90
May 14 19:38:14 my-desktop kernel: [3561362.632446]  [<c01b4b16>] filemap_fault+0x316/0x340
May 14 19:38:14 my-desktop kernel: [3561362.632466]  [<c01cabeb>] __do_fault+0x3b/0x470
May 14 19:38:14 my-desktop kernel: [3561362.632471]  [<c01cc3e4>] handle_mm_fault+0x134/0x380
May 14 19:38:14 my-desktop kernel: [3561362.632477]  [<c05760f8>] do_page_fault+0x148/0x380
May 14 19:38:14 my-desktop kernel: [3561362.632482]  [<c0575fb0>] ? do_page_fault+0x0/0x380
May 14 19:38:14 my-desktop kernel: [3561362.632486]  [<c0573fe3>] error_code+0x73/0x80
May 14 19:38:14 my-desktop kernel: [3561362.632490] Mem-Info:
May 14 19:38:14 my-desktop kernel: [3561362.632492] DMA per-cpu:
May 14 19:38:14 my-desktop kernel: [3561362.632495] CPU    0: hi:    0, btch:   1 usd:   0
May 14 19:38:14 my-desktop kernel: [3561362.632498] CPU    1: hi:    0, btch:   1 usd:   0
May 14 19:38:14 my-desktop kernel: [3561362.632500] Normal per-cpu:
May 14 19:38:14 my-desktop kernel: [3561362.632502] CPU    0: hi:  186, btch:  31 usd: 142
May 14 19:38:14 my-desktop kernel: [3561362.632505] CPU    1: hi:  186, btch:  31 usd: 169
May 14 19:38:14 my-desktop kernel: [3561362.632508] HighMem per-cpu:
May 14 19:38:14 my-desktop kernel: [3561362.632511] CPU    0: hi:  186, btch:  31 usd:  93
May 14 19:38:14 my-desktop kernel: [3561362.632514] CPU    1: hi:  186, btch:  31 usd: 157
May 14 19:38:14 my-desktop kernel: [3561362.632519] Active_anon:448923 active_file:272 inactive_anon:153736
May 14 19:38:14 my-desktop kernel: [3561362.632520]  inactive_file:257 unevictable:0 dirty:0 writeback:0 unstable:0
May 14 19:38:14 my-desktop kernel: [3561362.632521]  free:18411 slab:9847 mapped:5678 pagetables:2836 bounce:0
May 14 19:38:14 my-desktop kernel: [3561362.632526] DMA free:7788kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB present:15804kB pages_scanned:0 all_unreclaimable? yes
May 14 19:38:14 my-desktop kernel: [3561362.632531] lowmem_reserve[]: 0 865 2777 2777
May 14 19:38:14 my-desktop kernel: [3561362.632540] Normal free:64812kB min:3728kB low:4660kB high:5592kB active_anon:338320kB inactive_anon:129020kB active_file:176kB inactive_file:52kB unevictable:0kB present:885944kB pages_scanned:450 all_unreclaimable? no
May 14 19:38:14 my-desktop kernel: [3561362.632544] lowmem_reserve[]: 0 0 15295 15295
May 14 19:38:14 my-desktop kernel: [3561362.632552] HighMem free:1044kB min:512kB low:2572kB high:4632kB active_anon:1457372kB inactive_anon:485924kB active_file:912kB inactive_file:976kB unevictable:0kB present:1957776kB pages_scanned:32 all_unreclaimable? no
May 14 19:38:14 my-desktop kernel: [3561362.632556] lowmem_reserve[]: 0 0 0 0
May 14 19:38:14 my-desktop kernel: [3561362.632562] DMA: 5*4kB 17*8kB 13*16kB 14*32kB 17*64kB 12*128kB 7*256kB 3*512kB 1*1024kB 0*2048kB 0*4096kB = 7788kB
May 14 19:38:14 my-desktop kernel: [3561362.632576] Normal: 3299*4kB 2910*8kB 800*16kB 394*32kB 36*64kB 5*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 64828kB
May 14 19:38:14 my-desktop kernel: [3561362.632590] HighMem: 261*4kB 0*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1044kB
May 14 19:38:14 my-desktop kernel: [3561362.632604] 16183 total pagecache pages
May 14 19:38:14 my-desktop kernel: [3561362.632606] 0 pages in swap cache
May 14 19:38:14 my-desktop kernel: [3561362.632609] Swap cache stats: add 0, delete 0, find 0/0
May 14 19:38:14 my-desktop kernel: [3561362.632611] Free swap  = 0kB
May 14 19:38:14 my-desktop kernel: [3561362.632613] Total swap = 0kB
May 14 19:38:14 my-desktop kernel: [3561362.640554] 720608 pages RAM
May 14 19:38:14 my-desktop kernel: [3561362.640557] 493298 pages HighMem
May 14 19:38:14 my-desktop kernel: [3561362.640559] 11353 pages reserved
May 14 19:38:14 my-desktop kernel: [3561362.640561] 25851 pages shared
May 14 19:38:14 my-desktop kernel: [3561362.640564] 676435 pages non-shared
May 14 19:38:14 my-desktop kernel: [3561362.640568] Out of memory: kill process 4495 (**firefox**) score 182289 or a child
May 14 19:38:14 my-desktop kernel: [3561362.640622] Killed process 4495 (**firefox**)
May 14 19:38:22 my-desktop kernel: [3561372.767052] **pidgin**[23244]: segfault at 28 ip b4bd2b75 sp bfb8e7a0 error 4 in libmsn.so[b4bae000+43000]


---

### Post by Lucky75 on 2010-05-15
up

---

### Post by Lucky75 on 2010-05-15
up

---

