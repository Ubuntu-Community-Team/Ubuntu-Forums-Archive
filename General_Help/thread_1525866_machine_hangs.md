---
title: "machine hangs"
date: 2010-07-07
forum: General Help
---

### Post by ub007 on 2010-07-07
Hi,

My server hangs during a read operation. I've attached the Sysrq trace of all processes running at that time. Can someone have a squint & shed some light on whats causing the issue here.

Apologies for the lengthy spew :(

> SysRq : Show State

                                               sibling
  task             PC      pid father child younger older
init          S 00000014   760     1      0     2               (NOTLB)
       f7c0bf50 00000082 cdede207 00000014 925de982 00000014 00000002 00000007 
       f7c0aaa0 cdee44c8 00000014 000062c1 00000001 f7c0abac c34794c4 f7d66c80 
       00000000 f7c0bf24 00000004 ffffffff f7c0aaa0 ffffffff c3479980 ffffffff 
Call Trace:
 [<c042815a>] do_wait+0x9bf/0xac1
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0428283>] sys_wait4+0x27/0x2a
 [<c0428299>] sys_waitpid+0x13/0x17
 [<c0404f17>] syscall_call+0x7/0xb
 =======================
migration/0   S 0000A245  3676     2      1             3       (L-TLB)
       f7c14fac 00000046 1f3c2733 0000a245 c3480308 c04202df 0005da6e 00000001 
       f7c12550 1f3c2abd 0000a245 0000038a 00000000 f7c1265c c3472680 f52d5ac0 
       c3472b3c 00000000 c3472f64 c3472f64 00000460 c3480e68 c3472680 ffffffff 
Call Trace:
 [<c04202df>] move_tasks+0x26b/0x30f
 [<c0422920>] migration_thread+0x151/0x1d3
 [<c04227cf>] migration_thread+0x0/0x1d3
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
ksoftirqd/0   S 0000A24A  3696     3      1             4     2 (L-TLB)
       f7c16fc0 00000046 f7e17bdc 0000a24a f7f23aa0 7c70cac3 00008521 0000000a 
       f7c12000 f7e1aa3e 0000a24a 00002e62 00000000 f7c1210c c3472680 f7962740 
       02d35480 00000000 c3472b3c 00000000 c0745000 0000007b 00000000 ffffffff 
Call Trace:
 [<c042a643>] ksoftirqd+0x0/0xd9
 [<c042a68f>] ksoftirqd+0x4c/0xd9
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
watchdog/0    S 0000A251  3696     4      1             5     3 (L-TLB)
       f7c18fc0 00000046 3058c33e 0000a251 00000000 00000200 00000000 00000001 
       f7c17aa0 3058c44c 0000a251 0000010e 00000000 f7c17bac c3472680 f52d5ac0 
       00000000 00000000 00000000 f7c0bf58 c044cb62 00000000 c3472b3c ffffffff 
Call Trace:
 [<c044cb62>] watchdog+0x0/0x5a
 [<c044cb62>] watchdog+0x0/0x5a
 [<c044cbad>] watchdog+0x4b/0x5a
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
migration/1   S 0000A0C2  3676     5      1             6     4 (L-TLB)
       f7c19fac 00000046 028cd89a 0000a0c2 c3472680 c04202df 00069840 00000001 
       f7c17550 028ce32a 0000a0c2 00000a90 00000001 f7c1765c c34794c4 f7bf1900 
       c3479980 c34726c4 c3479db0 c3479db0 00000460 c3473100 c3479980 c3472680 
Call Trace:
 [<c04202df>] move_tasks+0x26b/0x30f
 [<c04228e3>] migration_thread+0x114/0x1d3
 [<c0422920>] migration_thread+0x151/0x1d3
 [<c04227cf>] migration_thread+0x0/0x1d3
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
ksoftirqd/1   S 0000A239  3680     6      1             7     5 (L-TLB)
       c35e2fc0 00000046 96e67de7 0000a239 f7f23aa0 46c8e16f 0000a0cb 0000000a 
       f7c17000 96e68019 0000a239 00000232 00000001 f7c1710c c34794c4 f7bf13c0 
       c34794c4 00000000 c3479980 c35e2fc0 00000000 0000007b 00000001 ffffffff 
Call Trace:
 [<c042a643>] ksoftirqd+0x0/0xd9
 [<c042a68f>] ksoftirqd+0x4c/0xd9
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
watchdog/1    S 0000A251  3696     7      1             8     6 (L-TLB)
       c35e4fc0 00000046 38ac89f5 0000a251 00000000 00000200 00000000 00000009 
       c35e3aa0 38ac8b07 0000a251 00000112 00000001 c35e3bac c34794c4 f7bf13c0 
       00000000 00000000 00000000 c35e4000 c35e3aa0 f7c0bf34 c3479980 ffffffff 
Call Trace:
 [<c044cb62>] watchdog+0x0/0x5a
 [<c044cbad>] watchdog+0x4b/0x5a
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
migration/2   S 00007D9A  3676     8      1             9     7 (L-TLB)
       c35e5fac 00000046 0a7bf732 00007d9a c348714c c04202df 00069840 00000001 
       c35e3550 0a7c0d25 00007d9a 000015f3 00000002 c35e365c c3480308 f7da0c80 
       c348034c c3487608 c3480714 c3480714 00000400 c3487bcc c348034c c348714c 
