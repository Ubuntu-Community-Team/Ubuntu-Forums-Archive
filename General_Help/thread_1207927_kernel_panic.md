---
title: "kernel panic"
date: 2009-07-08
forum: General Help
---

### Post by ene_dene on 2009-07-08
I had a crash, before that I had a crash once again 2 days ago. I don't know why is it happening. I've selected part of syslog in time when kernel panic happened, can someone make something out of this? I was doing the usual desktop stuff, surfing and watching a movie in vlc, while I had few more opened programs, some consoles, evolution mail...

```
Jul  8 19:19:01 killers2 /USR/SBIN/CRON[22375]: (root) CMD (export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin && [ -x /usr/sbin/uptrack-upgrade ] && /usr/sbin/uptrack-upgrade --cron)
Jul  8 19:19:01 killers2 kernel: [152365.439546] BUG: unable to handle kernel paging request at ffffffff50a13df9
Jul  8 19:19:01 killers2 kernel: [152365.439552] IP: [<ffffffff805dd291>] ip_append_data+0x1/0xa40
Jul  8 19:19:01 killers2 kernel: [152365.439560] PGD 203067 PUD 0 
Jul  8 19:19:01 killers2 kernel: [152365.439562] Oops: 0002 [#10] SMP 
Jul  8 19:19:01 killers2 kernel: [152365.439565] last sysfs file: /sys/devices/platform/coretemp.3/temp1_input
Jul  8 19:19:01 killers2 kernel: [152365.439568] CPU 2 
Jul  8 19:19:01 killers2 kernel: [152365.439569] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat serpent twofish twofish_common aes_x86_64 aes_generic xts gf128mul dm_crypt xt_limit xt_tcpudp ipt_LOG ipt_MASQUERADE xt_DSCP ipt_REJECT nf_conntrack_irc nf_conntrack_ftp xt_state xt_multiport binfmt_misc ppdev bridge stp bnep vboxnetadp vboxnetflt vboxdrv input_polldev video output nfsd auth_rpcgss exportfs nfs lockd nfs_acl sunrpc coretemp lp parport snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_util_mem snd_hwdep snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 snd iptable_mangle iTCO_wdt soundcore nvidia(P) intel_agp iTCO_vendor_support iptable_filter ip_tables x_tables pcspkr usbhid ohci1394 ieee1394 skge sky2 floppy fbcon tileblit font bitblit softcursor
Jul  8 19:19:01 killers2 kernel: [152365.439619] Pid: 22376, comm: uptrack-upgrade Tainted: P      D    2.6.28-13-generic #45-Ubuntu
Jul  8 19:19:01 killers2 kernel: [152365.439621] RIP: 0010:[<ffffffff805dd291>]  [<ffffffff805dd291>] ip_append_data+0x1/0xa40
Jul  8 19:19:01 killers2 kernel: [152365.439624] RSP: 0018:ffff8801092c7ba0  EFLAGS: 00010246
Jul  8 19:19:01 killers2 kernel: [152365.439626] RAX: 000000000200a8c0 RBX: 00000000c9d64140 RCX: 000000000000002d
Jul  8 19:19:01 killers2 kernel: [152365.439628] RDX: ffff8801092c7f28 RSI: ffffffff805ddcd0 RDI: ffff88022c1ced80
Jul  8 19:19:01 killers2 kernel: [152365.439629] RBP: ffff8801092c7c78 R08: 0000000000000008 R09: ffff8801092c7c28
Jul  8 19:19:01 killers2 kernel: [152365.439631] R10: 0000000000000000 R11: 0000000000000000 R12: ffff88022c1ced80
Jul  8 19:19:01 killers2 kernel: [152365.439632] R13: 0000000000000000 R14: ffff8801092c7ee8 R15: 0000000000000025
Jul  8 19:19:01 killers2 kernel: [152365.439634] FS:  00007f150c8c96f0(0000) GS:ffff88022f802d80(0000) knlGS:0000000000000000
Jul  8 19:19:01 killers2 kernel: [152365.439636] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jul  8 19:19:01 killers2 kernel: [152365.439638] CR2: ffffffff50a13df9 CR3: 000000010937e000 CR4: 00000000000006a0
Jul  8 19:19:01 killers2 kernel: [152365.439639] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jul  8 19:19:01 killers2 kernel: [152365.439641] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jul  8 19:19:01 killers2 kernel: [152365.439643] Process uptrack-upgrade (pid: 22376, threadinfo ffff8801092c6000, task ffff8802166f5980)
Jul  8 19:19:01 killers2 kernel: [152365.439644] Stack:
Jul  8 19:19:01 killers2 kernel: [152365.439646]  ffffffff806003f9 ffff8801c9d64140 0000000100004040 ffffffff802f8400
Jul  8 19:19:01 killers2 kernel: [152365.439649]  0000000000000000 0000000100000000 fe01a8c0fe01a8c0 3500ffff0200a8c0
Jul  8 19:19:01 killers2 kernel: [152365.439652]  0000002500000000 ffff8801c9d64140 ffffffff808ff260 ffff8801092c7c24
Jul  8 19:19:01 killers2 kernel: [152365.439656] Call Trace:
Jul  8 19:19:01 killers2 kernel: [152365.439658]  [<ffffffff806003f9>] ? udp_sendmsg+0x2f9/0x740
Jul  8 19:19:01 killers2 kernel: [152365.439661]  [<ffffffff802f8400>] ? __pollwait+0x0/0x120
Jul  8 19:19:01 killers2 kernel: [152365.439665]  [<ffffffff80602012>] ? arp_bind_neighbour+0x92/0xd0
Jul  8 19:19:01 killers2 kernel: [152365.439668]  [<ffffffff806078a5>] inet_sendmsg+0x45/0x80
Jul  8 19:19:01 killers2 kernel: [152365.439671]  [<ffffffff805a29c7>] sock_sendmsg+0x107/0x130
Jul  8 19:19:01 killers2 kernel: [152365.439674]  [<ffffffff80268900>] ? autoremove_wake_function+0x0/0x40
Jul  8 19:19:01 killers2 kernel: [152365.439679]  [<ffffffff805d8c03>] ? ip_route_output_flow+0x73/0x290
Jul  8 19:19:01 killers2 kernel: [152365.439681]  [<ffffffff805fcf59>] ? ip4_datagram_connect+0x259/0x2e0
Jul  8 19:19:01 killers2 kernel: [152365.439685]  [<ffffffff805a2e5a>] sys_sendto+0xea/0x120
Jul  8 19:19:01 killers2 kernel: [152365.439687]  [<ffffffff8060791e>] ? inet_dgram_connect+0x3e/0x80
Jul  8 19:19:01 killers2 kernel: [152365.439689]  [<ffffffff8069a357>] ? lock_kernel+0x37/0x60
Jul  8 19:19:01 killers2 kernel: [152365.439693]  [<ffffffff8069a3ad>] ? unlock_kernel+0x2d/0x34
Jul  8 19:19:01 killers2 kernel: [152365.439696]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Jul  8 19:19:01 killers2 kernel: [152365.439700] Code: b9 0c 89 44 22 c1 df 08 e9 bf 98 9e 75 0e 5f 72 08 5d 33 39 38 a2 18 9e f2 f1 2a 5d 20 72 05 be 9b 64 cb 2c da 86 5d 9c 2c bc 93 <87> 15 62 6b 43 d0 55 ae a0 2f ec 6c b7 cc 01 7f b6 e7 1c 74 e5 
Jul  8 19:19:01 killers2 kernel: [152365.439726] RIP  [<ffffffff805dd291>] ip_append_data+0x1/0xa40
Jul  8 19:19:01 killers2 kernel: [152365.439728]  RSP <ffff8801092c7ba0>
Jul  8 19:19:01 killers2 kernel: [152365.439730] CR2: ffffffff50a13df9
Jul  8 19:19:01 killers2 kernel: [152365.439732] ---[ end trace c1d5393bd43b690d ]---
Jul  8 19:20:01 killers2 kernel: [152425.102353] BUG: unable to handle kernel paging request at ffffffff50a13df9
Jul  8 19:20:01 killers2 kernel: [152425.102359] IP: [<ffffffff805dd291>] ip_append_data+0x1/0xa40
Jul  8 19:20:01 killers2 kernel: [152425.102367] PGD 203067 PUD 0 
Jul  8 19:20:01 killers2 kernel: [152425.102369] Oops: 0002 [#11] SMP 
Jul  8 19:20:01 killers2 kernel: [152425.102371] last sysfs file: /sys/devices/platform/coretemp.3/temp1_input
Jul  8 19:20:01 killers2 kernel: [152425.102374] CPU 0 
Jul  8 19:20:01 killers2 kernel: [152425.102376] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat serpent twofish twofish_common aes_x86_64 aes_generic xts gf128mul dm_crypt xt_limit xt_tcpudp ipt_LOG ipt_MASQUERADE xt_DSCP ipt_REJECT nf_conntrack_irc nf_conntrack_ftp xt_state xt_multiport binfmt_misc ppdev bridge stp bnep vboxnetadp vboxnetflt vboxdrv input_polldev video output nfsd auth_rpcgss exportfs nfs lockd nfs_acl sunrpc coretemp lp parport snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_util_mem snd_hwdep snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 snd iptable_mangle iTCO_wdt soundcore nvidia(P) intel_agp iTCO_vendor_support iptable_filter ip_tables x_tables pcspkr usbhid ohci1394 ieee1394 skge sky2 floppy fbcon tileblit font bitblit softcursor
Jul  8 19:20:01 killers2 kernel: [152425.102426] Pid: 18035, comm: perl Tainted: P      D    2.6.28-13-generic #45-Ubuntu
Jul  8 19:20:01 killers2 kernel: [152425.102428] RIP: 0010:[<ffffffff805dd291>]  [<ffffffff805dd291>] ip_append_data+0x1/0xa40
Jul  8 19:20:01 killers2 kernel: [152425.102431] RSP: 0018:ffff8801b2dbbba0  EFLAGS: 00010246
Jul  8 19:20:01 killers2 kernel: [152425.102432] RAX: 000000000200a8c0 RBX: 00000000c9d64140 RCX: 0000000000000028
Jul  8 19:20:01 killers2 /USR/SBIN/CRON[22551]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jul  8 19:20:01 killers2 kernel: [152425.102434] RDX: ffff8801b2dbbf28 RSI: ffffffff805ddcd0 RDI: ffff880205a33400
Jul  8 19:20:01 killers2 kernel: [152425.102436] RBP: ffff8801b2dbbc78 R08: 0000000000000008 R09: ffff8801b2dbbc28
Jul  8 19:20:01 killers2 kernel: [152425.102437] R10: 0000000000000000 R11: 0000000000000000 R12: ffff880205a33400
Jul  8 19:20:01 killers2 kernel: [152425.102439] R13: 0000000000000000 R14: ffff8801b2dbbee8 R15: 0000000000000020
Jul  8 19:20:01 killers2 kernel: [152425.102441] FS:  00007fe7f645d6f0(0000) GS:ffffffff80a9a000(0000) knlGS:0000000000000000
Jul  8 19:20:01 killers2 kernel: [152425.102443] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jul  8 19:20:01 killers2 kernel: [152425.102444] CR2: ffffffff50a13df9 CR3: 000000011ed8b000 CR4: 00000000000006a0
Jul  8 19:20:01 killers2 kernel: [152425.102446] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jul  8 19:20:01 killers2 kernel: [152425.102447] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jul  8 19:20:01 killers2 kernel: [152425.102449] Process perl (pid: 18035, threadinfo ffff8801b2dba000, task ffff88006a9facc0)
Jul  8 19:20:01 killers2 kernel: [152425.102451] Stack:
Jul  8 19:20:01 killers2 kernel: [152425.102452]  ffffffff806003f9 ffff8801c9d64140 0000000100004040 ffffffff802f8400
Jul  8 19:20:01 killers2 kernel: [152425.102455]  0000000000000000 0000000100000000 fe01a8c0fe01a8c0 3500ffff0200a8c0
Jul  8 19:20:01 killers2 kernel: [152425.102459]  0000002000000000 ffff8801b2dbbbf8 ffffffff8022f669 ffff8801b2dbbc18
Jul  8 19:20:01 killers2 kernel: [152425.102463] Call Trace:
Jul  8 19:20:01 killers2 kernel: [152425.102464]  [<ffffffff806003f9>] ? udp_sendmsg+0x2f9/0x740
Jul  8 19:20:01 killers2 kernel: [152425.102468]  [<ffffffff802f8400>] ? __pollwait+0x0/0x120
Jul  8 19:20:01 killers2 kernel: [152425.102472]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
Jul  8 19:20:01 killers2 kernel: [152425.102476]  [<ffffffff8069a059>] ? _spin_lock+0x9/0x10
Jul  8 19:20:01 killers2 kernel: [152425.102481]  [<ffffffff806078a5>] inet_sendmsg+0x45/0x80
Jul  8 19:20:01 killers2 kernel: [152425.102483]  [<ffffffff805a29c7>] sock_sendmsg+0x107/0x130
Jul  8 19:20:01 killers2 kernel: [152425.102487]  [<ffffffff80268900>] ? autoremove_wake_function+0x0/0x40
Jul  8 19:20:01 killers2 kernel: [152425.102491]  [<ffffffff802f385f>] ? path_walk+0xbf/0xd0
Jul  8 19:20:01 killers2 kernel: [152425.102494]  [<ffffffff805d8c03>] ? ip_route_output_flow+0x73/0x290
Jul  8 19:20:01 killers2 kernel: [152425.102497]  [<ffffffff805fcf59>] ? ip4_datagram_connect+0x259/0x2e0
Jul  8 19:20:01 killers2 kernel: [152425.102500]  [<ffffffff805a2e5a>] sys_sendto+0xea/0x120
Jul  8 19:20:01 killers2 kernel: [152425.102502]  [<ffffffff8060791e>] ? inet_dgram_connect+0x3e/0x80
Jul  8 19:20:01 killers2 kernel: [152425.102505]  [<ffffffff8069a357>] ? lock_kernel+0x37/0x60
Jul  8 19:20:01 killers2 kernel: [152425.102507]  [<ffffffff8069a3ad>] ? unlock_kernel+0x2d/0x34
Jul  8 19:20:01 killers2 kernel: [152425.102510]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Jul  8 19:20:01 killers2 kernel: [152425.102514] Code: b9 0c 89 44 22 c1 df 08 e9 bf 98 9e 75 0e 5f 72 08 5d 33 39 38 a2 18 9e f2 f1 2a 5d 20 72 05 be 9b 64 cb 2c da 86 5d 9c 2c bc 93 <87> 15 62 6b 43 d0 55 ae a0 2f ec 6c b7 cc 01 7f b6 e7 1c 74 e5 
Jul  8 19:20:01 killers2 kernel: [152425.102540] RIP  [<ffffffff805dd291>] ip_append_data+0x1/0xa40
Jul  8 19:20:01 killers2 kernel: [152425.102542]  RSP <ffff8801b2dbbba0>
Jul  8 19:20:01 killers2 kernel: [152425.102544] CR2: ffffffff50a13df9
Jul  8 19:20:01 killers2 kernel: [152425.102546] ---[ end trace c1d5393bd43b690d ]---
```

