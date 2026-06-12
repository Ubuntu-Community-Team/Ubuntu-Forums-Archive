---
title: "System crashed (possibly network or USB related)"
date: 2009-08-14
forum: General Help
---

### Post by bchurchill on 2009-08-14
I recently bought a new computer and installed Ubuntu 9.04.  I don't have any other operating systems installed so I don't know if this is really Ubuntu-specific.  I was running the following programs when my computer froze:

- a few instances of konsole
- firefox
- a program I'm working on that communicates with USB devices for DMX control (this includes dmxd and dmxtcl; the former shows up on logs)
- Kate
- RhythmBox

I left the room  for a few minutes and when I returned the music was stuttering and the computer was entirely unresponsive.  After rebooting, the last 15 minutes of /var/log/syslog before the reboot is listed below.

I would appreciate any explaination of what happened, if this is a software issue (in particular, if it's my applications fault), or a hardware issue.  Suggestions for fixes would be highly appreciated.  In the log I see lots of messages about networking, some from dmxd and USB, and a lot of stuff I don't understand.

/var/log/syslog:
```

Aug 13 21:30:01 berkeley-justice /USR/SBIN/CRON[3656]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 13 21:38:21 berkeley-justice kernel: [11501.152100] usb 8-2: USB disconnect, address 2
Aug 13 21:38:25 berkeley-justice kernel: [11505.048065] usb 8-2: new low speed USB device using uhci_hcd and address 3
Aug 13 21:38:25 berkeley-justice kernel: [11505.223237] usb 8-2: configuration #1 chosen from 1 choice
Aug 13 21:38:25 berkeley-justice kernel: [11505.244214] generic-usb 0003:10CF:8062.000B: hiddev98,hidraw4: USB HID v1.00 Device [Velleman  USB K8062] on usb-0000:00:1d.2-2/input0
Aug 13 21:38:52 berkeley-justice kernel: [11532.648110] usb 8-2: USB disconnect, address 3
Aug 13 21:38:56 berkeley-justice kernel: [11536.113575] usb 8-2: new low speed USB device using uhci_hcd and address 4
Aug 13 21:38:56 berkeley-justice kernel: [11536.291229] usb 8-2: configuration #1 chosen from 1 choice
Aug 13 21:38:56 berkeley-justice kernel: [11536.313195] generic-usb 0003:10CF:8062.000C: hiddev98,hidraw4: USB HID v1.00 Device [Velleman  USB K8062] on usb-0000:00:1d.2-2/input0
Aug 13 21:40:01 berkeley-justice /USR/SBIN/CRON[4884]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 13 21:46:46 berkeley-justice kernel: [12006.381196] general protection fault: 0000 [#1] SMP 
Aug 13 21:46:46 berkeley-justice kernel: [12006.381201] last sysfs file: /sys/devices/virtual/net/pan0/statistics/collisions
Aug 13 21:46:46 berkeley-justice kernel: [12006.381205] Dumping ftrace buffer:
Aug 13 21:46:46 berkeley-justice kernel: [12006.381208]    (ftrace buffer empty)
Aug 13 21:46:46 berkeley-justice kernel: [12006.381210] CPU 2 
Aug 13 21:46:46 berkeley-justice kernel: [12006.381212] Modules linked in: usb_storage cifs aes_x86_64 aes_generic binfmt_misc ppdev bridge stp bnep input_polldev nls_iso8859_1 nls_cp437 vfat fat lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi arc4 snd_rawmidi ecb snd_seq_midi_event snd_seq snd_timer snd_seq_device iwlagn iwlcore led_class snd mac80211 psmouse soundcore sdhci_pci pcspkr serio_raw snd_page_alloc sdhci intel_agp iTCO_wdt iTCO_vendor_support cfg80211 usbhid btusb video output ohci1394 ieee1394 r8169 mii fbcon tileblit font bitblit softcursor
Aug 13 21:46:46 berkeley-justice kernel: [12006.381258] Pid: 4772, comm: dmxd Not tainted 2.6.28-14-generic #47-Ubuntu
Aug 13 21:46:46 berkeley-justice kernel: [12006.381260] RIP: 0010:[<ffffffff802e33b4>]  [<ffffffff802e33b4>] __kmalloc+0x74/0x110
Aug 13 21:46:46 berkeley-justice kernel: [12006.381269] RSP: 0018:ffff880089f53d58  EFLAGS: 00010006
Aug 13 21:46:46 berkeley-justice kernel: [12006.381271] RAX: 0000000000000000 RBX: 194059476837b9fc RCX: 0000000000000000
Aug 13 21:46:46 berkeley-justice kernel: [12006.381274] RDX: ffff88002804e000 RSI: 00000000000000d0 RDI: 0000000000000008
Aug 13 21:46:46 berkeley-justice kernel: [12006.381276] RBP: ffff880089f53d88 R08: 0000000000000000 R09: ffff8800bec52de0
Aug 13 21:46:46 berkeley-justice kernel: [12006.381279] R10: ffff880089f53e48 R11: 0000000000000000 R12: ffffffff809abcb8
Aug 13 21:46:46 berkeley-justice kernel: [12006.381281] R13: 0000000000000282 R14: 00000000000000d0 R15: ffffffff805394c5
Aug 13 21:46:46 berkeley-justice kernel: [12006.381284] FS:  00007f80c10c1700(0000) GS:ffff88013f802d80(0000) knlGS:0000000000000000
Aug 13 21:46:46 berkeley-justice kernel: [12006.381286] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 13 21:46:46 berkeley-justice kernel: [12006.381289] CR2: 0000000001af5a78 CR3: 00000000be86e000 CR4: 00000000000406a0
Aug 13 21:46:46 berkeley-justice kernel: [12006.381291] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 13 21:46:46 berkeley-justice kernel: [12006.381293] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 13 21:46:46 berkeley-justice kernel: [12006.381296] Process dmxd (pid: 4772, threadinfo ffff880089f52000, task ffff8800bd00d980)
Aug 13 21:46:46 berkeley-justice kernel: [12006.381298] Stack:
Aug 13 21:46:46 berkeley-justice kernel: [12006.381300]  00000008c90e5770 ffff88004f829cc0 0000000000000000 ffff8800bec52de0
Aug 13 21:46:46 berkeley-justice kernel: [12006.381305]  00007fffc90e5770 ffff88000ed43d80 ffff880089f53e18 ffffffff805394c5
Aug 13 21:46:46 berkeley-justice kernel: [12006.381310]  ffff88004f9b7240 ffff88013e10f0c0 00007fffc90e5770 00007fff00000000
Aug 13 21:46:46 berkeley-justice kernel: [12006.381315] Call Trace:
Aug 13 21:46:46 berkeley-justice kernel: [12006.381317]  [<ffffffff805394c5>] proc_do_submiturb+0x2d5/0x9f0
Aug 13 21:46:46 berkeley-justice kernel: [12006.381323]  [<ffffffff80537653>] ? free_async+0x43/0x50
Aug 13 21:46:46 berkeley-justice kernel: [12006.381327]  [<ffffffff80539e97>] usbdev_ioctl+0x2b7/0xe70
Aug 13 21:46:46 berkeley-justice kernel: [12006.381330]  [<ffffffff8022ce93>] ? read_hpet+0x13/0x20
Aug 13 21:46:46 berkeley-justice kernel: [12006.381335]  [<ffffffff8026c6e9>] ? ktime_get_ts+0x59/0x60
Aug 13 21:46:46 berkeley-justice kernel: [12006.381339]  [<ffffffff802f650d>] vfs_ioctl+0x7d/0xa0
Aug 13 21:46:46 berkeley-justice kernel: [12006.381344]  [<ffffffff802f6875>] do_vfs_ioctl+0x75/0x230
Aug 13 21:46:46 berkeley-justice kernel: [12006.381348]  [<ffffffff802f6ac9>] sys_ioctl+0x99/0xa0
Aug 13 21:46:46 berkeley-justice kernel: [12006.381351]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Aug 13 21:46:46 berkeley-justice kernel: [12006.381355] Code: fa 0f 1f 80 00 00 00 00 65 8b 04 25 24 00 00 00 48 98 49 8b 94 c4 e8 00 00 00 8b 7a 18 89 7d d4 48 8b 1a 48 85 db 74 4f 8b 42 14 <48> 8b 04 c3 48 89 02 4c 89 ef 57 9d 66 0f 1f 44 00 00 66 45 85 
Aug 13 21:46:46 berkeley-justice kernel: [12006.381392] RIP  [<ffffffff802e33b4>] __kmalloc+0x74/0x110
Aug 13 21:46:46 berkeley-justice kernel: [12006.381395]  RSP <ffff880089f53d58>
Aug 13 21:46:46 berkeley-justice kernel: [12006.381398] ---[ end trace a6ca28ec8233ffdb ]---
Aug 13 21:46:49 berkeley-justice kernel: [12008.834805] general protection fault: 0000 [#2] SMP 
Aug 13 21:46:49 berkeley-justice kernel: [12008.834810] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/net/wlan0/statistics/collisions
Aug 13 21:46:49 berkeley-justice kernel: [12008.834813] CPU 2 
Aug 13 21:46:49 berkeley-justice kernel: [12008.834815] Modules linked in: usb_storage cifs aes_x86_64 aes_generic binfmt_misc ppdev bridge stp bnep input_polldev nls_iso8859_1 nls_cp437 vfat fat lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi arc4 snd_rawmidi ecb snd_seq_midi_event snd_seq snd_timer snd_seq_device iwlagn iwlcore led_class snd mac80211 psmouse soundcore sdhci_pci pcspkr serio_raw snd_page_alloc sdhci intel_agp iTCO_wdt iTCO_vendor_support cfg80211 usbhid btusb video output ohci1394 ieee1394 r8169 mii fbcon tileblit font bitblit softcursor
Aug 13 21:46:49 berkeley-justice kernel: [12008.834862] Pid: 5690, comm: ifconfig Tainted: G      D    2.6.28-14-generic #47-Ubuntu
Aug 13 21:46:49 berkeley-justice kernel: [12008.834865] RIP: 0010:[<ffffffff802e33b4>]  [<ffffffff802e33b4>] __kmalloc+0x74/0x110
Aug 13 21:46:49 berkeley-justice kernel: [12008.834874] RSP: 0018:ffff8800b59b3c98  EFLAGS: 00010006
Aug 13 21:46:49 berkeley-justice kernel: [12008.834876] RAX: 0000000000000000 RBX: 194059476837b9fc RCX: 0000000000000004
Aug 13 21:46:49 berkeley-justice kernel: [12008.834879] RDX: ffff88002804e000 RSI: 00000000000080d0 RDI: 0000000000000008
Aug 13 21:46:49 berkeley-justice kernel: [12008.834881] RBP: ffff8800b59b3cc8 R08: ffff880103ae03c0 R09: 0000000000000000
Aug 13 21:46:49 berkeley-justice kernel: [12008.834883] R10: ffff88013410cc38 R11: ffffffff8080a8ce R12: ffffffff809abcb8
Aug 13 21:46:49 berkeley-justice kernel: [12008.834886] R13: 0000000000000282 R14: 00000000000080d0 R15: ffffffff803045f7
Aug 13 21:46:49 berkeley-justice kernel: [12008.834889] FS:  00007f04ce8096f0(0000) GS:ffff88013f802d80(0000) knlGS:0000000000000000
Aug 13 21:46:49 berkeley-justice kernel: [12008.834891] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 13 21:46:49 berkeley-justice kernel: [12008.834893] CR2: 00007f04ce3072f0 CR3: 000000000eccd000 CR4: 00000000000406a0
Aug 13 21:46:49 berkeley-justice kernel: [12008.834896] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 13 21:46:49 berkeley-justice kernel: [12008.834898] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 13 21:46:49 berkeley-justice kernel: [12008.834901] Process ifconfig (pid: 5690, threadinfo ffff8800b59b2000, task ffff8800bd00acc0)
Aug 13 21:46:49 berkeley-justice kernel: [12008.834903] Stack:
Aug 13 21:46:49 berkeley-justice kernel: [12008.834905]  00000008b59b3d48 ffff88013cc5a540 ffffffff806ff100 ffff880103ae03c0
Aug 13 21:46:49 berkeley-justice kernel: [12008.834909]  0000000000000000 ffff88013410cc38 ffff8800b59b3cf8 ffffffff803045f7
Aug 13 21:46:49 berkeley-justice kernel: [12008.834914]  ffff8800b59b3e38 ffff88013cc5a540 ffff880089ef8d00 0000000000000001
Aug 13 21:46:49 berkeley-justice kernel: [12008.834920] Call Trace:
Aug 13 21:46:49 berkeley-justice kernel: [12008.834922]  [<ffffffff803045f7>] __seq_open_private+0x27/0x70
Aug 13 21:46:49 berkeley-justice kernel: [12008.834927]  [<ffffffff80340122>] seq_open_net+0x32/0x40
Aug 13 21:46:49 berkeley-justice kernel: [12008.834932]  [<ffffffff806337b5>] if6_seq_open+0x15/0x20
Aug 13 21:46:49 berkeley-justice kernel: [12008.834937]  [<ffffffff80336dd4>] proc_reg_open+0xa4/0x180
Aug 13 21:46:49 berkeley-justice kernel: [12008.834941]  [<ffffffff806337a0>] ? if6_seq_open+0x0/0x20
Aug 13 21:46:49 berkeley-justice kernel: [12008.834944]  [<ffffffff803400a0>] ? seq_release_net+0x0/0x10
Aug 13 21:46:49 berkeley-justice kernel: [12008.834948]  [<ffffffff802e5af8>] __dentry_open+0xd8/0x2d0
Aug 13 21:46:49 berkeley-justice kernel: [12008.834952]  [<ffffffff80336d30>] ? proc_reg_open+0x0/0x180
Aug 13 21:46:49 berkeley-justice kernel: [12008.834956]  [<ffffffff802e5dd4>] nameidata_to_filp+0x44/0x60
Aug 13 21:46:49 berkeley-justice kernel: [12008.834959]  [<ffffffff802f4e7e>] do_filp_open+0x20e/0x930
Aug 13 21:46:49 berkeley-justice kernel: [12008.834964]  [<ffffffff8042065c>] ? strncpy_from_user+0x4c/0x80
Aug 13 21:46:49 berkeley-justice kernel: [12008.834969]  [<ffffffff8069b529>] ? _spin_lock+0x9/0x10
Aug 13 21:46:49 berkeley-justice kernel: [12008.834974]  [<ffffffff802ff2a1>] ? alloc_fd+0x121/0x150
Aug 13 21:46:49 berkeley-justice kernel: [12008.834978]  [<ffffffff802e5901>] do_sys_open+0x81/0x150
Aug 13 21:46:49 berkeley-justice kernel: [12008.834981]  [<ffffffff802e59fb>] sys_open+0x1b/0x20
Aug 13 21:46:49 berkeley-justice kernel: [12008.834985]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Aug 13 21:46:49 berkeley-justice kernel: [12008.834989] Code: fa 0f 1f 80 00 00 00 00 65 8b 04 25 24 00 00 00 48 98 49 8b 94 c4 e8 00 00 00 8b 7a 18 89 7d d4 48 8b 1a 48 85 db 74 4f 8b 42 14 <48> 8b 04 c3 48 89 02 4c 89 ef 57 9d 66 0f 1f 44 00 00 66 45 85 
Aug 13 21:46:49 berkeley-justice kernel: [12008.835026] RIP  [<ffffffff802e33b4>] __kmalloc+0x74/0x110
Aug 13 21:46:49 berkeley-justice kernel: [12008.835030]  RSP <ffff8800b59b3c98>
Aug 13 21:46:49 berkeley-justice kernel: [12008.835033] ---[ end trace a6ca28ec8233ffdb ]---
Aug 13 21:46:53 berkeley-justice kernel: [12012.838643] general protection fault: 0000 [#3] SMP 
Aug 13 21:46:53 berkeley-justice kernel: [12012.838649] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/net/wlan0/statistics/collisions
Aug 13 21:46:53 berkeley-justice kernel: [12012.838652] CPU 2 
Aug 13 21:46:53 berkeley-justice kernel: [12012.838654] Modules linked in: usb_storage cifs aes_x86_64 aes_generic binfmt_misc ppdev bridge stp bnep input_polldev nls_iso8859_1 nls_cp437 vfat fat lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi arc4 snd_rawmidi ecb snd_seq_midi_event snd_seq snd_timer snd_seq_device iwlagn iwlcore led_class snd mac80211 psmouse soundcore sdhci_pci pcspkr serio_raw snd_page_alloc sdhci intel_agp iTCO_wdt iTCO_vendor_support cfg80211 usbhid btusb video output ohci1394 ieee1394 r8169 mii fbcon tileblit font bitblit softcursor
Aug 13 21:46:53 berkeley-justice kernel: [12012.838700] Pid: 5719, comm: ifconfig Tainted: G      D    2.6.28-14-generic #47-Ubuntu
Aug 13 21:46:53 berkeley-justice kernel: [12012.838703] RIP: 0010:[<ffffffff802e33b4>]  [<ffffffff802e33b4>] __kmalloc+0x74/0x110
Aug 13 21:46:53 berkeley-justice kernel: [12012.838711] RSP: 0018:ffff8800b5819c98  EFLAGS: 00010006
Aug 13 21:46:53 berkeley-justice kernel: [12012.838713] RAX: 0000000000000000 RBX: 194059476837b9fc RCX: 0000000000000004
Aug 13 21:46:53 berkeley-justice kernel: [12012.838716] RDX: ffff88002804e000 RSI: 00000000000080d0 RDI: 0000000000000008
Aug 13 21:46:53 berkeley-justice kernel: [12012.838718] RBP: ffff8800b5819cc8 R08: ffff880062ff7c00 R09: 0000000000000000
Aug 13 21:46:53 berkeley-justice kernel: [12012.838720] R10: ffff88013410cc38 R11: ffffffff8080a8ce R12: ffffffff809abcb8
Aug 13 21:46:53 berkeley-justice kernel: [12012.838723] R13: 0000000000000282 R14: 00000000000080d0 R15: ffffffff803045f7
Aug 13 21:46:53 berkeley-justice kernel: [12012.838726] FS:  00007f59a636b6f0(0000) GS:ffff88013f802d80(0000) knlGS:0000000000000000
Aug 13 21:46:53 berkeley-justice kernel: [12012.838728] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 13 21:46:53 berkeley-justice kernel: [12012.838731] CR2: 00007f59a5f37d94 CR3: 000000008532f000 CR4: 00000000000406a0
Aug 13 21:46:53 berkeley-justice kernel: [12012.838733] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 13 21:46:53 berkeley-justice kernel: [12012.838735] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 13 21:46:53 berkeley-justice kernel: [12012.838738] Process ifconfig (pid: 5719, threadinfo ffff8800b5818000, task ffff88012dcad980)
Aug 13 21:46:53 berkeley-justice kernel: [12012.838740] Stack:
Aug 13 21:46:53 berkeley-justice kernel: [12012.838742]  00000008b5819d48 ffff88013cc5a540 ffffffff806ff100 ffff880062ff7c00
Aug 13 21:46:53 berkeley-justice kernel: [12012.838746]  0000000000000000 ffff88013410cc38 ffff8800b5819cf8 ffffffff803045f7
Aug 13 21:46:53 berkeley-justice kernel: [12012.838751]  ffff8800b5819e38 ffff88013cc5a540 ffff880089ef8500 0000000000000001
Aug 13 21:46:53 berkeley-justice kernel: [12012.838756] Call Trace:
Aug 13 21:46:53 berkeley-justice kernel: [12012.838758]  [<ffffffff803045f7>] __seq_open_private+0x27/0x70
Aug 13 21:46:53 berkeley-justice kernel: [12012.838764]  [<ffffffff80340122>] seq_open_net+0x32/0x40
Aug 13 21:46:53 berkeley-justice kernel: [12012.838769]  [<ffffffff806337b5>] if6_seq_open+0x15/0x20
Aug 13 21:46:53 berkeley-justice kernel: [12012.838774]  [<ffffffff80336dd4>] proc_reg_open+0xa4/0x180
Aug 13 21:46:53 berkeley-justice kernel: [12012.838777]  [<ffffffff806337a0>] ? if6_seq_open+0x0/0x20
Aug 13 21:46:53 berkeley-justice kernel: [12012.838781]  [<ffffffff803400a0>] ? seq_release_net+0x0/0x10
Aug 13 21:46:53 berkeley-justice kernel: [12012.838785]  [<ffffffff802e5af8>] __dentry_open+0xd8/0x2d0
Aug 13 21:46:53 berkeley-justice kernel: [12012.838789]  [<ffffffff80336d30>] ? proc_reg_open+0x0/0x180
Aug 13 21:46:53 berkeley-justice kernel: [12012.838792]  [<ffffffff802e5dd4>] nameidata_to_filp+0x44/0x60
Aug 13 21:46:53 berkeley-justice kernel: [12012.838796]  [<ffffffff802f4e7e>] do_filp_open+0x20e/0x930
Aug 13 21:46:53 berkeley-justice kernel: [12012.838800]  [<ffffffff8042065c>] ? strncpy_from_user+0x4c/0x80
Aug 13 21:46:53 berkeley-justice kernel: [12012.838805]  [<ffffffff8069b529>] ? _spin_lock+0x9/0x10
Aug 13 21:46:53 berkeley-justice kernel: [12012.838810]  [<ffffffff802ff2a1>] ? alloc_fd+0x121/0x150
Aug 13 21:46:53 berkeley-justice kernel: [12012.838814]  [<ffffffff802e5901>] do_sys_open+0x81/0x150
Aug 13 21:46:53 berkeley-justice kernel: [12012.838817]  [<ffffffff802e59fb>] sys_open+0x1b/0x20
Aug 13 21:46:53 berkeley-justice kernel: [12012.838821]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Aug 13 21:46:53 berkeley-justice kernel: [12012.838825] Code: fa 0f 1f 80 00 00 00 00 65 8b 04 25 24 00 00 00 48 98 49 8b 94 c4 e8 00 00 00 8b 7a 18 89 7d d4 48 8b 1a 48 85 db 74 4f 8b 42 14 <48> 8b 04 c3 48 89 02 4c 89 ef 57 9d 66 0f 1f 44 00 00 66 45 85 
Aug 13 21:46:53 berkeley-justice kernel: [12012.838862] RIP  [<ffffffff802e33b4>] __kmalloc+0x74/0x110
Aug 13 21:46:53 berkeley-justice kernel: [12012.838865]  RSP <ffff8800b5819c98>
Aug 13 21:46:53 berkeley-justice kernel: [12012.838868] ---[ end trace a6ca28ec8233ffdb ]---
Aug 13 21:46:53 berkeley-justice avahi-daemon[3134]: Withdrawing address record for fe80::221:6aff:fe58:b39e on wlan0.
Aug 13 21:46:53 berkeley-justice dhclient: receive_packet failed on wlan0: Network is down
Aug 13 21:46:53 berkeley-justice dhclient: There is already a pid file /var/run/dhclient.pid with pid 5247
Aug 13 21:46:53 berkeley-justice dhclient: killed old client process, removed PID file
Aug 13 21:46:53 berkeley-justice dhclient: Internet Systems Consortium DHCP Client V3.1.1
Aug 13 21:46:53 berkeley-justice dhclient: Copyright 2004-2008 Internet Systems Consortium.
Aug 13 21:46:53 berkeley-justice dhclient: All rights reserved.
Aug 13 21:46:53 berkeley-justice dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Aug 13 21:46:53 berkeley-justice dhclient: 
Aug 13 21:46:53 berkeley-justice dhclient: wmaster0: unknown hardware address type 801
Aug 13 21:46:53 berkeley-justice dhclient: wmaster0: unknown hardware address type 801
Aug 13 21:46:53 berkeley-justice dhclient: Bind socket to interface: No such device
Aug 13 21:46:53 berkeley-justice dhclient: Internet Systems Consortium DHCP Client V3.1.1
Aug 13 21:46:53 berkeley-justice dhclient: Copyright 2004-2008 Internet Systems Consortium.
Aug 13 21:46:53 berkeley-justice dhclient: All rights reserved.
Aug 13 21:46:53 berkeley-justice dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Aug 13 21:46:53 berkeley-justice dhclient: 
Aug 13 21:46:53 berkeley-justice dhclient: wmaster0: unknown hardware address type 801
Aug 13 21:46:53 berkeley-justice dhclient: wmaster0: unknown hardware address type 801
Aug 13 21:46:53 berkeley-justice dhclient: Bind socket to interface: No such device
Aug 13 21:46:53 berkeley-justice avahi-daemon[3134]: Withdrawing address record for 192.168.0.15 on wlan0.
Aug 13 21:46:53 berkeley-justice avahi-daemon[3134]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.15.
Aug 13 21:46:53 berkeley-justice avahi-daemon[3134]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug 13 21:46:53 berkeley-justice kernel: [12013.029078] Registered led device: iwl-phy0:radio
Aug 13 21:46:53 berkeley-justice kernel: [12013.029098] Registered led device: iwl-phy0:assoc
Aug 13 21:46:53 berkeley-justice kernel: [12013.029116] Registered led device: iwl-phy0:RX
Aug 13 21:46:53 berkeley-justice kernel: [12013.029133] Registered led device: iwl-phy0:TX
Aug 13 21:46:53 berkeley-justice kernel: [12013.044662] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 13 21:46:53 berkeley-justice kernel: [12013.073902] wlan0: deauthenticating by local choice (reason=3)

```/var/log/messages:
```

Aug 13 21:38:21 berkeley-justice kernel: [11501.152100] usb 8-2: USB disconnect, address 2
Aug 13 21:38:25 berkeley-justice kernel: [11505.048065] usb 8-2: new low speed USB device using uhci_hcd and address 3
Aug 13 21:38:25 berkeley-justice kernel: [11505.223237] usb 8-2: configuration #1 chosen from 1 choice
Aug 13 21:38:25 berkeley-justice kernel: [11505.244214] generic-usb 0003:10CF:8062.000B: hiddev98,hidraw4: USB HID v1.00 Device [Velleman  USB K8062] on usb-0000:00:1d.2-2/input0
Aug 13 21:38:52 berkeley-justice kernel: [11532.648110] usb 8-2: USB disconnect, address 3
Aug 13 21:38:56 berkeley-justice kernel: [11536.113575] usb 8-2: new low speed USB device using uhci_hcd and address 4
Aug 13 21:38:56 berkeley-justice kernel: [11536.291229] usb 8-2: configuration #1 chosen from 1 choice
Aug 13 21:38:56 berkeley-justice kernel: [11536.313195] generic-usb 0003:10CF:8062.000C: hiddev98,hidraw4: USB HID v1.00 Device [Velleman  USB K8062] on usb-0000:00:1d.2-2/input0
Aug 13 21:46:46 berkeley-justice kernel: [12006.381205] Dumping ftrace buffer:
Aug 13 21:46:46 berkeley-justice kernel: [12006.381208]    (ftrace buffer empty)
Aug 13 21:46:46 berkeley-justice kernel: [12006.381210] CPU 2 
Aug 13 21:46:46 berkeley-justice kernel: [12006.381212] Modules linked in: usb_storage cifs aes_x86_64 aes_generic binfmt_misc ppdev bridge stp bnep input_polldev nls_iso8859_1 nls_cp437 vfat fat lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi arc4 snd_rawmidi ecb snd_seq_midi_event snd_seq snd_timer snd_seq_device iwlagn iwlcore led_class snd mac80211 psmouse soundcore sdhci_pci pcspkr serio_raw snd_page_alloc sdhci intel_agp iTCO_wdt iTCO_vendor_support cfg80211 usbhid btusb video output ohci1394 ieee1394 r8169 mii fbcon tileblit font bitblit softcursor
Aug 13 21:46:46 berkeley-justice kernel: [12006.381258] Pid: 4772, comm: dmxd Not tainted 2.6.28-14-generic #47-Ubuntu
Aug 13 21:46:46 berkeley-justice kernel: [12006.381260] RIP: 0010:[<ffffffff802e33b4>]  [<ffffffff802e33b4>] __kmalloc+0x74/0x110
Aug 13 21:46:46 berkeley-justice kernel: [12006.381269] RSP: 0018:ffff880089f53d58  EFLAGS: 00010006
Aug 13 21:46:46 berkeley-justice kernel: [12006.381271] RAX: 0000000000000000 RBX: 194059476837b9fc RCX: 0000000000000000
Aug 13 21:46:46 berkeley-justice kernel: [12006.381274] RDX: ffff88002804e000 RSI: 00000000000000d0 RDI: 0000000000000008
Aug 13 21:46:46 berkeley-justice kernel: [12006.381276] RBP: ffff880089f53d88 R08: 0000000000000000 R09: ffff8800bec52de0
Aug 13 21:46:46 berkeley-justice kernel: [12006.381279] R10: ffff880089f53e48 R11: 0000000000000000 R12: ffffffff809abcb8
Aug 13 21:46:46 berkeley-justice kernel: [12006.381281] R13: 0000000000000282 R14: 00000000000000d0 R15: ffffffff805394c5
Aug 13 21:46:46 berkeley-justice kernel: [12006.381284] FS:  00007f80c10c1700(0000) GS:ffff88013f802d80(0000) knlGS:0000000000000000
Aug 13 21:46:46 berkeley-justice kernel: [12006.381286] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 13 21:46:46 berkeley-justice kernel: [12006.381289] CR2: 0000000001af5a78 CR3: 00000000be86e000 CR4: 00000000000406a0
Aug 13 21:46:46 berkeley-justice kernel: [12006.381291] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 13 21:46:46 berkeley-justice kernel: [12006.381293] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 13 21:46:46 berkeley-justice kernel: [12006.381296] Process dmxd (pid: 4772, threadinfo ffff880089f52000, task ffff8800bd00d980)
Aug 13 21:46:46 berkeley-justice kernel: [12006.381300]  00000008c90e5770 ffff88004f829cc0 0000000000000000 ffff8800bec52de0
Aug 13 21:46:46 berkeley-justice kernel: [12006.381395]  RSP <ffff880089f53d58>
Aug 13 21:46:46 berkeley-justice kernel: [12006.381398] ---[ end trace a6ca28ec8233ffdb ]---
Aug 13 21:46:49 berkeley-justice kernel: [12008.834813] CPU 2 
Aug 13 21:46:49 berkeley-justice kernel: [12008.834815] Modules linked in: usb_storage cifs aes_x86_64 aes_generic binfmt_misc ppdev bridge stp bnep input_polldev nls_iso8859_1 nls_cp437 vfat fat lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi arc4 snd_rawmidi ecb snd_seq_midi_event snd_seq snd_timer snd_seq_device iwlagn iwlcore led_class snd mac80211 psmouse soundcore sdhci_pci pcspkr serio_raw snd_page_alloc sdhci intel_agp iTCO_wdt iTCO_vendor_support cfg80211 usbhid btusb video output ohci1394 ieee1394 r8169 mii fbcon tileblit font bitblit softcursor
Aug 13 21:46:49 berkeley-justice kernel: [12008.834862] Pid: 5690, comm: ifconfig Tainted: G      D    2.6.28-14-generic #47-Ubuntu
Aug 13 21:46:49 berkeley-justice kernel: [12008.834865] RIP: 0010:[<ffffffff802e33b4>]  [<ffffffff802e33b4>] __kmalloc+0x74/0x110
Aug 13 21:46:49 berkeley-justice kernel: [12008.834874] RSP: 0018:ffff8800b59b3c98  EFLAGS: 00010006
Aug 13 21:46:49 berkeley-justice kernel: [12008.834876] RAX: 0000000000000000 RBX: 194059476837b9fc RCX: 0000000000000004
Aug 13 21:46:49 berkeley-justice kernel: [12008.834879] RDX: ffff88002804e000 RSI: 00000000000080d0 RDI: 0000000000000008
Aug 13 21:46:49 berkeley-justice kernel: [12008.834881] RBP: ffff8800b59b3cc8 R08: ffff880103ae03c0 R09: 0000000000000000
Aug 13 21:46:49 berkeley-justice kernel: [12008.834883] R10: ffff88013410cc38 R11: ffffffff8080a8ce R12: ffffffff809abcb8
Aug 13 21:46:49 berkeley-justice kernel: [12008.834886] R13: 0000000000000282 R14: 00000000000080d0 R15: ffffffff803045f7
Aug 13 21:46:49 berkeley-justice kernel: [12008.834889] FS:  00007f04ce8096f0(0000) GS:ffff88013f802d80(0000) knlGS:0000000000000000
Aug 13 21:46:49 berkeley-justice kernel: [12008.834891] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 13 21:46:49 berkeley-justice kernel: [12008.834893] CR2: 00007f04ce3072f0 CR3: 000000000eccd000 CR4: 00000000000406a0
Aug 13 21:46:49 berkeley-justice kernel: [12008.834896] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 13 21:46:49 berkeley-justice kernel: [12008.834898] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 13 21:46:49 berkeley-justice kernel: [12008.834901] Process ifconfig (pid: 5690, threadinfo ffff8800b59b2000, task ffff8800bd00acc0)
Aug 13 21:46:49 berkeley-justice kernel: [12008.834905]  00000008b59b3d48 ffff88013cc5a540 ffffffff806ff100 ffff880103ae03c0
Aug 13 21:46:49 berkeley-justice kernel: [12008.835030]  RSP <ffff8800b59b3c98>
Aug 13 21:46:49 berkeley-justice kernel: [12008.835033] ---[ end trace a6ca28ec8233ffdb ]---
Aug 13 21:46:53 berkeley-justice kernel: [12012.838652] CPU 2 
Aug 13 21:46:53 berkeley-justice kernel: [12012.838654] Modules linked in: usb_storage cifs aes_x86_64 aes_generic binfmt_misc ppdev bridge stp bnep input_polldev nls_iso8859_1 nls_cp437 vfat fat lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi arc4 snd_rawmidi ecb snd_seq_midi_event snd_seq snd_timer snd_seq_device iwlagn iwlcore led_class snd mac80211 psmouse soundcore sdhci_pci pcspkr serio_raw snd_page_alloc sdhci intel_agp iTCO_wdt iTCO_vendor_support cfg80211 usbhid btusb video output ohci1394 ieee1394 r8169 mii fbcon tileblit font bitblit softcursor
Aug 13 21:46:53 berkeley-justice kernel: [12012.838700] Pid: 5719, comm: ifconfig Tainted: G      D    2.6.28-14-generic #47-Ubuntu
Aug 13 21:46:53 berkeley-justice kernel: [12012.838703] RIP: 0010:[<ffffffff802e33b4>]  [<ffffffff802e33b4>] __kmalloc+0x74/0x110
Aug 13 21:46:53 berkeley-justice kernel: [12012.838711] RSP: 0018:ffff8800b5819c98  EFLAGS: 00010006
Aug 13 21:46:53 berkeley-justice kernel: [12012.838713] RAX: 0000000000000000 RBX: 194059476837b9fc RCX: 0000000000000004
Aug 13 21:46:53 berkeley-justice kernel: [12012.838716] RDX: ffff88002804e000 RSI: 00000000000080d0 RDI: 0000000000000008
Aug 13 21:46:53 berkeley-justice kernel: [12012.838718] RBP: ffff8800b5819cc8 R08: ffff880062ff7c00 R09: 0000000000000000
Aug 13 21:46:53 berkeley-justice kernel: [12012.838720] R10: ffff88013410cc38 R11: ffffffff8080a8ce R12: ffffffff809abcb8
Aug 13 21:46:53 berkeley-justice kernel: [12012.838723] R13: 0000000000000282 R14: 00000000000080d0 R15: ffffffff803045f7
Aug 13 21:46:53 berkeley-justice kernel: [12012.838726] FS:  00007f59a636b6f0(0000) GS:ffff88013f802d80(0000) knlGS:0000000000000000
Aug 13 21:46:53 berkeley-justice kernel: [12012.838728] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 13 21:46:53 berkeley-justice kernel: [12012.838731] CR2: 00007f59a5f37d94 CR3: 000000008532f000 CR4: 00000000000406a0
Aug 13 21:46:53 berkeley-justice kernel: [12012.838733] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 13 21:46:53 berkeley-justice kernel: [12012.838735] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 13 21:46:53 berkeley-justice kernel: [12012.838738] Process ifconfig (pid: 5719, threadinfo ffff8800b5818000, task ffff88012dcad980)
Aug 13 21:46:53 berkeley-justice kernel: [12012.838742]  00000008b5819d48 ffff88013cc5a540 ffffffff806ff100 ffff880062ff7c00
Aug 13 21:46:53 berkeley-justice kernel: [12012.838865]  RSP <ffff8800b5819c98>
Aug 13 21:46:53 berkeley-justice kernel: [12012.838868] ---[ end trace a6ca28ec8233ffdb ]---
Aug 13 21:46:53 berkeley-justice kernel: [12013.029078] Registered led device: iwl-phy0:radio
Aug 13 21:46:53 berkeley-justice kernel: [12013.029098] Registered led device: iwl-phy0:assoc
Aug 13 21:46:53 berkeley-justice kernel: [12013.029116] Registered led device: iwl-phy0:RX
Aug 13 21:46:53 berkeley-justice kernel: [12013.029133] Registered led device: iwl-phy0:TX
Aug 13 21:46:53 berkeley-justice kernel: [12013.044662] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by P4man on 2009-08-14
I have yet to meet someone who truly understands everything in the log files :) but i dont think its your app. This here I think is the most relevant line:

[B]general protection fault: 0000 [#1] SMP 
last sysfs file: /sys/devices/virtual/net/pan0/statistics/collisions
[/B]

Then your wifi seems to crash. Are you using wifi or some GSM dongle thing?

Anyway, if you google on it, you'll find others having same problem. They all seem to use the 64 bit kernel, and it always seems related to (dialup) networking.  Not sure how to solve it though :s

---

### Post by bchurchill on 2009-08-14
Thank you!  This is helpful.

Yes, I'm running a 64-bit system with an Intel 5300 wireless card.  Using wicd for a manager.  However I'm not using dialup... although I do have an internal modem which I've never used.  I'll google around.

---

### Post by P4man on 2009-08-14
Could well be the intel 5300 driver. Here, I found this:

[http://ubuntuforums.org/showthread.php?t=903240&page=4](http://ubuntuforums.org/showthread.php?t=903240&page=4)

Post 35 and onwards. Same card, 64 bit, kernel panics, he got it fixed using instructions in that thread...

good luck!

---

### Post by bchurchill on 2009-08-14
Thank you again.  I've followed the instructions there and everything appears to be working fine.  As in the other thread, crashes seem to happen sporadically after the system has been up for at least  a day.  So the problem is probably resolved, and if it isn't I'll post back here.

---

