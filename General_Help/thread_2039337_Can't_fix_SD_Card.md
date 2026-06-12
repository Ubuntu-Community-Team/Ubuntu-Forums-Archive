---
title: "Can't fix SD Card"
date: 2012-08-08
forum: General Help
---

### Post by joelstitch on 2012-08-08
I got a brand new SD Card for my friends Android phone and when he put it in it asked to format the card so he did and since then the phone doesn't want to read it. I tried formatting it on Windows using SDFormatter and it fails, I also did a chkdsk /f and it still has the same problems. I formatted it with GParted fine but when I plug it to the phone it asks to format it again. 

I also tried** sudo fsck -a /dev/sdb1** and this is what it tells me:

```
ubuntu@ubuntu:~$ sudo fsck -a /dev/sdb1
fsck from util-linux-ng 2.17.2
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb1
/dev/sdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

This is a brand new 32GB MicroSD card and I really wish I could get it to work. I would appreciate some help. Thanks in advance.

---

### Post by lukeiamyourfather on 2012-08-08
If formatting it on multiple different operating systems doesn't work I'd say the card might be bad. Flash memory, or any other data storage device for that matter, is not perfect and is prone to failures and faults.

---

### Post by efflandt on 2012-08-08
What asked to format it, the phone or Linux?  If the phone asked to format it, and after that could not read it, it sounds like it may be defective.

If you formatted it in Linux, what file system type did you format it as?  Most flash memory would come formatted as FAT (2 GB or less) or FAT32 (> 2 GB), which most any operating system should be able to read.

What shows up in **dmesg** in Linux when you insert it, and what does **sudo fdisk -l** show for it?

---

### Post by joelstitch on 2012-08-08
> **efflandt said:**
> What asked to format it, the phone or Linux?  If the phone asked to format it, and after that could not read it, it sounds like it may be defective.

If you formatted it in Linux, what file system type did you format it as?  Most flash memory would come formatted as FAT (2 GB or less) or FAT32 (> 2 GB), which most any operating system should be able to read.

What shows up in **dmesg** in Linux when you insert it, and what does **sudo fdisk -l** show for it?

This is what I get from dmesg:

```
[ 1773.758892]  [<f8f431c8>] ath_rx_tasklet+0x1b8/0x540 [ath9k]
[ 1773.758912]  [<f8f40f26>] ath9k_tasklet+0xf6/0x120 [ath9k]
[ 1773.758923]  [<c0151ee7>] tasklet_action+0xa7/0xb0
[ 1773.758930]  [<c01534d8>] __do_softirq+0x98/0x1b0
[ 1773.758939]  [<c0122b7b>] ? ack_apic_level+0x6b/0x170
[ 1773.758947]  [<c016dcae>] ? sched_clock_tick+0x5e/0xa0
[ 1773.758954]  [<c0153635>] do_softirq+0x45/0x50
[ 1773.758960]  [<c0153785>] irq_exit+0x65/0x70
[ 1773.758969]  [<c0592ae5>] do_IRQ+0x55/0xc0
[ 1773.758978]  [<c0176644>] ? tick_broadcast_oneshot_control+0xa4/0x110
[ 1773.758987]  [<c0103a30>] common_interrupt+0x30/0x40
[ 1773.758996]  [<c0129aaa>] ? native_safe_halt+0xa/0x10
[ 1773.759003]  [<c010a840>] default_idle+0x40/0x90
[ 1773.759009]  [<c010a917>] c1e_idle+0x87/0x110
[ 1773.759016]  [<c01021d4>] cpu_idle+0x94/0xd0
[ 1773.759025]  [<c0589825>] start_secondary+0xc4/0xc6
[ 1773.759030] Mem-Info:
[ 1773.759034] DMA per-cpu:
[ 1773.759040] CPU    0: hi:    0, btch:   1 usd:   0
[ 1773.759045] CPU    1: hi:    0, btch:   1 usd:   0
[ 1773.759049] Normal per-cpu:
[ 1773.759054] CPU    0: hi:  186, btch:  31 usd: 156
[ 1773.759060] CPU    1: hi:  186, btch:  31 usd: 195
[ 1773.759064] HighMem per-cpu:
[ 1773.759068] CPU    0: hi:  186, btch:  31 usd:  24
[ 1773.759073] CPU    1: hi:  186, btch:  31 usd:   0
[ 1773.759086] active_anon:31460 inactive_anon:34969 isolated_anon:0
[ 1773.759088]  active_file:55486 inactive_file:291516 isolated_file:39
[ 1773.759091]  unevictable:8 dirty:1150 writeback:0 unstable:0
[ 1773.759094]  free:11228 slab_reclaimable:9717 slab_unreclaimable:4317
[ 1773.759096]  mapped:19762 shmem:1384 pagetables:1435 bounce:0
[ 1773.759112] DMA free:3468kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:4904kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15852kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:104kB slab_unreclaimable:48kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[ 1773.759124] lowmem_reserve[]: 0 865 1757 1757
[ 1773.759144] Normal free:7152kB min:3728kB low:4660kB high:5592kB active_anon:2472kB inactive_anon:9136kB active_file:93284kB inactive_file:668720kB unevictable:0kB isolated(anon):0kB isolated(file):140kB present:885944kB mlocked:0kB dirty:1192kB writeback:0kB mapped:6852kB shmem:904kB slab_reclaimable:38764kB slab_unreclaimable:17220kB kernel_stack:2352kB pagetables:192kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:35 all_unreclaimable? no
[ 1773.759158] lowmem_reserve[]: 0 0 7137 7137
[ 1773.759177] HighMem free:34416kB min:512kB low:1472kB high:2432kB active_anon:123368kB inactive_anon:130740kB active_file:128660kB inactive_file:492300kB unevictable:32kB isolated(anon):0kB isolated(file):0kB present:913644kB mlocked:32kB dirty:3408kB writeback:0kB mapped:72196kB shmem:4632kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:5548kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[ 1773.759190] lowmem_reserve[]: 0 0 0 0
[ 1773.759198] DMA: 1*4kB 1*8kB 0*16kB 0*32kB 0*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3468kB
[ 1773.759220] Normal: 1538*4kB 34*8kB 13*16kB 4*32kB 0*64kB 1*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 7400kB
[ 1773.759242] HighMem: 12*4kB 48*8kB 148*16kB 62*32kB 235*64kB 66*128kB 16*256kB 4*512kB 0*1024kB 0*2048kB 0*4096kB = 34416kB
[ 1773.759264] 348325 total pagecache pages
[ 1773.759267] 0 pages in swap cache
[ 1773.759272] Swap cache stats: add 0, delete 0, find 0/0
[ 1773.759276] Free swap  = 0kB
[ 1773.759279] Total swap = 0kB
[ 1773.762640] 458496 pages RAM
[ 1773.762640] 231170 pages HighMem
[ 1773.762640] 9003 pages reserved
[ 1773.762640] 313058 pages shared
[ 1773.762640] 201413 pages non-shared
[ 1773.762640] SLUB: Unable to allocate memory on node -1 (gfp=0x20)
[ 1773.762640]   cache: kmalloc-8192, object size: 8192, buffer size: 8192, default order: 3, min order: 1
[ 1773.762640]   node 0: slabs: 146, objs: 572, free: 0
[ 1773.772104] skbuff alloc of size 3904 failed
[ 1774.553252] swapper: page allocation failure. order:1, mode:0x4020
[ 1774.553265] Pid: 0, comm: swapper Not tainted 2.6.32-28-generic #55-Ubuntu
[ 1774.553271] Call Trace:
[ 1774.553286]  [<c058bf3e>] ? printk+0x1d/0x1f
[ 1774.553300]  [<c01d0c6b>] __alloc_pages_slowpath+0x3ab/0x4a0
[ 1774.553310]  [<c016d9c5>] ? sched_clock_local+0xa5/0x180
[ 1774.553319]  [<c01d0e9a>] __alloc_pages_nodemask+0x13a/0x170
[ 1774.553327]  [<c01fce62>] new_slab+0x1a2/0x200
[ 1774.553335]  [<c01fe625>] __slab_alloc+0x1a5/0x220
[ 1774.553343]  [<c01ff67d>] __kmalloc_track_caller+0xcd/0x170
[ 1774.553359]  [<f814702f>] ? ath_rxbuf_alloc+0x2f/0xa0 [ath]
[ 1774.553369]  [<f814702f>] ? ath_rxbuf_alloc+0x2f/0xa0 [ath]
[ 1774.553378]  [<c04bc2a2>] __alloc_skb+0x52/0x130
[ 1774.553387]  [<f814702f>] ath_rxbuf_alloc+0x2f/0xa0 [ath]
[ 1774.553410]  [<f8f431c8>] ath_rx_tasklet+0x1b8/0x540 [ath9k]
[ 1774.553431]  [<f8f40f26>] ath9k_tasklet+0xf6/0x120 [ath9k]
[ 1774.553440]  [<c0151ee7>] tasklet_action+0xa7/0xb0
[ 1774.553448]  [<c01534d8>] __do_softirq+0x98/0x1b0
[ 1774.553457]  [<c0122b7b>] ? ack_apic_level+0x6b/0x170
[ 1774.553464]  [<c016dcae>] ? sched_clock_tick+0x5e/0xa0
[ 1774.553471]  [<c0153635>] do_softirq+0x45/0x50
[ 1774.553478]  [<c0153785>] irq_exit+0x65/0x70
[ 1774.553486]  [<c0592ae5>] do_IRQ+0x55/0xc0
[ 1774.553495]  [<c0176644>] ? tick_broadcast_oneshot_control+0xa4/0x110
[ 1774.553504]  [<c0103a30>] common_interrupt+0x30/0x40
[ 1774.553513]  [<c0129aaa>] ? native_safe_halt+0xa/0x10
[ 1774.553520]  [<c010a840>] default_idle+0x40/0x90
[ 1774.553527]  [<c010a917>] c1e_idle+0x87/0x110
[ 1774.553534]  [<c01021d4>] cpu_idle+0x94/0xd0
[ 1774.553543]  [<c0589825>] start_secondary+0xc4/0xc6
[ 1774.553549] Mem-Info:
[ 1774.553553] DMA per-cpu:
[ 1774.553558] CPU    0: hi:    0, btch:   1 usd:   0
[ 1774.553564] CPU    1: hi:    0, btch:   1 usd:   0
[ 1774.553568] Normal per-cpu:
[ 1774.553573] CPU    0: hi:  186, btch:  31 usd: 157
[ 1774.553579] CPU    1: hi:  186, btch:  31 usd: 107
[ 1774.553583] HighMem per-cpu:
[ 1774.553587] CPU    0: hi:  186, btch:  31 usd:   0
[ 1774.553592] CPU    1: hi:  186, btch:  31 usd:   0
[ 1774.553604] active_anon:31462 inactive_anon:34969 isolated_anon:0
[ 1774.553607]  active_file:55498 inactive_file:290993 isolated_file:32
[ 1774.553610]  unevictable:8 dirty:1162 writeback:0 unstable:0
[ 1774.553612]  free:11827 slab_reclaimable:9718 slab_unreclaimable:4333
[ 1774.553615]  mapped:19762 shmem:1384 pagetables:1435 bounce:0
[ 1774.553631] DMA free:3468kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:4904kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15852kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:104kB slab_unreclaimable:48kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[ 1774.553643] lowmem_reserve[]: 0 865 1757 1757
[ 1774.553663] Normal free:9476kB min:3728kB low:4660kB high:5592kB active_anon:2472kB inactive_anon:9136kB active_file:93320kB inactive_file:666612kB unevictable:0kB isolated(anon):0kB isolated(file):128kB present:885944kB mlocked:0kB dirty:1192kB writeback:0kB mapped:6852kB shmem:904kB slab_reclaimable:38768kB slab_unreclaimable:17284kB kernel_stack:2352kB pagetables:192kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[ 1774.553676] lowmem_reserve[]: 0 0 7137 7137
[ 1774.553695] HighMem free:34488kB min:512kB low:1472kB high:2432kB active_anon:123376kB inactive_anon:130740kB active_file:128672kB inactive_file:492328kB unevictable:32kB isolated(anon):0kB isolated(file):0kB present:913644kB mlocked:32kB dirty:3456kB writeback:0kB mapped:72196kB shmem:4632kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:5548kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[ 1774.553708] lowmem_reserve[]: 0 0 0 0
[ 1774.553717] DMA: 1*4kB 1*8kB 0*16kB 0*32kB 0*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3468kB
[ 1774.553739] Normal: 2087*4kB 20*8kB 18*16kB 10*32kB 1*64kB 0*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 9692kB
[ 1774.553760] HighMem: 16*4kB 55*8kB 148*16kB 62*32kB 235*64kB 66*128kB 16*256kB 4*512kB 0*1024kB 0*2048kB 0*4096kB = 34488kB
[ 1774.553782] 347783 total pagecache pages
[ 1774.553786] 0 pages in swap cache
[ 1774.553790] Swap cache stats: add 0, delete 0, find 0/0
[ 1774.553795] Free swap  = 0kB
[ 1774.553798] Total swap = 0kB
[ 1774.557152] 458496 pages RAM
[ 1774.557152] 231170 pages HighMem
[ 1774.557152] 9003 pages reserved
[ 1774.557152] 312652 pages shared
[ 1774.557152] 201447 pages non-shared
[ 1774.557152] SLUB: Unable to allocate memory on node -1 (gfp=0x20)
[ 1774.557152]   cache: kmalloc-8192, object size: 8192, buffer size: 8192, default order: 3, min order: 1
[ 1774.557152]   node 0: slabs: 150, objs: 588, free: 0
[ 1774.566625] skbuff alloc of size 3904 failed
[ 1775.271437] swapper: page allocation failure. order:1, mode:0x4020
[ 1775.271449] Pid: 0, comm: swapper Not tainted 2.6.32-28-generic #55-Ubuntu
[ 1775.271455] Call Trace:
[ 1775.271470]  [<c058bf3e>] ? printk+0x1d/0x1f
[ 1775.271483]  [<c01d0c6b>] __alloc_pages_slowpath+0x3ab/0x4a0
[ 1775.271494]  [<c01d0e9a>] __alloc_pages_nodemask+0x13a/0x170
[ 1775.271503]  [<c01fce62>] new_slab+0x1a2/0x200
[ 1775.271510]  [<c01fe625>] __slab_alloc+0x1a5/0x220
[ 1775.271518]  [<c01ff67d>] __kmalloc_track_caller+0xcd/0x170
[ 1775.271535]  [<f814702f>] ? ath_rxbuf_alloc+0x2f/0xa0 [ath]
[ 1775.271544]  [<f814702f>] ? ath_rxbuf_alloc+0x2f/0xa0 [ath]
[ 1775.271553]  [<c04bc2a2>] __alloc_skb+0x52/0x130
[ 1775.271562]  [<f814702f>] ath_rxbuf_alloc+0x2f/0xa0 [ath]
[ 1775.271585]  [<f8f431c8>] ath_rx_tasklet+0x1b8/0x540 [ath9k]
[ 1775.271606]  [<f8f40f26>] ath9k_tasklet+0xf6/0x120 [ath9k]
[ 1775.271616]  [<c0151ee7>] tasklet_action+0xa7/0xb0
[ 1775.271623]  [<c01534d8>] __do_softirq+0x98/0x1b0
[ 1775.271632]  [<c0122b7b>] ? ack_apic_level+0x6b/0x170
[ 1775.271640]  [<c016dcae>] ? sched_clock_tick+0x5e/0xa0
[ 1775.271647]  [<c0153635>] do_softirq+0x45/0x50
[ 1775.271653]  [<c0153785>] irq_exit+0x65/0x70
[ 1775.271662]  [<c0592ae5>] do_IRQ+0x55/0xc0
[ 1775.271671]  [<c0176644>] ? tick_broadcast_oneshot_control+0xa4/0x110
[ 1775.271680]  [<c0103a30>] common_interrupt+0x30/0x40
[ 1775.271689]  [<c0129aaa>] ? native_safe_halt+0xa/0x10
[ 1775.271696]  [<c010a840>] default_idle+0x40/0x90
[ 1775.271703]  [<c010a917>] c1e_idle+0x87/0x110
[ 1775.271709]  [<c01021d4>] cpu_idle+0x94/0xd0
[ 1775.271718]  [<c0589825>] start_secondary+0xc4/0xc6
[ 1775.271724] Mem-Info:
[ 1775.271728] DMA per-cpu:
[ 1775.271733] CPU    0: hi:    0, btch:   1 usd:   0
[ 1775.271739] CPU    1: hi:    0, btch:   1 usd:   0
[ 1775.271743] Normal per-cpu:
[ 1775.271748] CPU    0: hi:  186, btch:  31 usd:  13
[ 1775.271753] CPU    1: hi:  186, btch:  31 usd:   7
[ 1775.271757] HighMem per-cpu:
[ 1775.271762] CPU    0: hi:  186, btch:  31 usd:   0
[ 1775.271766] CPU    1: hi:  186, btch:  31 usd:   0
[ 1775.271778] active_anon:31463 inactive_anon:34969 isolated_anon:0
[ 1775.271781]  active_file:55504 inactive_file:291959 isolated_file:0
[ 1775.271784]  unevictable:8 dirty:1167 writeback:0 unstable:0
[ 1775.271786]  free:11087 slab_reclaimable:9720 slab_unreclaimable:4365
[ 1775.271789]  mapped:19762 shmem:1384 pagetables:1435 bounce:0
[ 1775.271804] DMA free:3468kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:4904kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15852kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:104kB slab_unreclaimable:48kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[ 1775.271817] lowmem_reserve[]: 0 865 1757 1757
[ 1775.271837] Normal free:6412kB min:3728kB low:4660kB high:5592kB active_anon:2472kB inactive_anon:9136kB active_file:93332kB inactive_file:670596kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:1192kB writeback:0kB mapped:6852kB shmem:904kB slab_reclaimable:38776kB slab_unreclaimable:17412kB kernel_stack:2352kB pagetables:192kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[ 1775.271850] lowmem_reserve[]: 0 0 7137 7137
[ 1775.271869] HighMem free:34468kB min:512kB low:1472kB high:2432kB active_anon:123380kB inactive_anon:130740kB active_file:128684kB inactive_file:492336kB unevictable:32kB isolated(anon):0kB isolated(file):0kB present:913644kB mlocked:32kB dirty:3476kB writeback:0kB mapped:72196kB shmem:4632kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:5548kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[ 1775.271881] lowmem_reserve[]: 0 0 0 0
[ 1775.271889] DMA: 1*4kB 1*8kB 0*16kB 0*32kB 0*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3468kB
[ 1775.271911] Normal: 1451*4kB 0*8kB 0*16kB 1*32kB 1*64kB 0*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 6412kB
[ 1775.271932] HighMem: 13*4kB 54*8kB 148*16kB 62*32kB 235*64kB 66*128kB 16*256kB 4*512kB 0*1024kB 0*2048kB 0*4096kB = 34468kB
[ 1775.271954] 348854 total pagecache pages
[ 1775.271957] 0 pages in swap cache
[ 1775.271962] Swap cache stats: add 0, delete 0, find 0/0
[ 1775.271966] Free swap  = 0kB
[ 1775.271969] Total swap = 0kB
[ 1775.275367] 458496 pages RAM
[ 1775.275367] 231170 pages HighMem
[ 1775.275367] 9003 pages reserved
[ 1775.275367] 314111 pages shared
[ 1775.275367] 201464 pages non-shared
[ 1775.275367] SLUB: Unable to allocate memory on node -1 (gfp=0x20)
[ 1775.275367]   cache: kmalloc-8192, object size: 8192, buffer size: 8192, default order: 3, min order: 1
[ 1775.275367]   node 0: slabs: 152, objs: 596, free: 0
[ 1775.284876] skbuff alloc of size 3904 failed
[ 2131.148975] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
[ 2378.628822] aufs au_plink_append:280:dpkg[14982]: unexpectedly many pseudo links, 101
[ 2396.405957] aufs au_plink_append:280:dpkg[15704]: unexpectedly many pseudo links, 357
[ 2397.242860] aufs au_plink_append:280:dpkg[15704]: unexpectedly many pseudo links, 613
[ 2408.927960] aufs au_plink_append:280:dpkg[15800]: unexpectedly many pseudo links, 869
[ 2427.301012] aufs au_plink_append:280:dpkg[15934]: unexpectedly many pseudo links, 1125
[ 2429.402460] aufs au_plink_append:280:dpkg[15934]: unexpectedly many pseudo links, 1381
[ 2433.139166] aufs au_plink_append:280:dpkg[15934]: unexpectedly many pseudo links, 1637
[ 2434.048381] aufs au_plink_append:280:dpkg[15934]: unexpectedly many pseudo links, 1893
[ 2435.139423] aufs au_plink_append:280:dpkg[15934]: unexpectedly many pseudo links, 2149
[ 2437.470672] aufs au_plink_append:280:dpkg[15934]: unexpectedly many pseudo links, 2405
[ 2437.858695] aufs au_plink_append:280:dpkg[15934]: unexpectedly many pseudo links, 2661
[ 2438.312938] aufs au_plink_append:280:dpkg[15934]: unexpectedly many pseudo links, 2917
[ 2438.867901] aufs au_plink_append:280:dpkg[15934]: unexpectedly many pseudo links, 3173
[ 2439.338402] aufs au_plink_append:280:dpkg[15934]: unexpectedly many pseudo links, 3429
[ 2449.532801] aufs au_plink_append:280:dpkg[16030]: unexpectedly many pseudo links, 3685
[ 2450.235605] aufs au_plink_append:280:dpkg[16030]: unexpectedly many pseudo links, 3941
[ 2451.255965] aufs au_plink_append:280:dpkg[16030]: unexpectedly many pseudo links, 4197
[ 2456.336885] aufs au_plink_append:280:dpkg[16030]: unexpectedly many pseudo links, 4453
[ 2456.830824] aufs au_plink_append:280:dpkg[16030]: unexpectedly many pseudo links, 4709
[ 2482.333520] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 4965
[ 2485.824694] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 5221
[ 2494.939068] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 5477
[ 2496.018919] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 5733
[ 2496.317645] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 5989
[ 2496.647524] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 6245
[ 2503.109019] ath9k: Failed to stop TX DMA in 100 msec after killing last frame
[ 2503.118695] ath9k: Failed to stop TX DMA in 100 msec after killing last frame
[ 2503.118716] ath9k: Unable to stop TxDMA. Reset HAL!
[ 2503.962063] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 6501
[ 2508.326550] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 6757
[ 2509.251744] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 7013
[ 2517.963393] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 7269
[ 2523.670897] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 7525
[ 2526.171688] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 7781
[ 2528.741671] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 8037
[ 2536.023091] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 8293
[ 2536.885019] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 8549
[ 2538.456170] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 8805
[ 2539.742898] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 9061
[ 2548.759145] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 9317
[ 2550.669610] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 9573
[ 2552.486676] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 9829
[ 2559.944803] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 10085
[ 2565.403674] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 10341
[ 2568.513189] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 10597
[ 2570.697219] aufs au_plink_append:280:dpkg[16505]: unexpectedly many pseudo links, 10853
[ 2608.071554] aufs au_plink_append:280:dpkg[17565]: unexpectedly many pseudo links, 11109
[ 2622.252561] aufs au_plink_append:280:dpkg[17819]: unexpectedly many pseudo links, 11365
[ 2645.003670] aufs au_plink_append:280:dpkg[18178]: unexpectedly many pseudo links, 11621
[ 2659.961711] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 11877
[ 2665.485610] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 12133
[ 2667.291172] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 12389
[ 2682.348599] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 12645
[ 2692.669270] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 12901
[ 2706.578946] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 13157
[ 2718.377711] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 13413
[ 2730.267971] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 13669
[ 2737.985237] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 13925
[ 2744.320979] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 14181
[ 2760.216209] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 14437
[ 2763.991949] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 14693
[ 2768.241075] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 14949
[ 2783.187165] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 15205
[ 2784.143191] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 15461
[ 2794.483531] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 15717
[ 2795.780789] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 15973
[ 2818.539629] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 16229
[ 2819.267367] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 16485
[ 2827.635203] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 16741
[ 2835.081555] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 16997
[ 2840.427333] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 17253
[ 2854.881956] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 17509
[ 2877.279013] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 17765
[ 2891.566751] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 18021
[ 2912.853958] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 18277
[ 2918.785278] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 18533
[ 2925.115621] usb 2-2: USB disconnect, address 22
[ 2925.564165] usb 2-2: new high speed USB device using ehci_hcd and address 23
[ 2925.766644] usb 2-2: configuration #1 chosen from 1 choice
[ 2925.767098] scsi8 : SCSI emulation for USB Mass Storage devices
[ 2925.767346] usb-storage: device found at 23
[ 2925.767351] usb-storage: waiting for device to settle before scanning
[ 2930.764804] usb-storage: device scan complete
[ 2930.765319] scsi 8:0:0:0: Direct-Access     WD       My Book 3.0 1123 1006 PQ: 0 ANSI: 4
[ 2930.767141] sd 8:0:0:0: Attached scsi generic sg3 type 0
[ 2930.778774] sd 8:0:0:0: [sdd] 1953519616 512-byte logical blocks: (1.00 TB/931 GiB)
[ 2930.779642] sd 8:0:0:0: [sdd] Write Protect is off
[ 2930.779645] sd 8:0:0:0: [sdd] Mode Sense: 0a 00 10 00
[ 2930.779648] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[ 2930.781411] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[ 2930.781425]  sdd: sdd1
[ 2930.787008] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[ 2930.787021] sd 8:0:0:0: [sdd] Attached SCSI disk
[ 2937.622503] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 18789
[ 2949.264585] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 19045
[ 2950.019791] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 19301
[ 2951.105140] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 19557
[ 2952.138476] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 19813
[ 2952.946591] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 20069
[ 2953.724060] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 20325
[ 2955.463263] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 20581
[ 2957.089344] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 20837
[ 2958.038428] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 21093
[ 2980.498479] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 21349
[ 3005.174959] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 21605
[ 3011.134402] usb 2-2: USB disconnect, address 23
[ 3011.261935] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 21861
[ 3012.588193] usb 2-2: new high speed USB device using ehci_hcd and address 24
[ 3013.386553] usb 2-2: configuration #1 chosen from 1 choice
[ 3013.387094] scsi9 : SCSI emulation for USB Mass Storage devices
[ 3013.387427] usb-storage: device found at 24
[ 3013.387432] usb-storage: waiting for device to settle before scanning
[ 3018.986613] usb-storage: device scan complete
[ 3018.987220] scsi 9:0:0:0: Direct-Access     WD       My Book 3.0 1123 1006 PQ: 0 ANSI: 4
[ 3018.990603] sd 9:0:0:0: Attached scsi generic sg3 type 0
[ 3018.998575] sd 9:0:0:0: [sdd] 1953519616 512-byte logical blocks: (1.00 TB/931 GiB)
[ 3018.999571] sd 9:0:0:0: [sdd] Write Protect is off
[ 3018.999583] sd 9:0:0:0: [sdd] Mode Sense: 0a 00 10 00
[ 3018.999590] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[ 3019.002444] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[ 3019.002457]  sdd: sdd1
[ 3019.011300] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[ 3019.011313] sd 9:0:0:0: [sdd] Attached SCSI disk
[ 3019.239601] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 22117
[ 3034.456212] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 22373
[ 3035.460775] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 22629
[ 3041.251784] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 22885
[ 3042.012084] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 23141
[ 3050.017812] aufs au_plink_append:280:dpkg[19118]: unexpectedly many pseudo links, 23397
[ 3211.154159] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
[ 3228.934095] CPU0 attaching NULL sched-domain.
[ 3228.934102] CPU1 attaching NULL sched-domain.
[ 3228.956173] CPU0 attaching sched-domain:
[ 3228.956183]  domain 0: span 0-1 level MC
[ 3228.956190]   groups: 0 1
[ 3228.956203] CPU1 attaching sched-domain:
[ 3228.956208]  domain 0: span 0-1 level MC
[ 3228.956214]   groups: 1 0
[ 3241.314986] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04771/0xe40000
[ 3241.314993] Synaptics: Clickpad mode enabled
[ 3241.398032] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
[ 4240.098587] usb 2-2: USB disconnect, address 24
[ 4241.828246] usb 5-2: new full speed USB device using ohci_hcd and address 3
[ 4241.968243] usb 5-2: device descriptor read/64, error -62
[ 4242.212098] usb 5-2: device descriptor read/64, error -62
[ 4242.452246] usb 5-2: new full speed USB device using ohci_hcd and address 4
[ 4242.592246] usb 5-2: device descriptor read/64, error -62
[ 4242.836244] usb 5-2: device descriptor read/64, error -62
[ 4243.076266] usb 5-2: new full speed USB device using ohci_hcd and address 5
[ 4243.484167] usb 5-2: device not accepting address 5, error -62
[ 4243.620183] usb 5-2: new full speed USB device using ohci_hcd and address 6
[ 4244.028216] usb 5-2: device not accepting address 6, error -62
[ 4244.028246] hub 5-0:1.0: unable to enumerate USB device on port 2
[ 4279.365917] ath9k: Failed to stop TX DMA in 100 msec after killing last frame
[ 4279.374766] ath9k: Failed to stop TX DMA in 100 msec after killing last frame
[ 4279.374788] ath9k: Unable to stop TxDMA. Reset HAL!
[ 4329.028436] sd 3:0:0:0: [sdb] 64227328 512-byte logical blocks: (32.8 GB/30.6 GiB)
[ 4329.029420] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 4329.031162] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 4329.031176]  sdb: sdb1 sdb2 sdb3 sdb4
[ 4329.032704] sdb: p2 size 1149239296 exceeds device capacity, limited to end of disk
[ 4329.032859] sdb: p4 ignored, start 537133057 is behind the end of the disk
ubuntu@ubuntu:~$ 

