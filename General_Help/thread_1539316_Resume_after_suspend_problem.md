---
title: "Resume after suspend problem"
date: 2010-07-26
forum: General Help
---

### Post by Dimath on 2010-07-26
Sometimes my laptop fails to resume after suspend. Actually, it does resume, but the HD goes crazy reading/writing constantly and it's impossible even to type your password (everything is so slow). It happens like 30% of times.

The following messages are in the system.log, repeating million times per second in a circle:

```

Jul 26 08:45:43 dimath-laptop kernel: [26691.311564]  =======================
Jul 26 08:45:43 dimath-laptop kernel: [26691.311565] Mem-Info:
Jul 26 08:45:43 dimath-laptop kernel: [26691.311567] DMA per-cpu:
Jul 26 08:45:43 dimath-laptop kernel: [26691.311569] CPU    0: hi:    0, btch:   1 usd:   0
Jul 26 08:45:43 dimath-laptop kernel: [26691.311571] CPU    1: hi:    0, btch:   1 usd:   0
Jul 26 08:45:43 dimath-laptop kernel: [26691.311573] Normal per-cpu:
Jul 26 08:45:43 dimath-laptop kernel: [26691.311575] CPU    0: hi:  186, btch:  31 usd:  67
Jul 26 08:45:43 dimath-laptop kernel: [26691.311577] CPU    1: hi:  186, btch:  31 usd: 169
Jul 26 08:45:43 dimath-laptop kernel: [26691.311579] HighMem per-cpu:
Jul 26 08:45:43 dimath-laptop kernel: [26691.311581] CPU    0: hi:  186, btch:  31 usd:  91
Jul 26 08:45:43 dimath-laptop kernel: [26691.311584] CPU    1: hi:  186, btch:  31 usd: 178
Jul 26 08:45:43 dimath-laptop kernel: [26691.311587] Active:317838 inactive:74616 dirty:0 writeback:0 unstable:0
Jul 26 08:45:43 dimath-laptop kernel: [26691.311589]  free:32915 slab:14329 mapped:38830 pagetables:1691 bounce:0
Jul 26 08:45:43 dimath-laptop kernel: [26691.311593] DMA free:4828kB min:64kB low:80kB high:96kB active:0kB inactive:40kB present:15852kB pages_scanned:0 all_unreclaimable? no
Jul 26 08:45:43 dimath-laptop kernel: [26691.311596] lowmem_reserve[]: 0 872 2012 2012
Jul 26 08:45:43 dimath-laptop kernel: [26691.311601] Normal free:75304kB min:3744kB low:4680kB high:5616kB active:396716kB inactive:154160kB present:893200kB pages_scanned:0 all_unreclaimable? no
Jul 26 08:45:43 dimath-laptop kernel: [26691.311604] lowmem_reserve[]: 0 0 9123 9123
Jul 26 08:45:43 dimath-laptop kernel: [26691.311610] HighMem free:51528kB min:512kB low:1736kB high:2960kB active:874636kB inactive:144264kB present:1167756kB pages_scanned:0 all_unreclaimable? no
Jul 26 08:45:43 dimath-laptop kernel: [26691.311613] lowmem_reserve[]: 0 0 0 0
Jul 26 08:45:43 dimath-laptop kernel: [26691.311616] DMA: 57*4kB 77*8kB 65*16kB 34*32kB 13*64kB 4*128kB 2*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 4828kB
Jul 26 08:45:43 dimath-laptop kernel: [26691.311624] Normal: 5002*4kB 1672*8kB 1224*16kB 74*32kB 206*64kB 51*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 75304kB
Jul 26 08:45:43 dimath-laptop kernel: [26691.311633] HighMem: 3016*4kB 2343*8kB 791*16kB 130*32kB 19*64kB 9*128kB 4*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 51528kB
Jul 26 08:45:43 dimath-laptop kernel: [26691.311642] 132968 total pagecache pages
Jul 26 08:45:43 dimath-laptop kernel: [26691.311644] 1761 pages in swap cache
Jul 26 08:45:43 dimath-laptop kernel: [26691.311647] Swap cache stats: add 398790, delete 397029, find 101381/121190
Jul 26 08:45:43 dimath-laptop kernel: [26691.311650] Free swap  = 1966356kB
Jul 26 08:45:43 dimath-laptop kernel: [26691.311652] Total swap = 2000084kB
Jul 26 08:45:43 dimath-laptop kernel: [26691.321770] 523904 pages RAM
Jul 26 08:45:43 dimath-laptop kernel: [26691.321772] 294528 pages HighMem
Jul 26 08:45:43 dimath-laptop kernel: [26691.321773] 55775 pages reserved
Jul 26 08:45:43 dimath-laptop kernel: [26691.321775] 202724 pages shared
Jul 26 08:45:43 dimath-laptop kernel: [26691.321777] 367238 pages non-shared
Jul 26 08:45:43 dimath-laptop kernel: [26691.445964] pm-suspend: page allocation failure. order:7, mode:0x4020
Jul 26 08:45:43 dimath-laptop kernel: [26691.445969] Pid: 21680, comm: pm-suspend Tainted: P        W 2.6.27-17-generic #1
Jul 26 08:45:43 dimath-laptop kernel: [26691.445972]  [<c037e40b>] ? printk+0x1d/0x22
Jul 26 08:45:43 dimath-laptop kernel: [26691.445978]  [<c018a967>] __alloc_pages_internal+0x387/0x490
Jul 26 08:45:43 dimath-laptop kernel: [26691.445990]  [<f8ba3000>] ? constant_test_bit+0x0/0x30 [joydev]
Jul 26 08:45:43 dimath-laptop kernel: [26691.446007]  [<c018aad9>] __get_free_pages+0x29/0x40
Jul 26 08:45:43 dimath-laptop kernel: [26691.446010]  [<c01ae0e6>] __kmalloc+0xf6/0x100
Jul 26 08:45:43 dimath-laptop kernel: [26691.446024]  [<f8ce1d65>] KCL_MEM_SmallBufferAllocAtomic+0x15/0x20 [fglrx]
Jul 26 08:45:43 dimath-laptop kernel: [26691.446081]  [<f8cf7f7b>] firegl_save_fb+0x3b/0x1a0 [fglrx]
Jul 26 08:45:43 dimath-laptop kernel: [26691.446147]  [<f8cf7d97>] ? firegl_pm_save_framebuffer+0x1f7/0x290 [fglrx]
Jul 26 08:45:43 dimath-laptop kernel: [26691.446203]  [<f8d1717c>] ? firegl_cmmqs_recoverable_surface_info+0xbc/0xd0 [fglrx]
Jul 26 08:45:43 dimath-laptop kernel: [26691.446265]  [<f8cfa167>] ? firegl_cail_powerdown+0xa7/0x140 [fglrx]
Jul 26 08:45:43 dimath-laptop kernel: [26691.446331]  [<f8ce4b8b>] ? fglrx_pci_suspend+0x8b/0x150 [fglrx]
Jul 26 08:45:43 dimath-laptop kernel: [26691.446390]  [<c026445b>] ? pci_legacy_suspend+0x2b/0x70
Jul 26 08:45:43 dimath-laptop kernel: [26691.446396]  [<f8ce4b00>] ? fglrx_pci_suspend+0x0/0x150 [fglrx]
Jul 26 08:45:43 dimath-laptop kernel: [26691.446439]  [<c02646a8>] ? pci_pm_suspend+0xa8/0xb0
Jul 26 08:45:43 dimath-laptop kernel: [26691.446443]  [<c02c8b6a>] ? pm_op+0x11a/0x150
Jul 26 08:45:43 dimath-laptop kernel: [26691.446447]  [<c02c902c>] ? suspend_device+0x8c/0x140
Jul 26 08:45:43 dimath-laptop kernel: [26691.446451]  [<c02c9191>] ? dpm_suspend+0xb1/0x110
Jul 26 08:45:43 dimath-laptop kernel: [26691.446454]  [<c02c9212>] ? device_suspend+0x22/0x30
Jul 26 08:45:43 dimath-laptop kernel: [26691.446458]  [<c015d699>] ? suspend_devices_and_enter+0x69/0x190
Jul 26 08:45:43 dimath-laptop kernel: [26691.446462]  [<c015d991>] ? enter_state+0xd1/0x100
Jul 26 08:45:43 dimath-laptop kernel: [26691.446466]  [<c015da45>] ? state_store+0x85/0xd0
Jul 26 08:45:43 dimath-laptop kernel: [26691.446469]  [<c015d9c0>] ? state_store+0x0/0xd0
Jul 26 08:45:43 dimath-laptop kernel: [26691.446472]  [<c024f894>] ? kobj_attr_store+0x24/0x30
Jul 26 08:45:43 dimath-laptop kernel: [26691.446477]  [<c02004c7>] ? sysfs_write_file+0x97/0x100
Jul 26 08:45:43 dimath-laptop kernel: [26691.446481]  [<c01b2ed0>] ? vfs_write+0xa0/0x110
Jul 26 08:45:43 dimath-laptop kernel: [26691.446485]  [<c0200430>] ? sysfs_write_file+0x0/0x100
Jul 26 08:45:43 dimath-laptop kernel: [26691.446489]  [<c01b3012>] ? sys_write+0x42/0x70
Jul 26 08:45:43 dimath-laptop kernel: [26691.446492]  [<c0103f7b>] ? sysenter_do_call+0x12/0x2f
Jul 26 08:45:43 dimath-laptop kernel: [26691.446497]  [<c0380000>] ? account_scheduler_latency+0x40/0x220
Jul 26 08:45:43 dimath-laptop kernel: [26691.446501]  =======================

```


My system:
Ubuntu 8.10, 2.6.27.17-generic kernel
ACER 5670 laptop

Does anyone knows what it can be, or how to fix it? Thanks!

---

### Post by P4man on 2010-07-26
Looks similar to this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290184](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290184)

The poster of that bug wrote in 2008 it longer happened to him; so I assume you ran all updates?

---

