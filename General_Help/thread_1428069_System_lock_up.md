---
title: "System lock up"
date: 2010-03-12
forum: General Help
---

### Post by dvlchd3 on 2010-03-12
In the past 15 minutes, my system has locked up twice.  The two crashes may be unrelated.  The first seemed to possibly be due to backintime attempting to backup to a corrupt hard drive.  The second I can make no sense of.

The system froze, Ctrl+Alt+F1 did not do anything.  I waited 3 minutes, and still nothing happened, so I forced the system off, and back on.  Upon restart, I found this in the messages, syslog, and kern.log log files.  I can make no sense of it, perhaps someone else can help.

```

Mar 12 09:30:22 BRICKMAN kernel: [  470.257713] /build/buildd/linux-2.6.31/mm/memory.c:118: bad pgd ffff880018a58958(ffff880018a58a08).
Mar 12 09:30:22 BRICKMAN kernel: [  470.258082] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
Mar 12 09:30:22 BRICKMAN kernel: [  470.258093] IP: [<ffffffff810ffce5>] anon_vma_unlink+0x35/0x90
Mar 12 09:30:22 BRICKMAN kernel: [  470.258112] PGD 0 
Mar 12 09:30:22 BRICKMAN kernel: [  470.258119] Oops: 0002 [#1] SMP 
Mar 12 09:30:22 BRICKMAN kernel: [  470.258126] last sysfs file: /sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/PNP0C0A:00/power_supply/BAT1/charge_full
Mar 12 09:30:22 BRICKMAN kernel: [  470.258135] CPU 0 
Mar 12 09:30:22 BRICKMAN kernel: [  470.258140] Modules linked in: binfmt_misc ppdev joydev pcmcia arc4 ecb xt_state iptable_mangle iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 iptable_filter tifm_7xx1 snd_atiixp yenta_socket rsrc_nonstatic snd_atiixp_modem snd_ac97_codec ip_tables x_tables b43 mac80211 cfg80211 snd_seq_dummy sdhci_pci sdhci led_class tifm_core pcmcia_core amd64_edac_mod psmouse serio_raw i2c_piix4 ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc edac_core shpchp k8temp lp parport 8139too radeon ttm drm i2c_algo_bit ssb ohci1394 ieee1394 8139cp mii video output
Mar 12 09:30:22 BRICKMAN kernel: [  470.258249] Pid: 2565, comm: gnome-panel Not tainted 2.6.31-20-generic #57-Ubuntu Pavilion dv8000 (EZ579UA#ABA)     
Mar 12 09:30:22 BRICKMAN kernel: [  470.258257] RIP: 0010:[<ffffffff810ffce5>]  [<ffffffff810ffce5>] anon_vma_unlink+0x35/0x90
Mar 12 09:30:22 BRICKMAN kernel: [  470.258271] RSP: 0018:ffff8800189cdac8  EFLAGS: 00010246
Mar 12 09:30:22 BRICKMAN kernel: [  470.258276] RAX: ffff88003a11a488 RBX: ffff88003a1260a0 RCX: ffff88003a479518
Mar 12 09:30:22 BRICKMAN kernel: [  470.258282] RDX: 0000000000000000 RSI: ffff8800497253d0 RDI: ffff88003a1260a0
Mar 12 09:30:22 BRICKMAN kernel: [  470.258289] RBP: ffff8800189cdae8 R08: 00007fb3639c4000 R09: 0000000000000000
Mar 12 09:30:22 BRICKMAN kernel: [  470.258295] R10: ffff880001deb0c0 R11: 0000000000000001 R12: ffff880018a588f0
Mar 12 09:30:22 BRICKMAN kernel: [  470.258301] R13: ffff880001a089c0 R14: 0000000000000000 R15: 00007fb35293b000
Mar 12 09:30:22 BRICKMAN kernel: [  470.258309] FS:  00007fb366dad7d0(0000) GS:ffff8800019fa000(0000) knlGS:0000000000000000
Mar 12 09:30:22 BRICKMAN kernel: [  470.258316] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 12 09:30:22 BRICKMAN kernel: [  470.258321] CR2: 0000000000000008 CR3: 0000000018a7b000 CR4: 00000000000006f0
Mar 12 09:30:22 BRICKMAN kernel: [  470.258328] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Mar 12 09:30:22 BRICKMAN kernel: [  470.258334] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Mar 12 09:30:22 BRICKMAN kernel: [  470.258342] Process gnome-panel (pid: 2565, threadinfo ffff8800189cc000, task ffff880038cf0000)
Mar 12 09:30:22 BRICKMAN kernel: [  470.258347] Stack:
Mar 12 09:30:22 BRICKMAN kernel: [  470.258351]  ffff880018a588f0 ffff880018a589a0 0000000000000000 ffff880001a089c0
Mar 12 09:30:22 BRICKMAN kernel: [  470.258360] <0> ffff8800189cdb38 ffffffff810f5799 ffff8800189bec60 ffff880018a588f0
Mar 12 09:30:22 BRICKMAN kernel: [  470.258370] <0> ffff8800189cdb38 ffff8800189be8f0 ffff88003a14f740 ffff880001a089c0
Mar 12 09:30:22 BRICKMAN kernel: [  470.258381] Call Trace:
Mar 12 09:30:22 BRICKMAN kernel: [  470.258391]  [<ffffffff810f5799>] free_pgtables+0x89/0x110
Mar 12 09:30:22 BRICKMAN kernel: [  470.258400]  [<ffffffff810fc1bc>] exit_mmap+0xdc/0x190
Mar 12 09:30:22 BRICKMAN kernel: [  470.258412]  [<ffffffff8105c648>] mmput+0x38/0xd0
Mar 12 09:30:22 BRICKMAN kernel: [  470.258421]  [<ffffffff81125282>] exec_mmap+0x122/0x1e0
Mar 12 09:30:22 BRICKMAN kernel: [  470.258430]  [<ffffffff8112541f>] flush_old_exec+0x7f/0x380
Mar 12 09:30:22 BRICKMAN kernel: [  470.258442]  [<ffffffff8111fadf>] ? vfs_read+0x12f/0x1a0
Mar 12 09:30:22 BRICKMAN kernel: [  470.258452]  [<ffffffff81166b83>] load_elf_binary+0x363/0xee0
Mar 12 09:30:22 BRICKMAN kernel: [  470.258462]  [<ffffffff8111fadf>] ? vfs_read+0x12f/0x1a0
Mar 12 09:30:22 BRICKMAN kernel: [  470.258471]  [<ffffffff81124987>] search_binary_handler+0xe7/0x2b0
Mar 12 09:30:22 BRICKMAN kernel: [  470.258479]  [<ffffffff81164084>] load_script+0x214/0x2b0
Mar 12 09:30:22 BRICKMAN kernel: [  470.258487]  [<ffffffff810f928f>] ? get_user_pages+0x2f/0x40
Mar 12 09:30:22 BRICKMAN kernel: [  470.258495]  [<ffffffff811244eb>] ? get_arg_page+0x4b/0xb0
Mar 12 09:30:22 BRICKMAN kernel: [  470.258504]  [<ffffffff81124987>] search_binary_handler+0xe7/0x2b0
Mar 12 09:30:22 BRICKMAN kernel: [  470.258513]  [<ffffffff8112680b>] do_execve+0x22b/0x300
Mar 12 09:30:22 BRICKMAN kernel: [  470.258524]  [<ffffffff81010535>] sys_execve+0x45/0x70
Mar 12 09:30:22 BRICKMAN kernel: [  470.258533]  [<ffffffff8101251a>] stub_execve+0x6a/0xc0
Mar 12 09:30:22 BRICKMAN kernel: [  470.258538] Code: 65 f0 48 89 5d e8 49 89 fc 4c 89 6d f8 48 8b 5f 78 48 85 db 74 42 48 89 df e8 78 d2 42 00 49 8b 54 24 68 49 8b 44 24 70 48 89 df <48> 89 42 08 48 89 10 49 c7 44 24 68 00 01 10 00 49 c7 44 24 70 
Mar 12 09:30:22 BRICKMAN kernel: [  470.258609] RIP  [<ffffffff810ffce5>] anon_vma_unlink+0x35/0x90
Mar 12 09:30:22 BRICKMAN kernel: [  470.258618]  RSP <ffff8800189cdac8>
Mar 12 09:30:22 BRICKMAN kernel: [  470.258622] CR2: 0000000000000008
Mar 12 09:30:22 BRICKMAN kernel: [  470.258637] ---[ end trace 7886d3f76a3a37ff ]---

```

uname -a
```

Linux BRICKMAN 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux
```

---

