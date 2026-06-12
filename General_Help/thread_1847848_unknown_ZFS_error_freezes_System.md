---
title: "unknown ZFS error freezes System"
date: 2011-09-21
forum: General Help
---

### Post by PhilipVinc on 2011-09-21
I have a system connected to a zfs pool comprised of 2 drives. The OS is installed in an 8 Gb USB Stick.

Right now, I am copying a lot of data (1.5 Tb ) made of various big documents (700Mb-10Gb) from a Nas in my 10/100 Ethernet network over to my ZFS array.

Over the course of 24 hours, I found the system frozen 3 times ( With Frozen I mean that even moving the mouse would not move the cursor, and any keyboard command would not do anything. Even pushing the power button, that should make a window pop up, made nothing). Every time this happened the system was copying some files in the zfs array.

Every time I found the system frozen, I also found the 2 HD  spun down and completely silent.

That made me think that the source of the error could be zfs.

Apparently, in the log, there are few message until a precise time, when the error occurred, after wich no more messages are logged (until reboot).

If you could help me, I would be really glad.

System Info:
Asus E35M1-i deluxe ( AMD E350 APU motherboard)
4Gb ram
OS installed on a USB stick.
2X2Tb Western Digital Caviar Green EAX (connected to sata ports 1-2)

Software: Ubuntu 11.04 (Updated)
ZFS kernel module installed from official repository (zfsonlinux.com)
Transmission client downloading data to the zfs disk is also running

ZFS:
There is no RaidZ on the pool. It's just a pool created with 
"sudo zpool create tank "device1" "device2"

