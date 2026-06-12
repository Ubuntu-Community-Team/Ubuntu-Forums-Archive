---
title: "Logs growing exponentially"
date: 2010-06-27
forum: General Help
---

### Post by shafin on 2010-06-27
Hi,
Recently I've been facing a problems with log files growing exponentially. After inspecting the logs like daemon.log, kern.log, messages and syslog, I found that modem manager is generating huge amounts of logs in these files. For example, this lines are repeated in daemon.log

```
Jun 27 16:30:35 C2D-desktop NetworkManager: <info>  Trying to start the modem-manager...
Jun 27 16:30:35 C2D-desktop NetworkManager: <info>  modem-manager is now available
Jun 27 16:30:35 C2D-desktop modem-manager: Loaded plugin Option High-Speed
Jun 27 16:30:35 C2D-desktop modem-manager: Loaded plugin Sierra
Jun 27 16:30:35 C2D-desktop modem-manager: Loaded plugin Generic
Jun 27 16:30:35 C2D-desktop modem-manager: Loaded plugin Huawei
Jun 27 16:30:35 C2D-desktop modem-manager: Loaded plugin Nokia
Jun 27 16:30:35 C2D-desktop modem-manager: Loaded plugin AnyData
Jun 27 16:30:35 C2D-desktop modem-manager: Loaded plugin ZTE
Jun 27 16:30:35 C2D-desktop modem-manager: Loaded plugin Novatel
Jun 27 16:30:35 C2D-desktop modem-manager: Loaded plugin Gobi
Jun 27 16:30:35 C2D-desktop modem-manager: Loaded plugin Longcheer
Jun 27 16:30:35 C2D-desktop modem-manager: Loaded plugin MotoC
Jun 27 16:30:35 C2D-desktop modem-manager: Loaded plugin Option
Jun 27 16:30:35 C2D-desktop modem-manager: Loaded plugin Ericsson MBM
Jun 27 16:30:35 C2D-desktop modem-manager: (ttyS1) opening serial device...
Jun 27 16:30:35 C2D-desktop modem-manager: (ttyS1): probe requested by plugin 'Generic'
Jun 27 16:30:35 C2D-desktop modem-manager: (ttyS2) opening serial device...
Jun 27 16:30:35 C2D-desktop NetworkManager: <info>  modem manager disappeared
Jun 27 16:30:35 C2D-desktop NetworkManager: <info>  Trying to start the modem-manager...
```

These are the repeated lines in kern.log and syslog

