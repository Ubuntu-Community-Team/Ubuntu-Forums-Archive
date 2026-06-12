---
title: "LVM blocking disk access for several minutes"
date: 2011-08-31
forum: General Help
---

### Post by LiquidStranger on 2011-08-31
I'm running a 5TB LVM with one ext4 file system spanning 4 disks of varying size (750GB to 2TB) on my desktop computer. Recently I've been having occasions where access to the file system is blocked for 2minutes or more. The hard drive LED is on at these times and the following errors appear in the syslog. SMART-data indicates all disks are in good health.
Any idea what may cause these blocks and how to stop them?

```
Aug 31 12:46:05 PC kernel: [ 4681.370191] INFO: task jbd2/dm-0-8:969 blocked for more than 120 seconds.
Aug 31 12:46:05 PC kernel: [ 4681.370199] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Aug 31 12:46:05 PC kernel: [ 4681.370207] jbd2/dm-0-8     D 0000000000000001     0   969      2 0x00000000
Aug 31 12:46:05 PC kernel: [ 4681.370218]  ffff880127d23d20 0000000000000046 ffff880127d23fd8 ffff880127d22000
Aug 31 12:46:05 PC kernel: [ 4681.370228]  0000000000013d00 ffff880126c73178 ffff880127d23fd8 0000000000013d00
Aug 31 12:46:05 PC kernel: [ 4681.370237]  ffff880137718000 ffff880126c72dc0 ffff880126c72dc0 ffff8800bf5c07a0
Aug 31 12:46:05 PC kernel: [ 4681.370246] Call Trace:
Aug 31 12:46:05 PC kernel: [ 4681.370261]  [<ffffffff81242e10>] jbd2_journal_commit_transaction+0x1b0/0x1190
Aug 31 12:46:05 PC kernel: [ 4681.370273]  [<ffffffff8100a6e0>] ? __switch_to+0xc0/0x2f0
Aug 31 12:46:05 PC kernel: [ 4681.370281]  [<ffffffff815c337e>] ? _raw_spin_lock+0xe/0x20
Aug 31 12:46:05 PC kernel: [ 4681.370291]  [<ffffffff8107502b>] ? lock_timer_base.clone.20+0x3b/0x70
Aug 31 12:46:05 PC kernel: [ 4681.370300]  [<ffffffff81087fb0>] ? autoremove_wake_function+0x0/0x40
Aug 31 12:46:05 PC kernel: [ 4681.370309]  [<ffffffff81247f5b>] kjournald2+0xbb/0x220
Aug 31 12:46:05 PC kernel: [ 4681.370317]  [<ffffffff81087fb0>] ? autoremove_wake_function+0x0/0x40
Aug 31 12:46:05 PC kernel: [ 4681.370324]  [<ffffffff81247ea0>] ? kjournald2+0x0/0x220
Aug 31 12:46:05 PC kernel: [ 4681.370331]  [<ffffffff81087866>] kthread+0x96/0xa0
Aug 31 12:46:05 PC kernel: [ 4681.370339]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Aug 31 12:46:05 PC kernel: [ 4681.370346]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Aug 31 12:46:05 PC kernel: [ 4681.370353]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Aug 31 12:46:05 PC kernel: [ 4681.370403] INFO: task nautilus:2829 blocked for more than 120 seconds.
Aug 31 12:46:05 PC kernel: [ 4681.370407] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Aug 31 12:46:05 PC kernel: [ 4681.370413] nautilus        D 0000000000000003     0  2829   1861 0x00000000
Aug 31 12:46:05 PC kernel: [ 4681.370422]  ffff880064ddbce8 0000000000000082 ffff880064ddbfd8 ffff880064dda000
Aug 31 12:46:05 PC kernel: [ 4681.370431]  0000000000013d00 ffff88010615c858 ffff880064ddbfd8 0000000000013d00
Aug 31 12:46:05 PC kernel: [ 4681.370440]  ffff8801377344a0 ffff88010615c4a0 ffff880064ddbd38 ffff880133483000
Aug 31 12:46:05 PC kernel: [ 4681.370448] Call Trace:
Aug 31 12:46:05 PC kernel: [ 4681.370458]  [<ffffffff812406c2>] start_this_handle.clone.7+0x362/0x4a0
Aug 31 12:46:05 PC kernel: [ 4681.370466]  [<ffffffff81087fb0>] ? autoremove_wake_function+0x0/0x40
Aug 31 12:46:05 PC kernel: [ 4681.370475]  [<ffffffff812408ca>] jbd2__journal_start+0xca/0x110
Aug 31 12:46:05 PC kernel: [ 4681.370484]  [<ffffffff81240923>] jbd2_journal_start+0x13/0x20
Aug 31 12:46:05 PC kernel: [ 4681.370492]  [<ffffffff8121dc53>] ext4_journal_start_sb+0xb3/0x140
Aug 31 12:46:05 PC kernel: [ 4681.370501]  [<ffffffff81176b20>] ? filldir+0x0/0xe0
Aug 31 12:46:05 PC kernel: [ 4681.370509]  [<ffffffff81209fa7>] ext4_dirty_inode+0x27/0x60
Aug 31 12:46:05 PC kernel: [ 4681.370517]  [<ffffffff8118b39f>] __mark_inode_dirty+0x3f/0x260
Aug 31 12:46:05 PC kernel: [ 4681.370525]  [<ffffffff8117d6fb>] touch_atime+0x12b/0x180
Aug 31 12:46:05 PC kernel: [ 4681.370533]  [<ffffffff81176b20>] ? filldir+0x0/0xe0
Aug 31 12:46:05 PC kernel: [ 4681.370540]  [<ffffffff81176a1e>] vfs_readdir+0xce/0xe0
Aug 31 12:46:05 PC kernel: [ 4681.370548]  [<ffffffff81176cf9>] sys_getdents+0x89/0xf0
Aug 31 12:46:05 PC kernel: [ 4681.370555]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
Aug 31 12:46:05 PC kernel: [ 4681.370590] INFO: task flush-252:0:2810 blocked for more than 120 seconds.
Aug 31 12:46:05 PC kernel: [ 4681.370594] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Aug 31 12:46:05 PC kernel: [ 4681.370599] flush-252:0     D 0000000000000002     0  2810      2 0x00000000
Aug 31 12:46:05 PC kernel: [ 4681.370607]  ffff8800a8f0b990 0000000000000046 ffff8800a8f0bfd8 ffff8800a8f0a000
Aug 31 12:46:05 PC kernel: [ 4681.370616]  0000000000013d00 ffff88010a351a98 ffff8800a8f0bfd8 0000000000013d00
Aug 31 12:46:05 PC kernel: [ 4681.370624]  ffff88013771db80 ffff88010a3516e0 000000000000000e ffff880133483000
Aug 31 12:46:05 PC kernel: [ 4681.370632] Call Trace:
Aug 31 12:46:05 PC kernel: [ 4681.370641]  [<ffffffff812406c2>] start_this_handle.clone.7+0x362/0x4a0
Aug 31 12:46:05 PC kernel: [ 4681.370650]  [<ffffffff81087fb0>] ? autoremove_wake_function+0x0/0x40
Aug 31 12:46:05 PC kernel: [ 4681.370659]  [<ffffffff812408ca>] jbd2__journal_start+0xca/0x110
Aug 31 12:46:05 PC kernel: [ 4681.370667]  [<ffffffff81240923>] jbd2_journal_start+0x13/0x20
Aug 31 12:46:05 PC kernel: [ 4681.370675]  [<ffffffff8121dc53>] ext4_journal_start_sb+0xb3/0x140
Aug 31 12:46:05 PC kernel: [ 4681.370682]  [<ffffffff81203145>] ? ext4_meta_trans_blocks+0x75/0xe0
Aug 31 12:46:05 PC kernel: [ 4681.370690]  [<ffffffff812098b7>] ext4_da_writepages+0x2b7/0x630
Aug 31 12:46:05 PC kernel: [ 4681.370701]  [<ffffffff81117191>] do_writepages+0x21/0x40
Aug 31 12:46:05 PC kernel: [ 4681.370708]  [<ffffffff8118b65f>] writeback_single_inode+0x9f/0x240
Aug 31 12:46:05 PC kernel: [ 4681.370716]  [<ffffffff8118ba4b>] writeback_sb_inodes+0xcb/0x160
Aug 31 12:46:05 PC kernel: [ 4681.370724]  [<ffffffff81104461>] ? __perf_event_task_sched_out+0x31/0x40
Aug 31 12:46:05 PC kernel: [ 4681.370733]  [<ffffffff8118bc9b>] writeback_inodes_wb+0x10b/0x1c0
Aug 31 12:46:05 PC kernel: [ 4681.370740]  [<ffffffff8118c0ce>] wb_writeback+0x37e/0x490
Aug 31 12:46:05 PC kernel: [ 4681.370747]  [<ffffffff815c352f>] ? _raw_spin_lock_irqsave+0x2f/0x40
Aug 31 12:46:05 PC kernel: [ 4681.370756]  [<ffffffff8107502b>] ? lock_timer_base.clone.20+0x3b/0x70
Aug 31 12:46:05 PC kernel: [ 4681.370765]  [<ffffffff8118c401>] wb_do_writeback+0x221/0x230
Aug 31 12:46:05 PC kernel: [ 4681.370773]  [<ffffffff8118c492>] bdi_writeback_thread+0x82/0x260
Aug 31 12:46:05 PC kernel: [ 4681.370781]  [<ffffffff8118c410>] ? bdi_writeback_thread+0x0/0x260
Aug 31 12:46:05 PC kernel: [ 4681.370788]  [<ffffffff81087866>] kthread+0x96/0xa0
Aug 31 12:46:05 PC kernel: [ 4681.370796]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Aug 31 12:46:05 PC kernel: [ 4681.370803]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Aug 31 12:46:05 PC kernel: [ 4681.370810]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10

```

