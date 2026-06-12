---
title: "Infinte loop...."
date: 2011-06-22
forum: General Help
---

### Post by wizodd0 on 2011-06-22
System:
64 bit AMD 4Gb 3 processors
Ubuntu 10.10 64bit
Running programs:
FireFox, Office, gimp, document displays

Description:

I was in FF with about53 tabs open the current tab was Google Images. I was scrolling the page and the machine hung and began thrashing the disk. This continued for ~15 minutes until I did a hardware reset. The machine was periodically responsive (moving the cursor small amounts) but wasn't evenupdating the clock.

Below is the message log which seems to me to show it locked in a loop.


Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428119] events/0      D f74b7e88     0    12      2 0x00000000
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428131]  f74b7e98 00000046 00000002 f74b7e88 f6d8a000 c0601b40 c090a480 c090a480
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428147]  dfd879eb 000053be c090a480 c090a480 00000000 000053be 00000000 c090a480
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428161]  c090a480 f74c0000 00000000 f2d874c4 f74b7ea4 f2d87458 f74b7ec4 f8587c7d
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428175] Call Trace:
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428202]  [<f8587c7d>] ttm_bo_wait_unreserved+0xdd/0x130 [ttm]
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428216]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428233]  [<f8587d7f>] ttm_bo_reserve_locked+0xaf/0xe0 [ttm]
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428248]  [<f8587eaf>] ttm_bo_cleanup_refs+0xff/0x230 [ttm]
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428281]  [<f8587000>] ? ttm_bo_release_list+0x10/0xb0 [ttm]
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428294]  [<f8586ff0>] ? ttm_bo_release_list+0x0/0xb0 [ttm]
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428315]  [<f858805f>] ttm_bo_delayed_delete+0x7f/0xe0 [ttm]
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428336]  [<f85880d7>] ttm_bo_delayed_workqueue+0x17/0x30 [ttm]
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428353]  [<c016a24e>] run_workqueue+0x8e/0x150
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428373]  [<f85880c0>] ? ttm_bo_delayed_workqueue+0x0/0x30 [ttm]
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428391]  [<c016a394>] worker_thread+0x84/0xe0
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428405]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428420]  [<c016a310>] ? worker_thread+0x0/0xe0
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428435]  [<c016e1e4>] kthread+0x74/0x80
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428448]  [<c016e170>] ? kthread+0x0/0x80
Jun 22 11:41:03 charles-Ubuntu kernel: [92280.428462]  [<c010997e>] kernel_thread_helper+0x6/0x10
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428364] events/0      D f74b7e88     0    12      2 0x00000000
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428377]  f74b7e98 00000046 00000002 f74b7e88 f6d8a000 c0601b40 c090a480 c090a480
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428394]  dfd879eb 000053be c090a480 c090a480 00000000 000053be 00000000 c090a480
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428409]  c090a480 f74c0000 00000000 f2d874c4 f74b7ea4 f2d87458 f74b7ec4 f8587c7d
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428423] Call Trace:
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428450]  [<f8587c7d>] ttm_bo_wait_unreserved+0xdd/0x130 [ttm]
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428466]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428483]  [<f8587d7f>] ttm_bo_reserve_locked+0xaf/0xe0 [ttm]
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428497]  [<f8587eaf>] ttm_bo_cleanup_refs+0xff/0x230 [ttm]
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428511]  [<f8587000>] ? ttm_bo_release_list+0x10/0xb0 [ttm]
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428524]  [<f8586ff0>] ? ttm_bo_release_list+0x0/0xb0 [ttm]
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428537]  [<f858805f>] ttm_bo_delayed_delete+0x7f/0xe0 [ttm]
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428551]  [<f85880d7>] ttm_bo_delayed_workqueue+0x17/0x30 [ttm]
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428561]  [<c016a24e>] run_workqueue+0x8e/0x150
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428574]  [<f85880c0>] ? ttm_bo_delayed_workqueue+0x0/0x30 [ttm]
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428584]  [<c016a394>] worker_thread+0x84/0xe0
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428592]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428601]  [<c016a310>] ? worker_thread+0x0/0xe0
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428608]  [<c016e1e4>] kthread+0x74/0x80
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428615]  [<c016e170>] ? kthread+0x0/0x80
Jun 22 11:43:03 charles-Ubuntu kernel: [92400.428623]  [<c010997e>] kernel_thread_helper+0x6/0x10
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428356] events/0      D f74b7e88     0    12      2 0x00000000
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428369]  f74b7e98 00000046 00000002 f74b7e88 f6d8a000 c0601b40 c090a480 c090a480
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428390]  dfd879eb 000053be c090a480 c090a480 00000000 000053be 00000000 c090a480
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428405]  c090a480 f74c0000 00000000 f2d874c4 f74b7ea4 f2d87458 f74b7ec4 f8587c7d
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428419] Call Trace:
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428446]  [<f8587c7d>] ttm_bo_wait_unreserved+0xdd/0x130 [ttm]
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428461]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428478]  [<f8587d7f>] ttm_bo_reserve_locked+0xaf/0xe0 [ttm]
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428493]  [<f8587eaf>] ttm_bo_cleanup_refs+0xff/0x230 [ttm]
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428513]  [<f8587000>] ? ttm_bo_release_list+0x10/0xb0 [ttm]
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428526]  [<f8586ff0>] ? ttm_bo_release_list+0x0/0xb0 [ttm]
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428540]  [<f858805f>] ttm_bo_delayed_delete+0x7f/0xe0 [ttm]
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428554]  [<f85880d7>] ttm_bo_delayed_workqueue+0x17/0x30 [ttm]
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428564]  [<c016a24e>] run_workqueue+0x8e/0x150
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428577]  [<f85880c0>] ? ttm_bo_delayed_workqueue+0x0/0x30 [ttm]
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428587]  [<c016a394>] worker_thread+0x84/0xe0
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428595]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428603]  [<c016a310>] ? worker_thread+0x0/0xe0
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428616]  [<c016e1e4>] kthread+0x74/0x80
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428624]  [<c016e170>] ? kthread+0x0/0x80
Jun 22 11:45:02 charles-Ubuntu kernel: [92520.428631]  [<c010997e>] kernel_thread_helper+0x6/0x10
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432274] events/0      D f74b7e88     0    12      2 0x00000000
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432278]  f74b7e98 00000046 00000002 f74b7e88 f6d8a000 c0601b40 c090a480 c090a480
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432282]  dfd879eb 000053be c090a480 c090a480 00000000 000053be 00000000 c090a480
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432286]  c090a480 f74c0000 00000000 f2d874c4 f74b7ea4 f2d87458 f74b7ec4 f8587c7d
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432290] Call Trace:
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432302]  [<f8587c7d>] ttm_bo_wait_unreserved+0xdd/0x130 [ttm]
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432308]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432312]  [<f8587d7f>] ttm_bo_reserve_locked+0xaf/0xe0 [ttm]
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432316]  [<f8587eaf>] ttm_bo_cleanup_refs+0xff/0x230 [ttm]
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432319]  [<f8587000>] ? ttm_bo_release_list+0x10/0xb0 [ttm]
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432323]  [<f8586ff0>] ? ttm_bo_release_list+0x0/0xb0 [ttm]
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432327]  [<f858805f>] ttm_bo_delayed_delete+0x7f/0xe0 [ttm]
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432330]  [<f85880d7>] ttm_bo_delayed_workqueue+0x17/0x30 [ttm]
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432333]  [<c016a24e>] run_workqueue+0x8e/0x150
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432339]  [<f85880c0>] ? ttm_bo_delayed_workqueue+0x0/0x30 [ttm]
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432341]  [<c016a394>] worker_thread+0x84/0xe0
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432343]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432346]  [<c016a310>] ? worker_thread+0x0/0xe0
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432347]  [<c016e1e4>] kthread+0x74/0x80
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432349]  [<c016e170>] ? kthread+0x0/0x80
Jun 22 11:47:02 charles-Ubuntu kernel: [92640.432352]  [<c010997e>] kernel_thread_helper+0x6/0x10
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428305] events/0      D f74b7e88     0    12      2 0x00000000
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428318]  f74b7e98 00000046 00000002 f74b7e88 f6d8a000 c0601b40 c090a480 c090a480
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428334]  dfd879eb 000053be c090a480 c090a480 00000000 000053be 00000000 c090a480
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428349]  c090a480 f74c0000 00000000 f2d874c4 f74b7ea4 f2d87458 f74b7ec4 f8587c7d
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428363] Call Trace:
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428390]  [<f8587c7d>] ttm_bo_wait_unreserved+0xdd/0x130 [ttm]
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428405]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428422]  [<f8587d7f>] ttm_bo_reserve_locked+0xaf/0xe0 [ttm]
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428443]  [<f8587eaf>] ttm_bo_cleanup_refs+0xff/0x230 [ttm]
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428457]  [<f8587000>] ? ttm_bo_release_list+0x10/0xb0 [ttm]
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428470]  [<f8586ff0>] ? ttm_bo_release_list+0x0/0xb0 [ttm]
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428484]  [<f858805f>] ttm_bo_delayed_delete+0x7f/0xe0 [ttm]
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428498]  [<f85880d7>] ttm_bo_delayed_workqueue+0x17/0x30 [ttm]
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428508]  [<c016a24e>] run_workqueue+0x8e/0x150
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428522]  [<f85880c0>] ? ttm_bo_delayed_workqueue+0x0/0x30 [ttm]
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428531]  [<c016a394>] worker_thread+0x84/0xe0
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428539]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428548]  [<c016a310>] ? worker_thread+0x0/0xe0
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428555]  [<c016e1e4>] kthread+0x74/0x80
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428562]  [<c016e170>] ? kthread+0x0/0x80
Jun 22 11:49:06 charles-Ubuntu kernel: [92760.428570]  [<c010997e>] kernel_thread_helper+0x6/0x10
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428117] events/0      D f74b7e88     0    12      2 0x00000000
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428129]  f74b7e98 00000046 00000002 f74b7e88 f6d8a000 c0601b40 c090a480 c090a480
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428146]  dfd879eb 000053be c090a480 c090a480 00000000 000053be 00000000 c090a480
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428161]  c090a480 f74c0000 00000000 f2d874c4 f74b7ea4 f2d87458 f74b7ec4 f8587c7d
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428175] Call Trace:
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428202]  [<f8587c7d>] ttm_bo_wait_unreserved+0xdd/0x130 [ttm]
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428217]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428234]  [<f8587d7f>] ttm_bo_reserve_locked+0xaf/0xe0 [ttm]
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428249]  [<f8587eaf>] ttm_bo_cleanup_refs+0xff/0x230 [ttm]
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428262]  [<f8587000>] ? ttm_bo_release_list+0x10/0xb0 [ttm]
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428275]  [<f8586ff0>] ? ttm_bo_release_list+0x0/0xb0 [ttm]
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428289]  [<f858805f>] ttm_bo_delayed_delete+0x7f/0xe0 [ttm]
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428303]  [<f85880d7>] ttm_bo_delayed_workqueue+0x17/0x30 [ttm]
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428312]  [<c016a24e>] run_workqueue+0x8e/0x150
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428326]  [<f85880c0>] ? ttm_bo_delayed_workqueue+0x0/0x30 [ttm]
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428335]  [<c016a394>] worker_thread+0x84/0xe0
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428344]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428352]  [<c016a310>] ? worker_thread+0x0/0xe0
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428359]  [<c016e1e4>] kthread+0x74/0x80
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428366]  [<c016e170>] ? kthread+0x0/0x80
Jun 22 11:51:02 charles-Ubuntu kernel: [92880.428374]  [<c010997e>] kernel_thread_helper+0x6/0x10
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428100] events/0      D f74b7e88     0    12      2 0x00000000
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428113]  f74b7e98 00000046 00000002 f74b7e88 f6d8a000 c0601b40 c090a480 c090a480
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428129]  dfd879eb 000053be c090a480 c090a480 00000000 000053be 00000000 c090a480
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428143]  c090a480 f74c0000 00000000 f2d874c4 f74b7ea4 f2d87458 f74b7ec4 f8587c7d
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428157] Call Trace:
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428183]  [<f8587c7d>] ttm_bo_wait_unreserved+0xdd/0x130 [ttm]
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428198]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428215]  [<f8587d7f>] ttm_bo_reserve_locked+0xaf/0xe0 [ttm]
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428230]  [<f8587eaf>] ttm_bo_cleanup_refs+0xff/0x230 [ttm]
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428243]  [<f8587000>] ? ttm_bo_release_list+0x10/0xb0 [ttm]
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428256]  [<f8586ff0>] ? ttm_bo_release_list+0x0/0xb0 [ttm]
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428270]  [<f858805f>] ttm_bo_delayed_delete+0x7f/0xe0 [ttm]
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428284]  [<f85880d7>] ttm_bo_delayed_workqueue+0x17/0x30 [ttm]
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428294]  [<c016a24e>] run_workqueue+0x8e/0x150
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428307]  [<f85880c0>] ? ttm_bo_delayed_workqueue+0x0/0x30 [ttm]
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428316]  [<c016a394>] worker_thread+0x84/0xe0
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428324]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428333]  [<c016a310>] ? worker_thread+0x0/0xe0
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428340]  [<c016e1e4>] kthread+0x74/0x80
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428347]  [<c016e170>] ? kthread+0x0/0x80
Jun 22 11:53:03 charles-Ubuntu kernel: [93000.428355]  [<c010997e>] kernel_thread_helper+0x6/0x10
Jun 22 11:55:08 charles-Ubuntu kernel: [93120.428115] events/0      D f74b7e88     0    12      2 0x00000000
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428128]  f74b7e98 00000046 00000002 f74b7e88 f6d8a000 c0601b40 c090a480 c090a480
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428144]  dfd879eb 000053be c090a480 c090a480 00000000 000053be 00000000 c090a480
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428159]  c090a480 f74c0000 00000000 f2d874c4 f74b7ea4 f2d87458 f74b7ec4 f8587c7d
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428173] Call Trace:
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428200]  [<f8587c7d>] ttm_bo_wait_unreserved+0xdd/0x130 [ttm]
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428215]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428232]  [<f8587d7f>] ttm_bo_reserve_locked+0xaf/0xe0 [ttm]
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428246]  [<f8587eaf>] ttm_bo_cleanup_refs+0xff/0x230 [ttm]
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428260]  [<f8587000>] ? ttm_bo_release_list+0x10/0xb0 [ttm]
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428273]  [<f8586ff0>] ? ttm_bo_release_list+0x0/0xb0 [ttm]
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428286]  [<f858805f>] ttm_bo_delayed_delete+0x7f/0xe0 [ttm]
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428300]  [<f85880d7>] ttm_bo_delayed_workqueue+0x17/0x30 [ttm]
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428310]  [<c016a24e>] run_workqueue+0x8e/0x150
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428323]  [<f85880c0>] ? ttm_bo_delayed_workqueue+0x0/0x30 [ttm]
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428333]  [<c016a394>] worker_thread+0x84/0xe0
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428341]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428349]  [<c016a310>] ? worker_thread+0x0/0xe0
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428356]  [<c016e1e4>] kthread+0x74/0x80
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428364]  [<c016e170>] ? kthread+0x0/0x80
Jun 22 11:55:10 charles-Ubuntu kernel: [93120.428372]  [<c010997e>] kernel_thread_helper+0x6/0x10
Jun 22 11:57:31 charles-Ubuntu kernel: [93240.428114] events/0      D f74b7e88     0    12      2 0x00000000
Jun 22 11:57:37 charles-Ubuntu kernel: [93240.428126]  f74b7e98 00000046 00000002 f74b7e88 f6d8a000 c0601b40 c090a480 c090a480
Jun 22 11:57:41 charles-Ubuntu kernel: [93240.428143]  dfd879eb 000053be c090a480 c090a480 00000000 000053be 00000000 c090a480
Jun 22 11:58:08 charles-Ubuntu kernel: [93240.428158]  c090a480 f74c0000 00000000 f2d874c4 f74b7ea4 f2d87458 f74b7ec4 f8587c7d
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428172] Call Trace:
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428198]  [<f8587c7d>] ttm_bo_wait_unreserved+0xdd/0x130 [ttm]
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428213]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428230]  [<f8587d7f>] ttm_bo_reserve_locked+0xaf/0xe0 [ttm]
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428244]  [<f8587eaf>] ttm_bo_cleanup_refs+0xff/0x230 [ttm]
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428258]  [<f8587000>] ? ttm_bo_release_list+0x10/0xb0 [ttm]
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428271]  [<f8586ff0>] ? ttm_bo_release_list+0x0/0xb0 [ttm]
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428284]  [<f858805f>] ttm_bo_delayed_delete+0x7f/0xe0 [ttm]
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428298]  [<f85880d7>] ttm_bo_delayed_workqueue+0x17/0x30 [ttm]
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428308]  [<c016a24e>] run_workqueue+0x8e/0x150
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428321]  [<f85880c0>] ? ttm_bo_delayed_workqueue+0x0/0x30 [ttm]
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428330]  [<c016a394>] worker_thread+0x84/0xe0
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428339]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428347]  [<c016a310>] ? worker_thread+0x0/0xe0
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428354]  [<c016e1e4>] kthread+0x74/0x80
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428362]  [<c016e170>] ? kthread+0x0/0x80
Jun 22 11:58:12 charles-Ubuntu kernel: [93240.428369]  [<c010997e>] kernel_thread_helper+0x6/0x10
Jun 22 12:00:00 charles-Ubuntu kernel: [93360.428169] events/0      D f74b7e88     0    12      2 0x00000000
Jun 22 12:00:17 charles-Ubuntu kernel: [93360.428181]  f74b7e98 00000046 00000002 f74b7e88 f6d8a000 c0601b40 c090a480 c090a480
Jun 22 12:00:23 charles-Ubuntu kernel: [93360.428198]  dfd879eb 000053be c090a480 c090a480 00000000 000053be 00000000 c090a480
Jun 22 12:00:34 charles-Ubuntu kernel: [93360.428213]  c090a480 f74c0000 00000000 f2d874c4 f74b7ea4 f2d87458 f74b7ec4 f8587c7d
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428227] Call Trace:
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428253]  [<f8587c7d>] ttm_bo_wait_unreserved+0xdd/0x130 [ttm]
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428269]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428285]  [<f8587d7f>] ttm_bo_reserve_locked+0xaf/0xe0 [ttm]
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428300]  [<f8587eaf>] ttm_bo_cleanup_refs+0xff/0x230 [ttm]
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428314]  [<f8587000>] ? ttm_bo_release_list+0x10/0xb0 [ttm]
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428327]  [<f8586ff0>] ? ttm_bo_release_list+0x0/0xb0 [ttm]
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428340]  [<f858805f>] ttm_bo_delayed_delete+0x7f/0xe0 [ttm]
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428354]  [<f85880d7>] ttm_bo_delayed_workqueue+0x17/0x30 [ttm]
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428364]  [<c016a24e>] run_workqueue+0x8e/0x150
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428377]  [<f85880c0>] ? ttm_bo_delayed_workqueue+0x0/0x30 [ttm]
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428386]  [<c016a394>] worker_thread+0x84/0xe0
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428395]  [<c016e610>] ? autoremove_wake_function+0x0/0x50
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428403]  [<c016a310>] ? worker_thread+0x0/0xe0
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428410]  [<c016e1e4>] kthread+0x74/0x80
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428418]  [<c016e170>] ? kthread+0x0/0x80
Jun 22 12:01:15 charles-Ubuntu kernel: [93360.428425]  [<c010997e>] kernel_thread_helper+0x6/0x10
Jun 22 12:10:44 charles-Ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jun 22 12:10:44 charles-Ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1047" x-info="http://www.rsyslog.com"] (re)start
Jun 22 12:10:44 charles-Ubuntu rsyslogd: rsyslogd's groupid changed to 103
Jun 22 12:10:44 charles-Ubuntu rsyslogd: rsyslogd's userid changed to 101

---

