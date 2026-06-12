---
title: "tasks deluged, md, flush blocked for more than 120 seconds"
date: 2012-06-16
forum: General Help
---

### Post by joerg_ac on 2012-06-16
Hi,

I am running Ubuntu 12.04. All updates are applied. Kernel is 3.2.0-25-generic.

I have a md raid 5 device. I use deluge deamon and connect to it locally and with web UI.

Everyting works well until I start using deluge. It also runs well for a while and then it seems to crash. What is even worse is that, when this happens the md device goes from clean to active. As you can see from the following log, deluged, md and flush seem to have a problem now. However, I can still access the data on the md device.

The dmesg shows the following:
```

[ 3239.823238] INFO: task deluged:2307 blocked for more than 120 seconds.
[ 3239.823257] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3239.823261] deluged         D ffffffff81806240     0  2307      1 0x00000000
[ 3239.823267]  ffff8800b0d99c58 0000000000000082 ffff8800b0d99d70 0000000000000000
[ 3239.823273]  ffff8800b0d99fd8 ffff8800b0d99fd8 ffff8800b0d99fd8 0000000000013780
[ 3239.823278]  ffff880130ec16f0 ffff8800b62d96f0 ffff8800b0d99c38 ffff880137c54040
[ 3239.823285] Call Trace:
[ 3239.823296]  [<ffffffff81117200>] ? __lock_page+0x70/0x70
[ 3239.823302]  [<ffffffff8165b71f>] schedule+0x3f/0x60
[ 3239.823306]  [<ffffffff8165b7cf>] io_schedule+0x8f/0xd0
[ 3239.823310]  [<ffffffff8111720e>] sleep_on_page+0xe/0x20
[ 3239.823315]  [<ffffffff8165bfef>] __wait_on_bit+0x5f/0x90
[ 3239.823337]  [<ffffffff81117378>] wait_on_page_bit+0x78/0x80
[ 3239.823343]  [<ffffffff8108b070>] ? autoremove_wake_function+0x40/0x40
[ 3239.823347]  [<ffffffff8111748c>] filemap_fdatawait_range+0x10c/0x1a0
[ 3239.823351]  [<ffffffff8111754b>] filemap_fdatawait+0x2b/0x30
[ 3239.823357]  [<ffffffff811198a4>] filemap_write_and_wait+0x44/0x60
[ 3239.823363]  [<ffffffff811898f5>] ioctl_fiemap.isra.7+0x185/0x1b0
[ 3239.823366]  [<ffffffff8118a0ab>] do_vfs_ioctl+0x11b/0x340
[ 3239.823369]  [<ffffffff8118a361>] sys_ioctl+0x91/0xa0
[ 3239.823374]  [<ffffffff81665c42>] system_call_fastpath+0x16/0x1b
[ 3359.792729] INFO: task jbd2/md1-8:939 blocked for more than 120 seconds.
[ 3359.792734] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3359.792739] jbd2/md1-8      D ffffffff81806240     0   939      2 0x00000000
[ 3359.792744]  ffff88012d4dfac0 0000000000000046 ffff88012d4dfa60 ffffffff8103dcf9
[ 3359.792748]  ffff88012d4dffd8 ffff88012d4dffd8 ffff88012d4dffd8 0000000000013780
[ 3359.792761]  ffff880130ec16f0 ffff880118a896f0 ffff88012d4dfa90 ffff880137c54040
[ 3359.792765] Call Trace:
[ 3359.792774]  [<ffffffff8103dcf9>] ? default_spin_lock_flags+0x9/0x10
[ 3359.792783]  [<ffffffff81117200>] ? __lock_page+0x70/0x70
[ 3359.792789]  [<ffffffff8165b71f>] schedule+0x3f/0x60
[ 3359.792792]  [<ffffffff8165b7cf>] io_schedule+0x8f/0xd0
[ 3359.792795]  [<ffffffff8111720e>] sleep_on_page+0xe/0x20
[ 3359.792798]  [<ffffffff8165bfef>] __wait_on_bit+0x5f/0x90
[ 3359.792811]  [<ffffffff81117378>] wait_on_page_bit+0x78/0x80
[ 3359.792816]  [<ffffffff8108b070>] ? autoremove_wake_function+0x40/0x40
[ 3359.792819]  [<ffffffff8111748c>] filemap_fdatawait_range+0x10c/0x1a0
[ 3359.792823]  [<ffffffff8111754b>] filemap_fdatawait+0x2b/0x30
[ 3359.792830]  [<ffffffff812603c0>] journal_finish_inode_data_buffers+0x70/0x170
[ 3359.792836]  [<ffffffff81260cb5>] jbd2_journal_commit_transaction+0x665/0x1240
[ 3359.792844]  [<ffffffff81077d02>] ? try_to_del_timer_sync+0x92/0x130
[ 3359.792848]  [<ffffffff8126555b>] kjournald2+0xbb/0x220
[ 3359.792850]  [<ffffffff8108b030>] ? add_wait_queue+0x60/0x60
[ 3359.792853]  [<ffffffff812654a0>] ? commit_timeout+0x10/0x10
[ 3359.792857]  [<ffffffff8108a59c>] kthread+0x8c/0xa0
[ 3359.792864]  [<ffffffff81667db4>] kernel_thread_helper+0x4/0x10
[ 3359.792868]  [<ffffffff8108a510>] ? flush_kthread_worker+0xa0/0xa0
[ 3359.792872]  [<ffffffff81667db0>] ? gs_change+0x13/0x13
[ 3359.792888] INFO: task flush-9:1:1226 blocked for more than 120 seconds.
[ 3359.792890] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3359.792892] flush-9:1       D ffffffff81806240     0  1226      2 0x00000000
[ 3359.792896]  ffff8801194295e0 0000000000000046 ffff8801194295f0 ffffffff8125ece8
[ 3359.792900]  ffff880119429fd8 ffff880119429fd8 ffff880119429fd8 0000000000013780
[ 3359.792904]  ffff880130ec16f0 ffff88012ce4c4d0 ffff8801194295f0 ffff880119429650
[ 3359.792909] Call Trace:
[ 3359.792915]  [<ffffffff8125ece8>] ? __jbd2_journal_file_buffer+0x188/0x270
[ 3359.792918]  [<ffffffff8165b71f>] schedule+0x3f/0x60
[ 3359.792928]  [<ffffffff8125f7ed>] do_get_write_access+0x27d/0x4f0
[ 3359.792934]  [<ffffffff811a8373>] ? __find_get_block_slow+0xd3/0x190
[ 3359.792938]  [<ffffffff8108b070>] ? autoremove_wake_function+0x40/0x40
[ 3359.792942]  [<ffffffff811a94d7>] ? __find_get_block+0x87/0xe0
[ 3359.792946]  [<ffffffff8125fba0>] jbd2_journal_get_write_access+0x30/0x50
[ 3359.792951]  [<ffffffff81241b2e>] __ext4_journal_get_write_access+0x3e/0x80
[ 3359.792955]  [<ffffffff81248e4b>] ext4_mb_mark_diskspace_used+0xfb/0x500
[ 3359.792960]  [<ffffffff811645ed>] ? kmem_cache_alloc+0x11d/0x140
[ 3359.792970]  [<ffffffff8124a4ef>] ext4_mb_new_blocks+0x2bf/0x4a0
[ 3359.792974]  [<ffffffff8123c2ac>] ? ext4_ext_check_overlap.isra.20+0xbc/0xd0
[ 3359.792977]  [<ffffffff81240d0a>] ext4_ext_map_blocks+0xc7a/0xe70
[ 3359.792983]  [<ffffffff8131105d>] ? radix_tree_gang_lookup_tag_slot+0x8d/0xd0
[ 3359.792989]  [<ffffffff81216175>] ext4_map_blocks+0x1b5/0x280
[ 3359.792993]  [<ffffffff8121a4d9>] mpage_da_map_and_submit+0xb9/0x370
[ 3359.793008]  [<ffffffff8121b041>] ext4_da_writepages+0x381/0x640
[ 3359.793014]  [<ffffffff814e187b>] ? plugger_unplug+0x3b/0x50
[ 3359.793020]  [<ffffffff81122b21>] do_writepages+0x21/0x40
[ 3359.793024]  [<ffffffff811a11f0>] writeback_single_inode+0x180/0x430
[ 3359.793027]  [<ffffffff811a18b6>] writeback_sb_inodes+0x1b6/0x270
[ 3359.793031]  [<ffffffff811a1a0e>] __writeback_inodes_wb+0x9e/0xd0
[ 3359.793040]  [<ffffffff811a1cbb>] wb_writeback+0x27b/0x330
[ 3359.793045]  [<ffffffff810126e5>] ? __switch_to+0xf5/0x360
[ 3359.793050]  [<ffffffff811933a2>] ? get_nr_dirty_inodes+0x52/0x80
[ 3359.793054]  [<ffffffff811a1e0f>] wb_check_old_data_flush+0x9f/0xb0
[ 3359.793058]  [<ffffffff811a2d01>] wb_do_writeback+0x151/0x1d0
[ 3359.793062]  [<ffffffff81076c20>] ? usleep_range+0x50/0x50
[ 3359.793068]  [<ffffffff811a2e03>] bdi_writeback_thread+0x83/0x2a0
[ 3359.793071]  [<ffffffff811a2d80>] ? wb_do_writeback+0x1d0/0x1d0
[ 3359.793073]  [<ffffffff8108a59c>] kthread+0x8c/0xa0
[ 3359.793076]  [<ffffffff81667db4>] kernel_thread_helper+0x4/0x10
[ 3359.793080]  [<ffffffff8108a510>] ? flush_kthread_worker+0xa0/0xa0
[ 3359.793084]  [<ffffffff81667db0>] ? gs_change+0x13/0x13
[ 3359.793116] INFO: task deluged:2307 blocked for more than 120 seconds.
[ 3359.793117] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3359.793119] deluged         D ffffffff81806240     0  2307      1 0x00000000
[ 3359.793123]  ffff8800b0d99c58 0000000000000082 ffff8800b0d99d70 0000000000000000
[ 3359.793127]  ffff8800b0d99fd8 ffff8800b0d99fd8 ffff8800b0d99fd8 0000000000013780
[ 3359.793133]  ffff880130ec16f0 ffff8800b62d96f0 ffff8800b0d99c38 ffff880137c54040
[ 3359.793136] Call Trace:
[ 3359.793140]  [<ffffffff81117200>] ? __lock_page+0x70/0x70
[ 3359.793143]  [<ffffffff8165b71f>] schedule+0x3f/0x60
[ 3359.793145]  [<ffffffff8165b7cf>] io_schedule+0x8f/0xd0
[ 3359.793156]  [<ffffffff8111720e>] sleep_on_page+0xe/0x20
[ 3359.793158]  [<ffffffff8165bfef>] __wait_on_bit+0x5f/0x90
[ 3359.793161]  [<ffffffff81117378>] wait_on_page_bit+0x78/0x80
[ 3359.793164]  [<ffffffff8108b070>] ? autoremove_wake_function+0x40/0x40
[ 3359.793168]  [<ffffffff8111748c>] filemap_fdatawait_range+0x10c/0x1a0
[ 3359.793173]  [<ffffffff8111754b>] filemap_fdatawait+0x2b/0x30
[ 3359.793178]  [<ffffffff811198a4>] filemap_write_and_wait+0x44/0x60
[ 3359.793183]  [<ffffffff811898f5>] ioctl_fiemap.isra.7+0x185/0x1b0
[ 3359.793198]  [<ffffffff8118a0ab>] do_vfs_ioctl+0x11b/0x340
[ 3359.793201]  [<ffffffff8118a361>] sys_ioctl+0x91/0xa0
[ 3359.793204]  [<ffffffff81665c42>] system_call_fastpath+0x16/0x1b
[ 3479.762235] INFO: task jbd2/md1-8:939 blocked for more than 120 seconds.
[ 3479.762239] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3479.762242] jbd2/md1-8      D ffffffff81806240     0   939      2 0x00000000
[ 3479.762251]  ffff88012d4dfac0 0000000000000046 ffff88012d4dfa60 ffffffff8103dcf9
[ 3479.762257]  ffff88012d4dffd8 ffff88012d4dffd8 ffff88012d4dffd8 0000000000013780
[ 3479.762262]  ffff880130ec16f0 ffff880118a896f0 ffff88012d4dfa90 ffff880137c54040
[ 3479.762267] Call Trace:
[ 3479.762276]  [<ffffffff8103dcf9>] ? default_spin_lock_flags+0x9/0x10
[ 3479.762282]  [<ffffffff81117200>] ? __lock_page+0x70/0x70
[ 3479.762291]  [<ffffffff8165b71f>] schedule+0x3f/0x60
[ 3479.762294]  [<ffffffff8165b7cf>] io_schedule+0x8f/0xd0
[ 3479.762297]  [<ffffffff8111720e>] sleep_on_page+0xe/0x20
[ 3479.762300]  [<ffffffff8165bfef>] __wait_on_bit+0x5f/0x90
[ 3479.762304]  [<ffffffff81117378>] wait_on_page_bit+0x78/0x80
[ 3479.762308]  [<ffffffff8108b070>] ? autoremove_wake_function+0x40/0x40
[ 3479.762312]  [<ffffffff8111748c>] filemap_fdatawait_range+0x10c/0x1a0
[ 3479.762315]  [<ffffffff8111754b>] filemap_fdatawait+0x2b/0x30
[ 3479.762322]  [<ffffffff812603c0>] journal_finish_inode_data_buffers+0x70/0x170
[ 3479.762330]  [<ffffffff81260cb5>] jbd2_journal_commit_transaction+0x665/0x1240
[ 3479.762337]  [<ffffffff81077d02>] ? try_to_del_timer_sync+0x92/0x130
[ 3479.762341]  [<ffffffff8126555b>] kjournald2+0xbb/0x220
[ 3479.762344]  [<ffffffff8108b030>] ? add_wait_queue+0x60/0x60
[ 3479.762347]  [<ffffffff812654a0>] ? commit_timeout+0x10/0x10
[ 3479.762354]  [<ffffffff8108a59c>] kthread+0x8c/0xa0
[ 3479.762358]  [<ffffffff81667db4>] kernel_thread_helper+0x4/0x10
[ 3479.762361]  [<ffffffff8108a510>] ? flush_kthread_worker+0xa0/0xa0
[ 3479.762364]  [<ffffffff81667db0>] ? gs_change+0x13/0x13
[ 3479.762372] INFO: task flush-9:1:1226 blocked for more than 120 seconds.
[ 3479.762374] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3479.762376] flush-9:1       D ffffffff81806240     0  1226      2 0x00000000
[ 3479.762380]  ffff8801194295e0 0000000000000046 ffff8801194295f0 ffffffff8125ece8
[ 3479.762383]  ffff880119429fd8 ffff880119429fd8 ffff880119429fd8 0000000000013780
[ 3479.762388]  ffff880130ec16f0 ffff88012ce4c4d0 ffff8801194295f0 ffff880119429650
[ 3479.762393] Call Trace:
[ 3479.762396]  [<ffffffff8125ece8>] ? __jbd2_journal_file_buffer+0x188/0x270
[ 3479.762399]  [<ffffffff8165b71f>] schedule+0x3f/0x60
[ 3479.762402]  [<ffffffff8125f7ed>] do_get_write_access+0x27d/0x4f0
[ 3479.762418]  [<ffffffff811a8373>] ? __find_get_block_slow+0xd3/0x190
[ 3479.762424]  [<ffffffff8108b070>] ? autoremove_wake_function+0x40/0x40
[ 3479.762427]  [<ffffffff811a94d7>] ? __find_get_block+0x87/0xe0
[ 3479.762430]  [<ffffffff8125fba0>] jbd2_journal_get_write_access+0x30/0x50
[ 3479.762436]  [<ffffffff81241b2e>] __ext4_journal_get_write_access+0x3e/0x80
[ 3479.762447]  [<ffffffff81248e4b>] ext4_mb_mark_diskspace_used+0xfb/0x500
[ 3479.762452]  [<ffffffff811645ed>] ? kmem_cache_alloc+0x11d/0x140
[ 3479.762455]  [<ffffffff8124a4ef>] ext4_mb_new_blocks+0x2bf/0x4a0
[ 3479.762459]  [<ffffffff8123c2ac>] ? ext4_ext_check_overlap.isra.20+0xbc/0xd0
[ 3479.762463]  [<ffffffff81240d0a>] ext4_ext_map_blocks+0xc7a/0xe70
[ 3479.762468]  [<ffffffff8131105d>] ? radix_tree_gang_lookup_tag_slot+0x8d/0xd0
[ 3479.762475]  [<ffffffff81216175>] ext4_map_blocks+0x1b5/0x280
[ 3479.762480]  [<ffffffff8121a4d9>] mpage_da_map_and_submit+0xb9/0x370
[ 3479.762496]  [<ffffffff8121b041>] ext4_da_writepages+0x381/0x640
[ 3479.762502]  [<ffffffff814e187b>] ? plugger_unplug+0x3b/0x50
[ 3479.762509]  [<ffffffff81122b21>] do_writepages+0x21/0x40
[ 3479.762514]  [<ffffffff811a11f0>] writeback_single_inode+0x180/0x430
[ 3479.762525]  [<ffffffff811a18b6>] writeback_sb_inodes+0x1b6/0x270
[ 3479.762531]  [<ffffffff811a1a0e>] __writeback_inodes_wb+0x9e/0xd0
[ 3479.762536]  [<ffffffff811a1cbb>] wb_writeback+0x27b/0x330
[ 3479.762542]  [<ffffffff810126e5>] ? __switch_to+0xf5/0x360
[ 3479.762547]  [<ffffffff811933a2>] ? get_nr_dirty_inodes+0x52/0x80
[ 3479.762551]  [<ffffffff811a1e0f>] wb_check_old_data_flush+0x9f/0xb0
[ 3479.762556]  [<ffffffff811a2d01>] wb_do_writeback+0x151/0x1d0
[ 3479.762576]  [<ffffffff81076c20>] ? usleep_range+0x50/0x50
[ 3479.762581]  [<ffffffff811a2e03>] bdi_writeback_thread+0x83/0x2a0
[ 3479.762586]  [<ffffffff811a2d80>] ? wb_do_writeback+0x1d0/0x1d0
[ 3479.762590]  [<ffffffff8108a59c>] kthread+0x8c/0xa0
[ 3479.762594]  [<ffffffff81667db4>] kernel_thread_helper+0x4/0x10
[ 3479.762598]  [<ffffffff8108a510>] ? flush_kthread_worker+0xa0/0xa0
[ 3479.762603]  [<ffffffff81667db0>] ? gs_change+0x13/0x13
[ 3479.762647] INFO: task deluged:2307 blocked for more than 120 seconds.
[ 3479.762650] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3479.762653] deluged         D ffffffff81806240     0  2307      1 0x00000000
[ 3479.762657]  ffff8800b0d99c58 0000000000000082 ffff8800b0d99d70 0000000000000000
[ 3479.762662]  ffff8800b0d99fd8 ffff8800b0d99fd8 ffff8800b0d99fd8 0000000000013780
[ 3479.762668]  ffff880130ec16f0 ffff8800b62d96f0 ffff8800b0d99c38 ffff880137c54040
[ 3479.762672] Call Trace:
[ 3479.762677]  [<ffffffff81117200>] ? __lock_page+0x70/0x70
[ 3479.762695]  [<ffffffff8165b71f>] schedule+0x3f/0x60
[ 3479.762699]  [<ffffffff8165b7cf>] io_schedule+0x8f/0xd0
[ 3479.762703]  [<ffffffff8111720e>] sleep_on_page+0xe/0x20
[ 3479.762707]  [<ffffffff8165bfef>] __wait_on_bit+0x5f/0x90
[ 3479.762711]  [<ffffffff81117378>] wait_on_page_bit+0x78/0x80
[ 3479.762715]  [<ffffffff8108b070>] ? autoremove_wake_function+0x40/0x40
[ 3479.762720]  [<ffffffff8111748c>] filemap_fdatawait_range+0x10c/0x1a0
[ 3479.762732]  [<ffffffff8111754b>] filemap_fdatawait+0x2b/0x30
[ 3479.762738]  [<ffffffff811198a4>] filemap_write_and_wait+0x44/0x60
[ 3479.762745]  [<ffffffff811898f5>] ioctl_fiemap.isra.7+0x185/0x1b0
[ 3479.762749]  [<ffffffff8118a0ab>] do_vfs_ioctl+0x11b/0x340
[ 3479.762753]  [<ffffffff8118a361>] sys_ioctl+0x91/0xa0
[ 3479.762770]  [<ffffffff81665c42>] system_call_fastpath+0x16/0x1b
[ 3599.731767] INFO: task jbd2/md1-8:939 blocked for more than 120 seconds.
[ 3599.731773] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3599.731778] jbd2/md1-8      D ffffffff81806240     0   939      2 0x00000000
[ 3599.731791]  ffff88012d4dfac0 0000000000000046 ffff88012d4dfa60 ffffffff8103dcf9
[ 3599.731796]  ffff88012d4dffd8 ffff88012d4dffd8 ffff88012d4dffd8 0000000000013780
[ 3599.731799]  ffff880130ec16f0 ffff880118a896f0 ffff88012d4dfa90 ffff880137c54040
[ 3599.731803] Call Trace:
[ 3599.731812]  [<ffffffff8103dcf9>] ? default_spin_lock_flags+0x9/0x10
[ 3599.731818]  [<ffffffff81117200>] ? __lock_page+0x70/0x70
[ 3599.731822]  [<ffffffff8165b71f>] schedule+0x3f/0x60
[ 3599.731825]  [<ffffffff8165b7cf>] io_schedule+0x8f/0xd0
[ 3599.731828]  [<ffffffff8111720e>] sleep_on_page+0xe/0x20
[ 3599.731831]  [<ffffffff8165bfef>] __wait_on_bit+0x5f/0x90
[ 3599.731834]  [<ffffffff81117378>] wait_on_page_bit+0x78/0x80
[ 3599.731839]  [<ffffffff8108b070>] ? autoremove_wake_function+0x40/0x40
[ 3599.731842]  [<ffffffff8111748c>] filemap_fdatawait_range+0x10c/0x1a0
[ 3599.731846]  [<ffffffff8111754b>] filemap_fdatawait+0x2b/0x30
[ 3599.731852]  [<ffffffff812603c0>] journal_finish_inode_data_buffers+0x70/0x170
[ 3599.731856]  [<ffffffff81260cb5>] jbd2_journal_commit_transaction+0x665/0x1240
[ 3599.731862]  [<ffffffff81077d02>] ? try_to_del_timer_sync+0x92/0x130
[ 3599.731865]  [<ffffffff8126555b>] kjournald2+0xbb/0x220
[ 3599.731868]  [<ffffffff8108b030>] ? add_wait_queue+0x60/0x60
[ 3599.731871]  [<ffffffff812654a0>] ? commit_timeout+0x10/0x10
[ 3599.731886]  [<ffffffff8108a59c>] kthread+0x8c/0xa0
[ 3599.731891]  [<ffffffff81667db4>] kernel_thread_helper+0x4/0x10
[ 3599.731895]  [<ffffffff8108a510>] ? flush_kthread_worker+0xa0/0xa0
[ 3599.731900]  [<ffffffff81667db0>] ? gs_change+0x13/0x13
[ 3599.731909] INFO: task flush-9:1:1226 blocked for more than 120 seconds.
[ 3599.731910] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3599.731912] flush-9:1       D ffffffff81806240     0  1226      2 0x00000000
[ 3599.731916]  ffff8801194295e0 0000000000000046 ffff8801194295f0 ffffffff8125ece8
[ 3599.731920]  ffff880119429fd8 ffff880119429fd8 ffff880119429fd8 0000000000013780
[ 3599.731939]  ffff880130ec16f0 ffff88012ce4c4d0 ffff8801194295f0 ffff880119429650
[ 3599.731942] Call Trace:
[ 3599.731946]  [<ffffffff8125ece8>] ? __jbd2_journal_file_buffer+0x188/0x270
[ 3599.731950]  [<ffffffff8165b71f>] schedule+0x3f/0x60
[ 3599.731953]  [<ffffffff8125f7ed>] do_get_write_access+0x27d/0x4f0
[ 3599.731959]  [<ffffffff811a8373>] ? __find_get_block_slow+0xd3/0x190
[ 3599.731964]  [<ffffffff8108b070>] ? autoremove_wake_function+0x40/0x40
[ 3599.731968]  [<ffffffff811a94d7>] ? __find_get_block+0x87/0xe0
[ 3599.731972]  [<ffffffff8125fba0>] jbd2_journal_get_write_access+0x30/0x50
[ 3599.731977]  [<ffffffff81241b2e>] __ext4_journal_get_write_access+0x3e/0x80
[ 3599.731981]  [<ffffffff81248e4b>] ext4_mb_mark_diskspace_used+0xfb/0x500
[ 3599.731985]  [<ffffffff811645ed>] ? kmem_cache_alloc+0x11d/0x140
[ 3599.731997]  [<ffffffff8124a4ef>] ext4_mb_new_blocks+0x2bf/0x4a0
[ 3599.732000]  [<ffffffff8123c2ac>] ? ext4_ext_check_overlap.isra.20+0xbc/0xd0
[ 3599.732005]  [<ffffffff81240d0a>] ext4_ext_map_blocks+0xc7a/0xe70
[ 3599.732011]  [<ffffffff8131105d>] ? radix_tree_gang_lookup_tag_slot+0x8d/0xd0
[ 3599.732018]  [<ffffffff81216175>] ext4_map_blocks+0x1b5/0x280
[ 3599.732024]  [<ffffffff8121a4d9>] mpage_da_map_and_submit+0xb9/0x370
[ 3599.732028]  [<ffffffff8121b041>] ext4_da_writepages+0x381/0x640
[ 3599.732034]  [<ffffffff814e187b>] ? plugger_unplug+0x3b/0x50
[ 3599.732041]  [<ffffffff81122b21>] do_writepages+0x21/0x40
[ 3599.732045]  [<ffffffff811a11f0>] writeback_single_inode+0x180/0x430
[ 3599.732054]  [<ffffffff811a18b6>] writeback_sb_inodes+0x1b6/0x270
[ 3599.732058]  [<ffffffff811a1a0e>] __writeback_inodes_wb+0x9e/0xd0
[ 3599.732061]  [<ffffffff811a1cbb>] wb_writeback+0x27b/0x330
[ 3599.732065]  [<ffffffff810126e5>] ? __switch_to+0xf5/0x360
[ 3599.732069]  [<ffffffff811933a2>] ? get_nr_dirty_inodes+0x52/0x80
[ 3599.732072]  [<ffffffff811a1e0f>] wb_check_old_data_flush+0x9f/0xb0
[ 3599.732075]  [<ffffffff811a2d01>] wb_do_writeback+0x151/0x1d0
[ 3599.732079]  [<ffffffff81076c20>] ? usleep_range+0x50/0x50
[ 3599.732082]  [<ffffffff811a2e03>] bdi_writeback_thread+0x83/0x2a0
[ 3599.732086]  [<ffffffff811a2d80>] ? wb_do_writeback+0x1d0/0x1d0
[ 3599.732091]  [<ffffffff8108a59c>] kthread+0x8c/0xa0
[ 3599.732095]  [<ffffffff81667db4>] kernel_thread_helper+0x4/0x10
[ 3599.732109]  [<ffffffff8108a510>] ? flush_kthread_worker+0xa0/0xa0
[ 3599.732114]  [<ffffffff81667db0>] ? gs_change+0x13/0x13
[ 3599.732141] INFO: task deluged:2307 blocked for more than 120 seconds.
[ 3599.732143] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3599.732145] deluged         D ffffffff81806240     0  2307      1 0x00000000
[ 3599.732148]  ffff8800b0d99c58 0000000000000082 ffff8800b0d99d70 0000000000000000
[ 3599.732161]  ffff8800b0d99fd8 ffff8800b0d99fd8 ffff8800b0d99fd8 0000000000013780
[ 3599.732165]  ffff880130ec16f0 ffff8800b62d96f0 ffff8800b0d99c38 ffff880137c54040
[ 3599.732169] Call Trace:
[ 3599.732173]  [<ffffffff81117200>] ? __lock_page+0x70/0x70
[ 3599.732177]  [<ffffffff8165b71f>] schedule+0x3f/0x60
[ 3599.732180]  [<ffffffff8165b7cf>] io_schedule+0x8f/0xd0
[ 3599.732183]  [<ffffffff8111720e>] sleep_on_page+0xe/0x20
[ 3599.732186]  [<ffffffff8165bfef>] __wait_on_bit+0x5f/0x90
[ 3599.732189]  [<ffffffff81117378>] wait_on_page_bit+0x78/0x80
[ 3599.732192]  [<ffffffff8108b070>] ? autoremove_wake_function+0x40/0x40
[ 3599.732195]  [<ffffffff8111748c>] filemap_fdatawait_range+0x10c/0x1a0
[ 3599.732199]  [<ffffffff8111754b>] filemap_fdatawait+0x2b/0x30
[ 3599.732211]  [<ffffffff811198a4>] filemap_write_and_wait+0x44/0x60
[ 3599.732218]  [<ffffffff811898f5>] ioctl_fiemap.isra.7+0x185/0x1b0
[ 3599.732222]  [<ffffffff8118a0ab>] do_vfs_ioctl+0x11b/0x340
[ 3599.732226]  [<ffffffff8118a361>] sys_ioctl+0x91/0xa0
[ 3599.732231]  [<ffffffff81665c42>] system_call_fastpath+0x16/0x1b


```Deluge does not show any activity any more. 
Trying to kill the deluged process with kill -9 fails and leaves deluged as defunct zombie. 

The system also hangs at shutdown. After the restart the md device is active, resyncing, which takes a while. unmounting the md device is refused with device is busy.

The deluge version is 1.3.5
libtorrent is 0.15.10.0

Before moving to a freshly installed 12.04 I used a similar configuration on 10.04 without any problems.

Does anybody have a clue what is going on and how this might be solved. Most annoying is that a using deluge also affects the md device. All ideas are highly appreciated.

best regards, Joerg

---

### Post by joerg_ac on 2012-06-17
Hi again,

Nobody has an idea or hint? Is this the right forum category to ask this kind of question? Or should I move this to a more technical part of the forum? The question is which one?

best regards, Jörg

---

