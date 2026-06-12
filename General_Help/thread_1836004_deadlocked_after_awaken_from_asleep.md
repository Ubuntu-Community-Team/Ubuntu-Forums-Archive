---
title: "deadlocked after awaken from asleep"
date: 2011-08-30
forum: General Help
---

### Post by pf_miles on 2011-08-30
I'm using ubuntu 11.04 natty on Lenovo x220 laptop.With kernel version Linux version 2.6.38-11-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ), x86 64.
I usually lock my screen and close the laptop then go away for a while. When I came back and awaken the system , I found that I couldn't execute many major commands like 'kill', 'ifconfig', 'shutdown' etc. But 'less', 'dmesg' works..The gnome desktop widgets are all frozen and the network is disconneted too.Mouse works but helps little...

I switched to another terminal by pressing ctrl+ alt+f1 but I couldn't shutdown or kill anything..
It's useless to sending shutdown signal by pressing ctrl + alt + del, it will block at some steps .
I have to hold down the power button to power off..

The dmesg info which I think is helpful posted here: ```

[17106.223425] e1000e 0000:00:19.0: BAR 0: set to [mem 0xf2500000-0xf251ffff] (PCI address [0xf2500000-0xf251ffff])
[17106.223447] e1000e 0000:00:19.0: BAR 1: set to [mem 0xf252a000-0xf252afff] (PCI address [0xf252a000-0xf252afff])
[17106.223465] e1000e 0000:00:19.0: BAR 2: set to [io  0x5060-0x507f] (PCI address [0x5060-0x507f])
[17106.223497] e1000e 0000:00:19.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[17106.223535] e1000e 0000:00:19.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[17106.223595] e1000e 0000:00:19.0: PME# disabled
[17106.223733] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[17111.137799] cfg80211: All devices are disconnected, going to restore regulatory settings
[17111.137813] cfg80211: Restoring regulatory settings
[17111.137824] cfg80211: Calling CRDA to update world regulatory domain
[17111.146682] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[17111.146687] cfg80211: World regulatory domain updated:
[17111.146689] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[17111.146692] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[17111.146695] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[17111.146697] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[17111.146700] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[17111.146702] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[17255.770904] INFO: task multiload-apple:2534 blocked for more than 120 seconds.
[17255.770913] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[17255.770919] multiload-apple D 0000000000000003     0  2534      1 0x00000000
[17255.770930]  ffff8800d613fcc8 0000000000000086 ffff8800d613ffd8 ffff8800d613e000
[17255.770940]  0000000000013d00 ffff8800d6064858 ffff8800d613ffd8 0000000000013d00
[17255.770948]  ffff880115f5c4a0 ffff8800d60644a0 ffff8801047e6000 ffffffff81a89ea0
[17255.770957] Call Trace:
[17255.770974]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
[17255.770984]  [<ffffffff8159c360>] ? ioctl_standard_call+0x0/0xd0
[17255.770993]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
[17255.771002]  [<ffffffff814dfb55>] rtnl_lock+0x15/0x20
[17255.771009]  [<ffffffff8159b879>] wext_ioctl_dispatch+0x59/0xb0
[17255.771016]  [<ffffffff8159cff0>] ? ioctl_private_call+0x0/0xb0
[17255.771023]  [<ffffffff8159c516>] wext_handle_ioctl+0x46/0xa0
[17255.771033]  [<ffffffff814d4ffc>] ? dev_ioctl+0x1bc/0x320
[17255.771042]  [<ffffffff814d5149>] dev_ioctl+0x309/0x320
[17255.771051]  [<ffffffff814bbcaa>] sock_ioctl+0x10a/0x2f0
[17255.771062]  [<ffffffff811764ff>] do_vfs_ioctl+0x8f/0x360
[17255.771070]  [<ffffffff81176861>] sys_ioctl+0x91/0xa0
[17255.771078]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
[17255.771115] INFO: task kworker/1:1:10643 blocked for more than 120 seconds.
[17255.771119] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[17255.771124] kworker/1:1     D 0000000000000001     0 10643      2 0x00000000
[17255.771133]  ffff880077c33d50 0000000000000046 ffff880077c33fd8 ffff880077c32000
[17255.771141]  0000000000013d00 ffff8800705cb178 ffff880077c33fd8 0000000000013d00
[17255.771149]  ffff880054fe96e0 ffff8800705cadc0 ffff880077c33df0 ffffffff81a89ea0
[17255.771157] Call Trace:
[17255.771167]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
[17255.771179]  [<ffffffff8100a6e0>] ? __switch_to+0xc0/0x2f0
[17255.771186]  [<ffffffff8159b8d0>] ? wireless_nlevent_process+0x0/0x80
[17255.771194]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
[17255.771202]  [<ffffffff814dfb55>] rtnl_lock+0x15/0x20
[17255.771208]  [<ffffffff8159b8e1>] wireless_nlevent_process+0x11/0x80
[17255.771219]  [<ffffffff8108284d>] process_one_work+0x11d/0x420
[17255.771228]  [<ffffffff810832e9>] worker_thread+0x169/0x360
[17255.771237]  [<ffffffff81083180>] ? worker_thread+0x0/0x360
[17255.771244]  [<ffffffff81087866>] kthread+0x96/0xa0
[17255.771252]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
[17255.771260]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
[17255.771267]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
[17255.771272] INFO: task kworker/1:4:10645 blocked for more than 120 seconds.
[17255.771276] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[17255.771280] kworker/1:4     D 0000000000000001     0 10645      2 0x00000000
[17255.771288]  ffff88007060bd60 0000000000000046 ffff88007060bfd8 ffff88007060a000
[17255.771296]  0000000000013d00 ffff8800705cc858 ffff88007060bfd8 0000000000013d00
[17255.771304]  ffff880115f38000 ffff8800705cc4a0 0000000000013d00 ffffffff81a89ea0
[17255.771312] Call Trace:
[17255.771321]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
[17255.771330]  [<ffffffff814e2ea0>] ? linkwatch_event+0x0/0x30
[17255.771338]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
[17255.771346]  [<ffffffff814dfb55>] rtnl_lock+0x15/0x20
[17255.771354]  [<ffffffff814e2eae>] linkwatch_event+0xe/0x30
[17255.771362]  [<ffffffff8108284d>] process_one_work+0x11d/0x420
[17255.771371]  [<ffffffff810832e9>] worker_thread+0x169/0x360
[17255.771379]  [<ffffffff81083180>] ? worker_thread+0x0/0x360
[17255.771386]  [<ffffffff81087866>] kthread+0x96/0xa0
[17255.771393]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
[17255.771400]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
[17255.771407]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
[17255.771414] INFO: task ethtool:10757 blocked for more than 120 seconds.
[17255.771418] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[17255.771422] ethtool         D 0000000000000000     0 10757  10756 0x00000000
[17255.771430]  ffff8800c99abd28 0000000000000082 ffff8800c99abfd8 ffff8800c99aa000
[17255.771438]  0000000000013d00 ffff8800705b1a98 ffff8800c99abfd8 0000000000013d00
[17255.771446]  ffffffff81a0b020 ffff8800705b16e0 000000011184b025 ffffffff81a89ea0
[17255.771454] Call Trace:
[17255.771462]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
[17255.771471]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
[17255.771479]  [<ffffffff814dfb55>] rtnl_lock+0x15/0x20
[17255.771487]  [<ffffffff814d5068>] dev_ioctl+0x228/0x320
[17255.771495]  [<ffffffff81131d48>] ? handle_mm_fault+0x158/0x260
[17255.771503]  [<ffffffff814bacfd>] sock_do_ioctl+0x5d/0x70
[17255.771510]  [<ffffffff814bbc19>] sock_ioctl+0x79/0x2f0
[17255.771518]  [<ffffffff811764ff>] do_vfs_ioctl+0x8f/0x360
[17255.771526]  [<ffffffff81176861>] sys_ioctl+0x91/0xa0
[17255.771533]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
[17375.592602] INFO: task multiload-apple:2534 blocked for more than 120 seconds.
[17375.592614] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[17375.592623] multiload-apple D 0000000000000003     0  2534      1 0x00000000
[17375.592638]  ffff8800d613fcc8 0000000000000086 ffff8800d613ffd8 ffff8800d613e000
[17375.592652]  0000000000013d00 ffff8800d6064858 ffff8800d613ffd8 0000000000013d00
[17375.592664]  ffff880115f5c4a0 ffff8800d60644a0 ffff8801047e6000 ffffffff81a89ea0
[17375.592678] Call Trace:
[17375.592701]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
[17375.592716]  [<ffffffff8159c360>] ? ioctl_standard_call+0x0/0xd0
[17375.592729]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
[17375.592741]  [<ffffffff814dfb55>] rtnl_lock+0x15/0x20
[17375.592752]  [<ffffffff8159b879>] wext_ioctl_dispatch+0x59/0xb0
[17375.592763]  [<ffffffff8159cff0>] ? ioctl_private_call+0x0/0xb0
[17375.592770]  [<ffffffff8159c516>] wext_handle_ioctl+0x46/0xa0
[17375.592780]  [<ffffffff814d4ffc>] ? dev_ioctl+0x1bc/0x320
[17375.592788]  [<ffffffff814d5149>] dev_ioctl+0x309/0x320
[17375.592797]  [<ffffffff814bbcaa>] sock_ioctl+0x10a/0x2f0
[17375.592808]  [<ffffffff811764ff>] do_vfs_ioctl+0x8f/0x360
[17375.592816]  [<ffffffff81176861>] sys_ioctl+0x91/0xa0
[17375.592827]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
[17375.592851] INFO: task firefox-bin:10187 blocked for more than 120 seconds.
[17375.592859] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[17375.592865] firefox-bin     D 0000000000000001     0 10187      1 0x00000000
[17375.592878]  ffff88009e2f7b08 0000000000000082 ffff88009e2f7fd8 ffff88009e2f6000
[17375.592890]  0000000000013d00 ffff8801024503b8 ffff88009e2f7fd8 0000000000013d00
[17375.592903]  ffff8800cbafadc0 ffff880102450000 ffff88009e2f7b78 ffffffff81a89ea0
[17375.592917] Call Trace:
[17375.592931]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
[17375.592944]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
[17375.592956]  [<ffffffff814dfb55>] rtnl_lock+0x15/0x20
[17375.592967]  [<ffffffff814dfb76>] rtnetlink_rcv+0x16/0x40
[17375.592980]  [<ffffffff814fb68b>] netlink_unicast+0x2fb/0x310
[17375.592990]  [<ffffffff814c892d>] ? memcpy_fromiovec+0x7d/0xa0
[17375.593003]  [<ffffffff814fb8f4>] netlink_sendmsg+0x254/0x3a0
[17375.593015]  [<ffffffff815c0c5c>] ? schedule+0x3ec/0x760
[17375.593026]  [<ffffffff814bc113>] sock_sendmsg+0xf3/0x130
[17375.593041]  [<ffffffff8108bd92>] ? hrtimer_cancel+0x22/0x30
[17375.593054]  [<ffffffff8104e413>] ? __wake_up+0x53/0x70
[17375.593066]  [<ffffffff814fa3f3>] ? netlink_table_ungrab+0x33/0x40
[17375.593079]  [<ffffffff814fa49e>] ? netlink_insert+0x9e/0x180
[17375.593090]  [<ffffffff814bd901>] ? move_addr_to_kernel+0x71/0x80
[17375.593101]  [<ffffffff814be3fd>] sys_sendto+0x13d/0x190
[17375.593115]  [<ffffffff81163517>] ? fd_install+0x67/0x80
[17375.593126]  [<ffffffff814bb4ea>] ? sock_map_fd+0x2a/0x40
[17375.593135]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
[17375.593166] INFO: task kworker/1:1:10643 blocked for more than 120 seconds.
[17375.593172] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[17375.593179] kworker/1:1     D 0000000000000001     0 10643      2 0x00000000
[17375.593191]  ffff880077c33d50 0000000000000046 ffff880077c33fd8 ffff880077c32000
[17375.593204]  0000000000013d00 ffff8800705cb178 ffff880077c33fd8 0000000000013d00
[17375.593216]  ffff880054fe96e0 ffff8800705cadc0 ffff880077c33df0 ffffffff81a89ea0
[17375.593224] Call Trace:
[17375.593234]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
[17375.593246]  [<ffffffff8100a6e0>] ? __switch_to+0xc0/0x2f0
[17375.593254]  [<ffffffff8159b8d0>] ? wireless_nlevent_process+0x0/0x80
[17375.593262]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
[17375.593270]  [<ffffffff814dfb55>] rtnl_lock+0x15/0x20
[17375.593276]  [<ffffffff8159b8e1>] wireless_nlevent_process+0x11/0x80
[17375.593286]  [<ffffffff8108284d>] process_one_work+0x11d/0x420
[17375.593295]  [<ffffffff810832e9>] worker_thread+0x169/0x360
[17375.593304]  [<ffffffff81083180>] ? worker_thread+0x0/0x360
[17375.593311]  [<ffffffff81087866>] kthread+0x96/0xa0
[17375.593319]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
[17375.593326]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
[17375.593333]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
[17375.593339] INFO: task kworker/1:4:10645 blocked for more than 120 seconds.
[17375.593343] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[17375.593347] kworker/1:4     D 0000000000000001     0 10645      2 0x00000000
[17375.593355]  ffff88007060bd60 0000000000000046 ffff88007060bfd8 ffff88007060a000
[17375.593363]  0000000000013d00 ffff8800705cc858 ffff88007060bfd8 0000000000013d00
[17375.593371]  ffff880115f38000 ffff8800705cc4a0 0000000000013d00 ffffffff81a89ea0
[17375.593379] Call Trace:
[17375.593388]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
[17375.593399]  [<ffffffff814e2ea0>] ? linkwatch_event+0x0/0x30
[17375.593411]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
[17375.593421]  [<ffffffff814dfb55>] rtnl_lock+0x15/0x20
[17375.593432]  [<ffffffff814e2eae>] linkwatch_event+0xe/0x30
[17375.593443]  [<ffffffff8108284d>] process_one_work+0x11d/0x420
[17375.593456]  [<ffffffff810832e9>] worker_thread+0x169/0x360
[17375.593468]  [<ffffffff81083180>] ? worker_thread+0x0/0x360
[17375.593477]  [<ffffffff81087866>] kthread+0x96/0xa0
[17375.593486]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
[17375.593495]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
[17375.593503]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
[17375.593514] INFO: task ethtool:10757 blocked for more than 120 seconds.
[17375.593518] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[17375.593525] ethtool         D 0000000000000000     0 10757  10756 0x00000000
[17375.593536]  ffff8800c99abd28 0000000000000082 ffff8800c99abfd8 ffff8800c99aa000
[17375.593548]  0000000000013d00 ffff8800705b1a98 ffff8800c99abfd8 0000000000013d00
[17375.593562]  ffffffff81a0b020 ffff8800705b16e0 000000011184b025 ffffffff81a89ea0
[17375.593573] Call Trace:
[17375.593584]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
[17375.593595]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
[17375.593605]  [<ffffffff814dfb55>] rtnl_lock+0x15/0x20
[17375.593616]  [<ffffffff814d5068>] dev_ioctl+0x228/0x320
[17375.593627]  [<ffffffff81131d48>] ? handle_mm_fault+0x158/0x260
[17375.593638]  [<ffffffff814bacfd>] sock_do_ioctl+0x5d/0x70
[17375.593647]  [<ffffffff814bbc19>] sock_ioctl+0x79/0x2f0
[17375.593659]  [<ffffffff811764ff>] do_vfs_ioctl+0x8f/0x360
[17375.593671]  [<ffffffff81176861>] sys_ioctl+0x91/0xa0
[17375.593682]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
[17495.414327] INFO: task irqbalance:1388 blocked for more than 120 seconds.
[17495.414336] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[17495.414342] irqbalance      D 0000000000000000     0  1388      1 0x00000000
[17495.414353]  ffff880104633d28 0000000000000086 ffff880104633fd8 ffff880104632000
[17495.414362]  0000000000013d00 ffff880114115f38 ffff880104633fd8 0000000000013d00
[17495.414371]  ffffffff81a0b020 ffff880114115b80 0000000000000000 ffffffff81a89ea0
[17495.414379] Call Trace:
[17495.414397]  [<ffffffff815c20b7>] __mutex_lock_slowpath+0xf7/0x180
[17495.414407]  [<ffffffff815c1b0b>] mutex_lock+0x2b/0x50
[17495.414416]  [<ffffffff814dfb55>] rtnl_lock+0x15/0x20
[17495.414426]  [<ffffffff814d5068>] dev_ioctl+0x228/0x320
[17495.414436]  [<ffffffff81166441>] ? get_empty_filp+0xa1/0x170
[17495.414445]  [<ffffffff811555cf>] ? kmem_cache_alloc_trace+0xff/0x120
[17495.414454]  [<ffffffff814bacfd>] sock_do_ioctl+0x5d/0x70
[17495.414461]  [<ffffffff814bbc19>] sock_ioctl+0x79/0x2f0
[17495.414470]  [<ffffffff811764ff>] do_vfs_ioctl+0x8f/0x360
[17495.414478]  [<ffffffff81176861>] sys_ioctl+0x91/0xa0
[17495.414485]  [<ffffffff814bd961>] ? sys_socket+0x51/0x80
[17495.414493]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b

```I think my kernel version is rather new and I googled for the problem for a while. There's some thread discussed  the similar problem but with a much more old kernel version.

It looks like many processes are waiting on a lock or something after awaken, so they could not response.

Is there some one who encountered the same problem when using ubuntu 11.04? I've no idea how to solve this, any help is appreciated. Thanks.

---

### Post by pf_miles on 2011-08-31
It hurts...
Nobody knows how to fix this problem?

---

### Post by boolean_ on 2011-09-02
I don't know how to fix this problem (except for reboot).  But I think I know the cause.  It seems like some applications lock themselves when they loose Internet access. For me this has been pidgin and spotify. The processes get unkillable (rtnl_lock).

---

### Post by boolean_ on 2011-09-02
A small update from me. Decided to see if Spotify was the culprit and did not start it today.  I did start Pidgin however and just now that process is locked with rtnl_lock.  So gonna try after reboot with neither Pidgin or Spotify and see how that goes.

---

