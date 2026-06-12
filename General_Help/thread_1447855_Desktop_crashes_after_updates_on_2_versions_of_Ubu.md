---
title: "Desktop crashes after updates on 2 versions of Ubuntu"
date: 2010-04-05
forum: General Help
---

### Post by djoxyk on 2010-04-05
I have used ubuntu 8.04 and it worked ok. After recent updates it started to crash from Virtualbox into screen of death. I did not had any clue why. 
I have created new partition, installed bare lucid from command line and added minimum of apps incl. latest virtualbox. This version gave me the same crashes but instead of black screen it just kicks me into display manager. Also i have tried to use qemu instead of virtualbox. It worked a bit longer but eventually crashed in the same way. While using windows xp on 3d boot i have pretty stable PC (no crashes in months). 

My videocard is ATI Radeon 3650 HD (using radeonhd driver). Tech guy checked my PC and did not found any hardware issues. 

Below is the part of log from lucid before crash. Please help me to understand who is  causing it.


```


Apr  6 04:09:02 top CRON[23936]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Apr  6 04:12:36 top kernel: [ 4288.558043] BUG: unable to handle kernel NULL pointer dereference at 0000000000000007
Apr  6 04:12:36 top kernel: [ 4288.558052] IP: [<ffffffff814e0c20>] unix_stream_recvmsg+0x1a0/0x580
Apr  6 04:12:36 top kernel: [ 4288.558062] PGD 72800067 PUD 56bb8067 PMD 0 
Apr  6 04:12:36 top kernel: [ 4288.558066] Oops: 0000 [#2] SMP 
Apr  6 04:12:36 top kernel: [ 4288.558069] last sysfs file: /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
Apr  6 04:12:36 top kernel: [ 4288.558073] CPU 1 
Apr  6 04:12:36 top kernel: [ 4288.558075] Modules linked in: btrfs zlib_deflate crc32c libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs exportfs reiserfs xt_TCPMSS xt_tcpmss iptable_mangle binfmt_misc vboxnetadp vboxnetflt vboxdrv ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT xt_tcpudp iptable_filter ip_tables x_tables kvm_amd kvm pppoe pppox snd_hda_codec_atihdmi fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy bridge stp snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event radeon snd_seq ttm snd_timer snd_seq_device psmouse drm_kms_helper ppdev snd serio_raw parport_pc i2c_piix4 k8temp drm edac_core i2c_algo_bit edac_mce_amd soundcore snd_page_alloc lp parport usb_storage r8169 mii pata_atiixp ahci
Apr  6 04:12:36 top kernel: [ 4288.558132] Pid: 2776, comm: Xorg Tainted: G      D    2.6.32-17-generic #26-Ubuntu GA-MA69VM-S2
Apr  6 04:12:36 top kernel: [ 4288.558135] RIP: 0010:[<ffffffff814e0c20>]  [<ffffffff814e0c20>] unix_stream_recvmsg+0x1a0/0x580
Apr  6 04:12:36 top kernel: [ 4288.558140] RSP: 0018:ffff88007b60bc08  EFLAGS: 00010246
Apr  6 04:12:36 top kernel: [ 4288.558142] RAX: ffff880037411400 RBX: ffff880037411400 RCX: 0000000000000008
Apr  6 04:12:36 top kernel: [ 4288.558144] RDX: 0000000000000001 RSI: ffff88003741143c RDI: ffff88007b60bc8c
Apr  6 04:12:36 top kernel: [ 4288.558146] RBP: ffff88007b60bce8 R08: 00000000000007c8 R09: 0000000000000001
Apr  6 04:12:36 top kernel: [ 4288.558149] R10: ffff880001e2a100 R11: 0000000000000400 R12: ffff88007b60bd40
Apr  6 04:12:36 top kernel: [ 4288.558151] R13: ffff88007b60bd08 R14: 0000000000000000 R15: 0000000000024cb8
Apr  6 04:12:36 top kernel: [ 4288.558154] FS:  00007f0681c83700(0000) GS:ffff880001c80000(0000) knlGS:00000000f49e5b70
Apr  6 04:12:36 top kernel: [ 4288.558156] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Apr  6 04:12:36 top kernel: [ 4288.558158] CR2: 0000000000000007 CR3: 000000004343d000 CR4: 00000000000006e0
Apr  6 04:12:36 top kernel: [ 4288.558161] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Apr  6 04:12:36 top kernel: [ 4288.558163] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Apr  6 04:12:36 top kernel: [ 4288.558166] Process Xorg (pid: 2776, threadinfo ffff88007b60a000, task ffff880074112de0)
Apr  6 04:12:36 top kernel: [ 4288.558167] Stack:
Apr  6 04:12:36 top kernel: [ 4288.558169]  ffffffff81154840 0000000000000040 ffff8800657bb44c ffff880074112de0
Apr  6 04:12:36 top kernel: [ 4288.558173] <0> ffff8800657bb300 0000000000000000 ffff8800657bb568 ffffffa17b60bab8
Apr  6 04:12:36 top kernel: [ 4288.558176] <0> 0000000100000000 0000000000100100 0000000000200200 ffff8800657bb3b0
Apr  6 04:12:36 top kernel: [ 4288.558180] Call Trace:
Apr  6 04:12:36 top kernel: [ 4288.558187]  [<ffffffff81154840>] ? pollwake+0x0/0x60
Apr  6 04:12:36 top kernel: [ 4288.558193]  [<ffffffff8144cd69>] sock_aio_read+0x159/0x160
Apr  6 04:12:36 top kernel: [ 4288.558197]  [<ffffffff811426aa>] do_sync_read+0xfa/0x140
Apr  6 04:12:36 top kernel: [ 4288.558202]  [<ffffffff810852e0>] ? autoremove_wake_function+0x0/0x40
Apr  6 04:12:36 top kernel: [ 4288.558209]  [<ffffffff810397a9>] ? default_spin_lock_flags+0x9/0x10
Apr  6 04:12:36 top kernel: [ 4288.558214]  [<ffffffff81250756>] ? security_file_permission+0x16/0x20
Apr  6 04:12:36 top kernel: [ 4288.558217]  [<ffffffff81143091>] vfs_read+0x181/0x1a0
Apr  6 04:12:36 top kernel: [ 4288.558222]  [<ffffffff81543148>] ? do_page_fault+0x158/0x3b0
Apr  6 04:12:36 top kernel: [ 4288.558225]  [<ffffffff81143181>] sys_read+0x51/0x80
Apr  6 04:12:36 top kernel: [ 4288.558230]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
Apr  6 04:12:36 top kernel: [ 4288.558232] Code: 89 c3 0f 84 d9 01 00 00 48 8b 7d 90 e8 4a 8b b5 ff 66 90 8b 55 84 85 d2 0f 84 a6 01 00 00 49 8b 7d 28 48 8d 73 38 b9 0c 00 00 00 <f3> a6 0f 85 0b 03 00 00 4d 85 f6 74 39 48 8b 43 10 41 c7 44 24 
Apr  6 04:12:36 top kernel: [ 4288.558259] RIP  [<ffffffff814e0c20>] unix_stream_recvmsg+0x1a0/0x580
Apr  6 04:12:36 top kernel: [ 4288.558262]  RSP <ffff88007b60bc08>
Apr  6 04:12:36 top kernel: [ 4288.558264] CR2: 0000000000000007
Apr  6 04:12:36 top kernel: [ 4288.558267] ---[ end trace 752e3d4d0e379924 ]---
Apr  6 04:12:38 top kernel: [ 4290.817434] VirtualBox[23990]: segfault at 13a83cb0 ip 00007fecb7cb81b5 sp 00007fec9b6978d0 error 4 in libc-2.11.1.so[7fecb7c7f000+178000]
Apr  6 04:12:44 top gdm-simple-slave[24003]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr  6 04:12:49 top gnome-session[24029]: WARNING: Could not launch application 'gnome-power-manager.desktop': Unable to start application: Failed to execute child process "gnome-power-manager" (No such file or directory)
Apr  6 04:12:49 top gdm-session-worker[24037]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr  6 04:12:50 top gdm-simple-greeter[24035]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.UPower was not provided by any .service files
Apr  6 04:12:50 top gdm-simple-greeter[24035]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.UPower was not provided by any .service files
Apr  6 04:12:50 top gdm-simple-greeter[24035]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Apr  6 04:12:53 top gdm-session-worker[24037]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed


```

---

