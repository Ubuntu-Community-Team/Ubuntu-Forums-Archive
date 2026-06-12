---
title: "Kernel Panics"
date: 2010-04-26
forum: General Help
---

### Post by infecticide on 2010-04-26
I've been having this issue on and off for about a year now.  When I plugin a usb key or my blackberry (both mass storage) the kernel panics.

I finally got around to installing and setting up netconsole.

During the first panic I could see it mentions poem which is a component of BOINC.  So I shutdown BOINC and tried again and here's what I got:

```
$ netcat -l -u -p 6666 | tee netconsole.log 
[  319.260114] usb 6-3: new full speed USB device using ohci_hcd and address 3
[  319.474540] usb 6-3: configuration #1 chosen from 1 choice
[  319.476387] pl2303 6-3:1.0: pl2303 converter detected
[  319.500035] usb 6-3: pl2303 converter now attached to ttyUSB0
[  326.263565] usb 6-3: USB disconnect, address 3
[  326.264342] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[  326.264377] pl2303 6-3:1.0: device disconnected
[  331.160105] usb 1-3: new high speed USB device using ehci_hcd and address 5
[  331.312574] usb 1-3: configuration #1 chosen from 1 choice
[  331.361092] Initializing USB Mass Storage driver...
[  331.361595] scsi6 : SCSI emulation for USB Mass Storage devices
[  331.361696] usb-storage: device found at 5
[  331.361699] usbcore: registered new interface driver usb-storage
[  331.361704] USB Mass Storage support registered.
[  331.361716] usb-storage: waiting for device to settle before scanning
[  336.350500] usb-storage: device scan complete
[  336.352105] BUG: unable to handle kernel paging request at ffff880023243000
[  336.352121] IP: [<ffffffff812807cb>] memcpy_c+0xb/0x20
[  336.352143] PGD 1002063 PUD 1006063 PMD 232001e2 
[  336.352161] Oops: 0000 [#1] SMP 
[  336.352174] last sysfs file: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.1/bInterfaceProtocol
[  336.352184] CPU 3 
[  336.352191] Modules linked in: usb_storage pl2303 usbserial binfmt_misc nls_cp437 cifs ppdev kvm_amd kvm snd_hda_codec_analog nfsd exportfs nfs lockd nfs_acl auth_rpcgss sunrpc snd_usb_audio snd_usb_lib snd_hda_intel snd_hda_codec snd_seq_dummy snd_hwdep snd_seq_oss netconsole snd_seq_midi snd_pcm_oss snd_mixer_oss snd_rawmidi amd64_edac_mod snd_seq_midi_event snd_pcm psmouse snd_page_alloc snd_seq edac_core snd_timer snd_seq_device snd soundcore configfs uvcvideo videodev v4l1_compat v4l2_compat_ioctl32 iptable_filter ip_tables x_tables asus_atk0110 nvidia(P) serio_raw i2c_piix4 lp parport raid10 raid456 hid_logitech ff_memless usbhid raid6_pq async_xor async_memcpy async_tx raid1 raid0 multipath linear dm_raid45 xor ohci1394 r8169 mii ieee1394
[  336.352465] Pid: 0, comm: swapper Tainted: P           2.6.31-20-generic #58-Ubuntu System Product Name
[  336.352473] RIP: 0010:[<ffffffff812807cb>]  [<ffffffff812807cb>] memcpy_c+0xb/0x20
[  336.352489] RSP: 0018:ffff88002807fb50  EFLAGS: 00010002
[  336.352497] RAX: ffff880117c47340 RBX: 0000000000001364 RCX: 0000000000000004
[  336.352504] RDX: 0000000000000004 RSI: ffff880023243000 RDI: ffff880117c47340
[  336.352512] RBP: ffff88002807fb98 R08: ffff880000000000 R09: 0000000000000024
[  336.352519] R10: 0000000000000000 R11: 00000000ffffff86 R12: ffff880023243000
[  336.352526] R13: ffff880117c9aa80 R14: 0000000000000024 R15: 0000000000000024
[  336.352535] FS:  00007ff7c2e916f0(0000) GS:ffff88002807c000(0000) knlGS:00000000f5a8db70
[  336.352543] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
[  336.352551] CR2: ffff880023243000 CR3: 00000001198e4000 CR4: 00000000000006e0
[  336.352558] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  336.352566] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  336.352574] Process swapper (pid: 0, threadinfo ffff880133ac6000, task ffff880133ac96b0)
[  336.352581] Stack:
[  336.352586]  ffffffff813b2419 0000000000000003 0000000000000024 ffff880028091880
[  336.352602] <0> 0000000000000000 0000000023243000 0000000000000024 ffff880117c9aa80
[  336.352624] <0> 0000000000001000 ffff88002807fbe8 ffffffff813b3929 ffff88002807fc18
[  336.352648] Call Trace:
[  336.352654]  <IRQ> 
[  336.352669]  [<ffffffff813b2419>] ? mon_copy_to_buff+0x79/0xa0
[  336.352682]  [<ffffffff813b3929>] mon_dmapeek_vec+0x99/0x100
[  336.352693]  [<ffffffff813b289f>] mon_bin_event+0x45f/0x520
[  336.352704]  [<ffffffff813b2970>] mon_bin_complete+0x10/0x20
[  336.352714]  [<ffffffff813b051d>] mon_bus_complete+0x4d/0x80
[  336.352724]  [<ffffffff813b0575>] mon_complete+0x25/0x50
[  336.352735]  [<ffffffff813a1203>] usb_hcd_giveback_urb+0x93/0xe0
[  336.352745]  [<ffffffff813b75ca>] ehci_urb_done+0xca/0xf0
[  336.352755]  [<ffffffff813b7ded>] qh_completions+0x3dd/0x490
[  336.352764]  [<ffffffff813b8600>] scan_async+0x90/0x180
[  336.352783]  [<ffffffffa002648c>] ? rtl8169_poll+0x1ec/0x270 [r8169]
[  336.352793]  [<ffffffff813b8b43>] ehci_work+0x33/0x80
[  336.352802]  [<ffffffff813b9179>] ehci_irq+0x229/0x230
[  336.352814]  [<ffffffff81018b39>] ? read_tsc+0x9/0x20
[  336.352824]  [<ffffffff813a08db>] usb_hcd_irq+0x3b/0x80
[  336.352835]  [<ffffffff810b39f8>] handle_IRQ_event+0x58/0x160
[  336.352845]  [<ffffffff8107e873>] ? sched_clock_tick+0x83/0xd0
[  336.352855]  [<ffffffff810b5b50>] handle_fasteoi_irq+0x80/0x100
[  336.352865]  [<ffffffff81014c9d>] handle_irq+0x1d/0x30
[  336.352874]  [<ffffffff81014177>] do_IRQ+0x67/0xe0
[  336.352885]  [<ffffffff81012a93>] ret_from_intr+0x0/0x11
[  336.352892]  <EOI> 
[  336.352904]  [<ffffffff810356f6>] ? native_safe_halt+0x6/0x10
[  336.352914]  [<ffffffff8101a24c>] ? default_idle+0x4c/0xe0
[  336.352925]  [<ffffffff810853e9>] ? clockevents_notify+0x49/0xa0
[  336.352935]  [<ffffffff8101a37a>] ? c1e_idle+0x9a/0x120
[  336.352945]  [<ffffffff81010e52>] ? cpu_idle+0xb2/0x100
[  336.352956]  [<ffffffff815270aa>] ? start_secondary+0xa9/0xab
[  336.352963] Code: 81 ea d8 1f 00 00 48 3b 42 20 73 07 48 8b 50 f9 31 c0 c3 31 d2 48 c7 c0 f2 ff ff ff c3 90 90 90 48 89 f8 89 d1 c1 e9 03 83 e2 07 <f3> 48 a5 89 d1 f3 a4 c3 66 66 66 66 2e 0f 1f 84 00 00 00 00 00 
[  336.353169] RIP  [<ffffffff812807cb>] memcpy_c+0xb/0x20
[  336.353183]  RSP <ffff88002807fb50>
[  336.353189] CR2: ffff880023243000
[  336.353197] ---[ end trace 45d1f055ac450c9a ]---
[  336.353204] Kernel panic - not syncing: Fatal exception in interrupt
[  336.353213] Pid: 0, comm: swapper Tainted: P      D    2.6.31-20-generic #58-Ubuntu
[  336.353220] Call Trace:
[  336.353225]  <IRQ>  [<ffffffff8152a0dd>] panic+0x73/0x12b
[  336.353243]  [<ffffffff8152dc7a>] oops_end+0xea/0xf0
[  336.353253]  [<ffffffff8103cdcb>] no_context+0xeb/0x180
[  336.353264]  [<ffffffff8146d8f8>] ? ip_output+0xb8/0xc0
[  336.353274]  [<ffffffff8103cfa5>] __bad_area_nosemaphore+0x145/0x200
[  336.353285]  [<ffffffff8146bd5a>] ? ip_queue_xmit+0x18a/0x400
[  336.353295]  [<ffffffff81036419>] ? default_spin_lock_flags+0x9/0x10
[  336.353306]  [<ffffffff8152c98a>] ? _spin_lock_irqsave+0x2a/0x40
[  336.353316]  [<ffffffff8106af57>] ? lock_timer_base+0x37/0x70
[  336.353325]  [<ffffffff8103d06e>] bad_area_nosemaphore+0xe/0x10
[  336.353335]  [<ffffffff8152f764>] do_page_fault+0x2c4/0x370
[  336.353345]  [<ffffffff8152cf85>] page_fault+0x25/0x30
[  336.353356]  [<ffffffff812807cb>] ? memcpy_c+0xb/0x20
[  336.353366]  [<ffffffff813b2419>] ? mon_copy_to_buff+0x79/0xa0
[  336.353377]  [<ffffffff813b3929>] mon_dmapeek_vec+0x99/0x100
[  336.353387]  [<ffffffff813b289f>] mon_bin_event+0x45f/0x520
[  336.353398]  [<ffffffff813b2970>] mon_bin_complete+0x10/0x20
[  336.353407]  [<ffffffff813b051d>] mon_bus_complete+0x4d/0x80
[  336.353417]  [<ffffffff813b0575>] mon_complete+0x25/0x50
[  336.353427]  [<ffffffff813a1203>] usb_hcd_giveback_urb+0x93/0xe0
[  336.353436]  [<ffffffff813b75ca>] ehci_urb_done+0xca/0xf0
[  336.353445]  [<ffffffff813b7ded>] qh_completions+0x3dd/0x490
[  336.353455]  [<ffffffff813b8600>] scan_async+0x90/0x180
[  336.353475]  [<ffffffffa002648c>] ? rtl8169_poll+0x1ec/0x270 [r8169]
[  336.353484]  [<ffffffff813b8b43>] ehci_work+0x33/0x80
[  336.353492]  [<ffffffff813b9179>] ehci_irq+0x229/0x230
[  336.353502]  [<ffffffff81018b39>] ? read_tsc+0x9/0x20
[  336.353512]  [<ffffffff813a08db>] usb_hcd_irq+0x3b/0x80
[  336.353522]  [<ffffffff810b39f8>] handle_IRQ_event+0x58/0x160
[  336.353531]  [<ffffffff8107e873>] ? sched_clock_tick+0x83/0xd0
[  336.353540]  [<ffffffff810b5b50>] handle_fasteoi_irq+0x80/0x100
[  336.353549]  [<ffffffff81014c9d>] handle_irq+0x1d/0x30
[  336.353559]  [<ffffffff81014177>] do_IRQ+0x67/0xe0
[  336.353569]  [<ffffffff81012a93>] ret_from_intr+0x0/0x11
[  336.353575]  <EOI>  [<ffffffff810356f6>] ? native_safe_halt+0x6/0x10
[  336.353593]  [<ffffffff8101a24c>] ? default_idle+0x4c/0xe0
[  336.353603]  [<ffffffff810853e9>] ? clockevents_notify+0x49/0xa0
[  336.353613]  [<ffffffff8101a37a>] ? c1e_idle+0x9a/0x120
[  336.353623]  [<ffffffff81010e52>] ? cpu_idle+0xb2/0x100
[  336.353632]  [<ffffffff815270aa>] ? start_secondary+0xa9/0xab
```

