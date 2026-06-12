---
title: "ndiswrapper freezes if is run under /etc/modules"
date: 2009-10-30
forum: General Help
---

### Post by arepaking on 2009-10-30
Hi All,
I tried to add a line into /etc/modules to run "ndiswrapper" everytime I start my computer. When I added this line my wireless network card does not work. However, if I remove that line and I manually execute via console ```
sudo modprobe ndiswrapper
``` then it works fine.

---

### Post by arepaking on 2009-10-31
This is what I get on the system.log everytime ndiswrapper hangs on me.
```

31 12:27:27 carlos-desktop kernel: [    5.828008] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Oct 31 12:27:27 carlos-desktop kernel: [    5.834165] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c5)
Oct 31 12:27:27 carlos-desktop kernel: [    5.895888] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
Oct 31 12:27:27 carlos-desktop kernel: [    5.896654] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
Oct 31 12:27:27 carlos-desktop kernel: [    5.896849] ndiswrapper 0000:06:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Oct 31 12:27:27 carlos-desktop kernel: [    5.897342] ndiswrapper: using IRQ 21
Oct 31 12:27:27 carlos-desktop kernel: [    5.970076] BUG: unable to handle kernel paging request at ffffc94019d34510
Oct 31 12:27:27 carlos-desktop kernel: [    5.970082] IP: [<ffffc90019cf443c>] 0xffffc90019cf443c
Oct 31 12:27:27 carlos-desktop kernel: [    5.970087] PGD 7c216067 PUD 0 
Oct 31 12:27:27 carlos-desktop kernel: [    5.970091] Oops: 0000 [#1] SMP 
Oct 31 12:27:27 carlos-desktop kernel: [    5.970094] last sysfs file: /sys/module/snd_rawmidi/initstate
Oct 31 12:27:27 carlos-desktop kernel: [    5.970097] CPU 0 
Oct 31 12:27:27 carlos-desktop kernel: [    5.970099] Modules linked in: snd_hwdep snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer uvcvideo(+) ndiswrapper(+) snd_seq_device videodev iptable_filter psmouse v4l1_compat snd ip_tables lp v4l2_compat_ioctl32 heci(C) snd_page_alloc serio_raw soundcore x_tables parport usbhid dm_raid45 xor fbcon tileblit font bitblit softcursor i915 drm i2c_algo_bit ohci1394 ieee1394 e1000e video output intel_agp
Oct 31 12:27:27 carlos-desktop kernel: [    5.970133] Pid: 971, comm: work_for_cpu Tainted: P         C 2.6.31-14-generic #48-Ubuntu         
Oct 31 12:27:27 carlos-desktop kernel: [    5.970135] RIP: 0010:[<ffffc90019cf443c>]  [<ffffc90019cf443c>] 0xffffc90019cf443c
Oct 31 12:27:27 carlos-desktop kernel: [    5.970139] RSP: 0000:ffff880076e899e8  EFLAGS: 00010206
Oct 31 12:27:27 carlos-desktop kernel: [    5.970142] RAX: 0000003fffff7bc0 RBX: ffffc90019d46000 RCX: 0000000000000005
Oct 31 12:27:27 carlos-desktop kernel: [    5.970144] RDX: 0000000000000000 RSI: 0000000000000000 RDI: 0000000000000005
Oct 31 12:27:27 carlos-desktop kernel: [    5.970146] RBP: ffff880076e89bb0 R08: 0000000000000000 R09: 0000000000000000
Oct 31 12:27:27 carlos-desktop kernel: [    5.970149] R10: ffffffffa01d28d0 R11: 0000000000000000 R12: 00000000fffffdef
Oct 31 12:27:27 carlos-desktop kernel: [    5.970151] R13: 0000000000000000 R14: ffff880076fcd030 R15: ffffc90019d3c950
Oct 31 12:27:27 carlos-desktop kernel: [    5.970154] FS:  0000000000000000(0000) GS:ffff8800019f4000(0000) knlGS:0000000000000000
Oct 31 12:27:27 carlos-desktop kernel: [    5.970156] CS:  0010 DS: 0018 ES: 0018 CR0: 0000000080050033
Oct 31 12:27:27 carlos-desktop kernel: [    5.970158] CR2: ffffc94019d34510 CR3: 0000000079d67000 CR4: 00000000000006f0
Oct 31 12:27:27 carlos-desktop kernel: [    5.970161] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Oct 31 12:27:27 carlos-desktop kernel: [    5.970163] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Oct 31 12:27:27 carlos-desktop kernel: [    5.970166] Process work_for_cpu (pid: 971, threadinfo ffff880076e88000, task ffff880076e80000)
Oct 31 12:27:27 carlos-desktop kernel: [    5.970168] Stack:
Oct 31 12:27:27 carlos-desktop kernel: [    5.970170]  ffffc90019d46000 ffffc90019d11cb9 0000000000000000 ffffc90019cf1c20
Oct 31 12:27:27 carlos-desktop kernel: [    5.970174] <0> 0000000000000000 ffff880076fcd030 ffff880076fcd230 ffff880076c12580
Oct 31 12:27:27 carlos-desktop kernel: [    5.970178] <0> 0000000000000160 0000000000000000 ffffc90019d46000 ffffc90019d0183e
Oct 31 12:27:27 carlos-desktop kernel: [    5.970183] Call Trace:
Oct 31 12:27:27 carlos-desktop kernel: [    5.970205]  [<ffffffffa01dae3e>] ? RtlZeroMemory+0xe/0x10 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970229]  [<ffffffffa01e1ec7>] ? win2lin2+0xe/0x11 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970245]  [<ffffffffa01e1edb>] ? win2lin3+0x11/0x14 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970260]  [<ffffffffa01d620a>] ? IofCompleteRequest+0x18a/0x1c0 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970276]  [<ffffffffa01de03a>] ? mp_init+0x6a/0x200 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970290]  [<ffffffffa01d60d9>] ? IofCompleteRequest+0x59/0x1c0 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970305]  [<ffffffffa01d856d>] ? pdoDispatchPnp+0x3d/0xf0 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970321]  [<ffffffffa01df117>] ndis_start_device+0x27/0x860 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970336]  [<ffffffffa01d5705>] ? IofCallDriver+0x65/0xc0 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970342]  [<ffffffff815295d4>] ? _spin_unlock_bh+0x14/0x20
Oct 31 12:27:27 carlos-desktop kernel: [    5.970357]  [<ffffffffa01d5690>] ? IoReleaseCancelSpinLock+0x10/0x20 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970371]  [<ffffffffa01d56d9>] ? IofCallDriver+0x39/0xc0 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970386]  [<ffffffffa01d5c61>] ? IoSyncForwardIrp+0x91/0xd0 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970401]  [<ffffffffa01df9f3>] NdisDispatchPnp+0xa3/0x150 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970417]  [<ffffffffa01e1ec7>] win2lin2+0xe/0x11 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970432]  [<ffffffffa01d5690>] ? IoReleaseCancelSpinLock+0x10/0x20 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970446]  [<ffffffffa01d5705>] ? IofCallDriver+0x65/0xc0 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970450]  [<ffffffff815295d4>] ? _spin_unlock_bh+0x14/0x20
Oct 31 12:27:27 carlos-desktop kernel: [    5.970464]  [<ffffffffa01d5690>] ? IoReleaseCancelSpinLock+0x10/0x20 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970479]  [<ffffffffa01d56d9>] ? IofCallDriver+0x39/0xc0 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970494]  [<ffffffffa01d7638>] IoSendIrpTopDev+0xd8/0x120 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970497]  [<ffffffff815295d4>] ? _spin_unlock_bh+0x14/0x20
Oct 31 12:27:27 carlos-desktop kernel: [    5.970512]  [<ffffffffa01d5543>] ? IoAttachDeviceToDeviceStack+0x63/0x80 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970527]  [<ffffffffa01d79f7>] pnp_start_device+0x47/0x90 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970542]  [<ffffffffa01d7cf1>] wrap_pnp_start_device+0x121/0x180 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970548]  [<ffffffff81073f60>] ? do_work_for_cpu+0x0/0x30
Oct 31 12:27:27 carlos-desktop kernel: [    5.970563]  [<ffffffffa01d7ec0>] wrap_pnp_start_pci_device+0x60/0x80 [ndiswrapper]
Oct 31 12:27:27 carlos-desktop kernel: [    5.970567]  [<ffffffff8128ddf2>] local_pci_probe+0x12/0x20
Oct 31 12:27:27 carlos-desktop kernel: [    5.970570]  [<ffffffff81073f73>] do_work_for_cpu+0x13/0x30
Oct 31 12:27:27 carlos-desktop kernel: [    5.970573]  [<ffffffff81078746>] kthread+0xa6/0xb0
Oct 31 12:27:27 carlos-desktop kernel: [    5.970576]  [<ffffffff810130ea>] child_rip+0xa/0x20
Oct 31 12:27:27 carlos-desktop kernel: [    5.970579]  [<ffffffff810786a0>] ? kthread+0x0/0xb0
Oct 31 12:27:27 carlos-desktop kernel: [    5.970582]  [<ffffffff810130e0>] ? child_rip+0x0/0x20
```

---

