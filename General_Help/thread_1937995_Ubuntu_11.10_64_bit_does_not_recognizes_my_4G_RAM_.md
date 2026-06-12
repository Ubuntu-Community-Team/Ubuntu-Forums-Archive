---
title: "Ubuntu 11.10 64 bit does not recognizes my 4G RAM (32bit+PAE does)"
date: 2012-03-08
forum: General Help
---

### Post by Marko Darko on 2012-03-08
Hi Folks,

This question may have been answered before, but I failed to find any answer because, if it exists, it's buried in thousands of Google results for another problem (people tring to get 32 bit non-PAE systems to map more than ~3 GB RAM).



I have installed Ubuntu 11.10 in a Dell Inspiron N4050 laptop with a Core i5 processor (Sandy Bridge, 2nd generation), but the system fails to recognize all my 4GB of RAM.

In this 64 bit installation, free shows me:
```
$ free
             total       used       free     shared    buffers     cached
Mem:       3963304    2107852    1855452          0     110656    1245604
-/+ buffers/cache:     751592    3211712
Swap:      5857276     150400    5706876

```

For pure experimentation/investigation, I formatted the system removing the 64 bit edition and installed Ubuntu 32 bits + a PAE enabled kernel; all my 4096 MB of memory was correctly identified.

Since I have no plans of running a 32 bit system in this machine, I removed the 32 bit edition (formatting the disk) and installed the 64 bit edition again to try to solve the problem.  Have someone got a similar problem?



Some quick facts:

- The system **is** running a 64 bit Ubuntu 11.10 now;
- I use Linux for almost ten years now and I'm not afraid of commands;
- The memory **IS** ok; It passes memtest86, it was shown as expected in the 32 bit + PAE edition;
- All the memory was also identified by the Windows 7 which came pre-installed in the machine (now removed);
- The system have a Intel HD Graphics controller which (AFAIK) should not reserve any memory -- from another system I have here, it seems that the driver allocates memory on the fly instead of reserving it;
- The system is updated;


Also, follows uname and lspci

```

$uname -a
Linux stark 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```



Do someone anybody knows what is happening?

---

### Post by dcstar on 2012-03-09
> **Marko Darko said:**
> Hi Folks,

This question may have been answered before, but I failed to find any answer because, if it exists, it's buried in thousands of Google results for another problem (people tring to get 32 bit non-PAE systems to map more than ~3 GB RAM).



I have installed Ubuntu 11.10 in a Dell Inspiron N4050 laptop with a Core i5 processor (Sandy Bridge, 2nd generation), but the system fails to recognize all my 4GB of RAM.

In this 64 bit installation, free shows me:
```
$ free
             total       used       free     shared    buffers     cached
Mem:       **3963304**    2107852    1855452          0     110656    1245604
-/+ buffers/cache:     751592    3211712
Swap:      5857276     150400    5706876

```
...........

Why do **you** think that is virtually not the full 4GB?

---

### Post by Marko Darko on 2012-03-09
Because 4GB should appear as 4194304 (4*1024*1024) KB as does the 32 bit edition + PAE? My BIOS and memtest also shows 4096 MB, which matches the expectations.

Or am I missing some weird behavior of "true" x64 systems here?

