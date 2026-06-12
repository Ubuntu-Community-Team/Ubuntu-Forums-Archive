---
title: "migration/0 &amp; /1 processes killing CPU all the time"
date: 2011-08-04
forum: General Help
---

### Post by bpmelo on 2011-08-04
Hello everyone, I gave up and turned to the Ubuntu forum hoping someone could shed a light on this annoying problem I have with my Ubuntu installation :

Hardware : Notebook HP DV-4 (Intel Dual Core 2G memory)
Ubuntu : 10.10
Kernel : 2.6.35-30-generic-pae

Just standard installation, what happens is these processes :

migration/0
migration/1

they eat all my CPU during infinite time, my mouse can't barely move, all windows became grayed out and either I wait for like 20 minutes with my CPU at full level or reset.

After I reset the behavior starts again after 2 minutes or after 2 hours.

I checked the system.out logs, nothing appears, also checked the dmesg output, nothing appears there as well.

Also I always try to kill these processes with -9 or -6 with no success at all, they can't be killed !!! what a heck !!??

---

### Post by Gyokuro on 2011-08-04
Hi,

those processes which you are seeing are kernel threads and are responsible to move threads between CPU's and part of the kernel scheduler (for each CPU you will see one). Therefore you can't kill them - however they are busy and it will be interesting why. Can you please post a complete

output of top, your dmesg and lsmod. Thank you in advance.

---

### Post by bpmelo on 2011-08-05
Today my machine is bursting CPU to 100% every couple of seconds, I'm suspecting of a hardware failure somehow, although nothing shows on the kernel logs.

output of "top" :
```
top - 11:09:45 up 1 day, 12:26,  2 users,  load average: 1.60, 1.30, 0.97
Tasks: 167 total,   2 running, 165 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.2%us, 29.4%sy,  0.0%ni, 68.8%id,  0.5%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   4018644k total,  2558904k used,  1459740k free,   320956k buffers
Swap:  3951612k total,        0k used,  3951612k free,  1394460k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
13933 root      RT   0     0    0    0 S   16  0.0 112:20.73 migration/1        
    4 root      RT   0     0    0    0 S   11  0.0   7:51.30 migration/0        
24541 root      15  -5     0    0    0 S    9  0.0   0:13.92 kslowd000          
24520 root      15  -5     0    0    0 S    9  0.0   0:15.56 kslowd001          
24525 root      15  -5     0    0    0 R    7  0.0   0:13.88 kslowd003          
13934 root      20   0     0    0    0 S    3  0.0   0:18.96 ksoftirqd/1        
24542 root      15  -5     0    0    0 S    3  0.0   0:13.65 kslowd002          
14299 bruno     20   0  216m  44m  20m S    2  1.1  33:13.59 plugin-containe    
 1473 root      20   0  105m  44m  20m S    1  1.1  36:08.79 Xorg               
14193 bruno     20   0  835m 296m  40m S    1  7.5  52:29.60 firefox-bin        
24552 bruno     20   0 87988  12m  10m S    1  0.3   0:00.53 gnome-terminal     
 1108 root      20   0 19264 4360 3588 S    0  0.1   0:11.62 NetworkManager     
 1848 bruno     20   0 71468  11m 9028 S    0  0.3   0:14.02 gtk-window-deco    
24575 bruno     20   0  2620 1140  840 R    0  0.0   0:00.26 top                
    1 root      20   0  2888 1692 1224 S    0  0.0   0:00.51 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.01 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   3:22.85 ksoftirqd/0   
```


