---
title: "Karmic Hard Crashes"
date: 2010-01-19
forum: General Help
---

### Post by rmcd on 2010-01-19
I'm running Karmic on a Lenovo X200s. Periodically the keyboard and screen will freeze and I have to do a hard reset. (Ctrl-Alt-F1 doesn't work.) The crashes seem to occur when I am moving the trackpoint. (Others seem to have noted similar problems in earlier threads, but those don't seem to have been resolved and the crash dumps that I've seen were different.) 

Here is an excerpt from syslog from the last crash. It's apparent from the last entry (wpa_supplicant) that the machine is still running after the problem occurs. Is this an Xorg problem? 

> Jan 19 10:08:25 fin8344m1 kernel: [43079.721890] BUG: unable to handle kernel paging request at 00aaaaaa
Jan 19 10:08:25 fin8344m1 kernel: [43079.721905] IP: [<f8441465>] drm_ht_insert_item+0x25/0xa0 [drm]
Jan 19 10:08:25 fin8344m1 kernel: [43079.721953] *pde = bbe3d067 
Jan 19 10:08:25 fin8344m1 kernel: [43079.721961] Oops: 0000 [#1] SMP 
Jan 19 10:08:25 fin8344m1 kernel: [43079.721969] last sysfs file: /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
Jan 19 10:08:25 fin8344m1 kernel: [43079.721976] Modules linked in: tun aes_i586 aes_generic binfmt_misc vboxnetadp vboxnetflt vboxdrv input_polldev snd_hda_codec_conexant snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm arc4 snd_seq_dummy ecb snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event iwlagn snd_seq iwlcore snd_timer snd_seq_device iptable_filter ip_tables thinkpad_acpi mac80211 coretemp snd soundcore led_class snd_page_alloc psmouse x_tables cfg80211 heci(C) lp nvram serio_raw parport dm_raid45 xor fbcon tileblit font bitblit softcursor i915 drm i2c_algo_bit e1000e video output intel_agp agpgart [last unloaded: kvm]
Jan 19 10:08:25 fin8344m1 kernel: [43079.722095] 
Jan 19 10:08:25 fin8344m1 kernel: [43079.722103] Pid: 1425, comm: Xorg Tainted: G         C (2.6.31-18-generic #55-Ubuntu)        
Jan 19 10:08:25 fin8344m1 kernel: [43079.722111] EIP: 0060:[<f8441465>] EFLAGS: 00013206 CPU: 1
Jan 19 10:08:25 fin8344m1 kernel: [43079.722145] EIP is at drm_ht_insert_item+0x25/0xa0 [drm]
Jan 19 10:08:25 fin8344m1 kernel: [43079.722151] EAX: f64402e0 EBX: 001bf62b ECX: 0000000d EDX: ef5c3978
Jan 19 10:08:25 fin8344m1 kernel: [43079.722157] ESI: f85bab1c EDI: 00aaaaaa EBP: f015fe2c ESP: f015fe20
Jan 19 10:08:25 fin8344m1 kernel: [43079.722163]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jan 19 10:08:25 fin8344m1 kernel: [43079.722170] Process Xorg (pid: 1425, ti=f015e000 task=ef2725b0 task.ti=f015e000)
Jan 19 10:08:25 fin8344m1 kernel: [43079.722175] Stack:
Jan 19 10:08:25 fin8344m1 kernel: [43079.722179]  ef5c3960 f4da02c0 f64402c0 f015fe60 f84b02ec 00000000 f015fe40 efffd5a0
Jan 19 10:08:25 fin8344m1 kernel: [43079.722195] <0> 00000000 ef1fc300 ef5c3960 00000040 f0249100 f0249100 f015fec0 f699f000
Jan 19 10:08:25 fin8344m1 kernel: [43079.722213] <0> f015fe80 f84b2d9e 00000000 ef5c3960 f6b1a414 ef1fc300 f6b1a400 f84dbad0
Jan 19 10:08:25 fin8344m1 kernel: [43079.722232] Call Trace:
Jan 19 10:08:25 fin8344m1 kernel: [43079.722271]  [<f84b02ec>] ? i915_gem_create_mmap_offset+0xac/0x180 [i915]
Jan 19 10:08:25 fin8344m1 kernel: [43079.722306]  [<f84b2d9e>] ? i915_gem_mmap_gtt_ioctl+0x7e/0x140 [i915]
Jan 19 10:08:25 fin8344m1 kernel: [43079.722349]  [<f843a6c0>] ? drm_ioctl+0x180/0x360 [drm]
Jan 19 10:08:25 fin8344m1 kernel: [43079.722371]  [<c0106464>] ? write_ldt+0x64/0x1e0
Jan 19 10:08:25 fin8344m1 kernel: [43079.722400]  [<f84b2d20>] ? i915_gem_mmap_gtt_ioctl+0x0/0x140 [i915]
Jan 19 10:08:25 fin8344m1 kernel: [43079.722409]  [<c0106464>] ? write_ldt+0x64/0x1e0
Jan 19 10:08:25 fin8344m1 kernel: [43079.722420]  [<c0573ce3>] ? _spin_lock_irq+0x13/0x20
Jan 19 10:08:25 fin8344m1 kernel: [43079.722430]  [<c0150186>] ? run_timer_softirq+0x156/0x200
Jan 19 10:08:25 fin8344m1 kernel: [43079.722441]  [<c016a085>] ? tick_dev_program_event+0x45/0xe0
Jan 19 10:08:25 fin8344m1 kernel: [43079.722451]  [<c014b395>] ? __do_softirq+0xe5/0x1a0
Jan 19 10:08:25 fin8344m1 kernel: [43079.722469]  [<c01f5383>] ? vfs_ioctl+0x73/0x90
Jan 19 10:08:25 fin8344m1 kernel: [43079.722477]  [<c0106464>] ? write_ldt+0x64/0x1e0
Jan 19 10:08:25 fin8344m1 kernel: [43079.722485]  [<c01f5651>] ? do_vfs_ioctl+0x71/0x310
Jan 19 10:08:25 fin8344m1 kernel: [43079.722494]  [<c01f594f>] ? sys_ioctl+0x5f/0x80
Jan 19 10:08:25 fin8344m1 kernel: [43079.722502]  [<c01033ac>] ? syscall_call+0x7/0xb
Jan 19 10:08:25 fin8344m1 kernel: [43079.722510]  [<c0106464>] ? write_ldt+0x64/0x1e0
Jan 19 10:08:25 fin8344m1 kernel: [43079.722515] Code: 90 90 90 90 90 90 55 b9 20 00 00 00 89 e5 57 56 53 8b 5a 08 2b 48 04 69 f3 01 00 37 9e d3 ee c1 e6 02 03 70 0c 8b 3e 85 ff 74 55 <8b> 07 0f 18 00 90 8b 4f 08 39 d9 74 3e 39 cb 73 17 eb 54 8b 30 
Jan 19 10:08:25 fin8344m1 kernel: [43079.722612] EIP: [<f8441465>] drm_ht_insert_item+0x25/0xa0 [drm] SS:ESP 0068:f015fe20
Jan 19 10:08:25 fin8344m1 kernel: [43079.722653] CR2: 0000000000aaaaaa
Jan 19 10:08:25 fin8344m1 kernel: [43079.722660] ---[ end trace ce33ccbad71edd8d ]---
Jan 19 10:09:09 fin8344m1 wpa_supplicant[1298]: CTRL-EVENT-SCAN-RESULTS 

I have had this problem with Karmic so I have been aggressive about upgrading components from karmic-proposed. This occurred with kernel 2.6.18.31 and xserver-xorg-core 2:1.6.4-2ubuntu4.1. But it was occurring with earlier versions, which is why I upgraded.

Any help or suggestions appreciated. Thanks.

---

### Post by rmcd on 2010-01-30
And again. No one has any thoughts about this?

Jan 30 11:02:54 fin8344m1 kernel: [157610.102774] BUG: unable to handle kernel paging request at 00aaaaaa
Jan 30 11:02:54 fin8344m1 kernel: [157610.102782] IP: [<f8441465>] drm_ht_insert_item+0x25/0xa0 [drm]
Jan 30 11:02:54 fin8344m1 kernel: [157610.102804] *pde = bbc60067 
Jan 30 11:02:54 fin8344m1 kernel: [157610.102807] Oops: 0000 [#1] SMP 
Jan 30 11:02:54 fin8344m1 kernel: [157610.102810] last sysfs file: /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
Jan 30 11:02:54 fin8344m1 kernel: [157610.102813] Modules linked in: iwlagn iwlcore mac80211 usb_storage tun nls_cp437 cifs aes_i586 aes_generic binfmt_misc vboxnetadp vboxnetflt vboxdrv input_polldev snd_hda_codec_conexant snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm arc4 snd_seq_dummy snd_seq_oss ecb snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device iptable_filter snd soundcore ip_tables snd_page_alloc psmouse thinkpad_acpi coretemp cfg80211 x_tables heci(C) serio_raw led_class lp nvram parport dm_raid45 xor fbcon tileblit font bitblit softcursor i915 drm i2c_algo_bit video output e1000e intel_agp agpgart [last unloaded: mac80211]
Jan 30 11:02:54 fin8344m1 kernel: [157610.102869] 
Jan 30 11:02:54 fin8344m1 kernel: [157610.102873] Pid: 1318, comm: Xorg Tainted: G         C (2.6.31-18-generic #55-Ubuntu)        
Jan 30 11:02:54 fin8344m1 kernel: [157610.102876] EIP: 0060:[<f8441465>] EFLAGS: 00013206 CPU: 1
Jan 30 11:02:54 fin8344m1 kernel: [157610.102891] EIP is at drm_ht_insert_item+0x25/0xa0 [drm]
Jan 30 11:02:54 fin8344m1 kernel: [157610.102894] EAX: f68ffde0 EBX: 001fa6fb ECX: 0000000d EDX: d3bb24f8
Jan 30 11:02:54 fin8344m1 kernel: [157610.102897] ESI: f8674194 EDI: 00aaaaaa EBP: e13ebe2c ESP: e13ebe20
Jan 30 11:02:54 fin8344m1 kernel: [157610.102899]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jan 30 11:02:54 fin8344m1 kernel: [157610.102902] Process Xorg (pid: 1318, ti=e13ea000 task=d81be480 task.ti=e13ea000)
Jan 30 11:02:54 fin8344m1 kernel: [157610.102904] Stack:
Jan 30 11:02:54 fin8344m1 kernel: [157610.102906]  d3bb24e0 d6b75e00 f68ffdc0 e13ebe60 f84b02ec 00000000 f6931014 d3bb2f60
Jan 30 11:02:54 fin8344m1 kernel: [157610.102913] <0> e13ebe5c e11ade40 d3bb24e0 00000040 e1381980 e1381980 e13ebec0 f690f000
Jan 30 11:02:54 fin8344m1 kernel: [157610.102921] <0> e13ebe80 f84b2d9e 00000000 d3bb24e0 f6931014 e11ade40 f6931000 f84dbad0
Jan 30 11:02:54 fin8344m1 kernel: [157610.102929] Call Trace:
Jan 30 11:02:54 fin8344m1 kernel: [157610.102948]  [<f84b02ec>] ? i915_gem_create_mmap_offset+0xac/0x180 [i915]
Jan 30 11:02:54 fin8344m1 kernel: [157610.102963]  [<f84b2d9e>] ? i915_gem_mmap_gtt_ioctl+0x7e/0x140 [i915]
Jan 30 11:02:54 fin8344m1 kernel: [157610.102982]  [<f843a6c0>] ? drm_ioctl+0x180/0x360 [drm]
Jan 30 11:02:54 fin8344m1 kernel: [157610.102993]  [<c0106464>] ? write_ldt+0x64/0x1e0
Jan 30 11:02:54 fin8344m1 kernel: [157610.103006]  [<f84b2d20>] ? i915_gem_mmap_gtt_ioctl+0x0/0x140 [i915]
Jan 30 11:02:54 fin8344m1 kernel: [157610.103010]  [<c0106464>] ? write_ldt+0x64/0x1e0
Jan 30 11:02:54 fin8344m1 kernel: [157610.103016]  [<c015c1d0>] ? autoremove_wake_function+0x0/0x40
Jan 30 11:02:54 fin8344m1 kernel: [157610.103021]  [<c02cbb7f>] ? security_file_permission+0xf/0x20
Jan 30 11:02:54 fin8344m1 kernel: [157610.103029]  [<c01f5383>] ? vfs_ioctl+0x73/0x90
Jan 30 11:02:54 fin8344m1 kernel: [157610.103033]  [<c0106464>] ? write_ldt+0x64/0x1e0
Jan 30 11:02:54 fin8344m1 kernel: [157610.103037]  [<c01f5651>] ? do_vfs_ioctl+0x71/0x310
Jan 30 11:02:54 fin8344m1 kernel: [157610.103040]  [<c01f594f>] ? sys_ioctl+0x5f/0x80
Jan 30 11:02:54 fin8344m1 kernel: [157610.103044]  [<c01033ac>] ? syscall_call+0x7/0xb
Jan 30 11:02:54 fin8344m1 kernel: [157610.103048]  [<c0106464>] ? write_ldt+0x64/0x1e0
Jan 30 11:02:54 fin8344m1 kernel: [157610.103050] Code: 90 90 90 90 90 90 55 b9 20 00 00 00 89 e5 57 56 53 8b 5a 08 2b 48 04 69 f3 01 00 37 9e d3 ee c1 e6 02 03 70 0c 8b 3e 85 ff 74 55 <8b> 07 0f 18 00 90 8b 4f 08 39 d9 74 3e 39 cb 73 17 eb 54 8b 30 
Jan 30 11:02:54 fin8344m1 kernel: [157610.103092] EIP: [<f8441465>] drm_ht_insert_item+0x25/0xa0 [drm] SS:ESP 0068:e13ebe20
Jan 30 11:02:54 fin8344m1 kernel: [157610.103110] CR2: 0000000000aaaaaa
Jan 30 11:02:54 fin8344m1 kernel: [157610.103114] ---[ end trace 3b504376bdaa5403 ]---

---

