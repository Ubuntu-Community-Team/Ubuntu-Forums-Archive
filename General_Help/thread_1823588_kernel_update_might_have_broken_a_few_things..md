---
title: "kernel update might have broken a few things."
date: 2011-08-12
forum: General Help
---

### Post by mandarke on 2011-08-12
updated to the latest kernel earlier on today (2.6.35-30-generic #57-Ubuntu SMP Tue Aug 9 17:59:24 UTC 2011) and now google chrome seems to be broken:

Aug 12 18:41:35 acer8730 kernel: [  167.207996] input input4: event field not found
Aug 12 18:41:37 acer8730 kernel: [  169.630732] input input4: event field not found
Aug 12 18:42:29 acer8730 kernel: [  221.870285] lo: Disabled Privacy Extensions
Aug 12 18:43:29 acer8730 kernel: [  281.956095] BUG: unable to handle kernel paging request at fffffffffffffff3
Aug 12 18:43:29 acer8730 kernel: [  281.956100] IP: [<ffffffff811ab2d9>] vma_stop+0x19/0x40
Aug 12 18:43:29 acer8730 kernel: [  281.956109] PGD 1a2c067 PUD 1a2d067 PMD 0 
Aug 12 18:43:29 acer8730 kernel: [  281.956113] Oops: 0000 [#2] SMP 
Aug 12 18:43:29 acer8730 kernel: [  281.956116] last sysfs file: /sys/devices/virtual/backlight/acpi_video0/uevent
Aug 12 18:43:29 acer8730 kernel: [  281.956120] CPU 1 
Aug 12 18:43:29 acer8730 kernel: [  281.956121] Modules linked in: binfmt_misc parport_pc ppdev joydev nvidia(P) snd_hda_codec_nvhdmi snd_hda_codec_realtek arc4 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq iwlagn iwlcore mac80211 snd_timer snd_seq_device cfg80211 acer_wmi snd led_class uvcvideo videodev v4l1_compat v4l2_compat_ioctl32 psmouse video serio_raw soundcore output snd_page_alloc intel_agp lp parport usbhid hid usb_storage ahci libahci tg3
Aug 12 18:43:29 acer8730 kernel: [  281.956155] 
Aug 12 18:43:29 acer8730 kernel: [  281.956159] Pid: 1907, comm: chrome Tainted: P      D     2.6.35-30-generic #57-Ubuntu BigBear2                       /Aspire 8730                    
Aug 12 18:43:29 acer8730 kernel: [  281.956162] RIP: 0010:[<ffffffff811ab2d9>]  [<ffffffff811ab2d9>] vma_stop+0x19/0x40
Aug 12 18:43:29 acer8730 kernel: [  281.956167] RSP: 0018:ffff88011e055e38  EFLAGS: 00010213
Aug 12 18:43:29 acer8730 kernel: [  281.956169] RAX: 00000000fffffff3 RBX: ffff8801159d12a0 RCX: 0000000000000013
Aug 12 18:43:29 acer8730 kernel: [  281.956171] RDX: ffffffff8161e180 RSI: fffffffffffffff3 RDI: ffff8801159d12a0
Aug 12 18:43:29 acer8730 kernel: [  281.956174] RBP: ffff88011e055e48 R08: 00000000000000d0 R09: ffff88013fc30000
Aug 12 18:43:29 acer8730 kernel: [  281.956176] R10: 0000000000000022 R11: 0000000000000293 R12: ffff8801243f5240
Aug 12 18:43:29 acer8730 kernel: [  281.956179] R13: fffffffffffffff3 R14: 0000000000010000 R15: ffff88011e055eb0
Aug 12 18:43:29 acer8730 kernel: [  281.956182] FS:  00007fb32a8a3700(0000) GS:ffff880001f00000(0000) knlGS:0000000000000000
Aug 12 18:43:29 acer8730 kernel: [  281.956184] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 12 18:43:29 acer8730 kernel: [  281.956187] CR2: fffffffffffffff3 CR3: 0000000122ad7000 CR4: 00000000000406e0
Aug 12 18:43:29 acer8730 kernel: [  281.956189] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 12 18:43:29 acer8730 kernel: [  281.956192] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 12 18:43:29 acer8730 kernel: [  281.956195] Process chrome (pid: 1907, threadinfo ffff88011e054000, task ffff880122b72de0)
Aug 12 18:43:29 acer8730 kernel: [  281.956197] Stack:
Aug 12 18:43:29 acer8730 kernel: [  281.956198]  0000000000000022 ffff8801159d12a0 ffff88011e055e68 ffffffff811ab38a
Aug 12 18:43:29 acer8730 kernel: [  281.956202] <0> 0000000000010000 ffff88011e313880 ffff88011e055ee8 ffffffff81174260
Aug 12 18:43:29 acer8730 kernel: [  281.956206] <0> 00000000fffffff3 00007fb32a8920f0 ffff88011e3138b8 ffff88011e055f48
Aug 12 18:43:29 acer8730 kernel: [  281.956211] Call Trace:
Aug 12 18:43:29 acer8730 kernel: [  281.956216]  [<ffffffff811ab38a>] m_stop+0x1a/0x40
Aug 12 18:43:29 acer8730 kernel: [  281.956220]  [<ffffffff81174260>] seq_read+0x1d0/0x410
Aug 12 18:43:29 acer8730 kernel: [  281.956225]  [<ffffffff81155275>] vfs_read+0xb5/0x1a0
Aug 12 18:43:29 acer8730 kernel: [  281.956228]  [<ffffffff811553b1>] sys_read+0x51/0x80
Aug 12 18:43:29 acer8730 kernel: [  281.956233]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
Aug 12 18:43:29 acer8730 kernel: [  281.956235] Code: c9 90 c3 eb 0d 90 90 90 90 90 90 90 90 90 90 90 90 90 55 48 89 e5 53 48 83 ec 08 0f 1f 44 00 00 48 85 f6 74 1a 48 39 77 10 74 14 <48> 8b 1e 48 8d 7b 68 e8 7b 9f ed ff 48 89 df e8 73 3f eb ff 48 
Aug 12 18:43:29 acer8730 kernel: [  281.956269] RIP  [<ffffffff811ab2d9>] vma_stop+0x19/0x40
Aug 12 18:43:29 acer8730 kernel: [  281.956273]  RSP <ffff88011e055e38>
Aug 12 18:43:29 acer8730 kernel: [  281.956275] CR2: fffffffffffffff3
Aug 12 18:43:29 acer8730 kernel: [  281.956278] ---[ end trace 211604e16b5c8bf9 ]---

so i tried using gnome-system-monitor to shut it down and got:


Aug 12 18:54:39 acer8730 kernel: [  951.644102] BUG: unable to handle kernel paging request at fffffffffffffff3
Aug 12 18:54:39 acer8730 kernel: [  951.644107] IP: [<ffffffff811ab2d9>] vma_stop+0x19/0x40
Aug 12 18:54:39 acer8730 kernel: [  951.644114] PGD 1a2c067 PUD 1a2d067 PMD 0 
Aug 12 18:54:39 acer8730 kernel: [  951.644118] Oops: 0000 [#4] SMP 
Aug 12 18:54:39 acer8730 kernel: [  951.644122] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0/statistics/collisions
Aug 12 18:54:39 acer8730 kernel: [  951.644125] CPU 1 
Aug 12 18:54:39 acer8730 kernel: [  951.644127] Modules linked in: binfmt_misc parport_pc ppdev joydev nvidia(P) snd_hda_codec_nvhdmi snd_hda_codec_realtek arc4 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq iwlagn iwlcore mac80211 snd_timer snd_seq_device cfg80211 acer_wmi snd led_class uvcvideo videodev v4l1_compat v4l2_compat_ioctl32 psmouse video serio_raw soundcore output snd_page_alloc intel_agp lp parport usbhid hid usb_storage ahci libahci tg3
Aug 12 18:54:39 acer8730 kernel: [  951.644161] 
Aug 12 18:54:39 acer8730 kernel: [  951.644164] Pid: 2307, comm: gnome-system-mo Tainted: P      D     2.6.35-30-generic #57-Ubuntu BigBear2                       /Aspire 8730                    
Aug 12 18:54:39 acer8730 kernel: [  951.644167] RIP: 0010:[<ffffffff811ab2d9>]  [<ffffffff811ab2d9>] vma_stop+0x19/0x40
Aug 12 18:54:39 acer8730 kernel: [  951.644172] RSP: 0018:ffff88011e399e38  EFLAGS: 00010213
Aug 12 18:54:39 acer8730 kernel: [  951.644174] RAX: 00000000fffffff3 RBX: ffff880139f73260 RCX: 0000000000000013
Aug 12 18:54:39 acer8730 kernel: [  951.644177] RDX: ffffffff8161e180 RSI: fffffffffffffff3 RDI: ffff880139f73260
Aug 12 18:54:39 acer8730 kernel: [  951.644179] RBP: ffff88011e399e48 R08: 00000000000000d0 R09: ffff88013fc30000
Aug 12 18:54:39 acer8730 kernel: [  951.644182] R10: 0000000000000022 R11: 0000000000000293 R12: ffff880115969840
Aug 12 18:54:39 acer8730 kernel: [  951.644184] R13: fffffffffffffff3 R14: 0000000000000000 R15: ffff88011e399eb0
Aug 12 18:54:39 acer8730 kernel: [  951.644187] FS:  00007fba3a77e940(0000) GS:ffff880001f00000(0000) knlGS:0000000000000000
Aug 12 18:54:39 acer8730 kernel: [  951.644190] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 12 18:54:39 acer8730 kernel: [  951.644192] CR2: fffffffffffffff3 CR3: 000000012cc38000 CR4: 00000000000406e0
Aug 12 18:54:39 acer8730 kernel: [  951.644195] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 12 18:54:39 acer8730 kernel: [  951.644197] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 12 18:54:39 acer8730 kernel: [  951.644200] Process gnome-system-mo (pid: 2307, threadinfo ffff88011e398000, task ffff8801229b5bc0)
Aug 12 18:54:39 acer8730 kernel: [  951.644202] Stack:
Aug 12 18:54:39 acer8730 kernel: [  951.644203]  0000000000000022 ffff880139f73260 ffff88011e399e68 ffffffff811ab38a
Aug 12 18:54:39 acer8730 kernel: [  951.644208] <0> 0000000000000000 ffff88012bef9200 ffff88011e399ee8 ffffffff81174260
Aug 12 18:54:39 acer8730 kernel: [  951.644212] <0> 00000000fffffff3 00007fba3a79c000 ffff88012bef9238 ffff88011e399f48
Aug 12 18:54:39 acer8730 kernel: [  951.644217] Call Trace:
Aug 12 18:54:39 acer8730 kernel: [  951.644221]  [<ffffffff811ab38a>] m_stop+0x1a/0x40
Aug 12 18:54:39 acer8730 kernel: [  951.644226]  [<ffffffff81174260>] seq_read+0x1d0/0x410
Aug 12 18:54:39 acer8730 kernel: [  951.644230]  [<ffffffff81155275>] vfs_read+0xb5/0x1a0
Aug 12 18:54:39 acer8730 kernel: [  951.644233]  [<ffffffff811553b1>] sys_read+0x51/0x80
Aug 12 18:54:39 acer8730 kernel: [  951.644238]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
Aug 12 18:54:39 acer8730 kernel: [  951.644240] Code: c9 90 c3 eb 0d 90 90 90 90 90 90 90 90 90 90 90 90 90 55 48 89 e5 53 48 83 ec 08 0f 1f 44 00 00 48 85 f6 74 1a 48 39 77 10 74 14 <48> 8b 1e 48 8d 7b 68 e8 7b 9f ed ff 48 89 df e8 73 3f eb ff 48 
Aug 12 18:54:39 acer8730 kernel: [  951.644275] RIP  [<ffffffff811ab2d9>] vma_stop+0x19/0x40
Aug 12 18:54:39 acer8730 kernel: [  951.644279]  RSP <ffff88011e399e38>
Aug 12 18:54:39 acer8730 kernel: [  951.644280] CR2: fffffffffffffff3
Aug 12 18:54:39 acer8730 kernel: [  951.644283] ---[ end trace 211604e16b5c8bfb ]---

am i doing something wrong?

---

### Post by RedRonin on 2011-08-13
I'm not sure if it was the Kernel update or not for me... I updated the Kernel, restarted the system, then updated Chrome [13.0.782.112] as well.  Now Chrome crashes when attempting to open sites it used to have no problem with...  It times out on the slightest form request... It can't seem to run any plugins at all...  

Meanwhile, Chromium [13.0.782.107 (Developer Build 94237 Linux)] and Firefox [3.6.18] both work just fine.  Of course, I think I am still using the same versions of those that were in place prior to the Kernel update.  

There is also the fact I am running Ubuntu 10.10 instead of 11.04 too... Maybe Chrome would have been fine if I moved to Natty Narwhal?
 :confused: 

Red Ronin

---

### Post by mandarke on 2011-08-14
i'm running 10.10 also. i updated my google chrome to 13 prior the kernel update and all seemed fine except for firefox 5 (from the stable ppa) taking a very long time to open sites that chrome used to be able to open (without having cached files, etc) in an instant.

would you mind pasting your kern.log either here or on pastebin?

---

### Post by jakewc2 on 2011-08-16
I am having similar problems, and I just created a launchpad bug #827198 and just wondered, it needs to be confirmed by people and more information added if people have any more.....would be good if somebody could confirm the more the better......thanks

jakewc2

---

### Post by mandarke on 2011-08-16
> **jakewc2 said:**
> I am having similar problems, and I just created a launchpad bug #827198 and just wondered, it needs to be confirmed by people and more information added if people have any more.....would be good if somebody could confirm the more the better......thanks

jakewc2

done.

i've also filed a report which can be found here #825660

---