output of "dmesg" :
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-30-generic-pae (buildd@vernadsky) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #56-Ubuntu SMP Mon Jul 11 21:51:12 UTC 2011 (Ubuntu 2.6.35-30.56-generic-pae 2.6.35.13)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b9e6b000 (usable)
[    0.000000]  BIOS-e820: 00000000b9e6b000 - 00000000b9ebf000 (reserved)
[    0.000000]  BIOS-e820: 00000000b9ebf000 - 00000000b9f83000 (usable)
[    0.000000]  BIOS-e820: 00000000b9f83000 - 00000000b9fbf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b9fbf000 - 00000000b9fdf000 (usable)
[    0.000000]  BIOS-e820: 00000000b9fdf000 - 00000000b9ff6000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b9ff6000 - 00000000b9ffe000 (usable)
[    0.000000]  BIOS-e820: 00000000b9ffe000 - 00000000b9fff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b9fff000 - 00000000ba000000 (usable)
[    0.000000]  BIOS-e820: 00000000ba000000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-combining
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FFF00000 mask FFFF00000 write-protect
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0BA000000 mask FFE000000 uncachable
[    0.000000]   5 base 100000000 mask FC0000000 write-back
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009e000 (usable)
[    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000b9e6b000 (usable)
[    0.000000]  modified: 00000000b9e6b000 - 00000000b9ebf000 (reserved)
[    0.000000]  modified: 00000000b9ebf000 - 00000000b9f83000 (usable)
[    0.000000]  modified: 00000000b9f83000 - 00000000b9fbf000 (ACPI NVS)
[    0.000000]  modified: 00000000b9fbf000 - 00000000b9fdf000 (usable)
[    0.000000]  modified: 00000000b9fdf000 - 00000000b9ff6000 (ACPI data)
[    0.000000]  modified: 00000000b9ff6000 - 00000000b9ffe000 (usable)
[    0.000000]  modified: 00000000b9ffe000 - 00000000b9fff000 (ACPI data)
[    0.000000]  modified: 00000000b9fff000 - 00000000ba000000 (usable)
[    0.000000]  modified: 00000000ba000000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 15000-1a000
[    0.000000] RAMDISK: 375a8000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 00a08000 - 0144f94b
[    0.000000] Move RAMDISK from 00000000375a8000 - 0000000037fef94a to 00a08000 - 0144f94a
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 HP    )
[    0.000000] ACPI: XSDT b9ffe120 00074 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP b9ff3000 000F4 (v04 HP     BLADE    00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT b9fe4000 0A96B (v01 HP     BLADE    00000001 MSFT 01000013)
[    0.000000] ACPI: FACS b9f8c000 00040
[    0.000000] ACPI: DMAR b9ff5000 000B8 (v01               ? 00000001      00000000)
[    0.000000] ACPI: SSDT b9ff4000 00655 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: HPET b9ff2000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC b9ff1000 0006C (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG b9ff0000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: ASF! b9fef000 000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC b9fe3000 00176 (v01 HPQOEM SLIC-MPC 00000001 LOHR 000F4240)
[    0.000000] ACPI: BOOT b9fe2000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT b9fe1000 00296 (v01 INTEL  SataAhci 00001000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4228MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[8] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000b9e6b
[    0.000000]     0: 0x000b9ebf -> 0x000b9f83
[    0.000000]     0: 0x000b9fbf -> 0x000b9fdf
[    0.000000]     0: 0x000b9ff6 -> 0x000b9ffe
[    0.000000]     0: 0x000b9fff -> 0x000ba000
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1023719
[    0.000000] free_area_init_node: node 0, pgdat c0842d00, node_mem_map c1451020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8457 pages used for memmap
[    0.000000]   HighMem zone: 787025 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:38000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c3e00000 s39872 r0 d21568 u524288
[    0.000000] pcpu-alloc: s39872 r0 d21568 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] early_res array is doubled to 128 at [16800 - 177ff]
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1013478
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-30-generic-pae root=UUID=68478cb8-d395-40f8-9e77-241d026b3ceb ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 26214380 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (60 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009ff65c]   TEXT DATA BSS
[    0.000000]   #3 [000009e000 - 0000100000]   BIOS reserved
[    0.000000]   #4 [0000a00000 - 0000a071a4]             BRK
[    0.000000]   #5 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #6 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #7 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #8 [0000a08000 - 0001450000]     NEW RAMDISK
[    0.000000]   #9 [0001450000 - 0001451000]         BOOTMEM
[    0.000000]   #10 [0001451000 - 0003c51000]         BOOTMEM
[    0.000000]   #11 [0003c51000 - 0003c51004]         BOOTMEM
[    0.000000]   #12 [0003c51040 - 0003c51100]         BOOTMEM
[    0.000000]   #13 [0003c51100 - 0003c511a8]         BOOTMEM
[    0.000000]   #14 [0003c511c0 - 0003c541c0]         BOOTMEM
[    0.000000]   #15 [0003c541c0 - 0003c544dc]         BOOTMEM
[    0.000000]   #16 [0003c54500 - 0003c60500]         BOOTMEM
[    0.000000]   #17 [0003c60500 - 0003c6052d]         BOOTMEM
[    0.000000]   #18 [0003c60540 - 0003c6056f]         BOOTMEM
[    0.000000]   #19 [0003c60580 - 0003c608e0]         BOOTMEM
[    0.000000]   #20 [0003c60900 - 0003c60940]         BOOTMEM
[    0.000000]   #21 [0003c60940 - 0003c60980]         BOOTMEM
[    0.000000]   #22 [0003c60980 - 0003c609c0]         BOOTMEM
[    0.000000]   #23 [0003c609c0 - 0003c60a00]         BOOTMEM
[    0.000000]   #24 [0003c60a00 - 0003c60a40]         BOOTMEM
[    0.000000]   #25 [0003c60a40 - 0003c60a80]         BOOTMEM
[    0.000000]   #26 [0003c60a80 - 0003c60ac0]         BOOTMEM
[    0.000000]   #27 [0003c60ac0 - 0003c60b00]         BOOTMEM
[    0.000000]   #28 [0003c60b00 - 0003c60b40]         BOOTMEM
[    0.000000]   #29 [0003c60b40 - 0003c60b80]         BOOTMEM
[    0.000000]   #30 [0003c60b80 - 0003c60bc0]         BOOTMEM
[    0.000000]   #31 [0003c60bc0 - 0003c60c00]         BOOTMEM
[    0.000000]   #32 [0003c60c00 - 0003c60c40]         BOOTMEM
[    0.000000]   #33 [0003c60c40 - 0003c60c80]         BOOTMEM
[    0.000000]   #34 [0003c60c80 - 0003c60cc0]         BOOTMEM
[    0.000000]   #35 [0003c60cc0 - 0003c60d00]         BOOTMEM
[    0.000000]   #36 [0003c60d00 - 0003c60d40]         BOOTMEM
[    0.000000]   #37 [0003c60d40 - 0003c60d80]         BOOTMEM
[    0.000000]   #38 [0003c60d80 - 0003c60dc0]         BOOTMEM
[    0.000000]   #39 [0003c60dc0 - 0003c60e00]         BOOTMEM
[    0.000000]   #40 [0003c60e00 - 0003c60e40]         BOOTMEM
[    0.000000]   #41 [0003c60e40 - 0003c60e50]         BOOTMEM
[    0.000000]   #42 [0003c60e80 - 0003c60e90]         BOOTMEM
[    0.000000]   #43 [0003c60ec0 - 0003c60f2e]         BOOTMEM
[    0.000000]   #44 [0003c60f40 - 0003c60fae]         BOOTMEM
[    0.000000]   #45 [0003e00000 - 0003e0f000]         BOOTMEM
[    0.000000]   #46 [0003e80000 - 0003e8f000]         BOOTMEM
[    0.000000]   #47 [0003f00000 - 0003f0f000]         BOOTMEM
[    0.000000]   #48 [0003f80000 - 0003f8f000]         BOOTMEM
[    0.000000]   #49 [0003c62fc0 - 0003c62fc4]         BOOTMEM
[    0.000000]   #50 [0003c63000 - 0003c63004]         BOOTMEM
[    0.000000]   #51 [0003c63040 - 0003c63050]         BOOTMEM
[    0.000000]   #52 [0003c63080 - 0003c63090]         BOOTMEM
[    0.000000]   #53 [0003c630c0 - 0003c63158]         BOOTMEM
[    0.000000]   #54 [0003c63180 - 0003c631b8]         BOOTMEM
[    0.000000]   #55 [0003c631c0 - 0003c671c0]         BOOTMEM
[    0.000000]   #56 [0003c671c0 - 0003ce71c0]         BOOTMEM
[    0.000000]   #57 [0003ce71c0 - 0003d271c0]         BOOTMEM
[    0.000000]   #58 [0003c60fc0 - 0003c61200]         BOOTMEM
[    0.000000]   #59 [0003f8f000 - 000588efec]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00037bfe:00140000)
[    0.000000] Memory: 4007408k/5242880k available (5097k kernel code, 87468k reserved, 2436k data, 708k init, 3181928k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc085c000 - 0xc090d000   ( 708 kB)
[    0.000000]       .data : 0xc05fa6ba - 0xc085b948   (2436 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05fa6ba   (5097 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2094.804 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4189.60 BogoMIPS (lpj=8379216)
[    0.004010] pid_max: default: 32768 minimum: 301
[    0.004030] Security Framework initialized
[    0.004046] AppArmor: AppArmor initialized
[    0.004048] Yama: becoming mindful.
[    0.004101] Mount-cache hash table entries: 512
[    0.004225] Initializing cgroup subsys ns
[    0.004229] Initializing cgroup subsys cpuacct
[    0.004234] Initializing cgroup subsys memory
[    0.004242] Initializing cgroup subsys devices
[    0.004245] Initializing cgroup subsys freezer
[    0.004247] Initializing cgroup subsys net_cls
[    0.004275] CPU: Physical Processor ID: 0
[    0.004276] CPU: Processor Core ID: 0
[    0.004279] mce: CPU supports 6 MCE banks
[    0.004288] CPU0: Thermal monitoring enabled (TM1)
[    0.004291] using mwait in idle threads.
[    0.004298] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.004306] ... version:                2
[    0.004308] ... bit width:              40
[    0.004309] ... generic registers:      2
[    0.004311] ... value mask:             000000ffffffffff
[    0.004313] ... max period:             000000007fffffff
[    0.004315] ... fixed-purpose events:   3
[    0.004317] ... event mask:             0000000700000003
[    0.007326] ACPI: Core revision 20100428
[    0.024009] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.024014] ftrace: allocating 22411 entries in 44 pages
[    0.028051] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028405] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.071452] CPU0: Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz stepping 0a
[    0.072000] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.160014] Brought up 2 CPUs
[    0.160017] Total of 2 processors activated (8379.56 BogoMIPS).
[    0.161019] devtmpfs: initialized
[    0.161019] regulator: core version 0.5
[    0.161019] Time:  1:42:57  Date: 08/04/11
[    0.161060] NET: Registered protocol family 16
[    0.161081] Trying to unpack rootfs image as initramfs...
[    0.161181] EISA bus registered
[    0.161189] ACPI: bus type pci registered
[    0.161264] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.161267] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.161269] PCI: Using MMCONFIG for extended config space
[    0.161271] PCI: Using configuration type 1 for base access
[    0.168058] bio: create slab <bio-0> at 0
[    0.170593] ACPI: EC: Look up EC in DSDT
[    0.173237] ACPI: Executed 1 blocks of module-level executable AML code
[    0.176039] ACPI: BIOS _OSI(Linux) query ignored
[    0.183672] ACPI: SSDT b9e6ec98 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.184351] ACPI: Dynamic OEM Table Load:
[    0.184354] ACPI: SSDT (null) 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.184703] ACPI: SSDT b9e6c618 005B3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.185349] ACPI: Dynamic OEM Table Load:
[    0.185352] ACPI: SSDT (null) 005B3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.185951] ACPI: SSDT b9e6de18 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.186641] ACPI: Dynamic OEM Table Load:
[    0.186644] ACPI: SSDT (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.186848] ACPI: SSDT b9e6ef18 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.187511] ACPI: Dynamic OEM Table Load:
[    0.187514] ACPI: SSDT (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.318125] ACPI: Interpreter enabled
[    0.318125] ACPI: (supports S0 S3 S4 S5)
[    0.318125] ACPI: Using IOAPIC for interrupt routing
[    0.432709] Freeing initrd memory: 10528k freed
[    0.544287] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.545685] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.565419] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.568111] ACPI: Power Resource [FN00] (off)
[    0.568500] ACPI: No dock devices found.
[    0.568505] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.569092] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.570239] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.570243] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.570246] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.570250] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
[    0.570321] pci 0000:00:02.0: reg 10: [mem 0xd0000000-0xd03fffff 64bit]
[    0.570329] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.570334] pci 0000:00:02.0: reg 20: [io  0x60f0-0x60f7]
[    0.570374] pci 0000:00:02.1: reg 10: [mem 0xd5400000-0xd54fffff 64bit]
[    0.570491] pci 0000:00:1a.0: reg 20: [io  0x60c0-0x60df]
[    0.570617] pci 0000:00:1a.1: reg 20: [io  0x60a0-0x60bf]
[    0.570723] pci 0000:00:1a.7: reg 10: [mem 0xda504c00-0xda504fff]
[    0.570799] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.570805] pci 0000:00:1a.7: PME# disabled
[    0.570854] pci 0000:00:1b.0: reg 10: [mem 0xda500000-0xda503fff 64bit]
[    0.570917] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.570921] pci 0000:00:1b.0: PME# disabled
[    0.571021] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.571026] pci 0000:00:1c.0: PME# disabled
[    0.572104] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.572109] pci 0000:00:1c.2: PME# disabled
[    0.572210] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.572215] pci 0000:00:1c.3: PME# disabled
[    0.572314] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.572318] pci 0000:00:1c.4: PME# disabled
[    0.572415] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.572420] pci 0000:00:1c.5: PME# disabled
[    0.572508] pci 0000:00:1d.0: reg 20: [io  0x6080-0x609f]
[    0.572633] pci 0000:00:1d.1: reg 20: [io  0x6060-0x607f]
[    0.572758] pci 0000:00:1d.2: reg 20: [io  0x6040-0x605f]
[    0.572863] pci 0000:00:1d.7: reg 10: [mem 0xda504800-0xda504bff]
[    0.572938] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.572943] pci 0000:00:1d.7: PME# disabled
[    0.573166] pci 0000:00:1f.2: reg 10: [io  0x60e8-0x60ef]
[    0.573173] pci 0000:00:1f.2: reg 14: [io  0x60fc-0x60ff]
[    0.573180] pci 0000:00:1f.2: reg 18: [io  0x60e0-0x60e7]
[    0.573188] pci 0000:00:1f.2: reg 1c: [io  0x60f8-0x60fb]
[    0.573195] pci 0000:00:1f.2: reg 20: [io  0x6020-0x603f]
[    0.573203] pci 0000:00:1f.2: reg 24: [mem 0xda504000-0xda5047ff]
[    0.573250] pci 0000:00:1f.2: PME# supported from D3hot
[    0.573254] pci 0000:00:1f.2: PME# disabled
[    0.573293] pci 0000:00:1f.3: reg 10: [mem 0xda505000-0xda5050ff 64bit]
[    0.573313] pci 0000:00:1f.3: reg 20: [io  0x6000-0x601f]
[    0.573396] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.573401] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.573407] pci 0000:00:1c.0:   bridge window [mem 0xd9500000-0xda4fffff]
[    0.573415] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd13fffff 64bit pref]
[    0.573688] pci 0000:02:00.0: reg 10: [mem 0xd8500000-0xd8503fff 64bit]
[    0.573804] pci 0000:02:00.0: supports D1 D2
[    0.573882] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    0.573887] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.573892] pci 0000:00:1c.2:   bridge window [mem 0xd8500000-0xd94fffff]
[    0.573901] pci 0000:00:1c.2:   bridge window [mem 0xd1400000-0xd23fffff 64bit pref]
[    0.574069] pci 0000:03:00.0: reg 10: [io  0x3000-0x30ff]
[    0.574146] pci 0000:03:00.0: reg 18: [mem 0xd2410000-0xd2410fff 64bit pref]
[    0.574197] pci 0000:03:00.0: reg 20: [mem 0xd2400000-0xd240ffff 64bit pref]
[    0.574224] pci 0000:03:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.574375] pci 0000:03:00.0: supports D1 D2
[    0.574377] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.574392] pci 0000:03:00.0: PME# disabled
[    0.574537] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    0.574542] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.574547] pci 0000:00:1c.3:   bridge window [mem 0xd7500000-0xd84fffff]
[    0.574555] pci 0000:00:1c.3:   bridge window [mem 0xd2400000-0xd33fffff 64bit pref]
[    0.574651] pci 0000:04:00.0: reg 10: [mem 0xd6500300-0xd65003ff]
[    0.574804] pci 0000:04:00.2: reg 10: [mem 0xd6500200-0xd65002ff]
[    0.574955] pci 0000:04:00.3: reg 10: [mem 0xd6500100-0xd65001ff]
[    0.575104] pci 0000:04:00.4: reg 10: [mem 0xd6500000-0xd65000ff]
[    0.580023] pci 0000:00:1c.4: PCI bridge to [bus 04-04]
[    0.580029] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    0.580033] pci 0000:00:1c.4:   bridge window [mem 0xd6500000-0xd74fffff]
[    0.580041] pci 0000:00:1c.4:   bridge window [mem 0xd3400000-0xd43fffff 64bit pref]
[    0.580103] pci 0000:00:1c.5: PCI bridge to [bus 05-07]
[    0.580108] pci 0000:00:1c.5:   bridge window [io  0x1000-0x1fff]
[    0.580113] pci 0000:00:1c.5:   bridge window [mem 0xd5500000-0xd64fffff]
[    0.580121] pci 0000:00:1c.5:   bridge window [mem 0xd4400000-0xd53fffff 64bit pref]
[    0.580205] pci 0000:00:1e.0: PCI bridge to [bus 08-08] (subtractive decode)
[    0.580210] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.580216] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.580223] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.580226] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.580228] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.580231] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.580234] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    0.580271] pci_bus 0000:00: on NUMA node 0
[    0.580278] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.580649] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.580817] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.580936] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.581067] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.581199] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    0.581374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP6._PRT]
[    0.592959] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.593107] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.593255] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.593400] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.593545] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.593689] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.593834] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.593978] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.594053] HEST: Table is not found!
[    0.594133] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.594151] vgaarb: loaded
[    0.594322] SCSI subsystem initialized
[    0.594332] libata version 3.00 loaded.
[    0.594332] usbcore: registered new interface driver usbfs
[    0.594332] usbcore: registered new interface driver hub
[    0.594332] usbcore: registered new device driver usb
[    0.594332] ACPI: WMI: Mapper loaded
[    0.594332] PCI: Using ACPI for IRQ routing
[    0.594332] PCI: pci_cache_line_size set to 64 bytes
[    0.594332] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.594332] reserve RAM buffer: 000000000009e000 - 000000000009ffff 
[    0.594332] reserve RAM buffer: 00000000b9e6b000 - 00000000bbffffff 
[    0.594332] reserve RAM buffer: 00000000b9f83000 - 00000000bbffffff 
[    0.594332] reserve RAM buffer: 00000000b9fdf000 - 00000000bbffffff 
[    0.594332] reserve RAM buffer: 00000000b9ffe000 - 00000000bbffffff 
[    0.594332] reserve RAM buffer: 00000000ba000000 - 00000000bbffffff 
[    0.594332] NetLabel: Initializing
[    0.594332] NetLabel:  domain hash size = 128
[    0.594332] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.594332] NetLabel:  unlabeled traffic allowed by default
[    0.594332] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.594332] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.594332] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.600021] Switching to clocksource tsc
[    0.610759] AppArmor: AppArmor Filesystem Enabled
[    0.610776] pnp: PnP ACPI init
[    0.610797] ACPI: bus type pnp registered
[    0.725174] pnp 00:01: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.5 BAR 13 [io  0x1000-0x1fff]
[    0.726026]   alloc irq_desc for 23 on node -1
[    0.726028]   alloc kstat_irqs on node -1
[    0.726578] pnp: PnP ACPI: found 11 devices
[    0.726580] ACPI: ACPI bus type pnp unregistered
[    0.726584] PnPBIOS: Disabled by ACPI PNP
[    0.726596] system 00:01: [io  0x0600-0x060f] has been reserved
[    0.726599] system 00:01: [io  0x0610] has been reserved
[    0.726602] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.726605] system 00:01: [io  0x0810-0x0817] has been reserved
[    0.726608] system 00:01: [io  0x0820-0x0823] has been reserved
[    0.726611] system 00:01: [io  0x0400-0x047f] has been reserved
[    0.726614] system 00:01: [io  0x0500-0x053f] has been reserved
[    0.726618] system 00:01: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.726621] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.726624] system 00:01: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.726627] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.726630] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.726633] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.726636] system 00:01: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.726639] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.762638] pci 0000:03:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.762703] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.762707] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.762714] pci 0000:00:1c.0:   bridge window [mem 0xd9500000-0xda4fffff]
[    0.762719] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd13fffff 64bit pref]
[    0.762727] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    0.762730] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.762737] pci 0000:00:1c.2:   bridge window [mem 0xd8500000-0xd94fffff]
[    0.762742] pci 0000:00:1c.2:   bridge window [mem 0xd1400000-0xd23fffff 64bit pref]
[    0.762753] pci 0000:03:00.0: BAR 6: assigned [mem 0xd2420000-0xd243ffff pref]
[    0.762756] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    0.762759] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.762766] pci 0000:00:1c.3:   bridge window [mem 0xd7500000-0xd84fffff]
[    0.762771] pci 0000:00:1c.3:   bridge window [mem 0xd2400000-0xd33fffff 64bit pref]
[    0.762780] pci 0000:00:1c.4: PCI bridge to [bus 04-04]
[    0.762783] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    0.762790] pci 0000:00:1c.4:   bridge window [mem 0xd6500000-0xd74fffff]
[    0.762795] pci 0000:00:1c.4:   bridge window [mem 0xd3400000-0xd43fffff 64bit pref]
[    0.762803] pci 0000:00:1c.5: PCI bridge to [bus 05-07]
[    0.762807] pci 0000:00:1c.5:   bridge window [io  0x1000-0x1fff]
[    0.762814] pci 0000:00:1c.5:   bridge window [mem 0xd5500000-0xd64fffff]
[    0.762819] pci 0000:00:1c.5:   bridge window [mem 0xd4400000-0xd53fffff 64bit pref]
[    0.762827] pci 0000:00:1e.0: PCI bridge to [bus 08-08]
[    0.762829] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.762835] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.762840] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.762857]   alloc irq_desc for 16 on node -1
[    0.762858]   alloc kstat_irqs on node -1
[    0.762863] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.762869] pci 0000:00:1c.0: setting latency timer to 64
[    0.762879]   alloc irq_desc for 18 on node -1
[    0.762881]   alloc kstat_irqs on node -1
[    0.762885] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.762890] pci 0000:00:1c.2: setting latency timer to 64
[    0.762900]   alloc irq_desc for 19 on node -1
[    0.762901]   alloc kstat_irqs on node -1
[    0.762905] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.762910] pci 0000:00:1c.3: setting latency timer to 64
[    0.762920] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.762925] pci 0000:00:1c.4: setting latency timer to 64
[    0.762935]   alloc irq_desc for 17 on node -1
[    0.762937]   alloc kstat_irqs on node -1
[    0.762941] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.762946] pci 0000:00:1c.5: setting latency timer to 64
[    0.762954] pci 0000:00:1e.0: setting latency timer to 64
[    0.762958] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.762961] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.762963] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.762965] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfebfffff]
[    0.762968] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    0.762970] pci_bus 0000:01: resource 1 [mem 0xd9500000-0xda4fffff]
[    0.762973] pci_bus 0000:01: resource 2 [mem 0xd0400000-0xd13fffff 64bit pref]
[    0.762975] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.762978] pci_bus 0000:02: resource 1 [mem 0xd8500000-0xd94fffff]
[    0.762980] pci_bus 0000:02: resource 2 [mem 0xd1400000-0xd23fffff 64bit pref]
[    0.762983] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.762985] pci_bus 0000:03: resource 1 [mem 0xd7500000-0xd84fffff]
[    0.762988] pci_bus 0000:03: resource 2 [mem 0xd2400000-0xd33fffff 64bit pref]
[    0.762991] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.762993] pci_bus 0000:04: resource 1 [mem 0xd6500000-0xd74fffff]
[    0.762995] pci_bus 0000:04: resource 2 [mem 0xd3400000-0xd43fffff 64bit pref]
[    0.762998] pci_bus 0000:05: resource 0 [io  0x1000-0x1fff]
[    0.763001] pci_bus 0000:05: resource 1 [mem 0xd5500000-0xd64fffff]
[    0.763003] pci_bus 0000:05: resource 2 [mem 0xd4400000-0xd53fffff 64bit pref]
[    0.763006] pci_bus 0000:08: resource 4 [io  0x0000-0x0cf7]
[    0.763008] pci_bus 0000:08: resource 5 [io  0x0d00-0xffff]
[    0.763010] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
[    0.763013] pci_bus 0000:08: resource 7 [mem 0xc0000000-0xfebfffff]
[    0.763047] NET: Registered protocol family 2
[    0.763116] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.763371] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.763840] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.764050] TCP: Hash tables configured (established 131072 bind 65536)
[    0.764053] TCP reno registered
[    0.764056] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.764066] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.764151] NET: Registered protocol family 1
[    0.764167] pci 0000:00:02.0: Boot video device
[    0.796101] PCI: CLS 64 bytes, default 64
[    0.796125] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.796127] Simple Boot Flag at 0x44 set to 0x1
[    0.796303] cpufreq-nforce2: No nForce2 chipset.
[    0.796334] Scanning for low memory corruption every 60 seconds
[    0.796463] audit: initializing netlink socket (disabled)
[    0.796473] type=2000 audit(1312422177.792:1): initialized
[    0.807602] highmem bounce pool size: 64 pages
[    0.807608] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.809037] VFS: Disk quotas dquot_6.5.2
[    0.809100] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.809685] fuse init (API version 7.14)
[    0.809776] msgmni has been set to 1632
[    0.812263] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.812267] io scheduler noop registered
[    0.812268] io scheduler deadline registered
[    0.812282] io scheduler cfq registered (default)
[    0.812409] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.812459]   alloc irq_desc for 40 on node -1
[    0.812461]   alloc kstat_irqs on node -1
[    0.812473] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.812580] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.812627]   alloc irq_desc for 41 on node -1
[    0.812628]   alloc kstat_irqs on node -1
[    0.812637] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    0.812739] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.812786]   alloc irq_desc for 42 on node -1
[    0.812788]   alloc kstat_irqs on node -1
[    0.812796] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.812900] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.812947]   alloc irq_desc for 43 on node -1
[    0.812949]   alloc kstat_irqs on node -1
[    0.812958] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
[    0.813061] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.813108]   alloc irq_desc for 44 on node -1
[    0.813110]   alloc kstat_irqs on node -1
[    0.813121] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
[    0.813252] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.813482] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.813573] intel_idle: MWAIT substates: 0x22220
[    0.813575] intel_idle: does not run on family 6 model 23
[    0.940065] ACPI: AC Adapter [AC] (on-line)
[    0.940145] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.940151] ACPI: Power Button [PWRB]
[    0.940192] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.940262] ACPI: Lid Switch [LID0]
[    0.940306] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.940310] ACPI: Sleep Button [SLPB]
[    0.940373] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.940377] ACPI: Power Button [PWRF]
[    0.949726] ACPI: Fan [FAN] (off)
[    0.950224] ACPI: acpi_idle registered with cpuidle
[    0.950434] Monitor-Mwait will be used to enter C-1 state
[    0.950454] Monitor-Mwait will be used to enter C-2 state
[    0.950471] Monitor-Mwait will be used to enter C-3 state
[    0.950476] Marking TSC unstable due to TSC halts in idle
[    0.950517] Switching to clocksource hpet
[    1.101487] thermal LNXTHERM:01: registered as thermal_zone0
[    1.101534] ACPI: Thermal Zone [THRM] (23 C)
[    1.101627] ERST: Table is not found!
[    1.101669] isapnp: Scanning for PnP cards...
[    1.101905] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.103384] brd: module loaded
[    1.104007] loop: module loaded
[    1.104521] Fixed MDIO Bus: probed
[    1.104553] PPP generic driver version 2.4.2
[    1.104586] tun: Universal TUN/TAP device driver, 1.6
[    1.104588] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.104668] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.104690] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.104702] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.104706] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.104743] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.104778] ehci_hcd 0000:00:1a.7: debug port 1
[    1.108654] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    1.108672] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xda504c00
[    1.124515] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.124624] hub 1-0:1.0: USB hub found
[    1.124628] hub 1-0:1.0: 4 ports detected
[    1.124704]   alloc irq_desc for 20 on node -1
[    1.124706]   alloc kstat_irqs on node -1
[    1.124712] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.124723] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.124727] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.124759] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.124793] ehci_hcd 0000:00:1d.7: debug port 1
[    1.128672] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.128687] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xda504800
[    1.144514] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.144624] hub 2-0:1.0: USB hub found
[    1.144630] hub 2-0:1.0: 6 ports detected
[    1.144707] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.144721] uhci_hcd: USB Universal Host Controller Interface driver
[    1.144740] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.144747] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.144751] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.144781] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.144818] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000060c0
[    1.144932] hub 3-0:1.0: USB hub found
[    1.144937] hub 3-0:1.0: 2 ports detected
[    1.145000] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.145007] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.145011] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.145041] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.145077] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000060a0
[    1.145188] hub 4-0:1.0: USB hub found
[    1.145192] hub 4-0:1.0: 2 ports detected
[    1.145260] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.145267] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.145270] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.145302] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.145329] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006080
[    1.145444] hub 5-0:1.0: USB hub found
[    1.145448] hub 5-0:1.0: 2 ports detected
[    1.145511]   alloc irq_desc for 22 on node -1
[    1.145513]   alloc kstat_irqs on node -1
[    1.145518] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.145524] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.145528] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.145560] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.145597] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00006060
[    1.145712] hub 6-0:1.0: USB hub found
[    1.145716] hub 6-0:1.0: 2 ports detected
[    1.145778] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.145784] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.145788] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.145818] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.145845] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006040
[    1.145957] hub 7-0:1.0: USB hub found
[    1.145961] hub 7-0:1.0: 2 ports detected
[    1.146088] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    1.182212] ACPI: Battery Slot [BAT0] (battery absent)
[    1.189245] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.189251] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.189307] mice: PS/2 mouse device common for all mice
[    1.189453] rtc_cmos 00:03: RTC can wake from S4
[    1.189486] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.189518] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.189617] device-mapper: uevent: version 1.0.3
[    1.189717] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    1.189781] device-mapper: multipath: version 1.1.1 loaded
[    1.189783] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.189892] EISA: Probing bus 0 at eisa.0
[    1.189894] EISA: Cannot allocate resource for mainboard
[    1.189896] Cannot allocate resource for EISA slot 1
[    1.189898] Cannot allocate resource for EISA slot 2
[    1.189900] Cannot allocate resource for EISA slot 3
[    1.189902] Cannot allocate resource for EISA slot 4
[    1.189904] Cannot allocate resource for EISA slot 5
[    1.189906] Cannot allocate resource for EISA slot 6
[    1.189908] Cannot allocate resource for EISA slot 7
[    1.189910] Cannot allocate resource for EISA slot 8
[    1.189912] EISA: Detected 0 cards.
[    1.190040] cpuidle: using governor ladder
[    1.190144] cpuidle: using governor menu
[    1.190450] TCP cubic registered
[    1.190582] NET: Registered protocol family 10
[    1.190949] lo: Disabled Privacy Extensions
[    1.191183] NET: Registered protocol family 17
[    1.191713] Using IPI No-Shortcut mode
[    1.191788] PM: Resume from disk failed.
[    1.191798] registered taskstats version 1
[    1.192522]   Magic number: 7:99:710
[    1.193939] rtc_cmos 00:03: setting system clock to 2011-08-04 01:42:58 UTC (1312422178)
[    1.193942] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.193943] EDD information not available.
[    1.234258] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.455601] isapnp: No Plug & Play device found
[    1.455655] Freeing unused kernel memory: 708k freed
[    1.456038] Write protecting the kernel text: 5100k
[    1.456140] Write protecting the kernel read-only data: 2016k
[    1.472805] udev[82]: starting version 163
[    1.557670] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.557723] r8169 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.557777] r8169 0000:03:00.0: setting latency timer to 64
[    1.557836]   alloc irq_desc for 45 on node -1
[    1.557838]   alloc kstat_irqs on node -1
[    1.557855] r8169 0000:03:00.0: irq 45 for MSI/MSI-X
[    1.558386] r8169 0000:03:00.0: eth0: RTL8102e at 0xf849e000, 00:23:5a:b9:e5:3d, XID 04c00000 IRQ 45
[    1.568557] usb 2-5: new high speed USB device using ehci_hcd and address 3
[    1.587776] ahci 0000:00:1f.2: version 3.0
[    1.587797]   alloc irq_desc for 21 on node -1
[    1.587799]   alloc kstat_irqs on node -1
[    1.587806] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.587852]   alloc irq_desc for 46 on node -1
[    1.587854]   alloc kstat_irqs on node -1
[    1.587864] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
[    1.587921] ahci: SSS flag set, parallel bus scan disabled
[    1.587962] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.587966] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems sxs 
[    1.587972] ahci 0000:00:1f.2: setting latency timer to 64
[    1.588582] sdhci: Secure Digital Host Controller Interface driver
[    1.588584] sdhci: Copyright(c) Pierre Ossman
[    1.589967] sdhci-pci 0000:04:00.0: SDHCI controller found [197b:2382] (rev 0)
[    1.589991] sdhci-pci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.590035] sdhci-pci 0000:04:00.0: setting latency timer to 64
[    1.590076] Registered led device: mmc0::
[    1.590124] mmc0: SDHCI controller on PCI [0000:04:00.0] using ADMA
[    1.590136] sdhci-pci 0000:04:00.2: SDHCI controller found [197b:2381] (rev 0)
[    1.590156] sdhci-pci 0000:04:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.590163] sdhci-pci 0000:04:00.2: Refusing to bind to secondary interface.
[    1.590171] sdhci-pci 0000:04:00.2: PCI INT A disabled
[    1.654604] scsi0 : ahci
[    1.654740] scsi1 : ahci
[    1.654810] scsi2 : ahci
[    1.654878] scsi3 : ahci
[    1.654946] scsi4 : ahci
[    1.655015] scsi5 : ahci
[    1.655382] ata1: SATA max UDMA/133 abar m2048@0xda504000 port 0xda504100 irq 46
[    1.655387] ata2: SATA max UDMA/133 abar m2048@0xda504000 port 0xda504180 irq 46
[    1.655390] ata3: DUMMY
[    1.655391] ata4: DUMMY
[    1.655394] ata5: SATA max UDMA/133 abar m2048@0xda504000 port 0xda504300 irq 46
[    1.655398] ata6: SATA max UDMA/133 abar m2048@0xda504000 port 0xda504380 irq 46
[    1.940101] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    2.144538] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.144849] usbcore: registered new interface driver hiddev
[    2.145427] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.145499] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    2.145565] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 (SET FEATURES) succeeded
[    2.145572] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.145645] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    2.145703] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) succeeded
[    2.146109] ata1.00: ATA-8: TOSHIBA MK3255GSX, FG011C, max UDMA/100
[    2.146114] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.147054] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.147116] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    2.147123] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.147195] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    2.147245] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) succeeded
[    2.147685] ata1.00: configured for UDMA/100
[    2.148200] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input5
[    2.148279] generic-usb 0003:046D:C529.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[    2.153177] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input6
[    2.153304] generic-usb 0003:046D:C529.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
[    2.153319] usbcore: registered new interface driver usbhid
[    2.153320] usbhid: USB HID core driver
[    2.160248] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3255GS FG01 PQ: 0 ANSI: 5
[    2.160398] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.160481] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.160532] sd 0:0:0:0: [sda] Write Protect is off
[    2.160535] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.160556] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.160732]  sda: sda1 sda2 < sda5 >
[    2.260848] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.168632] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    8.168110] ata2.00: qc timeout (cmd 0xa1)
[    8.168122] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[    8.772135] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   18.772095] ata2.00: qc timeout (cmd 0xa1)
[   18.772106] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   18.772111] ata2: limiting SATA link speed to 1.5 Gbps
[   19.376135] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   49.376127] ata2.00: qc timeout (cmd 0xa1)
[   49.376142] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   49.980109] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   50.316138] ata5: SATA link down (SStatus 0 SControl 300)
[   50.652110] ata6: SATA link down (SStatus 0 SControl 300)
[   65.689478] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[   65.689482] EXT4-fs (sda1): write access will be enabled during recovery
[   70.196320] EXT4-fs (sda1): orphan cleanup on readonly fs
[   70.230606] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 8913050
[   70.230732] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 8913047
[   70.230760] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 8913029
[   70.230791] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 12067940
[   70.248977] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 12063377
[   70.249027] EXT4-fs (sda1): 5 orphan inodes deleted
[   70.249033] EXT4-fs (sda1): recovery complete
[   70.539330] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   82.413008] udev[530]: starting version 163
[   82.475702] lp: driver loaded but no devices found
[   82.544496] Adding 3951612k swap on /dev/sda5.  Priority:-1 extents:1 across:3951612k 
[   82.597037] lirc_dev: IR Remote Control driver registered, major 250 
[   82.597128] lirc_ene0100: module is from the staging directory, the quality is unknown, you have been warned.
[   82.597822] enecir 00:0a: lirc_dev: driver enecir registered at minor = 0
[   82.597894] enecir: unknown ENE chip detected, assuming KB3926D
[   82.597896] enecir: driver support incomplete
[   82.597898] enecir: chip is 0x3926 - 0x00, 0xd2
[   82.597906] enecir: hardware features:
[   82.597908] enecir: learning and tx off, gpio40_learn off, fan_in off
[   82.597909] enecir: driver has been succesfully loaded
[   82.617987] lis3lv02d: laptop model unknown, using default axes configuration
[   82.618673] lis3lv02d: 8 bits sensor found
[   82.660172] Linux agpgart interface v0.103
[   82.663465] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[   82.711547] lib80211: common routines for IEEE802.11 drivers
[   82.711551] lib80211_crypt: registered algorithm 'NULL'
[   82.754906] jmb38x_ms 0000:04:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   82.754915] jmb38x_ms 0000:04:00.3: setting latency timer to 64
[   82.770356] agpgart-intel 0000:00:00.0: detected 65532K stolen memory, trimming to 32768K
[   82.788518] wl: module license 'MIXED/Proprietary' taints kernel.
[   82.788521] Disabling lock debugging due to kernel taint
[   82.804433] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input7
[   82.804742] Registered led device: hp::hddprotect
[   82.804782] lis3lv02d driver loaded.
[   82.815838] Linux video capture interface: v2.00
[   82.841309] input: HP WMI hotkeys as /devices/virtual/input/input8
[   82.842635] wl 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   82.842646] wl 0000:02:00.0: setting latency timer to 64
[   82.847368] uvcvideo: Found UVC 1.00 device HP Webcam (090c:137b)
[   82.887508] lib80211_crypt: registered algorithm 'TKIP'
[   82.887775] eth1: Broadcom BCM432b 802.11 Hybrid Wireless Controller 5.60.48.36 
[   82.890254] [drm] Initialized drm 1.1.0 20060810
[   82.912185] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   82.946537] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   82.946544] i915 0000:00:02.0: setting latency timer to 64
[   82.982041] type=1400 audit(1312422260.282:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=903 comm="apparmor_parser"
[   82.982731] type=1400 audit(1312422260.282:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=903 comm="apparmor_parser"
[   82.983108] type=1400 audit(1312422260.282:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=903 comm="apparmor_parser"
[   82.984530] type=1400 audit(1312422260.282:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=917 comm="apparmor_parser"
[   82.985230] type=1400 audit(1312422260.282:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=917 comm="apparmor_parser"
[   82.985607] type=1400 audit(1312422260.282:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=917 comm="apparmor_parser"
[   82.987078] type=1400 audit(1312422260.282:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=922 comm="apparmor_parser"
[   82.987767] type=1400 audit(1312422260.290:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=922 comm="apparmor_parser"
[   82.988143] type=1400 audit(1312422260.290:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=922 comm="apparmor_parser"
[   82.990708] [drm] detected 63M stolen memory, trimming to 32M
[   82.990790]   alloc irq_desc for 47 on node -1
[   82.990793]   alloc kstat_irqs on node -1
[   82.990802] i915 0000:00:02.0: irq 47 for MSI/MSI-X
[   82.990816] [drm] set up 32M of stolen space
[   82.991004] [drm:init_ring_common] *ERROR* render ring head not reset to zero ctl 00000000 head 02001000 tail 00000000 start 02001000
[   82.991081] [drm:init_ring_common] *ERROR* render ring head forced to zero ctl 00000000 head 00000000 tail 00000000 start 02001000
[   83.078099] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input9
[   83.078156] usbcore: registered new interface driver uvcvideo
[   83.078158] USB Video Class driver (v0.1.0)
[   83.108229] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   83.188549] Skipping EDID probe due to cached edid
[   83.229264] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   83.400602] type=1400 audit(1312422260.702:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1093 comm="apparmor_parser"
[   83.498283] r8169 0000:03:00.0: eth0: link down
[   83.498471] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   83.542336] Console: switching to colour frame buffer device 160x50
[   83.546157] fb0: inteldrmfb frame buffer device
[   83.546160] drm: registered panic notifier
[   83.546163] Slow work thread pool: Starting up
[   83.546225] Slow work thread pool: Ready
[   83.546264] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   83.547697] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   83.556599] acpi device:02: registered as cooling_device3
[   83.556932] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10
[   83.556993] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   83.557067] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   83.571086] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   83.585858] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   83.585911] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   83.585974]   alloc irq_desc for 48 on node -1
[   83.585976]   alloc kstat_irqs on node -1
[   83.585990] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   83.586024] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   83.606852] Skipping EDID probe due to cached edid
[   83.744617] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   83.744700] input: HDA Intel Mic at Sep UNKNOWN Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   83.744769] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   83.784261] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input14
[   83.828363] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input15
[   84.053255] ppdev: user-space parallel port driver
[   84.614904] Skipping EDID probe due to cached edid
[   84.848106] Skipping EDID probe due to cached edid
[   85.547453] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   86.380656] ip_tables: (C) 2000-2006 Netfilter Core Team
[   86.392616] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   86.392992] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   86.392995] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   86.392997] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   86.784155] Skipping EDID probe due to cached edid
[   87.012111] Skipping EDID probe due to cached edid
[   87.248147] Skipping EDID probe due to cached edid
[   87.476108] Skipping EDID probe due to cached edid
[   89.167208] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   93.952031] eth1: no IPv6 routers present
[  322.400052] Skipping EDID probe due to cached edid
[  322.636584] Skipping EDID probe due to cached edid
[  322.872124] Skipping EDID probe due to cached edid
[  323.924700] Skipping EDID probe due to cached edid
[  339.760556] Skipping EDID probe due to cached edid
[  586.800704] CE: hpet increased min_delta_ns to 7500 nsec
[ 6928.448758] CE: hpet increased min_delta_ns to 11250 nsec
[70263.940289] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[70267.192031] PM: Syncing filesystems ... done.
[70267.202614] PM: Preparing system for mem sleep
[70276.716332] Freezing user space processes ... (elapsed 0.01 seconds) done.
[70276.732070] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[70276.748056] PM: Entering mem sleep
[70276.748095] Suspending console(s) (use no_console_suspend to debug)
[70276.748741] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[70276.748797] sd 0:0:0:0: [sda] Stopping disk
[70276.805656] ACPI handle has no context!
[70276.805850] jmb38x_ms 0000:04:00.3: PCI INT A disabled
[70276.805966] sdhci-pci 0000:04:00.0: PCI INT A disabled
[70276.806254] wl 0000:02:00.0: PCI INT A disabled
[70276.806262] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[70276.806275] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[70276.806277] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[70276.806312] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[70276.806322] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[70276.806333] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[70276.820038] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[70277.116070] HDA Intel 0000:00:1b.0: PCI INT B disabled
[70277.152552] HDA Intel 0000:00:1b.0: power state changed by ACPI to D3
[70277.152559] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 346.259 msecs
[70277.283998] PM: suspend of drv:sd dev:0:0:0:0 complete after 535.267 msecs
[70277.284011] PM: suspend of drv:scsi dev:target0:0:0 complete after 535.204 msecs
[70277.284019] PM: suspend of drv:scsi dev:host0 complete after 535.104 msecs
[70277.364514] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 558.312 msecs
[70277.364523] PM: suspend of drv: dev:pci0000:00 complete after 557.909 msecs
[70277.364532] PM: suspend of devices complete after 616.086 msecs
[70277.364535] PM: suspend devices took 0.616 seconds
[70277.365180] r8169 0000:03:00.0: PME# enabled
[70277.384553] r8169 0000:03:00.0: wake-up capability enabled by ACPI
[70277.432723] PM: late suspend of devices complete after 68.184 msecs
[70277.433009] ACPI: Preparing to enter system sleep state S3
[70277.433199] PM: Saving platform NVS memory
[70277.440229] Disabling non-boot CPUs ...
[70277.456600] Broke affinity for irq 12
[70277.456625] Broke affinity for irq 18
[70277.560016] CPU 1 is now offline
[70277.560019] SMP alternatives: switching to UP code
[70277.567472] Back to C!
[70277.567472] PM: Restoring platform NVS memory
[70277.567472] Enabling non-boot CPUs ...
[70277.567472] SMP alternatives: switching to SMP code
[70277.574701] Booting Node 0 Processor 1 APIC 0x1
[70277.567110] Initializing CPU#1
[70277.685557] CPU1 is up
[70277.686912] ACPI: Waking up from system sleep state S3
[70277.708320] i915 0000:00:02.0: restoring config space at offset 0x6 (was 0xc, writing 0xc000000c)
[70277.708327] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[70277.708391] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[70277.708434] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[70277.708486] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[70277.708544] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[70277.708551] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[70277.708598] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20005050, writing 0x5050)
[70277.708611] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[70277.708682] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[70277.708754] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[70277.708817] pcieport 0000:00:1c.4: restoring config space at offset 0x7 (was 0x20002020, writing 0x2020)
[70277.708830] pcieport 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[70277.708893] pcieport 0000:00:1c.5: restoring config space at offset 0x7 (was 0x20001010, writing 0x1010)
[70277.708905] pcieport 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[70277.708970] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[70277.709013] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[70277.709055] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[70277.709106] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[70277.709144] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[70277.709149] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
[70277.709155] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x228000f0)
[70277.709167] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[70277.709269] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[70277.709788] r8169 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[70277.709809] r8169 0000:03:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[70277.709990] sdhci-pci 0000:04:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[70277.710028] sdhci-pci 0000:04:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[70277.710080] pci 0000:04:00.2: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[70277.710118] pci 0000:04:00.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100003)
[70277.710170] jmb38x_ms 0000:04:00.3: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[70277.710208] jmb38x_ms 0000:04:00.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[70277.710260] pci 0000:04:00.4: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[70277.710298] pci 0000:04:00.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[70277.710783] PM: early resume of devices complete after 2.648 msecs
[70277.711091] i915 0000:00:02.0: setting latency timer to 64
[70277.711121] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[70277.711127] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[70277.711154] usb usb3: root hub lost power or was reset
[70277.711177] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[70277.711184] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[70277.711210] usb usb4: root hub lost power or was reset
[70277.711231] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[70277.711238] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[70277.711334] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[70277.711341] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[70277.711364] usb usb5: root hub lost power or was reset
[70277.711387] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[70277.711393] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[70277.711419] usb usb6: root hub lost power or was reset
[70277.711450] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[70277.711457] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[70277.711482] usb usb7: root hub lost power or was reset
[70277.711504] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[70277.711511] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[70277.711578] pci 0000:00:1e.0: setting latency timer to 64
[70277.711595] ahci 0000:00:1f.2: setting latency timer to 64
[70277.711654] wl 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[70277.711663] wl 0000:02:00.0: setting latency timer to 64
[70277.734917] sdhci-pci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[70277.734933] sdhci-pci 0000:04:00.0: setting latency timer to 64
[70277.734961] jmb38x_ms 0000:04:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[70277.734968] jmb38x_ms 0000:04:00.3: setting latency timer to 64
[70277.735390] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[70277.735845] sd 0:0:0:0: [sda] Starting disk
[70277.740218] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[70277.751112] r8169 0000:03:00.0: wake-up capability disabled by ACPI
[70277.751130] r8169 0000:03:00.0: PME# disabled
[70277.763814] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[70277.775451] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[70277.791641] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[70277.791651] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[70277.791659] HDA Intel 0000:00:1b.0: setting latency timer to 64
[70277.791708] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[70277.791931] [drm:init_ring_common] *ERROR* render ring head not reset to zero ctl 00000000 head 02001000 tail 00000000 start 02001000
[70277.791936] [drm:init_ring_common] *ERROR* render ring head forced to zero ctl 00000000 head 00000000 tail 00000000 start 02001000
[70277.860116] PM: resume of drv:battery dev:PNP0C0A:00 complete after 124.495 msecs
[70277.876642] PM: resume of drv:usb dev:usb7 complete after 140.945 msecs
[70277.876671] PM: resume of drv:hub dev:7-0:1.0 complete after 140.956 msecs
[70277.876676] PM: resume of drv:usb dev:usb5 complete after 141.647 msecs
[70277.876705] PM: resume of drv:usb dev:usb3 complete after 141.698 msecs
[70277.876710] PM: resume of drv:usb dev:usb4 complete after 141.692 msecs
[70277.876718] PM: resume of drv:hub dev:5-0:1.0 complete after 141.690 msecs
[70277.876727] PM: resume of drv:hub dev:3-0:1.0 complete after 141.715 msecs
[70277.876736] PM: resume of drv:hub dev:4-0:1.0 complete after 141.716 msecs
[70277.980525] PM: resume of drv:usb dev:usb6 complete after 245.494 msecs
[70277.980534] PM: resume of drv:hub dev:6-0:1.0 complete after 244.853 msecs
[70277.988033] PM: resume of drv:usb dev:usb2 complete after 253.035 msecs
[70277.988042] PM: resume of drv:hub dev:2-0:1.0 complete after 253.040 msecs
[70277.988119] PM: resume of drv:ac dev:ACPI0003:00 complete after 127.996 msecs
[70278.068039] ata5: SATA link down (SStatus 0 SControl 300)
[70278.076037] ata6: SATA link down (SStatus 0 SControl 300)
[70278.100028] usb 2-5: reset high speed USB device using ehci_hcd and address 3
[70278.344031] usb 6-1: reset full speed USB device using uhci_hcd and address 2
[70278.499128] PM: resume of drv:usb dev:6-1 complete after 763.325 msecs
[70278.499137] PM: resume of drv:usbhid dev:6-1:1.0 complete after 763.319 msecs
[70278.499143] PM: resume of drv:usbhid dev:6-1:1.1 complete after 763.311 msecs
[70278.576756] PM: resume of drv:i915 dev:0000:00:02.0 complete after 865.665 msecs
[70278.648046] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[70278.662055] PM: resume of drv:usb dev:2-5 complete after 926.293 msecs
[70278.662074] PM: resume of drv:uvcvideo dev:2-5:1.0 complete after 926.297 msecs
[70278.662080] PM: resume of drv:uvcvideo dev:2-5:1.1 complete after 926.284 msecs
[70278.662087] PM: resume of drv: dev:ep_83 complete after 564.081 msecs
[70278.687549] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[70278.708926] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 (SET FEATURES) succeeded
[70278.731418] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 (SET FEATURES) succeeded
[70278.731421] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 (SET FEATURES) filtered out
[70278.755456] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 (SET FEATURES) succeeded
[70278.773078] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 (SET FEATURES) succeeded
[70278.811513] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633M, 0200, max UDMA/100
[70278.858479] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[70279.136119] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 (SET FEATURES) succeeded
[70279.157534] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 (SET FEATURES) succeeded
[70279.157540] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 (SET FEATURES) filtered out
[70279.178896] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 (SET FEATURES) succeeded
[70279.217445] ata2.00: configured for UDMA/100
[70279.307085] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633M  0200 PQ: 0 ANSI: 5
[70279.459744] sr0: scsi3-mmc drive: 8x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[70279.459749] Uniform CD-ROM driver Revision: 3.20
[70279.459923] sr 1:0:0:0: Attached scsi CD-ROM sr0
[70279.459992] sr 1:0:0:0: Attached scsi generic sg1 type 5
[70279.964097] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[70279.965202] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[70279.965275] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[70279.965349] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 (SET FEATURES) succeeded
[70279.965355] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[70279.965425] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[70279.965500] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) succeeded
[70279.967286] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[70279.967376] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[70279.967382] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[70279.967461] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[70279.967538] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) succeeded
[70279.968221] ata1.00: configured for UDMA/100
[70280.016252] PM: resume of drv:sd dev:0:0:0:0 complete after 2280.399 msecs
[70280.016271] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 1354.114 msecs
[70280.016281] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2280.398 msecs
[70280.029136] PM: resume of devices complete after 2318.275 msecs
[70280.029365] PM: resume devices took 2.320 seconds
[70280.029408] PM: Finishing wakeup.
[70280.029409] Restarting tasks ... done.
[70280.044097] video LNXVIDEO:00: Restoring backlight state
[70280.218090] r8169 0000:03:00.0: eth0: link down
[70280.218335] ADDRCONF(NETDEV_UP): eth0: link is not ready
[70280.424566] Skipping EDID probe due to cached edid
[70281.308313] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[70290.600107] eth1: no IPv6 routers present
[70671.664111] Skipping EDID probe due to cached edid
[71932.544222] CE: hpet increased min_delta_ns to 16875 nsec
[127641.164559] Skipping EDID probe due to cached edid
```



output of "lsmod" :```

