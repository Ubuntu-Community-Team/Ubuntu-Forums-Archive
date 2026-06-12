---
title: "Shell crash after npcmount"
date: 2011-05-17
forum: General Help
---

### Post by skyde77 on 2011-05-17
Hello,

After upgrading to 11.04 I have encountered the following problem.
When I npcmount a drive, screen turns to black and I something like below is on the screen.
I can recover with ctrl+alt+F8/F7 but the shell will be very unstable. Pressing tab crashes again and I cannot umount the npcmounted drive since it is busy etc.
Reading the second line of the trace talks about kernel BUG so what should I do?

May 17 09:58:56 T1500 kernel: [  141.061059] ------------[ cut here ]------------
May 17 09:58:56 T1500 kernel: [  141.061111] kernel BUG at /build/buildd/linux-2.6.38/fs/dcache.c:2134!
May 17 09:58:56 T1500 kernel: [  141.061166] invalid opcode: 0000 [#1] SMP 
May 17 09:58:56 T1500 kernel: [  141.061209] last sysfs file: /sys/devices/virtual/bdi/ncpfs-1/uevent
May 17 09:58:56 T1500 kernel: [  141.061261] CPU 2 
May 17 09:58:56 T1500 kernel: [  141.061280] Modules linked in: nls_cp850 nls_utf8 ncpfs binfmt_misc parport_pc ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event radeon snd_seq snd_timer snd_seq_device snd ttm drm_kms_helper psmouse dcdbas serio_raw soundcore snd_page_alloc drm i2c_algo_bit lp parport usbhid hid ahci tg3 libahci
May 17 09:58:56 T1500 kernel: [  141.061661] 
May 17 09:58:56 T1500 kernel: [  141.061678] Pid: 1800, comm: gvfs-gdu-volume Not tainted 2.6.38-8-generic #42-Ubuntu Dell Inc. Precision T1500/0XC7MM
May 17 09:58:56 T1500 kernel: [  141.061780] RIP: 0010:[<ffffffff81179495>]  [<ffffffff81179495>] dentry_update_name_case+0x75/0x80
May 17 09:58:56 T1500 kernel: [  141.061862] RSP: 0018:ffff88017b581988  EFLAGS: 00010246
May 17 09:58:56 T1500 kernel: [  141.061906] RAX: 0000000000000001 RBX: ffff88017b581e58 RCX: ffff88017032a840
May 17 09:58:56 T1500 kernel: [  141.061964] RDX: 0000000000000000 RSI: ffff88017b581a98 RDI: ffff88017032a840
May 17 09:58:56 T1500 kernel: [  141.062020] RBP: ffff88017b5819a8 R08: 000000000000006b R09: ffff88017032a87e
May 17 09:58:56 T1500 kernel: [  141.062076] R10: ffffffffa02a1000 R11: ffff88017b581aa8 R12: ffff88017032a840
May 17 09:58:56 T1500 kernel: [  141.062133] R13: ffff88017b581a98 R14: 0000000000000000 R15: ffff88017b581c58
May 17 09:58:56 T1500 kernel: [  141.062190] FS:  00007f7748bc37c0(0000) GS:ffff8800bf480000(0000) knlGS:0000000000000000
May 17 09:58:56 T1500 kernel: [  141.062255] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 17 09:58:56 T1500 kernel: [  141.062301] CR2: 00007f7747e32ac0 CR3: 000000017b635000 CR4: 00000000000006e0
May 17 09:58:56 T1500 kernel: [  141.062358] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 17 09:58:56 T1500 kernel: [  141.062414] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 17 09:58:56 T1500 kernel: [  141.062471] Process gvfs-gdu-volume (pid: 1800, threadinfo ffff88017b580000, task ffff880184f52dc0)
May 17 09:58:56 T1500 kernel: [  141.062541] Stack:
May 17 09:58:56 T1500 kernel: [  141.062559]  ffff88017027fb40 ffff88017b581e58 ffff88017027fb40 ffff8801703a0048
May 17 09:58:56 T1500 kernel: [  141.062631]  ffff88017b581be8 ffffffffa03120bd ffff88017b581a18 ffffffff8100a82e
May 17 09:58:56 T1500 kernel: [  141.062702]  ffff88017b5819d8 ffff88017032a840 ffffffff81176ab0 ffff88017b581f38
May 17 09:58:56 T1500 kernel: [  141.062774] Call Trace:
May 17 09:58:56 T1500 kernel: [  141.062802]  [<ffffffffa03120bd>] ncp_fill_cache.clone.15+0x22d/0x670 [ncpfs]
May 17 09:58:56 T1500 kernel: [  141.062865]  [<ffffffff8100a82e>] ? __switch_to+0x20e/0x2f0
May 17 09:58:56 T1500 kernel: [  141.062912]  [<ffffffff81176ab0>] ? filldir+0x0/0xe0
May 17 09:58:56 T1500 kernel: [  141.062959]  [<ffffffffa031a7d7>] ? do_ncp_rpc_call+0x197/0x2e0 [ncpfs]
May 17 09:58:56 T1500 kernel: [  141.063015]  [<ffffffff81087f30>] ? autoremove_wake_function+0x0/0x40
May 17 09:58:56 T1500 kernel: [  141.063070]  [<ffffffff8113c872>] ? map_vm_area+0x32/0x50
May 17 09:58:56 T1500 kernel: [  141.063116]  [<ffffffff81038c79>] ? default_spin_lock_flags+0x9/0x10
May 17 09:58:56 T1500 kernel: [  141.063171]  [<ffffffffa031aa7e>] ? ncp_do_request+0x15e/0x180 [ncpfs]
May 17 09:58:56 T1500 kernel: [  141.063227]  [<ffffffffa031b802>] ? ncp_request2+0x52/0x90 [ncpfs]
May 17 09:58:56 T1500 kernel: [  141.063280]  [<ffffffffa031b979>] ? ncp_unlock_server+0x29/0x40 [ncpfs]
May 17 09:58:56 T1500 kernel: [  141.063337]  [<ffffffffa0319398>] ? ncp_search_for_fileset+0x1f8/0x260 [ncpfs]
May 17 09:58:56 T1500 kernel: [  141.063396]  [<ffffffff81176ab0>] ? filldir+0x0/0xe0
May 17 09:58:56 T1500 kernel: [  141.063438]  [<ffffffff81176ab0>] ? filldir+0x0/0xe0
May 17 09:58:56 T1500 kernel: [  141.063482]  [<ffffffffa03127c8>] ncp_do_readdir+0x198/0x1e0 [ncpfs]
May 17 09:58:56 T1500 kernel: [  141.063538]  [<ffffffff811815ee>] ? vfsmount_lock_local_unlock+0x1e/0x30
May 17 09:58:56 T1500 kernel: [  141.063595]  [<ffffffff811831e6>] ? mntput_no_expire+0x36/0xf0
May 17 09:58:56 T1500 kernel: [  141.063644]  [<ffffffff811832bf>] ? mntput+0x1f/0x30
May 17 09:58:56 T1500 kernel: [  141.063687]  [<ffffffff8116eff2>] ? path_put+0x22/0x30
May 17 09:58:56 T1500 kernel: [  141.063731]  [<ffffffff812df74e>] ? radix_tree_lookup_slot+0xe/0x10
May 17 09:58:56 T1500 kernel: [  141.063785]  [<ffffffff8110c81e>] ? find_get_page+0x1e/0x90
May 17 09:58:56 T1500 kernel: [  141.067827]  [<ffffffff8110c8c7>] ? find_lock_page+0x37/0x80
May 17 09:58:56 T1500 kernel: [  141.071884]  [<ffffffffa0313196>] ncp_readdir+0x366/0x5f0 [ncpfs]
May 17 09:58:56 T1500 kernel: [  141.075917]  [<ffffffff81176ab0>] ? filldir+0x0/0xe0
May 17 09:58:56 T1500 kernel: [  141.079907]  [<ffffffff81176ab0>] ? filldir+0x0/0xe0
May 17 09:58:56 T1500 kernel: [  141.083845]  [<ffffffff81176998>] vfs_readdir+0xb8/0xe0
May 17 09:58:56 T1500 kernel: [  141.087763]  [<ffffffff81176c89>] sys_getdents+0x89/0xf0
May 17 09:58:56 T1500 kernel: [  141.091676]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
May 17 09:58:56 T1500 kernel: [  141.095575] Code: 8b 7c 24 28 49 8b 75 08 e8 99 d1 16 00 41 83 44 24 04 01 48 89 df e8 9b f7 eb ff 66 90 48 8b 5d e8 4c 8b 65 f0 4c 8b 6d f8 c9 c3 <0f> 0b 0f 0b 0f 1f 80 00 00 00 00 55 48 89 e5 48 83 ec 10 48 89 
May 17 09:58:56 T1500 kernel: [  141.099979] RIP  [<ffffffff81179495>] dentry_update_name_case+0x75/0x80
May 17 09:58:56 T1500 kernel: [  141.104197]  RSP <ffff88017b581988>
May 17 09:58:56 T1500 kernel: [  141.142364] ---[ end trace 7618865ee801c0ae ]---
May 17 09:59:05 T1500 kernel: [  150.162835] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id

---

### Post by skyde77 on 2011-05-18
Problem occurs both on netware and linux (SUSE10-OES2) fileservers.

---

### Post by cwitte on 2011-07-14
I'm getting the same problem, I guess it is related to [https://bugs.launchpad.net/ubuntu/+source/ncpfs/+bug/773211](https://bugs.launchpad.net/ubuntu/+source/ncpfs/+bug/773211)

Chris.

---

