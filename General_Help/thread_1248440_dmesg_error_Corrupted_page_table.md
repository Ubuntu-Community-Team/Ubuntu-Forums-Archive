---
title: "dmesg error: Corrupted page table"
date: 2009-08-24
forum: General Help
---

### Post by pveurshout on 2009-08-24
Hello,

The following just happened to me and I have no idea what caused it or whether something's totally wrong (I'm on a new laptop so I'm wondering whether it might be faulty hardware or something..) but some things look frightening, like:
```

[ 9776.420499] BUG: soft lockup - CPU#1 stuck for 61s! [gnome-system-mo:9731]

``` (full dmesg output below)

After writing some files to my external HDD, I unmounted, unhooked, and then started Vuze. The screen turned grey and although I managed to do a forced quit for the application, the whole system was messed up. Firefox, Epiphany, System Monitor, they all wouldn't start up anymore (actually the latter did nothing when I clicked it whereas the other two would freeze once the window had appeared). Fortunately, I could still get a terminal window and start gedit, so I was able to save the dmesg output. There was a whole bunch of stuff, but even with the help of Google I didn't manage to understand anything of what just happened :(

I'm particularly interested whether it has something to do with writing to an external (NTFS) HDD device, as this has given me some trouble in Ubuntu before (I'm hoping I can rule this link out, though).

Anyway, first, I wrote some files to an external (NTFS formatted) HDD device, which all seemed to go just fine:
```

[ 8028.872293] usb 2-5: new high speed USB device using ehci_hcd and address 3
[ 8029.010847] usb 2-5: configuration #1 chosen from 1 choice
[ 8029.150246] Initializing USB Mass Storage driver...
[ 8029.150595] scsi7 : SCSI emulation for USB Mass Storage devices
[ 8029.150799] usb-storage: device found at 3
[ 8029.150804] usb-storage: waiting for device to settle before scanning
[ 8029.150804] usbcore: registered new interface driver usb-storage
[ 8029.150811] USB Mass Storage support registered.
[ 8034.149130] usb-storage: device scan complete
[ 8034.150557] scsi 7:0:0:0: Direct-Access     WD       4000KS External  101a PQ: 0 ANSI: 4
[ 8034.154038] sd 7:0:0:0: [sdb] 781422768 512-byte hardware sectors: (400 GB/372 GiB)
[ 8034.154663] sd 7:0:0:0: [sdb] Write Protect is off
[ 8034.154669] sd 7:0:0:0: [sdb] Mode Sense: 11 00 00 00
[ 8034.154674] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 8034.156038] sd 7:0:0:0: [sdb] 781422768 512-byte hardware sectors: (400 GB/372 GiB)
[ 8034.156526] sd 7:0:0:0: [sdb] Write Protect is off
[ 8034.156531] sd 7:0:0:0: [sdb] Mode Sense: 11 00 00 00
[ 8034.156535] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 8034.156542]  sdb: sdb1
[ 8034.170923] sd 7:0:0:0: [sdb] Attached SCSI disk
[ 8034.171058] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 9060.800419] usb 2-5: USB disconnect, address 3

```

