---
title: "random system freeze/lockup, nothing in logs"
date: 2011-06-03
forum: General Help
---

### Post by f-bomb on 2011-06-03
Running updated 11.04 on a older Dell Precision 360n.  Been having random system freezes for the past month that requires a hard restart (REISUB doesn't work) each time.  Sometimes the caps lock and scroll lock LEDs blink, other times not.  sometimes it happens during boot, other times during normal usage.  There hasn't been anything in any of the logs (except once, which I'll post below).  This happened running 10.04 and 10.10 as well.  I've run PC-check a few times and all hardware diagnostics have passed.  Until today, i've been able to boot and run Trinity Rescue Kit 3.4 to mount the disk and examine the logs (and do backups), but now TRK won't boot and spews kernel panics when loading.  Any ideas on what to look at?

```

Jun  2 10:29:17 mercury kernel: [   33.820428] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
Jun  2 10:29:17 mercury kernel: [   33.820448] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
Jun  2 10:29:17 mercury kernel: [   33.820490] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
Jun  2 10:29:18 mercury kernel: [   35.073339] audit_printk_skb: 39 callbacks suppressed
Jun  2 10:29:18 mercury kernel: [   35.073344] type=1400 audit(1307035758.761:25): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=910 comm="apparmor_parser"
Jun  2 10:29:18 mercury kernel: [   35.120768] type=1400 audit(1307035758.809:26): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=913 comm="apparmor_parser"
Jun  2 10:29:19 mercury kernel: [   35.604825] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jun  2 10:29:19 mercury kernel: [   35.604830] apm: overridden by ACPI.
Jun  2 10:29:20 mercury kernel: [   36.337288] BUG: unable to handle kernel NULL pointer dereference at 00000008
Jun  2 10:29:20 mercury kernel: [   36.337298] IP: [<c104e102>] copy_process+0x162/0xbb0
Jun  2 10:29:20 mercury kernel: [   36.337309] *pde = 7fa88067
Jun  2 10:29:20 mercury kernel: [   36.337313] Oops: 0000 [#1] SMP
Jun  2 10:29:20 mercury kernel: [   36.337317] last sysfs file: /sys/devices/virtual/sound/timer/uevent
Jun  2 10:29:20 mercury kernel: [   36.337322] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_seq_midi nvidia(P) snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc dcdbas ppdev shpchp psmouse parport_pc serio_raw lp parport e1000 floppy
Jun  2 10:29:20 mercury kernel: [   36.337344]
Jun  2 10:29:20 mercury kernel: [   36.337348] Pid: 985, comm: dbus-daemon Tainted: P            2.6.38-8-generic #42-Ubuntu Dell Computer Corporation Precision WorkStation 360    /0W2563
Jun  2 10:29:20 mercury kernel: [   36.337356] EIP: 0060:[<c104e102>] EFLAGS: 00010202 CPU: 0
Jun  2 10:29:20 mercury kernel: [   36.337360] EIP is at copy_process+0x162/0xbb0
Jun  2 10:29:20 mercury kernel: [   36.337363] EAX: 00000008 EBX: ee7425e0 ECX: c1074733 EDX: c1074700
Jun  2 10:29:20 mercury kernel: [   36.337366] ESI: b78d6788 EDI: fffffff5 EBP: eea5ff3c ESP: eea5ff0c
Jun  2 10:29:20 mercury kernel: [   36.337370]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jun  2 10:29:20 mercury kernel: [   36.337373] Process dbus-daemon (pid: 985, ti=eea5e000 task=ee5ff1a0 task.ti=eea5e000)
Jun  2 10:29:20 mercury kernel: [   36.337376] Stack:
Jun  2 10:29:20 mercury kernel: [   36.337378]  0000000f 00080000 eea5ff40 c141ee64 00000008 eea5ffb4 bfabc00c 01200011
Jun  2 10:29:20 mercury kernel: [   36.337386]  c11259cc 00000000 b78d6788 b78d6788 eea5ff84 c104ebf3 00000000 b78d6788
Jun  2 10:29:20 mercury kernel: [   36.337393]  00000000 00000000 ee72d100 ee01b800 ee01b600 00000000 01200011 bfabc2c0
Jun  2 10:29:20 mercury kernel: [   36.337401] Call Trace:
Jun  2 10:29:20 mercury kernel: [   36.337408]  [<c141ee64>] ? sock_alloc_file+0x84/0xf0
Jun  2 10:29:20 mercury kernel: [   36.337414]  [<c11259cc>] ? fd_install+0x4c/0x60
Jun  2 10:29:20 mercury kernel: [   36.337418]  [<c104ebf3>] do_fork+0x63/0x2d0
Jun  2 10:29:20 mercury kernel: [   36.337423]  [<c1421496>] ? sys_socketcall+0x1f6/0x2a0
Jun  2 10:29:20 mercury kernel: [   36.337428]  [<c100acc4>] sys_clone+0x34/0x40
Jun  2 10:29:20 mercury kernel: [   36.337432]  [<c1003219>] ptregs_clone+0x15/0x3c
Jun  2 10:29:20 mercury kernel: [   36.337439]  [<c1509bf4>] ? syscall_call+0x7/0xb
Jun  2 10:29:20 mercury kernel: [   36.337441] Code: 88 ad 02 00 00 a1 bc 04 85 c1 bf f5 ff ff ff 39 05 b0 04 85 c1 0f 8d 83 02 00 00 8b 43 04 8b 40 04 8b 40 24 85 c0 89 45 e0 74 17 <83> 38 02 0f 84 6a 02 00 00 8b 80 78 01 00 00 64 ff 00 3e 8d 74
Jun  2 10:29:20 mercury kernel: [   36.337483] EIP: [<c104e102>] copy_process+0x162/0xbb0 SS:ESP 0068:eea5ff0c
Jun  2 10:29:20 mercury kernel: [   36.337489] CR2: 0000000000000008
Jun  2 10:29:20 mercury kernel: [   36.337493] ---[ end trace ba3dd4357ec40994 ]---
Jun  2 10:29:20 mercury kernel: [   36.337697] BUG: unable to handle kernel NULL pointer dereference at 00000180
Jun  2 10:29:20 mercury kernel: [   36.337702] IP: [<c10851fa>] module_put+0x1a/0x80
Jun  2 10:29:20 mercury kernel: [   36.337710] *pde = 00000000
Jun  2 10:29:20 mercury kernel: [   36.337713] Oops: 0000 [#2] SMP
Jun  2 10:29:20 mercury kernel: [   36.337716] last sysfs file: /sys/devices/virtual/sound/timer/uevent
Jun  2 10:29:20 mercury kernel: [   36.337718] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_seq_midi nvidia(P) snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc dcdbas ppdev shpchp psmouse parport_pc serio_raw lp parport e1000 floppy
Jun  2 10:29:20 mercury kernel: [   36.337738]
Jun  2 10:29:20 mercury kernel: [   36.337741] Pid: 985, comm: dbus-daemon Tainted: P      D     2.6.38-8-generic #42-Ubuntu Dell Computer Corporation Precision WorkStation 360    /0W2563
Jun  2 10:29:20 mercury kernel: [   36.337749] EIP: 0060:[<c10851fa>] EFLAGS: 00010202 CPU: 0
Jun  2 10:29:20 mercury kernel: [   36.337753] EIP is at module_put+0x1a/0x80
Jun  2 10:29:20 mercury kernel: [   36.337756] EAX: 00000008 EBX: ee5ff1a0 ECX: ee93eb84 EDX: 0000d7d7
Jun  2 10:29:20 mercury kernel: [   36.337758] ESI: f392dc00 EDI: 00000008 EBP: eea5fd80 ESP: eea5fd70
Jun  2 10:29:20 mercury kernel: [   36.337761]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jun  2 10:29:20 mercury kernel: [   36.337764] Process dbus-daemon (pid: 985, ti=eea5e000 task=ee5ff1a0 task.ti=eea5e000)
Jun  2 10:29:20 mercury kernel: [   36.337767] Stack:
Jun  2 10:29:20 mercury kernel: [   36.337769]  c1097638 ee5ff1a0 f392dc00 00000001 eea5fdb8 c1053a39 00000246 eea5fd9c
Jun  2 10:29:20 mercury kernel: [   36.337776]  c150717f 00000000 00000031 0000009f f3af2500 00000009 eea5fed0 00000009
Jun  2 10:29:20 mercury kernel: [   36.337783]  eea5fed0 00000246 eea5fdd0 c150ae36 eea5fdd0 eea5fed0 00000009 ee5ff1a0
Jun  2 10:29:20 mercury kernel: [   36.337790] Call Trace:
Jun  2 10:29:20 mercury kernel: [   36.337795]  [<c1097638>] ? cgroup_exit+0x98/0xd0
Jun  2 10:29:20 mercury kernel: [   36.337800]  [<c1053a39>] do_exit+0x169/0x350
Jun  2 10:29:20 mercury kernel: [   36.337804]  [<c150717f>] ? printk+0x30/0x39
Jun  2 10:29:20 mercury kernel: [   36.337808]  [<c150ae36>] oops_end+0x96/0xd0
Jun  2 10:29:20 mercury kernel: [   36.337813]  [<c102e5dc>] no_context+0xbc/0x150
Jun  2 10:29:20 mercury kernel: [   36.337817]  [<c102e855>] __bad_area_nosemaphore+0x95/0x140
Jun  2 10:29:20 mercury kernel: [   36.337822]  [<c102e960>] bad_area+0x40/0x50
Jun  2 10:29:20 mercury kernel: [   36.337826]  [<c150ce00>] ? do_page_fault+0x0/0x490
Jun  2 10:29:20 mercury kernel: [   36.337829]  [<c150d284>] do_page_fault+0x484/0x490
Jun  2 10:29:20 mercury kernel: [   36.337834]  [<c111a95d>] ? kmem_cache_alloc_trace+0xdd/0x100
Jun  2 10:29:20 mercury kernel: [   36.337838]  [<c100a706>] ? arch_dup_task_struct+0x46/0xa0
Jun  2 10:29:20 mercury kernel: [   36.337844]  [<c1244c7e>] ? aa_alloc_task_context+0x2e/0x50
Jun  2 10:29:20 mercury kernel: [   36.337848]  [<c1244c7e>] ? aa_alloc_task_context+0x2e/0x50
Jun  2 10:29:20 mercury kernel: [   36.337852]  [<c1244d33>] ? aa_dup_task_context+0x33/0x60
Jun  2 10:29:20 mercury kernel: [   36.337856]  [<c150ce00>] ? do_page_fault+0x0/0x490
Jun  2 10:29:20 mercury kernel: [   36.337860]  [<c150a2df>] error_code+0x67/0x6c
Jun  2 10:29:20 mercury kernel: [   36.337865]  [<c1074733>] ? copy_creds+0xc3/0x180
Jun  2 10:29:20 mercury kernel: [   36.337869]  [<c1074700>] ? copy_creds+0x90/0x180
Jun  2 10:29:20 mercury kernel: [   36.337873]  [<c107007b>] ? posix_cpu_timer_set+0x45b/0x480
Jun  2 10:29:20 mercury kernel: [   36.337877]  [<c104e102>] ? copy_process+0x162/0xbb0
Jun  2 10:29:20 mercury kernel: [   36.337881]  [<c141ee64>] ? sock_alloc_file+0x84/0xf0
Jun  2 10:29:20 mercury kernel: [   36.337885]  [<c11259cc>] ? fd_install+0x4c/0x60
Jun  2 10:29:20 mercury kernel: [   36.337889]  [<c104ebf3>] do_fork+0x63/0x2d0
Jun  2 10:29:20 mercury kernel: [   36.337893]  [<c1421496>] ? sys_socketcall+0x1f6/0x2a0
Jun  2 10:29:20 mercury kernel: [   36.337897]  [<c100acc4>] sys_clone+0x34/0x40
Jun  2 10:29:20 mercury kernel: [   36.337901]  [<c1003219>] ptregs_clone+0x15/0x3c
Jun  2 10:29:20 mercury kernel: [   36.337905]  [<c1509bf4>] ? syscall_call+0x7/0xb
Jun  2 10:29:20 mercury kernel: [   36.337908] Code: 00 89 ca 29 c2 c1 e0 0c e8 a4 ae fa ff eb a0 66 90 55 89 e5 83 ec 10 89 5d f4 89 75 f8 89 7d fc 3e 8d 74 26 00 85 c0 89 c7 74 1a <8b> 80 78 01 00 00 64 ff 40 04 8b 45 04 89 45 f0 3e 8d 74 26 00
Jun  2 10:29:20 mercury kernel: [   36.337950] EIP: [<c10851fa>] module_put+0x1a/0x80 SS:ESP 0068:eea5fd70
Jun  2 10:29:20 mercury kernel: [   36.337957] CR2: 0000000000000180
Jun  2 10:29:20 mercury kernel: [   36.337960] ---[ end trace ba3dd4357ec40995 ]---
Jun  2 10:29:20 mercury kernel: [   36.337962] Fixing recursive fault but reboot is needed!
Jun  2 10:29:20 mercury kernel: [   36.804381] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
Jun  2 10:29:20 mercury kernel: [   36.804404] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
Jun  2 10:29:20 mercury kernel: [   36.804445] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
Jun  2 10:29:25 mercury kernel: [   41.600032] eth0: no IPv6 routers present
Jun  2 10:29:30 mercury kernel: [   46.468157] NET: Registered protocol family 15
Jun  2 10:29:30 mercury kernel: [   46.717043] padlock_sha: VIA PadLock Hash Engine not detected.
Jun  2 10:29:30 mercury kernel: [   46.773679] padlock_sha: VIA PadLock Hash Engine not detected.
Jun  2 10:29:31 mercury kernel: [   47.000067] Intel AES-NI instructions are not detected.
Jun  2 10:29:31 mercury kernel: [   47.009473] padlock_aes: VIA PadLock not detected.
Jun  2 11:09:16 mercury kernel: [ 2432.169390] BUG: unable to handle kernel NULL pointer dereference at 00000028
Jun  2 11:09:16 mercury kernel: [ 2432.169400] IP: [<c150834b>] mutex_lock+0x1b/0x40
Jun  2 11:09:16 mercury kernel: [ 2432.169411] *pde = 00000000
Jun  2 11:09:16 mercury kernel: [ 2432.169415] Oops: 0002 [#3] SMP
Jun  2 11:09:16 mercury kernel: [ 2432.169419] last sysfs file: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0c.0/net/eth0/statistics/collisions
Jun  2 11:09:16 mercury kernel: [ 2432.169424] Modules linked in: binfmt_misc deflate zlib_deflate ctr twofish_generic twofish_i586 twofish_common camellia serpent blowfish cast5 des_generic cryptd aes_i586 aes_generic xcbc rmd160 sha512_generic sha256_generic sha1_generic crypto_null af_key snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_seq_midi nvidia(P) snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc dcdbas ppdev shpchp psmouse parport_pc serio_raw lp parport e1000 floppy
Jun  2 11:09:16 mercury kernel: [ 2432.169465]
Jun  2 11:09:16 mercury kernel: [ 2432.169470] Pid: 3826, comm: crashreporter Tainted: P      D     2.6.38-8-generic #42-Ubuntu Dell Computer Corporation Precision WorkStation 360    /0W2563
Jun  2 11:09:16 mercury kernel: [ 2432.169478] EIP: 0060:[<c150834b>] EFLAGS: 00010246 CPU: 0
Jun  2 11:09:16 mercury kernel: [ 2432.169482] EIP is at mutex_lock+0x1b/0x40
Jun  2 11:09:16 mercury kernel: [ 2432.169485] EAX: 00000028 EBX: 00000028 ECX: 00000018 EDX: ee794000
Jun  2 11:09:16 mercury kernel: [ 2432.169488] ESI: 00000000 EDI: ecee2b80 EBP: ee795dc0 ESP: ee795db8
Jun  2 11:09:16 mercury kernel: [ 2432.169491]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jun  2 11:09:16 mercury kernel: [ 2432.169494] Process crashreporter (pid: 3826, ti=ee794000 task=edf4f1a0 task.ti=ee794000)
Jun  2 11:09:16 mercury kernel: [ 2432.169497] Stack:
Jun  2 11:09:16 mercury kernel: [ 2432.169499]  ededa300 00000000 ee795e00 c11439d5 00000008 ee795dec c11439b0 00000028
Jun  2 11:09:16 mercury kernel: [ 2432.169507]  00000018 ef38bc80 ededa300 c1159b9c c1904b88 ee795e04 ededa308 ededa300
Jun  2 11:09:16 mercury kernel: [ 2432.169514]  ef38bc80 ecee2b80 ee795e0c c1159eee ededa300 ee795e18 c1159f3b ededa300
Jun  2 11:09:16 mercury kernel: [ 2432.169522] Call Trace:
Jun  2 11:09:16 mercury kernel: [ 2432.169530]  [<c11439d5>] seq_read+0x25/0x390
Jun  2 11:09:16 mercury kernel: [ 2432.169534]  [<c11439b0>] ? seq_read+0x0/0x390
Jun  2 11:09:16 mercury kernel: [ 2432.169540]  [<c1159b9c>] ? fsnotify_flush_notify+0x7c/0x90
Jun  2 11:09:16 mercury kernel: [ 2432.169545]  [<c1159eee>] fsnotify_final_destroy_group+0x1e/0x30
Jun  2 11:09:16 mercury kernel: [ 2432.169549]  [<c1159f3b>] fsnotify_put_group+0x3b/0x40
Jun  2 11:09:16 mercury kernel: [ 2432.169554]  [<c115b6f6>] inotify_release+0x26/0x40
Jun  2 11:09:16 mercury kernel: [ 2432.169559]  [<c1128275>] __fput+0x95/0x1c0
Jun  2 11:09:16 mercury kernel: [ 2432.169563]  [<c11283bd>] fput+0x1d/0x30
Jun  2 11:09:16 mercury kernel: [ 2432.169567]  [<c11250fe>] filp_close+0x4e/0x70
Jun  2 11:09:16 mercury kernel: [ 2432.169571]  [<c1125925>] sys_close+0x75/0xd0
Jun  2 11:09:16 mercury kernel: [ 2432.169575]  [<c112dd04>] setup_new_exec+0x184/0x240
Jun  2 11:09:16 mercury kernel: [ 2432.169581]  [<c1008c5a>] ? flush_ptrace_hw_breakpoint+0x1a/0x40
Jun  2 11:09:16 mercury kernel: [ 2432.169587]  [<c1167a6d>] load_elf_binary+0x29d/0xa60
Jun  2 11:09:16 mercury kernel: [ 2432.169592]  [<c102d8c8>] ? default_spin_lock_flags+0x8/0x10
Jun  2 11:09:16 mercury kernel: [ 2432.169597]  [<c150996f>] ? _raw_spin_lock_irqsave+0x2f/0x50
Jun  2 11:09:16 mercury kernel: [ 2432.169602]  [<c10fcc63>] ? page_address+0xd3/0xe0
Jun  2 11:09:16 mercury kernel: [ 2432.169607]  [<c112c412>] search_binary_handler+0xb2/0x2b0
Jun  2 11:09:16 mercury kernel: [ 2432.169612]  [<c11677d0>] ? load_elf_binary+0x0/0xa60
Jun  2 11:09:16 mercury kernel: [ 2432.169616]  [<c112da9f>] do_execve+0x1ef/0x270
Jun  2 11:09:16 mercury kernel: [ 2432.169621]  [<c100ad07>] sys_execve+0x37/0x70
Jun  2 11:09:16 mercury kernel: [ 2432.169625]  [<c10031ae>] ptregs_execve+0x12/0x18
Jun  2 11:09:16 mercury kernel: [ 2432.169630]  [<c1509bf4>] ? syscall_call+0x7/0xb
Jun  2 11:09:16 mercury kernel: [ 2432.169634]  [<c1500000>] ? print_cpu_info+0xe3/0x126
Jun  2 11:09:16 mercury kernel: [ 2432.169637] Code: ff 89 42 10 b8 01 00 00 00 5d c3 31 c0 5d c3 90 55 89 e5 83 ec 08 89 1c 24 89 74 24 04 3e 8d 74 26 00 89 c3 e8 97 f7 ff ff 89 d8 <3e> ff 08 79 05 e8 bb 03 00 00 89 e0 8b 74 24 04 25 00 e0 ff ff
Jun  2 11:09:16 mercury kernel: [ 2432.169679] EIP: [<c150834b>] mutex_lock+0x1b/0x40 SS:ESP 0068:ee795db8
Jun  2 11:09:16 mercury kernel: [ 2432.169686] CR2: 0000000000000028
Jun  2 11:09:16 mercury kernel: [ 2432.169690] ---[ end trace ba3dd4357ec40996 ]---
Jun  2 11:09:16 mercury kernel: [ 2432.921086] BUG: unable to handle kernel paging request at 0012efec
Jun  2 11:09:16 mercury kernel: [ 2432.921096] IP: [<c11033e9>] find_vma+0x39/0x70
Jun  2 11:09:16 mercury kernel: [ 2432.921108] *pde = 7de34067
Jun  2 11:09:16 mercury kernel: [ 2432.921112] Oops: 0000 [#4] SMP
Jun  2 11:09:16 mercury kernel: [ 2432.921116] last sysfs file: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0c.0/net/eth0/statistics/collisions
Jun  2 11:09:16 mercury kernel: [ 2432.921121] Modules linked in: binfmt_misc deflate zlib_deflate ctr twofish_generic twofish_i586 twofish_common camellia serpent blowfish cast5 des_generic cryptd aes_i586 aes_generic xcbc rmd160 sha512_generic sha256_generic sha1_generic crypto_null af_key snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_seq_midi nvidia(P) snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc dcdbas ppdev shpchp psmouse parport_pc serio_raw lp parport e1000 floppy
Jun  2 11:09:16 mercury kernel: [ 2432.921160]
Jun  2 11:09:16 mercury kernel: [ 2432.921164] Pid: 676, comm: polkitd Tainted: P      D     2.6.38-8-generic #42-Ubuntu Dell Computer Corporation Precision WorkStation 360    /0W2563
Jun  2 11:09:16 mercury kernel: [ 2432.921172] EIP: 0060:[<c11033e9>] EFLAGS: 00010206 CPU: 0
Jun  2 11:09:16 mercury kernel: [ 2432.921177] EIP is at find_vma+0x39/0x70
Jun  2 11:09:16 mercury kernel: [ 2432.921181] EAX: eea11600 EBX: 0012efe4 ECX: 0012f000 EDX: b7726000
Jun  2 11:09:16 mercury kernel: [ 2432.921184] ESI: 00000000 EDI: eea11600 EBP: eeb01f0c ESP: eeb01f04
Jun  2 11:09:16 mercury kernel: [ 2432.921187]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jun  2 11:09:16 mercury kernel: [ 2432.921191] Process polkitd (pid: 676, ti=eeb00000 task=ee8f3f20 task.ti=eeb00000)
Jun  2 11:09:16 mercury kernel: [ 2432.921193] Stack:
Jun  2 11:09:16 mercury kernel: [ 2432.921195]  b7726000 00001000 eeb01f34 c110487d 00000913 00000000 b7727000 ea77ad00
Jun  2 11:09:16 mercury kernel: [ 2432.921203]  00000000 00001000 c1104770 00000001 eeb01f4c c11034f7 00000000 00000001
Jun  2 11:09:16 mercury kernel: [ 2432.921209]  00000000 ea77ad00 eeb01f84 c1105739 00000000 00000001 00000000 0034e2a8
Jun  2 11:09:16 mercury kernel: [ 2432.921217] Call Trace:
Jun  2 11:09:16 mercury kernel: [ 2432.921223]  [<c110487d>] arch_get_unmapped_area_topdown+0x10d/0x170
Jun  2 11:09:16 mercury kernel: [ 2432.921228]  [<c1104770>] ? arch_get_unmapped_area_topdown+0x0/0x170
Jun  2 11:09:16 mercury kernel: [ 2432.921232]  [<c11034f7>] get_unmapped_area_prot+0x57/0xb0
Jun  2 11:09:16 mercury kernel: [ 2432.921236]  [<c1105739>] do_mmap_pgoff+0xe9/0x300
Jun  2 11:09:16 mercury kernel: [ 2432.921241]  [<c1105af7>] sys_mmap_pgoff+0x1a7/0x1d0
Jun  2 11:09:16 mercury kernel: [ 2432.921247]  [<c1509bf4>] syscall_call+0x7/0xb
Jun  2 11:09:16 mercury kernel: [ 2432.921252]  [<c1500000>] ? print_cpu_info+0xe3/0x126
Jun  2 11:09:16 mercury kernel: [ 2432.921254] Code: 74 3c 8b 70 08 85 f6 74 05 39 56 08 77 3c 8b 48 04 31 f6 85 c9 75 11 eb 25 90 3b 53 04 73 3b 8b 49 08 89 de 85 c9 74 0f 8d 59 e4 <3b> 53 08 72 ea 8b 49 04 85 c9 75 f1 85 f6 74 03 89 70 08 89 f0
Jun  2 11:09:16 mercury kernel: [ 2432.921293] EIP: [<c11033e9>] find_vma+0x39/0x70 SS:ESP 0068:eeb01f04
Jun  2 11:09:16 mercury kernel: [ 2432.921299] CR2: 000000000012efec
Jun  2 11:09:16 mercury kernel: [ 2432.921303] ---[ end trace ba3dd4357ec40997 ]---

```

---

### Post by f-bomb on 2011-06-03
running another hardware diagnostic and now one of the RAM sticks has failed.  Will pull it after the test completes and see if it changes anything....

---

### Post by f-bomb on 2011-06-08
new RAM, but 5 days later it froze up again.  I'm not sure what to look for, or even where to start.....

---

### Post by f-bomb on 2011-06-08
^bump^ so it doesn't get buried.....

---

### Post by no2498 on 2011-06-08
id try seeing if some thing is using to much memory or cpu
install htop type it in a terminal it tells you how to install it
htop click enter after its installed

just keep an eye on things

hope it helps

---

### Post by f-bomb on 2011-06-08
ok, after I hard reset, the box wouldn't post.  it would powerup, but not post/boot.  I cracked the case open and reseated everything in the mobo (RAM, power, IDE connectors, graphics card) and was able to get it to boot.  i had just installed htop, then fired up Firefox, when it suddenly rebooted.  Now its stuck on "Starting up ...".  if it won't finished booting, i'll boot off a rescue disk and browse the logs.  I'm thinking the mobo is going bad....

---

### Post by no2498 on 2011-06-09
if you have a spare power supply id try it first

---