Call Trace:
 [<c04202df>] move_tasks+0x26b/0x30f
 [<c04228e3>] migration_thread+0x114/0x1d3
 [<c0422920>] migration_thread+0x151/0x1d3
 [<c04227cf>] migration_thread+0x0/0x1d3
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
ksoftirqd/2   S 000087EB  3680     9      1            10     8 (L-TLB)
       c35edfc0 00000046 aee1a839 000087eb e395daa0 45c3d838 000077fc 00000008 
       c35e3000 aee1b028 000087eb 000007ef 00000002 c35e310c c3480308 c3660040 
       02d43108 00000000 00000000 00000000 c0747000 0000007b c34807c4 ffffffff 
Call Trace:
 [<c042a643>] ksoftirqd+0x0/0xd9
 [<c042a68f>] ksoftirqd+0x4c/0xd9
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
watchdog/2    S 0000A1F2  3696    10      1            11     9 (L-TLB)
       c35effc0 00000046 c1644b8d 0000a1f2 00000000 00000200 00000000 00000009 
       c35eeaa0 c1644eb6 0000a1f2 00000329 00000002 c35eebac c3480308 f72b8e40 
       00000002 00000000 00000000 c35ef000 c35eeaa0 f7c0bf34 c348034c ffffffff 
Call Trace:
 [<c044cb62>] watchdog+0x0/0x5a
 [<c044cbad>] watchdog+0x4b/0x5a
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
migration/3   S 00008007  3676    11      1            12    10 (L-TLB)
       c35f0fac 00000046 e50ebd00 00008007 c3480308 c04202df 00069840 00000001 
       c35ee550 e50ed0f1 00008007 000013f1 00000003 c35ee65c c348714c f7da0c80 
       c3487608 c348034c c34879d0 c34879d0 00000400 c3480d88 c3487608 c3480308 
Call Trace:
 [<c04202df>] move_tasks+0x26b/0x30f
 [<c04228e3>] migration_thread+0x114/0x1d3
 [<c0422920>] migration_thread+0x151/0x1d3
 [<c04227cf>] migration_thread+0x0/0x1d3
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
ksoftirqd/3   S 0000A24E  3668    12      1            13    11 (L-TLB)
       c35f7fc0 00000046 6aa0b406 0000a24e f7f23aa0 0d916d3b 000077e4 00000006 
       c35ee000 6aa0b89a 0000a24e 00000494 00000003 c35ee10c c348714c c3660040 
       02d49f4c 00000000 00000000 00000000 c0748000 0000007b c3487608 ffffffff 
Call Trace:
 [<c042a643>] ksoftirqd+0x0/0xd9
 [<c042a68f>] ksoftirqd+0x4c/0xd9
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
watchdog/3    S 0000A251  3696    13      1            14    12 (L-TLB)
       c35fafc0 00000046 48ac991b 0000a251 00000000 00000200 00000000 00000009 
       c35f9aa0 48ac9ae8 0000a251 000001cd 00000003 c35f9bac c348714c f7bf13c0 
       00000246 00000000 00000000 00000246 c0421063 c35fafc8 c3487608 ffffffff 
Call Trace:
 [<c0421063>] sched_setscheduler+0x1fa/0x217
 [<c044cb62>] watchdog+0x0/0x5a
 [<c044cbad>] watchdog+0x4b/0x5a
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
events/0      S 0000A251  3640    14      1            15    13 (L-TLB)
       f7feff88 00000046 1f282b82 0000a251 c363e8c0 e6ad3040 00000003 0000000a 
       c35f9550 1f286402 0000a251 00003880 00000000 c35f965c c3472680 f52d5ac0 
       00000003 00000082 c3473a00 c3473a04 c35ea640 00000082 c3472b3c f7feffa4 
Call Trace:
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
events/1      R running  3012    15      1            16    14 (L-TLB)
       f7fedf88 00000046 2c2ee41b 0000a251 c35f5ad4 00000005 00000003 0000000a 
       c35f9000 2c2f5b4e 0000a251 00007733 00000001 c35f910c c34794c4 f7bf13c0 
       00000003 00000000 c347a844 c347a848 c35ea440 00000082 c043368e ffffffff 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
events/2      S 0000A251  3624    16      1            17    15 (L-TLB)
       f7febf88 00000046 6fa2461c 0000a251 c35ece14 00000008 00000003 0000000a 
       f7fecaa0 6fa29172 0000a251 00004b56 00000002 f7fecbac c3480308 f72b8e40 
       00000003 00000000 c3481688 c348168c c35ea7c0 00000082 c043368e ffffffff 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
events/3      S 0000A251  2988    17      1            18    16 (L-TLB)
       f7feaf88 00000046 578b57f7 0000a251 c35f4014 00000018 00000003 0000000a 
       f7fec550 578c03e9 0000a251 0000abf2 00000003 f7fec65c c348714c f7bf13c0 
       00000003 00000000 c34884cc c34884d0 c35ea740 00000082 c043368e ffffffff 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
