---
title: "kernel crash-and-burn paging error in VirtualBox guest"
date: 2010-11-26
forum: General Help
---

### Post by Defrector on 2010-11-26
Can anyone tell me what likely triggered this kernel crash? It occurred on ubuntu 10.04 amd64 as a VirtualBox guest on ubuntu-server 10.04 amd64(headless over X11-SSH). I am not sure to whom I should file this bug with. 

Isn't rmiregistry java-based? Seems hard to pagefault something like that.

I wasn't doing anything spectacular at the time- just coding in Eclipse when apps started crashing one after another and then the whole thing went down. It would ping back but ssh would not respond (not even a rejection or lack of route to host)

```
Nov 26 06:55:40 vbox-guest kernel: [13560.002728] BUG: unable to handle kernel paging request at ffffffff79038760
Nov 26 06:55:40 vbox-guest kernel: [13560.002749] IP: [<ffffffff79038760>] 0xffffffff79038760
Nov 26 06:55:40 vbox-guest kernel: [13560.002762] PGD 1003067 PUD 0 
Nov 26 06:55:40 vbox-guest kernel: [13560.002770] Oops: 0010 [#1] SMP 
Nov 26 06:55:40 vbox-guest kernel: [13560.002778] last sysfs file: /sys/devices/pci0000:00/0000:00:14.0/local_cpus
Nov 26 06:55:40 vbox-guest kernel: [13560.002784] CPU 1 
Nov 26 06:55:40 vbox-guest kernel: [13560.002787] Modules linked in: binfmt_misc nls_cp437 cifs fbcon tileblit font ppdev bitblit softcursor parport_pc psmouse serio_raw lp parport vga16fb i2c_piix4 vgastate virtio_net floppy mptspi mptscsih virtio_pci virtio_ring virtio mptbase scsi_transport_spi
Nov 26 06:55:40 vbox-guest kernel: [13560.002803] Pid: 3999, comm: rmiregistry Not tainted 2.6.32-25-generic #44-Ubuntu VirtualBox
Nov 26 06:55:40 vbox-guest kernel: [13560.002807] RIP: 0010:[<ffffffff79038760>]  [<ffffffff79038760>] 0xffffffff79038760
Nov 26 06:55:40 vbox-guest kernel: [13560.002812] RSP: 0018:ffff880078833e60  EFLAGS: 00010246
Nov 26 06:55:40 vbox-guest kernel: [13560.002814] RAX: ffffffff819b8668 RBX: 0000000000000000 RCX: 00000000360544d6
Nov 26 06:55:40 vbox-guest kernel: [13560.002818] RDX: 000000007b8054d6 RSI: 0000000000006c0a RDI: ffffffff819b8650
Nov 26 06:55:40 vbox-guest kernel: [13560.002820] RBP: ffff880078833ec8 R08: 0000000000000000 R09: 0000000000000000
Nov 26 06:55:40 vbox-guest kernel: [13560.002823] R10: 00007f4bbc007c50 R11: 0000000000000001 R12: ffffffff819b8650
Nov 26 06:55:40 vbox-guest kernel: [13560.002826] R13: ffff880078833e78 R14: 0000000000000001 R15: 00000000ffffffff
Nov 26 06:55:40 vbox-guest kernel: [13560.002833] FS:  00007f4bc0d50710(0000) GS:ffff880001c80000(0000) knlGS:00000000f698c760
Nov 26 06:55:40 vbox-guest kernel: [13560.002835] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Nov 26 06:55:40 vbox-guest kernel: [13560.002836] CR2: ffffffff79038760 CR3: 000000004b372000 CR4: 00000000000006e0
Nov 26 06:55:40 vbox-guest kernel: [13560.002839] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Nov 26 06:55:40 vbox-guest kernel: [13560.002841] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Nov 26 06:55:40 vbox-guest kernel: [13560.002843] Process rmiregistry (pid: 3999, threadinfo ffff880078832000, task ffff880076d38000)
Nov 26 06:55:40 vbox-guest kernel: [13560.002844] Stack:
Nov 26 06:55:40 vbox-guest kernel: [13560.002845]  ffffffff810959e8 0000000000000f9f ffffffff810888f4 00007f4bbc007000
Nov 26 06:55:40 vbox-guest kernel: [13560.002847] <0> ffff880078106680 0000000000000c28 00000000963051d7 000000004e2a6a18
Nov 26 06:55:40 vbox-guest kernel: [13560.002849] <0> 0000000000000081 0000000000000001 0000000000000001 0000000000000000
Nov 26 06:55:40 vbox-guest kernel: [13560.002852] Call Trace:
Nov 26 06:55:40 vbox-guest kernel: [13560.002857]  [<ffffffff810959e8>] ? futex_wake+0x108/0x130
Nov 26 06:55:40 vbox-guest kernel: [13560.002861]  [<ffffffff810888f4>] ? hrtimer_start_range_ns+0x14/0x20
Nov 26 06:55:40 vbox-guest kernel: [13560.002863]  [<ffffffff81098128>] do_futex+0xb8/0x1b0
Nov 26 06:55:40 vbox-guest kernel: [13560.002865]  [<ffffffff8108e970>] ? getnstimeofday+0x60/0xf0
Nov 26 06:55:40 vbox-guest kernel: [13560.002867]  [<ffffffff8109829b>] sys_futex+0x7b/0x170
Nov 26 06:55:40 vbox-guest kernel: [13560.002869]  [<ffffffff8108ea00>] ? ktime_get_real+0x0/0x50
Nov 26 06:55:40 vbox-guest kernel: [13560.002872]  [<ffffffff8106b950>] ? sys_gettimeofday+0x40/0x90
Nov 26 06:55:40 vbox-guest kernel: [13560.002875]  [<ffffffff810121b2>] system_call_fastpath+0x16/0x1b
Nov 26 06:55:40 vbox-guest kernel: [13560.002877] Code:  Bad RIP value.
Nov 26 06:55:40 vbox-guest kernel: [13560.002880] RIP  [<ffffffff79038760>] 0xffffffff79038760
Nov 26 06:55:40 vbox-guest kernel: [13560.002882]  RSP <ffff880078833e60>
Nov 26 06:55:40 vbox-guest kernel: [13560.002883] CR2: ffffffff79038760
Nov 26 06:55:40 vbox-guest kernel: [13560.002885] ---[ end trace 4d0a754ed9dcc317 ]---
Nov 26 06:55:40 vbox-guest kernel: [13560.002892] BUG: unable to handle kernel paging request at ffffffff79038760
Nov 26 06:55:40 vbox-guest kernel: [13560.002894] IP: [<ffffffff79038760>] 0xffffffff79038760
Nov 26 06:55:40 vbox-guest kernel: [13560.002895] PGD 1003067 PUD 0 
Nov 26 06:55:40 vbox-guest kernel: [13560.002897] Oops: 0010 [#2] SMP 
Nov 26 06:55:40 vbox-guest kernel: [13560.002898] last sysfs file: /sys/devices/pci0000:00/0000:00:14.0/local_cpus
Nov 26 06:55:40 vbox-guest kernel: [13560.002900] CPU 1 
Nov 26 06:55:40 vbox-guest kernel: [13560.002900] Modules linked in: binfmt_misc nls_cp437 cifs fbcon tileblit font ppdev bitblit softcursor parport_pc psmouse serio_raw lp parport vga16fb i2c_piix4 vgastate virtio_net floppy mptspi mptscsih virtio_pci virtio_ring virtio mptbase scsi_transport_spi
Nov 26 06:55:40 vbox-guest kernel: [13560.002911] Pid: 3999, comm: rmiregistry Tainted: G      D    2.6.32-25-generic #44-Ubuntu VirtualBox
Nov 26 06:55:40 vbox-guest kernel: [13560.002912] RIP: 0010:[<ffffffff79038760>]  [<ffffffff79038760>] 0xffffffff79038760
Nov 26 06:55:40 vbox-guest kernel: [13560.002915] RSP: 0018:ffff880078833ac0  EFLAGS: 00010246
Nov 26 06:55:40 vbox-guest kernel: [13560.002916] RAX: ffffffff819b8e10 RBX: 0000000000000000 RCX: 000000007560d31c
Nov 26 06:55:40 vbox-guest kernel: [13560.002917] RDX: 000000009914df1c RSI: 000000000000eac1 RDI: ffffffff819b8df8
Nov 26 06:55:40 vbox-guest kernel: [13560.002919] RBP: ffff880078833b28 R08: 0000000000000000 R09: 66c0000000000000
Nov 26 06:55:40 vbox-guest kernel: [13560.002920] R10: 0000000000000007 R11: 0000000000000207 R12: ffffffff819b8df8
Nov 26 06:55:40 vbox-guest kernel: [13560.002922] R13: ffff880078833ad8 R14: 0000000000000001 R15: 00000000ffffffff
Nov 26 06:55:40 vbox-guest kernel: [13560.002932] FS:  00007f4bc0d50710(0000) GS:ffff880001c80000(0000) knlGS:00000000f698c760
Nov 26 06:55:40 vbox-guest kernel: [13560.002934] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Nov 26 06:55:40 vbox-guest kernel: [13560.002935] CR2: ffffffff79038760 CR3: 000000004b372000 CR4: 00000000000006e0
Nov 26 06:55:40 vbox-guest kernel: [13560.002937] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Nov 26 06:55:40 vbox-guest kernel: [13560.002938] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Nov 26 06:55:40 vbox-guest kernel: [13560.002940] Process rmiregistry (pid: 3999, threadinfo ffff880078832000, task ffff880076d38000)
Nov 26 06:55:40 vbox-guest kernel: [13560.002941] Stack:
Nov 26 06:55:40 vbox-guest kernel: [13560.002942]  ffffffff810959e8 ffff880078833ae8 ffff880078833ae8 00007f4bc0d50000
Nov 26 06:55:40 vbox-guest kernel: [13560.002944] <0> ffff880078106680 00000000000009e2 ffffffff8108943f ffff880078833b18
Nov 26 06:55:40 vbox-guest kernel: [13560.002946] <0> 0000000000000001 0000000000000001 0000000000000001 0000000000000000
Nov 26 06:55:40 vbox-guest kernel: [13560.002949] Call Trace:
Nov 26 06:55:40 vbox-guest kernel: [13560.002950]  [<ffffffff810959e8>] ? futex_wake+0x108/0x130
Nov 26 06:55:40 vbox-guest kernel: [13560.002953]  [<ffffffff8108943f>] ? up+0x2f/0x50
Nov 26 06:55:40 vbox-guest kernel: [13560.002955]  [<ffffffff81098128>] do_futex+0xb8/0x1b0
Nov 26 06:55:40 vbox-guest kernel: [13560.002956]  [<ffffffff8109829b>] sys_futex+0x7b/0x170
Nov 26 06:55:40 vbox-guest kernel: [13560.002958]  [<ffffffff81096060>] ? exit_robust_list+0x90/0x160
Nov 26 06:55:40 vbox-guest kernel: [13560.002960]  [<ffffffff81063c1e>] mm_release+0xce/0x130
Nov 26 06:55:40 vbox-guest kernel: [13560.002962]  [<ffffffff8106a206>] exit_mm+0x26/0x150
Nov 26 06:55:40 vbox-guest kernel: [13560.002965]  [<ffffffff810a8300>] ? acct_collect+0x160/0x1b0
Nov 26 06:55:40 vbox-guest kernel: [13560.002967]  [<ffffffff8106a565>] do_exit+0x125/0x380
Nov 26 06:55:40 vbox-guest kernel: [13560.002971]  [<ffffffff815448f0>] oops_end+0xb0/0xf0
Nov 26 06:55:40 vbox-guest kernel: [13560.002973]  [<ffffffff8103f923>] no_context+0xf3/0x190
Nov 26 06:55:40 vbox-guest kernel: [13560.002975]  [<ffffffff8103fae5>] __bad_area_nosemaphore+0x125/0x1e0
Nov 26 06:55:40 vbox-guest kernel: [13560.002977]  [<ffffffff8103fbb3>] bad_area_nosemaphore+0x13/0x20
Nov 26 06:55:40 vbox-guest kernel: [13560.002979]  [<ffffffff815464d4>] do_page_fault+0x2e4/0x3b0
Nov 26 06:55:40 vbox-guest kernel: [13560.002981]  [<ffffffff81543c65>] page_fault+0x25/0x30
Nov 26 06:55:40 vbox-guest kernel: [13560.002983]  [<ffffffff810959e8>] ? futex_wake+0x108/0x130
Nov 26 06:55:40 vbox-guest kernel: [13560.002985]  [<ffffffff810888f4>] ? hrtimer_start_range_ns+0x14/0x20
Nov 26 06:55:40 vbox-guest kernel: [13560.002987]  [<ffffffff81098128>] do_futex+0xb8/0x1b0
Nov 26 06:55:40 vbox-guest kernel: [13560.002989]  [<ffffffff8108e970>] ? getnstimeofday+0x60/0xf0
Nov 26 06:55:40 vbox-guest kernel: [13560.002990]  [<ffffffff8109829b>] sys_futex+0x7b/0x170
Nov 26 06:55:40 vbox-guest kernel: [13560.002992]  [<ffffffff8108ea00>] ? ktime_get_real+0x0/0x50
Nov 26 06:55:40 vbox-guest kernel: [13560.002995]  [<ffffffff8106b950>] ? sys_gettimeofday+0x40/0x90
Nov 26 06:55:40 vbox-guest kernel: [13560.002997]  [<ffffffff810121b2>] system_call_fastpath+0x16/0x1b
Nov 26 06:55:40 vbox-guest kernel: [13560.002998] Code:  Bad RIP value.
Nov 26 06:55:40 vbox-guest kernel: [13560.003000] RIP  [<ffffffff79038760>] 0xffffffff79038760
Nov 26 06:55:40 vbox-guest kernel: [13560.003002]  RSP <ffff880078833ac0>
Nov 26 06:55:40 vbox-guest kernel: [13560.003003] CR2: ffffffff79038760
Nov 26 06:55:40 vbox-guest kernel: [13560.003004] ---[ end trace 4d0a754ed9dcc318 ]---
Nov 26 06:55:40 vbox-guest kernel: [13560.003005] Fixing recursive fault but reboot is needed!
```

---