Error Log
> Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570193] INFO: task z_wr_int/0:1299 blocked for more than 120 seconds.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570207] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570216] z_wr_int/0      D 0000000000000000     0  1299      2 0x00000000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570230]  ffff88011d7fdbe0 0000000000000046 ffff88011d7fdfd8 ffff88011d7fc000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570242]  0000000000013d00 ffff88011f56df38 ffff88011d7fdfd8 0000000000013d00
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570254]  ffff88012229db80 ffff88011f56db80 ffff88011d7fc000 ffffc90012c22c30
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570265] Call Trace:
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570287]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570343]  [<ffffffffa00b9246>] ? kmem_free_debug+0x16/0x20 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570355]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570467]  [<ffffffffa01e5d88>] zio_remove_child+0x48/0xf0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570548]  [<ffffffffa01ea763>] zio_done+0x273/0xb80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570628]  [<ffffffffa01b22f4>] ? vdev_mirror_map_free+0x24/0x30 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570708]  [<ffffffffa01eab22>] zio_done+0x632/0xb80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570719]  [<ffffffff815c1afe>] ? mutex_lock+0x1e/0x50
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570797]  [<ffffffffa01e5b53>] ? zio_wait_for_children+0x63/0x80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570875]  [<ffffffffa01e6af0>] zio_execute+0xb0/0x150 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570887]  [<ffffffff81038c79>] ? default_spin_lock_flags+0x9/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570914]  [<ffffffffa00bbb00>] taskq_thread+0x1c0/0x390 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570926]  [<ffffffff8105f600>] ? default_wake_function+0x0/0x20
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570952]  [<ffffffffa00bb940>] ? taskq_thread+0x0/0x390 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570963]  [<ffffffff81087866>] kthread+0x96/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570974]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570984]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.570993]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571003] INFO: task z_wr_int/2:1301 blocked for more than 120 seconds.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571009] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571016] z_wr_int/2      D 0000000000000000     0  1301      2 0x00000000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571028]  ffff88011cb69be0 0000000000000046 ffff88011cb69fd8 ffff88011cb68000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571040]  0000000000013d00 ffff88012229df38 ffff88011cb69fd8 0000000000013d00
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571051]  ffff880121c916e0 ffff88012229db80 ffffc9001266b690 ffffc90012c22c30
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571062] Call Trace:
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571073]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571099]  [<ffffffffa00b9246>] ? kmem_free_debug+0x16/0x20 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571110]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571187]  [<ffffffffa01e5d88>] zio_remove_child+0x48/0xf0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571264]  [<ffffffffa01ea763>] zio_done+0x273/0xb80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571343]  [<ffffffffa01b22f4>] ? vdev_mirror_map_free+0x24/0x30 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571420]  [<ffffffffa01eab22>] zio_done+0x632/0xb80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571431]  [<ffffffff815c1afe>] ? mutex_lock+0x1e/0x50
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571507]  [<ffffffffa01e5b53>] ? zio_wait_for_children+0x63/0x80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571584]  [<ffffffffa01e6af0>] zio_execute+0xb0/0x150 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571594]  [<ffffffff81038c79>] ? default_spin_lock_flags+0x9/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571620]  [<ffffffffa00bbb00>] taskq_thread+0x1c0/0x390 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571631]  [<ffffffff8105f600>] ? default_wake_function+0x0/0x20
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571657]  [<ffffffffa00bb940>] ? taskq_thread+0x0/0x390 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571667]  [<ffffffff81087866>] kthread+0x96/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571677]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571687]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571696]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571705] INFO: task z_wr_int/4:1303 blocked for more than 120 seconds.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571711] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571718] z_wr_int/4      D 0000000000000000     0  1303      2 0x00000000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571729]  ffff88011dbb7be0 0000000000000046 ffff88011dbb7fd8 ffff88011dbb6000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571741]  0000000000013d00 ffff8801222983b8 ffff88011dbb7fd8 0000000000013d00
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571752]  ffff88004d84adc0 ffff880122298000 ffffc900112a3b68 ffffc90012c22c30
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571763] Call Trace:
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571774]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571799]  [<ffffffffa00b9246>] ? kmem_free_debug+0x16/0x20 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571810]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571887]  [<ffffffffa01e5d88>] zio_remove_child+0x48/0xf0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.571964]  [<ffffffffa01ea763>] zio_done+0x273/0xb80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572042]  [<ffffffffa01b22f4>] ? vdev_mirror_map_free+0x24/0x30 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572119]  [<ffffffffa01eab22>] zio_done+0x632/0xb80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572130]  [<ffffffff815c1afe>] ? mutex_lock+0x1e/0x50
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572206]  [<ffffffffa01e5b53>] ? zio_wait_for_children+0x63/0x80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572284]  [<ffffffffa01e6af0>] zio_execute+0xb0/0x150 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572293]  [<ffffffff81038c79>] ? default_spin_lock_flags+0x9/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572320]  [<ffffffffa00bbb00>] taskq_thread+0x1c0/0x390 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572330]  [<ffffffff8105f600>] ? default_wake_function+0x0/0x20
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572356]  [<ffffffffa00bb940>] ? taskq_thread+0x0/0x390 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572366]  [<ffffffff81087866>] kthread+0x96/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572376]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572386]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572394]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572403] INFO: task z_wr_int/6:1305 blocked for more than 120 seconds.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572409] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572416] z_wr_int/6      D 0000000000000000     0  1305      2 0x00000000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572428]  ffff88011d1bfbe0 0000000000000046 ffff88011d1bffd8 ffff88011d1be000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572439]  0000000000013d00 ffff88012229b178 ffff88011d1bffd8 0000000000013d00
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572450]  ffff88011d158000 ffff88012229adc0 ffffc900112a42d8 ffffc90012c22c30
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572461] Call Trace:
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572472]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572497]  [<ffffffffa00b9246>] ? kmem_free_debug+0x16/0x20 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572508]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572584]  [<ffffffffa01e5d88>] zio_remove_child+0x48/0xf0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572660]  [<ffffffffa01ea763>] zio_done+0x273/0xb80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572739]  [<ffffffffa01b22f4>] ? vdev_mirror_map_free+0x24/0x30 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572816]  [<ffffffffa01eab22>] zio_done+0x632/0xb80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572826]  [<ffffffff815c1afe>] ? mutex_lock+0x1e/0x50
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572902]  [<ffffffffa01e5b53>] ? zio_wait_for_children+0x63/0x80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572979]  [<ffffffffa01e6af0>] zio_execute+0xb0/0x150 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.572989]  [<ffffffff81038c79>] ? default_spin_lock_flags+0x9/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573016]  [<ffffffffa00bbb00>] taskq_thread+0x1c0/0x390 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573026]  [<ffffffff8105f600>] ? default_wake_function+0x0/0x20
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573052]  [<ffffffffa00bb940>] ? taskq_thread+0x0/0x390 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573062]  [<ffffffff81087866>] kthread+0x96/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573071]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573081]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573090]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573099] INFO: task z_wr_int/8:1307 blocked for more than 120 seconds.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573105] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573112] z_wr_int/8      D 0000000000000000     0  1307      2 0x00000000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573123]  ffff88011d06bbe0 0000000000000046 ffff88011d06bfd8 ffff88011d06a000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573134]  0000000000013d00 ffff88011d1583b8 ffff88011d06bfd8 0000000000013d00
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573145]  ffff880122298000 ffff88011d158000 ffffc900112a3040 ffffc90012c22c30
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573156] Call Trace:
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573167]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573193]  [<ffffffffa00b9246>] ? kmem_free_debug+0x16/0x20 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573204]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573280]  [<ffffffffa01e5d88>] zio_remove_child+0x48/0xf0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573356]  [<ffffffffa01ea763>] zio_done+0x273/0xb80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573435]  [<ffffffffa01b22f4>] ? vdev_mirror_map_free+0x24/0x30 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573512]  [<ffffffffa01eab22>] zio_done+0x632/0xb80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573522]  [<ffffffff815c1afe>] ? mutex_lock+0x1e/0x50
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573599]  [<ffffffffa01e5b53>] ? zio_wait_for_children+0x63/0x80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573676]  [<ffffffffa01e6af0>] zio_execute+0xb0/0x150 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573686]  [<ffffffff81038c79>] ? default_spin_lock_flags+0x9/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573713]  [<ffffffffa00bbb00>] taskq_thread+0x1c0/0x390 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573723]  [<ffffffff8105f600>] ? default_wake_function+0x0/0x20
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573749]  [<ffffffffa00bb940>] ? taskq_thread+0x0/0x390 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573759]  [<ffffffff81087866>] kthread+0x96/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573769]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573779]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573788]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573797] INFO: task z_wr_int/10:1309 blocked for more than 120 seconds.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573803] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573809] z_wr_int/10     D 0000000000000000     0  1309      2 0x00000000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573820]  ffff88011cb7fbe0 0000000000000046 ffff88011cb7ffd8 ffff88011cb7e000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573832]  0000000000013d00 ffff88011f571a98 ffff88011cb7ffd8 0000000000013d00
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573842]  ffff88009dd416e0 ffff88011f5716e0 ffffc900115841b8 ffffc90012c22c30
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573853] Call Trace:
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573864]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573890]  [<ffffffffa00b9246>] ? kmem_free_debug+0x16/0x20 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573901]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.573978]  [<ffffffffa01e5d88>] zio_remove_child+0x48/0xf0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574055]  [<ffffffffa01ea763>] zio_done+0x273/0xb80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574133]  [<ffffffffa01b22f4>] ? vdev_mirror_map_free+0x24/0x30 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574210]  [<ffffffffa01eab22>] zio_done+0x632/0xb80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574221]  [<ffffffff815c1afe>] ? mutex_lock+0x1e/0x50
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574297]  [<ffffffffa01e5b53>] ? zio_wait_for_children+0x63/0x80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574374]  [<ffffffffa01e6af0>] zio_execute+0xb0/0x150 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574383]  [<ffffffff81038c79>] ? default_spin_lock_flags+0x9/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574410]  [<ffffffffa00bbb00>] taskq_thread+0x1c0/0x390 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574420]  [<ffffffff8105f600>] ? default_wake_function+0x0/0x20
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574446]  [<ffffffffa00bb940>] ? taskq_thread+0x0/0x390 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574456]  [<ffffffff81087866>] kthread+0x96/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574466]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574475]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574484]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574493] INFO: task z_wr_int/12:1311 blocked for more than 120 seconds.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574500] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574506] z_wr_int/12     D 0000000000000000     0  1311      2 0x00000000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574517]  ffff88012238dbe0 0000000000000046 ffff88012238dfd8 ffff88012238c000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574528]  0000000000013d00 ffff880121c91a98 ffff88012238dfd8 0000000000013d00
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574539]  ffff88012229adc0 ffff880121c916e0 ffffc900112a37b0 ffffc90012c22c30
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574550] Call Trace:
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574561]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574586]  [<ffffffffa00b9246>] ? kmem_free_debug+0x16/0x20 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574597]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574674]  [<ffffffffa01e5d88>] zio_remove_child+0x48/0xf0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574750]  [<ffffffffa01ea763>] zio_done+0x273/0xb80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574829]  [<ffffffffa01b22f4>] ? vdev_mirror_map_free+0x24/0x30 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574905]  [<ffffffffa01eab22>] zio_done+0x632/0xb80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574916]  [<ffffffff815c1afe>] ? mutex_lock+0x1e/0x50
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.574992]  [<ffffffffa01e5b53>] ? zio_wait_for_children+0x63/0x80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575070]  [<ffffffffa01e6af0>] zio_execute+0xb0/0x150 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575080]  [<ffffffff81038c79>] ? default_spin_lock_flags+0x9/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575106]  [<ffffffffa00bbb00>] taskq_thread+0x1c0/0x390 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575116]  [<ffffffff8105f600>] ? default_wake_function+0x0/0x20
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575142]  [<ffffffffa00bb940>] ? taskq_thread+0x0/0x390 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575152]  [<ffffffff81087866>] kthread+0x96/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575162]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575171]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575180]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575189] INFO: task z_wr_int/14:1313 blocked for more than 120 seconds.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575196] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575202] z_wr_int/14     D 0000000000000000     0  1313      2 0x00000000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575213]  ffff88011cbb7be0 0000000000000046 ffff88011cbb7fd8 ffff88011cbb6000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575224]  0000000000013d00 ffff8801201e3178 ffff88011cbb7fd8 0000000000013d00
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575235]  ffff88009dd416e0 ffff8801201e2dc0 ffffc900115823f8 ffffc90012c22c30
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575246] Call Trace:
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575257]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575283]  [<ffffffffa00b9246>] ? kmem_free_debug+0x16/0x20 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575294]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575370]  [<ffffffffa01e5d88>] zio_remove_child+0x48/0xf0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575446]  [<ffffffffa01ea763>] zio_done+0x273/0xb80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575525]  [<ffffffffa01b22f4>] ? vdev_mirror_map_free+0x24/0x30 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575601]  [<ffffffffa01eab22>] zio_done+0x632/0xb80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575612]  [<ffffffff815c1afe>] ? mutex_lock+0x1e/0x50
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575687]  [<ffffffffa01e5b53>] ? zio_wait_for_children+0x63/0x80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575764]  [<ffffffffa01e6af0>] zio_execute+0xb0/0x150 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575773]  [<ffffffff81038c79>] ? default_spin_lock_flags+0x9/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575800]  [<ffffffffa00bbb00>] taskq_thread+0x1c0/0x390 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575810]  [<ffffffff8105f600>] ? default_wake_function+0x0/0x20
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575836]  [<ffffffffa00bb940>] ? taskq_thread+0x0/0x390 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575846]  [<ffffffff81087866>] kthread+0x96/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575855]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575865]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575874]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575938] INFO: task txg_sync:1461 blocked for more than 120 seconds.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575944] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575951] txg_sync        D 0000000000000001     0  1461      2 0x00000000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575979]  ffff88010884dbc0 0000000000000046 ffff88010884dfd8 ffff88010884c000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.575990]  0000000000013d00 ffff880120665f38 ffff88010884dfd8 0000000000013d00
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576001]  ffff88011e8b16e0 ffff880120665b80 ffff8801202dbc00 ffffc900112523d8
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576012] Call Trace:
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576042]  [<ffffffffa00bed37>] cv_wait_common+0x77/0xd0 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576054]  [<ffffffff81087fb0>] ? autoremove_wake_function+0x0/0x40
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576081]  [<ffffffffa00bedc3>] __cv_wait+0x13/0x20 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576160]  [<ffffffffa01e9023>] zio_wait+0xf3/0x1b0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576231]  [<ffffffffa01852a9>] dsl_pool_sync+0xd9/0x4a0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576308]  [<ffffffffa01e601e>] ? zio_destroy+0xae/0xf0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576385]  [<ffffffffa019a02b>] spa_sync+0x3ab/0x9b0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576396]  [<ffffffff81087fc6>] ? autoremove_wake_function+0x16/0x40
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576408]  [<ffffffff8104e413>] ? __wake_up+0x53/0x70
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576486]  [<ffffffffa01a8621>] txg_sync_thread+0x241/0x3c0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576565]  [<ffffffffa01a83e0>] ? txg_sync_thread+0x0/0x3c0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576591]  [<ffffffffa00bb158>] thread_generic_wrapper+0x78/0x90 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576617]  [<ffffffffa00bb0e0>] ? thread_generic_wrapper+0x0/0x90 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576627]  [<ffffffff81087866>] kthread+0x96/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576637]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576647]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576656]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576710] INFO: task nautilus:5479 blocked for more than 120 seconds.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576716] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576723] nautilus        D 0000000000000000     0  5479   2742 0x00000000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576734]  ffff880088ddfb88 0000000000000082 ffff880088ddffd8 ffff880088dde000
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576745]  0000000000013d00 ffff88004ded03b8 ffff880088ddffd8 0000000000013d00
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576756]  ffff8801206244a0 ffff88004ded0000 ffff880088ddfba8 ffff8801223f0330
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576767] Call Trace:
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576796]  [<ffffffffa00bed37>] cv_wait_common+0x77/0xd0 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576807]  [<ffffffff81087fb0>] ? autoremove_wake_function+0x0/0x40
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576834]  [<ffffffffa00bedc3>] __cv_wait+0x13/0x20 [spl]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576915]  [<ffffffffa01a7b53>] txg_wait_open+0x73/0xb0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.576979]  [<ffffffffa016e1ad>] dmu_tx_wait+0xed/0xf0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.577058]  [<ffffffffa01daf8e>] zfs_write+0x38e/0xca0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.577138]  [<ffffffffa01ed672>] zpl_write_common+0x52/0x80 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.577215]  [<ffffffffa01ed708>] zpl_write+0x68/0xa0 [zfs]
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.577227]  [<ffffffff81164e46>] vfs_write+0xc6/0x180
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.577237]  [<ffffffff81165161>] sys_write+0x51/0x90
Sep 21 19:19:55 Smartyv-Ubuntu kernel: [16801.577246]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b