khelper       S 00000012  3356    18      1            19    17 (L-TLB)
       f7fe8f88 00000046 c658194b 00000012 00000000 00000000 00000003 0000000a 
       f7fec000 c65829f1 00000012 000010a6 00000001 f7fec10c c34794c4 c3660c80 
       00000003 00000082 f5494dd8 f5494ddc c35ea5c0 00000082 c043368e f7fe8fa4 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
kthread       S 00000021  3412    19      1    25     918    18 (L-TLB)
       f7fdbf88 00000046 ff46c1af 00000021 00000000 00000003 00000003 0000000a 
       f7fdcaa0 ff46d045 00000021 00000e96 00000000 f7fdcbac c3472680 f7d66740 
       00000003 00000000 f50abc8c f50abc90 f7fdd7c0 00000082 c043368e ffffffff 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
kblockd/0     S 000084FB  3008    25     19            26       (L-TLB)
       f7fa9f88 00000046 4a5dd764 000084fb 00000000 00000000 00000003 00000001 
       f7faaaa0 4a5de734 000084fb 00000fd0 00000000 f7faabac c3472680 f7da0c80 
       00000003 00000000 f7d63108 f7d6310c f7fc2d40 00000082 c043368e ffffffff 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
kblockd/1     S 0000A0CB  2940    26     19            27    25 (L-TLB)
       f7fa8f88 00000046 466377a1 0000a0cb f7d637e4 f6dea000 00000003 0000000a 
       f7faa550 46639a52 0000a0cb 000022b1 00000001 f7faa65c c34794c4 f52d5740 
       00000003 00000082 f6dea0b0 f6dea0b4 f7fc2cc0 00000082 c3479980 f7fa8fa4 
Call Trace:
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
kblockd/2     S 0000A0C2  2940    27     19            28    26 (L-TLB)
       f7fa7f88 00000046 01b7aa0c 0000a0c2 00000000 f6dc7000 00000003 0000000a 
       f7faa000 01b7c1e9 0000a0c2 000017dd 00000002 f7faa10c c3480308 f55d1200 
       00000003 00000082 f6dea0b0 f6dea0b4 f7fc2c40 00000082 c34807c4 f7fa7fa4 
Call Trace:
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
kblockd/3     S 0000851B  2932    28     19            29    27 (L-TLB)
       f7fa5f88 00000046 10390d49 0000851b 00000000 00000000 00000003 0000000a 
       f7fa6aa0 103927cb 0000851b 00001a82 00000003 f7fa6bac c348714c f52d5740 
       00000003 00000082 f7d63108 f7d6310c f7fc2bc0 00000082 c3487608 f7fa5fa4 
Call Trace:
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
kacpid        S 00000000  3636    29     19           169    28 (L-TLB)
       f7fa0f88 00000046 17152aa1 00000000 c34794c4 f7fc2940 00000003 00000003 
       f7fa6550 17153054 00000000 000005b3 00000000 f7fa665c c3472680 c0689200 
       00000003 00000000 f7fa2e80 f7fa2e84 f7fc2940 00000082 c043368e ffffffff 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
cqueue/0      S 00000000  3768   169     19           170    29 (L-TLB)
       f7fcaf88 00000046 192366fd 00000000 00000086 c041fbc9 00000000 00000003 
       f7fcd000 192369fd 00000000 00000300 00000000 f7fcd10c c3472680 c0689200 
       f7fcafc8 c061bad8 f7fcd000 00000011 f7fa4184 c042f92c c34726c4 f7fcafa4 
Call Trace:
 [<c041fbc9>] try_to_wake_up+0x3e8/0x3f2
 [<c061bad8>] schedule+0x9cc/0xa55
 [<c042f92c>] recalc_sigpending_and_wake+0x8/0x18
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
cqueue/1      S 00000000  3640   170     19           171   169 (L-TLB)
       f7fcbf88 00000046 19238f72 00000000 00000086 c041fbc9 00000000 00000001 
       f7fcd550 192396fe 00000000 0000078c 00000001 f7fcd65c c34794c4 c0689200 
       f7fcbfc8 00000000 f7fcd550 00000011 f7f3ec04 c042f92c f7fcd550 ffffffff 
Call Trace:
 [<c041fbc9>] try_to_wake_up+0x3e8/0x3f2
 [<c042f92c>] recalc_sigpending_and_wake+0x8/0x18
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
cqueue/2      S 00000000  3640   171     19           172   170 (L-TLB)
       f7fcef88 00000046 1923afe2 00000000 00000086 c041fbc9 00000000 00000001 
       f7fcdaa0 1923b960 00000000 0000097e 00000002 f7fcdbac c3480308 c0689200 
       f7fcefc8 00000000 f7fcdaa0 00000011 f7f3e6c4 c042f92c f7fcdaa0 ffffffff 
Call Trace:
 [<c041fbc9>] try_to_wake_up+0x3e8/0x3f2
 [<c042f92c>] recalc_sigpending_and_wake+0x8/0x18
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
cqueue/3      S 00000000  3640   172     19           175   171 (L-TLB)
       f7fcff88 00000046 1923cd19 00000000 00000086 c041fbc9 00000000 0000000a 
       f7fdc000 1923d5d4 00000000 000008bb 00000003 f7fdc10c c348714c c0689200 
       f7fcffc8 00000000 f7fdc000 00000011 f7f3e184 c042f92c f7fdc000 ffffffff 
