---
title: "Can't suspend or hibernate for a second time because of udisks-daemon"
date: 2011-07-14
forum: General Help
---

### Post by lampak on 2011-07-14
When I try to suspend or hibernate my computer for the first time since a boot up, everything goes fine. But if I try to do this again it fails. I get an error message *Freezing of tasks failed after 20.01 seconds (1 tasks refusing to freeze, wq_busy=0)* and then it goes straight to the unlock screen, as if I had just resumed from suspension. /var/log/syslog contains the following log, which suggests the task refusing to freeze is **udisks-daemon**. 

> Jul 14 19:24:02 laptop kernel: [26240.298517] PM: Preparing system for mem sleep
Jul 14 19:24:22 laptop kernel: [26240.552426] Freezing user space processes ... 
[B]Jul 14 19:24:22 laptop kernel: [26260.568035] Freezing of tasks failed after 20.01 seconds (1 tasks refusing to freeze, wq_busy=0):
Jul 14 19:24:22 laptop kernel: [26260.568147] udisks-daemon   D 810af5cb     0  1299   1295 0x00800004[/B]
Jul 14 19:24:22 laptop kernel: [26260.568153]  ece97c48 00000086 f7006920 810af5cb 000017d0 0001a829 ece9828c c183a8c0
Jul 14 19:24:22 laptop kernel: [26260.568160]  80fbf20b 000017d0 ece98288 c183a8c0 c183a8c0 f70068c0 ece98000 f3079940
Jul 14 19:24:22 laptop kernel: [26260.568167]  00000001 4cd27560 ece84a00 00000000 ece97c98 c1507bfd 000772d6 f133d2b4
Jul 14 19:24:22 laptop kernel: [26260.568175] Call Trace:
Jul 14 19:24:22 laptop kernel: [26260.568188]  [<c1507bfd>] ? schedule+0x3ad/0x740
Jul 14 19:24:22 laptop kernel: [26260.568192]  [<c15085cd>] schedule_timeout+0x1ed/0x260
Jul 14 19:24:22 laptop kernel: [26260.568198]  [<c10385c2>] ? check_preempt_curr+0x72/0x90
Jul 14 19:24:22 laptop kernel: [26260.568203]  [<c1049f53>] ? try_to_wake_up+0x223/0x3c0
Jul 14 19:24:22 laptop kernel: [26260.568207]  [<c1508150>] wait_for_common+0xa0/0x130
Jul 14 19:24:22 laptop kernel: [26260.568211]  [<c104a124>] ? wake_up_process+0x14/0x20
Jul 14 19:24:22 laptop kernel: [26260.568214]  [<c104a0f0>] ? default_wake_function+0x0/0x20
Jul 14 19:24:22 laptop kernel: [26260.568218]  [<c15082b7>] wait_for_completion+0x17/0x20
Jul 14 19:24:22 laptop kernel: [26260.568224]  [<c1068100>] flush_work+0x30/0x40
Jul 14 19:24:22 laptop kernel: [26260.568228]  [<c10666d0>] ? wq_barrier_func+0x0/0x20
Jul 14 19:24:22 laptop kernel: [26260.568231]  [<c10697eb>] flush_delayed_work+0x3b/0x40
Jul 14 19:24:22 laptop kernel: [26260.568236]  [<c12653a5>] disk_clear_events+0x75/0x120
Jul 14 19:24:22 laptop kernel: [26260.568241]  [<c1153b7d>] check_disk_change+0x2d/0x70
Jul 14 19:24:22 laptop kernel: [26260.568246]  [<c139cb80>] cdrom_open+0x30/0x1c0
Jul 14 19:24:22 laptop kernel: [26260.568251]  [<c1273012>] ? kobject_get+0x12/0x20
Jul 14 19:24:22 laptop kernel: [26260.568255]  [<c1263b78>] ? get_disk+0x48/0xa0
Jul 14 19:24:22 laptop kernel: [26260.568259]  [<c1273012>] ? kobject_get+0x12/0x20
Jul 14 19:24:22 laptop kernel: [26260.568264]  [<c1330c08>] ? get_device+0x18/0x20
Jul 14 19:24:22 laptop kernel: [26260.568269]  [<c1351b23>] ? scsi_device_get+0x43/0xa0
Jul 14 19:24:22 laptop kernel: [26260.568274]  [<c1367fa7>] sr_block_open+0x67/0xb0
Jul 14 19:24:22 laptop kernel: [26260.568278]  [<c1154e3e>] __blkdev_get+0x8e/0x330
Jul 14 19:24:22 laptop kernel: [26260.568281]  [<c11551cf>] blkdev_get+0xef/0x230
Jul 14 19:24:22 laptop kernel: [26260.568285]  [<c1155368>] blkdev_open+0x58/0x70
Jul 14 19:24:22 laptop kernel: [26260.568289]  [<c1125361>] __dentry_open+0xc1/0x280
Jul 14 19:24:22 laptop kernel: [26260.568292]  [<c11266ce>] nameidata_to_filp+0x6e/0x80
Jul 14 19:24:22 laptop kernel: [26260.568296]  [<c1155310>] ? blkdev_open+0x0/0x70
Jul 14 19:24:22 laptop kernel: [26260.568300]  [<c1133b7f>] finish_open+0xaf/0x1a0
Jul 14 19:24:22 laptop kernel: [26260.568303]  [<c1133428>] ? do_path_lookup+0x68/0x120
Jul 14 19:24:22 laptop kernel: [26260.568307]  [<c11341c7>] do_filp_open+0x207/0x6e0
Jul 14 19:24:22 laptop kernel: [26260.568311]  [<c1351ad7>] ? scsi_device_put+0x47/0x50
Jul 14 19:24:22 laptop kernel: [26260.568327]  [<c1002a31>] ? do_signal+0x61/0x120
Jul 14 19:24:22 laptop kernel: [26260.568332]  [<c113fee9>] ? vfsmount_lock_local_unlock+0x19/0x20
Jul 14 19:24:22 laptop kernel: [26260.568336]  [<c1126736>] do_sys_open+0x56/0x120
Jul 14 19:24:22 laptop kernel: [26260.568339]  [<c112682e>] sys_open+0x2e/0x40
Jul 14 19:24:22 laptop kernel: [26260.568343]  [<c150a194>] syscall_call+0x7/0xb
Jul 14 19:24:22 laptop kernel: [26260.568347]  [<c1500000>] ? detect_ht+0x14f/0x16d
Jul 14 19:24:22 laptop kernel: [26260.568425] 
Jul 14 19:24:22 laptop rtkit-daemon[1256]: The canary thread is apparently starving. Taking action.
Jul 14 19:24:22 laptop rtkit-daemon[1256]: Demoting known real-time threads.
Jul 14 19:24:22 laptop rtkit-daemon[1256]: Successfully demoted thread 1956 of process 1954 (n/a).
Jul 14 19:24:22 laptop rtkit-daemon[1256]: Successfully demoted thread 1955 of process 1954 (n/a).
Jul 14 19:24:22 laptop rtkit-daemon[1256]: Successfully demoted thread 1954 of process 1954 (n/a).
Jul 14 19:24:22 laptop rtkit-daemon[1256]: Demoted 3 threads.
Jul 14 19:24:22 laptop kernel: [26260.568426] Restarting tasks ... done.
Jul 14 19:24:22 laptop acpid: client 2110[0:0] has disconnected
Jul 14 19:24:22 laptop acpid: client connected from 2110[0:0]
Jul 14 19:24:22 laptop acpid: 1 client rule loaded
Jul 14 19:24:22 laptop kernel: [26260.588395] video LNXVIDEO:00: Restoring backlight state

After I restart the system I can do one suspension or hibernation again - but only one. 

I've done a bit of googling and it seems to be a common symptom but it can be caused by many different tasks. I haven't found a solution for udisks-daemon. Do you know one?

---

