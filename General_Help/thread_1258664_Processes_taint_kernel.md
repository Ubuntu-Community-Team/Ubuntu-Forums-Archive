---
title: "Processes taint kernel"
date: 2009-09-05
forum: General Help
---

### Post by pveurshout on 2009-09-05
Hello,

Recently I've been experiencing quite a lot of lockups, often complete system freezes. Sometimes I could use Alt+SysRq+<key> (R-E-I-S-U-B) combinations to softly reboot, but most of the times I had to do a hard reboot by pressing the power button. In the logs (when there were any - if the system was entirely stuck and Alt+sysrq wouldn't work, there was nothing in them) I have noticed that they all contained something like this:
```

[ 3453.580479] Pid: 4061, comm: ktorrent Tainted: P           2.6.28-14-generic #47-Ubuntu

```
As this had to do with a different application each time (so far I have noticed java, kmess, ktorrent, gnome-screensav, gnome-system-mo) I doubt it's caused by a single program and there should be more to it than just a buggy application.

The following was in /var/log/messages just after it happened the third time today (I locked the session with ktorrent running and when I came back I could move the cursor (although it was kind of 'blinking') but the window to enter my password wouldn't show up. I used Alt+SysRq+{R-E-I-S-U-B} to reboot):

```
Sep  5 15:27:52 peter-hp-ubuntu -- MARK --
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580338] PGD b890f067 PUD bccf8067 PMD 0 
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580360] Dumping ftrace buffer:
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580366]    (ftrace buffer empty)
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580369] CPU 0 
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580373] Modules linked in: binfmt_misc bridge stp bnep input_polldev lp pata_pcmcia snd_hda_intel snd_pcm_oss snd_mixer_oss arc4 ecb snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event iwlagn snd_seq iwlcore snd_timer snd_seq_device snd uvcvideo leds_hp_disk mac80211 video led_class soundcore compat_ioctl32 psmouse pcmcia ppdev parport_pc joydev iTCO_wdt videodev serio_raw pcspkr tpm_infineon tpm tpm_bios parport sdhci_pci sdhci ricoh_mmc output snd_page_alloc cfg80211 intel_agp btusb lis3lv02d iTCO_vendor_support v4l1_compat usbhid yenta_socket rsrc_nonstatic pcmcia_core nvidia(P) ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580479] Pid: 4061, comm: ktorrent Tainted: P           2.6.28-14-generic #47-Ubuntu
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580483] RIP: 0010:[<ffffffff802fa385>]  [<ffffffff802fa385>] d_path+0x25/0xf0
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580492] RSP: 0018:ffff8800b8877dd8  EFLAGS: 00010286
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580496] RAX: 000000000000012a RBX: ffff880067584300 RCX: ffff8800b8877e58
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580501] RDX: 0000000000000ed6 RSI: ffff88004209e12a RDI: 0000000000000000
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580506] RBP: ffff8800b8877e18 R08: 0000000000000003 R09: 0000000000000000
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580510] R10: 0000000000000003 R11: ffff88004209e117 R12: ffff8800b8877e58
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580515] R13: 0000000000000ed6 R14: ffff88004209e12a R15: ffff88013c9bc400
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580521] FS:  00007ff9fd008750(0000) GS:ffffffff80a9a000(0000) knlGS:0000000000000000
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580526] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580530] CR2: 0000000000000088 CR3: 0000000037973000 CR4: 00000000000006a0
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580535] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580539] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580545] Process ktorrent (pid: 4061, threadinfo ffff8800b8876000, task ffff8800b8849660)
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580552]  ffff8800b8877e28 ffffffff80303e0d ffff88013cc43d00 ffffffff807f8161
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580723]  RSP <ffff8800b8877dd8>
Sep  5 15:45:13 peter-hp-ubuntu kernel: [ 3453.580732] ---[ end trace 2e7244c1733dac3b 
```
This was followed by the following, which actually appeared in the logs like ten times: (it's exactly the same type of error message, except that another process (gnome-screensav) is mentioned. Also notice that the above message states CPU0 in the second line, whereas the one below states CPU1)
```
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030393] PGD 3c455067 PUD 427e5067 PMD 0 
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030414] CPU 1 
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030418] Modules linked in: binfmt_misc bridge stp bnep input_polldev lp pata_pcmcia snd_hda_intel snd_pcm_oss snd_mixer_oss arc4 ecb snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event iwlagn snd_seq iwlcore snd_timer snd_seq_device snd uvcvideo leds_hp_disk mac80211 video led_class soundcore compat_ioctl32 psmouse pcmcia ppdev parport_pc joydev iTCO_wdt videodev serio_raw pcspkr tpm_infineon tpm tpm_bios parport sdhci_pci sdhci ricoh_mmc output snd_page_alloc cfg80211 intel_agp btusb lis3lv02d iTCO_vendor_support v4l1_compat usbhid yenta_socket rsrc_nonstatic pcmcia_core nvidia(P) ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030524] Pid: 5716, comm: gnome-screensav Tainted: P      D    2.6.28-14-generic #47-Ubuntu
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030530] RIP: 0010:[<ffffffff802fa385>]  [<ffffffff802fa385>] d_path+0x25/0xf0
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030538] RSP: 0018:ffff88003c457dd8  EFLAGS: 00010286
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030543] RAX: 000000000000012a RBX: ffff880067584180 RCX: ffff88003c457e58
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030548] RDX: 0000000000000ed6 RSI: ffff88001af3f12a RDI: 0000000000000000
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030553] RBP: ffff88003c457e18 R08: 0000000000000003 R09: 0000000000000000
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030557] R10: 0000000000000003 R11: ffff88001af3f117 R12: ffff88003c457e58
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030562] R13: 0000000000000ed6 R14: ffff88001af3f12a R15: ffff88013c9bc400
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030568] FS:  00007ffadfc487d0(0000) GS:ffff88013f802d80(0000) knlGS:0000000000000000
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030573] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030577] CR2: 0000000000000088 CR3: 000000004e0d8000 CR4: 00000000000006a0
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030582] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030587] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030592] Process gnome-screensav (pid: 5716, threadinfo ffff88003c456000, task ffff8800b8815980)
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030600]  ffff88003c457e28 ffffffff80303e0d ffff88013cc43d00 ffffffff807f8161
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030769]  RSP <ffff88003c457dd8>
Sep  5 15:47:38 peter-hp-ubuntu kernel: [ 3599.030847] ---[ end trace 2e7244c1733dac3b ]---
```

I'm using amd64 Jaunty and I've been running into this both when booting kernel 2.6.28-14-generic and 2.6.28-15-generic. Also, I have run memtest+ which didn't return any errors. Does anyone know what is happening and what could cause this to happen?

---

### Post by pveurshout on 2009-09-05
Just got the same kind of error message. My wireless network connection stopped working (DNS first, and a few minutes later the rest of it as well) and I got this in dmesg:

```
[ 4210.914044] wlan0: disassociating by local choice (reason=3)
[ 4211.063678] ------------[ cut here ]------------
[ 4211.063686] WARNING: at /build/buildd/linux-2.6.28/fs/sysfs/group.c:138 sysfs_remove_group+0xd9/0xe0()
[ 4211.063691] sysfs group ffffffff808dee80 not found for kobject 'iwl-phy0:assoc'
[ 4211.063695] Modules linked in: usbhid binfmt_misc bridge stp bnep input_polldev lp pata_pcmcia snd_hda_intel arc4 snd_pcm_oss snd_mixer_oss ecb snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq iwlagn iwlcore uvcvideo pcmcia compat_ioctl32 snd_timer snd_seq_device ppdev mac80211 leds_hp_disk led_class psmouse snd parport_pc sdhci_pci tpm_infineon tpm yenta_socket rsrc_nonstatic video joydev videodev soundcore serio_raw parport ricoh_mmc sdhci tpm_bios intel_agp btusb cfg80211 iTCO_wdt iTCO_vendor_support pcmcia_core pcspkr output lis3lv02d v4l1_compat snd_page_alloc nvidia(P) ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
[ 4211.063804] Pid: 3081, comm: NetworkManager Tainted: P           2.6.28-15-generic #49-Ubuntu
[ 4211.063809] Call Trace:
[ 4211.063819]  [<ffffffff80250ad7>] warn_slowpath+0xb7/0xf0
[ 4211.063830]  [<ffffffff8048bd0a>] ? extract_buf+0x8a/0xe0
[ 4211.063840]  [<ffffffff8069b839>] ? _spin_lock+0x9/0x10
[ 4211.063847]  [<ffffffff802df3a2>] ? add_partial+0x52/0x90
[ 4211.063854]  [<ffffffff80348fd1>] ? release_sysfs_dirent+0x61/0xe0
[ 4211.063860]  [<ffffffff8034870d>] ? sysfs_find_dirent+0x2d/0x40
[ 4211.063867]  [<ffffffff8034a309>] sysfs_remove_group+0xd9/0xe0
[ 4211.063875]  [<ffffffff804be157>] dpm_sysfs_remove+0x17/0x20
[ 4211.063883]  [<ffffffff804b7af2>] device_del+0x22/0x1e0
[ 4211.063890]  [<ffffffff804b7cc1>] device_unregister+0x11/0x20
[ 4211.063901]  [<ffffffffa0971098>] led_classdev_unregister+0x58/0xa0 [led_class]
[ 4211.063924]  [<ffffffffa0a0e0e4>] iwl_leds_unregister_led+0x44/0x70 [iwlcore]
[ 4211.063941]  [<ffffffffa0a0e12a>] iwl_leds_unregister+0x1a/0x60 [iwlcore]
[ 4211.064001]  [<ffffffffa0a23707>] __iwl4965_down+0x47/0x470 [iwlagn]
[ 4211.064016]  [<ffffffffa0a23b5b>] iwl4965_down+0x2b/0x50 [iwlagn]
[ 4211.064030]  [<ffffffffa0a24c68>] iwl4965_mac_stop+0x78/0x110 [iwlagn]
[ 4211.064060]  [<ffffffffa0989f53>] ieee80211_stop+0x243/0x4d0 [mac80211]
[ 4211.064070]  [<ffffffff805c7d93>] ? dev_deactivate+0x1b3/0x1d0
[ 4211.064077]  [<ffffffff805b1266>] dev_close+0x66/0xb0
[ 4211.064084]  [<ffffffff805b33c6>] dev_change_flags+0x96/0x1e0
[ 4211.064092]  [<ffffffff805bd53c>] do_setlink+0x23c/0x3e0
[ 4211.064099]  [<ffffffff805d24dd>] ? nla_reserve+0x2d/0x40
[ 4211.064106]  [<ffffffff805bcd2c>] ? rtnl_fill_ifinfo+0x32c/0x460
[ 4211.064112]  [<ffffffff805d2806>] ? nla_parse+0x36/0x110
[ 4211.064118]  [<ffffffff805bd7ed>] rtnl_setlink+0x10d/0x150
[ 4211.064125]  [<ffffffff805d161b>] ? netlink_dump_start+0x15b/0x1a0
[ 4211.064132]  [<ffffffff805bce60>] ? rtnl_dump_ifinfo+0x0/0xa0
[ 4211.064139]  [<ffffffff805bc76e>] rtnetlink_rcv_msg+0x18e/0x240
[ 4211.064145]  [<ffffffff805bc5e0>] ? rtnetlink_rcv_msg+0x0/0x240
[ 4211.064151]  [<ffffffff805d0df9>] netlink_rcv_skb+0x89/0xb0
[ 4211.064158]  [<ffffffff805bc5c7>] rtnetlink_rcv+0x27/0x40
[ 4211.064164]  [<ffffffff805d1c99>] ? netlink_sendmsg+0x149/0x2f0
[ 4211.064170]  [<ffffffff805d0b15>] netlink_unicast+0x2c5/0x2e0
[ 4211.064178]  [<ffffffff805a9cde>] ? __alloc_skb+0x6e/0x150
[ 4211.064184]  [<ffffffff805d1d54>] netlink_sendmsg+0x204/0x2f0
[ 4211.064191]  [<ffffffff805a3b17>] sock_sendmsg+0x107/0x130
[ 4211.064199]  [<ffffffff80268ae0>] ? autoremove_wake_function+0x0/0x40
[ 4211.064206]  [<ffffffff805a3427>] ? move_addr_to_kernel+0x57/0x60
[ 4211.064212]  [<ffffffff805ac22c>] ? verify_iovec+0x3c/0xd0
[ 4211.064218]  [<ffffffff805a3cc9>] sys_sendmsg+0x189/0x320
[ 4211.064224]  [<ffffffff805a3faa>] ? sys_sendto+0xea/0x120
[ 4211.064230]  [<ffffffff802f9700>] ? d_free+0x50/0x60
[ 4211.064238]  [<ffffffff802e9340>] ? __fput+0x170/0x1f0
[ 4211.064246]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
[ 4211.064250] ---[ end trace 00ba3b3a01f015c0 ]---
[ 4211.064303] ------------[ cut here ]------------
[ 4211.064307] WARNING: at /build/buildd/linux-2.6.28/fs/sysfs/group.c:138 sysfs_remove_group+0xd9/0xe0()
[ 4211.064312] sysfs group ffffffff808dee80 not found for kobject 'iwl-phy0:RX'
[ 4211.064316] Modules linked in: usbhid binfmt_misc bridge stp bnep input_polldev lp pata_pcmcia snd_hda_intel arc4 snd_pcm_oss snd_mixer_oss ecb snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq iwlagn iwlcore uvcvideo pcmcia compat_ioctl32 snd_timer snd_seq_device ppdev mac80211 leds_hp_disk led_class psmouse snd parport_pc sdhci_pci tpm_infineon tpm yenta_socket rsrc_nonstatic video joydev videodev soundcore serio_raw parport ricoh_mmc sdhci tpm_bios intel_agp btusb cfg80211 iTCO_wdt iTCO_vendor_support pcmcia_core pcspkr output lis3lv02d v4l1_compat snd_page_alloc nvidia(P) ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
[ 4211.064408] Pid: 3081, comm: NetworkManager Tainted: P        W  2.6.28-15-generic #49-Ubuntu
[ 4211.064412] Call Trace:
[ 4211.064418]  [<ffffffff80250ad7>] warn_slowpath+0xb7/0xf0
[ 4211.064425]  [<ffffffff802fde8c>] ? ifind_fast+0x9c/0xa0
[ 4211.064431]  [<ffffffff802fdec6>] ? ilookup+0x36/0x50
[ 4211.064437]  [<ffffffff803488c4>] ? sysfs_drop_dentry+0x24/0x140
[ 4211.064444]  [<ffffffff80348fd1>] ? release_sysfs_dirent+0x61/0xe0
[ 4211.064450]  [<ffffffff8034870d>] ? sysfs_find_dirent+0x2d/0x40
[ 4211.064456]  [<ffffffff8034a309>] sysfs_remove_group+0xd9/0xe0
[ 4211.064463]  [<ffffffff804be157>] dpm_sysfs_remove+0x17/0x20
[ 4211.064470]  [<ffffffff804b7af2>] device_del+0x22/0x1e0
[ 4211.064477]  [<ffffffff804b7cc1>] device_unregister+0x11/0x20
[ 4211.064487]  [<ffffffffa0971098>] led_classdev_unregister+0x58/0xa0 [led_class]
[ 4211.064505]  [<ffffffffa0a0e0e4>] iwl_leds_unregister_led+0x44/0x70 [iwlcore]
[ 4211.064549]  [<ffffffffa0a0e138>] iwl_leds_unregister+0x28/0x60 [iwlcore]
[ 4211.064564]  [<ffffffffa0a23707>] __iwl4965_down+0x47/0x470 [iwlagn]
[ 4211.064577]  [<ffffffffa0a23b5b>] iwl4965_down+0x2b/0x50 [iwlagn]
[ 4211.064591]  [<ffffffffa0a24c68>] iwl4965_mac_stop+0x78/0x110 [iwlagn]
[ 4211.064617]  [<ffffffffa0989f53>] ieee80211_stop+0x243/0x4d0 [mac80211]
[ 4211.064625]  [<ffffffff805c7d93>] ? dev_deactivate+0x1b3/0x1d0
[ 4211.064631]  [<ffffffff805b1266>] dev_close+0x66/0xb0
[ 4211.064637]  [<ffffffff805b33c6>] dev_change_flags+0x96/0x1e0
[ 4211.064644]  [<ffffffff805bd53c>] do_setlink+0x23c/0x3e0
[ 4211.064650]  [<ffffffff805d24dd>] ? nla_reserve+0x2d/0x40
[ 4211.064657]  [<ffffffff805bcd2c>] ? rtnl_fill_ifinfo+0x32c/0x460
[ 4211.064662]  [<ffffffff805d2806>] ? nla_parse+0x36/0x110
[ 4211.064669]  [<ffffffff805bd7ed>] rtnl_setlink+0x10d/0x150
[ 4211.064676]  [<ffffffff805d161b>] ? netlink_dump_start+0x15b/0x1a0
[ 4211.064682]  [<ffffffff805bce60>] ? rtnl_dump_ifinfo+0x0/0xa0
[ 4211.064689]  [<ffffffff805bc76e>] rtnetlink_rcv_msg+0x18e/0x240
[ 4211.064695]  [<ffffffff805bc5e0>] ? rtnetlink_rcv_msg+0x0/0x240
[ 4211.064702]  [<ffffffff805d0df9>] netlink_rcv_skb+0x89/0xb0
[ 4211.064708]  [<ffffffff805bc5c7>] rtnetlink_rcv+0x27/0x40
[ 4211.064714]  [<ffffffff805d1c99>] ? netlink_sendmsg+0x149/0x2f0
[ 4211.064720]  [<ffffffff805d0b15>] netlink_unicast+0x2c5/0x2e0
[ 4211.064727]  [<ffffffff805a9cde>] ? __alloc_skb+0x6e/0x150
[ 4211.064733]  [<ffffffff805d1d54>] netlink_sendmsg+0x204/0x2f0
[ 4211.064738]  [<ffffffff805a3b17>] sock_sendmsg+0x107/0x130
[ 4211.064746]  [<ffffffff80268ae0>] ? autoremove_wake_function+0x0/0x40
[ 4211.064753]  [<ffffffff805a3427>] ? move_addr_to_kernel+0x57/0x60
[ 4211.064759]  [<ffffffff805ac22c>] ? verify_iovec+0x3c/0xd0
[ 4211.064764]  [<ffffffff805a3cc9>] sys_sendmsg+0x189/0x320
[ 4211.064770]  [<ffffffff805a3faa>] ? sys_sendto+0xea/0x120
[ 4211.064775]  [<ffffffff802f9700>] ? d_free+0x50/0x60
[ 4211.064782]  [<ffffffff802e9340>] ? __fput+0x170/0x1f0
[ 4211.064789]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
[ 4211.064793] ---[ end trace 00ba3b3a01f015c0 ]---
[ 4211.064829] ------------[ cut here ]------------
[ 4211.064833] WARNING: at /build/buildd/linux-2.6.28/fs/sysfs/group.c:138 sysfs_remove_group+0xd9/0xe0()
[ 4211.064838] sysfs group ffffffff808dee80 not found for kobject 'iwl-phy0:TX'
[ 4211.064841] Modules linked in: usbhid binfmt_misc bridge stp bnep input_polldev lp pata_pcmcia snd_hda_intel arc4 snd_pcm_oss snd_mixer_oss ecb snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq iwlagn iwlcore uvcvideo pcmcia compat_ioctl32 snd_timer snd_seq_device ppdev mac80211 leds_hp_disk led_class psmouse snd parport_pc sdhci_pci tpm_infineon tpm yenta_socket rsrc_nonstatic video joydev videodev soundcore serio_raw parport ricoh_mmc sdhci tpm_bios intel_agp btusb cfg80211 iTCO_wdt iTCO_vendor_support pcmcia_core pcspkr output lis3lv02d v4l1_compat snd_page_alloc nvidia(P) ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
[ 4211.064933] Pid: 3081, comm: NetworkManager Tainted: P        W  2.6.28-15-generic #49-Ubuntu

```
(actually it displayed the same thing a couple of times more, probably it stopped doing that once I disabled wireless in the network manager and re-enabled it)

Notice how it, again, says "Tainted: P        W  2.6.28-15-generic #49-Ubuntu". I have absolutely no clue what this means :confused:

---

### Post by falconindy on 2009-09-05
Is it always ktorrent generating the taint? If it is, switch BT clients.

Simple explanation: taint occurs when a program overwrites a parent function call and tries to make it do something its not supposed to. Sometimes its recoverable. Sometimes, as you've found, it ends somewhat disasterously. Taint is also the basis for attacks such as SQL injection.

---

### Post by pveurshout on 2009-09-05
No, it's not always KTorrent. I actually switched from Vuze to KTorrent because I suspected Vuze caused these lockups. Today I tried Deluge for a change, but unfortunately this resulted in a complete system freeze as well while it was checking the files of a previously downloaded torrent (which I added so I could seed) :(

Could it have something to do with reading/writing from/to an (internal) NTFS-partition (because I've gotten these taints from three different torrent clients, all writing to this partition, now)? I have never seen anything specific mentioning the partition or ntfs-3g or something in the logs, though.

---

### Post by falconindy on 2009-09-05
> **pveurshout said:**
> No, it's not always KTorrent. I actually switched from Vuze to KTorrent because I suspected Vuze caused these lockups. Today I tried Deluge for a change, but unfortunately this resulted in a complete system freeze as well while it was checking the files of a previously downloaded torrent (which I added so I could seed) :(

Could it have something to do with reading/writing from/to an (internal) NTFS-partition (because I've gotten these taints from three different torrent clients, all writing to this partition, now)? I have never seen anything specific mentioning the partition or ntfs-3g or something in the logs, though.
It seems unlikely, but it's easy enough to test and rule out, though. Is it possible for you to unmount the NTFS partition and temporarily write your torrent data elsewhere?

---

### Post by pveurshout on 2009-09-05
I copied some of the torrent data to my / partition (it's only 12 GB), unmounted the NTFS-partition where I normally write this kind of data to and added the torrents to KTorrent again (after removing the other ones which would otherwise try to write to the unmounted partition). Thanks for your help so far! Tomorrow (it's getting late over here) I'll wait and see what happens if I keep KTorrent running for a while and I'll report back either when the system freezes or when it keeps running without any problems for a full day.

---

### Post by pveurshout on 2009-09-06
OK, first results: for the past 2 hours and up until now it works just fine. I'm uploading a 5.6 GB torrent consisting of 478 items from the (ext3) root partition.

I also stumbled upon the [NTFS-3G release history]("http://www.ntfs-3g.org/releases.html") ([http://www.ntfs-3g.org/releases.html](http://www.ntfs-3g.org/releases.html)). Notice how it says version 2009.4.4 fixed the following:
> # Fix: The driver could crash handling highly fragmented files. 
I'm pre-allocating, but not 'zeroing', disk space before a new torrent starts (I'm not sure up to what extent this prevents the files from becoming fragmented compared to "Pre-allocate and zero" (Vuze) or "Fully reserve disk space"(KTorrent)). This morning I copied 12.6 GB of files (which I downloaded yesterday while the system froze three times) to my external (NTFS-formatted) hard drive and this caused no problems whatsoever. Currently I'm using version 2009.2.1 of ntfs-3g (this came with Jaunty). Would it be helpful to try out the newer version of ntfs-3g, or would it be better to try something else out first (as copying the same files to a HDD did not cause any trouble)?

EDIT: Actually, I thought of something I might better do first: move the files back from the ext3 partition to my NTFS partition, so they're non-fragmented (**Is this assumption correct?**) and see what happens then when I add, check and seed them.

---

### Post by 3rdalbum on 2009-09-06
I thought the word "Tainted" referred to the presence of proprietary kernel modules? If you look in your dmesg output, it shows: "NetworkManager Tained: P" and then if you look in the module list in the dmesg output, beside the word "nvidia" it has the capital P.

---

### Post by cos85 on 2009-09-06
Run a diagnostic on the disc you suspect may be causing the problem. If you're keeping an NTFS partition you must have Windows, so use that to defrag the partition the way it was intended to be defragged. If you don't have Windows, get rid of NTFS and use something else.

Note: If you hibernate Windows and boot into Linux, or hibernate Linux and boot into Windows while you have NTFS mounted, bad things might happen.

---

### Post by pveurshout on 2009-09-06
> **3rdalbum said:**
> I thought the word "Tainted" referred to the presence of proprietary kernel modules? If you look in your dmesg output, it shows: "NetworkManager Tained: P" and then if you look in the module list in the dmesg output, beside the word "nvidia" it has the capital P.

I can't find "nvidia" with a "P" besides it, but I have indeed noticed in dmesg that the proprietary nvidia drivers taint the kernel. However, can this be the cause for other applications -I've noticed about a dozen so far, not just the different bittorrent clients- tainting the kernel?

> **cos85 said:**
> Run a diagnostic on the disc you suspect may be causing the problem. If you're keeping an NTFS partition you must have Windows, so use that to defrag the partition the way it was intended to be defragged. If you don't have Windows, get rid of NTFS and use something else.

I did a file system check and checked for bad sectors with Vista (there was something wrong with the file system which was repaired..actually it always says it corrects something when I run this test, although I've never noticed anything being wrong with it, actually) and afterwards used Auslogics Disk Defrag to defragment the disk (I don't like the built-in Vista defrag tool as it doesn't graphically show what it's doing/has done). It was heavily fragmented (52%). I'm excited to see if this did the trick for getting rid of the problems in Ubuntu. I'll let you guys know and mark the thread as [solved] if it keeps working the next few days.

If it does, I'd like to upgrade to NTFS-3G version 2009.4.4. Is there an easy way to do this using Synaptic, or should I wait until Karmic is released? Unfortunately it only shows version 2009.2.1 in the package list (currently installed).

Anyway, all this still leaves me wondering why this problem, which is likely to be caused by a bug in ntfs-3g, doesn't show up as such in any log file, but gives the impression there's something wrong with all these other applications instead. Anyone have any thoughts on this?

---

### Post by 3rdalbum on 2009-09-06
From post #2:

> Modules linked in: usbhid binfmt_misc bridge stp (...) nvidia(P) (...)
Pid: 3081, comm: NetworkManager Tainted: P

Actually now that you mention it, I believe I remember reading that some processes can taint the kernel. But I think the dmesg output is not actually saying that the NetworkManager (or whatever) process has tainted the kernel, merely that the kernel is tainted.

NTFS-3G is a possible likely cause of your problems, because it's a userspace program that interfaces at a fairly low-level with your hardware.

---

### Post by pveurshout on 2009-09-06
> 
Actually now that you mention it, I believe I remember reading that some processes can taint the kernel. But I think the dmesg output is not actually saying that the NetworkManager (or whatever) process has tainted the kernel, merely that the kernel is tainted.
So could this actually be ntfs-3g that's tainting the kernel when it fails to do a certain task (read/write to the NTFS-partition)?

It just froze on me again, this time the caps lock light went on and I couldn't do anything but press the power button (Alt+SysRq+REISUB didn't work) :cry: I'm afraid defragging didn't solve the problem after all, so either something (ntfs-3g, kernel, I'm afraid I don't know enough about Ubuntu to tell..) is not doing what it's supposed to do, or it's just Jaunty which is buggy (while searching for a solution to my problem, I've read many complaints from people experiencing random freezes in Jaunty where the caps lock indicator light (and sometimes other lights, too) on their keyboards started blinking and stuff) (these had nothing to do with bittorrenting+NTFS-partitions).

[EDIT]
[http://www.google.nl/#hl=nl&q=random+freezes+jaunty+blinking+%22caps+lock%22&meta=&fp=cc575a2f8f3b2b71](http://www.google.nl/#hl=nl&q=random+freezes+jaunty+blinking+%22caps+lock%22&meta=&fp=cc575a2f8f3b2b71)
The caps lock indicator-thing seems to be quite common [S]and may be related to the wireless card (I'm using an Intel WiFi Link 5300). If it is, I should find out by taking the step below.[/S] (yesterday it also froze while checking the contents of a previously downloaded torrent I added, so before there was any wireless activity)
[/EDIT]

Unfortunately there was nothing in the logs again. I was running a bittorrent client (Deluge) (though it was only seeding from a 0% fragmented partition) so I'm gonna run one reading from my ext3 partition only the next couple of days to find out whether it still freezes (it has actually frozen before without a bittorrent client running, although if I remember correctly this always happened within a minute after logging on or so).

If anyone has a better plan to find/rule out possible causes to this, that'd of course be very much appreciated :)

---

### Post by pveurshout on 2009-09-10
Alright, it definately seems to be an ntfs-3g problem. I've had no trouble in the past few days seeding from an ext3 partition and when I was transferring a 2 GB file over the network (from an NTFS partition) a couple of minutes ago, the system froze on me again after just a couple of minutes. I guess I should consider getting rid of NTFS completely when it comes to heavy file usage (so just leave some documents I really need on both Ubuntu and Vista on an NTFS partition). (Come to think of it..I haven't really *ever* used Vista since buying this laptop except for solving some problems that came with it(=Vista) :lol: )

I just have 2 more questions:

1) Can I update to ntfs-3g version 2009.4.4 in Jaunty, as this should have the bug causing problems with heavily fragmented files fixed? (I'm currently using 2009.2.1, which comes with Jaunty)
2) If I run the 'long' smartctl HDD test, and it says there are no errors, does this mean I can rule out hardware causing these system freezes with my NTFS-partition?

---

### Post by pveurshout on 2009-09-13
OK, I reformatted my NTFS partition to ext3 and so far it seemed to have been working great for about a day, but a couple of minutes ago something went wrong again. I thought it was just X crashing (the screen was messed up and I could only move my mouse a little bit once every few seconds) or had something to do with OpenOffice (it crashed just when I opened a document - it has done that once before), but in the logs I saw the following:
```

Sep 13 20:04:35 peter-hp-ubuntu kernel: [ 4999.724574] NVRM: Xid (0001:00): 8, Channel 00000001
Sep 13 20:04:35 peter-hp-ubuntu kernel: [ 4999.794166] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00000f10 00000000 00000040
Sep 13 20:04:35 peter-hp-ubuntu kernel: [ 4999.795142] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00000f10 00000000 00000040
Sep 13 20:04:35 peter-hp-ubuntu kernel: [ 4999.803395] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00000f10 00000000 00000040
Sep 13 20:04:35 peter-hp-ubuntu kernel: [ 5000.102970] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00001310 00000000 00000040
Sep 13 20:04:35 peter-hp-ubuntu kernel: [ 5000.106336] NVRM: Xid (0001:00): 6, PE0001 
Sep 13 20:04:35 peter-hp-ubuntu kernel: [ 5000.378227] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 000015e0 00000000 00000040
Sep 13 20:04:36 peter-hp-ubuntu kernel: [ 5000.546770] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 000015e0 00000000 00000040
Sep 13 20:09:46 peter-hp-ubuntu kernel: [ 5311.069177] wlan0: disassociating by local choice (reason=3)
Sep 13 20:09:47 peter-hp-ubuntu kernel: [ 5311.477735] deluge[4060]: segfault at 160000008e ip 00007fadc799d7db sp 00007fffd27f5d00 error 4 in libgtk-x11-2.0.so.0.1600.1[7fadc7825000+3ef000]
```
Especially notice how the last message says 'deluge'. It -again!- seems like having something to do with torrenting/certain-partition-disk-activity! Is it really Deluge causing this (even though 1) it crashed exactly while opening OpenOffice Writer and I've had such a crash before when doing that, but without having any bittorrent client running, and 2) it didn't entirely freeze, but (eventually and with a lot of effort) allowed me to shut down)

I've read something about segmentation faults having to do with memory. Can this be caused by bad memory? I've run memtest+ and it showed no errors, though.

EDIT: quick additional question: If yes (bad memory), is it likely that all the previous system freezes (which were entire freezes, unlike this) have had to do with this, or would in that case just the app have crashed instead of having the system freeze _entirely_?

---