```
Jun 27 16:31:17 C2D-desktop NetworkManager: <info>  modem-manager is now available
Jun 27 16:31:17 C2D-desktop modem-manager: Loaded plugin Option High-Speed
Jun 27 16:31:17 C2D-desktop modem-manager: Loaded plugin Sierra
Jun 27 16:31:17 C2D-desktop modem-manager: Loaded plugin Generic
Jun 27 16:31:17 C2D-desktop modem-manager: Loaded plugin Huawei
Jun 27 16:31:17 C2D-desktop modem-manager: Loaded plugin Nokia
Jun 27 16:31:17 C2D-desktop modem-manager: Loaded plugin AnyData
Jun 27 16:31:17 C2D-desktop modem-manager: Loaded plugin ZTE
Jun 27 16:31:17 C2D-desktop modem-manager: Loaded plugin Novatel
Jun 27 16:31:17 C2D-desktop modem-manager: Loaded plugin Gobi
Jun 27 16:31:17 C2D-desktop modem-manager: Loaded plugin Longcheer
Jun 27 16:31:17 C2D-desktop modem-manager: Loaded plugin MotoC
Jun 27 16:31:17 C2D-desktop modem-manager: Loaded plugin Option
Jun 27 16:31:17 C2D-desktop modem-manager: Loaded plugin Ericsson MBM
Jun 27 16:31:17 C2D-desktop modem-manager: (ttyS1) opening serial device...
Jun 27 16:31:17 C2D-desktop modem-manager: (ttyS1): probe requested by plugin 'Generic'
Jun 27 16:31:17 C2D-desktop modem-manager: (ttyS2) opening serial device...
Jun 27 16:31:17 C2D-desktop kernel: [  577.100411] BUG: unable to handle kernel paging request at ffffff817ef44030
Jun 27 16:31:17 C2D-desktop NetworkManager: <info>  modem manager disappeared
Jun 27 16:31:17 C2D-desktop NetworkManager: <info>  Trying to start the modem-manager...
Jun 27 16:31:17 C2D-desktop kernel: [  577.100419] IP: [<ffffffff8135e3a9>] uart_open+0x79/0x280
Jun 27 16:31:17 C2D-desktop kernel: [  577.100429] PGD 1003067 PUD 0
Jun 27 16:31:17 C2D-desktop kernel: [  577.100433] Oops: 0000 [#4274] SMP
Jun 27 16:31:17 C2D-desktop kernel: [  577.100437] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/uevent
Jun 27 16:31:17 C2D-desktop kernel: [  577.100442] CPU 1
Jun 27 16:31:17 C2D-desktop kernel: [  577.100444] Modules linked in: pppoe pppox binfmt_misc vboxnetadp vboxnetflt vboxdrv snd_hda_codec_realtek vga16fb vgastate ipt_REJECT xt_limit xt_tcpudp ipt_addrtype xt_state ip6table_filter snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss ip6_tables snd_pcm snd_seq_dummy nf_nat_irc snd_seq_oss nf_conntrack_irc snd_seq_midi nf_nat_ftp nf_nat snd_rawmidi nf_conntrack_ipv4 nf_defrag_ipv4 snd_seq_midi_event nf_conntrack_ftp snd_seq nf_conntrack iptable_filter ppdev snd_timer snd_seq_device ip_tables i915 drm_kms_helper x_tables lp parport_pc asus_atk0110 snd psmouse serio_raw fbcon tileblit font bitblit softcursor parport drm i2c_algo_bit intel_agp soundcore snd_page_alloc video output e1000e
Jun 27 16:31:17 C2D-desktop kernel: [  577.100506] Pid: 13730, comm: modem-manager Tainted: G   M  D    2.6.32-22-generic #36-Ubuntu System Product Name
Jun 27 16:31:17 C2D-desktop kernel: [  577.100509] RIP: 0010:[<ffffffff8135e3a9>]  [<ffffffff8135e3a9>] uart_open+0x79/0x280
Jun 27 16:31:17 C2D-desktop kernel: [  577.100515] RSP: 0018:ffff8800248c7c28  EFLAGS: 00010202
Jun 27 16:31:17 C2D-desktop kernel: [  577.100518] RAX: 0000000000000020 RBX: 00000000000001e0 RCX: ffffff817ef44000
Jun 27 16:31:17 C2D-desktop kernel: [  577.100521] RDX: ffff88007bfe09ff RSI: 0000000000000000 RDI: ffff88007bfc0000
Jun 27 16:31:17 C2D-desktop kernel: [  577.100524] RBP: ffff8800248c7c58 R08: 0000000000000000 R09: ffff880025e60c00
Jun 27 16:31:17 C2D-desktop kernel: [  577.100527] R10: ffff88007cc43900 R11: 0000000000000002 R12: ffff88007bfc0000
Jun 27 16:31:17 C2D-desktop kernel: [  577.100530] R13: ffff880025d6dd80 R14: 0000000000000100 R15: 0000000000008982
Jun 27 16:31:17 C2D-desktop kernel: [  577.100533] FS:  00007fab6012d700(0000) GS:ffff880001c80000(0000) knlGS:0000000000000000
Jun 27 16:31:17 C2D-desktop kernel: [  577.100537] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun 27 16:31:17 C2D-desktop kernel: [  577.100540] CR2: ffffff817ef44030 CR3: 0000000025f18000 CR4: 00000000000006e0
Jun 27 16:31:17 C2D-desktop kernel: [  577.100543] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 27 16:31:17 C2D-desktop kernel: [  577.100546] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun 27 16:31:17 C2D-desktop kernel: [  577.100550] Process modem-manager (pid: 13730, threadinfo ffff8800248c6000, task ffff880037b28000)
Jun 27 16:31:17 C2D-desktop kernel: [  577.100552] Stack:
Jun 27 16:31:17 C2D-desktop kernel: [  577.100554]  ffff8800248c7c58 ffffffff813281dd ffff88007bfe0a00 0000000000400042
Jun 27 16:31:17 C2D-desktop kernel: [  577.100559] <0> ffff880025d6dd80 0000000000000100 ffff8800248c7cc8 ffffffff8132bd79
Jun 27 16:31:17 C2D-desktop kernel: [  577.100565] <0> ffff88007bfc0020 ffff88007bfdefb0 ffff880037b28000 ffff88007bfc0000
Jun 27 16:31:17 C2D-desktop kernel: [  577.100571] Call Trace:
Jun 27 16:31:17 C2D-desktop kernel: [  577.100578]  [<ffffffff813281dd>] ? check_tty_count+0x5d/0xd0
Jun 27 16:31:17 C2D-desktop kernel: [  577.100583]  [<ffffffff8132bd79>] __tty_open+0x209/0x510
Jun 27 16:31:17 C2D-desktop kernel: [  577.100587]  [<ffffffff8132c0ac>] tty_open+0x2c/0x40
Jun 27 16:31:17 C2D-desktop kernel: [  577.100593]  [<ffffffff8114666a>] chrdev_open+0x13a/0x240
Jun 27 16:31:17 C2D-desktop kernel: [  577.100598]  [<ffffffff8115e4c0>] ? mntput_no_expire+0x30/0x110
Jun 27 16:31:17 C2D-desktop kernel: [  577.100603]  [<ffffffff81146530>] ? chrdev_open+0x0/0x240
Jun 27 16:31:17 C2D-desktop kernel: [  577.100607]  [<ffffffff81140983>] __dentry_open+0x113/0x370
Jun 27 16:31:17 C2D-desktop kernel: [  577.100612]  [<ffffffff81251b8f>] ? security_inode_permission+0x1f/0x30
Jun 27 16:31:17 C2D-desktop kernel: [  577.100617]  [<ffffffff8114ccff>] ? inode_permission+0xaf/0xd0
Jun 27 16:31:17 C2D-desktop kernel: [  577.100621]  [<ffffffff81140cf7>] nameidata_to_filp+0x57/0x70
Jun 27 16:31:17 C2D-desktop kernel: [  577.100625]  [<ffffffff81150f3a>] do_filp_open+0x2da/0xba0
Jun 27 16:31:17 C2D-desktop kernel: [  577.100630]  [<ffffffff813309cd>] ? n_tty_ioctl_helper+0x3d/0x1c0
Jun 27 16:31:17 C2D-desktop kernel: [  577.100635]  [<ffffffff812b6f96>] ? rb_erase+0xd6/0x160
Jun 27 16:31:17 C2D-desktop kernel: [  577.100641]  [<ffffffff81058620>] ? finish_task_switch+0x50/0xe0
Jun 27 16:31:17 C2D-desktop kernel: [  577.100646]  [<ffffffff8115c9ea>] ? alloc_fd+0x10a/0x150
Jun 27 16:31:17 C2D-desktop kernel: [  577.100650]  [<ffffffff811406f9>] do_sys_open+0x69/0x170
Jun 27 16:31:17 C2D-desktop kernel: [  577.100653]  [<ffffffff81140840>] sys_open+0x20/0x30
Jun 27 16:31:17 C2D-desktop kernel: [  577.100659]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
Jun 27 16:31:17 C2D-desktop kernel: [  577.100662] Code: ff ff 7c 16 48 8b 5d e0 4c 8b 65 e8 4c 8b 6d f0 4c 8b 75 f8 c9 c3 0f 1f 40 00 48 63 db 48 89 d8 48 c1 e3 08 48 c1 e0 04 48 29 c3 <48> 03 59 30 4c 8d 73 70 4c 89 f7 e8 77 13 1e 00 85 c0 0f 85 cf
Jun 27 16:31:17 C2D-desktop kernel: [  577.100707] RIP  [<ffffffff8135e3a9>] uart_open+0x79/0x280
Jun 27 16:31:17 C2D-desktop kernel: [  577.100711]  RSP <ffff8800248c7c28>
Jun 27 16:31:17 C2D-desktop kernel: [  577.100714] CR2: ffffff817ef44030
Jun 27 16:31:17 C2D-desktop kernel: [  577.100717] ---[ end trace 237f4eb503ccad64 ]---
Jun 27 16:31:17 C2D-desktop NetworkManager: <info>  modem-manager is now available
```