Also, free -m shows me:
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3870       1070       2800          0         55        488
-/+ buffers/cache:        525       3344
Swap:         5719          0       5719
```

---

### Post by Jon Monreal on 2012-03-09
I would imagine that this is the result of the kernel (and possibly hardware drivers) reserving address space. With 64-bit, more space in RAM may be required (this is true of 64-bit applications as well).

I don't think you would see the "full" amount of RAM on a machine running 32-bit Ubuntu either. Are you saying that you do?

---

### Post by Marko Darko on 2012-03-09
> **Jon Monreal said:**
> I don't think you would see the "full" amount of RAM on a machine running 32-bit Ubuntu either. Are you saying that you do?

Yes, it happened. Unless I hit some bug or unusual behavior in PAE, the 32 bit edition shows all memory.

For a time, I suspected on the video controller, but I see no reason why it should reserve memory in 64 bit but not in 32 bit. Also, I remember those Intel controllers do not reserve memory.

---

### Post by Marko Darko on 2012-03-10
A little bit more information regarding this case. Doing my experimentations, I booted the system passing a "mem=4096M" parameter to the kernel that actually **decreased** the amount of mapped memory to something near to 3,5GiB (I forgot copying the exact values).

Follows the output of "dmesg" for both cases:

Without forced memory:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-16-generic (buildd@roseapple) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 (Ubuntu 3.0.0-16.29-generic 3.0.20)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.0.0-16-generic root=/dev/mapper/gr1-root ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000da4ea000 (usable)
[    0.000000]  BIOS-e820: 00000000da4ea000 - 00000000da52d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000da52d000 - 00000000da798000 (usable)
[    0.000000]  BIOS-e820: 00000000da798000 - 00000000da967000 (reserved)
[    0.000000]  BIOS-e820: 00000000da967000 - 00000000dacbc000 (usable)
[    0.000000]  BIOS-e820: 00000000dacbc000 - 00000000dad68000 (reserved)
[    0.000000]  BIOS-e820: 00000000dad68000 - 00000000dafe8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dafe8000 - 00000000db000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000db800000 - 00000000dfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000011fe00000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Dell Inc. Inspiron N4050/0X0DC1, BIOS A06 11/14/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x11fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FE0000000 write-back
[    0.000000]   2 base 0DB800000 mask FFF800000 uncachable
[    0.000000]   3 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   5 base 11FE00000 mask FFFE00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 4, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 5, base: 4606MB, range: 2MB, type UC
[    0.000000] total RAM covered: 4022M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 7      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 4, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 5, base: 4GB, range: 512MB, type WB
[    0.000000] reg 6, base: 4606MB, range: 2MB, type UC
[    0.000000] e820 update range: 00000000db800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdacbc max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fd1b0] fd1b0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000dacbc000
[    0.000000]  0000000000 - 00dac00000 page 2M
[    0.000000]  00dac00000 - 00dacbc000 page 4k
[    0.000000] kernel direct mapping tables up to dacbc000 @ 1fffa000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000011fe00000
[    0.000000]  0100000000 - 011fe00000 page 2M
[    0.000000] kernel direct mapping tables up to 11fe00000 @ dacb6000-dacbc000
[    0.000000] RAMDISK: 358ea000 - 36c6d000
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v02   DELL)
[    0.000000] ACPI: XSDT 00000000dafe8078 0006C (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000daff1c38 000F4 (v04   DELL     WN09 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000dafe8170 09AC8 (v02   DELL     WN09 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000dafe4f80 00040
[    0.000000] ACPI: APIC 00000000daff1d30 00072 (v03   DELL     WN09 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000daff1da8 0003C (v01   DELL     WN09 01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000daff1de8 004B0 (v01 TrmRef PtidDevc 00001000 INTL 20091112)
[    0.000000] ACPI: SLIC 00000000daff2298 00176 (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: HPET 00000000daff2410 00038 (v01   DELL     WN09 01072009 AMI. 00000004)
[    0.000000] ACPI: SSDT 00000000daff2448 007C2 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000daff2c10 00996 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: OSFR 00000000daff35a8 0008C (v01 DELL    M08     07DB0B0E ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000011fe00000
[    0.000000] Initmem setup node 0 0000000000000000-000000011fe00000
[    0.000000]   NODE_DATA [000000011fdfb000 - 000000011fdfffff]
[    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff88011b400000-ffff88011edfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0011fe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000da4ea
[    0.000000]     0: 0x000da52d -> 0x000da798
[    0.000000]     0: 0x000da967 -> 0x000dacbc
[    0.000000]     0: 0x00100000 -> 0x0011fe00
[    0.000000] On node 0 totalpages: 1025079
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3920 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 876258 pages, LIFO batch:31
[    0.000000]   Normal zone: 1785 pages used for memmap
[    0.000000]   Normal zone: 128775 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
[    0.000000] PM: Registered nosave memory: 00000000da4ea000 - 00000000da52d000
[    0.000000] PM: Registered nosave memory: 00000000da798000 - 00000000da967000
[    0.000000] PM: Registered nosave memory: 00000000dacbc000 - 00000000dad68000
[    0.000000] PM: Registered nosave memory: 00000000dad68000 - 00000000dafe8000
[    0.000000] PM: Registered nosave memory: 00000000dafe8000 - 00000000db000000
[    0.000000] PM: Registered nosave memory: 00000000db000000 - 00000000db800000
[    0.000000] PM: Registered nosave memory: 00000000db800000 - 00000000dfa00000
[    0.000000] PM: Registered nosave memory: 00000000dfa00000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed04000
[    0.000000] PM: Registered nosave memory: 00000000fed04000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at dfa00000 (gap: dfa00000:18600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88011fa00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1008953
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.0-16-generic root=/dev/mapper/gr1-root ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3938912k/4716544k available (6140k kernel code, 616228k absent, 161404k reserved, 6894k data, 988k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2394.617 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4789.23 BogoMIPS (lpj=9578468)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000026] Security Framework initialized
[    0.000038] AppArmor: AppArmor initialized
[    0.000040] Yama: becoming mindful.
[    0.000428] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001475] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001916] Mount-cache hash table entries: 256
[    0.002012] Initializing cgroup subsys cpuacct
[    0.002016] Initializing cgroup subsys memory
[    0.002022] Initializing cgroup subsys devices
[    0.002023] Initializing cgroup subsys freezer
[    0.002025] Initializing cgroup subsys net_cls
[    0.002026] Initializing cgroup subsys blkio
[    0.002031] Initializing cgroup subsys perf_event
[    0.002055] CPU: Physical Processor ID: 0
[    0.002056] CPU: Processor Core ID: 0
[    0.002060] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002061] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002064] mce: CPU supports 7 MCE banks
[    0.002075] CPU0: Thermal monitoring enabled (TM1)
[    0.002081] using mwait in idle threads.
[    0.004402] ACPI: Core revision 20110413
[    0.014445] ftrace: allocating 25748 entries in 101 pages
[    0.041563] x2apic not enabled, IRQ remapping init failed
[    0.042028] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.081662] CPU0: Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz stepping 07
[    0.187676] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.187692] ... version:                3
[    0.187695] ... bit width:              48
[    0.187698] ... generic registers:      4
[    0.187702] ... value mask:             0000ffffffffffff
[    0.187706] ... max period:             000000007fffffff
[    0.187709] ... fixed-purpose events:   3
[    0.187713] ... event mask:             000000070000000f
[    0.188717] Booting Node   0, Processors  #1
[    0.188724] smpboot cpu 1: start_ip = 98000
[    0.299813]  #2
[    0.299818] smpboot cpu 2: start_ip = 98000
[    0.407640]  #3 Ok.
[    0.407644] smpboot cpu 3: start_ip = 98000
[    0.515391] Brought up 4 CPUs
[    0.515398] Total of 4 processors activated (19156.18 BogoMIPS).
[    0.521929] devtmpfs: initialized
[    0.522234] PM: Registering ACPI NVS region at da4ea000 (274432 bytes)
[    0.522251] PM: Registering ACPI NVS region at dad68000 (2621440 bytes)
[    0.526002] print_constraints: dummy: 
[    0.526042] Time: 20:10:32  Date: 03/10/12
[    0.526113] NET: Registered protocol family 16
[    0.526331] Trying to unpack rootfs image as initramfs...
[    0.526358] ACPI: bus type pci registered
[    0.526481] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.526489] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.568627] PCI: Using configuration type 1 for base access
[    0.570373] bio: create slab <bio-0> at 0
[    0.574489] ACPI: EC: Look up EC in DSDT
[    0.578687] ACPI: Executed 1 blocks of module-level executable AML code
[    0.588252] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.619309] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.620222] ACPI: SSDT 00000000dad51698 0064F (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.621238] ACPI: Dynamic OEM Table Load:
[    0.621245] ACPI: SSDT           (null) 0064F (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.639761] ACPI: SSDT 00000000dad52a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.640852] ACPI: Dynamic OEM Table Load:
[    0.640858] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.675349] ACPI: SSDT 00000000dad50d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.676347] ACPI: Dynamic OEM Table Load:
[    0.676353] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.708396] ACPI: Interpreter enabled
[    0.708405] ACPI: (supports S0 S1 S3 S4 S5)
[    0.708473] ACPI: Using IOAPIC for interrupt routing
[    0.747991] ACPI: No dock devices found.
[    0.747997] HEST: Table not found.
[    0.748004] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.748836] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.749996] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.750003] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.750009] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.750015] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.750021] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.750026] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.750031] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.750036] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.750043] pci_root PNP0A08:00: host bridge window [mem 0xdfa00000-0xfeafffff]
[    0.750048] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    0.750078] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    0.750170] pci 0000:00:02.0: [8086:0116] type 0 class 0x000300
[    0.750198] pci 0000:00:02.0: reg 10: [mem 0xf6800000-0xf6bfffff 64bit]
[    0.750216] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.750228] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    0.750361] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    0.750410] pci 0000:00:16.0: reg 10: [mem 0xf7e0a000-0xf7e0a00f 64bit]
[    0.750567] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.750577] pci 0000:00:16.0: PME# disabled
[    0.750645] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    0.750689] pci 0000:00:1a.0: reg 10: [mem 0xf7e08000-0xf7e083ff]
[    0.750877] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.750887] pci 0000:00:1a.0: PME# disabled
[    0.750936] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    0.750977] pci 0000:00:1b.0: reg 10: [mem 0xf7e00000-0xf7e03fff 64bit]
[    0.751131] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.751140] pci 0000:00:1b.0: PME# disabled
[    0.751183] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    0.751353] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.751361] pci 0000:00:1c.0: PME# disabled
[    0.751408] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    0.751578] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.751586] pci 0000:00:1c.1: PME# disabled
[    0.751640] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
[    0.751810] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.751818] pci 0000:00:1c.3: PME# disabled
[    0.751871] pci 0000:00:1c.7: [8086:1c1e] type 1 class 0x000604
[    0.752042] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.752051] pci 0000:00:1c.7: PME# disabled
[    0.752108] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    0.752152] pci 0000:00:1d.0: reg 10: [mem 0xf7e07000-0xf7e073ff]
[    0.752337] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.752346] pci 0000:00:1d.0: PME# disabled
[    0.752393] pci 0000:00:1f.0: [8086:1c4b] type 0 class 0x000601
[    0.752630] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    0.752675] pci 0000:00:1f.2: reg 10: [io  0xf0b0-0xf0b7]
[    0.752694] pci 0000:00:1f.2: reg 14: [io  0xf0a0-0xf0a3]
[    0.752713] pci 0000:00:1f.2: reg 18: [io  0xf090-0xf097]
[    0.752732] pci 0000:00:1f.2: reg 1c: [io  0xf080-0xf083]
[    0.752751] pci 0000:00:1f.2: reg 20: [io  0xf060-0xf07f]
[    0.752770] pci 0000:00:1f.2: reg 24: [mem 0xf7e06000-0xf7e067ff]
[    0.752879] pci 0000:00:1f.2: PME# supported from D3hot
[    0.752887] pci 0000:00:1f.2: PME# disabled
[    0.752924] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    0.752958] pci 0000:00:1f.3: reg 10: [mem 0xf7e05000-0xf7e050ff 64bit]
[    0.753006] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    0.753159] pci 0000:00:1c.0: PCI bridge to [bus 03-04]
[    0.753169] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.753179] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.753193] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.753323] pci 0000:05:00.0: [10ec:8136] type 0 class 0x000200
[    0.753358] pci 0000:05:00.0: reg 10: [io  0xe000-0xe0ff]
[    0.753416] pci 0000:05:00.0: reg 18: [mem 0xf1104000-0xf1104fff 64bit pref]
[    0.753455] pci 0000:05:00.0: reg 20: [mem 0xf1100000-0xf1103fff 64bit pref]
[    0.753611] pci 0000:05:00.0: supports D1 D2
[    0.753615] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.753626] pci 0000:05:00.0: PME# disabled
[    0.758982] pci 0000:00:1c.1: PCI bridge to [bus 05-06]
[    0.758991] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.759001] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.759015] pci 0000:00:1c.1:   bridge window [mem 0xf1100000-0xf11fffff 64bit pref]
[    0.759145] pci 0000:09:00.0: [168c:002b] type 0 class 0x000280
[    0.759192] pci 0000:09:00.0: reg 10: [mem 0xf7d00000-0xf7d0ffff 64bit]
[    0.759409] pci 0000:09:00.0: supports D1
[    0.759414] pci 0000:09:00.0: PME# supported from D0 D1 D3hot
[    0.759424] pci 0000:09:00.0: PME# disabled
[    0.766961] pci 0000:00:1c.3: PCI bridge to [bus 09-0a]
[    0.766971] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
[    0.766981] pci 0000:00:1c.3:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.766994] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.767090] pci 0000:00:1c.7: PCI bridge to [bus 11-1f]
[    0.767099] pci 0000:00:1c.7:   bridge window [io  0xc000-0xdfff]
[    0.767108] pci 0000:00:1c.7:   bridge window [mem 0xf6c00000-0xf7cfffff]
[    0.767122] pci 0000:00:1c.7:   bridge window [mem 0xf0000000-0xf10fffff 64bit pref]
[    0.767171] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.767503] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.767591] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.767680] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.767777] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08._PRT]
[    0.768109]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.768585]  pci0000:00: ACPI _OSC control (0x19) granted
[    0.776383] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.776497] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.776608] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.776716] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.776821] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.776929] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.777036] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.777149] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.777367] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.777383] vgaarb: loaded
[    0.777386] vgaarb: bridge control possible 0000:00:02.0
[    0.777764] SCSI subsystem initialized
[    0.777879] libata version 3.00 loaded.
[    0.777961] usbcore: registered new interface driver usbfs
[    0.777986] usbcore: registered new interface driver hub
[    0.778065] usbcore: registered new device driver usb
[    0.778256] PCI: Using ACPI for IRQ routing
[    0.781894] PCI: pci_cache_line_size set to 64 bytes
[    0.782019] reserve RAM buffer: 000000000009d400 - 000000000009ffff 
[    0.782025] reserve RAM buffer: 00000000da4ea000 - 00000000dbffffff 
[    0.782033] reserve RAM buffer: 00000000da798000 - 00000000dbffffff 
[    0.782041] reserve RAM buffer: 00000000dacbc000 - 00000000dbffffff 
[    0.782047] reserve RAM buffer: 000000011fe00000 - 000000011fffffff 
[    0.782242] NetLabel: Initializing
[    0.782246] NetLabel:  domain hash size = 128
[    0.782249] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.782272] NetLabel:  unlabeled traffic allowed by default
[    0.782359] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.782374] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.784406] Switching to clocksource hpet
[    0.786774] Switched to NOHz mode on CPU #0
[    0.786911] Switched to NOHz mode on CPU #2
[    0.786937] Switched to NOHz mode on CPU #1
[    0.786988] Switched to NOHz mode on CPU #3
[    0.797497] AppArmor: AppArmor Filesystem Enabled
[    0.797544] pnp: PnP ACPI init
[    0.797571] ACPI: bus type pnp registered
[    0.798233] pnp 00:00: [bus 00-3e]
[    0.798240] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.798245] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.798250] pnp 00:00: [io  0x0d00-0xffff window]
[    0.798255] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.798260] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.798265] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.798270] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.798274] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.798279] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.798284] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.798289] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.798294] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.798299] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.798303] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.798308] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.798313] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.798318] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.798323] pnp 00:00: [mem 0xdfa00000-0xfeafffff window]
[    0.798328] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.798473] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.798509] pnp 00:01: [io  0x0000-0x001f]
[    0.798514] pnp 00:01: [io  0x0081-0x0091]
[    0.798518] pnp 00:01: [io  0x0093-0x009f]
[    0.798522] pnp 00:01: [io  0x00c0-0x00df]
[    0.798527] pnp 00:01: [dma 4]
[    0.798576] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.798597] pnp 00:02: [mem 0xff000000-0xffffffff]
[    0.798638] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.798817] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.798861] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.798891] pnp 00:04: [io  0x002e-0x002f]
[    0.798895] pnp 00:04: [io  0x004e-0x004f]
[    0.798899] pnp 00:04: [io  0x0061]
[    0.798903] pnp 00:04: [io  0x0063]
[    0.798907] pnp 00:04: [io  0x0065]
[    0.798910] pnp 00:04: [io  0x0067]
[    0.798914] pnp 00:04: [io  0x0070]
[    0.798918] pnp 00:04: [io  0x0080]
[    0.798921] pnp 00:04: [io  0x0092]
[    0.798926] pnp 00:04: [io  0x00b2-0x00b3]
[    0.798930] pnp 00:04: [io  0x0680-0x069f]
[    0.798934] pnp 00:04: [io  0x1000-0x100f]
[    0.798938] pnp 00:04: [io  0xffff]
[    0.798942] pnp 00:04: [io  0xffff]
[    0.798946] pnp 00:04: [io  0x0400-0x0453]
[    0.798950] pnp 00:04: [io  0x0458-0x047f]
[    0.798954] pnp 00:04: [io  0x0500-0x057f]
[    0.798958] pnp 00:04: [io  0x164e-0x164f]
[    0.799052] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.799058] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.799064] system 00:04: [io  0xffff] has been reserved
[    0.799069] system 00:04: [io  0xffff] has been reserved
[    0.799075] system 00:04: [io  0x0400-0x0453] has been reserved
[    0.799080] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.799086] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.799091] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.799099] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.799119] pnp 00:05: [io  0x0070-0x0077]
[    0.799137] pnp 00:05: [irq 8]
[    0.799191] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.799256] pnp 00:06: [io  0x0454-0x0457]
[    0.799327] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.799334] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.799354] pnp 00:07: [io  0x00f0-0x00ff]
[    0.799365] pnp 00:07: [irq 13]
[    0.799415] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.799453] pnp 00:08: [io  0x0010-0x001f]
[    0.799457] pnp 00:08: [io  0x0022-0x003f]
[    0.799461] pnp 00:08: [io  0x0044-0x005f]
[    0.799465] pnp 00:08: [io  0x0068-0x006f]
[    0.799469] pnp 00:08: [io  0x0072-0x007f]
[    0.799473] pnp 00:08: [io  0x0080]
[    0.799477] pnp 00:08: [io  0x0084-0x0086]
[    0.799481] pnp 00:08: [io  0x0088]
[    0.799485] pnp 00:08: [io  0x008c-0x008e]
[    0.799489] pnp 00:08: [io  0x0090-0x009f]
[    0.799493] pnp 00:08: [io  0x00a2-0x00bf]
[    0.799497] pnp 00:08: [io  0x00e0-0x00ef]
[    0.799501] pnp 00:08: [io  0x04d0-0x04d1]
[    0.799509] pnp 00:08: [mem 0xfe800000-0xfe802fff]
[    0.799589] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.799597] system 00:08: [mem 0xfe800000-0xfe802fff] has been reserved
[    0.799604] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.799650] pnp 00:09: [irq 12]
[    0.799706] pnp 00:09: Plug and Play ACPI device, IDs DLL0502 SYN0600 SYN0002 PNP0f13 (active)
[    0.799739] pnp 00:0a: [io  0x0060]
[    0.799743] pnp 00:0a: [io  0x0064]
[    0.799747] pnp 00:0a: [io  0x0062]
[    0.799751] pnp 00:0a: [io  0x0066]
[    0.799760] pnp 00:0a: [irq 1]
[    0.799807] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.800260] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
[    0.800265] pnp 00:0b: [mem 0xfed10000-0xfed17fff]
[    0.800270] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
[    0.800274] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
[    0.800279] pnp 00:0b: [mem 0xf8000000-0xfbffffff]
[    0.800283] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
[    0.800287] pnp 00:0b: [mem 0xfed90000-0xfed93fff]
[    0.800292] pnp 00:0b: [mem 0xfed45000-0xfed8ffff]
[    0.800296] pnp 00:0b: [mem 0xff000000-0xffffffff]
[    0.800301] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
[    0.800305] pnp 00:0b: [mem 0xdfa00000-0xdfa00fff]
[    0.800420] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.800427] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.800433] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.800439] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.800445] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.800451] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.800457] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.800463] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.800469] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    0.800475] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.800481] system 00:0b: [mem 0xdfa00000-0xdfa00fff] has been reserved
[    0.800489] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.800811] pnp 00:0c: [mem 0x20000000-0x201fffff]
[    0.800816] pnp 00:0c: [mem 0x40000000-0x401fffff]
[    0.800966] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
[    0.800972] system 00:0c: [mem 0x40000000-0x401fffff] has been reserved
[    0.800980] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.801099] pnp: PnP ACPI: found 13 devices
[    0.801103] ACPI: ACPI bus type pnp unregistered
[    0.808475] PCI: max bus depth: 1 pci_try_num: 2
[    0.808548] pci 0000:00:1c.0: PCI bridge to [bus 03-04]
[    0.808552] pci 0000:00:1c.0:   bridge window [io  disabled]
[    0.808563] pci 0000:00:1c.0:   bridge window [mem disabled]
[    0.808572] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    0.808586] pci 0000:00:1c.1: PCI bridge to [bus 05-06]
[    0.808593] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.808604] pci 0000:00:1c.1:   bridge window [mem disabled]
[    0.808614] pci 0000:00:1c.1:   bridge window [mem 0xf1100000-0xf11fffff 64bit pref]
[    0.808628] pci 0000:00:1c.3: PCI bridge to [bus 09-0a]
[    0.808632] pci 0000:00:1c.3:   bridge window [io  disabled]
[    0.808643] pci 0000:00:1c.3:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.808652] pci 0000:00:1c.3:   bridge window [mem pref disabled]
[    0.808665] pci 0000:00:1c.7: PCI bridge to [bus 11-1f]
[    0.808673] pci 0000:00:1c.7:   bridge window [io  0xc000-0xdfff]
[    0.808684] pci 0000:00:1c.7:   bridge window [mem 0xf6c00000-0xf7cfffff]
[    0.808695] pci 0000:00:1c.7:   bridge window [mem 0xf0000000-0xf10fffff 64bit pref]
[    0.808736] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.808747] pci 0000:00:1c.0: setting latency timer to 64
[    0.808769] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.808778] pci 0000:00:1c.1: setting latency timer to 64
[    0.808798] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.808807] pci 0000:00:1c.3: setting latency timer to 64
[    0.808837] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.808847] pci 0000:00:1c.7: setting latency timer to 64
[    0.808857] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.808862] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.808868] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.808873] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.808878] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.808883] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
[    0.808888] pci_bus 0000:00: resource 10 [mem 0x000e0000-0x000e3fff]
[    0.808893] pci_bus 0000:00: resource 11 [mem 0x000e4000-0x000e7fff]
[    0.808898] pci_bus 0000:00: resource 12 [mem 0xdfa00000-0xfeafffff]
[    0.808904] pci_bus 0000:00: resource 13 [mem 0xfed40000-0xfed44fff]
[    0.808909] pci_bus 0000:05: resource 0 [io  0xe000-0xefff]
[    0.808915] pci_bus 0000:05: resource 2 [mem 0xf1100000-0xf11fffff 64bit pref]
[    0.808921] pci_bus 0000:09: resource 1 [mem 0xf7d00000-0xf7dfffff]
[    0.808926] pci_bus 0000:11: resource 0 [io  0xc000-0xdfff]
[    0.808931] pci_bus 0000:11: resource 1 [mem 0xf6c00000-0xf7cfffff]
[    0.808937] pci_bus 0000:11: resource 2 [mem 0xf0000000-0xf10fffff 64bit pref]
[    0.809002] NET: Registered protocol family 2
[    0.809384] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.811885] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.815607] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.815927] TCP: Hash tables configured (established 524288 bind 65536)
[    0.815932] TCP reno registered
[    0.815959] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.816011] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.816197] NET: Registered protocol family 1
[    0.816224] pci 0000:00:02.0: Boot video device
[    1.056499] PCI: CLS 64 bytes, default 64
[    1.056505] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.056511] Placing 64MB software IO TLB between ffff8800d64ea000 - ffff8800da4ea000
[    1.056516] software IO TLB at phys 0xd64ea000 - 0xda4ea000
[    1.057492] audit: initializing netlink socket (disabled)
[    1.057511] type=2000 audit(1331410231.876:1): initialized
[    1.126872] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.149653] VFS: Disk quotas dquot_6.5.2
[    1.149782] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.151046] fuse init (API version 7.16)
[    1.151242] msgmni has been set to 7693
[    1.152010] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.152066] io scheduler noop registered
[    1.152074] io scheduler deadline registered
[    1.152167] io scheduler cfq registered (default)
[    1.152662] pcieport 0000:00:1c.7: setting latency timer to 64
[    1.152764] pcieport 0000:00:1c.7: irq 40 for MSI/MSI-X
[    1.152938] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.153023] pciehp 0000:00:1c.7:pcie04: HPC vendor_id 8086 device_id 1c1e ss_vid 1028 ss_did 502
[    1.153094] pciehp 0000:00:1c.7:pcie04: service driver pciehp loaded
[    1.153108] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.153186] intel_idle: MWAIT substates: 0x21120
[    1.153190] intel_idle: v0.4 model 0x2A
[    1.153193] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.153384] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.153488] ACPI: AC Adapter [AC] (on-line)
[    1.153728] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.155088] ACPI: Lid Switch [LID0]
[    1.155178] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.155188] ACPI: Power Button [PWRB]
[    1.155262] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.155270] ACPI: Sleep Button [SBTN]
[    1.155345] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.155351] ACPI: Power Button [PWRF]
[    1.155410] ACPI: acpi_idle yielding to intel_idle
[    1.169017] thermal LNXTHERM:00: registered as thermal_zone0
[    1.169023] ACPI: Thermal Zone [THM] (56 C)
[    1.169077] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.169107] ERST: Table is not found!
[    1.169235] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.217628] ACPI: Battery Slot [BAT0] (battery present)
[    1.749287] Freeing initrd memory: 19980k freed
[    1.839957] Linux agpgart interface v0.103
[    1.840135] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.840522] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.843971] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.844173] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.846257] brd: module loaded
[    1.847235] loop: module loaded
[    1.848074] Fixed MDIO Bus: probed
[    1.848117] PPP generic driver version 2.4.2
[    1.848186] tun: Universal TUN/TAP device driver, 1.6
[    1.848190] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.848329] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.848363] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.848400] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.848408] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.848477] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.848523] ehci_hcd 0000:00:1a.0: debug port 2
[    1.852397] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.852438] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7e08000
[    1.867256] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.867488] hub 1-0:1.0: USB hub found
[    1.867498] hub 1-0:1.0: 2 ports detected
[    1.867623] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.867654] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.867661] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.867742] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.867783] ehci_hcd 0000:00:1d.0: debug port 2
[    1.871654] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.871681] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7e07000
[    1.887224] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.887425] hub 2-0:1.0: USB hub found
[    1.887436] hub 2-0:1.0: 2 ports detected
[    1.887540] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.887562] uhci_hcd: USB Universal Host Controller Interface driver
[    1.887684] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2] at 0x60,0x64 irq 1,12
[    1.889822] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.889836] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.890054] mousedev: PS/2 mouse device common for all mice
[    1.890358] rtc_cmos 00:05: RTC can wake from S4
[    1.890503] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.890543] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.890747] device-mapper: uevent: version 1.0.3
[    1.890891] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.891135] cpuidle: using governor ladder
[    1.891539] cpuidle: using governor menu
[    1.891543] EFI Variables Facility v0.08 2004-May-17
[    1.891990] TCP cubic registered
[    1.892266] NET: Registered protocol family 10
[    1.893151] NET: Registered protocol family 17
[    1.893180] Registering the dns_resolver key type
[    1.893381] PM: Hibernation image not present or could not be loaded.
[    1.893406] registered taskstats version 1
[    1.911891] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.917752]   Magic number: 4:470:194
[    1.917883] rtc_cmos 00:05: setting system clock to 2012-03-10 20:10:33 UTC (1331410233)
[    1.919516] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.919518] EDD information not available.
[    1.920712] Freeing unused kernel memory: 988k freed
[    1.920810] Write protecting the kernel read-only data: 12288k
[    1.925221] Freeing unused kernel memory: 2032k freed
[    1.928367] Freeing unused kernel memory: 1388k freed
[    1.940952] udevd[90]: starting version 173
[    1.958040] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.958078] r8169 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.958126] r8169 0000:05:00.0: setting latency timer to 64
[    1.958197] r8169 0000:05:00.0: irq 41 for MSI/MSI-X
[    1.958593] r8169 0000:05:00.0: eth0: RTL8105e at 0xffffc9000065c000, d0:67:e5:f5:ac:e2, XID 00a00000 IRQ 41
[    1.963982] ahci 0000:00:1f.2: version 3.0
[    1.963999] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.964056] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.964093] ahci: SSS flag set, parallel bus scan disabled
[    1.973650] [drm] Initialized drm 1.1.0 20060810
[    1.974176] wmi: Mapper loaded
[    1.979107] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x11 impl SATA mode
[    1.979112] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems apst 
[    1.979119] ahci 0000:00:1f.2: setting latency timer to 64
[    1.987788] scsi0 : ahci
[    1.987979] scsi1 : ahci
[    1.988050] scsi2 : ahci
[    1.988113] scsi3 : ahci
[    1.988180] scsi4 : ahci
[    1.988236] scsi5 : ahci
[    1.988565] ata1: SATA max UDMA/133 abar m2048@0xf7e06000 port 0xf7e06100 irq 42
[    1.988567] ata2: DUMMY
[    1.988569] ata3: DUMMY
[    1.988570] ata4: DUMMY
[    1.988573] ata5: SATA max UDMA/133 abar m2048@0xf7e06000 port 0xf7e06300 irq 42
[    1.988575] ata6: DUMMY
[    1.988640] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.988645] i915 0000:00:02.0: setting latency timer to 64
[    2.044830] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[    2.044835] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.044836] [drm] Driver supports precise vblank timestamp query.
[    2.044862] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.054972] Refined TSC clocksource calibration: 2394.561 MHz.
[    2.054976] Switching to clocksource tsc
[    2.214780] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    2.234582] fbcon: inteldrmfb (fb0) is primary device
[    2.235012] Console: switching to colour frame buffer device 170x48
[    2.235025] fb0: inteldrmfb frame buffer device
[    2.235026] drm: registered panic notifier
[    2.263454] acpi device:33: registered as cooling_device4
[    2.263590] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    2.263616] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.263635] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.306644] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.308795] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.309216] ata1.00: ATA-8: ST9500325AS, D005DEM1, max UDMA/133
[    2.309225] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.311762] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.312151] ata1.00: configured for UDMA/133
[    2.312314] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      D005 PQ: 0 ANSI: 5
[    2.312445] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.312448] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.312505] sd 0:0:0:0: [sda] Write Protect is off
[    2.312508] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.312544] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.336229]  sda: sda1 sda2 sda3 < sda5 >
[    2.336570] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.347317] hub 1-1:1.0: USB hub found
[    2.347408] hub 1-1:1.0: 6 ports detected
[    2.458428] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    2.590952] hub 2-1:1.0: USB hub found
[    2.591045] hub 2-1:1.0: 8 ports detected
[    2.630161] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.634304] ata5.00: ATAPI: TSSTcorp DVD+/-RW SN-208BB, D100, max UDMA/100
[    2.640586] ata5.00: configured for UDMA/100
[    2.654166] scsi 4:0:0:0: CD-ROM            TSSTcorp DVD+-RW SN-208BB D100 PQ: 0 ANSI: 5
[    2.662271] usb 1-1.4: new full speed USB device number 3 using ehci_hcd
[    2.668421] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.668430] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.668562] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.668598] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    2.837962] usb 1-1.5: new high speed USB device number 4 using ehci_hcd
[  226.978494] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[  237.099640] udevd[441]: starting version 173
[  237.133535] Adding 5857276k swap on /dev/mapper/gr1-swap.  Priority:-1 extents:1 across:5857276k 
[  237.133950] lp: driver loaded but no devices found
[  237.149605] mei: module is from the staging directory, the quality is unknown, you have been warned.
[  237.150506] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  237.150515] mei 0000:00:16.0: setting latency timer to 64
[  237.220263] cfg80211: Calling CRDA to update world regulatory domain
[  237.224967] Bluetooth: Core ver 2.16
[  237.224988] NET: Registered protocol family 31
[  237.224990] Bluetooth: HCI device and connection manager initialized
[  237.224992] Bluetooth: HCI socket layer initialized
[  237.224993] Bluetooth: L2CAP socket layer initialized
[  237.226614] Bluetooth: SCO socket layer initialized
[  237.228633] Bluetooth: Generic Bluetooth USB driver ver 0.6
[  237.229386] type=1400 audit(1331410469.157:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=686 comm="apparmor_parser"
[  237.229703] type=1400 audit(1331410469.157:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=686 comm="apparmor_parser"
[  237.229717] ath9k 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  237.229730] ath9k 0000:09:00.0: setting latency timer to 64
[  237.229910] type=1400 audit(1331410469.157:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=686 comm="apparmor_parser"
[  237.238868] usbcore: registered new interface driver btusb
[  237.267760] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[  237.276597] Linux video capture interface: v2.00
[  237.277097] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:643e)
[  237.279799] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  237.279859] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[  237.279888] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  237.292580] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input6
[  237.294109] ath: EEPROM regdomain: 0x60
[  237.294111] ath: EEPROM indicates we should expect a direct regpair map
[  237.294114] ath: Country alpha2 being used: 00
[  237.294115] ath: Regpair used: 0x60
[  237.294118] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  237.294121] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  237.294122] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  237.294125] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  237.294127] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  237.294129] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  237.294131] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  237.294133] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  237.294135] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  237.294137] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  237.294139] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  237.294141] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  237.294143] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  237.294146] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  237.294147] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  237.294150] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  237.294151] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  237.294154] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  237.294156] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  237.294158] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  237.294160] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  237.294162] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  237.294164] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  237.294167] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  237.294169] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  237.294171] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  237.294173] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  237.294175] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  237.294381] usbcore: registered new interface driver uvcvideo
[  237.294383] USB Video Class driver (v1.1.0)
[  237.295608] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
[  237.295621] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  237.297688] input: Dell WMI hotkeys as /devices/virtual/input/input7
[  237.309453] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[  237.310277] Registered led device: ath9k-phy0
[  237.310286] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc900050a0000, irq=19
[  237.371822] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  237.371826] cfg80211: World regulatory domain updated:
[  237.371828] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  237.371831] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  237.371834] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  237.371836] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  237.371844] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  237.371846] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  237.488291] alps.c: Enabled hardware quirk, falling back to psmouse-core
[  237.501029] input: ImPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[  237.844591] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[  237.844753] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[  237.844837] input: HDA Intel PCH Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[  237.844903] input: HDA Intel PCH HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[  238.235305] hci_cmd_timer: hci0 command tx timeout
[  238.844076] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[  238.962915] EXT4-fs (dm-3): mounted filesystem with ordered data mode. Opts: (null)
[  239.233817] hci_cmd_timer: hci0 command tx timeout
[  239.347250] EXT4-fs (dm-4): mounted filesystem with ordered data mode. Opts: (null)
[  239.493719] type=1400 audit(1331410471.425:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1057 comm="apparmor_parser"
[  239.493923] type=1400 audit(1331410471.425:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1058 comm="apparmor_parser"
[  239.494253] type=1400 audit(1331410471.425:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1058 comm="apparmor_parser"
[  239.494458] type=1400 audit(1331410471.425:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1058 comm="apparmor_parser"
[  239.496042] type=1400 audit(1331410471.425:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1061 comm="apparmor_parser"
[  239.496412] type=1400 audit(1331410471.425:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1061 comm="apparmor_parser"
[  239.496954] type=1400 audit(1331410471.425:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1062 comm="apparmor_parser"
[  239.523031] ppdev: user-space parallel port driver
[  239.614798] init: failsafe main process (1013) killed by TERM signal
[  239.615774] init: apport pre-start process (1127) terminated with status 1
[  239.623114] init: apport post-stop process (1155) terminated with status 1
[  239.879793] r8169 0000:05:00.0: eth0: link down
[  239.880039] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  239.921858] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  239.970242] Bluetooth: RFCOMM TTY layer initialized
[  239.970246] Bluetooth: RFCOMM socket layer initialized
[  239.970248] Bluetooth: RFCOMM ver 1.11
[  239.971061] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  239.971064] Bluetooth: BNEP filters: protocol multicast
[  240.232330] hci_cmd_timer: hci0 command tx timeout
[  241.230827] hci_cmd_timer: hci0 command tx timeout
[  241.433118] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro,commit=0
[  241.654146] EXT4-fs (sda2): re-mounted. Opts: commit=0
[  241.662426] EXT4-fs (dm-3): re-mounted. Opts: commit=0
[  241.664020] EXT4-fs (dm-4): re-mounted. Opts: commit=0
[  241.995718] init: plymouth-stop pre-start process (1528) terminated with status 1
[  242.229360] hci_cmd_timer: hci0 command tx timeout
[  242.863112] wlan0: authenticate with 5c:d9:98:74:bc:0e (try 1)
[  242.865454] wlan0: authenticated
[  242.895285] wlan0: associate with 5c:d9:98:74:bc:0e (try 1)
[  242.898097] wlan0: RX AssocResp from 5c:d9:98:74:bc:0e (capab=0x411 status=0 aid=1)
[  242.898104] wlan0: associated
[  242.898560] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  243.227872] hci_cmd_timer: hci0 command tx timeout
[  244.226387] hci_cmd_timer: hci0 command tx timeout
[  245.224900] hci_cmd_timer: hci0 command tx timeout
[  246.223516] hci_cmd_timer: hci0 command tx timeout
[  247.222022] hci_cmd_timer: hci0 command tx timeout
[  248.220419] hci_cmd_timer: hci0 command tx timeout
[  249.218939] hci_cmd_timer: hci0 command tx timeout
[  250.217442] hci_cmd_timer: hci0 command tx timeout
[  251.215967] hci_cmd_timer: hci0 command tx timeout
[  252.214479] hci_cmd_timer: hci0 command tx timeout
[  253.193035] wlan0: no IPv6 routers present
[  253.212989] hci_cmd_timer: hci0 command tx timeout
[  254.211425] hci_cmd_timer: hci0 command tx timeout
[  255.209436] hci_cmd_timer: hci0 command tx timeout
[  256.207455] hci_cmd_timer: hci0 command tx timeout
[  257.205466] hci_cmd_timer: hci0 command tx timeout
[  258.203562] hci_cmd_timer: hci0 command tx timeout
```With forced memory:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-16-generic (buildd@roseapple) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 (Ubuntu 3.0.0-16.29-generic 3.0.20)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.0.0-16-generic root=/dev/mapper/gr1-root mem=4096M ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000da4ea000 (usable)
[    0.000000]  BIOS-e820: 00000000da4ea000 - 00000000da52d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000da52d000 - 00000000da798000 (usable)
[    0.000000]  BIOS-e820: 00000000da798000 - 00000000da967000 (reserved)
[    0.000000]  BIOS-e820: 00000000da967000 - 00000000dacbc000 (usable)
[    0.000000]  BIOS-e820: 00000000dacbc000 - 00000000dad68000 (reserved)
[    0.000000]  BIOS-e820: 00000000dad68000 - 00000000dafe8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dafe8000 - 00000000db000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000db800000 - 00000000dfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000011fe00000 (usable)
[    0.000000] e820 remove range: 0000000100000000 - ffffffffffffffff (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] user-defined physical RAM map:
[    0.000000]  user: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  user: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  user: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  user: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  user: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  user: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  user: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  user: 0000000040200000 - 00000000da4ea000 (usable)
[    0.000000]  user: 00000000da4ea000 - 00000000da52d000 (ACPI NVS)
[    0.000000]  user: 00000000da52d000 - 00000000da798000 (usable)
[    0.000000]  user: 00000000da798000 - 00000000da967000 (reserved)
[    0.000000]  user: 00000000da967000 - 00000000dacbc000 (usable)
[    0.000000]  user: 00000000dacbc000 - 00000000dad68000 (reserved)
[    0.000000]  user: 00000000dad68000 - 00000000dafe8000 (ACPI NVS)
[    0.000000]  user: 00000000dafe8000 - 00000000db000000 (ACPI data)
[    0.000000]  user: 00000000db800000 - 00000000dfa00000 (reserved)
[    0.000000]  user: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  user: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  user: 00000000fed00000 - 00000000fed04000 (reserved)
[    0.000000]  user: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  user: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  user: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Dell Inc. Inspiron N4050/0X0DC1, BIOS A06 11/14/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0xdacbc max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FE0000000 write-back
[    0.000000]   2 base 0DB800000 mask FFF800000 uncachable
[    0.000000]   3 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   5 base 11FE00000 mask FFFE00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 4, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 5, base: 4606MB, range: 2MB, type UC
[    0.000000] total RAM covered: 4022M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 7      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 4, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 5, base: 4GB, range: 512MB, type WB
[    0.000000] reg 6, base: 4606MB, range: 2MB, type UC
[    0.000000] e820 update range: 00000000db800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [ffff8800000fd1b0] fd1b0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000dacbc000
[    0.000000]  0000000000 - 00dac00000 page 2M
[    0.000000]  00dac00000 - 00dacbc000 page 4k
[    0.000000] kernel direct mapping tables up to dacbc000 @ 1fffa000-20000000
[    0.000000] RAMDISK: 358ea000 - 36c6d000
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v02   DELL)
[    0.000000] ACPI: XSDT 00000000dafe8078 0006C (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000daff1c38 000F4 (v04   DELL     WN09 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000dafe8170 09AC8 (v02   DELL     WN09 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000dafe4f80 00040
[    0.000000] ACPI: APIC 00000000daff1d30 00072 (v03   DELL     WN09 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000daff1da8 0003C (v01   DELL     WN09 01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000daff1de8 004B0 (v01 TrmRef PtidDevc 00001000 INTL 20091112)
[    0.000000] ACPI: SLIC 00000000daff2298 00176 (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: HPET 00000000daff2410 00038 (v01   DELL     WN09 01072009 AMI. 00000004)
[    0.000000] ACPI: SSDT 00000000daff2448 007C2 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000daff2c10 00996 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: OSFR 00000000daff35a8 0008C (v01 DELL    M08     07DB0B0E ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000000dacbc000
[    0.000000] Initmem setup node 0 0000000000000000-00000000dacbc000
[    0.000000]   NODE_DATA [00000000dacb7000 - 00000000dacbbfff]
[    0.000000]  [ffffea0000000000-ffffea00031fffff] PMD -> [ffff8800d6400000-ffff8800d95fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000da4ea
[    0.000000]     0: 0x000da52d -> 0x000da798
[    0.000000]     0: 0x000da967 -> 0x000dacbc
[    0.000000] On node 0 totalpages: 894519
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3920 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12197 pages used for memmap
[    0.000000]   DMA32 zone: 878341 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
[    0.000000] PM: Registered nosave memory: 00000000da4ea000 - 00000000da52d000
[    0.000000] PM: Registered nosave memory: 00000000da798000 - 00000000da967000
[    0.000000] Allocating PCI resources starting at dfa00000 (gap: dfa00000:18600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff8800daa00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 882261
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.0-16-generic root=/dev/mapper/gr1-root mem=4096M ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3490836k/3584752k available (6140k kernel code, 6676k absent, 87240k reserved, 6894k data, 988k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 29360128 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2394.647 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4789.29 BogoMIPS (lpj=9578588)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000025] Security Framework initialized
[    0.000037] AppArmor: AppArmor initialized
[    0.000038] Yama: becoming mindful.
[    0.000429] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001482] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001920] Mount-cache hash table entries: 256
[    0.002017] Initializing cgroup subsys cpuacct
[    0.002021] Initializing cgroup subsys memory
[    0.002027] Initializing cgroup subsys devices
[    0.002029] Initializing cgroup subsys freezer
[    0.002030] Initializing cgroup subsys net_cls
[    0.002032] Initializing cgroup subsys blkio
[    0.002037] Initializing cgroup subsys perf_event
[    0.002061] CPU: Physical Processor ID: 0
[    0.002062] CPU: Processor Core ID: 0
[    0.002066] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002067] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002070] mce: CPU supports 7 MCE banks
[    0.002081] CPU0: Thermal monitoring enabled (TM1)
[    0.002087] using mwait in idle threads.
[    0.004422] ACPI: Core revision 20110413
[    0.014401] ftrace: allocating 25748 entries in 101 pages
[    0.041511] x2apic not enabled, IRQ remapping init failed
[    0.041977] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.081611] CPU0: Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz stepping 07
[    0.187677] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.187693] ... version:                3
[    0.187696] ... bit width:              48
[    0.187699] ... generic registers:      4
[    0.187703] ... value mask:             0000ffffffffffff
[    0.187707] ... max period:             000000007fffffff
[    0.187710] ... fixed-purpose events:   3
[    0.187713] ... event mask:             000000070000000f
[    0.188714] Booting Node   0, Processors  #1
[    0.188721] smpboot cpu 1: start_ip = 98000
[    0.299807]  #2
[    0.299811] smpboot cpu 2: start_ip = 98000
[    0.407649]  #3 Ok.
[    0.407654] smpboot cpu 3: start_ip = 98000
[    0.515306] Brought up 4 CPUs
[    0.515312] Total of 4 processors activated (19156.25 BogoMIPS).
[    0.521944] devtmpfs: initialized
[    0.522247] PM: Registering ACPI NVS region at da4ea000 (274432 bytes)
[    0.522264] PM: Registering ACPI NVS region at dad68000 (2621440 bytes)
[    0.526010] print_constraints: dummy: 
[    0.526051] Time: 20:02:10  Date: 03/10/12
[    0.526122] NET: Registered protocol family 16
[    0.526340] Trying to unpack rootfs image as initramfs...
[    0.526367] ACPI: bus type pci registered
[    0.526491] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.526499] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.563675] PCI: Using configuration type 1 for base access
[    0.565416] bio: create slab <bio-0> at 0
[    0.569517] ACPI: EC: Look up EC in DSDT
[    0.573720] ACPI: Executed 1 blocks of module-level executable AML code
[    0.583107] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.619145] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.620064] ACPI: SSDT 00000000dad51698 0064F (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.621080] ACPI: Dynamic OEM Table Load:
[    0.621088] ACPI: SSDT           (null) 0064F (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.643594] ACPI: SSDT 00000000dad52a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.644678] ACPI: Dynamic OEM Table Load:
[    0.644685] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.675180] ACPI: SSDT 00000000dad50d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.676173] ACPI: Dynamic OEM Table Load:
[    0.676179] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.708242] ACPI: Interpreter enabled
[    0.708250] ACPI: (supports S0 S1 S3 S4 S5)
[    0.708316] ACPI: Using IOAPIC for interrupt routing
[    0.746853] ACPI: No dock devices found.
[    0.746860] HEST: Table not found.
[    0.746866] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.747704] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.748871] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.748878] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.748884] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.748890] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.748895] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.748901] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.748906] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.748911] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.748918] pci_root PNP0A08:00: host bridge window [mem 0xdfa00000-0xfeafffff]
[    0.748923] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    0.748954] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    0.749045] pci 0000:00:02.0: [8086:0116] type 0 class 0x000300
[    0.749073] pci 0000:00:02.0: reg 10: [mem 0xf6800000-0xf6bfffff 64bit]
[    0.749091] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.749103] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    0.749236] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    0.749285] pci 0000:00:16.0: reg 10: [mem 0xf7e0a000-0xf7e0a00f 64bit]
[    0.749442] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.749452] pci 0000:00:16.0: PME# disabled
[    0.749519] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    0.749563] pci 0000:00:1a.0: reg 10: [mem 0xf7e08000-0xf7e083ff]
[    0.749749] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.749758] pci 0000:00:1a.0: PME# disabled
[    0.749807] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    0.749842] pci 0000:00:1b.0: reg 10: [mem 0xf7e00000-0xf7e03fff 64bit]
[    0.749996] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.750005] pci 0000:00:1b.0: PME# disabled
[    0.750047] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    0.750216] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.750224] pci 0000:00:1c.0: PME# disabled
[    0.750271] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    0.750441] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.750449] pci 0000:00:1c.1: PME# disabled
[    0.750498] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
[    0.750667] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.750676] pci 0000:00:1c.3: PME# disabled
[    0.750734] pci 0000:00:1c.7: [8086:1c1e] type 1 class 0x000604
[    0.750913] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.750922] pci 0000:00:1c.7: PME# disabled
[    0.750981] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    0.751025] pci 0000:00:1d.0: reg 10: [mem 0xf7e07000-0xf7e073ff]
[    0.751211] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.751220] pci 0000:00:1d.0: PME# disabled
[    0.751267] pci 0000:00:1f.0: [8086:1c4b] type 0 class 0x000601
[    0.751513] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    0.751558] pci 0000:00:1f.2: reg 10: [io  0xf0b0-0xf0b7]
[    0.751577] pci 0000:00:1f.2: reg 14: [io  0xf0a0-0xf0a3]
[    0.751596] pci 0000:00:1f.2: reg 18: [io  0xf090-0xf097]
[    0.751615] pci 0000:00:1f.2: reg 1c: [io  0xf080-0xf083]
[    0.751634] pci 0000:00:1f.2: reg 20: [io  0xf060-0xf07f]
[    0.751654] pci 0000:00:1f.2: reg 24: [mem 0xf7e06000-0xf7e067ff]
[    0.751762] pci 0000:00:1f.2: PME# supported from D3hot
[    0.751770] pci 0000:00:1f.2: PME# disabled
[    0.751807] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    0.751842] pci 0000:00:1f.3: reg 10: [mem 0xf7e05000-0xf7e050ff 64bit]
[    0.751891] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    0.752044] pci 0000:00:1c.0: PCI bridge to [bus 03-04]
[    0.752054] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.752064] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.752078] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.752208] pci 0000:05:00.0: [10ec:8136] type 0 class 0x000200
[    0.752242] pci 0000:05:00.0: reg 10: [io  0xe000-0xe0ff]
[    0.752301] pci 0000:05:00.0: reg 18: [mem 0xf1104000-0xf1104fff 64bit pref]
[    0.752339] pci 0000:05:00.0: reg 20: [mem 0xf1100000-0xf1103fff 64bit pref]
[    0.752493] pci 0000:05:00.0: supports D1 D2
[    0.752498] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.752508] pci 0000:05:00.0: PME# disabled
[    0.758834] pci 0000:00:1c.1: PCI bridge to [bus 05-06]
[    0.758844] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.758854] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.758868] pci 0000:00:1c.1:   bridge window [mem 0xf1100000-0xf11fffff 64bit pref]
[    0.758999] pci 0000:09:00.0: [168c:002b] type 0 class 0x000280
[    0.759046] pci 0000:09:00.0: reg 10: [mem 0xf7d00000-0xf7d0ffff 64bit]
[    0.759263] pci 0000:09:00.0: supports D1
[    0.759268] pci 0000:09:00.0: PME# supported from D0 D1 D3hot
[    0.759278] pci 0000:09:00.0: PME# disabled
[    0.766812] pci 0000:00:1c.3: PCI bridge to [bus 09-0a]
[    0.766822] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
[    0.766831] pci 0000:00:1c.3:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.766845] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.766947] pci 0000:00:1c.7: PCI bridge to [bus 11-1f]
[    0.766958] pci 0000:00:1c.7:   bridge window [io  0xc000-0xdfff]
[    0.766967] pci 0000:00:1c.7:   bridge window [mem 0xf6c00000-0xf7cfffff]
[    0.766982] pci 0000:00:1c.7:   bridge window [mem 0xf0000000-0xf10fffff 64bit pref]
[    0.767031] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.767357] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.767443] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.767541] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.767639] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08._PRT]
[    0.767972]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.768448]  pci0000:00: ACPI _OSC control (0x19) granted
[    0.776249] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.776363] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.776473] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.776583] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.776688] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.776795] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.776902] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.777011] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.777221] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.777238] vgaarb: loaded
[    0.777241] vgaarb: bridge control possible 0000:00:02.0
[    0.777605] SCSI subsystem initialized
[    0.777732] libata version 3.00 loaded.
[    0.777816] usbcore: registered new interface driver usbfs
[    0.777840] usbcore: registered new interface driver hub
[    0.777912] usbcore: registered new device driver usb
[    0.778100] PCI: Using ACPI for IRQ routing
[    0.781748] PCI: pci_cache_line_size set to 64 bytes
[    0.781873] reserve RAM buffer: 000000000009d400 - 000000000009ffff 
[    0.781879] reserve RAM buffer: 00000000da4ea000 - 00000000dbffffff 
[    0.781887] reserve RAM buffer: 00000000da798000 - 00000000dbffffff 
[    0.781894] reserve RAM buffer: 00000000dacbc000 - 00000000dbffffff 
[    0.782090] NetLabel: Initializing
[    0.782094] NetLabel:  domain hash size = 128
[    0.782097] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.782121] NetLabel:  unlabeled traffic allowed by default
[    0.782209] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.782223] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.784257] Switching to clocksource hpet
[    0.786768] Switched to NOHz mode on CPU #0
[    0.786908] Switched to NOHz mode on CPU #3
[    0.786925] Switched to NOHz mode on CPU #2
[    0.786932] Switched to NOHz mode on CPU #1
[    0.797189] AppArmor: AppArmor Filesystem Enabled
[    0.797236] pnp: PnP ACPI init
[    0.797263] ACPI: bus type pnp registered
[    0.797920] pnp 00:00: [bus 00-3e]
[    0.797927] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.797932] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.797936] pnp 00:00: [io  0x0d00-0xffff window]
[    0.797942] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.797947] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.797952] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.797956] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.797961] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.797966] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.797979] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.797984] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.797988] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.797993] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.797998] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.798003] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.798007] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.798012] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.798017] pnp 00:00: [mem 0xdfa00000-0xfeafffff window]
[    0.798023] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.798170] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.798201] pnp 00:01: [io  0x0000-0x001f]
[    0.798205] pnp 00:01: [io  0x0081-0x0091]
[    0.798209] pnp 00:01: [io  0x0093-0x009f]
[    0.798213] pnp 00:01: [io  0x00c0-0x00df]
[    0.798218] pnp 00:01: [dma 4]
[    0.798268] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.798288] pnp 00:02: [mem 0xff000000-0xffffffff]
[    0.798330] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.798507] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.798551] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.798580] pnp 00:04: [io  0x002e-0x002f]
[    0.798585] pnp 00:04: [io  0x004e-0x004f]
[    0.798589] pnp 00:04: [io  0x0061]
[    0.798592] pnp 00:04: [io  0x0063]
[    0.798596] pnp 00:04: [io  0x0065]
[    0.798600] pnp 00:04: [io  0x0067]
[    0.798603] pnp 00:04: [io  0x0070]
[    0.798607] pnp 00:04: [io  0x0080]
[    0.798611] pnp 00:04: [io  0x0092]
[    0.798615] pnp 00:04: [io  0x00b2-0x00b3]
[    0.798619] pnp 00:04: [io  0x0680-0x069f]
[    0.798623] pnp 00:04: [io  0x1000-0x100f]
[    0.798627] pnp 00:04: [io  0xffff]
[    0.798631] pnp 00:04: [io  0xffff]
[    0.798635] pnp 00:04: [io  0x0400-0x0453]
[    0.798639] pnp 00:04: [io  0x0458-0x047f]
[    0.798643] pnp 00:04: [io  0x0500-0x057f]
[    0.798647] pnp 00:04: [io  0x164e-0x164f]
[    0.798742] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.798748] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.798754] system 00:04: [io  0xffff] has been reserved
[    0.798759] system 00:04: [io  0xffff] has been reserved
[    0.798764] system 00:04: [io  0x0400-0x0453] has been reserved
[    0.798770] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.798775] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.798781] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.798789] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.798808] pnp 00:05: [io  0x0070-0x0077]
[    0.798828] pnp 00:05: [irq 8]
[    0.798871] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.798935] pnp 00:06: [io  0x0454-0x0457]
[    0.799009] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.799017] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.799037] pnp 00:07: [io  0x00f0-0x00ff]
[    0.799048] pnp 00:07: [irq 13]
[    0.799097] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.799135] pnp 00:08: [io  0x0010-0x001f]
[    0.799139] pnp 00:08: [io  0x0022-0x003f]
[    0.799147] pnp 00:08: [io  0x0044-0x005f]
[    0.799151] pnp 00:08: [io  0x0068-0x006f]
[    0.799155] pnp 00:08: [io  0x0072-0x007f]
[    0.799159] pnp 00:08: [io  0x0080]
[    0.799163] pnp 00:08: [io  0x0084-0x0086]
[    0.799167] pnp 00:08: [io  0x0088]
[    0.799171] pnp 00:08: [io  0x008c-0x008e]
[    0.799175] pnp 00:08: [io  0x0090-0x009f]
[    0.799179] pnp 00:08: [io  0x00a2-0x00bf]
[    0.799183] pnp 00:08: [io  0x00e0-0x00ef]
[    0.799187] pnp 00:08: [io  0x04d0-0x04d1]
[    0.799191] pnp 00:08: [mem 0xfe800000-0xfe802fff]
[    0.799271] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.799280] system 00:08: [mem 0xfe800000-0xfe802fff] has been reserved
[    0.799287] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.799328] pnp 00:09: [irq 12]
[    0.799383] pnp 00:09: Plug and Play ACPI device, IDs DLL0502 SYN0600 SYN0002 PNP0f13 (active)
[    0.799416] pnp 00:0a: [io  0x0060]
[    0.799420] pnp 00:0a: [io  0x0064]
[    0.799424] pnp 00:0a: [io  0x0062]
[    0.799427] pnp 00:0a: [io  0x0066]
[    0.799437] pnp 00:0a: [irq 1]
[    0.799484] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.799938] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
[    0.799943] pnp 00:0b: [mem 0xfed10000-0xfed17fff]
[    0.799948] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
[    0.799952] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
[    0.799956] pnp 00:0b: [mem 0xf8000000-0xfbffffff]
[    0.799961] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
[    0.799965] pnp 00:0b: [mem 0xfed90000-0xfed93fff]
[    0.799969] pnp 00:0b: [mem 0xfed45000-0xfed8ffff]
[    0.799974] pnp 00:0b: [mem 0xff000000-0xffffffff]
[    0.799978] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
[    0.799982] pnp 00:0b: [mem 0xdfa00000-0xdfa00fff]
[    0.800104] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.800111] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.800117] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.800123] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.800129] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.800135] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.800141] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.800147] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.800153] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    0.800159] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.800165] system 00:0b: [mem 0xdfa00000-0xdfa00fff] has been reserved
[    0.800173] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.800500] pnp 00:0c: [mem 0x20000000-0x201fffff]
[    0.800505] pnp 00:0c: [mem 0x40000000-0x401fffff]
[    0.800647] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
[    0.800654] system 00:0c: [mem 0x40000000-0x401fffff] has been reserved
[    0.800661] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.800779] pnp: PnP ACPI: found 13 devices
[    0.800783] ACPI: ACPI bus type pnp unregistered
[    0.808148] PCI: max bus depth: 1 pci_try_num: 2
[    0.808222] pci 0000:00:1c.0: PCI bridge to [bus 03-04]
[    0.808227] pci 0000:00:1c.0:   bridge window [io  disabled]
[    0.808237] pci 0000:00:1c.0:   bridge window [mem disabled]
[    0.808246] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    0.808260] pci 0000:00:1c.1: PCI bridge to [bus 05-06]
[    0.808268] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.808278] pci 0000:00:1c.1:   bridge window [mem disabled]
[    0.808288] pci 0000:00:1c.1:   bridge window [mem 0xf1100000-0xf11fffff 64bit pref]
[    0.808302] pci 0000:00:1c.3: PCI bridge to [bus 09-0a]
[    0.808306] pci 0000:00:1c.3:   bridge window [io  disabled]
[    0.808318] pci 0000:00:1c.3:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.808327] pci 0000:00:1c.3:   bridge window [mem pref disabled]
[    0.808340] pci 0000:00:1c.7: PCI bridge to [bus 11-1f]
[    0.808348] pci 0000:00:1c.7:   bridge window [io  0xc000-0xdfff]
[    0.808359] pci 0000:00:1c.7:   bridge window [mem 0xf6c00000-0xf7cfffff]
[    0.808370] pci 0000:00:1c.7:   bridge window [mem 0xf0000000-0xf10fffff 64bit pref]
[    0.808413] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.808424] pci 0000:00:1c.0: setting latency timer to 64
[    0.808445] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.808454] pci 0000:00:1c.1: setting latency timer to 64
[    0.808479] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.808489] pci 0000:00:1c.3: setting latency timer to 64
[    0.808503] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.808512] pci 0000:00:1c.7: setting latency timer to 64
[    0.808521] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.808539] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.808544] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.808549] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.808554] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.808560] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
[    0.808565] pci_bus 0000:00: resource 10 [mem 0x000e0000-0x000e3fff]
[    0.808570] pci_bus 0000:00: resource 11 [mem 0x000e4000-0x000e7fff]
[    0.808575] pci_bus 0000:00: resource 12 [mem 0xdfa00000-0xfeafffff]
[    0.808581] pci_bus 0000:00: resource 13 [mem 0xfed40000-0xfed44fff]
[    0.808587] pci_bus 0000:05: resource 0 [io  0xe000-0xefff]
[    0.808592] pci_bus 0000:05: resource 2 [mem 0xf1100000-0xf11fffff 64bit pref]
[    0.808598] pci_bus 0000:09: resource 1 [mem 0xf7d00000-0xf7dfffff]
[    0.808603] pci_bus 0000:11: resource 0 [io  0xc000-0xdfff]
[    0.808608] pci_bus 0000:11: resource 1 [mem 0xf6c00000-0xf7cfffff]
[    0.808614] pci_bus 0000:11: resource 2 [mem 0xf0000000-0xf10fffff 64bit pref]
[    0.808674] NET: Registered protocol family 2
[    0.809039] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.811470] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.815163] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.815495] TCP: Hash tables configured (established 524288 bind 65536)
[    0.815501] TCP reno registered
[    0.815525] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.815579] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.815773] NET: Registered protocol family 1
[    0.815800] pci 0000:00:02.0: Boot video device
[    1.056219] PCI: CLS 64 bytes, default 64
[    1.057175] audit: initializing netlink socket (disabled)
[    1.057202] type=2000 audit(1331409730.876:1): initialized
[    1.125450] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.146005] VFS: Disk quotas dquot_6.5.2
[    1.146128] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.147379] fuse init (API version 7.16)
[    1.147569] msgmni has been set to 6818
[    1.148342] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.148399] io scheduler noop registered
[    1.148406] io scheduler deadline registered
[    1.148499] io scheduler cfq registered (default)
[    1.148958] pcieport 0000:00:1c.7: setting latency timer to 64
[    1.149060] pcieport 0000:00:1c.7: irq 40 for MSI/MSI-X
[    1.149231] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.149318] pciehp 0000:00:1c.7:pcie04: HPC vendor_id 8086 device_id 1c1e ss_vid 1028 ss_did 502
[    1.149387] pciehp 0000:00:1c.7:pcie04: service driver pciehp loaded
[    1.149401] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.149477] intel_idle: MWAIT substates: 0x21120
[    1.149481] intel_idle: v0.4 model 0x2A
[    1.149484] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.149672] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.149780] ACPI: AC Adapter [AC] (on-line)
[    1.150060] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.151018] ACPI: Lid Switch [LID0]
[    1.151114] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.151125] ACPI: Power Button [PWRB]
[    1.151200] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.151208] ACPI: Sleep Button [SBTN]
[    1.151284] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.151291] ACPI: Power Button [PWRF]
[    1.151349] ACPI: acpi_idle yielding to intel_idle
[    1.164887] thermal LNXTHERM:00: registered as thermal_zone0
[    1.164894] ACPI: Thermal Zone [THM] (57 C)
[    1.164948] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.164978] ERST: Table is not found!
[    1.165105] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.209336] ACPI: Battery Slot [BAT0] (battery present)
[    1.764783] Freeing initrd memory: 19980k freed
[    1.851658] Linux agpgart interface v0.103
[    1.851834] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.852166] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.855487] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.855699] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.857766] brd: module loaded
[    1.858750] loop: module loaded
[    1.859591] Fixed MDIO Bus: probed
[    1.859634] PPP generic driver version 2.4.2
[    1.859705] tun: Universal TUN/TAP device driver, 1.6
[    1.859709] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.859847] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.859883] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.859918] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.859926] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.860008] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.860054] ehci_hcd 0000:00:1a.0: debug port 2
[    1.863956] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.864000] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7e08000
[    1.878954] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.879190] hub 1-0:1.0: USB hub found
[    1.879200] hub 1-0:1.0: 2 ports detected
[    1.879325] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.879350] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.879358] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.879429] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.879476] ehci_hcd 0000:00:1d.0: debug port 2
[    1.883365] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.883393] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7e07000
[    1.898922] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.899126] hub 2-0:1.0: USB hub found
[    1.899135] hub 2-0:1.0: 2 ports detected
[    1.899241] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.899263] uhci_hcd: USB Universal Host Controller Interface driver
[    1.899386] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2] at 0x60,0x64 irq 1,12
[    1.901634] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.901649] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.901869] mousedev: PS/2 mouse device common for all mice
[    1.902172] rtc_cmos 00:05: RTC can wake from S4
[    1.902322] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.902362] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.902566] device-mapper: uevent: version 1.0.3
[    1.902710] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.902977] cpuidle: using governor ladder
[    1.903363] cpuidle: using governor menu
[    1.903368] EFI Variables Facility v0.08 2004-May-17
[    1.903808] TCP cubic registered
[    1.904083] NET: Registered protocol family 10
[    1.904971] NET: Registered protocol family 17
[    1.905000] Registering the dns_resolver key type
[    1.905181] PM: Hibernation image not present or could not be loaded.
[    1.905205] registered taskstats version 1
[    1.924369] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.928676]   Magic number: 4:814:42
[    1.928695] bdi 7:7: hash matches
[    1.928865] rtc_cmos 00:05: setting system clock to 2012-03-10 20:02:12 UTC (1331409732)
[    1.930552] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.930553] EDD information not available.
[    1.931694] Freeing unused kernel memory: 988k freed
[    1.931796] Write protecting the kernel read-only data: 12288k
[    1.936195] Freeing unused kernel memory: 2032k freed
[    1.939322] Freeing unused kernel memory: 1388k freed
[    1.951808] udevd[90]: starting version 173
[    1.969897] [drm] Initialized drm 1.1.0 20060810
[    1.970486] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.970527] r8169 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.970580] r8169 0000:05:00.0: setting latency timer to 64
[    1.970656] r8169 0000:05:00.0: irq 41 for MSI/MSI-X
[    1.971078] r8169 0000:05:00.0: eth0: RTL8105e at 0xffffc9000061e000, d0:67:e5:f5:ac:e2, XID 00a00000 IRQ 41
[    1.974241] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.974246] i915 0000:00:02.0: setting latency timer to 64
[    1.975831] wmi: Mapper loaded
[    2.028804] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[    2.028808] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.028817] [drm] Driver supports precise vblank timestamp query.
[    2.028844] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.089160] Refined TSC clocksource calibration: 2394.560 MHz.
[    2.089163] Switching to clocksource tsc
[    2.198525] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    2.206245] fbcon: inteldrmfb (fb0) is primary device
[    2.206682] Console: switching to colour frame buffer device 170x48
[    2.206695] fb0: inteldrmfb frame buffer device
[    2.206696] drm: registered panic notifier
[    2.275138] acpi device:33: registered as cooling_device4
[    2.275309] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    2.275353] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.275377] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.275395] ahci 0000:00:1f.2: version 3.0
[    2.275405] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.275458] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    2.275486] ahci: SSS flag set, parallel bus scan disabled
[    2.290404] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x11 impl SATA mode
[    2.290415] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems apst 
[    2.290428] ahci 0000:00:1f.2: setting latency timer to 64
[    2.298890] scsi0 : ahci
[    2.299022] scsi1 : ahci
[    2.299123] scsi2 : ahci
[    2.299222] scsi3 : ahci
[    2.299322] scsi4 : ahci
[    2.299421] scsi5 : ahci
[    2.299636] ata1: SATA max UDMA/133 abar m2048@0xf7e06000 port 0xf7e06100 irq 43
[    2.299638] ata2: DUMMY
[    2.299638] ata3: DUMMY
[    2.299639] ata4: DUMMY
[    2.299641] ata5: SATA max UDMA/133 abar m2048@0xf7e06000 port 0xf7e06300 irq 43
[    2.299642] ata6: DUMMY
[    2.331042] hub 1-1:1.0: USB hub found
[    2.331131] hub 1-1:1.0: 6 ports detected
[    2.442162] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    2.574664] hub 2-1:1.0: USB hub found
[    2.574759] hub 2-1:1.0: 8 ports detected
[    2.617894] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.620046] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.620440] ata1.00: ATA-8: ST9500325AS, D005DEM1, max UDMA/133
[    2.620449] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.622923] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.623316] ata1.00: configured for UDMA/133
[    2.623479] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      D005 PQ: 0 ANSI: 5
[    2.623595] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.623601] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.623653] sd 0:0:0:0: [sda] Write Protect is off
[    2.623657] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.623684] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.646072] usb 1-1.4: new full speed USB device number 3 using ehci_hcd
[    2.651734]  sda: sda1 sda2 sda3 < sda5 >
[    2.652025] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.809832] usb 1-1.5: new high speed USB device number 4 using ehci_hcd
[    2.941418] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.949782] ata5.00: ATAPI: TSSTcorp DVD+/-RW SN-208BB, D100, max UDMA/100
[    2.956096] ata5.00: configured for UDMA/100
[    2.965545] scsi 4:0:0:0: CD-ROM            TSSTcorp DVD+-RW SN-208BB D100 PQ: 0 ANSI: 5
[    2.980345] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.980355] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.980491] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.980527] sr 4:0:0:0: Attached scsi generic sg1 type 5
[   12.069307] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   22.267396] udevd[436]: starting version 173
[   22.292214] lp: driver loaded but no devices found
[   22.299510] Adding 5857276k swap on /dev/mapper/gr1-swap.  Priority:-1 extents:1 across:5857276k 
[   22.306246] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   22.308151] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.308158] mei 0000:00:16.0: setting latency timer to 64
[   22.312796] cfg80211: Calling CRDA to update world regulatory domain
[   22.333045] ath9k 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   22.333060] ath9k 0000:09:00.0: setting latency timer to 64
[   22.352886] type=1400 audit(1331409752.952:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=551 comm="apparmor_parser"
[   22.353206] type=1400 audit(1331409752.952:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=551 comm="apparmor_parser"
[   22.353417] type=1400 audit(1331409752.952:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=551 comm="apparmor_parser"
[   22.385891] ath: EEPROM regdomain: 0x60
[   22.385895] ath: EEPROM indicates we should expect a direct regpair map
[   22.385899] ath: Country alpha2 being used: 00
[   22.385900] ath: Regpair used: 0x60
[   22.387441] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   22.387446] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.387448] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   22.387451] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.387453] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   22.387456] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.387458] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   22.387461] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.387463] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   22.387466] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.387467] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   22.387470] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.387472] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   22.387474] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.387476] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   22.387479] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.387481] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   22.387483] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.387485] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   22.387487] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.387489] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   22.387492] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.387494] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   22.387496] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.387498] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   22.387501] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.387503] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   22.387505] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   22.388921] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   22.402304] Bluetooth: Core ver 2.16
[   22.402323] NET: Registered protocol family 31
[   22.402324] Bluetooth: HCI device and connection manager initialized
[   22.402327] Bluetooth: HCI socket layer initialized
[   22.402329] Bluetooth: L2CAP socket layer initialized
[   22.404320] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   22.405054] Registered led device: ath9k-phy0
[   22.405062] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc900050a0000, irq=19
[   22.407834] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   22.407893] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   22.407921] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   22.408133] Bluetooth: SCO socket layer initialized
[   22.408971] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   22.409591] usbcore: registered new interface driver btusb
[   22.426697] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
[   22.449685] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   22.480644] Linux video capture interface: v2.00
[   22.483515] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:643e)
[   22.500902] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input6
[   22.500971] usbcore: registered new interface driver uvcvideo
[   22.500973] USB Video Class driver (v1.1.0)
[   22.515981] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   22.653918] alps.c: Enabled hardware quirk, falling back to psmouse-core
[   22.659248] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   22.659251] cfg80211: World regulatory domain updated:
[   22.659253] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.659256] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.659258] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.659260] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.659263] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.659265] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.667347] input: ImPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   22.968393] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   22.968540] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   22.968628] input: HDA Intel PCH Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   22.968664] input: HDA Intel PCH HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   23.406877] hci_cmd_timer: hci0 command tx timeout
[   24.405482] hci_cmd_timer: hci0 command tx timeout
[   24.989788] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   25.200237] EXT4-fs (dm-3): mounted filesystem with ordered data mode. Opts: (null)
[   25.403905] hci_cmd_timer: hci0 command tx timeout
[   25.569010] EXT4-fs (dm-4): mounted filesystem with ordered data mode. Opts: (null)
[   25.717306] type=1400 audit(1331409756.320:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1058 comm="apparmor_parser"
[   25.717658] type=1400 audit(1331409756.320:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1059 comm="apparmor_parser"
[   25.717993] type=1400 audit(1331409756.320:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1059 comm="apparmor_parser"
[   25.718199] type=1400 audit(1331409756.320:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1059 comm="apparmor_parser"
[   25.719997] type=1400 audit(1331409756.324:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1064 comm="apparmor_parser"
[   25.720488] type=1400 audit(1331409756.324:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1064 comm="apparmor_parser"
[   25.720750] type=1400 audit(1331409756.324:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1067 comm="apparmor_parser"
[   25.744220] ppdev: user-space parallel port driver
[   25.899102] init: failsafe main process (1014) killed by TERM signal
[   25.900005] init: apport pre-start process (1129) terminated with status 1
[   25.910146] init: apport post-stop process (1162) terminated with status 1
[   25.950233] Bluetooth: RFCOMM TTY layer initialized
[   25.950239] Bluetooth: RFCOMM socket layer initialized
[   25.950240] Bluetooth: RFCOMM ver 1.11
[   25.956409] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.956413] Bluetooth: BNEP filters: protocol multicast
[   26.013940] r8169 0000:05:00.0: eth0: link down
[   26.014189] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.056231] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.402417] hci_cmd_timer: hci0 command tx timeout
[   27.094085] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro,commit=0
[   27.325725] EXT4-fs (sda2): re-mounted. Opts: commit=0
[   27.327519] EXT4-fs (dm-3): re-mounted. Opts: commit=0
[   27.328905] EXT4-fs (dm-4): re-mounted. Opts: commit=0
[   27.401027] hci_cmd_timer: hci0 command tx timeout
[   27.711321] init: plymouth-stop pre-start process (1487) terminated with status 1
[   28.399439] hci_cmd_timer: hci0 command tx timeout
[   28.993128] wlan0: authenticate with 5c:d9:98:74:bc:0e (try 1)
[   28.995435] wlan0: authenticated
[   29.025157] wlan0: associate with 5c:d9:98:74:bc:0e (try 1)
[   29.028442] wlan0: RX AssocResp from 5c:d9:98:74:bc:0e (capab=0x411 status=0 aid=1)
[   29.028449] wlan0: associated
[   29.028913] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.398021] hci_cmd_timer: hci0 command tx timeout
[   30.396470] hci_cmd_timer: hci0 command tx timeout
[   31.394987] hci_cmd_timer: hci0 command tx timeout
[   32.393535] hci_cmd_timer: hci0 command tx timeout
[   33.392063] hci_cmd_timer: hci0 command tx timeout
[   34.390526] hci_cmd_timer: hci0 command tx timeout
[   35.389031] hci_cmd_timer: hci0 command tx timeout
[   36.387561] hci_cmd_timer: hci0 command tx timeout
[   37.386061] hci_cmd_timer: hci0 command tx timeout
[   38.384567] hci_cmd_timer: hci0 command tx timeout
[   39.111501] wlan0: no IPv6 routers present
[   39.383078] hci_cmd_timer: hci0 command tx timeout
[   40.382098] hci_cmd_timer: hci0 command tx timeout
[   41.381116] hci_cmd_timer: hci0 command tx timeout
[   42.380125] hci_cmd_timer: hci0 command tx timeout
[   43.379148] hci_cmd_timer: hci0 command tx timeout
```Actually, my attempt at forcing the system to see all the memory caused it to reserve some regions. Follows the first lines of a diff between the two dmesgs:

```
--- dmesg-without-forced-memory.txt    2012-03-10 17:16:18.564032916 -0300
+++ dmesg-with-mem=4096M.txt    2012-03-10 17:10:03.168092297 -0300
@@ -1,7 +1,7 @@
 [    0.000000] Initializing cgroup subsys cpuset
 [    0.000000] Initializing cgroup subsys cpu
 [    0.000000] Linux version 3.0.0-16-generic (buildd@roseapple) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 (Ubuntu 3.0.0-16.29-generic 3.0.20)
-[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.0.0-16-generic root=/dev/mapper/gr1-root ro quiet splash vt.handoff=7
+[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.0.0-16-generic root=/dev/mapper/gr1-root mem=4096M ro quiet splash vt.handoff=7
 [    0.000000] KERNEL supported cpus:
 [    0.000000]   Intel GenuineIntel
 [    0.000000]   AMD AuthenticAMD
@@ -30,13 +30,37 @@
 [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
 [    0.000000]  BIOS-e820: 0000000100000000 - 000000011fe00000 (usable)
+[    0.000000] e820 remove range: 0000000100000000 - ffffffffffffffff (usable)
 [    0.000000] NX (Execute Disable) protection: active
+[    0.000000] user-defined physical RAM map:
+[    0.000000]  user: 0000000000000000 - 000000000009d400 (usable)
+[    0.000000]  user: 000000000009d400 - 00000000000a0000 (reserved)
+[    0.000000]  user: 00000000000e0000 - 0000000000100000 (reserved)
+[    0.000000]  user: 0000000000100000 - 0000000020000000 (usable)
+[    0.000000]  user: 0000000020000000 - 0000000020200000 (reserved)
+[    0.000000]  user: 0000000020200000 - 0000000040000000 (usable)
+[    0.000000]  user: 0000000040000000 - 0000000040200000 (reserved)
+[    0.000000]  user: 0000000040200000 - 00000000da4ea000 (usable)
+[    0.000000]  user: 00000000da4ea000 - 00000000da52d000 (ACPI NVS)
+[    0.000000]  user: 00000000da52d000 - 00000000da798000 (usable)
+[    0.000000]  user: 00000000da798000 - 00000000da967000 (reserved)
+[    0.000000]  user: 00000000da967000 - 00000000dacbc000 (usable)
+[    0.000000]  user: 00000000dacbc000 - 00000000dad68000 (reserved)
+[    0.000000]  user: 00000000dad68000 - 00000000dafe8000 (ACPI NVS)
+[    0.000000]  user: 00000000dafe8000 - 00000000db000000 (ACPI data)
+[    0.000000]  user: 00000000db800000 - 00000000dfa00000 (reserved)
+[    0.000000]  user: 00000000f8000000 - 00000000fc000000 (reserved)
+[    0.000000]  user: 00000000fec00000 - 00000000fec01000 (reserved)
+[    0.000000]  user: 00000000fed00000 - 00000000fed04000 (reserved)
+[    0.000000]  user: 00000000fed1c000 - 00000000fed20000 (reserved)
+[    0.000000]  user: 00000000fee00000 - 00000000fee01000 (reserved)
+[    0.000000]  user: 00000000ff000000 - 0000000100000000 (reserved)
 [    0.000000] DMI 2.6 present.
 [    0.000000] DMI: Dell Inc. Inspiron N4050/0X0DC1, BIOS A06 11/14/2011
 [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
 [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
 [    0.000000] No AGP bridge found
-[    0.000000] last_pfn = 0x11fe00 max_arch_pfn = 0x400000000
+[    0.000000] last_pfn = 0xdacbc max_arch_pfn = 0x400000000
 [    0.000000] MTRR default type: uncachable
 [    0.000000] MTRR fixed ranges enabled:
 [    0.000000]   00000-9FFFF write-back
@@ -75,7 +99,6 @@
 [    0.000000] reg 5, base: 4GB, range: 512MB, type WB
 [    0.000000] reg 6, base: 4606MB, range: 2MB, type UC
 [    0.000000] e820 update range: 00000000db800000 - 0000000100000000 (usable) ==> (reserved)
-[    0.000000] last_pfn = 0xdacbc max_arch_pfn = 0x400000000
 [    0.000000] found SMP MP-table at [ffff8800000fd1b0] fd1b0
 [    0.000000] initial memory mapped : 0 - 20000000
 [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
@@ -83,9 +106,6 @@
 [    0.000000]  0000000000 - 00dac00000 page 2M
 [    0.000000]  00dac00000 - 00dacbc000 page 4k
 [    0.000000] kernel direct mapping tables up to dacbc000 @ 1fffa000-20000000
-[    0.000000] init_memory_mapping: 0000000100000000-000000011fe00000
-[    0.000000]  0100000000 - 011fe00000 page 2M
-[    0.000000] kernel direct mapping tables up to 11fe00000 @ dacb6000-dacbc000
 [    0.000000] RAMDISK: 358ea000 - 36c6d000
 [    0.000000] ACPI: RSDP 00000000000f0410 00024 (v02   DELL)
 [    0.000000] ACPI: XSDT 00000000dafe8078 0006C (v01 DELL    WN09    01072009 AMI  00010013)
@@ -102,31 +122,28 @@
 [    0.000000] ACPI: OSFR 00000000daff35a8 0008C (v01 DELL    M08     07DB0B0E ASL  00000061)
 [    0.000000] ACPI: Local APIC address 0xfee00000
 [    0.000000] No NUMA configuration found
-[    0.000000] Faking a node at 0000000000000000-000000011fe00000
-[    0.000000] Initmem setup node 0 0000000000000000-000000011fe00000
-[    0.000000]   NODE_DATA [000000011fdfb000 - 000000011fdfffff]
-[    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff88011b400000-ffff88011edfffff] on node 0
+[    0.000000] Faking a node at 0000000000000000-00000000dacbc000
+[    0.000000] Initmem setup node 0 0000000000000000-00000000dacbc000
+[    0.000000]   NODE_DATA [00000000dacb7000 - 00000000dacbbfff]
+[    0.000000]  [ffffea0000000000-ffffea00031fffff] PMD -> [ffff8800d6400000-ffff8800d95fffff] on node 0
 [    0.000000] Zone PFN ranges:
 [    0.000000]   DMA      0x00000010 -> 0x00001000
 [    0.000000]   DMA32    0x00001000 -> 0x00100000
-[    0.000000]   Normal   0x00100000 -> 0x0011fe00
+[    0.000000]   Normal   empty
 [    0.000000] Movable zone start PFN for each node
-[    0.000000] early_node_map[7] active PFN ranges
+[    0.000000] early_node_map[6] active PFN ranges
 [    0.000000]     0: 0x00000010 -> 0x0000009d
 [    0.000000]     0: 0x00000100 -> 0x00020000
 [    0.000000]     0: 0x00020200 -> 0x00040000
 [    0.000000]     0: 0x00040200 -> 0x000da4ea
 [    0.000000]     0: 0x000da52d -> 0x000da798
 [    0.000000]     0: 0x000da967 -> 0x000dacbc
-[    0.000000]     0: 0x00100000 -> 0x0011fe00
-[    0.000000] On node 0 totalpages: 1025079
+[    0.000000] On node 0 totalpages: 894519
 [    0.000000]   DMA zone: 56 pages used for memmap
 [    0.000000]   DMA zone: 5 pages reserved
 [    0.000000]   DMA zone: 3920 pages, LIFO batch:0
```
The system seems to reserve some block of memory for some unknow reason. I'm currently researching this part:
```
[    0.000000] DMI: Dell Inc. Inspiron N4050/0X0DC1, BIOS A06 11/14/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)

```Any help in this matter is welcome.

---

### Post by pbrane on 2012-03-10
On my xubuntu 64 bit with 4GB RAM. Core 2 Duo. Dell Inspiron 1720.
```

$ cat /proc/meminfo | grep MemTotal
MemTotal:        4049140 kB

```

```

$ free
             total       used       free     shared    buffers     cached
Mem:       4049140    2424684    1624456          0     240568    1547532
-/+ buffers/cache:     636584    3412556
Swap:      3914748          0    3914748

```

---

### Post by Marko Darko on 2012-03-10
So, it's related to memory reservation after all. Do someone understand why so much memory gets reserved?

I also ran some tests with the 12.04 beta 32 bits (PAE is enabled by default now) and 64 bits booting from a USB thumbdrive. They are also reserving memory, but the 64 bit edition reserves a lot more.

32 bits + PAE
```
ubuntu@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:       4034312    1404996    2629316          0     148400     948364
-/+ buffers/cache:     308232    3726080
Swap:            0          0          0



ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3939       1372       2567          0        144        926
-/+ buffers/cache:        301       3638
Swap:            0          0          0



ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.2.0-17-generic-pae #27-Ubuntu SMP Fri Feb 24 15:59:25 UTC 2012 i686 i686 i386 GNU/Linux




ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

ubuntu@ubuntu:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-17-generic-pae (buildd@roseapple) (gcc version 4.6.2 (Ubuntu/Linaro 4.6.2-16ubuntu1) ) #27-Ubuntu SMP Fri Feb 24 15:59:25 UTC 2012 (Ubuntu 3.2.0-17.27-generic-pae 3.2.6)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000da4ea000 (usable)
[    0.000000]  BIOS-e820: 00000000da4ea000 - 00000000da52d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000da52d000 - 00000000da798000 (usable)
[    0.000000]  BIOS-e820: 00000000da798000 - 00000000da967000 (reserved)
[    0.000000]  BIOS-e820: 00000000da967000 - 00000000dacbc000 (usable)
[    0.000000]  BIOS-e820: 00000000dacbc000 - 00000000dad68000 (reserved)
[    0.000000]  BIOS-e820: 00000000dad68000 - 00000000dafe8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dafe8000 - 00000000db000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000db800000 - 00000000dfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000011fe00000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Dell Inc. Inspiron N4050/0X0DC1, BIOS A06 11/14/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x11fe00 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FE0000000 write-back
[    0.000000]   2 base 0DB800000 mask FFF800000 uncachable
[    0.000000]   3 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   5 base 11FE00000 mask FFFE00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 4, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 5, base: 4606MB, range: 2MB, type UC
[    0.000000] total RAM covered: 4022M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K  chunk_size: 128M    num_reg: 7      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 4, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 5, base: 4GB, range: 512MB, type WB
[    0.000000] reg 6, base: 4606MB, range: 2MB, type UC
[    0.000000] e820 update range: 00000000db800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00fd1b0] fd1b0
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 7f1e9000 - 80000000
[    0.000000] Allocated new RAMDISK: 36de7000 - 37bfd4b1
[    0.000000] Move RAMDISK from 000000007f1e9000 - 000000007ffff4b0 to 36de7000 - 37bfd4b0
[    0.000000] ACPI: RSDP 000f0410 00024 (v02   DELL)
[    0.000000] ACPI: XSDT dafe8078 0006C (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: FACP daff1c38 000F4 (v04   DELL     WN09 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT dafe8170 09AC8 (v02   DELL     WN09 00000000 INTL 20051117)
[    0.000000] ACPI: FACS dafe4f80 00040
[    0.000000] ACPI: APIC daff1d30 00072 (v03   DELL     WN09 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG daff1da8 0003C (v01   DELL     WN09 01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT daff1de8 004B0 (v01 TrmRef PtidDevc 00001000 INTL 20091112)
[    0.000000] ACPI: SLIC daff2298 00176 (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: HPET daff2410 00038 (v01   DELL     WN09 01072009 AMI. 00000004)
[    0.000000] ACPI: SSDT daff2448 007C2 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT daff2c10 00996 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: OSFR daff35a8 0008C (v01 DELL    M08     07DB0B0E ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 3714MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0011fe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000da4ea
[    0.000000]     0: 0x000da52d -> 0x000da798
[    0.000000]     0: 0x000da967 -> 0x000dacbc
[    0.000000]     0: 0x00100000 -> 0x0011fe00
[    0.000000] On node 0 totalpages: 1025079
[    0.000000] free_area_init_node: node 0, pgdat c18651c0, node_mem_map f49e6200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 221990 pages, LIFO batch:31
[    0.000000]   HighMem zone: 7429 pages used for memmap
[    0.000000]   HighMem zone: 789927 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] Allocating PCI resources starting at dfa00000 (gap: dfa00000:18600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f4600000 s34176 r0 d23168 u524288
[    0.000000] pcpu-alloc: s34176 r0 d23168 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1015866
[    0.000000] Kernel command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] allocated 18865920 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0011fe00)
[    0.000000] Memory: 4019144k/4716544k available (5811k kernel code, 81172k reserved, 2839k data, 740k init, 3189424k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1873000 - 0xc192c000   ( 740 kB)
[    0.000000]       .data : 0xc15accbc - 0xc1872a40   (2839 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15accbc   (5811 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f300a000 soft=f300c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2394.678 MHz processor.
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 4789.35 BogoMIPS (lpj=9578712)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000022] Security Framework initialized
[    0.000033] AppArmor: AppArmor initialized
[    0.000035] Yama: becoming mindful.
[    0.000076] Mount-cache hash table entries: 512
[    0.000171] Initializing cgroup subsys cpuacct
[    0.000175] Initializing cgroup subsys memory
[    0.000181] Initializing cgroup subsys devices
[    0.000183] Initializing cgroup subsys freezer
[    0.000185] Initializing cgroup subsys blkio
[    0.000189] Initializing cgroup subsys perf_event
[    0.000211] CPU: Physical Processor ID: 0
[    0.000212] CPU: Processor Core ID: 0
[    0.000217] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.000217] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.000220] mce: CPU supports 7 MCE banks
[    0.000231] CPU0: Thermal monitoring enabled (TM1)
[    0.000237] using mwait in idle threads.
[    0.002379] ACPI: Core revision 20110623
[    0.013197] ftrace: allocating 26549 entries in 52 pages
[    0.040880] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.041352] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.080987] CPU0: Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz stepping 07
[    0.187680] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.187694] PEBS disabled due to CPU errata.
[    0.187700] ... version:                3
[    0.187703] ... bit width:              48
[    0.187706] ... generic registers:      4
[    0.187710] ... value mask:             0000ffffffffffff
[    0.187714] ... max period:             000000007fffffff
[    0.187718] ... fixed-purpose events:   3
[    0.187722] ... event mask:             000000070000000f
[    0.188024] NMI watchdog enabled, takes one hw-pmu counter.
[    0.188211] CPU 1 irqstacks, hard=f3112000 soft=f3114000
[    0.188216] Booting Node   0, Processors  #1
[    0.188222] smpboot cpu 1: start_ip = 99000
[    0.198910] Initializing CPU#1
[    0.295703] NMI watchdog enabled, takes one hw-pmu counter.
[    0.295873] CPU 2 irqstacks, hard=f3120000 soft=f3122000
[    0.295878]  #2
[    0.295881] smpboot cpu 2: start_ip = 99000
[    0.306626] Initializing CPU#2
[    0.403553] NMI watchdog enabled, takes one hw-pmu counter.
[    0.403743] CPU 3 irqstacks, hard=f312e000 soft=f3138000
[    0.403747]  #3 Ok.
[    0.403751] smpboot cpu 3: start_ip = 99000
[    0.414437] Initializing CPU#3
[    0.511331] NMI watchdog enabled, takes one hw-pmu counter.
[    0.511389] Brought up 4 CPUs
[    0.511394] Total of 4 processors activated (19156.31 BogoMIPS).
[    0.521106] devtmpfs: initialized
[    0.521402] EVM: security.selinux
[    0.521406] EVM: security.SMACK64
[    0.521409] EVM: security.capability
[    0.521470] PM: Registering ACPI NVS region at da4ea000 (274432 bytes)
[    0.521495] PM: Registering ACPI NVS region at dad68000 (2621440 bytes)
[    0.524090] print_constraints: dummy: 
[    0.524141] RTC time: 23:05:00, date: 03/10/12
[    0.524226] NET: Registered protocol family 16
[    0.524458] Trying to unpack rootfs image as initramfs...
[    0.524484] EISA bus registered
[    0.524521] ACPI: bus type pci registered
[    0.524670] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.524679] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.524683] PCI: Using MMCONFIG for extended config space
[    0.524687] PCI: Using configuration type 1 for base access
[    0.527256] bio: create slab <bio-0> at 0
[    0.527456] ACPI: Added _OSI(Module Device)
[    0.527462] ACPI: Added _OSI(Processor Device)
[    0.527467] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.527473] ACPI: Added _OSI(Processor Aggregator Device)
[    0.532053] ACPI: EC: Look up EC in DSDT
[    0.537061] ACPI: Executed 1 blocks of module-level executable AML code
[    0.547784] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    6.555732] sched: RT throttling activated
[    6.595025] ACPI: SSDT dad51698 0064F (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    6.596249] ACPI: Dynamic OEM Table Load:
[    6.596258] ACPI: SSDT   (null) 0064F (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    6.610505] ACPI: SSDT dad52a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    6.611837] ACPI: Dynamic OEM Table Load:
[    6.611844] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    6.626048] ACPI: SSDT dad50d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    6.627266] ACPI: Dynamic OEM Table Load:
[    6.627272] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    8.855980] ACPI: Interpreter enabled
[    8.856002] ACPI: (supports S0 S1 S3 S4 S5)
[    8.856078] ACPI: Using IOAPIC for interrupt routing
[    8.877781] Freeing initrd memory: 14428k freed
[    8.899237] ACPI: No dock devices found.
[    8.899245] HEST: Table not found.
[    8.899255] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    8.900195] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    8.901528] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    8.901535] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    8.901542] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    8.901549] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    8.901555] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    8.901561] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    8.901566] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    8.901572] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    8.901579] pci_root PNP0A08:00: host bridge window [mem 0xdfa00000-0xfeafffff]
[    8.901585] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    8.901623] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    8.901727] pci 0000:00:02.0: [8086:0116] type 0 class 0x000300
[    8.901759] pci 0000:00:02.0: reg 10: [mem 0xf6800000-0xf6bfffff 64bit]
[    8.901778] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    8.901792] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    8.901934] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    8.901985] pci 0000:00:16.0: reg 10: [mem 0xf7e0a000-0xf7e0a00f 64bit]
[    8.902150] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    8.902160] pci 0000:00:16.0: PME# disabled
[    8.902232] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    8.902278] pci 0000:00:1a.0: reg 10: [mem 0xf7e08000-0xf7e083ff]
[    8.902485] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    8.902495] pci 0000:00:1a.0: PME# disabled
[    8.902548] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    8.902585] pci 0000:00:1b.0: reg 10: [mem 0xf7e00000-0xf7e03fff 64bit]
[    8.902749] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    8.902758] pci 0000:00:1b.0: PME# disabled
[    8.902807] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    8.902986] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    8.902995] pci 0000:00:1c.0: PME# disabled
[    8.903046] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    8.903225] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    8.903234] pci 0000:00:1c.1: PME# disabled
[    8.903288] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
[    8.903467] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    8.903477] pci 0000:00:1c.3: PME# disabled
[    8.903537] pci 0000:00:1c.7: [8086:1c1e] type 1 class 0x000604
[    8.903730] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    8.903740] pci 0000:00:1c.7: PME# disabled
[    8.903801] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    8.903848] pci 0000:00:1d.0: reg 10: [mem 0xf7e07000-0xf7e073ff]
[    8.904044] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    8.904054] pci 0000:00:1d.0: PME# disabled
[    8.904101] pci 0000:00:1f.0: [8086:1c4b] type 0 class 0x000601
[    8.904350] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    8.904397] pci 0000:00:1f.2: reg 10: [io  0xf0b0-0xf0b7]
[    8.904418] pci 0000:00:1f.2: reg 14: [io  0xf0a0-0xf0a3]
[    8.904438] pci 0000:00:1f.2: reg 18: [io  0xf090-0xf097]
[    8.904459] pci 0000:00:1f.2: reg 1c: [io  0xf080-0xf083]
[    8.904479] pci 0000:00:1f.2: reg 20: [io  0xf060-0xf07f]
[    8.904499] pci 0000:00:1f.2: reg 24: [mem 0xf7e06000-0xf7e067ff]
[    8.904614] pci 0000:00:1f.2: PME# supported from D3hot
[    8.904623] pci 0000:00:1f.2: PME# disabled
[    8.904661] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    8.904698] pci 0000:00:1f.3: reg 10: [mem 0xf7e05000-0xf7e050ff 64bit]
[    8.904750] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    8.904911] pci 0000:00:1c.0: PCI bridge to [bus 03-04]
[    8.905069] pci 0000:05:00.0: [10ec:8136] type 0 class 0x000200
[    8.905106] pci 0000:05:00.0: reg 10: [io  0xe000-0xe0ff]
[    8.905168] pci 0000:05:00.0: reg 18: [mem 0xf1104000-0xf1104fff 64bit pref]
[    8.905208] pci 0000:05:00.0: reg 20: [mem 0xf1100000-0xf1103fff 64bit pref]
[    8.905369] pci 0000:05:00.0: supports D1 D2
[    8.905374] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    8.905385] pci 0000:05:00.0: PME# disabled
[    8.910438] pci 0000:00:1c.1: PCI bridge to [bus 05-06]
[    8.910448] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    8.910467] pci 0000:00:1c.1:   bridge window [mem 0xf1100000-0xf11fffff 64bit pref]
[    8.910607] pci 0000:09:00.0: [168c:002b] type 0 class 0x000280
[    8.910657] pci 0000:09:00.0: reg 10: [mem 0xf7d00000-0xf7d0ffff 64bit]
[    8.910883] pci 0000:09:00.0: supports D1
[    8.910888] pci 0000:09:00.0: PME# supported from D0 D1 D3hot
[    8.910899] pci 0000:09:00.0: PME# disabled
[    8.918416] pci 0000:00:1c.3: PCI bridge to [bus 09-0a]
[    8.918431] pci 0000:00:1c.3:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    8.918549] pci 0000:00:1c.7: PCI bridge to [bus 11-1f]
[    8.918560] pci 0000:00:1c.7:   bridge window [io  0xc000-0xdfff]
[    8.918571] pci 0000:00:1c.7:   bridge window [mem 0xf6c00000-0xf7cfffff]
[    8.918587] pci 0000:00:1c.7:   bridge window [mem 0xf0000000-0xf10fffff 64bit pref]
[    8.918635] pci_bus 0000:00: on NUMA node 0
[    8.918642] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.919107] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    8.919211] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    8.919318] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    8.919436] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08._PRT]
[    8.919817]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    8.920363]  pci0000:00: ACPI _OSC control (0x19) granted
[    8.930115] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    8.930244] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 10 11 12 14 15)
[    8.930379] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    8.930501] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    8.930620] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    8.930742] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    8.930864] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    8.930982] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 10 11 12 14 15)
[    8.931246] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    8.931267] vgaarb: loaded
[    8.931270] vgaarb: bridge control possible 0000:00:02.0
[    8.931534] i2c-core: driver [aat2870] using legacy suspend method
[    8.931538] i2c-core: driver [aat2870] using legacy resume method
[    8.931721] SCSI subsystem initialized
[    8.931827] libata version 3.00 loaded.
[    8.931932] usbcore: registered new interface driver usbfs
[    8.931959] usbcore: registered new interface driver hub
[    8.932015] usbcore: registered new device driver usb
[    8.932218] PCI: Using ACPI for IRQ routing
[    8.935963] PCI: pci_cache_line_size set to 64 bytes
[    8.936098] reserve RAM buffer: 000000000009d400 - 000000000009ffff 
[    8.936105] reserve RAM buffer: 00000000da4ea000 - 00000000dbffffff 
[    8.936115] reserve RAM buffer: 00000000da798000 - 00000000dbffffff 
[    8.936123] reserve RAM buffer: 00000000dacbc000 - 00000000dbffffff 
[    8.936131] reserve RAM buffer: 000000011fe00000 - 000000011fffffff 
[    8.936355] NetLabel: Initializing
[    8.936359] NetLabel:  domain hash size = 128
[    8.936363] NetLabel:  protocols = UNLABELED CIPSOv4
[    8.936386] NetLabel:  unlabeled traffic allowed by default
[    8.936490] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    8.936508] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    8.938541] Switching to clocksource hpet
[    8.955836] AppArmor: AppArmor Filesystem Enabled
[    8.955882] pnp: PnP ACPI init
[    8.955915] ACPI: bus type pnp registered
[    8.956659] pnp 00:00: [bus 00-3e]
[    8.956667] pnp 00:00: [io  0x0000-0x0cf7 window]
[    8.956672] pnp 00:00: [io  0x0cf8-0x0cff]
[    8.956678] pnp 00:00: [io  0x0d00-0xffff window]
[    8.956684] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    8.956690] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    8.956695] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    8.956701] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    8.956706] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    8.956712] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    8.956717] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    8.956723] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    8.956728] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    8.956734] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    8.956740] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    8.956745] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    8.956751] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    8.956756] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    8.956762] pnp 00:00: [mem 0xdfa00000-0xfeafffff window]
[    8.956768] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    8.956921] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    8.956954] pnp 00:01: [io  0x0000-0x001f]
[    8.956959] pnp 00:01: [io  0x0081-0x0091]
[    8.956968] pnp 00:01: [io  0x0093-0x009f]
[    8.956972] pnp 00:01: [io  0x00c0-0x00df]
[    8.956978] pnp 00:01: [dma 4]
[    8.957041] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    8.957062] pnp 00:02: [mem 0xff000000-0xffffffff]
[    8.957119] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    8.957291] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    8.957350] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    8.957383] pnp 00:04: [io  0x002e-0x002f]
[    8.957388] pnp 00:04: [io  0x004e-0x004f]
[    8.957393] pnp 00:04: [io  0x0061]
[    8.957397] pnp 00:04: [io  0x0063]
[    8.957401] pnp 00:04: [io  0x0065]
[    8.957406] pnp 00:04: [io  0x0067]
[    8.957410] pnp 00:04: [io  0x0070]
[    8.957415] pnp 00:04: [io  0x0080]
[    8.957419] pnp 00:04: [io  0x0092]
[    8.957423] pnp 00:04: [io  0x00b2-0x00b3]
[    8.957428] pnp 00:04: [io  0x0680-0x069f]
[    8.957433] pnp 00:04: [io  0x1000-0x100f]
[    8.957438] pnp 00:04: [io  0xffff]
[    8.957443] pnp 00:04: [io  0xffff]
[    8.957448] pnp 00:04: [io  0x0400-0x0453]
[    8.957453] pnp 00:04: [io  0x0458-0x047f]
[    8.957457] pnp 00:04: [io  0x0500-0x057f]
[    8.957462] pnp 00:04: [io  0x164e-0x164f]
[    8.957573] system 00:04: [io  0x0680-0x069f] has been reserved
[    8.957580] system 00:04: [io  0x1000-0x100f] has been reserved
[    8.957587] system 00:04: [io  0xffff] has been reserved
[    8.957593] system 00:04: [io  0xffff] has been reserved
[    8.957599] system 00:04: [io  0x0400-0x0453] has been reserved
[    8.957605] system 00:04: [io  0x0458-0x047f] has been reserved
[    8.957611] system 00:04: [io  0x0500-0x057f] has been reserved
[    8.957617] system 00:04: [io  0x164e-0x164f] has been reserved
[    8.957625] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    8.957647] pnp 00:05: [io  0x0070-0x0077]
[    8.957667] pnp 00:05: [irq 8]
[    8.957726] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    8.957800] pnp 00:06: [io  0x0454-0x0457]
[    8.957893] system 00:06: [io  0x0454-0x0457] has been reserved
[    8.957901] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    8.957923] pnp 00:07: [io  0x00f0-0x00ff]
[    8.957935] pnp 00:07: [irq 13]
[    8.958016] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    8.958059] pnp 00:08: [io  0x0010-0x001f]
[    8.958064] pnp 00:08: [io  0x0022-0x003f]
[    8.958068] pnp 00:08: [io  0x0044-0x005f]
[    8.958073] pnp 00:08: [io  0x0068-0x006f]
[    8.958078] pnp 00:08: [io  0x0072-0x007f]
[    8.958082] pnp 00:08: [io  0x0080]
[    8.958087] pnp 00:08: [io  0x0084-0x0086]
[    8.958091] pnp 00:08: [io  0x0088]
[    8.958096] pnp 00:08: [io  0x008c-0x008e]
[    8.958100] pnp 00:08: [io  0x0090-0x009f]
[    8.958105] pnp 00:08: [io  0x00a2-0x00bf]
[    8.958110] pnp 00:08: [io  0x00e0-0x00ef]
[    8.958114] pnp 00:08: [io  0x04d0-0x04d1]
[    8.958120] pnp 00:08: [mem 0xfe800000-0xfe802fff]
[    8.958219] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    8.958228] system 00:08: [mem 0xfe800000-0xfe802fff] has been reserved
[    8.958235] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    8.958274] pnp 00:09: [irq 12]
[    8.958344] pnp 00:09: Plug and Play ACPI device, IDs DLL0502 SYN0600 SYN0002 PNP0f13 (active)
[    8.958379] pnp 00:0a: [io  0x0060]
[    8.958383] pnp 00:0a: [io  0x0064]
[    8.958388] pnp 00:0a: [io  0x0062]
[    8.958392] pnp 00:0a: [io  0x0066]
[    8.958402] pnp 00:0a: [irq 1]
[    8.958463] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 (active)
[    8.958979] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
[    8.958985] pnp 00:0b: [mem 0xfed10000-0xfed17fff]
[    8.958990] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
[    8.958995] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
[    8.959000] pnp 00:0b: [mem 0xf8000000-0xfbffffff]
[    8.959009] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
[    8.959014] pnp 00:0b: [mem 0xfed90000-0xfed93fff]
[    8.959019] pnp 00:0b: [mem 0xfed45000-0xfed8ffff]
[    8.959024] pnp 00:0b: [mem 0xff000000-0xffffffff]
[    8.959029] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
[    8.959034] pnp 00:0b: [mem 0xdfa00000-0xdfa00fff]
[    8.959179] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    8.959186] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    8.959193] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    8.959199] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    8.959206] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    8.959213] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    8.959219] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    8.959226] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    8.959233] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    8.959240] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    8.959247] system 00:0b: [mem 0xdfa00000-0xdfa00fff] has been reserved
[    8.959255] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    8.959611] pnp 00:0c: [mem 0x20000000-0x201fffff]
[    8.959617] pnp 00:0c: [mem 0x40000000-0x401fffff]
[    8.959768] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
[    8.959774] system 00:0c: [mem 0x40000000-0x401fffff] has been reserved
[    8.959782] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    8.959903] pnp: PnP ACPI: found 13 devices
[    8.959907] ACPI: ACPI bus type pnp unregistered
[    8.959913] PnPBIOS: Disabled by ACPI PNP
[    8.999222] PCI: max bus depth: 1 pci_try_num: 2
[    8.999300] pci 0000:00:1c.0: PCI bridge to [bus 03-04]
[    8.999327] pci 0000:00:1c.1: PCI bridge to [bus 05-06]
[    8.999335] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    8.999353] pci 0000:00:1c.1:   bridge window [mem 0xf1100000-0xf11fffff 64bit pref]
[    8.999368] pci 0000:00:1c.3: PCI bridge to [bus 09-0a]
[    8.999380] pci 0000:00:1c.3:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    8.999399] pci 0000:00:1c.7: PCI bridge to [bus 11-1f]
[    8.999407] pci 0000:00:1c.7:   bridge window [io  0xc000-0xdfff]
[    8.999420] pci 0000:00:1c.7:   bridge window [mem 0xf6c00000-0xf7cfffff]
[    8.999431] pci 0000:00:1c.7:   bridge window [mem 0xf0000000-0xf10fffff 64bit pref]
[    8.999473] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.999484] pci 0000:00:1c.0: setting latency timer to 64
[    8.999507] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    8.999517] pci 0000:00:1c.1: setting latency timer to 64
[    8.999539] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    8.999548] pci 0000:00:1c.3: setting latency timer to 64
[    8.999563] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    8.999574] pci 0000:00:1c.7: setting latency timer to 64
[    8.999583] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    8.999589] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    8.999595] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    8.999601] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    8.999606] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    8.999612] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
[    8.999618] pci_bus 0000:00: resource 10 [mem 0x000e0000-0x000e3fff]
[    8.999623] pci_bus 0000:00: resource 11 [mem 0x000e4000-0x000e7fff]
[    8.999629] pci_bus 0000:00: resource 12 [mem 0xdfa00000-0xfeafffff]
[    8.999635] pci_bus 0000:00: resource 13 [mem 0xfed40000-0xfed44fff]
[    8.999641] pci_bus 0000:05: resource 0 [io  0xe000-0xefff]
[    8.999647] pci_bus 0000:05: resource 2 [mem 0xf1100000-0xf11fffff 64bit pref]
[    8.999653] pci_bus 0000:09: resource 1 [mem 0xf7d00000-0xf7dfffff]
[    8.999659] pci_bus 0000:11: resource 0 [io  0xc000-0xdfff]
[    8.999665] pci_bus 0000:11: resource 1 [mem 0xf6c00000-0xf7cfffff]
[    8.999671] pci_bus 0000:11: resource 2 [mem 0xf0000000-0xf10fffff 64bit pref]
[    8.999738] NET: Registered protocol family 2
[    8.999857] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.000222] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.000828] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.001094] TCP: Hash tables configured (established 131072 bind 65536)
[    9.001100] TCP reno registered
[    9.001106] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    9.001121] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    9.001247] NET: Registered protocol family 1
[    9.001274] pci 0000:00:02.0: Boot video device
[    9.241617] PCI: CLS 64 bytes, default 64
[    9.242727] audit: initializing netlink socket (disabled)
[    9.242744] type=2000 audit(1331420709.072:1): initialized
[    9.312007] highmem bounce pool size: 64 pages
[    9.312020] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    9.327182] VFS: Disk quotas dquot_6.5.2
[    9.327332] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.328573] fuse init (API version 7.17)
[    9.328792] msgmni has been set to 1648
[    9.329579] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    9.329642] io scheduler noop registered
[    9.329647] io scheduler deadline registered
[    9.329663] io scheduler cfq registered (default)
[    9.330174] pcieport 0000:00:1c.7: setting latency timer to 64
[    9.330283] pcieport 0000:00:1c.7: irq 40 for MSI/MSI-X
[    9.330492] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    9.330586] pciehp 0000:00:1c.7:pcie04: HPC vendor_id 8086 device_id 1c1e ss_vid 1028 ss_did 502
[    9.330659] pciehp 0000:00:1c.7:pcie04: service driver pciehp loaded
[    9.330676] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    9.330825] intel_idle: MWAIT substates: 0x21120
[    9.330830] intel_idle: v0.4 model 0x2A
[    9.330834] intel_idle: lapic_timer_reliable_states 0xffffffff
[    9.331000] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    9.331111] ACPI: AC Adapter [AC] (on-line)
[    9.331373] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    9.333183] ACPI: Lid Switch [LID0]
[    9.333289] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    9.333299] ACPI: Power Button [PWRB]
[    9.333398] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    9.333406] ACPI: Sleep Button [SBTN]
[    9.333520] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    9.333528] ACPI: Power Button [PWRF]
[    9.347124] thermal LNXTHERM:00: registered as thermal_zone0
[    9.347131] ACPI: Thermal Zone [THM] (54 C)
[    9.347192] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    9.347209] ACPI: Battery Slot [BAT0] (battery present)
[    9.347269] ERST: Table is not found!
[    9.347272] GHES: HEST is not enabled!
[    9.347442] isapnp: Scanning for PnP cards...
[    9.347477] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    9.502144] ACPI: Battery Slot [BAT0] (battery present)
[    9.701002] isapnp: No Plug & Play device found
[    9.737695] Linux agpgart interface v0.103
[    9.737923] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    9.738136] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    9.740959] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    9.741183] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    9.744589] brd: module loaded
[    9.746351] loop: module loaded
[    9.746642] ahci 0000:00:1f.2: version 3.0
[    9.746665] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    9.746765] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    9.746825] ahci: SSS flag set, parallel bus scan disabled
[    9.760841] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x11 impl SATA mode
[    9.760850] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems apst 
[    9.760861] ahci 0000:00:1f.2: setting latency timer to 64
[    9.770002] scsi0 : ahci
[    9.770219] scsi1 : ahci
[    9.770387] scsi2 : ahci
[    9.770549] scsi3 : ahci
[    9.770720] scsi4 : ahci
[    9.770881] scsi5 : ahci
[    9.771681] ata1: SATA max UDMA/133 abar m2048@0xf7e06000 port 0xf7e06100 irq 41
[    9.771687] ata2: DUMMY
[    9.771690] ata3: DUMMY
[    9.771693] ata4: DUMMY
[    9.771699] ata5: SATA max UDMA/133 abar m2048@0xf7e06000 port 0xf7e06300 irq 41
[    9.771704] ata6: DUMMY
[    9.772624] Fixed MDIO Bus: probed
[    9.772671] tun: Universal TUN/TAP device driver, 1.6
[    9.772675] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    9.772826] PPP generic driver version 2.4.2
[    9.773066] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    9.773101] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.773134] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    9.773142] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    9.773247] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    9.773296] ehci_hcd 0000:00:1a.0: debug port 2
[    9.777187] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    9.777220] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7e08000
[    9.792771] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    9.793086] hub 1-0:1.0: USB hub found
[    9.793096] hub 1-0:1.0: 2 ports detected
[    9.793247] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    9.793275] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    9.793283] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    9.793401] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    9.793444] ehci_hcd 0000:00:1d.0: debug port 2
[    9.797330] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    9.797360] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7e07000
[    9.812740] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    9.813015] hub 2-0:1.0: USB hub found
[    9.813024] hub 2-0:1.0: 2 ports detected
[    9.813159] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    9.813187] uhci_hcd: USB Universal Host Controller Interface driver
[    9.813298] usbcore: registered new interface driver libusual
[    9.813417] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2] at 0x60,0x64 irq 1,12
[    9.815626] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.815641] serio: i8042 AUX port at 0x60,0x64 irq 12
[    9.815930] mousedev: PS/2 mouse device common for all mice
[    9.816381] rtc_cmos 00:05: RTC can wake from S4
[    9.816587] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    9.816631] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    9.816785] device-mapper: uevent: version 1.0.3
[    9.816964] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    9.817037] EISA: Probing bus 0 at eisa.0
[    9.817042] EISA: Cannot allocate resource for mainboard
[    9.817047] Cannot allocate resource for EISA slot 1
[    9.817051] Cannot allocate resource for EISA slot 2
[    9.817055] Cannot allocate resource for EISA slot 3
[    9.817059] Cannot allocate resource for EISA slot 4
[    9.817063] Cannot allocate resource for EISA slot 5
[    9.817068] Cannot allocate resource for EISA slot 6
[    9.817072] Cannot allocate resource for EISA slot 7
[    9.817076] Cannot allocate resource for EISA slot 8
[    9.817080] EISA: Detected 0 cards.
[    9.817097] cpufreq-nforce2: No nForce2 chipset.
[    9.817442] cpuidle: using governor ladder
[    9.818002] cpuidle: using governor menu
[    9.818006] EFI Variables Facility v0.08 2004-May-17
[    9.818475] TCP cubic registered
[    9.818748] NET: Registered protocol family 10
[    9.819766] NET: Registered protocol family 17
[    9.819804] Registering the dns_resolver key type
[    9.819868] Using IPI No-Shortcut mode
[    9.820154] PM: Hibernation image not present or could not be loaded.
[    9.820176] registered taskstats version 1
[    9.834939] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    9.841745]   Magic number: 4:685:99
[    9.841923] rtc_cmos 00:05: setting system clock to 2012-03-10 23:05:10 UTC (1331420710)
[    9.843278] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    9.843279] EDD information not available.
[   10.088424] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   10.090666] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[   10.091089] ata1.00: ATA-8: ST9500325AS, D005DEM1, max UDMA/133
[   10.091100] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   10.093736] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[   10.094178] ata1.00: configured for UDMA/133
[   10.094493] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      D005 PQ: 0 ANSI: 5
[   10.094650] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   10.094662] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[   10.094769] sd 0:0:0:0: [sda] Write Protect is off
[   10.094773] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   10.094807] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.104393] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[   10.119684]  sda: sda1 sda2 sda3 < sda5 >
[   10.120789] sd 0:0:0:0: [sda] Attached SCSI disk
[   10.237136] hub 1-1:1.0: USB hub found
[   10.237280] hub 1-1:1.0: 6 ports detected
[   10.240142] Refined TSC clocksource calibration: 2394.560 MHz.
[   10.240153] Switching to clocksource tsc
[   10.347956] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[   10.411931] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   10.416170] ata5.00: ATAPI: TSSTcorp DVD+/-RW SN-208BB, D100, max UDMA/100
[   10.422539] ata5.00: configured for UDMA/100
[   10.439704] scsi 4:0:0:0: CD-ROM            TSSTcorp DVD+-RW SN-208BB D100 PQ: 0 ANSI: 5
[   10.453999] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   10.454009] cdrom: Uniform CD-ROM driver Revision: 3.20
[   10.454226] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   10.454357] sr 4:0:0:0: Attached scsi generic sg1 type 5
[   10.454718] Freeing unused kernel memory: 740k freed
[   10.454880] Write protecting the kernel text: 5812k
[   10.454963] Write protecting the kernel read-only data: 2372k
[   10.454964] NX-protecting the kernel data: 4428k
[   10.468772] udevd[110]: starting version 175
[   10.483768] hub 2-1:1.0: USB hub found
[   10.483844] hub 2-1:1.0: 8 ports detected
[   10.488956] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   10.488992] r8169 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.489025] r8169 0000:05:00.0: setting latency timer to 64
[   10.489096] r8169 0000:05:00.0: irq 42 for MSI/MSI-X
[   10.490574] [drm] Initialized drm 1.1.0 20060810
[   10.490999] r8169 0000:05:00.0: eth0: RTL8105e at 0xf8424000, d0:67:e5:f5:ac:e2, XID 00a00000 IRQ 42
[   10.495198] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.495203] i915 0000:00:02.0: setting latency timer to 64
[   10.505284] wmi: Mapper loaded
[   10.529973] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   10.529978] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.529980] [drm] Driver supports precise vblank timestamp query.
[   10.530011] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   10.555739] usb 1-1.2: new high-speed USB device number 3 using ehci_hcd
[   10.654359] Initializing USB Mass Storage driver...
[   10.654425] scsi6 : usb-storage 1-1.2:1.0
[   10.654545] usbcore: registered new interface driver usb-storage
[   10.654547] USB Mass Storage support registered.
[   10.654554] usbcore: registered new interface driver uas
[   10.723524] usb 1-1.4: new full-speed USB device number 4 using ehci_hcd
[   10.887444] usb 1-1.5: new high-speed USB device number 5 using ehci_hcd
[   11.142813] fbcon: inteldrmfb (fb0) is primary device
[   11.489035] Console: switching to colour frame buffer device 170x48
[   11.491647] fb0: inteldrmfb frame buffer device
[   11.491648] drm: registered panic notifier
[   11.492613] acpi device:33: registered as cooling_device4
[   11.492779] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   11.492850] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   11.492878] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.651732] scsi 6:0:0:0: Direct-Access     Kingston DT 101 G2        PMAP PQ: 0 ANSI: 0 CCS
[   11.652261] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   11.653394] sd 6:0:0:0: [sdb] 7827456 512-byte logical blocks: (4.00 GB/3.73 GiB)
[   11.654020] sd 6:0:0:0: [sdb] Write Protect is off
[   11.654028] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   11.654751] sd 6:0:0:0: [sdb] No Caching mode page present
[   11.654754] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   11.658499] sd 6:0:0:0: [sdb] No Caching mode page present
[   11.658502] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   11.660102]  sdb: sdb1
[   11.662737] sd 6:0:0:0: [sdb] No Caching mode page present
[   11.662739] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   11.662741] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   11.887365] Btrfs loaded
[   11.891198] xor: automatically using best checksumming function: pIII_sse
[   11.909591]    pIII_sse  : 12645.000 MB/sec
[   11.909593] xor: using function: pIII_sse (12645.000 MB/sec)
[   11.909994] device-mapper: dm-raid45: initialized v0.2594b
[   12.247970] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   12.758303] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   17.159229] kjournald starting.  Commit interval 5 seconds
[   17.160421] EXT3-fs (loop1): using internal journal
[   17.160435] EXT3-fs (loop1): mounted filesystem with ordered data mode
[   48.014513] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   48.044443] udevd[2502]: starting version 175
[   48.951981] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   48.960774] device-mapper: multipath: version 1.3.0 loaded
[   48.967222] input: Dell WMI hotkeys as /devices/virtual/input/input6
[   49.019148] init: failsafe main process (2686) killed by TERM signal
[   49.048024] Bluetooth: Core ver 2.16
[   49.048045] NET: Registered protocol family 31
[   49.048047] Bluetooth: HCI device and connection manager initialized
[   49.048049] Bluetooth: HCI socket layer initialized
[   49.048051] Bluetooth: L2CAP socket layer initialized
[   49.048056] Bluetooth: SCO socket layer initialized
[   49.057367] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   49.057724] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   49.057730] mei 0000:00:16.0: setting latency timer to 64
[   49.057787] mei 0000:00:16.0: irq 44 for MSI/MSI-X
[   49.071938] Linux video capture interface: v2.00
[   49.077420] cfg80211: Calling CRDA to update world regulatory domain
[   49.096727] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:643e)
[   49.098836] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   49.099716] usbcore: registered new interface driver btusb
[   49.112250] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input7
[   49.112328] usbcore: registered new interface driver uvcvideo
[   49.112330] USB Video Class driver (1.1.1)
[   49.201584] cfg80211: World regulatory domain updated:
[   49.201587] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   49.201591] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.201594] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   49.201597] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   49.201599] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.201602] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.207520] ath9k 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   49.207532] ath9k 0000:09:00.0: setting latency timer to 64
[   49.257992] ath: EEPROM regdomain: 0x60
[   49.257994] ath: EEPROM indicates we should expect a direct regpair map
[   49.257997] ath: Country alpha2 being used: 00
[   49.257998] ath: Regpair used: 0x60
[   49.258000] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   49.258002] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   49.258004] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   49.258005] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   49.258007] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   49.258009] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   49.258010] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   49.258012] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   49.258013] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   49.258015] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   49.258016] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   49.258018] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   49.258020] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   49.258021] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   49.258023] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   49.258025] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   49.258026] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   49.258028] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   49.258029] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   49.258031] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   49.258032] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   49.258034] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   49.258035] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   49.258037] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   49.258039] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   49.258040] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   49.258042] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   49.258044] cfg80211: 2474000 KHz - 2494000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   49.259504] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   49.270685] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   49.270740] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   49.270766] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   49.273702] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   49.274282] Registered led device: ath9k-phy0
[   49.274290] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf9220000, irq=19
[   49.579665] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   49.579669] Bluetooth: BNEP filters: protocol multicast
[   49.634910] Bluetooth: RFCOMM TTY layer initialized
[   49.634915] Bluetooth: RFCOMM socket layer initialized
[   49.634917] Bluetooth: RFCOMM ver 1.11
[   49.658363] init: hybrid-gfx main process (2964) terminated with status 127
[   49.955346] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input8
[   49.968004] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input9
[   50.230100] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   50.230195] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   50.230286] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   50.230354] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   51.547271] lp: driver loaded but no devices found
[   51.612045] ppdev: user-space parallel port driver
[   51.685293] r8169 0000:05:00.0: eth0: link down
[   51.685470] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   51.685835] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   51.728165] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.731130] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   56.737642] init: plymouth-stop pre-start process (4165) terminated with status 1
```

64 bits
```
ubuntu@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:       3956180    1922872    2033308          0     175056    1103488
-/+ buffers/cache:     644328    3311852
Swap:            0          0          0


ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3863       1872       1990          0        170       1072
-/+ buffers/cache:        629       3233
Swap:            0          0          0


ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.2.0-17-generic #27-Ubuntu SMP Fri Feb 24 15:37:36 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


