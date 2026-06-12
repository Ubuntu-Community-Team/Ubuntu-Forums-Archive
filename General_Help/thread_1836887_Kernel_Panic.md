---
title: "Kernel Panic"
date: 2011-08-31
forum: General Help
---

### Post by 11ghjones on 2011-08-31
I've had this problem for a while, up till the kernel update today (I haven't tested it enough after the update). Every so often (not every time, just enough to be annoying) when I boot up my computer, it appears to lock up before GDM starts and just display a black screen.  I don't get any sort of graphic before GDM ever, as I'm using a NVIDIA card with the official drivers, so that's not unusual, but it stops before the login screen appears.  I noticed my keyboard lights flashing, so I guessed it may be a kernel panic.  I checked my kernel logs, and sure enough, there it was.

Here's where I believe the problem to lie:

```

Aug 31 09:00:58 gjones-desktop kernel: [    7.747672] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Aug 31 09:00:58 gjones-desktop kernel: [   11.931609] <30>udev[352]: starting version 167
Aug 31 09:00:58 gjones-desktop kernel: [   11.944341] nvidia: module license 'NVIDIA' taints kernel.
Aug 31 09:00:58 gjones-desktop kernel: [   11.944343] Disabling lock debugging due to kernel taint
Aug 31 09:00:58 gjones-desktop kernel: [   11.944917] lp: driver loaded but no devices found
Aug 31 09:00:58 gjones-desktop kernel: [   11.954226] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 31 09:00:58 gjones-desktop kernel: [   11.963091] cfg80211: Calling CRDA to update world regulatory domain
Aug 31 09:00:58 gjones-desktop kernel: [   11.988733] rt2800pci 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 31 09:00:58 gjones-desktop kernel: [   11.988742] rt2800pci 0000:04:00.0: setting latency timer to 64
Aug 31 09:00:58 gjones-desktop kernel: [   12.024413] ------------[ cut here ]------------
Aug 31 09:00:58 gjones-desktop kernel: [   12.024416] kernel BUG at /build/buildd/linux-2.6.38/fs/ext4/extents.c:1943!
Aug 31 09:00:58 gjones-desktop kernel: [   12.024418] invalid opcode: 0000 [#1] SMP 
Aug 31 09:00:58 gjones-desktop kernel: [   12.024419] last sysfs file: /sys/devices/virtual/vc/vcs3/uevent
Aug 31 09:00:58 gjones-desktop kernel: [   12.024421] CPU 3 
Aug 31 09:00:58 gjones-desktop kernel: [   12.024421] Modules linked in: snd_timer(+) snd_seq_device snd rt2800pci(+) rt2800lib crc_ccitt rt2x00pci rt2x00lib mac80211 cfg80211 eeprom_93cx6 shpchp soundcore lp snd_page_alloc parport uvesafb usbhid hid firewire_ohci firewire_core crc_itu_t r8169
Aug 31 09:00:58 gjones-desktop kernel: [   12.024432] 
Aug 31 09:00:58 gjones-desktop kernel: [   12.024433] Pid: 653, comm: 91-release-upgr Tainted: P            2.6.38-11-generic #48-Ubuntu Gigabyte Technology Co., Ltd. Z68X-UD3-B3/Z68X-UD3-B3
Aug 31 09:00:58 gjones-desktop kernel: [   12.024436] RIP: 0010:[<ffffffff812244e9>]  [<ffffffff812244e9>] ext4_ext_put_in_cache+0x79/0x80
Aug 31 09:00:58 gjones-desktop kernel: [   12.024442] RSP: 0000:ffff88010a0e5768  EFLAGS: 00010246
Aug 31 09:00:58 gjones-desktop kernel: [   12.024443] RAX: 000000000210a7df RBX: ffff88010a0e58e8 RCX: 000000000210a7df
Aug 31 09:00:58 gjones-desktop kernel: [   12.024445] RDX: 0000000000000000 RSI: 0000000000000000 RDI: ffff88011b090f30
Aug 31 09:00:58 gjones-desktop kernel: [   12.024446] RBP: ffff88010a0e5798 R08: 0000000000000000 R09: 000000000210a7df
Aug 31 09:00:58 gjones-desktop kernel: [   12.024447] R10: 0000000000000000 R11: 0000000000000000 R12: 0000000000000000
Aug 31 09:00:58 gjones-desktop kernel: [   12.024448] R13: 0000000000000000 R14: ffff88011b090f30 R15: 000000000210a7df
Aug 31 09:00:58 gjones-desktop kernel: [   12.024450] FS:  00007fcc3536b720(0000) GS:ffff8800df4c0000(0000) knlGS:0000000000000000
Aug 31 09:00:58 gjones-desktop kernel: [   12.024451] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 31 09:00:58 gjones-desktop kernel: [   12.024452] CR2: 00007f4872f602b0 CR3: 0000000115668000 CR4: 00000000000406e0
Aug 31 09:00:58 gjones-desktop kernel: [   12.024453] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 31 09:00:58 gjones-desktop kernel: [   12.024455] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 31 09:00:58 gjones-desktop kernel: [   12.024456] Process 91-release-upgr (pid: 653, threadinfo ffff88010a0e4000, task ffff88010a0d5b80)
Aug 31 09:00:58 gjones-desktop kernel: [   12.024457] Stack:
Aug 31 09:00:58 gjones-desktop kernel: [   12.024458]  00000000000280da ffff88010a0e58e8 ffff8801132e48a0 ffff88011b090e80
Aug 31 09:00:58 gjones-desktop kernel: [   12.024460]  ffff88011b090f30 0000000000000000 ffff88010a0e5868 ffffffff81228334
Aug 31 09:00:58 gjones-desktop kernel: [   12.024462]  0000000000000000 ffff88011f7fcc00 00000000000084d0 000000000210a7df
Aug 31 09:00:58 gjones-desktop kernel: [   12.024464] Call Trace:
Aug 31 09:00:58 gjones-desktop kernel: [   12.024467]  [<ffffffff81228334>] ext4_ext_map_blocks+0x234/0x770
Aug 31 09:00:58 gjones-desktop kernel: [   12.024472]  [<ffffffff8115d497>] ? __mem_cgroup_commit_charge.clone.39+0x67/0xb0
Aug 31 09:00:58 gjones-desktop kernel: [   12.024475]  [<ffffffff812068a4>] ext4_map_blocks+0x74/0x280
Aug 31 09:00:58 gjones-desktop kernel: [   12.024477]  [<ffffffff81113714>] ? get_page_from_freelist+0x264/0x650
Aug 31 09:00:58 gjones-desktop kernel: [   12.024479]  [<ffffffff81206b56>] _ext4_get_block+0xa6/0x160
Aug 31 09:00:58 gjones-desktop kernel: [   12.024481]  [<ffffffff81206c76>] ext4_get_block+0x16/0x20
Aug 31 09:00:58 gjones-desktop kernel: [   12.024484]  [<ffffffff8119c032>] do_mpage_readpage+0x432/0x510
Aug 31 09:00:58 gjones-desktop kernel: [   12.024487]  [<ffffffff8110ca9a>] ? add_to_page_cache_locked+0xea/0x160
Aug 31 09:00:58 gjones-desktop kernel: [   12.024489]  [<ffffffff8119c282>] mpage_readpages+0x102/0x150
Aug 31 09:00:58 gjones-desktop kernel: [   12.024491]  [<ffffffff81206c60>] ? ext4_get_block+0x0/0x20
Aug 31 09:00:58 gjones-desktop kernel: [   12.024492]  [<ffffffff81206c60>] ? ext4_get_block+0x0/0x20
Aug 31 09:00:58 gjones-desktop kernel: [   12.024494]  [<ffffffff81113442>] ? prep_new_page+0x142/0x1b0
Aug 31 09:00:58 gjones-desktop kernel: [   12.024496]  [<ffffffff81149f95>] ? alloc_pages_current+0xa5/0x110
Aug 31 09:00:58 gjones-desktop kernel: [   12.024498]  [<ffffffff81201e8d>] ext4_readpages+0x1d/0x20
Aug 31 09:00:58 gjones-desktop kernel: [   12.024501]  [<ffffffff8111748b>] __do_page_cache_readahead+0x14b/0x220
Aug 31 09:00:58 gjones-desktop kernel: [   12.024503]  [<ffffffff811178c1>] ra_submit+0x21/0x30
Aug 31 09:00:58 gjones-desktop kernel: [   12.024505]  [<ffffffff811179e5>] ondemand_readahead+0x115/0x230
Aug 31 09:00:58 gjones-desktop kernel: [   12.024507]  [<ffffffff81117bf1>] page_cache_sync_readahead+0x31/0x50
Aug 31 09:00:58 gjones-desktop kernel: [   12.024509]  [<ffffffff8110d266>] do_generic_file_read.clone.23+0x2c6/0x450
Aug 31 09:00:58 gjones-desktop kernel: [   12.024511]  [<ffffffff8110deaa>] generic_file_aio_read+0x1ca/0x240
Aug 31 09:00:58 gjones-desktop kernel: [   12.024514]  [<ffffffff811647e2>] do_sync_read+0xd2/0x110
Aug 31 09:00:58 gjones-desktop kernel: [   12.024516]  [<ffffffff812a9884>] ? aa_get_name+0x84/0x120
Aug 31 09:00:58 gjones-desktop kernel: [   12.024519]  [<ffffffff81279cf3>] ? security_file_permission+0x93/0xb0
Aug 31 09:00:58 gjones-desktop kernel: [   12.024521]  [<ffffffff81164b01>] ? rw_verify_area+0x61/0xf0
Aug 31 09:00:58 gjones-desktop kernel: [   12.024523]  [<ffffffff81164fc3>] vfs_read+0xc3/0x180
Aug 31 09:00:58 gjones-desktop kernel: [   12.024525]  [<ffffffff8116a1f6>] kernel_read+0x46/0x60
Aug 31 09:00:58 gjones-desktop kernel: [   12.024527]  [<ffffffff8116a2e5>] prepare_binprm+0xd5/0x100
Aug 31 09:00:58 gjones-desktop kernel: [   12.024528]  [<ffffffff8116c46a>] do_execve+0x1da/0x2d0
Aug 31 09:00:58 gjones-desktop kernel: [   12.024531]  [<ffffffff8101521a>] sys_execve+0x4a/0x80
Aug 31 09:00:58 gjones-desktop kernel: [   12.024533]  [<ffffffff8100c45c>] stub_execve+0x6c/0xc0
Aug 31 09:00:58 gjones-desktop kernel: [   12.024534] Code: 1c 03 00 00 48 89 df 4d 89 be 10 03 00 00 e8 4f 47 e1 ff 66 90 48 8b 5d d8 4c 8b 65 e0 4c 8b 6d e8 4c 8b 75 f0 4c 8b 7d f8 c9 c3 <0f> 0b 0f 1f 44 00 00 55 48 89 e5 41 54 53 0f 1f 44 00 00 0f b7 
Aug 31 09:00:58 gjones-desktop kernel: [   12.024551] RIP  [<ffffffff812244e9>] ext4_ext_put_in_cache+0x79/0x80
Aug 31 09:00:58 gjones-desktop kernel: [   12.024553]  RSP <ffff88010a0e5768>
Aug 31 09:00:58 gjones-desktop kernel: [   12.024556] ---[ end trace 9ac29e5859d4d5f6 ]---

```

So I notice that the last thing before the panic has to do with a Ralink wireless module.  The card itself (Asus PCE-N13) could be the problem, as my wireless connection has been slowly degrading lately. But looking at the "kernel bug", it's mentioning extents and other fs related things.  Anyone with more kernel knowledge than little me have any idea what's going on?

---

### Post by 11ghjones on 2011-09-01
OK, now after the kernel upgrade, I still am getting the same problem, and now a freezing problem that somehow involves init.  I got a virtual terminal during boot up, and at the end it wrote to the screen:

Kernel panic -- not syncing: Attempted to kill init!

I didn't write everything down, as I naively thought that it would be written to the kernel log, but apparently I was wrong.  Any thoughts?

---

### Post by 11ghjones on 2011-09-01
Anyone?  Please?

---

### Post by whiskers751 on 2012-03-11
Can't you boot an earlier kernel?

---

