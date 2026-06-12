---
title: "ubuntu server disappears from network, hard reboot required"
date: 2010-11-15
forum: General Help
---

### Post by talz13 on 2010-11-15
I've been having issues with my ubuntu server (10.04 LTS) lately.  Every once in a while, anywhere from 3 days to a month or more, the server will just disappear from the network.  All manner of trying to reach it from the outside fails, even from the LAN.  Since it's headless, this is kind of problematic.  After a hard power down or reboot, the server will always come back online, but this is very annoying for a remotely administered server.

What should I look for when trying to determine why the server keeps going offline?  I can't tell if there are any other issues like a hard lockup or anything, just that it is not on the network anymore when this happens.

---

### Post by TSJason on 2010-11-15
Have you checked the logs to see if there are any error messages? The /var/log/messages or /var/log/syslog would be a good place to start.

---

### Post by sikander3786 on 2010-11-15
What type of servers is it running on it?

I wonder if it has got more than 1 HDDs and the non-Ubuntu HDD goes to sleep when un-used for a longer period of time. And thus, the shares don't show up on the network.

---

### Post by talz13 on 2010-11-15
Well this looks great:```
Nov 14 06:55:41 server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1056" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Nov 14 20:52:44 server kernel: [196697.916273] swapper: page allocation failure. order:0, mode:0x4020
Nov 14 20:52:44 server kernel: [196697.916279] Pid: 0, comm: swapper Not tainted 2.6.32-25-server #45-Ubuntu
Nov 14 20:52:44 server kernel: [196697.916282] Call Trace:
Nov 14 20:52:44 server kernel: [196697.916285]  <IRQ>  [<ffffffff810f9a2e>] __alloc_pages_slowpath+0x56e/0x580
Nov 14 20:52:44 server kernel: [196697.916298]  [<ffffffff810f9bb1>] __alloc_pages_nodemask+0x171/0x180
Nov 14 20:52:44 server kernel: [196697.916304]  [<ffffffff8112cae7>] alloc_pages_current+0x87/0xd0
Nov 14 20:52:44 server kernel: [196697.916309]  [<ffffffff81132b27>] new_slab+0x2f7/0x310
Nov 14 20:52:44 server kernel: [196697.916313]  [<ffffffff811353d1>] __slab_alloc+0x201/0x2d0
Nov 14 20:52:44 server kernel: [196697.916318]  [<ffffffff81468de6>] ? __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196697.916323]  [<ffffffff811363af>] __kmalloc_node_track_caller+0xaf/0x160
Nov 14 20:52:44 server kernel: [196697.916327]  [<ffffffff81468de6>] ? __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196697.916330]  [<ffffffff81468aa0>] __alloc_skb+0x80/0x190
Nov 14 20:52:44 server kernel: [196697.916334]  [<ffffffff81468de6>] __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196697.916351]  [<ffffffffa000b5c7>] rtl8169_rx_interrupt+0x247/0x5b0 [r8169]
Nov 14 20:52:44 server kernel: [196697.916357]  [<ffffffffa000baad>] rtl8169_poll+0x3d/0x270 [r8169]
Nov 14 20:52:44 server kernel: [196697.916363]  [<ffffffff810387b9>] ? default_spin_lock_flags+0x9/0x10
Nov 14 20:52:44 server kernel: [196697.916368]  [<ffffffff8147300f>] net_rx_action+0x10f/0x250
Nov 14 20:52:44 server kernel: [196697.916375]  [<ffffffffa000954e>] ? rtl8169_interrupt+0xde/0x1e0 [r8169]
Nov 14 20:52:44 server kernel: [196697.916379]  [<ffffffff8106d477>] __do_softirq+0xb7/0x1e0
Nov 14 20:52:44 server kernel: [196697.916384]  [<ffffffff810c4030>] ? handle_IRQ_event+0x60/0x170
Nov 14 20:52:44 server kernel: [196697.916388]  [<ffffffff810132ec>] call_softirq+0x1c/0x30
Nov 14 20:52:44 server kernel: [196697.916392]  [<ffffffff81014cb5>] do_softirq+0x65/0xa0
Nov 14 20:52:44 server kernel: [196697.916396]  [<ffffffff8106d315>] irq_exit+0x85/0x90
Nov 14 20:52:44 server kernel: [196697.916401]  [<ffffffff8155f2a5>] do_IRQ+0x75/0xf0
Nov 14 20:52:44 server kernel: [196697.916404]  [<ffffffff81012b13>] ret_from_intr+0x0/0x11
Nov 14 20:52:44 server kernel: [196697.916407]  <EOI>  [<ffffffff81037adb>] ? native_safe_halt+0xb/0x10
Nov 14 20:52:44 server kernel: [196697.916415]  [<ffffffff8108e6c6>] ? ktime_get_real+0x16/0x50
Nov 14 20:52:44 server kernel: [196697.916421]  [<ffffffff8130e24f>] ? acpi_idle_do_entry+0x3e/0x67
Nov 14 20:52:44 server kernel: [196697.916425]  [<ffffffff8130e2ea>] ? acpi_idle_enter_c1+0x72/0xc1
Nov 14 20:52:44 server kernel: [196697.916429]  [<ffffffff8155ce86>] ? notifier_call_chain+0x16/0x80
Nov 14 20:52:44 server kernel: [196697.916435]  [<ffffffff8144e42d>] ? menu_select+0x10d/0x2a0
Nov 14 20:52:44 server kernel: [196697.916439]  [<ffffffff8144d367>] ? cpuidle_idle_call+0xa7/0x140
Nov 14 20:52:44 server kernel: [196697.916444]  [<ffffffff81010e63>] ? cpu_idle+0xb3/0x110
Nov 14 20:52:44 server kernel: [196697.916448]  [<ffffffff81551fab>] ? start_secondary+0xa8/0xaa
Nov 14 20:52:44 server kernel: [196697.916451] Mem-Info:
Nov 14 20:52:44 server kernel: [196697.916453] Node 0 DMA per-cpu:
Nov 14 20:52:44 server kernel: [196697.916457] CPU    0: hi:    0, btch:   1 usd:   0
Nov 14 20:52:44 server kernel: [196697.916459] CPU    1: hi:    0, btch:   1 usd:   0
Nov 14 20:52:44 server kernel: [196697.916462] Node 0 DMA32 per-cpu:
Nov 14 20:52:44 server kernel: [196697.916465] CPU    0: hi:  186, btch:  31 usd: 171
Nov 14 20:52:44 server kernel: [196697.916468] CPU    1: hi:  186, btch:  31 usd:  60
Nov 14 20:52:44 server kernel: [196697.916470] Node 0 Normal per-cpu:
Nov 14 20:52:44 server kernel: [196697.916473] CPU    0: hi:  186, btch:  31 usd: 146
Nov 14 20:52:44 server kernel: [196697.916476] CPU    1: hi:  186, btch:  31 usd: 117
Nov 14 20:52:44 server kernel: [196697.916481] active_anon:98612 inactive_anon:67367 isolated_anon:0
Nov 14 20:52:44 server kernel: [196697.916483]  active_file:61118 inactive_file:693132 isolated_file:0
Nov 14 20:52:44 server kernel: [196697.916484]  unevictable:0 dirty:35512 writeback:0 unstable:0
Nov 14 20:52:44 server kernel: [196697.916485]  free:5706 slab_reclaimable:37466 slab_unreclaimable:7139
Nov 14 20:52:44 server kernel: [196697.916487]  mapped:11697 shmem:2001 pagetables:2401 bounce:0
Nov 14 20:52:44 server kernel: [196697.916490] Node 0 DMA free:15908kB min:28kB low:32kB high:40kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15340kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Nov 14 20:52:44 server kernel: [196697.916501] lowmem_reserve[]: 0 2965 3975 3975
Nov 14 20:52:44 server kernel: [196697.916507] Node 0 DMA32 free:6256kB min:6004kB low:7504kB high:9004kB active_anon:192324kB inactive_anon:62168kB active_file:59336kB inactive_file:2486792kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:3036256kB mlocked:0kB dirty:141196kB writeback:0kB mapped:668kB shmem:380kB slab_reclaimable:134556kB slab_unreclaimable:15460kB kernel_stack:72kB pagetables:1080kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Nov 14 20:52:44 server kernel: [196697.916520] lowmem_reserve[]: 0 0 1010 1010
Nov 14 20:52:44 server kernel: [196697.916524] Node 0 Normal free:660kB min:2044kB low:2552kB high:3064kB active_anon:202124kB inactive_anon:207300kB active_file:185136kB inactive_file:285736kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:1034240kB mlocked:0kB dirty:852kB writeback:0kB mapped:46120kB shmem:7624kB slab_reclaimable:15308kB slab_unreclaimable:13096kB kernel_stack:2704kB pagetables:8524kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:32 all_unreclaimable? no
Nov 14 20:52:44 server kernel: [196697.916537] lowmem_reserve[]: 0 0 0 0
Nov 14 20:52:44 server kernel: [196697.916542] Node 0 DMA: 3*4kB 3*8kB 2*16kB 3*32kB 2*64kB 0*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 3*4096kB = 15908kB
Nov 14 20:52:44 server kernel: [196697.916555] Node 0 DMA32: 1286*4kB 1*8kB 3*16kB 0*32kB 0*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 6352kB
Nov 14 20:52:44 server kernel: [196697.916567] Node 0 Normal: 165*4kB 0*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 660kB
Nov 14 20:52:44 server kernel: [196697.916579] 756371 total pagecache pages
Nov 14 20:52:44 server kernel: [196697.916581] 116 pages in swap cache
Nov 14 20:52:44 server kernel: [196697.916583] Swap cache stats: add 1220, delete 1104, find 1308/1322
Nov 14 20:52:44 server kernel: [196697.916586] Free swap  = 15618740kB
Nov 14 20:52:44 server kernel: [196697.916588] Total swap = 15623172kB
Nov 14 20:52:44 server kernel: [196697.926264] 1048576 pages RAM
Nov 14 20:52:44 server kernel: [196697.926264] 42584 pages reserved
Nov 14 20:52:44 server kernel: [196697.926264] 751338 pages shared
Nov 14 20:52:44 server kernel: [196697.926264] 271093 pages non-shared
Nov 14 20:52:44 server kernel: [196697.926264] SLUB: Unable to allocate memory on node -1 (gfp=0x20)
Nov 14 20:52:44 server kernel: [196697.926264]   cache: kmalloc-4096, object size: 4096, buffer size: 4096, default order: 3, min order: 0
Nov 14 20:52:44 server kernel: [196697.926264]   node 0: slabs: 680, objs: 1471, free: 0
Nov 14 20:52:44 server kernel: [196697.934142] swapper: page allocation failure. order:0, mode:0x4020
Nov 14 20:52:44 server kernel: [196697.934147] Pid: 0, comm: swapper Not tainted 2.6.32-25-server #45-Ubuntu
Nov 14 20:52:44 server kernel: [196697.934149] Call Trace:
Nov 14 20:52:44 server kernel: [196697.934151]  <IRQ>  [<ffffffff810f9a2e>] __alloc_pages_slowpath+0x56e/0x580
Nov 14 20:52:44 server kernel: [196697.934164]  [<ffffffff810f9bb1>] __alloc_pages_nodemask+0x171/0x180
Nov 14 20:52:44 server kernel: [196697.934170]  [<ffffffff8112cae7>] alloc_pages_current+0x87/0xd0
Nov 14 20:52:44 server kernel: [196697.934174]  [<ffffffff81132b27>] new_slab+0x2f7/0x310
Nov 14 20:52:44 server kernel: [196697.934178]  [<ffffffff811353d1>] __slab_alloc+0x201/0x2d0
Nov 14 20:52:44 server kernel: [196697.934184]  [<ffffffff81468de6>] ? __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196697.934188]  [<ffffffff811363af>] __kmalloc_node_track_caller+0xaf/0x160
Nov 14 20:52:44 server kernel: [196697.934192]  [<ffffffff81468de6>] ? __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196697.934196]  [<ffffffff81468aa0>] __alloc_skb+0x80/0x190
Nov 14 20:52:44 server kernel: [196697.934199]  [<ffffffff81468de6>] __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196697.934213]  [<ffffffffa000b5c7>] rtl8169_rx_interrupt+0x247/0x5b0 [r8169]
Nov 14 20:52:44 server kernel: [196697.934219]  [<ffffffffa000baad>] rtl8169_poll+0x3d/0x270 [r8169]
Nov 14 20:52:44 server kernel: [196697.934225]  [<ffffffff810387b9>] ? default_spin_lock_flags+0x9/0x10
Nov 14 20:52:44 server kernel: [196697.934230]  [<ffffffff8147300f>] net_rx_action+0x10f/0x250
Nov 14 20:52:44 server kernel: [196697.934236]  [<ffffffffa000954e>] ? rtl8169_interrupt+0xde/0x1e0 [r8169]
Nov 14 20:52:44 server kernel: [196697.934241]  [<ffffffff8106d477>] __do_softirq+0xb7/0x1e0
Nov 14 20:52:44 server kernel: [196697.934246]  [<ffffffff810c4030>] ? handle_IRQ_event+0x60/0x170
Nov 14 20:52:44 server kernel: [196697.934250]  [<ffffffff810132ec>] call_softirq+0x1c/0x30
Nov 14 20:52:44 server kernel: [196697.934254]  [<ffffffff81014cb5>] do_softirq+0x65/0xa0
Nov 14 20:52:44 server kernel: [196697.934257]  [<ffffffff8106d315>] irq_exit+0x85/0x90
Nov 14 20:52:44 server kernel: [196697.934262]  [<ffffffff8155f2a5>] do_IRQ+0x75/0xf0
Nov 14 20:52:44 server kernel: [196697.934266]  [<ffffffff81012b13>] ret_from_intr+0x0/0x11
Nov 14 20:52:44 server kernel: [196697.934268]  <EOI>  [<ffffffff81037adb>] ? native_safe_halt+0xb/0x10
Nov 14 20:52:44 server kernel: [196697.934277]  [<ffffffff8108e6c6>] ? ktime_get_real+0x16/0x50
Nov 14 20:52:44 server kernel: [196697.934283]  [<ffffffff8130e24f>] ? acpi_idle_do_entry+0x3e/0x67
Nov 14 20:52:44 server kernel: [196697.934287]  [<ffffffff8130e2ea>] ? acpi_idle_enter_c1+0x72/0xc1
Nov 14 20:52:44 server kernel: [196697.934291]  [<ffffffff8155ce86>] ? notifier_call_chain+0x16/0x80
Nov 14 20:52:44 server kernel: [196697.934296]  [<ffffffff8144e42d>] ? menu_select+0x10d/0x2a0
Nov 14 20:52:44 server kernel: [196697.934300]  [<ffffffff8144d367>] ? cpuidle_idle_call+0xa7/0x140
Nov 14 20:52:44 server kernel: [196697.934305]  [<ffffffff81010e63>] ? cpu_idle+0xb3/0x110
Nov 14 20:52:44 server kernel: [196697.934310]  [<ffffffff81551fab>] ? start_secondary+0xa8/0xaa
Nov 14 20:52:44 server kernel: [196697.934312] Mem-Info:
Nov 14 20:52:44 server kernel: [196697.934314] Node 0 DMA per-cpu:
Nov 14 20:52:44 server kernel: [196697.934318] CPU    0: hi:    0, btch:   1 usd:   0
Nov 14 20:52:44 server kernel: [196697.934320] CPU    1: hi:    0, btch:   1 usd:   0
Nov 14 20:52:44 server kernel: [196697.934322] Node 0 DMA32 per-cpu:
Nov 14 20:52:44 server kernel: [196697.934326] CPU    0: hi:  186, btch:  31 usd: 158
Nov 14 20:52:44 server kernel: [196697.934328] CPU    1: hi:  186, btch:  31 usd:  60
Nov 14 20:52:44 server kernel: [196697.934330] Node 0 Normal per-cpu:
Nov 14 20:52:44 server kernel: [196697.934334] CPU    0: hi:  186, btch:  31 usd: 146
Nov 14 20:52:44 server kernel: [196697.934336] CPU    1: hi:  186, btch:  31 usd: 117
Nov 14 20:52:44 server kernel: [196697.934342] active_anon:98612 inactive_anon:67367 isolated_anon:0
Nov 14 20:52:44 server kernel: [196697.934344]  active_file:61118 inactive_file:692972 isolated_file:0
Nov 14 20:52:44 server kernel: [196697.934345]  unevictable:0 dirty:35512 writeback:0 unstable:0
Nov 14 20:52:44 server kernel: [196697.934346]  free:5885 slab_reclaimable:37466 slab_unreclaimable:7139
Nov 14 20:52:44 server kernel: [196697.934347]  mapped:11697 shmem:2001 pagetables:2401 bounce:0
Nov 14 20:52:44 server kernel: [196697.934350] Node 0 DMA free:15908kB min:28kB low:32kB high:40kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15340kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Nov 14 20:52:44 server kernel: [196697.934362] lowmem_reserve[]: 0 2965 3975 3975
Nov 14 20:52:44 server kernel: [196697.934367] Node 0 DMA32 free:6972kB min:6004kB low:7504kB high:9004kB active_anon:192324kB inactive_anon:62168kB active_file:59336kB inactive_file:2486152kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:3036256kB mlocked:0kB dirty:141196kB writeback:0kB mapped:668kB shmem:380kB slab_reclaimable:134556kB slab_unreclaimable:15460kB kernel_stack:72kB pagetables:1080kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Nov 14 20:52:44 server kernel: [196697.934380] lowmem_reserve[]: 0 0 1010 1010
Nov 14 20:52:44 server kernel: [196697.934385] Node 0 Normal free:660kB min:2044kB low:2552kB high:3064kB active_anon:202124kB inactive_anon:207300kB active_file:185136kB inactive_file:285736kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:1034240kB mlocked:0kB dirty:852kB writeback:0kB mapped:46120kB shmem:7624kB slab_reclaimable:15308kB slab_unreclaimable:13096kB kernel_stack:2704kB pagetables:8524kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:32 all_unreclaimable? no
Nov 14 20:52:44 server kernel: [196697.934397] lowmem_reserve[]: 0 0 0 0
Nov 14 20:52:44 server kernel: [196697.934402] Node 0 DMA: 3*4kB 3*8kB 2*16kB 3*32kB 2*64kB 0*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 3*4096kB = 15908kB
Nov 14 20:52:44 server kernel: [196697.934415] Node 0 DMA32: 1429*4kB 5*8kB 4*16kB 0*32kB 0*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 6972kB
Nov 14 20:52:44 server kernel: [196697.934427] Node 0 Normal: 165*4kB 0*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 660kB
Nov 14 20:52:44 server kernel: [196697.934439] 756223 total pagecache pages
Nov 14 20:52:44 server kernel: [196697.934441] 116 pages in swap cache
Nov 14 20:52:44 server kernel: [196697.934443] Swap cache stats: add 1220, delete 1104, find 1308/1323
Nov 14 20:52:44 server kernel: [196697.934446] Free swap  = 15618740kB
Nov 14 20:52:44 server kernel: [196697.934448] Total swap = 15623172kB
Nov 14 20:52:44 server kernel: [196697.944098] 1048576 pages RAM
Nov 14 20:52:44 server kernel: [196697.944098] 42584 pages reserved
Nov 14 20:52:44 server kernel: [196697.944098] 751180 pages shared
Nov 14 20:52:44 server kernel: [196697.944098] 271091 pages non-shared
Nov 14 20:52:44 server kernel: [196697.944098] SLUB: Unable to allocate memory on node -1 (gfp=0x20)
Nov 14 20:52:44 server kernel: [196697.944098]   cache: kmalloc-4096, object size: 4096, buffer size: 4096, default order: 3, min order: 0
Nov 14 20:52:44 server kernel: [196697.944098]   node 0: slabs: 680, objs: 1471, free: 0
Nov 14 20:52:44 server kernel: [196697.952414] swapper: page allocation failure. order:3, mode:0x4020
Nov 14 20:52:44 server kernel: [196697.952419] Pid: 0, comm: swapper Not tainted 2.6.32-25-server #45-Ubuntu
Nov 14 20:52:44 server kernel: [196697.952422] Call Trace:
Nov 14 20:52:44 server kernel: [196697.952424]  <IRQ>  [<ffffffff810f9a2e>] __alloc_pages_slowpath+0x56e/0x580
Nov 14 20:52:44 server kernel: [196697.952437]  [<ffffffff810f9bb1>] __alloc_pages_nodemask+0x171/0x180
Nov 14 20:52:44 server kernel: [196697.952442]  [<ffffffff81131df2>] kmalloc_large_node+0x62/0xb0
Nov 14 20:52:44 server kernel: [196697.952446]  [<ffffffff81136409>] __kmalloc_node_track_caller+0x109/0x160
Nov 14 20:52:44 server kernel: [196697.952451]  [<ffffffff81468de6>] ? __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196697.952455]  [<ffffffff81468aa0>] __alloc_skb+0x80/0x190
Nov 14 20:52:44 server kernel: [196697.952459]  [<ffffffff81468de6>] __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196697.952472]  [<ffffffffa000b1ea>] rtl8169_rx_fill+0xba/0x250 [r8169]
Nov 14 20:52:44 server kernel: [196697.952477]  [<ffffffff8147250a>] ? netif_receive_skb+0x38a/0x5d0
Nov 14 20:52:44 server kernel: [196697.952483]  [<ffffffffa000b78b>] rtl8169_rx_interrupt+0x40b/0x5b0 [r8169]
Nov 14 20:52:44 server kernel: [196697.952490]  [<ffffffffa000baad>] rtl8169_poll+0x3d/0x270 [r8169]
Nov 14 20:52:44 server kernel: [196697.952496]  [<ffffffff810387b9>] ? default_spin_lock_flags+0x9/0x10
Nov 14 20:52:44 server kernel: [196697.952500]  [<ffffffff8147300f>] net_rx_action+0x10f/0x250
Nov 14 20:52:44 server kernel: [196697.952506]  [<ffffffffa000954e>] ? rtl8169_interrupt+0xde/0x1e0 [r8169]
Nov 14 20:52:44 server kernel: [196697.952511]  [<ffffffff8106d477>] __do_softirq+0xb7/0x1e0
Nov 14 20:52:44 server kernel: [196697.952516]  [<ffffffff810c4030>] ? handle_IRQ_event+0x60/0x170
Nov 14 20:52:44 server kernel: [196697.952520]  [<ffffffff810132ec>] call_softirq+0x1c/0x30
Nov 14 20:52:44 server kernel: [196697.952524]  [<ffffffff81014cb5>] do_softirq+0x65/0xa0
Nov 14 20:52:44 server kernel: [196697.952528]  [<ffffffff8106d315>] irq_exit+0x85/0x90
Nov 14 20:52:44 server kernel: [196697.952532]  [<ffffffff8155f2a5>] do_IRQ+0x75/0xf0
Nov 14 20:52:44 server kernel: [196697.952536]  [<ffffffff81012b13>] ret_from_intr+0x0/0x11
Nov 14 20:52:44 server kernel: [196697.952538]  <EOI>  [<ffffffff81037adb>] ? native_safe_halt+0xb/0x10
Nov 14 20:52:44 server kernel: [196697.952547]  [<ffffffff8108e6c6>] ? ktime_get_real+0x16/0x50
Nov 14 20:52:44 server kernel: [196697.952552]  [<ffffffff8130e24f>] ? acpi_idle_do_entry+0x3e/0x67
Nov 14 20:52:44 server kernel: [196697.952556]  [<ffffffff8130e2ea>] ? acpi_idle_enter_c1+0x72/0xc1
Nov 14 20:52:44 server kernel: [196697.952560]  [<ffffffff8155ce86>] ? notifier_call_chain+0x16/0x80
Nov 14 20:52:44 server kernel: [196697.952566]  [<ffffffff8144e42d>] ? menu_select+0x10d/0x2a0
Nov 14 20:52:44 server kernel: [196697.952570]  [<ffffffff8144d367>] ? cpuidle_idle_call+0xa7/0x140
Nov 14 20:52:44 server kernel: [196697.952575]  [<ffffffff81010e63>] ? cpu_idle+0xb3/0x110
Nov 14 20:52:44 server kernel: [196697.952579]  [<ffffffff81551fab>] ? start_secondary+0xa8/0xaa
Nov 14 20:52:44 server kernel: [196697.952582] Mem-Info:
Nov 14 20:52:44 server kernel: [196697.952584] Node 0 DMA per-cpu:
Nov 14 20:52:44 server kernel: [196697.952587] CPU    0: hi:    0, btch:   1 usd:   0
Nov 14 20:52:44 server kernel: [196697.952590] CPU    1: hi:    0, btch:   1 usd:   0
Nov 14 20:52:44 server kernel: [196697.952592] Node 0 DMA32 per-cpu:
Nov 14 20:52:44 server kernel: [196697.952595] CPU    0: hi:  186, btch:  31 usd: 176
Nov 14 20:52:44 server kernel: [196697.952598] CPU    1: hi:  186, btch:  31 usd:  59
Nov 14 20:52:44 server kernel: [196697.952600] Node 0 Normal per-cpu:
Nov 14 20:52:44 server kernel: [196697.952603] CPU    0: hi:  186, btch:  31 usd: 146
Nov 14 20:52:44 server kernel: [196697.952606] CPU    1: hi:  186, btch:  31 usd: 117
Nov 14 20:52:44 server kernel: [196697.952612] active_anon:98612 inactive_anon:67367 isolated_anon:0
Nov 14 20:52:44 server kernel: [196697.952613]  active_file:61118 inactive_file:692972 isolated_file:0
Nov 14 20:52:44 server kernel: [196697.952614]  unevictable:0 dirty:35512 writeback:0 unstable:0
Nov 14 20:52:44 server kernel: [196697.952615]  free:5822 slab_reclaimable:37466 slab_unreclaimable:7196
Nov 14 20:52:44 server kernel: [196697.952617]  mapped:11697 shmem:2001 pagetables:2401 bounce:0
Nov 14 20:52:44 server kernel: [196697.952620] Node 0 DMA free:15908kB min:28kB low:32kB high:40kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15340kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Nov 14 20:52:44 server kernel: [196697.952631] lowmem_reserve[]: 0 2965 3975 3975
Nov 14 20:52:44 server kernel: [196697.952636] Node 0 DMA32 free:6720kB min:6004kB low:7504kB high:9004kB active_anon:192324kB inactive_anon:62168kB active_file:59336kB inactive_file:2486152kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:3036256kB mlocked:0kB dirty:141196kB writeback:0kB mapped:668kB shmem:380kB slab_reclaimable:134556kB slab_unreclaimable:15688kB kernel_stack:72kB pagetables:1080kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Nov 14 20:52:44 server kernel: [196697.952649] lowmem_reserve[]: 0 0 1010 1010
Nov 14 20:52:44 server kernel: [196697.952654] Node 0 Normal free:660kB min:2044kB low:2552kB high:3064kB active_anon:202124kB inactive_anon:207300kB active_file:185136kB inactive_file:285736kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:1034240kB mlocked:0kB dirty:852kB writeback:0kB mapped:46120kB shmem:7624kB slab_reclaimable:15308kB slab_unreclaimable:13096kB kernel_stack:2704kB pagetables:8524kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:32 all_unreclaimable? no
Nov 14 20:52:44 server kernel: [196697.952667] lowmem_reserve[]: 0 0 0 0
Nov 14 20:52:44 server kernel: [196697.952671] Node 0 DMA: 3*4kB 3*8kB 2*16kB 3*32kB 2*64kB 0*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 3*4096kB = 15908kB
Nov 14 20:52:44 server kernel: [196697.952684] Node 0 DMA32: 1398*4kB 5*8kB 4*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 6720kB
Nov 14 20:52:44 server kernel: [196697.952696] Node 0 Normal: 165*4kB 0*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 660kB
Nov 14 20:52:44 server kernel: [196697.952707] 756223 total pagecache pages
Nov 14 20:52:44 server kernel: [196697.952710] 116 pages in swap cache
Nov 14 20:52:44 server kernel: [196697.952712] Swap cache stats: add 1220, delete 1104, find 1308/1323
Nov 14 20:52:44 server kernel: [196697.952714] Free swap  = 15618740kB
Nov 14 20:52:44 server kernel: [196697.952716] Total swap = 15623172kB
Nov 14 20:52:44 server kernel: [196697.970201] 1048576 pages RAM
Nov 14 20:52:44 server kernel: [196697.970203] 42584 pages reserved
Nov 14 20:52:44 server kernel: [196697.970205] 751180 pages shared
Nov 14 20:52:44 server kernel: [196697.970207] 271155 pages non-shared
Nov 14 20:52:44 server kernel: [196697.970506] swapper: page allocation failure. order:3, mode:0x4020
Nov 14 20:52:44 server kernel: [196697.970511] Pid: 0, comm: swapper Not tainted 2.6.32-25-server #45-Ubuntu
Nov 14 20:52:44 server kernel: [196697.970514] Call Trace:
Nov 14 20:52:44 server kernel: [196697.970517]  <IRQ>  [<ffffffff810f9a2e>] __alloc_pages_slowpath+0x56e/0x580
Nov 14 20:52:44 server kernel: [196697.970529]  [<ffffffff810f9bb1>] __alloc_pages_nodemask+0x171/0x180
Nov 14 20:52:44 server kernel: [196697.970534]  [<ffffffff81131df2>] kmalloc_large_node+0x62/0xb0
Nov 14 20:52:44 server kernel: [196697.970538]  [<ffffffff81136409>] __kmalloc_node_track_caller+0x109/0x160
Nov 14 20:52:44 server kernel: [196697.970543]  [<ffffffff81468de6>] ? __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196697.970547]  [<ffffffff81468aa0>] __alloc_skb+0x80/0x190
Nov 14 20:52:44 server kernel: [196697.970551]  [<ffffffff81468de6>] __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196697.970564]  [<ffffffffa000b1ea>] rtl8169_rx_fill+0xba/0x250 [r8169]
Nov 14 20:52:44 server kernel: [196697.970569]  [<ffffffff8147250a>] ? netif_receive_skb+0x38a/0x5d0
Nov 14 20:52:44 server kernel: [196697.970576]  [<ffffffffa000b78b>] rtl8169_rx_interrupt+0x40b/0x5b0 [r8169]
Nov 14 20:52:44 server kernel: [196697.970582]  [<ffffffffa000baad>] rtl8169_poll+0x3d/0x270 [r8169]
Nov 14 20:52:44 server kernel: [196697.970586]  [<ffffffff8147300f>] net_rx_action+0x10f/0x250
Nov 14 20:52:44 server kernel: [196697.970591]  [<ffffffff8106d477>] __do_softirq+0xb7/0x1e0
Nov 14 20:52:44 server kernel: [196697.970596]  [<ffffffff810c4030>] ? handle_IRQ_event+0x60/0x170
Nov 14 20:52:44 server kernel: [196697.970600]  [<ffffffff810132ec>] call_softirq+0x1c/0x30
Nov 14 20:52:44 server kernel: [196697.970604]  [<ffffffff81014cb5>] do_softirq+0x65/0xa0
Nov 14 20:52:44 server kernel: [196697.970608]  [<ffffffff8106d315>] irq_exit+0x85/0x90
Nov 14 20:52:44 server kernel: [196697.970612]  [<ffffffff8155f2a5>] do_IRQ+0x75/0xf0
Nov 14 20:52:44 server kernel: [196697.970616]  [<ffffffff81012b13>] ret_from_intr+0x0/0x11
Nov 14 20:52:44 server kernel: [196697.970618]  <EOI>  [<ffffffff81037adb>] ? native_safe_halt+0xb/0x10
Nov 14 20:52:44 server kernel: [196697.970627]  [<ffffffff8108e6c6>] ? ktime_get_real+0x16/0x50
Nov 14 20:52:44 server kernel: [196697.970632]  [<ffffffff8130e24f>] ? acpi_idle_do_entry+0x3e/0x67
Nov 14 20:52:44 server kernel: [196697.970636]  [<ffffffff8130e2ea>] ? acpi_idle_enter_c1+0x72/0xc1
Nov 14 20:52:44 server kernel: [196697.970641]  [<ffffffff8155ce86>] ? notifier_call_chain+0x16/0x80
Nov 14 20:52:44 server kernel: [196697.970646]  [<ffffffff8144e42d>] ? menu_select+0x10d/0x2a0
Nov 14 20:52:44 server kernel: [196697.970650]  [<ffffffff8144d367>] ? cpuidle_idle_call+0xa7/0x140
Nov 14 20:52:44 server kernel: [196697.970655]  [<ffffffff81010e63>] ? cpu_idle+0xb3/0x110
Nov 14 20:52:44 server kernel: [196697.970659]  [<ffffffff81551fab>] ? start_secondary+0xa8/0xaa
Nov 14 20:52:44 server kernel: [196697.970662] Mem-Info:
Nov 14 20:52:44 server kernel: [196697.970664] Node 0 DMA per-cpu:
Nov 14 20:52:44 server kernel: [196697.970667] CPU    0: hi:    0, btch:   1 usd:   0
Nov 14 20:52:44 server kernel: [196697.970670] CPU    1: hi:    0, btch:   1 usd:   0
Nov 14 20:52:44 server kernel: [196697.970673] Node 0 DMA32 per-cpu:
Nov 14 20:52:44 server kernel: [196697.970676] CPU    0: hi:  186, btch:  31 usd: 176
Nov 14 20:52:44 server kernel: [196697.970678] CPU    1: hi:  186, btch:  31 usd:  57
Nov 14 20:52:44 server kernel: [196697.970680] Node 0 Normal per-cpu:
Nov 14 20:52:44 server kernel: [196697.970684] CPU    0: hi:  186, btch:  31 usd: 146
Nov 14 20:52:44 server kernel: [196697.970686] CPU    1: hi:  186, btch:  31 usd: 117
Nov 14 20:52:44 server kernel: [196697.970692] active_anon:98612 inactive_anon:67367 isolated_anon:0
Nov 14 20:52:44 server kernel: [196697.970693]  active_file:61118 inactive_file:692972 isolated_file:0
Nov 14 20:52:44 server kernel: [196697.970695]  unevictable:0 dirty:35512 writeback:0 unstable:0
Nov 14 20:52:44 server kernel: [196697.970696]  free:5791 slab_reclaimable:37466 slab_unreclaimable:7221
Nov 14 20:52:44 server kernel: [196697.970697]  mapped:11697 shmem:2001 pagetables:2401 bounce:0
Nov 14 20:52:44 server kernel: [196697.970700] Node 0 DMA free:15908kB min:28kB low:32kB high:40kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15340kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Nov 14 20:52:44 server kernel: [196697.970712] lowmem_reserve[]: 0 2965 3975 3975
Nov 14 20:52:44 server kernel: [196697.970717] Node 0 DMA32 free:6596kB min:6004kB low:7504kB high:9004kB active_anon:192324kB inactive_anon:62168kB active_file:59336kB inactive_file:2486152kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:3036256kB mlocked:0kB dirty:141196kB writeback:0kB mapped:668kB shmem:380kB slab_reclaimable:134556kB slab_unreclaimable:15788kB kernel_stack:72kB pagetables:1080kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Nov 14 20:52:44 server kernel: [196697.970729] lowmem_reserve[]: 0 0 1010 1010
Nov 14 20:52:44 server kernel: [196697.970734] Node 0 Normal free:660kB min:2044kB low:2552kB high:3064kB active_anon:202124kB inactive_anon:207300kB active_file:185136kB inactive_file:285736kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:1034240kB mlocked:0kB dirty:852kB writeback:0kB mapped:46120kB shmem:7624kB slab_reclaimable:15308kB slab_unreclaimable:13096kB kernel_stack:2704kB pagetables:8524kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:32 all_unreclaimable? no
Nov 14 20:52:44 server kernel: [196697.970747] lowmem_reserve[]: 0 0 0 0
Nov 14 20:52:44 server kernel: [196697.970752] Node 0 DMA: 3*4kB 3*8kB 2*16kB 3*32kB 2*64kB 0*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 3*4096kB = 15908kB
Nov 14 20:52:44 server kernel: [196697.970764] Node 0 DMA32: 1367*4kB 5*8kB 4*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 6596kB
Nov 14 20:52:44 server kernel: [196697.970776] Node 0 Normal: 165*4kB 0*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 660kB
Nov 14 20:52:44 server kernel: [196697.970788] 756223 total pagecache pages
Nov 14 20:52:44 server kernel: [196697.970790] 116 pages in swap cache
Nov 14 20:52:44 server kernel: [196697.970792] Swap cache stats: add 1220, delete 1104, find 1308/1323
Nov 14 20:52:44 server kernel: [196697.970795] Free swap  = 15618740kB
Nov 14 20:52:44 server kernel: [196697.970797] Total swap = 15623172kB
Nov 14 20:52:44 server kernel: [196697.988309] 1048576 pages RAM
Nov 14 20:52:44 server kernel: [196697.988311] 42584 pages reserved
Nov 14 20:52:44 server kernel: [196697.988313] 751180 pages shared
Nov 14 20:52:44 server kernel: [196697.988314] 271188 pages non-shared
Nov 14 20:52:44 server kernel: [196697.988613] swapper: page allocation failure. order:3, mode:0x4020
Nov 14 20:52:44 server kernel: [196697.988618] Pid: 0, comm: swapper Not tainted 2.6.32-25-server #45-Ubuntu
Nov 14 20:52:44 server kernel: [196697.988621] Call Trace:
Nov 14 20:52:44 server kernel: [196697.988623]  <IRQ>  [<ffffffff810f9a2e>] __alloc_pages_slowpath+0x56e/0x580
Nov 14 20:52:44 server kernel: [196697.988635]  [<ffffffff810f9bb1>] __alloc_pages_nodemask+0x171/0x180
Nov 14 20:52:44 server kernel: [196697.988640]  [<ffffffff81131df2>] kmalloc_large_node+0x62/0xb0
Nov 14 20:52:44 server kernel: [196697.988645]  [<ffffffff81136409>] __kmalloc_node_track_caller+0x109/0x160
Nov 14 20:52:44 server kernel: [196697.988650]  [<ffffffff81468de6>] ? __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196697.988654]  [<ffffffff81468aa0>] __alloc_skb+0x80/0x190
Nov 14 20:52:44 server kernel: [196697.988658]  [<ffffffff81468de6>] __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196697.988671]  [<ffffffffa000b1ea>] rtl8169_rx_fill+0xba/0x250 [r8169]
Nov 14 20:52:44 server kernel: [196697.988677]  [<ffffffff8147250a>] ? netif_receive_skb+0x38a/0x5d0
Nov 14 20:52:44 server kernel: [196697.988683]  [<ffffffffa000b78b>] rtl8169_rx_interrupt+0x40b/0x5b0 [r8169]
Nov 14 20:52:44 server kernel: [196697.988689]  [<ffffffffa000baad>] rtl8169_poll+0x3d/0x270 [r8169]
Nov 14 20:52:44 server kernel: [196697.988694]  [<ffffffff8147300f>] net_rx_action+0x10f/0x250
Nov 14 20:52:44 server kernel: [196697.988699]  [<ffffffff8106d477>] __do_softirq+0xb7/0x1e0
Nov 14 20:52:44 server kernel: [196697.988703]  [<ffffffff810c4030>] ? handle_IRQ_event+0x60/0x170
Nov 14 20:52:44 server kernel: [196697.988708]  [<ffffffff810132ec>] call_softirq+0x1c/0x30
Nov 14 20:52:44 server kernel: [196697.988712]  [<ffffffff81014cb5>] do_softirq+0x65/0xa0
Nov 14 20:52:44 server kernel: [196697.988715]  [<ffffffff8106d315>] irq_exit+0x85/0x90
Nov 14 20:52:44 server kernel: [196697.988720]  [<ffffffff8155f2a5>] do_IRQ+0x75/0xf0
Nov 14 20:52:44 server kernel: [196697.988724]  [<ffffffff81012b13>] ret_from_intr+0x0/0x11
Nov 14 20:52:44 server kernel: [196697.988726]  <EOI>  [<ffffffff81037adb>] ? native_safe_halt+0xb/0x10
Nov 14 20:52:44 server kernel: [196697.988735]  [<ffffffff8108e6c6>] ? ktime_get_real+0x16/0x50
Nov 14 20:52:44 server kernel: [196697.988740]  [<ffffffff8130e24f>] ? acpi_idle_do_entry+0x3e/0x67
Nov 14 20:52:44 server kernel: [196697.988744]  [<ffffffff8130e2ea>] ? acpi_idle_enter_c1+0x72/0xc1
Nov 14 20:52:44 server kernel: [196697.988749]  [<ffffffff8155ce86>] ? notifier_call_chain+0x16/0x80
Nov 14 20:52:44 server kernel: [196697.988754]  [<ffffffff8144e42d>] ? menu_select+0x10d/0x2a0
Nov 14 20:52:44 server kernel: [196697.988758]  [<ffffffff8144d367>] ? cpuidle_idle_call+0xa7/0x140
Nov 14 20:52:44 server kernel: [196697.988763]  [<ffffffff81010e63>] ? cpu_idle+0xb3/0x110
Nov 14 20:52:44 server kernel: [196697.988767]  [<ffffffff81551fab>] ? start_secondary+0xa8/0xaa
Nov 14 20:52:44 server kernel: [196697.988770] Mem-Info:
Nov 14 20:52:44 server kernel: [196697.988772] Node 0 DMA per-cpu:
Nov 14 20:52:44 server kernel: [196697.988775] CPU    0: hi:    0, btch:   1 usd:   0
Nov 14 20:52:44 server kernel: [196697.988778] CPU    1: hi:    0, btch:   1 usd:   0
Nov 14 20:52:44 server kernel: [196697.988780] Node 0 DMA32 per-cpu:
Nov 14 20:52:44 server kernel: [196697.988783] CPU    0: hi:  186, btch:  31 usd: 176
Nov 14 20:52:44 server kernel: [196697.988786] CPU    1: hi:  186, btch:  31 usd:  54
Nov 14 20:52:44 server kernel: [196697.988788] Node 0 Normal per-cpu:
Nov 14 20:52:44 server kernel: [196697.988791] CPU    0: hi:  186, btch:  31 usd: 146
Nov 14 20:52:44 server kernel: [196697.988794] CPU    1: hi:  186, btch:  31 usd: 117
Nov 14 20:52:44 server kernel: [196697.988800] active_anon:98612 inactive_anon:67367 isolated_anon:0
Nov 14 20:52:44 server kernel: [196697.988801]  active_file:61118 inactive_file:692972 isolated_file:0
Nov 14 20:52:44 server kernel: [196697.988802]  unevictable:0 dirty:35512 writeback:0 unstable:0
Nov 14 20:52:44 server kernel: [196697.988804]  free:5760 slab_reclaimable:37466 slab_unreclaimable:7271
Nov 14 20:52:44 server kernel: [196697.988805]  mapped:11697 shmem:2001 pagetables:2401 bounce:0
Nov 14 20:52:44 server kernel: [196697.988808] Node 0 DMA free:15908kB min:28kB low:32kB high:40kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15340kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Nov 14 20:52:44 server kernel: [196697.988819] lowmem_reserve[]: 0 2965 3975 3975
Nov 14 20:52:44 server kernel: [196697.988825] Node 0 DMA32 free:6472kB min:6004kB low:7504kB high:9004kB active_anon:192324kB inactive_anon:62168kB active_file:59336kB inactive_file:2486152kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:3036256kB mlocked:0kB dirty:141196kB writeback:0kB mapped:668kB shmem:380kB slab_reclaimable:134556kB slab_unreclaimable:15988kB kernel_stack:72kB pagetables:1080kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Nov 14 20:52:44 server kernel: [196697.988837] lowmem_reserve[]: 0 0 1010 1010
Nov 14 20:52:44 server kernel: [196697.988842] Node 0 Normal free:660kB min:2044kB low:2552kB high:3064kB active_anon:202124kB inactive_anon:207300kB active_file:185136kB inactive_file:285736kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:1034240kB mlocked:0kB dirty:852kB writeback:0kB mapped:46120kB shmem:7624kB slab_reclaimable:15308kB slab_unreclaimable:13096kB kernel_stack:2704kB pagetables:8524kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:32 all_unreclaimable? no
Nov 14 20:52:44 server kernel: [196697.988855] lowmem_reserve[]: 0 0 0 0
Nov 14 20:52:44 server kernel: [196697.988859] Node 0 DMA: 3*4kB 3*8kB 2*16kB 3*32kB 2*64kB 0*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 3*4096kB = 15908kB
Nov 14 20:52:44 server kernel: [196697.988872] Node 0 DMA32: 1336*4kB 5*8kB 4*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 6472kB
Nov 14 20:52:44 server kernel: [196697.988884] Node 0 Normal: 165*4kB 0*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 660kB
Nov 14 20:52:44 server kernel: [196697.988896] 756223 total pagecache pages
Nov 14 20:52:44 server kernel: [196697.988898] 116 pages in swap cache
Nov 14 20:52:44 server kernel: [196697.988900] Swap cache stats: add 1220, delete 1104, find 1308/1323
Nov 14 20:52:44 server kernel: [196697.988903] Free swap  = 15618740kB
Nov 14 20:52:44 server kernel: [196697.988905] Total swap = 15623172kB
Nov 14 20:52:44 server kernel: [196698.006410] 1048576 pages RAM
Nov 14 20:52:44 server kernel: [196698.006412] 42584 pages reserved
Nov 14 20:52:44 server kernel: [196698.006414] 751180 pages shared
Nov 14 20:52:44 server kernel: [196698.006416] 271222 pages non-shared
Nov 14 20:52:44 server kernel: [196698.006762] swapper: page allocation failure. order:3, mode:0x4020
Nov 14 20:52:44 server kernel: [196698.006766] Pid: 0, comm: swapper Not tainted 2.6.32-25-server #45-Ubuntu
Nov 14 20:52:44 server kernel: [196698.006769] Call Trace:
Nov 14 20:52:44 server kernel: [196698.006771]  <IRQ>  [<ffffffff810f9a2e>] __alloc_pages_slowpath+0x56e/0x580
Nov 14 20:52:44 server kernel: [196698.006784]  [<ffffffff810f9bb1>] __alloc_pages_nodemask+0x171/0x180
Nov 14 20:52:44 server kernel: [196698.006789]  [<ffffffff81131df2>] kmalloc_large_node+0x62/0xb0
Nov 14 20:52:44 server kernel: [196698.006793]  [<ffffffff81136409>] __kmalloc_node_track_caller+0x109/0x160
Nov 14 20:52:44 server kernel: [196698.006798]  [<ffffffff81468de6>] ? __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196698.006802]  [<ffffffff81468aa0>] __alloc_skb+0x80/0x190
Nov 14 20:52:44 server kernel: [196698.006806]  [<ffffffff81468de6>] __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196698.006819]  [<ffffffffa000b1ea>] rtl8169_rx_fill+0xba/0x250 [r8169]
Nov 14 20:52:44 server kernel: [196698.006824]  [<ffffffff8147250a>] ? netif_receive_skb+0x38a/0x5d0
Nov 14 20:52:44 server kernel: [196698.006831]  [<ffffffffa000b78b>] rtl8169_rx_interrupt+0x40b/0x5b0 [r8169]
Nov 14 20:52:44 server kernel: [196698.006837]  [<ffffffffa000baad>] rtl8169_poll+0x3d/0x270 [r8169]
Nov 14 20:52:44 server kernel: [196698.006842]  [<ffffffff8147300f>] net_rx_action+0x10f/0x250
Nov 14 20:52:44 server kernel: [196698.006846]  [<ffffffff8106d477>] __do_softirq+0xb7/0x1e0
Nov 14 20:52:44 server kernel: [196698.006851]  [<ffffffff810c4030>] ? handle_IRQ_event+0x60/0x170
Nov 14 20:52:44 server kernel: [196698.006855]  [<ffffffff810132ec>] call_softirq+0x1c/0x30
Nov 14 20:52:44 server kernel: [196698.006859]  [<ffffffff81014cb5>] do_softirq+0x65/0xa0
Nov 14 20:52:44 server kernel: [196698.006863]  [<ffffffff8106d315>] irq_exit+0x85/0x90
Nov 14 20:52:44 server kernel: [196698.006867]  [<ffffffff8155f2a5>] do_IRQ+0x75/0xf0
Nov 14 20:52:44 server kernel: [196698.006871]  [<ffffffff81012b13>] ret_from_intr+0x0/0x11
Nov 14 20:52:44 server kernel: [196698.006873]  <EOI>  [<ffffffff81037adb>] ? native_safe_halt+0xb/0x10
Nov 14 20:52:44 server kernel: [196698.006882]  [<ffffffff8108e6c6>] ? ktime_get_real+0x16/0x50
Nov 14 20:52:44 server kernel: [196698.006887]  [<ffffffff8130e24f>] ? acpi_idle_do_entry+0x3e/0x67
Nov 14 20:52:44 server kernel: [196698.006891]  [<ffffffff8130e2ea>] ? acpi_idle_enter_c1+0x72/0xc1
Nov 14 20:52:44 server kernel: [196698.006896]  [<ffffffff8155ce86>] ? notifier_call_chain+0x16/0x80
Nov 14 20:52:44 server kernel: [196698.006901]  [<ffffffff8144e42d>] ? menu_select+0x10d/0x2a0
Nov 14 20:52:44 server kernel: [196698.006905]  [<ffffffff8144d367>] ? cpuidle_idle_call+0xa7/0x140
Nov 14 20:52:44 server kernel: [196698.006910]  [<ffffffff81010e63>] ? cpu_idle+0xb3/0x110
Nov 14 20:52:44 server kernel: [196698.006914]  [<ffffffff81551fab>] ? start_secondary+0xa8/0xaa
Nov 14 20:52:44 server kernel: [196698.006917] Mem-Info:
Nov 14 20:52:44 server kernel: [196698.006919] Node 0 DMA per-cpu:
Nov 14 20:52:44 server kernel: [196698.006922] CPU    0: hi:    0, btch:   1 usd:   0
Nov 14 20:52:44 server kernel: [196698.006925] CPU    1: hi:    0, btch:   1 usd:   0
Nov 14 20:52:44 server kernel: [196698.006927] Node 0 DMA32 per-cpu:
Nov 14 20:52:44 server kernel: [196698.006930] CPU    0: hi:  186, btch:  31 usd: 176
Nov 14 20:52:44 server kernel: [196698.006933] CPU    1: hi:  186, btch:  31 usd:  44
Nov 14 20:52:44 server kernel: [196698.006934] Node 0 Normal per-cpu:
Nov 14 20:52:44 server kernel: [196698.006938] CPU    0: hi:  186, btch:  31 usd: 146
Nov 14 20:52:44 server kernel: [196698.006940] CPU    1: hi:  186, btch:  31 usd: 117
Nov 14 20:52:44 server kernel: [196698.006946] active_anon:98612 inactive_anon:67367 isolated_anon:0
Nov 14 20:52:44 server kernel: [196698.006947]  active_file:61118 inactive_file:692972 isolated_file:0
Nov 14 20:52:44 server kernel: [196698.006948]  unevictable:0 dirty:35512 writeback:0 unstable:0
Nov 14 20:52:44 server kernel: [196698.006950]  free:5729 slab_reclaimable:37466 slab_unreclaimable:7296
Nov 14 20:52:44 server kernel: [196698.006951]  mapped:11697 shmem:2001 pagetables:2401 bounce:0
Nov 14 20:52:44 server kernel: [196698.006954] Node 0 DMA free:15908kB min:28kB low:32kB high:40kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15340kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Nov 14 20:52:44 server kernel: [196698.006966] lowmem_reserve[]: 0 2965 3975 3975
Nov 14 20:52:44 server kernel: [196698.006971] Node 0 DMA32 free:6348kB min:6004kB low:7504kB high:9004kB active_anon:192324kB inactive_anon:62168kB active_file:59336kB inactive_file:2486152kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:3036256kB mlocked:0kB dirty:141196kB writeback:0kB mapped:668kB shmem:380kB slab_reclaimable:134556kB slab_unreclaimable:16088kB kernel_stack:72kB pagetables:1080kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Nov 14 20:52:44 server kernel: [196698.006984] lowmem_reserve[]: 0 0 1010 1010
Nov 14 20:52:44 server kernel: [196698.006989] Node 0 Normal free:660kB min:2044kB low:2552kB high:3064kB active_anon:202124kB inactive_anon:207300kB active_file:185136kB inactive_file:285736kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:1034240kB mlocked:0kB dirty:852kB writeback:0kB mapped:46120kB shmem:7624kB slab_reclaimable:15308kB slab_unreclaimable:13096kB kernel_stack:2704kB pagetables:8524kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:32 all_unreclaimable? no
Nov 14 20:52:44 server kernel: [196698.007001] lowmem_reserve[]: 0 0 0 0
Nov 14 20:52:44 server kernel: [196698.007006] Node 0 DMA: 3*4kB 3*8kB 2*16kB 3*32kB 2*64kB 0*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 3*4096kB = 15908kB
Nov 14 20:52:44 server kernel: [196698.007019] Node 0 DMA32: 1305*4kB 5*8kB 4*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 6348kB
Nov 14 20:52:44 server kernel: [196698.007031] Node 0 Normal: 165*4kB 0*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 660kB
Nov 14 20:52:44 server kernel: [196698.007043] 756223 total pagecache pages
Nov 14 20:52:44 server kernel: [196698.007045] 116 pages in swap cache
Nov 14 20:52:44 server kernel: [196698.007047] Swap cache stats: add 1220, delete 1104, find 1308/1323
Nov 14 20:52:44 server kernel: [196698.007049] Free swap  = 15618740kB
Nov 14 20:52:44 server kernel: [196698.007051] Total swap = 15623172kB
Nov 14 20:52:44 server kernel: [196698.024562] 1048576 pages RAM
Nov 14 20:52:44 server kernel: [196698.024565] 42584 pages reserved
Nov 14 20:52:44 server kernel: [196698.024567] 751177 pages shared
Nov 14 20:52:44 server kernel: [196698.024568] 271266 pages non-shared
Nov 14 20:52:44 server kernel: [196698.024746] swapper: page allocation failure. order:0, mode:0x4020
Nov 14 20:52:44 server kernel: [196698.024751] Pid: 0, comm: swapper Not tainted 2.6.32-25-server #45-Ubuntu
Nov 14 20:52:44 server kernel: [196698.024753] Call Trace:
Nov 14 20:52:44 server kernel: [196698.024756]  <IRQ>  [<ffffffff810f9a2e>] __alloc_pages_slowpath+0x56e/0x580
Nov 14 20:52:44 server kernel: [196698.024768]  [<ffffffff810f9bb1>] __alloc_pages_nodemask+0x171/0x180
Nov 14 20:52:44 server kernel: [196698.024773]  [<ffffffff8112cae7>] alloc_pages_current+0x87/0xd0
Nov 14 20:52:44 server kernel: [196698.024778]  [<ffffffff81132b27>] new_slab+0x2f7/0x310
Nov 14 20:52:44 server kernel: [196698.024782]  [<ffffffff811353d1>] __slab_alloc+0x201/0x2d0
Nov 14 20:52:44 server kernel: [196698.024787]  [<ffffffff81468de6>] ? __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196698.024791]  [<ffffffff811363af>] __kmalloc_node_track_caller+0xaf/0x160
Nov 14 20:52:44 server kernel: [196698.024795]  [<ffffffff81468de6>] ? __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196698.024799]  [<ffffffff81468aa0>] __alloc_skb+0x80/0x190
Nov 14 20:52:44 server kernel: [196698.024803]  [<ffffffff81468de6>] __netdev_alloc_skb+0x36/0x60
Nov 14 20:52:44 server kernel: [196698.024816]  [<ffffffffa000b5c7>] rtl8169_rx_interrupt+0x247/0x5b0 [r8169]
Nov 14 20:52:44 server kernel: [196698.024822]  [<ffffffffa000baad>] rtl8169_poll+0x3d/0x270 [r8169]
Nov 14 20:52:44 server kernel: [196698.024827]  [<ffffffff8147300f>] net_rx_action+0x10f/0x250
Nov 14 20:52:44 server kernel: [196698.024832]  [<ffffffff8106d477>] __do_softirq+0xb7/0x1e0
Nov 14 20:52:44 server kernel: [196698.024837]  [<ffffffff810c4030>] ? handle_IRQ_event+0x60/0x170
Nov 14 20:52:44 server kernel: [196698.024841]  [<ffffffff810132ec>] call_softirq+0x1c/0x30
Nov 14 20:52:44 server kernel: [196698.024845]  [<ffffffff81014cb5>] do_softirq+0x65/0xa0
Nov 14 20:52:44 server kernel: [196698.024848]  [<ffffffff8106d315>] irq_exit+0x85/0x90
Nov 14 20:52:44 server kernel: [196698.024853]  [<ffffffff8155f2a5>] do_IRQ+0x75/0xf0
Nov 14 20:52:44 server kernel: [196698.024857]  [<ffffffff81012b13>] ret_from_intr+0x0/0x11
Nov 14 20:52:44 server kernel: [196698.024859]  <EOI>  [<ffffffff81037adb>] ? native_safe_halt+0xb/0x10
Nov 14 20:52:44 server kernel: [196698.024868]  [<ffffffff8108e6c6>] ? ktime_get_real+0x16/0x50
Nov 14 20:52:44 server kernel: [196698.024873]  [<ffffffff8130e24f>] ? acpi_idle_do_entry+0x3e/0x67
Nov 14 20:52:44 server kernel: [196698.024877]  [<ffffffff8130e2ea>] ? acpi_idle_enter_c1+0x72/0xc1
Nov 14 20:52:44 server kernel: [196698.024881]  [<ffffffff8155ce86>] ? notifier_call_chain+0x16/0x80
Nov 14 20:52:44 server kernel: [196698.024887]  [<ffffffff8144e42d>] ? menu_select+0x10d/0x2a0
Nov 14 20:52:44 server kernel: [196698.024891]  [<ffffffff8144d367>] ? cpuidle_idle_call+0xa7/0x140
Nov 14 20:52:44 server kernel: [196698.024896]  [<ffffffff81010e63>] ? cpu_idle+0xb3/0x110
Nov 14 20:52:44 server kernel: [196698.024900]  [<ffffffff81551fab>] ? start_secondary+0xa8/0xaa
Nov 14 20:52:44 server kernel: [196698.024903] Mem-Info:
Nov 14 20:52:44 server kernel: [196698.024905] Node 0 DMA per-cpu:
Nov 14 20:52:44 server kernel: [196698.024908] CPU    0: hi:    0, btch:   1 usd:   0
Nov 14 20:52:44 server kernel: [196698.024911] CPU    1: hi:    0, btch:   1 usd:   0
Nov 14 20:52:44 server kernel: [196698.024913] Node 0 DMA32 per-cpu:
Nov 14 20:52:44 server kernel: [196698.024916] CPU    0: hi:  186, btch:  31 usd: 176
Nov 14 20:52:44 server kernel: [196698.024919] CPU    1: hi:  186, btch:  31 usd:  60
Nov 14 20:52:44 server kernel: [196698.024921] Node 0 Normal per-cpu:
Nov 14 20:52:44 server kernel: [196698.024924] CPU    0: hi:  186, btch:  31 usd: 146
Nov 14 20:52:44 server kernel: [196698.024927] CPU    1: hi:  186, btch:  31 usd: 117
Nov 14 20:52:44 server kernel: [196698.024933] active_anon:98612 inactive_anon:67367 isolated_anon:0
Nov 14 20:52:44 server kernel: [196698.024934]  active_file:61118 inactive_file:692972 isolated_file:0
Nov 14 20:52:44 server kernel: [196698.024936]  unevictable:0 dirty:35512 writeback:0 unstable:0
Nov 14 20:52:44 server kernel: [196698.024937]  free:5698 slab_reclaimable:37466 slab_unreclaimable:7321
Nov 14 20:52:44 server kernel: [196698.024938]  mapped:11697 shmem:2001 pagetables:2401 bounce:0
Nov 14 20:52:44 server kernel: [196698.024941] Node 0 DMA free:15908kB min:28kB low:32kB high:40kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15340kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Nov 14 20:52:44 server kernel: [196698.024953] lowmem_reserve[]: 0 2965 3975 3975
Nov 14 20:52:44 server kernel: [196698.024958] Node 0 DMA32 free:6224kB min:6004kB low:7504kB high:9004kB active_anon:192324kB inactive_anon:62168kB active_file:59336kB inactive_file:2486152kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:3036256kB mlocked:0kB dirty:141196kB writeback:0kB mapped:668kB shmem:380kB slab_reclaimable:134556kB slab_unreclaimable:16188kB kernel_stack:72kB pagetables:1080kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Nov 14 20:52:44 server kernel: [196698.024971] lowmem_reserve[]: 0 0 1010 1010
Nov 14 20:52:44 server kernel: [196698.024975] Node 0 Normal free:660kB min:2044kB low:2552kB high:3064kB active_anon:202124kB inactive_anon:207300kB active_file:185136kB inactive_file:285736kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:1034240kB mlocked:0kB dirty:852kB writeback:0kB mapped:46120kB shmem:7624kB slab_reclaimable:15308kB slab_unreclaimable:13096kB kernel_stack:2704kB pagetables:8524kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:32 all_unreclaimable? no
Nov 14 20:52:44 server kernel: [196698.024988] lowmem_reserve[]: 0 0 0 0
Nov 14 20:52:44 server kernel: [196698.024993] Node 0 DMA: 3*4kB 3*8kB 2*16kB 3*32kB 2*64kB 0*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 3*4096kB = 15908kB
Nov 14 20:52:44 server kernel: [196698.025005] Node 0 DMA32: 1274*4kB 5*8kB 4*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 6224kB
Nov 14 20:52:44 server kernel: [196698.025017] Node 0 Normal: 165*4kB 0*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 660kB
Nov 14 20:52:44 server kernel: [196698.025030] 756223 total pagecache pages
Nov 14 20:52:44 server kernel: [196698.025032] 116 pages in swap cache
Nov 14 20:52:44 server kernel: [196698.025034] Swap cache stats: add 1220, delete 1104, find 1308/1323
Nov 14 20:52:44 server kernel: [196698.025037] Free swap  = 15618740kB
Nov 14 20:52:44 server kernel: [196698.025039] Total swap = 15623172kB
Nov 14 20:52:44 server kernel: [196698.040074] 1048576 pages RAM
Nov 14 20:52:44 server kernel: [196698.040074] 42584 pages reserved
Nov 14 20:52:44 server kernel: [196698.040074] 751176 pages shared
Nov 14 20:52:44 server kernel: [196698.040074] 271282 pages non-shared
Nov 14 20:52:44 server kernel: [196698.040074] SLUB: Unable to allocate memory on node -1 (gfp=0x20)
Nov 14 20:52:44 server kernel: [196698.040074]   cache: kmalloc-4096, object size: 4096, buffer size: 4096, default order: 3, min order: 0
Nov 14 20:52:44 server kernel: [196698.040074]   node 0: slabs: 827, objs: 1646, free: 0
Nov 15 15:28:23 server kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov 15 15:28:23 server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1076" x-info="http://www.rsyslog.com"] (re)start
Nov 15 15:28:23 server rsyslogd: rsyslogd's groupid changed to 102
Nov 15 15:28:23 server rsyslogd: rsyslogd's userid changed to 101
Nov 15 15:28:23 server kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 15 15:28:23 server kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 15 15:28:23 server kernel: [    0.000000] Linux version 2.6.32-25-server (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #45-Ubuntu SMP Sat Oct 16 20:06:58 UTC 2010 (Ubuntu 2.6.32-25.45-server 2.6.32.21+drm33.7)
Nov 15 15:28:23 server kernel: [    0.000000] Command line: root=UUID=44862d65-d880-4f88-9d4c-8e5e08a7242a ro quiet splash 
Nov 15 15:28:23 server kernel: [    0.000000] KERNEL supported cpus:
Nov 15 15:28:23 server kernel: [    0.000000]   Intel GenuineIntel
Nov 15 15:28:23 server kernel: [    0.000000]   AMD AuthenticAMD
Nov 15 15:28:23 server kernel: [    0.000000]   Centaur CentaurHauls
Nov 15 15:28:23 server kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 15 15:28:23 server kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Nov 15 15:28:23 server kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Nov 15 15:28:23 server kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov 15 15:28:23 server kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bdce0000 (usable)
Nov 15 15:28:23 server kernel: [    0.000000]  BIOS-e820: 00000000bdce0000 - 00000000bdce3000 (ACPI NVS)
Nov 15 15:28:23 server kernel: [    0.000000]  BIOS-e820: 00000000bdce3000 - 00000000bdcf0000 (ACPI data)
Nov 15 15:28:23 server kernel: [    0.000000]  BIOS-e820: 00000000bdcf0000 - 00000000bdd00000 (reserved)
Nov 15 15:28:23 server kernel: [    0.000000]  BIOS-e820: 00000000c0000000 - 00000000d0000000 (reserved)
Nov 15 15:28:23 server kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Nov 15 15:28:23 server kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Nov 15 15:28:23 server kernel: [    0.000000] DMI 2.4 present.
Nov 15 15:28:23 server kernel: [    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
Nov 15 15:28:23 server kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 15 15:28:23 server kernel: [    0.000000] last_pfn = 0xbdce0 max_arch_pfn = 0x400000000
Nov 15 15:28:23 server kernel: [    0.000000] Scanning 1 areas for low memory corruption
Nov 15 15:28:23 server kernel: [    0.000000] modified physical RAM map:
Nov 15 15:28:23 server kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Nov 15 15:28:23 server kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
Nov 15 15:28:23 server kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Nov 15 15:28:23 server kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Nov 15 15:28:23 server kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Nov 15 15:28:23 server kernel: [    0.000000]  modified: 0000000000100000 - 00000000bdce0000 (usable)
Nov 15 15:28:23 server kernel: [    0.000000]  modified: 00000000bdce0000 - 00000000bdce3000 (ACPI NVS)
Nov 15 15:28:23 server kernel: [    0.000000]  modified: 00000000bdce3000 - 00000000bdcf0000 (ACPI data)
Nov 15 15:28:23 server kernel: [    0.000000]  modified: 00000000bdcf0000 - 00000000bdd00000 (reserved)
Nov 15 15:28:23 server kernel: [    0.000000]  modified: 00000000c0000000 - 00000000d0000000 (reserved)
Nov 15 15:28:23 server kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Nov 15 15:28:23 server kernel: [    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
Nov 15 15:28:23 server kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bdce0000
Nov 15 15:28:23 server kernel: [    0.000000] NX (Execute Disable) protection: active
Nov 15 15:28:23 server kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
Nov 15 15:28:23 server kernel: [    0.000000] NX (Execute Disable) protection: active
Nov 15 15:28:23 server kernel: [    0.000000] RAMDISK: 377d3000 - 37fefd59
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: RSDP 00000000000f70d0 00014 (v00 GBT   )
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: RSDT 00000000bdce3040 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: FACP 00000000bdce30c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: DSDT 00000000bdce3180 04526 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: FACS 00000000bdce0000 00040
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: HPET 00000000bdce7800 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: MCFG 00000000bdce7880 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: APIC 00000000bdce7700 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: SSDT 00000000bdce7f20 003AB (v01  PmRef    CpuPm 00003000 INTL 20040311)
Nov 15 15:28:23 server kernel: [    0.000000] No NUMA configuration found
Nov 15 15:28:23 server kernel: [    0.000000] Faking a node at 0000000000000000-0000000140000000
Nov 15 15:28:23 server kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
Nov 15 15:28:23 server kernel: [    0.000000]   NODE_DATA [000000000000c000 - 0000000000010fff]
Nov 15 15:28:23 server kernel: [    0.000000]   bootmap [0000000000011000 -  0000000000038fff] pages 28
Nov 15 15:28:23 server kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
Nov 15 15:28:23 server kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Nov 15 15:28:23 server kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Nov 15 15:28:23 server kernel: [    0.000000]   #2 [0001000000 - 0001a4caa4]    TEXT DATA BSS ==> [0001000000 - 0001a4caa4]
Nov 15 15:28:23 server kernel: [    0.000000]   #3 [00377d3000 - 0037fefd59]          RAMDISK ==> [00377d3000 - 0037fefd59]
Nov 15 15:28:23 server kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Nov 15 15:28:23 server kernel: [    0.000000]   #5 [0001a4d000 - 0001a4d0f6]              BRK ==> [0001a4d000 - 0001a4d0f6]
Nov 15 15:28:23 server kernel: [    0.000000]   #6 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
Nov 15 15:28:23 server kernel: [    0.000000]   #7 [000000b000 - 000000c000]          PGTABLE ==> [000000b000 - 000000c000]
Nov 15 15:28:23 server kernel: [    0.000000] found SMP MP-table at [ffff8800000f56e0] f56e0
Nov 15 15:28:23 server kernel: [    0.000000] Zone PFN ranges:
Nov 15 15:28:23 server kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Nov 15 15:28:23 server kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Nov 15 15:28:23 server kernel: [    0.000000]   Normal   0x00100000 -> 0x00140000
Nov 15 15:28:23 server kernel: [    0.000000] Movable zone start PFN for each node
Nov 15 15:28:23 server kernel: [    0.000000] early_node_map[4] active PFN ranges
Nov 15 15:28:23 server kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
Nov 15 15:28:23 server kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Nov 15 15:28:23 server kernel: [    0.000000]     0: 0x00000100 -> 0x000bdce0
Nov 15 15:28:23 server kernel: [    0.000000]     0: 0x00100000 -> 0x00140000
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 15 15:28:23 server kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 15 15:28:23 server kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 15 15:28:23 server kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Nov 15 15:28:23 server kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Nov 15 15:28:23 server kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
Nov 15 15:28:23 server kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov 15 15:28:23 server kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Nov 15 15:28:23 server kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Nov 15 15:28:23 server kernel: [    0.000000] PM: Registered nosave memory: 00000000bdce0000 - 00000000bdce3000
Nov 15 15:28:23 server kernel: [    0.000000] PM: Registered nosave memory: 00000000bdce3000 - 00000000bdcf0000
Nov 15 15:28:23 server kernel: [    0.000000] PM: Registered nosave memory: 00000000bdcf0000 - 00000000bdd00000
Nov 15 15:28:23 server kernel: [    0.000000] PM: Registered nosave memory: 00000000bdd00000 - 00000000c0000000
Nov 15 15:28:23 server kernel: [    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000d0000000
Nov 15 15:28:23 server kernel: [    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fec00000
Nov 15 15:28:23 server kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Nov 15 15:28:23 server kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ec00000)
Nov 15 15:28:23 server kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Nov 15 15:28:23 server kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Nov 15 15:28:23 server kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880005600000 s91544 r8192 d23144 u524288
Nov 15 15:28:23 server kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
Nov 15 15:28:23 server kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Nov 15 15:28:23 server kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1021459
Nov 15 15:28:23 server kernel: [    0.000000] Policy zone: Normal
Nov 15 15:28:23 server kernel: [    0.000000] Kernel command line: root=UUID=44862d65-d880-4f88-9d4c-8e5e08a7242a ro quiet splash 
Nov 15 15:28:23 server kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Nov 15 15:28:23 server kernel: [    0.000000] Initializing CPU#0
Nov 15 15:28:23 server kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Nov 15 15:28:23 server kernel: [    0.000000] Checking aperture...
Nov 15 15:28:23 server kernel: [    0.000000] No AGP bridge found
Nov 15 15:28:23 server kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Nov 15 15:28:23 server kernel: [    0.000000] Placing 64MB software IO TLB between ffff88000579e000 - ffff88000979e000
Nov 15 15:28:23 server kernel: [    0.000000] software IO TLB at phys 0x579e000 - 0x979e000
Nov 15 15:28:23 server kernel: [    0.000000] Memory: 4014868k/5242880k available (5510k kernel code, 1084952k absent, 143060k reserved, 3087k data, 796k init)
Nov 15 15:28:23 server kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Nov 15 15:28:23 server kernel: [    0.000000] Hierarchical RCU implementation.
Nov 15 15:28:23 server kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
Nov 15 15:28:23 server kernel: [    0.000000] Console: colour VGA+ 80x25
Nov 15 15:28:23 server kernel: [    0.000000] console [tty0] enabled
Nov 15 15:28:23 server kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Nov 15 15:28:23 server kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov 15 15:28:23 server kernel: [    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Nov 15 15:28:23 server kernel: [    0.000000] Fast TSC calibration using PIT
Nov 15 15:28:23 server kernel: [    0.000000] Detected 2800.172 MHz processor.
Nov 15 15:28:23 server kernel: [    0.000005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5600.34 BogoMIPS (lpj=28001720)
Nov 15 15:28:23 server kernel: [    0.000026] Security Framework initialized
Nov 15 15:28:23 server kernel: [    0.000042] AppArmor: AppArmor initialized
Nov 15 15:28:23 server kernel: [    0.010229] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Nov 15 15:28:23 server kernel: [    0.011892] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Nov 15 15:28:23 server kernel: [    0.012658] Mount-cache hash table entries: 256
Nov 15 15:28:23 server kernel: [    0.012786] Initializing cgroup subsys ns
Nov 15 15:28:23 server kernel: [    0.012792] Initializing cgroup subsys cpuacct
Nov 15 15:28:23 server kernel: [    0.012794] Initializing cgroup subsys memory
Nov 15 15:28:23 server kernel: [    0.012800] Initializing cgroup subsys devices
Nov 15 15:28:23 server kernel: [    0.012802] Initializing cgroup subsys freezer
Nov 15 15:28:23 server kernel: [    0.012804] Initializing cgroup subsys net_cls
Nov 15 15:28:23 server kernel: [    0.012821] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 15 15:28:23 server kernel: [    0.012823] CPU: L2 cache: 2048K
Nov 15 15:28:23 server kernel: [    0.012826] CPU 0/0x0 -> Node 0
Nov 15 15:28:23 server kernel: [    0.012828] CPU: Physical Processor ID: 0
Nov 15 15:28:23 server kernel: [    0.012829] CPU: Processor Core ID: 0
Nov 15 15:28:23 server kernel: [    0.012832] mce: CPU supports 6 MCE banks
Nov 15 15:28:23 server kernel: [    0.012838] CPU0: Thermal monitoring enabled (TM2)
Nov 15 15:28:23 server kernel: [    0.012842] using mwait in idle threads.
Nov 15 15:28:23 server kernel: [    0.012843] Performance Events: Core2 events, Intel PMU driver.
Nov 15 15:28:23 server kernel: [    0.012848] ... version:                2
Nov 15 15:28:23 server kernel: [    0.012849] ... bit width:              40
Nov 15 15:28:23 server kernel: [    0.012850] ... generic registers:      2
Nov 15 15:28:23 server kernel: [    0.012851] ... value mask:             000000ffffffffff
Nov 15 15:28:23 server kernel: [    0.012853] ... max period:             000000007fffffff
Nov 15 15:28:23 server kernel: [    0.012854] ... fixed-purpose events:   3
Nov 15 15:28:23 server kernel: [    0.012855] ... event mask:             0000000700000003
Nov 15 15:28:23 server kernel: [    0.014949] ACPI: Core revision 20090903
Nov 15 15:28:23 server kernel: [    0.020965] ftrace: converting mcount calls to 0f 1f 44 00 00
Nov 15 15:28:23 server kernel: [    0.020973] ftrace: allocating 22828 entries in 90 pages
Nov 15 15:28:23 server kernel: [    0.028690] Setting APIC routing to flat
Nov 15 15:28:23 server kernel: [    0.028993] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 15 15:28:23 server kernel: [    0.129013] CPU0: Intel Pentium(R) Dual-Core  CPU      E6300  @ 2.80GHz stepping 0a
Nov 15 15:28:23 server kernel: [    0.130000] Booting processor 1 APIC 0x1 ip 0x6000
Nov 15 15:28:23 server kernel: [    0.010000] Initializing CPU#1
Nov 15 15:28:23 server kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 15 15:28:23 server kernel: [    0.010000] CPU: L2 cache: 2048K
Nov 15 15:28:23 server kernel: [    0.010000] CPU 1/0x1 -> Node 0
Nov 15 15:28:23 server kernel: [    0.010000] CPU: Physical Processor ID: 0
Nov 15 15:28:23 server kernel: [    0.010000] CPU: Processor Core ID: 1
Nov 15 15:28:23 server kernel: [    0.010000] CPU1: Thermal monitoring enabled (TM2)
Nov 15 15:28:23 server kernel: [    0.280106] CPU1: Intel Pentium(R) Dual-Core  CPU      E6300  @ 2.80GHz stepping 0a
Nov 15 15:28:23 server kernel: [    0.280112] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Nov 15 15:28:23 server kernel: [    0.290014] Brought up 2 CPUs
Nov 15 15:28:23 server kernel: [    0.290016] Total of 2 processors activated (11200.52 BogoMIPS).
Nov 15 15:28:23 server kernel: [    0.290512] devtmpfs: initialized
Nov 15 15:28:23 server kernel: [    0.292095] regulator: core version 0.5
Nov 15 15:28:23 server kernel: [    0.292095] Time: 20:28:01  Date: 11/15/10
Nov 15 15:28:23 server kernel: [    0.292095] NET: Registered protocol family 16
Nov 15 15:28:23 server kernel: [    0.292095] ACPI: bus type pci registered
Nov 15 15:28:23 server kernel: [    0.292095] PCI: MCFG configuration 0: base c0000000 segment 0 buses 0 - 255
Nov 15 15:28:23 server kernel: [    0.292095] PCI: MCFG area at c0000000 reserved in E820
Nov 15 15:28:23 server kernel: [    0.295823] PCI: Using MMCONFIG at c0000000 - cfffffff
Nov 15 15:28:23 server kernel: [    0.295825] PCI: Using configuration type 1 for base access
Nov 15 15:28:23 server kernel: [    0.296430] Trying to unpack rootfs image as initramfs...
Nov 15 15:28:23 server kernel: [    0.300053] bio: create slab <bio-0> at 0
Nov 15 15:28:23 server kernel: [    0.304811] ACPI: Interpreter enabled
Nov 15 15:28:23 server kernel: [    0.304816] ACPI: (supports S0 S3 S4 S5)
Nov 15 15:28:23 server kernel: [    0.304833] ACPI: Using IOAPIC for interrupt routing
Nov 15 15:28:23 server kernel: [    0.308057] ACPI: No dock devices found.
Nov 15 15:28:23 server kernel: [    0.308138] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 15 15:28:23 server kernel: [    0.308576] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Nov 15 15:28:23 server kernel: [    0.308579] pci 0000:00:1c.0: PME# disabled
Nov 15 15:28:23 server kernel: [    0.308637] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Nov 15 15:28:23 server kernel: [    0.308640] pci 0000:00:1c.5: PME# disabled
Nov 15 15:28:23 server kernel: [    0.309338] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 15 15:28:23 server kernel: [    0.309342] pci 0000:02:00.0: PME# disabled
Nov 15 15:28:23 server kernel: [    0.309481] pci 0000:03:07.0: PME# supported from D0 D1 D2 D3hot
Nov 15 15:28:23 server kernel: [    0.309484] pci 0000:03:07.0: PME# disabled
Nov 15 15:28:23 server kernel: [    0.309517] pci 0000:00:1e.0: transparent bridge
Nov 15 15:28:23 server kernel: [    0.321671] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Nov 15 15:28:23 server kernel: [    0.321744] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 15 15:28:23 server kernel: [    0.321815] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Nov 15 15:28:23 server kernel: [    0.321890] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 *15)
Nov 15 15:28:23 server kernel: [    0.321960] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 15 15:28:23 server kernel: [    0.322033] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Nov 15 15:28:23 server kernel: [    0.322103] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 15 15:28:23 server kernel: [    0.322176] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 12 *14 15)
Nov 15 15:28:23 server kernel: [    0.322266] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Nov 15 15:28:23 server kernel: [    0.322275] vgaarb: loaded
Nov 15 15:28:23 server kernel: [    0.322364] SCSI subsystem initialized
Nov 15 15:28:23 server kernel: [    0.322484] usbcore: registered new interface driver usbfs
Nov 15 15:28:23 server kernel: [    0.322495] usbcore: registered new interface driver hub
Nov 15 15:28:23 server kernel: [    0.322515] usbcore: registered new device driver usb
Nov 15 15:28:23 server kernel: [    0.322612] ACPI: WMI: Mapper loaded
Nov 15 15:28:23 server kernel: [    0.322613] PCI: Using ACPI for IRQ routing
Nov 15 15:28:23 server kernel: [    0.322743] NetLabel: Initializing
Nov 15 15:28:23 server kernel: [    0.322745] NetLabel:  domain hash size = 128
Nov 15 15:28:23 server kernel: [    0.322746] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 15 15:28:23 server kernel: [    0.322756] NetLabel:  unlabeled traffic allowed by default
Nov 15 15:28:23 server kernel: [    0.322782] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Nov 15 15:28:23 server kernel: [    0.322786] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Nov 15 15:28:23 server kernel: [    0.330117] Switching to clocksource tsc
Nov 15 15:28:23 server kernel: [    0.331392] AppArmor: AppArmor Filesystem Enabled
Nov 15 15:28:23 server kernel: [    0.331407] pnp: PnP ACPI init
Nov 15 15:28:23 server kernel: [    0.331421] ACPI: bus type pnp registered
Nov 15 15:28:23 server kernel: [    0.333015] pnp: PnP ACPI: found 11 devices
Nov 15 15:28:23 server kernel: [    0.333017] ACPI: ACPI bus type pnp unregistered
Nov 15 15:28:23 server kernel: [    0.333026] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Nov 15 15:28:23 server kernel: [    0.333029] system 00:01: ioport range 0x290-0x29f has been reserved
Nov 15 15:28:23 server kernel: [    0.333031] system 00:01: ioport range 0x800-0x87f has been reserved
Nov 15 15:28:23 server kernel: [    0.333033] system 00:01: ioport range 0x290-0x294 has been reserved
Nov 15 15:28:23 server kernel: [    0.333034] system 00:01: ioport range 0x880-0x88f has been reserved
Nov 15 15:28:23 server kernel: [    0.333036] system 00:01: ioport range 0x4c0-0x4ff could not be reserved
Nov 15 15:28:23 server kernel: [    0.333041] system 00:07: ioport range 0x400-0x4bf has been reserved
Nov 15 15:28:23 server kernel: [    0.333046] system 00:08: iomem range 0xc0000000-0xcfffffff has been reserved
Nov 15 15:28:23 server kernel: [    0.333049] system 00:09: iomem range 0xcc600-0xcffff has been reserved
Nov 15 15:28:23 server kernel: [    0.333052] system 00:09: iomem range 0xf0000-0xf7fff could not be reserved
Nov 15 15:28:23 server kernel: [    0.333054] system 00:09: iomem range 0xf8000-0xfbfff could not be reserved
Nov 15 15:28:23 server kernel: [    0.333056] system 00:09: iomem range 0xfc000-0xfffff could not be reserved
Nov 15 15:28:23 server kernel: [    0.333057] system 00:09: iomem range 0xbdce0000-0xbdcfffff could not be reserved
Nov 15 15:28:23 server kernel: [    0.333060] system 00:09: iomem range 0x0-0x9ffff could not be reserved
Nov 15 15:28:23 server kernel: [    0.333062] system 00:09: iomem range 0x100000-0xbdcdffff could not be reserved
Nov 15 15:28:23 server kernel: [    0.333064] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
Nov 15 15:28:23 server kernel: [    0.333066] system 00:09: iomem range 0xfed10000-0xfed1dfff has been reserved
Nov 15 15:28:23 server kernel: [    0.333068] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
Nov 15 15:28:23 server kernel: [    0.333070] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
Nov 15 15:28:23 server kernel: [    0.333072] system 00:09: iomem range 0xffb00000-0xffb7ffff has been reserved
Nov 15 15:28:23 server kernel: [    0.333074] system 00:09: iomem range 0xfff00000-0xffffffff has been reserved
Nov 15 15:28:23 server kernel: [    0.333078] system 00:09: iomem range 0xe0000-0xeffff has been reserved
Nov 15 15:28:23 server kernel: [    0.337761] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
Nov 15 15:28:23 server kernel: [    0.337765] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
Nov 15 15:28:23 server kernel: [    0.337769] pci 0000:00:1c.0:   MEM window: 0xe1800000-0xe19fffff
Nov 15 15:28:23 server kernel: [    0.337772] pci 0000:00:1c.0:   PREFETCH window: 0x000000e1a00000-0x000000e1bfffff
Nov 15 15:28:23 server kernel: [    0.337777] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
Nov 15 15:28:23 server kernel: [    0.337780] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
Nov 15 15:28:23 server kernel: [    0.337784] pci 0000:00:1c.5:   MEM window: 0xe0000000-0xe0ffffff
Nov 15 15:28:23 server kernel: [    0.337787] pci 0000:00:1c.5:   PREFETCH window: 0x000000e1500000-0x000000e15fffff
Nov 15 15:28:23 server kernel: [    0.337792] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Nov 15 15:28:23 server kernel: [    0.337793] pci 0000:00:1e.0:   IO window: disabled
Nov 15 15:28:23 server kernel: [    0.337796] pci 0000:00:1e.0:   MEM window: 0xe1600000-0xe16fffff
Nov 15 15:28:23 server kernel: [    0.337799] pci 0000:00:1e.0:   PREFETCH window: disabled
Nov 15 15:28:23 server kernel: [    0.337820] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 15 15:28:23 server kernel: [    0.337836] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov 15 15:28:23 server kernel: [    0.337894] NET: Registered protocol family 2
Nov 15 15:28:23 server kernel: [    0.338033] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Nov 15 15:28:23 server kernel: [    0.338995] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Nov 15 15:28:23 server kernel: [    0.342474] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Nov 15 15:28:23 server kernel: [    0.342894] TCP: Hash tables configured (established 524288 bind 65536)
Nov 15 15:28:23 server kernel: [    0.342896] TCP reno registered
Nov 15 15:28:23 server kernel: [    0.342992] NET: Registered protocol family 1
Nov 15 15:28:23 server kernel: [    0.343301] Scanning for low memory corruption every 60 seconds
Nov 15 15:28:23 server kernel: [    0.343403] audit: initializing netlink socket (disabled)
Nov 15 15:28:23 server kernel: [    0.343416] type=2000 audit(1289852880.339:1): initialized
Nov 15 15:28:23 server kernel: [    0.350776] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Nov 15 15:28:23 server kernel: [    0.351792] VFS: Disk quotas dquot_6.5.2
Nov 15 15:28:23 server kernel: [    0.351833] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Nov 15 15:28:23 server kernel: [    0.352259] fuse init (API version 7.13)
Nov 15 15:28:23 server kernel: [    0.352317] msgmni has been set to 7841
Nov 15 15:28:23 server kernel: [    0.352469] alg: No test for stdrng (krng)
Nov 15 15:28:23 server kernel: [    0.352511] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Nov 15 15:28:23 server kernel: [    0.352513] io scheduler noop registered
Nov 15 15:28:23 server kernel: [    0.352515] io scheduler anticipatory registered
Nov 15 15:28:23 server kernel: [    0.352516] io scheduler deadline registered (default)
Nov 15 15:28:23 server kernel: [    0.352540] io scheduler cfq registered
Nov 15 15:28:23 server kernel: [    0.352835] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 15 15:28:23 server kernel: [    0.352892] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov 15 15:28:23 server kernel: [    0.352970] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Nov 15 15:28:23 server kernel: [    0.352973] ACPI: Power Button [PWRB]
Nov 15 15:28:23 server kernel: [    0.353011] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Nov 15 15:28:23 server kernel: [    0.353013] ACPI: Power Button [PWRF]
Nov 15 15:28:23 server kernel: [    0.353417] ACPI: SSDT 00000000bdce7900 0026C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
Nov 15 15:28:23 server kernel: [    0.353536] Marking TSC unstable due to TSC halts in idle
Nov 15 15:28:23 server kernel: [    0.353592] processor LNXCPU:00: registered as cooling_device0
Nov 15 15:28:23 server kernel: [    0.353747] ACPI: SSDT 00000000bdce7dc0 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
Nov 15 15:28:23 server kernel: [    0.353886] Switching to clocksource hpet
Nov 15 15:28:23 server kernel: [    0.353885] processor LNXCPU:01: registered as cooling_device1
Nov 15 15:28:23 server kernel: [    0.356320] Linux agpgart interface v0.103
Nov 15 15:28:23 server kernel: [    0.356344] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Nov 15 15:28:23 server kernel: [    0.357218] brd: module loaded
Nov 15 15:28:23 server kernel: [    0.357550] loop: module loaded
Nov 15 15:28:23 server kernel: [    0.357619] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Nov 15 15:28:23 server kernel: [    0.357725] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 15 15:28:23 server kernel: [    0.357729] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Nov 15 15:28:23 server kernel: [    0.363602] scsi0 : ata_piix
Nov 15 15:28:23 server kernel: [    0.363713] scsi1 : ata_piix
Nov 15 15:28:23 server kernel: [    0.364304] ata1: SATA max UDMA/133 cmd 0xd700 ctl 0xd800 bmdma 0xdb00 irq 19
Nov 15 15:28:23 server kernel: [    0.364308] ata2: SATA max UDMA/133 cmd 0xd900 ctl 0xda00 bmdma 0xdb08 irq 19
Nov 15 15:28:23 server kernel: [    0.364334] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 15 15:28:23 server kernel: [    0.364338] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Nov 15 15:28:23 server kernel: [    0.364407] scsi2 : ata_piix
Nov 15 15:28:23 server kernel: [    0.364445] scsi3 : ata_piix
Nov 15 15:28:23 server kernel: [    0.364865] ata3: SATA max UDMA/133 cmd 0xde00 ctl 0xdf00 bmdma 0xe200 irq 19
Nov 15 15:28:23 server kernel: [    0.364868] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xe100 bmdma 0xe208 irq 19
Nov 15 15:28:23 server kernel: [    0.365104] Fixed MDIO Bus: probed
Nov 15 15:28:23 server kernel: [    0.365127] PPP generic driver version 2.4.2
Nov 15 15:28:23 server kernel: [    0.365174] tun: Universal TUN/TAP device driver, 1.6
Nov 15 15:28:23 server kernel: [    0.365176] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Nov 15 15:28:23 server kernel: [    0.365260] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov 15 15:28:23 server kernel: [    0.365282] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 15 15:28:23 server kernel: [    0.365305] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Nov 15 15:28:23 server kernel: [    0.365328] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Nov 15 15:28:23 server kernel: [    0.369228] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xe1701000
Nov 15 15:28:23 server kernel: [    0.390033] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Nov 15 15:28:23 server kernel: [    0.390137] usb usb1: configuration #1 chosen from 1 choice
Nov 15 15:28:23 server kernel: [    0.390158] hub 1-0:1.0: USB hub found
Nov 15 15:28:23 server kernel: [    0.390165] hub 1-0:1.0: 6 ports detected
Nov 15 15:28:23 server kernel: [    0.390224] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 15 15:28:23 server kernel: [    0.390246] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov 15 15:28:23 server kernel: [    0.390278] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Nov 15 15:28:23 server kernel: [    0.394197] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe1700000
Nov 15 15:28:23 server kernel: [    0.410023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Nov 15 15:28:23 server kernel: [    0.410114] usb usb2: configuration #1 chosen from 1 choice
Nov 15 15:28:23 server kernel: [    0.410138] hub 2-0:1.0: USB hub found
Nov 15 15:28:23 server kernel: [    0.410147] hub 2-0:1.0: 6 ports detected
Nov 15 15:28:23 server kernel: [    0.410196] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 15 15:28:23 server kernel: [    0.410212] uhci_hcd: USB Universal Host Controller Interface driver
Nov 15 15:28:23 server kernel: [    0.410255] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 15 15:28:23 server kernel: [    0.410265] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Nov 15 15:28:23 server kernel: [    0.410300] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Nov 15 15:28:23 server kernel: [    0.410334] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000d000
Nov 15 15:28:23 server kernel: [    0.410398] usb usb3: configuration #1 chosen from 1 choice
Nov 15 15:28:23 server kernel: [    0.410415] hub 3-0:1.0: USB hub found
Nov 15 15:28:23 server kernel: [    0.410420] hub 3-0:1.0: 2 ports detected
Nov 15 15:28:23 server kernel: [    0.410459] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Nov 15 15:28:23 server kernel: [    0.410467] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Nov 15 15:28:23 server kernel: [    0.410491] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Nov 15 15:28:23 server kernel: [    0.410517] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d100
Nov 15 15:28:23 server kernel: [    0.410581] usb usb4: configuration #1 chosen from 1 choice
Nov 15 15:28:23 server kernel: [    0.410600] hub 4-0:1.0: USB hub found
Nov 15 15:28:23 server kernel: [    0.410604] hub 4-0:1.0: 2 ports detected
Nov 15 15:28:23 server kernel: [    0.410634] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 15 15:28:23 server kernel: [    0.410641] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Nov 15 15:28:23 server kernel: [    0.410663] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Nov 15 15:28:23 server kernel: [    0.410684] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000d200
Nov 15 15:28:23 server kernel: [    0.410747] usb usb5: configuration #1 chosen from 1 choice
Nov 15 15:28:23 server kernel: [    0.410766] hub 5-0:1.0: USB hub found
Nov 15 15:28:23 server kernel: [    0.410770] hub 5-0:1.0: 2 ports detected
Nov 15 15:28:23 server kernel: [    0.410801] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 15 15:28:23 server kernel: [    0.410807] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov 15 15:28:23 server kernel: [    0.410829] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Nov 15 15:28:23 server kernel: [    0.410851] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
Nov 15 15:28:23 server kernel: [    0.410919] usb usb6: configuration #1 chosen from 1 choice
Nov 15 15:28:23 server kernel: [    0.410936] hub 6-0:1.0: USB hub found
Nov 15 15:28:23 server kernel: [    0.410940] hub 6-0:1.0: 2 ports detected
Nov 15 15:28:23 server kernel: [    0.410978] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 15 15:28:23 server kernel: [    0.410985] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov 15 15:28:23 server kernel: [    0.411006] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Nov 15 15:28:23 server kernel: [    0.411026] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d500
Nov 15 15:28:23 server kernel: [    0.411088] usb usb7: configuration #1 chosen from 1 choice
Nov 15 15:28:23 server kernel: [    0.411104] hub 7-0:1.0: USB hub found
Nov 15 15:28:23 server kernel: [    0.411109] hub 7-0:1.0: 2 ports detected
Nov 15 15:28:23 server kernel: [    0.411141] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 15 15:28:23 server kernel: [    0.411148] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov 15 15:28:23 server kernel: [    0.411169] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Nov 15 15:28:23 server kernel: [    0.411189] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d600
Nov 15 15:28:23 server kernel: [    0.411251] usb usb8: configuration #1 chosen from 1 choice
Nov 15 15:28:23 server kernel: [    0.411270] hub 8-0:1.0: USB hub found
Nov 15 15:28:23 server kernel: [    0.411274] hub 8-0:1.0: 2 ports detected
Nov 15 15:28:23 server kernel: [    0.411342] PNP: No PS/2 controller found. Probing ports directly.
Nov 15 15:28:23 server kernel: [    0.411698] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 15 15:28:23 server kernel: [    0.411703] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov 15 15:28:23 server kernel: [    0.411762] mice: PS/2 mouse device common for all mice
Nov 15 15:28:23 server kernel: [    0.411834] rtc_cmos 00:04: RTC can wake from S4
Nov 15 15:28:23 server kernel: [    0.411863] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Nov 15 15:28:23 server kernel: [    0.411885] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Nov 15 15:28:23 server kernel: [    0.411977] device-mapper: uevent: version 1.0.3
Nov 15 15:28:23 server kernel: [    0.412080] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Nov 15 15:28:23 server kernel: [    0.412130] device-mapper: multipath: version 1.1.0 loaded
Nov 15 15:28:23 server kernel: [    0.412132] device-mapper: multipath round-robin: version 1.0.0 loaded
Nov 15 15:28:23 server kernel: [    0.412261] cpuidle: using governor ladder
Nov 15 15:28:23 server kernel: [    0.412301] cpuidle: using governor menu
Nov 15 15:28:23 server kernel: [    0.412565] TCP cubic registered
Nov 15 15:28:23 server kernel: [    0.412666] NET: Registered protocol family 10
Nov 15 15:28:23 server kernel: [    0.412997] lo: Disabled Privacy Extensions
Nov 15 15:28:23 server kernel: [    0.413199] NET: Registered protocol family 17
Nov 15 15:28:23 server kernel: [    0.414737] registered taskstats version 1
Nov 15 15:28:23 server kernel: [    0.415017]   Magic number: 2:207:498
Nov 15 15:28:23 server kernel: [    0.415097] rtc_cmos 00:04: setting system clock to 2010-11-15 20:28:01 UTC (1289852881)
Nov 15 15:28:23 server kernel: [    0.415099] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 15 15:28:23 server kernel: [    0.415100] EDD information not available.
Nov 15 15:28:23 server kernel: [    0.445659] Freeing initrd memory: 8307k freed
Nov 15 15:28:23 server kernel: [    0.730670] ata4: SATA link down (SStatus 0 SControl 300)
Nov 15 15:28:23 server kernel: [    0.890049] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 15 15:28:23 server kernel: [    0.917992] ata3.00: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
Nov 15 15:28:23 server kernel: [    0.917997] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Nov 15 15:28:23 server kernel: [    0.930015] usb 4-2: new low speed USB device using uhci_hcd and address 2
Nov 15 15:28:23 server kernel: [    0.950549] ata3.00: configured for UDMA/133
Nov 15 15:28:23 server kernel: [    1.171649] usb 4-2: configuration #1 chosen from 1 choice
Nov 15 15:28:23 server kernel: [    1.240064] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 15 15:28:23 server kernel: [    1.240079] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 15 15:28:23 server kernel: [    1.240198] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 15 15:28:23 server kernel: [    1.240209] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 15 15:28:23 server kernel: [    1.288521] ata2.00: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
Nov 15 15:28:23 server kernel: [    1.288525] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Nov 15 15:28:23 server kernel: [    1.299769] ata2.01: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
Nov 15 15:28:23 server kernel: [    1.299773] ata2.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Nov 15 15:28:23 server kernel: [    1.300213] ata1.00: HPA unlocked: 1250261615 -> 1250263728, native 1250263728
Nov 15 15:28:23 server kernel: [    1.300218] ata1.00: ATA-8: WDC WD6400AACS-00G8B1, 05.04C05, max UDMA/133
Nov 15 15:28:23 server kernel: [    1.300223] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 0/32)
Nov 15 15:28:23 server kernel: [    1.310053] ata1.01: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
Nov 15 15:28:23 server kernel: [    1.310057] ata1.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Nov 15 15:28:23 server kernel: [    1.320654] ata2.00: configured for UDMA/133
Nov 15 15:28:23 server kernel: [    1.341311] ata1.00: configured for UDMA/133
Nov 15 15:28:23 server kernel: [    1.360885] ata2.01: configured for UDMA/133
Nov 15 15:28:23 server kernel: [    1.380523] ata1.01: configured for UDMA/133
Nov 15 15:28:23 server kernel: [    1.380634] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400AACS-0 05.0 PQ: 0 ANSI: 5
Nov 15 15:28:23 server kernel: [    1.380745] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Nov 15 15:28:23 server kernel: [    1.380758] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 15 15:28:23 server kernel: [    1.380778] sd 0:0:0:0: [sda] Write Protect is off
Nov 15 15:28:23 server kernel: [    1.380797] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 15 15:28:23 server kernel: [    1.380831] scsi 0:0:1:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
Nov 15 15:28:23 server kernel: [    1.380905]  sda:
Nov 15 15:28:23 server kernel: [    1.380907] sd 0:0:1:0: Attached scsi generic sg1 type 0
Nov 15 15:28:23 server kernel: [    1.381005] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
Nov 15 15:28:23 server kernel: [    1.381074] sd 1:0:0:0: Attached scsi generic sg2 type 0
Nov 15 15:28:23 server kernel: [    1.381157] sd 1:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Nov 15 15:28:23 server kernel: [    1.381158] scsi 1:0:1:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
Nov 15 15:28:23 server kernel: [    1.381190] sd 1:0:0:0: [sdc] Write Protect is off
Nov 15 15:28:23 server kernel: [    1.381223] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 15 15:28:23 server kernel: [    1.381228] sd 1:0:1:0: Attached scsi generic sg3 type 0
Nov 15 15:28:23 server kernel: [    1.381298] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
Nov 15 15:28:23 server kernel: [    1.381334]  sdc:
Nov 15 15:28:23 server kernel: [    1.381368] sd 2:0:0:0: Attached scsi generic sg4 type 0
Nov 15 15:28:23 server kernel: [    1.381405] sd 2:0:0:0: [sde] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Nov 15 15:28:23 server kernel: [    1.381435] sd 2:0:0:0: [sde] Write Protect is off
Nov 15 15:28:23 server kernel: [    1.381453] sd 2:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 15 15:28:23 server kernel: [    1.381529]  sde: sdc1
Nov 15 15:28:23 server kernel: [    1.384615] sd 1:0:1:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Nov 15 15:28:23 server kernel: [    1.384671] sd 1:0:1:0: [sdd] Write Protect is off
Nov 15 15:28:23 server kernel: [    1.384702] sd 1:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 15 15:28:23 server kernel: [    1.384837] sd 1:0:0:0: [sdc] Attached SCSI disk
Nov 15 15:28:23 server kernel: [    1.384847]  sdd: sde1
Nov 15 15:28:23 server kernel: [    1.389259] sd 2:0:0:0: [sde] Attached SCSI disk
Nov 15 15:28:23 server kernel: [    1.390840]  sda1 sda2 <
Nov 15 15:28:23 server kernel: [    1.390859] sd 0:0:1:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Nov 15 15:28:23 server kernel: [    1.395854]  sdd1
Nov 15 15:28:23 server kernel: [    1.396048] sd 1:0:1:0: [sdd] Attached SCSI disk
Nov 15 15:28:23 server kernel: [    1.407283]  sda5 sda6 sda7 >
Nov 15 15:28:23 server kernel: [    1.429036] sd 0:0:1:0: [sdb] Write Protect is off
Nov 15 15:28:23 server kernel: [    1.429068] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 15 15:28:23 server kernel: [    1.429261]  sdb: sdb1
Nov 15 15:28:23 server kernel: [    1.439549] sd 0:0:0:0: [sda] Attached SCSI disk
Nov 15 15:28:23 server kernel: [    1.439659] sd 0:0:1:0: [sdb] Attached SCSI disk
Nov 15 15:28:23 server kernel: [    1.439676] Freeing unused kernel memory: 796k freed
Nov 15 15:28:23 server kernel: [    1.439901] Write protecting the kernel read-only data: 7800k
Nov 15 15:28:23 server kernel: [    1.450357] udev: starting version 151
Nov 15 15:28:23 server kernel: [    1.520722] md: linear personality registered for level -1
Nov 15 15:28:23 server kernel: [    1.529948] md: multipath personality registered for level -4
Nov 15 15:28:23 server kernel: [    1.532901] ohci1394 0000:03:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 15 15:28:23 server kernel: [    1.536369] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Nov 15 15:28:23 server kernel: [    1.536388] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 15 15:28:23 server kernel: [    1.536905] eth0: RTL8168c/8111c at 0xffffc90000654000, 00:1f:d0:27:53:6d, XID 1c4000c0 IRQ 26
Nov 15 15:28:23 server kernel: [    1.537941] usbcore: registered new interface driver hiddev
Nov 15 15:28:23 server kernel: [    1.541397] md: raid0 personality registered for level 0
Nov 15 15:28:23 server kernel: [    1.543749] md: raid1 personality registered for level 1
Nov 15 15:28:23 server kernel: [    1.545000] async_tx: api initialized (async)
Nov 15 15:28:23 server kernel: [    1.575414] md: bind<sde1>
Nov 15 15:28:23 server kernel: [    1.590047] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[e1604000-e16047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 15 15:28:23 server kernel: [    1.605692] md: bind<sdd1>
Nov 15 15:28:23 server kernel: [    1.607011] md: bind<sdc1>
Nov 15 15:28:23 server kernel: [    1.672416] md: bind<sdb1>
Nov 15 15:28:23 server kernel: [    1.710014] raid6: int64x1   2150 MB/s
Nov 15 15:28:23 server kernel: [    1.880005] raid6: int64x2   2912 MB/s
Nov 15 15:28:23 server kernel: [    2.050009] raid6: int64x4   2135 MB/s
Nov 15 15:28:23 server kernel: [    2.211632] generic-usb 0003:051D:0002.0001: hiddev96,hidraw0: USB HID v1.10 Device [American Power Conversion Back-UPS NS 1050 FW:7.g2 .D USB FW:g2 ] on usb-0000:00:1a.1-2/input0
Nov 15 15:28:23 server kernel: [    2.211654] usbcore: registered new interface driver usbhid
Nov 15 15:28:23 server kernel: [    2.211656] usbhid: v2.6:USB HID core driver
Nov 15 15:28:23 server kernel: [    2.220010] raid6: int64x8   1875 MB/s
Nov 15 15:28:23 server kernel: [    2.390005] raid6: sse2x1    4600 MB/s
Nov 15 15:28:23 server kernel: [    2.560005] raid6: sse2x2    5359 MB/s
Nov 15 15:28:23 server kernel: [    2.730004] raid6: sse2x4    8293 MB/s
Nov 15 15:28:23 server kernel: [    2.730004] raid6: using algorithm sse2x4 (8293 MB/s)
Nov 15 15:28:23 server kernel: [    2.730849] xor: automatically using best checksumming function: generic_sse
Nov 15 15:28:23 server kernel: [    2.780004]    generic_sse: 10704.000 MB/sec
Nov 15 15:28:23 server kernel: [    2.780006] xor: using function: generic_sse (10704.000 MB/sec)
Nov 15 15:28:23 server kernel: [    2.783021] md: raid6 personality registered for level 6
Nov 15 15:28:23 server kernel: [    2.783022] md: raid5 personality registered for level 5
Nov 15 15:28:23 server kernel: [    2.783024] md: raid4 personality registered for level 4
Nov 15 15:28:23 server kernel: [    2.787218] md: raid10 personality registered for level 10
Nov 15 15:28:23 server kernel: [    2.798797] raid5: md0 is not clean -- starting background reconstruction
Nov 15 15:28:23 server kernel: [    2.798808] raid5: device sdb1 operational as raid disk 1
Nov 15 15:28:23 server kernel: [    2.798809] raid5: device sdc1 operational as raid disk 0
Nov 15 15:28:23 server kernel: [    2.798811] raid5: device sdd1 operational as raid disk 2
Nov 15 15:28:23 server kernel: [    2.798813] raid5: device sde1 operational as raid disk 3
Nov 15 15:28:23 server kernel: [    2.799131] raid5: allocated 4282kB for md0
Nov 15 15:28:23 server kernel: [    2.799224] 1: w=1 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
Nov 15 15:28:23 server kernel: [    2.799226] 0: w=2 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
Nov 15 15:28:23 server kernel: [    2.799228] 2: w=3 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
Nov 15 15:28:23 server kernel: [    2.799230] 3: w=4 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
Nov 15 15:28:23 server kernel: [    2.799232] raid5: raid level 5 set md0 active with 4 out of 4 devices, algorithm 2
Nov 15 15:28:23 server kernel: [    2.799233] RAID5 conf printout:
Nov 15 15:28:23 server kernel: [    2.799234]  --- rd:4 wd:4
Nov 15 15:28:23 server kernel: [    2.799236]  disk 0, o:1, dev:sdc1
Nov 15 15:28:23 server kernel: [    2.799238]  disk 1, o:1, dev:sdb1
Nov 15 15:28:23 server kernel: [    2.799239]  disk 2, o:1, dev:sdd1
Nov 15 15:28:23 server kernel: [    2.799240]  disk 3, o:1, dev:sde1
Nov 15 15:28:23 server kernel: [    2.799264] md0: detected capacity change from 0 to 3000606523392
Nov 15 15:28:23 server kernel: [    2.800577]  md0:
Nov 15 15:28:23 server kernel: [    2.800706] EXT3-fs: INFO: recovery required on readonly filesystem.
Nov 15 15:28:23 server kernel: [    2.800708] EXT3-fs: write access will be enabled during recovery.
Nov 15 15:28:23 server kernel: [    2.801099]  unknown partition table
Nov 15 15:28:23 server kernel: [    2.801904] md: resync of RAID array md0
Nov 15 15:28:23 server kernel: [    2.801906] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Nov 15 15:28:23 server kernel: [    2.801907] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
Nov 15 15:28:23 server kernel: [    2.801912] md: using 128k window, over a total of 976759936 blocks.
Nov 15 15:28:23 server kernel: [    4.649204] kjournald starting.  Commit interval 5 seconds
Nov 15 15:28:23 server kernel: [    4.649227] EXT3-fs: sda1: orphan cleanup on readonly fs
Nov 15 15:28:23 server kernel: [    4.649295] EXT3-fs: sda1: 5 orphan inodes deleted
Nov 15 15:28:23 server kernel: [    4.649297] EXT3-fs: recovery complete.
Nov 15 15:28:23 server kernel: [    4.655729] EXT3-fs: mounted filesystem with ordered data mode.
Nov 15 15:28:23 server kernel: [    7.150582] Adding 15623172k swap on /dev/sda5.  Priority:-1 extents:1 across:15623172k 
Nov 15 15:28:23 server kernel: [    7.873089] udev: starting version 151
Nov 15 15:28:23 server kernel: [    9.513909] type=1505 audit(1289852890.594:2):  operation="profile_load" pid=617 name="/sbin/dhclient3"
Nov 15 15:28:23 server kernel: [    9.514388] type=1505 audit(1289852890.594:3):  operation="profile_load" pid=617 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Nov 15 15:28:23 server kernel: [    9.514722] type=1505 audit(1289852890.594:4):  operation="profile_load" pid=617 name="/usr/lib/connman/scripts/dhclient-script"
Nov 15 15:28:23 server kernel: [    9.602204] lp: driver loaded but no devices found
Nov 15 15:28:23 server kernel: [    9.611007] agpgart-intel 0000:00:00.0: Intel G45/G43 Chipset
Nov 15 15:28:23 server kernel: [    9.611521] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
Nov 15 15:28:23 server kernel: [    9.630124] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Nov 15 15:28:23 server kernel: [   10.036762] it87: Found IT8718F chip at 0x290, revision 5
Nov 15 15:28:23 server kernel: [   10.036773] it87: in3 is VCC (+5V)
Nov 15 15:28:23 server kernel: [   10.216176] [drm] Initialized drm 1.1.0 20060810
Nov 15 15:28:23 server kernel: [   10.562759] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 15 15:28:23 server kernel: [   10.576103] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
Nov 15 15:28:23 server kernel: [   10.576107] [drm] MTRR allocation failed.  Graphics performance may suffer.
Nov 15 15:28:23 server kernel: [   10.576215] [drm] set up 31M of stolen space
Nov 15 15:28:23 server kernel: [   10.712619] type=1505 audit(1289852891.796:5):  operation="profile_load" pid=724 name="/usr/sbin/ntpd"
Nov 15 15:28:23 server kernel: [   10.836123] fb0: inteldrmfb frame buffer device
Nov 15 15:28:23 server kernel: [   10.836125] registered panic notifier
Nov 15 15:28:23 server kernel: [   10.836141] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Nov 15 15:28:23 server kernel: [   10.957587] EXT3 FS on sda1, internal journal
Nov 15 15:28:23 server kernel: [   11.043370] r8169: eth0: link up
Nov 15 15:28:23 server kernel: [   11.043379] r8169: eth0: link up
Nov 15 15:28:23 server kernel: [   11.197856] vga16fb: mapped to 0xffff8800000a0000
Nov 15 15:28:23 server kernel: [   11.197861] vga16fb: not registering due to another framebuffer present
Nov 15 15:28:23 server kernel: [   12.283729] Console: switching to colour frame buffer device 210x65
Nov 15 15:28:23 server kernel: [   12.734210] RPC: Registered udp transport module.
Nov 15 15:28:23 server kernel: [   12.734213] RPC: Registered tcp transport module.
Nov 15 15:28:23 server kernel: [   12.734214] RPC: Registered tcp NFSv4.1 backchannel transport module.
Nov 15 15:28:23 server kernel: [   13.520594] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Nov 15 15:28:23 server kernel: [   13.521421] SGI XFS Quota Management subsystem
Nov 15 15:28:23 server kernel: [   13.526517] Filesystem "md0": Disabling barriers, trial barrier write failed
Nov 15 15:28:23 server kernel: [   13.546871] XFS mounting filesystem md0
Nov 15 15:28:23 server kernel: [   14.649465] Starting XFS recovery on filesystem: md0 (logdev: internal)
Nov 15 15:28:23 server kernel: [   18.271366] Ending XFS recovery on filesystem: md0 (logdev: internal)
Nov 15 15:28:23 server kernel: [   18.737480] kjournald starting.  Commit interval 5 seconds
Nov 15 15:28:23 server kernel: [   18.764446] EXT3 FS on sda7, internal journal
Nov 15 15:28:23 server kernel: [   18.764452] EXT3-fs: mounted filesystem with ordered data mode.
Nov 15 15:28:23 server kernel: [   20.227122] kjournald starting.  Commit interval 5 seconds
Nov 15 15:28:23 server kernel: [   20.227421] EXT3 FS on sda6, internal journal
Nov 15 15:28:23 server kernel: [   20.227425] EXT3-fs: mounted filesystem with ordered data mode.
Nov 15 15:28:23 server kernel: [   21.884054] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Nov 15 15:28:23 server kernel: [   22.015053] type=1505 audit(1289852903.094:6):  operation="profile_replace" pid=1094 name="/sbin/dhclient3"
Nov 15 15:28:23 server kernel: [   22.015536] type=1505 audit(1289852903.094:7):  operation="profile_replace" pid=1094 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Nov 15 15:28:23 server kernel: [   22.015796] type=1505 audit(1289852903.094:8):  operation="profile_replace" pid=1094 name="/usr/lib/connman/scripts/dhclient-script"
Nov 15 15:28:23 server kernel: [   22.164165] type=1505 audit(1289852903.244:9):  operation="profile_load" pid=1096 name="/usr/bin/freshclam"
Nov 15 15:28:23 server kernel: [   22.238718] type=1505 audit(1289852903.314:10):  operation="profile_load" pid=1099 name="/usr/sbin/mysqld"
Nov 15 15:28:23 server kernel: [   22.286939] type=1505 audit(1289852903.364:11):  operation="profile_replace" pid=1100 name="/usr/sbin/ntpd"
Nov 15 15:28:23 server kernel: [   22.417864] type=1505 audit(1289852903.494:12):  operation="profile_load" pid=1101 name="/usr/sbin/slapd"
Nov 15 15:28:23 server kernel: [   22.464793] type=1505 audit(1289852903.544:13):  operation="profile_load" pid=1102 name="/usr/sbin/tcpdump"
Nov 15 15:28:26 server kernel: [   25.813203] type=1505 audit(1289852906.896:14):  operation="profile_replace" pid=1211 name="/usr/sbin/mysqld"
Nov 15 15:28:33 server kernel: [   32.486096] svc: failed to register lockdv1 RPC service (errno 97).
Nov 15 15:28:33 server kernel: [   32.488567] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Nov 15 15:28:33 server kernel: [   32.514054] NFSD: starting 90-second grace period
Nov 15 15:28:45 server kernel: [   44.566244] VBoxDrv: dbg - g_abExecMemory=ffffffffa03ccc80
Nov 15 15:28:45 server kernel: [   44.566258] vboxdrv: fAsync=0 offMin=0x1ae offMax=0x608
Nov 15 15:28:45 server kernel: [   44.566292] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Nov 15 15:28:53 server kernel: [   52.020857] ip_tables: (C) 2000-2006 Netfilter Core Team
```

