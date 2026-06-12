---
title: "Problems with running 3D games(LOG INCLUDED)"
date: 2010-08-10
forum: General Help
---

### Post by staar2 on 2010-08-10
I made clean install to xubuntu 10.04 + i also installed a game Regnum online, installing worked, updating worked, but soon as i start the game loading it stops in the middle and crashes + also kills the firefox.

Same behaviour has with Wurm online java game. But not killing the ff. I tried the Runescape OpenGL based and worked fine. Am I missing some packages ?

Using AMD fx-55, video nvida geforce 7950GT, 1gig ram.

dmesg

[HTML]
[    3.584801]  sda: sda1
[    3.590775] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.896022] ata4: SATA link down (SStatus 0 SControl 300)
[    4.059365] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   13.060639] udev: starting version 151
[   13.145911] lp: driver loaded but no devices found
[   13.196848] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[   13.196867] i2c i2c-1: nForce2 SMBus adapter at 0x1c40
[   13.198425] vga16fb: initializing
[   13.198428] vga16fb: mapped to 0xc00a0000
[   13.198491] fb0: VGA16 VGA frame buffer device
[   13.361979] Linux agpgart interface v0.103
[   13.521762] type=1505 audit(1281423017.011:2):  operation="profile_load" pid=615 name="/sbin/dhclient3"
[   13.521994] type=1505 audit(1281423017.011:3):  operation="profile_load" pid=615 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.522122] type=1505 audit(1281423017.011:4):  operation="profile_load" pid=615 name="/usr/lib/connman/scripts/dhclient-script"
[   13.960074] type=1505 audit(1281423017.451:5):  operation="profile_replace" pid=704 name="/sbin/dhclient3"
[   13.960335] type=1505 audit(1281423017.451:6):  operation="profile_replace" pid=704 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.960476] type=1505 audit(1281423017.451:7):  operation="profile_replace" pid=704 name="/usr/lib/connman/scripts/dhclient-script"
[   13.966471] type=1505 audit(1281423017.455:8):  operation="profile_load" pid=705 name="/usr/bin/evince"
[   13.969784] type=1505 audit(1281423017.459:9):  operation="profile_load" pid=705 name="/usr/bin/evince-previewer"
[   13.971563] type=1505 audit(1281423017.459:10):  operation="profile_load" pid=705 name="/usr/bin/evince-thumbnailer"
[   13.979581] type=1505 audit(1281423017.467:11):  operation="profile_load" pid=708 name="/usr/lib/cups/backend/cups-pdf"
[   14.078600] nvidia: module license 'NVIDIA' taints kernel.
[   14.078605] Disabling lock debugging due to kernel taint
[   14.873145] skge eth0: enabling interface
[   14.890093] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.926195] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   14.926200]   alloc irq_desc for 19 on node -1
[   14.926203]   alloc kstat_irqs on node -1
[   14.926211] SB-XFi 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[   15.285778] Console: switching to colour frame buffer device 80x30
[   15.382562] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   15.382569]   alloc irq_desc for 17 on node -1
[   15.382571]   alloc kstat_irqs on node -1
[   15.382581] nvidia 0000:02:00.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   15.382588] nvidia 0000:02:00.0: setting latency timer to 64
[   15.383497] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
[   15.491527] ppdev: user-space parallel port driver
[   25.620016] eth1: no IPv6 routers present
[  717.764453] __ratelimit: 6 callbacks suppressed
[  717.764457] game invoked oom-killer: gfp_mask=0x280da, order=0, oom_adj=0
[  717.764461] game cpuset=/ mems_allowed=0
[  717.764465] Pid: 1841, comm: game Tainted: P           2.6.32-24-generic #38-Ubuntu
[  717.764467] Call Trace:
[  717.764478]  [<c01cd1f4>] oom_kill_process+0xa4/0x2b0
[  717.764482]  [<c01cd869>] ? select_bad_process+0xa9/0xe0
[  717.764485]  [<c01cd8f1>] __out_of_memory+0x51/0xa0
[  717.764488]  [<c01cd998>] out_of_memory+0x58/0xb0
[  717.764491]  [<c01d01a7>] __alloc_pages_slowpath+0x407/0x4a0
[  717.764494]  [<c01d037a>] __alloc_pages_nodemask+0x13a/0x170
[  717.764498]  [<c01e33a0>] do_anonymous_page+0x100/0x270
[  717.764502]  [<c013052c>] ? kmap_atomic_prot+0x4c/0xf0
[  717.764504]  [<c01e6e48>] handle_mm_fault+0x338/0x390
[  717.764508]  [<c058ac2c>] ? schedule+0x44c/0x840
[  717.764512]  [<c058f19d>] do_page_fault+0x10d/0x3a0
[  717.764515]  [<c058f090>] ? do_page_fault+0x0/0x3a0
[  717.764518]  [<c058d093>] error_code+0x73/0x80
[  717.764520] Mem-Info:
[  717.764522] DMA per-cpu:
[  717.764523] CPU    0: hi:    0, btch:   1 usd:   0
[  717.764525] Normal per-cpu:
[  717.764527] CPU    0: hi:  186, btch:  31 usd: 153
[  717.764528] HighMem per-cpu:
[  717.764530] CPU    0: hi:   42, btch:   7 usd:   6
[  717.764534] active_anon:212985 inactive_anon:24975 isolated_anon:0
[  717.764535]  active_file:39 inactive_file:48 isolated_file:0
[  717.764536]  unevictable:0 dirty:0 writeback:0 unstable:0
[  717.764537]  free:3018 slab_reclaimable:1493 slab_unreclaimable:2560
[  717.764538]  mapped:6403 shmem:1283 pagetables:1374 bounce:0
[  717.764544] DMA free:4060kB min:64kB low:80kB high:96kB active_anon:3256kB inactive_anon:1180kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15804kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:8kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
[  717.764548] lowmem_reserve[]: 0 865 999 999
[  717.764555] Normal free:7900kB min:3728kB low:4660kB high:5592kB active_anon:780248kB inactive_anon:30208kB active_file:88kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:0kB mapped:25260kB shmem:4796kB slab_reclaimable:5972kB slab_unreclaimable:10232kB kernel_stack:1976kB pagetables:5152kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:453 all_unreclaimable? yes
[  717.764560] lowmem_reserve[]: 0 0 1070 1070
[  717.764566] HighMem free:112kB min:132kB low:276kB high:420kB active_anon:68436kB inactive_anon:68512kB active_file:68kB inactive_file:192kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:137040kB mlocked:0kB dirty:0kB writeback:0kB mapped:352kB shmem:336kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:344kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:192 all_unreclaimable? no
[  717.764571] lowmem_reserve[]: 0 0 0 0
[  717.764574] DMA: 1*4kB 1*8kB 1*16kB 0*32kB 1*64kB 3*128kB 2*256kB 2*512kB 2*1024kB 0*2048kB 0*4096kB = 4060kB
[  717.764581] Normal: 967*4kB 0*8kB 0*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 7900kB
[  717.764588] HighMem: 0*4kB 0*8kB 1*16kB 1*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 112kB
[  717.764595] 1381 total pagecache pages
[  717.764596] 0 pages in swap cache
[  717.764598] Swap cache stats: add 0, delete 0, find 0/0
[  717.764599] Free swap  = 0kB
[  717.764600] Total swap = 0kB
[  717.769129] 261840 pages RAM
[  717.769131] 34530 pages HighMem
[  717.769132] 5513 pages reserved
[  717.769133] 8480 pages shared
[  717.769135] 246288 pages non-shared
[  717.769138] Out of memory: kill process 1429 (run-mozilla.sh) score 428313 or a child
[  717.769141] Killed process 1433 (firefox-bin)
[  722.739437] game invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
[  722.739443] game cpuset=/ mems_allowed=0
[  722.739447] Pid: 1841, comm: game Tainted: P           2.6.32-24-generic #38-Ubuntu
[  722.739453] Call Trace:
[  722.739463]  [<c01cd1f4>] oom_kill_process+0xa4/0x2b0
[  722.739467]  [<c01cd869>] ? select_bad_process+0xa9/0xe0
[  722.739470]  [<c01cd8f1>] __out_of_memory+0x51/0xa0
[  722.739473]  [<c01cd998>] out_of_memory+0x58/0xb0
[  722.739476]  [<c01d01a7>] __alloc_pages_slowpath+0x407/0x4a0
[  722.739479]  [<c01d037a>] __alloc_pages_nodemask+0x13a/0x170
[  722.739483]  [<c01d29ba>] __do_page_cache_readahead+0xea/0x200
[  722.739486]  [<c01d2af6>] ra_submit+0x26/0x30
[  722.739489]  [<c01ccaec>] filemap_fault+0x3dc/0x410
[  722.739492]  [<c01e5040>] __do_fault+0x40/0x490
[  722.739498]  [<c03502d4>] ? rb_erase+0xb4/0x120
[  722.739501]  [<c01e6c49>] handle_mm_fault+0x139/0x390
[  722.739506]  [<c058f19d>] do_page_fault+0x10d/0x3a0
[  722.739509]  [<c058f090>] ? do_page_fault+0x0/0x3a0
[  722.739512]  [<c058d093>] error_code+0x73/0x80
[  722.739514] Mem-Info:
[  722.739516] DMA per-cpu:
[  722.739517] CPU    0: hi:    0, btch:   1 usd:   0
[  722.739519] Normal per-cpu:
[  722.739521] CPU    0: hi:  186, btch:  31 usd:  30
[  722.739522] HighMem per-cpu:
[  722.739524] CPU    0: hi:   42, btch:   7 usd:  27
[  722.739528] active_anon:212076 inactive_anon:25967 isolated_anon:0
[  722.739529]  active_file:82 inactive_file:193 isolated_file:0
[  722.739530]  unevictable:0 dirty:2 writeback:0 unstable:0
[  722.739531]  free:3023 slab_reclaimable:1487 slab_unreclaimable:2540
[  722.739532]  mapped:6432 shmem:1267 pagetables:1252 bounce:0
[  722.739538] DMA free:4060kB min:64kB low:80kB high:96kB active_anon:3260kB inactive_anon:1180kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15804kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:8kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
[  722.739542] lowmem_reserve[]: 0 865 999 999
[  722.739549] Normal free:7920kB min:3728kB low:4660kB high:5592kB active_anon:776448kB inactive_anon:34048kB active_file:288kB inactive_file:772kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:8kB writeback:0kB mapped:25380kB shmem:4732kB slab_reclaimable:5948kB slab_unreclaimable:10152kB kernel_stack:1864kB pagetables:4664kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:1056 all_unreclaimable? yes
[  722.739554] lowmem_reserve[]: 0 0 1070 1070
[  722.739560] HighMem free:112kB min:132kB low:276kB high:420kB active_anon:68596kB inactive_anon:68640kB active_file:40kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:137040kB mlocked:0kB dirty:0kB writeback:0kB mapped:348kB shmem:336kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:344kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:99 all_unreclaimable? yes
[  722.739565] lowmem_reserve[]: 0 0 0 0
[  722.739567] DMA: 1*4kB 1*8kB 1*16kB 0*32kB 1*64kB 3*128kB 2*256kB 2*512kB 2*1024kB 0*2048kB 0*4096kB = 4060kB
[  722.739575] Normal: 972*4kB 0*8kB 0*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 7920kB
[  722.739581] HighMem: 0*4kB 0*8kB 1*16kB 1*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 112kB
[  722.739588] 1553 total pagecache pages
[  722.739590] 0 pages in swap cache
[  722.739591] Swap cache stats: add 0, delete 0, find 0/0
[  722.739593] Free swap  = 0kB
[  722.739594] Total swap = 0kB
[  722.744171] 261840 pages RAM
[  722.744172] 34530 pages HighMem
[  722.744174] 5513 pages reserved
[  722.744175] 8885 pages shared
[  722.744176] 246357 pages non-shared
[  722.744179] Out of memory: kill process 1841 (game) score 215699 or a child
[  722.744182] Killed process 1841 (game)

[/HTML]

---

### Post by Autonomous_user on 2010-08-10
I didnt read your data, but what driver did you install for your video card?

---

### Post by snek on 2010-08-10
Looking at the last few lines it looks like you don't have a swap partition enabled and the computer is running out of RAM.
Basically, the computer runs out of RAM and then tries to copy some of the data in RAM to a seperate partition on the HDD. 
However, since you don't have swap space things start to crash.

You can find more information on swap [here]("https://help.ubuntu.com/community/SwapFaq").

Out of interest, and just to verify this, can you run the command "free -m" and put the results here? 
That would show if you have any swap space, and how much RAM your machine has in total and is available to applications.

Did you let Ubuntu configure your partitions automatically or did you do it manually?
Swap space should normally be created by the installer.

---

### Post by staar2 on 2010-08-10
Yes as I also read the log i saw the swamp usage is 0, so I started to make swamp partition, but accidently i formated my wrong partition so i now changed to kubuntu + now i got swamp also. Ty ill try to install the game also.

---

