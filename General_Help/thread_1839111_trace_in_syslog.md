---
title: "trace in syslog"
date: 2011-09-05
forum: General Help
---

### Post by quequotion on 2011-09-05
What does this mean?


[code]Sep  5 12:10:34 Shiroko kernel: [72127.450023] ------------[ cut here ]------------
Sep  5 12:10:34 Shiroko kernel: [72127.450043] WARNING: at /build/buildd/linux-2.6.38/net/ipv4/tcp_input.c:4294 tcp_data_queue+0x944/0x9e0()
Sep  5 12:10:34 Shiroko kernel: [72127.450050] Hardware name: TA890FXE
Sep  5 12:10:34 Shiroko kernel: [72127.450055] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat snd_seq_dummy nls_utf8 isofs cryptd aes_x86_64 aes_generic parport_pc ppdev dm_crypt vesafb binfmt_misc rfcomm snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul tuner_simple tuner_types vp27smpx wm8739 upd64083 upd64031a tea5767 tda9887 tda8290 tuner sco bnep l2cap nvidia(P) snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_util_mem snd_hwdep snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq ipheth edac_core snd_timer snd_seq_device snd saa7115 btusb ivtv cx2341x i2c_algo_bit v4l2_common bluetooth videodev v4l2_compat_ioctl32 emu10k1_gp joydev gameport psmouse tveeprom k10temp edac_mce_amd soundcore serio_raw sp5100_tco i2c_piix4 vhba lp parport dm_raid45 xor usb_storage usbhid firewire_ohci uas hid firewire_core r8169 pata_via crc_itu_t ahci e1000e libahci
Sep  5 12:10:34 Shiroko kernel: [72127.450199] Pid: 14521, comm: firefox-bin Tainted: P      D W   2.6.38-11-generic #49-Ubuntu
Sep  5 12:10:34 Shiroko kernel: [72127.450205] Call Trace:
Sep  5 12:10:34 Shiroko kernel: [72127.450210]  <IRQ>  [<ffffffff81065cbf>] ? warn_slowpath_common+0x7f/0xc0
Sep  5 12:10:34 Shiroko kernel: [72127.450229]  [<ffffffff81065d1a>] ? warn_slowpath_null+0x1a/0x20
Sep  5 12:10:34 Shiroko kernel: [72127.450237]  [<ffffffff8151c2b4>] ? tcp_data_queue+0x944/0x9e0
Sep  5 12:10:34 Shiroko kernel: [72127.450245]  [<ffffffff8151f64a>] ? tcp_rcv_established+0x3ba/0x720
Sep  5 12:10:34 Shiroko kernel: [72127.450255]  [<ffffffff81453730>] ? ehci_urb_enqueue+0x90/0x120
Sep  5 12:10:34 Shiroko kernel: [72127.450264]  [<ffffffff815272f1>] ? tcp_v4_do_rcv+0xb1/0x1c0
Sep  5 12:10:34 Shiroko kernel: [72127.450272]  [<ffffffff815297b6>] ? tcp_v4_rcv+0x646/0x900
Sep  5 12:10:34 Shiroko kernel: [72127.450282]  [<ffffffff81154ce2>] ? get_partial_node+0x92/0xb0
Sep  5 12:10:34 Shiroko kernel: [72127.450290]  [<ffffffff815057fd>] ? ip_local_deliver_finish+0xdd/0x280
Sep  5 12:10:34 Shiroko kernel: [72127.450298]  [<ffffffff81505b68>] ? ip_local_deliver+0x88/0x90
Sep  5 12:10:34 Shiroko kernel: [72127.450306]  [<ffffffff815054a5>] ? ip_rcv_finish+0x145/0x3c0
Sep  5 12:10:34 Shiroko kernel: [72127.450314]  [<ffffffff81505dac>] ? ip_rcv+0x23c/0x300
Sep  5 12:10:34 Shiroko kernel: [72127.450322]  [<ffffffff8159746a>] ? packet_rcv_spkt+0x4a/0x1a0
Sep  5 12:10:34 Shiroko kernel: [72127.450332]  [<ffffffff814d0f13>] ? __netif_receive_skb+0x3e3/0x580
Sep  5 12:10:34 Shiroko kernel: [72127.450342]  [<ffffffff81076964>] ? mod_timer+0x144/0x2b0
Sep  5 12:10:34 Shiroko kernel: [72127.450350]  [<ffffffff814d150b>] ? process_backlog+0xab/0x1a0
Sep  5 12:10:34 Shiroko kernel: [72127.450357]  [<ffffffff81450d98>] ? ehci_work+0x68/0x80
Sep  5 12:10:34 Shiroko kernel: [72127.450365]  [<ffffffff814d2478>] ? net_rx_action+0x128/0x270
Sep  5 12:10:34 Shiroko kernel: [72127.450373]  [<ffffffff8106d508>] ? __do_softirq+0xa8/0x1c0
Sep  5 12:10:34 Shiroko kernel: [72127.450382]  [<ffffffff81030608>] ? ack_apic_level+0x78/0x1a0
Sep  5 12:10:34 Shiroko kernel: [72127.450390]  [<ffffffff8100cf1c>] ? call_softirq+0x1c/0x30
Sep  5 12:10:34 Shiroko kernel: [72127.450398]  [<ffffffff8100ea45>] ? do_softirq+0x65/0xa0
Sep  5 12:10:34 Shiroko kernel: [72127.450405]  [<ffffffff8106d725>] ? irq_exit+0x85/0x90
Sep  5 12:10:34 Shiroko kernel: [72127.450414]  [<ffffffff815cb8c6>] ? do_IRQ+0x66/0xe0
Sep  5 12:10:34 Shiroko kernel: [72127.450421]  [<ffffffff815c3c13>] ? ret_from_intr+0x0/0x15
Sep  5 12:10:34 Shiroko kernel: [72127.450426]  <EOI>  [<ffffffff8100c002>] ? system_call_fastpath+0x16/0x1b
Sep  5 12:10:34 Shiroko kernel: [72127.450438] ---[ end trace 1ce93e10de483d85 ]---[code]

Not long after this, my syslog comes to an abrupt end. Everything was frozen, to the point of needing to literally pull the plug.

---

### Post by quequotion on 2011-09-23
No takers?

I really have no idea what that dump is about and I could use some help translating it into English.

Also, I'm not sure if this is related or not, but my computer is freezing somewhat frequently.

There's no particular pattern, but it freezes most frequently while watching videos in Totem on the Unity-Compiz desktop. Occasionally it freezes while using firefox and having a lot of tabs open. Other times it freezes while doing absolutely nothing (no windows open, just the desktop displayed, suddenly the mouse stops moving, everything stops)

I re-enabled the keys to restart X:

[Ctrl]+[Alt]+[Backspace]

But there's no response.


I tried the magic keys:

[Alt]+[SysRq]+R,E,I,S,U,B

But they do not work. (Just to be sure, I tried them while the computer was operating normally and they did work, so this freeze is kernel-deep)

The only way out is to pull the plug.

---

