---
title: "ubuntu 11.04 btrfs mount crash after kernel 3.0 installed"
date: 2011-08-18
forum: General Help
---

### Post by masuch on 2011-08-18
Hi,

  I have/had installed ubuntu 11.04 on btrfs file system. It has been working more or less fine. Couple of times I had to reinstall kernel or proprietary catalyst 11.6 graphics driver (or both) until I firstly installed ubuntu kernel version 3.0. It is going to freeze in busybox. only cold reset is working.
  From this moment I cannot even mount btrfs file system at all. From log I got error:


[ 2209.813049] ------------[ cut here ]------------
[ 2209.813051] kernel BUG at /build/buildd/linux-3.0.0/fs/btrfs/inode.c:4586!
[ 2209.813052] invalid opcode: 0000 [#1] SMP 
[ 2209.813053] CPU 1 
[ 2209.813054] Modules linked in: ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs reiserfs nls_iso8859_1 nls_cp437 vfat fat binfmt_misc rfcomm bnep pci_stub vboxpci vboxnetadp vboxnetflt vboxdrv speedstep_lib kvm_intel kvm dm_crypt uvcvideo snd_hda_codec_hdmi videodev ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec parport_pc psmouse v4l2_compat_ioctl32 eeepc_wmi snd_usb_audio snd_usbmidi_lib lp asus_wmi btusb sparse_keymap bluetooth parport snd_hwdep serio_raw snd_pcm mei(C) fglrx(P) snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc usb_storage uas raid10 raid456 async_pq async_xor async_memcpy async_raid6_recov usbhid hid raid6_pq async_tx raid1 raid0 multipath linear dm_raid45 xor btrfs zlib_deflate libcrc32c vesafb mxm_wmi ahci libahci xhci_hcd e1000e wmi
[ 2209.813076] 
[ 2209.813077] Pid: 19776, comm: mount Tainted: P         C  3.0.0-8-generic #10-Ubuntu System manufacturer System Product Name/Maximus IV Extreme
[ 2209.813079] RIP: 0010:[<ffffffffa00d72b1>]  [<ffffffffa00d72b1>] btrfs_add_link+0x161/0x1c0 [btrfs]
[ 2209.813088] RSP: 0018:ffff8804257957c8  EFLAGS: 00010282
[ 2209.813088] RAX: 00000000ffffffef RBX: ffff88032b754098 RCX: 0000000000000092
[ 2209.813089] RDX: 0000000000000091 RSI: 000060fbc0805030 RDI: ffffea000aa7b438
[ 2209.813090] RBP: ffff880425795838 R08: ffffffffa00a91ca R09: ffff880425795748
[ 2209.813091] R10: ffffffffa0115f00 R11: 0000000000000000 R12: ffff88032b754488
[ 2209.813092] R13: ffff8802714d9800 R14: 000000000000000e R15: ffff880306b25000
[ 2209.813093] FS:  00007ffafae9d800(0000) GS:ffff88043f440000(0000) knlGS:0000000000000000
[ 2209.813094] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[ 2209.813095] CR2: 00007f57ad9bf000 CR3: 000000041eea1000 CR4: 00000000000406e0
[ 2209.813095] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 2209.813096] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 2209.813097] Process mount (pid: 19776, threadinfo ffff880425794000, task ffff88033217ade0)
[ 2209.813098] Stack:
[ 2209.813099]  ffff880400000001 0000000000000078 ffff880425795968 0000000000000078
[ 2209.813100]  0000000000000ece 0000000000000001 0000000000001000 0000000000000000
[ 2209.813102]  ffff88042664f000 0000000000000000 000000000000015f ffff880425795aa8
[ 2209.813103] Call Trace:
[ 2209.813109]  [<ffffffffa010034f>] add_inode_ref+0x30f/0x3d0 [btrfs]
[ 2209.813114]  [<ffffffffa010242e>] replay_one_buffer+0x27e/0x330 [btrfs]
[ 2209.813119]  [<ffffffffa0100a47>] walk_up_log_tree+0x117/0x2a0 [btrfs]
[ 2209.813123]  [<ffffffffa0101128>] walk_log_tree+0xd8/0x240 [btrfs]
[ 2209.813127]  [<ffffffffa010404d>] btrfs_recover_log_trees+0x22d/0x330 [btrfs]
[ 2209.813132]  [<ffffffffa01021b0>] ? replay_one_extent+0x580/0x580 [btrfs]
[ 2209.813137]  [<ffffffffa00c949d>] open_ctree+0x13ed/0x1790 [btrfs]
[ 2209.813139]  [<ffffffff812f7c74>] ? snprintf+0x34/0x40
[ 2209.813143]  [<ffffffffa00a4838>] btrfs_fill_super.clone.25+0x78/0x150 [btrfs]
[ 2209.813145]  [<ffffffff811d7c64>] ? disk_name+0x64/0xc0
[ 2209.813146]  [<ffffffff812f49a7>] ? strlcpy+0x47/0x60
[ 2209.813150]  [<ffffffffa00a6766>] btrfs_mount+0x3b6/0x460 [btrfs]
[ 2209.813153]  [<ffffffff811723d7>] mount_fs+0x47/0x1c0
[ 2209.813154]  [<ffffffff8118cfe3>] vfs_kern_mount+0x63/0xd0
[ 2209.813156]  [<ffffffff8118d894>] do_kern_mount+0x54/0x110
[ 2209.813157]  [<ffffffff8118f40a>] do_mount+0x1ea/0x230
[ 2209.813159]  [<ffffffff8118f830>] sys_mount+0x90/0xe0
[ 2209.813161]  [<ffffffff815f1d82>] system_call_fastpath+0x16/0x1b
[ 2209.813161] Code: 44 89 f1 4c 89 ee 4c 89 ff 4c 89 1c 24 4c 89 55 a8 4c 89 5d a0 e8 c0 b1 fe ff 4c 8b 5d a0 4c 8b 55 a8 85 c0 75 b4 e9 2d ff ff ff <0f> 0b 49 8b b4 24 68 fe ff ff 48 8d 7d b0 b9 11 00 00 00 4d 89 
[ 2209.813173] RIP  [<ffffffffa00d72b1>] btrfs_add_link+0x161/0x1c0 [btrfs]
[ 2209.813178]  RSP <ffff8804257957c8>
[ 2209.813179] ---[ end trace e8dcfe86883a4fa2 ]---


Does anybody know how to fix it?

Thanks for any help,
Martin

---

### Post by masuch on 2011-08-24
Unfortunately application of btrfs-zero-log from git repository did not help on kernel 3.0.3. But, I have read that it should be fixed in 3.1  kernel ... .

---

### Post by masuch on 2011-09-06
Finally it works with kernel 3.0.4  
But another problem appears. When I remove some kernel/s - it is going to crash after restart but on second chance it works. From log/s it seems to has something to do with catalyst 11.8 but not sure. Does anybody else has such problem - any idea what is going on ?

---

