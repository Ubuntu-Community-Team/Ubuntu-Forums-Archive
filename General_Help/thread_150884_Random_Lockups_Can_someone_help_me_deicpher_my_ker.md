---
title: "Random Lockups: Can someone help me deicpher my kern.log?"
date: 2006-03-26
forum: General Help
---

### Post by ShiftyPowers on 2006-03-26
Sorry, incorrectly posted this only in the Dapper forum.

Hey all, I have my headless HTPC with some stability issues that are pretty consistent.  Once in a while, out of the blue the system locks up completely and is not responsive to either ssh or to mouse and other commands.  I've been trying to figure out what is going one but can't decipher the logs.  I think the best log to look at is kern.log but please correct me if it's not.  I've attached the file to here since it's pretty big but I'll also but paste some of the output here.

I've tested the ram modules with memtest86 and one of them gives me some errors.  However, whenever I restart ubuntu with only one memory module (256mb instead of 512mb), ubuntu will not boot.

Here's the output I can't figure out and it shows up right before the system locks up:

```
Mar 25 12:40:37 localhost kernel: [4294745.418000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Mar 25 12:40:37 localhost kernel: [4294745.418000] apm: overridden by ACPI.
Mar 25 12:40:37 localhost kernel: [4294745.868000] hdd: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
Mar 25 12:40:37 localhost kernel: [4294745.868000] hdd: drive_cmd: error=0x04 { AbortedCommand }
Mar 25 12:40:37 localhost kernel: [4294745.868000] ide: failed opcode was: 0xec
Mar 25 12:40:37 localhost kernel: [4294745.962000] hdd: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
Mar 25 12:40:37 localhost kernel: [4294745.962000] hdd: drive_cmd: error=0x04 { AbortedCommand }
Mar 25 12:40:37 localhost kernel: [4294745.962000] ide: failed opcode was: 0xec
```

and this one:

```
Mar 26 15:55:18 localhost kernel: [4294796.979000] Unable to handle kernel paging request at virtual address 49544157
Mar 26 15:55:18 localhost kernel: [4294796.979000]  printing eip:
Mar 26 15:55:18 localhost kernel: [4294796.979000] c015cbcb
Mar 26 15:55:18 localhost kernel: [4294796.979000] *pde = 00000000
Mar 26 15:55:18 localhost kernel: [4294796.979000] Oops: 0000 [#1]
Mar 26 15:55:18 localhost kernel: [4294796.979000] PREEMPT SMP 
Mar 26 15:55:18 localhost kernel: [4294796.979000] Modules linked in: radeon drm video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec reiserfs dm_mod dv1394 raw1394 md_mod sr_mod sbp2 parport_pc lp parport tsdev snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_timer i2c_nforce2 snd ohci1394 ieee1394 i2c_core ftdi_sio soundcore usbserial snd_page_alloc psmouse serio_raw shpchp pci_hotplug nvidia_agp agpgart ipv6 evdev ext3 jbd ide_generic ehci_hcd forcedeth ohci_hcd usbcore ide_cd cdrom ide_disk generic amd74xx sata_nv libata scsi_mod thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Mar 26 15:55:18 localhost kernel: [4294796.979000] CPU:    0
Mar 26 15:55:18 localhost kernel: [4294796.979000] EIP:    0060:[vm_normal_page+27/160]    Tainted: G S    VLI
Mar 26 15:55:18 localhost kernel: [4294796.979000] EFLAGS: 00210286   (2.6.15-19-k7) 
Mar 26 15:55:18 localhost kernel: [4294796.979000] EIP is at vm_normal_page+0x1b/0xa0
Mar 26 15:55:18 localhost kernel: [4294796.979000] eax: 00000020   ebx: 49544143   ecx: 49544143   edx: 00000000
Mar 26 15:55:18 localhost kernel: [4294796.979000] esi: 0574e045   edi: 0804d000   ebp: 0804d000   esp: c5407e30
Mar 26 15:55:18 localhost kernel: [4294796.979000] ds: 007b   es: 007b   ss: 0068
Mar 26 15:55:18 localhost kernel: [4294796.979000] Process bzip2 (pid: 5163, threadinfo=c5406000 task=c6cb8050)
Mar 26 15:55:18 localhost kernel: [4294796.979000] Stack: 00000001 00000001 00000130 0574e045 0574e045 c56d0134 c015cdd2 49544143 
Mar 26 15:55:18 localhost kernel: [4294796.979000]        0804d000 0574e045 c6c8d5cc c5670134 c10c354c 00000008 c10c27cc 00000000 
Mar 26 15:55:18 localhost kernel: [4294796.979000]        00000001 c5ba8080 c5780080 0806d000 0806d000 c015d01b c6c8d580 c6c8d900 
Mar 26 15:55:18 localhost kernel: [4294796.979000] Call Trace:
Mar 26 15:55:18 localhost kernel: [4294796.979000]  [copy_pte_range+386/800] copy_pte_range+0x182/0x320
Mar 26 15:55:18 localhost kernel: [4294796.979000]  [copy_page_range+171/224] copy_page_range+0xab/0xe0
Mar 26 15:55:18 localhost kernel: [4294796.979000]  [copy_mm+679/944] copy_mm+0x2a7/0x3b0
Mar 26 15:55:18 localhost kernel: [4294796.979000]  [copy_process+1549/3936] copy_process+0x60d/0xf60
Mar 26 15:55:18 localhost kernel: [4294796.979000]  [do_fork+122/533] do_fork+0x7a/0x215
Mar 26 15:55:18 localhost kernel: [4294796.979000]  [set_close_on_exec+50/128] set_close_on_exec+0x32/0x80
Mar 26 15:55:18 localhost kernel: [4294796.979000]  [sys_clone+62/80] sys_clone+0x3e/0x50
Mar 26 15:55:18 localhost kernel: [4294796.979000]  [sysenter_past_esp+84/117] sysenter_past_esp+0x54/0x75
Mar 26 15:55:18 localhost kernel: [4294796.979000] Code: 1c 83 c4 20 e9 b7 77 fa ff 8d b4 26 00 00 00 00 83 ec 18 89 5c 24 0c 8b 5c 24 1c 89 74 24 10 8b 74 24 24 89 7c 24 14 8b 7c 24 20 <8b> 4b 14 89 f2 c1 ea 0c f6 c5 04 75 28 3b 15 c0 19 43 c0 73 4d 
Mar 26 15:55:18 localhost kernel: [4294796.979000]  <6>note: bzip2[5163] exited with preempt_count 4
Mar 26 15:55:18 localhost kernel: [4294796.979000] scheduling while atomic: bzip2/0x00000004/5163
Mar 26 15:55:18 localhost kernel: [4294796.979000]  [schedule+2445/3360] schedule+0x98d/0xd20
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [call_console_drivers+326/368] call_console_drivers+0x146/0x170
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [release_console_sem+128/192] release_console_sem+0x80/0xc0
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [vprintk+757/768] vprintk+0x2f5/0x300
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [rwsem_down_read_failed+149/416] rwsem_down_read_failed+0x95/0x1a0
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [.text.lock.exit+39/133] .text.lock.exit+0x27/0x85
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [do_exit+264/1088] do_exit+0x108/0x440
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [die+395/400] die+0x18b/0x190
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [do_page_fault+0/1582] do_page_fault+0x0/0x62e
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [do_page_fault+891/1582] do_page_fault+0x37b/0x62e
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [do_page_fault+0/1582] do_page_fault+0x0/0x62e
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [error_code+79/84] error_code+0x4f/0x54
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [vm_normal_page+27/160] vm_normal_page+0x1b/0xa0
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [copy_pte_range+386/800] copy_pte_range+0x182/0x320
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [copy_page_range+171/224] copy_page_range+0xab/0xe0
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [copy_mm+679/944] copy_mm+0x2a7/0x3b0
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [copy_process+1549/3936] copy_process+0x60d/0xf60
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [do_fork+122/533] do_fork+0x7a/0x215
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [set_close_on_exec+50/128] set_close_on_exec+0x32/0x80
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [sys_clone+62/80] sys_clone+0x3e/0x50
Mar 26 15:55:18 localhost kernel: [4294796.980000]  [sysenter_past_esp+84/117] sysenter_past_esp+0x54/0x75
Mar 26 20:11:55 localhost kernel: Inspecting /boot/System.map-2.6.15-19-k7
```

I think the problem is with the memory module because it seems the system locks up when "[4294796.979000] Unable to handle kernel paging request at virtual address 49544157" happens which seems to be related to memory.  

Any ideas would be great.  Or even if someone knows how to restart a system after removing a memory module.  Shouldn't ubuntu automatically figure out I have less ram and be able to start it up?

---

### Post by nanotube on 2006-03-26
yea seems like a memory problem indeed - especially since memtest confirms. ubuntu should not have any problems with changing amounts of memory... are you sure you are leaving the one and only ram chip (after removing the bad one) in the first mem slot?

---

### Post by ShiftyPowers on 2006-03-27
yeah just ran memtest overnight and now i'm going to see how it works with the only good ram stick.  This is such a pain.

---