Call Trace:
 [<c041fbc9>] try_to_wake_up+0x3e8/0x3f2
 [<c042f92c>] recalc_sigpending_and_wake+0x8/0x18
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
khubd         S 00000000  2740   175     19           177   172 (L-TLB)
       f7fd3f54 00000046 d4c4d5d0 00000000 c058be70 000428da 000000a3 0000000a 
       f7fdc550 d4c4d885 00000000 000002b5 00000003 f7fdc65c c348714c c3593c80 
       000000a3 00000000 00000001 f7d4c9e0 00000004 000003e8 f7fd3f9c ffffffff 
Call Trace:
 [<c058be70>] usb_control_msg+0xc5/0xcf
 [<c0589ad2>] hub_thread+0x917/0x97d
 [<c04363ff>] autoremove_wake_function+0x0/0x2d
 [<c05891bb>] hub_thread+0x0/0x97d
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
kseriod       S 00000000  3124   177     19           255   175 (L-TLB)
       c35d2fa0 00000046 bf29d144 00000000 c06aa368 c3591ee8 ffffffef 0000000a 
       f7fa6000 bf29e450 00000000 0000130c 00000003 f7fa610c c348714c c3593c80 
       c06aa368 00000000 c06aa368 c055dae8 00000028 c06b3f28 c35d2fa8 ffffffff 
Call Trace:
 [<c055dae8>] driver_create_file+0x28/0x2e
 [<c059b657>] serio_thread+0x240/0x285
 [<c04363ff>] autoremove_wake_function+0x0/0x2d
 [<c059b417>] serio_thread+0x0/0x285
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
khungtaskd    S 0000A245  3172   255     19           256   177 (L-TLB)
       c35d4f8c 00000046 e3852076 0000a245 c064030b c04262c7 c0635b01 00000004 
       f7f18aa0 e386898a 0000a245 00016914 00000003 f7f18bac c348714c f72b8900 
       00000046 00000000 00000286 c042da21 c3600000 c35d4f94 00000286 ffffffff 
Call Trace:
 [<c04262c7>] printk+0x18/0x8e
 [<c042da21>] lock_timer_base+0x15/0x2f
 [<c061c1f9>] schedule_timeout+0x71/0x8c
 [<c042d1cd>] process_timeout+0x0/0x5
 [<c044cc3b>] watchdog+0x41/0x15a
 [<c044cbfa>] watchdog+0x0/0x15a
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
pdflush       S 0000789D   816   256     19           257   255 (L-TLB)
       c35d5fa0 00000046 f68d063d 0000789d c04e1573 00000000 f7f18550 0000000a 
       f7f18550 f68d0a9d 0000789d 00000460 00000001 f7f1865c c34794c4 f7da0c80 
       00000000 00000400 00000000 00000000 00000000 00000000 00000000 00000021 
Call Trace:
 [<c04e1573>] blk_congestion_wait+0x5e/0x67
 [<c045c271>] pdflush+0x0/0x1a3
 [<c045c328>] pdflush+0xb7/0x1a3
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
pdflush       S 0000A250   972   257     19           258   256 (L-TLB)
       c35d7fa0 00000046 7b2b6f0a 0000a250 c042da21 c35dc000 c0695fa8 0000000a 
       f7f18000 7b2bcbae 0000a250 00005ca4 00000001 f7f1810c c34794c4 f7bf13c0 
       00000000 00000000 c35d7f94 00000400 00000000 00000000 00000000 ffffffff 
Call Trace:
 [<c042da21>] lock_timer_base+0x15/0x2f
 [<c045c271>] pdflush+0x0/0x1a3
 [<c045c328>] pdflush+0xb7/0x1a3
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
kswapd0       S 00008522   940   258     19           259   257 (L-TLB)
       c35d9f50 00000046 a1743f97 00008522 00000001 00000070 00000280 0000000a 
       f7f1baa0 a1835c2c 00008522 000f1c95 00000002 f7f1bbac c3480308 f7bf13c0 
       c374a760 00000000 000000d0 c045ebf7 00000000 00000000 c35d9f94 ffffffff 
Call Trace:
 [<c045ebf7>] shrink_slab+0x130/0x13c
 [<c045ed33>] kswapd+0xb4/0x3ab
 [<c04363ff>] autoremove_wake_function+0x0/0x2d
 [<c045ec7f>] kswapd+0x0/0x3ab
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
aio/0         S 00000000  3768   259     19           260   258 (L-TLB)
       f7f34f88 00000046 1a1cbdeb 00000000 00000086 c041fbc9 00000000 00000001 
       f7f1b550 1a1cc60b 00000000 00000820 00000000 f7f1b65c c3472680 c0689200 
       f7f34fc8 c061bad8 f7f1b550 00000011 f7f1cc04 c042f92c c34726c4 f7f34fa4 
Call Trace:
 [<c041fbc9>] try_to_wake_up+0x3e8/0x3f2
 [<c061bad8>] schedule+0x9cc/0xa55
 [<c042f92c>] recalc_sigpending_and_wake+0x8/0x18
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
aio/1         S 00000000  3640   260     19           261   259 (L-TLB)
       c35daf88 00000046 1a1cffdc 00000000 00000086 c041fbc9 00000000 00000001 
       f7f1b000 1a1d07ac 00000000 000007d0 00000001 f7f1b10c c34794c4 c0689200 
       c35dafc8 00000000 f7f1b000 00000011 f7f1c6c4 c042f92c f7f1b000 ffffffff 