Does this sound like an issue with the drive the swap partition is on?

I see that there was also nothing logged between yesterday at Nov 14 20:52:44 and today at Nov 15 15:28:23 (where I hard powered off, power button for 4 secs, and powered on a short time later).

I had noticed an issue last Friday where there were 444 processes listed in top.  Upon investigating, there were a huge number of CRON instances, and procs that were triggered by one of my cron jobs every 15 or 30 minutes.

---

### Post by talz13 on 2010-11-16
Ok, I just got up this morning and went to SSH into the server, and it's locked up again!  I need to figure this out, since my daily data collection jobs are not running, and my rss feeds aren't getting downloaded while the server is down...

---

### Post by TSJason on 2010-11-16
Yeah, the whole "swapper: page allocation failure. order:0, mode:0x4020" seems to be a problem with where swap is stored. 

Maybe try disabling that swap (in /etc/fstab) and putting up a virtual swap file somewhere else to test the theory: [http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

### Post by talz13 on 2010-11-16
Ok, I'm running a swap FILE on a different partition than the swap partition, and disabled automounting the swap partition on boot (fstab points to my swap file now).

Are there any kinds of diagnostics I can run on my disk to check it out?

---

### Post by talz13 on 2010-11-17
I ran 'badblocks' this morning, first on the partition that was being used as swap (/dev/sda5), then on the whole drive (/dev/sda):```
jeff@server:~$ sudo badblocks -v /dev/sda5
Checking blocks 0 to 15623180
Checking for bad blocks (read-only test): done
Pass completed, 0 bad blocks found.
jeff@server:~$ sudo badblocks -v /dev/sda
Checking blocks 0 to 625131863
Checking for bad blocks (read-only test): done
Pass completed, 0 bad blocks found.
jeff@server:~$
```Nothing came up with this, any other tests that I could do?

My hard drive setup is:
1x 640gb drive partitioned for root, swap, var:```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001c182

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14589   117186111   83  Linux
/dev/sda2           14590       77825   507943170    5  Extended
/dev/sda5           14590       16534    15623181   82  Linux swap / Solaris
/dev/sda6           16535       18358    14651248+  83  Linux
/dev/sda7           18359       77825   477668646   83  Linux
```

and 4x 1TB drives in a software raid 5 array, each set up the same way:```
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00081af5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect
```

and the /dev/md0 on the above raid 5 array where the home partition resides:```
Disk /dev/md0: 3000.6 GB, 3000606523392 bytes
2 heads, 4 sectors/track, 732569952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 196608 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```

---

### Post by talz13 on 2010-12-14
Well, it just happened again just this evening.  I was downloading with sabnzbd on the server, and viewing some pics in Lightroom on my desktop over the samba share, and suddenly the sabnzbd page stopped responding and my Lightroom marked all the images as "media offline".  I tried to SSH over and see if the server was down, and sure enough it was.

I walked over there and power cycled it again (power button for 4 sec.), and it came up fine after booting.  This time I didn't see anything suspicious in the syslog, and since my last post I moved my swap file to my RAID 5 array.  It was stable for about 3 weeks now, but the problem still persists.

Here's my syslog from today:```
Dec 14 06:47:14 server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="956" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Dec 14 06:55:01 server CRON[842]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 07:00:01 server CRON[863]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 07:00:01 server CRON[861]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 07:00:01 server CRON[864]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 07:00:01 server CRON[862]: (jeff) CMD (/home/jeff/scripts/fileInventory.sh    #Make file inventory listings for convenience, in case I need to re-download videos, etc.)
Dec 14 07:00:01 server CRON[866]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 07:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 07:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 07:00:01 server CRON[867]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 07:00:01 server slapd[1127]: connection_read(23): no connection!
Dec 14 07:00:01 server slapd[1127]: connection_read(23): no connection!
Dec 14 07:00:01 server slapd[1127]: connection_read(24): no connection!
Dec 14 07:00:01 server slapd[1127]: connection_read(24): no connection!
Dec 14 07:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 07:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 07:00:01 server slapd[1127]: connection_read(23): no connection!
Dec 14 07:00:01 server slapd[1127]: connection_read(23): no connection!
Dec 14 07:00:10 server slapd[1127]: connection_read(18): no connection!
Dec 14 07:05:01 server CRON[1167]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 07:09:01 server CRON[1295]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 07:15:01 server CRON[1847]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 07:17:01 server CRON[1856]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 07:20:01 server CRON[1866]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 07:20:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 07:20:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 07:25:01 server CRON[1897]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 07:30:01 server CRON[1917]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 07:30:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 07:30:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 07:35:01 server CRON[1937]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 07:39:01 server CRON[1948]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 07:40:01 server CRON[1960]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 07:40:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 07:40:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 07:45:01 server CRON[2043]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 07:55:01 server CRON[2076]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 08:00:01 server CRON[2094]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 08:00:01 server CRON[2095]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 08:00:01 server CRON[2096]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 08:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 08:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 08:00:01 server CRON[2097]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 08:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 08:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 08:00:01 server CRON[2099]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 08:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 08:01:17 server slapd[1127]: last message repeated 3 times
Dec 14 08:05:01 server CRON[2364]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 08:09:01 server CRON[2380]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 08:12:02 server ntpd[1457]: kernel time sync status change 6001
Dec 14 08:15:01 server CRON[2401]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 08:17:01 server CRON[2409]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 08:20:01 server CRON[2421]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 08:20:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 08:25:01 server CRON[2454]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 08:30:01 server CRON[2468]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 08:30:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 08:30:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 08:35:01 server CRON[2487]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 08:39:01 server CRON[2502]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 08:40:01 server CRON[2512]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 08:40:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 08:45:01 server CRON[2542]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 08:45:29 server dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 192.168.1.1 port 67
Dec 14 08:45:29 server dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Dec 14 08:45:29 server dhclient: bound to 192.168.1.2 -- renewal in 35344 seconds.
Dec 14 08:55:01 server CRON[2586]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 09:00:01 server CRON[2607]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 09:00:01 server CRON[2608]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 09:00:01 server CRON[2606]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 09:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 09:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 09:00:01 server CRON[2611]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 09:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 09:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 09:00:01 server CRON[2614]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 09:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 09:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 09:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 09:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 09:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 09:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 09:05:01 server CRON[2877]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 09:09:01 server CRON[2889]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 09:15:01 server CRON[2911]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 09:17:01 server CRON[2920]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 09:20:01 server CRON[2929]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 09:20:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 09:25:01 server CRON[2962]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 09:30:01 server CRON[2976]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 09:30:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 09:30:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 09:35:01 server CRON[2993]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 09:39:01 server CRON[3007]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 09:40:01 server CRON[3020]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 09:40:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 09:45:01 server CRON[3050]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 09:54:30 server ntpd[1457]: kernel time sync status change 2001
Dec 14 09:55:01 server CRON[3076]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 10:00:01 server CRON[3094]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 10:00:01 server CRON[3095]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 10:00:01 server CRON[3093]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 10:00:01 server CRON[3096]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 10:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 10:00:01 server slapd[1127]: last message repeated 3 times
Dec 14 10:00:01 server CRON[3099]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 10:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 10:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 10:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 10:01:23 server slapd[1127]: last message repeated 3 times
Dec 14 10:05:01 server CRON[3366]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 10:09:01 server CRON[3380]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 10:15:01 server CRON[3400]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 10:17:01 server CRON[3410]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 10:20:01 server CRON[3419]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 10:20:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 10:25:01 server CRON[3450]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 10:30:01 server CRON[3465]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 10:30:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 10:30:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 10:35:01 server CRON[3483]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 10:39:01 server CRON[3495]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 10:40:01 server CRON[3505]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 10:40:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 10:45:01 server CRON[3537]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 10:55:01 server CRON[3560]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 11:00:01 server CRON[3580]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 11:00:01 server CRON[3581]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 11:00:01 server CRON[3582]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 11:00:01 server CRON[3583]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 11:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 11:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 11:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 11:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 11:00:01 server CRON[3584]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 11:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 11:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 11:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 11:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 11:00:10 server slapd[1127]: connection_read(25): no connection!
Dec 14 11:00:10 server slapd[1127]: connection_read(25): no connection!
Dec 14 11:05:01 server CRON[3850]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 11:09:01 server CRON[3864]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 11:15:01 server CRON[3884]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 11:17:01 server CRON[3892]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 11:19:52 server ntpd[1457]: kernel time sync status change 6001
Dec 14 11:20:01 server CRON[3901]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 11:20:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 11:20:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 11:20:08 server slapd[1127]: connection_read(18): no connection!
Dec 14 11:20:08 server slapd[1127]: connection_read(18): no connection!
Dec 14 11:25:01 server CRON[3939]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 11:30:01 server CRON[3954]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 11:30:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 11:30:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 11:35:01 server CRON[3974]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 11:36:55 server ntpd[1457]: kernel time sync status change 2001
Dec 14 11:39:01 server CRON[3986]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 11:40:01 server CRON[3996]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 11:40:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 11:45:01 server CRON[4027]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 11:55:01 server CRON[4052]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 12:00:01 server CRON[4070]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 12:00:01 server CRON[4071]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 12:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 12:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 12:00:01 server CRON[4072]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 12:00:01 server CRON[4074]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 12:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 12:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 12:00:01 server CRON[4075]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 12:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 12:01:29 server slapd[1127]: last message repeated 5 times
Dec 14 12:05:01 server CRON[4342]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 12:09:01 server CRON[4353]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 12:15:01 server CRON[4374]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 12:17:01 server CRON[4385]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 12:20:01 server CRON[4398]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 12:20:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 12:20:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 12:25:01 server CRON[4433]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 12:30:01 server CRON[4453]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 12:30:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 12:30:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 12:35:01 server CRON[4477]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 12:39:01 server CRON[4492]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 12:40:01 server CRON[4505]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 12:40:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 12:45:01 server CRON[4540]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 12:55:01 server CRON[4576]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 13:00:01 server CRON[4598]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 13:00:01 server CRON[4599]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 13:00:01 server CRON[4600]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 13:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 13:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 13:00:01 server CRON[4601]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 13:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 13:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 13:00:01 server CRON[4603]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 13:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 13:01:02 server slapd[1127]: last message repeated 5 times
Dec 14 13:05:01 server CRON[4938]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 13:09:01 server CRON[4955]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 13:15:01 server CRON[5202]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 13:17:01 server CRON[5212]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 13:20:01 server CRON[5227]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 13:20:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 13:20:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 13:25:01 server CRON[5262]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 13:30:01 server CRON[5280]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 13:30:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 13:30:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 13:35:01 server CRON[5302]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 13:39:01 server CRON[5313]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 13:40:02 server CRON[5323]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 13:40:02 server slapd[1127]: connection_read(26): no connection!
Dec 14 13:45:01 server CRON[5355]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 13:55:01 server CRON[5379]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 14:00:01 server CRON[5399]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 14:00:01 server CRON[5400]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 14:00:01 server CRON[5398]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 14:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 14:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 14:00:01 server CRON[5401]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 14:00:01 server slapd[1127]: connection_read(27): no connection!
Dec 14 14:00:01 server slapd[1127]: connection_read(27): no connection!
Dec 14 14:00:01 server CRON[5405]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 14:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 14:01:04 server slapd[1127]: last message repeated 5 times
Dec 14 14:05:01 server CRON[5668]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 14:09:01 server CRON[5680]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 14:15:01 server CRON[5702]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 14:17:01 server CRON[5710]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 14:20:01 server CRON[5719]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 14:20:02 server slapd[1127]: connection_read(26): no connection!
Dec 14 14:20:02 server slapd[1127]: connection_read(26): no connection!
Dec 14 14:25:01 server CRON[5753]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 14:30:01 server CRON[5766]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 14:30:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 14:35:01 server CRON[5783]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 14:39:01 server CRON[5797]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 14:40:01 server CRON[5807]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 14:40:02 server slapd[1127]: connection_read(26): no connection!
Dec 14 14:40:02 server slapd[1127]: connection_read(26): no connection!
Dec 14 14:45:01 server CRON[5837]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 14:55:01 server CRON[5865]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 15:00:01 server CRON[5882]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 15:00:01 server CRON[5884]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 15:00:01 server CRON[5883]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 15:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 15:00:01 server slapd[1127]: last message repeated 3 times
Dec 14 15:00:01 server CRON[5896]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 15:00:01 server CRON[5897]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 15:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 15:01:07 server slapd[1127]: last message repeated 3 times
Dec 14 15:01:44 server ntpd[1457]: kernel time sync status change 6001
Dec 14 15:05:02 server CRON[6155]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 15:09:01 server CRON[6167]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 15:15:02 server CRON[6187]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 15:17:01 server CRON[6197]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 15:18:47 server ntpd[1457]: kernel time sync status change 2001
Dec 14 15:20:02 server CRON[6207]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 15:20:03 server slapd[1127]: connection_read(26): no connection!
Dec 14 15:20:03 server slapd[1127]: connection_read(26): no connection!
Dec 14 15:25:01 server CRON[6238]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 15:30:01 server CRON[6253]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 15:30:02 server slapd[1127]: connection_read(26): no connection!
Dec 14 15:30:02 server slapd[1127]: connection_read(26): no connection!
Dec 14 15:35:01 server CRON[6272]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 15:39:01 server CRON[6283]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 15:40:01 server CRON[6293]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 15:40:02 server slapd[1127]: connection_read(26): no connection!
Dec 14 15:40:02 server slapd[1127]: connection_read(26): no connection!
Dec 14 15:45:01 server CRON[6325]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 15:55:01 server CRON[6351]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 16:00:01 server CRON[6370]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 16:00:01 server CRON[6369]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 16:00:01 server CRON[6371]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 16:00:01 server CRON[6373]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 16:00:01 server CRON[6372]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 16:00:01 server slapd[1127]: connection_read(27): no connection!
Dec 14 16:00:01 server slapd[1127]: connection_read(27): no connection!
Dec 14 16:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 16:00:01 server slapd[1127]: last message repeated 3 times
Dec 14 16:00:01 server slapd[1127]: connection_read(27): no connection!
Dec 14 16:00:01 server slapd[1127]: connection_read(27): no connection!
Dec 14 16:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 16:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 16:01:23 server slapd[1127]: connection_read(26): no connection!
Dec 14 16:01:23 server slapd[1127]: connection_read(26): no connection!
Dec 14 16:05:02 server CRON[6639]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 16:09:02 server CRON[6653]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 16:15:02 server CRON[6674]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 16:17:01 server CRON[6682]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 16:20:02 server CRON[6691]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 16:20:03 server slapd[1127]: connection_read(26): no connection!
Dec 14 16:20:03 server slapd[1127]: connection_read(26): no connection!
Dec 14 16:25:02 server CRON[6724]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 16:30:01 server CRON[6737]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 16:30:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 16:30:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 16:35:02 server CRON[6757]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 16:39:01 server CRON[6768]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 16:40:01 server CRON[6777]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 16:45:02 server CRON[6807]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 16:55:01 server CRON[6833]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 17:00:01 server CRON[6853]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 17:00:01 server CRON[6854]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 17:00:01 server CRON[6852]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 17:00:01 server CRON[6855]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 17:00:01 server CRON[6857]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 17:00:02 server slapd[1127]: connection_read(29): no connection!
Dec 14 17:00:02 server slapd[1127]: connection_read(29): no connection!
Dec 14 17:00:02 server slapd[1127]: connection_read(27): no connection!
Dec 14 17:00:02 server slapd[1127]: connection_read(28): no connection!
Dec 14 17:00:02 server slapd[1127]: connection_read(27): no connection!
Dec 14 17:00:02 server slapd[1127]: connection_read(28): no connection!
Dec 14 17:00:02 server slapd[1127]: connection_read(26): no connection!
Dec 14 17:01:10 server slapd[1127]: last message repeated 4 times
Dec 14 17:01:10 server slapd[1127]: connection_read(26): no connection!
Dec 14 17:05:01 server CRON[7123]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 17:09:01 server CRON[7135]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 17:15:01 server CRON[7157]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 17:17:01 server CRON[7166]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 17:20:01 server CRON[7298]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 17:20:01 server slapd[1127]: connection_read(28): no connection!
Dec 14 17:20:01 server slapd[1127]: connection_read(28): no connection!
Dec 14 17:20:22 server slapd[1127]: connection_read(27): no connection!
Dec 14 17:20:22 server slapd[1127]: connection_read(27): no connection!
Dec 14 17:20:22 server slapd[1127]: connection_read(26): no connection!
Dec 14 17:20:22 server slapd[1127]: connection_read(26): no connection!
Dec 14 17:25:01 server CRON[7332]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 17:30:01 server CRON[7347]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 17:30:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 17:30:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 17:35:01 server CRON[7365]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 17:39:01 server CRON[7379]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 17:40:01 server CRON[7388]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 17:40:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 17:40:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 17:45:01 server CRON[7418]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 17:52:29 server ntpd[1457]: kernel time sync status change 6001
Dec 14 17:55:01 server CRON[7444]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 18:00:01 server CRON[7463]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 18:00:01 server CRON[7464]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 18:00:01 server CRON[7462]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 18:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 18:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 18:00:01 server CRON[7465]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 18:00:01 server slapd[1127]: connection_read(27): no connection!
Dec 14 18:00:01 server slapd[1127]: connection_read(27): no connection!
Dec 14 18:00:01 server CRON[7468]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 18:00:01 server slapd[1127]: connection_read(28): no connection!
Dec 14 18:00:01 server slapd[1127]: connection_read(28): no connection!
Dec 14 18:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 18:01:17 server slapd[1127]: last message repeated 3 times
Dec 14 18:05:01 server CRON[7734]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 18:09:01 server CRON[7746]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 18:09:32 server ntpd[1457]: kernel time sync status change 2001
Dec 14 18:15:01 server CRON[7768]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 18:17:01 server CRON[7775]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 18:20:01 server CRON[7787]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 18:20:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 18:25:01 server CRON[7817]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 18:30:01 server CRON[7831]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 18:30:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 18:30:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 18:34:33 server dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 192.168.1.1 port 67
Dec 14 18:34:33 server dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Dec 14 18:34:33 server dhclient: bound to 192.168.1.2 -- renewal in 32381 seconds.
Dec 14 18:35:01 server CRON[7864]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 18:39:01 server CRON[7876]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 18:40:01 server CRON[7885]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 18:40:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 18:45:01 server CRON[7918]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 18:55:01 server CRON[7941]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 19:00:01 server CRON[7962]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 19:00:01 server CRON[7963]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 19:00:01 server CRON[7961]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 19:00:01 server CRON[7964]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 19:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 19:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 19:00:01 server slapd[1127]: connection_read(27): no connection!
Dec 14 19:00:01 server slapd[1127]: connection_read(27): no connection!
Dec 14 19:00:01 server CRON[7969]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 19:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 19:00:01 server slapd[1127]: connection_read(27): no connection!
Dec 14 19:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 19:00:01 server slapd[1127]: connection_read(27): no connection!
Dec 14 19:00:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 19:00:45 server slapd[1127]: last message repeated 3 times
Dec 14 19:00:45 server ntpd[1457]: kernel time sync status change 6001
Dec 14 19:05:01 server CRON[8231]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 19:09:01 server CRON[8242]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 19:15:01 server CRON[8265]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 19:17:01 server CRON[8272]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 19:20:01 server CRON[8282]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 19:20:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 19:20:01 server slapd[1127]: connection_read(26): no connection!
Dec 14 19:22:24 server slapd[1127]: connection_read(18): no connection!
Dec 14 19:22:24 server slapd[1127]: connection_read(18): no connection!
Dec 14 19:22:51 server slapd[1127]: connection_read(25): no connection!
Dec 14 19:22:51 server slapd[1127]: connection_read(25): no connection!
Dec 14 19:25:01 server CRON[8319]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 19:30:01 server CRON[8333]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 19:30:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 19:30:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 19:35:01 server CRON[8350]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 19:39:01 server CRON[8364]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 19:40:01 server CRON[8374]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 19:40:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 19:45:01 server CRON[8404]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 19:55:01 server CRON[8430]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 20:00:01 server CRON[8447]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 20:00:01 server CRON[8448]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 20:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 20:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 20:00:01 server CRON[8449]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 20:00:01 server CRON[8450]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 20:00:01 server CRON[8453]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 20:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 20:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 20:00:09 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:00:09 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:05:01 server CRON[8720]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 20:09:01 server CRON[8732]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 20:15:01 server CRON[8754]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 20:16:56 server avahi-daemon[1116]: Invalid query packet.
Dec 14 20:16:59 server avahi-daemon[1116]: last message repeated 2 times
Dec 14 20:16:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:17:01 server slapd[1127]: last message repeated 3 times
Dec 14 20:17:01 server CRON[8764]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 20:19:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:19:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:20:01 server CRON[8775]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 20:20:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:22:58 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:24:23 server slapd[1127]: last message repeated 3 times
Dec 14 20:25:01 server CRON[8808]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 20:25:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:25:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:28:58 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:30:01 server slapd[1127]: last message repeated 3 times
Dec 14 20:30:01 server CRON[8827]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 20:30:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:30:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:31:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:31:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:34:58 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:35:01 server slapd[1127]: last message repeated 3 times
Dec 14 20:35:01 server CRON[8850]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 20:37:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:37:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:39:01 server CRON[8864]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 20:40:01 server CRON[8874]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 20:40:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:41:24 server slapd[1127]: last message repeated 2 times
Dec 14 20:43:13 server ntpd[1457]: kernel time sync status change 2001
Dec 14 20:43:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:43:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:45:01 server CRON[8910]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 20:46:58 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:48:24 server slapd[1127]: last message repeated 3 times
Dec 14 20:52:58 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:54:25 server slapd[1127]: last message repeated 3 times
Dec 14 20:55:01 server CRON[8951]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 20:55:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:55:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:58:58 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:00:01 server slapd[1127]: last message repeated 3 times
Dec 14 21:00:01 server CRON[8973]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 21:00:01 server CRON[8974]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 21:00:01 server CRON[8976]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 21:00:01 server CRON[8975]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 21:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 21:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 21:00:01 server CRON[8978]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 21:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 21:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 21:00:10 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:00:10 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:01:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:01:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:04:58 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:04:58 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:05:01 server CRON[9247]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 21:07:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:09:01 server CRON[9263]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 21:10:58 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:12:26 server slapd[1127]: last message repeated 3 times
Dec 14 21:13:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:13:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:15:02 server CRON[9289]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 21:20:03 server kernel: imklog 4.2.0, log source = /proc/kmsg started.
Dec 14 21:20:03 server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1052" x-info="http://www.rsyslog.com"] (re)start
Dec 14 21:20:03 server rsyslogd: rsyslogd's groupid changed to 102
Dec 14 21:20:03 server rsyslogd: rsyslogd's userid changed to 101
Dec 14 21:20:03 server rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Dec 14 21:20:03 server kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 14 21:20:03 server kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 14 21:20:03 server kernel: [    0.000000] Linux version 2.6.32-26-server (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #48-Ubuntu SMP Wed Nov 24 10:28:32 UTC 2010 (Ubuntu 2.6.32-26.48-server 2.6.32.24+drm33.11)
Dec 14 21:20:03 server kernel: [    0.000000] Command line: root=UUID=44862d65-d880-4f88-9d4c-8e5e08a7242a ro quiet splash 
Dec 14 21:20:03 server kernel: [    0.000000] KERNEL supported cpus:
Dec 14 21:20:03 server kernel: [    0.000000]   Intel GenuineIntel
Dec 14 21:20:03 server kernel: [    0.000000]   AMD AuthenticAMD
Dec 14 21:20:03 server kernel: [    0.000000]   Centaur CentaurHauls
Dec 14 21:20:03 server kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bdce0000 (usable)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 00000000bdce0000 - 00000000bdce3000 (ACPI NVS)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 00000000bdce3000 - 00000000bdcf0000 (ACPI data)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 00000000bdcf0000 - 00000000bdd00000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 00000000c0000000 - 00000000d0000000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Dec 14 21:20:03 server kernel: [    0.000000] DMI 2.4 present.
Dec 14 21:20:03 server kernel: [    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
Dec 14 21:20:03 server kernel: [    0.000000] MTRR default type: uncachable
Dec 14 21:20:03 server kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 14 21:20:03 server kernel: [    0.000000]   00000-9FFFF write-back
Dec 14 21:20:03 server kernel: [    0.000000]   A0000-BFFFF uncachable
Dec 14 21:20:03 server kernel: [    0.000000]   C0000-CBFFF write-protect
Dec 14 21:20:03 server kernel: [    0.000000]   CC000-EFFFF uncachable
Dec 14 21:20:03 server kernel: [    0.000000]   F0000-FFFFF write-through
Dec 14 21:20:03 server kernel: [    0.000000] MTRR variable ranges enabled:
Dec 14 21:20:03 server kernel: [    0.000000]   0 base 000000000 mask F00000000 write-back
Dec 14 21:20:03 server kernel: [    0.000000]   1 base 0C0000000 mask FC0000000 uncachable
Dec 14 21:20:03 server kernel: [    0.000000]   2 base 0BE000000 mask FFE000000 uncachable
Dec 14 21:20:03 server kernel: [    0.000000]   3 base 0BDE00000 mask FFFE00000 uncachable
Dec 14 21:20:03 server kernel: [    0.000000]   4 base 100000000 mask FC0000000 write-back
Dec 14 21:20:03 server kernel: [    0.000000]   5 base 0BDD00000 mask FFFF00000 uncachable
Dec 14 21:20:03 server kernel: [    0.000000]   6 disabled
Dec 14 21:20:03 server kernel: [    0.000000]   7 disabled
Dec 14 21:20:03 server kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 14 21:20:03 server kernel: [    0.000000] e820 update range: 00000000bdd00000 - 0000000100000000 (usable) ==> (reserved)
Dec 14 21:20:03 server kernel: [    0.000000] last_pfn = 0xbdce0 max_arch_pfn = 0x400000000
Dec 14 21:20:03 server kernel: [    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
Dec 14 21:20:03 server kernel: [    0.000000] Scanning 1 areas for low memory corruption
Dec 14 21:20:03 server kernel: [    0.000000] modified physical RAM map:
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 0000000000100000 - 00000000bdce0000 (usable)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 00000000bdce0000 - 00000000bdce3000 (ACPI NVS)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 00000000bdce3000 - 00000000bdcf0000 (ACPI data)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 00000000bdcf0000 - 00000000bdd00000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 00000000c0000000 - 00000000d0000000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
Dec 14 21:20:03 server kernel: [    0.000000] initial memory mapped : 0 - 20000000
Dec 14 21:20:03 server kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bdce0000
Dec 14 21:20:03 server kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 14 21:20:03 server kernel: [    0.000000]  0000000000 - 00bdc00000 page 2M
Dec 14 21:20:03 server kernel: [    0.000000]  00bdc00000 - 00bdce0000 page 4k
Dec 14 21:20:03 server kernel: [    0.000000] kernel direct mapping tables up to bdce0000 @ 8000-d000
Dec 14 21:20:03 server kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
Dec 14 21:20:03 server kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 14 21:20:03 server kernel: [    0.000000]  0100000000 - 0140000000 page 2M
Dec 14 21:20:03 server kernel: [    0.000000] kernel direct mapping tables up to 140000000 @ b000-11000
Dec 14 21:20:03 server kernel: [    0.000000] RAMDISK: 377d2000 - 37fef196
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: RSDP 00000000000f70d0 00014 (v00 GBT   )
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: RSDT 00000000bdce3040 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: FACP 00000000bdce30c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: DSDT 00000000bdce3180 04526 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: FACS 00000000bdce0000 00040
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: HPET 00000000bdce7800 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: MCFG 00000000bdce7880 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: APIC 00000000bdce7700 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: SSDT 00000000bdce7f20 003AB (v01  PmRef    CpuPm 00003000 INTL 20040311)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 14 21:20:03 server kernel: [    0.000000] No NUMA configuration found
Dec 14 21:20:03 server kernel: [    0.000000] Faking a node at 0000000000000000-0000000140000000
Dec 14 21:20:03 server kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
Dec 14 21:20:03 server kernel: [    0.000000]   NODE_DATA [000000000000c000 - 0000000000010fff]
Dec 14 21:20:03 server kernel: [    0.000000]   bootmap [0000000000011000 -  0000000000038fff] pages 28
Dec 14 21:20:03 server kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
Dec 14 21:20:03 server kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Dec 14 21:20:03 server kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Dec 14 21:20:03 server kernel: [    0.000000]   #2 [0001000000 - 0001a4caa4]    TEXT DATA BSS ==> [0001000000 - 0001a4caa4]
Dec 14 21:20:03 server kernel: [    0.000000]   #3 [00377d2000 - 0037fef196]          RAMDISK ==> [00377d2000 - 0037fef196]
Dec 14 21:20:03 server kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Dec 14 21:20:03 server kernel: [    0.000000]   #5 [0001a4d000 - 0001a4d0f6]              BRK ==> [0001a4d000 - 0001a4d0f6]
Dec 14 21:20:03 server kernel: [    0.000000]   #6 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
Dec 14 21:20:03 server kernel: [    0.000000]   #7 [000000b000 - 000000c000]          PGTABLE ==> [000000b000 - 000000c000]
Dec 14 21:20:03 server kernel: [    0.000000] found SMP MP-table at [ffff8800000f56e0] f56e0
Dec 14 21:20:03 server kernel: [    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880001c00000-ffff8800053fffff] on node 0
Dec 14 21:20:03 server kernel: [    0.000000] Zone PFN ranges:
Dec 14 21:20:03 server kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Dec 14 21:20:03 server kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Dec 14 21:20:03 server kernel: [    0.000000]   Normal   0x00100000 -> 0x00140000
Dec 14 21:20:03 server kernel: [    0.000000] Movable zone start PFN for each node
Dec 14 21:20:03 server kernel: [    0.000000] early_node_map[4] active PFN ranges
Dec 14 21:20:03 server kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
Dec 14 21:20:03 server kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Dec 14 21:20:03 server kernel: [    0.000000]     0: 0x00000100 -> 0x000bdce0
Dec 14 21:20:03 server kernel: [    0.000000]     0: 0x00100000 -> 0x00140000
Dec 14 21:20:03 server kernel: [    0.000000] On node 0 totalpages: 1039482
Dec 14 21:20:03 server kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Dec 14 21:20:03 server kernel: [    0.000000]   DMA zone: 103 pages reserved
Dec 14 21:20:03 server kernel: [    0.000000]   DMA zone: 3835 pages, LIFO batch:0
Dec 14 21:20:03 server kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Dec 14 21:20:03 server kernel: [    0.000000]   DMA32 zone: 759064 pages, LIFO batch:31
Dec 14 21:20:03 server kernel: [    0.000000]   Normal zone: 3584 pages used for memmap
Dec 14 21:20:03 server kernel: [    0.000000]   Normal zone: 258560 pages, LIFO batch:31
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 14 21:20:03 server kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 14 21:20:03 server kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Dec 14 21:20:03 server kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Dec 14 21:20:03 server kernel: [    0.000000] nr_irqs_gsi: 24
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000bdce0000 - 00000000bdce3000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000bdce3000 - 00000000bdcf0000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000bdcf0000 - 00000000bdd00000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000bdd00000 - 00000000c0000000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000d0000000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fec00000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Dec 14 21:20:03 server kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ec00000)
Dec 14 21:20:03 server kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 14 21:20:03 server kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Dec 14 21:20:03 server kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880005600000 s91544 r8192 d23144 u524288
Dec 14 21:20:03 server kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
Dec 14 21:20:03 server kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Dec 14 21:20:03 server kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1021459
Dec 14 21:20:03 server kernel: [    0.000000] Policy zone: Normal
Dec 14 21:20:03 server kernel: [    0.000000] Kernel command line: root=UUID=44862d65-d880-4f88-9d4c-8e5e08a7242a ro quiet splash 
Dec 14 21:20:03 server kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Dec 14 21:20:03 server kernel: [    0.000000] Initializing CPU#0
Dec 14 21:20:03 server kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Dec 14 21:20:03 server kernel: [    0.000000] Checking aperture...
Dec 14 21:20:03 server kernel: [    0.000000] No AGP bridge found
Dec 14 21:20:03 server kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Dec 14 21:20:03 server kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Dec 14 21:20:03 server kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Dec 14 21:20:03 server kernel: [    0.000000] Placing 64MB software IO TLB between ffff88000579e000 - ffff88000979e000
Dec 14 21:20:03 server kernel: [    0.000000] software IO TLB at phys 0x579e000 - 0x979e000
Dec 14 21:20:03 server kernel: [    0.000000] Memory: 4014864k/5242880k available (5511k kernel code, 1084952k absent, 143064k reserved, 3085k data, 796k init)
Dec 14 21:20:03 server kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Dec 14 21:20:03 server kernel: [    0.000000] Hierarchical RCU implementation.
Dec 14 21:20:03 server kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
Dec 14 21:20:03 server kernel: [    0.000000] Console: colour VGA+ 80x25
Dec 14 21:20:03 server kernel: [    0.000000] console [tty0] enabled
Dec 14 21:20:03 server kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Dec 14 21:20:03 server kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 14 21:20:03 server kernel: [    0.000000] hpet clockevent registered
Dec 14 21:20:03 server kernel: [    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Dec 14 21:20:03 server kernel: [    0.000000] Fast TSC calibration using PIT
Dec 14 21:20:03 server kernel: [    0.000000] Detected 2800.392 MHz processor.
Dec 14 21:20:03 server kernel: [    0.000005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5600.78 BogoMIPS (lpj=28003920)
Dec 14 21:20:03 server kernel: [    0.000026] Security Framework initialized
Dec 14 21:20:03 server kernel: [    0.000043] AppArmor: AppArmor initialized
Dec 14 21:20:03 server kernel: [    0.010234] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Dec 14 21:20:03 server kernel: [    0.011888] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Dec 14 21:20:03 server kernel: [    0.012652] Mount-cache hash table entries: 256
Dec 14 21:20:03 server kernel: [    0.012782] Initializing cgroup subsys ns
Dec 14 21:20:03 server kernel: [    0.012787] Initializing cgroup subsys cpuacct
Dec 14 21:20:03 server kernel: [    0.012790] Initializing cgroup subsys memory
Dec 14 21:20:03 server kernel: [    0.012795] Initializing cgroup subsys devices
Dec 14 21:20:03 server kernel: [    0.012797] Initializing cgroup subsys freezer
Dec 14 21:20:03 server kernel: [    0.012799] Initializing cgroup subsys net_cls
Dec 14 21:20:03 server kernel: [    0.012817] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 14 21:20:03 server kernel: [    0.012818] CPU: L2 cache: 2048K
Dec 14 21:20:03 server kernel: [    0.012821] CPU 0/0x0 -> Node 0
Dec 14 21:20:03 server kernel: [    0.012823] CPU: Physical Processor ID: 0
Dec 14 21:20:03 server kernel: [    0.012824] CPU: Processor Core ID: 0
Dec 14 21:20:03 server kernel: [    0.012826] mce: CPU supports 6 MCE banks
Dec 14 21:20:03 server kernel: [    0.012833] CPU0: Thermal monitoring enabled (TM2)
Dec 14 21:20:03 server kernel: [    0.012837] using mwait in idle threads.
Dec 14 21:20:03 server kernel: [    0.012838] Performance Events: Core2 events, Intel PMU driver.
Dec 14 21:20:03 server kernel: [    0.012843] ... version:                2
Dec 14 21:20:03 server kernel: [    0.012844] ... bit width:              40
Dec 14 21:20:03 server kernel: [    0.012846] ... generic registers:      2
Dec 14 21:20:03 server kernel: [    0.012847] ... value mask:             000000ffffffffff
Dec 14 21:20:03 server kernel: [    0.012848] ... max period:             000000007fffffff
Dec 14 21:20:03 server kernel: [    0.012849] ... fixed-purpose events:   3
Dec 14 21:20:03 server kernel: [    0.012850] ... event mask:             0000000700000003
Dec 14 21:20:03 server kernel: [    0.014948] ACPI: Core revision 20090903
Dec 14 21:20:03 server kernel: [    0.020022] ftrace: converting mcount calls to 0f 1f 44 00 00
Dec 14 21:20:03 server kernel: [    0.020030] ftrace: allocating 22834 entries in 90 pages
Dec 14 21:20:03 server kernel: [    0.027745] Setting APIC routing to flat
Dec 14 21:20:03 server kernel: [    0.028048] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 14 21:20:03 server kernel: [    0.128977] CPU0: Intel Pentium(R) Dual-Core  CPU      E6300  @ 2.80GHz stepping 0a
Dec 14 21:20:03 server kernel: [    0.130000] Booting processor 1 APIC 0x1 ip 0x6000
Dec 14 21:20:03 server kernel: [    0.010000] Initializing CPU#1
Dec 14 21:20:03 server kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 14 21:20:03 server kernel: [    0.010000] CPU: L2 cache: 2048K
Dec 14 21:20:03 server kernel: [    0.010000] CPU 1/0x1 -> Node 0
Dec 14 21:20:03 server kernel: [    0.010000] CPU: Physical Processor ID: 0
Dec 14 21:20:03 server kernel: [    0.010000] CPU: Processor Core ID: 1
Dec 14 21:20:03 server kernel: [    0.010000] CPU1: Thermal monitoring enabled (TM2)
Dec 14 21:20:03 server kernel: [    0.280059] CPU1: Intel Pentium(R) Dual-Core  CPU      E6300  @ 2.80GHz stepping 0a
Dec 14 21:20:03 server kernel: [    0.280065] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec 14 21:20:03 server kernel: [    0.290018] Brought up 2 CPUs
Dec 14 21:20:03 server kernel: [    0.290020] Total of 2 processors activated (11200.97 BogoMIPS).
Dec 14 21:20:03 server kernel: [    0.290423] CPU0 attaching sched-domain:
Dec 14 21:20:03 server kernel: [    0.290426]  domain 0: span 0-1 level MC
Dec 14 21:20:03 server kernel: [    0.290428]   groups: 0 1
Dec 14 21:20:03 server kernel: [    0.290433] CPU1 attaching sched-domain:
Dec 14 21:20:03 server kernel: [    0.290434]  domain 0: span 0-1 level MC
Dec 14 21:20:03 server kernel: [    0.290436]   groups: 1 0
Dec 14 21:20:03 server kernel: [    0.290502] devtmpfs: initialized
Dec 14 21:20:03 server kernel: [    0.292276] regulator: core version 0.5
Dec 14 21:20:03 server kernel: [    0.292276] Time:  2:19:43  Date: 12/15/10
Dec 14 21:20:03 server kernel: [    0.292276] NET: Registered protocol family 16
Dec 14 21:20:03 server kernel: [    0.292276] ACPI: bus type pci registered
Dec 14 21:20:03 server kernel: [    0.292276] PCI: MCFG configuration 0: base c0000000 segment 0 buses 0 - 255
Dec 14 21:20:03 server kernel: [    0.292276] PCI: MCFG area at c0000000 reserved in E820
Dec 14 21:20:03 server kernel: [    0.295384] PCI: Using MMCONFIG at c0000000 - cfffffff
Dec 14 21:20:03 server kernel: [    0.295386] PCI: Using configuration type 1 for base access
Dec 14 21:20:03 server kernel: [    0.295998] Trying to unpack rootfs image as initramfs...
Dec 14 21:20:03 server kernel: [    0.296038] bio: create slab <bio-0> at 0
Dec 14 21:20:03 server kernel: [    0.296524] ACPI: EC: Look up EC in DSDT
Dec 14 21:20:03 server kernel: [    0.304155] ACPI: Interpreter enabled
Dec 14 21:20:03 server kernel: [    0.304161] ACPI: (supports S0 S3 S4 S5)
Dec 14 21:20:03 server kernel: [    0.304178] ACPI: Using IOAPIC for interrupt routing
Dec 14 21:20:03 server kernel: [    0.307443] ACPI: No dock devices found.
Dec 14 21:20:03 server kernel: [    0.307525] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 14 21:20:03 server kernel: [    0.307593] pci 0000:00:02.0: reg 10 64bit mmio: [0xe1000000-0xe13fffff]
Dec 14 21:20:03 server kernel: [    0.307598] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xd0000000-0xdfffffff]
Dec 14 21:20:03 server kernel: [    0.307602] pci 0000:00:02.0: reg 20 io port: [0xd300-0xd307]
Dec 14 21:20:03 server kernel: [    0.307634] pci 0000:00:02.1: reg 10 64bit mmio: [0xe1400000-0xe14fffff]
Dec 14 21:20:03 server kernel: [    0.307708] pci 0000:00:1a.0: reg 20 io port: [0xd000-0xd01f]
Dec 14 21:20:03 server kernel: [    0.307767] pci 0000:00:1a.1: reg 20 io port: [0xd100-0xd11f]
Dec 14 21:20:03 server kernel: [    0.307824] pci 0000:00:1a.2: reg 20 io port: [0xd200-0xd21f]
Dec 14 21:20:03 server kernel: [    0.307875] pci 0000:00:1a.7: reg 10 32bit mmio: [0xe1701000-0xe17013ff]
Dec 14 21:20:03 server kernel: [    0.307961] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Dec 14 21:20:03 server kernel: [    0.307964] pci 0000:00:1c.0: PME# disabled
Dec 14 21:20:03 server kernel: [    0.308019] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Dec 14 21:20:03 server kernel: [    0.308022] pci 0000:00:1c.5: PME# disabled
Dec 14 21:20:03 server kernel: [    0.308069] pci 0000:00:1d.0: reg 20 io port: [0xd400-0xd41f]
Dec 14 21:20:03 server kernel: [    0.308127] pci 0000:00:1d.1: reg 20 io port: [0xd500-0xd51f]
Dec 14 21:20:03 server kernel: [    0.308185] pci 0000:00:1d.2: reg 20 io port: [0xd600-0xd61f]
Dec 14 21:20:03 server kernel: [    0.308237] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe1700000-0xe17003ff]
Dec 14 21:20:03 server kernel: [    0.308415] pci 0000:00:1f.2: reg 10 io port: [0xd700-0xd707]
Dec 14 21:20:03 server kernel: [    0.308419] pci 0000:00:1f.2: reg 14 io port: [0xd800-0xd803]
Dec 14 21:20:03 server kernel: [    0.308424] pci 0000:00:1f.2: reg 18 io port: [0xd900-0xd907]
Dec 14 21:20:03 server kernel: [    0.308428] pci 0000:00:1f.2: reg 1c io port: [0xda00-0xda03]
Dec 14 21:20:03 server kernel: [    0.308433] pci 0000:00:1f.2: reg 20 io port: [0xdb00-0xdb0f]
Dec 14 21:20:03 server kernel: [    0.308437] pci 0000:00:1f.2: reg 24 io port: [0xdc00-0xdc0f]
Dec 14 21:20:03 server kernel: [    0.308475] pci 0000:00:1f.3: reg 10 64bit mmio: [0xe1702000-0xe17020ff]
Dec 14 21:20:03 server kernel: [    0.308486] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
Dec 14 21:20:03 server kernel: [    0.308523] pci 0000:00:1f.5: reg 10 io port: [0xde00-0xde07]
Dec 14 21:20:03 server kernel: [    0.308528] pci 0000:00:1f.5: reg 14 io port: [0xdf00-0xdf03]
Dec 14 21:20:03 server kernel: [    0.308532] pci 0000:00:1f.5: reg 18 io port: [0xe000-0xe007]
Dec 14 21:20:03 server kernel: [    0.308537] pci 0000:00:1f.5: reg 1c io port: [0xe100-0xe103]
Dec 14 21:20:03 server kernel: [    0.308541] pci 0000:00:1f.5: reg 20 io port: [0xe200-0xe20f]
Dec 14 21:20:03 server kernel: [    0.308545] pci 0000:00:1f.5: reg 24 io port: [0xe300-0xe30f]
Dec 14 21:20:03 server kernel: [    0.308644] pci 0000:02:00.0: reg 10 io port: [0xc000-0xc0ff]
Dec 14 21:20:03 server kernel: [    0.308662] pci 0000:02:00.0: reg 18 64bit mmio pref: [0xe1510000-0xe1510fff]
Dec 14 21:20:03 server kernel: [    0.308674] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xe1500000-0xe150ffff]
Dec 14 21:20:03 server kernel: [    0.308682] pci 0000:02:00.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
Dec 14 21:20:03 server kernel: [    0.308717] pci 0000:02:00.0: supports D1 D2
Dec 14 21:20:03 server kernel: [    0.308718] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 21:20:03 server kernel: [    0.308722] pci 0000:02:00.0: PME# disabled
Dec 14 21:20:03 server kernel: [    0.308770] pci 0000:00:1c.5: bridge io port: [0xc000-0xcfff]
Dec 14 21:20:03 server kernel: [    0.308773] pci 0000:00:1c.5: bridge 32bit mmio: [0xe0000000-0xe0ffffff]
Dec 14 21:20:03 server kernel: [    0.308778] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xe1500000-0xe15fffff]
Dec 14 21:20:03 server kernel: [    0.308815] pci 0000:03:07.0: reg 10 32bit mmio: [0xe1604000-0xe16047ff]
Dec 14 21:20:03 server kernel: [    0.308821] pci 0000:03:07.0: reg 14 32bit mmio: [0xe1600000-0xe1603fff]
Dec 14 21:20:03 server kernel: [    0.308859] pci 0000:03:07.0: supports D1 D2
Dec 14 21:20:03 server kernel: [    0.308860] pci 0000:03:07.0: PME# supported from D0 D1 D2 D3hot
Dec 14 21:20:03 server kernel: [    0.308864] pci 0000:03:07.0: PME# disabled
Dec 14 21:20:03 server kernel: [    0.308896] pci 0000:00:1e.0: transparent bridge
Dec 14 21:20:03 server kernel: [    0.308900] pci 0000:00:1e.0: bridge 32bit mmio: [0xe1600000-0xe16fffff]
Dec 14 21:20:03 server kernel: [    0.308917] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 14 21:20:03 server kernel: [    0.309036] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Dec 14 21:20:03 server kernel: [    0.309083] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
Dec 14 21:20:03 server kernel: [    0.309119] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Dec 14 21:20:03 server kernel: [    0.322240] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Dec 14 21:20:03 server kernel: [    0.322316] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Dec 14 21:20:03 server kernel: [    0.322388] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Dec 14 21:20:03 server kernel: [    0.322460] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 *15)
Dec 14 21:20:03 server kernel: [    0.322531] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Dec 14 21:20:03 server kernel: [    0.322603] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Dec 14 21:20:03 server kernel: [    0.322676] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Dec 14 21:20:03 server kernel: [    0.322747] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 12 *14 15)
Dec 14 21:20:03 server kernel: [    0.322838] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Dec 14 21:20:03 server kernel: [    0.322850] vgaarb: loaded
Dec 14 21:20:03 server kernel: [    0.322932] SCSI subsystem initialized
Dec 14 21:20:03 server kernel: [    0.323057] libata version 3.00 loaded.
Dec 14 21:20:03 server kernel: [    0.323061] usbcore: registered new interface driver usbfs
Dec 14 21:20:03 server kernel: [    0.323072] usbcore: registered new interface driver hub
Dec 14 21:20:03 server kernel: [    0.323094] usbcore: registered new device driver usb
Dec 14 21:20:03 server kernel: [    0.323195] ACPI: WMI: Mapper loaded
Dec 14 21:20:03 server kernel: [    0.323197] PCI: Using ACPI for IRQ routing
Dec 14 21:20:03 server kernel: [    0.323325] NetLabel: Initializing
Dec 14 21:20:03 server kernel: [    0.323326] NetLabel:  domain hash size = 128
Dec 14 21:20:03 server kernel: [    0.323327] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 14 21:20:03 server kernel: [    0.323338] NetLabel:  unlabeled traffic allowed by default
Dec 14 21:20:03 server kernel: [    0.323363] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Dec 14 21:20:03 server kernel: [    0.323367] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Dec 14 21:20:03 server kernel: [    0.330032] Switching to clocksource tsc
Dec 14 21:20:03 server kernel: [    0.331384] AppArmor: AppArmor Filesystem Enabled
Dec 14 21:20:03 server kernel: [    0.331399] pnp: PnP ACPI init
Dec 14 21:20:03 server kernel: [    0.331414] ACPI: bus type pnp registered
Dec 14 21:20:03 server kernel: [    0.333027] pnp: PnP ACPI: found 11 devices
Dec 14 21:20:03 server kernel: [    0.333029] ACPI: ACPI bus type pnp unregistered
Dec 14 21:20:03 server kernel: [    0.333039] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Dec 14 21:20:03 server kernel: [    0.333041] system 00:01: ioport range 0x290-0x29f has been reserved
Dec 14 21:20:03 server kernel: [    0.333043] system 00:01: ioport range 0x800-0x87f has been reserved
Dec 14 21:20:03 server kernel: [    0.333045] system 00:01: ioport range 0x290-0x294 has been reserved
Dec 14 21:20:03 server kernel: [    0.333047] system 00:01: ioport range 0x880-0x88f has been reserved
Dec 14 21:20:03 server kernel: [    0.333049] system 00:01: ioport range 0x4c0-0x4ff could not be reserved
Dec 14 21:20:03 server kernel: [    0.333054] system 00:07: ioport range 0x400-0x4bf has been reserved
Dec 14 21:20:03 server kernel: [    0.333058] system 00:08: iomem range 0xc0000000-0xcfffffff has been reserved
Dec 14 21:20:03 server kernel: [    0.333062] system 00:09: iomem range 0xcc600-0xcffff has been reserved
Dec 14 21:20:03 server kernel: [    0.333064] system 00:09: iomem range 0xf0000-0xf7fff could not be reserved
Dec 14 21:20:03 server kernel: [    0.333066] system 00:09: iomem range 0xf8000-0xfbfff could not be reserved
Dec 14 21:20:03 server kernel: [    0.333068] system 00:09: iomem range 0xfc000-0xfffff could not be reserved
Dec 14 21:20:03 server kernel: [    0.333070] system 00:09: iomem range 0xbdce0000-0xbdcfffff could not be reserved
Dec 14 21:20:03 server kernel: [    0.333072] system 00:09: iomem range 0x0-0x9ffff could not be reserved
Dec 14 21:20:03 server kernel: [    0.333074] system 00:09: iomem range 0x100000-0xbdcdffff could not be reserved
Dec 14 21:20:03 server kernel: [    0.333076] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
Dec 14 21:20:03 server kernel: [    0.333078] system 00:09: iomem range 0xfed10000-0xfed1dfff has been reserved
Dec 14 21:20:03 server kernel: [    0.333080] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
Dec 14 21:20:03 server kernel: [    0.333082] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
Dec 14 21:20:03 server kernel: [    0.333084] system 00:09: iomem range 0xffb00000-0xffb7ffff has been reserved
Dec 14 21:20:03 server kernel: [    0.333086] system 00:09: iomem range 0xfff00000-0xffffffff has been reserved
Dec 14 21:20:03 server kernel: [    0.333088] system 00:09: iomem range 0xe0000-0xeffff has been reserved
Dec 14 21:20:03 server kernel: [    0.337767] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
Dec 14 21:20:03 server kernel: [    0.337771] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
Dec 14 21:20:03 server kernel: [    0.337775] pci 0000:00:1c.0:   MEM window: 0xe1800000-0xe19fffff
Dec 14 21:20:03 server kernel: [    0.337778] pci 0000:00:1c.0:   PREFETCH window: 0x000000e1a00000-0x000000e1bfffff
Dec 14 21:20:03 server kernel: [    0.337783] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
Dec 14 21:20:03 server kernel: [    0.337786] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
Dec 14 21:20:03 server kernel: [    0.337789] pci 0000:00:1c.5:   MEM window: 0xe0000000-0xe0ffffff
Dec 14 21:20:03 server kernel: [    0.337792] pci 0000:00:1c.5:   PREFETCH window: 0x000000e1500000-0x000000e15fffff
Dec 14 21:20:03 server kernel: [    0.337797] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Dec 14 21:20:03 server kernel: [    0.337799] pci 0000:00:1e.0:   IO window: disabled
Dec 14 21:20:03 server kernel: [    0.337802] pci 0000:00:1e.0:   MEM window: 0xe1600000-0xe16fffff
Dec 14 21:20:03 server kernel: [    0.337805] pci 0000:00:1e.0:   PREFETCH window: disabled
Dec 14 21:20:03 server kernel: [    0.337818]   alloc irq_desc for 16 on node -1
Dec 14 21:20:03 server kernel: [    0.337820]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    0.337825] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 14 21:20:03 server kernel: [    0.337829] pci 0000:00:1c.0: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.337835]   alloc irq_desc for 17 on node -1
Dec 14 21:20:03 server kernel: [    0.337837]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    0.337839] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec 14 21:20:03 server kernel: [    0.337842] pci 0000:00:1c.5: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.337847] pci 0000:00:1e.0: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.337851] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Dec 14 21:20:03 server kernel: [    0.337853] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Dec 14 21:20:03 server kernel: [    0.337854] pci_bus 0000:01: resource 0 io:  [0x1000-0x1fff]
Dec 14 21:20:03 server kernel: [    0.337856] pci_bus 0000:01: resource 1 mem: [0xe1800000-0xe19fffff]
Dec 14 21:20:03 server kernel: [    0.337858] pci_bus 0000:01: resource 2 pref mem [0xe1a00000-0xe1bfffff]
Dec 14 21:20:03 server kernel: [    0.337860] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
Dec 14 21:20:03 server kernel: [    0.337861] pci_bus 0000:02: resource 1 mem: [0xe0000000-0xe0ffffff]
Dec 14 21:20:03 server kernel: [    0.337863] pci_bus 0000:02: resource 2 pref mem [0xe1500000-0xe15fffff]
Dec 14 21:20:03 server kernel: [    0.337865] pci_bus 0000:03: resource 1 mem: [0xe1600000-0xe16fffff]
Dec 14 21:20:03 server kernel: [    0.337866] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
Dec 14 21:20:03 server kernel: [    0.337868] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
Dec 14 21:20:03 server kernel: [    0.337899] NET: Registered protocol family 2
Dec 14 21:20:03 server kernel: [    0.338036] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 14 21:20:03 server kernel: [    0.338985] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Dec 14 21:20:03 server kernel: [    0.342494] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Dec 14 21:20:03 server kernel: [    0.342907] TCP: Hash tables configured (established 524288 bind 65536)
Dec 14 21:20:03 server kernel: [    0.342909] TCP reno registered
Dec 14 21:20:03 server kernel: [    0.343020] NET: Registered protocol family 1
Dec 14 21:20:03 server kernel: [    0.343036] pci 0000:00:02.0: Boot video device
Dec 14 21:20:03 server kernel: [    0.343330] Scanning for low memory corruption every 60 seconds
Dec 14 21:20:03 server kernel: [    0.343433] audit: initializing netlink socket (disabled)
Dec 14 21:20:03 server kernel: [    0.343446] type=2000 audit(1292379582.339:1): initialized
Dec 14 21:20:03 server kernel: [    0.350598] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 14 21:20:03 server kernel: [    0.351606] VFS: Disk quotas dquot_6.5.2
Dec 14 21:20:03 server kernel: [    0.351648] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Dec 14 21:20:03 server kernel: [    0.352072] fuse init (API version 7.13)
Dec 14 21:20:03 server kernel: [    0.352131] msgmni has been set to 7841
Dec 14 21:20:03 server kernel: [    0.352288] alg: No test for stdrng (krng)
Dec 14 21:20:03 server kernel: [    0.352330] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Dec 14 21:20:03 server kernel: [    0.352332] io scheduler noop registered
Dec 14 21:20:03 server kernel: [    0.352334] io scheduler anticipatory registered
Dec 14 21:20:03 server kernel: [    0.352335] io scheduler deadline registered (default)
Dec 14 21:20:03 server kernel: [    0.352359] io scheduler cfq registered
Dec 14 21:20:03 server kernel: [    0.352476]   alloc irq_desc for 24 on node -1
Dec 14 21:20:03 server kernel: [    0.352478]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    0.352486] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
Dec 14 21:20:03 server kernel: [    0.352493] pcieport 0000:00:1c.0: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.352583]   alloc irq_desc for 25 on node -1
Dec 14 21:20:03 server kernel: [    0.352585]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    0.352590] pcieport 0000:00:1c.5: irq 25 for MSI/MSI-X
Dec 14 21:20:03 server kernel: [    0.352596] pcieport 0000:00:1c.5: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.352660] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 14 21:20:03 server kernel: [    0.352721] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 14 21:20:03 server kernel: [    0.352793] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Dec 14 21:20:03 server kernel: [    0.352796] ACPI: Power Button [PWRB]
Dec 14 21:20:03 server kernel: [    0.352834] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Dec 14 21:20:03 server kernel: [    0.352836] ACPI: Power Button [PWRF]
Dec 14 21:20:03 server kernel: [    0.353233] ACPI: SSDT 00000000bdce7900 0026C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
Dec 14 21:20:03 server kernel: [    0.353365] Marking TSC unstable due to TSC halts in idle
Dec 14 21:20:03 server kernel: [    0.353418] processor LNXCPU:00: registered as cooling_device0
Dec 14 21:20:03 server kernel: [    0.353574] ACPI: SSDT 00000000bdce7dc0 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
Dec 14 21:20:03 server kernel: [    0.353714] processor LNXCPU:01: registered as cooling_device1
Dec 14 21:20:03 server kernel: [    0.356211] Linux agpgart interface v0.103
Dec 14 21:20:03 server kernel: [    0.356236] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Dec 14 21:20:03 server kernel: [    0.357140] brd: module loaded
Dec 14 21:20:03 server kernel: [    0.357479] loop: module loaded
Dec 14 21:20:03 server kernel: [    0.357548] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Dec 14 21:20:03 server kernel: [    0.357651] ata_piix 0000:00:1f.2: version 2.13
Dec 14 21:20:03 server kernel: [    0.357665]   alloc irq_desc for 19 on node -1
Dec 14 21:20:03 server kernel: [    0.357667]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    0.357673] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 14 21:20:03 server kernel: [    0.357677] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Dec 14 21:20:03 server kernel: [    0.357716] ata_piix 0000:00:1f.2: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.357780] scsi0 : ata_piix
Dec 14 21:20:03 server kernel: [    0.357830] scsi1 : ata_piix
Dec 14 21:20:03 server kernel: [    0.358409] ata1: SATA max UDMA/133 cmd 0xd700 ctl 0xd800 bmdma 0xdb00 irq 19
Dec 14 21:20:03 server kernel: [    0.358414] ata2: SATA max UDMA/133 cmd 0xd900 ctl 0xda00 bmdma 0xdb08 irq 19
Dec 14 21:20:03 server kernel: [    0.358434] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 14 21:20:03 server kernel: [    0.358437] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Dec 14 21:20:03 server kernel: [    0.358441] Switching to clocksource hpet
Dec 14 21:20:03 server kernel: [    0.358470] ata_piix 0000:00:1f.5: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.358599] scsi2 : ata_piix
Dec 14 21:20:03 server kernel: [    0.358661] scsi3 : ata_piix
Dec 14 21:20:03 server kernel: [    0.359085] ata3: SATA max UDMA/133 cmd 0xde00 ctl 0xdf00 bmdma 0xe200 irq 19
Dec 14 21:20:03 server kernel: [    0.359088] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xe100 bmdma 0xe208 irq 19
Dec 14 21:20:03 server kernel: [    0.359321] Fixed MDIO Bus: probed
Dec 14 21:20:03 server kernel: [    0.359345] PPP generic driver version 2.4.2
Dec 14 21:20:03 server kernel: [    0.359378] tun: Universal TUN/TAP device driver, 1.6
Dec 14 21:20:03 server kernel: [    0.359379] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 14 21:20:03 server kernel: [    0.359458] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 14 21:20:03 server kernel: [    0.359475]   alloc irq_desc for 18 on node -1
Dec 14 21:20:03 server kernel: [    0.359476]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    0.359480] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 14 21:20:03 server kernel: [    0.359501] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.359504] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Dec 14 21:20:03 server kernel: [    0.359528] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Dec 14 21:20:03 server kernel: [    0.363430] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Dec 14 21:20:03 server kernel: [    0.363448] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xe1701000
Dec 14 21:20:03 server kernel: [    0.391275] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Dec 14 21:20:03 server kernel: [    0.391382] usb usb1: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    0.391406] hub 1-0:1.0: USB hub found
Dec 14 21:20:03 server kernel: [    0.391414] hub 1-0:1.0: 6 ports detected
Dec 14 21:20:03 server kernel: [    0.391474]   alloc irq_desc for 23 on node -1
Dec 14 21:20:03 server kernel: [    0.391476]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    0.391483] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 14 21:20:03 server kernel: [    0.391503] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.391506] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 14 21:20:03 server kernel: [    0.391537] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Dec 14 21:20:03 server kernel: [    0.395434] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Dec 14 21:20:03 server kernel: [    0.395448] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe1700000
Dec 14 21:20:03 server kernel: [    0.411267] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Dec 14 21:20:03 server kernel: [    0.411367] usb usb2: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    0.411388] hub 2-0:1.0: USB hub found
Dec 14 21:20:03 server kernel: [    0.411395] hub 2-0:1.0: 6 ports detected
Dec 14 21:20:03 server kernel: [    0.411444] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 14 21:20:03 server kernel: [    0.411460] uhci_hcd: USB Universal Host Controller Interface driver
Dec 14 21:20:03 server kernel: [    0.411498] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 14 21:20:03 server kernel: [    0.411507] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.411510] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Dec 14 21:20:03 server kernel: [    0.411539] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Dec 14 21:20:03 server kernel: [    0.411573] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000d000
Dec 14 21:20:03 server kernel: [    0.411641] usb usb3: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    0.411658] hub 3-0:1.0: USB hub found
Dec 14 21:20:03 server kernel: [    0.411663] hub 3-0:1.0: 2 ports detected
Dec 14 21:20:03 server kernel: [    0.411697]   alloc irq_desc for 21 on node -1
Dec 14 21:20:03 server kernel: [    0.411698]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    0.411703] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Dec 14 21:20:03 server kernel: [    0.411707] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.411709] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Dec 14 21:20:03 server kernel: [    0.411734] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Dec 14 21:20:03 server kernel: [    0.411759] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d100
Dec 14 21:20:03 server kernel: [    0.411821] usb usb4: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    0.411842] hub 4-0:1.0: USB hub found
Dec 14 21:20:03 server kernel: [    0.411846] hub 4-0:1.0: 2 ports detected
Dec 14 21:20:03 server kernel: [    0.411876] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 14 21:20:03 server kernel: [    0.411881] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.411883] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Dec 14 21:20:03 server kernel: [    0.411912] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Dec 14 21:20:03 server kernel: [    0.411933] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000d200
Dec 14 21:20:03 server kernel: [    0.411996] usb usb5: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    0.412015] hub 5-0:1.0: USB hub found
Dec 14 21:20:03 server kernel: [    0.412019] hub 5-0:1.0: 2 ports detected
Dec 14 21:20:03 server kernel: [    0.412050] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 14 21:20:03 server kernel: [    0.412054] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.412057] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 14 21:20:03 server kernel: [    0.412080] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Dec 14 21:20:03 server kernel: [    0.412101] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
Dec 14 21:20:03 server kernel: [    0.412168] usb usb6: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    0.412185] hub 6-0:1.0: USB hub found
Dec 14 21:20:03 server kernel: [    0.412190] hub 6-0:1.0: 2 ports detected
Dec 14 21:20:03 server kernel: [    0.412225] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 14 21:20:03 server kernel: [    0.412230] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.412232] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 14 21:20:03 server kernel: [    0.412253] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Dec 14 21:20:03 server kernel: [    0.412273] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d500
Dec 14 21:20:03 server kernel: [    0.412332] usb usb7: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    0.412349] hub 7-0:1.0: USB hub found
Dec 14 21:20:03 server kernel: [    0.412355] hub 7-0:1.0: 2 ports detected
Dec 14 21:20:03 server kernel: [    0.412387] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 14 21:20:03 server kernel: [    0.412391] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.412393] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 14 21:20:03 server kernel: [    0.412415] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Dec 14 21:20:03 server kernel: [    0.412435] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d600
Dec 14 21:20:03 server kernel: [    0.412499] usb usb8: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    0.412517] hub 8-0:1.0: USB hub found
Dec 14 21:20:03 server kernel: [    0.412522] hub 8-0:1.0: 2 ports detected
Dec 14 21:20:03 server kernel: [    0.412589] PNP: No PS/2 controller found. Probing ports directly.
Dec 14 21:20:03 server kernel: [    0.412949] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 14 21:20:03 server kernel: [    0.412953] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 14 21:20:03 server kernel: [    0.413008] mice: PS/2 mouse device common for all mice
Dec 14 21:20:03 server kernel: [    0.413079] rtc_cmos 00:04: RTC can wake from S4
Dec 14 21:20:03 server kernel: [    0.413107] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Dec 14 21:20:03 server kernel: [    0.413128] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Dec 14 21:20:03 server kernel: [    0.413227] device-mapper: uevent: version 1.0.3
Dec 14 21:20:03 server kernel: [    0.413328] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Dec 14 21:20:03 server kernel: [    0.413376] device-mapper: multipath: version 1.1.0 loaded
Dec 14 21:20:03 server kernel: [    0.413378] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec 14 21:20:03 server kernel: [    0.413517] cpuidle: using governor ladder
Dec 14 21:20:03 server kernel: [    0.413558] cpuidle: using governor menu
Dec 14 21:20:03 server kernel: [    0.413809] TCP cubic registered
Dec 14 21:20:03 server kernel: [    0.413910] NET: Registered protocol family 10
Dec 14 21:20:03 server kernel: [    0.414233] lo: Disabled Privacy Extensions
Dec 14 21:20:03 server kernel: [    0.414433] NET: Registered protocol family 17
Dec 14 21:20:03 server kernel: [    0.415957] PM: Resume from disk failed.
Dec 14 21:20:03 server kernel: [    0.415968] registered taskstats version 1
Dec 14 21:20:03 server kernel: [    0.416257]   Magic number: 6:643:308
Dec 14 21:20:03 server kernel: [    0.416283] tty tty37: hash matches
Dec 14 21:20:03 server kernel: [    0.416340] rtc_cmos 00:04: setting system clock to 2010-12-15 02:19:43 UTC (1292379583)
Dec 14 21:20:03 server kernel: [    0.416342] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 14 21:20:03 server kernel: [    0.416343] EDD information not available.
Dec 14 21:20:03 server kernel: [    0.443841] Freeing initrd memory: 8308k freed
Dec 14 21:20:03 server kernel: [    0.730728] ata4: SATA link down (SStatus 0 SControl 300)
Dec 14 21:20:03 server kernel: [    0.880047] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 14 21:20:03 server kernel: [    0.903651] ata3.00: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
Dec 14 21:20:03 server kernel: [    0.903656] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 14 21:20:03 server kernel: [    0.920716] ata3.00: configured for UDMA/133
Dec 14 21:20:03 server kernel: [    0.990013] usb 4-1: new low speed USB device using uhci_hcd and address 2
Dec 14 21:20:03 server kernel: [    1.173880] usb 4-1: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    1.240063] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 14 21:20:03 server kernel: [    1.240077] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 14 21:20:03 server kernel: [    1.240247] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 14 21:20:03 server kernel: [    1.240258] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 14 21:20:03 server kernel: [    1.287501] ata2.00: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
Dec 14 21:20:03 server kernel: [    1.287506] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 14 21:20:03 server kernel: [    1.291627] ata2.01: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
Dec 14 21:20:03 server kernel: [    1.291632] ata2.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 14 21:20:03 server kernel: [    1.300192] ata1.00: HPA unlocked: 1250261615 -> 1250263728, native 1250263728
Dec 14 21:20:03 server kernel: [    1.300195] ata1.00: ATA-8: WDC WD6400AACS-00G8B1, 05.04C05, max UDMA/133
Dec 14 21:20:03 server kernel: [    1.300197] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 14 21:20:03 server kernel: [    1.318864] ata1.01: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
Dec 14 21:20:03 server kernel: [    1.318868] ata1.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 14 21:20:03 server kernel: [    1.320529] ata1.00: configured for UDMA/133
Dec 14 21:20:03 server kernel: [    1.320873] ata2.00: configured for UDMA/133
Dec 14 21:20:03 server kernel: [    1.341715] ata1.01: configured for UDMA/133
Dec 14 21:20:03 server kernel: [    1.341841] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400AACS-0 05.0 PQ: 0 ANSI: 5
Dec 14 21:20:03 server kernel: [    1.341969] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Dec 14 21:20:03 server kernel: [    1.341996] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 14 21:20:03 server kernel: [    1.342026] sd 0:0:0:0: [sda] Write Protect is off
Dec 14 21:20:03 server kernel: [    1.342028] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 14 21:20:03 server kernel: [    1.342046] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 14 21:20:03 server kernel: [    1.342076] scsi 0:0:1:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
Dec 14 21:20:03 server kernel: [    1.342145]  sda:
Dec 14 21:20:03 server kernel: [    1.342154] sd 0:0:1:0: Attached scsi generic sg1 type 0
Dec 14 21:20:03 server kernel: [    1.355174] sd 0:0:1:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec 14 21:20:03 server kernel: [    1.355177]  sda1 sda2 <
Dec 14 21:20:03 server kernel: [    1.362101] ata2.01: configured for UDMA/133
Dec 14 21:20:03 server kernel: [    1.362187] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
Dec 14 21:20:03 server kernel: [    1.362294] sd 1:0:0:0: Attached scsi generic sg2 type 0
Dec 14 21:20:03 server kernel: [    1.362316] sd 1:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec 14 21:20:03 server kernel: [    1.362358] scsi 1:0:1:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
Dec 14 21:20:03 server kernel: [    1.362363] sd 1:0:0:0: [sdc] Write Protect is off
Dec 14 21:20:03 server kernel: [    1.362365] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Dec 14 21:20:03 server kernel: [    1.362382] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 14 21:20:03 server kernel: [    1.362428] sd 1:0:1:0: Attached scsi generic sg3 type 0
Dec 14 21:20:03 server kernel: [    1.362482]  sdc:
Dec 14 21:20:03 server kernel: [    1.362495] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
Dec 14 21:20:03 server kernel: [    1.362564] sd 2:0:0:0: Attached scsi generic sg4 type 0
Dec 14 21:20:03 server kernel: [    1.362566] sd 2:0:0:0: [sde] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec 14 21:20:03 server kernel: [    1.362598] sd 2:0:0:0: [sde] Write Protect is off
Dec 14 21:20:03 server kernel: [    1.362600] sd 2:0:0:0: [sde] Mode Sense: 00 3a 00 00
Dec 14 21:20:03 server kernel: [    1.362625] sd 2:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 14 21:20:03 server kernel: [    1.362729]  sde: sde1
Dec 14 21:20:03 server kernel: [    1.366592] sd 2:0:0:0: [sde] Attached SCSI disk
Dec 14 21:20:03 server kernel: [    1.366925] sd 1:0:1:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec 14 21:20:03 server kernel: [    1.366928]  sdc1
Dec 14 21:20:03 server kernel: [    1.366980] sd 1:0:1:0: [sdd] Write Protect is off
Dec 14 21:20:03 server kernel: [    1.366983] sd 1:0:1:0: [sdd] Mode Sense: 00 3a 00 00
Dec 14 21:20:03 server kernel: [    1.367012] sd 1:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 14 21:20:03 server kernel: [    1.367150] sd 1:0:0:0: [sdc] Attached SCSI disk
Dec 14 21:20:03 server kernel: [    1.367164]  sdd: sda5 sdd1
Dec 14 21:20:03 server kernel: [    1.379565] sd 1:0:1:0: [sdd] Attached SCSI disk
Dec 14 21:20:03 server kernel: [    1.380631]  sda6
Dec 14 21:20:03 server kernel: [    1.380649] sd 0:0:1:0: [sdb] Write Protect is off
Dec 14 21:20:03 server kernel: [    1.380653] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Dec 14 21:20:03 server kernel: [    1.393360]  sda7
Dec 14 21:20:03 server kernel: [    1.393363] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 14 21:20:03 server kernel: [    1.393367]  >
Dec 14 21:20:03 server kernel: [    1.393587]  sdb: sdb1
Dec 14 21:20:03 server kernel: [    1.406837] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 14 21:20:03 server kernel: [    1.406842] sd 0:0:1:0: [sdb] Attached SCSI disk
Dec 14 21:20:03 server kernel: [    1.406859] Freeing unused kernel memory: 796k freed
Dec 14 21:20:03 server kernel: [    1.407092] Write protecting the kernel read-only data: 7804k
Dec 14 21:20:03 server kernel: [    1.417583] udev: starting version 151
Dec 14 21:20:03 server kernel: [    1.451313] usb 4-2: new low speed USB device using uhci_hcd and address 3
Dec 14 21:20:03 server kernel: [    1.459122] md: linear personality registered for level -1
Dec 14 21:20:03 server kernel: [    1.460832] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 14 21:20:03 server kernel: [    1.460851] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 14 21:20:03 server kernel: [    1.460893] r8169 0000:02:00.0: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    1.460932]   alloc irq_desc for 26 on node -1
Dec 14 21:20:03 server kernel: [    1.460934]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    1.460945] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
Dec 14 21:20:03 server kernel: [    1.461367] eth0: RTL8168c/8111c at 0xffffc9000065e000, 00:1f:d0:27:53:6d, XID 1c4000c0 IRQ 26
Dec 14 21:20:03 server kernel: [    1.482800] md: multipath personality registered for level -4
Dec 14 21:20:03 server kernel: [    1.487773] ohci1394 0000:03:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 14 21:20:03 server kernel: [    1.498407] usbcore: registered new interface driver hiddev
Dec 14 21:20:03 server kernel: [    1.505096] md: raid0 personality registered for level 0
Dec 14 21:20:03 server kernel: [    1.509337] md: raid1 personality registered for level 1
Dec 14 21:20:03 server kernel: [    1.510750] async_tx: api initialized (async)
Dec 14 21:20:03 server kernel: [    1.512057] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input3
Dec 14 21:20:03 server kernel: [    1.512124] generic-usb 0003:046D:C308.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1a.1-1/input0
Dec 14 21:20:03 server kernel: [    1.541377] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[e1604000-e16047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Dec 14 21:20:03 server kernel: [    1.552900] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.1/input/input4
Dec 14 21:20:03 server kernel: [    1.552984] generic-usb 0003:046D:C308.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:1a.1-1/input1
Dec 14 21:20:03 server kernel: [    1.553006] usbcore: registered new interface driver usbhid
Dec 14 21:20:03 server kernel: [    1.553008] usbhid: v2.6:USB HID core driver
Dec 14 21:20:03 server kernel: [    1.569757] md: bind<sde1>
Dec 14 21:20:03 server kernel: [    1.587749] md: bind<sdd1>
Dec 14 21:20:03 server kernel: [    1.589212] md: bind<sdc1>
Dec 14 21:20:03 server kernel: [    1.658983] md: bind<sdb1>
Dec 14 21:20:03 server kernel: [    1.680030] raid6: int64x1   2142 MB/s
Dec 14 21:20:03 server kernel: [    1.692863] usb 4-2: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    1.850023] raid6: int64x2   2916 MB/s
Dec 14 21:20:03 server kernel: [    2.020029] raid6: int64x4   2136 MB/s
Dec 14 21:20:03 server kernel: [    2.190034] raid6: int64x8   1842 MB/s
Dec 14 21:20:03 server kernel: [    2.323881] generic-usb 0003:051D:0002.0003: hiddev96,hidraw2: USB HID v1.10 Device [American Power Conversion Back-UPS NS 1050 FW:7.g2 .D USB FW:g2 ] on usb-0000:00:1a.1-2/input0
Dec 14 21:20:03 server kernel: [    2.360009] raid6: sse2x1    4603 MB/s
Dec 14 21:20:03 server kernel: [    2.530012] raid6: sse2x2    5446 MB/s
Dec 14 21:20:03 server kernel: [    2.700011] raid6: sse2x4    8293 MB/s
Dec 14 21:20:03 server kernel: [    2.700012] raid6: using algorithm sse2x4 (8293 MB/s)
Dec 14 21:20:03 server kernel: [    2.700856] xor: automatically using best checksumming function: generic_sse
Dec 14 21:20:03 server kernel: [    2.749986]    generic_sse: 10670.400 MB/sec
Dec 14 21:20:03 server kernel: [    2.750004] xor: using function: generic_sse (10670.400 MB/sec)
Dec 14 21:20:03 server kernel: [    2.753073] md: raid6 personality registered for level 6
Dec 14 21:20:03 server kernel: [    2.753075] md: raid5 personality registered for level 5
Dec 14 21:20:03 server kernel: [    2.753076] md: raid4 personality registered for level 4
Dec 14 21:20:03 server kernel: [    2.757278] md: raid10 personality registered for level 10
Dec 14 21:20:03 server kernel: [    2.770565] EXT3-fs: INFO: recovery required on readonly filesystem.
Dec 14 21:20:03 server kernel: [    2.770567] EXT3-fs: write access will be enabled during recovery.
Dec 14 21:20:03 server kernel: [    2.784491] raid5: md0 is not clean -- starting background reconstruction
Dec 14 21:20:03 server kernel: [    2.784499] raid5: device sdb1 operational as raid disk 1
Dec 14 21:20:03 server kernel: [    2.784500] raid5: device sdc1 operational as raid disk 0
Dec 14 21:20:03 server kernel: [    2.784501] raid5: device sdd1 operational as raid disk 2
Dec 14 21:20:03 server kernel: [    2.784503] raid5: device sde1 operational as raid disk 3
Dec 14 21:20:03 server kernel: [    2.784820] raid5: allocated 4282kB for md0
Dec 14 21:20:03 server kernel: [    2.784854] 1: w=1 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
Dec 14 21:20:03 server kernel: [    2.784856] 0: w=2 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
Dec 14 21:20:03 server kernel: [    2.784858] 2: w=3 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
Dec 14 21:20:03 server kernel: [    2.784860] 3: w=4 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
Dec 14 21:20:03 server kernel: [    2.784862] raid5: raid level 5 set md0 active with 4 out of 4 devices, algorithm 2
Dec 14 21:20:03 server kernel: [    2.784863] RAID5 conf printout:
Dec 14 21:20:03 server kernel: [    2.784864]  --- rd:4 wd:4
Dec 14 21:20:03 server kernel: [    2.784866]  disk 0, o:1, dev:sdc1
Dec 14 21:20:03 server kernel: [    2.784867]  disk 1, o:1, dev:sdb1
Dec 14 21:20:03 server kernel: [    2.784868]  disk 2, o:1, dev:sdd1
Dec 14 21:20:03 server kernel: [    2.784869]  disk 3, o:1, dev:sde1
Dec 14 21:20:03 server kernel: [    2.784893] md0: detected capacity change from 0 to 3000606523392
Dec 14 21:20:03 server kernel: [    2.784953] md: resync of RAID array md0
Dec 14 21:20:03 server kernel: [    2.784954] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Dec 14 21:20:03 server kernel: [    2.784956] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
Dec 14 21:20:03 server kernel: [    2.784960] md: using 128k window, over a total of 976759936 blocks.
Dec 14 21:20:03 server kernel: [    2.785768]  md0: unknown partition table
Dec 14 21:20:03 server kernel: [    2.860145] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[002ce08400001fd0]
Dec 14 21:20:03 server kernel: [    3.467837] kjournald starting.  Commit interval 5 seconds
Dec 14 21:20:03 server kernel: [    3.467861] EXT3-fs: sda1: orphan cleanup on readonly fs
Dec 14 21:20:03 server kernel: [    3.489523] ext3_orphan_cleanup: deleting unreferenced inode 7184496
Dec 14 21:20:03 server kernel: [    3.499710] ext3_orphan_cleanup: deleting unreferenced inode 7184484
Dec 14 21:20:03 server kernel: [    3.512350] ext3_orphan_cleanup: deleting unreferenced inode 2282240
Dec 14 21:20:03 server kernel: [    3.536649] ext3_orphan_cleanup: deleting unreferenced inode 5153063
Dec 14 21:20:03 server kernel: [    3.546935] ext3_orphan_cleanup: deleting unreferenced inode 5153062
Dec 14 21:20:03 server kernel: [    3.555393] ext3_orphan_cleanup: deleting unreferenced inode 5153059
Dec 14 21:20:03 server kernel: [    3.567755] ext3_orphan_cleanup: deleting unreferenced inode 5153058
Dec 14 21:20:03 server kernel: [    3.567766] ext3_orphan_cleanup: deleting unreferenced inode 5153057
Dec 14 21:20:03 server kernel: [    3.579435] ext3_orphan_cleanup: deleting unreferenced inode 5153038
Dec 14 21:20:03 server kernel: [    3.580724] ext3_orphan_cleanup: deleting unreferenced inode 5152995
Dec 14 21:20:03 server kernel: [    3.585220] ext3_orphan_cleanup: deleting unreferenced inode 5152991
Dec 14 21:20:03 server kernel: [    3.585372] ext3_orphan_cleanup: deleting unreferenced inode 5152933
Dec 14 21:20:03 server kernel: [    3.585542] ext3_orphan_cleanup: deleting unreferenced inode 5152922
Dec 14 21:20:03 server kernel: [    3.593877] ext3_orphan_cleanup: deleting unreferenced inode 5152899
Dec 14 21:20:03 server kernel: [    3.598926] ext3_orphan_cleanup: deleting unreferenced inode 5152821
Dec 14 21:20:03 server kernel: [    3.618047] ext3_orphan_cleanup: deleting unreferenced inode 2280274
Dec 14 21:20:03 server kernel: [    3.628571] ext3_orphan_cleanup: deleting unreferenced inode 2280077
Dec 14 21:20:03 server kernel: [    3.643035] ext3_orphan_cleanup: deleting unreferenced inode 2280071
Dec 14 21:20:03 server kernel: [    3.655641] ext3_orphan_cleanup: deleting unreferenced inode 2278129
Dec 14 21:20:03 server kernel: [    3.659689] ext3_orphan_cleanup: deleting unreferenced inode 1130506
Dec 14 21:20:03 server kernel: [    3.659704] ext3_orphan_cleanup: deleting unreferenced inode 1130505
Dec 14 21:20:03 server kernel: [    3.659711] ext3_orphan_cleanup: deleting unreferenced inode 1130504
Dec 14 21:20:03 server kernel: [    3.659718] ext3_orphan_cleanup: deleting unreferenced inode 1130503
Dec 14 21:20:03 server kernel: [    3.659725] ext3_orphan_cleanup: deleting unreferenced inode 1130502
Dec 14 21:20:03 server kernel: [    3.659904] ext3_orphan_cleanup: deleting unreferenced inode 5152959
Dec 14 21:20:03 server kernel: [    3.670260] ext3_orphan_cleanup: deleting unreferenced inode 5152850
Dec 14 21:20:03 server kernel: [    3.674303] EXT3-fs: sda1: 26 orphan inodes deleted
Dec 14 21:20:03 server kernel: [    3.674306] EXT3-fs: recovery complete.
Dec 14 21:20:03 server kernel: [    3.698090] EXT3-fs: mounted filesystem with ordered data mode.
Dec 14 21:20:03 server kernel: [    6.769538] udev: starting version 151
Dec 14 21:20:03 server kernel: [    8.405530] type=1505 audit(1292379591.483:2):  operation="profile_load" pid=586 name="/sbin/dhclient3"
Dec 14 21:20:03 server kernel: [    8.406009] type=1505 audit(1292379591.483:3):  operation="profile_load" pid=586 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Dec 14 21:20:03 server kernel: [    8.406265] type=1505 audit(1292379591.483:4):  operation="profile_load" pid=586 name="/usr/lib/connman/scripts/dhclient-script"
Dec 14 21:20:03 server kernel: [    8.498516] agpgart-intel 0000:00:00.0: Intel G45/G43 Chipset
Dec 14 21:20:03 server kernel: [    8.499026] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
Dec 14 21:20:03 server kernel: [    8.516977] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Dec 14 21:20:03 server kernel: [    8.519875] EXT3 FS on sda1, internal journal
Dec 14 21:20:03 server kernel: [    8.607895] lp: driver loaded but no devices found
Dec 14 21:20:03 server kernel: [    9.398150] it87: Found IT8718F chip at 0x290, revision 5
Dec 14 21:20:03 server kernel: [    9.398161] it87: in3 is VCC (+5V)
Dec 14 21:20:03 server kernel: [    9.985701] [drm] Initialized drm 1.1.0 20060810
Dec 14 21:20:03 server kernel: [   10.607997] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 14 21:20:03 server kernel: [   10.608001] i915 0000:00:02.0: setting latency timer to 64
Dec 14 21:20:03 server kernel: [   10.618749] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
Dec 14 21:20:03 server kernel: [   10.618753] [drm] MTRR allocation failed.  Graphics performance may suffer.
Dec 14 21:20:03 server kernel: [   10.619254]   alloc irq_desc for 27 on node -1
Dec 14 21:20:03 server kernel: [   10.619256]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [   10.619263] i915 0000:00:02.0: irq 27 for MSI/MSI-X
Dec 14 21:20:03 server kernel: [   10.619269] [drm] set up 31M of stolen space
Dec 14 21:20:03 server kernel: [   10.630272] type=1505 audit(1292379593.704:5):  operation="profile_load" pid=703 name="/usr/sbin/ntpd"
Dec 14 21:20:03 server kernel: [   10.832540] r8169: eth0: link up
Dec 14 21:20:03 server kernel: [   10.832546] r8169: eth0: link up
Dec 14 21:20:03 server kernel: [   10.864293] fb0: inteldrmfb frame buffer device
Dec 14 21:20:03 server kernel: [   10.864295] registered panic notifier
Dec 14 21:20:03 server kernel: [   10.864311] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Dec 14 21:20:03 server kernel: [   11.467746] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Dec 14 21:20:03 server kernel: [   11.468619] SGI XFS Quota Management subsystem
Dec 14 21:20:03 server kernel: [   11.475522] Filesystem "md0": Disabling barriers, trial barrier write failed
Dec 14 21:20:03 server kernel: [   11.522399] XFS mounting filesystem md0
Dec 14 21:20:03 server kernel: [   11.550743] vga16fb: initializing
Dec 14 21:20:03 server kernel: [   11.550747] vga16fb: mapped to 0xffff8800000a0000
Dec 14 21:20:03 server kernel: [   11.550750] vga16fb: not registering due to another framebuffer present
Dec 14 21:20:03 server kernel: [   12.034903] Console: switching to colour frame buffer device 210x65
Dec 14 21:20:03 server kernel: [   12.127241] Starting XFS recovery on filesystem: md0 (logdev: internal)
Dec 14 21:20:03 server kernel: [   12.292546] RPC: Registered udp transport module.
Dec 14 21:20:03 server kernel: [   12.292549] RPC: Registered tcp transport module.
Dec 14 21:20:03 server kernel: [   12.292550] RPC: Registered tcp NFSv4.1 backchannel transport module.
Dec 14 21:20:03 server kernel: [   15.406958] Ending XFS recovery on filesystem: md0 (logdev: internal)
Dec 14 21:20:03 server kernel: [   15.761401] Adding 4194296k swap on /home/swap/swapfile.  Priority:-1 extents:2 across:4339384k 
Dec 14 21:20:03 server kernel: [   16.145884] kjournald starting.  Commit interval 5 seconds
Dec 14 21:20:03 server kernel: [   16.146239] EXT3 FS on sda7, internal journal
Dec 14 21:20:03 server kernel: [   16.146244] EXT3-fs: mounted filesystem with ordered data mode.
Dec 14 21:20:03 server kernel: [   18.849099] kjournald starting.  Commit interval 5 seconds
Dec 14 21:20:03 server kernel: [   18.849378] EXT3 FS on sda6, internal journal
Dec 14 21:20:03 server kernel: [   18.849382] EXT3-fs: mounted filesystem with ordered data mode.
Dec 14 21:20:03 server kernel: [   20.497753] type=1505 audit(1292379603.573:6):  operation="profile_replace" pid=1066 name="/sbin/dhclient3"
Dec 14 21:20:03 server kernel: [   20.498243] type=1505 audit(1292379603.573:7):  operation="profile_replace" pid=1066 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Dec 14 21:20:03 server kernel: [   20.498503] type=1505 audit(1292379603.573:8):  operation="profile_replace" pid=1066 name="/usr/lib/connman/scripts/dhclient-script"
Dec 14 21:20:03 server kernel: [   20.632840] type=1505 audit(1292379603.714:9):  operation="profile_load" pid=1067 name="/usr/bin/freshclam"
Dec 14 21:20:03 server kernel: [   20.676606] type=1505 audit(1292379603.754:10):  operation="profile_load" pid=1069 name="/usr/sbin/mysqld"
Dec 14 21:20:03 server kernel: [   20.722185] type=1505 audit(1292379603.804:11):  operation="profile_replace" pid=1074 name="/usr/sbin/ntpd"
Dec 14 21:20:03 server kernel: [   20.889281] type=1505 audit(1292379603.963:12):  operation="profile_load" pid=1075 name="/usr/sbin/slapd"
Dec 14 21:20:04 server kernel: [   20.943291] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Dec 14 21:20:04 server kernel: [   20.973109] type=1505 audit(1292379604.053:13):  operation="profile_load" pid=1076 name="/usr/sbin/tcpdump"
Dec 14 21:20:04 server kernel: [   21.060011] eth0: no IPv6 routers present
Dec 14 21:20:05 server cron[1121]: (CRON) INFO (pidfile fd = 3)
Dec 14 21:20:05 server acpid: starting up with proc fs
Dec 14 21:20:05 server init: apport pre-start process (1117) terminated with status 1
Dec 14 21:20:05 server init: apport post-stop process (1140) terminated with status 1
Dec 14 21:20:05 server cron[1146]: (CRON) STARTUP (fork ok)
Dec 14 21:20:06 server acpid: 1 rule loaded
Dec 14 21:20:06 server acpid: waiting for events: event logging is off
Dec 14 21:20:06 server cron[1146]: (CRON) INFO (Running @reboot jobs)
Dec 14 21:20:06 server avahi-daemon[1184]: Found user 'avahi' (UID 107) and group 'avahi' (GID 116).
Dec 14 21:20:06 server avahi-daemon[1184]: Successfully dropped root privileges.
Dec 14 21:20:06 server avahi-daemon[1184]: avahi-daemon 0.6.25 starting up.
Dec 14 21:20:06 server avahi-daemon[1184]: Successfully called chroot().
Dec 14 21:20:06 server avahi-daemon[1184]: Successfully dropped remaining capabilities.
Dec 14 21:20:06 server avahi-daemon[1184]: No service file found in /etc/avahi/services.
Dec 14 21:20:07 server avahi-daemon[1184]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Dec 14 21:20:07 server avahi-daemon[1184]: New relevant interface eth0.IPv4 for mDNS.
Dec 14 21:20:07 server avahi-daemon[1184]: Network interface enumeration completed.
Dec 14 21:20:07 server avahi-daemon[1184]: Registering new address record for fe80::21f:d0ff:fe27:536d on eth0.*.
Dec 14 21:20:07 server avahi-daemon[1184]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Dec 14 21:20:07 server avahi-daemon[1184]: Registering HINFO record with values 'X86_64'/'LINUX'.
Dec 14 21:20:07 server slapd[1170]: @(#) $OpenLDAP: slapd 2.4.21 (Aug 10 2010 17:08:36) $#012#011buildd@yellow:/build/buildd/openldap-2.4.21/debian/build/servers/slapd
Dec 14 21:20:07 server kernel: [   24.335325] type=1505 audit(1292379607.414:14):  operation="profile_replace" pid=1186 name="/usr/sbin/mysqld"
Dec 14 21:20:07 server avahi-daemon[1184]: Server startup complete. Host name is server.local. Local service cookie is 2292651374.
Dec 14 21:20:08 server slapd[1195]: hdb_db_open: database "dc=server,dc=home": unclean shutdown detected; attempting recovery.
Dec 14 21:20:13 server /etc/mysql/debian-start[1330]: Upgrading MySQL tables if necessary.
Dec 14 21:20:13 server /etc/mysql/debian-start[1333]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Dec 14 21:20:13 server /etc/mysql/debian-start[1333]: Looking for 'mysql' as: /usr/bin/mysql
Dec 14 21:20:13 server /etc/mysql/debian-start[1333]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Dec 14 21:20:13 server /etc/mysql/debian-start[1333]: This installation of MySQL is already upgraded to 5.1.41, use --force if you still need to run mysql_upgrade
Dec 14 21:20:13 server /etc/mysql/debian-start[1340]: Checking for insecure root accounts.
Dec 14 21:20:13 server /etc/mysql/debian-start[1344]: Triggering myisam-recover for all MyISAM tables
Dec 14 21:20:14 server slapd[1195]: slapd starting
Dec 14 21:20:14 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:20:14 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:20:14 server exportfs[1402]: No host name given with /export/judyVideo (anonuid=1001,anongid=1001,insecure,no_subtree_check,rw,nohide), suggest *(anonuid=1001,anongid=1001,insecure,no_subtree_check,rw,nohide) to avoid warning
Dec 14 21:20:14 server kernel: [   31.528130] svc: failed to register lockdv1 RPC service (errno 97).
Dec 14 21:20:14 server kernel: [   31.528786] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Dec 14 21:20:14 server kernel: [   31.575179] NFSD: starting 90-second grace period
Dec 14 21:20:14 server pptpd[1428]: MGR: Maximum of 100 connections reduced to 55, not enough IP addresses given
Dec 14 21:20:14 server pptpd[1429]: MGR: Manager process started
Dec 14 21:20:14 server pptpd[1429]: MGR: Maximum of 55 connections available
Dec 14 21:20:15 server slapd[1195]: connection_read(17): no connection!
Dec 14 21:20:15 server slapd[1195]: connection_read(17): no connection!
Dec 14 21:20:26 server kernel: [   43.234876] vboxdrv: Found 2 processor cores.
Dec 14 21:20:26 server kernel: [   43.234940] VBoxDrv: dbg - g_abExecMemory=ffffffffa03cbd00
Dec 14 21:20:26 server kernel: [   43.234954] vboxdrv: fAsync=0 offMin=0x1ae offMax=0x61d
Dec 14 21:20:26 server kernel: [   43.234994] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Dec 14 21:20:26 server kernel: [   43.234996] vboxdrv: Successfully loaded version 3.2.12 (interface 0x00140001).
Dec 14 21:20:27 server sm-mta[1582]: starting daemon (8.14.3): SMTP+queueing@00:10:00
Dec 14 21:20:30 server apcupsd[1628]: apcupsd 3.14.6 (16 May 2009) debian startup succeeded
Dec 14 21:20:30 server apcupsd[1628]: NIS server startup succeeded
Dec 14 21:20:32 server kernel: [   49.536645] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec 14 21:20:33 server sendmail[1743]: oBF2KWKj001743: from=fail2ban, size=147, class=0, nrcpts=1, msgid=<201012150220.oBF2KWKj001743@server.home>, relay=root@localhost
Dec 14 21:20:33 server sm-mta[1744]: oBF2KXk6001744: from=<fail2ban@server.home>, size=396, class=0, nrcpts=1, msgid=<201012150220.oBF2KWKj001743@server.home>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Dec 14 21:20:33 server sendmail[1743]: oBF2KWKj001743: to=root@localhost, delay=00:00:01, xdelay=00:00:00, mailer=relay, pri=30147, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (oBF2KXk6001744 Message accepted for delivery)
Dec 14 21:20:33 server slapd[1195]: connection_read(17): no connection!
Dec 14 21:20:33 server slapd[1195]: connection_read(17): no connection!
Dec 14 21:20:33 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:20:33 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:20:33 server sm-mta[1745]: oBF2KXk6001744: to=<root@server.home>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30593, dsn=2.0.0, stat=Sent
Dec 14 21:20:33 server slapd[1195]: connection_read(23): no connection!
Dec 14 21:20:33 server slapd[1195]: connection_read(23): no connection!
Dec 14 21:20:36 server slapd[1195]: connection_read(17): no connection!
Dec 14 21:20:36 server slapd[1195]: connection_read(17): no connection!
Dec 14 21:22:58 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:24:03 server slapd[1195]: last message repeated 3 times
Dec 14 21:24:19 server ntpd[999]: synchronized to 91.189.94.4, stratum 2
Dec 14 21:24:19 server ntpd[999]: time reset -0.369576 s
Dec 14 21:25:01 server CRON[1832]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 21:25:59 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:25:59 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:28:58 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:29:31 server slapd[1195]: last message repeated 3 times
Dec 14 21:29:31 server ntpd[999]: synchronized to 91.189.94.4, stratum 2
Dec 14 21:30:01 server CRON[1843]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 21:30:01 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:30:01 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:31:58 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:31:58 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:34:59 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:34:59 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:34:59 server slapd[1195]: connection_read(23): no connection!
Dec 14 21:34:59 server slapd[1195]: connection_read(23): no connection!
Dec 14 21:35:01 server CRON[1860]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 21:39:02 server CRON[1872]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 21:40:01 server CRON[1881]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 21:40:01 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:40:01 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:40:16 server ntpd[999]: time reset +0.162645 s
Dec 14 21:40:16 server ntpd[999]: kernel time sync status change 2001
Dec 14 21:40:58 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:42:04 server slapd[1195]: last message repeated 3 times
Dec 14 21:45:01 server CRON[1909]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 21:46:58 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:48:05 server slapd[1195]: last message repeated 3 times
Dec 14 21:49:59 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:49:59 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:51:13 server ntpd[999]: synchronized to 91.189.94.4, stratum 2
Dec 14 21:52:58 server slapd[1195]: connection_read(25): no connection!
Dec 14 21:54:05 server slapd[1195]: last message repeated 3 times
Dec 14 21:55:01 server CRON[2396]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 21:55:59 server slapd[1195]: connection_read(25): no connection!
Dec 14 21:55:59 server slapd[1195]: connection_read(25): no connection!
Dec 14 21:58:08 server slapd[1195]: connection_read(24): no connection!
Dec 14 21:58:08 server slapd[1195]: connection_read(24): no connection!
Dec 14 21:58:08 server slapd[1195]: connection_read(23): no connection!
Dec 14 21:58:08 server slapd[1195]: connection_read(23): no connection!
Dec 14 22:00:01 server CRON[2616]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 22:00:01 server CRON[2617]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 22:00:01 server CRON[2618]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 22:00:01 server CRON[2619]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 22:00:01 server slapd[1195]: connection_read(24): no connection!
Dec 14 22:00:01 server slapd[1195]: connection_read(24): no connection!
Dec 14 22:00:01 server slapd[1195]: connection_read(23): no connection!
Dec 14 22:00:01 server slapd[1195]: connection_read(23): no connection!
Dec 14 22:00:01 server CRON[2620]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 22:00:01 server slapd[1195]: connection_read(25): no connection!
Dec 14 22:00:01 server slapd[1195]: connection_read(25): no connection!
Dec 14 22:00:01 server slapd[1195]: connection_read(26): no connection!
Dec 14 22:00:01 server slapd[1195]: connection_read(26): no connection!
Dec 14 22:00:19 server slapd[1195]: connection_read(23): no connection!
Dec 14 22:00:19 server slapd[1195]: connection_read(23): no connection!
Dec 14 22:05:01 server CRON[2885]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 22:05:06 server ntpd[999]: time reset -0.344027 s
Dec 14 22:09:01 server CRON[3079]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 22:10:08 server ntpd[999]: synchronized to 91.189.94.4, stratum 2
```

---

### Post by talz13 on 2010-12-14
Well, it just happened again just this evening.  I was downloading with sabnzbd on the server, and viewing some pics in Lightroom on my desktop over the samba share, and suddenly the sabnzbd page stopped responding and my Lightroom marked all the images as "media offline".  I tried to SSH over and see if the server was down, and sure enough it was.

I walked over there and power cycled it again (power button for 4 sec.), and it came up fine after booting.  This time I didn't see anything suspicious in the syslog, and since my last post I moved my swap file to my RAID 5 array.  It was stable for about 3 weeks now, but the problem still persists.

Here's an excerpt from my syslog from the crash today:```
Dec 14 20:45:01 server CRON[8910]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 20:46:58 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:48:24 server slapd[1127]: last message repeated 3 times
Dec 14 20:52:58 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:54:25 server slapd[1127]: last message repeated 3 times
Dec 14 20:55:01 server CRON[8951]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 20:55:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:55:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 20:58:58 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:00:01 server slapd[1127]: last message repeated 3 times
Dec 14 21:00:01 server CRON[8973]: (jeff) CMD (/home/jeff/scripts/delugeLogs.sh > /home/jeff/.flexget/importantLogs.txt)
Dec 14 21:00:01 server CRON[8974]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 14 21:00:01 server CRON[8976]: (jeff) CMD (/usr/local/bin/flexget --cron)
Dec 14 21:00:01 server CRON[8975]: (jeff) CMD (/home/jeff/scripts/fixSambaPerms.sh /home/shares jeff jeff > /dev/null)
Dec 14 21:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 21:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 21:00:01 server CRON[8978]: (jeff) CMD (find /home/shares/video/ -iname "*.nfo" -exec rm -rf {} \;  #remove nfo files)
Dec 14 21:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:00:01 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 21:00:01 server slapd[1127]: connection_read(25): no connection!
Dec 14 21:00:10 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:00:10 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:01:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:01:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:04:58 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:04:58 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:05:01 server CRON[9247]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 21:07:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:09:01 server CRON[9263]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 14 21:10:58 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:12:26 server slapd[1127]: last message repeated 3 times
Dec 14 21:13:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:13:59 server slapd[1127]: connection_read(18): no connection!
Dec 14 21:15:02 server CRON[9289]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 14 21:20:03 server kernel: imklog 4.2.0, log source = /proc/kmsg started.
Dec 14 21:20:03 server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1052" x-info="http://www.rsyslog.com"] (re)start
Dec 14 21:20:03 server rsyslogd: rsyslogd's groupid changed to 102
Dec 14 21:20:03 server rsyslogd: rsyslogd's userid changed to 101
Dec 14 21:20:03 server rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Dec 14 21:20:03 server kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 14 21:20:03 server kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 14 21:20:03 server kernel: [    0.000000] Linux version 2.6.32-26-server (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #48-Ubuntu SMP Wed Nov 24 10:28:32 UTC 2010 (Ubuntu 2.6.32-26.48-server 2.6.32.24+drm33.11)
Dec 14 21:20:03 server kernel: [    0.000000] Command line: root=UUID=44862d65-d880-4f88-9d4c-8e5e08a7242a ro quiet splash 
Dec 14 21:20:03 server kernel: [    0.000000] KERNEL supported cpus:
Dec 14 21:20:03 server kernel: [    0.000000]   Intel GenuineIntel
Dec 14 21:20:03 server kernel: [    0.000000]   AMD AuthenticAMD
Dec 14 21:20:03 server kernel: [    0.000000]   Centaur CentaurHauls
Dec 14 21:20:03 server kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bdce0000 (usable)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 00000000bdce0000 - 00000000bdce3000 (ACPI NVS)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 00000000bdce3000 - 00000000bdcf0000 (ACPI data)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 00000000bdcf0000 - 00000000bdd00000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 00000000c0000000 - 00000000d0000000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Dec 14 21:20:03 server kernel: [    0.000000] DMI 2.4 present.
Dec 14 21:20:03 server kernel: [    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
Dec 14 21:20:03 server kernel: [    0.000000] MTRR default type: uncachable
Dec 14 21:20:03 server kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 14 21:20:03 server kernel: [    0.000000]   00000-9FFFF write-back
Dec 14 21:20:03 server kernel: [    0.000000]   A0000-BFFFF uncachable
Dec 14 21:20:03 server kernel: [    0.000000]   C0000-CBFFF write-protect
Dec 14 21:20:03 server kernel: [    0.000000]   CC000-EFFFF uncachable
Dec 14 21:20:03 server kernel: [    0.000000]   F0000-FFFFF write-through
Dec 14 21:20:03 server kernel: [    0.000000] MTRR variable ranges enabled:
Dec 14 21:20:03 server kernel: [    0.000000]   0 base 000000000 mask F00000000 write-back
Dec 14 21:20:03 server kernel: [    0.000000]   1 base 0C0000000 mask FC0000000 uncachable
Dec 14 21:20:03 server kernel: [    0.000000]   2 base 0BE000000 mask FFE000000 uncachable
Dec 14 21:20:03 server kernel: [    0.000000]   3 base 0BDE00000 mask FFFE00000 uncachable
Dec 14 21:20:03 server kernel: [    0.000000]   4 base 100000000 mask FC0000000 write-back
Dec 14 21:20:03 server kernel: [    0.000000]   5 base 0BDD00000 mask FFFF00000 uncachable
Dec 14 21:20:03 server kernel: [    0.000000]   6 disabled
Dec 14 21:20:03 server kernel: [    0.000000]   7 disabled
Dec 14 21:20:03 server kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 14 21:20:03 server kernel: [    0.000000] e820 update range: 00000000bdd00000 - 0000000100000000 (usable) ==> (reserved)
Dec 14 21:20:03 server kernel: [    0.000000] last_pfn = 0xbdce0 max_arch_pfn = 0x400000000
Dec 14 21:20:03 server kernel: [    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
Dec 14 21:20:03 server kernel: [    0.000000] Scanning 1 areas for low memory corruption
Dec 14 21:20:03 server kernel: [    0.000000] modified physical RAM map:
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 0000000000100000 - 00000000bdce0000 (usable)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 00000000bdce0000 - 00000000bdce3000 (ACPI NVS)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 00000000bdce3000 - 00000000bdcf0000 (ACPI data)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 00000000bdcf0000 - 00000000bdd00000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 00000000c0000000 - 00000000d0000000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Dec 14 21:20:03 server kernel: [    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
Dec 14 21:20:03 server kernel: [    0.000000] initial memory mapped : 0 - 20000000
Dec 14 21:20:03 server kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bdce0000
Dec 14 21:20:03 server kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 14 21:20:03 server kernel: [    0.000000]  0000000000 - 00bdc00000 page 2M
Dec 14 21:20:03 server kernel: [    0.000000]  00bdc00000 - 00bdce0000 page 4k
Dec 14 21:20:03 server kernel: [    0.000000] kernel direct mapping tables up to bdce0000 @ 8000-d000
Dec 14 21:20:03 server kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
Dec 14 21:20:03 server kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 14 21:20:03 server kernel: [    0.000000]  0100000000 - 0140000000 page 2M
Dec 14 21:20:03 server kernel: [    0.000000] kernel direct mapping tables up to 140000000 @ b000-11000
Dec 14 21:20:03 server kernel: [    0.000000] RAMDISK: 377d2000 - 37fef196
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: RSDP 00000000000f70d0 00014 (v00 GBT   )
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: RSDT 00000000bdce3040 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: FACP 00000000bdce30c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: DSDT 00000000bdce3180 04526 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: FACS 00000000bdce0000 00040
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: HPET 00000000bdce7800 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: MCFG 00000000bdce7880 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: APIC 00000000bdce7700 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: SSDT 00000000bdce7f20 003AB (v01  PmRef    CpuPm 00003000 INTL 20040311)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 14 21:20:03 server kernel: [    0.000000] No NUMA configuration found
Dec 14 21:20:03 server kernel: [    0.000000] Faking a node at 0000000000000000-0000000140000000
Dec 14 21:20:03 server kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
Dec 14 21:20:03 server kernel: [    0.000000]   NODE_DATA [000000000000c000 - 0000000000010fff]
Dec 14 21:20:03 server kernel: [    0.000000]   bootmap [0000000000011000 -  0000000000038fff] pages 28
Dec 14 21:20:03 server kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
Dec 14 21:20:03 server kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Dec 14 21:20:03 server kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Dec 14 21:20:03 server kernel: [    0.000000]   #2 [0001000000 - 0001a4caa4]    TEXT DATA BSS ==> [0001000000 - 0001a4caa4]
Dec 14 21:20:03 server kernel: [    0.000000]   #3 [00377d2000 - 0037fef196]          RAMDISK ==> [00377d2000 - 0037fef196]
Dec 14 21:20:03 server kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Dec 14 21:20:03 server kernel: [    0.000000]   #5 [0001a4d000 - 0001a4d0f6]              BRK ==> [0001a4d000 - 0001a4d0f6]
Dec 14 21:20:03 server kernel: [    0.000000]   #6 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
Dec 14 21:20:03 server kernel: [    0.000000]   #7 [000000b000 - 000000c000]          PGTABLE ==> [000000b000 - 000000c000]
Dec 14 21:20:03 server kernel: [    0.000000] found SMP MP-table at [ffff8800000f56e0] f56e0
Dec 14 21:20:03 server kernel: [    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880001c00000-ffff8800053fffff] on node 0
Dec 14 21:20:03 server kernel: [    0.000000] Zone PFN ranges:
Dec 14 21:20:03 server kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Dec 14 21:20:03 server kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Dec 14 21:20:03 server kernel: [    0.000000]   Normal   0x00100000 -> 0x00140000
Dec 14 21:20:03 server kernel: [    0.000000] Movable zone start PFN for each node
Dec 14 21:20:03 server kernel: [    0.000000] early_node_map[4] active PFN ranges
Dec 14 21:20:03 server kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
Dec 14 21:20:03 server kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Dec 14 21:20:03 server kernel: [    0.000000]     0: 0x00000100 -> 0x000bdce0
Dec 14 21:20:03 server kernel: [    0.000000]     0: 0x00100000 -> 0x00140000
Dec 14 21:20:03 server kernel: [    0.000000] On node 0 totalpages: 1039482
Dec 14 21:20:03 server kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Dec 14 21:20:03 server kernel: [    0.000000]   DMA zone: 103 pages reserved
Dec 14 21:20:03 server kernel: [    0.000000]   DMA zone: 3835 pages, LIFO batch:0
Dec 14 21:20:03 server kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Dec 14 21:20:03 server kernel: [    0.000000]   DMA32 zone: 759064 pages, LIFO batch:31
Dec 14 21:20:03 server kernel: [    0.000000]   Normal zone: 3584 pages used for memmap
Dec 14 21:20:03 server kernel: [    0.000000]   Normal zone: 258560 pages, LIFO batch:31
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 14 21:20:03 server kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 14 21:20:03 server kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 14 21:20:03 server kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Dec 14 21:20:03 server kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Dec 14 21:20:03 server kernel: [    0.000000] nr_irqs_gsi: 24
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000bdce0000 - 00000000bdce3000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000bdce3000 - 00000000bdcf0000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000bdcf0000 - 00000000bdd00000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000bdd00000 - 00000000c0000000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000d0000000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fec00000
Dec 14 21:20:03 server kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Dec 14 21:20:03 server kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ec00000)
Dec 14 21:20:03 server kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 14 21:20:03 server kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Dec 14 21:20:03 server kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880005600000 s91544 r8192 d23144 u524288
Dec 14 21:20:03 server kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
Dec 14 21:20:03 server kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Dec 14 21:20:03 server kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1021459
Dec 14 21:20:03 server kernel: [    0.000000] Policy zone: Normal
Dec 14 21:20:03 server kernel: [    0.000000] Kernel command line: root=UUID=44862d65-d880-4f88-9d4c-8e5e08a7242a ro quiet splash 
Dec 14 21:20:03 server kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Dec 14 21:20:03 server kernel: [    0.000000] Initializing CPU#0
Dec 14 21:20:03 server kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Dec 14 21:20:03 server kernel: [    0.000000] Checking aperture...
Dec 14 21:20:03 server kernel: [    0.000000] No AGP bridge found
Dec 14 21:20:03 server kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Dec 14 21:20:03 server kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Dec 14 21:20:03 server kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Dec 14 21:20:03 server kernel: [    0.000000] Placing 64MB software IO TLB between ffff88000579e000 - ffff88000979e000
Dec 14 21:20:03 server kernel: [    0.000000] software IO TLB at phys 0x579e000 - 0x979e000
Dec 14 21:20:03 server kernel: [    0.000000] Memory: 4014864k/5242880k available (5511k kernel code, 1084952k absent, 143064k reserved, 3085k data, 796k init)
Dec 14 21:20:03 server kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Dec 14 21:20:03 server kernel: [    0.000000] Hierarchical RCU implementation.
Dec 14 21:20:03 server kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
Dec 14 21:20:03 server kernel: [    0.000000] Console: colour VGA+ 80x25
Dec 14 21:20:03 server kernel: [    0.000000] console [tty0] enabled
Dec 14 21:20:03 server kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Dec 14 21:20:03 server kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 14 21:20:03 server kernel: [    0.000000] hpet clockevent registered
Dec 14 21:20:03 server kernel: [    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Dec 14 21:20:03 server kernel: [    0.000000] Fast TSC calibration using PIT
Dec 14 21:20:03 server kernel: [    0.000000] Detected 2800.392 MHz processor.
Dec 14 21:20:03 server kernel: [    0.000005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5600.78 BogoMIPS (lpj=28003920)
Dec 14 21:20:03 server kernel: [    0.000026] Security Framework initialized
Dec 14 21:20:03 server kernel: [    0.000043] AppArmor: AppArmor initialized
Dec 14 21:20:03 server kernel: [    0.010234] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Dec 14 21:20:03 server kernel: [    0.011888] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Dec 14 21:20:03 server kernel: [    0.012652] Mount-cache hash table entries: 256
Dec 14 21:20:03 server kernel: [    0.012782] Initializing cgroup subsys ns
Dec 14 21:20:03 server kernel: [    0.012787] Initializing cgroup subsys cpuacct
Dec 14 21:20:03 server kernel: [    0.012790] Initializing cgroup subsys memory
Dec 14 21:20:03 server kernel: [    0.012795] Initializing cgroup subsys devices
Dec 14 21:20:03 server kernel: [    0.012797] Initializing cgroup subsys freezer
Dec 14 21:20:03 server kernel: [    0.012799] Initializing cgroup subsys net_cls
Dec 14 21:20:03 server kernel: [    0.012817] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 14 21:20:03 server kernel: [    0.012818] CPU: L2 cache: 2048K
Dec 14 21:20:03 server kernel: [    0.012821] CPU 0/0x0 -> Node 0
Dec 14 21:20:03 server kernel: [    0.012823] CPU: Physical Processor ID: 0
Dec 14 21:20:03 server kernel: [    0.012824] CPU: Processor Core ID: 0
Dec 14 21:20:03 server kernel: [    0.012826] mce: CPU supports 6 MCE banks
Dec 14 21:20:03 server kernel: [    0.012833] CPU0: Thermal monitoring enabled (TM2)
Dec 14 21:20:03 server kernel: [    0.012837] using mwait in idle threads.
Dec 14 21:20:03 server kernel: [    0.012838] Performance Events: Core2 events, Intel PMU driver.
Dec 14 21:20:03 server kernel: [    0.012843] ... version:                2
Dec 14 21:20:03 server kernel: [    0.012844] ... bit width:              40
Dec 14 21:20:03 server kernel: [    0.012846] ... generic registers:      2
Dec 14 21:20:03 server kernel: [    0.012847] ... value mask:             000000ffffffffff
Dec 14 21:20:03 server kernel: [    0.012848] ... max period:             000000007fffffff
Dec 14 21:20:03 server kernel: [    0.012849] ... fixed-purpose events:   3
Dec 14 21:20:03 server kernel: [    0.012850] ... event mask:             0000000700000003
Dec 14 21:20:03 server kernel: [    0.014948] ACPI: Core revision 20090903
Dec 14 21:20:03 server kernel: [    0.020022] ftrace: converting mcount calls to 0f 1f 44 00 00
Dec 14 21:20:03 server kernel: [    0.020030] ftrace: allocating 22834 entries in 90 pages
Dec 14 21:20:03 server kernel: [    0.027745] Setting APIC routing to flat
Dec 14 21:20:03 server kernel: [    0.028048] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 14 21:20:03 server kernel: [    0.128977] CPU0: Intel Pentium(R) Dual-Core  CPU      E6300  @ 2.80GHz stepping 0a
Dec 14 21:20:03 server kernel: [    0.130000] Booting processor 1 APIC 0x1 ip 0x6000
Dec 14 21:20:03 server kernel: [    0.010000] Initializing CPU#1
Dec 14 21:20:03 server kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 14 21:20:03 server kernel: [    0.010000] CPU: L2 cache: 2048K
Dec 14 21:20:03 server kernel: [    0.010000] CPU 1/0x1 -> Node 0
Dec 14 21:20:03 server kernel: [    0.010000] CPU: Physical Processor ID: 0
Dec 14 21:20:03 server kernel: [    0.010000] CPU: Processor Core ID: 1
Dec 14 21:20:03 server kernel: [    0.010000] CPU1: Thermal monitoring enabled (TM2)
Dec 14 21:20:03 server kernel: [    0.280059] CPU1: Intel Pentium(R) Dual-Core  CPU      E6300  @ 2.80GHz stepping 0a
Dec 14 21:20:03 server kernel: [    0.280065] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec 14 21:20:03 server kernel: [    0.290018] Brought up 2 CPUs
Dec 14 21:20:03 server kernel: [    0.290020] Total of 2 processors activated (11200.97 BogoMIPS).
Dec 14 21:20:03 server kernel: [    0.290423] CPU0 attaching sched-domain:
Dec 14 21:20:03 server kernel: [    0.290426]  domain 0: span 0-1 level MC
Dec 14 21:20:03 server kernel: [    0.290428]   groups: 0 1
Dec 14 21:20:03 server kernel: [    0.290433] CPU1 attaching sched-domain:
Dec 14 21:20:03 server kernel: [    0.290434]  domain 0: span 0-1 level MC
Dec 14 21:20:03 server kernel: [    0.290436]   groups: 1 0
Dec 14 21:20:03 server kernel: [    0.290502] devtmpfs: initialized
Dec 14 21:20:03 server kernel: [    0.292276] regulator: core version 0.5
Dec 14 21:20:03 server kernel: [    0.292276] Time:  2:19:43  Date: 12/15/10
Dec 14 21:20:03 server kernel: [    0.292276] NET: Registered protocol family 16
Dec 14 21:20:03 server kernel: [    0.292276] ACPI: bus type pci registered
Dec 14 21:20:03 server kernel: [    0.292276] PCI: MCFG configuration 0: base c0000000 segment 0 buses 0 - 255
Dec 14 21:20:03 server kernel: [    0.292276] PCI: MCFG area at c0000000 reserved in E820
Dec 14 21:20:03 server kernel: [    0.295384] PCI: Using MMCONFIG at c0000000 - cfffffff
Dec 14 21:20:03 server kernel: [    0.295386] PCI: Using configuration type 1 for base access
Dec 14 21:20:03 server kernel: [    0.295998] Trying to unpack rootfs image as initramfs...
Dec 14 21:20:03 server kernel: [    0.296038] bio: create slab <bio-0> at 0
Dec 14 21:20:03 server kernel: [    0.296524] ACPI: EC: Look up EC in DSDT
Dec 14 21:20:03 server kernel: [    0.304155] ACPI: Interpreter enabled
Dec 14 21:20:03 server kernel: [    0.304161] ACPI: (supports S0 S3 S4 S5)
Dec 14 21:20:03 server kernel: [    0.304178] ACPI: Using IOAPIC for interrupt routing
Dec 14 21:20:03 server kernel: [    0.307443] ACPI: No dock devices found.
Dec 14 21:20:03 server kernel: [    0.307525] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 14 21:20:03 server kernel: [    0.307593] pci 0000:00:02.0: reg 10 64bit mmio: [0xe1000000-0xe13fffff]
Dec 14 21:20:03 server kernel: [    0.307598] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xd0000000-0xdfffffff]
Dec 14 21:20:03 server kernel: [    0.307602] pci 0000:00:02.0: reg 20 io port: [0xd300-0xd307]
Dec 14 21:20:03 server kernel: [    0.307634] pci 0000:00:02.1: reg 10 64bit mmio: [0xe1400000-0xe14fffff]
Dec 14 21:20:03 server kernel: [    0.307708] pci 0000:00:1a.0: reg 20 io port: [0xd000-0xd01f]
Dec 14 21:20:03 server kernel: [    0.307767] pci 0000:00:1a.1: reg 20 io port: [0xd100-0xd11f]
Dec 14 21:20:03 server kernel: [    0.307824] pci 0000:00:1a.2: reg 20 io port: [0xd200-0xd21f]
Dec 14 21:20:03 server kernel: [    0.307875] pci 0000:00:1a.7: reg 10 32bit mmio: [0xe1701000-0xe17013ff]
Dec 14 21:20:03 server kernel: [    0.307961] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Dec 14 21:20:03 server kernel: [    0.307964] pci 0000:00:1c.0: PME# disabled
Dec 14 21:20:03 server kernel: [    0.308019] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Dec 14 21:20:03 server kernel: [    0.308022] pci 0000:00:1c.5: PME# disabled
Dec 14 21:20:03 server kernel: [    0.308069] pci 0000:00:1d.0: reg 20 io port: [0xd400-0xd41f]
Dec 14 21:20:03 server kernel: [    0.308127] pci 0000:00:1d.1: reg 20 io port: [0xd500-0xd51f]
Dec 14 21:20:03 server kernel: [    0.308185] pci 0000:00:1d.2: reg 20 io port: [0xd600-0xd61f]
Dec 14 21:20:03 server kernel: [    0.308237] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe1700000-0xe17003ff]
Dec 14 21:20:03 server kernel: [    0.308415] pci 0000:00:1f.2: reg 10 io port: [0xd700-0xd707]
Dec 14 21:20:03 server kernel: [    0.308419] pci 0000:00:1f.2: reg 14 io port: [0xd800-0xd803]
Dec 14 21:20:03 server kernel: [    0.308424] pci 0000:00:1f.2: reg 18 io port: [0xd900-0xd907]
Dec 14 21:20:03 server kernel: [    0.308428] pci 0000:00:1f.2: reg 1c io port: [0xda00-0xda03]
Dec 14 21:20:03 server kernel: [    0.308433] pci 0000:00:1f.2: reg 20 io port: [0xdb00-0xdb0f]
Dec 14 21:20:03 server kernel: [    0.308437] pci 0000:00:1f.2: reg 24 io port: [0xdc00-0xdc0f]
Dec 14 21:20:03 server kernel: [    0.308475] pci 0000:00:1f.3: reg 10 64bit mmio: [0xe1702000-0xe17020ff]
Dec 14 21:20:03 server kernel: [    0.308486] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
Dec 14 21:20:03 server kernel: [    0.308523] pci 0000:00:1f.5: reg 10 io port: [0xde00-0xde07]
Dec 14 21:20:03 server kernel: [    0.308528] pci 0000:00:1f.5: reg 14 io port: [0xdf00-0xdf03]
Dec 14 21:20:03 server kernel: [    0.308532] pci 0000:00:1f.5: reg 18 io port: [0xe000-0xe007]
Dec 14 21:20:03 server kernel: [    0.308537] pci 0000:00:1f.5: reg 1c io port: [0xe100-0xe103]
Dec 14 21:20:03 server kernel: [    0.308541] pci 0000:00:1f.5: reg 20 io port: [0xe200-0xe20f]
Dec 14 21:20:03 server kernel: [    0.308545] pci 0000:00:1f.5: reg 24 io port: [0xe300-0xe30f]
Dec 14 21:20:03 server kernel: [    0.308644] pci 0000:02:00.0: reg 10 io port: [0xc000-0xc0ff]
Dec 14 21:20:03 server kernel: [    0.308662] pci 0000:02:00.0: reg 18 64bit mmio pref: [0xe1510000-0xe1510fff]
Dec 14 21:20:03 server kernel: [    0.308674] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xe1500000-0xe150ffff]
Dec 14 21:20:03 server kernel: [    0.308682] pci 0000:02:00.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
Dec 14 21:20:03 server kernel: [    0.308717] pci 0000:02:00.0: supports D1 D2
Dec 14 21:20:03 server kernel: [    0.308718] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 21:20:03 server kernel: [    0.308722] pci 0000:02:00.0: PME# disabled
Dec 14 21:20:03 server kernel: [    0.308770] pci 0000:00:1c.5: bridge io port: [0xc000-0xcfff]
Dec 14 21:20:03 server kernel: [    0.308773] pci 0000:00:1c.5: bridge 32bit mmio: [0xe0000000-0xe0ffffff]
Dec 14 21:20:03 server kernel: [    0.308778] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xe1500000-0xe15fffff]
Dec 14 21:20:03 server kernel: [    0.308815] pci 0000:03:07.0: reg 10 32bit mmio: [0xe1604000-0xe16047ff]
Dec 14 21:20:03 server kernel: [    0.308821] pci 0000:03:07.0: reg 14 32bit mmio: [0xe1600000-0xe1603fff]
Dec 14 21:20:03 server kernel: [    0.308859] pci 0000:03:07.0: supports D1 D2
Dec 14 21:20:03 server kernel: [    0.308860] pci 0000:03:07.0: PME# supported from D0 D1 D2 D3hot
Dec 14 21:20:03 server kernel: [    0.308864] pci 0000:03:07.0: PME# disabled
Dec 14 21:20:03 server kernel: [    0.308896] pci 0000:00:1e.0: transparent bridge
Dec 14 21:20:03 server kernel: [    0.308900] pci 0000:00:1e.0: bridge 32bit mmio: [0xe1600000-0xe16fffff]
Dec 14 21:20:03 server kernel: [    0.308917] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 14 21:20:03 server kernel: [    0.309036] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Dec 14 21:20:03 server kernel: [    0.309083] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
Dec 14 21:20:03 server kernel: [    0.309119] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Dec 14 21:20:03 server kernel: [    0.322240] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Dec 14 21:20:03 server kernel: [    0.322316] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Dec 14 21:20:03 server kernel: [    0.322388] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Dec 14 21:20:03 server kernel: [    0.322460] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 *15)
Dec 14 21:20:03 server kernel: [    0.322531] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Dec 14 21:20:03 server kernel: [    0.322603] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Dec 14 21:20:03 server kernel: [    0.322676] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Dec 14 21:20:03 server kernel: [    0.322747] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 12 *14 15)
Dec 14 21:20:03 server kernel: [    0.322838] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Dec 14 21:20:03 server kernel: [    0.322850] vgaarb: loaded
Dec 14 21:20:03 server kernel: [    0.322932] SCSI subsystem initialized
Dec 14 21:20:03 server kernel: [    0.323057] libata version 3.00 loaded.
Dec 14 21:20:03 server kernel: [    0.323061] usbcore: registered new interface driver usbfs
Dec 14 21:20:03 server kernel: [    0.323072] usbcore: registered new interface driver hub
Dec 14 21:20:03 server kernel: [    0.323094] usbcore: registered new device driver usb
Dec 14 21:20:03 server kernel: [    0.323195] ACPI: WMI: Mapper loaded
Dec 14 21:20:03 server kernel: [    0.323197] PCI: Using ACPI for IRQ routing
Dec 14 21:20:03 server kernel: [    0.323325] NetLabel: Initializing
Dec 14 21:20:03 server kernel: [    0.323326] NetLabel:  domain hash size = 128
Dec 14 21:20:03 server kernel: [    0.323327] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 14 21:20:03 server kernel: [    0.323338] NetLabel:  unlabeled traffic allowed by default
Dec 14 21:20:03 server kernel: [    0.323363] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Dec 14 21:20:03 server kernel: [    0.323367] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Dec 14 21:20:03 server kernel: [    0.330032] Switching to clocksource tsc
Dec 14 21:20:03 server kernel: [    0.331384] AppArmor: AppArmor Filesystem Enabled
Dec 14 21:20:03 server kernel: [    0.331399] pnp: PnP ACPI init
Dec 14 21:20:03 server kernel: [    0.331414] ACPI: bus type pnp registered
Dec 14 21:20:03 server kernel: [    0.333027] pnp: PnP ACPI: found 11 devices
Dec 14 21:20:03 server kernel: [    0.333029] ACPI: ACPI bus type pnp unregistered
Dec 14 21:20:03 server kernel: [    0.333039] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Dec 14 21:20:03 server kernel: [    0.333041] system 00:01: ioport range 0x290-0x29f has been reserved
Dec 14 21:20:03 server kernel: [    0.333043] system 00:01: ioport range 0x800-0x87f has been reserved
Dec 14 21:20:03 server kernel: [    0.333045] system 00:01: ioport range 0x290-0x294 has been reserved
Dec 14 21:20:03 server kernel: [    0.333047] system 00:01: ioport range 0x880-0x88f has been reserved
Dec 14 21:20:03 server kernel: [    0.333049] system 00:01: ioport range 0x4c0-0x4ff could not be reserved
Dec 14 21:20:03 server kernel: [    0.333054] system 00:07: ioport range 0x400-0x4bf has been reserved
Dec 14 21:20:03 server kernel: [    0.333058] system 00:08: iomem range 0xc0000000-0xcfffffff has been reserved
Dec 14 21:20:03 server kernel: [    0.333062] system 00:09: iomem range 0xcc600-0xcffff has been reserved
Dec 14 21:20:03 server kernel: [    0.333064] system 00:09: iomem range 0xf0000-0xf7fff could not be reserved
Dec 14 21:20:03 server kernel: [    0.333066] system 00:09: iomem range 0xf8000-0xfbfff could not be reserved
Dec 14 21:20:03 server kernel: [    0.333068] system 00:09: iomem range 0xfc000-0xfffff could not be reserved
Dec 14 21:20:03 server kernel: [    0.333070] system 00:09: iomem range 0xbdce0000-0xbdcfffff could not be reserved
Dec 14 21:20:03 server kernel: [    0.333072] system 00:09: iomem range 0x0-0x9ffff could not be reserved
Dec 14 21:20:03 server kernel: [    0.333074] system 00:09: iomem range 0x100000-0xbdcdffff could not be reserved
Dec 14 21:20:03 server kernel: [    0.333076] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
Dec 14 21:20:03 server kernel: [    0.333078] system 00:09: iomem range 0xfed10000-0xfed1dfff has been reserved
Dec 14 21:20:03 server kernel: [    0.333080] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
Dec 14 21:20:03 server kernel: [    0.333082] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
Dec 14 21:20:03 server kernel: [    0.333084] system 00:09: iomem range 0xffb00000-0xffb7ffff has been reserved
Dec 14 21:20:03 server kernel: [    0.333086] system 00:09: iomem range 0xfff00000-0xffffffff has been reserved
Dec 14 21:20:03 server kernel: [    0.333088] system 00:09: iomem range 0xe0000-0xeffff has been reserved
Dec 14 21:20:03 server kernel: [    0.337767] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
Dec 14 21:20:03 server kernel: [    0.337771] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
Dec 14 21:20:03 server kernel: [    0.337775] pci 0000:00:1c.0:   MEM window: 0xe1800000-0xe19fffff
Dec 14 21:20:03 server kernel: [    0.337778] pci 0000:00:1c.0:   PREFETCH window: 0x000000e1a00000-0x000000e1bfffff
Dec 14 21:20:03 server kernel: [    0.337783] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
Dec 14 21:20:03 server kernel: [    0.337786] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
Dec 14 21:20:03 server kernel: [    0.337789] pci 0000:00:1c.5:   MEM window: 0xe0000000-0xe0ffffff
Dec 14 21:20:03 server kernel: [    0.337792] pci 0000:00:1c.5:   PREFETCH window: 0x000000e1500000-0x000000e15fffff
Dec 14 21:20:03 server kernel: [    0.337797] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Dec 14 21:20:03 server kernel: [    0.337799] pci 0000:00:1e.0:   IO window: disabled
Dec 14 21:20:03 server kernel: [    0.337802] pci 0000:00:1e.0:   MEM window: 0xe1600000-0xe16fffff
Dec 14 21:20:03 server kernel: [    0.337805] pci 0000:00:1e.0:   PREFETCH window: disabled
Dec 14 21:20:03 server kernel: [    0.337818]   alloc irq_desc for 16 on node -1
Dec 14 21:20:03 server kernel: [    0.337820]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    0.337825] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 14 21:20:03 server kernel: [    0.337829] pci 0000:00:1c.0: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.337835]   alloc irq_desc for 17 on node -1
Dec 14 21:20:03 server kernel: [    0.337837]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    0.337839] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec 14 21:20:03 server kernel: [    0.337842] pci 0000:00:1c.5: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.337847] pci 0000:00:1e.0: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.337851] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Dec 14 21:20:03 server kernel: [    0.337853] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Dec 14 21:20:03 server kernel: [    0.337854] pci_bus 0000:01: resource 0 io:  [0x1000-0x1fff]
Dec 14 21:20:03 server kernel: [    0.337856] pci_bus 0000:01: resource 1 mem: [0xe1800000-0xe19fffff]
Dec 14 21:20:03 server kernel: [    0.337858] pci_bus 0000:01: resource 2 pref mem [0xe1a00000-0xe1bfffff]
Dec 14 21:20:03 server kernel: [    0.337860] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
Dec 14 21:20:03 server kernel: [    0.337861] pci_bus 0000:02: resource 1 mem: [0xe0000000-0xe0ffffff]
Dec 14 21:20:03 server kernel: [    0.337863] pci_bus 0000:02: resource 2 pref mem [0xe1500000-0xe15fffff]
Dec 14 21:20:03 server kernel: [    0.337865] pci_bus 0000:03: resource 1 mem: [0xe1600000-0xe16fffff]
Dec 14 21:20:03 server kernel: [    0.337866] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
Dec 14 21:20:03 server kernel: [    0.337868] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
Dec 14 21:20:03 server kernel: [    0.337899] NET: Registered protocol family 2
Dec 14 21:20:03 server kernel: [    0.338036] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 14 21:20:03 server kernel: [    0.338985] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Dec 14 21:20:03 server kernel: [    0.342494] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Dec 14 21:20:03 server kernel: [    0.342907] TCP: Hash tables configured (established 524288 bind 65536)
Dec 14 21:20:03 server kernel: [    0.342909] TCP reno registered
Dec 14 21:20:03 server kernel: [    0.343020] NET: Registered protocol family 1
Dec 14 21:20:03 server kernel: [    0.343036] pci 0000:00:02.0: Boot video device
Dec 14 21:20:03 server kernel: [    0.343330] Scanning for low memory corruption every 60 seconds
Dec 14 21:20:03 server kernel: [    0.343433] audit: initializing netlink socket (disabled)
Dec 14 21:20:03 server kernel: [    0.343446] type=2000 audit(1292379582.339:1): initialized
Dec 14 21:20:03 server kernel: [    0.350598] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 14 21:20:03 server kernel: [    0.351606] VFS: Disk quotas dquot_6.5.2
Dec 14 21:20:03 server kernel: [    0.351648] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Dec 14 21:20:03 server kernel: [    0.352072] fuse init (API version 7.13)
Dec 14 21:20:03 server kernel: [    0.352131] msgmni has been set to 7841
Dec 14 21:20:03 server kernel: [    0.352288] alg: No test for stdrng (krng)
Dec 14 21:20:03 server kernel: [    0.352330] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Dec 14 21:20:03 server kernel: [    0.352332] io scheduler noop registered
Dec 14 21:20:03 server kernel: [    0.352334] io scheduler anticipatory registered
Dec 14 21:20:03 server kernel: [    0.352335] io scheduler deadline registered (default)
Dec 14 21:20:03 server kernel: [    0.352359] io scheduler cfq registered
Dec 14 21:20:03 server kernel: [    0.352476]   alloc irq_desc for 24 on node -1
Dec 14 21:20:03 server kernel: [    0.352478]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    0.352486] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
Dec 14 21:20:03 server kernel: [    0.352493] pcieport 0000:00:1c.0: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.352583]   alloc irq_desc for 25 on node -1
Dec 14 21:20:03 server kernel: [    0.352585]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    0.352590] pcieport 0000:00:1c.5: irq 25 for MSI/MSI-X
Dec 14 21:20:03 server kernel: [    0.352596] pcieport 0000:00:1c.5: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.352660] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 14 21:20:03 server kernel: [    0.352721] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 14 21:20:03 server kernel: [    0.352793] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Dec 14 21:20:03 server kernel: [    0.352796] ACPI: Power Button [PWRB]
Dec 14 21:20:03 server kernel: [    0.352834] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Dec 14 21:20:03 server kernel: [    0.352836] ACPI: Power Button [PWRF]
Dec 14 21:20:03 server kernel: [    0.353233] ACPI: SSDT 00000000bdce7900 0026C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
Dec 14 21:20:03 server kernel: [    0.353365] Marking TSC unstable due to TSC halts in idle
Dec 14 21:20:03 server kernel: [    0.353418] processor LNXCPU:00: registered as cooling_device0
Dec 14 21:20:03 server kernel: [    0.353574] ACPI: SSDT 00000000bdce7dc0 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
Dec 14 21:20:03 server kernel: [    0.353714] processor LNXCPU:01: registered as cooling_device1
Dec 14 21:20:03 server kernel: [    0.356211] Linux agpgart interface v0.103
Dec 14 21:20:03 server kernel: [    0.356236] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Dec 14 21:20:03 server kernel: [    0.357140] brd: module loaded
Dec 14 21:20:03 server kernel: [    0.357479] loop: module loaded
Dec 14 21:20:03 server kernel: [    0.357548] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Dec 14 21:20:03 server kernel: [    0.357651] ata_piix 0000:00:1f.2: version 2.13
Dec 14 21:20:03 server kernel: [    0.357665]   alloc irq_desc for 19 on node -1
Dec 14 21:20:03 server kernel: [    0.357667]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    0.357673] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 14 21:20:03 server kernel: [    0.357677] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Dec 14 21:20:03 server kernel: [    0.357716] ata_piix 0000:00:1f.2: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.357780] scsi0 : ata_piix
Dec 14 21:20:03 server kernel: [    0.357830] scsi1 : ata_piix
Dec 14 21:20:03 server kernel: [    0.358409] ata1: SATA max UDMA/133 cmd 0xd700 ctl 0xd800 bmdma 0xdb00 irq 19
Dec 14 21:20:03 server kernel: [    0.358414] ata2: SATA max UDMA/133 cmd 0xd900 ctl 0xda00 bmdma 0xdb08 irq 19
Dec 14 21:20:03 server kernel: [    0.358434] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 14 21:20:03 server kernel: [    0.358437] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Dec 14 21:20:03 server kernel: [    0.358441] Switching to clocksource hpet
Dec 14 21:20:03 server kernel: [    0.358470] ata_piix 0000:00:1f.5: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.358599] scsi2 : ata_piix
Dec 14 21:20:03 server kernel: [    0.358661] scsi3 : ata_piix
Dec 14 21:20:03 server kernel: [    0.359085] ata3: SATA max UDMA/133 cmd 0xde00 ctl 0xdf00 bmdma 0xe200 irq 19
Dec 14 21:20:03 server kernel: [    0.359088] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xe100 bmdma 0xe208 irq 19
Dec 14 21:20:03 server kernel: [    0.359321] Fixed MDIO Bus: probed
Dec 14 21:20:03 server kernel: [    0.359345] PPP generic driver version 2.4.2
Dec 14 21:20:03 server kernel: [    0.359378] tun: Universal TUN/TAP device driver, 1.6
Dec 14 21:20:03 server kernel: [    0.359379] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 14 21:20:03 server kernel: [    0.359458] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 14 21:20:03 server kernel: [    0.359475]   alloc irq_desc for 18 on node -1
Dec 14 21:20:03 server kernel: [    0.359476]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    0.359480] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 14 21:20:03 server kernel: [    0.359501] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.359504] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Dec 14 21:20:03 server kernel: [    0.359528] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Dec 14 21:20:03 server kernel: [    0.363430] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Dec 14 21:20:03 server kernel: [    0.363448] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xe1701000
Dec 14 21:20:03 server kernel: [    0.391275] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Dec 14 21:20:03 server kernel: [    0.391382] usb usb1: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    0.391406] hub 1-0:1.0: USB hub found
Dec 14 21:20:03 server kernel: [    0.391414] hub 1-0:1.0: 6 ports detected
Dec 14 21:20:03 server kernel: [    0.391474]   alloc irq_desc for 23 on node -1
Dec 14 21:20:03 server kernel: [    0.391476]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    0.391483] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 14 21:20:03 server kernel: [    0.391503] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.391506] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 14 21:20:03 server kernel: [    0.391537] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Dec 14 21:20:03 server kernel: [    0.395434] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Dec 14 21:20:03 server kernel: [    0.395448] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe1700000
Dec 14 21:20:03 server kernel: [    0.411267] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Dec 14 21:20:03 server kernel: [    0.411367] usb usb2: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    0.411388] hub 2-0:1.0: USB hub found
Dec 14 21:20:03 server kernel: [    0.411395] hub 2-0:1.0: 6 ports detected
Dec 14 21:20:03 server kernel: [    0.411444] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 14 21:20:03 server kernel: [    0.411460] uhci_hcd: USB Universal Host Controller Interface driver
Dec 14 21:20:03 server kernel: [    0.411498] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 14 21:20:03 server kernel: [    0.411507] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.411510] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Dec 14 21:20:03 server kernel: [    0.411539] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Dec 14 21:20:03 server kernel: [    0.411573] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000d000
Dec 14 21:20:03 server kernel: [    0.411641] usb usb3: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    0.411658] hub 3-0:1.0: USB hub found
Dec 14 21:20:03 server kernel: [    0.411663] hub 3-0:1.0: 2 ports detected
Dec 14 21:20:03 server kernel: [    0.411697]   alloc irq_desc for 21 on node -1
Dec 14 21:20:03 server kernel: [    0.411698]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    0.411703] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Dec 14 21:20:03 server kernel: [    0.411707] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.411709] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Dec 14 21:20:03 server kernel: [    0.411734] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Dec 14 21:20:03 server kernel: [    0.411759] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d100
Dec 14 21:20:03 server kernel: [    0.411821] usb usb4: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    0.411842] hub 4-0:1.0: USB hub found
Dec 14 21:20:03 server kernel: [    0.411846] hub 4-0:1.0: 2 ports detected
Dec 14 21:20:03 server kernel: [    0.411876] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 14 21:20:03 server kernel: [    0.411881] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.411883] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Dec 14 21:20:03 server kernel: [    0.411912] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Dec 14 21:20:03 server kernel: [    0.411933] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000d200
Dec 14 21:20:03 server kernel: [    0.411996] usb usb5: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    0.412015] hub 5-0:1.0: USB hub found
Dec 14 21:20:03 server kernel: [    0.412019] hub 5-0:1.0: 2 ports detected
Dec 14 21:20:03 server kernel: [    0.412050] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 14 21:20:03 server kernel: [    0.412054] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.412057] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 14 21:20:03 server kernel: [    0.412080] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Dec 14 21:20:03 server kernel: [    0.412101] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
Dec 14 21:20:03 server kernel: [    0.412168] usb usb6: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    0.412185] hub 6-0:1.0: USB hub found
Dec 14 21:20:03 server kernel: [    0.412190] hub 6-0:1.0: 2 ports detected
Dec 14 21:20:03 server kernel: [    0.412225] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 14 21:20:03 server kernel: [    0.412230] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.412232] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 14 21:20:03 server kernel: [    0.412253] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Dec 14 21:20:03 server kernel: [    0.412273] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d500
Dec 14 21:20:03 server kernel: [    0.412332] usb usb7: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    0.412349] hub 7-0:1.0: USB hub found
Dec 14 21:20:03 server kernel: [    0.412355] hub 7-0:1.0: 2 ports detected
Dec 14 21:20:03 server kernel: [    0.412387] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 14 21:20:03 server kernel: [    0.412391] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    0.412393] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 14 21:20:03 server kernel: [    0.412415] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Dec 14 21:20:03 server kernel: [    0.412435] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d600
Dec 14 21:20:03 server kernel: [    0.412499] usb usb8: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    0.412517] hub 8-0:1.0: USB hub found
Dec 14 21:20:03 server kernel: [    0.412522] hub 8-0:1.0: 2 ports detected
Dec 14 21:20:03 server kernel: [    0.412589] PNP: No PS/2 controller found. Probing ports directly.
Dec 14 21:20:03 server kernel: [    0.412949] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 14 21:20:03 server kernel: [    0.412953] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 14 21:20:03 server kernel: [    0.413008] mice: PS/2 mouse device common for all mice
Dec 14 21:20:03 server kernel: [    0.413079] rtc_cmos 00:04: RTC can wake from S4
Dec 14 21:20:03 server kernel: [    0.413107] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Dec 14 21:20:03 server kernel: [    0.413128] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Dec 14 21:20:03 server kernel: [    0.413227] device-mapper: uevent: version 1.0.3
Dec 14 21:20:03 server kernel: [    0.413328] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Dec 14 21:20:03 server kernel: [    0.413376] device-mapper: multipath: version 1.1.0 loaded
Dec 14 21:20:03 server kernel: [    0.413378] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec 14 21:20:03 server kernel: [    0.413517] cpuidle: using governor ladder
Dec 14 21:20:03 server kernel: [    0.413558] cpuidle: using governor menu
Dec 14 21:20:03 server kernel: [    0.413809] TCP cubic registered
Dec 14 21:20:03 server kernel: [    0.413910] NET: Registered protocol family 10
Dec 14 21:20:03 server kernel: [    0.414233] lo: Disabled Privacy Extensions
Dec 14 21:20:03 server kernel: [    0.414433] NET: Registered protocol family 17
Dec 14 21:20:03 server kernel: [    0.415957] PM: Resume from disk failed.
Dec 14 21:20:03 server kernel: [    0.415968] registered taskstats version 1
Dec 14 21:20:03 server kernel: [    0.416257]   Magic number: 6:643:308
Dec 14 21:20:03 server kernel: [    0.416283] tty tty37: hash matches
Dec 14 21:20:03 server kernel: [    0.416340] rtc_cmos 00:04: setting system clock to 2010-12-15 02:19:43 UTC (1292379583)
Dec 14 21:20:03 server kernel: [    0.416342] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 14 21:20:03 server kernel: [    0.416343] EDD information not available.
Dec 14 21:20:03 server kernel: [    0.443841] Freeing initrd memory: 8308k freed
Dec 14 21:20:03 server kernel: [    0.730728] ata4: SATA link down (SStatus 0 SControl 300)
Dec 14 21:20:03 server kernel: [    0.880047] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 14 21:20:03 server kernel: [    0.903651] ata3.00: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
Dec 14 21:20:03 server kernel: [    0.903656] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 14 21:20:03 server kernel: [    0.920716] ata3.00: configured for UDMA/133
Dec 14 21:20:03 server kernel: [    0.990013] usb 4-1: new low speed USB device using uhci_hcd and address 2
Dec 14 21:20:03 server kernel: [    1.173880] usb 4-1: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    1.240063] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 14 21:20:03 server kernel: [    1.240077] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 14 21:20:03 server kernel: [    1.240247] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 14 21:20:03 server kernel: [    1.240258] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 14 21:20:03 server kernel: [    1.287501] ata2.00: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
Dec 14 21:20:03 server kernel: [    1.287506] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 14 21:20:03 server kernel: [    1.291627] ata2.01: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
Dec 14 21:20:03 server kernel: [    1.291632] ata2.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 14 21:20:03 server kernel: [    1.300192] ata1.00: HPA unlocked: 1250261615 -> 1250263728, native 1250263728
Dec 14 21:20:03 server kernel: [    1.300195] ata1.00: ATA-8: WDC WD6400AACS-00G8B1, 05.04C05, max UDMA/133
Dec 14 21:20:03 server kernel: [    1.300197] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 14 21:20:03 server kernel: [    1.318864] ata1.01: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
Dec 14 21:20:03 server kernel: [    1.318868] ata1.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 14 21:20:03 server kernel: [    1.320529] ata1.00: configured for UDMA/133
Dec 14 21:20:03 server kernel: [    1.320873] ata2.00: configured for UDMA/133
Dec 14 21:20:03 server kernel: [    1.341715] ata1.01: configured for UDMA/133
Dec 14 21:20:03 server kernel: [    1.341841] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400AACS-0 05.0 PQ: 0 ANSI: 5
Dec 14 21:20:03 server kernel: [    1.341969] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Dec 14 21:20:03 server kernel: [    1.341996] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 14 21:20:03 server kernel: [    1.342026] sd 0:0:0:0: [sda] Write Protect is off
Dec 14 21:20:03 server kernel: [    1.342028] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 14 21:20:03 server kernel: [    1.342046] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 14 21:20:03 server kernel: [    1.342076] scsi 0:0:1:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
Dec 14 21:20:03 server kernel: [    1.342145]  sda:
Dec 14 21:20:03 server kernel: [    1.342154] sd 0:0:1:0: Attached scsi generic sg1 type 0
Dec 14 21:20:03 server kernel: [    1.355174] sd 0:0:1:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec 14 21:20:03 server kernel: [    1.355177]  sda1 sda2 <
Dec 14 21:20:03 server kernel: [    1.362101] ata2.01: configured for UDMA/133
Dec 14 21:20:03 server kernel: [    1.362187] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
Dec 14 21:20:03 server kernel: [    1.362294] sd 1:0:0:0: Attached scsi generic sg2 type 0
Dec 14 21:20:03 server kernel: [    1.362316] sd 1:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec 14 21:20:03 server kernel: [    1.362358] scsi 1:0:1:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
Dec 14 21:20:03 server kernel: [    1.362363] sd 1:0:0:0: [sdc] Write Protect is off
Dec 14 21:20:03 server kernel: [    1.362365] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Dec 14 21:20:03 server kernel: [    1.362382] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 14 21:20:03 server kernel: [    1.362428] sd 1:0:1:0: Attached scsi generic sg3 type 0
Dec 14 21:20:03 server kernel: [    1.362482]  sdc:
Dec 14 21:20:03 server kernel: [    1.362495] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
Dec 14 21:20:03 server kernel: [    1.362564] sd 2:0:0:0: Attached scsi generic sg4 type 0
Dec 14 21:20:03 server kernel: [    1.362566] sd 2:0:0:0: [sde] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec 14 21:20:03 server kernel: [    1.362598] sd 2:0:0:0: [sde] Write Protect is off
Dec 14 21:20:03 server kernel: [    1.362600] sd 2:0:0:0: [sde] Mode Sense: 00 3a 00 00
Dec 14 21:20:03 server kernel: [    1.362625] sd 2:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 14 21:20:03 server kernel: [    1.362729]  sde: sde1
Dec 14 21:20:03 server kernel: [    1.366592] sd 2:0:0:0: [sde] Attached SCSI disk
Dec 14 21:20:03 server kernel: [    1.366925] sd 1:0:1:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec 14 21:20:03 server kernel: [    1.366928]  sdc1
Dec 14 21:20:03 server kernel: [    1.366980] sd 1:0:1:0: [sdd] Write Protect is off
Dec 14 21:20:03 server kernel: [    1.366983] sd 1:0:1:0: [sdd] Mode Sense: 00 3a 00 00
Dec 14 21:20:03 server kernel: [    1.367012] sd 1:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 14 21:20:03 server kernel: [    1.367150] sd 1:0:0:0: [sdc] Attached SCSI disk
Dec 14 21:20:03 server kernel: [    1.367164]  sdd: sda5 sdd1
Dec 14 21:20:03 server kernel: [    1.379565] sd 1:0:1:0: [sdd] Attached SCSI disk
Dec 14 21:20:03 server kernel: [    1.380631]  sda6
Dec 14 21:20:03 server kernel: [    1.380649] sd 0:0:1:0: [sdb] Write Protect is off
Dec 14 21:20:03 server kernel: [    1.380653] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Dec 14 21:20:03 server kernel: [    1.393360]  sda7
Dec 14 21:20:03 server kernel: [    1.393363] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 14 21:20:03 server kernel: [    1.393367]  >
Dec 14 21:20:03 server kernel: [    1.393587]  sdb: sdb1
Dec 14 21:20:03 server kernel: [    1.406837] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 14 21:20:03 server kernel: [    1.406842] sd 0:0:1:0: [sdb] Attached SCSI disk
Dec 14 21:20:03 server kernel: [    1.406859] Freeing unused kernel memory: 796k freed
Dec 14 21:20:03 server kernel: [    1.407092] Write protecting the kernel read-only data: 7804k
Dec 14 21:20:03 server kernel: [    1.417583] udev: starting version 151
Dec 14 21:20:03 server kernel: [    1.451313] usb 4-2: new low speed USB device using uhci_hcd and address 3
Dec 14 21:20:03 server kernel: [    1.459122] md: linear personality registered for level -1
Dec 14 21:20:03 server kernel: [    1.460832] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 14 21:20:03 server kernel: [    1.460851] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 14 21:20:03 server kernel: [    1.460893] r8169 0000:02:00.0: setting latency timer to 64
Dec 14 21:20:03 server kernel: [    1.460932]   alloc irq_desc for 26 on node -1
Dec 14 21:20:03 server kernel: [    1.460934]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [    1.460945] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
Dec 14 21:20:03 server kernel: [    1.461367] eth0: RTL8168c/8111c at 0xffffc9000065e000, 00:1f:d0:27:53:6d, XID 1c4000c0 IRQ 26
Dec 14 21:20:03 server kernel: [    1.482800] md: multipath personality registered for level -4
Dec 14 21:20:03 server kernel: [    1.487773] ohci1394 0000:03:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 14 21:20:03 server kernel: [    1.498407] usbcore: registered new interface driver hiddev
Dec 14 21:20:03 server kernel: [    1.505096] md: raid0 personality registered for level 0
Dec 14 21:20:03 server kernel: [    1.509337] md: raid1 personality registered for level 1
Dec 14 21:20:03 server kernel: [    1.510750] async_tx: api initialized (async)
Dec 14 21:20:03 server kernel: [    1.512057] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input3
Dec 14 21:20:03 server kernel: [    1.512124] generic-usb 0003:046D:C308.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1a.1-1/input0
Dec 14 21:20:03 server kernel: [    1.541377] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[e1604000-e16047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Dec 14 21:20:03 server kernel: [    1.552900] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.1/input/input4
Dec 14 21:20:03 server kernel: [    1.552984] generic-usb 0003:046D:C308.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:1a.1-1/input1
Dec 14 21:20:03 server kernel: [    1.553006] usbcore: registered new interface driver usbhid
Dec 14 21:20:03 server kernel: [    1.553008] usbhid: v2.6:USB HID core driver
Dec 14 21:20:03 server kernel: [    1.569757] md: bind<sde1>
Dec 14 21:20:03 server kernel: [    1.587749] md: bind<sdd1>
Dec 14 21:20:03 server kernel: [    1.589212] md: bind<sdc1>
Dec 14 21:20:03 server kernel: [    1.658983] md: bind<sdb1>
Dec 14 21:20:03 server kernel: [    1.680030] raid6: int64x1   2142 MB/s
Dec 14 21:20:03 server kernel: [    1.692863] usb 4-2: configuration #1 chosen from 1 choice
Dec 14 21:20:03 server kernel: [    1.850023] raid6: int64x2   2916 MB/s
Dec 14 21:20:03 server kernel: [    2.020029] raid6: int64x4   2136 MB/s
Dec 14 21:20:03 server kernel: [    2.190034] raid6: int64x8   1842 MB/s
Dec 14 21:20:03 server kernel: [    2.323881] generic-usb 0003:051D:0002.0003: hiddev96,hidraw2: USB HID v1.10 Device [American Power Conversion Back-UPS NS 1050 FW:7.g2 .D USB FW:g2 ] on usb-0000:00:1a.1-2/input0
Dec 14 21:20:03 server kernel: [    2.360009] raid6: sse2x1    4603 MB/s
Dec 14 21:20:03 server kernel: [    2.530012] raid6: sse2x2    5446 MB/s
Dec 14 21:20:03 server kernel: [    2.700011] raid6: sse2x4    8293 MB/s
Dec 14 21:20:03 server kernel: [    2.700012] raid6: using algorithm sse2x4 (8293 MB/s)
Dec 14 21:20:03 server kernel: [    2.700856] xor: automatically using best checksumming function: generic_sse
Dec 14 21:20:03 server kernel: [    2.749986]    generic_sse: 10670.400 MB/sec
Dec 14 21:20:03 server kernel: [    2.750004] xor: using function: generic_sse (10670.400 MB/sec)
Dec 14 21:20:03 server kernel: [    2.753073] md: raid6 personality registered for level 6
Dec 14 21:20:03 server kernel: [    2.753075] md: raid5 personality registered for level 5
Dec 14 21:20:03 server kernel: [    2.753076] md: raid4 personality registered for level 4
Dec 14 21:20:03 server kernel: [    2.757278] md: raid10 personality registered for level 10
Dec 14 21:20:03 server kernel: [    2.770565] EXT3-fs: INFO: recovery required on readonly filesystem.
Dec 14 21:20:03 server kernel: [    2.770567] EXT3-fs: write access will be enabled during recovery.
Dec 14 21:20:03 server kernel: [    2.784491] raid5: md0 is not clean -- starting background reconstruction
Dec 14 21:20:03 server kernel: [    2.784499] raid5: device sdb1 operational as raid disk 1
Dec 14 21:20:03 server kernel: [    2.784500] raid5: device sdc1 operational as raid disk 0
Dec 14 21:20:03 server kernel: [    2.784501] raid5: device sdd1 operational as raid disk 2
Dec 14 21:20:03 server kernel: [    2.784503] raid5: device sde1 operational as raid disk 3
Dec 14 21:20:03 server kernel: [    2.784820] raid5: allocated 4282kB for md0
Dec 14 21:20:03 server kernel: [    2.784854] 1: w=1 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
Dec 14 21:20:03 server kernel: [    2.784856] 0: w=2 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
Dec 14 21:20:03 server kernel: [    2.784858] 2: w=3 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
Dec 14 21:20:03 server kernel: [    2.784860] 3: w=4 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
Dec 14 21:20:03 server kernel: [    2.784862] raid5: raid level 5 set md0 active with 4 out of 4 devices, algorithm 2
Dec 14 21:20:03 server kernel: [    2.784863] RAID5 conf printout:
Dec 14 21:20:03 server kernel: [    2.784864]  --- rd:4 wd:4
Dec 14 21:20:03 server kernel: [    2.784866]  disk 0, o:1, dev:sdc1
Dec 14 21:20:03 server kernel: [    2.784867]  disk 1, o:1, dev:sdb1
Dec 14 21:20:03 server kernel: [    2.784868]  disk 2, o:1, dev:sdd1
Dec 14 21:20:03 server kernel: [    2.784869]  disk 3, o:1, dev:sde1
Dec 14 21:20:03 server kernel: [    2.784893] md0: detected capacity change from 0 to 3000606523392
Dec 14 21:20:03 server kernel: [    2.784953] md: resync of RAID array md0
Dec 14 21:20:03 server kernel: [    2.784954] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Dec 14 21:20:03 server kernel: [    2.784956] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
Dec 14 21:20:03 server kernel: [    2.784960] md: using 128k window, over a total of 976759936 blocks.
Dec 14 21:20:03 server kernel: [    2.785768]  md0: unknown partition table
Dec 14 21:20:03 server kernel: [    2.860145] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[002ce08400001fd0]
Dec 14 21:20:03 server kernel: [    3.467837] kjournald starting.  Commit interval 5 seconds
Dec 14 21:20:03 server kernel: [    3.467861] EXT3-fs: sda1: orphan cleanup on readonly fs
Dec 14 21:20:03 server kernel: [    3.489523] ext3_orphan_cleanup: deleting unreferenced inode 7184496
Dec 14 21:20:03 server kernel: [    3.499710] ext3_orphan_cleanup: deleting unreferenced inode 7184484
Dec 14 21:20:03 server kernel: [    3.512350] ext3_orphan_cleanup: deleting unreferenced inode 2282240
Dec 14 21:20:03 server kernel: [    3.536649] ext3_orphan_cleanup: deleting unreferenced inode 5153063
Dec 14 21:20:03 server kernel: [    3.546935] ext3_orphan_cleanup: deleting unreferenced inode 5153062
Dec 14 21:20:03 server kernel: [    3.555393] ext3_orphan_cleanup: deleting unreferenced inode 5153059
Dec 14 21:20:03 server kernel: [    3.567755] ext3_orphan_cleanup: deleting unreferenced inode 5153058
Dec 14 21:20:03 server kernel: [    3.567766] ext3_orphan_cleanup: deleting unreferenced inode 5153057
Dec 14 21:20:03 server kernel: [    3.579435] ext3_orphan_cleanup: deleting unreferenced inode 5153038
Dec 14 21:20:03 server kernel: [    3.580724] ext3_orphan_cleanup: deleting unreferenced inode 5152995
Dec 14 21:20:03 server kernel: [    3.585220] ext3_orphan_cleanup: deleting unreferenced inode 5152991
Dec 14 21:20:03 server kernel: [    3.585372] ext3_orphan_cleanup: deleting unreferenced inode 5152933
Dec 14 21:20:03 server kernel: [    3.585542] ext3_orphan_cleanup: deleting unreferenced inode 5152922
Dec 14 21:20:03 server kernel: [    3.593877] ext3_orphan_cleanup: deleting unreferenced inode 5152899
Dec 14 21:20:03 server kernel: [    3.598926] ext3_orphan_cleanup: deleting unreferenced inode 5152821
Dec 14 21:20:03 server kernel: [    3.618047] ext3_orphan_cleanup: deleting unreferenced inode 2280274
Dec 14 21:20:03 server kernel: [    3.628571] ext3_orphan_cleanup: deleting unreferenced inode 2280077
Dec 14 21:20:03 server kernel: [    3.643035] ext3_orphan_cleanup: deleting unreferenced inode 2280071
Dec 14 21:20:03 server kernel: [    3.655641] ext3_orphan_cleanup: deleting unreferenced inode 2278129
Dec 14 21:20:03 server kernel: [    3.659689] ext3_orphan_cleanup: deleting unreferenced inode 1130506
Dec 14 21:20:03 server kernel: [    3.659704] ext3_orphan_cleanup: deleting unreferenced inode 1130505
Dec 14 21:20:03 server kernel: [    3.659711] ext3_orphan_cleanup: deleting unreferenced inode 1130504
Dec 14 21:20:03 server kernel: [    3.659718] ext3_orphan_cleanup: deleting unreferenced inode 1130503
Dec 14 21:20:03 server kernel: [    3.659725] ext3_orphan_cleanup: deleting unreferenced inode 1130502
Dec 14 21:20:03 server kernel: [    3.659904] ext3_orphan_cleanup: deleting unreferenced inode 5152959
Dec 14 21:20:03 server kernel: [    3.670260] ext3_orphan_cleanup: deleting unreferenced inode 5152850
Dec 14 21:20:03 server kernel: [    3.674303] EXT3-fs: sda1: 26 orphan inodes deleted
Dec 14 21:20:03 server kernel: [    3.674306] EXT3-fs: recovery complete.
Dec 14 21:20:03 server kernel: [    3.698090] EXT3-fs: mounted filesystem with ordered data mode.
Dec 14 21:20:03 server kernel: [    6.769538] udev: starting version 151
Dec 14 21:20:03 server kernel: [    8.405530] type=1505 audit(1292379591.483:2):  operation="profile_load" pid=586 name="/sbin/dhclient3"
Dec 14 21:20:03 server kernel: [    8.406009] type=1505 audit(1292379591.483:3):  operation="profile_load" pid=586 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Dec 14 21:20:03 server kernel: [    8.406265] type=1505 audit(1292379591.483:4):  operation="profile_load" pid=586 name="/usr/lib/connman/scripts/dhclient-script"
Dec 14 21:20:03 server kernel: [    8.498516] agpgart-intel 0000:00:00.0: Intel G45/G43 Chipset
Dec 14 21:20:03 server kernel: [    8.499026] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
Dec 14 21:20:03 server kernel: [    8.516977] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Dec 14 21:20:03 server kernel: [    8.519875] EXT3 FS on sda1, internal journal
Dec 14 21:20:03 server kernel: [    8.607895] lp: driver loaded but no devices found
Dec 14 21:20:03 server kernel: [    9.398150] it87: Found IT8718F chip at 0x290, revision 5
Dec 14 21:20:03 server kernel: [    9.398161] it87: in3 is VCC (+5V)
Dec 14 21:20:03 server kernel: [    9.985701] [drm] Initialized drm 1.1.0 20060810
Dec 14 21:20:03 server kernel: [   10.607997] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 14 21:20:03 server kernel: [   10.608001] i915 0000:00:02.0: setting latency timer to 64
Dec 14 21:20:03 server kernel: [   10.618749] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
Dec 14 21:20:03 server kernel: [   10.618753] [drm] MTRR allocation failed.  Graphics performance may suffer.
Dec 14 21:20:03 server kernel: [   10.619254]   alloc irq_desc for 27 on node -1
Dec 14 21:20:03 server kernel: [   10.619256]   alloc kstat_irqs on node -1
Dec 14 21:20:03 server kernel: [   10.619263] i915 0000:00:02.0: irq 27 for MSI/MSI-X
Dec 14 21:20:03 server kernel: [   10.619269] [drm] set up 31M of stolen space
Dec 14 21:20:03 server kernel: [   10.630272] type=1505 audit(1292379593.704:5):  operation="profile_load" pid=703 name="/usr/sbin/ntpd"
Dec 14 21:20:03 server kernel: [   10.832540] r8169: eth0: link up
Dec 14 21:20:03 server kernel: [   10.832546] r8169: eth0: link up
Dec 14 21:20:03 server kernel: [   10.864293] fb0: inteldrmfb frame buffer device
Dec 14 21:20:03 server kernel: [   10.864295] registered panic notifier
Dec 14 21:20:03 server kernel: [   10.864311] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Dec 14 21:20:03 server kernel: [   11.467746] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Dec 14 21:20:03 server kernel: [   11.468619] SGI XFS Quota Management subsystem
Dec 14 21:20:03 server kernel: [   11.475522] Filesystem "md0": Disabling barriers, trial barrier write failed
Dec 14 21:20:03 server kernel: [   11.522399] XFS mounting filesystem md0
Dec 14 21:20:03 server kernel: [   11.550743] vga16fb: initializing
Dec 14 21:20:03 server kernel: [   11.550747] vga16fb: mapped to 0xffff8800000a0000
Dec 14 21:20:03 server kernel: [   11.550750] vga16fb: not registering due to another framebuffer present
Dec 14 21:20:03 server kernel: [   12.034903] Console: switching to colour frame buffer device 210x65
Dec 14 21:20:03 server kernel: [   12.127241] Starting XFS recovery on filesystem: md0 (logdev: internal)
Dec 14 21:20:03 server kernel: [   12.292546] RPC: Registered udp transport module.
Dec 14 21:20:03 server kernel: [   12.292549] RPC: Registered tcp transport module.
Dec 14 21:20:03 server kernel: [   12.292550] RPC: Registered tcp NFSv4.1 backchannel transport module.
Dec 14 21:20:03 server kernel: [   15.406958] Ending XFS recovery on filesystem: md0 (logdev: internal)
Dec 14 21:20:03 server kernel: [   15.761401] Adding 4194296k swap on /home/swap/swapfile.  Priority:-1 extents:2 across:4339384k 
Dec 14 21:20:03 server kernel: [   16.145884] kjournald starting.  Commit interval 5 seconds
Dec 14 21:20:03 server kernel: [   16.146239] EXT3 FS on sda7, internal journal
Dec 14 21:20:03 server kernel: [   16.146244] EXT3-fs: mounted filesystem with ordered data mode.
Dec 14 21:20:03 server kernel: [   18.849099] kjournald starting.  Commit interval 5 seconds
Dec 14 21:20:03 server kernel: [   18.849378] EXT3 FS on sda6, internal journal
Dec 14 21:20:03 server kernel: [   18.849382] EXT3-fs: mounted filesystem with ordered data mode.
Dec 14 21:20:03 server kernel: [   20.497753] type=1505 audit(1292379603.573:6):  operation="profile_replace" pid=1066 name="/sbin/dhclient3"
Dec 14 21:20:03 server kernel: [   20.498243] type=1505 audit(1292379603.573:7):  operation="profile_replace" pid=1066 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Dec 14 21:20:03 server kernel: [   20.498503] type=1505 audit(1292379603.573:8):  operation="profile_replace" pid=1066 name="/usr/lib/connman/scripts/dhclient-script"
Dec 14 21:20:03 server kernel: [   20.632840] type=1505 audit(1292379603.714:9):  operation="profile_load" pid=1067 name="/usr/bin/freshclam"
Dec 14 21:20:03 server kernel: [   20.676606] type=1505 audit(1292379603.754:10):  operation="profile_load" pid=1069 name="/usr/sbin/mysqld"
Dec 14 21:20:03 server kernel: [   20.722185] type=1505 audit(1292379603.804:11):  operation="profile_replace" pid=1074 name="/usr/sbin/ntpd"
Dec 14 21:20:03 server kernel: [   20.889281] type=1505 audit(1292379603.963:12):  operation="profile_load" pid=1075 name="/usr/sbin/slapd"
Dec 14 21:20:04 server kernel: [   20.943291] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Dec 14 21:20:04 server kernel: [   20.973109] type=1505 audit(1292379604.053:13):  operation="profile_load" pid=1076 name="/usr/sbin/tcpdump"
Dec 14 21:20:04 server kernel: [   21.060011] eth0: no IPv6 routers present
Dec 14 21:20:05 server cron[1121]: (CRON) INFO (pidfile fd = 3)
Dec 14 21:20:05 server acpid: starting up with proc fs
Dec 14 21:20:05 server init: apport pre-start process (1117) terminated with status 1
Dec 14 21:20:05 server init: apport post-stop process (1140) terminated with status 1
Dec 14 21:20:05 server cron[1146]: (CRON) STARTUP (fork ok)
Dec 14 21:20:06 server acpid: 1 rule loaded
Dec 14 21:20:06 server acpid: waiting for events: event logging is off
Dec 14 21:20:06 server cron[1146]: (CRON) INFO (Running @reboot jobs)
Dec 14 21:20:06 server avahi-daemon[1184]: Found user 'avahi' (UID 107) and group 'avahi' (GID 116).
Dec 14 21:20:06 server avahi-daemon[1184]: Successfully dropped root privileges.
Dec 14 21:20:06 server avahi-daemon[1184]: avahi-daemon 0.6.25 starting up.
Dec 14 21:20:06 server avahi-daemon[1184]: Successfully called chroot().
Dec 14 21:20:06 server avahi-daemon[1184]: Successfully dropped remaining capabilities.
Dec 14 21:20:06 server avahi-daemon[1184]: No service file found in /etc/avahi/services.
Dec 14 21:20:07 server avahi-daemon[1184]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Dec 14 21:20:07 server avahi-daemon[1184]: New relevant interface eth0.IPv4 for mDNS.
Dec 14 21:20:07 server avahi-daemon[1184]: Network interface enumeration completed.
Dec 14 21:20:07 server avahi-daemon[1184]: Registering new address record for fe80::21f:d0ff:fe27:536d on eth0.*.
Dec 14 21:20:07 server avahi-daemon[1184]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Dec 14 21:20:07 server avahi-daemon[1184]: Registering HINFO record with values 'X86_64'/'LINUX'.
Dec 14 21:20:07 server slapd[1170]: @(#) $OpenLDAP: slapd 2.4.21 (Aug 10 2010 17:08:36) $#012#011buildd@yellow:/build/buildd/openldap-2.4.21/debian/build/servers/slapd
Dec 14 21:20:07 server kernel: [   24.335325] type=1505 audit(1292379607.414:14):  operation="profile_replace" pid=1186 name="/usr/sbin/mysqld"
Dec 14 21:20:07 server avahi-daemon[1184]: Server startup complete. Host name is server.local. Local service cookie is 2292651374.
Dec 14 21:20:08 server slapd[1195]: hdb_db_open: database "dc=server,dc=home": unclean shutdown detected; attempting recovery.
Dec 14 21:20:13 server /etc/mysql/debian-start[1330]: Upgrading MySQL tables if necessary.
Dec 14 21:20:13 server /etc/mysql/debian-start[1333]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Dec 14 21:20:13 server /etc/mysql/debian-start[1333]: Looking for 'mysql' as: /usr/bin/mysql
Dec 14 21:20:13 server /etc/mysql/debian-start[1333]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Dec 14 21:20:13 server /etc/mysql/debian-start[1333]: This installation of MySQL is already upgraded to 5.1.41, use --force if you still need to run mysql_upgrade
Dec 14 21:20:13 server /etc/mysql/debian-start[1340]: Checking for insecure root accounts.
Dec 14 21:20:13 server /etc/mysql/debian-start[1344]: Triggering myisam-recover for all MyISAM tables
Dec 14 21:20:14 server slapd[1195]: slapd starting
Dec 14 21:20:14 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:20:14 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:20:14 server exportfs[1402]: No host name given with /export/judyVideo (anonuid=1001,anongid=1001,insecure,no_subtree_check,rw,nohide), suggest *(anonuid=1001,anongid=1001,insecure,no_subtree_check,rw,nohide) to avoid warning
Dec 14 21:20:14 server kernel: [   31.528130] svc: failed to register lockdv1 RPC service (errno 97).
Dec 14 21:20:14 server kernel: [   31.528786] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Dec 14 21:20:14 server kernel: [   31.575179] NFSD: starting 90-second grace period
Dec 14 21:20:14 server pptpd[1428]: MGR: Maximum of 100 connections reduced to 55, not enough IP addresses given
Dec 14 21:20:14 server pptpd[1429]: MGR: Manager process started
Dec 14 21:20:14 server pptpd[1429]: MGR: Maximum of 55 connections available
Dec 14 21:20:15 server slapd[1195]: connection_read(17): no connection!
Dec 14 21:20:15 server slapd[1195]: connection_read(17): no connection!
Dec 14 21:20:26 server kernel: [   43.234876] vboxdrv: Found 2 processor cores.
Dec 14 21:20:26 server kernel: [   43.234940] VBoxDrv: dbg - g_abExecMemory=ffffffffa03cbd00
Dec 14 21:20:26 server kernel: [   43.234954] vboxdrv: fAsync=0 offMin=0x1ae offMax=0x61d
Dec 14 21:20:26 server kernel: [   43.234994] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Dec 14 21:20:26 server kernel: [   43.234996] vboxdrv: Successfully loaded version 3.2.12 (interface 0x00140001).
Dec 14 21:20:27 server sm-mta[1582]: starting daemon (8.14.3): SMTP+queueing@00:10:00
Dec 14 21:20:30 server apcupsd[1628]: apcupsd 3.14.6 (16 May 2009) debian startup succeeded
Dec 14 21:20:30 server apcupsd[1628]: NIS server startup succeeded
Dec 14 21:20:32 server kernel: [   49.536645] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec 14 21:20:33 server sendmail[1743]: oBF2KWKj001743: from=fail2ban, size=147, class=0, nrcpts=1, msgid=<201012150220.oBF2KWKj001743@server.home>, relay=root@localhost
Dec 14 21:20:33 server sm-mta[1744]: oBF2KXk6001744: from=<fail2ban@server.home>, size=396, class=0, nrcpts=1, msgid=<201012150220.oBF2KWKj001743@server.home>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Dec 14 21:20:33 server sendmail[1743]: oBF2KWKj001743: to=root@localhost, delay=00:00:01, xdelay=00:00:00, mailer=relay, pri=30147, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (oBF2KXk6001744 Message accepted for delivery)
Dec 14 21:20:33 server slapd[1195]: connection_read(17): no connection!
Dec 14 21:20:33 server slapd[1195]: connection_read(17): no connection!
Dec 14 21:20:33 server slapd[1195]: connection_read(20): no connection!
Dec 14 21:20:33 server slapd[1195]: connection_read(20): no connection!
```

---