Module                  Size  Used by
michael_mic             1744  8 
arc4                    1165  4 
ipt_MASQUERADE          1419  1 
iptable_filter          1302  1 
iptable_nat             3752  1 
nf_nat                 16289  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      10783  3 iptable_nat,nf_nat
nf_conntrack           63258  4 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
ip_tables              10492  2 iptable_filter,iptable_nat
x_tables               15921  4 ipt_MASQUERADE,iptable_filter,iptable_nat,ip_tables
binfmt_misc             6599  1 
parport_pc             26378  0 
ppdev                   5556  0 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_idt      54951  1 
snd_hda_intel          22299  2 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
i915                  296491  5 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30168  1 i915
snd_timer              19067  2 snd_pcm,snd_seq
lib80211_crypt_tkip     7736  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   1959565  0 
joydev                  8767  0 
drm                   168796  5 i915,drm_kms_helper
uvcvideo               55943  0 
videodev               43098  1 uvcvideo
hp_wmi                  5223  0 
v4l1_compat            13359  2 uvcvideo,videodev
jmb38x_ms               7483  0 
snd                    49102  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211                5058  2 lib80211_crypt_tkip,wl
intel_agp              26926  2 i915
memstick                8249  1 jmb38x_ms
psmouse                59033  0 
serio_raw               4022  0 
hp_accel               13204  0 
soundcore                880  1 snd
lirc_ene0100            6899  0 
lis3lv02d               8556  1 hp_accel
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
lirc_dev                9393  1 lirc_ene0100
input_polldev           3491  1 lis3lv02d
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
agpgart                32075  2 drm,intel_agp
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36978  0 
hid                    67742  1 usbhid
sdhci_pci               6633  0 
ahci                   19326  2 
sdhci                  15986  1 sdhci_pci
r8169                  36841  0 
mii                     4425  1 r8169
led_class               2633  2 hp_accel,sdhci
libahci                21792  1 ahci
```

Also, I noticed this insane uptime for the migration/1 process, so here's the output of the correct uptime for my machine :
```

bruno@dv4:~$ uptime
 11:27:55 up 1 day, 12:45,  2 users,  load average: 0.18, 0.51, 0.75
bruno@dv4:~$ 
```


Also found out that, these 3 processes run concurrently and the CPU is stalled, and they keep concurring to run for a random time :
```

    4 root      RT   0     0    0    0 S   11  0.0   7:51.30 migration/...
24541 root      15  -5     0    0    0 S    9  0.0   0:13.92 kslowd00...
13933 root      RT   0     0    0    0 S   16  0.0   0:20.73 kondemand/...        

```

These process run at the same time concurring with CPU time and this is what stalls the machine so bad no even the mouse moves correctly.

This is all I found out so far, please help me out so I can figure this out, thanks.

---

### Post by yonib on 2012-01-24
Hi,
my macine also exhibit high cpu load with migration process.

output of top:

```

top - 04:10:42 up  2:19,  1 user,  load average: 0.04, 0.07, 0.06
Tasks: 152 total,   1 running, 151 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.8%us,  0.6%sy,  0.0%ni, 98.5%id,  0.0%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   4020200k total,  2115736k used,  1904464k free,   338184k buffers
Swap:  9822188k total,        0k used,  9822188k free,  1286632k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5303 root      20   0 56408  13m 5100 S    2  0.3   0:46.31 Xorg               
 5722 yoni      20   0 77596  14m  10m S    2  0.4   0:01.89 gnome-terminal     
 5495 yoni      20   0  249m  85m  22m S    1  2.2   0:38.69 compiz             
 2693 root      20   0     0    0    0 S    0  0.0   0:01.31 kworker/u:57       
 5923 yoni      20   0 76156  29m 9804 S    0  0.8   0:03.56 ubuntuone-syncd    
 6692 yoni      20   0  2820 1156  864 R    0  0.0   0:00.15 top                
    1 root      20   0  3320 1952 1288 S    0  0.0   0:00.90 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.86 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0  33:45.85 migration/0        
   17 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset             
   18 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper            
   19 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns              
   21 root      20   0     0    0    0 S    0  0.0   0:00.01 sync_supers        
   22 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default        
   23 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd        
   24 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd

