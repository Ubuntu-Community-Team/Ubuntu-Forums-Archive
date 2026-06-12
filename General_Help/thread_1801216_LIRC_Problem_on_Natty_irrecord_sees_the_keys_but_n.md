---
title: "LIRC Problem on Natty: irrecord sees the keys but not irw"
date: 2011-07-10
forum: General Help
---

### Post by CharlesT423 on 2011-07-10
I'm having a problem getting LIRC running on natty.  I tried the base 0.8.7 and also 0.9.0 from Oneric, but they both do the same thing:

I can read my remote fine with irrecord, but when I start lircd and run irw or mplayer, they don't detect the remote buttons being pressed.  I even ran strace on the lircd process and it does see the events (triggers a bunch of SELECT and READ calls when I press a button) but it doesn't pass them on to the listeners.

I'm running an eHome USB receiver that uses the mceusb driver, and I've confirmed that the device works on a Gentoo box running lirc 0.8.7.  Both systems are AMD64.

I've also noticed that if I try to unload the mceusb driver (either with rmmod or by simply unplugging the USB device) the driver crashes:

```

[ 9061.681953] usbcore: deregistering interface driver mceusb
[ 9061.685267] BUG: unable to handle kernel NULL pointer dereference at 0000000000000050
[ 9061.685270] IP: [<ffffffffa01036e7>] show_protocols+0xf7/0x130 [rc_core]
[ 9061.685275] PGD 6acc0067 PUD 8d6ca067 PMD 0
[ 9061.685277] Oops: 0000 [#1] SMP
[ 9061.685279] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/usb3/3-3/3-3:1.0/rc/rc0/protocols
[ 9061.685281] CPU 2
[ 9061.685281] Modules linked in: nfs lockd fscache nfs_acl auth_rpcgss sunrpc binfmt_misc vesafb snd_hda_codec_hdmi ir_lirc_codec lirc_dev ir_sony_decoder mceusb(-) ir_jvc_decoder ir_rc6_decoder ir_rc5_decoder joydev ir_nec_decoder usb_storage uas video eeepc_wmi lp ppdev usbhid hid rc_core nvidia(P) snd_hda_codec_realtek snd_seq_midi snd_rawmidi snd_seq_midi_event snd_hda_intel snd_hda_codec snd_seq snd_hwdep psmouse parport_pc serio_raw snd_pcm snd_seq_device snd_timer snd soundcore snd_page_alloc parport sparse_keymap pata_via r8169 xhci_hcd [last unloaded: rc_rc6_mce]
[ 9061.685300]
[ 9061.685302] Pid: 30229, comm: cat Tainted: P            2.6.38-8-generic #42-Ubuntu System manufacturer System Product Name/P8H67-M PRO
[ 9061.685305] RIP: 0010:[<ffffffffa01036e7>]  [<ffffffffa01036e7>] show_protocols+0xf7/0x130 [rc_core]
[ 9061.685308] RSP: 0018:ffff88006ac69e38  EFLAGS: 00010202
[ 9061.685309] RAX: 0000000000000000 RBX: ffffffffa0107160 RCX: ffffffffa01035f0
[ 9061.685310] RDX: ffff880036e44000 RSI: ffffffffa0107160 RDI: ffff880136466400
[ 9061.685311] RBP: ffff88006ac69e68 R08: ffffffff816507c0 R09: 0000000000023900
[ 9061.685312] R10: 0000000000000002 R11: 0000000000000001 R12: ffff880036e44000
[ 9061.685313] R13: 0000000000008000 R14: 0000000000ad5000 R15: ffff88006aef2600
[ 9061.685315] FS:  00007f5a3ad5e720(0000) GS:ffff8800bef00000(0000) knlGS:0000000000000000
[ 9061.685316] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033   
[ 9061.685317] CR2: 0000000000000050 CR3: 000000008d642000 CR4: 00000000000406e0
[ 9061.685318] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 9061.685319] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 9061.685321] Process cat (pid: 30229, threadinfo ffff88006ac68000, task ffff880122f496e0)
[ 9061.685321] Stack:
[ 9061.685322]  0000000000000000 ffffffffa0107160 ffff88006ac69f48 0000000000008000
[ 9061.685324]  0000000000ad5000 ffff88006aef2600 ffff88006ac69e98 ffffffff813b69b7
[ 9061.685326]  ffff88006ac69e88 ffffffff811107ee ffff88006ac69e98 ffff88006aef2620
[ 9061.685328] Call Trace:
[ 9061.685332]  [<ffffffff813b69b7>] dev_attr_show+0x27/0x50
[ 9061.685335]  [<ffffffff811107ee>] ? __get_free_pages+0xe/0x50   
[ 9061.685337]  [<ffffffff811d3e13>] sysfs_read_file+0xc3/0x190
[ 9061.685340]  [<ffffffff81164f73>] vfs_read+0xc3/0x180
[ 9061.685342]  [<ffffffff81165081>] sys_read+0x51/0x90
[ 9061.685344]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
[ 9061.685345] Code: 5c 41 5d 41 5e 41 5f c9 c3 0f 1f 00 49 8b 96 e8 60 10 a0 48 c7 c6 23 62 10 a0 eb ac 0f 1f 84 00 00 00 00 00 48 8b 87 b0 02 00 00 <4c> 8b 68 50 e8 c0 19 00 00 48 89 c3 e9 3f ff ff ff 4c 89 e9 48
[ 9061.685361] RIP  [<ffffffffa01036e7>] show_protocols+0xf7/0x130 [rc_core]
[ 9061.685364]  RSP <ffff88006ac69e38>
[ 9061.685364] CR2: 0000000000000050
[ 9061.685366] ---[ end trace 7da562ecac808b24 ]---

```Any ideas?

---

### Post by scox_nz on 2011-07-16
Have you tried running lircd daemon directly (as root) with the -n (no daemon) option?

I had exactly the same symptoms as you, and it worked running it manually, but not via /etc/init.d/lird start

running:
```

sudo dpkg-reconfigure lirc

```

and selecting the dev/input/by-id/usb-... device made things work.

---

### Post by douglasbagnall on 2012-06-23
This is a kernel bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1015836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1015836)

---