---

### Post by dino99 on 2011-08-31
might be due to the slower (older) hdd transfer capability or a too narrow band chipset transfer on Motherboard. Can you identify when this is happening ? eg when to move big files.
Otherwise use System Monitor to watch ram/swap used, maybe set a bigger swap partition.

---

### Post by LiquidStranger on 2011-08-31
All of the drives are SATA2 drives connected to SATA2/3 connectors on the mainboard and none of them are older than 3 years. Bandwidth shouldn't be a problem for the disks: I used hdparm to speed-test them before including them in the LVM. There is a 4GB swap partition which is usually only used by a few percent. Memory is usually around 30% of the available 4GB.

It seems as if the blocks are mostly happening during large local file transfers (5GB+) and when I copy data via NFS. But it's not happening every time.

---

### Post by LionelHutz on 2011-09-11
I am having the same issue, and I believe it's a faulty disk.

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             903G  8.4G  849G   1% /
none                  3.8G  348K  3.8G   1% /dev
none                  3.8G     0  3.8G   0% /dev/shm
none                  3.8G  296K  3.8G   1% /var/run
none                  3.8G     0  3.8G   0% /var/lock
/dev/md0              4.5T  3.0T  1.6T  66% /opt

```

```
Sep 11 00:10:21 mcp kernel: [  241.330067] INFO: task jbd2/md0-8:1108 blocked for more than 120 seconds.
Sep 11 00:10:21 mcp kernel: [  241.330174] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 11 00:10:21 mcp kernel: [  241.330285] jbd2/md0-8      D 0000000000000000     0  1108      2 0x00000000
Sep 11 00:10:21 mcp kernel: [  241.330293]  ffff88020fe45d20 0000000000000046 ffff88020fe45fd8 ffff88020fe44000
Sep 11 00:10:21 mcp kernel: [  241.330300]  0000000000013d00 ffff88020c0d83b8 ffff88020fe45fd8 0000000000013d00
Sep 11 00:10:21 mcp kernel: [  241.330306]  ffffffff81a0b020 ffff88020c0d8000 ffff88020c0d8000 ffff8802058687a0
Sep 11 00:10:21 mcp kernel: [  241.330314] Call Trace:
Sep 11 00:10:21 mcp kernel: [  241.330325]  [<ffffffff81242e10>] jbd2_journal_commit_transaction+0x1b0/0x1190
Sep 11 00:10:21 mcp kernel: [  241.330333]  [<ffffffff8104ee98>] ? hrtick_update+0x38/0x40
Sep 11 00:10:21 mcp kernel: [  241.330340]  [<ffffffff8105820f>] ? dequeue_task_fair+0x8f/0xa0
Sep 11 00:10:21 mcp kernel: [  241.330347]  [<ffffffff8100a6e0>] ? __switch_to+0xc0/0x2f0
Sep 11 00:10:21 mcp kernel: [  241.330353]  [<ffffffff8107502b>] ? lock_timer_base.clone.20+0x3b/0x70
Sep 11 00:10:21 mcp kernel: [  241.330359]  [<ffffffff81087fb0>] ? autoremove_wake_function+0x0/0x40
Sep 11 00:10:21 mcp kernel: [  241.330365]  [<ffffffff81247f5b>] kjournald2+0xbb/0x220
Sep 11 00:10:21 mcp kernel: [  241.330370]  [<ffffffff81087fb0>] ? autoremove_wake_function+0x0/0x40
Sep 11 00:10:21 mcp kernel: [  241.330375]  [<ffffffff81247ea0>] ? kjournald2+0x0/0x220
Sep 11 00:10:21 mcp kernel: [  241.330380]  [<ffffffff81087866>] kthread+0x96/0xa0
Sep 11 00:10:21 mcp kernel: [  241.330385]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Sep 11 00:10:21 mcp kernel: [  241.330390]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Sep 11 00:10:21 mcp kernel: [  241.330395]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Sep 11 00:10:21 mcp kernel: [  241.330410] INFO: task rsync:2528 blocked for more than 120 seconds.
Sep 11 00:10:21 mcp kernel: [  241.330501] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 11 00:10:21 mcp kernel: [  241.330611] rsync           D 0000000000000002     0  2528   2527 0x00000000
Sep 11 00:10:21 mcp kernel: [  241.330617]  ffff88020f7a7860 0000000000000086 ffff88020f7a7fd8 ffff88020f7a6000
Sep 11 00:10:21 mcp kernel: [  241.330623]  0000000000013d00 ffff88020f4d4858 ffff88020f7a7fd8 0000000000013d00
Sep 11 00:10:21 mcp kernel: [  241.330629]  ffff88020fd2db80 ffff88020f4d44a0 00000002cfd11880 ffff88020f4d44a0
Sep 11 00:10:21 mcp kernel: [  241.330634] Call Trace:
Sep 11 00:10:21 mcp kernel: [  241.330641]  [<ffffffff815c30dd>] rwsem_down_failed_common+0xcd/0x170
Sep 11 00:10:21 mcp kernel: [  241.330648]  [<ffffffff815c31b5>] rwsem_down_read_failed+0x15/0x17
Sep 11 00:10:21 mcp kernel: [  241.330658]  [<ffffffff812e6ac4>] call_rwsem_down_read_failed+0x14/0x30
Sep 11 00:10:21 mcp kernel: [  241.330664]  [<ffffffff815c24c4>] ? down_read+0x24/0x30
Sep 11 00:10:21 mcp kernel: [  241.330670]  [<ffffffff8120687f>] ext4_map_blocks+0x4f/0x280
Sep 11 00:10:21 mcp kernel: [  241.330677]  [<ffffffff81191753>] ? alloc_buffer_head+0x43/0x50
Sep 11 00:10:21 mcp kernel: [  241.330682]  [<ffffffff812070ca>] ext4_da_get_block_prep+0x8a/0x140
Sep 11 00:10:21 mcp kernel: [  241.330687]  [<ffffffff81192e69>] ? create_empty_buffers+0xa9/0xe0
Sep 11 00:10:21 mcp kernel: [  241.330692]  [<ffffffff81194c8b>] __block_write_begin+0x1fb/0x570
Sep 11 00:10:21 mcp kernel: [  241.330697]  [<ffffffff81207040>] ? ext4_da_get_block_prep+0x0/0x140
Sep 11 00:10:21 mcp kernel: [  241.330704]  [<ffffffff8110cc09>] ? grab_cache_page_write_begin+0x79/0xc0
Sep 11 00:10:21 mcp kernel: [  241.330710]  [<ffffffff81208098>] ext4_da_write_begin+0x158/0x280
Sep 11 00:10:21 mcp kernel: [  241.330716]  [<ffffffff8110b902>] generic_perform_write+0xc2/0x1d0
Sep 11 00:10:21 mcp kernel: [  241.330722]  [<ffffffff8110ba6e>] generic_file_buffered_write+0x5e/0x90
Sep 11 00:10:21 mcp kernel: [  241.330732]  [<ffffffff8110d9f9>] __generic_file_aio_write+0x229/0x440
Sep 11 00:10:21 mcp kernel: [  241.330738]  [<ffffffff8110dc76>] generic_file_aio_write+0x66/0xd0
Sep 11 00:10:21 mcp kernel: [  241.330743]  [<ffffffff811fe439>] ext4_file_write+0x69/0x280
Sep 11 00:10:21 mcp kernel: [  241.330749]  [<ffffffff811646d2>] do_sync_write+0xd2/0x110
Sep 11 00:10:21 mcp kernel: [  241.330755]  [<ffffffff81104461>] ? __perf_event_task_sched_out+0x31/0x40
Sep 11 00:10:21 mcp kernel: [  241.330762]  [<ffffffff812ae958>] ? apparmor_file_permission+0x18/0x20
Sep 11 00:10:21 mcp kernel: [  241.330769]  [<ffffffff81279c8c>] ? security_file_permission+0x2c/0xb0
Sep 11 00:10:21 mcp kernel: [  241.330774]  [<ffffffff81164b01>] ? rw_verify_area+0x61/0xf0
Sep 11 00:10:21 mcp kernel: [  241.330778]  [<ffffffff81164e46>] vfs_write+0xc6/0x180
Sep 11 00:10:21 mcp kernel: [  241.330783]  [<ffffffff81165161>] sys_write+0x51/0x90
Sep 11 00:10:21 mcp kernel: [  241.330788]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
Sep 11 00:12:21 mcp kernel: [  361.330064] INFO: task jbd2/md0-8:1108 blocked for more than 120 seconds.
Sep 11 00:12:21 mcp kernel: [  361.330170] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 11 00:12:21 mcp kernel: [  361.330281] jbd2/md0-8      D 0000000000000000     0  1108      2 0x00000000
Sep 11 00:12:21 mcp kernel: [  361.330289]  ffff88020fe45d20 0000000000000046 ffff88020fe45fd8 ffff88020fe44000
Sep 11 00:12:21 mcp kernel: [  361.330296]  0000000000013d00 ffff88020c0d83b8 ffff88020fe45fd8 0000000000013d00
Sep 11 00:12:21 mcp kernel: [  361.330302]  ffffffff81a0b020 ffff88020c0d8000 ffff88020c0d8000 ffff8802058687a0
Sep 11 00:12:21 mcp kernel: [  361.330307] Call Trace:
Sep 11 00:12:21 mcp kernel: [  361.330319]  [<ffffffff81242e10>] jbd2_journal_commit_transaction+0x1b0/0x1190
Sep 11 00:12:21 mcp kernel: [  361.330326]  [<ffffffff8104ee98>] ? hrtick_update+0x38/0x40
Sep 11 00:12:21 mcp kernel: [  361.330333]  [<ffffffff8105820f>] ? dequeue_task_fair+0x8f/0xa0
Sep 11 00:12:21 mcp kernel: [  361.330340]  [<ffffffff8100a6e0>] ? __switch_to+0xc0/0x2f0
Sep 11 00:12:21 mcp kernel: [  361.330346]  [<ffffffff8107502b>] ? lock_timer_base.clone.20+0x3b/0x70
Sep 11 00:12:21 mcp kernel: [  361.330352]  [<ffffffff81087fb0>] ? autoremove_wake_function+0x0/0x40
Sep 11 00:12:21 mcp kernel: [  361.330359]  [<ffffffff81247f5b>] kjournald2+0xbb/0x220
Sep 11 00:12:21 mcp kernel: [  361.330363]  [<ffffffff81087fb0>] ? autoremove_wake_function+0x0/0x40
Sep 11 00:12:21 mcp kernel: [  361.330368]  [<ffffffff81247ea0>] ? kjournald2+0x0/0x220
Sep 11 00:12:21 mcp kernel: [  361.330373]  [<ffffffff81087866>] kthread+0x96/0xa0
Sep 11 00:12:21 mcp kernel: [  361.330378]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Sep 11 00:12:21 mcp kernel: [  361.330383]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Sep 11 00:12:21 mcp kernel: [  361.330387]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Sep 11 00:12:21 mcp kernel: [  361.330398] INFO: task rsync:2528 blocked for more than 120 seconds.
Sep 11 00:12:21 mcp kernel: [  361.330488] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 11 00:12:21 mcp kernel: [  361.330597] rsync           D 0000000000000002     0  2528   2527 0x00000000
Sep 11 00:12:21 mcp kernel: [  361.330604]  ffff88020f7a7860 0000000000000086 ffff88020f7a7fd8 ffff88020f7a6000
Sep 11 00:12:21 mcp kernel: [  361.330610]  0000000000013d00 ffff88020f4d4858 ffff88020f7a7fd8 0000000000013d00
Sep 11 00:12:21 mcp kernel: [  361.330615]  ffff88020fd2db80 ffff88020f4d44a0 00000002cfd11880 ffff88020f4d44a0
Sep 11 00:12:21 mcp kernel: [  361.330621] Call Trace:
Sep 11 00:12:21 mcp kernel: [  361.330628]  [<ffffffff815c30dd>] rwsem_down_failed_common+0xcd/0x170
Sep 11 00:12:21 mcp kernel: [  361.330634]  [<ffffffff815c31b5>] rwsem_down_read_failed+0x15/0x17
Sep 11 00:12:21 mcp kernel: [  361.330645]  [<ffffffff812e6ac4>] call_rwsem_down_read_failed+0x14/0x30
Sep 11 00:12:21 mcp kernel: [  361.330651]  [<ffffffff815c24c4>] ? down_read+0x24/0x30
Sep 11 00:12:21 mcp kernel: [  361.330657]  [<ffffffff8120687f>] ext4_map_blocks+0x4f/0x280
Sep 11 00:12:21 mcp kernel: [  361.330663]  [<ffffffff81191753>] ? alloc_buffer_head+0x43/0x50
Sep 11 00:12:21 mcp kernel: [  361.330669]  [<ffffffff812070ca>] ext4_da_get_block_prep+0x8a/0x140
Sep 11 00:12:21 mcp kernel: [  361.330674]  [<ffffffff81192e69>] ? create_empty_buffers+0xa9/0xe0
Sep 11 00:12:21 mcp kernel: [  361.330678]  [<ffffffff81194c8b>] __block_write_begin+0x1fb/0x570
Sep 11 00:12:21 mcp kernel: [  361.330683]  [<ffffffff81207040>] ? ext4_da_get_block_prep+0x0/0x140
Sep 11 00:12:21 mcp kernel: [  361.330690]  [<ffffffff8110cc09>] ? grab_cache_page_write_begin+0x79/0xc0
Sep 11 00:12:21 mcp kernel: [  361.330696]  [<ffffffff81208098>] ext4_da_write_begin+0x158/0x280
Sep 11 00:12:21 mcp kernel: [  361.330702]  [<ffffffff8110b902>] generic_perform_write+0xc2/0x1d0
Sep 11 00:12:21 mcp kernel: [  361.330708]  [<ffffffff8110ba6e>] generic_file_buffered_write+0x5e/0x90
Sep 11 00:12:21 mcp kernel: [  361.330714]  [<ffffffff8110d9f9>] __generic_file_aio_write+0x229/0x440
Sep 11 00:12:21 mcp kernel: [  361.330720]  [<ffffffff8110dc76>] generic_file_aio_write+0x66/0xd0
Sep 11 00:12:21 mcp kernel: [  361.330725]  [<ffffffff811fe439>] ext4_file_write+0x69/0x280
Sep 11 00:12:21 mcp kernel: [  361.330731]  [<ffffffff811646d2>] do_sync_write+0xd2/0x110
Sep 11 00:12:21 mcp kernel: [  361.330737]  [<ffffffff81104461>] ? __perf_event_task_sched_out+0x31/0x40
Sep 11 00:12:21 mcp kernel: [  361.330744]  [<ffffffff812ae958>] ? apparmor_file_permission+0x18/0x20
Sep 11 00:12:21 mcp kernel: [  361.330750]  [<ffffffff81279c8c>] ? security_file_permission+0x2c/0xb0
Sep 11 00:12:21 mcp kernel: [  361.330755]  [<ffffffff81164b01>] ? rw_verify_area+0x61/0xf0
Sep 11 00:12:21 mcp kernel: [  361.330760]  [<ffffffff81164e46>] vfs_write+0xc6/0x180
Sep 11 00:12:21 mcp kernel: [  361.330765]  [<ffffffff81165161>] sys_write+0x51/0x90
Sep 11 00:12:21 mcp kernel: [  361.330769]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
Sep 11 00:12:21 mcp kernel: [  361.330775] INFO: task rsync:2948 blocked for more than 120 seconds.
Sep 11 00:12:21 mcp kernel: [  361.330865] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 11 00:12:21 mcp kernel: [  361.330974] rsync           D 0000000000000001     0  2948   2947 0x00000000
Sep 11 00:12:21 mcp kernel: [  361.330980]  ffff8801e0d7db58 0000000000000086 ffff8801e0d7dfd8 ffff8801e0d7c000
Sep 11 00:12:21 mcp kernel: [  361.330985]  0000000000013d00 ffff88020f4d1a98 ffff8801e0d7dfd8 0000000000013d00
Sep 11 00:12:21 mcp kernel: [  361.330994]  ffff88020fd28000 ffff88020f4d16e0 ffff8802017a5030 ffff880204836800
Sep 11 00:12:21 mcp kernel: [  361.330999] Call Trace:
Sep 11 00:12:21 mcp kernel: [  361.331010]  [<ffffffff812406c2>] start_this_handle.clone.7+0x362/0x4a0
Sep 11 00:12:21 mcp kernel: [  361.331016]  [<ffffffff81087fb0>] ? autoremove_wake_function+0x0/0x40
Sep 11 00:12:21 mcp kernel: [  361.331022]  [<ffffffff812408ca>] jbd2__journal_start+0xca/0x110
Sep 11 00:12:21 mcp kernel: [  361.331027]  [<ffffffff81240923>] jbd2_journal_start+0x13/0x20
Sep 11 00:12:21 mcp kernel: [  361.331032]  [<ffffffff8121dc53>] ext4_journal_start_sb+0xb3/0x140
Sep 11 00:12:21 mcp kernel: [  361.331038]  [<ffffffff8120e614>] ext4_create+0x74/0x140
Sep 11 00:12:21 mcp kernel: [  361.331043]  [<ffffffff8116ef83>] ? generic_permission+0x23/0xc0
Sep 11 00:12:21 mcp kernel: [  361.331049]  [<ffffffff81173191>] vfs_create+0xb1/0x110
Sep 11 00:12:21 mcp kernel: [  361.331053]  [<ffffffff81173866>] do_last+0x346/0x410
Sep 11 00:12:21 mcp kernel: [  361.331058]  [<ffffffff81173cc2>] do_filp_open+0x392/0x7c0
Sep 11 00:12:21 mcp kernel: [  361.331064]  [<ffffffff812e6c77>] ? __strncpy_from_user+0x27/0x60
Sep 11 00:12:21 mcp kernel: [  361.331070]  [<ffffffff81180f27>] ? alloc_fd+0xf7/0x150
Sep 11 00:12:21 mcp kernel: [  361.331075]  [<ffffffff811642aa>] do_sys_open+0x6a/0x150
Sep 11 00:12:21 mcp kernel: [  361.331080]  [<ffffffff811643b0>] sys_open+0x20/0x30
Sep 11 00:12:21 mcp kernel: [  361.331084]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
Sep 11 00:14:21 mcp kernel: [  481.330062] INFO: task jbd2/md0-8:1108 blocked for more than 120 seconds.
Sep 11 00:14:21 mcp kernel: [  481.330170] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 11 00:14:21 mcp kernel: [  481.330281] jbd2/md0-8      D 0000000000000000     0  1108      2 0x00000000
Sep 11 00:14:21 mcp kernel: [  481.330289]  ffff88020fe45d20 0000000000000046 ffff88020fe45fd8 ffff88020fe44000
Sep 11 00:14:21 mcp kernel: [  481.330296]  0000000000013d00 ffff88020c0d83b8 ffff88020fe45fd8 0000000000013d00
Sep 11 00:14:21 mcp kernel: [  481.330302]  ffffffff81a0b020 ffff88020c0d8000 ffff88020c0d8000 ffff8802058687a0
Sep 11 00:14:21 mcp kernel: [  481.330308] Call Trace:
Sep 11 00:14:21 mcp kernel: [  481.330320]  [<ffffffff81242e10>] jbd2_journal_commit_transaction+0x1b0/0x1190
Sep 11 00:14:21 mcp kernel: [  481.330328]  [<ffffffff8104ee98>] ? hrtick_update+0x38/0x40
Sep 11 00:14:21 mcp kernel: [  481.330334]  [<ffffffff8105820f>] ? dequeue_task_fair+0x8f/0xa0
Sep 11 00:14:21 mcp kernel: [  481.330341]  [<ffffffff8100a6e0>] ? __switch_to+0xc0/0x2f0
Sep 11 00:14:21 mcp kernel: [  481.330348]  [<ffffffff8107502b>] ? lock_timer_base.clone.20+0x3b/0x70
Sep 11 00:14:21 mcp kernel: [  481.330354]  [<ffffffff81087fb0>] ? autoremove_wake_function+0x0/0x40
Sep 11 00:14:21 mcp kernel: [  481.330360]  [<ffffffff81247f5b>] kjournald2+0xbb/0x220
Sep 11 00:14:21 mcp kernel: [  481.330365]  [<ffffffff81087fb0>] ? autoremove_wake_function+0x0/0x40
Sep 11 00:14:21 mcp kernel: [  481.330370]  [<ffffffff81247ea0>] ? kjournald2+0x0/0x220
Sep 11 00:14:21 mcp kernel: [  481.330374]  [<ffffffff81087866>] kthread+0x96/0xa0
Sep 11 00:14:21 mcp kernel: [  481.330380]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
Sep 11 00:14:21 mcp kernel: [  481.330384]  [<ffffffff810877d0>] ? kthread+0x0/0xa0
Sep 11 00:14:21 mcp kernel: [  481.330389]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Sep 11 00:14:21 mcp kernel: [  481.330399] INFO: task rsync:2528 blocked for more than 120 seconds.
Sep 11 00:14:21 mcp kernel: [  481.330490] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 11 00:14:21 mcp kernel: [  481.330599] rsync           D 0000000000000002     0  2528   2527 0x00000000
Sep 11 00:14:21 mcp kernel: [  481.330605]  ffff88020f7a7860 0000000000000086 ffff88020f7a7fd8 ffff88020f7a6000
Sep 11 00:14:21 mcp kernel: [  481.330612]  0000000000013d00 ffff88020f4d4858 ffff88020f7a7fd8 0000000000013d00
Sep 11 00:14:21 mcp kernel: [  481.330617]  ffff88020fd2db80 ffff88020f4d44a0 00000002cfd11880 ffff88020f4d44a0
Sep 11 00:14:21 mcp kernel: [  481.330623] Call Trace:
Sep 11 00:14:21 mcp kernel: [  481.330630]  [<ffffffff815c30dd>] rwsem_down_failed_common+0xcd/0x170
Sep 11 00:14:21 mcp kernel: [  481.330636]  [<ffffffff815c31b5>] rwsem_down_read_failed+0x15/0x17
Sep 11 00:14:21 mcp kernel: [  481.330647]  [<ffffffff812e6ac4>] call_rwsem_down_read_failed+0x14/0x30
Sep 11 00:14:21 mcp kernel: [  481.330653]  [<ffffffff815c24c4>] ? down_read+0x24/0x30
Sep 11 00:14:21 mcp kernel: [  481.330658]  [<ffffffff8120687f>] ext4_map_blocks+0x4f/0x280
Sep 11 00:14:21 mcp kernel: [  481.330665]  [<ffffffff81191753>] ? alloc_buffer_head+0x43/0x50

```

Can anyone confirm this is probably the case?

I'm running 2x swap as the 8g of ram in the box and the drives are all sata2/3 1T drives (some hitachi, some western digital, etc.)

Tonight it's happening when I rsync a 1.3G file over.  I'll try to gather whether it's the same drive throwing the issue each time.


ETA:

Yep.  same drive each time has the LED pegged on while the rest in the raid just flash occasionally.  There's something rotten in this disk array.

---

