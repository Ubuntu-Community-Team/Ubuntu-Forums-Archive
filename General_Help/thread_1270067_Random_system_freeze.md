---
title: "Random system freeze"
date: 2009-09-19
forum: General Help
---

### Post by Varro on 2009-09-19
Hi to everyone,
i use Ubuntu 9.04 but randomly, the system freezes itself. I think it's something related to pulse audio server because of the log reports something about that.

```

pulseaudio[3745]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
pulseaudio[3745]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
pulseaudio[3745]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 23,00 dB to 23,00 dB which makes no sense.

```

but i noticed this message is logged at system boot time. Nothing is logged when the system freezes.
I hope someone could help me to find a solution.
Regargs.

---

### Post by earthpigg on 2009-09-19
when it freezes, can you still ctrl+alt+F4 (or F5. or F6. etc) to get to another tty and work from there?

you can test this now: ctrl+alt+F7 will bring you back home.

---

### Post by Varro on 2009-09-19
> 
when it freezes, can you still ctrl+alt+F4 (or F5. or F6. etc) to get to another tty and work from there?


Hi earthpig, i'm working on my windows notebook now, but i have my desktop turned on in order to test what you asked me when the desktop freezes.

> 
you can test this now: ctrl+alt+F7 will bring you back home. 


I tested what you asked, ctrl+alt+f7 and ctrl+alt+f4 worked correctly. Now i'm waiting for a system freeze to test and reply.

Maybe could be useful to know i have a ASUS P5N-E SLI as a motherboard, and also be useful to apologize for my bad english :)

Thanks for the fast reply.

---

### Post by Varro on 2009-09-19
It freezed two minutes ago, i tried to press ctrl+alt+f5...6,7,8 etc but nothing happened.
What can i do?

---

### Post by earthpigg on 2009-09-19
> **Varro said:**
> It freezed two minutes ago, i tried to press ctrl+alt+f5...6,7,8 etc but nothing happened.
What can i do?

well, that would be what you call a hard freeze. which means probably a hardware issue, unfortunately.

1. is it an overheating issue? install lm-sensors:
```
sudo apt-get install lm-sensors
```
configure it (say yes to everything):
```
sudo sensors-detect
```
try keep your eye on the internal temps... every 5-10 min or so:
```
sensors
```

2. are you running out of memory? run free -m
look under the 'free' column. if those are ever all approaching zero, you have a problem.

3. is your RAM going bad? this isn't uncommon. run memtest86. usually folks run it overnight. [http://en.wikipedia.org/wiki/Memtest86](http://en.wikipedia.org/wiki/Memtest86)

i used [this one]("http://www.memtest86.com/") last, but some people prefer [the other one]("http://www.memtest.org/").



im pretty sure those are the three most common causes of hard lockups -- actually, #1 usually causes the computer to *shut down*... but i already typed it so meh :D

---