```

And this from **sudo fdisk -l**:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 30.0 GB, 30005821440 bytes
64 heads, 32 sectors/track, 28615 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00060fe8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28615    29301744    c  W95 FAT32 (LBA)

Disk /dev/sdb: 32.9 GB, 32884391936 bytes
239 heads, 63 sectors/track, 4265 cylinders
Units = cylinders of 15057 * 512 = 7709184 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         558        4265    27911559    3  XENIX usr
/dev/sdb2               1       76327   574619648    0  Empty
Partition 2 does not end on cylinder boundary.
/dev/sdb3               1           9       65536    0  Empty
Partition 3 does not end on cylinder boundary.
/dev/sdb4           35674       35674          80    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb3: 67 MB, 67108864 bytes
239 heads, 63 sectors/track, 8 cylinders
Units = cylinders of 15057 * 512 = 7709184 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02000000

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb3p1   *         558        4265    27911559    3  XENIX usr
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 129, 21) logical=(557, 32, 33)
Partition 1 has different physical/logical endings:
     phys=(1023, 238, 63) logical=(4264, 140, 47)
/dev/sdb3p2               1       76327   574619648    0  Empty
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(0, 32, 33)
Partition 2 has different physical/logical endings:
     phys=(0, 4, 0) logical=(76326, 12, 6)
Partition 2 does not end on cylinder boundary.
/dev/sdb3p3               1           9       65536    0  Empty
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(64, 0, 0) logical=(0, 0, 1)
Partition 3 has different physical/logical endings:
     phys=(16, 0, 0) logical=(8, 168, 32)
Partition 3 does not end on cylinder boundary.
/dev/sdb3p4           35674       35674          80    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(4, 0, 0) logical=(35673, 74, 35)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(35673, 77, 5)
Partition 4 does not end on cylinder boundary.
ubuntu@ubuntu:~$ 

```

The MicroSD card is **/dev/sdb1**

---

### Post by ajgreeny on 2012-08-08
Is the partition table corrupt?

It could be worth trying again with gparted, but this time go to **Device ->Create Partition Table.**  Choose the msdos option which is the default, and when that has finished (if it works), make a new fat32 partition in the unallocated space which will now be all that is showing..

---

### Post by joelstitch on 2012-08-08
I did that but Now I'm getting the error "unrecognized disk label". Its probably screwed.

---

### Post by ajgreeny on 2012-08-08
> **joelstitch said:**
> I did that but Now I'm getting the error "unrecognized disk label". Its probably screwed.
Where are you getting that error?

You could try giving the partition a new label in gparted to see if that helps.  Just make sure you use a simple alphanumeric label with no strange characters.

However, it does sound as if the flash card is dead.

---

