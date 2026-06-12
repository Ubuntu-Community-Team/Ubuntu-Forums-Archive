---
title: "Random System Crashes After Upgrading To SSD"
date: 2012-07-17
forum: General Help
---

### Post by clev on 2012-07-17
Ever since installing Ubuntu 64Bit 12.04 on my new SSD, I've been having random system crashes. I posted in the Desktop Environment area a couple of days ago but have since done more investigation and realised it wasn't the best place for my thread.

The PC will freeze refuse to to respond, even to SysRq-REISUB. A bit about my system:
[LIST]
[*]Corsair Force 3 SSD - Latest 5.02 firmware (sdb)
[*]ASUS P8Z77-V LX Motherboard - latest firmware
[*]Ubuntu root + encrypted swap installed on SSD, encrypted home partition on 1TB HDD (sdd)
[*]Only non-standard driver is for ATI graphics card - 12.6 Catalyst driver
[/LIST]

The crashes are fairly infrequent but seem to be more likely to happen during startup/shutdown (maybe related to SSD activity?). It can be reproduced fairly easily by restarting my PC continuously for 20mins or so.

I've managed to grab several kernel logs during several occurrences of the problem using netconsole. The logs are not consistent, and seem different every time. A couple of examples are below:

```

Jul 15 12:01:22 192.168.1.67 [   10.133850] console [netcon0] enabled
Jul 15 12:01:22 192.168.1.67 [   10.133854] netconsole: network logging started
Jul 15 12:01:48 192.168.1.67 [   36.158597] ------------[ cut here ]------------
Jul 15 12:01:48 192.168.1.67 [   36.158606] WARNING: at /build/buildd/linux-3.2.0/kernel/watchdog.c:241 watchdog_overflow_callback+0x9a/0xc0()
Jul 15 12:01:48 192.168.1.67 [   36.158608] Hardware name: System Product Name
Jul 15 12:01:48 192.168.1.67 [   36.158609] Watchdog detected hard LOCKUP on cpu 1
Jul 15 12:01:48 192.168.1.67 
Jul 15 12:01:48 192.168.1.67 [   36.158610] Modules linked in:
Jul 15 12:01:48 192.168.1.67 snd_hda_codec_hdmi
Jul 15 12:01:48 192.168.1.67 rfcomm
Jul 15 12:01:48 192.168.1.67 bnep
Jul 15 12:01:48 192.168.1.67 bluetooth
Jul 15 12:01:48 192.168.1.67 parport_pc
Jul 15 12:01:48 192.168.1.67 ppdev
Jul 15 12:01:48 192.168.1.67 snd_hda_codec_realtek
Jul 15 12:01:48 192.168.1.67 snd_seq_midi
Jul 15 12:01:48 192.168.1.67 snd_rawmidi
Jul 15 12:01:48 192.168.1.67 eeepc_wmi
Jul 15 12:01:48 192.168.1.67 snd_seq_midi_event
Jul 15 12:01:48 192.168.1.67 asus_wmi
Jul 15 12:01:48 192.168.1.67 snd_seq
Jul 15 12:01:48 192.168.1.67 psmouse
Jul 15 12:01:48 192.168.1.67 sparse_keymap
Jul 15 12:01:48 192.168.1.67 nls_iso8859_1
Jul 15 12:01:48 192.168.1.67 snd_seq_device
Jul 15 12:01:48 192.168.1.67 nls_cp437
Jul 15 12:01:48 192.168.1.67 snd_hda_intel(+)
Jul 15 12:01:48 192.168.1.67 vfat
Jul 15 12:01:48 192.168.1.67 fat
Jul 15 12:01:48 192.168.1.67 snd_hda_codec
Jul 15 12:01:48 192.168.1.67 snd_hwdep
Jul 15 12:01:48 192.168.1.67 snd_pcm
Jul 15 12:01:48 192.168.1.67 fglrx(P)
Jul 15 12:01:48 192.168.1.67 serio_raw
Jul 15 12:01:48 192.168.1.67 joydev
Jul 15 12:01:48 192.168.1.67 snd_timer
Jul 15 12:01:48 192.168.1.67 snd
Jul 15 12:01:48 192.168.1.67 soundcore
Jul 15 12:01:48 192.168.1.67 snd_page_alloc
Jul 15 12:01:48 192.168.1.67 mac_hid
Jul 15 12:01:48 192.168.1.67 mei(C)
Jul 15 12:01:48 192.168.1.67 netconsole
Jul 15 12:01:48 192.168.1.67 configfs
Jul 15 12:01:48 192.168.1.67 lp
Jul 15 12:01:48 192.168.1.67 parport
Jul 15 12:01:48 192.168.1.67 usbhid
Jul 15 12:01:48 192.168.1.67 hid
Jul 15 12:01:48 192.168.1.67 r8169
Jul 15 12:01:48 192.168.1.67 video
Jul 15 12:01:48 192.168.1.67 wmi
Jul 15 12:01:48 192.168.1.67 
Jul 15 12:01:48 192.168.1.67 [   36.158702] Pid: 0, comm: swapper/1 Tainted: P      D  C O 3.2.0-26-generic #41-Ubuntu
Jul 15 12:01:48 192.168.1.67 [   36.158703] Call Trace:
Jul 15 12:01:48 192.168.1.67 [   36.158705]  <NMI> 
Jul 15 12:01:48 192.168.1.67 [<ffffffff810672af>] warn_slowpath_common+0x7f/0xc0
Jul 15 12:01:48 192.168.1.67 [   36.158710]  [<ffffffff810673a6>] warn_slowpath_fmt+0x46/0x50
Jul 15 12:01:48 192.168.1.67 [   36.158713]  [<ffffffff8101adf3>] ? native_sched_clock+0x13/0x80
Jul 15 12:01:48 192.168.1.67 [   36.158716]  [<ffffffff810d838a>] watchdog_overflow_callback+0x9a/0xc0
Jul 15 12:01:48 192.168.1.67 [   36.158718]  [<ffffffff81111bc6>] __perf_event_overflow+0x96/0x1e0
Jul 15 12:01:48 192.168.1.67 [   36.158721]  [<ffffffff8110f151>] ? perf_event_update_userpage+0x11/0xc0
Jul 15 12:01:48 192.168.1.67 [   36.158724]  [<ffffffff81023aaa>] ? x86_perf_event_set_period+0xda/0x150
Jul 15 12:01:48 192.168.1.67 [   36.158726]  [<ffffffff81112114>] perf_event_overflow+0x14/0x20
Jul 15 12:01:48 192.168.1.67 [   36.158780]  [<ffffffff810281c3>] intel_pmu_handle_irq+0x163/0x210
Jul 15 12:01:48 192.168.1.67 [   36.158783]  [<ffffffff8165b501>] perf_event_nmi_handler+0x21/0x30
Jul 15 12:01:48 192.168.1.67 [   36.158785]  [<ffffffff8165adc9>] default_do_nmi+0x69/0x220
Jul 15 12:01:48 192.168.1.67 [   36.158787]  [<ffffffff8165b000>] do_nmi+0x80/0x90
Jul 15 12:01:48 192.168.1.67 [   36.158789]  [<ffffffff8165a3f0>] nmi+0x20/0x30
Jul 15 12:01:48 192.168.1.67 [   36.158791]  [<ffffffff8103dc65>] ? __ticket_spin_lock+0x25/0x30
Jul 15 12:01:48 192.168.1.67 [   36.158793]  <<EOE>> 
Jul 15 12:01:48 192.168.1.67 <IRQ> 
Jul 15 12:01:48 192.168.1.67 [<ffffffff81659cb5>] _raw_spin_lock_irq+0x15/0x20
Jul 15 12:01:48 192.168.1.67 [   36.158798]  [<ffffffff81077a18>] run_timer_softirq+0x48/0x2a0
Jul 15 12:01:48 192.168.1.67 [   36.158801]  [<ffffffff8108e499>] ? enqueue_hrtimer+0x39/0xc0
Jul 15 12:01:48 192.168.1.67 [   36.158803]  [<ffffffff8101a779>] ? read_tsc+0x9/0x20
Jul 15 12:01:48 192.168.1.67 [   36.158908]  [<ffffffff81095235>] ? ktime_get+0x65/0xe0
Jul 15 12:01:48 192.168.1.67 [   36.158912]  [<ffffffff8106ea58>] __do_softirq+0xa8/0x210
Jul 15 12:01:48 192.168.1.67 [   36.158914]  [<ffffffff8101a779>] ? read_tsc+0x9/0x20
Jul 15 12:01:48 192.168.1.67 [   36.158916]  [<ffffffff8109c1c4>] ? tick_program_event+0x24/0x30
Jul 15 12:01:48 192.168.1.67 [   36.158919]  [<ffffffff8166422c>] call_softirq+0x1c/0x30
Jul 15 12:01:48 192.168.1.67 [   36.158921]  [<ffffffff81015305>] do_softirq+0x65/0xa0
Jul 15 12:01:48 192.168.1.67 [   36.158924]  [<ffffffff8106ee3e>] irq_exit+0x8e/0xb0
Jul 15 12:01:48 192.168.1.67 [   36.158926]  [<ffffffff81664bce>] smp_apic_timer_interrupt+0x6e/0x99
Jul 15 12:01:48 192.168.1.67 [   36.158928]  [<ffffffff81662a9e>] apic_timer_interrupt+0x6e/0x80
Jul 15 12:01:48 192.168.1.67 [   36.158929]  <EOI> 
Jul 15 12:01:48 192.168.1.67 [<ffffffff810e1130>] ? rcu_needs_cpu+0xd0/0x230
Jul 15 12:01:48 192.168.1.67 [   36.158934]  [<ffffffff8101be45>] ? mwait_idle+0x95/0x210
Jul 15 12:01:48 192.168.1.67 [   36.159296]  [<ffffffff81012236>] cpu_idle+0xd6/0x120
Jul 15 12:01:48 192.168.1.67 [   36.159298]  [<ffffffff81637789>] start_secondary+0xd9/0xdb
Jul 15 12:01:48 192.168.1.67 [   36.159300] ---[ end trace 6ecc1cdd93b8b2a4 ]---

```