---

### Post by danwood76 on 2009-07-09
Looks like an issue with coretemp.
What temoeratures are your processors running at?

If they are overheating then this could cause unexpected crashing.

---

### Post by ene_dene on 2009-07-09
> **danwood76 said:**
> Looks like an issue with coretemp.
What temoeratures are your processors running at?

If they are overheating then this could cause unexpected crashing.
Hmm, I wouldn't think so. I have Q6600 which on full load goes up to 50°C, I have a very powerful cooler.

I think that it had something to do with ext4 file system, as I was able to reproduce this by copying large amount of data onto other computer. I've reinstalled Ubuntu, and formated partitions to ext3 and will try to reproduce the crush again, if I don't it could have been the problem.

---

### Post by danwood76 on 2009-07-09
Actually re-reading that trace it may be an issue with cron.

I have been using ext4 for months and had no problems at all. (using it on heavy use partitions aswell)

---

### Post by ene_dene on 2009-07-09
> **danwood76 said:**
> Actually re-reading that trace it may be an issue with cron.

I have been using ext4 for months and had no problems at all. (using it on heavy use partitions aswell)
Unfortunately I'm having problems again after reinstalation, but now I can pin-point more accurately where seems to be the problem.
After huge load on my network I get these problems. I have backup of all the data on my server computer, after reinstalling ubuntu I started to copy data from that computer, after a while I lost connection and copying stopped (connection could not be reestablished). On system before reinstall I had the same problem, which led to kernel panic.
This started few days ago... The only two things that I can remember that I put new in last few days are and which I installed here also are:
- virtualbox 3.0 (I used 2.24 without any problems before)
- ksplice for installing kernel modules without restarting [http://www.ksplice.com/](http://www.ksplice.com/) (it would be ironic if this was the problem)

I'm not sure, perhaps I'll try to install another distribution to see if the problem persists, it may be a hardware malfunction, I hope not. But first I'll try to remove virtualbox and see what happens.

---

### Post by danwood76 on 2009-07-09
Looking into ksplice it looks like the first panic was caused by the cron service they instal.

> 
Jul  8 19:19:01 killers2 /USR/SBIN/CRON[22375]: (root) CMD (export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin && [ -x /usr/sbin/uptrack-upgrade ] && **/usr/sbin/uptrack-upgrade --cron**)


Try installing without that nonsence.
You can install most kernel modules without restarting, its only a kernel update that requires a restart and to be honest I dont think there is a way of reloading the kernel without doing  fresh boot.

---

### Post by ene_dene on 2009-07-09
I've removed it and virtualbox, I didn't get the panic, but I got the same thing as before, connection loss, here is the log:
```
Jul  9 15:35:34 killers2 kernel: [ 5008.737382] sky2 0000:02:00.0: error interrupt status=0xc0000000
Jul  9 15:35:34 killers2 kernel: [ 5008.737389] sky2 0000:02:00.0: PCI hardware error (0x2010)
```
PCI hardware error... I'll have to see if this happens on Debian Stable distro.

---

### Post by ene_dene on 2009-07-09
Same problem in Debian Lenny stable.
It seems that my network card was the problem. Didn't expect that on my 300$ Asus motherboard, fortunately my other card on that MB is functional and it works well. 

A little digression.

While thinking about the alternatives of Ubuntu system. I've come to sad conclusion that Ubuntu is the only distribution worth having for desktop. The mayor part of desktop computer - graphical card in vast majority of distributions is a real nightmare to setup, although nvidia releases the drivers, not open source, but you need to be pragmatic. For example I would never use Debian because of hard work needed to be done to have 3D acceleration (in 21.century I'm not asking for much). Other distros have the same problem or problems with poor repositories.
Thank God for Ubuntu, or I'd had to use windows for my desktop.

---

