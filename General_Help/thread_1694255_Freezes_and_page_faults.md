---
title: "Freezes and page faults"
date: 2011-02-24
forum: General Help
---

### Post by waperboy on 2011-02-24
Yesterday my box suddenly just froze 4-5 times during the day, forcing me to do a hard reboot. One of the times there was a protection fault in syslog, the other times there was nothing:

```
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684685] general protection fault: 0000 [#1] SMP 
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684689] last sysfs file: /sys/devices/virtual/net/vboxnet0/statistics/collisions
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684691] CPU 0 
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684693] Modules linked in: nvidia(P) binfmt_misc vboxnetadp vboxnetflt vboxdrv ppdev parport_pc vmblock vmmon cx8800 cx88xx bttv ir_common videobuf_dma_sg videobuf_core btcx_risc lirc_i2c lirc_dev ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT xt_tcpudp iptable_filter ip_tables x_tables bridge stp kvm_intel kvm tuner_simple tuner_types tuner msp3400 snd_hda_codec_realtek saa7115 snd_usb_audio snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_usb_lib snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq coretemp ivtv i2c_algo_bit snd_timer cx2341x v4l2_common snd_seq_device snd_hwdep videodev snd v4l1_compat soundcore v4l2_compat_ioctl32 tveeprom snd_page_alloc asus_atk0110 hwmon_vid lp parport usbhid hid ahci r8169 mii
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684737] Pid: 2842, comm: chrome Tainted: P    B      2.6.32-24-generic #43-Ubuntu System Product Name
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684739] RIP: 0010:[<ffffffff810f4a14>]  [<ffffffff810f4a14>] sync_page+0x24/0x50
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684746] RSP: 0018:ffff8802e5411ca8  EFLAGS: 00010282
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684748] RAX: ffac88032de19cc8 RBX: ffff8802e5411d08 RCX: ffff88002802efb0
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684750] RDX: 020000000002006c RSI: 0000000000000282 RDI: ffffea000b119c50
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684752] RBP: ffff8802e5411ca8 R08: 0000000000000000 R09: e280000000000000
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684754] R10: 0000000000000001 R11: 0000000000000001 R12: ffff88002802efa8
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684757] R13: ffff8802e5411d18 R14: 0000000000000002 R15: ffffffff810f49f0
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684759] FS:  00007f7f9e35a7e0(0000) GS:ffff880028200000(0000) knlGS:0000000000000000
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684762] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684764] CR2: 00007fb3e5e7e000 CR3: 00000002e54e5000 CR4: 00000000000026f0
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684766] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684769] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684771] Process chrome (pid: 2842, threadinfo ffff8802e5410000, task ffff8802e57e0000)
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684772] Stack:
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684774]  ffff8802e5411cf8 ffffffff8154276a 0000000000000282 ffff8802e5411cd8
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684777] <0> 0000000000000282 ffff8802e5411d08 0000000000000003 ffffea000b119c50
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684780] <0> ffff88032de19cc8 0000000000000003 ffff8802e5411d58 ffffffff810f49c7
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684784] Call Trace:
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684790]  [<ffffffff8154276a>] __wait_on_bit_lock+0x5a/0xc0
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684793]  [<ffffffff810f49c7>] __lock_page+0x67/0x70
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684797]  [<ffffffff81085490>] ? wake_bit_function+0x0/0x40
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684800]  [<ffffffff810f47fe>] ? find_get_page+0x1e/0xa0
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684804]  [<ffffffff810f6053>] find_lock_page+0x63/0x80
Feb 23 19:52:45 per-big-desktop kernel: [ 6263.684807]  [<ffffffff810f62b2>] filemap_fault+0x182/Feb 23 19:54:54 per-big-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.

```

I also see loads of bad page page status crashes in syslog now, also during boot, and during desktop usage:

```
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057623] BUG: Bad page state in process updatedb.mlocat  pfn:2b79a6
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057628] page:ffffea0009829c50 flags:0200000000000000 count:0 mapcount:-13697024 
mapping:00ac000000000000 index:0
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057631] Pid: 15959, comm: updatedb.mlocat Tainted: P    B   W  2.6.32-24-generic
 #43-Ubuntu
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057632] Call Trace:
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057639]  [<ffffffff810f9185>] bad_page+0xf5/0x150
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057642]  [<ffffffff810fa012>] prep_new_page+0x1b2/0x1c0
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057645]  [<ffffffff81202a74>] ? ext4_ext_get_blocks+0x234/0x790
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057648]  [<ffffffff810fa2c4>] get_page_from_freelist+0x2a4/0x6d0
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057650]  [<ffffffff811ffe19>] ? ext4_ext_find_extent+0x2c9/0x300
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057653]  [<ffffffff810fae70>] __alloc_pages_nodemask+0xe0/0x1a0
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057656]  [<ffffffff8112dcd7>] alloc_pages_current+0x87/0xd0
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057659]  [<ffffffff81133b78>] new_slab+0x248/0x310
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057661]  [<ffffffff81136439>] __slab_alloc+0x169/0x2d0
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057663]  [<ffffffff811f6010>] ? ext4_alloc_inode+0x20/0x120
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057665]  [<ffffffff81136964>] kmem_cache_alloc+0xe4/0x150
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057667]  [<ffffffff811f6010>] ext4_alloc_inode+0x20/0x120
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057670]  [<ffffffff8115b547>] alloc_inode+0x27/0xa0
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057672]  [<ffffffff8115c6ff>] get_new_inode_fast+0x2f/0x170
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057674]  [<ffffffff8115c8a6>] iget_locked+0x66/0x70
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057677]  [<ffffffff811e2ef7>] ext4_iget+0x37/0x810
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057681]  [<ffffffff8154426e>] ? _spin_lock+0xe/0x20
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057683]  [<ffffffff81156d40>] ? d_rehash+0x50/0x60
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057686]  [<ffffffff811e6315>] ext4_lookup+0xa5/0x130
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057688]  [<ffffffff8114d9d2>] real_lookup+0xe2/0x160
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057690]  [<ffffffff8114f978>] do_lookup+0xb8/0xf0
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057692]  [<ffffffff8115908f>] ? dput+0xdf/0x1b0
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057694]  [<ffffffff811504a5>] __link_path_walk+0x765/0xf80
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057697]  [<ffffffff81150f3a>] path_walk+0x6a/0xe0
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057699]  [<ffffffff8115110b>] do_path_lookup+0x5b/0xa0
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057701]  [<ffffffff81151dd7>] user_path_at+0x57/0xa0
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057703]  [<ffffffff8154426e>] ? _spin_lock+0xe/0x20
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057706]  [<ffffffff812b3e35>] ? _atomic_dec_and_lock+0x55/0x80
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057710]  [<ffffffff81148304>] ? cp_new_stat+0xe4/0x100
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057712]  [<ffffffff8114852c>] vfs_fstatat+0x3c/0x80
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057714]  [<ffffffff811485de>] vfs_lstat+0x1e/0x20
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057716]  [<ffffffff81148604>] sys_newlstat+0x24/0x50
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057720]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b

Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709304] BUG: Bad page state in process sh  pfn:2b5e38
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709310] page:ffffea00097c9c40 flags:0200000000000000 count:0 mapcount:-11534336 mapping:002e000000000000 index:0
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709315] Pid: 18881, comm: sh Tainted: P    B   W  2.6.32-24-generic #43-Ubuntu
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709317] Call Trace:
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709327]  [<ffffffff810f9185>] bad_page+0xf5/0x150
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709332]  [<ffffffff8111299a>] ? copy_pte_range+0x2ba/0x450
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709336]  [<ffffffff810fa012>] prep_new_page+0x1b2/0x1c0
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709340]  [<ffffffff810fa2c4>] get_page_from_freelist+0x2a4/0x6d0
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709346]  [<ffffffff8154426e>] ? _spin_lock+0xe/0x20
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709350]  [<ffffffff810fae70>] __alloc_pages_nodemask+0xe0/0x1a0
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709356]  [<ffffffff8112dd92>] alloc_page_vma+0x72/0xf0
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709360]  [<ffffffff81115454>] do_wp_page+0x194/0x860
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709364]  [<ffffffff8105eb15>] ? task_new_fair+0xb5/0x100
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709369]  [<ffffffff8105a4f7>] ? wake_up_new_task+0xb7/0x110
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709373]  [<ffffffff8111624c>] handle_mm_fault+0x2ec/0x3c0
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709377]  [<ffffffff81546dea>] do_page_fault+0x12a/0x3b0
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709381]  [<ffffffff81544735>] page_fault+0x25/0x30

Feb 24 08:49:14 per-big-desktop kernel: [ 3204.367522] BUG: Bad page state in process chrome  pfn:2b5082
Feb 24 08:49:14 per-big-desktop kernel: [ 3204.367529] page:ffffea0009799c70 flags:0200000000000000 count:0 mapcount:-3407872 mapping:(null) index:0
Feb 24 08:49:14 per-big-desktop kernel: [ 3204.367534] Pid: 22854, comm: chrome Tainted: P    B   W  2.6.32-24-generic #43-Ubuntu
Feb 24 08:49:14 per-big-desktop kernel: [ 3204.367536] Call Trace:
Feb 24 08:49:14 per-big-desktop kernel: [ 3204.367546]  [<ffffffff810f9185>] bad_page+0xf5/0x150
Feb 24 08:49:14 per-big-desktop kernel: [ 3204.367550]  [<ffffffff810fa012>] prep_new_page+0x1b2/0x1c0
Feb 24 08:49:14 per-big-desktop kernel: [ 3204.367554]  [<ffffffff810fa2c4>] get_page_from_freelist+0x2a4/0x6d0
Feb 24 08:49:14 per-big-desktop kernel: [ 3204.367559]  [<ffffffff810fae70>] __alloc_pages_nodemask+0xe0/0x1a0
Feb 24 08:49:14 per-big-desktop kernel: [ 3204.367565]  [<ffffffff8112dd92>] alloc_page_vma+0x72/0xf0
Feb 24 08:49:14 per-big-desktop kernel: [ 3204.367568]  [<ffffffff810ff7b1>] ? lru_cache_add_lru+0x21/0x40
Feb 24 08:49:14 per-big-desktop kernel: [ 3204.367573]  [<ffffffff811116a8>] do_anonymous_page+0x158/0x310
Feb 24 08:49:14 per-big-desktop kernel: [ 3204.367577]  [<ffffffff8111627f>] handle_mm_fault+0x31f/0x3c0
Feb 24 08:49:14 per-big-desktop kernel: [ 3204.367581]  [<ffffffff8111b4d5>] ? do_mmap_pgoff+0x335/0x380
Feb 24 08:49:14 per-big-desktop kernel: [ 3204.367586]  [<ffffffff81546dea>] do_page_fault+0x12a/0x3b0
Feb 24 08:49:14 per-big-desktop kernel: [ 3204.367591]  [<ffffffff81544735>] page_fault+0x25/0x30
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699049] BUG: Bad page state in process sh  pfn:2b42ca
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699054] page:ffffea0009769c30 flags:0200000000000000 count:0 mapcount:0 mapping:004f000000000000 index:0
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699059] Pid: 23248, comm: sh Tainted: P    B   W  2.6.32-24-generic #43-Ubuntu
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699062] Call Trace:
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699071]  [<ffffffff810f9185>] bad_page+0xf5/0x150
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699076]  [<ffffffff8111299a>] ? copy_pte_range+0x2ba/0x450
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699081]  [<ffffffff810fa012>] prep_new_page+0x1b2/0x1c0
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699085]  [<ffffffff810fa2c4>] get_page_from_freelist+0x2a4/0x6d0
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699091]  [<ffffffff8154426e>] ? _spin_lock+0xe/0x20
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699098]  [<ffffffff810fae70>] __alloc_pages_nodemask+0xe0/0x1a0
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699104]  [<ffffffff8112dd92>] alloc_page_vma+0x72/0xf0
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699109]  [<ffffffff81115454>] do_wp_page+0x194/0x860
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699116]  [<ffffffff8105a4f7>] ? wake_up_new_task+0xb7/0x110
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699122]  [<ffffffff8111624c>] handle_mm_fault+0x2ec/0x3c0
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699127]  [<ffffffff81546dea>] do_page_fault+0x12a/0x3b0
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699133]  [<ffffffff81544735>] page_fault+0x25/0x30

```