I rebooted and shutdown BOINC, KDM, and removed the NVIDIA module entirely from the kernel.

Didn't help:
```

$ netcat -l -u -p 6666 | tee netconsole.log 
[  535.990147] usb 1-3: new high speed USB device using ehci_hcd and address 5
[  536.146233] usb 1-3: configuration #1 chosen from 1 choice
[  536.203296] Initializing USB Mass Storage driver...
[  536.203711] scsi6 : SCSI emulation for USB Mass Storage devices
[  536.203989] usb-storage: device found at 5
[  536.204012] usbcore: registered new interface driver usb-storage
[  536.204017] USB Mass Storage support registered.
[  536.204174] usb-storage: waiting for device to settle before scanning
[  541.200518] usb-storage: device scan complete
[  541.202854] BUG: unable to handle kernel paging request at ffff8800208c6000
[  541.203010] IP: [<ffffffff812807cb>] memcpy_c+0xb/0x20
[  541.203125] PGD 1002063 PUD 1006063 PMD 208001e2 
[  541.203319] Oops: 0000 [#1] SMP 
[  541.203465] last sysfs file: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.1/bInterfaceProtocol
[  541.203538] CPU 3 
[  541.203637] Modules linked in: usb_storage nls_cp437 cifs binfmt_misc ppdev kvm_amd kvm snd_hda_codec_analog nfsd exportfs nfs lockd nfs_acl auth_rpcgss sunrpc netconsole configfs snd_usb_audio snd_usb_lib snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm iptable_filter snd_seq_dummy ip_tables snd_seq_oss x_tables snd_seq_midi snd_seq_midi_event lp snd_seq parport snd_rawmidi snd_timer snd_hwdep psmouse snd_seq_device uvcvideo amd64_edac_mod videodev v4l1_compat serio_raw v4l2_compat_ioctl32 snd soundcore snd_page_alloc asus_atk0110 i2c_piix4 edac_core raid10 raid456 hid_logitech ff_memless usbhid raid6_pq async_xor async_memcpy async_tx raid1 raid0 multipath linear dm_raid45 xor r8169 mii ohci1394 ieee1394 [last unloaded: nvidia]
[  541.207046] Pid: 0, comm: swapper Tainted: P           2.6.31-20-generic #58-Ubuntu System Product Name
[  541.207119] RIP: 0010:[<ffffffff812807cb>]  [<ffffffff812807cb>] memcpy_c+0xb/0x20
[  541.207238] RSP: 0018:ffff88002807fb50  EFLAGS: 00010002
[  541.207298] RAX: ffff880117953340 RBX: 0000000000001364 RCX: 0000000000000004
[  541.207361] RDX: 0000000000000004 RSI: ffff8800208c6000 RDI: ffff880117953340
[  541.207423] RBP: ffff88002807fb98 R08: ffff880000000000 R09: 0000000000000024
[  541.207485] R10: 0000000000000000 R11: 00000000ffffff86 R12: ffff8800208c6000
[  541.207548] R13: ffff88012fdf26c0 R14: 0000000000000024 R15: 0000000000000024
[  541.207611] FS:  00007fbf3f9cb910(0000) GS:ffff88002807c000(0000) knlGS:000000005571f6c0
[  541.207682] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
[  541.207743] CR2: ffff8800208c6000 CR3: 000000011bc3c000 CR4: 00000000000006e0
[  541.207805] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  541.207868] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  541.207931] Process swapper (pid: 0, threadinfo ffff880133ac6000, task ffff880133ac96b0)
[  541.208000] Stack:
[  541.208055]  ffffffff813b2419 0000000000000003 0000000000000024 ffff880028091880
[  541.208252] <0> 0000000000000000 00000000208c6000 0000000000000024 ffff88012fdf26c0
[  541.208542] <0> 0000000000001000 ffff88002807fbe8 ffffffff813b3929 ffff88002807fc18
[  541.208885] Call Trace:
[  541.208941]  <IRQ> 
[  541.209048]  [<ffffffff813b2419>] ? mon_copy_to_buff+0x79/0xa0
[  541.209113]  [<ffffffff813b3929>] mon_dmapeek_vec+0x99/0x100
[  541.209177]  [<ffffffff813b289f>] mon_bin_event+0x45f/0x520
[  541.209241]  [<ffffffff813b2970>] mon_bin_complete+0x10/0x20
[  541.209304]  [<ffffffff813b051d>] mon_bus_complete+0x4d/0x80
[  541.209367]  [<ffffffff813b0575>] mon_complete+0x25/0x50
[  541.209430]  [<ffffffff813a1203>] usb_hcd_giveback_urb+0x93/0xe0
[  541.209493]  [<ffffffff813b75ca>] ehci_urb_done+0xca/0xf0
[  541.209555]  [<ffffffff813b7ded>] qh_completions+0x3dd/0x490
[  541.209618]  [<ffffffff813b8600>] scan_async+0x90/0x180
[  541.209679]  [<ffffffff813b8b43>] ehci_work+0x33/0x80
[  541.209741]  [<ffffffff813b9179>] ehci_irq+0x229/0x230
[  541.210349]  [<ffffffff81018b39>] ? read_tsc+0x9/0x20
[  541.210413]  [<ffffffff813a08db>] usb_hcd_irq+0x3b/0x80
[  541.210477]  [<ffffffff810b39f8>] handle_IRQ_event+0x58/0x160
[  541.210540]  [<ffffffff8107e873>] ? sched_clock_tick+0x83/0xd0
[  541.210603]  [<ffffffff810b5b50>] handle_fasteoi_irq+0x80/0x100
[  541.210666]  [<ffffffff81014c9d>] handle_irq+0x1d/0x30
[  541.210726]  [<ffffffff81014177>] do_IRQ+0x67/0xe0
[  541.210789]  [<ffffffff81012a93>] ret_from_intr+0x0/0x11
[  541.210848]  <EOI> 
[  541.210953]  [<ffffffff810356f6>] ? native_safe_halt+0x6/0x10
[  541.211016]  [<ffffffff8101a24c>] ? default_idle+0x4c/0xe0
[  541.211080]  [<ffffffff810853e9>] ? clockevents_notify+0x49/0xa0
[  541.211143]  [<ffffffff8101a37a>] ? c1e_idle+0x9a/0x120
[  541.211205]  [<ffffffff81010e52>] ? cpu_idle+0xb2/0x100
[  541.211268]  [<ffffffff815270aa>] ? start_secondary+0xa9/0xab
[  541.211328] Code: 81 ea d8 1f 00 00 48 3b 42 20 73 07 48 8b 50 f9 31 c0 c3 31 d2 48 c7 c0 f2 ff ff ff c3 90 90 90 48 89 f8 89 d1 c1 e9 03 83 e2 07 <f3> 48 a5 89 d1 f3 a4 c3 66 66 66 66 2e 0f 1f 84 00 00 00 00 00 
[  541.212827] RIP  [<ffffffff812807cb>] memcpy_c+0xb/0x20
[  541.212827]  RSP <ffff88002807fb50>
[  541.212827] CR2: ffff8800208c6000
[  541.212827] ---[ end trace 78536bd973a58400 ]---
[  541.212827] Kernel panic - not syncing: Fatal exception in interrupt
[  541.212827] Pid: 0, comm: swapper Tainted: P      D    2.6.31-20-generic #58-Ubuntu
[  541.212827] Call Trace:
[  541.212827]  <IRQ>  [<ffffffff8152a0dd>] panic+0x73/0x12b
[  541.212827]  [<ffffffff8152dc7a>] oops_end+0xea/0xf0
[  541.212827]  [<ffffffff8103cdcb>] no_context+0xeb/0x180
[  541.212827]  [<ffffffff8143e1a2>] ? dev_queue_xmit+0x112/0x430
[  541.212827]  [<ffffffff8103cfa5>] __bad_area_nosemaphore+0x145/0x200
[  541.212827]  [<ffffffff8146d664>] ? ip_finish_output+0x134/0x310
[  541.212827]  [<ffffffff8146d8f8>] ? ip_output+0xb8/0xc0
[  541.212827]  [<ffffffff8146a876>] ? ip_cork_release+0x36/0x50
[  541.212827]  [<ffffffff8146baeb>] ? ip_push_pending_frames+0x33b/0x420
[  541.212827]  [<ffffffff8103d06e>] bad_area_nosemaphore+0xe/0x10
[  541.212827]  [<ffffffff8152f764>] do_page_fault+0x2c4/0x370
[  541.212827]  [<ffffffff8146d4fc>] ? ip_send_reply+0x24c/0x280
[  541.212827]  [<ffffffff8152cf85>] page_fault+0x25/0x30
[  541.212827]  [<ffffffff812807cb>] ? memcpy_c+0xb/0x20
[  541.212827]  [<ffffffff813b2419>] ? mon_copy_to_buff+0x79/0xa0
[  541.212827]  [<ffffffff813b3929>] mon_dmapeek_vec+0x99/0x100
[  541.212827]  [<ffffffff813b289f>] mon_bin_event+0x45f/0x520
[  541.212827]  [<ffffffff813b2970>] mon_bin_complete+0x10/0x20
[  541.212827]  [<ffffffff813b051d>] mon_bus_complete+0x4d/0x80
[  541.212827]  [<ffffffff813b0575>] mon_complete+0x25/0x50
[  541.212827]  [<ffffffff813a1203>] usb_hcd_giveback_urb+0x93/0xe0
[  541.212827]  [<ffffffff813b75ca>] ehci_urb_done+0xca/0xf0
[  541.212827]  [<ffffffff813b7ded>] qh_completions+0x3dd/0x490
[  541.212827]  [<ffffffff813b8600>] scan_async+0x90/0x180
[  541.212827]  [<ffffffff813b8b43>] ehci_work+0x33/0x80
[  541.212827]  [<ffffffff813b9179>] ehci_irq+0x229/0x230
[  541.212827]  [<ffffffff81018b39>] ? read_tsc+0x9/0x20
[  541.212827]  [<ffffffff813a08db>] usb_hcd_irq+0x3b/0x80
[  541.212827]  [<ffffffff810b39f8>] handle_IRQ_event+0x58/0x160
[  541.212827]  [<ffffffff8107e873>] ? sched_clock_tick+0x83/0xd0
[  541.212827]  [<ffffffff810b5b50>] handle_fasteoi_irq+0x80/0x100
[  541.212827]  [<ffffffff81014c9d>] handle_irq+0x1d/0x30
[  541.212827]  [<ffffffff81014177>] do_IRQ+0x67/0xe0
[  541.212827]  [<ffffffff81012a93>] ret_from_intr+0x0/0x11
[  541.212827]  <EOI>  [<ffffffff810356f6>] ? native_safe_halt+0x6/0x10
[  541.212827]  [<ffffffff8101a24c>] ? default_idle+0x4c/0xe0
[  541.212827]  [<ffffffff810853e9>] ? clockevents_notify+0x49/0xa0
[  541.212827]  [<ffffffff8101a37a>] ? c1e_idle+0x9a/0x120
[  541.212827]  [<ffffffff81010e52>] ? cpu_idle+0xb2/0x100
[  541.212827]  [<ffffffff815270aa>] ? start_secondary+0xa9/0xab

```

