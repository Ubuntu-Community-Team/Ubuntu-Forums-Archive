---
title: "Computer freezes"
date: 2010-11-22
forum: General Help
---

### Post by haggai_e on 2010-11-22
Hi,

I have a problem with recurring freezes. I'm using Ubuntu maverick on amd64 (an ASUS M2NPV-VM board). After the last time it froze, I found this in the logs:

```
Nov 22 05:06:19 mrblack kernel: [39007.264275] general protection fault: 0000 [#1] SMP 
Nov 22 05:06:19 mrblack kernel: [39007.264281] last sysfs file: /sys/devices/virtual/net/vboxnet0/statistics/collisions
Nov 22 05:06:19 mrblack kernel: [39007.264284] CPU 0 
Nov 22 05:06:19 mrblack kernel: [39007.264285] Modules linked in: cryptd aes_x86_64 aes_generic binfmt_misc vboxnetadp vboxnetflt vboxdrv parport_pc ppdev snd_hda_codec_analog nvidia(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_s
eq_midi snd_rawmidi snd_seq_midi_event snd_seq ipt_REJECT xt_comment ipt_LOG xt_multiport xt_limit xt_tcpudp ipt_addrtype xt_state hwmon_vid ip6table_filter ip6_tables nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_nat nf_conntrack_ipv4 nf_de
frag_ipv4 nf_conntrack_ftp eeprom snd_timer nf_conntrack usblp snd_seq_device sbp2 iptable_filter ip_tables x_tables psmouse serio_raw ieee1394 asus_atk0110 edac_core snd soundcore k8temp edac_mce_amd i2c_nforce2 snd_page_alloc lp parpor
t raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid1 firewire_ohci firewire_core raid0 forcedeth crc_itu_t pata_amd multipath sata_nv linear
Nov 22 05:06:19 mrblack kernel: [39007.264342] 
Nov 22 05:06:19 mrblack kernel: [39007.264345] Pid: 3117, comm: dropbox Tainted: P        W   2.6.35-22-generic #35-Ubuntu M2NPV-VM/System Product Name
Nov 22 05:06:19 mrblack kernel: [39007.264349] RIP: 0010:[<ffffffff81142f54>]  [<ffffffff81142f54>] kmem_cache_alloc_notrace+0x64/0xd0
Nov 22 05:06:19 mrblack kernel: [39007.264357] RSP: 0018:ffff88016ef8ddf8  EFLAGS: 00010082
Nov 22 05:06:19 mrblack kernel: [39007.264359] RAX: ffff880001e128f0 RBX: 00000000000000d0 RCX: 0000000000000000
Nov 22 05:06:19 mrblack kernel: [39007.264362] RDX: 0000000000000000 RSI: 00000000000000d0 RDI: ffffffff81a25290
Nov 22 05:06:19 mrblack kernel: [39007.264364] RBP: ffff88016ef8de28 R08: ffff88016ef8df60 R09: 0000000000000000
Nov 22 05:06:19 mrblack kernel: [39007.264367] R10: ffffffff81d11da0 R11: 0000000000000202 R12: ffffffff81a25290
Nov 22 05:06:19 mrblack kernel: [39007.264370] R13: 0000000000000246 R14: 89ffff880002a7b9 R15: ffffffff81486d45
Nov 22 05:06:19 mrblack kernel: [39007.264373] FS:  00007f1db28fb710(0000) GS:ffff880001e00000(0000) knlGS:00000000f6955a90
Nov 22 05:06:19 mrblack kernel: [39007.264376] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Nov 22 05:06:19 mrblack kernel: [39007.264378] CR2: 00007fbc16afe000 CR3: 00000001851d1000 CR4: 00000000000006f0
Nov 22 05:06:19 mrblack kernel: [39007.264381] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Nov 22 05:06:19 mrblack kernel: [39007.264384] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Nov 22 05:06:19 mrblack kernel: [39007.264387] Process dropbox (pid: 3117, threadinfo ffff88016ef8c000, task ffff88016ef916e0)
Nov 22 05:06:19 mrblack kernel: [39007.264389] Stack:
Nov 22 05:06:19 mrblack kernel: [39007.264391]  ffff88016ef8de18 ffff8800b28fd680 ffff8801a913d000 ffff8801a913d000
Nov 22 05:06:19 mrblack kernel: [39007.264395] <0> 0000000000000000 0000000000000100 ffff88016ef8de68 ffffffff81486d45
Nov 22 05:06:19 mrblack kernel: [39007.264399] <0> ffff88016ef8de58 ffffffff81165c3f ffff8801808190c0 0000000000000001
Nov 22 05:06:19 mrblack kernel: [39007.264404] Call Trace:
Nov 22 05:06:19 mrblack kernel: [39007.264410]  [<ffffffff81486d45>] sock_alloc_inode+0x45/0x120
Nov 22 05:06:19 mrblack kernel: [39007.264415]  [<ffffffff81165c3f>] ? __d_free+0x3f/0x60
Nov 22 05:06:19 mrblack kernel: [39007.264419]  [<ffffffff8116a337>] alloc_inode+0x27/0xa0
Nov 22 05:06:19 mrblack kernel: [39007.264423]  [<ffffffff8116a3dd>] new_inode+0x2d/0xd0
Nov 22 05:06:19 mrblack kernel: [39007.264427]  [<ffffffff81486049>] sock_alloc+0x19/0x60
Nov 22 05:06:19 mrblack kernel: [39007.264430]  [<ffffffff81486423>] __sock_create+0x93/0x240
Nov 22 05:06:19 mrblack kernel: [39007.264434]  [<ffffffff81486630>] sock_create+0x30/0x40
Nov 22 05:06:19 mrblack kernel: [39007.264437]  [<ffffffff8148684c>] sys_socket+0x3c/0x80
Nov 22 05:06:19 mrblack kernel: [39007.264442]  [<ffffffff811509b7>] ? sys_close+0xb7/0x120
Nov 22 05:06:19 mrblack kernel: [39007.264447]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
Nov 22 05:06:19 mrblack kernel: [39007.264449] Code: 90 66 90 49 89 c5 fa 66 66 90 66 66 90 65 48 8b 14 25 58 eb 00 00 49 8b 04 24 48 8d 04 02 4c 8b 30 4d 85 f6 74 57 49 63 54 24 18 <49> 8b 14 16 48 89 10 4c 89 ef 57 9d 66 66 90 66 90 4d
 85 f6 75 
Nov 22 05:06:19 mrblack kernel: [39007.264481] RIP  [<ffffffff81142f54>] kmem_cache_alloc_notrace+0x64/0xd0
Nov 22 05:06:19 mrblack kernel: [39007.264485]  RSP <ffff88016ef8ddf8>
Nov 22 05:06:19 mrblack kernel: [39007.264489] ---[ end trace 6c98c32735743c31 ]---
```

Does anyone have an idea what should I do?

---

### Post by TeoBigusGeekus on 2010-11-22
The only thing I could understand is the word Dropbox.
If you have it running, try closing it and then monitor the behaviour of your system.

---