Call Trace:
 [<c041fbc9>] try_to_wake_up+0x3e8/0x3f2
 [<c042f92c>] recalc_sigpending_and_wake+0x8/0x18
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
aio/2         S 00000000  3640   261     19           262   260 (L-TLB)
       c35dbf88 00000046 1a1d3d9e 00000000 00000086 c041fbc9 00000000 00000001 
       f7f1eaa0 1a1d4701 00000000 00000963 00000002 f7f1ebac c3480308 c0689200 
       c35dbfc8 00000000 f7f1eaa0 00000011 f7f1c184 c042f92c f7f1eaa0 ffffffff 
Call Trace:
 [<c041fbc9>] try_to_wake_up+0x3e8/0x3f2
 [<c042f92c>] recalc_sigpending_and_wake+0x8/0x18
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
aio/3         S 00000000  3640   262     19           422   261 (L-TLB)
       c3615f88 00000046 1a1f6de5 00000000 00000086 c041fbc9 00000000 00000001 
       f7f1e550 1a1f74cc 00000000 000006e7 00000003 f7f1e65c c348714c c0689200 
       c3615fc8 00000000 f7f1e550 00000011 f7f1fc04 c042f92c f7f1e550 ffffffff 
Call Trace:
 [<c041fbc9>] try_to_wake_up+0x3e8/0x3f2
 [<c042f92c>] recalc_sigpending_and_wake+0x8/0x18
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
kpsmoused     S 00000000  3640   422     19           495   262 (L-TLB)
       f7f30f88 00000046 886e6247 00000000 00000086 c041fbc9 00000000 00000008 
       f7f1e000 886e6776 00000000 0000052f 00000000 f7f1e10c c3472680 c0689200 
       f7f30fc8 00000000 f7f1e000 00000011 f7f1f6c4 c042f92c f7f1e000 ffffffff 
Call Trace:
 [<c041fbc9>] try_to_wake_up+0x3e8/0x3f2
 [<c042f92c>] recalc_sigpending_and_wake+0x8/0x18
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
scsi_eh_0     S 00000001  3648   495     19           496   422 (L-TLB)
       f7d39f90 00000046 c692d93b 00000001 00000000 f7f23550 f7f23550 00000008 
       f7f23550 c692dee5 00000001 000005aa 00000000 f7f2365c c3472680 c3593e40 
       c692c1dc 00000000 00000000 c692c476 00000001 00000008 c06893c0 ffffffff 
Call Trace:
 [<f88bb615>] scsi_error_handler+0x0/0x422 [scsi_mod]
 [<f88bb668>] scsi_error_handler+0x53/0x422 [scsi_mod]
 [<c041ef71>] complete+0x2b/0x3d
 [<f88bb615>] scsi_error_handler+0x0/0x422 [scsi_mod]
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
usb-storage   S 0000A0CB  3052   496     19           568   495 (L-TLB)
       c3623f5c 00000046 4b262d88 0000a0cb f7c17000 f7c17000 c041f2ac 0000000a 
       f7f23aa0 4b263346 0000a0cb 000005be 00000001 f7f23bac c34794c4 f7bf13c0 
       c041fbc9 0000000d d7aef800 00000400 0000001f 00000000 c3479980 00000001 
Call Trace:
 [<c041f2ac>] enqueue_task+0x29/0x39
 [<c041fbc9>] try_to_wake_up+0x3e8/0x3f2
 [<c061d054>] __down_interruptible+0xb0/0xf5
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<f88fadc0>] usb_stor_control_thread+0x0/0x190 [usb_storage]
 [<c061b0bb>] __down_failed_interruptible+0x7/0xc
 [<f88fb09d>] .text.lock.usb+0x1b/0x22 [usb_storage]
 [<c041ef71>] complete+0x2b/0x3d
 [<f88fadc0>] usb_stor_control_thread+0x0/0x190 [usb_storage]
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
rpciod/0      S 000078E6  2920   568     19           569   496 (L-TLB)
       c3663f88 00000046 bea29e42 000078e6 c0633a60 f7830544 00000003 0000000a 
       f7d22000 bea31554 000078e6 00007712 00000000 f7d2210c c3472680 f7da0c80 
       00000003 00000000 f7830540 f7830544 f6e15d40 00000082 c043368e ffffffff 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
rpciod/1      S 00007B06  2680   569     19           570   568 (L-TLB)
       c3665f88 00000046 693d1e25 00007b06 c0633a60 f7830544 00000003 0000000a 
       f7d22550 693d9314 00007b06 000074ef 00000001 f7d2265c c34794c4 f7da0c80 
       00000003 00000082 00000000 f7830544 f6e15cc0 00000082 c043368e c3665fa4 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
rpciod/2      S 00007BEF  2920   570     19           571   569 (L-TLB)
       c3667f88 00000046 e915ef40 00007bef c0633a60 f7830544 00000003 0000000a 
       f7d22aa0 e9168a96 00007bef 00009b56 00000002 f7d22bac c3480308 f7da0c80 
       00000003 00000000 f7830540 f7830544 f6e15c40 00000082 c043368e ffffffff 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
