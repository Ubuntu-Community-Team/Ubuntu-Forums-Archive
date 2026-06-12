---
title: "system freezes"
date: 2009-09-15
forum: General Help
---

### Post by dadim on 2009-09-15
Hi everybody,
can please some help me. My system freezes up regularly. I'm running Karmic on a Pentium Duo with system data on a flash drive and user data on an ethernet NAS.

Prior to the crash the "messages" section in the Log file viewer repeatedly mentions key words like refrigerator, vfs, filesystem and do_sync. I suspect, that the connection to my NAS is broken, but then how can that happen?

Below is a small section of my log file.

Any help is highly appreciated.

Thank you,
Stefan


Sep 15 18:38:01 lianli kernel: [24570.444570] Call Trace:
Sep 15 18:38:01 lianli kernel: [24570.444572]  [<ffffffff8107b64d>] refrigerator+0xfd/0x160
Sep 15 18:38:01 lianli kernel: [24570.444575]  [<ffffffff8106a787>] get_signal_to_deliver+0x57/0x3b0
Sep 15 18:38:01 lianli kernel: [24570.444577]  [<ffffffff810119a0>] do_signal+0x70/0x1c0
Sep 15 18:38:01 lianli kernel: [24570.444580]  [<ffffffff81128ddd>] ? vfs_ioctl+0x1d/0xa0
Sep 15 18:38:01 lianli kernel: [24570.444582]  [<ffffffff8127328a>] ? __up_read+0x9a/0xc0
Sep 15 18:38:01 lianli kernel: [24570.444585]  [<ffffffff81129409>] ? do_vfs_ioctl+0x79/0x370
Sep 15 18:38:01 lianli kernel: [24570.444587]  [<ffffffff81077f79>] ? up_read+0x9/0x10
Sep 15 18:38:01 lianli kernel: [24570.444590]  [<ffffffff81011b28>] do_notify_resume+0x38/0x40
Sep 15 18:38:01 lianli kernel: [24570.444592]  [<ffffffff810120bb>] sysret_signal+0x7e/0xcf
Sep 15 18:38:01 lianli kernel: [24570.444594] console-kit-d D 00000000ffffffff     0  2321      1 0x00000000
Sep 15 18:38:01 lianli kernel: [24570.444597]  ffff880129d25dc8 0000000000000082 00000000fffffdfe 0000000000015580
Sep 15 18:38:01 lianli kernel: [24570.444600]  ffff880129d283b0 0000000000015580 0000000000015580 0000000000015580
Sep 15 18:38:01 lianli kernel: [24570.444603]  0000000000015580 ffff880129d283b0 0000000000015580 0000000000015580
Sep 15 18:38:01 lianli kernel: [24570.444606] Call Trace:
Sep 15 18:38:01 lianli kernel: [24570.444609]  [<ffffffff8107b64d>] refrigerator+0xfd/0x160
Sep 15 18:38:01 lianli kernel: [24570.444611]  [<ffffffff8106a787>] get_signal_to_deliver+0x57/0x3b0
Sep 15 18:38:01 lianli kernel: [24570.444614]  [<ffffffff810119a0>] do_signal+0x70/0x1c0
Sep 15 18:38:01 lianli kernel: [24570.444616]  [<ffffffff81128ddd>] ? vfs_ioctl+0x1d/0xa0
Sep 15 18:38:01 lianli kernel: [24570.444619]  [<ffffffff8127328a>] ? __up_read+0x9a/0xc0
Sep 15 18:38:01 lianli kernel: [24570.444621]  [<ffffffff81129409>] ? do_vfs_ioctl+0x79/0x370
Sep 15 18:38:01 lianli kernel: [24570.444623]  [<ffffffff81077f79>] ? up_read+0x9/0x10
Sep 15 18:38:01 lianli kernel: [24570.444626]  [<ffffffff81011b28>] do_notify_resume+0x38/0x40
Sep 15 18:38:01 lianli kernel: [24570.444629]  [<ffffffff810120bb>] sysret_signal+0x7e/0xcf
Sep 15 18:38:01 lianli kernel: [24570.444630] console-kit-d D 00000000ffffffff     0  2322      1 0x00000000
Sep 15 18:38:01 lianli kernel: [24570.444633]  ffff880129d27dc8 0000000000000082 00000000fffffdfe 0000000000015580
Sep 15 18:38:01 lianli kernel: [24570.444637]  ffff880129d29a60 0000000000015580 0000000000015580 0000000000015580
Sep 15 18:38:01 lianli kernel: [24570.444639]  0000000000015580 ffff880129d29a60 0000000000015580 0000000000015580
Sep 15 18:38:01 lianli kernel: [24570.444642] Call Trace:
Sep 15 18:38:01 lianli kernel: [24570.444645]  [<ffffffff8107b64d>] refrigerator+0xfd/0x160
Sep 15 18:38:01 lianli kernel: [24570.444647]  [<ffffffff8106a787>] get_signal_to_deliver+0x57/0x3b0
Sep 15 18:38:01 lianli kernel: [24570.444650]  [<ffffffff810119a0>] do_signal+0x70/0x1c0
Sep 15 18:38:01 lianli kernel: [24570.444653]  [<ffffffff81128ddd>] ? vfs_ioctl+0x1d/0xa0
Sep 15 18:38:01 lianli kernel: [24570.444655]  [<ffffffff8127328a>] ? __up_read+0x9a/0xc0
Sep 15 18:38:01 lianli kernel: [24570.444657]  [<ffffffff81129409>] ? do_vfs_ioctl+0x79/0x370
Sep 15 18:38:01 lianli kernel: [24570.444660]  [<ffffffff81077f79>] ? up_read+0x9/0x10
Sep 15 18:38:01 lianli kernel: [24570.444663]  [<ffffffff81011b28>] do_notify_resume+0x38/0x40
Sep 15 18:38:01 lianli kernel: [24570.444665]  [<ffffffff810120bb>] sysret_signal+0x7e/0xcf

---

### Post by dadim on 2009-09-15
Oh. I just saw that ubuntu informed me of having a serious kernel error. So this was probably the wrong forum anyway. Looks more like an error related to the alpha stage of this OS.

Never mind. Stefan

---

