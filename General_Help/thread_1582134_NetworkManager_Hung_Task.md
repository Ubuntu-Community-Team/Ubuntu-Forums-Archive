---
title: "NetworkManager Hung Task"
date: 2010-09-26
forum: General Help
---

### Post by VH-BIL on 2010-09-26
I am having trouble with the system hanging now that I have installed a NetGear WG311v3 WIFI card with ndiswrapper. It does not happen all of the time and I can not kill the NetworkManager as sudo does not work when the system hangs.

Does anyone know how to resolve this?

```
Sep 26 02:30:45 K10 kernel: [ 3120.496021] INFO: task NetworkManager:1052 blocked for more than 120 seconds.
Sep 26 02:30:45 K10 kernel: [ 3120.496024] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 26 02:30:45 K10 kernel: [ 3120.496026] NetworkManage D 000071de     0  1052      1 0x00000000
Sep 26 02:30:45 K10 kernel: [ 3120.496030]  efa15e4c 00000082 fffffff5 000071de 00000000 c0849760 ef9cf56c c0849760
Sep 26 02:30:45 K10 kernel: [ 3120.496036]  51e2aa1f 000002b7 c0849760 c0849760 ef9cf56c c0849760 c0849760 f0278a80
Sep 26 02:30:45 K10 kernel: [ 3120.496041]  51e220a4 000002b7 ef9cf2c0 c07935e0 c07935e4 ffffffff efa15e78 c058bd36
Sep 26 02:30:45 K10 kernel: [ 3120.496046] Call Trace:
Sep 26 02:30:45 K10 kernel: [ 3120.496053]  [<c058bd36>] __mutex_lock_slowpath+0xc6/0x130
Sep 26 02:30:45 K10 kernel: [ 3120.496056]  [<c058bc55>] mutex_lock+0x25/0x40
Sep 26 02:30:45 K10 kernel: [ 3120.496059]  [<c04cf692>] rtnl_lock+0x12/0x20
Sep 26 02:30:45 K10 kernel: [ 3120.496062]  [<c05710ae>] wext_handle_ioctl+0x4e/0xc0
Sep 26 02:30:45 K10 kernel: [ 3120.496065]  [<c058cecd>] ? _spin_lock+0xd/0x10
Sep 26 02:30:45 K10 kernel: [ 3120.496068]  [<c04c6b74>] dev_ioctl+0x614/0x720
Sep 26 02:30:45 K10 kernel: [ 3120.496071]  [<c021b803>] ? d_alloc+0x23/0x190
Sep 26 02:30:45 K10 kernel: [ 3120.496074]  [<c0239285>] ? inotify_d_instantiate+0x45/0x60
Sep 26 02:30:45 K10 kernel: [ 3120.496077]  [<c021a5fc>] ? __d_instantiate+0x9c/0xd0
Sep 26 02:30:45 K10 kernel: [ 3120.496080]  [<c02f6648>] ? security_d_instantiate+0x18/0x30
Sep 26 02:30:45 K10 kernel: [ 3120.496083]  [<c04b3bc3>] sock_ioctl+0x1d3/0x270
Sep 26 02:30:45 K10 kernel: [ 3120.496086]  [<c04b39f0>] ? sock_ioctl+0x0/0x270
Sep 26 02:30:45 K10 kernel: [ 3120.496088]  [<c0216c61>] vfs_ioctl+0x21/0x90
Sep 26 02:30:45 K10 kernel: [ 3120.496091]  [<c0216f49>] do_vfs_ioctl+0x79/0x310
Sep 26 02:30:45 K10 kernel: [ 3120.496094]  [<c0354529>] ? copy_to_user+0x39/0x130
Sep 26 02:30:45 K10 kernel: [ 3120.496096]  [<c0217247>] sys_ioctl+0x67/0x80
Sep 26 02:30:45 K10 kernel: [ 3120.496099]  [<c01033ec>] syscall_call+0x7/0xb
Sep 26 02:30:45 K10 kernel: [ 3120.496114] INFO: task ksysguardd:1754 blocked for more than 120 seconds.
Sep 26 02:30:45 K10 kernel: [ 3120.496115] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 26 02:30:45 K10 kernel: [ 3120.496117] ksysguardd    D 00027a27     0  1754   1731 0x00000000
Sep 26 02:30:45 K10 kernel: [ 3120.496121]  edadde90 00000082 00000004 00027a27 00000000 c0849760 f6ba68ac c0849760
Sep 26 02:30:45 K10 kernel: [ 3120.496126]  e6c2fec3 000002b6 c0849760 c0849760 f6ba68ac c0849760 c0849760 f6407880
Sep 26 02:30:45 K10 kernel: [ 3120.496131]  e6b4fda2 000002b6 f6ba6600 c07935e0 c07935e4 ffffffff edaddebc c058bd36
Sep 26 02:30:45 K10 kernel: [ 3120.496136] Call Trace:
Sep 26 02:30:45 K10 kernel: [ 3120.496139]  [<c058bd36>] __mutex_lock_slowpath+0xc6/0x130
Sep 26 02:30:45 K10 kernel: [ 3120.496143]  [<c0206b5d>] ? nameidata_to_filp+0x5d/0x70
Sep 26 02:30:45 K10 kernel: [ 3120.496145]  [<c058bc55>] mutex_lock+0x25/0x40
Sep 26 02:30:45 K10 kernel: [ 3120.496148]  [<c04cf692>] rtnl_lock+0x12/0x20
Sep 26 02:30:45 K10 kernel: [ 3120.496151]  [<c0570070>] wireless_dev_seq_start+0x20/0xb0
Sep 26 02:30:45 K10 kernel: [ 3120.496154]  [<c0223730>] ? seq_read+0x0/0x3a0
Sep 26 02:30:45 K10 kernel: [ 3120.496157]  [<c022380b>] seq_read+0xdb/0x3a0
Sep 26 02:30:45 K10 kernel: [ 3120.496160]  [<c0223730>] ? seq_read+0x0/0x3a0
Sep 26 02:30:45 K10 kernel: [ 3120.496162]  [<c024cef7>] proc_reg_read+0x67/0xa0
Sep 26 02:30:45 K10 kernel: [ 3120.496165]  [<c058cecd>] ? _spin_lock+0xd/0x10
Sep 26 02:30:45 K10 kernel: [ 3120.496168]  [<c0208e0f>] vfs_read+0x9f/0x1a0
Sep 26 02:30:45 K10 kernel: [ 3120.496171]  [<c024ce90>] ? proc_reg_read+0x0/0xa0
Sep 26 02:30:45 K10 kernel: [ 3120.496173]  [<c0208fc2>] sys_read+0x42/0x70
Sep 26 02:30:45 K10 kernel: [ 3120.496176]  [<c01033ec>] syscall_call+0x7/0xb
Sep 26 02:30:45 K10 kernel: [ 3120.496183] INFO: task skype:1875 blocked for more than 120 seconds.
Sep 26 02:30:45 K10 kernel: [ 3120.496184] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 26 02:30:45 K10 kernel: [ 3120.496186] skype         D 00001bd1     0  1875   1619 0x00000000
Sep 26 02:30:45 K10 kernel: [ 3120.496189]  ecedde70 00200082 76ad2067 00001bd1 00000000 c0849760 effe28ec c0849760
Sep 26 02:30:45 K10 kernel: [ 3120.496194]  e154876e 000002b8 c0849760 c0849760 effe28ec c0849760 c0849760 f6407340
Sep 26 02:30:45 K10 kernel: [ 3120.496199]  e153429b 000002b8 effe2640 c07935e0 c07935e4 ffffffff ecedde9c c058bd36
Sep 26 02:30:45 K10 kernel: [ 3120.496205] Call Trace:
Sep 26 02:30:45 K10 kernel: [ 3120.496208]  [<c058bd36>] __mutex_lock_slowpath+0xc6/0x130
Sep 26 02:30:45 K10 kernel: [ 3120.496211]  [<c04b85a2>] ? sk_prot_alloc+0x32/0x130
Sep 26 02:30:45 K10 kernel: [ 3120.496213]  [<c058bc55>] mutex_lock+0x25/0x40
Sep 26 02:30:45 K10 kernel: [ 3120.496216]  [<c04cf692>] rtnl_lock+0x12/0x20
Sep 26 02:30:45 K10 kernel: [ 3120.496219]  [<c04c6665>] dev_ioctl+0x105/0x720
Sep 26 02:30:45 K10 kernel: [ 3120.496221]  [<c058cecd>] ? _spin_lock+0xd/0x10
Sep 26 02:30:45 K10 kernel: [ 3120.496224]  [<c0239285>] ? inotify_d_instantiate+0x45/0x60
Sep 26 02:30:45 K10 kernel: [ 3120.496227]  [<c021a5fc>] ? __d_instantiate+0x9c/0xd0
Sep 26 02:30:45 K10 kernel: [ 3120.496229]  [<c02f6648>] ? security_d_instantiate+0x18/0x30
Sep 26 02:30:45 K10 kernel: [ 3120.496232]  [<c021a675>] ? d_instantiate+0x45/0x60
Sep 26 02:30:45 K10 kernel: [ 3120.496235]  [<c04b3dfd>] ? sock_attach_fd+0x7d/0xc0
Sep 26 02:30:45 K10 kernel: [ 3120.496238]  [<c0511080>] ? udp_ioctl+0x0/0x80
Sep 26 02:30:45 K10 kernel: [ 3120.496240]  [<c04b3a7a>] sock_ioctl+0x8a/0x270
Sep 26 02:30:45 K10 kernel: [ 3120.496243]  [<c04b39f0>] ? sock_ioctl+0x0/0x270
Sep 26 02:30:45 K10 kernel: [ 3120.496245]  [<c0216c61>] vfs_ioctl+0x21/0x90
Sep 26 02:30:45 K10 kernel: [ 3120.496248]  [<c0216f49>] do_vfs_ioctl+0x79/0x310
Sep 26 02:30:45 K10 kernel: [ 3120.496250]  [<c0217247>] sys_ioctl+0x67/0x80
Sep 26 02:30:45 K10 kernel: [ 3120.496253]  [<c01033ec>] syscall_call+0x7/0xb
Sep 26 02:32:45 K10 kernel: [ 3240.496519] INFO: task NetworkManager:1052 blocked for more than 120 seconds.
Sep 26 02:32:45 K10 kernel: [ 3240.496522] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 26 02:32:45 K10 kernel: [ 3240.496524] NetworkManage D 000071de     0  1052      1 0x00000000
Sep 26 02:32:45 K10 kernel: [ 3240.496528]  efa15e4c 00000082 fffffff5 000071de 00000000 c0849760 ef9cf56c c0849760
Sep 26 02:32:45 K10 kernel: [ 3240.496534]  51e2aa1f 000002b7 c0849760 c0849760 ef9cf56c c0849760 c0849760 f0278a80
Sep 26 02:32:45 K10 kernel: [ 3240.496539]  51e220a4 000002b7 ef9cf2c0 c07935e0 c07935e4 ffffffff efa15e78 c058bd36
Sep 26 02:32:45 K10 kernel: [ 3240.496545] Call Trace:
Sep 26 02:32:45 K10 kernel: [ 3240.496551]  [<c058bd36>] __mutex_lock_slowpath+0xc6/0x130
Sep 26 02:32:45 K10 kernel: [ 3240.496554]  [<c058bc55>] mutex_lock+0x25/0x40
Sep 26 02:32:45 K10 kernel: [ 3240.496557]  [<c04cf692>] rtnl_lock+0x12/0x20
Sep 26 02:32:45 K10 kernel: [ 3240.496560]  [<c05710ae>] wext_handle_ioctl+0x4e/0xc0
Sep 26 02:32:45 K10 kernel: [ 3240.496563]  [<c058cecd>] ? _spin_lock+0xd/0x10
Sep 26 02:32:45 K10 kernel: [ 3240.496566]  [<c04c6b74>] dev_ioctl+0x614/0x720
Sep 26 02:32:45 K10 kernel: [ 3240.496569]  [<c021b803>] ? d_alloc+0x23/0x190
Sep 26 02:32:45 K10 kernel: [ 3240.496572]  [<c0239285>] ? inotify_d_instantiate+0x45/0x60
Sep 26 02:32:45 K10 kernel: [ 3240.496575]  [<c021a5fc>] ? __d_instantiate+0x9c/0xd0
Sep 26 02:32:45 K10 kernel: [ 3240.496578]  [<c02f6648>] ? security_d_instantiate+0x18/0x30
Sep 26 02:32:45 K10 kernel: [ 3240.496581]  [<c04b3bc3>] sock_ioctl+0x1d3/0x270
Sep 26 02:32:45 K10 kernel: [ 3240.496584]  [<c04b39f0>] ? sock_ioctl+0x0/0x270
Sep 26 02:32:45 K10 kernel: [ 3240.496586]  [<c0216c61>] vfs_ioctl+0x21/0x90
Sep 26 02:32:45 K10 kernel: [ 3240.496589]  [<c0216f49>] do_vfs_ioctl+0x79/0x310
Sep 26 02:32:45 K10 kernel: [ 3240.496592]  [<c0354529>] ? copy_to_user+0x39/0x130
Sep 26 02:32:45 K10 kernel: [ 3240.496594]  [<c0217247>] sys_ioctl+0x67/0x80
Sep 26 02:32:45 K10 kernel: [ 3240.496597]  [<c01033ec>] syscall_call+0x7/0xb
Sep 26 02:32:45 K10 kernel: [ 3240.496609] INFO: task plasma-desktop:2275 blocked for more than 120 seconds.
Sep 26 02:32:45 K10 kernel: [ 3240.496610] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 26 02:32:45 K10 kernel: [ 3240.496612] plasma-deskto D 00000000     0  2275      1 0x00000000
Sep 26 02:32:45 K10 kernel: [ 3240.496615]  e2cfbd08 00000082 f7028e00 00000000 00000000 c0849760 ebd9b5ac c0849760
Sep 26 02:32:45 K10 kernel: [ 3240.496621]  a12f89b5 000002c3 c0849760 c0849760 ebd9b5ac c0849760 c0849760 f6bf6380
Sep 26 02:32:45 K10 kernel: [ 3240.496626]  a12e4375 000002c3 ebd9b300 c07935e0 c07935e4 ffffffff e2cfbd34 c058bd36
Sep 26 02:32:45 K10 kernel: [ 3240.496631] Call Trace:
Sep 26 02:32:45 K10 kernel: [ 3240.496634]  [<c058bd36>] __mutex_lock_slowpath+0xc6/0x130
Sep 26 02:32:45 K10 kernel: [ 3240.496637]  [<c058bc55>] mutex_lock+0x25/0x40
Sep 26 02:32:45 K10 kernel: [ 3240.496639]  [<c04cf692>] rtnl_lock+0x12/0x20
Sep 26 02:32:45 K10 kernel: [ 3240.496642]  [<c04cf6b0>] rtnetlink_rcv+0x10/0x30
Sep 26 02:32:45 K10 kernel: [ 3240.496645]  [<c04e2889>] netlink_unicast+0x259/0x280
Sep 26 02:32:45 K10 kernel: [ 3240.496647]  [<c04e34aa>] netlink_sendmsg+0x1ba/0x2a0
Sep 26 02:32:45 K10 kernel: [ 3240.496651]  [<c0321c55>] ? apparmor_socket_sendmsg+0x15/0x20
Sep 26 02:32:45 K10 kernel: [ 3240.496653]  [<c04b4f85>] sock_sendmsg+0xe5/0x110
Sep 26 02:32:45 K10 kernel: [ 3240.496657]  [<c01cbaaa>] ? T.904+0x3da/0x480
Sep 26 02:32:45 K10 kernel: [ 3240.496660]  [<c0167810>] ? autoremove_wake_function+0x0/0x50
Sep 26 02:32:45 K10 kernel: [ 3240.496663]  [<c013aa95>] ? __wake_up+0x45/0x60
Sep 26 02:32:45 K10 kernel: [ 3240.496666]  [<c04e3182>] ? netlink_insert+0x72/0x120
Sep 26 02:32:45 K10 kernel: [ 3240.496668]  [<c04b50e2>] sys_sendto+0xe2/0x130
Sep 26 02:32:45 K10 kernel: [ 3240.496671]  [<c021a5fc>] ? __d_instantiate+0x9c/0xd0
Sep 26 02:32:45 K10 kernel: [ 3240.496674]  [<c02f6648>] ? security_d_instantiate+0x18/0x30
Sep 26 02:32:45 K10 kernel: [ 3240.496677]  [<c021a675>] ? d_instantiate+0x45/0x60
Sep 26 02:32:45 K10 kernel: [ 3240.496679]  [<c04b3dfd>] ? sock_attach_fd+0x7d/0xc0
Sep 26 02:32:45 K10 kernel: [ 3240.496682]  [<c058cecd>] ? _spin_lock+0xd/0x10
Sep 26 02:32:45 K10 kernel: [ 3240.496685]  [<c020640c>] ? fd_install+0x4c/0x60
Sep 26 02:32:45 K10 kernel: [ 3240.496688]  [<c04b3e82>] ? sock_map_fd+0x42/0x70
Sep 26 02:32:45 K10 kernel: [ 3240.496690]  [<c04b5fa3>] sys_socketcall+0x183/0x280
Sep 26 02:32:45 K10 kernel: [ 3240.496693]  [<c01033ec>] syscall_call+0x7/0xb
Sep 26 02:32:45 K10 kernel: [ 3240.496699] INFO: task ksysguardd:1754 blocked for more than 120 seconds.
Sep 26 02:32:45 K10 kernel: [ 3240.496700] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 26 02:32:45 K10 kernel: [ 3240.496702] ksysguardd    D 00027a27     0  1754   1731 0x00000000
Sep 26 02:32:45 K10 kernel: [ 3240.496705]  edadde90 00000082 00000004 00027a27 00000000 c0849760 f6ba68ac c0849760
Sep 26 02:32:45 K10 kernel: [ 3240.496710]  e6c2fec3 000002b6 c0849760 c0849760 f6ba68ac c0849760 c0849760 f6407880
Sep 26 02:32:45 K10 kernel: [ 3240.496715]  e6b4fda2 000002b6 f6ba6600 c07935e0 c07935e4 ffffffff edaddebc c058bd36
Sep 26 02:32:45 K10 kernel: [ 3240.496721] Call Trace:
Sep 26 02:32:45 K10 kernel: [ 3240.496724]  [<c058bd36>] __mutex_lock_slowpath+0xc6/0x130
Sep 26 02:32:45 K10 kernel: [ 3240.496727]  [<c0206b5d>] ? nameidata_to_filp+0x5d/0x70
Sep 26 02:32:45 K10 kernel: [ 3240.496729]  [<c058bc55>] mutex_lock+0x25/0x40
Sep 26 02:32:45 K10 kernel: [ 3240.496732]  [<c04cf692>] rtnl_lock+0x12/0x20
Sep 26 02:32:45 K10 kernel: [ 3240.496735]  [<c0570070>] wireless_dev_seq_start+0x20/0xb0
Sep 26 02:32:45 K10 kernel: [ 3240.496738]  [<c0223730>] ? seq_read+0x0/0x3a0
Sep 26 02:32:45 K10 kernel: [ 3240.496741]  [<c022380b>] seq_read+0xdb/0x3a0
Sep 26 02:32:45 K10 kernel: [ 3240.496743]  [<c0223730>] ? seq_read+0x0/0x3a0
Sep 26 02:32:45 K10 kernel: [ 3240.496746]  [<c024cef7>] proc_reg_read+0x67/0xa0
Sep 26 02:32:45 K10 kernel: [ 3240.496749]  [<c058cecd>] ? _spin_lock+0xd/0x10
Sep 26 02:32:45 K10 kernel: [ 3240.496752]  [<c0208e0f>] vfs_read+0x9f/0x1a0
Sep 26 02:32:45 K10 kernel: [ 3240.496754]  [<c024ce90>] ? proc_reg_read+0x0/0xa0
Sep 26 02:32:45 K10 kernel: [ 3240.496757]  [<c0208fc2>] sys_read+0x42/0x70
Sep 26 02:32:45 K10 kernel: [ 3240.496760]  [<c01033ec>] syscall_call+0x7/0xb
Sep 26 02:32:45 K10 kernel: [ 3240.496766] INFO: task skype:1875 blocked for more than 120 seconds.
Sep 26 02:32:45 K10 kernel: [ 3240.496768] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 26 02:32:45 K10 kernel: [ 3240.496770] skype         D 00001bd1     0  1875   1619 0x00000000
Sep 26 02:32:45 K10 kernel: [ 3240.496773]  ecedde70 00200082 76ad2067 00001bd1 00000000 c0849760 effe28ec c0849760
Sep 26 02:32:45 K10 kernel: [ 3240.496778]  e154876e 000002b8 c0849760 c0849760 effe28ec c0849760 c0849760 f6407340
Sep 26 02:32:45 K10 kernel: [ 3240.496783]  e153429b 000002b8 effe2640 c07935e0 c07935e4 ffffffff ecedde9c c058bd36
Sep 26 02:32:45 K10 kernel: [ 3240.496788] Call Trace:
Sep 26 02:32:45 K10 kernel: [ 3240.496791]  [<c058bd36>] __mutex_lock_slowpath+0xc6/0x130
Sep 26 02:32:45 K10 kernel: [ 3240.496794]  [<c04b85a2>] ? sk_prot_alloc+0x32/0x130
Sep 26 02:32:45 K10 kernel: [ 3240.496797]  [<c058bc55>] mutex_lock+0x25/0x40
Sep 26 02:32:45 K10 kernel: [ 3240.496800]  [<c04cf692>] rtnl_lock+0x12/0x20
Sep 26 02:32:45 K10 kernel: [ 3240.496802]  [<c04c6665>] dev_ioctl+0x105/0x720
Sep 26 02:32:45 K10 kernel: [ 3240.496805]  [<c058cecd>] ? _spin_lock+0xd/0x10
Sep 26 02:32:45 K10 kernel: [ 3240.496808]  [<c0239285>] ? inotify_d_instantiate+0x45/0x60
Sep 26 02:32:45 K10 kernel: [ 3240.496810]  [<c021a5fc>] ? __d_instantiate+0x9c/0xd0
Sep 26 02:32:45 K10 kernel: [ 3240.496813]  [<c02f6648>] ? security_d_instantiate+0x18/0x30
Sep 26 02:32:45 K10 kernel: [ 3240.496816]  [<c021a675>] ? d_instantiate+0x45/0x60
Sep 26 02:32:45 K10 kernel: [ 3240.496818]  [<c04b3dfd>] ? sock_attach_fd+0x7d/0xc0
Sep 26 02:32:45 K10 kernel: [ 3240.496821]  [<c0511080>] ? udp_ioctl+0x0/0x80
Sep 26 02:32:45 K10 kernel: [ 3240.496824]  [<c04b3a7a>] sock_ioctl+0x8a/0x270
Sep 26 02:32:45 K10 kernel: [ 3240.496826]  [<c04b39f0>] ? sock_ioctl+0x0/0x270
Sep 26 02:32:45 K10 kernel: [ 3240.496829]  [<c0216c61>] vfs_ioctl+0x21/0x90
Sep 26 02:32:45 K10 kernel: [ 3240.496831]  [<c0216f49>] do_vfs_ioctl+0x79/0x310
Sep 26 02:32:45 K10 kernel: [ 3240.496834]  [<c0217247>] sys_ioctl+0x67/0x80
Sep 26 02:32:45 K10 kernel: [ 3240.496837]  [<c01033ec>] syscall_call+0x7/0xb
Sep 26 02:32:45 K10 kernel: [ 3240.496840] INFO: task ktorrent:2277 blocked for more than 120 seconds.
Sep 26 02:32:45 K10 kernel: [ 3240.496841] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 26 02:32:45 K10 kernel: [ 3240.496843] ktorrent      D 00000000     0  2277      1 0x00000000
Sep 26 02:32:45 K10 kernel: [ 3240.496846]  e2d9dd08 00000086 00000000 00000000 00000000 c0849760 ef85f56c c0849760
Sep 26 02:32:45 K10 kernel: [ 3240.496851]  48d1c2f7 000002ce c0849760 c0849760 ef85f56c c0849760 c0849760 f0b776c0
Sep 26 02:32:45 K10 kernel: [ 3240.496856]  48d02ae6 000002ce ef85f2c0 c07935e0 c07935e4 ffffffff e2d9dd34 c058bd36
Sep 26 02:32:45 K10 kernel: [ 3240.496861] Call Trace:
Sep 26 02:32:45 K10 kernel: [ 3240.496864]  [<c058bd36>] __mutex_lock_slowpath+0xc6/0x130
Sep 26 02:32:45 K10 kernel: [ 3240.496867]  [<c058bc55>] mutex_lock+0x25/0x40
Sep 26 02:32:45 K10 kernel: [ 3240.496870]  [<c04cf692>] rtnl_lock+0x12/0x20
Sep 26 02:32:45 K10 kernel: [ 3240.496872]  [<c04cf6b0>] rtnetlink_rcv+0x10/0x30
Sep 26 02:32:45 K10 kernel: [ 3240.496875]  [<c04e2889>] netlink_unicast+0x259/0x280
Sep 26 02:32:45 K10 kernel: [ 3240.496877]  [<c04e34aa>] netlink_sendmsg+0x1ba/0x2a0
Sep 26 02:32:45 K10 kernel: [ 3240.496880]  [<c0321c55>] ? apparmor_socket_sendmsg+0x15/0x20
Sep 26 02:32:45 K10 kernel: [ 3240.496883]  [<c04b4f85>] sock_sendmsg+0xe5/0x110
Sep 26 02:32:45 K10 kernel: [ 3240.496887]  [<c03b22be>] ? extract_entropy+0x6e/0x120
Sep 26 02:32:45 K10 kernel: [ 3240.496890]  [<c0167810>] ? autoremove_wake_function+0x0/0x50
Sep 26 02:32:45 K10 kernel: [ 3240.496893]  [<c013aa95>] ? __wake_up+0x45/0x60
Sep 26 02:32:45 K10 kernel: [ 3240.496895]  [<c04e3182>] ? netlink_insert+0x72/0x120
Sep 26 02:32:45 K10 kernel: [ 3240.496898]  [<c04b50e2>] sys_sendto+0xe2/0x130
Sep 26 02:32:45 K10 kernel: [ 3240.496901]  [<c021a5fc>] ? __d_instantiate+0x9c/0xd0
Sep 26 02:32:45 K10 kernel: [ 3240.496904]  [<c02f6648>] ? security_d_instantiate+0x18/0x30
Sep 26 02:32:45 K10 kernel: [ 3240.496906]  [<c021a675>] ? d_instantiate+0x45/0x60
Sep 26 02:32:45 K10 kernel: [ 3240.496909]  [<c04b3dfd>] ? sock_attach_fd+0x7d/0xc0
Sep 26 02:32:45 K10 kernel: [ 3240.496912]  [<c058cecd>] ? _spin_lock+0xd/0x10
Sep 26 02:32:45 K10 kernel: [ 3240.496914]  [<c020640c>] ? fd_install+0x4c/0x60
Sep 26 02:32:45 K10 kernel: [ 3240.496917]  [<c04b3e82>] ? sock_map_fd+0x42/0x70
Sep 26 02:32:45 K10 kernel: [ 3240.496920]  [<c04b5fa3>] sys_socketcall+0x183/0x280
Sep 26 02:32:45 K10 kernel: [ 3240.496923]  [<c01033ec>] syscall_call+0x7/0xb
Sep 26 02:34:45 K10 kernel: [ 3360.496019] INFO: task NetworkManager:1052 blocked for more than 120 seconds.
Sep 26 02:34:45 K10 kernel: [ 3360.496022] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 26 02:34:45 K10 kernel: [ 3360.496024] NetworkManage D 000071de     0  1052      1 0x00000000
Sep 26 02:34:45 K10 kernel: [ 3360.496028]  efa15e4c 00000082 fffffff5 000071de 00000000 c0849760 ef9cf56c c0849760
Sep 26 02:34:45 K10 kernel: [ 3360.496034]  51e2aa1f 000002b7 c0849760 c0849760 ef9cf56c c0849760 c0849760 f0278a80
Sep 26 02:34:45 K10 kernel: [ 3360.496039]  51e220a4 000002b7 ef9cf2c0 c07935e0 c07935e4 ffffffff efa15e78 c058bd36
Sep 26 02:34:45 K10 kernel: [ 3360.496044] Call Trace:
Sep 26 02:34:45 K10 kernel: [ 3360.496051]  [<c058bd36>] __mutex_lock_slowpath+0xc6/0x130
Sep 26 02:34:45 K10 kernel: [ 3360.496054]  [<c058bc55>] mutex_lock+0x25/0x40
Sep 26 02:34:45 K10 kernel: [ 3360.496057]  [<c04cf692>] rtnl_lock+0x12/0x20
Sep 26 02:34:45 K10 kernel: [ 3360.496060]  [<c05710ae>] wext_handle_ioctl+0x4e/0xc0
Sep 26 02:34:45 K10 kernel: [ 3360.496063]  [<c058cecd>] ? _spin_lock+0xd/0x10
Sep 26 02:34:45 K10 kernel: [ 3360.496066]  [<c04c6b74>] dev_ioctl+0x614/0x720
Sep 26 02:34:45 K10 kernel: [ 3360.496069]  [<c021b803>] ? d_alloc+0x23/0x190
Sep 26 02:34:45 K10 kernel: [ 3360.496072]  [<c0239285>] ? inotify_d_instantiate+0x45/0x60
Sep 26 02:34:45 K10 kernel: [ 3360.496075]  [<c021a5fc>] ? __d_instantiate+0x9c/0xd0
Sep 26 02:34:45 K10 kernel: [ 3360.496078]  [<c02f6648>] ? security_d_instantiate+0x18/0x30
Sep 26 02:34:45 K10 kernel: [ 3360.496082]  [<c04b3bc3>] sock_ioctl+0x1d3/0x270
Sep 26 02:34:45 K10 kernel: [ 3360.496084]  [<c04b39f0>] ? sock_ioctl+0x0/0x270
Sep 26 02:34:45 K10 kernel: [ 3360.496087]  [<c0216c61>] vfs_ioctl+0x21/0x90
Sep 26 02:34:45 K10 kernel: [ 3360.496089]  [<c0216f49>] do_vfs_ioctl+0x79/0x310
Sep 26 02:34:45 K10 kernel: [ 3360.496092]  [<c0354529>] ? copy_to_user+0x39/0x130
Sep 26 02:34:45 K10 kernel: [ 3360.496095]  [<c0217247>] sys_ioctl+0x67/0x80
Sep 26 02:34:45 K10 kernel: [ 3360.496097]  [<c01033ec>] syscall_call+0x7/0xb
Sep 26 02:34:45 K10 kernel: [ 3360.496101] INFO: task irqbalance:1141 blocked for more than 120 seconds.
Sep 26 02:34:45 K10 kernel: [ 3360.496102] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 26 02:34:45 K10 kernel: [ 3360.496104] irqbalance    D 00022f78     0  1141      1 0x00000000
Sep 26 02:34:45 K10 kernel: [ 3360.496107]  efb8de70 00000086 764fa067 00022f78 00000000 c0849760 efe91c2c c0849760
Sep 26 02:34:45 K10 kernel: [ 3360.496112]  a326067b 000002ec c0849760 c0849760 efe91c2c c0849760 c0849760 f01cee00
Sep 26 02:34:45 K10 kernel: [ 3360.496117]  a3219d84 000002ec efe91980 c07935e0 c07935e4 ffffffff efb8de9c c058bd36
Sep 26 02:34:45 K10 kernel: [ 3360.496123] Call Trace:
Sep 26 02:34:45 K10 kernel: [ 3360.496126]  [<c058bd36>] __mutex_lock_slowpath+0xc6/0x130
Sep 26 02:34:45 K10 kernel: [ 3360.496128]  [<c058bc55>] mutex_lock+0x25/0x40
Sep 26 02:34:45 K10 kernel: [ 3360.496131]  [<c04cf692>] rtnl_lock+0x12/0x20
Sep 26 02:34:45 K10 kernel: [ 3360.496134]  [<c04c695d>] dev_ioctl+0x3fd/0x720
Sep 26 02:34:45 K10 kernel: [ 3360.496136]  [<c021b803>] ? d_alloc+0x23/0x190
Sep 26 02:34:45 K10 kernel: [ 3360.496139]  [<c0239285>] ? inotify_d_instantiate+0x45/0x60
Sep 26 02:34:45 K10 kernel: [ 3360.496141]  [<c021a5fc>] ? __d_instantiate+0x9c/0xd0
Sep 26 02:34:45 K10 kernel: [ 3360.496144]  [<c02f6648>] ? security_d_instantiate+0x18/0x30
Sep 26 02:34:45 K10 kernel: [ 3360.496147]  [<c04b3a7a>] sock_ioctl+0x8a/0x270
Sep 26 02:34:45 K10 kernel: [ 3360.496149]  [<c04b39f0>] ? sock_ioctl+0x0/0x270
Sep 26 02:34:45 K10 kernel: [ 3360.496152]  [<c0216c61>] vfs_ioctl+0x21/0x90
Sep 26 02:34:45 K10 kernel: [ 3360.496154]  [<c0216f49>] do_vfs_ioctl+0x79/0x310
Sep 26 02:34:45 K10 kernel: [ 3360.496157]  [<c0217247>] sys_ioctl+0x67/0x80
Sep 26 02:34:45 K10 kernel: [ 3360.496159]  [<c01033ec>] syscall_call+0x7/0xb
Sep 26 03:08:24 K10 kernel: Kernel logging (proc) stopped.
```

---

### Post by coneheed on 2011-11-30
I have exactly the same problem.

I followed the instructions here: [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

As the original post states, the wireless connection works for a while and then crashes. In the /var/log/kern.log you see NetworkManager hung task and you cannot sudo -i to root as this hangs also.

Has anyone been able to resolve this?

I am using Ubuntu 11.10.

Many thanks in advance.

---