rpciod/3      S 0000A230  2920   571     19           592   570 (L-TLB)
       c361ff88 00000046 314df909 0000a230 c0633a60 f7830544 00000003 0000000a 
       f7d1a000 314e5415 0000a230 00005b0c 00000003 f7d1a10c c348714c f7d66900 
       00000003 00000000 f7830540 f7830544 f6e15bc0 00000082 c043368e ffffffff 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
xfslogd/0     S 00007C8D  3360   592     19           593   571 (L-TLB)
       f7c3bf88 00000046 24af61b5 00007c8d f7de1840 00010e00 00000003 0000000a 
       c35d8550 24af6bb8 00007c8d 00000a03 00000000 c35d865c c3472680 c3593c80 
       00000003 00000082 00000000 f6da4e28 c35aaf40 00000082 c043368e f7c3bfa4 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
xfslogd/1     S 0000A250  3472   593     19           594   592 (L-TLB)
       f7c3df88 00000046 c18f735c 0000a250 f7886cc0 00011a00 00000003 0000000a 
       c35d8000 c18f7e81 0000a250 00000b25 00000001 c35d810c c34794c4 c3593c80 
       00000003 00000082 00000000 f6da4828 c35aadc0 00000082 c043368e f7c3dfa4 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
xfslogd/2     S 00000016  3472   594     19           595   593 (L-TLB)
       c35d1f88 00000046 ed1d22f4 00000016 00000246 f5674dd0 00000003 0000000a 
       c3626550 ed1d3d4e 00000016 00001a5a 00000002 c362665c c3480308 f7da0c80 
       00000003 00000082 00000000 f553cce8 c35aad40 00000082 c043368e c35d1fa4 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
xfslogd/3     S 000052AC  3472   595     19           596   594 (L-TLB)
       c361cf88 00000046 58f8b57d 000052ac c374b8c0 0000ac00 00000003 0000000a 
       c3621550 58f8bf78 000052ac 000009fb 00000003 c362165c c348714c f7d66200 
       00000003 00000082 00000000 f6da4728 c35aacc0 00000082 c043368e c361cfa4 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
xfsdatad/0    S 00007C8D  3480   596     19           597   595 (L-TLB)
       f7f31f88 00000046 24a7f47d 00007c8d 00000000 00000001 00000003 0000000a 
       c366a000 24a7fa46 00007c8d 000005c9 00000000 c366a10c c3472680 c3593c80 
       00000003 00000000 f78b0674 f78b0678 c35aabc0 00000082 c043368e ffffffff 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
xfsdatad/1    S 0000A250  3480   597     19           598   596 (L-TLB)
       f7f28f88 00000046 c189342f 0000a250 00000000 00000001 00000003 0000000a 
       c366a550 c1893971 0000a250 00000542 00000001 c366a65c c34794c4 c3593c80 
       00000003 00000000 f78b082c f78b0830 c35aab40 00000082 c043368e ffffffff 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
xfsdatad/2    S 00000016  3572   598     19           599   597 (L-TLB)
       c35c8f88 00000046 c50dfcd7 00000016 00000000 00000001 00000003 0000000a 
       c3690aa0 c50e067f 00000016 000009a8 00000002 c3690bac c3480308 f7da0e40 
       00000003 00000000 f794ecfc f794ed00 c35aaac0 00000082 c043368e ffffffff 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
xfsdatad/3    S 000052AC  3572   599     19           649   598 (L-TLB)
       f7d2af88 00000046 58f2481e 000052ac 00000000 00000001 00000003 0000000a 
       f7f23000 58f24d14 000052ac 000004f6 00000003 f7f2310c c348714c f7d66200 
       00000003 00000000 d92ac5c4 d92ac5c8 c35aaa40 00000082 c043368e ffffffff 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
bond0         S 00000001  3640   649     19           651   599 (L-TLB)
       c3686f88 00000046 d5cbd468 00000001 00000086 c041fbc9 00000000 0000000a 
       c367c550 d5cbd8f8 00000001 00000490 00000000 c367c65c c3472680 c3593e40 
       c3686fc8 00000000 c367c550 00000011 c379e184 c042f92c c367c550 ffffffff 
Call Trace:
 [<c041fbc9>] try_to_wake_up+0x3e8/0x3f2
 [<c042f92c>] recalc_sigpending_and_wake+0x8/0x18
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
bond1         S 00000001  3640   651     19           738   649 (L-TLB)
       c3689f88 00000046 d5cd0f1b 00000001 00000000 00000000 00000000 00000001 
       c367c000 d5cd138b 00000001 00000470 00000000 c367c10c c3472680 c3593e40 
       c3689fc8 00000000 c367c000 00000011 c379fc04 c042f92c c367c000 ffffffff 
Call Trace:
 [<c042f92c>] recalc_sigpending_and_wake+0x8/0x18
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
nfsiod        S 000063D6  3536   738     19           783   651 (L-TLB)
       f7d30f88 00000046 9c0937c1 000063d6 c061d11e 00000001 00000003 0000000a 
       c3690000 9c0940d4 000063d6 00000913 00000002 c369010c c3480308 f7da0c80 
       00000003 00000000 d29d3974 d29d3978 f7f12140 00000082 c043368e ffffffff 