These lines are repeatedly appearing in messages

```
Jun 27 18:28:34 C2D-desktop kernel: [  474.520282] Process modem-manager (pid: 11423, threadinfo ffff8800291ae000, task ffff880043cc16f0)
Jun 27 18:28:34 C2D-desktop kernel: [  474.520284] Stack:
Jun 27 18:28:34 C2D-desktop kernel: [  474.520286]  ffff8800291afc58 ffffffff813281dd ffff88007bfe0a00 0000000000400042
Jun 27 18:28:34 C2D-desktop kernel: [  474.520292] <0> ffff8800565e2180 0000000000000100 ffff8800291afcc8 ffffffff8132bd79
Jun 27 18:28:34 C2D-desktop kernel: [  474.520297] <0> ffff88007bfc0020 ffff88007bfdefb0 ffff880043cc16f0 ffff88007bfc0000
Jun 27 18:28:34 C2D-desktop kernel: [  474.520303] Call Trace:
Jun 27 18:28:34 C2D-desktop kernel: [  474.520311]  [<ffffffff813281dd>] ? check_tty_count+0x5d/0xd0
Jun 27 18:28:34 C2D-desktop kernel: [  474.520315]  [<ffffffff8132bd79>] __tty_open+0x209/0x510
Jun 27 18:28:34 C2D-desktop kernel: [  474.520319]  [<ffffffff8132c0ac>] tty_open+0x2c/0x40
Jun 27 18:28:34 C2D-desktop kernel: [  474.520325]  [<ffffffff8114666a>] chrdev_open+0x13a/0x240
Jun 27 18:28:34 C2D-desktop kernel: [  474.520330]  [<ffffffff8115e4c0>] ? mntput_no_expire+0x30/0x110
Jun 27 18:28:34 C2D-desktop kernel: [  474.520334]  [<ffffffff81146530>] ? chrdev_open+0x0/0x240
Jun 27 18:28:34 C2D-desktop kernel: [  474.520339]  [<ffffffff81140983>] __dentry_open+0x113/0x370
Jun 27 18:28:34 C2D-desktop kernel: [  474.520344]  [<ffffffff81251b8f>] ? security_inode_permission+0x1f/0x30
Jun 27 18:28:34 C2D-desktop kernel: [  474.520348]  [<ffffffff8114ccff>] ? inode_permission+0xaf/0xd0
Jun 27 18:28:34 C2D-desktop kernel: [  474.520352]  [<ffffffff81140cf7>] nameidata_to_filp+0x57/0x70
Jun 27 18:28:34 C2D-desktop kernel: [  474.520357]  [<ffffffff81150f3a>] do_filp_open+0x2da/0xba0
Jun 27 18:28:34 C2D-desktop kernel: [  474.520361]  [<ffffffff813309cd>] ? n_tty_ioctl_helper+0x3d/0x1c0
Jun 27 18:28:34 C2D-desktop kernel: [  474.520367]  [<ffffffff812b6f96>] ? rb_erase+0xd6/0x160
Jun 27 18:28:34 C2D-desktop kernel: [  474.520372]  [<ffffffff81058620>] ? finish_task_switch+0x50/0xe0
Jun 27 18:28:34 C2D-desktop kernel: [  474.520377]  [<ffffffff8115c9ea>] ? alloc_fd+0x10a/0x150
Jun 27 18:28:34 C2D-desktop kernel: [  474.520381]  [<ffffffff811406f9>] do_sys_open+0x69/0x170
Jun 27 18:28:34 C2D-desktop kernel: [  474.520385]  [<ffffffff81140840>] sys_open+0x20/0x30
Jun 27 18:28:34 C2D-desktop kernel: [  474.520391]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
Jun 27 18:28:34 C2D-desktop kernel: [  474.520393] Code: ff ff 7c 16 48 8b 5d e0 4c 8b 65 e8 4c 8b 6d f0 4c 8b 75 f8 c9 c3 0f 1f 40 00 48 63 db 48 89 d8 48 c1 e3 08 48 c1 e0 04 48 29 c3 <48> 03 59 30 4c 8d 73 70 4c 89 f7 e8 77 13 1e 00 85 c0 0f 85 cf
Jun 27 18:28:34 C2D-desktop kernel: [  474.520438] RIP  [<ffffffff8135e3a9>] uart_open+0x79/0x280
Jun 27 18:28:34 C2D-desktop kernel: [  474.520443]  RSP <ffff8800291afc28>
Jun 27 18:28:34 C2D-desktop kernel: [  474.520445] CR2: ffffff817ef44030
Jun 27 18:28:34 C2D-desktop kernel: [  474.520448] ---[ end trace 66bb0678753fc5a3 ]---
Jun 27 18:28:34 C2D-desktop kernel: [  474.640269] BUG: unable to handle kernel paging request at ffffff817ef44030
Jun 27 18:28:34 C2D-desktop kernel: [  474.640276] IP: [<ffffffff8135e3a9>] uart_open+0x79/0x280
Jun 27 18:28:34 C2D-desktop kernel: [  474.640286] PGD 1003067 PUD 0
Jun 27 18:28:34 C2D-desktop kernel: [  474.640290] Oops: 0000 [#3352] SMP
Jun 27 18:28:34 C2D-desktop kernel: [  474.640293] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/uevent
Jun 27 18:28:34 C2D-desktop kernel: [  474.640297] CPU 0
Jun 27 18:28:34 C2D-desktop kernel: [  474.640299] Modules linked in: pppoe pppox binfmt_misc vboxnetadp vboxnetflt vboxdrv snd_hda_codec_realtek vga16fb vgastate ipt_REJECT xt_limit xt_tcpudp ipt_addrtype xt_state snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss ip6table_filter snd_pcm ip6_tables nf_nat_irc nf_conntrack_irc snd_seq_dummy nf_nat_ftp nf_nat snd_seq_oss nf_conntrack_ipv4 nf_defrag_ipv4 snd_seq_midi nf_conntrack_ftp snd_rawmidi nf_conntrack snd_seq_midi_event iptable_filter snd_seq ip_tables snd_timer snd_seq_device x_tables i915 drm_kms_helper ppdev snd lp drm i2c_algo_bit video parport_pc psmouse serio_raw asus_atk0110 soundcore snd_page_alloc intel_agp fbcon tileblit font bitblit softcursor output parport e1000e
Jun 27 18:28:34 C2D-desktop kernel: [  474.640353] Pid: 11425, comm: modem-manager Tainted: G      D    2.6.32-22-generic #36-Ubuntu System Product Name
Jun 27 18:28:34 C2D-desktop kernel: [  474.640356] RIP: 0010:[<ffffffff8135e3a9>]  [<ffffffff8135e3a9>] uart_open+0x79/0x280
Jun 27 18:28:34 C2D-desktop kernel: [  474.640360] RSP: 0018:ffff88002916fc28  EFLAGS: 00010202
Jun 27 18:28:34 C2D-desktop kernel: [  474.640363] RAX: 0000000000000020 RBX: 00000000000001e0 RCX: ffffff817ef44000
Jun 27 18:28:34 C2D-desktop kernel: [  474.640365] RDX: ffff88007bfe09ff RSI: 0000000000000000 RDI: ffff88007bfc0000
Jun 27 18:28:34 C2D-desktop kernel: [  474.640368] RBP: ffff88002916fc58 R08: 0000000000000000 R09: ffff88002d181300
Jun 27 18:28:34 C2D-desktop kernel: [  474.640371] R10: ffff88007cc43900 R11: 0000000000000002 R12: ffff88007bfc0000
Jun 27 18:28:34 C2D-desktop kernel: [  474.640373] R13: ffff88003ff06180 R14: 0000000000000100 R15: 0000000000008982
Jun 27 18:28:34 C2D-desktop kernel: [  474.640376] FS:  00007fc070297700(0000) GS:ffff880001c00000(0000) knlGS:0000000000000000
Jun 27 18:28:34 C2D-desktop kernel: [  474.640379] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun 27 18:28:34 C2D-desktop kernel: [  474.640382] CR2: ffffff817ef44030 CR3: 0000000043cdd000 CR4: 00000000000006f0
Jun 27 18:28:34 C2D-desktop kernel: [  474.640384] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 27 18:28:34 C2D-desktop kernel: [  474.640387] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
```

