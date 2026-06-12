---
title: "Problem with Server Locking Up"
date: 2009-12-25
forum: General Help
---

### Post by cantdrive55 on 2009-12-25
So for the past week I've been having problem with my server locking up on me. I was checking through the logs and found this: ```
Dec 25 00:05:30 poseidon kernel: [  369.175469] ------------[ cut here ]------------
Dec 25 00:05:30 poseidon kernel: [  369.175544] kernel BUG at /build/buildd/linux-2.6.28/fs/ext4/inode.c:1749!
Dec 25 00:05:30 poseidon kernel: [  369.175615] invalid opcode: 0000 [#1] SMP
Dec 25 00:05:30 poseidon kernel: [  369.175777] last sysfs file: /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
Dec 25 00:05:30 poseidon kernel: [  369.175860] Dumping ftrace buffer:
Dec 25 00:05:30 poseidon kernel: [  369.175926]    (ftrace buffer empty)
Dec 25 00:05:30 poseidon kernel: [  369.175991] CPU 0
Dec 25 00:05:30 poseidon kernel: [  369.176101] Modules linked in: video output input_polldev it87 hwmon_vid lp psmouse ppdev i2c_viapro serio_raw pcspkr via_agp shpchp parport_pc parport r8169 mii fbcon ti$
Dec 25 00:05:30 poseidon kernel: [  369.177315] Pid: 31, comm: pdflush Not tainted 2.6.28-17-server #58-Ubuntu
Dec 25 00:05:30 poseidon kernel: [  369.177385] RIP: 0010:[<ffffffff803698b0>]  [<ffffffff803698b0>] mpage_put_bnr_to_bhs+0x270/0x2c0
Dec 25 00:05:30 poseidon kernel: [  369.177527] RSP: 0018:ffff88007d7df740  EFLAGS: 00010246
Dec 25 00:05:30 poseidon kernel: [  369.177595] RAX: 4000000000000838 RBX: 00000000000015cb RCX: ffff88002dbd8930
Dec 25 00:05:30 poseidon kernel: [  369.177667] RDX: ffffe200009d37d0 RSI: 0000000000000008 RDI: ffff88007d7df7b0
Dec 25 00:05:30 poseidon kernel: [  369.177738] RBP: ffff88007d7df810 R08: 00000000000013f5 R09: 00000000000017ff
Dec 25 00:05:30 poseidon kernel: [  369.177809] R10: 000000000000000e R11: 00000000000015d1 R12: 0000000000e235cb
Dec 25 00:05:30 poseidon kernel: [  369.177879] R13: 00000000000015cb R14: 0000000000001800 R15: ffff88002e5707e0
Dec 25 00:05:30 poseidon kernel: [  369.177951] FS:  0000000000000000(0000) GS:ffffffff80a9b000(0000) knlGS:0000000000000000
Dec 25 00:05:30 poseidon kernel: [  369.178034] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Dec 25 00:05:30 poseidon kernel: [  369.178103] CR2: 00007f63e445d000 CR3: 000000006e194000 CR4: 00000000000006a0
Dec 25 00:05:30 poseidon kernel: [  369.178174] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec 25 00:05:30 poseidon kernel: [  369.178245] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec 25 00:05:30 poseidon kernel: [  369.178317] Process pdflush (pid: 31, threadinfo ffff88007d7de000, task ffff88007d7e1660)
Dec 25 00:05:30 poseidon kernel: [  369.178400] Stack:
Dec 25 00:05:30 poseidon kernel: [  369.178463]  00000000000017ff 00000000000013f5 ffff88007d7df778 ffff88002e5708f0
Dec 25 00:05:30 poseidon kernel: [  369.178681]  000000000000000e 0000000000000000 ffffe200009d3610 ffffe200009d3648
Dec 25 00:05:30 poseidon kernel: [  369.179002]  ffffe200009d3680 ffffe200009d36b8 ffffe200009d36f0 ffffe200009d3728
Dec 25 00:05:30 poseidon kernel: [  369.179386] Call Trace:
Dec 25 00:05:30 poseidon kernel: [  369.179451]  [<ffffffff80369ca6>] mpage_da_map_blocks+0x316/0x3b0
Dec 25 00:05:30 poseidon kernel: [  369.179570]  [<ffffffff8040614b>] ? generic_make_request+0x37b/0x4b0
Dec 25 00:05:30 poseidon kernel: [  369.179692]  [<ffffffff802b3393>] ? mempool_alloc+0x53/0x130
Dec 25 00:05:30 poseidon kernel: [  369.179812]  [<ffffffff8036a20c>] mpage_add_bh_to_extent+0x3c/0xe0
Dec 25 00:05:30 poseidon kernel: [  369.179932]  [<ffffffff8036ca98>] __mpage_da_writepage+0x158/0x1c0
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff802b09ca>] ? find_get_pages_tag+0x4a/0x120
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff802bff4e>] ? __dec_zone_page_state+0x1e/0x20
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff802b7de0>] ? __add_bdi_stat+0x30/0x40
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff802b8dd8>] write_cache_pages+0x228/0x480
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff8036c940>] ? __mpage_da_writepage+0x0/0x1c0
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff8036a01b>] ext4_da_writepages+0x2db/0x490
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff8036b310>] ? ext4_da_get_block_write+0x0/0x180
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff802b9088>] do_writepages+0x28/0x50
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff803070d5>] __sync_single_inode+0x75/0x330
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff803073e3>] __writeback_single_inode+0x53/0x1b0
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff80307ac4>] generic_sync_sb_inodes+0x314/0x4e0
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff80307e6a>] writeback_inodes+0x5a/0x100
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff802b8500>] background_writeout+0xb0/0xe0
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff802b9876>] __pdflush+0x136/0x220
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff802b99b6>] pdflush+0x56/0x60
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff802b8450>] ? background_writeout+0x0/0xe0
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff802b9960>] ? pdflush+0x0/0x60
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff80268659>] kthread+0x49/0x90
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff80213979>] child_rip+0xa/0x11
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff80268610>] ? kthread+0x0/0x90
Dec 25 00:05:30 poseidon kernel: [  369.180004]  [<ffffffff8021396f>] ? child_rip+0x0/0x11
Dec 25 00:05:30 poseidon kernel: [  369.180004] Code: 44 00 00 44 8b 95 50 ff ff ff 45 85 d2 75 24 4d 39 cd 0f 86 34 fe ff ff 48 81 c4 a8 00 00 00 5b 41 5c 41 5d 41 5e 41 5f c9 c3 90 <0f> 0b eb fe 0f 1f 40 $
Dec 25 00:05:30 poseidon kernel: [  369.180004] RIP  [<ffffffff803698b0>] mpage_put_bnr_to_bhs+0x270/0x2c0
Dec 25 00:05:30 poseidon kernel: [  369.180004]  RSP <ffff88007d7df740>
Dec 25 00:05:30 poseidon kernel: [  369.185953] ---[ end trace d4db6e63c97ea733 ]---


```

Any idea what the problem might be?

---