Call Trace:
 [<c061d11e>] __down+0x85/0xbb
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
mpt_poll_0    S 0000A252  3640   783     19           784   738 (L-TLB)
       f7d17f88 00000046 164c3c62 0000a252 c3678a18 00000246 00000003 0000000a 
       f7d2d550 164c4799 0000a252 00000b37 00000003 f7d2d65c c348714c f6d23c80 
       00000003 00000000 c3678b44 c3678b48 f790b440 00000082 c043368e ffffffff 
Call Trace:
 [<c043368e>] run_workqueue+0x98/0xb5
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
mpt/0         S 00000001  3640   784     19           795   783 (L-TLB)
       f7d1df88 00000046 df455e67 00000001 00000086 c041fbc9 00000000 00000001 
       c3682550 df456243 00000001 000003dc 00000000 c368265c c3472680 c3593e40 
       f7d1dfc8 00000000 c3682550 00000011 c370d184 c042f92c c3682550 ffffffff 
Call Trace:
 [<c041fbc9>] try_to_wake_up+0x3e8/0x3f2
 [<c042f92c>] recalc_sigpending_and_wake+0x8/0x18
 [<c0433efb>] worker_thread+0xb2/0x10b
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c0433e49>] worker_thread+0x0/0x10b
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
scsi_eh_1     S 00000005  3648   795     19           873   784 (L-TLB)
       c367ef90 00000046 cf06363f 00000005 00000000 c3621000 c3621000 00000009 
       c3621000 cf063c52 00000005 00000613 00000000 c362110c c3472680 c3593e40 
       cf061e09 00000000 00000000 cf062090 00000005 00000009 c06893c0 ffffffff 
Call Trace:
 [<f88bb615>] scsi_error_handler+0x0/0x422 [scsi_mod]
 [<f88bb668>] scsi_error_handler+0x53/0x422 [scsi_mod]
 [<c041ef71>] complete+0x2b/0x3d
 [<f88bb615>] scsi_error_handler+0x0/0x422 [scsi_mod]
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
kipmi0        S 0000A252  3552   873     19           898   795 (L-TLB)
       c3653f90 00000046 25771930 0000a252 c3653f44 00000000 00000246 0000000a 
       f7d34550 25e1b874 0000a252 00000e11 00000000 f7d3465c c3472680 f52d5ac0 
       00000009 00000000 00000286 c042da21 c07b9200 c3653f98 00000286 ffffffff 
Call Trace:
 [<c042da21>] lock_timer_base+0x15/0x2f
 [<c061c1f9>] schedule_timeout+0x71/0x8c
 [<c042d1cd>] process_timeout+0x0/0x5
 [<f8c1da82>] ipmi_thread+0x53/0x63 [ipmi_si]
 [<f8c1da2f>] ipmi_thread+0x0/0x63 [ipmi_si]
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
kjournald     S 0000A0C3  2788   898     19          1871   873 (L-TLB)
       c3669fa4 00000046 2b7fa1a0 0000a0c3 f89a2e2a 00000000 f53c7640 0000000a 
       f7d35aa0 2b7fb384 0000a0c3 000011e4 00000001 f7d35bac c34794c4 f7bf13c0 
       c3701250 00000000 00000001 c3669fa0 c041eff8 00000000 c3669fac c3701268 
Call Trace:
 [<f89a2e2a>] journal_commit_transaction+0xec6/0xeec [jbd]
 [<c041eff8>] __wake_up+0x2a/0x3d
 [<c043654b>] prepare_to_wait+0x24/0x46
 [<f89a5cc3>] kjournald+0x153/0x1c2 [jbd]
 [<c04363ff>] autoremove_wake_function+0x0/0x2d
 [<f89a5b70>] kjournald+0x0/0x1c2 [jbd]
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
busybox       S 0000A250  2612   918      1           990    19 (NOTLB)
       f782bdac 00000082 38228103 0000a250 c36fd2c8 f782bd50 00000004 0000000a 
       f78ab550 38229a23 0000a250 00001920 00000003 f78ab65c c348714c f7d66740 
       00000000 00000000 f782bdca 00000000 c36fd2c8 00000000 c36fd2c8 ffffffff 
Call Trace:
 [<c061c19b>] schedule_timeout+0x13/0x8c
 [<c04364da>] prepare_to_wait_exclusive+0x27/0x49
 [<c05bda1a>] __skb_recv_datagram+0x164/0x1dd
 [<c04363ff>] autoremove_wake_function+0x0/0x2d
 [<c05bdab0>] skb_recv_datagram+0x1d/0x21
 [<c061c408>] mutex_lock+0xb/0x19
 [<c0615552>] unix_dgram_recvmsg+0x53/0x212
 [<c05b5de6>] do_sock_read+0xbe/0xf7
 [<c05b617c>] sock_aio_read+0x53/0x61
 [<c04745bb>] do_sync_read+0xb6/0xf1
 [<c04363ff>] autoremove_wake_function+0x0/0x2d
 [<c0474ea5>] vfs_read+0xb0/0x141
 [<c04752e2>] sys_read+0x3c/0x63
 [<c0404f17>] syscall_call+0x7/0xb
 =======================
