---
title: "need help with memmap"
date: 2010-08-24
forum: General Help
---

### Post by Chris1274 on 2010-08-24
I've posted a lot lately on my "low memory corruption" problems:
```
Aug 21 23:04:43 Aedificium kernel: [   61.160801] Corrupted low memory at ffff880000006598 (6598 phys) = df0000000000

Aug 21 23:04:43 Aedificium kernel: [   61.160855] ------------[ cut here ]------------

Aug 21 23:04:43 Aedificium kernel: [   61.160864] WARNING: at /home/kernel-ppa/mainline/build/arch/x86/kernel/check.c:134 check_for_bios_corruption+0xea/0x100()

Aug 21 23:04:43 Aedificium kernel: [   61.160868] Hardware name: HP Pavilion dv6 Notebook PC

Aug 21 23:04:43 Aedificium kernel: [   61.160870] Memory corruption detected in low memory

Aug 21 23:04:43 Aedificium kernel: [   61.160872] Modules linked in: binfmt_misc ppdev dm_crypt snd_hda_codec_atihdmi snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi arc4 snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device uvcvideo snd videodev soundcore iwlagn snd_page_alloc iwlcore psmouse v4l1_compat serio_raw v4l2_compat_ioctl32 mac80211 joydev cfg80211 hp_accel lp lis3lv02d parport input_polldev led_class hp_wmi usbhid hid fbcon tileblit font bitblit softcursor radeon i915 ttm r8169 drm_kms_helper intel_agp mii video output drm i2c_algo_bit ahci

Aug 21 23:04:43 Aedificium kernel: [   61.160928] Pid: 15, comm: events/0 Not tainted 2.6.34-020634-generic #020634

Aug 21 23:04:43 Aedificium kernel: [   61.160931] Call Trace:

Aug 21 23:04:43 Aedificium kernel: [   61.160937]  [<ffffffff8103402a>] ? check_for_bios_corruption+0xea/0x100

Aug 21 23:04:43 Aedificium kernel: [   61.160943]  [<ffffffff8105f1dc>] warn_slowpath_common+0x8c/0xc0

Aug 21 23:04:43 Aedificium kernel: [   61.160947]  [<ffffffff8105f299>] warn_slowpath_fmt+0x69/0x70

Aug 21 23:04:43 Aedificium kernel: [   61.160953]  [<ffffffff81340bf0>] ? vt_console_print+0x0/0x300

Aug 21 23:04:43 Aedificium kernel: [   61.160960]  [<ffffffff8100985b>] ? __switch_to+0xbb/0x2e0

Aug 21 23:04:43 Aedificium kernel: [   61.160965]  [<ffffffff8105118e>] ? put_prev_entity+0x2e/0x80

Aug 21 23:04:43 Aedificium kernel: [   61.160969]  [<ffffffff81051af6>] ? finish_task_switch+0x66/0xd0

Aug 21 23:04:43 Aedificium kernel: [   61.160973]  [<ffffffff8103402a>] check_for_bios_corruption+0xea/0x100

Aug 21 23:04:43 Aedificium kernel: [   61.160977]  [<ffffffff81034040>] ? check_corruption+0x0/0x40

Aug 21 23:04:43 Aedificium kernel: [   61.160981]  [<ffffffff8103404e>] check_corruption+0xe/0x40

Aug 21 23:04:43 Aedificium kernel: [   61.160985]  [<ffffffff8107a0fc>] run_workqueue+0xbc/0x190

Aug 21 23:04:43 Aedificium kernel: [   61.160990]  [<ffffffff8107ab4b>] worker_thread+0x9b/0x100

Aug 21 23:04:43 Aedificium kernel: [   61.160995]  [<ffffffff8107edb0>] ? autoremove_wake_function+0x0/0x40

Aug 21 23:04:43 Aedificium kernel: [   61.160998]  [<ffffffff8107aab0>] ? worker_thread+0x0/0x100

Aug 21 23:04:43 Aedificium kernel: [   61.161001]  [<ffffffff8107e9d6>] kthread+0x96/0xa0

Aug 21 23:04:43 Aedificium kernel: [   61.161005]  [<ffffffff8100be64>] kernel_thread_helper+0x4/0x10

Aug 21 23:04:43 Aedificium kernel: [   61.161009]  [<ffffffff8107e940>] ? kthread+0x0/0xa0

Aug 21 23:04:43 Aedificium kernel: [   61.161012]  [<ffffffff8100be60>] ? kernel_thread_helper+0x0/0x10

Aug 21 23:04:43 Aedificium kernel: [   61.161015] ---[ end trace 547f4e85f025df69 ]---
```

What seems to be happening is the BIOs is corrupting the first 64K of physical memory, for God only knows what reason. So a possible solution is to use memmap to mark off that segment as "reserved" so that the kernel doesn't try to use it.

The problem is I'm not sure how memmap works. Is there anyone who might be able to offer some help?

---

### Post by naugtur on 2010-10-25
I've just found it for myself. Not tested if it works with Lucid

See here:
[http://gquigs.blogspot.com/2009/01/bad-memory-howto.html](http://gquigs.blogspot.com/2009/01/bad-memory-howto.html)

---

