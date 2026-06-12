---
title: "OS and program crashes"
date: 2006-06-11
forum: General Help
---

### Post by sizza on 2006-06-11
I'm running Xubuntu 6.06 on a Celeron 850/640mb/40gig/9200se. Since I installed the OS, i've been experiancing crashes every few hours. Somtimes just a program (Terminal, Firefox, Gaim, etc), and other times my whole system. I've installed flgrx drivers, but that hasn't helped.

```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1060 (X4.3.0-8.24.8)
```

Can anyone help me fix this? Here's some results from my syslog, I am not aware if they mean anything.

```
Jun 11 01:34:21 nix kernel: [50938.073709] Bad page state at prep_new_page (in process 'firefox-bin', page c12b7e40)
Jun 11 01:34:21 nix kernel: [50938.073736] flags:0x80000000 mapping:00000000 mapcount:0 count:-262144
Jun 11 01:34:21 nix kernel: [50938.073741] Backtrace:
Jun 11 01:34:21 nix kernel: [50938.073789]  [bad_page+93/176] bad_page+0x5d/0xb0
Jun 11 01:34:21 nix kernel: [50938.073826]  [prep_new_page+22/128] prep_new_page+0x16/0x80
Jun 11 01:34:21 nix kernel: [50938.073840]  [buffered_rmqueue+199/592] buffered_rmqueue+0xc7/0x250
Jun 11 01:34:21 nix kernel: [50938.073860]  [get_page_from_freelist+113/208] get_page_from_freelist+0x71/0xd0
Jun 11 01:34:21 nix kernel: [50938.073878]  [__alloc_pages+78/736] __alloc_pages+0x4e/0x2e0
Jun 11 01:34:21 nix kernel: [50938.073901]  [__get_free_pages+30/64] __get_free_pages+0x1e/0x40
Jun 11 01:34:21 nix kernel: [50938.073910]  [__pollwait+108/176] __pollwait+0x6c/0xb0
Jun 11 01:34:21 nix kernel: [50938.073926]  [unix_poll+32/160] unix_poll+0x20/0xa0
Jun 11 01:34:21 nix kernel: [50938.073951]  [sock_poll+19/32] sock_poll+0x13/0x20
Jun 11 01:34:21 nix kernel: [50938.073979]  [do_pollfd+71/208] do_pollfd+0x47/0xd0
Jun 11 01:34:21 nix kernel: [50938.073993]  [do_poll+111/224] do_poll+0x6f/0xe0
Jun 11 01:34:21 nix kernel: [50938.074010]  [sys_poll+317/672] sys_poll+0x13d/0x2a0
Jun 11 01:34:21 nix kernel: [50938.074074]  [sys_ioctl+93/144] sys_ioctl+0x5d/0x90
Jun 11 01:34:21 nix kernel: [50938.074084]  [__pollwait+0/176] __pollwait+0x0/0xb0
Jun 11 01:34:21 nix kernel: [50938.074098]  [sysenter_past_esp+84/121] sysenter_past_esp+0x54/0x79
Jun 11 01:34:21 nix kernel: [50938.074127] Trying to fix it up, but a reboot is needed

Jun 11 14:34:44 nix kernel: [14295.542755] ------------[ cut here ]------------
Jun 11 14:34:44 nix kernel: [14295.542783] kernel BUG at lib/kernel_lock.c:83!
Jun 11 14:34:44 nix kernel: [14295.542790] invalid operand: 0000 [#1]
Jun 11 14:34:44 nix kernel: [14295.542794] PREEMPT 
Jun 11 14:34:44 nix kernel: [14295.542799] Modules linked in: apm ppdev fglrx cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative dm_mod md_mod ipv6 lp af_packet floppy tsdev pcspkr parport_pc parport psmouse rtc snd_ens1371 gameport snd_rawmidi snd_seq_device snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc e100 snd_ac97_bus serio_raw mii shpchp pci_hotplug via_agp agpgart i2c_viapro i2c_core evdev ext3 jbd ide_generic ide_disk ide_cd cdrom via82cxxx generic processor capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Jun 11 14:34:44 nix kernel: [14295.542870] CPU:    0
Jun 11 14:34:44 nix kernel: [14295.542872] EIP:    0060:[unlock_kernel+33/43]    Tainted: P      VLI
Jun 11 14:34:44 nix kernel: [14295.542876] EFLAGS: 00010286   (2.6.15-23-386) 
Jun 11 14:34:44 nix kernel: [14295.542907] EIP is at unlock_kernel+0x21/0x2b
Jun 11 14:34:44 nix kernel: [14295.542914] eax: 9efc0000   ebx: 00000000   ecx: d762a000   edx: e5bd4a70
Jun 11 14:34:44 nix kernel: [14295.542922] esi: bff1bb1c   edi: 00005414   ebp: 0000000a   esp: e5bd9f4c
Jun 11 14:34:44 nix kernel: [14295.542929] ds: 007b   es: 007b   ss: 0068
Jun 11 14:34:44 nix kernel: [14295.542936] Process Terminal (pid: 4700, threadinfo=e5bd8000 task=e5bd4a70)
Jun 11 14:34:44 nix kernel: [14295.542942] Stack: c0172f1e d762a000 d762a000 bff1bb1c bff1bb1c d6f78300 d6f78300 bff1bb1c 
Jun 11 14:34:44 nix kernel: [14295.542959]        c01730b1 d6f78300 00005414 bff1bb1c 00000001 d6f783a0 d6f78300 00000000 
Jun 11 14:34:44 nix kernel: [14295.542975]        bff1bb1c c01732ad d6f78300 0000000a 00005414 bff1bb1c 00000000 0000000a 
Jun 11 14:34:44 nix kernel: [14295.542990] Call Trace:
Jun 11 14:34:44 nix kernel: [14295.542995]  [do_ioctl+110/128] do_ioctl+0x6e/0x80
Jun 11 14:34:44 nix kernel: [14295.543029]  [vfs_ioctl+81/496] vfs_ioctl+0x51/0x1f0
Jun 11 14:34:44 nix kernel: [14295.543046]  [sys_ioctl+93/144] sys_ioctl+0x5d/0x90
Jun 11 14:34:44 nix kernel: [14295.543064]  [sysenter_past_esp+84/121] sysenter_past_esp+0x54/0x79
Jun 11 14:34:44 nix kernel: [14295.543094] Code: 51 89 4a 14 c3 90 8d 74 26 00 b8 00 e0 ff ff 21 e0 8b 10 8b 42 14 85 c0 78 11 48 89 42 14 85 c0 79 08 ff 05 a0 f1 33 c0 7e 35 c3 <0f> 0b 53 00 15 8f 30 c0 eb e5 8d 05 a0 f1 33 c0 e8 f2 e6 ff ff 
Jun 11 14:34:44 nix kernel: [14295.543164]  ------------[ cut here ]------------
Jun 11 14:34:44 nix kernel: [14295.550861] kernel BUG at lib/kernel_lock.c:83!
Jun 11 14:34:44 nix kernel: [14295.550872] invalid operand: 0000 [#2]
Jun 11 14:34:44 nix kernel: [14295.550876] PREEMPT 
Jun 11 14:34:44 nix kernel: [14295.550881] Modules linked in: apm ppdev fglrx cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative dm_mod md_mod ipv6 lp af_packet floppy tsdev pcspkr parport_pc parport psmouse rtc snd_ens1371 gameport snd_rawmidi snd_seq_device snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc e100 snd_ac97_bus serio_raw mii shpchp pci_hotplug via_agp agpgart i2c_viapro i2c_core evdev ext3 jbd ide_generic ide_disk ide_cd cdrom via82cxxx generic processor capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Jun 11 14:34:44 nix kernel: [14295.550954] CPU:    0
Jun 11 14:34:44 nix kernel: [14295.550956] EIP:    0060:[unlock_kernel+33/43]    Tainted: P      VLI
Jun 11 14:34:44 nix kernel: [14295.550960] EFLAGS: 00010282   (2.6.15-23-386) 
Jun 11 14:34:44 nix kernel: [14295.550992] EIP is at unlock_kernel+0x21/0x2b
Jun 11 14:34:44 nix kernel: [14295.551000] eax: 9efc0002   ebx: e6acb00c   ecx: 00000001   edx: e5bd4a70
Jun 11 14:34:44 nix kernel: [14295.551007] esi: 00000000   edi: 00000000   ebp: e6acb00c   esp: e5bd9d14
Jun 11 14:34:44 nix kernel: [14295.551014] ds: 007b   es: 007b   ss: 0068
Jun 11 14:34:44 nix kernel: [14295.551021] Process Terminal (pid: 4700, threadinfo=e5bd8000 task=e5bd4a70)
Jun 11 14:34:44 nix kernel: [14295.551027] Stack: c021e1fd 00000000 00000000 00000001 df8b8000 dfad7c9c e6acb000 dcf4b2c0 
Jun 11 14:34:44 nix kernel: [14295.551043]        c021f2f4 e6acb000 dcf4b2c0 00000001 e5e0eb60 00000000 00000001 00000000 
Jun 11 14:34:44 nix kernel: [14295.551058]        dfeaaa80 e5e0eb60 00000000 e5e0ea00 c02e1475 e5e0eb60 0100000c c0161edc 
Jun 11 14:34:44 nix kernel: [14295.551075] Call Trace:
Jun 11 14:34:44 nix kernel: [14295.551080]  [do_tty_hangup+701/928] do_tty_hangup+0x2bd/0x3a0
Jun 11 14:34:44 nix kernel: [14295.551125]  [release_dev+324/1808] release_dev+0x144/0x710
Jun 11 14:34:44 nix kernel: [14295.551147]  [unix_release_sock+517/624] unix_release_sock+0x205/0x270
Jun 11 14:34:44 nix kernel: [14295.551169]  [invalidate_inode_buffers+12/96] invalidate_inode_buffers+0xc/0x60
Jun 11 14:34:44 nix kernel: [14295.551201]  [sock_destroy_inode+20/32] sock_destroy_inode+0x14/0x20
Jun 11 14:34:44 nix kernel: [14295.551237]  [tty_release+15/32] tty_release+0xf/0x20
Jun 11 14:34:44 nix kernel: [14295.551247]  [__fput+119/352] __fput+0x77/0x160
Jun 11 14:34:44 nix kernel: [14295.551263]  [filp_close+59/128] filp_close+0x3b/0x80
Jun 11 14:34:44 nix kernel: [14295.551279]  [put_files_struct+114/192] put_files_struct+0x72/0xc0
Jun 11 14:34:44 nix kernel: [14295.551315]  [do_exit+308/1056] do_exit+0x134/0x420
Jun 11 14:34:44 nix kernel: [14295.551327]  [do_invalid_op+0/160] do_invalid_op+0x0/0xa0
Jun 11 14:34:44 nix kernel: [14295.551344]  [die+355/368] die+0x163/0x170
Jun 11 14:34:44 nix kernel: [14295.551359]  [do_invalid_op+140/160] do_invalid_op+0x8c/0xa0
Jun 11 14:34:44 nix kernel: [14295.551378]  [unlock_kernel+33/43] unlock_kernel+0x21/0x2b
Jun 11 14:34:44 nix kernel: [14295.551387]  [copy_page_range+178/240] copy_page_range+0xb2/0xf0
Jun 11 14:34:44 nix kernel: [14295.551411]  [__group_send_sig_info+25/128] __group_send_sig_info+0x19/0x80
Jun 11 14:34:44 nix kernel: [14295.551447]  [__kill_pg_info+72/160] __kill_pg_info+0x48/0xa0
Jun 11 14:34:44 nix kernel: [14295.551467]  [error_code+79/96] error_code+0x4f/0x60
Jun 11 14:34:44 nix kernel: [14295.551488]  [unlock_kernel+33/43] unlock_kernel+0x21/0x2b
Jun 11 14:34:44 nix kernel: [14295.551499]  [do_ioctl+110/128] do_ioctl+0x6e/0x80
Jun 11 14:34:44 nix kernel: [14295.551518]  [vfs_ioctl+81/496] vfs_ioctl+0x51/0x1f0
Jun 11 14:34:44 nix kernel: [14295.551534]  [sys_ioctl+93/144] sys_ioctl+0x5d/0x90
Jun 11 14:34:44 nix kernel: [14295.551553]  [sysenter_past_esp+84/121] sysenter_past_esp+0x54/0x79
Jun 11 14:34:44 nix kernel: [14295.551578] Code: 51 89 4a 14 c3 90 8d 74 26 00 b8 00 e0 ff ff 21 e0 8b 10 8b 42 14 85 c0 78 11 48 89 42 14 85 c0 79 08 ff 05 a0 f1 33 c0 7e 35 c3 <0f> 0b 53 00 15 8f 30 c0 eb e5 8d 05 a0 f1 33 c0 e8 f2 e6 ff ff 
Jun 11 14:34:44 nix kernel: [14295.551649]  <1>Fixing recursive fault but reboot is needed!
```