```

dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-15-generic-pae (buildd@zirconium) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #26-Ubuntu SMP Fri Jan 20 17:07:31 UTC 2012 (Ubuntu 3.0.0-15.26-generic-pae 3.0.13)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009a800 (usable)
[    0.000000]  BIOS-e820: 000000000009a800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000caa37000 (usable)
[    0.000000]  BIOS-e820: 00000000caa37000 - 00000000caa7b000 (reserved)
[    0.000000]  BIOS-e820: 00000000caa7b000 - 00000000cadb7000 (usable)
[    0.000000]  BIOS-e820: 00000000cadb7000 - 00000000cade7000 (reserved)
[    0.000000]  BIOS-e820: 00000000cade7000 - 00000000cafe7000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cafe7000 - 00000000cafff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cafff000 - 00000000cb000000 (usable)
[    0.000000]  BIOS-e820: 00000000cb800000 - 00000000cfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 00000000ffc20000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000012f000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Dell Inc. Latitude E5420/0H5TG2, BIOS A03 09/19/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x12f000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FF8000000 write-back
[    0.000000]   3 base 0C8000000 mask FFC000000 write-back
[    0.000000]   4 base 0CB000000 mask FFF000000 uncachable
[    0.000000]   5 base 100000000 mask FE0000000 write-back
[    0.000000]   6 base 120000000 mask FF0000000 write-back
[    0.000000]   7 base 12F000000 mask FFF000000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 128MB, type WB
[    0.000000] reg 3, base: 3200MB, range: 64MB, type WB
[    0.000000] reg 4, base: 3248MB, range: 16MB, type UC
[    0.000000] reg 5, base: 4GB, range: 512MB, type WB
[    0.000000] reg 6, base: 4608MB, range: 256MB, type WB
[    0.000000] reg 7, base: 4848MB, range: 16MB, type UC
[    0.000000] total RAM covered: 4000M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 32M 	num_reg: 8  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 128MB, type WB
[    0.000000] reg 3, base: 3200MB, range: 64MB, type WB
[    0.000000] reg 4, base: 3248MB, range: 16MB, type UC
[    0.000000] reg 5, base: 4GB, range: 512MB, type WB
[    0.000000] reg 6, base: 4608MB, range: 256MB, type WB
[    0.000000] reg 7, base: 4848MB, range: 16MB, type UC
[    0.000000] e820 update range: 00000000cb000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00f1e40] f1e40
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c0096000] 96000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 35986000 - 36cbb000
[    0.000000] ACPI: RSDP 000fe300 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT caffde18 0007C (v01 DELL    CBX3    06222004 MSFT 00010013)
[    0.000000] ACPI: FACP caf87d98 000F4 (v04 DELL    CBX3    06222004 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110413/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xCAFE4E40/0x00000000CAFE4D40, using 32 (20110413/tbfadt-489)
[    0.000000] ACPI: DSDT caf66018 08471 (v02 INT430 SYSFexxx 00001001 INTL 20090903)
[    0.000000] ACPI: FACS cafe4e40 00040
[    0.000000] ACPI: APIC caffcf18 000CC (v02 DELL    CBX3    06222004 MSFT 00010013)
[    0.000000] ACPI: TCPA cafe5d18 00032 (v02                 00000000      00000000)
[    0.000000] ACPI: SSDT caf88a98 002F9 (v01 DELLTP      TPM 00003000 INTL 20090903)
[    0.000000] ACPI: MCFG cafe5c98 0003C (v01 DELL   SNDYBRDG 06222004 MSFT 00000097)
[    0.000000] ACPI: HPET cafe5c18 00038 (v01 A M I   PCHHPET 06222004 AMI. 00000003)
[    0.000000] ACPI: BOOT cafe5b98 00028 (v01 DELL   CBX3     06222004 AMI  00010013)
[    0.000000] ACPI: SSDT caf7d018 00804 (v01  PmRef  Cpu0Ist 00003000 INTL 20090903)
[    0.000000] ACPI: SSDT caf7c018 00996 (v01  PmRef    CpuPm 00003000 INTL 20090903)
[    0.000000] ACPI: DMAR caf87c18 000E8 (v01 INTEL      SNB  00000001 INTL 00000001)
[    0.000000] ACPI: SLIC caf86c18 00176 (v03 DELL    CBX3    06222004 MSFT 00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 3956MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0012f000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000caa37
[    0.000000]     0: 0x000caa7b -> 0x000cadb7
[    0.000000]     0: 0x000cafff -> 0x000cb000
[    0.000000]     0: 0x00100000 -> 0x0012f000
[    0.000000] On node 0 totalpages: 1022206
[    0.000000] free_area_init_node: node 0, pgdat c17f4440, node_mem_map f33a6200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3946 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 221990 pages, LIFO batch:31
[    0.000000]   HighMem zone: 7913 pages used for memmap
[    0.000000]   HighMem zone: 786573 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] 16 Processors exceeds NR_CPUS limit of 8
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] Allocating PCI resources starting at cfa00000 (gap: cfa00000:2f31c000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s29952 r0 d23296 u262144
[    0.000000] pcpu-alloc: s29952 r0 d23296 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1012509
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic-pae root=UUID=a92ec2c6-3c85-4e9b-a23a-10c35867fbc0 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] allocated 19857152 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0012f000)
[    0.000000] Memory: 3999812k/4964352k available (5523k kernel code, 89012k reserved, 2666k data, 720k init, 3177944k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1800000 - 0xc18b4000   ( 720 kB)
[    0.000000]       .data : 0xc1564dfc - 0xc17ff780   (2666 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1564dfc   (5523 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:744 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2494.080 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4988.16 BogoMIPS (lpj=9976320)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000023] Security Framework initialized
[    0.000034] AppArmor: AppArmor initialized
[    0.000035] Yama: becoming mindful.
[    0.000074] Mount-cache hash table entries: 512
[    0.000180] Initializing cgroup subsys cpuacct
[    0.000185] Initializing cgroup subsys memory
[    0.000191] Initializing cgroup subsys devices
[    0.000193] Initializing cgroup subsys freezer
[    0.000194] Initializing cgroup subsys net_cls
[    0.000196] Initializing cgroup subsys blkio
[    0.000200] Initializing cgroup subsys perf_event
[    0.000225] CPU: Physical Processor ID: 0
[    0.000226] CPU: Processor Core ID: 0
[    0.000230] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.000231] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.000234] mce: CPU supports 7 MCE banks
[    0.000245] CPU0: Thermal monitoring enabled (TM1)
[    0.000251] using mwait in idle threads.
[    0.002227] ACPI: Core revision 20110413
[    0.008216] ftrace: allocating 25655 entries in 51 pages
[    0.016988] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.017390] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.057019] CPU0: Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz stepping 07
[    0.163957] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.163963] ... version:                3
[    0.163964] ... bit width:              48
[    0.163965] ... generic registers:      4
[    0.163966] ... value mask:             0000ffffffffffff
[    0.163967] ... max period:             000000007fffffff
[    0.163968] ... fixed-purpose events:   3
[    0.163970] ... event mask:             000000070000000f
[    0.164274] CPU 1 irqstacks, hard=f74d6000 soft=f74e0000
[    0.164275] Booting Node   0, Processors  #1
[    0.164277] smpboot cpu 1: start_ip = 96000
[    0.174505] Initializing CPU#1
[    0.271981] CPU 2 irqstacks, hard=f74ea000 soft=f74ec000
[    0.271983]  #2
[    0.271984] smpboot cpu 2: start_ip = 96000
[    0.282222] Initializing CPU#2
[    0.379789] CPU 3 irqstacks, hard=f74f6000 soft=f74f8000
[    0.379791]  #3
[    0.379792] smpboot cpu 3: start_ip = 96000
[    0.390019] Initializing CPU#3
[    0.487635] Brought up 4 CPUs
[    0.487637] Total of 4 processors activated (19954.08 BogoMIPS).
[    0.490121] devtmpfs: initialized
[    0.490238] PM: Registering ACPI NVS region at cade7000 (2097152 bytes)
[    0.490282] Dell Latitude E5420 series board detected. Selecting PCI-method for reboots.
[    0.491773] print_constraints: dummy: 
[    0.491799] Time:  1:51:41  Date: 01/25/12
[    0.491829] NET: Registered protocol family 16
[    0.491910] Trying to unpack rootfs image as initramfs...
[    0.491915] EISA bus registered
[    0.491929] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.491931] ACPI: bus type pci registered
[    0.491985] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.491988] PCI: not using MMCONFIG
[    0.492045] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.492051] PCI: PCI BIOS revision 2.10 entry at 0xfce72, last bus=17
[    0.492052] PCI: Using configuration type 1 for base access
[    0.492058] dmi type 0xB1 record - unknown flag
[    0.492751] bio: create slab <bio-0> at 0
[    0.494281] ACPI: EC: Look up EC in DSDT
[    0.498477] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.695320] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.787491] ACPI: SSDT cadd7798 00727 (v01  PmRef  Cpu0Cst 00003001 INTL 20090903)
[    0.787868] ACPI: Dynamic OEM Table Load:
[    0.787871] ACPI: SSDT   (null) 00727 (v01  PmRef  Cpu0Cst 00003001 INTL 20090903)
[    0.819344] ACPI: SSDT cadd8a98 00303 (v01  PmRef    ApIst 00003000 INTL 20090903)
[    0.819759] ACPI: Dynamic OEM Table Load:
[    0.819761] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20090903)
[    0.843177] ACPI: SSDT cadd6d98 00119 (v01  PmRef    ApCst 00003000 INTL 20090903)
[    0.843558] ACPI: Dynamic OEM Table Load:
[    0.843560] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20090903)
[    0.846003] Freeing initrd memory: 19668k freed
[    0.935071] ACPI: Interpreter enabled
[    0.935078] ACPI: (supports S0 S3 S4 S5)
[    0.935098] ACPI: Using IOAPIC for interrupt routing
[    0.935118] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.935493] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in ACPI motherboard resources
[    0.935495] PCI: Using MMCONFIG for extended config space
[    1.474675] ACPI: EC: GPE = 0x10, I/O: command/status = 0x934, data = 0x930
[    1.498351] ACPI: No dock devices found.
[    1.498353] HEST: Table not found.
[    1.498357] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.498654] \_SB_.PCI0:_OSC invalid UUID
[    1.498656] _OSC request data:1 8 1f 
[    1.498659] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    1.499179] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.499182] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.499184] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.499186] pci_root PNP0A08:00: host bridge window [mem 0xcfa00000-0xfeafffff]
[    1.499188] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    1.499199] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    1.499234] pci 0000:00:02.0: [8086:0126] type 0 class 0x000300
[    1.499244] pci 0000:00:02.0: reg 10: [mem 0xe1c00000-0xe1ffffff 64bit]
[    1.499251] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.499255] pci 0000:00:02.0: reg 20: [io  0x7000-0x703f]
[    1.499306] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    1.499331] pci 0000:00:16.0: reg 10: [mem 0xe3d80000-0xe3d8000f 64bit]
[    1.499395] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.499399] pci 0000:00:16.0: PME# disabled
[    1.499433] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    1.499455] pci 0000:00:1a.0: reg 10: [mem 0xe3d50000-0xe3d503ff]
[    1.499530] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.499535] pci 0000:00:1a.0: PME# disabled
[    1.499560] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    1.499577] pci 0000:00:1b.0: reg 10: [mem 0xe3d40000-0xe3d43fff 64bit]
[    1.499634] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.499638] pci 0000:00:1b.0: PME# disabled
[    1.499663] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    1.499764] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.499769] pci 0000:00:1c.0: PME# disabled
[    1.499803] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    1.499905] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.499909] pci 0000:00:1c.1: PME# disabled
[    1.499943] pci 0000:00:1c.2: [8086:1c14] type 1 class 0x000604
[    1.500045] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.500050] pci 0000:00:1c.2: PME# disabled
[    1.500082] pci 0000:00:1c.5: [8086:1c1a] type 1 class 0x000604
[    1.500149] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    1.500154] pci 0000:00:1c.5: PME# disabled
[    1.500179] pci 0000:00:1c.6: [8086:1c1c] type 1 class 0x000604
[    1.500247] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    1.500251] pci 0000:00:1c.6: PME# disabled
[    1.500281] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    1.500302] pci 0000:00:1d.0: reg 10: [mem 0xe3d30000-0xe3d303ff]
[    1.500377] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.500382] pci 0000:00:1d.0: PME# disabled
[    1.500407] pci 0000:00:1f.0: [8086:1c49] type 0 class 0x000601
[    1.500523] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    1.500543] pci 0000:00:1f.2: reg 10: [io  0x70b0-0x70b7]
[    1.500551] pci 0000:00:1f.2: reg 14: [io  0x70a0-0x70a3]
[    1.500560] pci 0000:00:1f.2: reg 18: [io  0x7090-0x7097]
[    1.500568] pci 0000:00:1f.2: reg 1c: [io  0x7080-0x7083]
[    1.500577] pci 0000:00:1f.2: reg 20: [io  0x7060-0x707f]
[    1.500585] pci 0000:00:1f.2: reg 24: [mem 0xe3d20000-0xe3d207ff]
[    1.500619] pci 0000:00:1f.2: PME# supported from D3hot
[    1.500623] pci 0000:00:1f.2: PME# disabled
[    1.500641] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    1.500658] pci 0000:00:1f.3: reg 10: [mem 0xe3d10000-0xe3d100ff 64bit]
[    1.500680] pci 0000:00:1f.3: reg 20: [io  0x7040-0x705f]
[    1.500776] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.500782] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.500788] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.500796] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.501019] pci 0000:02:00.0: [8086:0082] type 0 class 0x000280
[    1.501167] pci 0000:02:00.0: reg 10: [mem 0xe3c00000-0xe3c01fff 64bit]
[    1.501727] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    1.501761] pci 0000:02:00.0: PME# disabled
[    1.501949] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    1.501953] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    1.501958] pci 0000:00:1c.1:   bridge window [mem 0xe3c00000-0xe3cfffff]
[    1.501964] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.502010] pci 0000:00:1c.2: PCI bridge to [bus 03-08]
[    1.502014] pci 0000:00:1c.2:   bridge window [io  0x6000-0x6fff]
[    1.502019] pci 0000:00:1c.2:   bridge window [mem 0xe3100000-0xe3afffff]
[    1.502026] pci 0000:00:1c.2:   bridge window [mem 0xe1100000-0xe1afffff 64bit pref]
[    1.502112] pci 0000:09:00.0: [1217:13f7] type 0 class 0x000c00
[    1.502147] pci 0000:09:00.0: reg 10: [mem 0xe3b30000-0xe3b30fff]
[    1.502353] pci 0000:09:00.0: supports D1 D2
[    1.502355] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.502364] pci 0000:09:00.0: PME# disabled
[    1.502440] pci 0000:09:00.1: [1217:8321] type 0 class 0x000805
[    1.502475] pci 0000:09:00.1: reg 10: [mem 0xe3b20000-0xe3b201ff]
[    1.502679] pci 0000:09:00.1: supports D1 D2
[    1.502680] pci 0000:09:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    1.502689] pci 0000:09:00.1: PME# disabled
[    1.502759] pci 0000:09:00.2: [1217:8331] type 0 class 0x000180
[    1.502793] pci 0000:09:00.2: reg 10: [mem 0xe3b10000-0xe3b103ff]
[    1.502839] pci 0000:09:00.2: reg 18: [mem 0xe3b00000-0xe3b003ff]
[    1.502996] pci 0000:09:00.2: supports D1 D2
[    1.502997] pci 0000:09:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    1.503006] pci 0000:09:00.2: PME# disabled
[    1.503107] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
[    1.503111] pci 0000:00:1c.5:   bridge window [io  0xf000-0x0000] (disabled)
[    1.503116] pci 0000:00:1c.5:   bridge window [mem 0xe3b00000-0xe3bfffff]
[    1.503122] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.503360] pci 0000:0a:00.0: [14e4:1681] type 0 class 0x000200
[    1.503399] pci 0000:0a:00.0: reg 10: [mem 0xe2010000-0xe201ffff 64bit]
[    1.503431] pci 0000:0a:00.0: reg 18: [mem 0xe2000000-0xe200ffff 64bit]
[    1.503565] pci 0000:0a:00.0: PME# supported from D3hot D3cold
[    1.503573] pci 0000:0a:00.0: PME# disabled
[    1.503629] pci 0000:00:1c.6: PCI bridge to [bus 0a-11]
[    1.503634] pci 0000:00:1c.6:   bridge window [io  0x2000-0x5fff]
[    1.503638] pci 0000:00:1c.6:   bridge window [mem 0xe2000000-0xe30fffff]
[    1.503645] pci 0000:00:1c.6:   bridge window [mem 0xe0000000-0xe10fffff 64bit pref]
[    1.503670] pci_bus 0000:00: on NUMA node 0
[    1.503672] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.503825] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.503858] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.503894] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    1.503927] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP07._PRT]
[    1.503967] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.504041] \_SB_.PCI0:_OSC invalid UUID
[    1.504042] _OSC request data:1 1f 1f 
[    1.504046]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.504074] \_SB_.PCI0:_OSC invalid UUID
[    1.504075] _OSC request data:1 0 1d 
[    1.504079]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    1.504080] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.507079] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.507121] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.507160] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    1.507198] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.507236] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.507275] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.507314] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    1.507352] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.507432] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.507440] vgaarb: loaded
[    1.507441] vgaarb: bridge control possible 0000:00:02.0
[    1.507593] SCSI subsystem initialized
[    1.507637] libata version 3.00 loaded.
[    1.507669] usbcore: registered new interface driver usbfs
[    1.507677] usbcore: registered new interface driver hub
[    1.507698] usbcore: registered new device driver usb
[    1.507759] PCI: Using ACPI for IRQ routing
[    1.508322] PCI: pci_cache_line_size set to 64 bytes
[    1.508415] reserve RAM buffer: 000000000009a800 - 000000000009ffff 
[    1.508418] reserve RAM buffer: 00000000caa37000 - 00000000cbffffff 
[    1.508421] reserve RAM buffer: 00000000cadb7000 - 00000000cbffffff 
[    1.508423] reserve RAM buffer: 00000000cb000000 - 00000000cbffffff 
[    1.508425] reserve RAM buffer: 000000012f000000 - 000000012fffffff 
[    1.508496] NetLabel: Initializing
[    1.508497] NetLabel:  domain hash size = 128
[    1.508498] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.508506] NetLabel:  unlabeled traffic allowed by default
[    1.508539] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.508544] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.510560] Switching to clocksource hpet
[    1.514202] Switched to NOHz mode on CPU #0
[    1.514258] Switched to NOHz mode on CPU #2
[    1.514303] Switched to NOHz mode on CPU #3
[    1.514310] Switched to NOHz mode on CPU #1
[    1.515680] AppArmor: AppArmor Filesystem Enabled
[    1.515698] pnp: PnP ACPI init
[    1.515708] ACPI: bus type pnp registered
[    1.515998] pnp 00:00: [bus 00-3e]
[    1.516000] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.516002] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.516004] pnp 00:00: [io  0x0d00-0xffff window]
[    1.516006] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.516007] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.516009] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.516011] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.516012] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.516014] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.516016] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.516017] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.516019] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.516021] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.516023] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.516024] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.516026] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.516028] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.516029] pnp 00:00: [mem 0xcfa00000-0xfeafffff window]
[    1.516031] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    1.516084] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.516096] pnp 00:01: [io  0x0000-0x001f]
[    1.516098] pnp 00:01: [io  0x0081-0x0091]
[    1.516099] pnp 00:01: [io  0x0093-0x009f]
[    1.516101] pnp 00:01: [io  0x00c0-0x00df]
[    1.516103] pnp 00:01: [dma 4]
[    1.516120] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.516126] pnp 00:02: [mem 0xff000000-0xffffffff]
[    1.516143] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.516202] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.516236] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    1.516238] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    1.516247] pnp 00:04: [io  0x00f0]
[    1.516255] pnp 00:04: [irq 13]
[    1.516273] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.516282] pnp 00:05: [io  0x002e-0x002f]
[    1.516283] pnp 00:05: [io  0x004e-0x004f]
[    1.516285] pnp 00:05: [io  0x0061]
[    1.516286] pnp 00:05: [io  0x0063]
[    1.516287] pnp 00:05: [io  0x0065]
[    1.516289] pnp 00:05: [io  0x0067]
[    1.516290] pnp 00:05: [io  0x0070]
[    1.516291] pnp 00:05: [io  0x0080]
[    1.516293] pnp 00:05: [io  0x0092]
[    1.516294] pnp 00:05: [io  0x00b2-0x00b3]
[    1.516296] pnp 00:05: [io  0x0680-0x069f]
[    1.516297] pnp 00:05: [io  0x1000-0x100f]
[    1.516298] pnp 00:05: [io  0xffff]
[    1.516300] pnp 00:05: [io  0xffff]
[    1.516301] pnp 00:05: [io  0x0400-0x047f]
[    1.516303] pnp 00:05: [io  0x0500-0x057f]
[    1.516304] pnp 00:05: [io  0x164e-0x164f]
[    1.516336] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.516338] system 00:05: [io  0x1000-0x100f] has been reserved
[    1.516340] system 00:05: [io  0xffff] has been reserved
[    1.516342] system 00:05: [io  0xffff] has been reserved
[    1.516344] system 00:05: [io  0x0400-0x047f] has been reserved
[    1.516346] system 00:05: [io  0x0500-0x057f] has been reserved
[    1.516348] system 00:05: [io  0x164e-0x164f] has been reserved
[    1.516350] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.516357] pnp 00:06: [io  0x0070-0x0077]
[    1.516362] pnp 00:06: [irq 8]
[    1.516380] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.516388] pnp 00:07: [io  0x0060]
[    1.516390] pnp 00:07: [io  0x0064]
[    1.516394] pnp 00:07: [irq 1]
[    1.516413] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.522798] pnp 00:08: Plug and Play ACPI device, IDs PNP0401 (disabled)
[    1.522810] pnp 00:09: [irq 12]
[    1.522829] pnp 00:09: Plug and Play ACPI device, IDs DLL049b PNP0f13 (active)
[    1.522960] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    1.522961] pnp 00:0a: [mem 0xfed10000-0xfed17fff]
[    1.522963] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
[    1.522965] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
[    1.522966] pnp 00:0a: [mem 0xf8000000-0xfbffffff]
[    1.522968] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    1.522969] pnp 00:0a: [mem 0xfed90000-0xfed93fff]
[    1.522971] pnp 00:0a: [mem 0xfed45000-0xfed8ffff]
[    1.522972] pnp 00:0a: [mem 0xff000000-0xffffffff]
[    1.522974] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    1.522976] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
[    1.522978] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
[    1.523020] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.523022] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.523024] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.523026] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.523028] system 00:0a: [mem 0xf8000000-0xfbffffff] has been reserved
[    1.523030] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.523032] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.523034] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.523037] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    1.523039] system 00:0a: [mem 0xfee00000-0xfeefffff] has been reserved
[    1.523041] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.523101] pnp 00:0b: [irq 23]
[    1.523128] pnp 00:0b: Plug and Play ACPI device, IDs SMO8800 (active)
[    1.546654] pnp 00:0c: [mem 0x20000000-0x201fffff]
[    1.546657] pnp 00:0c: [mem 0x40000000-0x401fffff]
[    1.550587] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
[    1.550590] system 00:0c: [mem 0x40000000-0x401fffff] has been reserved
[    1.550592] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.550601] pnp: PnP ACPI: found 13 devices
[    1.550602] ACPI: ACPI bus type pnp unregistered
[    1.550605] PnPBIOS: Disabled by ACPI PNP
[    1.586107] PCI: max bus depth: 1 pci_try_num: 2
[    1.586151] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.586153] pci 0000:00:1c.0:   bridge window [io  disabled]
[    1.586158] pci 0000:00:1c.0:   bridge window [mem disabled]
[    1.586163] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    1.586169] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    1.586170] pci 0000:00:1c.1:   bridge window [io  disabled]
[    1.586176] pci 0000:00:1c.1:   bridge window [mem 0xe3c00000-0xe3cfffff]
[    1.586180] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    1.586187] pci 0000:00:1c.2: PCI bridge to [bus 03-08]
[    1.586190] pci 0000:00:1c.2:   bridge window [io  0x6000-0x6fff]
[    1.586195] pci 0000:00:1c.2:   bridge window [mem 0xe3100000-0xe3afffff]
[    1.586200] pci 0000:00:1c.2:   bridge window [mem 0xe1100000-0xe1afffff 64bit pref]
[    1.586207] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
[    1.586208] pci 0000:00:1c.5:   bridge window [io  disabled]
[    1.586214] pci 0000:00:1c.5:   bridge window [mem 0xe3b00000-0xe3bfffff]
[    1.586218] pci 0000:00:1c.5:   bridge window [mem pref disabled]
[    1.586224] pci 0000:00:1c.6: PCI bridge to [bus 0a-11]
[    1.586227] pci 0000:00:1c.6:   bridge window [io  0x2000-0x5fff]
[    1.586233] pci 0000:00:1c.6:   bridge window [mem 0xe2000000-0xe30fffff]
[    1.586237] pci 0000:00:1c.6:   bridge window [mem 0xe0000000-0xe10fffff 64bit pref]
[    1.586256] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.586261] pci 0000:00:1c.0: setting latency timer to 64
[    1.586272] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.586276] pci 0000:00:1c.1: setting latency timer to 64
[    1.586285] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.586290] pci 0000:00:1c.2: setting latency timer to 64
[    1.586297] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.586301] pci 0000:00:1c.5: setting latency timer to 64
[    1.586308] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.586312] pci 0000:00:1c.6: setting latency timer to 64
[    1.586316] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.586318] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.586320] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.586322] pci_bus 0000:00: resource 7 [mem 0xcfa00000-0xfeafffff]
[    1.586324] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
[    1.586326] pci_bus 0000:02: resource 1 [mem 0xe3c00000-0xe3cfffff]
[    1.586328] pci_bus 0000:03: resource 0 [io  0x6000-0x6fff]
[    1.586329] pci_bus 0000:03: resource 1 [mem 0xe3100000-0xe3afffff]
[    1.586331] pci_bus 0000:03: resource 2 [mem 0xe1100000-0xe1afffff 64bit pref]
[    1.586333] pci_bus 0000:09: resource 1 [mem 0xe3b00000-0xe3bfffff]
[    1.586335] pci_bus 0000:0a: resource 0 [io  0x2000-0x5fff]
[    1.586337] pci_bus 0000:0a: resource 1 [mem 0xe2000000-0xe30fffff]
[    1.586339] pci_bus 0000:0a: resource 2 [mem 0xe0000000-0xe10fffff 64bit pref]
[    1.586364] NET: Registered protocol family 2
[    1.586414] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.586546] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.586767] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.586866] TCP: Hash tables configured (established 131072 bind 65536)
[    1.586868] TCP reno registered
[    1.586870] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    1.586875] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    1.586941] NET: Registered protocol family 1
[    1.586950] pci 0000:00:02.0: Boot video device
[    1.587027] PCI: CLS 64 bytes, default 64
[    1.587030] DMAR: Host address width 36
[    1.587031] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    1.587037] IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
[    1.587038] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    1.587043] IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
[    1.587045] DMAR: RMRR base: 0x000000cadc6000 end: 0x000000cadd5fff
[    1.587047] DMAR: RMRR base: 0x000000cb800000 end: 0x000000cf9fffff
[    1.587048] DMAR: No ATSR found
[    1.587055] Simple Boot Flag at 0xf3 set to 0x1
[    1.587414] audit: initializing netlink socket (disabled)
[    1.587421] type=2000 audit(1327456302.432:1): initialized
[    1.609320] highmem bounce pool size: 64 pages
[    1.609324] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.617718] VFS: Disk quotas dquot_6.5.2
[    1.617770] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.618264] fuse init (API version 7.16)
[    1.618330] msgmni has been set to 1643
[    1.618682] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.618710] io scheduler noop registered
[    1.618712] io scheduler deadline registered
[    1.618722] io scheduler cfq registered (default)
[    1.619024] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.619041] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.619079] intel_idle: MWAIT substates: 0x21120
[    1.619081] intel_idle: v0.4 model 0x2A
[    1.619082] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.619419] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.619730] ACPI: AC Adapter [AC] (off-line)
[    1.619872] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.620331] ACPI: Lid Switch [LID]
[    1.620391] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.620395] ACPI: Power Button [PBTN]
[    1.620423] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.620426] ACPI: Sleep Button [SBTN]
[    1.620453] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.620455] ACPI: Power Button [PWRF]
[    1.620476] ACPI: acpi_idle yielding to intel_idle
[    1.806217] thermal LNXTHERM:00: registered as thermal_zone0
[    1.806220] ACPI: Thermal Zone [THM] (25 C)
[    1.806239] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.806250] ERST: Table is not found!
[    1.806304] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.806308] isapnp: Scanning for PnP cards...
[    1.815985] ACPI: Battery Slot [BAT0] (battery present)
[    2.159823] isapnp: No Plug & Play device found
[    2.209910] Linux agpgart interface v0.103
[    2.209994] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    2.210060] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    2.210957] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    2.211061] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    2.211955] brd: module loaded
[    2.212365] loop: module loaded
[    2.212714] Fixed MDIO Bus: probed
[    2.212731] PPP generic driver version 2.4.2
[    2.212755] tun: Universal TUN/TAP device driver, 1.6
[    2.212756] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.212811] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.212828] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.212842] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.212846] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.212869] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.212892] ehci_hcd 0000:00:1a.0: debug port 2
[    2.216765] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    2.216780] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xe3d50000
[    2.229583] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.229719] hub 1-0:1.0: USB hub found
[    2.229722] hub 1-0:1.0: 2 ports detected
[    2.229772] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.229782] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.229785] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.229808] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.229828] ehci_hcd 0000:00:1d.0: debug port 2
[    2.233710] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    2.233723] ehci_hcd 0000:00:1d.0: irq 17, io mem 0xe3d30000
[    2.249555] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.249680] hub 2-0:1.0: USB hub found
[    2.249683] hub 2-0:1.0: 2 ports detected
[    2.249726] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.249735] uhci_hcd: USB Universal Host Controller Interface driver
[    2.249789] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.250004] i8042: Warning: Keylock active
[    2.251233] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.251238] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.251311] mousedev: PS/2 mouse device common for all mice
[    2.251433] rtc_cmos 00:06: RTC can wake from S4
[    2.251530] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.251566] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    2.251633] device-mapper: uevent: version 1.0.3
[    2.251700] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    2.251721] EISA: Probing bus 0 at eisa.0
[    2.251722] EISA: Cannot allocate resource for mainboard
[    2.251724] Cannot allocate resource for EISA slot 1
[    2.251725] Cannot allocate resource for EISA slot 2
[    2.251727] Cannot allocate resource for EISA slot 3
[    2.251728] Cannot allocate resource for EISA slot 4
[    2.251729] Cannot allocate resource for EISA slot 5
[    2.251731] Cannot allocate resource for EISA slot 6
[    2.251732] Cannot allocate resource for EISA slot 7
[    2.251733] Cannot allocate resource for EISA slot 8
[    2.251735] EISA: Detected 0 cards.
[    2.251742] cpufreq-nforce2: No nForce2 chipset.
[    2.251838] cpuidle: using governor ladder
[    2.252021] cpuidle: using governor menu
[    2.252023] EFI Variables Facility v0.08 2004-May-17
[    2.252206] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.252341] TCP cubic registered
[    2.252438] NET: Registered protocol family 10
[    2.252802] NET: Registered protocol family 17
[    2.252811] Registering the dns_resolver key type
[    2.252823] Using IPI No-Shortcut mode
[    2.252875] PM: Hibernation image not present or could not be loaded.
[    2.252886] registered taskstats version 1
[    2.261986]   Magic number: 12:289:863
[    2.262063] rtc_cmos 00:06: setting system clock to 2012-01-25 01:51:43 UTC (1327456303)
[    2.262851] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.262853] EDD information not available.
[    2.263079] Freeing unused kernel memory: 720k freed
[    2.263276] Write protecting the kernel text: 5524k
[    2.263367] Write protecting the kernel read-only data: 2240k
[    2.263370] NX-protecting the kernel data: 4716k
[    2.284994] zram: module is from the staging directory, the quality is unknown, you have been warned.
[    2.285275] zram: num_devices not specified. Using default: 1
[    2.285278] zram: Creating 1 devices ...
[    2.289514] udevd[96]: starting version 173
[    2.327372] [drm] Initialized drm 1.1.0 20060810
[    2.328463] wmi: Mapper loaded
[    2.330340] firewire_ohci 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.330354] firewire_ohci 0000:09:00.0: setting latency timer to 64
[    2.333848] sdhci: Secure Digital Host Controller Interface driver
[    2.333853] sdhci: Copyright(c) Pierre Ossman
[    2.346135] Adding 2010096k swap on /dev/zram0.  Priority:100 extents:1 across:2010096k SS
[    2.351018] tg3.c:v3.119 (May 18, 2011)
[    2.351041] tg3 0000:0a:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.351057] tg3 0000:0a:00.0: setting latency timer to 64
[    2.353469] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.353478] i915 0000:00:02.0: setting latency timer to 64
[    2.385502] firewire_ohci: Register access failure - please notify linux1394-devel@lists.sf.net
[    2.385536] firewire_ohci: Added fw-ohci device 0000:09:00.0, OHCI v1.10, 8 IR + 8 IT contexts, quirks 0x10
[    2.385778] sdhci-pci 0000:09:00.1: SDHCI controller found [1217:8321] (rev 5)
[    2.385802] sdhci-pci 0000:09:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.385846] sdhci-pci 0000:09:00.1: Invalid iomem size. You may experience problems.
[    2.385890] sdhci-pci 0000:09:00.1: setting latency timer to 64
[    2.385920] mmc0: no vmmc regulator found
[    2.385966] Registered led device: mmc0::
[    2.386020] mmc0: SDHCI controller on PCI [0000:09:00.1] using DMA
[    2.399109] i915 0000:00:02.0: irq 40 for MSI/MSI-X
[    2.399118] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.399122] [drm] Driver supports precise vblank timestamp query.
[    2.399179] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.478244] tg3 0000:0a:00.0: eth0: Tigon3 [partno(BCM95761) rev 5761100] (PCI Express) MAC address d0:67:e5:3f:cb:5e
[    2.478250] tg3 0000:0a:00.0: eth0: attached PHY is 5761 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    2.478254] tg3 0000:0a:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.478258] tg3 0000:0a:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.541259] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    2.585123] Refined TSC clocksource calibration: 2494.332 MHz.
[    2.585130] Switching to clocksource tsc
[    2.673698] hub 1-1:1.0: USB hub found
[    2.673896] hub 1-1:1.0: 6 ports detected
[    2.723748] fbcon: inteldrmfb (fb0) is primary device
[    2.723817] Console: switching to colour frame buffer device 170x48
[    2.723868] fb0: inteldrmfb frame buffer device
[    2.723871] drm: registered panic notifier
[    2.784906] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    2.881589] acpi device:36: registered as cooling_device4
[    2.892835] firewire_core: created device fw0: GUID 02879701364fc000, S400
[    2.917383] hub 2-1:1.0: USB hub found
[    2.917560] hub 2-1:1.0: 6 ports detected
[    2.948879] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    2.948927] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    2.968732] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.968913] ahci 0000:00:1f.2: version 3.0
[    2.988789] usb 1-1.3: new full speed USB device number 3 using ehci_hcd
[    2.992682] ahci 0000:00:1f.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.992761] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    2.992808] ahci: SSS flag set, parallel bus scan disabled
[    3.008642] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3b impl SATA mode
[    3.008650] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    3.008660] ahci 0000:00:1f.2: setting latency timer to 64
[    3.041170] scsi0 : ahci
[    3.041303] scsi1 : ahci
[    3.041408] scsi2 : ahci
[    3.041508] scsi3 : ahci
[    3.041598] scsi4 : ahci
[    3.041710] scsi5 : ahci
[    3.045665] ata1: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20100 irq 41
[    3.045670] ata2: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20180 irq 41
[    3.045673] ata3: DUMMY
[    3.045677] ata4: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20280 irq 41
[    3.045681] ata5: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20300 irq 41
[    3.045685] ata6: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20380 irq 41
[    3.152556] usb 1-1.4: new high speed USB device number 4 using ehci_hcd
[    3.324620] usb 2-1.6: new full speed USB device number 3 using ehci_hcd
[    3.364148] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.386973] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    3.387275] ata1.00: ATA-8: ST9500423AS, 0002DEM1, max UDMA/133
[    3.387285] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.536472] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    3.536757] ata1.00: configured for UDMA/133
[    3.544080] scsi 0:0:0:0: Direct-Access     ATA      ST9500423AS      0002 PQ: 0 ANSI: 5
[    3.544278] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.544316] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.544321] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    3.544426] sd 0:0:0:0: [sda] Write Protect is off
[    3.544431] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.544479] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.586032]  sda: sda1 sda2 sda3 sda4
[    3.586415] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.863499] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.866899] ata2.00: ATAPI: HL-DT-ST DVD+-RW GT50N, A101, max UDMA/133
[    3.869817] ata2.00: configured for UDMA/133
[    3.874354] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GT50N    A101 PQ: 0 ANSI: 5
[    3.881132] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.881151] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.881254] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.881309] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.199036] ata4: SATA link down (SStatus 0 SControl 300)
[    4.518648] ata5: SATA link down (SStatus 0 SControl 300)
[    4.838242] ata6: SATA link down (SStatus 0 SControl 300)
[    6.735320] Btrfs loaded
[    6.740729] xor: automatically using best checksumming function: pIII_sse
[    6.759695]    pIII_sse  :  8969.000 MB/sec
[    6.759700] xor: using function: pIII_sse (8969.000 MB/sec)
[    6.760277] device-mapper: dm-raid45: initialized v0.2594b
[    7.049495] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   16.709123] udevd[421]: starting version 173
[   16.756991] Adding 7812092k swap on /dev/sda4.  Priority:-1 extents:1 across:7812092k 
[   16.759912] lp: driver loaded but no devices found
[   16.763092] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   16.763357] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.763367] mei 0000:00:16.0: setting latency timer to 64
[   16.767087] cfg80211: Calling CRDA to update world regulatory domain
[   16.777573] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   16.777577] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   16.777628] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.777638] iwlagn 0000:02:00.0: setting latency timer to 64
[   16.777668] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   16.783195] type=1400 audit(1327449118.036:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=579 comm="apparmor_parser"
[   16.783610] type=1400 audit(1327449118.036:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=579 comm="apparmor_parser"
[   16.783873] type=1400 audit(1327449118.036:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=579 comm="apparmor_parser"
[   16.794829] iwlagn 0000:02:00.0: device EEPROM VER=0x715, CALIB=0x6
[   16.794832] iwlagn 0000:02:00.0: Device SKU: 0Xb
[   16.794834] iwlagn 0000:02:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   16.795163] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   16.795257] iwlagn 0000:02:00.0: irq 42 for MSI/MSI-X
[   16.810238] Linux video capture interface: v2.00
[   16.810719] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_FHD (05ca:181e)
[   16.814890] input: Laptop_Integrated_Webcam_FHD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input6
[   16.814958] usbcore: registered new interface driver uvcvideo
[   16.814960] USB Video Class driver (v1.1.0)
[   16.819993] parport_pc 00:08: [io  0x0378-0x037b]
[   16.820008] parport_pc 00:08: [io  0x0278-0x027b]
[   16.820019] parport_pc 00:08: [io  0x03bc-0x03bf]
[   16.820029] parport_pc 00:08: [io  0x0378-0x037b]
[   16.820092] parport_pc 00:08: [irq 7]
[   16.824742] Bluetooth: Core ver 2.16
[   16.824763] NET: Registered protocol family 31
[   16.824765] Bluetooth: HCI device and connection manager initialized
[   16.824767] Bluetooth: HCI socket layer initialized
[   16.824768] Bluetooth: L2CAP socket layer initialized
[   16.827748] Bluetooth: SCO socket layer initialized
[   16.828065] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   16.829047] usbcore: registered new interface driver btusb
[   16.870784] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.870838] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   16.870864] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.872586] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   16.937050] cfg80211: World regulatory domain updated:
[   16.937055] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.937058] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.937062] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.937064] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.937067] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.937069] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.937766] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   16.939034] ppdev: user-space parallel port driver
[   17.050519] parport_pc 00:08: activated
[   17.050523] parport_pc 00:08: reported by Plug and Play ACPI
[   17.050588] parport_pc 00:08: disabled
[   17.115732] iwlagn 0000:02:00.0: loaded firmware version 17.168.5.3 build 42301
[   17.115869] Registered led device: phy0-led
[   17.115895] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   17.118015] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   17.156928] alps.c: Enabled hardware quirk, falling back to psmouse-core
[   17.169857] input: ImPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   17.353421] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,user_xattr
[   17.438933] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   17.439050] HDMI status: Pin=6 Presence_Detect=0 ELD_Valid=0
[   17.439175] HDMI status: Pin=7 Presence_Detect=0 ELD_Valid=0
[   17.439406] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   17.439491] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   17.439583] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   17.439662] input: HDA Intel PCH Mic at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   17.439723] input: HDA Intel PCH Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   17.439813] input: HDA Intel PCH Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   17.439872] input: HDA Intel PCH HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   18.321193] type=1400 audit(1327449119.576:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=982 comm="apparmor_parser"
[   18.321441] type=1400 audit(1327449119.576:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=983 comm="apparmor_parser"
[   18.321833] type=1400 audit(1327449119.576:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=983 comm="apparmor_parser"
[   18.322084] type=1400 audit(1327449119.576:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=983 comm="apparmor_parser"
[   18.322386] type=1400 audit(1327449119.576:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=986 comm="apparmor_parser"
[   18.322741] type=1400 audit(1327449119.576:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=986 comm="apparmor_parser"
[   18.323773] type=1400 audit(1327449119.576:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=987 comm="apparmor_parser"
[   18.502056] init: failsafe main process (925) killed by TERM signal
[   18.502962] init: apport pre-start process (1021) terminated with status 1
[   18.513111] init: apport post-stop process (1071) terminated with status 1
[   18.683658] Bluetooth: RFCOMM TTY layer initialized
[   18.683662] Bluetooth: RFCOMM socket layer initialized
[   18.683664] Bluetooth: RFCOMM ver 1.11
[   18.687179] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.687182] Bluetooth: BNEP filters: protocol multicast
[   18.845069] init: anacron main process (1096) killed by TERM signal
[   18.955312] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.957305] tg3 0000:0a:00.0: irq 44 for MSI/MSI-X
[   19.033334] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.433426] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,user_xattr,commit=600
[   22.799911] init: plymouth-stop pre-start process (1489) terminated with status 1
[   26.535859] wlan0: authenticate with 00:21:63:40:ac:88 (try 1)
[   26.538717] wlan0: authenticated
[   26.539501] wlan0: associate with 00:21:63:40:ac:88 (try 1)
[   26.541947] wlan0: RX AssocResp from 00:21:63:40:ac:88 (capab=0x401 status=0 aid=2)
[   26.541956] wlan0: associated
[   26.544921] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   37.208293] wlan0: no IPv6 routers present
[  142.017482] EXT3-fs: barriers not enabled
[  142.024188] kjournald starting.  Commit interval 5 seconds
[  142.024337] EXT3-fs (dm-0): using internal journal
[  142.024414] EXT3-fs (dm-0): mounted filesystem with ordered data mode
[ 2023.889072] wlan0: deauthenticating from 00:21:63:40:ac:88 by local choice (reason=3)
[ 2023.976284] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2023.976291] cfg80211: Restoring regulatory settings
[ 2023.976294] cfg80211: Calling CRDA to update world regulatory domain
[ 2023.981291] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 2023.981296] cfg80211: World regulatory domain updated:
[ 2023.981297] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2023.981300] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2023.981302] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2023.981304] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2023.981306] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2023.981308] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2024.074415] tg3 0000:0a:00.0: PME# enabled
[ 2024.103530] tg3 0000:0a:00.0: wake-up capability enabled by ACPI
[ 2025.084101] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[ 2026.327917] init: anacron main process (2379) killed by TERM signal
[ 2026.581457] PM: Syncing filesystems ... done.
[ 2026.584276] PM: Preparing system for mem sleep
[ 2027.215567] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 2027.231454] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 2027.247442] PM: Entering mem sleep
[ 2027.247540] Suspending console(s) (use no_console_suspend to debug)
[ 2027.247748] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 2027.248101] sd 0:0:0:0: [sda] Stopping disk
[ 2027.262964] ACPI handle has no context!
[ 2027.262976] sdhci-pci 0000:09:00.1: PCI INT B disabled
[ 2027.262984] ACPI handle has no context!
[ 2027.295351] ehci_hcd 0000:00:1d.0: PCI INT A disabled
[ 2027.295361] ehci_hcd 0000:00:1a.0: PCI INT A disabled
[ 2027.367788] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 2027.383224] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 120.310 msecs
[ 2027.623615] PM: suspend of drv:sd dev:0:0:0:0 complete after 376.352 msecs
[ 2027.623650] PM: suspend of drv:scsi dev:target0:0:0 complete after 376.367 msecs
[ 2027.623675] PM: suspend of drv:scsi dev:host0 complete after 376.047 msecs
[ 2027.646880] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 384.351 msecs
[ 2027.647017] PM: suspend of drv: dev:pci0000:00 complete after 384.300 msecs
[ 2027.647026] PM: suspend of devices complete after 399.841 msecs
[ 2027.647028] PM: suspend devices took 0.400 seconds
[ 2027.710868] PM: late suspend of devices complete after 63.919 msecs
[ 2027.711038] ACPI: Preparing to enter system sleep state S3
[ 2027.738938] PM: Saving platform NVS memory
[ 2027.741301] Disabling non-boot CPUs ...
[ 2027.743036] CPU 1 is now offline
[ 2027.846622] CPU 2 is now offline
[ 2027.847415] Broke affinity for irq 17
[ 2027.950487] CPU 3 is now offline
[ 2027.950759] Extended CMOS year: 2000
[ 2027.951015] ACPI: Low-level resume complete
[ 2027.951054] PM: Restoring platform NVS memory
[ 2027.951754] Extended CMOS year: 2000
[ 2027.951790] Enabling non-boot CPUs ...
[ 2027.951861] Booting Node 0 Processor 1 APIC 0x2
[ 2027.951862] smpboot cpu 1: start_ip = 96000
[ 2027.962071] Initializing CPU#1
[ 2028.059781] CPU1 is up
[ 2028.060090] Booting Node 0 Processor 2 APIC 0x1
[ 2028.060092] smpboot cpu 2: start_ip = 96000
[ 2028.063296] Switched to NOHz mode on CPU #1
[ 2028.070192] Initializing CPU#2
[ 2028.167777] CPU2 is up
[ 2028.168002] Booting Node 0 Processor 3 APIC 0x3
[ 2028.168004] smpboot cpu 3: start_ip = 96000
[ 2028.171156] Switched to NOHz mode on CPU #2
[ 2028.178203] Initializing CPU#3
[ 2028.275826] CPU3 is up
[ 2028.278537] ACPI: Waking up from system sleep state S3
[ 2028.279034] Switched to NOHz mode on CPU #3
[ 2028.586907] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[ 2028.586927] mei 0000:00:16.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 2028.586943] mei 0000:00:16.0: restoring config space at offset 0x4 (was 0xfedb0004, writing 0xe3d80004)
[ 2028.586968] ehci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 2028.586983] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x4 (was 0x0, writing 0xe3d50000)
[ 2028.586989] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[ 2028.587015] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[ 2028.587028] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0x4, writing 0xe3d40004)
[ 2028.587032] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2028.587037] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
[ 2028.587071] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 2028.587088] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0xf0, writing 0x200000f0)
[ 2028.587098] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 2028.587105] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 2028.587153] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 2028.587170] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0xf0, writing 0x200000f0)
[ 2028.587180] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 2028.587187] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 2028.587235] pcieport 0000:00:1c.2: restoring config space at offset 0xf (was 0x300, writing 0x303)
[ 2028.587258] pcieport 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 2028.587264] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 2028.587306] pcieport 0000:00:1c.5: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 2028.587321] pcieport 0000:00:1c.5: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 2028.587325] pcieport 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 2028.587355] pcieport 0000:00:1c.6: restoring config space at offset 0xf (was 0x300, writing 0x303)
[ 2028.587369] pcieport 0000:00:1c.6: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 2028.587375] pcieport 0000:00:1c.6: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 2028.587402] ehci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 2028.587417] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x4 (was 0x0, writing 0xe3d30000)
[ 2028.587423] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[ 2028.587491] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 2028.587526] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800003)
[ 2028.587615] iwlagn 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 2028.587653] iwlagn 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xe3c00004)
[ 2028.587661] iwlagn 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2028.587672] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 2028.587761] firewire_ohci 0000:09:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 2028.587786] firewire_ohci 0000:09:00.0: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[ 2028.587793] firewire_ohci 0000:09:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 2028.587836] sdhci-pci 0000:09:00.1: restoring config space at offset 0xf (was 0x200, writing 0x203)
[ 2028.587860] sdhci-pci 0000:09:00.1: restoring config space at offset 0x4 (was 0x0, writing 0xe3b20000)
[ 2028.587865] sdhci-pci 0000:09:00.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[ 2028.587873] sdhci-pci 0000:09:00.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 2028.587916] pci 0000:09:00.2: restoring config space at offset 0xf (was 0x300, writing 0x30b)
[ 2028.587936] pci 0000:09:00.2: restoring config space at offset 0x6 (was 0x0, writing 0xe3b00000)
[ 2028.587944] pci 0000:09:00.2: restoring config space at offset 0x4 (was 0x0, writing 0xe3b10000)
[ 2028.587949] pci 0000:09:00.2: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[ 2028.587957] pci 0000:09:00.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 2028.588208] tg3 0000:0a:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2028.588216] tg3 0000:0a:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 2028.588323] PM: early resume of devices complete after 1.457 msecs
[ 2028.588399] i915 0000:00:02.0: setting latency timer to 64
[ 2028.588430] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2028.588436] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[ 2028.588450] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 2028.588456] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 2028.588480] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2028.588483] ahci 0000:00:1f.2: setting latency timer to 64
[ 2028.588490] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[ 2028.588522] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[ 2028.588526] sdhci-pci 0000:09:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[ 2028.588534] sdhci-pci 0000:09:00.1: setting latency timer to 64
[ 2028.602700] sd 0:0:0:0: [sda] Starting disk
[ 2028.642706] firewire_core: skipped bus generations, destroying all nodes
[ 2028.734873] PM: resume of drv:button dev:PNP0C0D:00 complete after 146.475 msecs
[ 2028.766499] PM: resume of drv:hub dev:2-1:1.0 complete after 178.074 msecs
[ 2028.766516] PM: resume of drv:hub dev:1-1:1.0 complete after 178.122 msecs
[ 2028.766519] PM: resume of drv: dev:ep_81 complete after 178.087 msecs
[ 2028.766522] PM: resume of drv: dev:ep_00 complete after 178.117 msecs
[ 2028.766524] PM: resume of drv: dev:ep_81 complete after 178.121 msecs
[ 2028.766527] PM: resume of drv: dev:ep_00 complete after 178.080 msecs
[ 2028.798579] tg3 0000:0a:00.0: wake-up capability disabled by ACPI
[ 2028.798590] tg3 0000:0a:00.0: PME# disabled
[ 2028.798593] PM: resume of drv:tg3 dev:0000:0a:00.0 complete after 210.340 msecs
[ 2028.838603] usb 1-1.3: reset full speed USB device number 3 using ehci_hcd
[ 2028.887114] Extended CMOS year: 2000
[ 2028.930235] ata5: SATA link down (SStatus 0 SControl 300)
[ 2028.931102] PM: resume of drv:usb dev:1-1.3:1.0 complete after 342.637 msecs
[ 2028.931118] PM: resume of drv: dev:ep_00 complete after 342.512 msecs
[ 2028.931127] PM: resume of drv: dev:ep_81 complete after 342.643 msecs
[ 2028.931137] PM: resume of drv: dev:ep_02 complete after 342.552 msecs
[ 2028.938219] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2028.943550] ata2.00: configured for UDMA/133
[ 2028.946220] ata4: SATA link down (SStatus 0 SControl 300)
[ 2028.954206] ata6: SATA link down (SStatus 0 SControl 300)
[ 2029.002250] usb 2-1.6: reset full speed USB device number 3 using ehci_hcd
[ 2029.096367] btusb 2-1.6:1.0: no reset_resume for driver btusb?
[ 2029.096374] btusb 2-1.6:1.1: no reset_resume for driver btusb?
[ 2029.142048] firewire_core: rediscovered device fw0
[ 2029.166014] usb 1-1.4: reset high speed USB device number 4 using ehci_hcd
[ 2029.304299] PM: resume of drv:i915 dev:0000:00:02.0 complete after 716.831 msecs
[ 2029.345900] PM: resume of drv:usb dev:2-1.6:1.0 complete after 757.365 msecs
[ 2029.345903] PM: resume of drv:usb dev:2-1.6:1.2 complete after 757.276 msecs
[ 2029.345908] PM: resume of drv:usb dev:2-1.6:1.1 complete after 757.323 msecs
[ 2029.345912] PM: resume of drv: dev:ep_81 complete after 757.365 msecs
[ 2029.345915] PM: resume of drv: dev:ep_83 complete after 757.318 msecs
[ 2029.345917] PM: resume of drv: dev:ep_82 complete after 757.356 msecs
[ 2029.345918] PM: resume of drv: dev:ep_03 complete after 757.308 msecs
[ 2029.345920] PM: resume of drv: dev:ep_02 complete after 757.349 msecs
[ 2029.345922] PM: resume of drv:usb dev:2-1.6:1.3 complete after 757.261 msecs
[ 2029.345924] PM: resume of drv: dev:ep_84 complete after 757.288 msecs
[ 2029.345930] PM: resume of drv: dev:ep_04 complete after 757.282 msecs
[ 2029.345932] PM: resume of drv: dev:ep_00 complete after 757.257 msecs
[ 2029.572163] PM: resume of drv:uvcvideo dev:1-1.4:1.1 complete after 984.209 msecs
[ 2029.572175] PM: resume of drv: dev:ep_00 complete after 983.940 msecs
[ 2029.572210] PM: resume of drv:uvcvideo dev:1-1.4:1.0 complete after 984.318 msecs
[ 2029.572270] PM: resume of drv: dev:ep_81 complete after 984.336 msecs
[ 2030.432281] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2030.699464] ata1.00: ACPI cmd ef/5a:00:00:00:00:a0 (SET FEATURES) succeeded
[ 2030.959995] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[ 2030.960269] ata1.00: configured for UDMA/133
[ 2031.001541] PM: resume of drv:sd dev:0:0:0:0 complete after 2414.978 msecs
[ 2031.001598] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 1699.439 msecs
[ 2031.001601] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2415.017 msecs
[ 2031.003236] PM: resume of devices complete after 2418.017 msecs
[ 2031.003454] PM: resume devices took 2.416 seconds
[ 2031.003479] PM: Finishing wakeup.
[ 2031.003480] Restarting tasks ... done.
[ 2031.021431] video LNXVIDEO:00: Restoring backlight state
[ 2031.155701] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[ 2032.335542] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[ 2032.555800] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2032.557599] tg3 0000:0a:00.0: irq 44 for MSI/MSI-X
[ 2032.633945] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2040.045117] wlan0: authenticate with 00:21:63:40:ac:88 (try 1)
[ 2040.047937] wlan0: authenticated
[ 2040.048448] wlan0: associate with 00:21:63:40:ac:88 (try 1)
[ 2040.050897] wlan0: RX AssocResp from 00:21:63:40:ac:88 (capab=0x401 status=0 aid=2)
[ 2040.050906] wlan0: associated
[ 2040.053399] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2050.238613] wlan0: no IPv6 routers present

```

