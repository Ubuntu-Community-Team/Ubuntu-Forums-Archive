---
title: "System hang with 10.04 x86_64"
date: 2010-05-29
forum: General Help
---

### Post by imageel on 2010-05-29
First post.. Great forums btw - very useful and friendly community.

I have installed 10.04 LTS and have a problem whilst scanning channels on my Hauppauge DVB HVR 2200 tuner.(installed mythtv +steven toth's drivers to mathc tuner). 
Mythtv-setup finds the tuners but starting a scan hangs with event/0 consuming all one core, system won't shutdown, I have to perform a hard reset to fix.

uname -a ->Linux proxy 2.6.32-21-server #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010 x86_64 GNU/Linux

dmesg shows -

May 29 08:20:03 proxy kernel: [204367.430000] Modules linked in: saa7164 usb_storage tda18271 tda10048 ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT xt_tcpudp iptable_filter ip_tables x_tables bridge stp iscsi_trgt crc32c kvm_intel kvm snd_hda_codec_analog fbcon tileblit font bitblit softcursor vga16fb vgastate nouveau snd_hda_intel ttm drm_kms_helper snd_hda_codec snd_hwdep drm i2c_algo_bit dvb_core tveeprom lp psmouse snd_pcm snd_timer snd soundcore asus_atk0110 serio_raw i2c_nforce2 shpchp snd_page_alloc parport floppy 3w_9xxx pata_marvell e1000e sata_nv pata_amd forcedeth ahci [last unloaded: saa7164]
May 29 08:20:03 proxy kernel: [204367.430000] CPU 0:
May 29 08:20:03 proxy kernel: [204367.430000] Modules linked in: saa7164 usb_storage tda18271 tda10048 ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT xt_tcpudp iptable_filter ip_tables x_tables bridge stp iscsi_trgt crc32c kvm_intel kvm snd_hda_codec_analog fbcon tileblit font bitblit softcursor vga16fb vgastate nouveau snd_hda_intel ttm drm_kms_helper snd_hda_codec snd_hwdep drm i2c_algo_bit dvb_core tveeprom lp psmouse snd_pcm snd_timer snd soundcore asus_atk0110 serio_raw i2c_nforce2 shpchp snd_page_alloc parport floppy 3w_9xxx pata_marvell e1000e sata_nv pata_amd forcedeth ahci [last unloaded: saa7164]
May 29 08:20:03 proxy kernel: [204367.430000] Pid: 9, comm: events/0 Not tainted 2.6.32-21-server #32-Ubuntu P5N-T DELUXE
May 29 08:20:03 proxy kernel: [204367.430000] RIP: 0010:[<ffffffffa02de78e>]  [<ffffffffa02de78e>] saa7164_bus_verify+0x1e/0xa0 [saa7164]
May 29 08:20:03 proxy kernel: [204367.430000] RSP: 0018:ffff88007d003b00  EFLAGS: 00000282
May 29 08:20:03 proxy kernel: [204367.430000] RAX: 0000000000000873 RBX: ffff88007d003b00 RCX: 0000000000000866
May 29 08:20:03 proxy kernel: [204367.430000] RDX: 0000000000000000 RSI: ffff88007d003ba0 RDI: ffff88006fa58000
May 29 08:20:03 proxy kernel: [204367.430000] RBP: ffffffff81013cae R08: 0000000000000000 R09: 0000000000000001
May 29 08:20:03 proxy kernel: [204367.430000] R10: 0000000000001000 R11: 0000000000000000 R12: ffff88007d003b00
May 29 08:20:03 proxy kernel: [204367.430000] R13: ffffffff81013cae R14: ffff88007d003ac0 R15: ffff88007b4c5bc0
May 29 08:20:03 proxy kernel: [204367.430000] FS:  0000000000000000(0000) GS:ffff880001c00000(0000) knlGS:0000000000000000
May 29 08:20:03 proxy kernel: [204367.430000] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
May 29 08:20:03 proxy kernel: [204367.430000] CR2: 00007fa120ded8a2 CR3: 0000000070f57000 CR4: 00000000000026f0
May 29 08:20:03 proxy kernel: [204367.430000] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 29 08:20:03 proxy kernel: [204367.430000] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 29 08:20:03 proxy kernel: [204367.430000] Call Trace:
May 29 08:20:03 proxy kernel: [204367.430000]  [<ffffffffa02de984>] ? saa7164_bus_get+0x174/0x510 [saa7164]
May 29 08:20:03 proxy kernel: [204367.430000]  [<ffffffffa02df6a2>] ? saa7164_irq_dequeue+0x102/0x210 [saa7164]
May 29 08:20:03 proxy kernel: [204367.430000]  [<ffffffff8105e528>] ? load_balance_newidle+0xa8/0x310
May 29 08:20:03 proxy kernel: [204367.430000]  [<ffffffff810116b0>] ? __switch_to+0xd0/0x320
May 29 08:20:03 proxy kernel: [204367.430000]  [<ffffffff81058660>] ? finish_task_switch+0x50/0xe0
May 29 08:20:03 proxy kernel: [204367.430000]  [<ffffffff81013b0e>] ? common_interrupt+0xe/0x13
May 29 08:20:03 proxy kernel: [204367.430000]  [<ffffffffa02db950>] ? saa7164_work_cmdhandler+0x0/0x20 [saa7164]
May 29 08:20:03 proxy kernel: [204367.430000]  [<ffffffffa02db965>] ? saa7164_work_cmdhandler+0x15/0x20 [saa7164]
May 29 08:20:03 proxy kernel: [204367.430000]  [<ffffffff81080427>] ? run_workqueue+0xc7/0x1a0
May 29 08:20:03 proxy kernel: [204367.430000]  [<ffffffff810805a3>] ? worker_thread+0xa3/0x110
May 29 08:20:03 proxy kernel: [204367.430000]  [<ffffffff81084fa0>] ? autoremove_wake_function+0x0/0x40
May 29 08:20:03 proxy kernel: [204367.430000]  [<ffffffff81080500>] ? worker_thread+0x0/0x110
May 29 08:20:03 proxy kernel: [204367.430000]  [<ffffffff81084c26>] ? kthread+0x96/0xa0
May 29 08:20:03 proxy kernel: [204367.430000]  [<ffffffff810141ea>] ? child_rip+0xa/0x20
May 29 08:20:03 proxy kernel: [204367.430000]  [<ffffffff81084b90>] ? kthread+0x0/0xa0
May 29 08:20:03 proxy kernel: [204367.430000]  [<ffffffff810141e0>] ? child_rip+0x0/0x20

Any advice as to how to resolve?

Thanks
Ed

---

