---
title: "teamspeak locking up"
date: 2009-08-08
forum: General Help
---

### Post by trav5 on 2009-08-08
Hi all, teamspeak is locking up a few minutes after connecting to the server. Here is the output of dmesg after boot:```
[ 1859.149105] BUG: unable to handle kernel paging request at ff000000
[ 1859.149117] IP: [<c042bb49>] skb_free_datagram+0x19/0x30
[ 1859.149131] *pde = 00000000 
[ 1859.149136] Oops: 0000 [#1] SMP 
[ 1859.149142] last sysfs file: /sys/devices/pci0000:00/0000:00:02.5/host2/target2:0:0/2:0:0:0/block/sda/sda1/stat
[ 1859.149148] Dumping ftrace buffer:
[ 1859.149153]    (ftrace buffer empty)
[ 1859.149156] Modules linked in: binfmt_misc bridge stp bnep video output input_polldev lp arc4 ecb snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss rt73usb crc_itu_t snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq rt2500usb snd_timer snd_seq_device rt2x00usb rt2x00lib led_class snd sis_agp mac80211 soundcore ppdev agpgart shpchp pcspkr snd_page_alloc parport_pc cfg80211 parport usbhid ohci1394 ieee1394 sis900 mii floppy fbcon tileblit font bitblit softcursor
[ 1859.149214] 
[ 1859.149218] Pid: 4113, comm: teamspeak.real Not tainted (2.6.28-14-generic #47-Ubuntu)  
[ 1859.149222] EIP: 0060:[<c042bb49>] EFLAGS: 00010246 CPU: 1
[ 1859.149226] EIP is at skb_free_datagram+0x19/0x30
[ 1859.149229] EAX: c06c40e0 EBX: f5fec280 ECX: f5ff9d00 EDX: f5ff9300
[ 1859.149232] ESI: f5fec280 EDI: f4d05ec4 EBP: f4d05d58 ESP: f4d05d54
[ 1859.149235]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[ 1859.149239] Process teamspeak.real (pid: 4113, ti=f4d04000 task=f4d13ed0 task.ti=f4d04000)
[ 1859.149242] Stack:
[ 1859.149244]  f5ff9d00 f4d05d9c c0475f48 00000000 0000014b f4d05d8c f4d05d88 f4d05f34
[ 1859.149254]  f4d05eb4 00000000 00000000 00000000 0000014b 0000014b 00000000 00000000
[ 1859.149264]  c06c40e0 f4d05f34 f4d05dc4 c0424a73 00000244 00000000 00004000 f4d05db4
[ 1859.149275] Call Trace:
[ 1859.149278]  [<c0475f48>] ? udp_recvmsg+0x198/0x2e0
[ 1859.149287]  [<c0424a73>] ? sock_common_recvmsg+0x43/0x60
[ 1859.149294]  [<c04240b4>] ? sock_recvmsg+0xf4/0x120
[ 1859.149300]  [<c014ece0>] ? autoremove_wake_function+0x0/0x50
[ 1859.149311]  [<c02cdcd5>] ? copy_from_user+0x35/0x130
[ 1859.149318]  [<c01cb814>] ? set_fd_set+0x34/0x50
[ 1859.149325]  [<c01cc5d4>] ? core_sys_select+0x1a4/0x270
[ 1859.149330]  [<c042438a>] ? sys_recvfrom+0x7a/0xd0
[ 1859.149335]  [<c01bd661>] ? do_sync_write+0xd1/0x110
[ 1859.149340]  [<c03cc13d>] ? scan_async+0x7d/0x190
[ 1859.149349]  [<c014ece0>] ? autoremove_wake_function+0x0/0x50
[ 1859.149356]  [<c01569b3>] ? getnstimeofday+0x53/0x110
[ 1859.149362]  [<c0424587>] ? sys_socketcall+0x167/0x2b0
[ 1859.149367]  [<c0103f6b>] ? sysenter_do_call+0x12/0x2f
[ 1859.149375] Code: 89 10 89 42 04 f0 ff 8e b4 00 00 00 31 ff eb c9 66 90 55 89 e5 53 89 c3 89 d0 e8 d3 ca ff ff 8b 43 20 83 40 50 85 c0 74 13 81 bb <a0> 00 00 00 ff 0f 00 00 7e 07 89 d8 e8 76 8d ff ff 5b 5d c3 8d 
[ 1859.149433] EIP: [<c042bb49>] skb_free_datagram+0x19/0x30 SS:ESP 0068:f4d05d54
[ 1859.149442] ---[ end trace dae553a38afd142a ]---
[ 1859.156379] BUG: unable to handle kernel paging request at b7a96779
[ 1859.156391] IP: [<c042bb44>] skb_free_datagram+0x14/0x30
[ 1859.156402] *pde = 00000000 
[ 1859.156409] Oops: 0002 [#2] SMP 
[ 1859.156415] last sysfs file: /sys/devices/pci0000:00/0000:00:02.5/host2/target2:0:0/2:0:0:0/block/sda/sda1/stat
[ 1859.156422] Modules linked in: binfmt_misc bridge stp bnep video output input_polldev lp arc4 ecb snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss rt73usb crc_itu_t snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq rt2500usb snd_timer snd_seq_device rt2x00usb rt2x00lib led_class snd sis_agp mac80211 soundcore ppdev agpgart shpchp pcspkr snd_page_alloc parport_pc cfg80211 parport usbhid ohci1394 ieee1394 sis900 mii floppy fbcon tileblit font bitblit softcursor
[ 1859.156569] 
[ 1859.156575] Pid: 2263, comm: syslogd Tainted: G      D    (2.6.28-14-generic #47-Ubuntu)  
[ 1859.156581] EIP: 0060:[<c042bb44>] EFLAGS: 00010282 CPU: 0
[ 1859.156587] EIP is at skb_free_datagram+0x14/0x30
[ 1859.156592] EAX: c06c6320 EBX: f63fe200 ECX: c16bf7b8 EDX: c16985f8
[ 1859.156598] ESI: f677bf14 EDI: 00000062 EBP: f677bd50 ESP: f677bd4c
[ 1859.156603]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[ 1859.156610] Process syslogd (pid: 2263, ti=f677a000 task=f603f110 task.ti=f677a000)
[ 1859.156614] Stack:
[ 1859.156618]  f677bd74 f677bda4 c049bb31 00000000 00000175 f6871680 f63fe384 f63fe200
[ 1859.156633]  f5fbdb00 f677be3c 000008f0 00000066 00000067 00000000 f5c43e9c 00000000
[ 1859.156669]  f677bd94 c02a8bb0 00000062 c053e100 000003fe f6871680 f677be88 c04240b4
[ 1859.156692] Call Trace:
[ 1859.156697]  [<c049bb31>] ? unix_dgram_recvmsg+0x191/0x2e0
[ 1859.156708]  [<c02a8bb0>] ? apparmor_socket_recvmsg+0x10/0x20
[ 1859.156726]  [<c04240b4>] ? sock_recvmsg+0xf4/0x120
[ 1859.156736]  [<c012f9eb>] ? finish_task_switch+0x2b/0xe0
[ 1859.156749]  [<c014ece0>] ? autoremove_wake_function+0x0/0x50
[ 1859.156758]  [<c04fedcb>] ? mutex_lock+0xb/0x20
[ 1859.156770]  [<c01c48cf>] ? pipe_write+0x25f/0x540
[ 1859.156786]  [<c01cb814>] ? set_fd_set+0x34/0x50
[ 1859.156801]  [<c042438a>] ? sys_recvfrom+0x7a/0xd0
[ 1859.156810]  [<c01569b3>] ? getnstimeofday+0x53/0x110
[ 1859.156820]  [<c0151eb5>] ? enqueue_hrtimer+0x75/0xf0
[ 1859.156829]  [<c0152ea9>] ? hrtimer_start_range_ns+0xe9/0x1e0
[ 1859.156839]  [<c0424416>] ? sys_recv+0x36/0x40
[ 1859.156849]  [<c04245d7>] ? sys_socketcall+0x1b7/0x2b0
[ 1859.156859]  [<c0103f6b>] ? sysenter_do_call+0x12/0x2f
[ 1859.156869] Code: 04 00 00 00 00 89 10 89 42 04 f0 ff 8e b4 00 00 00 31 ff eb c9 66 90 55 89 e5 53 89 c3 89 d0 e8 d3 ca ff ff 8b 43 20 83 40 50 85 <c0> 74 13 81 bb a0 00 00 00 ff 0f 00 00 7e 07 89 d8 e8 76 8d ff 
[ 1859.157001] EIP: [<c042bb44>] skb_free_datagram+0x14/0x30 SS:ESP 0068:f677bd4c
[ 1859.157012] ---[ end trace dae553a38afd142a ]---
[ 6050.764883] pulseaudio[3024]: segfault at 448c10ab ip 095f2ac5 sp b2d99124 error 4

```

---

