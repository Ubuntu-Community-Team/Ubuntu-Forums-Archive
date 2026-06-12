---
title: "What does this log message mean - check_for_bios_corruption"
date: 2011-04-06
forum: General Help
---

### Post by b.schelberg on 2011-04-06
Can anyone tell me what this log message means?
```
Apr  7 07:32:41 Morpheus kernel: [   62.526874] ------------[ cut here ]------------
Apr  7 07:32:41 Morpheus kernel: [   62.526887] WARNING: at /build/buildd/linux-2.6.35/arch/x86/kernel/check.c:134 check_for_bios_corruption+0xe5/0xf0()
Apr  7 07:32:41 Morpheus kernel: [   62.526893] Hardware name: HP Pavilion dv6 Notebook PC
Apr  7 07:32:41 Morpheus kernel: [   62.526900] Modules linked in: rfcomm binfmt_misc sco bnep l2cap vboxnetadp vboxnetflt vboxdrv kvm_intel kvm parport_pc ppdev snd_hda_codec_atihdmi snd_hda_codec_idt arc4 snd_seq_midi snd_rawmidi ath9k snd_hda_intel ath9k_common ath9k_hw snd_seq_midi_event snd_hda_codec snd_seq joydev i7core_edac btusb ath mac80211 snd_hwdep cdc_ether snd_pcm cdc_subset uvcvideo bluetooth hp_wmi usbnet snd_seq_device videodev snd_timer v4l1_compat v4l2_compat_ioctl32 cfg80211 fglrx(P) snd psmouse soundcore serio_raw edac_core video snd_page_alloc hp_accel lis3lv02d input_polldev led_class output lp parport usbhid hid r8169 ahci mii libahci nbd
Apr  7 07:32:41 Morpheus kernel: [   62.526943] Pid: 30, comm: events/3 Tainted: P            2.6.35-28-generic #49-Ubuntu
Apr  7 07:32:41 Morpheus kernel: [   62.526945] Call Trace:
Apr  7 07:32:41 Morpheus kernel: [   62.526950]  [<ffffffff81060b7f>] warn_slowpath_common+0x7f/0xc0
Apr  7 07:32:41 Morpheus kernel: [   62.526953]  [<ffffffff81060c76>] warn_slowpath_fmt+0x46/0x50
Apr  7 07:32:41 Morpheus kernel: [   62.526955]  [<ffffffff81037095>] check_for_bios_corruption+0xe5/0xf0
Apr  7 07:32:41 Morpheus kernel: [   62.526958]  [<ffffffff810370a0>] ? check_corruption+0x0/0x40
Apr  7 07:32:41 Morpheus kernel: [   62.526960]  [<ffffffff810370ae>] check_corruption+0xe/0x40
Apr  7 07:32:41 Morpheus kernel: [   62.526963]  [<ffffffff8107ac05>] run_workqueue+0xc5/0x1a0
Apr  7 07:32:41 Morpheus kernel: [   62.526965]  [<ffffffff8107ad83>] worker_thread+0xa3/0x110
Apr  7 07:32:41 Morpheus kernel: [   62.526968]  [<ffffffff8107fab0>] ? autoremove_wake_function+0x0/0x40
Apr  7 07:32:41 Morpheus kernel: [   62.526971]  [<ffffffff8107ace0>] ? worker_thread+0x0/0x110
Apr  7 07:32:41 Morpheus kernel: [   62.526973]  [<ffffffff8107f556>] kthread+0x96/0xa0
Apr  7 07:32:41 Morpheus kernel: [   62.526976]  [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
Apr  7 07:32:41 Morpheus kernel: [   62.526978]  [<ffffffff8107f4c0>] ? kthread+0x0/0xa0
Apr  7 07:32:41 Morpheus kernel: [   62.526980]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
Apr  7 07:32:41 Morpheus kernel: [   62.526981] ---[ end trace ae946e39c80d205b ]---
```

Thanks,
Bernie

---

