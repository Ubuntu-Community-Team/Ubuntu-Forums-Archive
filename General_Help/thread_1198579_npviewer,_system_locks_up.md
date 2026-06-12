---
title: "npviewer, system locks up"
date: 2009-06-27
forum: General Help
---

### Post by Per Olav on 2009-06-27
Ubuntu 9.04, 64bit, flash content on webpage causes system to lock up.. 

Jun 27 22:29:57 t500 kernel: [  152.563328] npviewer.bin[4113] general protection ip:f019d805 sp:fff51450 error:0 in libmurrine.so[f018e000+20000]
Jun 27 22:30:11 t500 kernel: [  166.980410] npviewer.bin[4140]: segfault at 6aac7340 ip 00000000f3c9a039 sp 00000000fff357ec error 4 in libmurrine.so[f3c8$
Jun 27 22:30:11 t500 kernel: [  167.473236] npviewer.bin[4314] general protection ip:f3ca0031 sp:fff0b7bc error:0 in libmurrine.so[f3c90000+20000]
Jun 27 22:31:35 t500 kernel: [  250.704657] general protection fault: 0000 [#1] SMP
Jun 27 22:31:35 t500 kernel: [  250.704667] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/rfkill/rfkill2/state
Jun 27 22:31:35 t500 kernel: [  250.704674] Dumping ftrace buffer:
Jun 27 22:31:35 t500 kernel: [  250.704679]    (ftrace buffer empty)
Jun 27 22:31:35 t500 kernel: [  250.704683] CPU 1
Jun 27 22:31:35 t500 kernel: [  250.704686] Modules linked in: binfmt_misc ppdev bridge stp bnep input_polldev joydev lp parport snd_hda_intel snd_pcm_oss$
Jun 27 22:31:35 t500 kernel: [  250.704794] Pid: 4330, comm: npviewer.bin Tainted: P           2.6.28-13-generic #44-Ubuntu
Jun 27 22:31:35 t500 kernel: [  250.704799] RIP: 0010:[<ffffffff802e236c>]  [<ffffffff802e236c>] kmem_cache_alloc+0x5c/0xc0
Jun 27 22:31:35 t500 kernel: [  250.704814] RSP: 0018:ffff880118c93d48  EFLAGS: 00010082
Jun 27 22:31:35 t500 kernel: [  250.704818] RAX: 0000000000000000 RBX: fd08f7954a03a8ae RCX: ffff880118c93e38
Jun 27 22:31:35 t500 kernel: [  250.704823] RDX: ffff88002803e020 RSI: 00000000000080d0 RDI: 00000000000000c0
Jun 27 22:31:35 t500 kernel: [  250.704827] RBP: ffff880118c93d78 R08: 0000000000000001 R09: 00000000ff9096bc
Jun 27 22:31:35 t500 kernel: [  250.704832] R10: ffff880118c92000 R11: 0000000000000000 R12: 0000000000000286
Jun 27 22:31:35 t500 kernel: [  250.704836] R13: ffffffff809aa9d0 R14: ffffffff802e8cf6 R15: 00000000000080d0
Jun 27 22:31:35 t500 kernel: [  250.704842] FS:  0000000000000000(0000) GS:ffff88013b802e00(0063) knlGS:00000000f7245750
Jun 27 22:31:35 t500 kernel: [  250.704847] CS:  0010 DS: 002b ES: 002b CR0: 0000000080050033
Jun 27 22:31:35 t500 kernel: [  250.704851] CR2: 00000000f7ed9000 CR3: 0000000115025000 CR4: 00000000000406a0
Jun 27 22:31:35 t500 kernel: [  250.704856] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 27 22:31:35 t500 kernel: [  250.704860] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun 27 22:31:35 t500 kernel: [  250.704866] Process npviewer.bin (pid: 4330, threadinfo ffff880118c92000, task ffff880126c34320)
Jun 27 22:31:35 t500 kernel: [  250.704870] Stack:
Jun 27 22:31:35 t500 kernel: [  250.704873]  000000c018c93d68 ffff880118c93e38 0000000000000001 00000000ffffffe9
Jun 27 22:31:35 t500 kernel: [  250.704881]  0000000000000001 ffff8801150f2000 ffff880118c93d98 ffffffff802e8cf6
Jun 27 22:31:35 t500 kernel: [  250.704890]  ffff880118c93e38 0000000000000001 ffff880118c93dd8 ffffffff802f3bf6

---