ubuntu@ubuntu:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-17-generic (buildd@allspice) (gcc version 4.6.2 (Ubuntu/Linaro 4.6.2-16ubuntu1) ) #27-Ubuntu SMP Fri Feb 24 15:37:36 UTC 2012 (Ubuntu 3.2.0-17.27-generic 3.2.6)
[    0.000000] Command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000da4ea000 (usable)
[    0.000000]  BIOS-e820: 00000000da4ea000 - 00000000da52d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000da52d000 - 00000000da798000 (usable)
[    0.000000]  BIOS-e820: 00000000da798000 - 00000000da967000 (reserved)
[    0.000000]  BIOS-e820: 00000000da967000 - 00000000dacbc000 (usable)
[    0.000000]  BIOS-e820: 00000000dacbc000 - 00000000dad68000 (reserved)
[    0.000000]  BIOS-e820: 00000000dad68000 - 00000000dafe8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dafe8000 - 00000000db000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000db800000 - 00000000dfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000011fe00000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Dell Inc. Inspiron N4050/0X0DC1, BIOS A06 11/14/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x11fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FE0000000 write-back
[    0.000000]   2 base 0DB800000 mask FFF800000 uncachable
[    0.000000]   3 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   5 base 11FE00000 mask FFFE00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 4, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 5, base: 4606MB, range: 2MB, type UC
[    0.000000] total RAM covered: 4022M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K  chunk_size: 128M    num_reg: 7      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 4, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 5, base: 4GB, range: 512MB, type WB
[    0.000000] reg 6, base: 4606MB, range: 2MB, type UC
[    0.000000] e820 update range: 00000000db800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdacbc max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fd1b0] fd1b0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000dacbc000
[    0.000000]  0000000000 - 00dac00000 page 2M
[    0.000000]  00dac00000 - 00dacbc000 page 4k
[    0.000000] kernel direct mapping tables up to dacbc000 @ 1fffa000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000011fe00000
[    0.000000]  0100000000 - 011fe00000 page 2M
[    0.000000] kernel direct mapping tables up to 11fe00000 @ dacb6000-dacbc000
[    0.000000] RAMDISK: 7f1cb000 - 80000000
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v02   DELL)
[    0.000000] ACPI: XSDT 00000000dafe8078 0006C (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000daff1c38 000F4 (v04   DELL     WN09 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000dafe8170 09AC8 (v02   DELL     WN09 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000dafe4f80 00040
[    0.000000] ACPI: APIC 00000000daff1d30 00072 (v03   DELL     WN09 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000daff1da8 0003C (v01   DELL     WN09 01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000daff1de8 004B0 (v01 TrmRef PtidDevc 00001000 INTL 20091112)
[    0.000000] ACPI: SLIC 00000000daff2298 00176 (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: HPET 00000000daff2410 00038 (v01   DELL     WN09 01072009 AMI. 00000004)
[    0.000000] ACPI: SSDT 00000000daff2448 007C2 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000daff2c10 00996 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: OSFR 00000000daff35a8 0008C (v01 DELL    M08     07DB0B0E ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000011fe00000
[    0.000000] Initmem setup node 0 0000000000000000-000000011fe00000
[    0.000000]   NODE_DATA [000000011fdfb000 - 000000011fdfffff]
[    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011b400000-ffff88011f3fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0011fe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000da4ea
[    0.000000]     0: 0x000da52d -> 0x000da798
[    0.000000]     0: 0x000da967 -> 0x000dacbc
[    0.000000]     0: 0x00100000 -> 0x0011fe00
[    0.000000] On node 0 totalpages: 1025079
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 874218 pages, LIFO batch:31
[    0.000000]   Normal zone: 2040 pages used for memmap
[    0.000000]   Normal zone: 128520 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
[    0.000000] PM: Registered nosave memory: 00000000da4ea000 - 00000000da52d000
[    0.000000] PM: Registered nosave memory: 00000000da798000 - 00000000da967000
[    0.000000] PM: Registered nosave memory: 00000000dacbc000 - 00000000dad68000
[    0.000000] PM: Registered nosave memory: 00000000dad68000 - 00000000dafe8000
[    0.000000] PM: Registered nosave memory: 00000000dafe8000 - 00000000db000000
[    0.000000] PM: Registered nosave memory: 00000000db000000 - 00000000db800000
[    0.000000] PM: Registered nosave memory: 00000000db800000 - 00000000dfa00000
[    0.000000] PM: Registered nosave memory: 00000000dfa00000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed04000
[    0.000000] PM: Registered nosave memory: 00000000fed04000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at dfa00000 (gap: dfa00000:18600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88011fa00000 s83072 r8192 d23424 u524288
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1006650
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3937892k/4716544k available (6552k kernel code, 616228k absent, 162424k reserved, 6650k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2394.788 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4789.57 BogoMIPS (lpj=9579152)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000025] Security Framework initialized
[    0.000037] AppArmor: AppArmor initialized
[    0.000038] Yama: becoming mindful.
[    0.000421] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001469] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001908] Mount-cache hash table entries: 256
[    0.002006] Initializing cgroup subsys cpuacct
[    0.002010] Initializing cgroup subsys memory
[    0.002017] Initializing cgroup subsys devices
[    0.002019] Initializing cgroup subsys freezer
[    0.002021] Initializing cgroup subsys blkio
[    0.002025] Initializing cgroup subsys perf_event
[    0.002049] CPU: Physical Processor ID: 0
[    0.002050] CPU: Processor Core ID: 0
[    0.002054] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002055] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002058] mce: CPU supports 7 MCE banks
[    0.002070] CPU0: Thermal monitoring enabled (TM1)
[    0.002076] using mwait in idle threads.
[    0.004509] ACPI: Core revision 20110623
[    0.014366] ftrace: allocating 27009 entries in 106 pages
[    0.042991] x2apic not enabled, IRQ remapping init failed
[    0.043454] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.083091] CPU0: Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz stepping 07
[    0.187677] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.187690] PEBS disabled due to CPU errata.
[    0.187696] ... version:                3
[    0.187700] ... bit width:              48
[    0.187703] ... generic registers:      4
[    0.187706] ... value mask:             0000ffffffffffff
[    0.187710] ... max period:             000000007fffffff
[    0.187714] ... fixed-purpose events:   3
[    0.187717] ... event mask:             000000070000000f
[    0.188019] NMI watchdog enabled, takes one hw-pmu counter.
[    0.188203] Booting Node   0, Processors  #1
[    0.188210] smpboot cpu 1: start_ip = 98000
[    0.295706] NMI watchdog enabled, takes one hw-pmu counter.
[    0.295896]  #2
[    0.295900] smpboot cpu 2: start_ip = 98000
[    0.403551] NMI watchdog enabled, takes one hw-pmu counter.
[    0.403746]  #3 Ok.
[    0.403750] smpboot cpu 3: start_ip = 98000
[    0.511335] NMI watchdog enabled, takes one hw-pmu counter.
[    0.511399] Brought up 4 CPUs
[    0.511405] Total of 4 processors activated (19156.52 BogoMIPS).
[    0.520936] devtmpfs: initialized
[    0.522856] EVM: security.selinux
[    0.522860] EVM: security.SMACK64
[    0.522863] EVM: security.capability
[    0.522923] PM: Registering ACPI NVS region at da4ea000 (274432 bytes)
[    0.522942] PM: Registering ACPI NVS region at dad68000 (2621440 bytes)
[    0.525044] print_constraints: dummy: 
[    0.525092] RTC time: 21:49:51, date: 03/10/12
[    0.525171] NET: Registered protocol family 16
[    0.525400] Trying to unpack rootfs image as initramfs...
[    0.525416] ACPI: bus type pci registered
[    0.525552] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.525560] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.566311] PCI: Using configuration type 1 for base access
[    0.568559] bio: create slab <bio-0> at 0
[    0.568743] ACPI: Added _OSI(Module Device)
[    0.568748] ACPI: Added _OSI(Processor Device)
[    0.568753] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.568757] ACPI: Added _OSI(Processor Aggregator Device)
[    0.572609] ACPI: EC: Look up EC in DSDT
[    0.576782] ACPI: Executed 1 blocks of module-level executable AML code
[    0.586100] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    6.392793] sched: RT throttling activated
[    6.431179] ACPI: SSDT 00000000dad51698 0064F (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    6.432223] ACPI: Dynamic OEM Table Load:
[    6.432231] ACPI: SSDT           (null) 0064F (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    6.446701] ACPI: SSDT 00000000dad52a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    6.447787] ACPI: Dynamic OEM Table Load:
[    6.447794] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    9.429757] ACPI: SSDT 00000000dad50d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    9.430771] ACPI: Dynamic OEM Table Load:
[    9.430778] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    9.445132] Freeing initrd memory: 14548k freed
[    9.450820] ACPI: Interpreter enabled
[    9.450830] ACPI: (supports S0 S1 S3 S4 S5)
[    9.450899] ACPI: Using IOAPIC for interrupt routing
[    9.490372] ACPI: No dock devices found.
[    9.490378] HEST: Table not found.
[    9.490385] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    9.491207] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    9.492381] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    9.492388] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    9.492394] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    9.492401] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    9.492406] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    9.492412] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    9.492417] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    9.492423] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    9.492429] pci_root PNP0A08:00: host bridge window [mem 0xdfa00000-0xfeafffff]
[    9.492435] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    9.492465] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    9.492558] pci 0000:00:02.0: [8086:0116] type 0 class 0x000300
[    9.492587] pci 0000:00:02.0: reg 10: [mem 0xf6800000-0xf6bfffff 64bit]
[    9.492604] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    9.492617] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    9.492749] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    9.492798] pci 0000:00:16.0: reg 10: [mem 0xf7e0a000-0xf7e0a00f 64bit]
[    9.492955] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    9.492965] pci 0000:00:16.0: PME# disabled
[    9.493034] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    9.493078] pci 0000:00:1a.0: reg 10: [mem 0xf7e08000-0xf7e083ff]
[    9.493266] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    9.493275] pci 0000:00:1a.0: PME# disabled
[    9.493338] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    9.493372] pci 0000:00:1b.0: reg 10: [mem 0xf7e00000-0xf7e03fff 64bit]
[    9.493529] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    9.493537] pci 0000:00:1b.0: PME# disabled
[    9.493583] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    9.493753] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    9.493762] pci 0000:00:1c.0: PME# disabled
[    9.493810] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    9.493980] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    9.493988] pci 0000:00:1c.1: PME# disabled
[    9.494038] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
[    9.494208] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    9.494216] pci 0000:00:1c.3: PME# disabled
[    9.494278] pci 0000:00:1c.7: [8086:1c1e] type 1 class 0x000604
[    9.494449] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    9.494457] pci 0000:00:1c.7: PME# disabled
[    9.494515] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    9.494559] pci 0000:00:1d.0: reg 10: [mem 0xf7e07000-0xf7e073ff]
[    9.494745] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    9.494754] pci 0000:00:1d.0: PME# disabled
[    9.494800] pci 0000:00:1f.0: [8086:1c4b] type 0 class 0x000601
[    9.495040] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    9.495085] pci 0000:00:1f.2: reg 10: [io  0xf0b0-0xf0b7]
[    9.495104] pci 0000:00:1f.2: reg 14: [io  0xf0a0-0xf0a3]
[    9.495123] pci 0000:00:1f.2: reg 18: [io  0xf090-0xf097]
[    9.495143] pci 0000:00:1f.2: reg 1c: [io  0xf080-0xf083]
[    9.495162] pci 0000:00:1f.2: reg 20: [io  0xf060-0xf07f]
[    9.495181] pci 0000:00:1f.2: reg 24: [mem 0xf7e06000-0xf7e067ff]
[    9.495290] pci 0000:00:1f.2: PME# supported from D3hot
[    9.495299] pci 0000:00:1f.2: PME# disabled
[    9.495336] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    9.495371] pci 0000:00:1f.3: reg 10: [mem 0xf7e05000-0xf7e050ff 64bit]
[    9.495419] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    9.495572] pci 0000:00:1c.0: PCI bridge to [bus 03-04]
[    9.495722] pci 0000:05:00.0: [10ec:8136] type 0 class 0x000200
[    9.495757] pci 0000:05:00.0: reg 10: [io  0xe000-0xe0ff]
[    9.495815] pci 0000:05:00.0: reg 18: [mem 0xf1104000-0xf1104fff 64bit pref]
[    9.495853] pci 0000:05:00.0: reg 20: [mem 0xf1100000-0xf1103fff 64bit pref]
[    9.496008] pci 0000:05:00.0: supports D1 D2
[    9.496012] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    9.496023] pci 0000:05:00.0: PME# disabled
[    9.501342] pci 0000:00:1c.1: PCI bridge to [bus 05-06]
[    9.501352] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    9.501370] pci 0000:00:1c.1:   bridge window [mem 0xf1100000-0xf11fffff 64bit pref]
[    9.501506] pci 0000:09:00.0: [168c:002b] type 0 class 0x000280
[    9.501554] pci 0000:09:00.0: reg 10: [mem 0xf7d00000-0xf7d0ffff 64bit]
[    9.501769] pci 0000:09:00.0: supports D1
[    9.501774] pci 0000:09:00.0: PME# supported from D0 D1 D3hot
[    9.501784] pci 0000:09:00.0: PME# disabled
[    9.509322] pci 0000:00:1c.3: PCI bridge to [bus 09-0a]
[    9.509336] pci 0000:00:1c.3:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    9.509440] pci 0000:00:1c.7: PCI bridge to [bus 11-1f]
[    9.509450] pci 0000:00:1c.7:   bridge window [io  0xc000-0xdfff]
[    9.509459] pci 0000:00:1c.7:   bridge window [mem 0xf6c00000-0xf7cfffff]
[    9.509473] pci 0000:00:1c.7:   bridge window [mem 0xf0000000-0xf10fffff 64bit pref]
[    9.509523] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.509838] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    9.509922] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    9.510017] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    9.510112] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08._PRT]
[    9.510436]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    9.510910]  pci0000:00: ACPI _OSC control (0x19) granted
[    9.518890] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    9.519006] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 10 11 12 14 15)
[    9.519116] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    9.519227] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    9.519335] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    9.519444] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    9.519552] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    9.519657] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 10 11 12 14 15)
[    9.519910] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    9.519927] vgaarb: loaded
[    9.519930] vgaarb: bridge control possible 0000:00:02.0
[    9.520153] i2c-core: driver [aat2870] using legacy suspend method
[    9.520157] i2c-core: driver [aat2870] using legacy resume method
[    9.520303] SCSI subsystem initialized
[    9.520414] libata version 3.00 loaded.
[    9.520512] usbcore: registered new interface driver usbfs
[    9.520535] usbcore: registered new interface driver hub
[    9.520589] usbcore: registered new device driver usb
[    9.520767] PCI: Using ACPI for IRQ routing
[    9.524420] PCI: pci_cache_line_size set to 64 bytes
[    9.524541] reserve RAM buffer: 000000000009d400 - 000000000009ffff 
[    9.524547] reserve RAM buffer: 00000000da4ea000 - 00000000dbffffff 
[    9.524555] reserve RAM buffer: 00000000da798000 - 00000000dbffffff 
[    9.524562] reserve RAM buffer: 00000000dacbc000 - 00000000dbffffff 
[    9.524568] reserve RAM buffer: 000000011fe00000 - 000000011fffffff 
[    9.524793] NetLabel: Initializing
[    9.524797] NetLabel:  domain hash size = 128
[    9.524801] NetLabel:  protocols = UNLABELED CIPSOv4
[    9.524824] NetLabel:  unlabeled traffic allowed by default
[    9.524933] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    9.524949] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    9.526983] Switching to clocksource hpet
[    9.541523] AppArmor: AppArmor Filesystem Enabled
[    9.541572] pnp: PnP ACPI init
[    9.541606] ACPI: bus type pnp registered
[    9.542263] pnp 00:00: [bus 00-3e]
[    9.542270] pnp 00:00: [io  0x0000-0x0cf7 window]
[    9.542275] pnp 00:00: [io  0x0cf8-0x0cff]
[    9.542280] pnp 00:00: [io  0x0d00-0xffff window]
[    9.542286] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    9.542291] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    9.542296] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    9.542301] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    9.542306] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    9.542311] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    9.542316] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    9.542321] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    9.542326] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    9.542331] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    9.542336] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    9.542341] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    9.542346] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    9.542351] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    9.542356] pnp 00:00: [mem 0xdfa00000-0xfeafffff window]
[    9.542361] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    9.542530] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    9.542566] pnp 00:01: [io  0x0000-0x001f]
[    9.542571] pnp 00:01: [io  0x0081-0x0091]
[    9.542575] pnp 00:01: [io  0x0093-0x009f]
[    9.542579] pnp 00:01: [io  0x00c0-0x00df]
[    9.542585] pnp 00:01: [dma 4]
[    9.542638] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    9.542658] pnp 00:02: [mem 0xff000000-0xffffffff]
[    9.542708] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    9.542888] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    9.542938] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    9.542968] pnp 00:04: [io  0x002e-0x002f]
[    9.542972] pnp 00:04: [io  0x004e-0x004f]
[    9.542976] pnp 00:04: [io  0x0061]
[    9.542980] pnp 00:04: [io  0x0063]
[    9.542984] pnp 00:04: [io  0x0065]
[    9.542988] pnp 00:04: [io  0x0067]
[    9.542991] pnp 00:04: [io  0x0070]
[    9.542995] pnp 00:04: [io  0x0080]
[    9.542999] pnp 00:04: [io  0x0092]
[    9.543003] pnp 00:04: [io  0x00b2-0x00b3]
[    9.543007] pnp 00:04: [io  0x0680-0x069f]
[    9.543012] pnp 00:04: [io  0x1000-0x100f]
[    9.543016] pnp 00:04: [io  0xffff]
[    9.543020] pnp 00:04: [io  0xffff]
[    9.543024] pnp 00:04: [io  0x0400-0x0453]
[    9.543028] pnp 00:04: [io  0x0458-0x047f]
[    9.543032] pnp 00:04: [io  0x0500-0x057f]
[    9.543036] pnp 00:04: [io  0x164e-0x164f]
[    9.543139] system 00:04: [io  0x0680-0x069f] has been reserved
[    9.543146] system 00:04: [io  0x1000-0x100f] has been reserved
[    9.543152] system 00:04: [io  0xffff] has been reserved
[    9.543157] system 00:04: [io  0xffff] has been reserved
[    9.543163] system 00:04: [io  0x0400-0x0453] has been reserved
[    9.543168] system 00:04: [io  0x0458-0x047f] has been reserved
[    9.543174] system 00:04: [io  0x0500-0x057f] has been reserved
[    9.543180] system 00:04: [io  0x164e-0x164f] has been reserved
[    9.543187] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    9.543207] pnp 00:05: [io  0x0070-0x0077]
[    9.543227] pnp 00:05: [irq 8]
[    9.543279] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    9.543348] pnp 00:06: [io  0x0454-0x0457]
[    9.543426] system 00:06: [io  0x0454-0x0457] has been reserved
[    9.543434] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    9.543454] pnp 00:07: [io  0x00f0-0x00ff]
[    9.543465] pnp 00:07: [irq 13]
[    9.543514] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    9.543551] pnp 00:08: [io  0x0010-0x001f]
[    9.543556] pnp 00:08: [io  0x0022-0x003f]
[    9.543560] pnp 00:08: [io  0x0044-0x005f]
[    9.543564] pnp 00:08: [io  0x0068-0x006f]
[    9.543568] pnp 00:08: [io  0x0072-0x007f]
[    9.543572] pnp 00:08: [io  0x0080]
[    9.543576] pnp 00:08: [io  0x0084-0x0086]
[    9.543580] pnp 00:08: [io  0x0088]
[    9.543584] pnp 00:08: [io  0x008c-0x008e]
[    9.543589] pnp 00:08: [io  0x0090-0x009f]
[    9.543593] pnp 00:08: [io  0x00a2-0x00bf]
[    9.543597] pnp 00:08: [io  0x00e0-0x00ef]
[    9.543601] pnp 00:08: [io  0x04d0-0x04d1]
[    9.543609] pnp 00:08: [mem 0xfe800000-0xfe802fff]
[    9.543697] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    9.543706] system 00:08: [mem 0xfe800000-0xfe802fff] has been reserved
[    9.543713] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    9.543750] pnp 00:09: [irq 12]
[    9.543809] pnp 00:09: Plug and Play ACPI device, IDs DLL0502 SYN0600 SYN0002 PNP0f13 (active)
[    9.543841] pnp 00:0a: [io  0x0060]
[    9.543846] pnp 00:0a: [io  0x0064]
[    9.543849] pnp 00:0a: [io  0x0062]
[    9.543853] pnp 00:0a: [io  0x0066]
[    9.543863] pnp 00:0a: [irq 1]
[    9.543914] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 (active)
[    9.544369] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
[    9.544374] pnp 00:0b: [mem 0xfed10000-0xfed17fff]
[    9.544379] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
[    9.544383] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
[    9.544388] pnp 00:0b: [mem 0xf8000000-0xfbffffff]
[    9.544392] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
[    9.544397] pnp 00:0b: [mem 0xfed90000-0xfed93fff]
[    9.544402] pnp 00:0b: [mem 0xfed45000-0xfed8ffff]
[    9.544406] pnp 00:0b: [mem 0xff000000-0xffffffff]
[    9.544411] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
[    9.544415] pnp 00:0b: [mem 0xdfa00000-0xdfa00fff]
[    9.544537] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    9.544544] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    9.544550] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    9.544556] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    9.544562] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    9.544568] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    9.544574] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    9.544580] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    9.544586] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    9.544593] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    9.544599] system 00:0b: [mem 0xdfa00000-0xdfa00fff] has been reserved
[    9.544606] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    9.544922] pnp 00:0c: [mem 0x20000000-0x201fffff]
[    9.544927] pnp 00:0c: [mem 0x40000000-0x401fffff]
[    9.545055] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
[    9.545061] system 00:0c: [mem 0x40000000-0x401fffff] has been reserved
[    9.545068] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    9.545184] pnp: PnP ACPI: found 13 devices
[    9.545188] ACPI: ACPI bus type pnp unregistered
[    9.554768] PCI: max bus depth: 1 pci_try_num: 2
[    9.554841] pci 0000:00:1c.0: PCI bridge to [bus 03-04]
[    9.554867] pci 0000:00:1c.1: PCI bridge to [bus 05-06]
[    9.554874] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    9.554891] pci 0000:00:1c.1:   bridge window [mem 0xf1100000-0xf11fffff 64bit pref]
[    9.554906] pci 0000:00:1c.3: PCI bridge to [bus 09-0a]
[    9.554917] pci 0000:00:1c.3:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    9.554936] pci 0000:00:1c.7: PCI bridge to [bus 11-1f]
[    9.554943] pci 0000:00:1c.7:   bridge window [io  0xc000-0xdfff]
[    9.554955] pci 0000:00:1c.7:   bridge window [mem 0xf6c00000-0xf7cfffff]
[    9.554966] pci 0000:00:1c.7:   bridge window [mem 0xf0000000-0xf10fffff 64bit pref]
[    9.555007] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.555018] pci 0000:00:1c.0: setting latency timer to 64
[    9.555041] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.555050] pci 0000:00:1c.1: setting latency timer to 64
[    9.555069] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    9.555079] pci 0000:00:1c.3: setting latency timer to 64
[    9.555094] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    9.555104] pci 0000:00:1c.7: setting latency timer to 64
[    9.555113] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    9.555119] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    9.555124] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    9.555129] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    9.555134] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    9.555140] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
[    9.555145] pci_bus 0000:00: resource 10 [mem 0x000e0000-0x000e3fff]
[    9.555150] pci_bus 0000:00: resource 11 [mem 0x000e4000-0x000e7fff]
[    9.555156] pci_bus 0000:00: resource 12 [mem 0xdfa00000-0xfeafffff]
[    9.555161] pci_bus 0000:00: resource 13 [mem 0xfed40000-0xfed44fff]
[    9.555167] pci_bus 0000:05: resource 0 [io  0xe000-0xefff]
[    9.555174] pci_bus 0000:05: resource 2 [mem 0xf1100000-0xf11fffff 64bit pref]
[    9.555180] pci_bus 0000:09: resource 1 [mem 0xf7d00000-0xf7dfffff]
[    9.555185] pci_bus 0000:11: resource 0 [io  0xc000-0xdfff]
[    9.555191] pci_bus 0000:11: resource 1 [mem 0xf6c00000-0xf7cfffff]
[    9.555197] pci_bus 0000:11: resource 2 [mem 0xf0000000-0xf10fffff 64bit pref]
[    9.555262] NET: Registered protocol family 2
[    9.555616] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.557971] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    9.561604] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    9.561921] TCP: Hash tables configured (established 524288 bind 65536)
[    9.561927] TCP reno registered
[    9.561950] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    9.562002] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    9.562165] NET: Registered protocol family 1
[    9.562198] pci 0000:00:02.0: Boot video device
[    9.802071] PCI: CLS 64 bytes, default 64
[    9.802076] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    9.802082] Placing 64MB software IO TLB between ffff8800d64ea000 - ffff8800da4ea000
[    9.802087] software IO TLB at phys 0xd64ea000 - 0xda4ea000
[    9.803145] audit: initializing netlink socket (disabled)
[    9.803162] type=2000 audit(1331416200.632:1): initialized
[    9.874289] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    9.899757] VFS: Disk quotas dquot_6.5.2
[    9.899880] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    9.900983] fuse init (API version 7.17)
[    9.901183] msgmni has been set to 7719
[    9.901924] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    9.901980] io scheduler noop registered
[    9.901987] io scheduler deadline registered
[    9.902063] io scheduler cfq registered (default)
[    9.902543] pcieport 0000:00:1c.7: setting latency timer to 64
[    9.902648] pcieport 0000:00:1c.7: irq 40 for MSI/MSI-X
[    9.902835] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    9.902923] pciehp 0000:00:1c.7:pcie04: HPC vendor_id 8086 device_id 1c1e ss_vid 1028 ss_did 502
[    9.902991] pciehp 0000:00:1c.7:pcie04: service driver pciehp loaded
[    9.903005] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    9.903114] intel_idle: MWAIT substates: 0x21120
[    9.903118] intel_idle: v0.4 model 0x2A
[    9.903121] intel_idle: lapic_timer_reliable_states 0xffffffff
[    9.903289] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    9.903391] ACPI: AC Adapter [AC] (on-line)
[    9.903638] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    9.905494] ACPI: Lid Switch [LID0]
[    9.905591] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    9.905600] ACPI: Power Button [PWRB]
[    9.905686] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    9.905694] ACPI: Sleep Button [SBTN]
[    9.905776] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    9.905782] ACPI: Power Button [PWRF]
[    9.919458] thermal LNXTHERM:00: registered as thermal_zone0
[    9.919465] ACPI: Thermal Zone [THM] (58 C)
[    9.919521] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    9.919538] ACPI: Battery Slot [BAT0] (battery present)
[    9.919591] ERST: Table is not found!
[    9.919594] GHES: HEST is not enabled!
[    9.919746] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    9.958608] ACPI: Battery Slot [BAT0] (battery present)
[   10.034620] Linux agpgart interface v0.103
[   10.034795] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[   10.035176] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[   10.038592] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[   10.038827] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   10.041964] brd: module loaded
[   10.043574] loop: module loaded
[   10.043833] ahci 0000:00:1f.2: version 3.0
[   10.043856] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   10.043956] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[   10.044011] ahci: SSS flag set, parallel bus scan disabled
[   10.057683] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x11 impl SATA mode
[   10.057692] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems apst 
[   10.057703] ahci 0000:00:1f.2: setting latency timer to 64
[   10.066712] scsi0 : ahci
[   10.066892] scsi1 : ahci
[   10.067044] scsi2 : ahci
[   10.067187] scsi3 : ahci
[   10.067328] scsi4 : ahci
[   10.067465] scsi5 : ahci
[   10.068138] ata1: SATA max UDMA/133 abar m2048@0xf7e06000 port 0xf7e06100 irq 41
[   10.068144] ata2: DUMMY
[   10.068147] ata3: DUMMY
[   10.068150] ata4: DUMMY
[   10.068155] ata5: SATA max UDMA/133 abar m2048@0xf7e06000 port 0xf7e06300 irq 41
[   10.068159] ata6: DUMMY
[   10.068931] Fixed MDIO Bus: probed
[   10.068974] tun: Universal TUN/TAP device driver, 1.6
[   10.068978] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   10.069097] PPP generic driver version 2.4.2
[   10.069324] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   10.069356] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.069389] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[   10.069396] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[   10.069506] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   10.069554] ehci_hcd 0000:00:1a.0: debug port 2
[   10.073434] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[   10.073464] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7e08000
[   10.085615] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[   10.085898] hub 1-0:1.0: USB hub found
[   10.085907] hub 1-0:1.0: 2 ports detected
[   10.086051] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   10.086081] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[   10.086088] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[   10.086194] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   10.086236] ehci_hcd 0000:00:1d.0: debug port 2
[   10.090132] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[   10.090160] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7e07000
[   10.105583] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[   10.105836] hub 2-0:1.0: USB hub found
[   10.105844] hub 2-0:1.0: 2 ports detected
[   10.105965] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   10.105989] uhci_hcd: USB Universal Host Controller Interface driver
[   10.106086] usbcore: registered new interface driver libusual
[   10.106172] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2] at 0x60,0x64 irq 1,12
[   10.108324] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.108338] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.108607] mousedev: PS/2 mouse device common for all mice
[   10.109037] rtc_cmos 00:05: RTC can wake from S4
[   10.109226] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[   10.109266] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[   10.109430] device-mapper: uevent: version 1.0.3
[   10.109598] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[   10.109881] cpuidle: using governor ladder
[   10.110311] cpuidle: using governor menu
[   10.110315] EFI Variables Facility v0.08 2004-May-17
[   10.110775] TCP cubic registered
[   10.111014] NET: Registered protocol family 10
[   10.111922] NET: Registered protocol family 17
[   10.111951] Registering the dns_resolver key type
[   10.112256] PM: Hibernation image not present or could not be loaded.
[   10.112281] registered taskstats version 1
[   10.132684] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[   10.137196]   Magic number: 4:747:853
[   10.137392] rtc_cmos 00:05: setting system clock to 2012-03-10 21:50:01 UTC (1331416201)
[   10.139155] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   10.139156] EDD information not available.
[   10.385267] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   10.387523] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[   10.387946] ata1.00: ATA-8: ST9500325AS, D005DEM1, max UDMA/133
[   10.387956] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   10.390590] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[   10.391031] ata1.00: configured for UDMA/133
[   10.391363] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      D005 PQ: 0 ANSI: 5
[   10.391513] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   10.391525] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[   10.391623] sd 0:0:0:0: [sda] Write Protect is off
[   10.391626] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   10.391662] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.397207] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[   10.409955]  sda: sda1 sda2 sda3 < sda5 >
[   10.410443] sd 0:0:0:0: [sda] Attached SCSI disk
[   10.529995] hub 1-1:1.0: USB hub found
[   10.530155] hub 1-1:1.0: 6 ports detected
[   10.640883] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[   10.708786] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   10.712988] ata5.00: ATAPI: TSSTcorp DVD+/-RW SN-208BB, D100, max UDMA/100
[   10.719808] ata5.00: configured for UDMA/100
[   10.740267] scsi 4:0:0:0: CD-ROM            TSSTcorp DVD+-RW SN-208BB D100 PQ: 0 ANSI: 5
[   10.751308] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   10.751319] cdrom: Uniform CD-ROM driver Revision: 3.20
[   10.751538] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   10.751673] sr 4:0:0:0: Attached scsi generic sg1 type 5
[   10.753105] Freeing unused kernel memory: 920k freed
[   10.753190] Write protecting the kernel read-only data: 12288k
[   10.757068] Freeing unused kernel memory: 1620k freed
[   10.759875] Freeing unused kernel memory: 1200k freed
[   10.773121] hub 2-1:1.0: USB hub found
[   10.773221] hub 2-1:1.0: 8 ports detected
[   10.774246] udevd[112]: starting version 175
[   10.791164] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   10.791202] r8169 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.791241] r8169 0000:05:00.0: setting latency timer to 64
[   10.791310] r8169 0000:05:00.0: irq 42 for MSI/MSI-X
[   10.791691] r8169 0000:05:00.0: eth0: RTL8105e at 0xffffc9000104a000, d0:67:e5:f5:ac:e2, XID 00a00000 IRQ 42
[   10.795160] [drm] Initialized drm 1.1.0 20060810
[   10.799147] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.799153] i915 0000:00:02.0: setting latency timer to 64
[   10.801588] Refined TSC clocksource calibration: 2394.560 MHz.
[   10.801595] Switching to clocksource tsc
[   10.820043] wmi: Mapper loaded
[   10.844619] usb 1-1.2: new high-speed USB device number 3 using ehci_hcd
[   10.862633] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   10.862637] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.862639] [drm] Driver supports precise vblank timestamp query.
[   10.862661] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   10.946286] Initializing USB Mass Storage driver...
[   10.946356] scsi6 : usb-storage 1-1.2:1.0
[   10.946454] usbcore: registered new interface driver usb-storage
[   10.946455] USB Mass Storage support registered.
[   10.946662] usbcore: registered new interface driver uas
[   11.016582] usb 1-1.4: new full-speed USB device number 4 using ehci_hcd
[   11.180203] usb 1-1.5: new high-speed USB device number 5 using ehci_hcd
[   11.471445] fbcon: inteldrmfb (fb0) is primary device
[   11.800977] Console: switching to colour frame buffer device 170x48
[   11.802762] fb0: inteldrmfb frame buffer device
[   11.802763] drm: registered panic notifier
[   11.803739] acpi device:33: registered as cooling_device4
[   11.803880] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   11.803958] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   11.803979] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.944576] scsi 6:0:0:0: Direct-Access     Kingston DT 101 G2        PMAP PQ: 0 ANSI: 0 CCS
[   11.944962] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   11.945979] sd 6:0:0:0: [sdb] 7827456 512-byte logical blocks: (4.00 GB/3.73 GiB)
[   11.946631] sd 6:0:0:0: [sdb] Write Protect is off
[   11.946634] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   11.947282] sd 6:0:0:0: [sdb] No Caching mode page present
[   11.947284] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   11.950979] sd 6:0:0:0: [sdb] No Caching mode page present
[   11.950981] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   11.952145]  sdb: sdb1
[   11.954864] sd 6:0:0:0: [sdb] No Caching mode page present
[   11.954867] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   11.954869] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   12.199655] Btrfs loaded
[   12.203167] xor: automatically using best checksumming function: generic_sse
[   12.222406]    generic_sse: 13332.000 MB/sec
[   12.222407] xor: using function: generic_sse (13332.000 MB/sec)
[   12.222787] device-mapper: dm-raid45: initialized v0.2594b
[   12.538438] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   12.891129] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   15.200980] kjournald starting.  Commit interval 5 seconds
[   15.202286] EXT3-fs (loop1): using internal journal
[   15.202301] EXT3-fs (loop1): mounted filesystem with ordered data mode
[   43.988081] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.015709] udevd[2481]: starting version 175
[   44.683227] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   44.683571] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   44.683577] mei 0000:00:16.0: setting latency timer to 64
[   44.683635] mei 0000:00:16.0: irq 44 for MSI/MSI-X
[   44.685797] Bluetooth: Core ver 2.16
[   44.685815] NET: Registered protocol family 31
[   44.685817] Bluetooth: HCI device and connection manager initialized
[   44.685819] Bluetooth: HCI socket layer initialized
[   44.685821] Bluetooth: L2CAP socket layer initialized
[   44.685827] Bluetooth: SCO socket layer initialized
[   44.705364] cfg80211: Calling CRDA to update world regulatory domain
[   44.758868] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   44.758935] usbcore: registered new interface driver btusb
[   44.785570] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   44.794933] Linux video capture interface: v2.00
[   44.834173] Bluetooth: Atheros AR30xx firmware driver ver 1.0
[   44.841171] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:643e)
[   44.856404] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input6
[   44.856538] usbcore: registered new interface driver uvcvideo
[   44.856540] USB Video Class driver (1.1.1)
[   44.858590] device-mapper: multipath: version 1.3.0 loaded
[   44.902111] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   45.262054] cfg80211: World regulatory domain updated:
[   45.262057] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   45.262059] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   45.262061] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   45.262062] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   45.262064] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   45.262066] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   45.273833] init: failsafe main process (2735) killed by TERM signal
[   45.282247] ath9k 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   45.282261] ath9k 0000:09:00.0: setting latency timer to 64
[   45.329789] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   45.329847] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   45.329872] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   45.332718] ath: EEPROM regdomain: 0x60
[   45.332720] ath: EEPROM indicates we should expect a direct regpair map
[   45.332722] ath: Country alpha2 being used: 00
[   45.332723] ath: Regpair used: 0x60
[   45.332726] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   45.332728] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   45.332729] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   45.332731] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   45.332732] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   45.332734] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   45.332736] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   45.332737] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   45.332739] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   45.332741] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   45.332742] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   45.332744] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   45.332745] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   45.332747] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   45.332748] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   45.332750] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   45.332751] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   45.332753] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   45.332755] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   45.332756] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   45.332758] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   45.332760] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   45.332761] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   45.332763] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   45.332764] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   45.332766] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   45.332767] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   45.332769] cfg80211: 2474000 KHz - 2494000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   45.334321] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   45.341209] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   45.341732] Registered led device: ath9k-phy0
[   45.341741] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90001120000, irq=19
[   45.495039] usbcore: registered new interface driver ath3k
[   45.582154] init: hybrid-gfx main process (3091) terminated with status 127
[   45.609967] usb 1-1.4: USB disconnect, device number 4
[   45.729909] Bluetooth: RFCOMM TTY layer initialized
[   45.729915] Bluetooth: RFCOMM socket layer initialized
[   45.729917] Bluetooth: RFCOMM ver 1.11
[   45.752842] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   45.752846] Bluetooth: BNEP filters: protocol multicast
[   45.867679] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input8
[   45.880238] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input9
[   45.880454] usb 1-1.4: new full-speed USB device number 6 using ehci_hcd
[   45.941751] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   45.941834] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   45.941919] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   45.941984] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   46.247369] r8169 0000:05:00.0: eth0: link down
[   46.247792] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   46.248101] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   46.299841] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   46.300566] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   46.353068] lp: driver loaded but no devices found
[   46.376332] usb 1-1.4: USB disconnect, device number 6
[   46.416225] ppdev: user-space parallel port driver
[   46.831409] usb 1-1.4: new full-speed USB device number 7 using ehci_hcd
[   52.683606] init: plymouth-stop pre-start process (4190) terminated with status 1
[  135.606960] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[  171.660060] wlan0: authenticate with 5c:d9:98:74:bc:0e (try 1)
[  171.662421] wlan0: authenticated
[  171.662624] wlan0: associate with 5c:d9:98:74:bc:0e (try 1)
[  171.665402] wlan0: RX AssocResp from 5c:d9:98:74:bc:0e (capab=0x411 status=0 aid=1)
[  171.665408] wlan0: associated
[  171.666082] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  182.245255] wlan0: no IPv6 routers present
[  276.171614] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

