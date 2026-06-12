---
title: "general protection fault - forced log off"
date: 2011-03-24
forum: General Help
---

### Post by skthetwo on 2011-03-24
Using a Quad core AMD, 64 bit Ubuntu 10.04 - Sometimes I get this situation where the CRT ( really old IBM monitor) sort of clicks off ( like when its lost connectivity ) then clicks on ( as its gained it back ) but now I'm at the logon screen - but everything I was doing while previously logged on has gone ( they aren't any hanging processes, the way one might if I'd remote logged into using NX say and then disconnected for whatever reason).

It doesn't happen to other configurations of PCs, monitors - all 64 bit Ubuntu. the other thing to mention is that generally I'm using the machine heavily for computation and just browsing the net waiting for things for finish

The entries is syslog at the time of problem is:


general protection fault: 0000 [#1] SMP 
Mar 24 20:0501 thermaltake kernel: [ 6065.155816] last sysfs file: /sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0/local_cpus
Mar 24 20:05:01 thermaltake kernel: [ 6065.155821] CPU 1 
Mar 24 20:05:01 thermaltake kernel: [ 6065.155826] Modules linked in: nls_utf8 udf crc_itu_t binfmt_misc snd_hda_codec_atihdmi fbcon tileblit font bitblit softcursor vga16fb vgastate ppdev snd_hda_codec_realtek snd_seq_dummy snd_hda_intel snd_hda_codec snd_hwdep snd_seq_oss snd_pcm_oss snd_mixer_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_pcm radeon snd_seq ttm drm_kms_helper snd_timer snd_seq_device drm snd i2c_algo_bit psmouse serio_raw edac_core edac_mce_amd soundcore snd_page_alloc i2c_piix4 shpchp lp parport r8169 mii pata_atiixp ahci
Mar 24 20:05:01 thermaltake kernel: [ 6065.155897] Pid: 1239, comm: Xorg Not tainted 2.6.32-29-generic #58-Ubuntu TA790GXB3
Mar 24 20:05:01 thermaltake kernel: [ 6065.155902] RIP: 0010:[<ffffffff81038729>]  [<ffffffff81038729>] __ticket_spin_lock+0x9/0x20
Mar 24 20:05:01 thermaltake kernel: [ 6065.155919] RSP: 0018:ffff880201631ca8  EFLAGS: 00010286
Mar 24 20:05:01 thermaltake kernel: [ 6065.155924] RAX: 0000000000000100 RBX: 0000000000000000 RCX: 0000000000000000
Mar 24 20:05:01 thermaltake kernel: [ 6065.155930] RDX: 0000000000000001 RSI: 0000000000000001 RDI: fff788021439b748
Mar 24 20:05:01 thermaltake kernel: [ 6065.155934] RBP: ffff880201631ca8 R08: 0000000000000000 R09: ffffffffa0186950
Mar 24 20:05:01 thermaltake kernel: [ 6065.155939] R10: 0000000000000000 R11: 0000000000000001 R12: ffff8801f7570878
Mar 24 20:05:01 thermaltake kernel: [ 6065.155944] R13: 0000000000000001 R14: 0000000000000001 R15: fff788021439b748
Mar 24 20:05:01 thermaltake kernel: [ 6065.155950] FS:  00007fd59f6a0700(0000) GS:ffff880028280000(0000) knlGS:00000000f75428d0
Mar 24 20:05:01 thermaltake kernel: [ 6065.155955] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 24 20:05:01 thermaltake kernel: [ 6065.155960] CR2: 00007fd599ade7a8 CR3: 00000002076c9000 CR4: 00000000000006e0
Mar 24 20:05:01 thermaltake kernel: [ 6065.155965] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Mar 24 20:05:01 thermaltake kernel: [ 6065.155970] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Mar 24 20:05:01 thermaltake kernel: [ 6065.155976] Process Xorg (pid: 1239, threadinfo ffff880201630000, task ffff880203775bc0)
Mar 24 20:05:01 thermaltake kernel: [ 6065.155980] Stack:
Mar 24 20:05:01 thermaltake kernel: [ 6065.155983]  ffff880201631cb8 ffffffff81544f7e ffff880201631d08 ffffffffa0118ae7
Mar 24 20:05:01 thermaltake kernel: [ 6065.155991] <0> ffff880201631cd8 00ff880207570e98 ffff880201631d08 00000000ffffffea
Mar 24 20:05:01 thermaltake kernel: [ 6065.155999] <0> ffff8801f7570800 ffff8801fa457900 ffff880201631dd8 ffff8801f7570878
Mar 24 20:05:01 thermaltake kernel: [ 6065.156008] Call Trace:
Mar 24 20:05:01 thermaltake kernel: [ 6065.156018]  [<ffffffff81544f7e>] _spin_lock+0xe/0x20
Mar 24 20:05:01 thermaltake kernel: [ 6065.156034]  [<ffffffffa0118ae7>] ttm_bo_reserve+0x37/0x120 [ttm]
Mar 24 20:05:01 thermaltake kernel: [ 6065.156074]  [<ffffffffa01869b7>] radeon_gem_busy_ioctl+0x67/0x180 [radeon]
Mar 24 20:05:01 thermaltake kernel: [ 6065.156099]  [<ffffffffa00c3ef8>] drm_ioctl+0x318/0x4c0 [drm]
Mar 24 20:05:01 thermaltake kernel: [ 6065.156134]  [<ffffffffa0186950>] ? radeon_gem_busy_ioctl+0x0/0x180 [radeon]
Mar 24 20:05:01 thermaltake kernel: [ 6065.156145]  [<ffffffff81118581>] ? __remove_shared_vm_struct+0x41/0x60
Mar 24 20:05:01 thermaltake kernel: [ 6065.156153]  [<ffffffff811232a1>] ? free_pages_and_swap_cache+0x21/0xe0
Mar 24 20:05:01 thermaltake kernel: [ 6065.156162]  [<ffffffff812b3adb>] ? cpumask_any_but+0x2b/0x40
Mar 24 20:05:01 thermaltake kernel: [ 6065.156170]  [<ffffffff81153bd2>] vfs_ioctl+0x22/0xa0
Mar 24 20:05:01 thermaltake kernel: [ 6065.156177]  [<ffffffff81153e81>] do_vfs_ioctl+0x81/0x380
Mar 24 20:05:01 thermaltake kernel: [ 6065.156185]  [<ffffffff8111a288>] ? do_munmap+0x2d8/0x380
Mar 24 20:05:01 thermaltake kernel: [ 6065.156192]  [<ffffffff81154201>] sys_ioctl+0x81/0xa0
Mar 24 20:05:01 thermaltake kernel: [ 6065.156200]  [<ffffffff8154576e>] ? do_device_not_available+0xe/0x10
Mar 24 20:05:01 thermaltake kernel: [ 6065.156209]  [<ffffffff810121b2>] system_call_fastpath+0x16/0x1b
Mar 24 20:05:01 thermaltake kernel: [ 6065.156213] Code: 00 00 48 c7 c2 2e 85 03 81 48 c7 c1 31 85 03 81 e9 dd fe ff ff 90 90 90 90 90 90 90 90 90 90 90 90 90 55 b8 00 01 00 00 48 89 e5 <f0> 66 0f c1 07 38 e0 74 06 f3 90 8a 07 eb f6 c9 c3 66 0f 1f 44 
Mar 24 20:05:01 thermaltake kernel: [ 6065.156271] RIP  [<ffffffff81038729>] __ticket_spin_lock+0x9/0x20
Mar 24 20:05:01 thermaltake kernel: [ 6065.156280]  RSP <ffff880201631ca8>
Mar 24 20:05:01 thermaltake kernel: [ 6065.156286] ---[ end trace e055f657001b3a24 ]---
Mar 24 20:05:02 thermaltake kernel: [ 6065.874190] [drm:drm_release] *ERROR* Device busy: 1
Mar 24 20:05:02 thermaltake gdm-simple-slave[5336]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar 24 20:05:02 thermaltake acpid: client 1239[0:0] has disconnected
Mar 24 20:05:02 thermaltake acpid: client connected from 5338[0:0]

---

### Post by skthetwo on 2011-03-26
Please follow this at

[http://ubuntuforums.org/showthread.php?t=1714509](http://ubuntuforums.org/showthread.php?t=1714509)

---