Since I'm not a kernel debug expert, where do I start?  Or can someone here help me out?

I do know that if I go into "recovery mode" it doesn't panic.

---

### Post by infecticide on 2010-04-29
Trying to access a CIFS mounted DNS323 NAS I get a panic, I have three NAS boxes which are all identical but only one causes this issue:

```

[  685.050002] BUG: soft lockup - CPU#0 stuck for 61s! [dolphin:2611]
[  685.050002] Modules linked in: pl2303 usbserial binfmt_misc ppdev kvm_amd kvm nls_cp437 cifs snd_hda_codec_analog nfsd exportfs nfs snd_hda_intel snd_hda_codec lockd snd_usb_audio nfs_acl snd_usb_lib snd_pcm_oss snd_mixer_oss snd_hwdep snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer auth_rpcgss snd_seq_device snd sunrpc nvidia(P) iptable_filter uvcvideo videodev ip_tables v4l1_compat soundcore i2c_piix4 netconsole snd_page_alloc configfs v4l2_compat_ioctl32 x_tables psmouse serio_raw asus_atk0110 amd64_edac_mod edac_core lp parport raid10 raid456 hid_logitech ff_memless usbhid raid6_pq async_xor async_memcpy async_tx raid1 raid0 multipath r8169 snd_hda_codec_analog snd_hda_intel snd_usb_lib snd_pcm snd_seq_midi_event auth_rpcgss iptable_filter v4l1_compat netconsole v4l2_compat_ioctl32 asus_atk0110 parport ff_memless async_memcpy multipath ohci1394
[  685.050002] Pid: 2611, comm: dolphin Tainted: P           2.6.31-21-generic #59-Ubuntu System Product Name
[  685.050002] RIP: 0010:[<ffffffffa0dcea10>]  [<ffffffffa0dcea10>] build_path_from_dentry+0x80/0x240 [cifs]
[  685.050002] RSP: 0018:ffff8800b4d21b78  EFLAGS: 00000283
[  685.050002] RAX: ffff8801334e2cc0 RBX: ffff8800b4d21bc8 RCX: ffff880130c5a8a0
[  685.050002] RDX: ffff880081eec000 RSI: 0000000000000039 RDI: ffff880118847630
[  685.050002] RBP: ffffffff81012a8e R08: 0000000000000001 R09: 0000000000000000
[  685.050002] R10: 000000000000007d R11: 0000000000000246 R12: ffff8800b4d21af8
[  685.050002] R13: ffff8800b4d21af8 R14: ffffffff81036419 R15: ffff8800b4d21ad8
[  685.050002] FS:  00007fc04adc2750(0000) GS:ffff880028022000(0000) knlGS:0000000000000000
[  685.050002] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  685.050002] CR2: 00007fc04ade2000 CR3: 000000008b471000 CR4: 00000000000006f0
[  685.050002] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  685.050002] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  685.050002] Call Trace:
[  685.050002]  [<ffffffffa0dceae2>] ? build_path_from_dentry+0x152/0x240 [cifs]
[  685.050002]  [<ffffffffa0dd732b>] ? cifs_revalidate+0x9b/0x420 [cifs]
[  685.050002]  [<ffffffff8152df99>] ? _spin_lock+0x9/0x10
[  685.050002]  [<ffffffffa0dd0380>] ? cifs_d_revalidate+0x20/0xf0 [cifs]
[  685.050002]  [<ffffffff8112b1c5>] ? do_lookup+0x55/0xe0
[  685.050002]  [<ffffffff8112b715>] ? __link_path_walk+0x155/0xdb0
[  685.050002]  [<ffffffff8112c557>] ? path_walk+0x57/0xb0
[  685.050002]  [<ffffffff8112c6e3>] ? do_path_lookup+0x53/0xa0
[  685.050002]  [<ffffffff8112d382>] ? user_path_at+0x52/0xa0
[  685.050002]  [<ffffffff8112a57c>] ? path_put+0x2c/0x40
[  685.050002]  [<ffffffff81129ffe>] ? putname+0x2e/0x40
[  685.050002]  [<ffffffff8112d38d>] ? user_path_at+0x5d/0xa0
[  685.050002]  [<ffffffff811244b7>] ? vfs_fstatat+0x37/0x70
[  685.050002]  [<ffffffff811395ab>] ? mntput_no_expire+0x2b/0x100
[  685.050002]  [<ffffffff81124616>] ? vfs_stat+0x16/0x20
[  685.050002]  [<ffffffff8112463f>] ? sys_newstat+0x1f/0x50
[  685.050002]  [<ffffffff8107ea7a>] ? __put_cred+0x1a/0x20
[  685.050002]  [<ffffffff8111e91e>] ? sys_faccessat+0x19e/0x1d0
[  685.050002]  [<ffffffff81012082>] ? system_call_fastpath+0x16/0x1b
[  686.121251] BUG: soft lockup - CPU#1 stuck for 61s! [plasma-desktop:2296]
[  686.121251] Modules linked in: pl2303 usbserial binfmt_misc ppdev kvm_amd kvm nls_cp437 cifs snd_hda_codec_analog nfsd exportfs nfs snd_hda_intel snd_hda_codec lockd snd_usb_audio nfs_acl snd_usb_lib snd_pcm_oss snd_mixer_oss snd_hwdep snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer auth_rpcgss snd_seq_device snd sunrpc nvidia(P) iptable_filter uvcvideo videodev ip_tables v4l1_compat soundcore i2c_piix4 netconsole snd_page_alloc configfs v4l2_compat_ioctl32 x_tables psmouse serio_raw asus_atk0110 amd64_edac_mod edac_core lp parport raid10 raid456 hid_logitech ff_memless usbhid raid6_pq async_xor async_memcpy async_tx raid1 raid0 multipath linear dm_raid45 xor ohci1394 ieee1394 r8169 mii
[  686.121251] CPU 1:
[  686.121251] Modules linked in: pl2303 usbserial binfmt_misc ppdev kvm snd_hda_codec_analog exportfs lockd snd_usb_lib snd_mixer_oss snd_seq_dummy snd_seq_midi snd_seq auth_rpcgss sunrpc iptable_filter ip_tables soundcore snd_page_alloc v4l2_compat_ioctl32 serio_raw amd64_edac_mod parport hid_logitech raid6_pq async_memcpy raid0 dm_raid45 ohci1394
[  686.121251] Pid: 2296, comm: plasma-desktop Tainted: P           2.6.31-21-generic #59-Ubuntu System Product Name
[  686.121251] RIP: 0010:[<ffffffffa0dcea00>]  [<ffffffffa0dcea00>] build_path_from_dentry+0x70/0x240 [cifs]
[  686.121251] RSP: 0018:ffff880110dc5d58  EFLAGS: 00000286
[  686.121251] RAX: 0000000000000006 RBX: ffff880110dc5da8 RCX: ffff880130c5a8a0
[  686.121251] RDX: ffff8801334e2cc0 RSI: 0000000000000039 RDI: ffff880118847630
[  686.121251] RBP: ffffffff81012c2e R08: 0000000000000001 R09: 0000000000000000
[  686.121251] R10: 0000000000000047 R11: 0000000000000246 R12: ffffffff8112bf92
[  686.121251] R13: ffff880110dc5d58 R14: ffff880110dc5dd8 R15: ffff88011c4fc2e0
[  686.121251] FS:  00007f0e5fc9d750(0000) GS:ffff880028040000(0000) knlGS:0000000000000000
[  686.121251] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  686.121251] CR2: 00007f9ec6757720 CR3: 0000000110d72000 CR4: 00000000000006e0
[  686.121251] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  686.121251] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  686.121251] Call Trace:
[  686.121251]  [<ffffffffa0dceae2>] ? build_path_from_dentry+0x152/0x240 [cifs]
[  686.121251]  [<ffffffffa0dd732b>] ? cifs_revalidate+0x9b/0x420 [cifs]
[  686.121251]  [<ffffffff81129ffe>] ? putname+0x2e/0x40
[  686.121251]  [<ffffffff8112d38d>] ? user_path_at+0x5d/0xa0
[  686.121251]  [<ffffffffa0dd76ce>] ? cifs_getattr+0x1e/0x60 [cifs]
[  686.121251]  [<ffffffff81124449>] ? vfs_getattr+0x49/0x80
[  686.121251]  [<ffffffff811244d8>] ? vfs_fstatat+0x58/0x70
[  686.121251]  [<ffffffff81225421>] ? security_file_permission+0x11/0x20
[  686.121251]  [<ffffffff81124616>] ? vfs_stat+0x16/0x20
[  686.121251]  [<ffffffff8112463f>] ? sys_newstat+0x1f/0x50
[  686.121251]  [<ffffffff81120a37>] ? sys_read+0x77/0x80
[  686.121251]  [<ffffffff81012082>] ? system_call_fastpath+0x16/0x1b

```

---