I'm having serious space problems due to this. Please help.

---

### Post by dino99 on 2010-06-27
logrotate might help you, see into synaptic

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

[http://manpages.ubuntu.com/manpages/jaunty/man8/logrotate.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/logrotate.8.html)

you can make room with bleachbit (set your prefs carefully, and use it as admin)

---

### Post by shafin on 2010-06-27
> **dino99 said:**
> logrotate might help you, see into synaptic

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

[http://manpages.ubuntu.com/manpages/jaunty/man8/logrotate.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/logrotate.8.html)

you can make room with bleachbit (set your prefs carefully, and use it as admin)
Thanks for your response. I'm looking for a solution that stops modem manager generating so many log entries. Surely it's not supposed to do so. logrotate and blechbit would certainly help, but a solution that stops the root of the problem is preferable. can you suggest one?

---

### Post by jordilin on 2010-06-27
If you are already aware of that and your system is running fine, you could write a cronjob to do some log maintenance, like backing them up and emptying them afterwards doing a cat dev/null into them. Take into account that every time you start up your system a huge amount of log information is being written as the kernel loads system modules.

---

### Post by dino99 on 2010-06-27
about modemmanager:

**** Provides a D-Bus interface to communicate with mobile broadband (GSM,
CDMA, UMTS, ...) cards. Implements a loadable plugin interface to add
work-arounds for non standard devices. Also provides patches to use
networkmanager (and the applet) with modem manager. ***

Do you really need it ? if not, remove/purge it into synaptic, otherwise:

sudo dpkg-reconfigure modemmanager

---

### Post by jordilin on 2010-06-27
I've got this modemmanager package installed as well, and I see this log traces in the daemon.log. I would write myself a cron job or a script to monitor that. It would depen of course on the hard disk space available.

---

### Post by shafin on 2010-06-27
I have made a mobile broadband connection in network manager even though I did not have a mobile broadband modem. Deleting that connection seems to do the work. However, it sure is a bug in modem  manager.

Thanks for your replies.

---

### Post by dino99 on 2010-06-27
so report on launchpad: into a console, run ubuntu-bug modemmanager

---