```

Jul 15 18:04:53 192.168.1.67 [   15.238022] console [netcon0] enabled
Jul 15 18:04:53 192.168.1.67 [   15.238026] netconsole: network logging started
Jul 15 18:04:53 192.168.1.67 [   15.238049] [fglrx] Gart USWC size:1280 M.
Jul 15 18:04:53 192.168.1.67 [   15.238052] [fglrx] Gart cacheable size:508 M.
Jul 15 18:04:53 192.168.1.67 [   15.238055] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Jul 15 18:04:53 192.168.1.67 [   15.238057] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
Jul 15 18:04:53 192.168.1.67 [   15.238058] [fglrx] Reserved FB block: Unshared offset:7ffef000, size:11000 
Jul 15 18:04:53 192.168.1.67 [   15.238163] BUG: unable to handle kernel 
Jul 15 18:04:53 192.168.1.67 paging request
Jul 15 18:04:53 192.168.1.67 at ffff880400e277f0
Jul 15 18:04:53 192.168.1.67 [   15.238167] IP:
Jul 15 18:04:53 192.168.1.67 [<ffffffff8113c823>] unmap_page_range+0xa3/0x300
Jul 15 18:04:53 192.168.1.67 [   15.238173] BAD
Jul 15 18:04:53 192.168.1.67 [   15.238174] Oops: 0000 [#2] 
Jul 15 18:04:53 192.168.1.67 SMP 
Jul 15 18:04:53 192.168.1.67 
Jul 15 18:04:53 192.168.1.67 [   15.238177] CPU 2 
Jul 15 18:04:53 192.168.1.67 
Jul 15 18:04:53 192.168.1.67 [   15.238178] Modules linked in:
Jul 15 18:04:53 192.168.1.67 snd_hda_codec_hdmi
Jul 15 18:04:53 192.168.1.67 rfcomm
Jul 15 18:04:53 192.168.1.67 bnep
Jul 15 18:04:53 192.168.1.67 bluetooth
Jul 15 18:04:53 192.168.1.67 parport_pc
Jul 15 18:04:53 192.168.1.67 ppdev
Jul 15 18:04:53 192.168.1.67 nls_iso8859_1
Jul 15 18:04:53 192.168.1.67 nls_cp437
Jul 15 18:04:53 192.168.1.67 vfat
Jul 15 18:04:53 192.168.1.67 fat
Jul 15 18:04:53 192.168.1.67 snd_hda_codec_realtek
Jul 15 18:04:53 192.168.1.67 eeepc_wmi
Jul 15 18:04:53 192.168.1.67 asus_wmi
Jul 15 18:04:53 192.168.1.67 sparse_keymap
Jul 15 18:04:53 192.168.1.67 fglrx(P)
Jul 15 18:04:53 192.168.1.67 joydev
Jul 15 18:04:53 192.168.1.67 snd_hda_intel
Jul 15 18:04:53 192.168.1.67 snd_hda_codec
Jul 15 18:04:53 192.168.1.67 snd_seq_midi
Jul 15 18:04:53 192.168.1.67 snd_rawmidi
Jul 15 18:04:53 192.168.1.67 snd_hwdep
Jul 15 18:04:53 192.168.1.67 snd_seq_midi_event
Jul 15 18:04:53 192.168.1.67 mac_hid
Jul 15 18:04:53 192.168.1.67 snd_pcm
Jul 15 18:04:53 192.168.1.67 snd_seq
Jul 15 18:04:53 192.168.1.67 snd_seq_device
Jul 15 18:04:53 192.168.1.67 snd_timer
Jul 15 18:04:53 192.168.1.67 psmouse
Jul 15 18:04:53 192.168.1.67 serio_raw
Jul 15 18:04:53 192.168.1.67 snd
Jul 15 18:04:53 192.168.1.67 soundcore
Jul 15 18:04:53 192.168.1.67 snd_page_alloc
Jul 15 18:04:53 192.168.1.67 mei(C)
Jul 15 18:04:53 192.168.1.67 netconsole
Jul 15 18:04:53 192.168.1.67 configfs
Jul 15 18:04:53 192.168.1.67 lp
Jul 15 18:04:53 192.168.1.67 parport
Jul 15 18:04:53 192.168.1.67 usbhid
Jul 15 18:04:53 192.168.1.67 hid
Jul 15 18:04:53 192.168.1.67 r8169
Jul 15 18:04:53 192.168.1.67 video
Jul 15 18:04:53 192.168.1.67 wmi
Jul 15 18:04:53 192.168.1.67 
Jul 15 18:04:53 192.168.1.67 [   15.238266] 
Jul 15 18:04:53 192.168.1.67 [   15.238268] Pid: 397, comm: udevadm Tainted: P      D  C O 3.2.0-26-generic #41-Ubuntu
Jul 15 18:04:53 192.168.1.67 System manufacturer System Product Name
Jul 15 18:04:53 192.168.1.67 /P8Z77-V LX
Jul 15 18:04:53 192.168.1.67 
Jul 15 18:04:53 192.168.1.67 [   15.238272] RIP: 0010:[<ffffffff8113c823>] 
Jul 15 18:04:53 192.168.1.67 [<ffffffff8113c823>] unmap_page_range+0xa3/0x300
Jul 15 18:04:53 192.168.1.67 [   15.238378] RSP: 0018:ffff88040238d588  EFLAGS: 00010206
Jul 15 18:04:53 192.168.1.67 [   15.238379] RAX: ffff880400e277f0 RBX: ffff8803ff0a8000 RCX: 00007f70d3475000
Jul 15 18:04:53 192.168.1.67 [   15.238381] RDX: ffffff8000000000 RSI: ffff8803ff0a8000 RDI: ffff88040238d678
Jul 15 18:04:53 192.168.1.67 [   15.238382] RBP: ffff88040238d608 R08: 0000000000000000 R09: 0000000000000000
Jul 15 18:04:53 192.168.1.67 [   15.238384] R10: 0000000000000004 R11: 0000000000000000 R12: 00007f70d345d000
Jul 15 18:04:53 192.168.1.67 [   15.238385] R13: 0000000000000000 R14: 00007f70d3475000 R15: ffff88040238d678
Jul 15 18:04:53 192.168.1.67 [   15.238387] FS:  0000000000000000(0000) GS:ffff88041ed00000(0000) knlGS:0000000000000000
Jul 15 18:04:53 192.168.1.67 [   15.238389] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Jul 15 18:04:53 192.168.1.67 [   15.238390] CR2: ffff880400e27880 CR3: 0000000400e27000 CR4: 00000000001406e0
Jul 15 18:04:53 192.168.1.67 [   15.238392] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jul 15 18:04:53 192.168.1.67 [   15.238393] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jul 15 18:04:53 192.168.1.67 [   15.238446] Process udevadm (pid: 397, threadinfo ffff88040238c000, task ffff8803fecac4d0)
Jul 15 18:04:53 192.168.1.67 [   15.238448] Stack:
Jul 15 18:04:53 192.168.1.67 [   15.238449]  ffff88040238d5b8
Jul 15 18:04:53 192.168.1.67 ffff88041ed10260
Jul 15 18:04:53 192.168.1.67 00007f70d3474fff
Jul 15 18:04:53 192.168.1.67 00007f70d3475000
Jul 15 18:04:53 192.168.1.67 
Jul 15 18:04:53 192.168.1.67 [   15.238815]  ffff88040238d678
Jul 15 18:04:53 192.168.1.67 0000000000000000
Jul 15 18:04:53 192.168.1.67 ffff88040238d618
Jul 15 18:04:53 192.168.1.67 ffff8803ff0a8000
Jul 15 18:04:53 192.168.1.67 
Jul 15 18:04:53 192.168.1.67 [   15.238822]  ffff880400e277f0
Jul 15 18:04:53 192.168.1.67 0000000000000282
Jul 15 18:04:53 192.168.1.67 ffff88041effbe00
Jul 15 18:04:53 192.168.1.67 ffff8803ff0a8000
Jul 15 18:04:53 192.168.1.67 
Jul 15 18:04:53 192.168.1.67 [   15.238828] Call Trace:
Jul 15 18:04:53 192.168.1.67 [   15.238883]  [<ffffffff8113d00a>] unmap_vmas+0xca/0x160
Jul 15 18:04:53 192.168.1.67 [   15.238885]  [<ffffffff81144547>] exit_mmap+0x97/0x140
Jul 15 18:04:53 192.168.1.67 [   15.238889]  [<ffffffff81657812>] ? _cond_resched+0x32/0x40
Jul 15 18:04:53 192.168.1.67 [   15.238892]  [<ffffffff810a08f8>] ? exit_robust_list+0x88/0x160
Jul 15 18:04:53 192.168.1.67 [   15.238894]  [<ffffffff81064f32>] mmput.part.16+0x42/0x130
Jul 15 18:04:53 192.168.1.67 [   15.238896]  [<ffffffff81065049>] mmput+0x29/0x30
Jul 15 18:04:53 192.168.1.67 [   15.238899]  [<ffffffff8106b9a3>] exit_mm+0x113/0x130
Jul 15 18:04:53 192.168.1.67 [   15.238901]  [<ffffffff810e4345>] ? taskstats_exit+0x45/0x240
Jul 15 18:04:53 192.168.1.67 [   15.238903]  [<ffffffff81659cb5>] ? _raw_spin_lock_irq+0x15/0x20
Jul 15 18:04:53 192.168.1.67 [   15.238906]  [<ffffffff8106bb2e>] do_exit+0x16e/0x420
Jul 15 18:04:53 192.168.1.67 [   15.238909]  [<ffffffff8165ab60>] oops_end+0xb0/0xf0
Jul 15 18:04:53 192.168.1.67 [   15.238964]  [<ffffffff8163fe4b>] no_context+0x150/0x15d
Jul 15 18:04:53 192.168.1.67 [   15.238966]  [<ffffffff81640021>] __bad_area_nosemaphore+0x1c9/0x1e8
Jul 15 18:04:53 192.168.1.67 [   15.238969]  [<ffffffff8163f6cd>] ? pmd_offset+0x1f/0x25
Jul 15 18:04:53 192.168.1.67 [   15.238970]  [<ffffffff81640053>] bad_area_nosemaphore+0x13/0x15
Jul 15 18:04:53 192.168.1.67 [   15.238973]  [<ffffffff8165d7b6>] do_page_fault+0x426/0x520
Jul 15 18:04:53 192.168.1.67 [   15.238976]  [<ffffffff81311d1e>] ? rb_erase+0xce/0x150
Jul 15 18:04:53 192.168.1.67 [   15.238978]  [<ffffffff813140e4>] ? timerqueue_del+0x34/0x90
Jul 15 18:04:53 192.168.1.67 [   15.238981]  [<ffffffff8108e900>] ? __remove_hrtimer+0x60/0xc0
Jul 15 18:04:53 192.168.1.67 [   15.238984]  [<ffffffff8108eee0>] ? hrtimer_try_to_cancel+0x50/0xc0
Jul 15 18:04:53 192.168.1.67 [   15.238986]  [<ffffffff8165a135>] page_fault+0x25/0x30
Jul 15 18:04:53 192.168.1.67 [   15.238988]  [<ffffffff8113dbb9>] ? handle_mm_fault+0x89/0x350
Jul 15 18:04:53 192.168.1.67 [   15.239042]  [<ffffffff8113db81>] ? handle_mm_fault+0x51/0x350
Jul 15 18:04:53 192.168.1.67 [   15.239045]  [<ffffffff811b9062>] ? inotify_poll+0x42/0x60
Jul 15 18:04:53 192.168.1.67 [   15.239047]  [<ffffffff8165d4e0>] do_page_fault+0x150/0x520
Jul 15 18:04:53 192.168.1.67 45 
Jul 15 18:04:53 192.168.1.67 98 
Jul 15 18:04:53 192.168.1.67 48 
Jul 15 18:04:53 192.168.1.67 84 
Jul 15 18:04:53 192.168.1.67 00 
Jul 15 18:04:53 192.168.1.67 fb 
Jul 15 18:04:53 192.168.1.67 00 
Jul 15 18:04:53 192.168.1.67 [   15.239801] RIP 
Jul 15 18:04:53 192.168.1.67 [   15.239808] ---[ end trace 2a60310bd7ff5a35 ]---

```

Things I've tried:
[LIST]
[*]Disabling the swap
[*]Disabling ureadahead (early occurences of this problem seemed to be associated with it)
[*]Mounted SSD with discard,noatime options
[*]Memtest passed the first pass
[/LIST]

Only other things I've noticed is that my sound can sometimes start going choppy before the crash happens, and my desktop icons sometimes appear on my unity launcher after restarting after the crash.

Also worth noting, I have an identical model SSD running Win7 on the same PC which works flawlessly.

I have no experience of interpreting these log files so any ideas would be gratefully received!

---

### Post by psion01 on 2012-07-17
I just returned two OCZ Petrol SSDs after installing them in two different PCs. I experienced increasingly common errors during boot until neither machine could be started. Eventually, both machines hung even before BIOS launched.

I wouldn't be too sure that just because the drive with Windows works that the Ubuntu drive also functions. I see on [Newegg's reviews of the Corsair Force 3 ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820233181")that it has a high failure rate.

---

### Post by Lupi on 2012-07-22
I cannot add too much except that I had the same problem while installing Linux Mint on a SSD. I would love to find an SSD that works well with Linux.

---