uptime:
```

 04:18:31 up  2:26,  1 user,  load average: 0.00, 0.03, 0.05

```

ps ax -o pid,comm,pcpu | grep "migration"
```

    6 migration/0     22.7
 2645 migration/1      0.0
 2648 migration/2      0.0
 2651 migration/3      0.0

```

lsmod:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-15-generic-pae (buildd@zirconium) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #26-Ubuntu SMP Fri Jan 20 17:07:31 UTC 2012 (Ubuntu 3.0.0-15.26-generic-pae 3.0.13)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009a800 (usable)
[    0.000000]  BIOS-e820: 000000000009a800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000caa37000 (usable)
[    0.000000]  BIOS-e820: 00000000caa37000 - 00000000caa7b000 (reserved)
[    0.000000]  BIOS-e820: 00000000caa7b000 - 00000000cadb7000 (usable)
[    0.000000]  BIOS-e820: 00000000cadb7000 - 00000000cade7000 (reserved)
[    0.000000]  BIOS-e820: 00000000cade7000 - 00000000cafe7000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cafe7000 - 00000000cafff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cafff000 - 00000000cb000000 (usable)
[    0.000000]  BIOS-e820: 00000000cb800000 - 00000000cfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 00000000ffc20000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000012f000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Dell Inc. Latitude E5420/0H5TG2, BIOS A03 09/19/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x12f000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FF8000000 write-back
[    0.000000]   3 base 0C8000000 mask FFC000000 write-back
[    0.000000]   4 base 0CB000000 mask FFF000000 uncachable
[    0.000000]   5 base 100000000 mask FE0000000 write-back
[    0.000000]   6 base 120000000 mask FF0000000 write-back
[    0.000000]   7 base 12F000000 mask FFF000000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 128MB, type WB
[    0.000000] reg 3, base: 3200MB, range: 64MB, type WB
[    0.000000] reg 4, base: 3248MB, range: 16MB, type UC
[    0.000000] reg 5, base: 4GB, range: 512MB, type WB
[    0.000000] reg 6, base: 4608MB, range: 256MB, type WB
[    0.000000] reg 7, base: 4848MB, range: 16MB, type UC
[    0.000000] total RAM covered: 4000M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 32M 	num_reg: 8  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 128MB, type WB
[    0.000000] reg 3, base: 3200MB, range: 64MB, type WB
[    0.000000] reg 4, base: 3248MB, range: 16MB, type UC
[    0.000000] reg 5, base: 4GB, range: 512MB, type WB
[    0.000000] reg 6, base: 4608MB, range: 256MB, type WB
[    0.000000] reg 7, base: 4848MB, range: 16MB, type UC
[    0.000000] e820 update range: 00000000cb000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00f1e40] f1e40
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c0096000] 96000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 35986000 - 36cbb000
[    0.000000] ACPI: RSDP 000fe300 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT caffde18 0007C (v01 DELL    CBX3    06222004 MSFT 00010013)
[    0.000000] ACPI: FACP caf87d98 000F4 (v04 DELL    CBX3    06222004 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110413/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xCAFE4E40/0x00000000CAFE4D40, using 32 (20110413/tbfadt-489)
[    0.000000] ACPI: DSDT caf66018 08471 (v02 INT430 SYSFexxx 00001001 INTL 20090903)
[    0.000000] ACPI: FACS cafe4e40 00040
[    0.000000] ACPI: APIC caffcf18 000CC (v02 DELL    CBX3    06222004 MSFT 00010013)
[    0.000000] ACPI: TCPA cafe5d18 00032 (v02                 00000000      00000000)
[    0.000000] ACPI: SSDT caf88a98 002F9 (v01 DELLTP      TPM 00003000 INTL 20090903)
[    0.000000] ACPI: MCFG cafe5c98 0003C (v01 DELL   SNDYBRDG 06222004 MSFT 00000097)
[    0.000000] ACPI: HPET cafe5c18 00038 (v01 A M I   PCHHPET 06222004 AMI. 00000003)
[    0.000000] ACPI: BOOT cafe5b98 00028 (v01 DELL   CBX3     06222004 AMI  00010013)
[    0.000000] ACPI: SSDT caf7d018 00804 (v01  PmRef  Cpu0Ist 00003000 INTL 20090903)
[    0.000000] ACPI: SSDT caf7c018 00996 (v01  PmRef    CpuPm 00003000 INTL 20090903)
[    0.000000] ACPI: DMAR caf87c18 000E8 (v01 INTEL      SNB  00000001 INTL 00000001)
[    0.000000] ACPI: SLIC caf86c18 00176 (v03 DELL    CBX3    06222004 MSFT 00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 3956MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0012f000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000caa37
[    0.000000]     0: 0x000caa7b -> 0x000cadb7
[    0.000000]     0: 0x000cafff -> 0x000cb000
[    0.000000]     0: 0x00100000 -> 0x0012f000
[    0.000000] On node 0 totalpages: 1022206
[    0.000000] free_area_init_node: node 0, pgdat c17f4440, node_mem_map f33a6200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3946 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 221990 pages, LIFO batch:31
[    0.000000]   HighMem zone: 7913 pages used for memmap
[    0.000000]   HighMem zone: 786573 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] 16 Processors exceeds NR_CPUS limit of 8
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] Allocating PCI resources starting at cfa00000 (gap: cfa00000:2f31c000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s29952 r0 d23296 u262144
[    0.000000] pcpu-alloc: s29952 r0 d23296 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1012509
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic-pae root=UUID=a92ec2c6-3c85-4e9b-a23a-10c35867fbc0 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] allocated 19857152 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0012f000)
[    0.000000] Memory: 3999812k/4964352k available (5523k kernel code, 89012k reserved, 2666k data, 720k init, 3177944k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1800000 - 0xc18b4000   ( 720 kB)
[    0.000000]       .data : 0xc1564dfc - 0xc17ff780   (2666 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1564dfc   (5523 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:744 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2494.080 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4988.16 BogoMIPS (lpj=9976320)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000023] Security Framework initialized
[    0.000034] AppArmor: AppArmor initialized
[    0.000035] Yama: becoming mindful.
[    0.000074] Mount-cache hash table entries: 512
[    0.000180] Initializing cgroup subsys cpuacct
[    0.000185] Initializing cgroup subsys memory
[    0.000191] Initializing cgroup subsys devices
[    0.000193] Initializing cgroup subsys freezer
[    0.000194] Initializing cgroup subsys net_cls
[    0.000196] Initializing cgroup subsys blkio
[    0.000200] Initializing cgroup subsys perf_event
[    0.000225] CPU: Physical Processor ID: 0
[    0.000226] CPU: Processor Core ID: 0
[    0.000230] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.000231] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.000234] mce: CPU supports 7 MCE banks
[    0.000245] CPU0: Thermal monitoring enabled (TM1)
[    0.000251] using mwait in idle threads.
[    0.002227] ACPI: Core revision 20110413
[    0.008216] ftrace: allocating 25655 entries in 51 pages
[    0.016988] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.017390] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.057019] CPU0: Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz stepping 07
[    0.163957] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.163963] ... version:                3
[    0.163964] ... bit width:              48
[    0.163965] ... generic registers:      4
[    0.163966] ... value mask:             0000ffffffffffff
[    0.163967] ... max period:             000000007fffffff
[    0.163968] ... fixed-purpose events:   3
[    0.163970] ... event mask:             000000070000000f
[    0.164274] CPU 1 irqstacks, hard=f74d6000 soft=f74e0000
[    0.164275] Booting Node   0, Processors  #1
[    0.164277] smpboot cpu 1: start_ip = 96000
[    0.174505] Initializing CPU#1
[    0.271981] CPU 2 irqstacks, hard=f74ea000 soft=f74ec000
[    0.271983]  #2
[    0.271984] smpboot cpu 2: start_ip = 96000
[    0.282222] Initializing CPU#2
[    0.379789] CPU 3 irqstacks, hard=f74f6000 soft=f74f8000
[    0.379791]  #3
[    0.379792] smpboot cpu 3: start_ip = 96000
[    0.390019] Initializing CPU#3
[    0.487635] Brought up 4 CPUs
[    0.487637] Total of 4 processors activated (19954.08 BogoMIPS).
[    0.490121] devtmpfs: initialized
[    0.490238] PM: Registering ACPI NVS region at cade7000 (2097152 bytes)
[    0.490282] Dell Latitude E5420 series board detected. Selecting PCI-method for reboots.
[    0.491773] print_constraints: dummy: 
[    0.491799] Time:  1:51:41  Date: 01/25/12
[    0.491829] NET: Registered protocol family 16
[    0.491910] Trying to unpack rootfs image as initramfs...
[    0.491915] EISA bus registered
[    0.491929] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.491931] ACPI: bus type pci registered
[    0.491985] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.491988] PCI: not using MMCONFIG
[    0.492045] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.492051] PCI: PCI BIOS revision 2.10 entry at 0xfce72, last bus=17
[    0.492052] PCI: Using configuration type 1 for base access
[    0.492058] dmi type 0xB1 record - unknown flag
[    0.492751] bio: create slab <bio-0> at 0
[    0.494281] ACPI: EC: Look up EC in DSDT
[    0.498477] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.695320] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.787491] ACPI: SSDT cadd7798 00727 (v01  PmRef  Cpu0Cst 00003001 INTL 20090903)
[    0.787868] ACPI: Dynamic OEM Table Load:
[    0.787871] ACPI: SSDT   (null) 00727 (v01  PmRef  Cpu0Cst 00003001 INTL 20090903)
[    0.819344] ACPI: SSDT cadd8a98 00303 (v01  PmRef    ApIst 00003000 INTL 20090903)
[    0.819759] ACPI: Dynamic OEM Table Load:
[    0.819761] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20090903)
[    0.843177] ACPI: SSDT cadd6d98 00119 (v01  PmRef    ApCst 00003000 INTL 20090903)
[    0.843558] ACPI: Dynamic OEM Table Load:
[    0.843560] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20090903)
[    0.846003] Freeing initrd memory: 19668k freed
[    0.935071] ACPI: Interpreter enabled
[    0.935078] ACPI: (supports S0 S3 S4 S5)
[    0.935098] ACPI: Using IOAPIC for interrupt routing
[    0.935118] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.935493] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in ACPI motherboard resources
[    0.935495] PCI: Using MMCONFIG for extended config space
[    1.474675] ACPI: EC: GPE = 0x10, I/O: command/status = 0x934, data = 0x930
[    1.498351] ACPI: No dock devices found.
[    1.498353] HEST: Table not found.
[    1.498357] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.498654] \_SB_.PCI0:_OSC invalid UUID
[    1.498656] _OSC request data:1 8 1f 
[    1.498659] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    1.499179] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.499182] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.499184] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.499186] pci_root PNP0A08:00: host bridge window [mem 0xcfa00000-0xfeafffff]
[    1.499188] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    1.499199] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    1.499234] pci 0000:00:02.0: [8086:0126] type 0 class 0x000300
[    1.499244] pci 0000:00:02.0: reg 10: [mem 0xe1c00000-0xe1ffffff 64bit]
[    1.499251] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.499255] pci 0000:00:02.0: reg 20: [io  0x7000-0x703f]
[    1.499306] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    1.499331] pci 0000:00:16.0: reg 10: [mem 0xe3d80000-0xe3d8000f 64bit]
[    1.499395] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.499399] pci 0000:00:16.0: PME# disabled
[    1.499433] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    1.499455] pci 0000:00:1a.0: reg 10: [mem 0xe3d50000-0xe3d503ff]
[    1.499530] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.499535] pci 0000:00:1a.0: PME# disabled
[    1.499560] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    1.499577] pci 0000:00:1b.0: reg 10: [mem 0xe3d40000-0xe3d43fff 64bit]
[    1.499634] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.499638] pci 0000:00:1b.0: PME# disabled
[    1.499663] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    1.499764] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.499769] pci 0000:00:1c.0: PME# disabled
[    1.499803] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    1.499905] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.499909] pci 0000:00:1c.1: PME# disabled
[    1.499943] pci 0000:00:1c.2: [8086:1c14] type 1 class 0x000604
[    1.500045] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.500050] pci 0000:00:1c.2: PME# disabled
[    1.500082] pci 0000:00:1c.5: [8086:1c1a] type 1 class 0x000604
[    1.500149] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    1.500154] pci 0000:00:1c.5: PME# disabled
[    1.500179] pci 0000:00:1c.6: [8086:1c1c] type 1 class 0x000604
[    1.500247] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    1.500251] pci 0000:00:1c.6: PME# disabled
[    1.500281] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    1.500302] pci 0000:00:1d.0: reg 10: [mem 0xe3d30000-0xe3d303ff]
[    1.500377] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.500382] pci 0000:00:1d.0: PME# disabled
[    1.500407] pci 0000:00:1f.0: [8086:1c49] type 0 class 0x000601
[    1.500523] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    1.500543] pci 0000:00:1f.2: reg 10: [io  0x70b0-0x70b7]
[    1.500551] pci 0000:00:1f.2: reg 14: [io  0x70a0-0x70a3]
[    1.500560] pci 0000:00:1f.2: reg 18: [io  0x7090-0x7097]
[    1.500568] pci 0000:00:1f.2: reg 1c: [io  0x7080-0x7083]
[    1.500577] pci 0000:00:1f.2: reg 20: [io  0x7060-0x707f]
[    1.500585] pci 0000:00:1f.2: reg 24: [mem 0xe3d20000-0xe3d207ff]
[    1.500619] pci 0000:00:1f.2: PME# supported from D3hot
[    1.500623] pci 0000:00:1f.2: PME# disabled
[    1.500641] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    1.500658] pci 0000:00:1f.3: reg 10: [mem 0xe3d10000-0xe3d100ff 64bit]
[    1.500680] pci 0000:00:1f.3: reg 20: [io  0x7040-0x705f]
[    1.500776] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.500782] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.500788] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.500796] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.501019] pci 0000:02:00.0: [8086:0082] type 0 class 0x000280
[    1.501167] pci 0000:02:00.0: reg 10: [mem 0xe3c00000-0xe3c01fff 64bit]
[    1.501727] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    1.501761] pci 0000:02:00.0: PME# disabled
[    1.501949] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    1.501953] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    1.501958] pci 0000:00:1c.1:   bridge window [mem 0xe3c00000-0xe3cfffff]
[    1.501964] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.502010] pci 0000:00:1c.2: PCI bridge to [bus 03-08]
[    1.502014] pci 0000:00:1c.2:   bridge window [io  0x6000-0x6fff]
[    1.502019] pci 0000:00:1c.2:   bridge window [mem 0xe3100000-0xe3afffff]
[    1.502026] pci 0000:00:1c.2:   bridge window [mem 0xe1100000-0xe1afffff 64bit pref]
[    1.502112] pci 0000:09:00.0: [1217:13f7] type 0 class 0x000c00
[    1.502147] pci 0000:09:00.0: reg 10: [mem 0xe3b30000-0xe3b30fff]
[    1.502353] pci 0000:09:00.0: supports D1 D2
[    1.502355] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.502364] pci 0000:09:00.0: PME# disabled
[    1.502440] pci 0000:09:00.1: [1217:8321] type 0 class 0x000805
[    1.502475] pci 0000:09:00.1: reg 10: [mem 0xe3b20000-0xe3b201ff]
[    1.502679] pci 0000:09:00.1: supports D1 D2
[    1.502680] pci 0000:09:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    1.502689] pci 0000:09:00.1: PME# disabled
[    1.502759] pci 0000:09:00.2: [1217:8331] type 0 class 0x000180
[    1.502793] pci 0000:09:00.2: reg 10: [mem 0xe3b10000-0xe3b103ff]
[    1.502839] pci 0000:09:00.2: reg 18: [mem 0xe3b00000-0xe3b003ff]
[    1.502996] pci 0000:09:00.2: supports D1 D2
[    1.502997] pci 0000:09:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    1.503006] pci 0000:09:00.2: PME# disabled
[    1.503107] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
[    1.503111] pci 0000:00:1c.5:   bridge window [io  0xf000-0x0000] (disabled)
[    1.503116] pci 0000:00:1c.5:   bridge window [mem 0xe3b00000-0xe3bfffff]
[    1.503122] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.503360] pci 0000:0a:00.0: [14e4:1681] type 0 class 0x000200
[    1.503399] pci 0000:0a:00.0: reg 10: [mem 0xe2010000-0xe201ffff 64bit]
[    1.503431] pci 0000:0a:00.0: reg 18: [mem 0xe2000000-0xe200ffff 64bit]
[    1.503565] pci 0000:0a:00.0: PME# supported from D3hot D3cold
[    1.503573] pci 0000:0a:00.0: PME# disabled
[    1.503629] pci 0000:00:1c.6: PCI bridge to [bus 0a-11]
[    1.503634] pci 0000:00:1c.6:   bridge window [io  0x2000-0x5fff]
[    1.503638] pci 0000:00:1c.6:   bridge window [mem 0xe2000000-0xe30fffff]
[    1.503645] pci 0000:00:1c.6:   bridge window [mem 0xe0000000-0xe10fffff 64bit pref]
[    1.503670] pci_bus 0000:00: on NUMA node 0
[    1.503672] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.503825] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.503858] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.503894] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    1.503927] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP07._PRT]
[    1.503967] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.504041] \_SB_.PCI0:_OSC invalid UUID
[    1.504042] _OSC request data:1 1f 1f 
[    1.504046]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.504074] \_SB_.PCI0:_OSC invalid UUID
[    1.504075] _OSC request data:1 0 1d 
[    1.504079]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    1.504080] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.507079] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.507121] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.507160] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    1.507198] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.507236] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.507275] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.507314] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    1.507352] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.507432] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.507440] vgaarb: loaded
[    1.507441] vgaarb: bridge control possible 0000:00:02.0
[    1.507593] SCSI subsystem initialized
[    1.507637] libata version 3.00 loaded.
[    1.507669] usbcore: registered new interface driver usbfs
[    1.507677] usbcore: registered new interface driver hub
[    1.507698] usbcore: registered new device driver usb
[    1.507759] PCI: Using ACPI for IRQ routing
[    1.508322] PCI: pci_cache_line_size set to 64 bytes
[    1.508415] reserve RAM buffer: 000000000009a800 - 000000000009ffff 
[    1.508418] reserve RAM buffer: 00000000caa37000 - 00000000cbffffff 
[    1.508421] reserve RAM buffer: 00000000cadb7000 - 00000000cbffffff 
[    1.508423] reserve RAM buffer: 00000000cb000000 - 00000000cbffffff 
[    1.508425] reserve RAM buffer: 000000012f000000 - 000000012fffffff 
[    1.508496] NetLabel: Initializing
[    1.508497] NetLabel:  domain hash size = 128
[    1.508498] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.508506] NetLabel:  unlabeled traffic allowed by default
[    1.508539] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.508544] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.510560] Switching to clocksource hpet
[    1.514202] Switched to NOHz mode on CPU #0
[    1.514258] Switched to NOHz mode on CPU #2
[    1.514303] Switched to NOHz mode on CPU #3
[    1.514310] Switched to NOHz mode on CPU #1
[    1.515680] AppArmor: AppArmor Filesystem Enabled
[    1.515698] pnp: PnP ACPI init
[    1.515708] ACPI: bus type pnp registered
[    1.515998] pnp 00:00: [bus 00-3e]
[    1.516000] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.516002] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.516004] pnp 00:00: [io  0x0d00-0xffff window]
[    1.516006] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.516007] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.516009] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.516011] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.516012] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.516014] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.516016] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.516017] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.516019] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.516021] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.516023] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.516024] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.516026] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.516028] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.516029] pnp 00:00: [mem 0xcfa00000-0xfeafffff window]
[    1.516031] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    1.516084] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.516096] pnp 00:01: [io  0x0000-0x001f]
[    1.516098] pnp 00:01: [io  0x0081-0x0091]
[    1.516099] pnp 00:01: [io  0x0093-0x009f]
[    1.516101] pnp 00:01: [io  0x00c0-0x00df]
[    1.516103] pnp 00:01: [dma 4]
[    1.516120] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.516126] pnp 00:02: [mem 0xff000000-0xffffffff]
[    1.516143] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.516202] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.516236] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    1.516238] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    1.516247] pnp 00:04: [io  0x00f0]
[    1.516255] pnp 00:04: [irq 13]
[    1.516273] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.516282] pnp 00:05: [io  0x002e-0x002f]
[    1.516283] pnp 00:05: [io  0x004e-0x004f]
[    1.516285] pnp 00:05: [io  0x0061]
[    1.516286] pnp 00:05: [io  0x0063]
[    1.516287] pnp 00:05: [io  0x0065]
[    1.516289] pnp 00:05: [io  0x0067]
[    1.516290] pnp 00:05: [io  0x0070]
[    1.516291] pnp 00:05: [io  0x0080]
[    1.516293] pnp 00:05: [io  0x0092]
[    1.516294] pnp 00:05: [io  0x00b2-0x00b3]
[    1.516296] pnp 00:05: [io  0x0680-0x069f]
[    1.516297] pnp 00:05: [io  0x1000-0x100f]
[    1.516298] pnp 00:05: [io  0xffff]
[    1.516300] pnp 00:05: [io  0xffff]
[    1.516301] pnp 00:05: [io  0x0400-0x047f]
[    1.516303] pnp 00:05: [io  0x0500-0x057f]
[    1.516304] pnp 00:05: [io  0x164e-0x164f]
[    1.516336] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.516338] system 00:05: [io  0x1000-0x100f] has been reserved
[    1.516340] system 00:05: [io  0xffff] has been reserved
[    1.516342] system 00:05: [io  0xffff] has been reserved
[    1.516344] system 00:05: [io  0x0400-0x047f] has been reserved
[    1.516346] system 00:05: [io  0x0500-0x057f] has been reserved
[    1.516348] system 00:05: [io  0x164e-0x164f] has been reserved
[    1.516350] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.516357] pnp 00:06: [io  0x0070-0x0077]
[    1.516362] pnp 00:06: [irq 8]
[    1.516380] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.516388] pnp 00:07: [io  0x0060]
[    1.516390] pnp 00:07: [io  0x0064]
[    1.516394] pnp 00:07: [irq 1]
[    1.516413] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.522798] pnp 00:08: Plug and Play ACPI device, IDs PNP0401 (disabled)
[    1.522810] pnp 00:09: [irq 12]
[    1.522829] pnp 00:09: Plug and Play ACPI device, IDs DLL049b PNP0f13 (active)
[    1.522960] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    1.522961] pnp 00:0a: [mem 0xfed10000-0xfed17fff]
[    1.522963] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
[    1.522965] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
[    1.522966] pnp 00:0a: [mem 0xf8000000-0xfbffffff]
[    1.522968] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    1.522969] pnp 00:0a: [mem 0xfed90000-0xfed93fff]
[    1.522971] pnp 00:0a: [mem 0xfed45000-0xfed8ffff]
[    1.522972] pnp 00:0a: [mem 0xff000000-0xffffffff]
[    1.522974] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    1.522976] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
[    1.522978] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
[    1.523020] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.523022] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.523024] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.523026] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.523028] system 00:0a: [mem 0xf8000000-0xfbffffff] has been reserved
[    1.523030] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.523032] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.523034] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.523037] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    1.523039] system 00:0a: [mem 0xfee00000-0xfeefffff] has been reserved
[    1.523041] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.523101] pnp 00:0b: [irq 23]
[    1.523128] pnp 00:0b: Plug and Play ACPI device, IDs SMO8800 (active)
[    1.546654] pnp 00:0c: [mem 0x20000000-0x201fffff]
[    1.546657] pnp 00:0c: [mem 0x40000000-0x401fffff]
[    1.550587] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
[    1.550590] system 00:0c: [mem 0x40000000-0x401fffff] has been reserved
[    1.550592] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.550601] pnp: PnP ACPI: found 13 devices
[    1.550602] ACPI: ACPI bus type pnp unregistered
[    1.550605] PnPBIOS: Disabled by ACPI PNP
[    1.586107] PCI: max bus depth: 1 pci_try_num: 2
[    1.586151] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.586153] pci 0000:00:1c.0:   bridge window [io  disabled]
[    1.586158] pci 0000:00:1c.0:   bridge window [mem disabled]
[    1.586163] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    1.586169] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    1.586170] pci 0000:00:1c.1:   bridge window [io  disabled]
[    1.586176] pci 0000:00:1c.1:   bridge window [mem 0xe3c00000-0xe3cfffff]
[    1.586180] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    1.586187] pci 0000:00:1c.2: PCI bridge to [bus 03-08]
[    1.586190] pci 0000:00:1c.2:   bridge window [io  0x6000-0x6fff]
[    1.586195] pci 0000:00:1c.2:   bridge window [mem 0xe3100000-0xe3afffff]
[    1.586200] pci 0000:00:1c.2:   bridge window [mem 0xe1100000-0xe1afffff 64bit pref]
[    1.586207] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
[    1.586208] pci 0000:00:1c.5:   bridge window [io  disabled]
[    1.586214] pci 0000:00:1c.5:   bridge window [mem 0xe3b00000-0xe3bfffff]
[    1.586218] pci 0000:00:1c.5:   bridge window [mem pref disabled]
[    1.586224] pci 0000:00:1c.6: PCI bridge to [bus 0a-11]
[    1.586227] pci 0000:00:1c.6:   bridge window [io  0x2000-0x5fff]
[    1.586233] pci 0000:00:1c.6:   bridge window [mem 0xe2000000-0xe30fffff]
[    1.586237] pci 0000:00:1c.6:   bridge window [mem 0xe0000000-0xe10fffff 64bit pref]
[    1.586256] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.586261] pci 0000:00:1c.0: setting latency timer to 64
[    1.586272] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.586276] pci 0000:00:1c.1: setting latency timer to 64
[    1.586285] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.586290] pci 0000:00:1c.2: setting latency timer to 64
[    1.586297] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.586301] pci 0000:00:1c.5: setting latency timer to 64
[    1.586308] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.586312] pci 0000:00:1c.6: setting latency timer to 64
[    1.586316] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.586318] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.586320] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.586322] pci_bus 0000:00: resource 7 [mem 0xcfa00000-0xfeafffff]
[    1.586324] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
[    1.586326] pci_bus 0000:02: resource 1 [mem 0xe3c00000-0xe3cfffff]
[    1.586328] pci_bus 0000:03: resource 0 [io  0x6000-0x6fff]
[    1.586329] pci_bus 0000:03: resource 1 [mem 0xe3100000-0xe3afffff]
[    1.586331] pci_bus 0000:03: resource 2 [mem 0xe1100000-0xe1afffff 64bit pref]
[    1.586333] pci_bus 0000:09: resource 1 [mem 0xe3b00000-0xe3bfffff]
[    1.586335] pci_bus 0000:0a: resource 0 [io  0x2000-0x5fff]
[    1.586337] pci_bus 0000:0a: resource 1 [mem 0xe2000000-0xe30fffff]
[    1.586339] pci_bus 0000:0a: resource 2 [mem 0xe0000000-0xe10fffff 64bit pref]
[    1.586364] NET: Registered protocol family 2
[    1.586414] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.586546] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.586767] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.586866] TCP: Hash tables configured (established 131072 bind 65536)
[    1.586868] TCP reno registered
[    1.586870] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    1.586875] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    1.586941] NET: Registered protocol family 1
[    1.586950] pci 0000:00:02.0: Boot video device
[    1.587027] PCI: CLS 64 bytes, default 64
[    1.587030] DMAR: Host address width 36
[    1.587031] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    1.587037] IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
[    1.587038] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    1.587043] IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
[    1.587045] DMAR: RMRR base: 0x000000cadc6000 end: 0x000000cadd5fff
[    1.587047] DMAR: RMRR base: 0x000000cb800000 end: 0x000000cf9fffff
[    1.587048] DMAR: No ATSR found
[    1.587055] Simple Boot Flag at 0xf3 set to 0x1
[    1.587414] audit: initializing netlink socket (disabled)
[    1.587421] type=2000 audit(1327456302.432:1): initialized
[    1.609320] highmem bounce pool size: 64 pages
[    1.609324] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.617718] VFS: Disk quotas dquot_6.5.2
[    1.617770] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.618264] fuse init (API version 7.16)
[    1.618330] msgmni has been set to 1643
[    1.618682] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.618710] io scheduler noop registered
[    1.618712] io scheduler deadline registered
[    1.618722] io scheduler cfq registered (default)
[    1.619024] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.619041] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.619079] intel_idle: MWAIT substates: 0x21120
[    1.619081] intel_idle: v0.4 model 0x2A
[    1.619082] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.619419] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.619730] ACPI: AC Adapter [AC] (off-line)
[    1.619872] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.620331] ACPI: Lid Switch [LID]
[    1.620391] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.620395] ACPI: Power Button [PBTN]
[    1.620423] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.620426] ACPI: Sleep Button [SBTN]
[    1.620453] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.620455] ACPI: Power Button [PWRF]
[    1.620476] ACPI: acpi_idle yielding to intel_idle
[    1.806217] thermal LNXTHERM:00: registered as thermal_zone0
[    1.806220] ACPI: Thermal Zone [THM] (25 C)
[    1.806239] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.806250] ERST: Table is not found!
[    1.806304] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.806308] isapnp: Scanning for PnP cards...
[    1.815985] ACPI: Battery Slot [BAT0] (battery present)
[    2.159823] isapnp: No Plug & Play device found
[    2.209910] Linux agpgart interface v0.103
[    2.209994] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    2.210060] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    2.210957] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    2.211061] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    2.211955] brd: module loaded
[    2.212365] loop: module loaded
[    2.212714] Fixed MDIO Bus: probed
[    2.212731] PPP generic driver version 2.4.2
[    2.212755] tun: Universal TUN/TAP device driver, 1.6
[    2.212756] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.212811] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.212828] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.212842] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.212846] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.212869] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.212892] ehci_hcd 0000:00:1a.0: debug port 2
[    2.216765] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    2.216780] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xe3d50000
[    2.229583] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.229719] hub 1-0:1.0: USB hub found
[    2.229722] hub 1-0:1.0: 2 ports detected
[    2.229772] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.229782] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.229785] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.229808] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.229828] ehci_hcd 0000:00:1d.0: debug port 2
[    2.233710] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    2.233723] ehci_hcd 0000:00:1d.0: irq 17, io mem 0xe3d30000
[    2.249555] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.249680] hub 2-0:1.0: USB hub found
[    2.249683] hub 2-0:1.0: 2 ports detected
[    2.249726] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.249735] uhci_hcd: USB Universal Host Controller Interface driver
[    2.249789] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.250004] i8042: Warning: Keylock active
[    2.251233] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.251238] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.251311] mousedev: PS/2 mouse device common for all mice
[    2.251433] rtc_cmos 00:06: RTC can wake from S4
[    2.251530] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.251566] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    2.251633] device-mapper: uevent: version 1.0.3
[    2.251700] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    2.251721] EISA: Probing bus 0 at eisa.0
[    2.251722] EISA: Cannot allocate resource for mainboard
[    2.251724] Cannot allocate resource for EISA slot 1
[    2.251725] Cannot allocate resource for EISA slot 2
[    2.251727] Cannot allocate resource for EISA slot 3
[    2.251728] Cannot allocate resource for EISA slot 4
[    2.251729] Cannot allocate resource for EISA slot 5
[    2.251731] Cannot allocate resource for EISA slot 6
[    2.251732] Cannot allocate resource for EISA slot 7
[    2.251733] Cannot allocate resource for EISA slot 8
[    2.251735] EISA: Detected 0 cards.
[    2.251742] cpufreq-nforce2: No nForce2 chipset.
[    2.251838] cpuidle: using governor ladder
[    2.252021] cpuidle: using governor menu
[    2.252023] EFI Variables Facility v0.08 2004-May-17
[    2.252206] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.252341] TCP cubic registered
[    2.252438] NET: Registered protocol family 10
[    2.252802] NET: Registered protocol family 17
[    2.252811] Registering the dns_resolver key type
[    2.252823] Using IPI No-Shortcut mode
[    2.252875] PM: Hibernation image not present or could not be loaded.
[    2.252886] registered taskstats version 1
[    2.261986]   Magic number: 12:289:863
[    2.262063] rtc_cmos 00:06: setting system clock to 2012-01-25 01:51:43 UTC (1327456303)
[    2.262851] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.262853] EDD information not available.
[    2.263079] Freeing unused kernel memory: 720k freed
[    2.263276] Write protecting the kernel text: 5524k
[    2.263367] Write protecting the kernel read-only data: 2240k
[    2.263370] NX-protecting the kernel data: 4716k
[    2.284994] zram: module is from the staging directory, the quality is unknown, you have been warned.
[    2.285275] zram: num_devices not specified. Using default: 1
[    2.285278] zram: Creating 1 devices ...
[    2.289514] udevd[96]: starting version 173
[    2.327372] [drm] Initialized drm 1.1.0 20060810
[    2.328463] wmi: Mapper loaded
[    2.330340] firewire_ohci 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.330354] firewire_ohci 0000:09:00.0: setting latency timer to 64
[    2.333848] sdhci: Secure Digital Host Controller Interface driver
[    2.333853] sdhci: Copyright(c) Pierre Ossman
[    2.346135] Adding 2010096k swap on /dev/zram0.  Priority:100 extents:1 across:2010096k SS
[    2.351018] tg3.c:v3.119 (May 18, 2011)
[    2.351041] tg3 0000:0a:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.351057] tg3 0000:0a:00.0: setting latency timer to 64
[    2.353469] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.353478] i915 0000:00:02.0: setting latency timer to 64
[    2.385502] firewire_ohci: Register access failure - please notify linux1394-devel@lists.sf.net
[    2.385536] firewire_ohci: Added fw-ohci device 0000:09:00.0, OHCI v1.10, 8 IR + 8 IT contexts, quirks 0x10
[    2.385778] sdhci-pci 0000:09:00.1: SDHCI controller found [1217:8321] (rev 5)
[    2.385802] sdhci-pci 0000:09:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.385846] sdhci-pci 0000:09:00.1: Invalid iomem size. You may experience problems.
[    2.385890] sdhci-pci 0000:09:00.1: setting latency timer to 64
[    2.385920] mmc0: no vmmc regulator found
[    2.385966] Registered led device: mmc0::
[    2.386020] mmc0: SDHCI controller on PCI [0000:09:00.1] using DMA
[    2.399109] i915 0000:00:02.0: irq 40 for MSI/MSI-X
[    2.399118] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.399122] [drm] Driver supports precise vblank timestamp query.
[    2.399179] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.478244] tg3 0000:0a:00.0: eth0: Tigon3 [partno(BCM95761) rev 5761100] (PCI Express) MAC address d0:67:e5:3f:cb:5e
[    2.478250] tg3 0000:0a:00.0: eth0: attached PHY is 5761 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    2.478254] tg3 0000:0a:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.478258] tg3 0000:0a:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.541259] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    2.585123] Refined TSC clocksource calibration: 2494.332 MHz.
[    2.585130] Switching to clocksource tsc
[    2.673698] hub 1-1:1.0: USB hub found
[    2.673896] hub 1-1:1.0: 6 ports detected
[    2.723748] fbcon: inteldrmfb (fb0) is primary device
[    2.723817] Console: switching to colour frame buffer device 170x48
[    2.723868] fb0: inteldrmfb frame buffer device
[    2.723871] drm: registered panic notifier
[    2.784906] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    2.881589] acpi device:36: registered as cooling_device4
[    2.892835] firewire_core: created device fw0: GUID 02879701364fc000, S400
[    2.917383] hub 2-1:1.0: USB hub found
[    2.917560] hub 2-1:1.0: 6 ports detected
[    2.948879] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    2.948927] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    2.968732] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.968913] ahci 0000:00:1f.2: version 3.0
[    2.988789] usb 1-1.3: new full speed USB device number 3 using ehci_hcd
[    2.992682] ahci 0000:00:1f.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.992761] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    2.992808] ahci: SSS flag set, parallel bus scan disabled
[    3.008642] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3b impl SATA mode
[    3.008650] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    3.008660] ahci 0000:00:1f.2: setting latency timer to 64
[    3.041170] scsi0 : ahci
[    3.041303] scsi1 : ahci
[    3.041408] scsi2 : ahci
[    3.041508] scsi3 : ahci
[    3.041598] scsi4 : ahci
[    3.041710] scsi5 : ahci
[    3.045665] ata1: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20100 irq 41
[    3.045670] ata2: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20180 irq 41
[    3.045673] ata3: DUMMY
[    3.045677] ata4: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20280 irq 41
[    3.045681] ata5: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20300 irq 41
[    3.045685] ata6: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20380 irq 41
[    3.152556] usb 1-1.4: new high speed USB device number 4 using ehci_hcd
[    3.324620] usb 2-1.6: new full speed USB device number 3 using ehci_hcd
[    3.364148] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.386973] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    3.387275] ata1.00: ATA-8: ST9500423AS, 0002DEM1, max UDMA/133
[    3.387285] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.536472] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    3.536757] ata1.00: configured for UDMA/133
[    3.544080] scsi 0:0:0:0: Direct-Access     ATA      ST9500423AS      0002 PQ: 0 ANSI: 5
[    3.544278] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.544316] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.544321] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    3.544426] sd 0:0:0:0: [sda] Write Protect is off
[    3.544431] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.544479] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.586032]  sda: sda1 sda2 sda3 sda4
[    3.586415] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.863499] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.866899] ata2.00: ATAPI: HL-DT-ST DVD+-RW GT50N, A101, max UDMA/133
[    3.869817] ata2.00: configured for UDMA/133
[    3.874354] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GT50N    A101 PQ: 0 ANSI: 5
[    3.881132] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.881151] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.881254] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.881309] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.199036] ata4: SATA link down (SStatus 0 SControl 300)
[    4.518648] ata5: SATA link down (SStatus 0 SControl 300)
[    4.838242] ata6: SATA link down (SStatus 0 SControl 300)
[    6.735320] Btrfs loaded
[    6.740729] xor: automatically using best checksumming function: pIII_sse
[    6.759695]    pIII_sse  :  8969.000 MB/sec
[    6.759700] xor: using function: pIII_sse (8969.000 MB/sec)
[    6.760277] device-mapper: dm-raid45: initialized v0.2594b
[    7.049495] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   16.709123] udevd[421]: starting version 173
[   16.756991] Adding 7812092k swap on /dev/sda4.  Priority:-1 extents:1 across:7812092k 
[   16.759912] lp: driver loaded but no devices found
[   16.763092] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   16.763357] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.763367] mei 0000:00:16.0: setting latency timer to 64
[   16.767087] cfg80211: Calling CRDA to update world regulatory domain
[   16.777573] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   16.777577] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   16.777628] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.777638] iwlagn 0000:02:00.0: setting latency timer to 64
[   16.777668] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   16.783195] type=1400 audit(1327449118.036:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=579 comm="apparmor_parser"
[   16.783610] type=1400 audit(1327449118.036:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=579 comm="apparmor_parser"
[   16.783873] type=1400 audit(1327449118.036:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=579 comm="apparmor_parser"
[   16.794829] iwlagn 0000:02:00.0: device EEPROM VER=0x715, CALIB=0x6
[   16.794832] iwlagn 0000:02:00.0: Device SKU: 0Xb
[   16.794834] iwlagn 0000:02:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   16.795163] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   16.795257] iwlagn 0000:02:00.0: irq 42 for MSI/MSI-X
[   16.810238] Linux video capture interface: v2.00
[   16.810719] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_FHD (05ca:181e)
[   16.814890] input: Laptop_Integrated_Webcam_FHD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input6
[   16.814958] usbcore: registered new interface driver uvcvideo
[   16.814960] USB Video Class driver (v1.1.0)
[   16.819993] parport_pc 00:08: [io  0x0378-0x037b]
[   16.820008] parport_pc 00:08: [io  0x0278-0x027b]
[   16.820019] parport_pc 00:08: [io  0x03bc-0x03bf]
[   16.820029] parport_pc 00:08: [io  0x0378-0x037b]
[   16.820092] parport_pc 00:08: [irq 7]
[   16.824742] Bluetooth: Core ver 2.16
[   16.824763] NET: Registered protocol family 31
[   16.824765] Bluetooth: HCI device and connection manager initialized
[   16.824767] Bluetooth: HCI socket layer initialized
[   16.824768] Bluetooth: L2CAP socket layer initialized
[   16.827748] Bluetooth: SCO socket layer initialized
[   16.828065] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   16.829047] usbcore: registered new interface driver btusb
[   16.870784] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.870838] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   16.870864] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.872586] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   16.937050] cfg80211: World regulatory domain updated:
[   16.937055] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.937058] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.937062] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.937064] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.937067] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.937069] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.937766] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   16.939034] ppdev: user-space parallel port driver
[   17.050519] parport_pc 00:08: activated
[   17.050523] parport_pc 00:08: reported by Plug and Play ACPI
[   17.050588] parport_pc 00:08: disabled
[   17.115732] iwlagn 0000:02:00.0: loaded firmware version 17.168.5.3 build 42301
[   17.115869] Registered led device: phy0-led
[   17.115895] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   17.118015] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   17.156928] alps.c: Enabled hardware quirk, falling back to psmouse-core
[   17.169857] input: ImPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   17.353421] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,user_xattr
[   17.438933] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   17.439050] HDMI status: Pin=6 Presence_Detect=0 ELD_Valid=0
[   17.439175] HDMI status: Pin=7 Presence_Detect=0 ELD_Valid=0
[   17.439406] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   17.439491] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   17.439583] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   17.439662] input: HDA Intel PCH Mic at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   17.439723] input: HDA Intel PCH Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   17.439813] input: HDA Intel PCH Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   17.439872] input: HDA Intel PCH HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   18.321193] type=1400 audit(1327449119.576:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=982 comm="apparmor_parser"
[   18.321441] type=1400 audit(1327449119.576:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=983 comm="apparmor_parser"
[   18.321833] type=1400 audit(1327449119.576:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=983 comm="apparmor_parser"
[   18.322084] type=1400 audit(1327449119.576:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=983 comm="apparmor_parser"
[   18.322386] type=1400 audit(1327449119.576:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=986 comm="apparmor_parser"
[   18.322741] type=1400 audit(1327449119.576:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=986 comm="apparmor_parser"
[   18.323773] type=1400 audit(1327449119.576:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=987 comm="apparmor_parser"
[   18.502056] init: failsafe main process (925) killed by TERM signal
[   18.502962] init: apport pre-start process (1021) terminated with status 1
[   18.513111] init: apport post-stop process (1071) terminated with status 1
[   18.683658] Bluetooth: RFCOMM TTY layer initialized
[   18.683662] Bluetooth: RFCOMM socket layer initialized
[   18.683664] Bluetooth: RFCOMM ver 1.11
[   18.687179] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.687182] Bluetooth: BNEP filters: protocol multicast
[   18.845069] init: anacron main process (1096) killed by TERM signal
[   18.955312] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.957305] tg3 0000:0a:00.0: irq 44 for MSI/MSI-X
[   19.033334] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.433426] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,user_xattr,commit=600
[   22.799911] init: plymouth-stop pre-start process (1489) terminated with status 1
[   26.535859] wlan0: authenticate with 00:21:63:40:ac:88 (try 1)
[   26.538717] wlan0: authenticated
[   26.539501] wlan0: associate with 00:21:63:40:ac:88 (try 1)
[   26.541947] wlan0: RX AssocResp from 00:21:63:40:ac:88 (capab=0x401 status=0 aid=2)
[   26.541956] wlan0: associated
[   26.544921] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   37.208293] wlan0: no IPv6 routers present
[  142.017482] EXT3-fs: barriers not enabled
[  142.024188] kjournald starting.  Commit interval 5 seconds
[  142.024337] EXT3-fs (dm-0): using internal journal
[  142.024414] EXT3-fs (dm-0): mounted filesystem with ordered data mode
[ 2023.889072] wlan0: deauthenticating from 00:21:63:40:ac:88 by local choice (reason=3)
[ 2023.976284] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2023.976291] cfg80211: Restoring regulatory settings
[ 2023.976294] cfg80211: Calling CRDA to update world regulatory domain
[ 2023.981291] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 2023.981296] cfg80211: World regulatory domain updated:
[ 2023.981297] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2023.981300] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2023.981302] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2023.981304] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2023.981306] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2023.981308] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2024.074415] tg3 0000:0a:00.0: PME# enabled
[ 2024.103530] tg3 0000:0a:00.0: wake-up capability enabled by ACPI
[ 2025.084101] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[ 2026.327917] init: anacron main process (2379) killed by TERM signal
[ 2026.581457] PM: Syncing filesystems ... done.
[ 2026.584276] PM: Preparing system for mem sleep
[ 2027.215567] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 2027.231454] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 2027.247442] PM: Entering mem sleep
[ 2027.247540] Suspending console(s) (use no_console_suspend to debug)
[ 2027.247748] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 2027.248101] sd 0:0:0:0: [sda] Stopping disk
[ 2027.262964] ACPI handle has no context!
[ 2027.262976] sdhci-pci 0000:09:00.1: PCI INT B disabled
[ 2027.262984] ACPI handle has no context!
[ 2027.295351] ehci_hcd 0000:00:1d.0: PCI INT A disabled
[ 2027.295361] ehci_hcd 0000:00:1a.0: PCI INT A disabled
[ 2027.367788] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 2027.383224] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 120.310 msecs
[ 2027.623615] PM: suspend of drv:sd dev:0:0:0:0 complete after 376.352 msecs
[ 2027.623650] PM: suspend of drv:scsi dev:target0:0:0 complete after 376.367 msecs
[ 2027.623675] PM: suspend of drv:scsi dev:host0 complete after 376.047 msecs
[ 2027.646880] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 384.351 msecs
[ 2027.647017] PM: suspend of drv: dev:pci0000:00 complete after 384.300 msecs
[ 2027.647026] PM: suspend of devices complete after 399.841 msecs
[ 2027.647028] PM: suspend devices took 0.400 seconds
[ 2027.710868] PM: late suspend of devices complete after 63.919 msecs
[ 2027.711038] ACPI: Preparing to enter system sleep state S3
[ 2027.738938] PM: Saving platform NVS memory
[ 2027.741301] Disabling non-boot CPUs ...
[ 2027.743036] CPU 1 is now offline
[ 2027.846622] CPU 2 is now offline
[ 2027.847415] Broke affinity for irq 17
[ 2027.950487] CPU 3 is now offline
[ 2027.950759] Extended CMOS year: 2000
[ 2027.951015] ACPI: Low-level resume complete
[ 2027.951054] PM: Restoring platform NVS memory
[ 2027.951754] Extended CMOS year: 2000
[ 2027.951790] Enabling non-boot CPUs ...
[ 2027.951861] Booting Node 0 Processor 1 APIC 0x2
[ 2027.951862] smpboot cpu 1: start_ip = 96000
[ 2027.962071] Initializing CPU#1
[ 2028.059781] CPU1 is up
[ 2028.060090] Booting Node 0 Processor 2 APIC 0x1
[ 2028.060092] smpboot cpu 2: start_ip = 96000
[ 2028.063296] Switched to NOHz mode on CPU #1
[ 2028.070192] Initializing CPU#2
[ 2028.167777] CPU2 is up
[ 2028.168002] Booting Node 0 Processor 3 APIC 0x3
[ 2028.168004] smpboot cpu 3: start_ip = 96000
[ 2028.171156] Switched to NOHz mode on CPU #2
[ 2028.178203] Initializing CPU#3
[ 2028.275826] CPU3 is up
[ 2028.278537] ACPI: Waking up from system sleep state S3
[ 2028.279034] Switched to NOHz mode on CPU #3
[ 2028.586907] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[ 2028.586927] mei 0000:00:16.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 2028.586943] mei 0000:00:16.0: restoring config space at offset 0x4 (was 0xfedb0004, writing 0xe3d80004)
[ 2028.586968] ehci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 2028.586983] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x4 (was 0x0, writing 0xe3d50000)
[ 2028.586989] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[ 2028.587015] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[ 2028.587028] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0x4, writing 0xe3d40004)
[ 2028.587032] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2028.587037] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
[ 2028.587071] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 2028.587088] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0xf0, writing 0x200000f0)
[ 2028.587098] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 2028.587105] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 2028.587153] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 2028.587170] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0xf0, writing 0x200000f0)
[ 2028.587180] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 2028.587187] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 2028.587235] pcieport 0000:00:1c.2: restoring config space at offset 0xf (was 0x300, writing 0x303)
[ 2028.587258] pcieport 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 2028.587264] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 2028.587306] pcieport 0000:00:1c.5: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 2028.587321] pcieport 0000:00:1c.5: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 2028.587325] pcieport 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 2028.587355] pcieport 0000:00:1c.6: restoring config space at offset 0xf (was 0x300, writing 0x303)
[ 2028.587369] pcieport 0000:00:1c.6: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 2028.587375] pcieport 0000:00:1c.6: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 2028.587402] ehci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 2028.587417] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x4 (was 0x0, writing 0xe3d30000)
[ 2028.587423] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[ 2028.587491] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 2028.587526] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800003)
[ 2028.587615] iwlagn 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 2028.587653] iwlagn 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xe3c00004)
[ 2028.587661] iwlagn 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2028.587672] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 2028.587761] firewire_ohci 0000:09:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 2028.587786] firewire_ohci 0000:09:00.0: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[ 2028.587793] firewire_ohci 0000:09:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 2028.587836] sdhci-pci 0000:09:00.1: restoring config space at offset 0xf (was 0x200, writing 0x203)
[ 2028.587860] sdhci-pci 0000:09:00.1: restoring config space at offset 0x4 (was 0x0, writing 0xe3b20000)
[ 2028.587865] sdhci-pci 0000:09:00.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[ 2028.587873] sdhci-pci 0000:09:00.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 2028.587916] pci 0000:09:00.2: restoring config space at offset 0xf (was 0x300, writing 0x30b)
[ 2028.587936] pci 0000:09:00.2: restoring config space at offset 0x6 (was 0x0, writing 0xe3b00000)
[ 2028.587944] pci 0000:09:00.2: restoring config space at offset 0x4 (was 0x0, writing 0xe3b10000)
[ 2028.587949] pci 0000:09:00.2: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[ 2028.587957] pci 0000:09:00.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 2028.588208] tg3 0000:0a:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2028.588216] tg3 0000:0a:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 2028.588323] PM: early resume of devices complete after 1.457 msecs
[ 2028.588399] i915 0000:00:02.0: setting latency timer to 64
[ 2028.588430] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2028.588436] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[ 2028.588450] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 2028.588456] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 2028.588480] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2028.588483] ahci 0000:00:1f.2: setting latency timer to 64
[ 2028.588490] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[ 2028.588522] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[ 2028.588526] sdhci-pci 0000:09:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[ 2028.588534] sdhci-pci 0000:09:00.1: setting latency timer to 64
[ 2028.602700] sd 0:0:0:0: [sda] Starting disk
[ 2028.642706] firewire_core: skipped bus generations, destroying all nodes
[ 2028.734873] PM: resume of drv:button dev:PNP0C0D:00 complete after 146.475 msecs
[ 2028.766499] PM: resume of drv:hub dev:2-1:1.0 complete after 178.074 msecs
[ 2028.766516] PM: resume of drv:hub dev:1-1:1.0 complete after 178.122 msecs
[ 2028.766519] PM: resume of drv: dev:ep_81 complete after 178.087 msecs
[ 2028.766522] PM: resume of drv: dev:ep_00 complete after 178.117 msecs
[ 2028.766524] PM: resume of drv: dev:ep_81 complete after 178.121 msecs
[ 2028.766527] PM: resume of drv: dev:ep_00 complete after 178.080 msecs
[ 2028.798579] tg3 0000:0a:00.0: wake-up capability disabled by ACPI
[ 2028.798590] tg3 0000:0a:00.0: PME# disabled
[ 2028.798593] PM: resume of drv:tg3 dev:0000:0a:00.0 complete after 210.340 msecs
[ 2028.838603] usb 1-1.3: reset full speed USB device number 3 using ehci_hcd
[ 2028.887114] Extended CMOS year: 2000
[ 2028.930235] ata5: SATA link down (SStatus 0 SControl 300)
[ 2028.931102] PM: resume of drv:usb dev:1-1.3:1.0 complete after 342.637 msecs
[ 2028.931118] PM: resume of drv: dev:ep_00 complete after 342.512 msecs
[ 2028.931127] PM: resume of drv: dev:ep_81 complete after 342.643 msecs
[ 2028.931137] PM: resume of drv: dev:ep_02 complete after 342.552 msecs
[ 2028.938219] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2028.943550] ata2.00: configured for UDMA/133
[ 2028.946220] ata4: SATA link down (SStatus 0 SControl 300)
[ 2028.954206] ata6: SATA link down (SStatus 0 SControl 300)
[ 2029.002250] usb 2-1.6: reset full speed USB device number 3 using ehci_hcd
[ 2029.096367] btusb 2-1.6:1.0: no reset_resume for driver btusb?
[ 2029.096374] btusb 2-1.6:1.1: no reset_resume for driver btusb?
[ 2029.142048] firewire_core: rediscovered device fw0
[ 2029.166014] usb 1-1.4: reset high speed USB device number 4 using ehci_hcd
[ 2029.304299] PM: resume of drv:i915 dev:0000:00:02.0 complete after 716.831 msecs
[ 2029.345900] PM: resume of drv:usb dev:2-1.6:1.0 complete after 757.365 msecs
[ 2029.345903] PM: resume of drv:usb dev:2-1.6:1.2 complete after 757.276 msecs
[ 2029.345908] PM: resume of drv:usb dev:2-1.6:1.1 complete after 757.323 msecs
[ 2029.345912] PM: resume of drv: dev:ep_81 complete after 757.365 msecs
[ 2029.345915] PM: resume of drv: dev:ep_83 complete after 757.318 msecs
[ 2029.345917] PM: resume of drv: dev:ep_82 complete after 757.356 msecs
[ 2029.345918] PM: resume of drv: dev:ep_03 complete after 757.308 msecs
[ 2029.345920] PM: resume of drv: dev:ep_02 complete after 757.349 msecs
[ 2029.345922] PM: resume of drv:usb dev:2-1.6:1.3 complete after 757.261 msecs
[ 2029.345924] PM: resume of drv: dev:ep_84 complete after 757.288 msecs
[ 2029.345930] PM: resume of drv: dev:ep_04 complete after 757.282 msecs
[ 2029.345932] PM: resume of drv: dev:ep_00 complete after 757.257 msecs
[ 2029.572163] PM: resume of drv:uvcvideo dev:1-1.4:1.1 complete after 984.209 msecs
[ 2029.572175] PM: resume of drv: dev:ep_00 complete after 983.940 msecs
[ 2029.572210] PM: resume of drv:uvcvideo dev:1-1.4:1.0 complete after 984.318 msecs
[ 2029.572270] PM: resume of drv: dev:ep_81 complete after 984.336 msecs
[ 2030.432281] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2030.699464] ata1.00: ACPI cmd ef/5a:00:00:00:00:a0 (SET FEATURES) succeeded
[ 2030.959995] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[ 2030.960269] ata1.00: configured for UDMA/133
[ 2031.001541] PM: resume of drv:sd dev:0:0:0:0 complete after 2414.978 msecs
[ 2031.001598] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 1699.439 msecs
[ 2031.001601] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2415.017 msecs
[ 2031.003236] PM: resume of devices complete after 2418.017 msecs
[ 2031.003454] PM: resume devices took 2.416 seconds
[ 2031.003479] PM: Finishing wakeup.
[ 2031.003480] Restarting tasks ... done.
[ 2031.021431] video LNXVIDEO:00: Restoring backlight state
[ 2031.155701] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[ 2032.335542] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[ 2032.555800] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2032.557599] tg3 0000:0a:00.0: irq 44 for MSI/MSI-X
[ 2032.633945] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2040.045117] wlan0: authenticate with 00:21:63:40:ac:88 (try 1)
[ 2040.047937] wlan0: authenticated
[ 2040.048448] wlan0: associate with 00:21:63:40:ac:88 (try 1)
[ 2040.050897] wlan0: RX AssocResp from 00:21:63:40:ac:88 (capab=0x401 status=0 aid=2)
[ 2040.050906] wlan0: associated
[ 2040.053399] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2050.238613] wlan0: no IPv6 routers present

```

---

