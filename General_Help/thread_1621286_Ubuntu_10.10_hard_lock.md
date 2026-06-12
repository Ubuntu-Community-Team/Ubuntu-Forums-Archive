---
title: "Ubuntu 10.10 hard lock"
date: 2010-11-14
forum: General Help
---

### Post by RoboJ1M on 2010-11-14
Hi,

I doubt I can do anything about this but I woke up this morning to find my htpc hard locked, nothing to do but hit the reset button. :(

Thought I would post the barf in the /var/log/messages in case it meant anything.

I just assuming 0804 is when it crashed as that's when the log stopped, and it's full of some sort of trace dumps.

lshw at the end.

```
Nov 14 08:04:00 livingroom kernel: [29290.185138] *pde = 6f806067 
Nov 14 08:04:00 livingroom kernel: [29290.185145] Modules linked in: parport_pc ppdev snd_hda_codec_hdmi binfmt_misc snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi radeon snd_seq_midi_event snd_seq snd_timer snd_seq_device ttm drm_kms_helper snd joydev drm serio_raw agpgart i2c_algo_bit i2c_piix4 soundcore snd_page_alloc k10temp lp shpchp parport r8169 firewire_ohci usbhid hid mii ahci firewire_core crc_itu_t libahci pata_atiixp
Nov 14 08:04:00 livingroom kernel: [29290.185162] 
Nov 14 08:04:00 livingroom kernel: [29290.185164] Pid: 2561, comm: Xorg Not tainted 2.6.35-22-generic #35-Ubuntu GA-MA785GMT-UD2H/GA-MA785GMT-UD2H
Nov 14 08:04:00 livingroom kernel: [29290.185166] EIP: 0060:[<c0270987>] EFLAGS: 00213246 CPU: 0
Nov 14 08:04:00 livingroom kernel: [29290.185168] EIP is at sysfs_find_dirent+0x27/0x50
Nov 14 08:04:00 livingroom kernel: [29290.185169] EAX: ffffffff EBX: 00000000 ECX: f3667944 EDX: f3667944
Nov 14 08:04:00 livingroom kernel: [29290.185171] ESI: 00002222 EDI: f3667944 EBP: f345faf0 ESP: f345fae4
Nov 14 08:04:00 livingroom kernel: [29290.185172]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Nov 14 08:04:00 livingroom kernel: [29290.185176]  f366781c 00000000 f3667944 f345fb0c c026f628 f366781c 00000000 f5d2b980
Nov 14 08:04:00 livingroom kernel: [29290.185179] <0> f3667800 f3d35ab0 f345fb14 c0270174 f345fb1c c03fd644 f345fb40 c039b446
Nov 14 08:04:00 livingroom kernel: [29290.185182] <0> c03d7329 00000001 c03db430 00000000 00000007 00000080 f5d2b980 f345fe48
Nov 14 08:04:00 livingroom kernel: [29290.185189]  [<c026f628>] ? sysfs_hash_and_remove+0x38/0x80
Nov 14 08:04:00 livingroom kernel: [29290.185191]  [<c0270174>] ? sysfs_remove_file+0x14/0x20
Nov 14 08:04:00 livingroom kernel: [29290.185195]  [<c03fd644>] ? device_remove_file+0x14/0x20
Nov 14 08:04:00 livingroom kernel: [29290.185198]  [<c039b446>] ? acpi_device_unregister+0x9e/0xc8
Nov 14 08:04:00 livingroom kernel: [29290.185201]  [<c03d7329>] ? tty_poll+0x69/0x80
Nov 14 08:04:00 livingroom kernel: [29290.185203]  [<c03db430>] ? n_tty_poll+0x0/0x190
Nov 14 08:04:00 livingroom kernel: [29290.185206]  [<c022809b>] ? do_select+0x37b/0x670
Nov 14 08:04:00 livingroom kernel: [29290.185208]  [<c0175802>] ? tick_dev_program_event+0x42/0x150
Nov 14 08:04:00 livingroom kernel: [29290.185210]  [<c0228390>] ? __pollwait+0x0/0xe0
Nov 14 08:04:00 livingroom kernel: [29290.185212]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185213]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185215]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185216]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185218]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185219]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185221]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185222]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185223]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185225]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185226]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185228]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185230]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185231]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185233]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185234]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185235]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185237]  [<c0228470>] ? pollwake+0x0/0x60
Nov 14 08:04:00 livingroom kernel: [29290.185239]  [<c0228a20>] ? core_sys_select+0x140/0x240
Nov 14 08:04:00 livingroom kernel: [29290.185241]  [<c016a739>] ? hrtimer_try_to_cancel+0x39/0xb0
Nov 14 08:04:00 livingroom kernel: [29290.185243]  [<c014f710>] ? do_setitimer+0x160/0x1f0
Nov 14 08:04:00 livingroom kernel: [29290.185245]  [<c0228d21>] ? sys_select+0x31/0xc0
Nov 14 08:04:00 livingroom kernel: [29290.185247]  [<c0164af0>] ? sys_clock_gettime+0x50/0xa0
Nov 14 08:04:00 livingroom kernel: [29290.185250]  [<c05c9114>] ? syscall_call+0x7/0xb
Nov 14 08:04:00 livingroom kernel: [29290.185273] ---[ end trace a3f33662725058a5 ]---
Nov 14 08:04:00 livingroom kernel: [29290.232045] bad magic number for tty struct (4:8) in tty_fasync
Nov 14 08:04:00 livingroom kernel: [29290.260312] *pde = 00000000 
Nov 14 08:04:00 livingroom kernel: [29290.260318] Modules linked in: parport_pc ppdev snd_hda_codec_hdmi binfmt_misc snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi radeon snd_seq_midi_event snd_seq snd_timer snd_seq_device ttm drm_kms_helper snd joydev drm serio_raw agpgart i2c_algo_bit i2c_piix4 soundcore snd_page_alloc k10temp lp shpchp parport r8169 firewire_ohci usbhid hid mii ahci firewire_core crc_itu_t libahci pata_atiixp
Nov 14 08:04:00 livingroom kernel: [29290.260335] 
Nov 14 08:04:00 livingroom kernel: [29290.260338] Pid: 4353, comm: mplayer Tainted: G      D     2.6.35-22-generic #35-Ubuntu GA-MA785GMT-UD2H/GA-MA785GMT-UD2H
Nov 14 08:04:00 livingroom kernel: [29290.260340] EIP: 0060:[<c0139c44>] EFLAGS: 00010086 CPU: 0
Nov 14 08:04:00 livingroom kernel: [29290.260342] EIP is at task_rq_lock+0x34/0x80
Nov 14 08:04:00 livingroom kernel: [29290.260343] EAX: 00001000 EBX: c08c3700 ECX: 00000086 EDX: f3609df0
Nov 14 08:04:00 livingroom kernel: [29290.260344] ESI: f344ef64 EDI: 00000000 EBP: f3609dd0 ESP: f3609dc0
Nov 14 08:04:00 livingroom kernel: [29290.260346]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Nov 14 08:04:00 livingroom kernel: [29290.260349]  f3609df0 00000001 f344ef64 00000000 f3609e00 c0142998 00000000 c165a840
Nov 14 08:04:00 livingroom kernel: [29290.260353] <0> 00000000 00000000 00000000 20080000 00000086 f344ef64 00000000 00000000
Nov 14 08:04:00 livingroom kernel: [29290.260356] <0> f3609e08 c0142d30 f3609e30 c02284c4 00000000 00000000 f344ef64 c0142d20
Nov 14 08:04:00 livingroom kernel: [29290.260363]  [<c0142998>] ? try_to_wake_up+0x28/0x3b0
Nov 14 08:04:00 livingroom kernel: [29290.260365]  [<c0142d30>] ? default_wake_function+0x10/0x20
Nov 14 08:04:00 livingroom kernel: [29290.260367]  [<c02284c4>] ? pollwake+0x54/0x60
Nov 14 08:04:00 livingroom kernel: [29290.260369]  [<c0142d20>] ? default_wake_function+0x0/0x20
Nov 14 08:04:00 livingroom kernel: [29290.260371]  [<c0135498>] ? __wake_up_common+0x48/0x70
Nov 14 08:04:00 livingroom kernel: [29290.260373]  [<c013947c>] ? __wake_up+0x3c/0x60
Nov 14 08:04:00 livingroom kernel: [29290.260376]  [<c04e9152>] ? sock_def_wakeup+0x32/0x40
Nov 14 08:04:00 livingroom kernel: [29290.260379]  [<c056f839>] ? unix_release_sock+0x1d9/0x220
Nov 14 08:04:00 livingroom kernel: [29290.260381]  [<c056f8a3>] ? unix_release+0x23/0x30
Nov 14 08:04:00 livingroom kernel: [29290.260383]  [<c04e5a90>] ? sock_release+0x20/0x80
Nov 14 08:04:00 livingroom kernel: [29290.260384]  [<c04e5b07>] ? sock_close+0x17/0x30
Nov 14 08:04:00 livingroom kernel: [29290.260387]  [<c0219e84>] ? __fput+0xe4/0x1e0
Nov 14 08:04:00 livingroom kernel: [29290.260389]  [<c0219f9d>] ? fput+0x1d/0x30
Nov 14 08:04:00 livingroom kernel: [29290.260391]  [<c021691c>] ? filp_close+0x4c/0x80
Nov 14 08:04:00 livingroom kernel: [29290.260393]  [<c014cc9b>] ? put_files_struct+0x6b/0xb0
Nov 14 08:04:00 livingroom kernel: [29290.260395]  [<c014cd28>] ? exit_files+0x48/0x60
Nov 14 08:04:00 livingroom kernel: [29290.260396]  [<c014eff4>] ? do_exit+0x134/0x340
Nov 14 08:04:00 livingroom kernel: [29290.260398]  [<c0218768>] ? vfs_write+0x128/0x190
Nov 14 08:04:00 livingroom kernel: [29290.260400]  [<c014f23e>] ? do_group_exit+0x3e/0xa0
Nov 14 08:04:00 livingroom kernel: [29290.260402]  [<c014f2b8>] ? sys_exit_group+0x18/0x20
Nov 14 08:04:00 livingroom kernel: [29290.260404]  [<c05c9114>] ? syscall_call+0x7/0xb
Nov 14 08:04:00 livingroom kernel: [29290.260427] ---[ end trace a3f33662725058a6 ]---
Nov 14 08:04:00 livingroom kernel: [29290.267924] *pde = 6e1c5067 
Nov 14 08:04:00 livingroom kernel: [29290.267930] Modules linked in: parport_pc ppdev snd_hda_codec_hdmi binfmt_misc snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi radeon snd_seq_midi_event snd_seq snd_timer snd_seq_device ttm drm_kms_helper snd joydev drm serio_raw agpgart i2c_algo_bit i2c_piix4 soundcore snd_page_alloc k10temp lp shpchp parport r8169 firewire_ohci usbhid hid mii ahci firewire_core crc_itu_t libahci pata_atiixp
Nov 14 08:04:00 livingroom kernel: [29290.267946] 
Nov 14 08:04:00 livingroom kernel: [29290.267949] Pid: 2749, comm: docky Tainted: G      D     2.6.35-22-generic #35-Ubuntu GA-MA785GMT-UD2H/GA-MA785GMT-UD2H
Nov 14 08:04:00 livingroom kernel: [29290.267951] EIP: 0060:[<c0139c41>] EFLAGS: 00210086 CPU: 1
Nov 14 08:04:00 livingroom kernel: [29290.267953] EIP is at task_rq_lock+0x31/0x80
Nov 14 08:04:00 livingroom kernel: [29290.267954] EAX: f6abfd2c EBX: c08c3700 ECX: 00200086 EDX: f6abfd2c
Nov 14 08:04:00 livingroom kernel: [29290.267956] ESI: 00000000 EDI: 00000000 EBP: f6abfd0c ESP: f6abfcfc
Nov 14 08:04:00 livingroom kernel: [29290.267957]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Nov 14 08:04:00 livingroom kernel: [29290.267961]  f6abfd2c 00000001 00000000 00000000 f6abfd3c c0142998 f5cc8c00 f6abfd48
Nov 14 08:04:00 livingroom kernel: [29290.267964] <0> 00200246 00000001 00000001 c04ece5e 00200086 00000000 000000c1 00000000
Nov 14 08:04:00 livingroom kernel: [29290.267967] <0> f6abfd44 c0142d30 f6abfd6c c02284c4 000000c1 00000000 00000000 c0142d20
Nov 14 08:04:00 livingroom kernel: [29290.267974]  [<c0142998>] ? try_to_wake_up+0x28/0x3b0
Nov 14 08:04:00 livingroom kernel: [29290.267977]  [<c04ece5e>] ? __alloc_skb+0x2e/0x100
Nov 14 08:04:00 livingroom kernel: [29290.267978]  [<c0142d30>] ? default_wake_function+0x10/0x20
Nov 14 08:04:00 livingroom kernel: [29290.267981]  [<c02284c4>] ? pollwake+0x54/0x60
Nov 14 08:04:00 livingroom kernel: [29290.267982]  [<c0142d20>] ? default_wake_function+0x0/0x20
Nov 14 08:04:00 livingroom kernel: [29290.267984]  [<c0135498>] ? __wake_up_common+0x48/0x70
Nov 14 08:04:00 livingroom kernel: [29290.267987]  [<c0139403>] ? __wake_up_sync_key+0x43/0x60
Nov 14 08:04:00 livingroom kernel: [29290.267989]  [<c04ea848>] ? sock_def_readable+0x38/0x70
Nov 14 08:04:00 livingroom kernel: [29290.267992]  [<c056fe90>] ? unix_stream_sendmsg+0x1d0/0x370
Nov 14 08:04:00 livingroom kernel: [29290.267994]  [<c04e630b>] ? sock_aio_write+0x12b/0x140
Nov 14 08:04:00 livingroom kernel: [29290.267997]  [<c021836d>] ? do_sync_readv_writev+0x9d/0xe0
Nov 14 08:04:00 livingroom kernel: [29290.268000]  [<c032e636>] ? apparmor_file_permission+0x16/0x20
Nov 14 08:04:00 livingroom kernel: [29290.268003]  [<c0302a84>] ? security_file_permission+0x14/0x20
Nov 14 08:04:00 livingroom kernel: [29290.268005]  [<c02185d2>] ? rw_verify_area+0x62/0xd0
Nov 14 08:04:00 livingroom kernel: [29290.268007]  [<c02191f8>] ? rw_copy_check_uvector+0x78/0xf0
Nov 14 08:04:00 livingroom kernel: [29290.268009]  [<c0219311>] ? do_readv_writev+0xa1/0x1b0
Nov 14 08:04:00 livingroom kernel: [29290.268011]  [<c04e61e0>] ? sock_aio_write+0x0/0x140
Nov 14 08:04:00 livingroom kernel: [29290.268013]  [<c016ffbd>] ? ktime_get_ts+0xed/0x120
Nov 14 08:04:00 livingroom kernel: [29290.268015]  [<c016fb56>] ? getnstimeofday+0x56/0x120
Nov 14 08:04:00 livingroom kernel: [29290.268017]  [<c0219465>] ? vfs_writev+0x45/0x60
Nov 14 08:04:00 livingroom kernel: [29290.268019]  [<c0219572>] ? sys_writev+0x42/0xa0
Nov 14 08:04:00 livingroom kernel: [29290.268021]  [<c05c9114>] ? syscall_call+0x7/0xb
Nov 14 08:04:00 livingroom kernel: [29290.268045] ---[ end trace a3f33662725058a7 ]---
Nov 14 08:04:01 livingroom kernel: [29291.256935] *pde = 00000000 
Nov 14 08:04:01 livingroom kernel: [29291.256955] Modules linked in: parport_pc ppdev snd_hda_codec_hdmi binfmt_misc snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi radeon snd_seq_midi_event snd_seq snd_timer snd_seq_device ttm drm_kms_helper snd joydev drm serio_raw agpgart i2c_algo_bit i2c_piix4 soundcore snd_page_alloc k10temp lp shpchp parport r8169 firewire_ohci usbhid hid mii ahci firewire_core crc_itu_t libahci pata_atiixp
Nov 14 08:04:01 livingroom kernel: [29291.257013] 
Nov 14 08:04:01 livingroom kernel: [29291.257021] Pid: 2802, comm: indicator-apple Tainted: G      D     2.6.35-22-generic #35-Ubuntu GA-MA785GMT-UD2H/GA-MA785GMT-UD2H
Nov 14 08:04:01 livingroom kernel: [29291.257029] EIP: 0060:[<c0139c47>] EFLAGS: 00010086 CPU: 0
Nov 14 08:04:01 livingroom kernel: [29291.257036] EIP is at task_rq_lock+0x37/0x80
Nov 14 08:04:01 livingroom kernel: [29291.257041] EAX: 7345e824 EBX: c08c3700 ECX: 00000086 EDX: f36f7d2c
Nov 14 08:04:01 livingroom kernel: [29291.257046] ESI: c0108a28 EDI: 00000000 EBP: f36f7d0c ESP: f36f7cfc
Nov 14 08:04:01 livingroom kernel: [29291.257051]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Nov 14 08:04:01 livingroom kernel: [29291.257064]  f36f7d2c 00000001 c0108a28 00000000 f36f7d3c c0142998 f4b87480 f36f7d48
Nov 14 08:04:01 livingroom kernel: [29291.257076] <0> 00000246 00000000 00000001 c04ece5e 00000086 c0108a28 000000c1 00000000
Nov 14 08:04:01 livingroom kernel: [29291.257088] <0> f36f7d44 c0142d30 f36f7d6c c02284c4 000000c1 00000000 c0108a28 c0142d20
Nov 14 08:04:01 livingroom kernel: [29291.257111]  [<c0108a28>] ? sched_clock+0x8/0x10
Nov 14 08:04:01 livingroom kernel: [29291.257119]  [<c0142998>] ? try_to_wake_up+0x28/0x3b0
Nov 14 08:04:01 livingroom kernel: [29291.257127]  [<c04ece5e>] ? __alloc_skb+0x2e/0x100
Nov 14 08:04:01 livingroom kernel: [29291.257134]  [<c0108a28>] ? sched_clock+0x8/0x10
Nov 14 08:04:01 livingroom kernel: [29291.257140]  [<c0142d30>] ? default_wake_function+0x10/0x20
Nov 14 08:04:01 livingroom kernel: [29291.257147]  [<c02284c4>] ? pollwake+0x54/0x60
Nov 14 08:04:01 livingroom kernel: [29291.257154]  [<c0108a28>] ? sched_clock+0x8/0x10
Nov 14 08:04:01 livingroom kernel: [29291.257161]  [<c0142d20>] ? default_wake_function+0x0/0x20
Nov 14 08:04:01 livingroom kernel: [29291.257168]  [<c0135498>] ? __wake_up_common+0x48/0x70
Nov 14 08:04:01 livingroom kernel: [29291.257175]  [<c0139403>] ? __wake_up_sync_key+0x43/0x60
Nov 14 08:04:01 livingroom kernel: [29291.257184]  [<c04ea848>] ? sock_def_readable+0x38/0x70
Nov 14 08:04:01 livingroom kernel: [29291.257192]  [<c056fe90>] ? unix_stream_sendmsg+0x1d0/0x370
Nov 14 08:04:01 livingroom kernel: [29291.257200]  [<c04e630b>] ? sock_aio_write+0x12b/0x140
Nov 14 08:04:01 livingroom kernel: [29291.257209]  [<c021836d>] ? do_sync_readv_writev+0x9d/0xe0
Nov 14 08:04:01 livingroom kernel: [29291.257218]  [<c032e636>] ? apparmor_file_permission+0x16/0x20
Nov 14 08:04:01 livingroom kernel: [29291.257227]  [<c0302a84>] ? security_file_permission+0x14/0x20
Nov 14 08:04:01 livingroom kernel: [29291.257235]  [<c02185d2>] ? rw_verify_area+0x62/0xd0
Nov 14 08:04:01 livingroom kernel: [29291.257242]  [<c02191f8>] ? rw_copy_check_uvector+0x78/0xf0
Nov 14 08:04:01 livingroom kernel: [29291.257250]  [<c0219311>] ? do_readv_writev+0xa1/0x1b0
Nov 14 08:04:01 livingroom kernel: [29291.257257]  [<c04e61e0>] ? sock_aio_write+0x0/0x140
Nov 14 08:04:01 livingroom kernel: [29291.257265]  [<c0219465>] ? vfs_writev+0x45/0x60
Nov 14 08:04:01 livingroom kernel: [29291.257272]  [<c0219572>] ? sys_writev+0x42/0xa0
Nov 14 08:04:01 livingroom kernel: [29291.257279]  [<c05c9114>] ? syscall_call+0x7/0xb
Nov 14 08:04:01 livingroom kernel: [29291.257364] ---[ end trace a3f33662725058a8 ]---
Nov 14 08:04:02 livingroom kernel: [29292.282328] *pde = 00000000 
Nov 14 08:04:02 livingroom kernel: [29292.282334] Modules linked in: parport_pc ppdev snd_hda_codec_hdmi binfmt_misc snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi radeon snd_seq_midi_event snd_seq snd_timer snd_seq_device ttm drm_kms_helper snd joydev drm serio_raw agpgart i2c_algo_bit i2c_piix4 soundcore snd_page_alloc k10temp lp shpchp parport r8169 firewire_ohci usbhid hid mii ahci firewire_core crc_itu_t libahci pata_atiixp
Nov 14 08:04:02 livingroom kernel: [29292.282351] 
Nov 14 08:04:02 livingroom kernel: [29292.282353] Pid: 3327, comm: firefox-bin Tainted: G      D     2.6.35-22-generic #35-Ubuntu GA-MA785GMT-UD2H/GA-MA785GMT-UD2H
Nov 14 08:04:02 livingroom kernel: [29292.282355] EIP: 0060:[<c0139c44>] EFLAGS: 00010086 CPU: 0
Nov 14 08:04:02 livingroom kernel: [29292.282357] EIP is at task_rq_lock+0x34/0x80
Nov 14 08:04:02 livingroom kernel: [29292.282359] EAX: 0026748d EBX: c08c3700 ECX: 00000086 EDX: f6733d2c
Nov 14 08:04:02 livingroom kernel: [29292.282360] ESI: c0108a28 EDI: 00000000 EBP: f6733d0c ESP: f6733cfc
Nov 14 08:04:02 livingroom kernel: [29292.282362]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Nov 14 08:04:02 livingroom kernel: [29292.282365]  f6733d2c 00000001 c0108a28 00000000 f6733d3c c0142998 00000000 f6733d48
Nov 14 08:04:02 livingroom kernel: [29292.282368] <0> 00000246 00000000 00000001 c04ece5e 00000086 c0108a28 000000c1 00000000
Nov 14 08:04:02 livingroom kernel: [29292.282372] <0> f6733d44 c0142d30 f6733d6c c02284c4 000000c1 00000000 c0108a28 c0142d20
Nov 14 08:04:02 livingroom kernel: [29292.282379]  [<c0108a28>] ? sched_clock+0x8/0x10
Nov 14 08:04:02 livingroom kernel: [29292.282382]  [<c0142998>] ? try_to_wake_up+0x28/0x3b0
Nov 14 08:04:02 livingroom kernel: [29292.282384]  [<c04ece5e>] ? __alloc_skb+0x2e/0x100
Nov 14 08:04:02 livingroom kernel: [29292.282386]  [<c0108a28>] ? sched_clock+0x8/0x10
Nov 14 08:04:02 livingroom kernel: [29292.282388]  [<c0142d30>] ? default_wake_function+0x10/0x20
Nov 14 08:04:02 livingroom kernel: [29292.282390]  [<c02284c4>] ? pollwake+0x54/0x60
Nov 14 08:04:02 livingroom kernel: [29292.282392]  [<c0108a28>] ? sched_clock+0x8/0x10
Nov 14 08:04:02 livingroom kernel: [29292.282394]  [<c0142d20>] ? default_wake_function+0x0/0x20
Nov 14 08:04:02 livingroom kernel: [29292.282396]  [<c0135498>] ? __wake_up_common+0x48/0x70
Nov 14 08:04:02 livingroom kernel: [29292.282398]  [<c0139403>] ? __wake_up_sync_key+0x43/0x60
Nov 14 08:04:02 livingroom kernel: [29292.282401]  [<c04ea848>] ? sock_def_readable+0x38/0x70
Nov 14 08:04:02 livingroom kernel: [29292.282403]  [<c056fe90>] ? unix_stream_sendmsg+0x1d0/0x370
Nov 14 08:04:02 livingroom kernel: [29292.282405]  [<c04e630b>] ? sock_aio_write+0x12b/0x140
Nov 14 08:04:02 livingroom kernel: [29292.282408]  [<c021836d>] ? do_sync_readv_writev+0x9d/0xe0
Nov 14 08:04:02 livingroom kernel: [29292.282411]  [<c032e636>] ? apparmor_file_permission+0x16/0x20
Nov 14 08:04:02 livingroom kernel: [29292.282414]  [<c0302a84>] ? security_file_permission+0x14/0x20
Nov 14 08:04:02 livingroom kernel: [29292.282416]  [<c02185d2>] ? rw_verify_area+0x62/0xd0
Nov 14 08:04:02 livingroom kernel: [29292.282418]  [<c02191f8>] ? rw_copy_check_uvector+0x78/0xf0
Nov 14 08:04:02 livingroom kernel: [29292.282420]  [<c0219311>] ? do_readv_writev+0xa1/0x1b0
Nov 14 08:04:02 livingroom kernel: [29292.282422]  [<c04e61e0>] ? sock_aio_write+0x0/0x140
Nov 14 08:04:02 livingroom kernel: [29292.282425]  [<c05c6a3a>] ? schedule+0x37a/0x7a0
Nov 14 08:04:02 livingroom kernel: [29292.282427]  [<c0219465>] ? vfs_writev+0x45/0x60
Nov 14 08:04:02 livingroom kernel: [29292.282428]  [<c0219572>] ? sys_writev+0x42/0xa0
Nov 14 08:04:02 livingroom kernel: [29292.282431]  [<c05c9114>] ? syscall_call+0x7/0xb
Nov 14 08:04:02 livingroom kernel: [29292.282454] ---[ end trace a3f33662725058a9 ]---
Nov 14 08:04:04 livingroom kernel: [29294.144622] *pde = 00000000 
Nov 14 08:04:04 livingroom kernel: [29294.144639] Modules linked in: parport_pc ppdev snd_hda_codec_hdmi binfmt_misc snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi radeon snd_seq_midi_event snd_seq snd_timer snd_seq_device ttm drm_kms_helper snd joydev drm serio_raw agpgart i2c_algo_bit i2c_piix4 soundcore snd_page_alloc k10temp lp shpchp parport r8169 firewire_ohci usbhid hid mii ahci firewire_core crc_itu_t libahci pata_atiixp
Nov 14 08:04:04 livingroom kernel: [29294.144698] 
Nov 14 08:04:04 livingroom kernel: [29294.144705] Pid: 2695, comm: gnome-power-man Tainted: G      D     2.6.35-22-generic #35-Ubuntu GA-MA785GMT-UD2H/GA-MA785GMT-UD2H
Nov 14 08:04:04 livingroom kernel: [29294.144712] EIP: 0060:[<c012cd88>] EFLAGS: 00010007 CPU: 0
Nov 14 08:04:04 livingroom kernel: [29294.144719] EIP is at __ticket_spin_lock+0x8/0x20
Nov 14 08:04:04 livingroom kernel: [29294.144724] EAX: 24136922 EBX: c08c3700 ECX: 00000086 EDX: 00000100
Nov 14 08:04:04 livingroom kernel: [29294.144729] ESI: c0108a28 EDI: 24136922 EBP: f6b9fcec ESP: f6b9fcec
Nov 14 08:04:04 livingroom kernel: [29294.144734]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Nov 14 08:04:04 livingroom kernel: [29294.144747]  f6b9fcf4 c05c8bdd f6b9fd0c c0139c57 f6b9fd2c 00000001 c0108a28 00000000
Nov 14 08:04:04 livingroom kernel: [29294.144758] <0> f6b9fd3c c0142998 f4b87b40 f6b9fd48 00000246 00000000 00000001 c04ece5e
Nov 14 08:04:04 livingroom kernel: [29294.144770] <0> 00000086 c0108a28 000000c1 00000000 f6b9fd44 c0142d30 f6b9fd6c c02284c4
Nov 14 08:04:04 livingroom kernel: [29294.144792]  [<c05c8bdd>] ? _raw_spin_lock+0xd/0x10
Nov 14 08:04:04 livingroom kernel: [29294.144800]  [<c0139c57>] ? task_rq_lock+0x47/0x80
Nov 14 08:04:04 livingroom kernel: [29294.144808]  [<c0108a28>] ? sched_clock+0x8/0x10
Nov 14 08:04:04 livingroom kernel: [29294.144815]  [<c0142998>] ? try_to_wake_up+0x28/0x3b0
Nov 14 08:04:04 livingroom kernel: [29294.144823]  [<c04ece5e>] ? __alloc_skb+0x2e/0x100
Nov 14 08:04:04 livingroom kernel: [29294.144829]  [<c0108a28>] ? sched_clock+0x8/0x10
Nov 14 08:04:04 livingroom kernel: [29294.144836]  [<c0142d30>] ? default_wake_function+0x10/0x20
Nov 14 08:04:04 livingroom kernel: [29294.144843]  [<c02284c4>] ? pollwake+0x54/0x60
Nov 14 08:04:04 livingroom kernel: [29294.144850]  [<c0108a28>] ? sched_clock+0x8/0x10
Nov 14 08:04:04 livingroom kernel: [29294.144856]  [<c0142d20>] ? default_wake_function+0x0/0x20
Nov 14 08:04:04 livingroom kernel: [29294.144863]  [<c0135498>] ? __wake_up_common+0x48/0x70
Nov 14 08:04:04 livingroom kernel: [29294.144871]  [<c0139403>] ? __wake_up_sync_key+0x43/0x60
Nov 14 08:04:04 livingroom kernel: [29294.144879]  [<c04ea848>] ? sock_def_readable+0x38/0x70
Nov 14 08:04:04 livingroom kernel: [29294.144887]  [<c056fe90>] ? unix_stream_sendmsg+0x1d0/0x370
Nov 14 08:04:04 livingroom kernel: [29294.144895]  [<c04e630b>] ? sock_aio_write+0x12b/0x140
Nov 14 08:04:04 livingroom kernel: [29294.144904]  [<c021836d>] ? do_sync_readv_writev+0x9d/0xe0
Nov 14 08:04:04 livingroom kernel: [29294.144913]  [<c032e636>] ? apparmor_file_permission+0x16/0x20
Nov 14 08:04:04 livingroom kernel: [29294.144922]  [<c0302a84>] ? security_file_permission+0x14/0x20
Nov 14 08:04:04 livingroom kernel: [29294.144929]  [<c02185d2>] ? rw_verify_area+0x62/0xd0
Nov 14 08:04:04 livingroom kernel: [29294.144936]  [<c02191f8>] ? rw_copy_check_uvector+0x78/0xf0
Nov 14 08:04:04 livingroom kernel: [29294.144944]  [<c0219311>] ? do_readv_writev+0xa1/0x1b0
Nov 14 08:04:04 livingroom kernel: [29294.144951]  [<c04e61e0>] ? sock_aio_write+0x0/0x140
Nov 14 08:04:04 livingroom kernel: [29294.144959]  [<c016ffbd>] ? ktime_get_ts+0xed/0x120
Nov 14 08:04:04 livingroom kernel: [29294.144966]  [<c016fb56>] ? getnstimeofday+0x56/0x120
Nov 14 08:04:04 livingroom kernel: [29294.144973]  [<c0219465>] ? vfs_writev+0x45/0x60
Nov 14 08:04:04 livingroom kernel: [29294.144980]  [<c0219572>] ? sys_writev+0x42/0xa0
Nov 14 08:04:04 livingroom kernel: [29294.144987]  [<c05c9114>] ? syscall_call+0x7/0xb
Nov 14 08:04:04 livingroom kernel: [29294.145071] ---[ end trace a3f33662725058aa ]---
Nov 14 08:04:46 livingroom rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="946" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Nov 14 08:04:47 livingroom rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="946" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Nov 14 08:05:00 livingroom kernel: [29349.445253] *pde = 00000000 
Nov 14 08:05:00 livingroom kernel: [29349.445260] Modules linked in: parport_pc ppdev snd_hda_codec_hdmi binfmt_misc snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi radeon snd_seq_midi_event snd_seq snd_timer snd_seq_device ttm drm_kms_helper snd joydev drm serio_raw agpgart i2c_algo_bit i2c_piix4 soundcore snd_page_alloc k10temp lp shpchp parport r8169 firewire_ohci usbhid hid mii ahci firewire_core crc_itu_t libahci pata_atiixp
Nov 14 08:05:00 livingroom kernel: [29349.445276] 
Nov 14 08:05:00 livingroom kernel: [29349.445279] Pid: 2806, comm: clock-applet Tainted: G      D     2.6.35-22-generic #35-Ubuntu GA-MA785GMT-UD2H/GA-MA785GMT-UD2H
Nov 14 08:05:00 livingroom kernel: [29349.445281] EIP: 0060:[<c012cd88>] EFLAGS: 00010083 CPU: 1
Nov 14 08:05:00 livingroom kernel: [29349.445283] EIP is at __ticket_spin_lock+0x8/0x20
Nov 14 08:05:00 livingroom kernel: [29349.445284] EAX: bb9c114a EBX: c08c3700 ECX: 00000086 EDX: 00000100
Nov 14 08:05:00 livingroom kernel: [29349.445285] ESI: c0108a28 EDI: bb9c114a EBP: f3761cec ESP: f3761cec
Nov 14 08:05:00 livingroom kernel: [29349.445287]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Nov 14 08:05:00 livingroom kernel: [29349.445290]  f3761cf4 c05c8bdd f3761d0c c0139c57 f3761d2c 00000001 c0108a28 00000000
Nov 14 08:05:00 livingroom kernel: [29349.445293] <0> f3761d3c c0142998 00000002 f3761d48 c020cc6d 00000001 00000001 c04ece5e
Nov 14 08:05:00 livingroom kernel: [29349.445297] <0> 00000086 c0108a28 000000c1 00000000 f3761d44 c0142d30 f3761d6c c02284c4
Nov 14 08:05:00 livingroom kernel: [29349.445304]  [<c05c8bdd>] ? _raw_spin_lock+0xd/0x10
Nov 14 08:05:00 livingroom kernel: [29349.445307]  [<c0139c57>] ? task_rq_lock+0x47/0x80
Nov 14 08:05:00 livingroom kernel: [29349.445309]  [<c0108a28>] ? sched_clock+0x8/0x10
Nov 14 08:05:00 livingroom kernel: [29349.445311]  [<c0142998>] ? try_to_wake_up+0x28/0x3b0
Nov 14 08:05:00 livingroom kernel: [29349.445314]  [<c020cc6d>] ? __kmalloc_track_caller+0x15d/0x170
Nov 14 08:05:00 livingroom kernel: [29349.445316]  [<c04ece5e>] ? __alloc_skb+0x2e/0x100
Nov 14 08:05:00 livingroom kernel: [29349.445318]  [<c0108a28>] ? sched_clock+0x8/0x10
Nov 14 08:05:00 livingroom kernel: [29349.445320]  [<c0142d30>] ? default_wake_function+0x10/0x20
Nov 14 08:05:00 livingroom kernel: [29349.445321]  [<c02284c4>] ? pollwake+0x54/0x60
Nov 14 08:05:00 livingroom kernel: [29349.445323]  [<c0108a28>] ? sched_clock+0x8/0x10
Nov 14 08:05:00 livingroom kernel: [29349.445325]  [<c0142d20>] ? default_wake_function+0x0/0x20
Nov 14 08:05:00 livingroom kernel: [29349.445327]  [<c0135498>] ? __wake_up_common+0x48/0x70
Nov 14 08:05:00 livingroom kernel: [29349.445329]  [<c0139403>] ? __wake_up_sync_key+0x43/0x60
Nov 14 08:05:00 livingroom kernel: [29349.445331]  [<c04ea848>] ? sock_def_readable+0x38/0x70
Nov 14 08:05:00 livingroom kernel: [29349.445334]  [<c056fe90>] ? unix_stream_sendmsg+0x1d0/0x370
Nov 14 08:05:00 livingroom kernel: [29349.445336]  [<c04e630b>] ? sock_aio_write+0x12b/0x140
Nov 14 08:05:00 livingroom kernel: [29349.445339]  [<c021836d>] ? do_sync_readv_writev+0x9d/0xe0
Nov 14 08:05:00 livingroom kernel: [29349.445342]  [<c032e636>] ? apparmor_file_permission+0x16/0x20
Nov 14 08:05:00 livingroom kernel: [29349.445344]  [<c0302a84>] ? security_file_permission+0x14/0x20
Nov 14 08:05:00 livingroom kernel: [29349.445346]  [<c02185d2>] ? rw_verify_area+0x62/0xd0
Nov 14 08:05:00 livingroom kernel: [29349.445348]  [<c02191f8>] ? rw_copy_check_uvector+0x78/0xf0
Nov 14 08:05:00 livingroom kernel: [29349.445350]  [<c0219311>] ? do_readv_writev+0xa1/0x1b0
Nov 14 08:05:00 livingroom kernel: [29349.445352]  [<c04e61e0>] ? sock_aio_write+0x0/0x140
Nov 14 08:05:00 livingroom kernel: [29349.445354]  [<c0219465>] ? vfs_writev+0x45/0x60
Nov 14 08:05:00 livingroom kernel: [29349.445356]  [<c0219572>] ? sys_writev+0x42/0xa0
Nov 14 08:05:00 livingroom kernel: [29349.445358]  [<c05c9114>] ? syscall_call+0x7/0xb
Nov 14 08:05:00 livingroom kernel: [29349.445381] ---[ end trace a3f33662725058ab ]---

```

lshw
```
livingroom
    description: Desktop Computer
    product: GA-MA785GMT-UD2H
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=36434630-3439-3044-3934-3830FFFFFFFF
  *-core
       description: Motherboard
       product: GA-MA785GMT-UD2H
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F5 (11/30/2009)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) II X2 250 Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.6.2
          slot: Socket M2
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 240MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L3 cache
             physical id: c
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM 1066 MHz (0.9 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: DIMM 1066 MHz (0.9 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:2
             description: DIMM 1066 MHz (0.9 ns) [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:3
             description: DIMM 1066 MHz (0.9 ns) [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             width: 64 bits
             clock: 1066MHz (0.9ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.6.2
          size: 800MHz
          capacity: 800MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 1MiB
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge Alternate
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          configuration: latency=32
          resources: memory:0-1fffffff
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (int gfx)
             vendor: Advanced Micro Devices [AMD]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:fde00000-fdffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS880 [Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:d0000000-dfffffff ioport:ee00(size=256) memory:fdfe0000-fdfeffff memory:fde00000-fdefffff
           *-multimedia
                description: Audio device
                product: RS880 Audio Device [Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:19 memory:fdffc000-fdffffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 5)
             vendor: Advanced Micro Devices [AMD]
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:fdd00000-fddfffff ioport:fda00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 6c:f0:49:0d:94:80
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.88.50 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:41 ioport:de00(size=256) memory:fdaff000-fdafffff memory:fdae0000-fdaeffff memory:fda00000-fda0ffff
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi2
             logical name: scsi3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:22 ioport:ff00(size=8) ioport:fe00(size=4) ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=16) memory:fe02f000-fe02f3ff
           *-disk
                description: ATA Disk
                product: INTEL SSDSA2M040
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 2CV1
                serial: CVGB00810074040GGN
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000f1201
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 9ff64945-d0b7-41d1-9fff-33cd64ce8993
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-05-30 22:49:56 filesystem=ext4 lastmountpoint=/ï¿œ*mï¿œï¿œïï¿œï¿œï¿œHï¿œï¿œï¿œbFï¿œxï¿œFï¿œï¿œl!ï¿œHï¿œï¿œï¿œhï¿œFï¿œï¿œwï¿œï¿œï¿œwï¿œï¿œï¿œï¿œïï¿œï¿œ ï¿œï¿œï¿œFï¿œyo!ï¿œï¿œd modified=2010-11-10 08:24:27 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-11-14 11:46:01 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 1610MiB
                   capacity: 1610MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1610MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7241S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:16 memory:fe02e000-fe02efff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:16 memory:fe02d000-fe02dfff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fe02c000-fe02c0ff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe02b000-fe02bfff
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe02a000-fe02afff
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:19 memory:fe029000-fe0290ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=32
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fa00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:fe024000-fe027fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
             resources: ioport:c000(size=4096) memory:fdc00000-fdcfffff memory:fdb00000-fdbfffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: e
                bus info: pci@0000:03:0e.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:22 memory:fdcff000-fdcff7ff memory:fdcf8000-fdcfbfff
        *-usb:6
             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe028000-fe028fff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
```

```
james@livingroom:~$ uname -r
2.6.35-22-generic

```

---

