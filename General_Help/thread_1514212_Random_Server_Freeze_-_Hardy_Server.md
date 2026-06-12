---
title: "Random Server Freeze - Hardy Server"
date: 2010-06-20
forum: General Help
---

### Post by YorYor on 2010-06-20
Hi,

I've recently been getting random freezes while the server is in use.
The most recent crash finally left a debug in syslog which I could grab.
Wonder if anyone could help shed some light on which area I should check on? Is it the memory, is it the harddisk, or is it a power supply problem? I ran a very quick memtest on the RAM (doing only the first test on the whole memory range, since errors usually turn up during the first test), but no errors were detected.

CPUs: Dual Opteron 275s
Memory: 14GB DDR-400 Reg ECC with ECC and Chipkill on
HDD: 4 x SATA2
- RAID1 for /
- RAID10 for one mounted folder for all data files
- RAID1 for swap
Kernel: 2.6.24-27-openvz
* I was getting freezes on 28-openvz as well, and thought it might be a kernel issue.

```
Jun 21 02:33:18 vz1 kernel: [63154.056818] Unable to handle kernel paging request at 0000000000001550 RIP:
Jun 21 02:33:18 vz1 kernel: [63154.056838]  [ide_core:_spin_lock_irqsave+0x3/0x30] _spin_lock_irqsave+0x3/0x30
Jun 21 02:33:18 vz1 kernel: [63154.056905] PGD 0
Jun 21 02:33:18 vz1 kernel: [63154.056925] Oops: 0002 [1] SMP
Jun 21 02:33:18 vz1 kernel: [63154.056949] CPU: 2
Jun 21 02:33:18 vz1 kernel: [63154.056970] Modules linked in: vzethdev vznetdev simfs vzrst vzcpt vzdquota vzmon vzdev ipt_iprange nf_nat_ftp xt_length ipt_$
Jun 21 02:33:18 vz1 kernel: al processor fan fuse
Jun 21 02:33:18 vz1 kernel: [63154.057415] Pid: 10269, comm: pidgin Not tainted 2.6.24-27-openvz #1 ovz005
Jun 21 02:33:18 vz1 kernel: [63154.057444] RIP: 0010:[ide_core:_spin_lock_irqsave+0x3/0x30]  [ide_core:_spin_lock_irqsave+0x3/0x30] _spin_lock_irqsave+0x3/0$
Jun 21 02:33:18 vz1 kernel: [63154.057490] RSP: 0000:ffff81020091bdf0  EFLAGS: 00010006
Jun 21 02:33:18 vz1 kernel: [63154.057516] RAX: 0000000000000006 RBX: ffff8103162bf7f0 RCX: 0000000000000020
Jun 21 02:33:18 vz1 kernel: [63154.057546] RDX: 0000000000000020 RSI: 0000000000000000 RDI: 0000000000001550
Jun 21 02:33:18 vz1 kernel: [63154.057576] RBP: 0000000000001500 R08: ffff810154f36e98 R09: 00000000fffffff8
Jun 21 02:33:18 vz1 kernel: [63154.057607] R10: 000000000001812f R11: 000000000000060c R12: 0000000000001550
Jun 21 02:33:18 vz1 kernel: [63154.057637] R13: 0000000000000020 R14: 0000000000000000 R15: ffff81020091bec0
Jun 21 02:33:18 vz1 kernel: [63154.057668] FS:  00007fa566ace6e0(0000) GS:ffff8103778de300(0000) knlGS:00000000b675f750
Jun 21 02:33:18 vz1 kernel: [63154.057714] CS:  0010 DS: 002b ES: 002b CR0: 000000008005003b
Jun 21 02:33:18 vz1 kernel: [63154.057742] CR2: 0000000000001550 CR3: 0000000000201000 CR4: 00000000000006e0
Jun 21 02:33:18 vz1 kernel: [63154.057772] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 21 02:33:18 vz1 kernel: [63154.057803] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun 21 02:33:18 vz1 kernel: [63154.057835] Process pidgin (pid: 10269, veid=10175, threadinfo ffff81020091a000, task ffff810200242000)
Jun 21 02:33:18 vz1 kernel: [63154.057883] Stack:  ffffffff80261132 ffff8103162bf7f0 ffff8101f7c03c00 ffff81037d1fba00
Jun 21 02:33:18 vz1 kernel: [63154.057930]  ffff8101f7c03c00 ffffffff802a51f1 ffffffff80262281 ffff8101f7c03c00
Jun 21 02:33:18 vz1 kernel: [63154.057977]  0000000000000287 ffff8102c7ee8fc0 ffffffff802bc36f ffff8102fad19f20
Jun 21 02:33:18 vz1 kernel: [63154.058008] Call Trace:
Jun 21 02:33:18 vz1 kernel: [63154.058047]  [x_tables:uncharge_beancounter+0x22/0x3b0] uncharge_beancounter+0x22/0x60
Jun 21 02:33:18 vz1 kernel: [63154.058081]  [free_pgtables+0x61/0xe0] free_pgtables+0x61/0xe0
Jun 21 02:33:18 vz1 kernel: [63154.058108]  [ub_slab_uncharge+0x31/0x60] ub_slab_uncharge+0x31/0x60
Jun 21 02:33:18 vz1 kernel: [63154.058140]  [nf_conntrack:kmem_cache_free+0xaf/0x180] kmem_cache_free+0xaf/0xe0
Jun 21 02:33:18 vz1 kernel: [63154.058172]  [free_pgtables+0x61/0xe0] free_pgtables+0x61/0xe0
Jun 21 02:33:18 vz1 kernel: [63154.058205]  [exit_mmap+0x92/0x100] exit_mmap+0x92/0x100
Jun 21 02:33:18 vz1 kernel: [63154.058236]  [mmput+0x1e/0xd0] mmput+0x1e/0xd0
Jun 21 02:33:18 vz1 kernel: [63154.058263]  [do_exit+0x1af/0x9f0] do_exit+0x1af/0x9f0
Jun 21 02:33:18 vz1 kernel: [63154.058295]  [fuse:mntput_no_expire+0x27/0x4ee0] mntput_no_expire+0x27/0xb0
Jun 21 02:33:18 vz1 kernel: [63154.058329]  [do_group_exit+0x2c/0x80] do_group_exit+0x2c/0x80
Jun 21 02:33:18 vz1 kernel: [63154.058360]  [ia32_sysret+0x0/0x05] ia32_sysret+0x0/0x5
Jun 21 02:33:18 vz1 kernel: [63154.058398]
Jun 21 02:33:18 vz1 kernel: [63154.058416]
Jun 21 02:33:18 vz1 kernel: [63154.058416] Code: f0 ff 0f 79 1b a9 00 02 00 00 74 0b fb f3 90 83 3f 00 7e f9
Jun 21 02:33:18 vz1 kernel: [63154.058499] RIP  [ide_core:_spin_lock_irqsave+0x3/0x30] _spin_lock_irqsave+0x3/0x30
Jun 21 02:33:18 vz1 kernel: [63154.058528]  RSP <ffff81020091bdf0>
Jun 21 02:33:18 vz1 kernel: [63154.058550] CR2: 0000000000001550
Jun 21 02:33:18 vz1 kernel: [63154.058731] ---[ end trace 14baaba38d3dde08 ]---
Jun 21 02:33:18 vz1 kernel: [63154.058776] Fixing recursive fault but reboot is needed!
```

---

