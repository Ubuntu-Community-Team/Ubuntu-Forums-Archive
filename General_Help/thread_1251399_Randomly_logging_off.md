---
title: "Randomly logging off"
date: 2009-08-27
forum: General Help
---

### Post by goldfish654 on 2009-08-27
Hi,

I've got various issues at the moment.  Firefox is randomly segfaulting, as is opera (probably a flash issue).  But, whilst that is annoying, it's not as mystifying the problem I've been having

Sometimes, entirely at random, I get logged out of my GNOME session and get dumped at the GDM prompt.  Here's what happens in dmesg around that time:

```

[ 2202.743023] BUG: unable to handle kernel paging request at 68ae46f0
[ 2202.743030] IP: [<c01a2044>] handle_mm_fault+0x74/0x380
[ 2202.743039] *pde = 00000000 
[ 2202.743043] Oops: 0000 [#1] SMP 
[ 2202.743046] last sysfs file: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
[ 2202.743050] Dumping ftrace buffer:
[ 2202.743053]    (ftrace buffer empty)
[ 2202.743055] Modules linked in: binfmt_misc bridge stp bnep vboxnetadp vboxnetflt vboxdrv video output input_polldev lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) nvidia_agp ppdev pcspkr i2c_nforce2 snd_page_alloc shpchp agpgart parport_pc joydev parport btusb hid_logitech ff_memless usbhid ohci1394 ieee1394 forcedeth floppy fbcon tileblit font bitblit softcursor
[ 2202.743084] 
[ 2202.743087] Pid: 5140, comm: dpkg Tainted: P           (2.6.28-15-generic #49-Ubuntu)  
[ 2202.743090] EIP: 0060:[<c01a2044>] EFLAGS: 00210202 CPU: 0
[ 2202.743093] EIP is at handle_mm_fault+0x74/0x380
[ 2202.743096] EAX: 23228067 EBX: e3228f34 ECX: d6832820 EDX: 23228067
[ 2202.743098] ESI: c1000000 EDI: d6936080 EBP: d68d9e60 ESP: d68d9e1c
[ 2202.743100]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[ 2202.743103] Process dpkg (pid: 5140, ti=d68d8000 task=d68b6480 task.ti=d68d8000)
[ 2202.743105] Stack:
[ 2202.743107]  d6936080 d6936080 c146450c 0b9b6065 d68d9e48 c01ce8de d68d9e80 c1000000
[ 2202.743112]  0b9b6065 080a45ec d68d00b0 d6832820 e3228f34 d6834494 d68d00b0 d6832854
[ 2202.743117]  d6832820 d68d9fb0 c050271d 00000001 d68d9e80 c0137c5f f6c01300 d684aee0
[ 2202.743123] Call Trace:
[ 2202.743125]  [<c01ce8de>] ? d_hash_and_lookup+0x5e/0x80
[ 2202.743132]  [<c050271d>] ? do_page_fault+0x1fd/0x790
[ 2202.743138]  [<c0137c5f>] ? __cleanup_signal+0x2f/0x40
[ 2202.743143]  [<c013c79d>] ? release_task+0x9d/0x110
[ 2202.743147]  [<c013cc4b>] ? wait_task_zombie+0x43b/0x530
[ 2202.743151]  [<c04fe54a>] ? schedule+0x41a/0x710
[ 2202.743157]  [<c012c71c>] ? enqueue_entity+0x13c/0x360
[ 2202.743163]  [<c014f0a8>] ? remove_wait_queue+0x38/0x50
[ 2202.743168]  [<c013d096>] ? do_wait+0x1f6/0x320
[ 2202.743172]  [<c0500136>] ? _spin_lock_irq+0x16/0x20
[ 2202.743175]  [<c0145488>] ? do_sigaction+0xf8/0x1a0
[ 2202.743180]  [<c02cde25>] ? copy_from_user+0x35/0x130
[ 2202.743185]  [<c01455c1>] ? sys_rt_sigaction+0x51/0xa0
[ 2202.743188]  [<c0502520>] ? do_page_fault+0x0/0x790
[ 2202.743191]  [<c0500582>] ? error_code+0x72/0x80
[ 2202.743195] Code: c7 03 79 24 0f 84 e5 00 00 00 8b 07 e8 76 ff f7 ff 90 a8 01 0f 84 be 00 00 00 8b 35 00 93 85 c0 89 75 d8 8b 17 89 d0 e8 5b ff f7 <ff> 90 89 c6 8b 45 d8 ba 07 00 00 00 c1 ee 0c c1 e6 05 01 f0 e8 
[ 2202.743220] EIP: [<c01a2044>] handle_mm_fault+0x74/0x380 SS:ESP 0068:d68d9e1c
[ 2202.743226] ---[ end trace c1669d3af5bfe151 ]---
[ 2431.335215] agpgart-nvidia 0000:00:00.0: AGP 3.0 bridge
[ 2431.335232] agpgart-nvidia 0000:00:00.0: putting AGP V3 device into 8x mode
[ 2431.335290] nvidia 0000:02:00.0: putting AGP V3 device into 8x mode
[ 2432.133573] BUG: unable to handle kernel paging request at 7d8b16f0
[ 2432.133582] IP: [<c01a2044>] handle_mm_fault+0x74/0x380
[ 2432.133592] *pde = 00000000 
[ 2432.133596] Oops: 0000 [#2] SMP 
[ 2432.133600] last sysfs file: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.0/resource
[ 2432.133604] Modules linked in: binfmt_misc bridge stp bnep vboxnetadp vboxnetflt vboxdrv video output input_polldev lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) nvidia_agp ppdev pcspkr i2c_nforce2 snd_page_alloc shpchp agpgart parport_pc joydev parport btusb hid_logitech ff_memless usbhid ohci1394 ieee1394 forcedeth floppy fbcon tileblit font bitblit softcursor
[ 2432.133633] 
[ 2432.133636] Pid: 5514, comm: xkbcomp Tainted: P      D    (2.6.28-15-generic #49-Ubuntu)  
[ 2432.133639] EIP: 0060:[<c01a2044>] EFLAGS: 00213202 CPU: 0
[ 2432.133642] EIP is at handle_mm_fault+0x74/0x380
[ 2432.133645] EAX: 37ff5067 EBX: f22ccb7c ECX: d68336c0 EDX: 37ff5067
[ 2432.133647] ESI: c1000000 EDI: f22ccbf8 EBP: e3115e60 ESP: e3115e1c
[ 2432.133649]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[ 2432.133652] Process xkbcomp (pid: 5514, ti=e3114000 task=f2298c90 task.ti=e3114000)
[ 2432.133654] Stack:
[ 2432.133656]  f22ccbf8 0000004c 00000000 00000000 00000002 f65c72e8 00000000 c1000000
[ 2432.133661]  00000001 bf9f3fcc f21980b0 d68336c0 fffb2c94 f2216cc8 f21980b0 d68336f4
[ 2432.133666]  d68336c0 e3115fb0 c050271d 00000001 000002e6 00000000 00000000 00000000
[ 2432.133672] Call Trace:
[ 2432.133674]  [<c050271d>] ? do_page_fault+0x1fd/0x790
[ 2432.133680]  [<c0190623>] ? generic_file_aio_read+0xa3/0x210
[ 2432.133684]  [<c018e750>] ? file_read_actor+0x0/0xe0
[ 2432.133691]  [<c01bd861>] ? do_sync_read+0xd1/0x110
[ 2432.133697]  [<c01c0fc4>] ? cp_new_stat64+0xe4/0x100
[ 2432.133701]  [<c014ede0>] ? autoremove_wake_function+0x0/0x50
[ 2432.133708]  [<c01d3b7d>] ? mntput_no_expire+0x1d/0x120
[ 2432.133713]  [<c05001f8>] ? _spin_lock+0x8/0x10
[ 2432.133716]  [<c01bedea>] ? __fput+0x14a/0x1c0
[ 2432.133720]  [<c01bee7f>] ? fput+0x1f/0x30
[ 2432.133723]  [<c01bb869>] ? filp_close+0x49/0x70
[ 2432.133726]  [<c01bb90a>] ? sys_close+0x7a/0xc0
[ 2432.133729]  [<c0502520>] ? do_page_fault+0x0/0x790
[ 2432.133732]  [<c0500582>] ? error_code+0x72/0x80
[ 2432.133736] Code: c7 03 79 24 0f 84 e5 00 00 00 8b 07 e8 76 ff f7 ff 90 a8 01 0f 84 be 00 00 00 8b 35 00 93 85 c0 89 75 d8 8b 17 89 d0 e8 5b ff f7 <ff> 90 89 c6 8b 45 d8 ba 07 00 00 00 c1 ee 0c c1 e6 05 01 f0 e8 
[ 2432.133761] EIP: [<c01a2044>] handle_mm_fault+0x74/0x380 SS:ESP 0068:e3115e1c
[ 2432.133766] ---[ end trace c1669d3af5bfe151 ]---
[ 2567.970928] BUG: unable to handle kernel paging request at 68bb16f0
[ 2567.970936] IP: [<c01a2044>] handle_mm_fault+0x74/0x380
[ 2567.970945] *pde = 00000000 
[ 2567.970949] Oops: 0000 [#3] SMP 
[ 2567.970952] last sysfs file: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.0/resource
[ 2567.970956] Modules linked in: binfmt_misc bridge stp bnep vboxnetadp vboxnetflt vboxdrv video output input_polldev lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) nvidia_agp ppdev pcspkr i2c_nforce2 snd_page_alloc shpchp agpgart parport_pc joydev parport btusb hid_logitech ff_memless usbhid ohci1394 ieee1394 forcedeth floppy fbcon tileblit font bitblit softcursor
[ 2567.970985] 
[ 2567.970989] Pid: 5917, comm: rhythmbox Tainted: P      D    (2.6.28-15-generic #49-Ubuntu)  
[ 2567.970992] EIP: 0060:[<c01a2044>] EFLAGS: 00210202 CPU: 0
[ 2567.970995] EIP is at handle_mm_fault+0x74/0x380
[ 2567.970997] EAX: 232f5067 EBX: c8f54b68 ECX: f65411e0 EDX: 232f5067
[ 2567.970999] ESI: c1000000 EDI: c8f54b78 EBP: c8c73e60 ESP: c8c73e1c
[ 2567.971002]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[ 2567.971004] Process rhythmbox (pid: 5917, ti=c8c72000 task=f229e480 task.ti=c8c72000)
[ 2567.971007] Stack:
[ 2567.971008]  c8f54b78 00000005 00000000 00000000 00000002 c11b5c20 c06cd900 c1000000
[ 2567.971014]  c8c73e64 b7a82240 f210cbb0 f65411e0 f213046c 00200216 f210cbb0 f6541214
[ 2567.971019]  f65411e0 c8c73fb0 c050271d 00000000 c8c73e84 c0197705 c8c73e90 c012740d
[ 2567.971025] Call Trace:
[ 2567.971027]  [<c050271d>] ? do_page_fault+0x1fd/0x790
[ 2567.971033]  [<c0197705>] ? put_page+0x45/0xf0
[ 2567.971039]  [<c012740d>] ? kunmap_atomic+0x7d/0xa0
[ 2567.971044]  [<c019ffe4>] ? unmap_vmas+0x1a4/0x380
[ 2567.971047]  [<c05001f8>] ? _spin_lock+0x8/0x10
[ 2567.971050]  [<c01a7b35>] ? anon_vma_unlink+0x45/0x70
[ 2567.971055]  [<c01197d5>] ? flush_tlb_mm+0x45/0xa0
[ 2567.971059]  [<c01a40b6>] ? unmap_region+0xe6/0x120
[ 2567.971063]  [<c01a4136>] ? remove_vma+0x46/0x60
[ 2567.971066]  [<c01a4136>] ? remove_vma+0x46/0x60
[ 2567.971069]  [<c01a4fd5>] ? do_munmap+0x225/0x280
[ 2567.971073]  [<c01a5076>] ? sys_munmap+0x46/0x60
[ 2567.971076]  [<c0502520>] ? do_page_fault+0x0/0x790
[ 2567.971079]  [<c0500582>] ? error_code+0x72/0x80
[ 2567.971083] Code: c7 03 79 24 0f 84 e5 00 00 00 8b 07 e8 76 ff f7 ff 90 a8 01 0f 84 be 00 00 00 8b 35 00 93 85 c0 89 75 d8 8b 17 89 d0 e8 5b ff f7 <ff> 90 89 c6 8b 45 d8 ba 07 00 00 00 c1 ee 0c c1 e6 05 01 f0 e8 
[ 2567.971108] EIP: [<c01a2044>] handle_mm_fault+0x74/0x380 SS:ESP 0068:c8c73e1c
[ 2567.971126] ---[ end trace c1669d3af5bfe151 ]---

```

Any ideas as to why this might be happening?

---

### Post by scragar on 2009-08-27
How many sticks of ram do you have? It might be worth removing one of them for a while, and seeing if the problems occur, then switching sticks and repeating. It sounds to me like a ram failure(hence loads of different programs all crash somewhat randomly, because ram is not storing the right details, causing bugs and errors).
Not a perfect solution, but it's a lot better than taking it into a shop for repairs.

---

### Post by goldfish654 on 2009-08-27
I have 2 sticks of RAM, 512MB each.  I'll try it.

---

### Post by paradigm2 on 2009-08-27
Get memtester from synaptic and run a test with 3 passes.  Or use memtest86 that comes witht he ubuntu install disk. Let us know the results.

---

