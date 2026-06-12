---
title: "My system keeps completely crashing"
date: 2010-06-22
forum: General Help
---

### Post by horde on 2010-06-22
My system keeps crashing...it freezes and I have to do a hard reset. I don't know why or what to do about it.  It usually happens when I have mencoder encoding video from a capture card.  I just did a clean install of Lucid because Karmic (with stock kernel) did the same thing...to no avail.

Getting the same message in /var/log/kern.log and /var/log/messages:
> Jun 22 12:50:11 golem kernel: [76000.385090] npviewer.bin[5063]: segfault at ee99c054 ip 00000000f6183033 sp 00000000ffe605c0 error 4 in libflashplayer.so[f5de4000+b04000]

It's not always npviewer.bin...in the past it's been mencoder or something else.

I have a brand new Core i5 750 system with 4GB memory and 7200rpm SATA HDD.  

Any help would be greatly appreciated.

---

### Post by sf-it-services on 2010-06-22
the problem seems to be with libflashplayer not npviewer, try updating the flash on the machine.... thats my tuppence worth

(check everything is 64bit versions too)

---

### Post by horde on 2010-06-22
Many thanks for your reply.  I'll give that a go and update the thread.

---

### Post by horde on 2010-06-22
Unfortunately that doesn't seem to have worked (though I did replace flash with the 64-bit version, it wasn't even running at the time of the crash).  This time after it crashed I left it running to see if it would log any more kernel messages...included below.  These look a lot more like the errors I was getting before I reinstalled (and the reason that I reinstalled):

/var/log/kern.log
```
Jun 23 00:00:02 golem kernel: [32482.648360] BUG: unable to handle kernel paging request at ffff8801525353a1
Jun 23 00:00:02 golem kernel: [32482.648364] IP: [<ffffffff8111bf09>] page_check_address+0x19/0x180
Jun 23 00:00:02 golem kernel: [32482.648370] PGD 1002063 PUD 0 
Jun 23 00:00:02 golem kernel: [32482.648373] Oops: 0000 [#1] SMP 
Jun 23 00:00:02 golem kernel: [32482.648375] last sysfs file: /sys/devices/pci0000:00/0000:00:1e.0/0000:04:05.1/local_cpus
Jun 23 00:00:02 golem kernel: [32482.648377] CPU 3 
Jun 23 00:00:02 golem kernel: [32482.648378] Modules linked in: nfs lockd nfs_acl auth_rpcgss sunrpc snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_bt87x snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq ppdev bttv v4l2_common videodev v4l1_compat v4l2_compat_ioctl32 ir_common snd_timer snd_seq_device joydev parport_pc fbcon i2c_algo_bit tileblit videobuf_dma_sg font bitblit softcursor videobuf_core btcx_risc tveeprom snd serio_raw nvidia(P) vga16fb vgastate soundcore snd_page_alloc lp parport usbhid hid usb_storage floppy pata_jmicron r8169 mii ahci
Jun 23 00:00:02 golem kernel: [32482.648407] Pid: 52, comm: kswapd0 Tainted: P           2.6.32-22-generic #36-Ubuntu P55-US3L
Jun 23 00:00:02 golem kernel: [32482.648409] RIP: 0010:[<ffffffff8111bf09>]  [<ffffffff8111bf09>] page_check_address+0x19/0x180
Jun 23 00:00:02 golem kernel: [32482.648412] RSP: 0018:ffff8801196d1a10  EFLAGS: 00010282
Jun 23 00:00:02 golem kernel: [32482.648414] RAX: ffff8800c4c12000 RBX: ffff8800c4c12000 RCX: ffff8801196d1a68
Jun 23 00:00:02 golem kernel: [32482.648415] RDX: 00007fe7cc3e1000 RSI: ffff880152535351 RDI: ffffea0003d40850
Jun 23 00:00:02 golem kernel: [32482.648417] RBP: ffff8801196d1a40 R08: 0000000000000000 R09: 0000000000000040
Jun 23 00:00:02 golem kernel: [32482.648418] R10: ffff8800b6d70308 R11: 0000000000000003 R12: 00007fe7cc3e1000
Jun 23 00:00:02 golem kernel: [32482.648420] R13: ffff8801196d1afc R14: ffff8801196d1c30 R15: ffff880152535351
Jun 23 00:00:02 golem kernel: [32482.648422] FS:  0000000000000000(0000) GS:ffff8800282c0000(0000) knlGS:0000000000000000
Jun 23 00:00:02 golem kernel: [32482.648423] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Jun 23 00:00:02 golem kernel: [32482.648425] CR2: ffff8801525353a1 CR3: 0000000001001000 CR4: 00000000000006e0
Jun 23 00:00:02 golem kernel: [32482.648426] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 23 00:00:02 golem kernel: [32482.648428] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun 23 00:00:02 golem kernel: [32482.648430] Process kswapd0 (pid: 52, threadinfo ffff8801196d0000, task ffff88011a9e5bc0)
Jun 23 00:00:02 golem kernel: [32482.648440] Call Trace:
Jun 23 00:00:02 golem kernel: [32482.648445]  [<ffffffff81044cd0>] ? ptep_clear_flush_young+0x50/0x70
Jun 23 00:00:02 golem kernel: [32482.648448]  [<ffffffff8111c1e0>] page_referenced_one+0x60/0x140
Jun 23 00:00:02 golem kernel: [32482.648452]  [<ffffffff812b4da6>] ? prio_tree_next+0x206/0x240
Jun 23 00:00:02 golem kernel: [32482.648454]  [<ffffffff8111d417>] page_referenced_file+0xb7/0xf0
Jun 23 00:00:02 golem kernel: [32482.648457]  [<ffffffff8111d653>] page_referenced+0x73/0x150
Jun 23 00:00:02 golem kernel: [32482.648460]  [<ffffffff81100b72>] shrink_active_list+0x1f2/0x3a0
Jun 23 00:00:02 golem kernel: [32482.648462]  [<ffffffff8110225c>] shrink_list+0xac/0xf0
Jun 23 00:00:02 golem kernel: [32482.648464]  [<ffffffff81102437>] shrink_zone+0x197/0x240
Jun 23 00:00:02 golem kernel: [32482.648467]  [<ffffffff811034c9>] balance_pgdat+0x659/0x6d0
Jun 23 00:00:02 golem kernel: [32482.648469]  [<ffffffff81100550>] ? isolate_pages_global+0x0/0x50
Jun 23 00:00:02 golem kernel: [32482.648471]  [<ffffffff8110363e>] kswapd+0xfe/0x150
Jun 23 00:00:02 golem kernel: [32482.648474]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
Jun 23 00:00:02 golem kernel: [32482.648476]  [<ffffffff81103540>] ? kswapd+0x0/0x150
Jun 23 00:00:02 golem kernel: [32482.648478]  [<ffffffff81084fa6>] kthread+0x96/0xa0
Jun 23 00:00:02 golem kernel: [32482.648481]  [<ffffffff810141ea>] child_rip+0xa/0x20
Jun 23 00:00:02 golem kernel: [32482.648483]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
Jun 23 00:00:02 golem kernel: [32482.648485]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
Jun 23 00:00:02 golem kernel: [32482.648486] Code: 00 02 20 00 c9 c3 0f 0b eb fe 0f 1f 84 00 00 00 00 00 55 48 89 e5 48 83 ec 30 48 89 5d e8 4c 89 65 f0 4c 89 6d f8 0f 1f 44 00 00 <48> 8b 76 50 48 89 d0 48 89 fb 48 c1 e8 27 25 f
f 01 00 00 48 8b 
Jun 23 00:00:02 golem kernel: [32482.648506] RIP  [<ffffffff8111bf09>] page_check_address+0x19/0x180
Jun 23 00:00:02 golem kernel: [32482.648509]  RSP <ffff8801196d1a10>
Jun 23 00:00:02 golem kernel: [32482.648510] CR2: ffff8801525353a1
Jun 23 00:00:02 golem kernel: [32482.648512] ---[ end trace 5a9c7cd4a95989c8 ]---

```