irqbalance    S 0000A251  3052   990      1          2254   918 (NOTLB)
       f783df3c 00000086 ce90862f 0000a251 15522288 f783def8 c3488278 0000000a 
       f7d35550 ce93ce57 0000a251 00034828 00000003 f7d3565c c348714c f7da03c0 
       c3488278 00000286 00000000 757875dd 0000a2a9 757875dd 0000a2a9 217ced5d 
Call Trace:
 [<c061c5ac>] do_nanosleep+0x3c/0x6a
 [<c04389f5>] hrtimer_nanosleep+0x50/0x106
 [<c04654a3>] unmap_region+0xe1/0xf0
 [<c04387dc>] hrtimer_wakeup+0x0/0x18
 [<c04efcf1>] copy_to_user+0x31/0x48
 [<c0438aec>] sys_nanosleep+0x41/0x51
 [<c0404ead>] sysenter_past_esp+0x56/0x79
 =======================
xfsbufd       S 0000A252  2712  1871     19          1872   898 (L-TLB)
       c3681f80 00000046 1ea00257 0000a252 016e4580 f7fb9540 f7fb9540 0000000a 
       c366aaa0 1ea004ce 0000a252 00000277 00000003 c366abac c348714c f6d23c80 
       00000200 00000000 00000286 c042da21 c3600000 c3681f88 00000286 ffffffff 
Call Trace:
 [<c042da21>] lock_timer_base+0x15/0x2f
 [<c061c1f9>] schedule_timeout+0x71/0x8c
 [<c042d1cd>] process_timeout+0x0/0x5
 [<f8acc2bc>] xfsbufd+0x69/0x16a [xfs]
 [<f8acc253>] xfsbufd+0x0/0x16a [xfs]
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
xfssyncd      S 0000A24F  2564  1872     19          2796  1871 (L-TLB)
       f6d30f88 00000046 f211462b 0000a24f 00000000 00000000 f7f2f400 00000004 
       c35d8aa0 f2132811 0000a24f 0001e1e6 00000003 c35d8bac c348714c f7bf13c0 
       f3b57b00 00000000 00000286 c042da21 c3600000 f6d30f90 00000286 ffffffff 
Call Trace:
 [<c042da21>] lock_timer_base+0x15/0x2f
 [<c061c1f9>] schedule_timeout+0x71/0x8c
 [<c042d1cd>] process_timeout+0x0/0x5
 [<f8ad0f1b>] xfssyncd+0x1e/0xe3 [xfs]
 [<f8ad0efd>] xfssyncd+0x0/0xe3 [xfs]
 [<c043633b>] kthread+0xc0/0xed
 [<c043627b>] kthread+0x0/0xed
 [<c0405c53>] kernel_thread_helper+0x7/0x10
 =======================
knconsole     S 0000A250   616  2254      1          2259   990 (NOTLB)
       f6e39b68 00200082 c18f7e81 0000a250 00000001 f7fb94c0 edf7c3d4 0000000a 
       f6d3a550 c1994223 0000a250 0009c3a2 00000001 f6d3a65c c34794c4 c3593c80 
       00000000 00000000 00200286 c042da21 c35dc000 f6e39b70 00200286 ffffffff 
Call Trace:
 [<c042da21>] lock_timer_base+0x15/0x2f
 [<c061c1f9>] schedule_timeout+0x71/0x8c
 [<c042d1cd>] process_timeout+0x0/0x5
 [<c04861c8>] do_select+0x371/0x3cb
 [<c048674b>] __pollwait+0x0/0xb2
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<c041fbd3>] default_wake_function+0x0/0xc
 [<f8a80ede>] xfs_alloc_log_block+0x31/0x37 [xfs]
 [<f8aba4d7>] xfs_icsb_modify_counters_int+0x59/0x1ce [xfs]
 [<f8acbe54>] xfs_buf_read_flags+0x13/0x76 [xfs]
 [<f8abfa49>] xfs_trans_read_buf+0x282/0x2c0 [xfs]
 [<f8aba4d7>] xfs_icsb_modify_counters_int+0x59/0x1ce [xfs]
 [<f8a97f76>] xfs_btree_read_bufs+0x6a/0x87 [xfs]
 [<c04c63ab>] avc_has_perm+0x3c/0x46
 [<c04c661f>] ipc_has_perm+0x58/0x60
 [<c04bd47b>] sys_semtimedop+0x6ce/0x700
 [<c04864cb>] core_sys_select+0x2a9/0x2ca
 [<c0425caa>] release_console_sem+0x17e/0x1b8
 [<c0547743>] do_con_write+0x1466/0x1497
 [<c04c69ff>] inode_has_perm+0x54/0x5c
 [<c045aaa8>] __pagevec_free+0x14/0x1a
 [<c0506e87>] vgacon_cursor+0x6e/0x199
 [<c0506e87>] vgacon_cursor+0x6e/0x199
 [<c0425caa>] release_console_sem+0x17e/0x1b8
 [<c041eff8>] __wake_up+0x2a/0x3d
 [<c0539a1d>] tty_ldisc_deref+0x50/0x5f
 [<c0486a92>] sys_select+0x9a/0x180
 [<c04efcf1>] copy_to_user+0x31/0x48
 [<c0404ead>] sysenter_past_esp+0x56/0x79

---