### Post by Varro on 2009-09-19
Hi earthpigg, i'm kinda frustrated, i installed lm sensors and the temperature is 40°C, perfectly normal.
I got 4gb of memory and memtest says i got no problems.
Maybe could be something due to hardware incompatibility? I got 4 blocks of the same ram model: Corsair 6400 XMS2.
They have a different latency, two of these have latency 5-5-5-12 and the others have latency 5-5-5-18.
I'm desperated and i dont't want to switch back to Windows :(

---

### Post by Varro on 2009-10-04
I noticed nobody answered me. I'm kinda frustrated by this error. Anybody else knows what i can do to solve the problem?
It's quite difficult to work with this problem.
Thank you

---

### Post by Varro on 2009-10-04
Nobody replies since two weeks, so i decided to continue making some tests to keep this thread alive for others may have the same problem.
I'm trying to disable nvidia drivers in order to see if it cause the freeze.
I'm leaving my pc turned on for the next 48 hours after i tried to use both 180 and 173 nvidia driver version.

---

### Post by earthpigg on 2009-10-04
have you tested for faulty RAM?

[http://www.memtest86.com/](http://www.memtest86.com/)

---

### Post by Varro on 2009-10-04
Yeah, it was one of the first things i tried.
It's a damned enigma

---

### Post by Varro on 2009-10-05
I tested again the ram with memtest along the night and it reported no errors at all.
Moreover, the freeze is not caused by nvidia drivers, yesterday the system freezed using default drivers with conpiz disabled.
The hardware temperatures are low.
Now i try to turn off the cpu scaling, maybe is something related to this processor feature.

---

### Post by Varro on 2009-10-05
Afted turning off cpu scaling, the pc shut down itself after 15 minutes.
I reset BIOS settings to their default value (Speedstep is disabled by default) and now i got no problems since an hour.
Sensors give me good results, temperature is quite good, cpu reaches at least 60° and has an average temperature of 55°.

---

### Post by Varro on 2009-10-05
After an afternoon the system freezed watching something on megavideo. 
I forgot to say that it is possibile to hear something during the freeze, like a sound loop.
So, let's make the point of the situation:
- RAM is ok
- Nvidia drivers are not the problem's cause
- BIOS features are not the problem's cause
I'm trying to understand if what i heard is related to something.
I expect other suggestion, trying to resist to switching back to windows.
Hope to solve this annoying problem.

P.S.: I think it's something related with X server

---

### Post by yeeeev on 2009-10-05
Are there still no logs from the freeze in /var/log/kern.log?

---

### Post by Varro on 2009-10-05
```

Oct  5 23:15:37 faye kernel: Inspecting /boot/System.map-2.6.28-15-server
Oct  5 23:15:37 faye kernel: Cannot find map file.
Oct  5 23:15:38 faye kernel: Loaded 75739 symbols from 48 modules.
Oct  5 23:15:38 faye kernel: [    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
Oct  5 23:15:38 faye kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct  5 23:15:38 faye kernel: [    0.000000] Initializing cgroup subsys cpu
Oct  5 23:15:38 faye kernel: [    0.000000] Linux version 2.6.28-15-server (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #52-Ubuntu SMP Wed Sep 9 11:50:50 UTC 2009 (Ubuntu 2.6.28-15.52-server)
Oct  5 23:15:38 faye kernel: [    0.000000] KERNEL supported cpus:
Oct  5 23:15:38 faye kernel: [    0.000000]   Intel GenuineIntel
Oct  5 23:15:38 faye kernel: [    0.000000]   AMD AuthenticAMD
Oct  5 23:15:38 faye kernel: [    0.000000]   NSC Geode by NSC
Oct  5 23:15:38 faye kernel: [    0.000000]   Cyrix CyrixInstead
Oct  5 23:15:38 faye kernel: [    0.000000]   Centaur CentaurHauls
Oct  5 23:15:38 faye kernel: [    0.000000]   Transmeta GenuineTMx86
Oct  5 23:15:38 faye kernel: [    0.000000]   Transmeta TransmetaCPU
Oct  5 23:15:38 faye kernel: [    0.000000]   UMC UMC UMC UMC
Oct  5 23:15:38 faye kernel: [    0.000000] BIOS-provided physical RAM map:
Oct  5 23:15:38 faye kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Oct  5 23:15:38 faye kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Oct  5 23:15:38 faye kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Oct  5 23:15:38 faye kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfef0000 (usable)
Oct  5 23:15:38 faye kernel: [    0.000000]  BIOS-e820: 00000000dfef0000 - 00000000dfef3000 (ACPI NVS)
Oct  5 23:15:38 faye kernel: [    0.000000]  BIOS-e820: 00000000dfef3000 - 00000000dff00000 (ACPI data)
Oct  5 23:15:38 faye kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f2000000 (reserved)
Oct  5 23:15:38 faye kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Oct  5 23:15:38 faye kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
Oct  5 23:15:38 faye kernel: [    0.000000] DMI 2.4 present.
Oct  5 23:15:38 faye kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Oct  5 23:15:38 faye kernel: [    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x1000000
Oct  5 23:15:38 faye kernel: [    0.000000] Scanning 0 areas for low memory corruption
Oct  5 23:15:38 faye kernel: [    0.000000] modified physical RAM map:
Oct  5 23:15:38 faye kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Oct  5 23:15:38 faye kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Oct  5 23:15:38 faye kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Oct  5 23:15:38 faye kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Oct  5 23:15:38 faye kernel: [    0.000000]  modified: 0000000000100000 - 00000000dfef0000 (usable)
Oct  5 23:15:38 faye kernel: [    0.000000]  modified: 00000000dfef0000 - 00000000dfef3000 (ACPI NVS)
Oct  5 23:15:38 faye kernel: [    0.000000]  modified: 00000000dfef3000 - 00000000dff00000 (ACPI data)
Oct  5 23:15:38 faye kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f2000000 (reserved)
Oct  5 23:15:38 faye kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Oct  5 23:15:38 faye kernel: [    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
Oct  5 23:15:38 faye kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-16000
Oct  5 23:15:38 faye kernel: [    0.000000] NX (Execute Disable) protection: active
Oct  5 23:15:38 faye kernel: [    0.000000] RAMDISK: 378b4000 - 37fef797
Oct  5 23:15:38 faye kernel: [    0.000000] Allocated new RAMDISK: 008ac000 - 00fe7797
Oct  5 23:15:38 faye kernel: [    0.000000] Move RAMDISK from 00000000378b4000 - 0000000037fef796 to 008ac000 - 00fe7796
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: RSDP 000F7910, 0024 (r2 Nvidia)
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: XSDT DFEF30C0, 004C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: FACP DFEF9880, 00F4 (r3 Nvidia ASUSACPI 42302E31 AWRD        0)
Oct  5 23:15:38 faye kernel: [    0.000000] FADT: X_PM1a_EVT_BLK.bit_width (8) does not match PM1_EVT_LEN (4)
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: DSDT DFEF3240, 65DB (r1 NVIDIA ASUSACPI     1000 MSFT  3000000)
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: FACS DFEF0000, 0040
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: HPET DFEF9AC0, 0038 (r1 Nvidia ASUSACPI 42302E31 AWRD       98)
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: MCFG DFEF9B40, 003C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: APIC DFEF99C0, 0098 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: SSDT DFEF9BC0, 087B (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct  5 23:15:38 faye kernel: [    0.000000] 3720MB HIGHMEM available.
Oct  5 23:15:38 faye kernel: [    0.000000] 887MB LOWMEM available.
Oct  5 23:15:38 faye kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Oct  5 23:15:38 faye kernel: [    0.000000]   low ram: 00000000 - 377fe000
Oct  5 23:15:38 faye kernel: [    0.000000]   bootmap 00013000 - 00019f00
Oct  5 23:15:38 faye kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Oct  5 23:15:38 faye kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Oct  5 23:15:38 faye kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Oct  5 23:15:38 faye kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Oct  5 23:15:38 faye kernel: [    0.000000]   #3 [0000100000 - 00008a29ac]    TEXT DATA BSS ==> [0000100000 - 00008a29ac]
Oct  5 23:15:38 faye kernel: [    0.000000]   #4 [00008a3000 - 00008ac000]    INIT_PG_TABLE ==> [00008a3000 - 00008ac000]
Oct  5 23:15:38 faye kernel: [    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Oct  5 23:15:38 faye kernel: [    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
Oct  5 23:15:38 faye kernel: [    0.000000]   #7 [00008ac000 - 0000fe7797]      NEW RAMDISK ==> [00008ac000 - 0000fe7797]
Oct  5 23:15:38 faye kernel: [    0.000000]   #8 [0000013000 - 000001a000]          BOOTMAP ==> [0000013000 - 000001a000]
Oct  5 23:15:38 faye kernel: [    0.000000] found SMP MP-table at [c00f5dd0] 000f5dd0
Oct  5 23:15:38 faye kernel: [    0.000000] Zone PFN ranges:
Oct  5 23:15:38 faye kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Oct  5 23:15:38 faye kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Oct  5 23:15:38 faye kernel: [    0.000000]   HighMem  0x000377fe -> 0x00120000
Oct  5 23:15:38 faye kernel: [    0.000000] Movable zone start PFN for each node
Oct  5 23:15:38 faye kernel: [    0.000000] early_node_map[3] active PFN ranges
Oct  5 23:15:38 faye kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Oct  5 23:15:38 faye kernel: [    0.000000]     0: 0x00000100 -> 0x000dfef0
Oct  5 23:15:38 faye kernel: [    0.000000]     0: 0x00100000 -> 0x00120000
Oct  5 23:15:38 faye kernel: [    0.000000] On node 0 totalpages: 1048191
Oct  5 23:15:38 faye kernel: [    0.000000] free_area_init_node: node 0, pgdat c06ded00, node_mem_map c1000200
Oct  5 23:15:38 faye kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Oct  5 23:15:38 faye kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct  5 23:15:38 faye kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Oct  5 23:15:38 faye kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Oct  5 23:15:38 faye kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Oct  5 23:15:38 faye kernel: [    0.000000]   HighMem zone: 7441 pages used for memmap
Oct  5 23:15:38 faye kernel: [    0.000000]   HighMem zone: 813537 pages, LIFO batch:31
Oct  5 23:15:38 faye kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Oct  5 23:15:38 faye kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: IRQ14 used by override.
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: IRQ15 used by override.
Oct  5 23:15:38 faye kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct  5 23:15:38 faye kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Oct  5 23:15:38 faye kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct  5 23:15:38 faye kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Oct  5 23:15:38 faye kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct  5 23:15:38 faye kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Oct  5 23:15:38 faye kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Oct  5 23:15:38 faye kernel: [    0.000000] Allocating PCI resources starting at e0000000 (gap: dff00000:10100000)
Oct  5 23:15:38 faye kernel: [    0.000000] PERCPU: Allocating 49152 bytes of per cpu data
Oct  5 23:15:38 faye kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Oct  5 23:15:38 faye kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1038974
Oct  5 23:15:38 faye kernel: [    0.000000] Kernel command line: root=UUID=50de47dc-b4a7-4fb8-bea0-e0087447c22d ro quiet splash 
Oct  5 23:15:38 faye kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct  5 23:15:38 faye kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct  5 23:15:38 faye kernel: [    0.000000] Initializing CPU#0
Oct  5 23:15:38 faye kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct  5 23:15:38 faye kernel: [    0.000000] Extended CMOS year: 2000
Oct  5 23:15:38 faye kernel: [    0.000000] Fast TSC calibration using PIT
Oct  5 23:15:38 faye kernel: [    0.000000] Detected 2199.712 MHz processor.
Oct  5 23:15:38 faye kernel: [    0.010000] spurious 8259A interrupt: IRQ7.
Oct  5 23:15:38 faye kernel: [    0.010000] Console: colour VGA+ 80x25
Oct  5 23:15:38 faye kernel: [    0.010000] console [tty0] enabled
Oct  5 23:15:38 faye kernel: [    0.010000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct  5 23:15:38 faye kernel: [    0.010000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct  5 23:15:38 faye kernel: [    0.010000] allocated 23592640 bytes of page_cgroup
Oct  5 23:15:38 faye kernel: [    0.010000] please try cgroup_disable=memory option if you don't want
Oct  5 23:15:38 faye kernel: [    0.010000] Scanning for low memory corruption every 60 seconds
Oct  5 23:15:38 faye kernel: [    0.010000] Memory: 4115652k/4718592k available (4169k kernel code, 76248k reserved, 2238k data, 548k init, 3283912k highmem)
Oct  5 23:15:38 faye kernel: [    0.010000] virtual kernel memory layout:
Oct  5 23:15:38 faye kernel: [    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
Oct  5 23:15:38 faye kernel: [    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
Oct  5 23:15:38 faye kernel: [    0.010000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Oct  5 23:15:38 faye kernel: [    0.010000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Oct  5 23:15:38 faye kernel: [    0.010000]       .init : 0xc0749000 - 0xc07d2000   ( 548 kB)
Oct  5 23:15:38 faye kernel: [    0.010000]       .data : 0xc05126b3 - 0xc0741fc0   (2238 kB)
Oct  5 23:15:38 faye kernel: [    0.010000]       .text : 0xc0100000 - 0xc05126b3   (4169 kB)
Oct  5 23:15:38 faye kernel: [    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Oct  5 23:15:38 faye kernel: [    0.010000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Oct  5 23:15:38 faye kernel: [    0.010000] hpet clockevent registered
Oct  5 23:15:38 faye kernel: [    0.010000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Oct  5 23:15:38 faye kernel: [    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4399.42 BogoMIPS (lpj=21997120)
Oct  5 23:15:38 faye kernel: [    0.010000] Security Framework initialized
Oct  5 23:15:38 faye kernel: [    0.010000] SELinux:  Disabled at boot.
Oct  5 23:15:38 faye kernel: [    0.010000] AppArmor: AppArmor initialized
Oct  5 23:15:38 faye kernel: [    0.010000] Mount-cache hash table entries: 512
Oct  5 23:15:38 faye kernel: [    0.010000] Initializing cgroup subsys ns
Oct  5 23:15:38 faye kernel: [    0.010000] Initializing cgroup subsys cpuacct
Oct  5 23:15:38 faye kernel: [    0.010000] Initializing cgroup subsys memory
Oct  5 23:15:38 faye kernel: [    0.010000] Initializing cgroup subsys freezer
Oct  5 23:15:38 faye kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct  5 23:15:38 faye kernel: [    0.010000] CPU: L2 cache: 2048K
Oct  5 23:15:38 faye kernel: [    0.010000] CPU: Physical Processor ID: 0
Oct  5 23:15:38 faye kernel: [    0.010000] CPU: Processor Core ID: 0
Oct  5 23:15:38 faye kernel: [    0.010000] using mwait in idle threads.
Oct  5 23:15:38 faye kernel: [    0.010000] Checking 'hlt' instruction... OK.
Oct  5 23:15:38 faye kernel: [    0.042212] ACPI: Core revision 20080926
Oct  5 23:15:38 faye kernel: [    0.043547] ACPI: Checking initramfs for custom DSDT
Oct  5 23:15:38 faye kernel: [    0.314052] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct  5 23:15:38 faye kernel: [    0.417850] CPU0: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
Oct  5 23:15:38 faye kernel: [    0.420000] Booting processor 1 APIC 0x1 ip 0x6000
Oct  5 23:15:38 faye kernel: [    0.010000] Initializing CPU#1
Oct  5 23:15:38 faye kernel: [    0.010000] Calibrating delay using timer specific routine.. 4399.97 BogoMIPS (lpj=21999861)
Oct  5 23:15:38 faye kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct  5 23:15:38 faye kernel: [    0.010000] CPU: L2 cache: 2048K
Oct  5 23:15:38 faye kernel: [    0.010000] CPU: Physical Processor ID: 0
Oct  5 23:15:38 faye kernel: [    0.010000] CPU: Processor Core ID: 1
Oct  5 23:15:38 faye kernel: [    0.570350] CPU1: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
Oct  5 23:15:38 faye kernel: [    0.570360] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Oct  5 23:15:38 faye kernel: [    0.580038] Brought up 2 CPUs
Oct  5 23:15:38 faye kernel: [    0.580041] Total of 2 processors activated (8799.39 BogoMIPS).
Oct  5 23:15:38 faye kernel: [    0.580118] CPU0 attaching sched-domain:
Oct  5 23:15:38 faye kernel: [    0.580120]  domain 0: span 0-1 level MC
Oct  5 23:15:38 faye kernel: [    0.580122]   groups: 0 1
Oct  5 23:15:38 faye kernel: [    0.580127] CPU1 attaching sched-domain:
Oct  5 23:15:38 faye kernel: [    0.580129]  domain 0: span 0-1 level MC
Oct  5 23:15:38 faye kernel: [    0.580131]   groups: 1 0
Oct  5 23:15:38 faye kernel: [    0.580197] net_namespace: 776 bytes
Oct  5 23:15:38 faye kernel: [    0.580197] Booting paravirtualized kernel on bare hardware
Oct  5 23:15:38 faye kernel: [    0.580293] Time: 21:15:18  Date: 10/05/09
Oct  5 23:15:38 faye kernel: [    0.580293] regulator: core version 0.5
Oct  5 23:15:38 faye kernel: [    0.580293] NET: Registered protocol family 16
Oct  5 23:15:38 faye kernel: [    0.580293] EISA bus registered
Oct  5 23:15:38 faye kernel: [    0.580293] ACPI: bus type pci registered
Oct  5 23:15:38 faye kernel: [    0.580293] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 31
Oct  5 23:15:38 faye kernel: [    0.580293] PCI: MCFG area at f0000000 reserved in E820
Oct  5 23:15:38 faye kernel: [    0.580293] PCI: Using MMCONFIG for extended config space
Oct  5 23:15:38 faye kernel: [    0.580293] PCI: Using configuration type 1 for base access
Oct  5 23:15:38 faye kernel: [    0.581169] ACPI: EC: Look up EC in DSDT
Oct  5 23:15:38 faye kernel: [    0.591947] ACPI: Interpreter enabled
Oct  5 23:15:38 faye kernel: [    0.591952] ACPI: (supports S0 S1 S3 S4 S5)
Oct  5 23:15:38 faye kernel: [    0.591974] ACPI: Using IOAPIC for interrupt routing
Oct  5 23:15:38 faye kernel: [    0.601237] ACPI: No dock devices found.
Oct  5 23:15:38 faye kernel: [    0.601248] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct  5 23:15:38 faye kernel: [    0.602115] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct  5 23:15:38 faye kernel: [    0.602119] pci 0000:00:03.0: PME# disabled
Oct  5 23:15:38 faye kernel: [    0.602161] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct  5 23:15:38 faye kernel: [    0.602164] pci 0000:00:07.0: PME# disabled
Oct  5 23:15:38 faye kernel: [    0.602402] pci 0000:00:0a.1: reg 20 io port: [0x1c00-0x1c3f]
Oct  5 23:15:38 faye kernel: [    0.602408] pci 0000:00:0a.1: reg 24 io port: [0x1c80-0x1cbf]
Oct  5 23:15:38 faye kernel: [    0.602423] pci 0000:00:0a.1: PME# supported from D3hot D3cold
Oct  5 23:15:38 faye kernel: [    0.602429] pci 0000:00:0a.1: PME# disabled
Oct  5 23:15:38 faye kernel: [    0.602505] pci 0000:00:0b.0: reg 10 32bit mmio: [0xfe02f000-0xfe02ffff]
Oct  5 23:15:38 faye kernel: [    0.602534] pci 0000:00:0b.0: supports D1 D2
Oct  5 23:15:38 faye kernel: [    0.602536] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct  5 23:15:38 faye kernel: [    0.602540] pci 0000:00:0b.0: PME# disabled
Oct  5 23:15:38 faye kernel: [    0.602571] pci 0000:00:0b.1: reg 10 32bit mmio: [0xfe02e000-0xfe02e0ff]
Oct  5 23:15:38 faye kernel: [    0.602600] pci 0000:00:0b.1: supports D1 D2
Oct  5 23:15:38 faye kernel: [    0.602602] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
Oct  5 23:15:38 faye kernel: [    0.602605] pci 0000:00:0b.1: PME# disabled
Oct  5 23:15:38 faye kernel: [    0.602652] pci 0000:00:0d.0: reg 20 io port: [0xf400-0xf40f]
Oct  5 23:15:38 faye kernel: [    0.602700] pci 0000:00:0e.0: reg 10 io port: [0x9f0-0x9f7]
Oct  5 23:15:38 faye kernel: [    0.602705] pci 0000:00:0e.0: reg 14 io port: [0xbf0-0xbf3]
Oct  5 23:15:38 faye kernel: [    0.602710] pci 0000:00:0e.0: reg 18 io port: [0x970-0x977]
Oct  5 23:15:38 faye kernel: [    0.602715] pci 0000:00:0e.0: reg 1c io port: [0xb70-0xb73]
Oct  5 23:15:38 faye kernel: [    0.602720] pci 0000:00:0e.0: reg 20 io port: [0xe000-0xe00f]
Oct  5 23:15:38 faye kernel: [    0.602726] pci 0000:00:0e.0: reg 24 32bit mmio: [0xfe02d000-0xfe02dfff]
Oct  5 23:15:38 faye kernel: [    0.602773] pci 0000:00:0f.0: reg 10 io port: [0x9e0-0x9e7]
Oct  5 23:15:38 faye kernel: [    0.602778] pci 0000:00:0f.0: reg 14 io port: [0xbe0-0xbe3]
Oct  5 23:15:38 faye kernel: [    0.602783] pci 0000:00:0f.0: reg 18 io port: [0x960-0x967]
Oct  5 23:15:38 faye kernel: [    0.602788] pci 0000:00:0f.0: reg 1c io port: [0xb60-0xb63]
Oct  5 23:15:38 faye kernel: [    0.602794] pci 0000:00:0f.0: reg 20 io port: [0xcc00-0xcc0f]
Oct  5 23:15:38 faye kernel: [    0.602799] pci 0000:00:0f.0: reg 24 32bit mmio: [0xfe02c000-0xfe02cfff]
Oct  5 23:15:38 faye kernel: [    0.602888] pci 0000:00:10.1: reg 10 32bit mmio: [0xfe024000-0xfe027fff]
Oct  5 23:15:38 faye kernel: [    0.602917] pci 0000:00:10.1: PME# supported from D3hot D3cold
Oct  5 23:15:38 faye kernel: [    0.602921] pci 0000:00:10.1: PME# disabled
Oct  5 23:15:38 faye kernel: [    0.602960] pci 0000:00:14.0: reg 10 32bit mmio: [0xfe02b000-0xfe02bfff]
Oct  5 23:15:38 faye kernel: [    0.602965] pci 0000:00:14.0: reg 14 io port: [0xc800-0xc807]
Oct  5 23:15:38 faye kernel: [    0.602989] pci 0000:00:14.0: supports D1 D2
Oct  5 23:15:38 faye kernel: [    0.602991] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct  5 23:15:38 faye kernel: [    0.602994] pci 0000:00:14.0: PME# disabled
Oct  5 23:15:38 faye kernel: [    0.603038] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
Oct  5 23:15:38 faye kernel: [    0.603047] pci 0000:01:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
Oct  5 23:15:38 faye kernel: [    0.603056] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfb000000-0xfbffffff]
Oct  5 23:15:38 faye kernel: [    0.603065] pci 0000:01:00.0: reg 30 32bit mmio: [0xfcfe0000-0xfcffffff]
Oct  5 23:15:38 faye kernel: [    0.603120] pci 0000:00:03.0: bridge io port: [0xb000-0xbfff]
Oct  5 23:15:38 faye kernel: [    0.603123] pci 0000:00:03.0: bridge 32bit mmio: [0xfa000000-0xfcffffff]
Oct  5 23:15:38 faye kernel: [    0.603128] pci 0000:00:03.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
Oct  5 23:15:38 faye kernel: [    0.603173] pci 0000:02:00.0: reg 10 io port: [0x8c00-0x8c07]
Oct  5 23:15:38 faye kernel: [    0.603181] pci 0000:02:00.0: reg 14 io port: [0x8800-0x8803]
Oct  5 23:15:38 faye kernel: [    0.603189] pci 0000:02:00.0: reg 18 io port: [0x8400-0x8407]
Oct  5 23:15:38 faye kernel: [    0.603196] pci 0000:02:00.0: reg 1c io port: [0x8000-0x8003]
Oct  5 23:15:38 faye kernel: [    0.603204] pci 0000:02:00.0: reg 20 io port: [0x7c00-0x7c0f]
Oct  5 23:15:38 faye kernel: [    0.603212] pci 0000:02:00.0: reg 24 32bit mmio: [0xfdcfe000-0xfdcfffff]
Oct  5 23:15:38 faye kernel: [    0.603229] pci 0000:02:00.0: PME# supported from D3hot
Oct  5 23:15:38 faye kernel: [    0.603233] pci 0000:02:00.0: PME# disabled
Oct  5 23:15:38 faye kernel: [    0.603285] pci 0000:00:07.0: bridge io port: [0x7000-0x8fff]
Oct  5 23:15:38 faye kernel: [    0.603288] pci 0000:00:07.0: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
Oct  5 23:15:38 faye kernel: [    0.603292] pci 0000:00:07.0: bridge 64bit mmio pref: [0xfdb00000-0xfdbfffff]
Oct  5 23:15:38 faye kernel: [    0.603364] pci 0000:03:06.0: supports D1 D2
Oct  5 23:15:38 faye kernel: [    0.603365] pci 0000:03:06.0: PME# supported from D0 D1 D2 D3hot
Oct  5 23:15:38 faye kernel: [    0.603369] pci 0000:03:06.0: PME# disabled
Oct  5 23:15:38 faye kernel: [    0.603433] pci 0000:03:06.1: supports D1 D2
Oct  5 23:15:38 faye kernel: [    0.603435] pci 0000:03:06.1: PME# supported from D0 D1 D2 D3hot
Oct  5 23:15:38 faye kernel: [    0.603439] pci 0000:03:06.1: PME# disabled
Oct  5 23:15:38 faye kernel: [    0.603503] pci 0000:03:06.2: supports D1 D2
Oct  5 23:15:38 faye kernel: [    0.603505] pci 0000:03:06.2: PME# supported from D0 D1 D2 D3hot
Oct  5 23:15:38 faye kernel: [    0.603509] pci 0000:03:06.2: PME# disabled
Oct  5 23:15:38 faye kernel: [    0.603548] pci 0000:03:08.0: reg 10 32bit mmio: [0xfdffd000-0xfdffd7ff]
Oct  5 23:15:38 faye kernel: [    0.603555] pci 0000:03:08.0: reg 14 io port: [0xac00-0xac7f]
Oct  5 23:15:38 faye kernel: [    0.603587] pci 0000:03:08.0: supports D2
Oct  5 23:15:38 faye kernel: [    0.603589] pci 0000:03:08.0: PME# supported from D2 D3hot D3cold
Oct  5 23:15:38 faye kernel: [    0.603593] pci 0000:03:08.0: PME# disabled
Oct  5 23:15:38 faye kernel: [    0.603627] pci 0000:00:10.0: transparent bridge
Oct  5 23:15:38 faye kernel: [    0.603630] pci 0000:00:10.0: bridge io port: [0x9000-0xafff]
Oct  5 23:15:38 faye kernel: [    0.603633] pci 0000:00:10.0: bridge 32bit mmio: [0xfde00000-0xfdffffff]
Oct  5 23:15:38 faye kernel: [    0.603637] pci 0000:00:10.0: bridge 32bit mmio pref: [0xfdd00000-0xfddfffff]
Oct  5 23:15:38 faye kernel: [    0.603649] bus 00 -> node 0
Oct  5 23:15:38 faye kernel: [    0.603655] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct  5 23:15:38 faye kernel: [    0.604053] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Oct  5 23:15:38 faye kernel: [    0.679781] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
Oct  5 23:15:38 faye kernel: [    0.679959] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.680151] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
Oct  5 23:15:38 faye kernel: [    0.680326] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.680503] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 *11 14 15)
Oct  5 23:15:38 faye kernel: [    0.680678] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 *10 11 14 15)
Oct  5 23:15:38 faye kernel: [    0.680853] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.681028] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.681207] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
Oct  5 23:15:38 faye kernel: [    0.681381] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.681558] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
Oct  5 23:15:38 faye kernel: [    0.681736] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.681912] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
Oct  5 23:15:38 faye kernel: [    0.682086] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.682262] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.682438] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
Oct  5 23:15:38 faye kernel: [    0.682613] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
Oct  5 23:15:38 faye kernel: [    0.682787] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.682963] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
Oct  5 23:15:38 faye kernel: [    0.683141] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
Oct  5 23:15:38 faye kernel: [    0.683354] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
Oct  5 23:15:38 faye kernel: [    0.683558] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.683761] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
Oct  5 23:15:38 faye kernel: [    0.683964] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.684168] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
Oct  5 23:15:38 faye kernel: [    0.684372] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0
Oct  5 23:15:38 faye kernel: [    0.684574] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.684777] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.684981] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
Oct  5 23:15:38 faye kernel: [    0.685186] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.685392] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
Oct  5 23:15:38 faye kernel: [    0.685597] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.685803] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.686007] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
Oct  5 23:15:38 faye kernel: [    0.686212] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.686417] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
Oct  5 23:15:38 faye kernel: [    0.686623] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
Oct  5 23:15:38 faye kernel: [    0.686827] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.687034] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Oct  5 23:15:38 faye kernel: [    0.687241] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Oct  5 23:15:38 faye kernel: [    0.687447] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
Oct  5 23:15:38 faye kernel: [    0.687590] ACPI: WMI: Mapper loaded
Oct  5 23:15:38 faye kernel: [    0.687624] SCSI subsystem initialized
Oct  5 23:15:38 faye kernel: [    0.687624] libata version 3.00 loaded.
Oct  5 23:15:38 faye kernel: [    0.687624] usbcore: registered new interface driver usbfs
Oct  5 23:15:38 faye kernel: [    0.687624] usbcore: registered new interface driver hub
Oct  5 23:15:38 faye kernel: [    0.687624] usbcore: registered new device driver usb
Oct  5 23:15:38 faye kernel: [    0.687624] PCI: Using ACPI for IRQ routing
Oct  5 23:15:38 faye kernel: [    0.700006] Bluetooth: Core ver 2.13
Oct  5 23:15:38 faye kernel: [    0.700019] NET: Registered protocol family 31
Oct  5 23:15:38 faye kernel: [    0.700019] Bluetooth: HCI device and connection manager initialized
Oct  5 23:15:38 faye kernel: [    0.700019] Bluetooth: HCI socket layer initialized
Oct  5 23:15:38 faye kernel: [    0.700019] NET: Registered protocol family 8
Oct  5 23:15:38 faye kernel: [    0.700019] NET: Registered protocol family 20
Oct  5 23:15:38 faye kernel: [    0.700029] NetLabel: Initializing
Oct  5 23:15:38 faye kernel: [    0.700030] NetLabel:  domain hash size = 128
Oct  5 23:15:38 faye kernel: [    0.700031] NetLabel:  protocols = UNLABELED CIPSOv4
Oct  5 23:15:38 faye kernel: [    0.700042] NetLabel:  unlabeled traffic allowed by default
Oct  5 23:15:38 faye kernel: [    0.700056] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Oct  5 23:15:38 faye kernel: [    0.700060] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Oct  5 23:15:38 faye kernel: [    0.710049] AppArmor: AppArmor Filesystem Enabled
Oct  5 23:15:38 faye kernel: [    0.720007] Switched to high resolution mode on CPU 0
Oct  5 23:15:38 faye kernel: [    0.720392] Switched to high resolution mode on CPU 1
Oct  5 23:15:38 faye kernel: [    0.730000] pnp: PnP ACPI init
Oct  5 23:15:38 faye kernel: [    0.730010] ACPI: bus type pnp registered
Oct  5 23:15:38 faye kernel: [    0.734850] pnp: PnP ACPI: found 15 devices
Oct  5 23:15:38 faye kernel: [    0.734852] ACPI: ACPI bus type pnp unregistered
Oct  5 23:15:38 faye kernel: [    0.734855] PnPBIOS: Disabled by ACPI PNP
Oct  5 23:15:38 faye kernel: [    0.734865] system 00:01: ioport range 0x1000-0x107f has been reserved
Oct  5 23:15:38 faye kernel: [    0.734867] system 00:01: ioport range 0x1080-0x10ff has been reserved
Oct  5 23:15:38 faye kernel: [    0.734870] system 00:01: ioport range 0x1400-0x147f has been reserved
Oct  5 23:15:38 faye kernel: [    0.734872] system 00:01: ioport range 0x1480-0x14ff has been reserved
Oct  5 23:15:38 faye kernel: [    0.734875] system 00:01: ioport range 0x1800-0x187f has been reserved
Oct  5 23:15:38 faye kernel: [    0.734877] system 00:01: ioport range 0x1880-0x18ff has been reserved
Oct  5 23:15:38 faye kernel: [    0.734882] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Oct  5 23:15:38 faye kernel: [    0.734885] system 00:02: ioport range 0x800-0x87f has been reserved
Oct  5 23:15:38 faye kernel: [    0.734887] system 00:02: ioport range 0x290-0x297 has been reserved
Oct  5 23:15:38 faye kernel: [    0.734889] system 00:02: ioport range 0x880-0x88f has been reserved
Oct  5 23:15:38 faye kernel: [    0.734898] system 00:0d: iomem range 0xf0000000-0xf1ffffff has been reserved
Oct  5 23:15:38 faye kernel: [    0.734903] system 00:0e: iomem range 0xda000-0xdbfff has been reserved
Oct  5 23:15:38 faye kernel: [    0.734906] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
Oct  5 23:15:38 faye kernel: [    0.734908] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
Oct  5 23:15:38 faye kernel: [    0.734910] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
Oct  5 23:15:38 faye kernel: [    0.734913] system 00:0e: iomem range 0xfeff0000-0xfeff00ff has been reserved
Oct  5 23:15:38 faye kernel: [    0.734916] system 00:0e: iomem range 0xdfef0000-0xdfefffff could not be reserved
Oct  5 23:15:38 faye kernel: [    0.734918] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
Oct  5 23:15:38 faye kernel: [    0.734920] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Oct  5 23:15:38 faye kernel: [    0.734923] system 00:0e: iomem range 0x100000-0xdfeeffff could not be reserved
Oct  5 23:15:38 faye kernel: [    0.734925] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Oct  5 23:15:38 faye kernel: [    0.734928] system 00:0e: iomem range 0xfee00000-0xfee00fff has been reserved
Oct  5 23:15:38 faye kernel: [    0.734930] system 00:0e: iomem range 0xfeff0000-0xfeff03ff could not be reserved
Oct  5 23:15:38 faye kernel: [    0.769658] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
Oct  5 23:15:38 faye kernel: [    0.769661] pci 0000:00:03.0:   IO window: 0xb000-0xbfff
Oct  5 23:15:38 faye kernel: [    0.769665] pci 0000:00:03.0:   MEM window: 0xfa000000-0xfcffffff
Oct  5 23:15:38 faye kernel: [    0.769668] pci 0000:00:03.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
Oct  5 23:15:38 faye kernel: [    0.769673] pci 0000:00:07.0: PCI bridge, secondary bus 0000:02
Oct  5 23:15:38 faye kernel: [    0.769675] pci 0000:00:07.0:   IO window: 0x7000-0x8fff
Oct  5 23:15:38 faye kernel: [    0.769679] pci 0000:00:07.0:   MEM window: 0xfdc00000-0xfdcfffff
Oct  5 23:15:38 faye kernel: [    0.769682] pci 0000:00:07.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Oct  5 23:15:38 faye kernel: [    0.769687] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
Oct  5 23:15:38 faye kernel: [    0.769689] pci 0000:00:10.0:   IO window: 0x9000-0xafff
Oct  5 23:15:38 faye kernel: [    0.769693] pci 0000:00:10.0:   MEM window: 0xfde00000-0xfdffffff
Oct  5 23:15:38 faye kernel: [    0.769697] pci 0000:00:10.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
Oct  5 23:15:38 faye kernel: [    0.769708] pci 0000:00:03.0: setting latency timer to 64
Oct  5 23:15:38 faye kernel: [    0.769714] pci 0000:00:07.0: setting latency timer to 64
Oct  5 23:15:38 faye kernel: [    0.769719] pci 0000:00:10.0: setting latency timer to 64
Oct  5 23:15:38 faye kernel: [    0.769722] bus: 00 index 0 io port: [0x00-0xffff]
Oct  5 23:15:38 faye kernel: [    0.769724] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
Oct  5 23:15:38 faye kernel: [    0.769726] bus: 01 index 0 io port: [0xb000-0xbfff]
Oct  5 23:15:38 faye kernel: [    0.769728] bus: 01 index 1 mmio: [0xfa000000-0xfcffffff]
Oct  5 23:15:38 faye kernel: [    0.769730] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
Oct  5 23:15:38 faye kernel: [    0.769732] bus: 01 index 3 mmio: [0x0-0x0]
Oct  5 23:15:38 faye kernel: [    0.769734] bus: 02 index 0 io port: [0x7000-0x8fff]
Oct  5 23:15:38 faye kernel: [    0.769736] bus: 02 index 1 mmio: [0xfdc00000-0xfdcfffff]
Oct  5 23:15:38 faye kernel: [    0.769737] bus: 02 index 2 mmio: [0xfdb00000-0xfdbfffff]
Oct  5 23:15:38 faye kernel: [    0.769739] bus: 02 index 3 mmio: [0x0-0x0]
Oct  5 23:15:38 faye kernel: [    0.769741] bus: 03 index 0 io port: [0x9000-0xafff]
Oct  5 23:15:38 faye kernel: [    0.769743] bus: 03 index 1 mmio: [0xfde00000-0xfdffffff]
Oct  5 23:15:38 faye kernel: [    0.769745] bus: 03 index 2 mmio: [0xfdd00000-0xfddfffff]
Oct  5 23:15:38 faye kernel: [    0.769746] bus: 03 index 3 io port: [0x00-0xffff]
Oct  5 23:15:38 faye kernel: [    0.769748] bus: 03 index 4 mmio: [0x000000-0xffffffffffffffff]
Oct  5 23:15:38 faye kernel: [    0.769755] NET: Registered protocol family 2
Oct  5 23:15:38 faye kernel: [    0.800055] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct  5 23:15:38 faye kernel: [    0.800282] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct  5 23:15:38 faye kernel: [    0.800662] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct  5 23:15:38 faye kernel: [    0.800899] TCP: Hash tables configured (established 131072 bind 65536)
Oct  5 23:15:38 faye kernel: [    0.800901] TCP reno registered
Oct  5 23:15:38 faye kernel: [    0.810082] NET: Registered protocol family 1
Oct  5 23:15:38 faye kernel: [    0.810179] checking if image is initramfs... it is
Oct  5 23:15:38 faye kernel: [    1.357970] Freeing initrd memory: 7405k freed
Oct  5 23:15:38 faye kernel: [    1.358198] cpufreq: No nForce2 chipset.
Oct  5 23:15:38 faye kernel: [    1.358323] audit: initializing netlink socket (disabled)
Oct  5 23:15:38 faye kernel: [    1.358347] type=2000 audit(1254777318.350:1): initialized
Oct  5 23:15:38 faye kernel: [    1.365036] highmem bounce pool size: 64 pages
Oct  5 23:15:38 faye kernel: [    1.365040] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Oct  5 23:15:38 faye kernel: [    1.366137] VFS: Disk quotas dquot_6.5.1
Oct  5 23:15:38 faye kernel: [    1.366188] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct  5 23:15:38 faye kernel: [    1.366710] fuse init (API version 7.10)
Oct  5 23:15:38 faye kernel: [    1.366781] msgmni has been set to 1640
Oct  5 23:15:38 faye kernel: [    1.366936] alg: No test for stdrng (krng)
Oct  5 23:15:38 faye kernel: [    1.366945] io scheduler noop registered
Oct  5 23:15:38 faye kernel: [    1.366947] io scheduler anticipatory registered
Oct  5 23:15:38 faye kernel: [    1.366949] io scheduler deadline registered (default)
Oct  5 23:15:38 faye kernel: [    1.366960] io scheduler cfq registered
Oct  5 23:15:38 faye kernel: [    1.367123] pci 0000:00:03.0: Disabling HT MSI mapping<6>pci 0000:00:07.0: Disabling HT MSI mapping<6>pci 0000:00:09.0: Disabling HT MSI mapping<6>pci 0000:00:0e.0: Disabling HT MSI mapping<6>pci 0000:00:0f.0: Disabling HT MSI mapping<6>pci 0000:00:10.0: Disabling HT MSI mapping<6>pci 0000:00:10.1: Disabling HT MSI mapping<7>pci 0000:01:00.0: Boot video device
Oct  5 23:15:38 faye kernel: [    1.387441] pcieport-driver 0000:00:03.0: setting latency timer to 64
Oct  5 23:15:38 faye kernel: [    1.387481] pcieport-driver 0000:00:03.0: found MSI capability
Oct  5 23:15:38 faye kernel: [    1.387504] pcieport-driver 0000:00:03.0: irq 2303 for MSI/MSI-X
Oct  5 23:15:38 faye kernel: [    1.387513] pci_express 0000:00:03.0:pcie00: allocate port service
Oct  5 23:15:38 faye kernel: [    1.387526] pci_express 0000:00:03.0:pcie03: allocate port service
Oct  5 23:15:38 faye kernel: [    1.387575] pcieport-driver 0000:00:07.0: setting latency timer to 64
Oct  5 23:15:38 faye kernel: [    1.387613] pcieport-driver 0000:00:07.0: found MSI capability
Oct  5 23:15:38 faye kernel: [    1.387633] pcieport-driver 0000:00:07.0: irq 2302 for MSI/MSI-X
Oct  5 23:15:38 faye kernel: [    1.387642] pci_express 0000:00:07.0:pcie00: allocate port service
Oct  5 23:15:38 faye kernel: [    1.387653] pci_express 0000:00:07.0:pcie03: allocate port service
Oct  5 23:15:38 faye kernel: [    1.387709] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct  5 23:15:38 faye kernel: [    1.387717] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Oct  5 23:15:38 faye kernel: [    1.387871] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Oct  5 23:15:38 faye kernel: [    1.387873] ACPI: Power Button (FF) [PWRF]
Oct  5 23:15:38 faye kernel: [    1.387910] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Oct  5 23:15:38 faye kernel: [    1.387912] ACPI: Power Button (CM) [PWRB]
Oct  5 23:15:38 faye kernel: [    1.387972] fan PNP0C0B:00: registered as cooling_device0
Oct  5 23:15:38 faye kernel: [    1.387977] ACPI: Fan [FAN] (on)
Oct  5 23:15:38 faye kernel: [    1.388538] processor ACPI_CPU:00: registered as cooling_device1
Oct  5 23:15:38 faye kernel: [    1.388799] processor ACPI_CPU:01: registered as cooling_device2
Oct  5 23:15:38 faye kernel: [    1.392974] thermal LNXTHERM:01: registered as thermal_zone0
Oct  5 23:15:38 faye kernel: [    1.393351] ACPI: Thermal Zone [THRM] (40 C)
Oct  5 23:15:38 faye kernel: [    1.393402] isapnp: Scanning for PnP cards...
Oct  5 23:15:38 faye kernel: [    1.749166] isapnp: No Plug & Play device found
Oct  5 23:15:38 faye kernel: [    1.761434] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Oct  5 23:15:38 faye kernel: [    1.761529] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct  5 23:15:38 faye kernel: [    1.761900] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct  5 23:15:38 faye kernel: [    1.762583] brd: module loaded
Oct  5 23:15:38 faye kernel: [    1.762854] loop: module loaded
Oct  5 23:15:38 faye kernel: [    1.762910] Fixed MDIO Bus: probed
Oct  5 23:15:38 faye kernel: [    1.762915] PPP generic driver version 2.4.2
Oct  5 23:15:38 faye kernel: [    1.762962] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Oct  5 23:15:38 faye kernel: [    1.762986] Driver 'sd' needs updating - please use bus_type methods
Oct  5 23:15:38 faye kernel: [    1.762994] Driver 'sr' needs updating - please use bus_type methods
Oct  5 23:15:38 faye kernel: [    1.763034] ahci 0000:02:00.0: version 3.0
Oct  5 23:15:38 faye kernel: [    1.763345] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
Oct  5 23:15:38 faye kernel: [    1.763351] ahci 0000:02:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
Oct  5 23:15:38 faye kernel: [    1.781272] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 1 ports 3 Gbps 0x1 impl SATA mode
Oct  5 23:15:38 faye kernel: [    1.781275] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Oct  5 23:15:38 faye kernel: [    1.781280] ahci 0000:02:00.0: setting latency timer to 64
Oct  5 23:15:38 faye kernel: [    1.781388] scsi0 : ahci
Oct  5 23:15:38 faye kernel: [    1.781441] ata1: SATA max UDMA/133 abar m8192@0xfdcfe000 port 0xfdcfe100 irq 16
Oct  5 23:15:38 faye kernel: [    2.130021] ata1: SATA link down (SStatus 0 SControl 300)
Oct  5 23:15:38 faye kernel: [    2.150164] sata_nv 0000:00:0e.0: version 3.5
Oct  5 23:15:38 faye kernel: [    2.150466] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Oct  5 23:15:38 faye kernel: [    2.150470] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Oct  5 23:15:38 faye kernel: [    2.150472] sata_nv 0000:00:0e.0: Using SWNCQ mode
Oct  5 23:15:38 faye kernel: [    2.150507] sata_nv 0000:00:0e.0: setting latency timer to 64
Oct  5 23:15:38 faye kernel: [    2.150617] scsi1 : sata_nv
Oct  5 23:15:38 faye kernel: [    2.150672] scsi2 : sata_nv
Oct  5 23:15:38 faye kernel: [    2.150813] ata2: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 23
Oct  5 23:15:38 faye kernel: [    2.150816] ata3: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 23
Oct  5 23:15:38 faye kernel: [    3.060040] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct  5 23:15:38 faye kernel: [    3.080555] ata2.00: ATA-8: MAXTOR STM3500320AS, MX15, max UDMA/133
Oct  5 23:15:38 faye kernel: [    3.080557] ata2.00: 976773168 sectors, multi 1: LBA48 NCQ (depth 31/32)
Oct  5 23:15:38 faye kernel: [    3.120575] ata2.00: configured for UDMA/133
Oct  5 23:15:38 faye kernel: [    4.030035] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct  5 23:15:38 faye kernel: [    4.092749] ata3.00: ATA-7: MAXTOR STM3160215AS, 3.AAD, max UDMA/133
Oct  5 23:15:38 faye kernel: [    4.092751] ata3.00: 312581808 sectors, multi 1: LBA48 NCQ (depth 31/32)
Oct  5 23:15:38 faye kernel: [    4.184404] ata3.00: configured for UDMA/133
Oct  5 23:15:38 faye kernel: [    4.184489] scsi 1:0:0:0: Direct-Access     ATA      MAXTOR STM350032 MX15 PQ: 0 ANSI: 5
Oct  5 23:15:38 faye kernel: [    4.184564] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
Oct  5 23:15:38 faye kernel: [    4.184577] sd 1:0:0:0: [sda] Write Protect is off
Oct  5 23:15:38 faye kernel: [    4.184579] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct  5 23:15:38 faye kernel: [    4.184601] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  5 23:15:38 faye kernel: [    4.184654] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
Oct  5 23:15:38 faye kernel: [    4.184666] sd 1:0:0:0: [sda] Write Protect is off
Oct  5 23:15:38 faye kernel: [    4.184668] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct  5 23:15:38 faye kernel: [    4.184688] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  5 23:15:38 faye kernel: [    4.184691]  sda: sda1 sda2 < sda5 >
Oct  5 23:15:38 faye kernel: [    4.219341] sd 1:0:0:0: [sda] Attached SCSI disk
Oct  5 23:15:38 faye kernel: [    4.219378] sd 1:0:0:0: Attached scsi generic sg0 type 0
Oct  5 23:15:38 faye kernel: [    4.219441] scsi 2:0:0:0: Direct-Access     ATA      MAXTOR STM316021 3.AA PQ: 0 ANSI: 5
Oct  5 23:15:38 faye kernel: [    4.219510] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Oct  5 23:15:38 faye kernel: [    4.219523] sd 2:0:0:0: [sdb] Write Protect is off
Oct  5 23:15:38 faye kernel: [    4.219525] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Oct  5 23:15:38 faye kernel: [    4.219546] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  5 23:15:38 faye kernel: [    4.219591] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Oct  5 23:15:38 faye kernel: [    4.219603] sd 2:0:0:0: [sdb] Write Protect is off
Oct  5 23:15:38 faye kernel: [    4.219605] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Oct  5 23:15:38 faye kernel: [    4.219625] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  5 23:15:38 faye kernel: [    4.219628]  sdb: sdb1
Oct  5 23:15:38 faye kernel: [    4.240792] sd 2:0:0:0: [sdb] Attached SCSI disk
Oct  5 23:15:38 faye kernel: [    4.240822] sd 2:0:0:0: Attached scsi generic sg1 type 0
Oct  5 23:15:38 faye kernel: [    4.241140] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
Oct  5 23:15:38 faye kernel: [    4.241144] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
Oct  5 23:15:38 faye kernel: [    4.241146] sata_nv 0000:00:0f.0: Using SWNCQ mode
Oct  5 23:15:38 faye kernel: [    4.241181] sata_nv 0000:00:0f.0: setting latency timer to 64
Oct  5 23:15:38 faye kernel: [    4.241315] scsi3 : sata_nv
Oct  5 23:15:38 faye kernel: [    4.241365] scsi4 : sata_nv
Oct  5 23:15:38 faye kernel: [    4.241510] ata4: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 22
Oct  5 23:15:38 faye kernel: [    4.241513] ata5: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 22
Oct  5 23:15:38 faye kernel: [    5.150049] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct  5 23:15:38 faye kernel: [    5.170160] ata4.00: ATAPI: ASUS    DRW-22B1LT, 1.00, max UDMA/100
Oct  5 23:15:38 faye kernel: [    5.210177] ata4.00: configured for UDMA/100
Oct  5 23:15:38 faye kernel: [    5.970568] ata5: SATA link down (SStatus 0 SControl 300)
Oct  5 23:15:38 faye kernel: [    5.972941] scsi 3:0:0:0: CD-ROM            ASUS     DRW-22B1LT       1.00 PQ: 0 ANSI: 5
Oct  5 23:15:38 faye kernel: [    5.979696] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
Oct  5 23:15:38 faye kernel: [    5.979699] Uniform CD-ROM driver Revision: 3.20
Oct  5 23:15:38 faye kernel: [    5.979777] sr 3:0:0:0: Attached scsi CD-ROM sr0
Oct  5 23:15:38 faye kernel: [    5.979810] sr 3:0:0:0: Attached scsi generic sg2 type 5
Oct  5 23:15:38 faye kernel: [    5.979899] pata_amd 0000:00:0d.0: version 0.3.10
Oct  5 23:15:38 faye kernel: [    5.979933] pata_amd 0000:00:0d.0: setting latency timer to 64
Oct  5 23:15:38 faye kernel: [    5.979987] scsi5 : pata_amd
Oct  5 23:15:38 faye kernel: [    5.980041] scsi6 : pata_amd
Oct  5 23:15:38 faye kernel: [    5.980601] ata6: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
Oct  5 23:15:38 faye kernel: [    5.980604] ata7: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
Oct  5 23:15:38 faye kernel: [    6.340290] ata7.01: ATAPI: ASUS    DRW-2014S1, 1.01, max UDMA/66
Oct  5 23:15:38 faye kernel: [    6.340312] ata7: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5) ACPI=0x1f01f (600:30:0x1c)
Oct  5 23:15:38 faye kernel: [    6.380242] ata7.01: configured for UDMA/66
Oct  5 23:15:38 faye kernel: [    6.380911] scsi 6:0:1:0: CD-ROM            ASUS     DRW-2014S1       1.01 PQ: 0 ANSI: 5
Oct  5 23:15:38 faye kernel: [    6.383939] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Oct  5 23:15:38 faye kernel: [    6.383990] sr 6:0:1:0: Attached scsi CD-ROM sr1
Oct  5 23:15:38 faye kernel: [    6.384021] sr 6:0:1:0: Attached scsi generic sg3 type 5
Oct  5 23:15:38 faye kernel: [    6.384527] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct  5 23:15:38 faye kernel: [    6.384847] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
Oct  5 23:15:38 faye kernel: [    6.384851] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
Oct  5 23:15:38 faye kernel: [    6.384861] ehci_hcd 0000:00:0b.1: setting latency timer to 64
Oct  5 23:15:38 faye kernel: [    6.384864] ehci_hcd 0000:00:0b.1: EHCI Host Controller
Oct  5 23:15:38 faye kernel: [    6.384922] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
Oct  5 23:15:38 faye kernel: [    6.384948] ehci_hcd 0000:00:0b.1: debug port 1
Oct  5 23:15:38 faye kernel: [    6.384953] ehci_hcd 0000:00:0b.1: cache line size of 32 is not supported
Oct  5 23:15:38 faye kernel: [    6.384967] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfe02e000
Oct  5 23:15:38 faye kernel: [    6.400010] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
Oct  5 23:15:38 faye kernel: [    6.400072] usb usb1: configuration #1 chosen from 1 choice
Oct  5 23:15:38 faye kernel: [    6.400096] hub 1-0:1.0: USB hub found
Oct  5 23:15:38 faye kernel: [    6.400104] hub 1-0:1.0: 8 ports detected
Oct  5 23:15:38 faye kernel: [    6.400491] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Oct  5 23:15:38 faye kernel: [    6.400496] ehci_hcd 0000:03:06.2: PCI INT C -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Oct  5 23:15:38 faye kernel: [    6.400501] ehci_hcd 0000:03:06.2: PCI INT C disabled
Oct  5 23:15:38 faye kernel: [    6.400504] ehci_hcd 0000:03:06.2: init 0000:03:06.2 fail, -16
Oct  5 23:15:38 faye kernel: [    6.400560] ehci_hcd: probe of 0000:03:06.2 failed with error -16
Oct  5 23:15:38 faye kernel: [    6.400572] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Oct  5 23:15:38 faye kernel: [    6.400882] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
Oct  5 23:15:38 faye kernel: [    6.400886] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
Oct  5 23:15:38 faye kernel: [    6.400895] ohci_hcd 0000:00:0b.0: setting latency timer to 64
Oct  5 23:15:38 faye kernel: [    6.400898] ohci_hcd 0000:00:0b.0: OHCI Host Controller
Oct  5 23:15:38 faye kernel: [    6.400935] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
Oct  5 23:15:38 faye kernel: [    6.400955] ohci_hcd 0000:00:0b.0: irq 20, io mem 0xfe02f000
Oct  5 23:15:38 faye kernel: [    6.462064] usb usb2: configuration #1 chosen from 1 choice
Oct  5 23:15:38 faye kernel: [    6.462088] hub 2-0:1.0: USB hub found
Oct  5 23:15:38 faye kernel: [    6.462095] hub 2-0:1.0: 8 ports detected
Oct  5 23:15:38 faye kernel: [    6.462473] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Oct  5 23:15:38 faye kernel: [    6.462476] ohci_hcd 0000:03:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
Oct  5 23:15:38 faye kernel: [    6.462482] ohci_hcd 0000:03:06.0: PCI INT A disabled
Oct  5 23:15:38 faye kernel: [    6.462484] ohci_hcd 0000:03:06.0: init 0000:03:06.0 fail, -16
Oct  5 23:15:38 faye kernel: [    6.462538] ohci_hcd: probe of 0000:03:06.0 failed with error -16
Oct  5 23:15:38 faye kernel: [    6.462838] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
Oct  5 23:15:38 faye kernel: [    6.462842] ohci_hcd 0000:03:06.1: PCI INT B -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
Oct  5 23:15:38 faye kernel: [    6.462848] ohci_hcd 0000:03:06.1: PCI INT B disabled
Oct  5 23:15:38 faye kernel: [    6.462850] ohci_hcd 0000:03:06.1: init 0000:03:06.1 fail, -16
Oct  5 23:15:38 faye kernel: [    6.462903] ohci_hcd: probe of 0000:03:06.1 failed with error -16
Oct  5 23:15:38 faye kernel: [    6.462913] uhci_hcd: USB Universal Host Controller Interface driver
Oct  5 23:15:38 faye kernel: [    6.462986] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct  5 23:15:38 faye kernel: [    6.463314] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct  5 23:15:38 faye kernel: [    6.463318] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct  5 23:15:38 faye kernel: [    6.470033] mice: PS/2 mouse device common for all mice
Oct  5 23:15:38 faye kernel: [    6.500070] rtc_cmos 00:05: RTC can wake from S4
Oct  5 23:15:38 faye kernel: [    6.500100] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Oct  5 23:15:38 faye kernel: [    6.500130] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Oct  5 23:15:38 faye kernel: [    6.500179] device-mapper: uevent: version 1.0.3
Oct  5 23:15:38 faye kernel: [    6.500265] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Oct  5 23:15:38 faye kernel: [    6.500324] device-mapper: multipath: version 1.0.5 loaded
Oct  5 23:15:38 faye kernel: [    6.500326] device-mapper: multipath round-robin: version 1.0.0 loaded
Oct  5 23:15:38 faye kernel: [    6.500395] EISA: Probing bus 0 at eisa.0
Oct  5 23:15:38 faye kernel: [    6.500401] Cannot allocate resource for EISA slot 1
Oct  5 23:15:38 faye kernel: [    6.500418] Cannot allocate resource for EISA slot 7
Oct  5 23:15:38 faye kernel: [    6.500420] Cannot allocate resource for EISA slot 8
Oct  5 23:15:38 faye kernel: [    6.500422] EISA: Detected 0 cards.
Oct  5 23:15:38 faye kernel: [    6.500463] cpuidle: using governor ladder
Oct  5 23:15:38 faye kernel: [    6.500464] cpuidle: using governor menu
Oct  5 23:15:38 faye kernel: [    6.500907] TCP cubic registered
Oct  5 23:15:38 faye kernel: [    6.501015] NET: Registered protocol family 10
Oct  5 23:15:38 faye kernel: [    6.501398] lo: Disabled Privacy Extensions
Oct  5 23:15:38 faye kernel: [    6.501693] NET: Registered protocol family 17
Oct  5 23:15:38 faye kernel: [    6.501706] Bluetooth: L2CAP ver 2.11
Oct  5 23:15:38 faye kernel: [    6.501708] Bluetooth: L2CAP socket layer initialized
Oct  5 23:15:38 faye kernel: [    6.501711] Bluetooth: SCO (Voice Link) ver 0.6
Oct  5 23:15:38 faye kernel: [    6.501712] Bluetooth: SCO socket layer initialized
Oct  5 23:15:38 faye kernel: [    6.501738] Bluetooth: RFCOMM socket layer initialized
Oct  5 23:15:38 faye kernel: [    6.501745] Bluetooth: RFCOMM TTY layer initialized
Oct  5 23:15:38 faye kernel: [    6.501747] Bluetooth: RFCOMM ver 1.10
Oct  5 23:15:38 faye kernel: [    6.501789] Using IPI No-Shortcut mode
Oct  5 23:15:38 faye kernel: [    6.501846] registered taskstats version 1
Oct  5 23:15:38 faye kernel: [    6.501987]   Magic number: 13:347:297
Oct  5 23:15:38 faye kernel: [    6.502056] rtc_cmos 00:05: setting system clock to 2009-10-05 21:15:24 UTC (1254777324)
Oct  5 23:15:38 faye kernel: [    6.502059] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct  5 23:15:38 faye kernel: [    6.502060] EDD information not available.
Oct  5 23:15:38 faye kernel: [    6.502334] Freeing unused kernel memory: 548k freed
Oct  5 23:15:38 faye kernel: [    6.502440] Write protecting the kernel text: 4172k
Oct  5 23:15:38 faye kernel: [    6.502518] Write protecting the kernel read-only data: 1544k
Oct  5 23:15:38 faye kernel: [    6.517995] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Oct  5 23:15:38 faye kernel: [    6.721272] usb 1-2: new high speed USB device using ehci_hcd and address 2
Oct  5 23:15:38 faye kernel: [    6.735533] Floppy drive(s): fd0 is 1.44M
Oct  5 23:15:38 faye kernel: [    6.763907] FDC 0 is a post-1991 82077
Oct  5 23:15:38 faye kernel: [    6.832814] ohci1394 0000:03:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Oct  5 23:15:38 faye kernel: [    6.885990] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fdffd000-fdffd7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Oct  5 23:15:38 faye kernel: [    6.895382] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Oct  5 23:15:38 faye kernel: [    6.895741] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
Oct  5 23:15:38 faye kernel: [    6.895745] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Oct  5 23:15:38 faye kernel: [    6.895750] forcedeth 0000:00:14.0: setting latency timer to 64
Oct  5 23:15:38 faye kernel: [    6.895808] nv_probe: set workaround bit for reversed mac addr
Oct  5 23:15:38 faye kernel: [    7.031629] usb 1-2: configuration #1 chosen from 1 choice
Oct  5 23:15:38 faye kernel: [    7.420781] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1d:60:0c:10:26
Oct  5 23:15:38 faye kernel: [    7.420784] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
Oct  5 23:15:38 faye kernel: [    7.482427] PM: Starting manual resume from disk
Oct  5 23:15:38 faye kernel: [    7.482430] PM: Resume from partition 8:5
Oct  5 23:15:38 faye kernel: [    7.482432] PM: Checking hibernation image.
Oct  5 23:15:38 faye kernel: [    7.482711] PM: Resume from disk failed.
Oct  5 23:15:38 faye kernel: [    7.495224] EXT3-fs: INFO: recovery required on readonly filesystem.
Oct  5 23:15:38 faye kernel: [    7.495227] EXT3-fs: write access will be enabled during recovery.
Oct  5 23:15:38 faye kernel: [    8.210127] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80001681bc6]
Oct  5 23:15:38 faye kernel: [    9.875195] kjournald starting.  Commit interval 5 seconds
Oct  5 23:15:38 faye kernel: [    9.875209] EXT3-fs: sda1: orphan cleanup on readonly fs
Oct  5 23:15:38 faye kernel: [    9.875214] ext3_orphan_cleanup: deleting unreferenced inode 18227566
Oct  5 23:15:38 faye kernel: [   10.119794] ext3_orphan_cleanup: deleting unreferenced inode 15818776
Oct  5 23:15:38 faye kernel: [   10.119805] ext3_orphan_cleanup: deleting unreferenced inode 15794182
Oct  5 23:15:38 faye kernel: [   10.119811] ext3_orphan_cleanup: deleting unreferenced inode 15794181
Oct  5 23:15:38 faye kernel: [   10.119817] ext3_orphan_cleanup: deleting unreferenced inode 15794180
Oct  5 23:15:38 faye kernel: [   10.119823] ext3_orphan_cleanup: deleting unreferenced inode 15794179
Oct  5 23:15:38 faye kernel: [   10.119828] ext3_orphan_cleanup: deleting unreferenced inode 15794178
Oct  5 23:15:38 faye kernel: [   10.119833] EXT3-fs: sda1: 7 orphan inodes deleted
Oct  5 23:15:38 faye kernel: [   10.119835] EXT3-fs: recovery complete.
Oct  5 23:15:38 faye kernel: [   10.130247] EXT3-fs: mounted filesystem with ordered data mode.
Oct  5 23:15:38 faye kernel: [   14.513597] udev: starting version 141
Oct  5 23:15:38 faye kernel: [   15.141804] ACPI: I/O resource nForce2_smbus [0x1c00-0x1c3f] conflicts with ACPI region SM00 [0x1c00-0x1c05]
Oct  5 23:15:38 faye kernel: [   15.141807] ACPI: Device needs an ACPI driver
Oct  5 23:15:38 faye kernel: [   15.141839] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Oct  5 23:15:38 faye kernel: [   15.141857] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c80
Oct  5 23:15:38 faye kernel: [   15.200274] Linux agpgart interface v0.103
Oct  5 23:15:38 faye kernel: [   15.224784] input: PC Speaker as /devices/platform/pcspkr/input/input4
Oct  5 23:15:38 faye kernel: [   15.237740] Linux video capture interface: v2.00
Oct  5 23:15:38 faye kernel: [   15.248344] parport_pc 00:0a: reported by Plug and Play ACPI
Oct  5 23:15:38 faye kernel: [   15.248372] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Oct  5 23:15:38 faye kernel: [   15.259811] ppdev: user-space parallel port driver
Oct  5 23:15:38 faye kernel: [   15.308360] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Oct  5 23:15:38 faye kernel: [   15.396214] nvidia: module license 'NVIDIA' taints kernel.
Oct  5 23:15:38 faye kernel: [   15.542963] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Oct  5 23:15:38 faye kernel: [   15.542968] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
Oct  5 23:15:38 faye kernel: [   15.543196] HDA Intel 0000:00:10.1: setting latency timer to 64
Oct  5 23:15:38 faye kernel: [   15.576625] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a4)
Oct  5 23:15:38 faye kernel: [   15.597804] input: UVC Camera (046d:09a4) as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2:1.0/input/input5
Oct  5 23:15:38 faye kernel: [   15.651699] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
Oct  5 23:15:38 faye kernel: [   15.651704] nvidia 0000:01:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
Oct  5 23:15:38 faye kernel: [   15.651712] nvidia 0000:01:00.0: setting latency timer to 64
Oct  5 23:15:38 faye kernel: [   15.651869] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Oct  5 23:15:38 faye kernel: [   15.653855] usbcore: registered new interface driver uvcvideo
Oct  5 23:15:38 faye kernel: [   15.653859] USB Video Class driver (v0.1.0)
Oct  5 23:15:38 faye kernel: [   15.676125] usbcore: registered new interface driver snd-usb-audio
Oct  5 23:15:38 faye kernel: [   15.766104] psmouse serio1: ID: 10 00 64<4>logips2pp: Detected unknown logitech mouse model 106
Oct  5 23:15:38 faye kernel: [   16.295117] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
Oct  5 23:15:38 faye kernel: [   17.083537] lp0: using parport0 (interrupt-driven).
Oct  5 23:15:38 faye kernel: [   17.105980] it87: Found IT8718F chip at 0x290, revision 2
Oct  5 23:15:38 faye kernel: [   17.105989] it87: in3 is VCC (+5V)
Oct  5 23:15:38 faye kernel: [   17.105990] it87: in7 is VCCH (+5V Stand-By)
Oct  5 23:15:38 faye kernel: [   17.115108] coretemp coretemp.0: Using relative temperature scale!
Oct  5 23:15:38 faye kernel: [   17.115145] coretemp coretemp.1: Using relative temperature scale!
Oct  5 23:15:38 faye kernel: [   17.192110] Adding 10586792k swap on /dev/sda5.  Priority:-1 extents:1 across:10586792k
Oct  5 23:15:38 faye kernel: [   17.724188] EXT3 FS on sda1, internal journal
Oct  5 23:15:38 faye kernel: [   18.806934] type=1505 audit(1254777336.797:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2226
Oct  5 23:15:38 faye kernel: [   18.847278] type=1505 audit(1254777336.837:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2230
Oct  5 23:15:38 faye kernel: [   18.847371] type=1505 audit(1254777336.837:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2230
Oct  5 23:15:38 faye kernel: [   18.847406] type=1505 audit(1254777336.837:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2230
Oct  5 23:15:38 faye kernel: [   18.847441] type=1505 audit(1254777336.837:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2230
Oct  5 23:15:38 faye kernel: [   18.871664] type=1505 audit(1254777336.867:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2235
Oct  5 23:15:38 faye kernel: [   18.982998] type=1505 audit(1254777336.977:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2239
Oct  5 23:15:38 faye kernel: [   18.983171] type=1505 audit(1254777336.977:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2239
Oct  5 23:15:38 faye kernel: [   19.009240] type=1505 audit(1254777336.997:10): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2243
Oct  5 23:15:38 faye kernel: [   19.032442] type=1505 audit(1254777337.027:11): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2247
Oct  5 23:15:48 faye kernel: [   30.865007] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Oct  5 23:15:48 faye kernel: [   30.865010] vboxdrv: Successfully done.
Oct  5 23:15:48 faye kernel: [   30.865011] vboxdrv: Found 2 processor cores.
Oct  5 23:15:48 faye kernel: [   30.865080] vboxdrv: fAsync=0 offMin=0x1b8 offMax=0x898
Oct  5 23:15:48 faye kernel: [   30.865130] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Oct  5 23:15:48 faye kernel: [   30.865132] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
Oct  5 23:15:50 faye kernel: [   32.533753] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Oct  5 23:15:50 faye kernel: [   32.533755] Bluetooth: BNEP filters: protocol multicast
Oct  5 23:15:50 faye kernel: [   32.595180] Bridge firewalling registered
Oct  5 23:16:03 faye kernel: [   48.851261] eth0: no IPv6 routers present
Oct  5 23:24:19 faye kernel: [  544.610532] UDP: bad checksum. From 69.70.118.58:24060 to 192.168.0.2:4672 ulen 43
Oct  5 23:38:44 faye kernel: Inspecting /boot/System.map-2.6.28-15-server
Oct  5 23:38:44 faye kernel: Cannot find map file.
Oct  5 23:38:44 faye kernel: Loaded 75739 symbols from 48 modules.
Oct  5 23:38:44 faye kernel: [    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
Oct  5 23:38:44 faye kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct  5 23:38:44 faye kernel: [    0.000000] Initializing cgroup subsys cpu
Oct  5 23:38:44 faye kernel: [    0.000000] Linux version 2.6.28-15-server (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #52-Ubuntu SMP Wed Sep 9 11:50:50 UTC 2009 (Ubuntu 2.6.28-15.52-server)
Oct  5 23:38:44 faye kernel: [    0.000000] KERNEL supported cpus:
Oct  5 23:38:44 faye kernel: [    0.000000]   Intel GenuineIntel
Oct  5 23:38:44 faye kernel: [    0.000000]   AMD AuthenticAMD
Oct  5 23:38:44 faye kernel: [    0.000000]   NSC Geode by NSC
Oct  5 23:38:44 faye kernel: [    0.000000]   Cyrix CyrixInstead
Oct  5 23:38:44 faye kernel: [    0.000000]   Centaur CentaurHauls
Oct  5 23:38:44 faye kernel: [    0.000000]   Transmeta GenuineTMx86
Oct  5 23:38:44 faye kernel: [    0.000000]   Transmeta TransmetaCPU
Oct  5 23:38:44 faye kernel: [    0.000000]   UMC UMC UMC UMC
Oct  5 23:38:44 faye kernel: [    0.000000] BIOS-provided physical RAM map:
Oct  5 23:38:44 faye kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Oct  5 23:38:44 faye kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Oct  5 23:38:44 faye kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Oct  5 23:38:44 faye kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfef0000 (usable)
Oct  5 23:38:44 faye kernel: [    0.000000]  BIOS-e820: 00000000dfef0000 - 00000000dfef3000 (ACPI NVS)
Oct  5 23:38:44 faye kernel: [    0.000000]  BIOS-e820: 00000000dfef3000 - 00000000dff00000 (ACPI data)
Oct  5 23:38:44 faye kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f2000000 (reserved)
Oct  5 23:38:44 faye kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Oct  5 23:38:44 faye kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
Oct  5 23:38:44 faye kernel: [    0.000000] DMI 2.4 present.
Oct  5 23:38:44 faye kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Oct  5 23:38:44 faye kernel: [    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x1000000
Oct  5 23:38:44 faye kernel: [    0.000000] Scanning 0 areas for low memory corruption
Oct  5 23:38:44 faye kernel: [    0.000000] modified physical RAM map:
Oct  5 23:38:44 faye kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Oct  5 23:38:44 faye kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Oct  5 23:38:44 faye kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Oct  5 23:38:44 faye kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Oct  5 23:38:44 faye kernel: [    0.000000]  modified: 0000000000100000 - 00000000dfef0000 (usable)
Oct  5 23:38:44 faye kernel: [    0.000000]  modified: 00000000dfef0000 - 00000000dfef3000 (ACPI NVS)
Oct  5 23:38:44 faye kernel: [    0.000000]  modified: 00000000dfef3000 - 00000000dff00000 (ACPI data)
Oct  5 23:38:44 faye kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f2000000 (reserved)
Oct  5 23:38:44 faye kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Oct  5 23:38:44 faye kernel: [    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
Oct  5 23:38:44 faye kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-16000
Oct  5 23:38:44 faye kernel: [    0.000000] NX (Execute Disable) protection: active
Oct  5 23:38:44 faye kernel: [    0.000000] RAMDISK: 378b4000 - 37fef797
Oct  5 23:38:44 faye kernel: [    0.000000] Allocated new RAMDISK: 008ac000 - 00fe7797
Oct  5 23:38:44 faye kernel: [    0.000000] Move RAMDISK from 00000000378b4000 - 0000000037fef796 to 008ac000 - 00fe7796
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: RSDP 000F7910, 0024 (r2 Nvidia)
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: XSDT DFEF30C0, 004C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: FACP DFEF9880, 00F4 (r3 Nvidia ASUSACPI 42302E31 AWRD        0)
Oct  5 23:38:44 faye kernel: [    0.000000] FADT: X_PM1a_EVT_BLK.bit_width (8) does not match PM1_EVT_LEN (4)
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: DSDT DFEF3240, 65DB (r1 NVIDIA ASUSACPI     1000 MSFT  3000000)
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: FACS DFEF0000, 0040
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: HPET DFEF9AC0, 0038 (r1 Nvidia ASUSACPI 42302E31 AWRD       98)
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: MCFG DFEF9B40, 003C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: APIC DFEF99C0, 0098 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: SSDT DFEF9BC0, 087B (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct  5 23:38:44 faye kernel: [    0.000000] 3720MB HIGHMEM available.
Oct  5 23:38:44 faye kernel: [    0.000000] 887MB LOWMEM available.
Oct  5 23:38:44 faye kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Oct  5 23:38:44 faye kernel: [    0.000000]   low ram: 00000000 - 377fe000
Oct  5 23:38:44 faye kernel: [    0.000000]   bootmap 00013000 - 00019f00
Oct  5 23:38:44 faye kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Oct  5 23:38:44 faye kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Oct  5 23:38:44 faye kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Oct  5 23:38:44 faye kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Oct  5 23:38:44 faye kernel: [    0.000000]   #3 [0000100000 - 00008a29ac]    TEXT DATA BSS ==> [0000100000 - 00008a29ac]
Oct  5 23:38:44 faye kernel: [    0.000000]   #4 [00008a3000 - 00008ac000]    INIT_PG_TABLE ==> [00008a3000 - 00008ac000]
Oct  5 23:38:44 faye kernel: [    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Oct  5 23:38:44 faye kernel: [    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
Oct  5 23:38:44 faye kernel: [    0.000000]   #7 [00008ac000 - 0000fe7797]      NEW RAMDISK ==> [00008ac000 - 0000fe7797]
Oct  5 23:38:44 faye kernel: [    0.000000]   #8 [0000013000 - 000001a000]          BOOTMAP ==> [0000013000 - 000001a000]
Oct  5 23:38:44 faye kernel: [    0.000000] found SMP MP-table at [c00f5dd0] 000f5dd0
Oct  5 23:38:44 faye kernel: [    0.000000] Zone PFN ranges:
Oct  5 23:38:44 faye kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Oct  5 23:38:44 faye kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Oct  5 23:38:44 faye kernel: [    0.000000]   HighMem  0x000377fe -> 0x00120000
Oct  5 23:38:44 faye kernel: [    0.000000] Movable zone start PFN for each node
Oct  5 23:38:44 faye kernel: [    0.000000] early_node_map[3] active PFN ranges
Oct  5 23:38:44 faye kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Oct  5 23:38:44 faye kernel: [    0.000000]     0: 0x00000100 -> 0x000dfef0
Oct  5 23:38:44 faye kernel: [    0.000000]     0: 0x00100000 -> 0x00120000
Oct  5 23:38:44 faye kernel: [    0.000000] On node 0 totalpages: 1048191
Oct  5 23:38:44 faye kernel: [    0.000000] free_area_init_node: node 0, pgdat c06ded00, node_mem_map c1000200
Oct  5 23:38:44 faye kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Oct  5 23:38:44 faye kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct  5 23:38:44 faye kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Oct  5 23:38:44 faye kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Oct  5 23:38:44 faye kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Oct  5 23:38:44 faye kernel: [    0.000000]   HighMem zone: 7441 pages used for memmap
Oct  5 23:38:44 faye kernel: [    0.000000]   HighMem zone: 813537 pages, LIFO batch:31
Oct  5 23:38:44 faye kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Oct  5 23:38:44 faye kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: IRQ14 used by override.
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: IRQ15 used by override.
Oct  5 23:38:44 faye kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct  5 23:38:44 faye kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Oct  5 23:38:44 faye kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct  5 23:38:44 faye kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Oct  5 23:38:44 faye kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct  5 23:38:44 faye kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Oct  5 23:38:44 faye kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Oct  5 23:38:44 faye kernel: [    0.000000] Allocating PCI resources starting at e0000000 (gap: dff00000:10100000)
Oct  5 23:38:44 faye kernel: [    0.000000] PERCPU: Allocating 49152 bytes of per cpu data
Oct  5 23:38:44 faye kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Oct  5 23:38:44 faye kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1038974
Oct  5 23:38:44 faye kernel: [    0.000000] Kernel command line: root=UUID=50de47dc-b4a7-4fb8-bea0-e0087447c22d ro quiet splash 
Oct  5 23:38:44 faye kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct  5 23:38:44 faye kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct  5 23:38:44 faye kernel: [    0.000000] Initializing CPU#0
Oct  5 23:38:44 faye kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct  5 23:38:44 faye kernel: [    0.000000] Extended CMOS year: 2000
Oct  5 23:38:44 faye kernel: [    0.000000] Fast TSC calibration using PIT
Oct  5 23:38:44 faye kernel: [    0.000000] Detected 2199.712 MHz processor.
Oct  5 23:38:44 faye kernel: [    0.010000] spurious 8259A interrupt: IRQ7.
Oct  5 23:38:44 faye kernel: [    0.010000] Console: colour VGA+ 80x25
Oct  5 23:38:44 faye kernel: [    0.010000] console [tty0] enabled
Oct  5 23:38:44 faye kernel: [    0.010000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct  5 23:38:44 faye kernel: [    0.010000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct  5 23:38:44 faye kernel: [    0.010000] allocated 23592640 bytes of page_cgroup
Oct  5 23:38:44 faye kernel: [    0.010000] please try cgroup_disable=memory option if you don't want
Oct  5 23:38:44 faye kernel: [    0.010000] Scanning for low memory corruption every 60 seconds
Oct  5 23:38:44 faye kernel: [    0.010000] Memory: 4115652k/4718592k available (4169k kernel code, 76248k reserved, 2238k data, 548k init, 3283912k highmem)
Oct  5 23:38:44 faye kernel: [    0.010000] virtual kernel memory layout:
Oct  5 23:38:44 faye kernel: [    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
Oct  5 23:38:44 faye kernel: [    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
Oct  5 23:38:44 faye kernel: [    0.010000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Oct  5 23:38:44 faye kernel: [    0.010000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Oct  5 23:38:44 faye kernel: [    0.010000]       .init : 0xc0749000 - 0xc07d2000   ( 548 kB)
Oct  5 23:38:44 faye kernel: [    0.010000]       .data : 0xc05126b3 - 0xc0741fc0   (2238 kB)
Oct  5 23:38:44 faye kernel: [    0.010000]       .text : 0xc0100000 - 0xc05126b3   (4169 kB)
Oct  5 23:38:44 faye kernel: [    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Oct  5 23:38:44 faye kernel: [    0.010000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Oct  5 23:38:44 faye kernel: [    0.010000] hpet clockevent registered
Oct  5 23:38:44 faye kernel: [    0.010000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Oct  5 23:38:44 faye kernel: [    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4399.42 BogoMIPS (lpj=21997120)
Oct  5 23:38:44 faye kernel: [    0.010000] Security Framework initialized
Oct  5 23:38:44 faye kernel: [    0.010000] SELinux:  Disabled at boot.
Oct  5 23:38:44 faye kernel: [    0.010000] AppArmor: AppArmor initialized
Oct  5 23:38:44 faye kernel: [    0.010000] Mount-cache hash table entries: 512
Oct  5 23:38:44 faye kernel: [    0.010000] Initializing cgroup subsys ns
Oct  5 23:38:44 faye kernel: [    0.010000] Initializing cgroup subsys cpuacct
Oct  5 23:38:44 faye kernel: [    0.010000] Initializing cgroup subsys memory
Oct  5 23:38:44 faye kernel: [    0.010000] Initializing cgroup subsys freezer
Oct  5 23:38:44 faye kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct  5 23:38:44 faye kernel: [    0.010000] CPU: L2 cache: 2048K
Oct  5 23:38:44 faye kernel: [    0.010000] CPU: Physical Processor ID: 0
Oct  5 23:38:44 faye kernel: [    0.010000] CPU: Processor Core ID: 0
Oct  5 23:38:44 faye kernel: [    0.010000] using mwait in idle threads.
Oct  5 23:38:44 faye kernel: [    0.010000] Checking 'hlt' instruction... OK.
Oct  5 23:38:44 faye kernel: [    0.042210] ACPI: Core revision 20080926
Oct  5 23:38:44 faye kernel: [    0.043544] ACPI: Checking initramfs for custom DSDT
Oct  5 23:38:44 faye kernel: [    0.314051] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct  5 23:38:44 faye kernel: [    0.417776] CPU0: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
Oct  5 23:38:44 faye kernel: [    0.420000] Booting processor 1 APIC 0x1 ip 0x6000
Oct  5 23:38:44 faye kernel: [    0.010000] Initializing CPU#1
Oct  5 23:38:44 faye kernel: [    0.010000] Calibrating delay using timer specific routine.. 4399.96 BogoMIPS (lpj=21999832)
Oct  5 23:38:44 faye kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct  5 23:38:44 faye kernel: [    0.010000] CPU: L2 cache: 2048K
Oct  5 23:38:44 faye kernel: [    0.010000] CPU: Physical Processor ID: 0
Oct  5 23:38:44 faye kernel: [    0.010000] CPU: Processor Core ID: 1
Oct  5 23:38:44 faye kernel: [    0.570350] CPU1: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
Oct  5 23:38:44 faye kernel: [    0.570360] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Oct  5 23:38:44 faye kernel: [    0.580038] Brought up 2 CPUs
Oct  5 23:38:44 faye kernel: [    0.580040] Total of 2 processors activated (8799.39 BogoMIPS).
Oct  5 23:38:44 faye kernel: [    0.580117] CPU0 attaching sched-domain:
Oct  5 23:38:44 faye kernel: [    0.580119]  domain 0: span 0-1 level MC
Oct  5 23:38:44 faye kernel: [    0.580121]   groups: 0 1
Oct  5 23:38:44 faye kernel: [    0.580127] CPU1 attaching sched-domain:
Oct  5 23:38:44 faye kernel: [    0.580129]  domain 0: span 0-1 level MC
Oct  5 23:38:44 faye kernel: [    0.580131]   groups: 1 0
Oct  5 23:38:44 faye kernel: [    0.580197] net_namespace: 776 bytes
Oct  5 23:38:44 faye kernel: [    0.580197] Booting paravirtualized kernel on bare hardware
Oct  5 23:38:44 faye kernel: [    0.580292] Time: 21:38:06  Date: 10/05/09
Oct  5 23:38:44 faye kernel: [    0.580292] regulator: core version 0.5
Oct  5 23:38:44 faye kernel: [    0.580292] NET: Registered protocol family 16
Oct  5 23:38:44 faye kernel: [    0.580292] EISA bus registered
Oct  5 23:38:44 faye kernel: [    0.580292] ACPI: bus type pci registered
Oct  5 23:38:44 faye kernel: [    0.580292] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 31
Oct  5 23:38:44 faye kernel: [    0.580292] PCI: MCFG area at f0000000 reserved in E820
Oct  5 23:38:44 faye kernel: [    0.580292] PCI: Using MMCONFIG for extended config space
Oct  5 23:38:44 faye kernel: [    0.580292] PCI: Using configuration type 1 for base access
Oct  5 23:38:44 faye kernel: [    0.581168] ACPI: EC: Look up EC in DSDT
Oct  5 23:38:44 faye kernel: [    0.591946] ACPI: Interpreter enabled
Oct  5 23:38:44 faye kernel: [    0.591952] ACPI: (supports S0 S1 S3 S4 S5)
Oct  5 23:38:44 faye kernel: [    0.591973] ACPI: Using IOAPIC for interrupt routing
Oct  5 23:38:44 faye kernel: [    0.601240] ACPI: No dock devices found.
Oct  5 23:38:44 faye kernel: [    0.601251] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct  5 23:38:44 faye kernel: [    0.602117] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct  5 23:38:44 faye kernel: [    0.602121] pci 0000:00:03.0: PME# disabled
Oct  5 23:38:44 faye kernel: [    0.602163] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct  5 23:38:44 faye kernel: [    0.602166] pci 0000:00:07.0: PME# disabled
Oct  5 23:38:44 faye kernel: [    0.602405] pci 0000:00:0a.1: reg 20 io port: [0x1c00-0x1c3f]
Oct  5 23:38:44 faye kernel: [    0.602411] pci 0000:00:0a.1: reg 24 io port: [0x1c80-0x1cbf]
Oct  5 23:38:44 faye kernel: [    0.602425] pci 0000:00:0a.1: PME# supported from D3hot D3cold
Oct  5 23:38:44 faye kernel: [    0.602431] pci 0000:00:0a.1: PME# disabled
Oct  5 23:38:44 faye kernel: [    0.602507] pci 0000:00:0b.0: reg 10 32bit mmio: [0xfe02f000-0xfe02ffff]
Oct  5 23:38:44 faye kernel: [    0.602537] pci 0000:00:0b.0: supports D1 D2
Oct  5 23:38:44 faye kernel: [    0.602538] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct  5 23:38:44 faye kernel: [    0.602542] pci 0000:00:0b.0: PME# disabled
Oct  5 23:38:44 faye kernel: [    0.602573] pci 0000:00:0b.1: reg 10 32bit mmio: [0xfe02e000-0xfe02e0ff]
Oct  5 23:38:44 faye kernel: [    0.602603] pci 0000:00:0b.1: supports D1 D2
Oct  5 23:38:44 faye kernel: [    0.602604] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
Oct  5 23:38:44 faye kernel: [    0.602608] pci 0000:00:0b.1: PME# disabled
Oct  5 23:38:44 faye kernel: [    0.602655] pci 0000:00:0d.0: reg 20 io port: [0xf400-0xf40f]
Oct  5 23:38:44 faye kernel: [    0.602702] pci 0000:00:0e.0: reg 10 io port: [0x9f0-0x9f7]
Oct  5 23:38:44 faye kernel: [    0.602707] pci 0000:00:0e.0: reg 14 io port: [0xbf0-0xbf3]
Oct  5 23:38:44 faye kernel: [    0.602713] pci 0000:00:0e.0: reg 18 io port: [0x970-0x977]
Oct  5 23:38:44 faye kernel: [    0.602718] pci 0000:00:0e.0: reg 1c io port: [0xb70-0xb73]
Oct  5 23:38:44 faye kernel: [    0.602723] pci 0000:00:0e.0: reg 20 io port: [0xe000-0xe00f]
Oct  5 23:38:44 faye kernel: [    0.602728] pci 0000:00:0e.0: reg 24 32bit mmio: [0xfe02d000-0xfe02dfff]
Oct  5 23:38:44 faye kernel: [    0.602775] pci 0000:00:0f.0: reg 10 io port: [0x9e0-0x9e7]
Oct  5 23:38:44 faye kernel: [    0.602781] pci 0000:00:0f.0: reg 14 io port: [0xbe0-0xbe3]
Oct  5 23:38:44 faye kernel: [    0.602786] pci 0000:00:0f.0: reg 18 io port: [0x960-0x967]
Oct  5 23:38:44 faye kernel: [    0.602791] pci 0000:00:0f.0: reg 1c io port: [0xb60-0xb63]
Oct  5 23:38:44 faye kernel: [    0.602796] pci 0000:00:0f.0: reg 20 io port: [0xcc00-0xcc0f]
Oct  5 23:38:44 faye kernel: [    0.602801] pci 0000:00:0f.0: reg 24 32bit mmio: [0xfe02c000-0xfe02cfff]
Oct  5 23:38:44 faye kernel: [    0.602890] pci 0000:00:10.1: reg 10 32bit mmio: [0xfe024000-0xfe027fff]
Oct  5 23:38:44 faye kernel: [    0.602920] pci 0000:00:10.1: PME# supported from D3hot D3cold
Oct  5 23:38:44 faye kernel: [    0.602923] pci 0000:00:10.1: PME# disabled
Oct  5 23:38:44 faye kernel: [    0.602962] pci 0000:00:14.0: reg 10 32bit mmio: [0xfe02b000-0xfe02bfff]
Oct  5 23:38:44 faye kernel: [    0.602968] pci 0000:00:14.0: reg 14 io port: [0xc800-0xc807]
Oct  5 23:38:44 faye kernel: [    0.602992] pci 0000:00:14.0: supports D1 D2
Oct  5 23:38:44 faye kernel: [    0.602993] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct  5 23:38:44 faye kernel: [    0.602997] pci 0000:00:14.0: PME# disabled
Oct  5 23:38:44 faye kernel: [    0.603041] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
Oct  5 23:38:44 faye kernel: [    0.603050] pci 0000:01:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
Oct  5 23:38:44 faye kernel: [    0.603059] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfb000000-0xfbffffff]
Oct  5 23:38:44 faye kernel: [    0.603067] pci 0000:01:00.0: reg 30 32bit mmio: [0xfcfe0000-0xfcffffff]
Oct  5 23:38:44 faye kernel: [    0.603123] pci 0000:00:03.0: bridge io port: [0xb000-0xbfff]
Oct  5 23:38:44 faye kernel: [    0.603126] pci 0000:00:03.0: bridge 32bit mmio: [0xfa000000-0xfcffffff]
Oct  5 23:38:44 faye kernel: [    0.603130] pci 0000:00:03.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
Oct  5 23:38:44 faye kernel: [    0.603176] pci 0000:02:00.0: reg 10 io port: [0x8c00-0x8c07]
Oct  5 23:38:44 faye kernel: [    0.603184] pci 0000:02:00.0: reg 14 io port: [0x8800-0x8803]
Oct  5 23:38:44 faye kernel: [    0.603191] pci 0000:02:00.0: reg 18 io port: [0x8400-0x8407]
Oct  5 23:38:44 faye kernel: [    0.603199] pci 0000:02:00.0: reg 1c io port: [0x8000-0x8003]
Oct  5 23:38:44 faye kernel: [    0.603207] pci 0000:02:00.0: reg 20 io port: [0x7c00-0x7c0f]
Oct  5 23:38:44 faye kernel: [    0.603215] pci 0000:02:00.0: reg 24 32bit mmio: [0xfdcfe000-0xfdcfffff]
Oct  5 23:38:44 faye kernel: [    0.603232] pci 0000:02:00.0: PME# supported from D3hot
Oct  5 23:38:44 faye kernel: [    0.603236] pci 0000:02:00.0: PME# disabled
Oct  5 23:38:44 faye kernel: [    0.603287] pci 0000:00:07.0: bridge io port: [0x7000-0x8fff]
Oct  5 23:38:44 faye kernel: [    0.603291] pci 0000:00:07.0: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
Oct  5 23:38:44 faye kernel: [    0.603295] pci 0000:00:07.0: bridge 64bit mmio pref: [0xfdb00000-0xfdbfffff]
Oct  5 23:38:44 faye kernel: [    0.603333] pci 0000:03:06.0: reg 10 32bit mmio: [0x000000-0x000fff]
Oct  5 23:38:44 faye kernel: [    0.603368] pci 0000:03:06.0: supports D1 D2
Oct  5 23:38:44 faye kernel: [    0.603370] pci 0000:03:06.0: PME# supported from D0 D1 D2 D3hot
Oct  5 23:38:44 faye kernel: [    0.603374] pci 0000:03:06.0: PME# disabled
Oct  5 23:38:44 faye kernel: [    0.603404] pci 0000:03:06.1: reg 10 32bit mmio: [0x000000-0x000fff]
Oct  5 23:38:44 faye kernel: [    0.603439] pci 0000:03:06.1: supports D1 D2
Oct  5 23:38:44 faye kernel: [    0.603441] pci 0000:03:06.1: PME# supported from D0 D1 D2 D3hot
Oct  5 23:38:44 faye kernel: [    0.603445] pci 0000:03:06.1: PME# disabled
Oct  5 23:38:44 faye kernel: [    0.603475] pci 0000:03:06.2: reg 10 32bit mmio: [0x000000-0x0000ff]
Oct  5 23:38:44 faye kernel: [    0.603511] pci 0000:03:06.2: supports D1 D2
Oct  5 23:38:44 faye kernel: [    0.603512] pci 0000:03:06.2: PME# supported from D0 D1 D2 D3hot
Oct  5 23:38:44 faye kernel: [    0.603516] pci 0000:03:06.2: PME# disabled
Oct  5 23:38:44 faye kernel: [    0.603555] pci 0000:03:08.0: reg 10 32bit mmio: [0xfdfff000-0xfdfff7ff]
Oct  5 23:38:44 faye kernel: [    0.603562] pci 0000:03:08.0: reg 14 io port: [0xac00-0xac7f]
Oct  5 23:38:44 faye kernel: [    0.603594] pci 0000:03:08.0: supports D2
Oct  5 23:38:44 faye kernel: [    0.603596] pci 0000:03:08.0: PME# supported from D2 D3hot D3cold
Oct  5 23:38:44 faye kernel: [    0.603600] pci 0000:03:08.0: PME# disabled
Oct  5 23:38:44 faye kernel: [    0.603634] pci 0000:00:10.0: transparent bridge
Oct  5 23:38:44 faye kernel: [    0.603637] pci 0000:00:10.0: bridge io port: [0x9000-0xafff]
Oct  5 23:38:44 faye kernel: [    0.603640] pci 0000:00:10.0: bridge 32bit mmio: [0xfde00000-0xfdffffff]
Oct  5 23:38:44 faye kernel: [    0.603644] pci 0000:00:10.0: bridge 32bit mmio pref: [0xfdd00000-0xfddfffff]
Oct  5 23:38:44 faye kernel: [    0.603656] bus 00 -> node 0
Oct  5 23:38:44 faye kernel: [    0.603662] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct  5 23:38:44 faye kernel: [    0.604059] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Oct  5 23:38:44 faye kernel: [    0.679711] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.679889] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.680081] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
Oct  5 23:38:44 faye kernel: [    0.680257] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.680434] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 *10 11 14 15)
Oct  5 23:38:44 faye kernel: [    0.680610] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 *11 14 15)
Oct  5 23:38:44 faye kernel: [    0.680784] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.680960] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.681138] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
Oct  5 23:38:44 faye kernel: [    0.681313] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.681489] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
Oct  5 23:38:44 faye kernel: [    0.681667] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.681843] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
Oct  5 23:38:44 faye kernel: [    0.682018] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.682194] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.682370] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
Oct  5 23:38:44 faye kernel: [    0.682545] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
Oct  5 23:38:44 faye kernel: [    0.682720] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.682896] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Oct  5 23:38:44 faye kernel: [    0.683074] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
Oct  5 23:38:44 faye kernel: [    0.683287] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.683492] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.683697] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
Oct  5 23:38:44 faye kernel: [    0.683900] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.684105] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
Oct  5 23:38:44 faye kernel: [    0.684308] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0
Oct  5 23:38:44 faye kernel: [    0.684512] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.684716] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.684920] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
Oct  5 23:38:44 faye kernel: [    0.685126] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.685332] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
Oct  5 23:38:44 faye kernel: [    0.685537] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.685742] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.685948] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
Oct  5 23:38:44 faye kernel: [    0.686152] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.686358] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
Oct  5 23:38:44 faye kernel: [    0.686563] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
Oct  5 23:38:44 faye kernel: [    0.686768] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.686974] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Oct  5 23:38:44 faye kernel: [    0.687180] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Oct  5 23:38:44 faye kernel: [    0.687386] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
Oct  5 23:38:44 faye kernel: [    0.687529] ACPI: WMI: Mapper loaded
Oct  5 23:38:44 faye kernel: [    0.687563] SCSI subsystem initialized
Oct  5 23:38:44 faye kernel: [    0.687563] libata version 3.00 loaded.
Oct  5 23:38:44 faye kernel: [    0.687563] usbcore: registered new interface driver usbfs
Oct  5 23:38:44 faye kernel: [    0.687563] usbcore: registered new interface driver hub
Oct  5 23:38:44 faye kernel: [    0.687563] usbcore: registered new device driver usb
Oct  5 23:38:44 faye kernel: [    0.687563] PCI: Using ACPI for IRQ routing
Oct  5 23:38:44 faye kernel: [    0.700006] Bluetooth: Core ver 2.13
Oct  5 23:38:44 faye kernel: [    0.700019] NET: Registered protocol family 31
Oct  5 23:38:44 faye kernel: [    0.700019] Bluetooth: HCI device and connection manager initialized
Oct  5 23:38:44 faye kernel: [    0.700019] Bluetooth: HCI socket layer initialized
Oct  5 23:38:44 faye kernel: [    0.700019] NET: Registered protocol family 8
Oct  5 23:38:44 faye kernel: [    0.700019] NET: Registered protocol family 20
Oct  5 23:38:44 faye kernel: [    0.700029] NetLabel: Initializing
Oct  5 23:38:44 faye kernel: [    0.700030] NetLabel:  domain hash size = 128
Oct  5 23:38:44 faye kernel: [    0.700031] NetLabel:  protocols = UNLABELED CIPSOv4
Oct  5 23:38:44 faye kernel: [    0.700042] NetLabel:  unlabeled traffic allowed by default
Oct  5 23:38:44 faye kernel: [    0.700056] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Oct  5 23:38:44 faye kernel: [    0.700060] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Oct  5 23:38:44 faye kernel: [    0.710049] AppArmor: AppArmor Filesystem Enabled
Oct  5 23:38:44 faye kernel: [    0.720007] Switched to high resolution mode on CPU 0
Oct  5 23:38:44 faye kernel: [    0.720392] Switched to high resolution mode on CPU 1
Oct  5 23:38:44 faye kernel: [    0.730000] pnp: PnP ACPI init
Oct  5 23:38:44 faye kernel: [    0.730010] ACPI: bus type pnp registered
Oct  5 23:38:44 faye kernel: [    0.734851] pnp: PnP ACPI: found 15 devices
Oct  5 23:38:44 faye kernel: [    0.734853] ACPI: ACPI bus type pnp unregistered
Oct  5 23:38:44 faye kernel: [    0.734856] PnPBIOS: Disabled by ACPI PNP
Oct  5 23:38:44 faye kernel: [    0.734866] system 00:01: ioport range 0x1000-0x107f has been reserved
Oct  5 23:38:44 faye kernel: [    0.734869] system 00:01: ioport range 0x1080-0x10ff has been reserved
Oct  5 23:38:44 faye kernel: [    0.734871] system 00:01: ioport range 0x1400-0x147f has been reserved
Oct  5 23:38:44 faye kernel: [    0.734874] system 00:01: ioport range 0x1480-0x14ff has been reserved
Oct  5 23:38:44 faye kernel: [    0.734876] system 00:01: ioport range 0x1800-0x187f has been reserved
Oct  5 23:38:44 faye kernel: [    0.734878] system 00:01: ioport range 0x1880-0x18ff has been reserved
Oct  5 23:38:44 faye kernel: [    0.734884] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Oct  5 23:38:44 faye kernel: [    0.734886] system 00:02: ioport range 0x800-0x87f has been reserved
Oct  5 23:38:44 faye kernel: [    0.734888] system 00:02: ioport range 0x290-0x297 has been reserved
Oct  5 23:38:44 faye kernel: [    0.734891] system 00:02: ioport range 0x880-0x88f has been reserved
Oct  5 23:38:44 faye kernel: [    0.734899] system 00:0d: iomem range 0xf0000000-0xf1ffffff has been reserved
Oct  5 23:38:44 faye kernel: [    0.734905] system 00:0e: iomem range 0xda000-0xdbfff has been reserved
Oct  5 23:38:44 faye kernel: [    0.734907] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
Oct  5 23:38:44 faye kernel: [    0.734910] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
Oct  5 23:38:44 faye kernel: [    0.734912] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
Oct  5 23:38:44 faye kernel: [    0.734914] system 00:0e: iomem range 0xfeff0000-0xfeff00ff has been reserved
Oct  5 23:38:44 faye kernel: [    0.734917] system 00:0e: iomem range 0xdfef0000-0xdfefffff could not be reserved
Oct  5 23:38:44 faye kernel: [    0.734919] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
Oct  5 23:38:44 faye kernel: [    0.734922] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Oct  5 23:38:44 faye kernel: [    0.734924] system 00:0e: iomem range 0x100000-0xdfeeffff could not be reserved
Oct  5 23:38:44 faye kernel: [    0.734927] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Oct  5 23:38:44 faye kernel: [    0.734929] system 00:0e: iomem range 0xfee00000-0xfee00fff has been reserved
Oct  5 23:38:44 faye kernel: [    0.734931] system 00:0e: iomem range 0xfeff0000-0xfeff03ff could not be reserved
Oct  5 23:38:44 faye kernel: [    0.769658] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
Oct  5 23:38:44 faye kernel: [    0.769661] pci 0000:00:03.0:   IO window: 0xb000-0xbfff
Oct  5 23:38:44 faye kernel: [    0.769665] pci 0000:00:03.0:   MEM window: 0xfa000000-0xfcffffff
Oct  5 23:38:44 faye kernel: [    0.769668] pci 0000:00:03.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
Oct  5 23:38:44 faye kernel: [    0.769673] pci 0000:00:07.0: PCI bridge, secondary bus 0000:02
Oct  5 23:38:44 faye kernel: [    0.769675] pci 0000:00:07.0:   IO window: 0x7000-0x8fff
Oct  5 23:38:44 faye kernel: [    0.769679] pci 0000:00:07.0:   MEM window: 0xfdc00000-0xfdcfffff
Oct  5 23:38:44 faye kernel: [    0.769682] pci 0000:00:07.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Oct  5 23:38:44 faye kernel: [    0.769695] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
Oct  5 23:38:44 faye kernel: [    0.769698] pci 0000:00:10.0:   IO window: 0x9000-0xafff
Oct  5 23:38:44 faye kernel: [    0.769702] pci 0000:00:10.0:   MEM window: 0xfde00000-0xfdffffff
Oct  5 23:38:44 faye kernel: [    0.769705] pci 0000:00:10.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
Oct  5 23:38:44 faye kernel: [    0.769716] pci 0000:00:03.0: setting latency timer to 64
Oct  5 23:38:44 faye kernel: [    0.769722] pci 0000:00:07.0: setting latency timer to 64
Oct  5 23:38:44 faye kernel: [    0.769727] pci 0000:00:10.0: setting latency timer to 64
Oct  5 23:38:44 faye kernel: [    0.769730] bus: 00 index 0 io port: [0x00-0xffff]
Oct  5 23:38:44 faye kernel: [    0.769732] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
Oct  5 23:38:44 faye kernel: [    0.769734] bus: 01 index 0 io port: [0xb000-0xbfff]
Oct  5 23:38:44 faye kernel: [    0.769736] bus: 01 index 1 mmio: [0xfa000000-0xfcffffff]
Oct  5 23:38:44 faye kernel: [    0.769738] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
Oct  5 23:38:44 faye kernel: [    0.769740] bus: 01 index 3 mmio: [0x0-0x0]
Oct  5 23:38:44 faye kernel: [    0.769742] bus: 02 index 0 io port: [0x7000-0x8fff]
Oct  5 23:38:44 faye kernel: [    0.769744] bus: 02 index 1 mmio: [0xfdc00000-0xfdcfffff]
Oct  5 23:38:44 faye kernel: [    0.769746] bus: 02 index 2 mmio: [0xfdb00000-0xfdbfffff]
Oct  5 23:38:44 faye kernel: [    0.769747] bus: 02 index 3 mmio: [0x0-0x0]
Oct  5 23:38:44 faye kernel: [    0.769749] bus: 03 index 0 io port: [0x9000-0xafff]
Oct  5 23:38:44 faye kernel: [    0.769751] bus: 03 index 1 mmio: [0xfde00000-0xfdffffff]
Oct  5 23:38:44 faye kernel: [    0.769753] bus: 03 index 2 mmio: [0xfdd00000-0xfddfffff]
Oct  5 23:38:44 faye kernel: [    0.769755] bus: 03 index 3 io port: [0x00-0xffff]
Oct  5 23:38:44 faye kernel: [    0.769756] bus: 03 index 4 mmio: [0x000000-0xffffffffffffffff]
Oct  5 23:38:44 faye kernel: [    0.769763] NET: Registered protocol family 2
Oct  5 23:38:44 faye kernel: [    0.800055] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct  5 23:38:44 faye kernel: [    0.800282] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct  5 23:38:44 faye kernel: [    0.800663] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct  5 23:38:44 faye kernel: [    0.800902] TCP: Hash tables configured (established 131072 bind 65536)
Oct  5 23:38:44 faye kernel: [    0.800904] TCP reno registered
Oct  5 23:38:44 faye kernel: [    0.810082] NET: Registered protocol family 1
Oct  5 23:38:44 faye kernel: [    0.810181] checking if image is initramfs... it is
Oct  5 23:38:44 faye kernel: [    1.357962] Freeing initrd memory: 7405k freed
Oct  5 23:38:44 faye kernel: [    1.358189] cpufreq: No nForce2 chipset.
Oct  5 23:38:44 faye kernel: [    1.358314] audit: initializing netlink socket (disabled)
Oct  5 23:38:44 faye kernel: [    1.358339] type=2000 audit(1254778686.350:1): initialized
Oct  5 23:38:44 faye kernel: [    1.365030] highmem bounce pool size: 64 pages
Oct  5 23:38:44 faye kernel: [    1.365034] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Oct  5 23:38:44 faye kernel: [    1.366132] VFS: Disk quotas dquot_6.5.1
Oct  5 23:38:44 faye kernel: [    1.366182] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct  5 23:38:44 faye kernel: [    1.366705] fuse init (API version 7.10)
Oct  5 23:38:44 faye kernel: [    1.366775] msgmni has been set to 1640
Oct  5 23:38:44 faye kernel: [    1.366932] alg: No test for stdrng (krng)
Oct  5 23:38:44 faye kernel: [    1.366941] io scheduler noop registered
Oct  5 23:38:44 faye kernel: [    1.366943] io scheduler anticipatory registered
Oct  5 23:38:44 faye kernel: [    1.366945] io scheduler deadline registered (default)
Oct  5 23:38:44 faye kernel: [    1.366956] io scheduler cfq registered
Oct  5 23:38:44 faye kernel: [    1.367120] pci 0000:00:03.0: Disabling HT MSI mapping<6>pci 0000:00:07.0: Disabling HT MSI mapping<6>pci 0000:00:09.0: Disabling HT MSI mapping<6>pci 0000:00:0e.0: Disabling HT MSI mapping<6>pci 0000:00:0f.0: Disabling HT MSI mapping<6>pci 0000:00:10.0: Disabling HT MSI mapping<6>pci 0000:00:10.1: Disabling HT MSI mapping<7>pci 0000:01:00.0: Boot video device
Oct  5 23:38:44 faye kernel: [    1.387445] pcieport-driver 0000:00:03.0: setting latency timer to 64
Oct  5 23:38:44 faye kernel: [    1.387485] pcieport-driver 0000:00:03.0: found MSI capability
Oct  5 23:38:44 faye kernel: [    1.387508] pcieport-driver 0000:00:03.0: irq 2303 for MSI/MSI-X
Oct  5 23:38:44 faye kernel: [    1.387517] pci_express 0000:00:03.0:pcie00: allocate port service
Oct  5 23:38:44 faye kernel: [    1.387529] pci_express 0000:00:03.0:pcie03: allocate port service
Oct  5 23:38:44 faye kernel: [    1.387579] pcieport-driver 0000:00:07.0: setting latency timer to 64
Oct  5 23:38:44 faye kernel: [    1.387617] pcieport-driver 0000:00:07.0: found MSI capability
Oct  5 23:38:44 faye kernel: [    1.387637] pcieport-driver 0000:00:07.0: irq 2302 for MSI/MSI-X
Oct  5 23:38:44 faye kernel: [    1.387646] pci_express 0000:00:07.0:pcie00: allocate port service
Oct  5 23:38:44 faye kernel: [    1.387657] pci_express 0000:00:07.0:pcie03: allocate port service
Oct  5 23:38:44 faye kernel: [    1.387712] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct  5 23:38:44 faye kernel: [    1.387720] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Oct  5 23:38:44 faye kernel: [    1.387874] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Oct  5 23:38:44 faye kernel: [    1.387877] ACPI: Power Button (FF) [PWRF]
Oct  5 23:38:44 faye kernel: [    1.387914] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Oct  5 23:38:44 faye kernel: [    1.387916] ACPI: Power Button (CM) [PWRB]
Oct  5 23:38:44 faye kernel: [    1.387977] fan PNP0C0B:00: registered as cooling_device0
Oct  5 23:38:44 faye kernel: [    1.387981] ACPI: Fan [FAN] (on)
Oct  5 23:38:44 faye kernel: [    1.388542] processor ACPI_CPU:00: registered as cooling_device1
Oct  5 23:38:44 faye kernel: [    1.388803] processor ACPI_CPU:01: registered as cooling_device2
Oct  5 23:38:44 faye kernel: [    1.392978] thermal LNXTHERM:01: registered as thermal_zone0
Oct  5 23:38:44 faye kernel: [    1.393355] ACPI: Thermal Zone [THRM] (40 C)
Oct  5 23:38:44 faye kernel: [    1.393406] isapnp: Scanning for PnP cards...
Oct  5 23:38:44 faye kernel: [    1.749167] isapnp: No Plug & Play device found
Oct  5 23:38:44 faye kernel: [    1.761432] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Oct  5 23:38:44 faye kernel: [    1.761528] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct  5 23:38:44 faye kernel: [    1.761899] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct  5 23:38:44 faye kernel: [    1.762582] brd: module loaded
Oct  5 23:38:44 faye kernel: [    1.762853] loop: module loaded
Oct  5 23:38:44 faye kernel: [    1.762909] Fixed MDIO Bus: probed
Oct  5 23:38:44 faye kernel: [    1.762914] PPP generic driver version 2.4.2
Oct  5 23:38:44 faye kernel: [    1.762961] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Oct  5 23:38:44 faye kernel: [    1.762985] Driver 'sd' needs updating - please use bus_type methods
Oct  5 23:38:44 faye kernel: [    1.762993] Driver 'sr' needs updating - please use bus_type methods
Oct  5 23:38:44 faye kernel: [    1.763033] ahci 0000:02:00.0: version 3.0
Oct  5 23:38:44 faye kernel: [    1.763345] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
Oct  5 23:38:44 faye kernel: [    1.763351] ahci 0000:02:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
Oct  5 23:38:44 faye kernel: [    1.781272] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 1 ports 3 Gbps 0x1 impl SATA mode
Oct  5 23:38:44 faye kernel: [    1.781274] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Oct  5 23:38:44 faye kernel: [    1.781279] ahci 0000:02:00.0: setting latency timer to 64
Oct  5 23:38:44 faye kernel: [    1.781387] scsi0 : ahci
Oct  5 23:38:44 faye kernel: [    1.781440] ata1: SATA max UDMA/133 abar m8192@0xfdcfe000 port 0xfdcfe100 irq 16
Oct  5 23:38:44 faye kernel: [    2.130021] ata1: SATA link down (SStatus 0 SControl 300)
Oct  5 23:38:44 faye kernel: [    2.150163] sata_nv 0000:00:0e.0: version 3.5
Oct  5 23:38:44 faye kernel: [    2.150466] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Oct  5 23:38:44 faye kernel: [    2.150470] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Oct  5 23:38:44 faye kernel: [    2.150472] sata_nv 0000:00:0e.0: Using SWNCQ mode
Oct  5 23:38:44 faye kernel: [    2.150507] sata_nv 0000:00:0e.0: setting latency timer to 64
Oct  5 23:38:44 faye kernel: [    2.150616] scsi1 : sata_nv
Oct  5 23:38:44 faye kernel: [    2.150670] scsi2 : sata_nv
Oct  5 23:38:44 faye kernel: [    2.150812] ata2: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 23
Oct  5 23:38:44 faye kernel: [    2.150814] ata3: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 23
Oct  5 23:38:44 faye kernel: [    3.060040] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct  5 23:38:44 faye kernel: [    3.080553] ata2.00: ATA-8: MAXTOR STM3500320AS, MX15, max UDMA/133
Oct  5 23:38:44 faye kernel: [    3.080556] ata2.00: 976773168 sectors, multi 1: LBA48 NCQ (depth 31/32)
Oct  5 23:38:44 faye kernel: [    3.120548] ata2.00: configured for UDMA/133
Oct  5 23:38:44 faye kernel: [    4.030035] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct  5 23:38:44 faye kernel: [    4.089885] ata3.00: ATA-7: MAXTOR STM3160215AS, 3.AAD, max UDMA/133
Oct  5 23:38:44 faye kernel: [    4.089888] ata3.00: 312581808 sectors, multi 1: LBA48 NCQ (depth 31/32)
Oct  5 23:38:44 faye kernel: [    4.181535] ata3.00: configured for UDMA/133
Oct  5 23:38:44 faye kernel: [    4.181620] scsi 1:0:0:0: Direct-Access     ATA      MAXTOR STM350032 MX15 PQ: 0 ANSI: 5
Oct  5 23:38:44 faye kernel: [    4.181695] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
Oct  5 23:38:44 faye kernel: [    4.181709] sd 1:0:0:0: [sda] Write Protect is off
Oct  5 23:38:44 faye kernel: [    4.181711] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct  5 23:38:44 faye kernel: [    4.181732] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  5 23:38:44 faye kernel: [    4.181784] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
Oct  5 23:38:44 faye kernel: [    4.181796] sd 1:0:0:0: [sda] Write Protect is off
Oct  5 23:38:44 faye kernel: [    4.181798] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct  5 23:38:44 faye kernel: [    4.181819] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  5 23:38:44 faye kernel: [    4.181822]  sda: sda1 sda2 < sda5 >
Oct  5 23:38:44 faye kernel: [    4.211001] sd 1:0:0:0: [sda] Attached SCSI disk
Oct  5 23:38:44 faye kernel: [    4.211038] sd 1:0:0:0: Attached scsi generic sg0 type 0
Oct  5 23:38:44 faye kernel: [    4.211102] scsi 2:0:0:0: Direct-Access     ATA      MAXTOR STM316021 3.AA PQ: 0 ANSI: 5
Oct  5 23:38:44 faye kernel: [    4.211171] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Oct  5 23:38:44 faye kernel: [    4.211184] sd 2:0:0:0: [sdb] Write Protect is off
Oct  5 23:38:44 faye kernel: [    4.211186] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Oct  5 23:38:44 faye kernel: [    4.211207] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  5 23:38:44 faye kernel: [    4.211252] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Oct  5 23:38:44 faye kernel: [    4.211264] sd 2:0:0:0: [sdb] Write Protect is off
Oct  5 23:38:44 faye kernel: [    4.211266] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Oct  5 23:38:44 faye kernel: [    4.211286] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  5 23:38:44 faye kernel: [    4.211289]  sdb: sdb1
Oct  5 23:38:44 faye kernel: [    4.229592] sd 2:0:0:0: [sdb] Attached SCSI disk
Oct  5 23:38:44 faye kernel: [    4.229622] sd 2:0:0:0: Attached scsi generic sg1 type 0
Oct  5 23:38:44 faye kernel: [    4.229939] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
Oct  5 23:38:44 faye kernel: [    4.229943] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
Oct  5 23:38:44 faye kernel: [    4.229946] sata_nv 0000:00:0f.0: Using SWNCQ mode
Oct  5 23:38:44 faye kernel: [    4.229980] sata_nv 0000:00:0f.0: setting latency timer to 64
Oct  5 23:38:44 faye kernel: [    4.230115] scsi3 : sata_nv
Oct  5 23:38:44 faye kernel: [    4.230165] scsi4 : sata_nv
Oct  5 23:38:44 faye kernel: [    4.230309] ata4: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 22
Oct  5 23:38:44 faye kernel: [    4.230312] ata5: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 22
Oct  5 23:38:44 faye kernel: [    5.140048] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct  5 23:38:44 faye kernel: [    5.160160] ata4.00: ATAPI: ASUS    DRW-22B1LT, 1.00, max UDMA/100
Oct  5 23:38:44 faye kernel: [    5.200177] ata4.00: configured for UDMA/100
Oct  5 23:38:44 faye kernel: [    5.960570] ata5: SATA link down (SStatus 0 SControl 300)
Oct  5 23:38:44 faye kernel: [    5.962982] scsi 3:0:0:0: CD-ROM            ASUS     DRW-22B1LT       1.00 PQ: 0 ANSI: 5
Oct  5 23:38:44 faye kernel: [    5.969803] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
Oct  5 23:38:44 faye kernel: [    5.969806] Uniform CD-ROM driver Revision: 3.20
Oct  5 23:38:44 faye kernel: [    5.969884] sr 3:0:0:0: Attached scsi CD-ROM sr0
Oct  5 23:38:44 faye kernel: [    5.969916] sr 3:0:0:0: Attached scsi generic sg2 type 5
Oct  5 23:38:44 faye kernel: [    5.970012] pata_amd 0000:00:0d.0: version 0.3.10
Oct  5 23:38:44 faye kernel: [    5.970046] pata_amd 0000:00:0d.0: setting latency timer to 64
Oct  5 23:38:44 faye kernel: [    5.970099] scsi5 : pata_amd
Oct  5 23:38:44 faye kernel: [    5.970146] scsi6 : pata_amd
Oct  5 23:38:44 faye kernel: [    5.970706] ata6: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
Oct  5 23:38:44 faye kernel: [    5.970709] ata7: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
Oct  5 23:38:44 faye kernel: [    6.330290] ata7.01: ATAPI: ASUS    DRW-2014S1, 1.01, max UDMA/66
Oct  5 23:38:44 faye kernel: [    6.330312] ata7: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5) ACPI=0x1f01f (600:30:0x1c)
Oct  5 23:38:44 faye kernel: [    6.370242] ata7.01: configured for UDMA/66
Oct  5 23:38:44 faye kernel: [    6.370898] scsi 6:0:1:0: CD-ROM            ASUS     DRW-2014S1       1.01 PQ: 0 ANSI: 5
Oct  5 23:38:44 faye kernel: [    6.374002] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Oct  5 23:38:44 faye kernel: [    6.374053] sr 6:0:1:0: Attached scsi CD-ROM sr1
Oct  5 23:38:44 faye kernel: [    6.374083] sr 6:0:1:0: Attached scsi generic sg3 type 5
Oct  5 23:38:44 faye kernel: [    6.374587] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct  5 23:38:44 faye kernel: [    6.374906] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
Oct  5 23:38:44 faye kernel: [    6.374911] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
Oct  5 23:38:44 faye kernel: [    6.374920] ehci_hcd 0000:00:0b.1: setting latency timer to 64
Oct  5 23:38:44 faye kernel: [    6.374923] ehci_hcd 0000:00:0b.1: EHCI Host Controller
Oct  5 23:38:44 faye kernel: [    6.374981] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
Oct  5 23:38:44 faye kernel: [    6.375007] ehci_hcd 0000:00:0b.1: debug port 1
Oct  5 23:38:44 faye kernel: [    6.375011] ehci_hcd 0000:00:0b.1: cache line size of 32 is not supported
Oct  5 23:38:44 faye kernel: [    6.375025] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfe02e000
Oct  5 23:38:44 faye kernel: [    6.390010] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
Oct  5 23:38:44 faye kernel: [    6.390073] usb usb1: configuration #1 chosen from 1 choice
Oct  5 23:38:44 faye kernel: [    6.390096] hub 1-0:1.0: USB hub found
Oct  5 23:38:44 faye kernel: [    6.390104] hub 1-0:1.0: 8 ports detected
Oct  5 23:38:44 faye kernel: [    6.390193] ehci_hcd 0000:03:06.2: enabling device (0000 -> 0002)
Oct  5 23:38:44 faye kernel: [    6.390496] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Oct  5 23:38:44 faye kernel: [    6.390500] ehci_hcd 0000:03:06.2: PCI INT C -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Oct  5 23:38:44 faye kernel: [    6.390510] ehci_hcd 0000:03:06.2: EHCI Host Controller
Oct  5 23:38:44 faye kernel: [    6.390548] ehci_hcd 0000:03:06.2: new USB bus registered, assigned bus number 2
Oct  5 23:38:44 faye kernel: [    6.420019] ehci_hcd 0000:03:06.2: cache line size of 32 is not supported
Oct  5 23:38:44 faye kernel: [    6.420032] ehci_hcd 0000:03:06.2: irq 18, io mem 0xfde02000
Oct  5 23:38:44 faye kernel: [    6.420040] ehci_hcd 0000:03:06.2: startup error -19
Oct  5 23:38:44 faye kernel: [    6.420096] ehci_hcd 0000:03:06.2: USB bus 2 deregistered
Oct  5 23:38:44 faye kernel: [    6.420135] ehci_hcd 0000:03:06.2: PCI INT C disabled
Oct  5 23:38:44 faye kernel: [    6.420137] ehci_hcd 0000:03:06.2: init 0000:03:06.2 fail, -19
Oct  5 23:38:44 faye kernel: [    6.420201] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Oct  5 23:38:44 faye kernel: [    6.420513] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
Oct  5 23:38:44 faye kernel: [    6.420517] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
Oct  5 23:38:44 faye kernel: [    6.420530] ohci_hcd 0000:00:0b.0: setting latency timer to 64
Oct  5 23:38:44 faye kernel: [    6.420533] ohci_hcd 0000:00:0b.0: OHCI Host Controller
Oct  5 23:38:44 faye kernel: [    6.420568] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
Oct  5 23:38:44 faye kernel: [    6.420589] ohci_hcd 0000:00:0b.0: irq 20, io mem 0xfe02f000
Oct  5 23:38:44 faye kernel: [    6.482063] usb usb2: configuration #1 chosen from 1 choice
Oct  5 23:38:44 faye kernel: [    6.482086] hub 2-0:1.0: USB hub found
Oct  5 23:38:44 faye kernel: [    6.482097] hub 2-0:1.0: 8 ports detected
Oct  5 23:38:44 faye kernel: [    6.482178] ohci_hcd 0000:03:06.0: enabling device (0000 -> 0002)
Oct  5 23:38:44 faye kernel: [    6.482479] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Oct  5 23:38:44 faye kernel: [    6.482482] ohci_hcd 0000:03:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
Oct  5 23:38:44 faye kernel: [    6.482492] ohci_hcd 0000:03:06.0: OHCI Host Controller
Oct  5 23:38:44 faye kernel: [    6.482527] ohci_hcd 0000:03:06.0: new USB bus registered, assigned bus number 3
Oct  5 23:38:44 faye kernel: [    6.710016] usb 1-2: new high speed USB device using ehci_hcd and address 2
Oct  5 23:38:44 faye kernel: [    6.968272] usb 1-2: configuration #1 chosen from 1 choice
Oct  5 23:38:44 faye kernel: [   16.480007] ohci_hcd 0000:03:06.0: USB HC takeover failed!  (BIOS/SMM bug)
Oct  5 23:38:44 faye kernel: [   16.480061] ohci_hcd 0000:03:06.0: can't setup
Oct  5 23:38:44 faye kernel: [   16.480111] ohci_hcd 0000:03:06.0: USB bus 3 deregistered
Oct  5 23:38:44 faye kernel: [   16.480149] ohci_hcd 0000:03:06.0: PCI INT A disabled
Oct  5 23:38:44 faye kernel: [   16.480151] ohci_hcd 0000:03:06.0: init 0000:03:06.0 fail, -16
Oct  5 23:38:44 faye kernel: [   16.480204] ohci_hcd: probe of 0000:03:06.0 failed with error -16
Oct  5 23:38:44 faye kernel: [   16.480214] ohci_hcd 0000:03:06.1: enabling device (0000 -> 0002)
Oct  5 23:38:44 faye kernel: [   16.480516] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
Oct  5 23:38:44 faye kernel: [   16.480520] ohci_hcd 0000:03:06.1: PCI INT B -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
Oct  5 23:38:44 faye kernel: [   16.480534] ohci_hcd 0000:03:06.1: setting latency timer to 64
Oct  5 23:38:44 faye kernel: [   16.480537] ohci_hcd 0000:03:06.1: OHCI Host Controller
Oct  5 23:38:44 faye kernel: [   16.480573] ohci_hcd 0000:03:06.1: new USB bus registered, assigned bus number 3
Oct  5 23:38:44 faye kernel: [   26.480007] ohci_hcd 0000:03:06.1: USB HC takeover failed!  (BIOS/SMM bug)
Oct  5 23:38:44 faye kernel: [   26.480061] ohci_hcd 0000:03:06.1: can't setup
Oct  5 23:38:44 faye kernel: [   26.480110] ohci_hcd 0000:03:06.1: USB bus 3 deregistered
Oct  5 23:38:44 faye kernel: [   26.480145] ohci_hcd 0000:03:06.1: PCI INT B disabled
Oct  5 23:38:44 faye kernel: [   26.480147] ohci_hcd 0000:03:06.1: init 0000:03:06.1 fail, -16
Oct  5 23:38:44 faye kernel: [   26.480200] ohci_hcd: probe of 0000:03:06.1 failed with error -16
Oct  5 23:38:44 faye kernel: [   26.480210] uhci_hcd: USB Universal Host Controller Interface driver
Oct  5 23:38:44 faye kernel: [   26.480284] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct  5 23:38:44 faye kernel: [   26.480608] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct  5 23:38:44 faye kernel: [   26.480613] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct  5 23:38:44 faye kernel: [   26.490037] mice: PS/2 mouse device common for all mice
Oct  5 23:38:44 faye kernel: [   26.520068] rtc_cmos 00:05: RTC can wake from S4
Oct  5 23:38:44 faye kernel: [   26.520096] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Oct  5 23:38:44 faye kernel: [   26.520126] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Oct  5 23:38:44 faye kernel: [   26.520178] device-mapper: uevent: version 1.0.3
Oct  5 23:38:44 faye kernel: [   26.520250] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Oct  5 23:38:44 faye kernel: [   26.520308] device-mapper: multipath: version 1.0.5 loaded
Oct  5 23:38:44 faye kernel: [   26.520310] device-mapper: multipath round-robin: version 1.0.0 loaded
Oct  5 23:38:44 faye kernel: [   26.520375] EISA: Probing bus 0 at eisa.0
Oct  5 23:38:44 faye kernel: [   26.520380] Cannot allocate resource for EISA slot 1
Oct  5 23:38:44 faye kernel: [   26.520397] Cannot allocate resource for EISA slot 7
Oct  5 23:38:44 faye kernel: [   26.520399] Cannot allocate resource for EISA slot 8
Oct  5 23:38:44 faye kernel: [   26.520401] EISA: Detected 0 cards.
Oct  5 23:38:44 faye kernel: [   26.520443] cpuidle: using governor ladder
Oct  5 23:38:44 faye kernel: [   26.520445] cpuidle: using governor menu
Oct  5 23:38:44 faye kernel: [   26.520892] TCP cubic registered
Oct  5 23:38:44 faye kernel: [   26.520997] NET: Registered protocol family 10
Oct  5 23:38:44 faye kernel: [   26.521381] lo: Disabled Privacy Extensions
Oct  5 23:38:44 faye kernel: [   26.521674] NET: Registered protocol family 17
Oct  5 23:38:44 faye kernel: [   26.521688] Bluetooth: L2CAP ver 2.11
Oct  5 23:38:44 faye kernel: [   26.521689] Bluetooth: L2CAP socket layer initialized
Oct  5 23:38:44 faye kernel: [   26.521692] Bluetooth: SCO (Voice Link) ver 0.6
Oct  5 23:38:44 faye kernel: [   26.521694] Bluetooth: SCO socket layer initialized
Oct  5 23:38:44 faye kernel: [   26.521717] Bluetooth: RFCOMM socket layer initialized
Oct  5 23:38:44 faye kernel: [   26.521724] Bluetooth: RFCOMM TTY layer initialized
Oct  5 23:38:44 faye kernel: [   26.521725] Bluetooth: RFCOMM ver 1.10
Oct  5 23:38:44 faye kernel: [   26.521769] Using IPI No-Shortcut mode
Oct  5 23:38:44 faye kernel: [   26.521825] registered taskstats version 1
Oct  5 23:38:44 faye kernel: [   26.521969]   Magic number: 13:209:651
Oct  5 23:38:44 faye kernel: [   26.521974] scsi_host host5: hash matches
Oct  5 23:38:44 faye kernel: [   26.521976] scsi host5: hash matches
Oct  5 23:38:44 faye kernel: [   26.522043] rtc_cmos 00:05: setting system clock to 2009-10-05 21:38:32 UTC (1254778712)
Oct  5 23:38:44 faye kernel: [   26.522046] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct  5 23:38:44 faye kernel: [   26.522047] EDD information not available.
Oct  5 23:38:44 faye kernel: [   26.522328] Freeing unused kernel memory: 548k freed
Oct  5 23:38:44 faye kernel: [   26.522434] Write protecting the kernel text: 4172k
Oct  5 23:38:44 faye kernel: [   26.522512] Write protecting the kernel read-only data: 1544k
Oct  5 23:38:44 faye kernel: [   26.537877] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Oct  5 23:38:44 faye kernel: [   26.744445] Floppy drive(s): fd0 is 1.44M
Oct  5 23:38:44 faye kernel: [   26.773941] FDC 0 is a post-1991 82077
Oct  5 23:38:44 faye kernel: [   26.807492] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Oct  5 23:38:44 faye kernel: [   26.807847] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
Oct  5 23:38:44 faye kernel: [   26.807851] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Oct  5 23:38:44 faye kernel: [   26.807857] forcedeth 0000:00:14.0: setting latency timer to 64
Oct  5 23:38:44 faye kernel: [   26.807921] nv_probe: set workaround bit for reversed mac addr
Oct  5 23:38:44 faye kernel: [   26.842954] ohci1394 0000:03:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Oct  5 23:38:44 faye kernel: [   26.896119] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fdfff000-fdfff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Oct  5 23:38:44 faye kernel: [   27.340864] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1d:60:0c:10:26
Oct  5 23:38:44 faye kernel: [   27.340868] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
Oct  5 23:38:44 faye kernel: [   27.389106] PM: Starting manual resume from disk
Oct  5 23:38:44 faye kernel: [   27.389109] PM: Resume from partition 8:5
Oct  5 23:38:44 faye kernel: [   27.389110] PM: Checking hibernation image.
Oct  5 23:38:44 faye kernel: [   27.389387] PM: Resume from disk failed.
Oct  5 23:38:44 faye kernel: [   27.400471] EXT3-fs: INFO: recovery required on readonly filesystem.
Oct  5 23:38:44 faye kernel: [   27.400473] EXT3-fs: write access will be enabled during recovery.
Oct  5 23:38:44 faye kernel: [   28.115739] kjournald starting.  Commit interval 5 seconds
Oct  5 23:38:44 faye kernel: [   28.115753] EXT3-fs: sda1: orphan cleanup on readonly fs
Oct  5 23:38:44 faye kernel: [   28.115758] ext3_orphan_cleanup: deleting unreferenced inode 18227558
Oct  5 23:38:44 faye kernel: [   28.115780] ext3_orphan_cleanup: deleting unreferenced inode 15826968
Oct  5 23:38:44 faye kernel: [   28.115789] ext3_orphan_cleanup: deleting unreferenced inode 15794182
Oct  5 23:38:44 faye kernel: [   28.115796] ext3_orphan_cleanup: deleting unreferenced inode 15794181
Oct  5 23:38:44 faye kernel: [   28.115801] ext3_orphan_cleanup: deleting unreferenced inode 15794180
Oct  5 23:38:44 faye kernel: [   28.115807] ext3_orphan_cleanup: deleting unreferenced inode 15794179
Oct  5 23:38:44 faye kernel: [   28.115812] ext3_orphan_cleanup: deleting unreferenced inode 15794178
Oct  5 23:38:44 faye kernel: [   28.115818] EXT3-fs: sda1: 7 orphan inodes deleted
Oct  5 23:38:44 faye kernel: [   28.115819] EXT3-fs: recovery complete.
Oct  5 23:38:44 faye kernel: [   28.143023] EXT3-fs: mounted filesystem with ordered data mode.
Oct  5 23:38:44 faye kernel: [   28.220116] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80001681bc6]
Oct  5 23:38:44 faye kernel: [   32.723152] udev: starting version 141
Oct  5 23:38:44 faye kernel: [   33.385277] parport_pc 00:0a: reported by Plug and Play ACPI
Oct  5 23:38:44 faye kernel: [   33.385305] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Oct  5 23:38:44 faye kernel: [   33.434400] input: PC Speaker as /devices/platform/pcspkr/input/input4
Oct  5 23:38:44 faye kernel: [   33.461999] Linux agpgart interface v0.103
Oct  5 23:38:44 faye kernel: [   33.467751] ppdev: user-space parallel port driver
Oct  5 23:38:44 faye kernel: [   33.476396] ACPI: I/O resource nForce2_smbus [0x1c00-0x1c3f] conflicts with ACPI region SM00 [0x1c00-0x1c05]
Oct  5 23:38:44 faye kernel: [   33.476399] ACPI: Device needs an ACPI driver
Oct  5 23:38:44 faye kernel: [   33.476428] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Oct  5 23:38:44 faye kernel: [   33.476446] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c80
Oct  5 23:38:44 faye kernel: [   33.502445] Linux video capture interface: v2.00
Oct  5 23:38:44 faye kernel: [   33.571986] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Oct  5 23:38:44 faye kernel: [   33.672618] nvidia: module license 'NVIDIA' taints kernel.
Oct  5 23:38:44 faye kernel: [   33.770050] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a4)
Oct  5 23:38:44 faye kernel: [   33.792918] input: UVC Camera (046d:09a4) as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2:1.0/input/input5
Oct  5 23:38:44 faye kernel: [   33.836046] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Oct  5 23:38:44 faye kernel: [   33.836051] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
Oct  5 23:38:44 faye kernel: [   33.836280] HDA Intel 0000:00:10.1: setting latency timer to 64
Oct  5 23:38:44 faye kernel: [   33.927725] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
Oct  5 23:38:44 faye kernel: [   33.927730] nvidia 0000:01:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
Oct  5 23:38:44 faye kernel: [   33.927736] nvidia 0000:01:00.0: setting latency timer to 64
Oct  5 23:38:44 faye kernel: [   33.927891] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Oct  5 23:38:44 faye kernel: [   33.929870] usbcore: registered new interface driver uvcvideo
Oct  5 23:38:44 faye kernel: [   33.929874] USB Video Class driver (v0.1.0)
Oct  5 23:38:44 faye kernel: [   34.029140] psmouse serio1: ID: 10 00 64<4>logips2pp: Detected unknown logitech mouse model 106
Oct  5 23:38:44 faye kernel: [   34.558228] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
Oct  5 23:38:44 faye kernel: [   34.930092] 2:3:1: cannot get freq at ep 0x86
Oct  5 23:38:44 faye kernel: [   35.618964] usbcore: registered new interface driver snd-usb-audio
Oct  5 23:38:44 faye kernel: [   35.734691] lp0: using parport0 (interrupt-driven).
Oct  5 23:38:44 faye kernel: [   35.757142] it87: Found IT8718F chip at 0x290, revision 2
Oct  5 23:38:44 faye kernel: [   35.757152] it87: in3 is VCC (+5V)
Oct  5 23:38:44 faye kernel: [   35.757154] it87: in7 is VCCH (+5V Stand-By)
Oct  5 23:38:44 faye kernel: [   35.766247] coretemp coretemp.0: Using relative temperature scale!
Oct  5 23:38:44 faye kernel: [   35.766287] coretemp coretemp.1: Using relative temperature scale!
Oct  5 23:38:44 faye kernel: [   35.844175] Adding 10586792k swap on /dev/sda5.  Priority:-1 extents:1 across:10586792k
Oct  5 23:38:44 faye kernel: [   36.376258] EXT3 FS on sda1, internal journal
Oct  5 23:38:44 faye kernel: [   37.332994] type=1505 audit(1254778723.307:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2245
Oct  5 23:38:44 faye kernel: [   37.373352] type=1505 audit(1254778723.347:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2249
Oct  5 23:38:44 faye kernel: [   37.373443] type=1505 audit(1254778723.347:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2249
Oct  5 23:38:44 faye kernel: [   37.373477] type=1505 audit(1254778723.347:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2249
Oct  5 23:38:44 faye kernel: [   37.373510] type=1505 audit(1254778723.347:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2249
Oct  5 23:38:44 faye kernel: [   37.397731] type=1505 audit(1254778723.369:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2254
Oct  5 23:38:44 faye kernel: [   37.509290] type=1505 audit(1254778723.477:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2258
Oct  5 23:38:44 faye kernel: [   37.509475] type=1505 audit(1254778723.477:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2258
Oct  5 23:38:44 faye kernel: [   37.535451] type=1505 audit(1254778723.507:10): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2262
Oct  5 23:38:44 faye kernel: [   37.558512] type=1505 audit(1254778723.527:11): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2266
Oct  5 23:38:55 faye kernel: [   49.616042] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Oct  5 23:38:55 faye kernel: [   49.616044] vboxdrv: Successfully done.
Oct  5 23:38:55 faye kernel: [   49.616046] vboxdrv: Found 2 processor cores.
Oct  5 23:38:55 faye kernel: [   49.616104] vboxdrv: fAsync=0 offMin=0x1ad offMax=0xb58
Oct  5 23:38:55 faye kernel: [   49.616141] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Oct  5 23:38:55 faye kernel: [   49.616143] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
Oct  5 23:38:57 faye kernel: [   51.381775] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Oct  5 23:38:57 faye kernel: [   51.381778] Bluetooth: BNEP filters: protocol multicast
Oct  5 23:38:57 faye kernel: [   51.420941] Bridge firewalling registered
Oct  5 23:39:09 faye kernel: [   66.980031] eth0: no IPv6 routers present

```

Here it is the log file, i noticed nothing about the freeze. Frustrating.
Thank you for replying

---

### Post by grafted_scion on 2009-10-09
You are not alone, i have been having the exact same problem for a month or so.
Random hard freeze and no errors to see in any of the log files but this:

"Oct  9 00:29:10 ******** pulseaudio[3315]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Oct  9 00:29:10 ******** pulseaudio[3315]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense."

I have reinstalled pulseaudio only to end up with the same problem after a few hours.

Tried nvidia drivers from 173 to 190 because i thought for a few weeks nvidia driver was the culprit.
memory seems ok

Its a old computer a Fujitsu Siemens Scaleo H with Asus P5LD2-FM working just fine in windoze

After decades of windows tweaking i jumped on the ubuntu wagon a few months ago and i don't want to go back.

Please help.

---

### Post by Varro on 2009-10-09
Hi grafted_scion, i looked for a solution everywhere. I tried also to use LTS 8.04, but this does not solve the problem.
Someone said i have hardware issues but it is not right, indeed installed "thanks" to MSDNAA windows 7 and i'm using it since 3 days and i had no system freezes.
So it's something related to Ubuntu, i tried to upgrade and compile last alsa drivers but nothing seems to solve this problem.
We're in the same boat.

---

### Post by Guy Sibley on 2009-10-09
I am confused about the cause of system freezes in the first place.  I havent been able to isolate any factor that would cause everything to so suddenly stop responding, including terminal.

---

### Post by Varro on 2009-10-09
You're right, it's very frustrating because it seems a hardware issue since it is not possible to find out a real cause.
But it seems there are lot of people with the same problem.
I'm confused like you.

---