/var/log/messages
```
Jun 23 00:00:02 golem kernel: [32482.648370] PGD 1002063 PUD 0 
Jun 23 00:00:02 golem kernel: [32482.648377] CPU 3 
Jun 23 00:00:02 golem kernel: [32482.648378] Modules linked in: nfs lockd nfs_acl auth_rpcgss sunrpc snd_hda_codec
_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_bt87x snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_o
ss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq ppdev bttv v4l2_common videodev v4l1_compat v4l2_compat_ioc
tl32 ir_common snd_timer snd_seq_device joydev parport_pc fbcon i2c_algo_bit tileblit videobuf_dma_sg font bitblit
 softcursor videobuf_core btcx_risc tveeprom snd serio_raw nvidia(P) vga16fb vgastate soundcore snd_page_alloc lp 
parport usbhid hid usb_storage floppy pata_jmicron r8169 mii ahci
Jun 23 00:00:02 golem kernel: [32482.648407] Pid: 52, comm: kswapd0 Tainted: P           2.6.32-22-generic #36-Ubu
ntu P55-US3L
Jun 23 00:00:02 golem kernel: [32482.648409] RIP: 0010:[<ffffffff8111bf09>]  [<ffffffff8111bf09>] page_check_addre
ss+0x19/0x180
Jun 23 00:00:02 golem kernel: [32482.648412] RSP: 0018:ffff8801196d1a10  EFLAGS: 00010282
Jun 23 00:00:02 golem kernel: [32482.648414] RAX: ffff8800c4c12000 RBX: ffff8800c4c12000 RCX: ffff8801196d1a68
Jun 23 00:00:02 golem kernel: [32482.648415] RDX: 00007fe7cc3e1000 RSI: ffff880152535351 RDI: ffffea0003d40850
Jun 23 00:00:02 golem kernel: [32482.648417] RBP: ffff8801196d1a40 R08: 0000000000000000 R09: 0000000000000040
Jun 23 00:00:02 golem kernel: [32482.648418] R10: ffff8800b6d70308 R11: 0000000000000003 R12: 00007fe7cc3e1000
Jun 23 00:00:02 golem kernel: [32482.648420] R13: ffff8801196d1afc R14: ffff8801196d1c30 R15: ffff880152535351
Jun 23 00:00:02 golem kernel: [32482.648422] FS:  0000000000000000(0000) GS:ffff8800282c0000(0000) knlGS:000000000
0000000
Jun 23 00:00:02 golem kernel: [32482.648423] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Jun 23 00:00:02 golem kernel: [32482.648425] CR2: ffff8801525353a1 CR3: 0000000001001000 CR4: 00000000000006e0
Jun 23 00:00:02 golem kernel: [32482.648426] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 23 00:00:02 golem kernel: [32482.648428] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun 23 00:00:02 golem kernel: [32482.648430] Process kswapd0 (pid: 52, threadinfo ffff8801196d0000, task ffff88011
a9e5bc0)
Jun 23 00:00:02 golem kernel: [32482.648432]  ffff8801196d1a40 ffffffff81044cd0 ffff8800c4dd8420 ffff8800c4c12000
Jun 23 00:00:02 golem kernel: [32482.648435] <0> 00007fe7cc3e1000 ffff8801196d1afc ffff8801196d1aa0 ffffffff8111c1e0
Jun 23 00:00:02 golem kernel: [32482.648437] <0> ffffffff812b4da6 0000000000000003 0000000000000000 ffffea0002b10788
Jun 23 00:00:02 golem kernel: [32482.648445]  [<ffffffff81044cd0>] ? ptep_clear_flush_young+0x50/0x70
Jun 23 00:00:02 golem kernel: [32482.648448]  [<ffffffff8111c1e0>] page_referenced_one+0x60/0x140
Jun 23 00:00:02 golem kernel: [32482.648452]  [<ffffffff812b4da6>] ? prio_tree_next+0x206/0x240
Jun 23 00:00:02 golem kernel: [32482.648454]  [<ffffffff8111d417>] page_referenced_file+0xb7/0xf0
Jun 23 00:00:02 golem kernel: [32482.648457]  [<ffffffff8111d653>] page_referenced+0x73/0x150
Jun 23 00:00:02 golem kernel: [32482.648460]  [<ffffffff81100b72>] shrink_active_list+0x1f2/0x3a0
Jun 23 00:00:02 golem kernel: [32482.648462]  [<ffffffff8110225c>] shrink_list+0xac/0xf0
Jun 23 00:00:02 golem kernel: [32482.648464]  [<ffffffff81102437>] shrink_zone+0x197/0x240
Jun 23 00:00:02 golem kernel: [32482.648467]  [<ffffffff811034c9>] balance_pgdat+0x659/0x6d0
Jun 23 00:00:02 golem kernel: [32482.648469]  [<ffffffff81100550>] ? isolate_pages_global+0x0/0x50
Jun 23 00:00:02 golem kernel: [32482.648471]  [<ffffffff8110363e>] kswapd+0xfe/0x150
Jun 23 00:00:02 golem kernel: [32482.648474]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
Jun 23 00:00:02 golem kernel: [32482.648476]  [<ffffffff81103540>] ? kswapd+0x0/0x150
Jun 23 00:00:02 golem kernel: [32482.648478]  [<ffffffff81084fa6>] kthread+0x96/0xa0
Jun 23 00:00:02 golem kernel: [32482.648481]  [<ffffffff810141ea>] child_rip+0xa/0x20
Jun 23 00:00:02 golem kernel: [32482.648483]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
Jun 23 00:00:02 golem kernel: [32482.648485]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
Jun 23 00:00:02 golem kernel: [32482.648509]  RSP <ffff8801196d1a10>
Jun 23 00:00:02 golem kernel: [32482.648512] ---[ end trace 5a9c7cd4a95989c8 ]---

```

I have no idea what any of this means or what the problem is.  Any ideas?

Edit: Not sure this is applicable, but I can ping the crashed machine from another one, but that's the only thing it responds to as far as I can tell.

---

### Post by horde on 2010-06-30
Sorry for asking again, but can anyone help me with this?

---

### Post by mcbarron on 2010-07-19
> **horde said:**
> Edit: Not sure this is applicable, but I can ping the crashed machine from another one, but that's the only thing it responds to as far as I can tell.

So you can't ssh into it?  Have you tried nmap to see if other ports are open?

---

### Post by horde on 2010-07-29
many thanks for your response.  Not a bad thought...when I get a chance I'll reproduce the error and see what nmap gives me.

Cheers.

---

### Post by horde on 2010-10-23
Finally found this solution: [http://ubuntuforums.org/showthread.php?t=1363283](http://ubuntuforums.org/showthread.php?t=1363283) 

That seems to have solved it.

---