Then, a few minutes later (didn't do anything in between), I started Vuze and that's when it all started to go wrong:
```

[ 9426.031628] java: Corrupted page table at address 7fef83000000
[ 9426.031632] PGD 100978067 PUD 102382067 PMD 104d61067 PTE b1bdd42acd15e423
[ 9426.031636] Bad pagetable: 000f [#1] SMP 
[ 9426.031638] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/rfkill/rfkill0/state
[ 9426.031641] Dumping ftrace buffer:
[ 9426.031644]    (ftrace buffer empty)
[ 9426.031645] CPU 0 
[ 9426.031646] Modules linked in: usb_storage binfmt_misc bridge stp bnep input_polldev lp arc4 snd_hda_intel ecb pata_pcmcia snd_pcm_oss snd_mixer_oss snd_pcm iwlagn snd_seq_dummy iwlcore snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer uvcvideo snd_seq_device mac80211 pcmcia compat_ioctl32 leds_hp_disk led_class tpm_infineon psmouse snd ppdev videodev tpm video joydev serio_raw pcspkr yenta_socket rsrc_nonstatic pcmcia_core parport_pc parport usbhid iTCO_wdt iTCO_vendor_support ricoh_mmc sdhci_pci sdhci cfg80211 v4l1_compat tpm_bios intel_agp btusb output lis3lv02d soundcore nvidia(P) snd_page_alloc ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
[ 9426.031694] Pid: 9674, comm: java Tainted: P           2.6.28-15-generic #49-Ubuntu
[ 9426.031695] RIP: 0033:[<00007fef9b6fc1ee>]  [<00007fef9b6fc1ee>] 0x7fef9b6fc1ee
[ 9426.031699] RSP: 002b:00007fef37874c40  EFLAGS: 00010283
[ 9426.031700] RAX: 0000000000004460 RBX: 00007fef9bb1af68 RCX: 00007fef82ffbba0
[ 9426.031702] RDX: 0000000000000447 RSI: 0000000000001001 RDI: 0000000000002001
[ 9426.031703] RBP: 00007fef37874c90 R08: 00007fef82ffbba0 R09: 0000000000002002
[ 9426.031705] R10: 00007fef82ffbb90 R11: 0000000000002002 R12: 0000000001b3c800
[ 9426.031706] R13: 0000000000002004 R14: 0000000000010002 R15: 0000000001b411f8
[ 9426.031707] FS:  00007fef37876950(0000) GS:ffffffff80a9a000(0000) knlGS:0000000000000000
[ 9426.031709] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[ 9426.031710] CR2: 00007fef83000000 CR3: 0000000108da6000 CR4: 00000000000006a0
[ 9426.031712] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 9426.031713] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 9426.031715] Process java (pid: 9674, threadinfo ffff880131da2000, task ffff880104d39660)
[ 9426.031716] 
[ 9426.031717] RIP  [<00007fef9b6fc1ee>] 0x7fef9b6fc1ee
[ 9426.031719]  RSP <00007fef37874c40>
[ 9426.031720] ---[ end trace cbf7cf47eb37210d ]---
[ 9556.954074] BUG: unable to handle kernel paging request at ffffe24695cdcc9c
[ 9556.954078] IP: [<ffffffff803363a8>] smaps_pte_range+0x148/0x220
[ 9556.954084] PGD 28103067 PUD 0 
[ 9556.954086] Oops: 0000 [#2] SMP 
[ 9556.954088] last sysfs file: /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/charge_full
[ 9556.954090] CPU 0 
[ 9556.954092] Modules linked in: usb_storage binfmt_misc bridge stp bnep input_polldev lp arc4 snd_hda_intel ecb pata_pcmcia snd_pcm_oss snd_mixer_oss snd_pcm iwlagn snd_seq_dummy iwlcore snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer uvcvideo snd_seq_device mac80211 pcmcia compat_ioctl32 leds_hp_disk led_class tpm_infineon psmouse snd ppdev videodev tpm video joydev serio_raw pcspkr yenta_socket rsrc_nonstatic pcmcia_core parport_pc parport usbhid iTCO_wdt iTCO_vendor_support ricoh_mmc sdhci_pci sdhci cfg80211 v4l1_compat tpm_bios intel_agp btusb output lis3lv02d soundcore nvidia(P) snd_page_alloc ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
[ 9556.954122] Pid: 9710, comm: gnome-system-mo Tainted: P      D    2.6.28-15-generic #49-Ubuntu
[ 9556.954123] RIP: 0010:[<ffffffff803363a8>]  [<ffffffff803363a8>] smaps_pte_range+0x148/0x220
[ 9556.954126] RSP: 0018:ffff88010f963c48  EFLAGS: 00010206
[ 9556.954127] RAX: b1bdc00000000423 RBX: b1bdd42acd15e423 RCX: ffffe24695cdcc90
[ 9556.954128] RDX: ffffe24695cdcc90 RSI: 00007fef83000000 RDI: b1bdc00000000423
[ 9556.954129] RBP: ffff88010f963cb8 R08: ffff88010f963e38 R09: 0000000000000000
[ 9556.954131] R10: ffff88010019f130 R11: ffff88010019f035 R12: ffff880104d61000
[ 9556.954132] R13: 00007fef83000000 R14: ffff88010f963de8 R15: 00007fef83200000
[ 9556.954134] FS:  00007f16d22517e0(0000) GS:ffffffff80a9a000(0000) knlGS:0000000000000000
[ 9556.954135] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[ 9556.954136] CR2: ffffe24695cdcc9c CR3: 0000000138d45000 CR4: 00000000000006a0
[ 9556.954138] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 9556.954139] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 9556.954140] Process gnome-system-mo (pid: 9710, threadinfo ffff88010f962000, task ffff880100f62cc0)
[ 9556.954142] Stack:
[ 9556.954143]  ffff8801001a0000 ffff8801023820c0 ffffe24695cdcc90 000000018041f2f8
[ 9556.954145]  00007fef00000000 00007fef81640000 ffffe2000390ed48 ffff8800b71d23f0
[ 9556.954148]  0019f0350f963cd8 ffff880100978df0 0000000102382000 00007fef83000000
[ 9556.954151] Call Trace:
[ 9556.954152]  [<ffffffff802d1e5a>] walk_pmd_range+0x10a/0x1d0
[ 9556.954155]  [<ffffffff802d2050>] walk_pud_range+0x130/0x150
[ 9556.954157]  [<ffffffff802d21b8>] walk_page_range+0x148/0x180
[ 9556.954158]  [<ffffffff80335fd0>] show_smap+0x150/0x160
[ 9556.954161]  [<ffffffff80338d7c>] ? mm_for_maps+0x7c/0xc0
[ 9556.954163]  [<ffffffff80336260>] ? smaps_pte_range+0x0/0x220
[ 9556.954165]  [<ffffffff803044ff>] seq_read+0x24f/0x3a0
[ 9556.954168]  [<ffffffff802e8478>] vfs_read+0xc8/0x130
[ 9556.954171]  [<ffffffff802e85d0>] sys_read+0x50/0x90
[ 9556.954173]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
[ 9556.954176] Code: e8 6e c0 f8 ff 48 85 c0 48 89 45 a0 74 ad 48 89 df e8 5d 84 ef ff 90 a8 20 0f 84 94 00 00 00 49 81 46 30 00 10 00 00 48 8b 55 a0 <8b> 42 0c 83 c0 01 89 45 ac 83 e8 01 0f 8e 8e 00 00 00 48 89 df 
[ 9556.954197] RIP  [<ffffffff803363a8>] smaps_pte_range+0x148/0x220
[ 9556.954198]  RSP <ffff88010f963c48>
[ 9556.954200] CR2: ffffe24695cdcc9c
[ 9556.954201] ---[ end trace cbf7cf47eb37210d ]---
[ 9589.316856] iwlagn: Microcode SW error detected.  Restarting 0x2000000.
[ 9593.668040] wlan0: No ProbeResp from current AP 00:0c:f6:1e:16:5e - assume out of range
[ 9645.424498] BUG: soft lockup - CPU#1 stuck for 61s! [gnome-system-mo:9731]
[ 9645.424501] Modules linked in: usb_storage binfmt_misc bridge stp bnep input_polldev lp arc4 snd_hda_intel ecb pata_pcmcia snd_pcm_oss snd_mixer_oss snd_pcm iwlagn snd_seq_dummy iwlcore snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer uvcvideo snd_seq_device mac80211 pcmcia compat_ioctl32 leds_hp_disk led_class tpm_infineon psmouse snd ppdev videodev tpm video joydev serio_raw pcspkr yenta_socket rsrc_nonstatic pcmcia_core parport_pc parport usbhid iTCO_wdt iTCO_vendor_support ricoh_mmc sdhci_pci sdhci cfg80211 v4l1_compat tpm_bios intel_agp btusb output lis3lv02d soundcore nvidia(P) snd_page_alloc ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
[ 9645.424504] CPU 1:
[ 9645.424504] Modules linked in: usb_storage binfmt_misc bridge stp bnep input_polldev lp arc4 snd_hda_intel ecb pata_pcmcia snd_pcm_oss snd_mixer_oss snd_pcm iwlagn snd_seq_dummy iwlcore snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer uvcvideo snd_seq_device mac80211 pcmcia compat_ioctl32 leds_hp_disk led_class tpm_infineon psmouse snd ppdev videodev tpm video joydev serio_raw pcspkr yenta_socket rsrc_nonstatic pcmcia_core parport_pc parport usbhid iTCO_wdt iTCO_vendor_support ricoh_mmc sdhci_pci sdhci cfg80211 v4l1_compat tpm_bios intel_agp btusb output lis3lv02d soundcore nvidia(P) snd_page_alloc ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
[ 9645.424504] Pid: 9731, comm: gnome-system-mo Tainted: P      D    2.6.28-15-generic #49-Ubuntu
[ 9645.424504] RIP: 0010:[<ffffffff8022f564>]  [<ffffffff8022f564>] __ticket_spin_lock+0x14/0x20
[ 9645.424504] RSP: 0018:ffff880100fc9c28  EFLAGS: 00000297
[ 9645.424504] RAX: 0000000000009897 RBX: ffff880100fc9c28 RCX: ffff880100fc9e38
[ 9645.424504] RDX: ffffe20000000000 RSI: 00007fef83000000 RDI: ffffe2000390ed48
[ 9645.424504] RBP: ffff880100fc9c28 R08: ffff880100fc9e38 R09: 0000000000000000
[ 9645.424504] R10: ffff8801356e7130 R11: ffff8801356e7035 R12: 0000000000000246
[ 9645.424504] R13: ffffffff80911500 R14: 0000000000000000 R15: 001280d200fc9b88
[ 9645.424504] FS:  00007fbe5d5937e0(0000) GS:ffff88013f802d80(0000) knlGS:0000000000000000
[ 9645.424504] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[ 9645.424504] CR2: 0000000000b54060 CR3: 00000001006ac000 CR4: 00000000000006a0
[ 9645.424504] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 9645.424504] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 9645.424504] Call Trace:
[ 9645.424504]  [<ffffffff8069b839>] _spin_lock+0x9/0x10
[ 9645.424504]  [<ffffffff803362d3>] smaps_pte_range+0x73/0x220
[ 9645.424504]  [<ffffffff802d1e5a>] walk_pmd_range+0x10a/0x1d0
[ 9645.424504]  [<ffffffff802d2050>] walk_pud_range+0x130/0x150
[ 9645.424504]  [<ffffffff802d21b8>] walk_page_range+0x148/0x180
[ 9645.424504]  [<ffffffff80335fd0>] show_smap+0x150/0x160
[ 9645.424504]  [<ffffffff80338d7c>] ? mm_for_maps+0x7c/0xc0
[ 9645.424504]  [<ffffffff80336260>] ? smaps_pte_range+0x0/0x220
[ 9645.424504]  [<ffffffff803044ff>] seq_read+0x24f/0x3a0
[ 9645.424504]  [<ffffffff802e8478>] vfs_read+0xc8/0x130
[ 9645.424504]  [<ffffffff802e85d0>] sys_read+0x50/0x90
[ 9645.424504]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
[ 9710.924498] BUG: soft lockup - CPU#1 stuck for 61s! [gnome-system-mo:9731]
[ 9710.924502] Modules linked in: usb_storage binfmt_misc bridge stp bnep input_polldev lp arc4 snd_hda_intel ecb pata_pcmcia snd_pcm_oss snd_mixer_oss snd_pcm iwlagn snd_seq_dummy iwlcore snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer uvcvideo snd_seq_device mac80211 pcmcia compat_ioctl32 leds_hp_disk led_class tpm_infineon psmouse snd ppdev videodev tpm video joydev serio_raw pcspkr yenta_socket rsrc_nonstatic pcmcia_core parport_pc parport usbhid iTCO_wdt iTCO_vendor_support ricoh_mmc sdhci_pci sdhci cfg80211 v4l1_compat tpm_bios intel_agp btusb output lis3lv02d soundcore nvidia(P) snd_page_alloc ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
[ 9710.924503] CPU 1:
[ 9710.924503] Modules linked in: usb_storage binfmt_misc bridge stp bnep input_polldev lp arc4 snd_hda_intel ecb pata_pcmcia snd_pcm_oss snd_mixer_oss snd_pcm iwlagn snd_seq_dummy iwlcore snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer uvcvideo snd_seq_device mac80211 pcmcia compat_ioctl32 leds_hp_disk led_class tpm_infineon psmouse snd ppdev videodev tpm video joydev serio_raw pcspkr yenta_socket rsrc_nonstatic pcmcia_core parport_pc parport usbhid iTCO_wdt iTCO_vendor_support ricoh_mmc sdhci_pci sdhci cfg80211 v4l1_compat tpm_bios intel_agp btusb output lis3lv02d soundcore nvidia(P) snd_page_alloc ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
[ 9710.924503] Pid: 9731, comm: gnome-system-mo Tainted: P      D    2.6.28-15-generic #49-Ubuntu
[ 9710.924503] RIP: 0010:[<ffffffff8022f564>]  [<ffffffff8022f564>] __ticket_spin_lock+0x14/0x20
[ 9710.924503] RSP: 0018:ffff880100fc9c28  EFLAGS: 00000297
[ 9710.924503] RAX: 0000000000009897 RBX: ffff880100fc9c28 RCX: ffff880100fc9e38
[ 9710.924503] RDX: ffffe20000000000 RSI: 00007fef83000000 RDI: ffffe2000390ed48
[ 9710.924503] RBP: ffff880100fc9c28 R08: ffff880100fc9e38 R09: 0000000000000000
[ 9710.924503] R10: ffff8801356e7130 R11: ffff8801356e7035 R12: 0000000000000246
[ 9710.924503] R13: ffffffff80911500 R14: 0000000000000000 R15: 001280d200fc9b88
[ 9710.924503] FS:  00007fbe5d5937e0(0000) GS:ffff88013f802d80(0000) knlGS:0000000000000000
[ 9710.924503] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[ 9710.924503] CR2: 0000000000b54060 CR3: 00000001006ac000 CR4: 00000000000006a0
[ 9710.924503] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 9710.924503] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 9710.924503] Call Trace:
[ 9710.924503]  [<ffffffff8069b839>] _spin_lock+0x9/0x10
[ 9710.924503]  [<ffffffff803362d3>] smaps_pte_range+0x73/0x220
[ 9710.924503]  [<ffffffff802d1e5a>] walk_pmd_range+0x10a/0x1d0
[ 9710.924503]  [<ffffffff802d2050>] walk_pud_range+0x130/0x150
[ 9710.924503]  [<ffffffff802d21b8>] walk_page_range+0x148/0x180
[ 9710.924503]  [<ffffffff80335fd0>] show_smap+0x150/0x160
[ 9710.924503]  [<ffffffff80338d7c>] ? mm_for_maps+0x7c/0xc0
[ 9710.924503]  [<ffffffff80336260>] ? smaps_pte_range+0x0/0x220
[ 9710.924503]  [<ffffffff803044ff>] seq_read+0x24f/0x3a0
[ 9710.924503]  [<ffffffff802e8478>] vfs_read+0xc8/0x130
[ 9710.924503]  [<ffffffff802e85d0>] sys_read+0x50/0x90
[ 9710.924503]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
[ 9776.420499] BUG: soft lockup - CPU#1 stuck for 61s! [gnome-system-mo:9731]
[ 9776.420502] Modules linked in: usb_storage binfmt_misc bridge stp bnep input_polldev lp arc4 snd_hda_intel ecb pata_pcmcia snd_pcm_oss snd_mixer_oss snd_pcm iwlagn snd_seq_dummy iwlcore snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer uvcvideo snd_seq_device mac80211 pcmcia compat_ioctl32 leds_hp_disk led_class tpm_infineon psmouse snd ppdev videodev tpm video joydev serio_raw pcspkr yenta_socket rsrc_nonstatic pcmcia_core parport_pc parport usbhid iTCO_wdt iTCO_vendor_support ricoh_mmc sdhci_pci sdhci cfg80211 v4l1_compat tpm_bios intel_agp btusb output lis3lv02d soundcore nvidia(P) snd_page_alloc ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
[ 9776.420503] CPU 1:
[ 9776.420503] Modules linked in: usb_storage binfmt_misc bridge stp bnep input_polldev lp arc4 snd_hda_intel ecb pata_pcmcia snd_pcm_oss snd_mixer_oss snd_pcm iwlagn snd_seq_dummy iwlcore snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer uvcvideo snd_seq_device mac80211 pcmcia compat_ioctl32 leds_hp_disk led_class tpm_infineon psmouse snd ppdev videodev tpm video joydev serio_raw pcspkr yenta_socket rsrc_nonstatic pcmcia_core parport_pc parport usbhid iTCO_wdt iTCO_vendor_support ricoh_mmc sdhci_pci sdhci cfg80211 v4l1_compat tpm_bios intel_agp btusb output lis3lv02d soundcore nvidia(P) snd_page_alloc ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
[ 9776.420503] Pid: 9731, comm: gnome-system-mo Tainted: P      D    2.6.28-15-generic #49-Ubuntu
[ 9776.420503] RIP: 0010:[<ffffffff8022f564>]  [<ffffffff8022f564>] __ticket_spin_lock+0x14/0x20
[ 9776.420503] RSP: 0018:ffff880100fc9c28  EFLAGS: 00000297
[ 9776.420503] RAX: 0000000000009897 RBX: ffff880100fc9c28 RCX: ffff880100fc9e38
[ 9776.420503] RDX: ffffe20000000000 RSI: 00007fef83000000 RDI: ffffe2000390ed48
[ 9776.420503] RBP: ffff880100fc9c28 R08: ffff880100fc9e38 R09: 0000000000000000
[ 9776.420503] R10: ffff8801356e7130 R11: ffff8801356e7035 R12: 0000000000000246
[ 9776.420503] R13: ffffffff80911500 R14: 0000000000000000 R15: 001280d200fc9b88
[ 9776.420503] FS:  00007fbe5d5937e0(0000) GS:ffff88013f802d80(0000) knlGS:0000000000000000
[ 9776.420503] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[ 9776.420503] CR2: 0000000000b54060 CR3: 00000001006ac000 CR4: 00000000000006a0
[ 9776.420503] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 9776.420503] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 9776.420503] Call Trace:
[ 9776.420503]  [<ffffffff8069b839>] _spin_lock+0x9/0x10
[ 9776.420503]  [<ffffffff803362d3>] smaps_pte_range+0x73/0x220
[ 9776.420503]  [<ffffffff802d1e5a>] walk_pmd_range+0x10a/0x1d0
[ 9776.420503]  [<ffffffff802d2050>] walk_pud_range+0x130/0x150
[ 9776.420503]  [<ffffffff802d21b8>] walk_page_range+0x148/0x180
[ 9776.420503]  [<ffffffff80335fd0>] show_smap+0x150/0x160
[ 9776.420503]  [<ffffffff80338d7c>] ? mm_for_maps+0x7c/0xc0
[ 9776.420503]  [<ffffffff80336260>] ? smaps_pte_range+0x0/0x220
[ 9776.420503]  [<ffffffff803044ff>] seq_read+0x24f/0x3a0
[ 9776.420503]  [<ffffffff802e8478>] vfs_read+0xc8/0x130
[ 9776.420503]  [<ffffffff802e85d0>] sys_read+0x50/0x90
[ 9776.420503]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b

```

Eventually I had to do a hard reboot, as properly shutting down the system left me with a the just desktop image for a few minutes.

Does anyone know what 'java: Corrupted page table at address ...' (what is a 'page table' anyway?) and 'BUG: soft lockup - CPU#1 stuck for 61s! [gnome-system-mo:9731]' mean and whether any of the above could be related to writing to an external HDD or even faulty hardware (or just a buggy application)?

Any help or just a simple explanation of what dmesg is telling me would be very much appreciated! :)

(I'm running Jaunty with kernel 2.6.28-15)

---

### Post by RATM_Owns on 2009-08-24
These might help you:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254326](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254326)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254326](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254326)

[http://en.wikipedia.org/wiki/Page_table](http://en.wikipedia.org/wiki/Page_table)

---

### Post by pveurshout on 2009-08-28
Thanks for your reply. In the bug report you suggested I read about running memtest to see if it's a memory-related problem, which I'll do later today. Actually the system just froze again shortly after -but not immediately upon- starting Vuze (I didn't start any other applications in between) - only this time it froze entirely and after a hard reboot (it ran a file system check and found+corrected a file system error, by the way, this is something I had never encountered before after forced hard reboots) there was nothing in the logs except for the usual boot-stuff.

I guess I'll start keeping some sort of log myself to see if there's any relation between system freezes and using certain applications, because although I can't remember exactly, I think it has been Vuze/java related every time so far. I'll be back if I find anything, for now thanks for your help!

---

