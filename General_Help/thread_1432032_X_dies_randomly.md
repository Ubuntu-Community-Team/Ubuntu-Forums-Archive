---
title: "X dies randomly"
date: 2010-03-17
forum: General Help
---

### Post by jojo786 on 2010-03-17
Hi,

I am running 9.10 on a HP Compaq. Every few days X will die. The screen goes blank and will not display anything. I have to SSH in, but even trying various commands like gdm restart does not help. I eventually have to reboot the box. Below is a snippet (hopefully not too large) of dmesg:

/dev/sr0 on /media/cdrom0 is a CDROM, but I dont think thats the issue.

[707515.629800] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[707515.629806] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[707515.629811] Info fld=0x45d18, ILI
[707515.629813] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[707515.629819] end_request: I/O error, dev sr0, sector 1143904
[707515.629823] Buffer I/O error on device sr0, logical block 142988
[707515.636287] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[707515.636291] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[707515.636295] Info fld=0x45d18, ILI
[707515.636297] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[707515.636302] end_request: I/O error, dev sr0, sector 1143904
[707515.636305] Buffer I/O error on device sr0, logical block 142988
[707515.641559] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[707515.641563] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[707515.641567] Info fld=0x45d18, ILI
[707515.641569] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[707515.641574] end_request: I/O error, dev sr0, sector 1143904
[707515.641576] Buffer I/O error on device sr0, logical block 142988
[707515.648698] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[707515.648702] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[707515.648706] Info fld=0x45d18, ILI
[707515.648708] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[707515.648713] end_request: I/O error, dev sr0, sector 1143904
[707515.648716] Buffer I/O error on device sr0, logical block 142988
[707515.654883] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[707515.654887] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[707515.654891] Info fld=0x45d18, ILI
[707515.654893] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[707515.654898] end_request: I/O error, dev sr0, sector 1143904
[707515.654901] Buffer I/O error on device sr0, logical block 142988
[707515.661257] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[707515.661261] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[707515.661266] Info fld=0x45d18, ILI
[707515.661267] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[707515.661273] end_request: I/O error, dev sr0, sector 1143904
[707515.661276] Buffer I/O error on device sr0, logical block 142988
[707515.666600] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 142988
[707517.983966] UDF-fs: No VRS found
[707517.983970] UDF-fs: No partition found (1)
[707518.007202] ISO 9660 Extensions: Microsoft Joliet Level 3
[707518.010345] ISOFS: changing to secondary root
[709591.832474] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[709592.194704] i2c-adapter i2c-1: unable to read EDID block.
[709592.194707] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[709592.199446] i2c-adapter i2c-1: unable to read EDID block.
[709592.199448] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[709592.510298] i2c-adapter i2c-1: unable to read EDID block.
[709592.510301] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[709592.514957] i2c-adapter i2c-1: unable to read EDID block.
[709592.514958] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[723600.504521] INFO: task i915/0:337 blocked for more than 120 seconds.
[723600.504524] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[723600.504527] i915/0        D c08145c0     0   337      2 0x00000000
[723600.504532]  f6b15f04 00000046 f6bd0cbc c08145c0 f6bd0f28 c08145c0 094edc7f 000291e8
[723600.504539]  c08145c0 c08145c0 f6bd0f28 c08145c0 094ed5fe 000291e8 c08145c0 e66e5180
[723600.504545]  f6bd0c90 f655dc14 f655dc18 ffffffff f6b15f30 c056fe76 f6919920 f655dc1c
[723600.504551] Call Trace:
[723600.504559]  [<c056fe76>] __mutex_lock_slowpath+0xc6/0x130
[723600.504562]  [<c056fd90>] mutex_lock+0x20/0x40
[723600.504582]  [<f840ac0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
[723600.504587]  [<c015794e>] run_workqueue+0x6e/0x140
[723600.504601]  [<f840abe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
[723600.504605]  [<c0157aa8>] worker_thread+0x88/0xe0
[723600.504609]  [<c015c0f0>] ? autoremove_wake_function+0x0/0x40
[723600.504613]  [<c0157a20>] ? worker_thread+0x0/0xe0
[723600.504616]  [<c015bdfc>] kthread+0x7c/0x90
[723600.504619]  [<c015bd80>] ? kthread+0x0/0x90
[723600.504623]  [<c0104007>] kernel_thread_helper+0x7/0x10
[723720.504521] INFO: task i915/0:337 blocked for more than 120 seconds.
[723720.504525] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[723720.504528] i915/0        D c08145c0     0   337      2 0x00000000
[723720.504533]  f6b15f04 00000046 f6bd0cbc c08145c0 f6bd0f28 c08145c0 094edc7f 000291e8
[723720.504540]  c08145c0 c08145c0 f6bd0f28 c08145c0 094ed5fe 000291e8 c08145c0 e66e5180
[723720.504546]  f6bd0c90 f655dc14 f655dc18 ffffffff f6b15f30 c056fe76 f6919920 f655dc1c
[723720.504552] Call Trace:
[723720.504560]  [<c056fe76>] __mutex_lock_slowpath+0xc6/0x130
[723720.504563]  [<c056fd90>] mutex_lock+0x20/0x40
[723720.504583]  [<f840ac0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
[723720.504589]  [<c015794e>] run_workqueue+0x6e/0x140
[723720.504602]  [<f840abe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
[723720.504606]  [<c0157aa8>] worker_thread+0x88/0xe0
[723720.504610]  [<c015c0f0>] ? autoremove_wake_function+0x0/0x40
[723720.504614]  [<c0157a20>] ? worker_thread+0x0/0xe0
[723720.504617]  [<c015bdfc>] kthread+0x7c/0x90
[723720.504620]  [<c015bd80>] ? kthread+0x0/0x90
[723720.504624]  [<c0104007>] kernel_thread_helper+0x7/0x10
[723840.504520] INFO: task i915/0:337 blocked for more than 120 seconds.
[723840.504523] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[723840.504526] i915/0        D c08145c0     0   337      2 0x00000000
[723840.504531]  f6b15f04 00000046 f6bd0cbc c08145c0 f6bd0f28 c08145c0 094edc7f 000291e8
[723840.504538]  c08145c0 c08145c0 f6bd0f28 c08145c0 094ed5fe 000291e8 c08145c0 e66e5180
[723840.504544]  f6bd0c90 f655dc14 f655dc18 ffffffff f6b15f30 c056fe76 f6919920 f655dc1c
[723840.504550] Call Trace:
[723840.504557]  [<c056fe76>] __mutex_lock_slowpath+0xc6/0x130
[723840.504561]  [<c056fd90>] mutex_lock+0x20/0x40
[723840.504581]  [<f840ac0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
[723840.504586]  [<c015794e>] run_workqueue+0x6e/0x140
[723840.504599]  [<f840abe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
[723840.504603]  [<c0157aa8>] worker_thread+0x88/0xe0
[723840.504607]  [<c015c0f0>] ? autoremove_wake_function+0x0/0x40
[723840.504611]  [<c0157a20>] ? worker_thread+0x0/0xe0
[723840.504614]  [<c015bdfc>] kthread+0x7c/0x90
[723840.504617]  [<c015bd80>] ? kthread+0x0/0x90
[723840.504621]  [<c0104007>] kernel_thread_helper+0x7/0x10
[723960.504521] INFO: task i915/0:337 blocked for more than 120 seconds.
[723960.504524] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[723960.504527] i915/0        D c08145c0     0   337      2 0x00000000
[723960.504532]  f6b15f04 00000046 f6bd0cbc c08145c0 f6bd0f28 c08145c0 094edc7f 000291e8
[723960.504538]  c08145c0 c08145c0 f6bd0f28 c08145c0 094ed5fe 000291e8 c08145c0 e66e5180
[723960.504545]  f6bd0c90 f655dc14 f655dc18 ffffffff f6b15f30 c056fe76 f6919920 f655dc1c
[723960.504551] Call Trace:
[723960.504559]  [<c056fe76>] __mutex_lock_slowpath+0xc6/0x130
[723960.504562]  [<c056fd90>] mutex_lock+0x20/0x40
[723960.504583]  [<f840ac0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
[723960.504587]  [<c015794e>] run_workqueue+0x6e/0x140
[723960.504601]  [<f840abe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
[723960.504605]  [<c0157aa8>] worker_thread+0x88/0xe0
[723960.504609]  [<c015c0f0>] ? autoremove_wake_function+0x0/0x40
[723960.504613]  [<c0157a20>] ? worker_thread+0x0/0xe0
[723960.504616]  [<c015bdfc>] kthread+0x7c/0x90
[723960.504619]  [<c015bd80>] ? kthread+0x0/0x90
[723960.504623]  [<c0104007>] kernel_thread_helper+0x7/0x10
[724080.504520] INFO: task i915/0:337 blocked for more than 120 seconds.
[724080.504523] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[724080.504526] i915/0        D c08145c0     0   337      2 0x00000000
[724080.504531]  f6b15f04 00000046 f6bd0cbc c08145c0 f6bd0f28 c08145c0 094edc7f 000291e8
[724080.504538]  c08145c0 c08145c0 f6bd0f28 c08145c0 094ed5fe 000291e8 c08145c0 e66e5180
[724080.504544]  f6bd0c90 f655dc14 f655dc18 ffffffff f6b15f30 c056fe76 f6919920 f655dc1c
[724080.504550] Call Trace:
[724080.504558]  [<c056fe76>] __mutex_lock_slowpath+0xc6/0x130
[724080.504561]  [<c056fd90>] mutex_lock+0x20/0x40
[724080.504581]  [<f840ac0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
[724080.504586]  [<c015794e>] run_workqueue+0x6e/0x140
[724080.504599]  [<f840abe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
[724080.504603]  [<c0157aa8>] worker_thread+0x88/0xe0
[724080.504607]  [<c015c0f0>] ? autoremove_wake_function+0x0/0x40
[724080.504611]  [<c0157a20>] ? worker_thread+0x0/0xe0
[724080.504614]  [<c015bdfc>] kthread+0x7c/0x90
[724080.504617]  [<c015bd80>] ? kthread+0x0/0x90
[724080.504621]  [<c0104007>] kernel_thread_helper+0x7/0x10
[724200.504520] INFO: task i915/0:337 blocked for more than 120 seconds.
[724200.504523] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[724200.504526] i915/0        D c08145c0     0   337      2 0x00000000
[724200.504531]  f6b15f04 00000046 f6bd0cbc c08145c0 f6bd0f28 c08145c0 094edc7f 000291e8
[724200.504538]  c08145c0 c08145c0 f6bd0f28 c08145c0 094ed5fe 000291e8 c08145c0 e66e5180
[724200.504544]  f6bd0c90 f655dc14 f655dc18 ffffffff f6b15f30 c056fe76 f6919920 f655dc1c
[724200.504550] Call Trace:
[724200.504557]  [<c056fe76>] __mutex_lock_slowpath+0xc6/0x130
[724200.504561]  [<c056fd90>] mutex_lock+0x20/0x40
[724200.504581]  [<f840ac0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
[724200.504586]  [<c015794e>] run_workqueue+0x6e/0x140
[724200.504599]  [<f840abe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
[724200.504603]  [<c0157aa8>] worker_thread+0x88/0xe0
[724200.504607]  [<c015c0f0>] ? autoremove_wake_function+0x0/0x40
[724200.504611]  [<c0157a20>] ? worker_thread+0x0/0xe0
[724200.504614]  [<c015bdfc>] kthread+0x7c/0x90
[724200.504617]  [<c015bd80>] ? kthread+0x0/0x90
[724200.504621]  [<c0104007>] kernel_thread_helper+0x7/0x10
[724320.504520] INFO: task i915/0:337 blocked for more than 120 seconds.
[724320.504524] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[724320.504526] i915/0        D c08145c0     0   337      2 0x00000000
[724320.504531]  f6b15f04 00000046 f6bd0cbc c08145c0 f6bd0f28 c08145c0 094edc7f 000291e8
[724320.504538]  c08145c0 c08145c0 f6bd0f28 c08145c0 094ed5fe 000291e8 c08145c0 e66e5180
[724320.504545]  f6bd0c90 f655dc14 f655dc18 ffffffff f6b15f30 c056fe76 f6919920 f655dc1c
[724320.504551] Call Trace:
[724320.504559]  [<c056fe76>] __mutex_lock_slowpath+0xc6/0x130
[724320.504562]  [<c056fd90>] mutex_lock+0x20/0x40
[724320.504582]  [<f840ac0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
[724320.504587]  [<c015794e>] run_workqueue+0x6e/0x140
[724320.504600]  [<f840abe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
[724320.504605]  [<c0157aa8>] worker_thread+0x88/0xe0
[724320.504609]  [<c015c0f0>] ? autoremove_wake_function+0x0/0x40
[724320.504612]  [<c0157a20>] ? worker_thread+0x0/0xe0
[724320.504615]  [<c015bdfc>] kthread+0x7c/0x90
[724320.504619]  [<c015bd80>] ? kthread+0x0/0x90
[724320.504622]  [<c0104007>] kernel_thread_helper+0x7/0x10
[724440.504520] INFO: task i915/0:337 blocked for more than 120 seconds.
[724440.504524] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[724440.504527] i915/0        D c08145c0     0   337      2 0x00000000
[724440.504531]  f6b15f04 00000046 f6bd0cbc c08145c0 f6bd0f28 c08145c0 094edc7f 000291e8
[724440.504538]  c08145c0 c08145c0 f6bd0f28 c08145c0 094ed5fe 000291e8 c08145c0 e66e5180
[724440.504545]  f6bd0c90 f655dc14 f655dc18 ffffffff f6b15f30 c056fe76 f6919920 f655dc1c
[724440.504551] Call Trace:
[724440.504558]  [<c056fe76>] __mutex_lock_slowpath+0xc6/0x130
[724440.504562]  [<c056fd90>] mutex_lock+0x20/0x40
[724440.504582]  [<f840ac0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
[724440.504587]  [<c015794e>] run_workqueue+0x6e/0x140
[724440.504600]  [<f840abe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
[724440.504604]  [<c0157aa8>] worker_thread+0x88/0xe0
[724440.504608]  [<c015c0f0>] ? autoremove_wake_function+0x0/0x40
[724440.504612]  [<c0157a20>] ? worker_thread+0x0/0xe0
[724440.504615]  [<c015bdfc>] kthread+0x7c/0x90
[724440.504618]  [<c015bd80>] ? kthread+0x0/0x90
[724440.504622]  [<c0104007>] kernel_thread_helper+0x7/0x10
[724560.504519] INFO: task i915/0:337 blocked for more than 120 seconds.
[724560.504523] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[724560.504526] i915/0        D c08145c0     0   337      2 0x00000000
[724560.504531]  f6b15f04 00000046 f6bd0cbc c08145c0 f6bd0f28 c08145c0 094edc7f 000291e8
[724560.504537]  c08145c0 c08145c0 f6bd0f28 c08145c0 094ed5fe 000291e8 c08145c0 e66e5180
[724560.504544]  f6bd0c90 f655dc14 f655dc18 ffffffff f6b15f30 c056fe76 f6919920 f655dc1c
[724560.504550] Call Trace:
[724560.504557]  [<c056fe76>] __mutex_lock_slowpath+0xc6/0x130
[724560.504561]  [<c056fd90>] mutex_lock+0x20/0x40
[724560.504580]  [<f840ac0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
[724560.504585]  [<c015794e>] run_workqueue+0x6e/0x140
[724560.504599]  [<f840abe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
[724560.504603]  [<c0157aa8>] worker_thread+0x88/0xe0
[724560.504607]  [<c015c0f0>] ? autoremove_wake_function+0x0/0x40
[724560.504610]  [<c0157a20>] ? worker_thread+0x0/0xe0
[724560.504614]  [<c015bdfc>] kthread+0x7c/0x90
[724560.504617]  [<c015bd80>] ? kthread+0x0/0x90
[724560.504620]  [<c0104007>] kernel_thread_helper+0x7/0x10
[724680.504520] INFO: task i915/0:337 blocked for more than 120 seconds.
[724680.504524] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[724680.504527] i915/0        D c08145c0     0   337      2 0x00000000
[724680.504531]  f6b15f04 00000046 f6bd0cbc c08145c0 f6bd0f28 c08145c0 094edc7f 000291e8
[724680.504538]  c08145c0 c08145c0 f6bd0f28 c08145c0 094ed5fe 000291e8 c08145c0 e66e5180
[724680.504545]  f6bd0c90 f655dc14 f655dc18 ffffffff f6b15f30 c056fe76 f6919920 f655dc1c
[724680.504551] Call Trace:
[724680.504558]  [<c056fe76>] __mutex_lock_slowpath+0xc6/0x130
[724680.504562]  [<c056fd90>] mutex_lock+0x20/0x40
[724680.504582]  [<f840ac0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
[724680.504587]  [<c015794e>] run_workqueue+0x6e/0x140
[724680.504600]  [<f840abe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
[724680.504604]  [<c0157aa8>] worker_thread+0x88/0xe0
[724680.504608]  [<c015c0f0>] ? autoremove_wake_function+0x0/0x40
[724680.504612]  [<c0157a20>] ? worker_thread+0x0/0xe0
[724680.504615]  [<c015bdfc>] kthread+0x7c/0x90
[724680.504618]  [<c015bd80>] ? kthread+0x0/0x90
[724680.504622]  [<c0104007>] kernel_thread_helper+0x7/0x10

---

### Post by yusufk on 2010-03-17
You sure the log is around the time of a crash? Doesn't seem to have anything significant in there?

Have you monitored your memory usage over a week? Is there perhaps a memory leak?

---

### Post by yusufk on 2010-03-17
Except maybe for this:
[709591.832474] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[709592.194704] i2c-adapter i2c-1: unable to read EDID block.
[709592.194707] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[709592.199446] i2c-adapter i2c-1: unable to read EDID block.
[709592.199448] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[709592.510298] i2c-adapter i2c-1: unable to read EDID block.
[709592.510301] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[709592.514957] i2c-adapter i2c-1: unable to read EDID block.
[709592.514958] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[723600.504521] INFO: task i915/0:337 blocked for more than 120 seconds.

Intel i915 ?

Seems to be struggling with HDMI or something.

---

### Post by aeiah on 2010-03-17
yea, i noticed the HDMI stuff too. your EDID is binary data your TV provides. you can request no EDID, or provide your own EDID file. you should be able to dump the EDID from the tv or monitor too, and provide it locally from the hard drive at all times.

you should really post your xorg error log file though. its hard to wade through that dmesg with all the cdrom errors going on (cdrom errors are fairly common, its probably just a crap disk you have in there)

---

