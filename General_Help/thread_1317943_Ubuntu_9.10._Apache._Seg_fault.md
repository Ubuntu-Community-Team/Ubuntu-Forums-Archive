---
title: "Ubuntu 9.10. Apache. Seg fault"
date: 2009-11-07
forum: General Help
---

### Post by wDevil on 2009-11-07
Apache installed from apt repos. All settings - default. Nothing changed after installation
$ uname -a
Linux klepa-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                                        Segmentation fault
Segmentation fault

$ tailf /var/log/syslog

Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158366] general protection fault: 0000 [#31] SMP 
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158372] last sysfs file: /sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0A:00/power_supply/BAT0/energy_full
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158375] CPU 1 
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158378] Modules linked in: binfmt_misc ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi arc4 snd_rawmidi snd_seq_midi_event ecb snd_seq ath9k snd_timer snd_seq_device mac80211 iptable_filter snd ath psmouse ip_tables soundcore uvcvideo nvidia(P) videodev v4l1_compat serio_raw shpchp asus_laptop x_tables v4l2_compat_ioctl32 i2c_nforce2 cfg80211 lp parport led_class snd_page_alloc usbhid r8169 mii video output
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158415] Pid: 4594, comm: pidof Tainted: P      D    2.6.31-14-generic #48-Ubuntu K50IN                
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158418] RIP: 0010:[<ffffffff810fa7ba>]  [<ffffffff810fa7ba>] find_vma+0x3a/0x90
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158427] RSP: 0018:ffff88007c09bcd8  EFLAGS: 00010202
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158429] RAX: ffff880068d7bd10 RBX: 00007fffc754d000 RCX: ffff880068d7bd10
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158432] RDX: 3781e7b64f12f189 RSI: 00007fffc754d000 RDI: ffff8800378430c0
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158434] RBP: ffff88007c09bcd8 R08: 0000000000000002 R09: ffff88007c09be08
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158436] R10: 0000000000000001 R11: 0000000000000000 R12: ffff880037cc0000
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158439] R13: ffff8800415a3000 R14: 0000000000000000 R15: ffff8800378430c0
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158442] FS:  00007f51d67806f0(0000) GS:ffff880001a12000(0000) knlGS:0000000000000000
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158444] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158446] CR2: 00007f51d679a000 CR3: 000000007c561000 CR4: 00000000000406e0
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158449] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158451] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158454] Process pidof (pid: 4594, threadinfo ffff88007c09a000, task ffff8800411b0000)
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158456] Stack:
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158457]  ffff88007c09bd08 ffffffff810fad16 0000000000000001 00007fffc754db66
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158461] <0> ffff880037cc0000 ffff8800415a3000 ffff88007c09bd88 ffffffff810f8c71
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158466] <0> ffffffff00000000 ffff880000012a50 0000000000000010 00000000005292f0
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158470] Call Trace:
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158474]  [<ffffffff810fad16>] find_extend_vma+0x26/0x90
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158478]  [<ffffffff810f8c71>] __get_user_pages+0x81/0x480
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158481]  [<ffffffff810f909f>] get_user_pages+0x2f/0x40
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158484]  [<ffffffff810f91c7>] access_process_vm+0x117/0x200
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158490]  [<ffffffff815293a9>] ? _spin_lock+0x9/0x10
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158495]  [<ffffffff81174368>] proc_pid_cmdline+0x68/0x120
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158499]  [<ffffffff8110cea2>] ? alloc_pages_current+0x82/0xd0
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158503]  [<ffffffff8117545d>] proc_info_read+0xad/0xf0
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158507]  [<ffffffff8111f215>] vfs_read+0xb5/0x1a0
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158510]  [<ffffffff8111f81c>] sys_read+0x4c/0x80
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158515]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158517] Code: c0 74 06 48 39 70 10 77 48 48 8b 57 08 48 85 d2 74 5f 31 c0 eb 15 0f 1f 00 48 3b 72 d8 73 42 48 8b 52 10 48 89 c8 48 85 d2 74 13 <48> 3b 72 e0 48 8d 4a d0 72 e4 48 8b 52 08 48 85 d2 75 ed 48 85 
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158551] RIP  [<ffffffff810fa7ba>] find_vma+0x3a/0x90
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158554]  RSP <ffff88007c09bcd8>
Nov  7 17:21:44 klepa-laptop kernel: [ 6296.158558] ---[ end trace 9ef8b52f87bd9f8c ]---

---