This goes on and on, although I wouldn't have noticed anything if I didn't check the syslog.
Seems to coincide with cron runs, but it doesn't always happen.

I've had to live with the occasional freeze (once every other week or so, mostly when straining the GPU), but this is getting  crazy all of a sudden.

What could cause of all this? Hardware failure?

---

### Post by zenwalker on 2011-02-24
I guess some thing is wrong with the hardware especially RAM

---

### Post by waperboy on 2011-02-24
I'll have to sacrifice some time to run the gruelling memtest - takes a while with 12 gigs...


One thing is that my 8-pin EPS12V cable is really *very* taught, since it just barely reaches from the PSU (bottom of case) to the motherboard socket (top of case). I had to really pull on it to manage to make it click into the socket with some effort, and it is taught against the video card and CPU cooling fins.

I should get an extension cable...

---

### Post by dino99 on 2011-02-24
check that is not a psu issue (in case psu cant deliver enought power)
[http://support.asus.com/PowerSupplyCalculator/PowerSupplyCalculator_right.aspx](http://support.asus.com/PowerSupplyCalculator/PowerSupplyCalculator_right.aspx)

are you using some untrusted third parties repo ?

---

### Post by waperboy on 2011-02-24
PSU should be ok, 650W, one video card, but I'll check it with a watt-meter.

Hmm this started happening the day after I added this to /etc/sysctl.conf, which I did 4 days ago:

```

fs.inotify.max_user_watches = 524288
vm.swappiness = 10

```

(for audio-related apps)

Grepping kern.log for pfn: does give a fairly close range of pages, always descending, starting 3 days ago:

```

Feb 21 09:22:16 per-big-desktop kernel: [ 9194.821280] BUG: Bad page state in process chrome  pfn:2f5514
Feb 21 09:25:55 per-big-desktop kernel: [   13.611069] BUG: Bad page state in process ureadahead  pfn:32d082
Feb 21 09:25:55 per-big-desktop kernel: [   13.614703] BUG: Bad page state in process ureadahead  pfn:32c2ca
Feb 21 09:25:55 per-big-desktop kernel: [   13.620883] BUG: Bad page state in process ureadahead  pfn:32b514
Feb 21 09:25:55 per-big-desktop kernel: [   13.624989] BUG: Bad page state in process ureadahead  pfn:3299a6
Feb 21 09:25:55 per-big-desktop kernel: [   13.629097] BUG: Bad page state in process ureadahead  pfn:327e38
Feb 21 09:25:55 per-big-desktop kernel: [   14.336321] BUG: Bad page state in process find  pfn:327082
Feb 21 09:25:55 per-big-desktop kernel: [   14.381387] BUG: Bad page state in process swapon  pfn:3262ca
Feb 21 09:25:55 per-big-desktop kernel: [   14.400459] BUG: Bad page state in process udevd  pfn:325514
Feb 21 09:25:55 per-big-desktop kernel: [   14.492264] BUG: Bad page state in process udisks-part-id  pfn:3239a6
Feb 21 09:25:55 per-big-desktop kernel: [   14.845783] BUG: Bad page state in process modprobe  pfn:321e38
Feb 21 09:25:55 per-big-desktop kernel: [   14.879971] BUG: Bad page state in process fsck.ext4  pfn:321082
Feb 21 09:25:55 per-big-desktop kernel: [   14.998765] BUG: Bad page state in process fsck.ext4  pfn:3202ca
Feb 21 09:26:57 per-big-desktop kernel: [   82.942474] BUG: Bad page state in process chrome  pfn:2f62ca
Feb 21 09:26:57 per-big-desktop kernel: [   83.046036] BUG: Bad page state in process chrome  pfn:2f5514
Feb 21 09:26:58 per-big-desktop kernel: [   83.345257] BUG: Bad page state in process chrome  pfn:2f39a6
Feb 21 09:26:58 per-big-desktop kernel: [   83.657206] BUG: Bad page state in process chrome  pfn:2f1e38
Feb 21 09:26:58 per-big-desktop kernel: [   83.732906] BUG: Bad page state in process chrome  pfn:2f1082
Feb 21 09:27:05 per-big-desktop kernel: [   90.236015] BUG: Bad page state in process chrome  pfn:2f02ca
Feb 21 09:27:05 per-big-desktop kernel: [   90.909144] BUG: Bad page state in process chrome  pfn:2ef514
Feb 21 09:27:27 per-big-desktop kernel: [  112.314744] BUG: Bad page state in process chrome  pfn:2ed9a6
Feb 21 09:27:27 per-big-desktop kernel: [  112.830605] BUG: Bad page state in process npviewer.bin  pfn:2ebe38
Feb 21 09:27:28 per-big-desktop kernel: [  113.175364] BUG: Bad page state in process npviewer.bin  pfn:2eb082
Feb 21 09:27:28 per-big-desktop kernel: [  113.572025] BUG: Bad page state in process npviewer.bin  pfn:2ea2ca
Feb 21 09:27:28 per-big-desktop kernel: [  113.723977] BUG: Bad page state in process chrome  pfn:2e9514
Feb 21 09:45:19 per-big-desktop kernel: [ 1181.650035] BUG: Bad page state in process jackd  pfn:2bf514
Feb 21 09:45:21 per-big-desktop kernel: [ 1183.907505] BUG: Bad page state in process pulseaudio  pfn:2bd9a6
Feb 21 09:45:21 per-big-desktop kernel: [ 1183.967409] BUG: Bad page state in process rakarrack  pfn:2bbe38
Feb 21 09:45:21 per-big-desktop kernel: [ 1183.971175] BUG: Bad page state in process rakarrack  pfn:2bb082
Feb 21 09:45:21 per-big-desktop kernel: [ 1183.977858] BUG: Bad page state in process rakarrack  pfn:2ba2ca
Feb 21 09:45:21 per-big-desktop kernel: [ 1183.981680] BUG: Bad page state in process rakarrack  pfn:2b9514
Feb 21 10:33:44 per-big-desktop kernel: [ 4079.521156] BUG: Bad page state in process npviewer.bin  pfn:2b79a6
Feb 21 10:36:05 per-big-desktop kernel: [ 4220.829060] BUG: Bad page state in process chrome  pfn:2b5e38
Feb 21 10:38:10 per-big-desktop kernel: [ 4345.317550] BUG: Bad page state in process chrome  pfn:2b5082
Feb 21 10:39:25 per-big-desktop kernel: [ 4419.702698] BUG: Bad page state in process npviewer.bin  pfn:2b42ca
Feb 21 10:40:07 per-big-desktop kernel: [ 4462.005192] BUG: Bad page state in process npviewer.bin  pfn:2b3514
Feb 21 16:07:13 per-big-desktop kernel: [24039.857326] BUG: Bad page state in process chrome  pfn:2879a6
Feb 21 16:07:14 per-big-desktop kernel: [24041.321040] BUG: Bad page state in process chrome  pfn:285e38
Feb 21 16:07:15 per-big-desktop kernel: [24041.846900] BUG: Bad page state in process chrome  pfn:285082
Feb 21 16:07:16 per-big-desktop kernel: [24042.793924] BUG: Bad page state in process chrome  pfn:2842ca
Feb 21 16:07:16 per-big-desktop kernel: [24043.311629] BUG: Bad page state in process chrome  pfn:283514
Feb 21 16:07:18 per-big-desktop kernel: [24044.795565] BUG: Bad page state in process chrome  pfn:2819a6
Feb 21 16:07:19 per-big-desktop kernel: [24046.294733] BUG: Bad page state in process chrome  pfn:27fe38
Feb 21 16:07:20 per-big-desktop kernel: [24046.838875] BUG: Bad page state in process chrome  pfn:27f082
Feb 21 16:07:21 per-big-desktop kernel: [24047.772748] BUG: Bad page state in process chrome  pfn:27e2ca
Feb 21 16:07:21 per-big-desktop kernel: [24048.294696] BUG: Bad page state in process chrome  pfn:27d514
Feb 21 16:07:23 per-big-desktop kernel: [24049.768118] BUG: Bad page state in process chrome  pfn:27b9a6
Feb 23 19:18:08 per-big-desktop kernel: [ 4191.185795] BUG: Bad page state in process vlc  pfn:2f1082
Feb 23 19:24:00 per-big-desktop kernel: [ 4542.373877] BUG: Bad page state in process docky  pfn:2f5514
Feb 23 22:18:04 per-big-desktop kernel: [   12.911175] BUG: Bad page state in process init  pfn:32d082
Feb 23 22:18:04 per-big-desktop kernel: [   13.009447] BUG: Bad page state in process ureadahead  pfn:32c2ca
Feb 23 22:18:04 per-big-desktop kernel: [   13.043347] BUG: Bad page state in process ureadahead  pfn:32b514
Feb 23 22:18:04 per-big-desktop kernel: [   13.187754] BUG: Bad page state in process udevd  pfn:3299a6
Feb 23 22:18:04 per-big-desktop kernel: [   13.406430] BUG: Bad page state in process fsck.ext4  pfn:327082
Feb 23 22:18:04 per-big-desktop kernel: [   13.408073] BUG: Bad page state in process alsactl  pfn:327e38
Feb 23 22:18:04 per-big-desktop kernel: [   13.419625] BUG: Bad page state in process ureadahead  pfn:3262ca
Feb 23 22:18:04 per-big-desktop kernel: [   13.427336] BUG: Bad page state in process fsck.ext4  pfn:325514
Feb 23 22:18:04 per-big-desktop kernel: [   13.467684] BUG: Bad page state in process modprobe  pfn:3239a6
Feb 23 22:18:04 per-big-desktop kernel: [   13.626105] BUG: Bad page state in process ureadahead  pfn:321e38
Feb 23 22:18:04 per-big-desktop kernel: [   13.751330] BUG: Bad page state in process ureadahead  pfn:321082
Feb 23 22:18:04 per-big-desktop kernel: [   13.782861] BUG: Bad page state in process fsck.ext4  pfn:3202ca
Feb 23 22:19:13 per-big-desktop kernel: [   85.234405] BUG: Bad page state in process bash  pfn:2f62ca
Feb 23 22:19:38 per-big-desktop kernel: [  109.784057] BUG: Bad page state in process ubuntuone-launc  pfn:2f5514
Feb 23 22:19:38 per-big-desktop kernel: [  110.259683] BUG: Bad page state in process ubuntuone-syncd  pfn:2f39a6
Feb 23 22:24:35 per-big-desktop kernel: [  406.302924] BUG: Bad page state in process vlc  pfn:2f1e38
Feb 23 22:24:36 per-big-desktop kernel: [  407.155528] BUG: Bad page state in process vlc  pfn:2f1082
Feb 23 22:24:37 per-big-desktop kernel: [  408.198322] BUG: Bad page state in process vlc  pfn:2f02ca
Feb 23 22:24:38 per-big-desktop kernel: [  409.426168] BUG: Bad page state in process vlc  pfn:2ef514
Feb 23 23:46:15 per-big-desktop kernel: [ 5293.633460] BUG: Bad page state in process firefox-bin  pfn:2ed9a6
Feb 23 23:46:15 per-big-desktop kernel: [ 5294.236463] BUG: Bad page state in process firefox-bin  pfn:2ebe38
Feb 23 23:46:15 per-big-desktop kernel: [ 5294.354146] BUG: Bad page state in process firefox-bin  pfn:2eb082
Feb 23 23:46:16 per-big-desktop kernel: [ 5295.020900] BUG: Bad page state in process firefox-bin  pfn:2ea2ca
Feb 23 23:46:16 per-big-desktop kernel: [ 5295.372109] BUG: Bad page state in process firefox-bin  pfn:2e9514
Feb 24 08:27:21 per-big-desktop kernel: [ 1894.885869] BUG: Bad page state in process updatedb.mlocat  pfn:2bf514
Feb 24 08:27:22 per-big-desktop kernel: [ 1895.779149] BUG: Bad page state in process updatedb.mlocat  pfn:2bd9a6
Feb 24 08:27:23 per-big-desktop kernel: [ 1896.644089] BUG: Bad page state in process updatedb.mlocat  pfn:2bbe38
Feb 24 08:27:23 per-big-desktop kernel: [ 1897.246278] BUG: Bad page state in process updatedb.mlocat  pfn:2bb082
Feb 24 08:27:24 per-big-desktop kernel: [ 1897.821104] BUG: Bad page state in process updatedb.mlocat  pfn:2ba2ca
Feb 24 08:27:24 per-big-desktop kernel: [ 1897.937772] BUG: Bad page state in process updatedb.mlocat  pfn:2b9514
Feb 24 08:27:24 per-big-desktop kernel: [ 1898.057623] BUG: Bad page state in process updatedb.mlocat  pfn:2b79a6
Feb 24 08:36:39 per-big-desktop kernel: [ 2451.709304] BUG: Bad page state in process sh  pfn:2b5e38
Feb 24 08:49:14 per-big-desktop kernel: [ 3204.367522] BUG: Bad page state in process chrome  pfn:2b5082
Feb 24 08:50:27 per-big-desktop kernel: [ 3277.699049] BUG: Bad page state in process sh  pfn:2b42ca
Feb 24 08:51:26 per-big-desktop kernel: [ 3336.127059] BUG: Bad page state in process chrome  pfn:2b3514

```

---

### Post by clhsharky on 2011-02-24
waperboy


Are you over clocking your system?



Sharky

---

### Post by waperboy on 2011-02-24
> **clhsharky said:**
> waperboy


Are you over clocking your system?



Sharky

No, no overclocking. Everything is on 'auto' in bios, though - could be an idea to check voltages and such.

It feels like there's a memory issue, which would really suck - bought the sticks just 4 months ago.

But, I really haven't powered down the system for a week or so, just suspend/resume, and then reset-button after freezes. Maybe a power cycle could work...

---

### Post by clhsharky on 2011-02-24
waperboy


Might kick up memory voltage a small amount to test. That a lot of ram.


Sharky

---

### Post by waperboy on 2011-02-24
> **clhsharky said:**
> waperboy


Might kick up memory voltage a small amount to test. That a lot of ram.


Sharky

Adding to todo list :)

12 gigs is enough to have e few dirs mapped to tmpfs, /tmp, apt temp dirs etc, can even compile the kernel entirely on tmpfs. If I remember correctly it took some... 16 minutes to build, with 8 compiler threads, from RAM.

---

### Post by clhsharky on 2011-02-24
waperboy

> 12 gigs is enough to have e few dirs mapped to tmpfs, /tmp, apt temp dirs etc, can even compile the kernel entirely on tmpfs. If I remember correctly it took some... 16 minutes to build, with 8 compiler threads, from RAM. 

OK understand.


Sharky

---

