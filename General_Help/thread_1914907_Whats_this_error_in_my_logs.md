---
title: "Whats this error in my logs?"
date: 2012-01-25
forum: General Help
---

### Post by hopelessone on 2012-01-25
Hi All,

My computer froze and I checked the logs:
```
Jan 25 22:19:04 oneiric kernel: [24986.371964] general protection fault: 0000 [#1] SMP 
Jan 25 22:19:04 oneiric kernel: [24986.372022] CPU 1 
Jan 25 22:19:04 oneiric kernel: [24986.372040] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat usb_storage uas rfcomm bnep bluetooth pci_stub vboxpci vboxnetadp vboxnetflt vboxdrv binfmt_misc tda1004x saa7134_dvb videobuf_dvb dvb_core saa7134_alsa snd_hda_codec_via snd_usb_audio uvcvideo ppdev snd_usbmidi_lib tda827x tda8290 tuner snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq psmouse serio_raw parport_pc asus_atk0110 snd_timer snd_seq_device ir_lirc_codec lirc_dev i915 ir_sony_decoder ir_jvc_decoder drm_kms_helper snd drm ir_rc6_decoder soundcore ir_rc5_decoder rc_asus_pc39 i2c_algo_bit saa7134 video ir_nec_decoder snd_page_alloc rc_core videobuf_dma_sg videobuf_core v4l2_common videodev v4l2_compat_ioctl32 tveeprom lp parport usbhid hid sata_sil r8169
Jan 25 22:19:04 oneiric kernel: [24986.372804] 
Jan 25 22:19:04 oneiric kernel: [24986.372821] Pid: 1901, comm: pulseaudio Not tainted 3.0.0-15-generic #25-Ubuntu System manufacturer System Product Name/P5G41C-M LX
Jan 25 22:19:04 oneiric kernel: [24986.372919] RIP: 0010:[<ffffffff811695c9>]  [<ffffffff811695c9>] fput+0x9/0x30
Jan 25 22:19:04 oneiric kernel: [24986.372984] RSP: 0018:ffff8800d5d27ad8  EFLAGS: 00010282
Jan 25 22:19:04 oneiric kernel: [24986.373026] RAX: 0000000000000282 RBX: ffff88002d8a5390 RCX: ffff880106231588
Jan 25 22:19:04 oneiric kernel: [24986.373081] RDX: ffff880106231588 RSI: 0000000000000282 RDI: f4c1c198bf2334e4
Jan 25 22:19:04 oneiric kernel: [24986.373135] RBP: ffff8800d5d27ad8 R08: ffff8800d5d74030 R09: 0000000000000001
Jan 25 22:19:04 oneiric kernel: [24986.373189] R10: 0000000000000000 R11: 0000000000000001 R12: ffffffffffffff40
Jan 25 22:19:04 oneiric kernel: [24986.373244] R13: ffff88002d8a5410 R14: ffff88002d8a5450 R15: ffff88002d8a5010
Jan 25 22:19:04 oneiric kernel: [24986.373298] FS:  00007fde51e02720(0000) GS:ffff88011fc80000(0000) knlGS:0000000000000000
Jan 25 22:19:04 oneiric kernel: [24986.373361] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Jan 25 22:19:04 oneiric kernel: [24986.373406] CR2: 00007f12ce539000 CR3: 00000000d4721000 CR4: 00000000000406e0
Jan 25 22:19:04 oneiric kernel: [24986.373460] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jan 25 22:19:04 oneiric kernel: [24986.373514] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jan 25 22:19:04 oneiric kernel: [24986.373570] Process pulseaudio (pid: 1901, threadinfo ffff8800d5d26000, task ffff8800d958c560)
Jan 25 22:19:04 oneiric kernel: [24986.375600] Stack:
Jan 25 22:19:04 oneiric kernel: [24986.375909]  ffff8800d5d27b28 ffffffff8117ab12 ffff8800d5d27cd0 ffff88002d8a5000
Jan 25 22:19:04 oneiric kernel: [24986.375909]  00000000000009ac 0000000000000000 0000000000000001 0000000002508e90
Jan 25 22:19:04 oneiric kernel: [24986.375909]  000000000000001a 00000000000001fe ffff8800d5d27ef8 ffffffff8117bf58
Jan 25 22:19:04 oneiric kernel: [24986.375909] Call Trace:
Jan 25 22:19:04 oneiric kernel: [24986.375909]  [<ffffffff8117ab12>] poll_freewait+0xa2/0xe0
Jan 25 22:19:04 oneiric kernel: [24986.375909]  [<ffffffff8117bf58>] do_sys_poll+0x1e8/0x260
Jan 25 22:19:04 oneiric kernel: [24986.375909]  [<ffffffff8117ab50>] ? poll_freewait+0xe0/0xe0
Jan 25 22:19:04 oneiric kernel: [24986.375909]  [<ffffffff8117ac40>] ? __pollwait+0xf0/0xf0
Jan 25 22:19:04 oneiric kernel: last message repeated 8 times
Jan 25 22:19:04 oneiric kernel: [24986.375909]  [<ffffffff8117c234>] sys_ppoll+0xe4/0x180
Jan 25 22:19:04 oneiric kernel: [24986.375909]  [<ffffffff811684e7>] ? sys_write+0x67/0x90
Jan 25 22:19:04 oneiric kernel: [24986.375909]  [<ffffffff815fa3c2>] system_call_fastpath+0x16/0x1b
Jan 25 22:19:04 oneiric kernel: [24986.375909] Code: 85 c0 0f 84 b7 fe ff ff 31 d2 48 89 de 83 cf ff ff d0 e9 9f fe ff ff 66 66 2e 0f 1f 84 00 00 00 00 00 55 48 89 e5 66 66 66 66 90 <f0> 48 ff 4f 30 0f 94 c0 84 c0 75 0b 5d c3 66 0f 1f 84 00 00 00 
Jan 25 22:19:04 oneiric kernel: [24986.375909] RIP  [<ffffffff811695c9>] fput+0x9/0x30
Jan 25 22:19:04 oneiric kernel: [24986.375909]  RSP <ffff8800d5d27ad8>
Jan 25 22:19:04 oneiric kernel: [24986.459673] ---[ end trace 45526170df0f6337 ]---
```

What does it all mean?

Thanks

---

### Post by dcstar on 2012-01-25
> **hopelessone said:**
> Hi All,

My computer froze and I checked the logs:
..........
What does it all mean?

Thanks

Something in Pulseaudio crashed (probably).

---

