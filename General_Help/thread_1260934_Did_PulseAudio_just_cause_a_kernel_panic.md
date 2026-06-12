---
title: "Did PulseAudio just cause a kernel panic?"
date: 2009-09-08
forum: General Help
---

### Post by spongypants23 on 2009-09-08
```
Sep  8 11:31:35 M1530 kernel: [64847.270571] BUG: unable to handle kernel NULL pointer dereference at 00000000000000a8
Sep  8 11:31:35 M1530 kernel: [64847.270577] IP: [<ffffffffa0a0cb57>] snd_pcm_playback_poll+0x17/0xf0 [snd_pcm]
Sep  8 11:31:35 M1530 kernel: [64847.270590] PGD 10fd3b067 PUD 10f08a067 PMD 0 
Sep  8 11:31:35 M1530 kernel: [64847.270593] Oops: 0000 [#1] SMP 
Sep  8 11:31:35 M1530 kernel: [64847.270595] last sysfs file: /sys/devices/virtual/hwmon/hwmon0/temp1_input
Sep  8 11:31:35 M1530 kernel: [64847.270598] Dumping ftrace buffer:
Sep  8 11:31:35 M1530 kernel: [64847.270601]    (ftrace buffer empty)
Sep  8 11:31:35 M1530 kernel: [64847.270602] CPU 1 
Sep  8 11:31:35 M1530 kernel: [64847.270603] Modules linked in: iwlagn aes_x86_64 aes_generic binfmt_misc ppdev bridge stp bnep vboxnetadp vboxnetflt vboxdrv input_polldev ipt_REJECT ipt_LOG xt_limit xt_tcpudp xt_state ipt_addrtype ip6table_filter ip6_tables nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables lp joydev parport snd_hda_intel snd_pcm_oss snd_mixer_oss arc4 ecb snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi iwlcore snd_seq_midi_event snd_seq snd_timer snd_seq_device uvcvideo led_class snd video psmouse compat_ioctl32 mac80211 soundcore videodev dcdbas sdhci_pci sdhci output pcspkr serio_raw intel_agp btusb iTCO_wdt iTCO_vendor_support snd_page_alloc usbhid v4l1_compat cfg80211 nvidia(P) ohci1394 ieee1394 sky2 fbcon tileblit font bitblit softcursor [last unloaded: iwlagn]
Sep  8 11:31:35 M1530 kernel: [64847.270646] Pid: 4262, comm: pulseaudio Tainted: P           2.6.28-15-generic #49-Ubuntu
Sep  8 11:31:35 M1530 kernel: [64847.270647] RIP: 0010:[<ffffffffa0a0cb57>]  [<ffffffffa0a0cb57>] snd_pcm_playback_poll+0x17/0xf0 [snd_pcm]
Sep  8 11:31:35 M1530 kernel: [64847.270654] RSP: 0018:ffff88010f1f9aa8  EFLAGS: 00010246
Sep  8 11:31:35 M1530 kernel: [64847.270656] RAX: ffff88011d0218c0 RBX: 0000000000000000 RCX: 0000000000000000
Sep  8 11:31:35 M1530 kernel: [64847.270657] RDX: 0000000000000006 RSI: 0000000000000000 RDI: ffff8800cf95a480
Sep  8 11:31:35 M1530 kernel: [64847.270659] RBP: ffff88010f1f9ab8 R08: 0000000000000005 R09: ffff8800cf95a4a8
Sep  8 11:31:35 M1530 kernel: [64847.270660] R10: 0000000000000000 R11: 0000000000000000 R12: 0000000000000000
Sep  8 11:31:35 M1530 kernel: [64847.270662] R13: ffff8800cf95a480 R14: 0000000000000000 R15: ffff88010f1f9ddc
Sep  8 11:31:35 M1530 kernel: [64847.270664] FS:  00007f69a7050950(0000) GS:ffff88011f803a80(0000) knlGS:0000000000000000
Sep  8 11:31:35 M1530 kernel: [64847.270666] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Sep  8 11:31:35 M1530 kernel: [64847.270667] CR2: 00000000000000a8 CR3: 000000010fd39000 CR4: 00000000000006a0
Sep  8 11:31:35 M1530 kernel: [64847.270669] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Sep  8 11:31:35 M1530 kernel: [64847.270670] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Sep  8 11:31:35 M1530 kernel: [64847.270672] Process pulseaudio (pid: 4262, threadinfo ffff88010f1f8000, task ffff88011d115980)
Sep  8 11:31:35 M1530 kernel: [64847.270674] Stack:
Sep  8 11:31:35 M1530 kernel: [64847.270675]  0000000000000000 ffff88010f1f9dd4 ffff88010f1f9b48 ffffffff802f7819
Sep  8 11:31:35 M1530 kernel: [64847.270678]  0000000000000000 ffff88010f1f9b68 ffff88010f1f9db8 0000000000000000
Sep  8 11:31:35 M1530 kernel: [64847.270681]  0000000000000000 000000000f1f9bf8 0000000000000000 ffff88010f1f9db8
Sep  8 11:31:35 M1530 kernel: [64847.270684] Call Trace:
Sep  8 11:31:35 M1530 kernel: [64847.270686]  [<ffffffff802f7819>] do_poll+0xe9/0x280
Sep  8 11:31:35 M1530 kernel: [64847.270691]  [<ffffffff802f7ce4>] do_sys_poll+0x134/0x200
Sep  8 11:31:35 M1530 kernel: [64847.270694]  [<ffffffff802f8740>] ? __pollwait+0x0/0x120
Sep  8 11:31:35 M1530 kernel: [64847.270697]  [<ffffffff8024a6f0>] ? default_wake_function+0x0/0x10
Sep  8 11:31:35 M1530 kernel: [64847.270700]  [<ffffffff8024a6f0>] ? default_wake_function+0x0/0x10
Sep  8 11:31:35 M1530 kernel: [64847.270702]  [<ffffffff8024a6f0>] ? default_wake_function+0x0/0x10
Sep  8 11:31:35 M1530 kernel: [64847.270705]  [<ffffffff8041cb21>] ? __rb_erase_color+0x101/0x1d0
Sep  8 11:31:35 M1530 kernel: [64847.270709]  [<ffffffff8023e0ef>] ? wake_affine+0xaf/0x240
Sep  8 11:31:35 M1530 kernel: [64847.270712]  [<ffffffff8041c9e9>] ? rb_insert_color+0x109/0x140
Sep  8 11:31:35 M1530 kernel: [64847.270714]  [<ffffffff80270bb9>] ? getnstimeofday+0x59/0xe0
Sep  8 11:31:35 M1530 kernel: [64847.270718]  [<ffffffff80270bb9>] ? getnstimeofday+0x59/0xe0
Sep  8 11:31:35 M1530 kernel: [64847.270721]  [<ffffffffa0a44172>] ? azx_pcm_pointer+0x22/0x50 [snd_hda_intel]
Sep  8 11:31:35 M1530 kernel: [64847.270739]  [<ffffffffa0a11f4b>] ? snd_pcm_update_hw_ptr+0x4b/0x270 [snd_pcm]
Sep  8 11:31:35 M1530 kernel: [64847.270747]  [<ffffffffa0a0cdd4>] ? snd_pcm_status+0x1a4/0x250 [snd_pcm]
Sep  8 11:31:35 M1530 kernel: [64847.270753]  [<ffffffffa0a0e337>] ? snd_pcm_common_ioctl1+0x187/0x770 [snd_pcm]
Sep  8 11:31:35 M1530 kernel: [64847.270759]  [<ffffffffa0a0ebfd>] ? snd_pcm_playback_ioctl1+0x4d/0x250 [snd_pcm]
Sep  8 11:31:35 M1530 kernel: [64847.270765]  [<ffffffff8023ec6a>] ? __wake_up_common+0x5a/0x90
Sep  8 11:31:35 M1530 kernel: [64847.270768]  [<ffffffff8069b741>] ? _spin_lock_irq+0x11/0x20
Sep  8 11:31:35 M1530 kernel: [64847.270773]  [<ffffffff802f7df9>] sys_ppoll+0x49/0x180
Sep  8 11:31:35 M1530 kernel: [64847.270775]  [<ffffffff802f6bd0>] ? sys_ioctl+0x80/0xa0
Sep  8 11:31:35 M1530 kernel: [64847.270778]  [<ffffffff802e8608>] ? sys_read+0x88/0x90
Sep  8 11:31:35 M1530 kernel: [64847.270782]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Sep  8 11:31:35 M1530 kernel: [64847.270785] Code: 48 89 df e8 0c fa ff ff 41 89 c4 90 e9 65 ff ff ff 0f 1f 00 55 48 89 f1 48 85 c9 48 89 e5 41 54 53 48 8b 87 98 00 00 00 4c 8b 20 <49> 8b 9c 24 a8 00 00 00 48 8d b3 f0 00 00 00 74 0a 48 85 f6 74 
Sep  8 11:31:35 M1530 kernel: [64847.270809] RIP  [<ffffffffa0a0cb57>] snd_pcm_playback_poll+0x17/0xf0 [snd_pcm]
Sep  8 11:31:35 M1530 kernel: [64847.270816]  RSP <ffff88010f1f9aa8>
Sep  8 11:31:35 M1530 kernel: [64847.270817] CR2: 00000000000000a8
Sep  8 11:31:35 M1530 kernel: [64847.270819] ---[ end trace ae74cf9b6771990b ]---
```

I can't tell. Anyone here who can decipher this stuff and tell me what went wrong? I was playing World of Warcraft when the sound went bonkers (like a skipping CD) and all of a sudden Scroll and Caps Lock LEDs start flashing.

Should I file this as a bug?

---