---

### Post by PhilipVinc on 2011-09-21
It now froze again. I found it once again completely frozen with Hard Drives Spun Down.

This time the system log hints at some problems with the wireless network ( I am connected via ethernet, but there is also a wifi network around, to wich he has a stored password).

If anyone could help, I would appreciate.

> Sep 21 21:17:01 Smartyv-Ubuntu CRON[3031]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 21 21:22:01 Smartyv-Ubuntu wpa_supplicant[788]: CTRL-EVENT-DISCONNECTED bssid=00:24:36:ab:b1:4d reason=0
Sep 21 21:22:01 Smartyv-Ubuntu NetworkManager[494]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Sep 21 21:22:01 Smartyv-Ubuntu kernel: [ 5289.713936] cfg80211: All devices are disconnected, going to restore regulatory settings
Sep 21 21:22:01 Smartyv-Ubuntu kernel: [ 5289.713955] cfg80211: Restoring regulatory settings
Sep 21 21:22:01 Smartyv-Ubuntu kernel: [ 5289.713971] cfg80211: Calling CRDA to update world regulatory domain
Sep 21 21:22:01 Smartyv-Ubuntu kernel: [ 5289.728263] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Sep 21 21:22:01 Smartyv-Ubuntu kernel: [ 5289.728284] cfg80211: World regulatory domain updated:
Sep 21 21:22:01 Smartyv-Ubuntu kernel: [ 5289.728291] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 21 21:22:01 Smartyv-Ubuntu kernel: [ 5289.728300] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 21 21:22:01 Smartyv-Ubuntu kernel: [ 5289.728310] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 21 21:22:01 Smartyv-Ubuntu kernel: [ 5289.728318] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 21 21:22:01 Smartyv-Ubuntu kernel: [ 5289.728327] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 21 21:22:01 Smartyv-Ubuntu kernel: [ 5289.728335] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 21 21:22:01 Smartyv-Ubuntu NetworkManager[494]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep 21 21:22:02 Smartyv-Ubuntu wpa_supplicant[788]: Trying to associate with 00:24:36:ab:b1:4d (SSID='Network di Meridiano Zero' freq=2452 MHz)
Sep 21 21:22:02 Smartyv-Ubuntu NetworkManager[494]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.882120] wlan0: authenticate with 00:24:36:ab:b1:4d (try 1)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.884509] wlan0: authenticated
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.884565] wlan0: associate with 00:24:36:ab:b1:4d (try 1)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.888088] wlan0: RX AssocResp from 00:24:36:ab:b1:4d (capab=0x431 status=0 aid=3)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.888097] wlan0: associated
Sep 21 21:22:02 Smartyv-Ubuntu NetworkManager[494]: <info> (wlan0): supplicant connection state:  associating -> associated
Sep 21 21:22:02 Smartyv-Ubuntu wpa_supplicant[788]: Associated with 00:24:36:ab:b1:4d
Sep 21 21:22:02 Smartyv-Ubuntu NetworkManager[494]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.897110] cfg80211: Calling CRDA for country: IT
Sep 21 21:22:02 Smartyv-Ubuntu wpa_supplicant[788]: WPA: Key negotiation completed with 00:24:36:ab:b1:4d [PTK=CCMP GTK=CCMP]
Sep 21 21:22:02 Smartyv-Ubuntu wpa_supplicant[788]: CTRL-EVENT-CONNECTED - Connection to 00:24:36:ab:b1:4d completed (reauth) [id=0 id_str=]
Sep 21 21:22:02 Smartyv-Ubuntu NetworkManager[494]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Sep 21 21:22:02 Smartyv-Ubuntu NetworkManager[494]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908399] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908409] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908414] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908418] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908423] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908427] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908431] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908435] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908439] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908444] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908453] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908457] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908461] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908466] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908469] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908474] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908477] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908482] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908485] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908490] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908494] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908498] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908502] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908506] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908510] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908514] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908517] cfg80211: Disabling freq 2484 MHz
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908526] cfg80211: Regulatory domain changed to country: IT
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908529] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908533] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908537] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908541] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 21 21:22:02 Smartyv-Ubuntu kernel: [ 5290.908545] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Sep 21 21:22:33 Smartyv-Ubuntu wpa_supplicant[788]: CTRL-EVENT-DISCONNECTED bssid=00:24:36:ab:b1:4d reason=0
Sep 21 21:22:33 Smartyv-Ubuntu NetworkManager[494]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Sep 21 21:22:33 Smartyv-Ubuntu kernel: [ 5321.685786] cfg80211: All devices are disconnected, going to restore regulatory settings
Sep 21 21:22:33 Smartyv-Ubuntu kernel: [ 5321.685805] cfg80211: Restoring regulatory settings
Sep 21 21:22:33 Smartyv-Ubuntu kernel: [ 5321.685820] cfg80211: Calling CRDA to update world regulatory domain
Sep 21 21:22:33 Smartyv-Ubuntu kernel: [ 5321.699759] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Sep 21 21:22:33 Smartyv-Ubuntu kernel: [ 5321.699780] cfg80211: World regulatory domain updated:
Sep 21 21:22:33 Smartyv-Ubuntu kernel: [ 5321.699787] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 21 21:22:33 Smartyv-Ubuntu kernel: [ 5321.699796] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 21 21:22:33 Smartyv-Ubuntu kernel: [ 5321.699805] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 21 21:22:33 Smartyv-Ubuntu kernel: [ 5321.699814] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 21 21:22:33 Smartyv-Ubuntu kernel: [ 5321.699823] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 21 21:22:33 Smartyv-Ubuntu kernel: [ 5321.699831] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 21 21:22:33 Smartyv-Ubuntu NetworkManager[494]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep 21 21:22:34 Smartyv-Ubuntu wpa_supplicant[788]: Trying to associate with 00:24:36:ab:b1:4d (SSID='Network di Meridiano Zero' freq=2452 MHz)
Sep 21 21:22:34 Smartyv-Ubuntu NetworkManager[494]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.851803] wlan0: authenticate with 00:24:36:ab:b1:4d (try 1)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.854076] wlan0: authenticated
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.871260] wlan0: associate with 00:24:36:ab:b1:4d (try 1)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.875042] wlan0: RX AssocResp from 00:24:36:ab:b1:4d (capab=0x431 status=0 aid=3)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.875051] wlan0: associated
Sep 21 21:22:34 Smartyv-Ubuntu NetworkManager[494]: <info> (wlan0): supplicant connection state:  associating -> associated
Sep 21 21:22:34 Smartyv-Ubuntu wpa_supplicant[788]: Associated with 00:24:36:ab:b1:4d
Sep 21 21:22:34 Smartyv-Ubuntu NetworkManager[494]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.884848] cfg80211: Calling CRDA for country: IT
Sep 21 21:22:34 Smartyv-Ubuntu wpa_supplicant[788]: WPA: Key negotiation completed with 00:24:36:ab:b1:4d [PTK=CCMP GTK=CCMP]
Sep 21 21:22:34 Smartyv-Ubuntu wpa_supplicant[788]: CTRL-EVENT-CONNECTED - Connection to 00:24:36:ab:b1:4d completed (reauth) [id=0 id_str=]
Sep 21 21:22:34 Smartyv-Ubuntu NetworkManager[494]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Sep 21 21:22:34 Smartyv-Ubuntu NetworkManager[494]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893485] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893495] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893499] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893504] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893508] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893512] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893516] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893521] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893524] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893529] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893532] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893537] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893540] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893544] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893548] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893552] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893556] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893560] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893564] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893568] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893572] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893576] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893580] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893584] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893588] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893592] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893596] cfg80211: Disabling freq 2484 MHz
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893604] cfg80211: Regulatory domain changed to country: IT
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893607] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893611] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893615] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893619] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 21 21:22:34 Smartyv-Ubuntu kernel: [ 5322.893623] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Sep 21 21:28:21 Smartyv-Ubuntu kernel: [ 5669.840328] r8169 0000:03:00.0: eth0: link up
Sep 21 21:28:21 Smartyv-Ubuntu kernel: [ 5669.840390] NOHZ: local_softirq_pending 08
Sep 21 21:28:21 Smartyv-Ubuntu kernel: [ 5669.845327] NOHZ: local_softirq_pending 08
Sep 21 21:28:21 Smartyv-Ubuntu kernel: [ 5669.845679] NOHZ: local_softirq_pending 08
Sep 21 21:28:21 Smartyv-Ubuntu kernel: [ 5669.846072] NOHZ: local_softirq_pending 08
Sep 21 21:28:21 Smartyv-Ubuntu kernel: [ 5669.846428] NOHZ: local_softirq_pending 08
Sep 21 21:28:21 Smartyv-Ubuntu kernel: [ 5669.846823] NOHZ: local_softirq_pending 08
Sep 21 21:28:21 Smartyv-Ubuntu kernel: [ 5669.847182] NOHZ: local_softirq_pending 08
Sep 21 21:28:21 Smartyv-Ubuntu kernel: [ 5669.847533] NOHZ: local_softirq_pending 08

---

### Post by edubidu on 2012-04-18
Hi, I have the same problem, but not only zfs is hanging. Have a ubuntu 11.10 64 bit server Linux 3.0.0-17-server x86_64, connected to some iscsi lefthand storages with some zpools.

Even a kill -9 does not help.

---

### Post by finn on 2012-05-08
Have you tried raising skinny elephants?  It might let you shut the system down cleanly next time this occurs.

[http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html](http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html)

---

