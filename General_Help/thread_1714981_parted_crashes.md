---
title: "parted crashes"
date: 2011-03-26
forum: General Help
---

### Post by jcoles on 2011-03-26
There is a problem with parted. Ubuntu 10.10 64-bit kernel 2.6.35 parted 2.3. 
Note the line about parted being tainted. Remove and reinstall with apt-get made no difference. Is there anything I can do? Or, will this be fixed by some future update?

[SIZE="1"]# parted -l 

[ 2667.880157] BUG: unable to handle kernel NULL pointer dereference at (null)
[ 2667.880169] IP: [<(null)>] (null)
[ 2667.880178] PGD 2c13e067 PUD 2c157067 PMD 0 
[ 2667.880188] Oops: 0010 [#10] SMP 
[ 2667.880194] last sysfs file: /sys/devices/virtual/block/scramdisk!master/queue/physical_block_size
[ 2667.880202] CPU 1 
[ 2667.880205] Modules linked in: usb_storage binfmt_misc parport_pc ppdev scramdisk vboxnetadp vboxnetflt vboxdrv snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi radeon snd_seq_midi_event snd_seq ttm drm_kms_helper snd_timer snd_seq_device drm i2c_algo_bit hp_wmi psmouse snd edac_core serio_raw edac_mce_amd soundcore lp i2c_piix4 snd_page_alloc k8temp parport shpchp usbhid hid ahci pata_atiixp tg3 libahci
[ 2667.880275] 
[ 2667.880283] Pid: 2821, comm: parted Tainted: G      D     2.6.35-28-generic #49-Ubuntu 0A64h/HP Compaq dc5750 Small Form Factor
[ 2667.880290] RIP: 0010:[<0000000000000000>]  [<(null)>] (null)
[ 2667.880298] RSP: 0018:ffff88002c131d40  EFLAGS: 00010246
[ 2667.880303] RAX: ffff880069d716c0 RBX: ffff880039e68480 RCX: 0000000000000008
[ 2667.880308] RDX: 0000000000000021 RSI: ffff880039e68480 RDI: ffff880072b06408
[ 2667.880314] RBP: ffff88002c131e18 R08: ffff88002c0f0cf0 R09: 00007f9d98748514
[ 2667.880319] R10: 0000000000000000 R11: 0000000000000246 R12: ffff880072b06408
[ 2667.880324] R13: 0000000000000000 R14: 0000000000000000 R15: 0000000007d00000
[ 2667.880331] FS:  00007f9d98b5e7e0(0000) GS:ffff880001f00000(0000) knlGS:0000000000000000
[ 2667.880337] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[ 2667.880342] CR2: 0000000000000000 CR3: 000000002c15d000 CR4: 00000000000006e0
[ 2667.880348] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 2667.880353] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 2667.880360] Process parted (pid: 2821, threadinfo ffff88002c130000, task ffff88002c1944a0)
[ 2667.880364] Stack:
[ 2667.880368]  ffffffff812a3a23 00000000000112d0 ffff88002c131da8 ffff88002c131dc0
[ 2667.880377] <0> ffff8800756683f0 ffff88002c131d78 ffffffff81103f15 ffff88002c1944a0
[ 2667.880386] <0> 0000000000000000 0000000000000000 0000000000000000 ffff88002c1944a0
[ 2667.880397] Call Trace:
[ 2667.880412]  [<ffffffff812a3a23>] ? generic_make_request+0x1b3/0x530
[ 2667.880423]  [<ffffffff81103f15>] ? mempool_alloc_slab+0x15/0x20
[ 2667.880432]  [<ffffffff812a3e22>] submit_bio+0x82/0x110
[ 2667.880442]  [<ffffffff812a7a51>] blkdev_issue_flush+0xb1/0x100
[ 2667.880453]  [<ffffffff811846f9>] blkdev_fsync+0x49/0x70
[ 2667.880461]  [<ffffffff8117ae5c>] vfs_fsync_range+0x7c/0xa0
[ 2667.880468]  [<ffffffff8117aeec>] vfs_fsync+0x1c/0x20
[ 2667.880475]  [<ffffffff8117af2a>] do_fsync+0x3a/0x60
[ 2667.880482]  [<ffffffff8117af80>] sys_fsync+0x10/0x20
[ 2667.880493]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
[ 2667.880497] Code:  Bad RIP value.
[ 2667.880507] RIP  [<(null)>] (null)
[ 2667.880513]  RSP <ffff88002c131d40>
[ 2667.880517] CR2: 0000000000000000
[ 2667.880523] ---[ end trace 42879a15bff590ed ]---
[/SIZE]

---

### Post by TeoBigusGeekus on 2011-03-26
Does this happen with fdisk as well?

---

### Post by jcoles on 2011-04-15
No problem with fdisk.

---

### Post by srs5694 on 2011-04-15
Parted is much more sensitive than fdisk to partition table errors. Usually it just refuses to work with a disk or shows a disk as empty when it's not, but sometimes it'll crash. My suspicion is that there's a minor problem with the partition table that's causing parted to misbehave. I recommend you run the following command:

```

sudo fdisk -lu

```

Post the results here between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. That'll let us see most of what's in your partition table that might cause parted to flake out.

---

### Post by psusi on 2011-04-15
That isn't parted; that is the kernel.  Can you boot with the previous kernel and see if it happens there?

---