---

### Post by sizza on 2006-06-11
Any ideas? I've since run memtest86 without any errors...

---

### Post by Stanislav Valasek on 2006-07-09
Hello,

I'm running Ubuntu 6.06 on a AMD with nVidia GeForce 6200.

But probably one month ago (Hoary went fine even early after update to Dapper system was stable) my PC started to freeze every few hours. Everytime the whole system crashes. CTRL+ALT+BackSpace or Ctrl+Alt+F1 doesn't work, only one sollution is hard reset. Now running on k7 kernel but ithe same is valid for i386 kernel.

I am not a developer but probably able to inspect my system to send more logs and info.

Attached is excerpt from syslog where are logged errors in XOrg.

Thank you for any hints how to solve this problem. I am able to do some investigation on my PC to find out a sollution for this problem. Thanks for any help.

Should I report this as a bug?

```
 Jul  9 17:28:46 ubuntu-pc kernel: [17179641.452000] Bad page state at prep_new_page (in process 'Xorg', page c11eb244)
Jul  9 17:28:46 ubuntu-pc kernel: [17179641.452000] flags:0x80000014 mapping:00000000 mapcount:0 count:0
Jul  9 17:28:46 ubuntu-pc kernel: [17179641.452000] Backtrace:
Jul  9 17:28:46 ubuntu-pc kernel: [17179641.452000]  [bad_page+129/192] bad_page+0x81/0xc0
Jul  9 17:28:46 ubuntu-pc kernel: [17179641.452000]  [prep_new_page+30/128] prep_new_page+0x1e/0x80
Jul  9 17:28:46 ubuntu-pc kernel: [17179641.452000]  [buffered_rmqueue+296/608] buffered_rmqueue+0x128/0x260
Jul  9 17:28:46 ubuntu-pc kernel: [17179641.452000]  [get_page_from_freelist+113/192] get_page_from_freelist+0x71/0xc0
Jul  9 17:28:46 ubuntu-pc kernel: [17179641.452000]  [__alloc_pages+116/816] __alloc_pages+0x74/0x330
Jul  9 17:28:46 ubuntu-pc kernel: [17179641.452000]  [do_anonymous_page+268/496] do_anonymous_page+0x10c/0x1f0
Jul  9 17:28:46 ubuntu-pc kernel: [17179641.452000]  [__handle_mm_fault+556/736] __handle_mm_fault+0x22c/0x2e0
Jul  9 17:28:46 ubuntu-pc kernel: [17179641.452000]  [do_page_fault+311/1582] do_page_fault+0x137/0x62e
Jul  9 17:28:46 ubuntu-pc kernel: [17179641.452000]  [do_page_fault+0/1582] do_page_fault+0x0/0x62e
Jul  9 17:28:46 ubuntu-pc kernel: [17179641.452000]  [error_code+79/84] error_code+0x4f/0x54
Jul  9 17:28:46 ubuntu-pc kernel: [17179641.452000] Trying to fix it up, but a reboot is needed
Jul  8 21:59:36 ubuntu-pc kernel: [17179673.768000] Bad page state at prep_new_page (in process 'nautilus', page c122b204)
Jul  8 21:59:36 ubuntu-pc kernel: [17179673.768000] flags:0x80000014 mapping:00000000 mapcount:0 count:0
Jul  8 21:59:36 ubuntu-pc kernel: [17179673.768000] Backtrace:
Jul  8 21:59:36 ubuntu-pc kernel: [17179673.768000]  [bad_page+129/192] bad_page+0x81/0xc0
Jul  8 21:59:36 ubuntu-pc kernel: [17179673.768000]  [prep_new_page+30/128] prep_new_page+0x1e/0x80
Jul  8 21:59:36 ubuntu-pc kernel: [17179673.768000]  [buffered_rmqueue+296/608] buffered_rmqueue+0x128/0x260
Jul  8 21:59:36 ubuntu-pc kernel: [17179673.768000]  [get_page_from_freelist+113/192] get_page_from_freelist+0x71/0xc0
Jul  8 21:59:36 ubuntu-pc kernel: [17179673.768000]  [__alloc_pages+116/816] __alloc_pages+0x74/0x330
Jul  8 21:59:36 ubuntu-pc kernel: [17179673.772000]  [do_anonymous_page+268/496] do_anonymous_page+0x10c/0x1f0
Jul  8 21:59:36 ubuntu-pc kernel: [17179673.772000]  [__handle_mm_fault+556/736] __handle_mm_fault+0x22c/0x2e0
Jul  8 21:59:36 ubuntu-pc kernel: [17179673.772000]  [do_page_fault+311/1582] do_page_fault+0x137/0x62e
Jul  8 21:59:36 ubuntu-pc kernel: [17179673.772000]  [do_page_fault+0/1582] do_page_fault+0x0/0x62e
Jul  8 21:59:37 ubuntu-pc kernel: [17179673.772000]  [error_code+79/84] error_code+0x4f/0x54
Jul  8 21:59:37 ubuntu-pc kernel: [17179673.772000] Trying to fix it up, but a reboot is needed
Jul  8 22:02:14 ubuntu-pc kernel: [17179831.768000] Bad page state at prep_new_page (in process 'gjots2', page c13baec4)
Jul  8 22:02:14 ubuntu-pc kernel: [17179831.768000] flags:0x80000014 mapping:00000000 mapcount:0 count:0
Jul  8 22:02:14 ubuntu-pc kernel: [17179831.768000] Backtrace:
Jul  8 22:02:14 ubuntu-pc kernel: [17179831.768000]  [bad_page+129/192] bad_page+0x81/0xc0
Jul  8 22:02:14 ubuntu-pc kernel: [17179831.768000]  [prep_new_page+30/128] prep_new_page+0x1e/0x80
Jul  8 22:02:14 ubuntu-pc kernel: [17179831.768000]  [buffered_rmqueue+296/608] buffered_rmqueue+0x128/0x260
Jul  8 22:02:14 ubuntu-pc kernel: [17179831.768000]  [get_page_from_freelist+113/192] get_page_from_freelist+0x71/0xc0
Jul  8 22:02:14 ubuntu-pc kernel: [17179831.768000]  [__alloc_pages+116/816] __alloc_pages+0x74/0x330
Jul  8 22:02:14 ubuntu-pc kernel: [17179831.768000]  [find_get_page+70/96] find_get_page+0x46/0x60
Jul  8 22:02:14 ubuntu-pc kernel: [17179831.768000]  [read_swap_cache_async+91/176] read_swap_cache_async+0x5b/0xb0
Jul  8 22:02:14 ubuntu-pc kernel: [17179831.768000]  [swapin_readahead+123/176] swapin_readahead+0x7b/0xb0
Jul  8 22:02:15 ubuntu-pc kernel: [17179831.768000]  [do_swap_page+536/784] do_swap_page+0x218/0x310
Jul  8 22:02:15 ubuntu-pc kernel: [17179831.768000]  [__handle_mm_fault+300/736] __handle_mm_fault+0x12c/0x2e0
Jul  8 22:02:15 ubuntu-pc kernel: [17179831.768000]  [do_page_fault+311/1582] do_page_fault+0x137/0x62e
Jul  8 22:02:15 ubuntu-pc kernel: [17179831.768000]  [do_page_fault+0/1582] do_page_fault+0x0/0x62e
Jul  8 22:02:15 ubuntu-pc kernel: [17179831.768000]  [error_code+79/84] error_code+0x4f/0x54
Jul  8 22:02:15 ubuntu-pc kernel: [17179831.768000] Trying to fix it up, but a reboot is needed
```

---