---

### Post by dcstar on 2012-03-10
> **Marko Darko said:**
> So, it's related to memory reservation after all. Do someone understand why so much memory gets reserved?
......

Because - as has been explained in the hundreds of other threads that already have addressed this issue - **your **hardware reserves address space below 4GB to make it 32-bit compatible. If your BIOS has a setting to remap address reservations above 4GB then set it, otherwise bad luck.

You are quibbling about ~78MB of "missing" RAM out of 4GB, that is less than 2% - is that seriously going to affect the performance of your system?

---

### Post by Marko Darko on 2012-03-10
> **dcstar said:**
> You are quibbling about ~78MB of "missing" RAM out of 4GB, that is less than 2% - is that seriously going to affect the performance of your system?

Well, that's ~232 MB (not 78 ) since I'm running the 64 bit version. The point was not about the absolute amount of memory but the feeling that was something wrong in my system, which now seems to be proved false.

---

### Post by Krupski on 2012-03-12
> **Marko Darko said:**
> Hi Folks,

This question may have been answered before, but I failed to find any answer because, if it exists, it's buried in thousands of Google results for another problem (people tring to get 32 bit non-PAE systems to map more than ~3 GB RAM).

A shot in the dark... do you have CUSTOM memory timings set in your bios (rather than "automatic")?

I found, strangely, that my Intel DQ45CB mobo will report the full 8GB I have installed when memory timing is set to automatic, but it reports only 7GB if I try to use custom settings.

BTW this is with Ubuntu 64 bit server (many versions since I started with 7.04). It's not Linux... it's the motherboard chipset eating 1 GB of ram for apparently no reason.

For what it's worth.....

-- Roger

---

