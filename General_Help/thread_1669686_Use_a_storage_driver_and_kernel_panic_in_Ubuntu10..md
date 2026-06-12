---
title: "Use a storage driver and kernel panic in Ubuntu10.04 x64 : ("
date: 2011-01-18
forum: General Help
---

### Post by dirk.chen on 2011-01-18
Dears,

I use a raid driver in Ubuntu 10.04 x64 (kernel 2.6.32), system show kernel panic after I do some RAID operation. (But normal READ /WRITE work fine.)

But I do the same operation and the same version raid driver in older Linux OS (Ex. RHEL 5, SLES 11 ), it works fine!!!

I have no idea so far, can anyone give some suggestion??

**[ kernel panic code stack ]**

root@ubuntu:~# [153858.655419] BUG: scheduling while atomic: smbd/8053/0xffffffff
[153858.672677] BUG: unable to handle kernel paging request at fffffffb8e5de780
[153858.682650] IP: [<ffffffff8105b584>] update_curr+0x124/0x1e0
[153858.682650] PGD 1003067 PUD 0 
[153858.682650] Thread overran stack, or stack corrupted
[153858.682650] Oops: 0000 [#1] SMP 
[153858.682650] last sysfs file: /sys/devices/system/cpu/cpu11/cache/index2/shared_cpu_map
[153858.682650] CPU 0 
[153858.682650] Modules linked in: ahci(P) binfmt_misc ppdev fbcon tileblit font bitblit softcursor vga16fb i2c_piix4 vgastate edac_core edac_mce_amd psmouse serio_raw lp parport ohci1394 dm_raid45 usbhid hid sata_promise ieee1394 pata_atiixp e1000e xor [last unloaded: ahci]
[153858.682650] Pid: 8053, comm: smbd Tainted: P           2.6.32-21-server #32-Ubuntu System Product Name
[153858.682650] RIP: 0010:[<ffffffff8105b584>]  [<ffffffff8105b584>] update_curr+0x124/0x1e0
[153858.682650] RSP: 0018:ffff880003c03d88  EFLAGS: 00010086
[153858.682650] RAX: ffff880077a6ade0 RBX: ffffffff819b0600 RCX: ffff88007b803700
[153858.682650] RDX: 00000000000186b0 RSI: 0000000000000000 RDI: ffff880077a6ae18
[153858.682650] RBP: ffff880003c03db8 R08: 0000000000000b40 R09: 000000000000000f
[153858.682650] R10: 0000000000000001 R11: 0000000000000000 R12: 0000000000000001
[153858.682650] R13: 0000000000000000 R14: 00000000010ad8fc R15: 0000000000015bc0
[153858.682650] FS:  00007f8d5b3bd720(0000) GS:ffff880003c00000(0000) knlGS:0000000000000000
[153858.682650] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[153858.682650] CR2: fffffffb8e5de780 CR3: 0000000077937000 CR4: 00000000000006f0
[153858.682650] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[153858.682650] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[153858.682650] Process smbd (pid: 8053, threadinfo ffff880066a26000, task ffff880077a6ade0)
[153858.682650] Stack:
[153858.682650]  ffff880003c03d98 ffffffff8105b292 ffff880077a6ae18 ffff880003c15c30
[153858.682650] <0> 0000000000000000 0000000000000000 ffff880003c03de8 ffffffff8105b667
[153858.682650] <0> ffff880003c03dd8 ffff880077a6ae18 0000000000000000 ffff880077a6ade0
[153858.682650] Call Trace:
[153858.682650]  <IRQ> 
[153858.682650]  [<ffffffff8105b292>] ? default_wake_function+0x12/0x20
[153858.682650]  [<ffffffff8105b667>] entity_tick+0x27/0x140
[153858.682650]  [<ffffffff8105b7b2>] task_tick_fair+0x32/0x50
[153858.682650]  [<ffffffff8105a3fd>] scheduler_tick+0xed/0x260
[153858.682650]  [<ffffffff8155c615>] ? do_IRQ+0x75/0xf0
[153858.682650]  [<ffffffff810944e0>] ? tick_sched_timer+0x0/0xc0
[153858.682650]  [<ffffffff81076e12>] update_process_times+0x52/0x70
[153858.682650]  [<ffffffff81094546>] tick_sched_timer+0x66/0xc0
[153858.682650]  [<ffffffff810887df>] __run_hrtimer+0x8f/0x1a0
[153858.682650]  [<ffffffff810c4880>] ? handle_IRQ_event+0x60/0x170
[153858.682650]  [<ffffffff81019e69>] ? read_tsc+0x9/0x20
[153858.682650]  [<ffffffff81088b76>] hrtimer_interrupt+0xd6/0x220
[153858.682650]  [<ffffffff8155c6fc>] smp_apic_timer_interrupt+0x6c/0x9c
[153858.682650]  [<ffffffff81013cb3>] apic_timer_interrupt+0x13/0x20
[153858.682650]  <EOI> 
[153858.682650]  [<ffffffff8106795c>] ? vprintk+0x1cc/0x470
[153858.682650]  [<ffffffff81554926>] ? printk+0x41/0x43
[153858.682650]  [<ffffffff810585d4>] ? __schedule_bug+0x54/0x90
[153858.682650]  [<ffffffff8155535f>] ? thread_return+0x1ff/0x420
[153858.682650]  [<ffffffff81143e52>] ? sys_pread64+0x82/0xa0
[153858.682650]  [<ffffffff8101322a>] ? sysret_careful+0x14/0x17
[153858.682650] Code: 00 44 8b 25 13 87 77 00 45 85 e4 74 32 48 8b 50 08 8b 5a 18 48 8b 90 e0 06 00 00 48 8b 4a 50 48 85 c9 74 1b 48 63 db 48 8b 51 20 <48> 03 14 dd 80 b7 85 81 4c 01 32 48 8b 49 78 48 85 c9 75 e8 4c 
[153858.682650] RIP  [<ffffffff8105b584>] update_curr+0x124/0x1e0
[153858.682650]  RSP <ffff880003c03d88>
[153858.682650] CR2: fffffffb8e5de780
[153858.682650] ---[ end trace 53f8b3858a14deca ]---
[153858.682650] Kernel panic - not syncing: Fatal exception in interrupt
[153858.682650] Pid: 8053, comm: smbd Tainted: P      D    2.6.32-21-server #32-Ubuntu
[153858.682650] Call Trace:
[153858.682650]  <IRQ>  [<ffffffff81554826>] panic+0x78/0x137
[153858.682650]  [<ffffffff815585ca>] oops_end+0xea/0xf0
[153858.682650]  [<ffffffff810409d3>] no_context+0xf3/0x190
[153858.682650]  [<ffffffff81040b95>] __bad_area_nosemaphore+0x125/0x1e0
[153858.682650]  [<ffffffff81040c63>] bad_area_nosemaphore+0x13/0x20
[153858.682650]  [<ffffffff8155a164>] do_page_fault+0x2e4/0x3b0
[153858.682650]  [<ffffffff81557905>] page_fault+0x25/0x30
[153858.682650]  [<ffffffff8105b584>] ? update_curr+0x124/0x1e0
[153858.682650]  [<ffffffff8105b546>] ? update_curr+0xe6/0x1e0
[153858.682650]  [<ffffffff8105b292>] ? default_wake_function+0x12/0x20
[153858.682650]  [<ffffffff8105b667>] entity_tick+0x27/0x140
[153858.682650]  [<ffffffff8105b7b2>] task_tick_fair+0x32/0x50
[153858.682650]  [<ffffffff8105a3fd>] scheduler_tick+0xed/0x260
[153858.682650]  [<ffffffff8155c615>] ? do_IRQ+0x75/0xf0
[153858.682650]  [<ffffffff810944e0>] ? tick_sched_timer+0x0/0xc0
[153858.682650]  [<ffffffff81076e12>] update_process_times+0x52/0x70
[153858.682650]  [<ffffffff81094546>] tick_sched_timer+0x66/0xc0
[153858.682650]  [<ffffffff810887df>] __run_hrtimer+0x8f/0x1a0
[153858.682650]  [<ffffffff810c4880>] ? handle_IRQ_event+0x60/0x170
[153858.682650]  [<ffffffff81019e69>] ? read_tsc+0x9/0x20
[153858.682650]  [<ffffffff81088b76>] hrtimer_interrupt+0xd6/0x220
[153858.682650]  [<ffffffff8155c6fc>] smp_apic_timer_interrupt+0x6c/0x9c
[153858.682650]  [<ffffffff81013cb3>] apic_timer_interrupt+0x13/0x20
[153858.682650]  <EOI>  [<ffffffff8106795c>] ? vprintk+0x1cc/0x470
[153858.682650]  [<ffffffff81554926>] ? printk+0x41/0x43
[153858.682650]  [<ffffffff810585d4>] ? __schedule_bug+0x54/0x90
[153858.682650]  [<ffffffff8155535f>] ? thread_return+0x1ff/0x420
[153858.682650]  [<ffffffff81143e52>] ? sys_pread64+0x82/0xa0
[153858.682650]  [<ffffffff8101322a>] ? sysret_careful+0x14/0x17

---

### Post by NickD-NLUG on 2011-09-18
> **dirk.chen said:**
> Dears,

I use a raid driver in Ubuntu 10.04 x64 (kernel 2.6.32), system show kernel panic after I do some RAID operation. (But normal READ /WRITE work fine.)

But I do the same operation and the same version raid driver in older Linux OS (Ex. RHEL 5, SLES 11 ), it works fine!!!

I have no idea so far, can anyone give some suggestion??

**[ kernel panic code stack ]**

root@ubuntu:~# [153858.655419] BUG: scheduling while atomic: smbd/8053/0xffffffff
[153858.672677] BUG: unable to handle kernel paging request at fffffffb8e5de780
[153858.682650] IP: [<ffffffff8105b584>] update_curr+0x124/0x1e0
[153858.682650] PGD 1003067 PUD 0 
[153858.682650] Thread overran stack, or stack corrupted
[153858.682650] Oops: 0000 [#1] SMP 
[153858.682650] last sysfs file: /sys/devices/system/cpu/cpu11/cache/index2/shared_cpu_map
[153858.682650] CPU 0 
[153858.682650] Modules linked in: ahci(P) binfmt_misc ppdev fbcon tileblit font bitblit softcursor vga16fb i2c_piix4 vgastate edac_core edac_mce_amd psmouse serio_raw lp parport ohci1394 dm_raid45 usbhid hid sata_promise ieee1394 pata_atiixp e1000e xor [last unloaded: ahci]
[153858.682650] Pid: 8053, comm: smbd Tainted: P           2.6.32-21-server #32-Ubuntu System Product Name
[153858.682650] RIP: 0010:[<ffffffff8105b584>]  [<ffffffff8105b584>] update_curr+0x124/0x1e0
[153858.682650] RSP: 0018:ffff880003c03d88  EFLAGS: 00010086
[153858.682650] RAX: ffff880077a6ade0 RBX: ffffffff819b0600 RCX: ffff88007b803700
[153858.682650] RDX: 00000000000186b0 RSI: 0000000000000000 RDI: ffff880077a6ae18
[153858.682650] RBP: ffff880003c03db8 R08: 0000000000000b40 R09: 000000000000000f
[153858.682650] R10: 0000000000000001 R11: 0000000000000000 R12: 0000000000000001
[153858.682650] R13: 0000000000000000 R14: 00000000010ad8fc R15: 0000000000015bc0
[153858.682650] FS:  00007f8d5b3bd720(0000) GS:ffff880003c00000(0000) knlGS:0000000000000000
[153858.682650] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[153858.682650] CR2: fffffffb8e5de780 CR3: 0000000077937000 CR4: 00000000000006f0
[153858.682650] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[153858.682650] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[153858.682650] Process smbd (pid: 8053, threadinfo ffff880066a26000, task ffff880077a6ade0)
[153858.682650] Stack:
[153858.682650]  ffff880003c03d98 ffffffff8105b292 ffff880077a6ae18 ffff880003c15c30
[153858.682650] <0> 0000000000000000 0000000000000000 ffff880003c03de8 ffffffff8105b667
[153858.682650] <0> ffff880003c03dd8 ffff880077a6ae18 0000000000000000 ffff880077a6ade0
[153858.682650] Call Trace:
[153858.682650]  <IRQ> 
[153858.682650]  [<ffffffff8105b292>] ? default_wake_function+0x12/0x20
[153858.682650]  [<ffffffff8105b667>] entity_tick+0x27/0x140
[153858.682650]  [<ffffffff8105b7b2>] task_tick_fair+0x32/0x50
[153858.682650]  [<ffffffff8105a3fd>] scheduler_tick+0xed/0x260
[153858.682650]  [<ffffffff8155c615>] ? do_IRQ+0x75/0xf0
[153858.682650]  [<ffffffff810944e0>] ? tick_sched_timer+0x0/0xc0
[153858.682650]  [<ffffffff81076e12>] update_process_times+0x52/0x70
[153858.682650]  [<ffffffff81094546>] tick_sched_timer+0x66/0xc0
[153858.682650]  [<ffffffff810887df>] __run_hrtimer+0x8f/0x1a0
[153858.682650]  [<ffffffff810c4880>] ? handle_IRQ_event+0x60/0x170
[153858.682650]  [<ffffffff81019e69>] ? read_tsc+0x9/0x20
[153858.682650]  [<ffffffff81088b76>] hrtimer_interrupt+0xd6/0x220
[153858.682650]  [<ffffffff8155c6fc>] smp_apic_timer_interrupt+0x6c/0x9c
[153858.682650]  [<ffffffff81013cb3>] apic_timer_interrupt+0x13/0x20
[153858.682650]  <EOI> 
[153858.682650]  [<ffffffff8106795c>] ? vprintk+0x1cc/0x470
[153858.682650]  [<ffffffff81554926>] ? printk+0x41/0x43
[153858.682650]  [<ffffffff810585d4>] ? __schedule_bug+0x54/0x90
[153858.682650]  [<ffffffff8155535f>] ? thread_return+0x1ff/0x420
[153858.682650]  [<ffffffff81143e52>] ? sys_pread64+0x82/0xa0
[153858.682650]  [<ffffffff8101322a>] ? sysret_careful+0x14/0x17
[153858.682650] Code: 00 44 8b 25 13 87 77 00 45 85 e4 74 32 48 8b 50 08 8b 5a 18 48 8b 90 e0 06 00 00 48 8b 4a 50 48 85 c9 74 1b 48 63 db 48 8b 51 20 <48> 03 14 dd 80 b7 85 81 4c 01 32 48 8b 49 78 48 85 c9 75 e8 4c 
[153858.682650] RIP  [<ffffffff8105b584>] update_curr+0x124/0x1e0
[153858.682650]  RSP <ffff880003c03d88>
[153858.682650] CR2: fffffffb8e5de780
[153858.682650] ---[ end trace 53f8b3858a14deca ]---
[153858.682650] Kernel panic - not syncing: Fatal exception in interrupt
[153858.682650] Pid: 8053, comm: smbd Tainted: P      D    2.6.32-21-server #32-Ubuntu
[153858.682650] Call Trace:
[153858.682650]  <IRQ>  [<ffffffff81554826>] panic+0x78/0x137
[153858.682650]  [<ffffffff815585ca>] oops_end+0xea/0xf0
[153858.682650]  [<ffffffff810409d3>] no_context+0xf3/0x190
[153858.682650]  [<ffffffff81040b95>] __bad_area_nosemaphore+0x125/0x1e0
[153858.682650]  [<ffffffff81040c63>] bad_area_nosemaphore+0x13/0x20
[153858.682650]  [<ffffffff8155a164>] do_page_fault+0x2e4/0x3b0
[153858.682650]  [<ffffffff81557905>] page_fault+0x25/0x30
[153858.682650]  [<ffffffff8105b584>] ? update_curr+0x124/0x1e0
[153858.682650]  [<ffffffff8105b546>] ? update_curr+0xe6/0x1e0
[153858.682650]  [<ffffffff8105b292>] ? default_wake_function+0x12/0x20
[153858.682650]  [<ffffffff8105b667>] entity_tick+0x27/0x140
[153858.682650]  [<ffffffff8105b7b2>] task_tick_fair+0x32/0x50
[153858.682650]  [<ffffffff8105a3fd>] scheduler_tick+0xed/0x260
[153858.682650]  [<ffffffff8155c615>] ? do_IRQ+0x75/0xf0
[153858.682650]  [<ffffffff810944e0>] ? tick_sched_timer+0x0/0xc0
[153858.682650]  [<ffffffff81076e12>] update_process_times+0x52/0x70
[153858.682650]  [<ffffffff81094546>] tick_sched_timer+0x66/0xc0
[153858.682650]  [<ffffffff810887df>] __run_hrtimer+0x8f/0x1a0
[153858.682650]  [<ffffffff810c4880>] ? handle_IRQ_event+0x60/0x170
[153858.682650]  [<ffffffff81019e69>] ? read_tsc+0x9/0x20
[153858.682650]  [<ffffffff81088b76>] hrtimer_interrupt+0xd6/0x220
[153858.682650]  [<ffffffff8155c6fc>] smp_apic_timer_interrupt+0x6c/0x9c
[153858.682650]  [<ffffffff81013cb3>] apic_timer_interrupt+0x13/0x20
[153858.682650]  <EOI>  [<ffffffff8106795c>] ? vprintk+0x1cc/0x470
[153858.682650]  [<ffffffff81554926>] ? printk+0x41/0x43
[153858.682650]  [<ffffffff810585d4>] ? __schedule_bug+0x54/0x90
[153858.682650]  [<ffffffff8155535f>] ? thread_return+0x1ff/0x420
[153858.682650]  [<ffffffff81143e52>] ? sys_pread64+0x82/0xa0
[153858.682650]  [<ffffffff8101322a>] ? sysret_careful+0x14/0x17

I'm seeing something that looks similar, also on a box using RAID.  Did you get anywhere with figuring out how to fix this?

---

