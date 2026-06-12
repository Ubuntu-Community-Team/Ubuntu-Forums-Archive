---
title: "Thinkpad L420 won't boot anymore, cannot even access GRUB"
date: 2012-01-02
forum: General Help
---

### Post by Elktro on 2012-01-02
I have ubuntu 11.10 64bit installed on my Lenovo thinkpad L420. Suddenly it stopped booting. I can use live cd though with 11.04.

After I power up the hdd led flashes couple of times and then stops. If I press shift in order to access grub, I get the "grub loading..." text, but then the screen goes blank.

I have lvm with seperate boot, root and home logical volumes. Smartctl didn't show any disk errors, and I can mount logvols without any problems.

I have not done anything special in my opinion that could have broken things, although Ubuntu may have installed an update, but I am not sure because I don't recall when was the last time I booted my laptop.

Here is my /etc/default/grub
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

/var/log doesn't show any logs created during the boot.

So, what should I do now? 

How could I figure out what has happened?

---

### Post by Elktro on 2012-01-02
My laptop booted, but there is still something fishy going on.

It just booted when I waited long enough. It seems that for some reason the booting is stuck for a minute or so. This prevents me entering grub.

Here is my dmesg. Could someone say what is going on?

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-14-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 (Ubuntu 3.0.0-14.23-generic 3.0.9)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.0.0-14-generic root=/dev/mapper/VG_triton00-root ro i915.semaphores=1 i915.modeset=1
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c400 (usable)
[    0.000000]  BIOS-e820: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000c6a7c000 (usable)
[    0.000000]  BIOS-e820: 00000000c6a7c000 - 00000000c6a82000 (reserved)
[    0.000000]  BIOS-e820: 00000000c6a82000 - 00000000c6bec000 (usable)
[    0.000000]  BIOS-e820: 00000000c6bec000 - 00000000c6c0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000c6c0f000 - 00000000c6c70000 (usable)
[    0.000000]  BIOS-e820: 00000000c6c70000 - 00000000c6cf1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000c6cf1000 - 00000000c6f0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000c6f0f000 - 00000000c6f18000 (usable)
[    0.000000]  BIOS-e820: 00000000c6f18000 - 00000000c6f1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000c6f1f000 - 00000000c6f6f000 (usable)
[    0.000000]  BIOS-e820: 00000000c6f6f000 - 00000000c6f9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000c6f9f000 - 00000000c6fdf000 (usable)
[    0.000000]  BIOS-e820: 00000000c6fdf000 - 00000000c6fff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000c6fff000 - 00000000c7000000 (usable)
[    0.000000]  BIOS-e820: 00000000c7000000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e00f8000 - 00000000e00f9000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000012f800000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: LENOVO 78544VG/78544VG, BIOS 8GET32WW (1.09 ) 05/09/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x12f800 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DBFFF uncachable
[    0.000000]   DC000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 disabled
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0C0000000 mask FF0000000 write-back
[    0.000000]   4 base 100000000 mask FE0000000 write-back
[    0.000000]   5 base 120000000 mask FF0000000 write-back
[    0.000000]   6 base 12F800000 mask FFF800000 uncachable
[    0.000000]   7 base 0C7800000 mask FFF800000 uncachable
[    0.000000]   8 base 0C8000000 mask FF8000000 uncachable
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 1, base: 0GB, range: 2GB, type WB
[    0.000000] reg 2, base: 2GB, range: 1GB, type WB
[    0.000000] reg 3, base: 3GB, range: 256MB, type WB
[    0.000000] reg 4, base: 4GB, range: 512MB, type WB
[    0.000000] reg 5, base: 4608MB, range: 256MB, type WB
[    0.000000] reg 6, base: 4856MB, range: 8MB, type UC
[    0.000000] reg 7, base: 3192MB, range: 8MB, type UC
[    0.000000] reg 8, base: 3200MB, range: 128MB, type UC
[    0.000000] total RAM covered: 3952M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 16M 	num_reg: 7  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 128MB, type WB
[    0.000000] reg 3, base: 3192MB, range: 8MB, type UC
[    0.000000] reg 4, base: 4GB, range: 512MB, type WB
[    0.000000] reg 5, base: 4608MB, range: 256MB, type WB
[    0.000000] reg 6, base: 4856MB, range: 8MB, type UC
[    0.000000] e820 update range: 00000000c7800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xc7000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000f6a20] f6a20
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000c7000000
[    0.000000]  0000000000 - 00c7000000 page 2M
[    0.000000] kernel direct mapping tables up to c7000000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000012f800000
[    0.000000]  0100000000 - 012f800000 page 2M
[    0.000000] kernel direct mapping tables up to 12f800000 @ c6fd9000-c6fdf000
[    0.000000] RAMDISK: 36498000 - 37244000
[    0.000000] ACPI: RSDP 00000000000f66d0 00024 (v04 LENOVO)
[    0.000000] ACPI: XSDT 00000000c6ff1fa5 0006C (v01 LENOVO TP-8G    00001090  LTP 00000000)
[    0.000000] ACPI: FACP 00000000c6fe1000 000F4 (v03 LENOVO TP-8G    00001090 PTEC 00000001)
[    0.000000] ACPI: DSDT 00000000c6fe2000 0CBC9 (v02 LENOVO TP-8G    00001090 INTL 20060912)
[    0.000000] ACPI: FACS 00000000c6f8cfc0 00040
[    0.000000] ACPI: HPET 00000000c6ffed6a 00038 (v01 LENOVO TP-8G    00001090 PTEC 00000001)
[    0.000000] ACPI: MCFG 00000000c6ffeda2 0003C (v01 LENOVO TP-8G    00001090 PTEC 00000001)
[    0.000000] ACPI: APIC 00000000c6ffedde 00084 (v01 LENOVO TP-8G    00001090  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000c6ffee62 00028 (v01 LENOVO TP-8G    00001090  LTP 00000001)
[    0.000000] ACPI: SLIC 00000000c6ffee8a 00176 (v01 LENOVO TP-8G    00001090  LTP 00000000)
[    0.000000] ACPI: TCPA 00000000c6fef000 00032 (v02    PTL  CRESTLN 06040000      00005A52)
[    0.000000] ACPI: SSDT 00000000c6fe0000 00780 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 00000000c6fdf000 00996 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000012f800000
[    0.000000] Initmem setup node 0 0000000000000000-000000012f800000
[    0.000000]   NODE_DATA [000000012f7fb000 - 000000012f7fffff]
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff88012b000000-ffff88012e7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0012f800
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[11] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000c6a7c
[    0.000000]     0: 0x000c6a82 -> 0x000c6bec
[    0.000000]     0: 0x000c6c0f -> 0x000c6c70
[    0.000000]     0: 0x000c6f0f -> 0x000c6f18
[    0.000000]     0: 0x000c6f1f -> 0x000c6f6f
[    0.000000]     0: 0x000c6f9f -> 0x000c6fdf
[    0.000000]     0: 0x000c6fff -> 0x000c7000
[    0.000000]     0: 0x00100000 -> 0x0012f800
[    0.000000] On node 0 totalpages: 1007725
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3919 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 794905 pages, LIFO batch:31
[    0.000000]   Normal zone: 2660 pages used for memmap
[    0.000000]   Normal zone: 191900 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
[    0.000000] PM: Registered nosave memory: 00000000c6a7c000 - 00000000c6a82000
[    0.000000] PM: Registered nosave memory: 00000000c6bec000 - 00000000c6c0f000
[    0.000000] PM: Registered nosave memory: 00000000c6c70000 - 00000000c6cf1000
[    0.000000] PM: Registered nosave memory: 00000000c6cf1000 - 00000000c6f0f000
[    0.000000] PM: Registered nosave memory: 00000000c6f18000 - 00000000c6f1f000
[    0.000000] PM: Registered nosave memory: 00000000c6f6f000 - 00000000c6f9f000
[    0.000000] PM: Registered nosave memory: 00000000c6fdf000 - 00000000c6fff000
[    0.000000] PM: Registered nosave memory: 00000000c7000000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000e00f8000
[    0.000000] PM: Registered nosave memory: 00000000e00f8000 - 00000000e00f9000
[    0.000000] PM: Registered nosave memory: 00000000e00f9000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e00f9000 (gap: e00f9000:1ec23000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88012f400000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 990724
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.0-14-generic root=/dev/mapper/VG_triton00-root ro i915.semaphores=1 i915.modeset=1
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3879568k/4972544k available (6109k kernel code, 941644k absent, 151332k reserved, 4876k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 32505856 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2295.157 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4590.31 BogoMIPS (lpj=9180628)
[    0.000009] pid_max: default: 32768 minimum: 301
[    0.000031] Security Framework initialized
[    0.000046] AppArmor: AppArmor initialized
[    0.000048] Yama: becoming mindful.
[    0.000451] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001512] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001957] Mount-cache hash table entries: 256
[    0.002058] Initializing cgroup subsys cpuacct
[    0.002065] Initializing cgroup subsys memory
[    0.002071] Initializing cgroup subsys devices
[    0.002075] Initializing cgroup subsys freezer
[    0.002078] Initializing cgroup subsys net_cls
[    0.002080] Initializing cgroup subsys blkio
[    0.002086] Initializing cgroup subsys perf_event
[    0.002112] CPU: Physical Processor ID: 0
[    0.002115] CPU: Processor Core ID: 0
[    0.002121] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002122] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002128] mce: CPU supports 7 MCE banks
[    0.002141] CPU0: Thermal monitoring enabled (TM1)
[    0.002149] using mwait in idle threads.
[    0.004580] ACPI: Core revision 20110413
[    0.023815] ftrace: allocating 25647 entries in 101 pages
[    0.033674] x2apic not enabled, IRQ remapping init failed
[    0.034030] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.073703] CPU0: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz stepping 07
[    0.179855] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.179863] ... version:                3
[    0.179866] ... bit width:              48
[    0.179868] ... generic registers:      4
[    0.179870] ... value mask:             0000ffffffffffff
[    0.179873] ... max period:             000000007fffffff
[    0.179875] ... fixed-purpose events:   3
[    0.179877] ... event mask:             000000070000000f
[    0.180258] Booting Node   0, Processors  #1
[    0.180261] smpboot cpu 1: start_ip = 97000
[    0.287982]  #2
[    0.287985] smpboot cpu 2: start_ip = 97000
[    0.395897]  #3 Ok.
[    0.395901] smpboot cpu 3: start_ip = 97000
[    0.503755] Brought up 4 CPUs
[    0.503760] Total of 4 processors activated (18358.41 BogoMIPS).
[    0.506465] devtmpfs: initialized
[    0.506580] PM: Registering ACPI NVS region at c6c70000 (528384 bytes)
[    0.506592] PM: Registering ACPI NVS region at c6f6f000 (196608 bytes)
[    0.507876] print_constraints: dummy: 
[    0.507903] Time: 22:49:02  Date: 01/02/12
[    0.507931] NET: Registered protocol family 16
[    0.508017] Trying to unpack rootfs image as initramfs...
[    0.508025] ACPI: bus type pci registered
[    0.508088] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.508093] PCI: not using MMCONFIG
[    0.508096] PCI: Using configuration type 1 for base access
[    0.508730] bio: create slab <bio-0> at 0
[    0.510590] ACPI: EC: Look up EC in DSDT
[    0.516576] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.516991] ACPI: SSDT 00000000c6f19018 007E7 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.517451] ACPI: Dynamic OEM Table Load:
[    0.517455] ACPI: SSDT           (null) 007E7 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.547907] ACPI: SSDT 00000000c6f1aa98 00303 (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.548402] ACPI: Dynamic OEM Table Load:
[    0.548406] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.579751] ACPI: SSDT 00000000c6f18d98 00119 (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.580213] ACPI: Dynamic OEM Table Load:
[    0.580217] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.606540] ACPI: Interpreter enabled
[    0.606546] ACPI: (supports S0 S3 S4 S5)
[    0.606570] ACPI: Using IOAPIC for interrupt routing
[    0.606593] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.610345] [Firmware Bug]: PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] not reserved in ACPI motherboard resources
[    0.610351] PCI: not using MMCONFIG
[    0.623391] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.624576] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.624580] HEST: Table not found.
[    0.624583] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.624844] \_SB_.PCI0:_OSC invalid UUID
[    0.624845] _OSC request data:1 8 1f 
[    0.624849] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.625277] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.625281] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.625284] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.625288] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.625292] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.625296] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.625300] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.625304] pci_root PNP0A08:00: host bridge window [mem 0xd0000000-0xfeafffff]
[    0.625308] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    0.625312] pci_root PNP0A08:00: host bridge window [mem 0xfeaff000-0xfeb00000]
[    0.625317] pci_root PNP0A08:00: host bridge window expanded to [mem 0xd0000000-0xfeb00000]; [mem 0xfeaff000-0xfeb00000] ignored
[    0.625331] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    0.625366] pci 0000:00:02.0: [8086:0116] type 0 class 0x000300
[    0.625376] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf03fffff 64bit]
[    0.625383] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.625387] pci 0000:00:02.0: reg 20: [io  0x1800-0x183f]
[    0.625438] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    0.625462] pci 0000:00:16.0: reg 10: [mem 0xf0904000-0xf090400f 64bit]
[    0.625526] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.625531] pci 0000:00:16.0: PME# disabled
[    0.625564] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    0.625585] pci 0000:00:1a.0: reg 10: [mem 0xf0907000-0xf09073ff]
[    0.625660] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.625664] pci 0000:00:1a.0: PME# disabled
[    0.625689] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    0.625704] pci 0000:00:1b.0: reg 10: [mem 0xf0900000-0xf0903fff 64bit]
[    0.625761] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.625765] pci 0000:00:1b.0: PME# disabled
[    0.625786] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    0.625848] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.625852] pci 0000:00:1c.0: PME# disabled
[    0.625876] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    0.625938] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.625943] pci 0000:00:1c.1: PME# disabled
[    0.625965] pci 0000:00:1c.2: [8086:1c14] type 1 class 0x000604
[    0.626028] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.626032] pci 0000:00:1c.2: PME# disabled
[    0.626055] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
[    0.626117] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.626121] pci 0000:00:1c.3: PME# disabled
[    0.626145] pci 0000:00:1c.4: [8086:1c18] type 1 class 0x000604
[    0.626208] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.626212] pci 0000:00:1c.4: PME# disabled
[    0.626235] pci 0000:00:1c.5: [8086:1c1a] type 1 class 0x000604
[    0.626297] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.626302] pci 0000:00:1c.5: PME# disabled
[    0.626333] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    0.626354] pci 0000:00:1d.0: reg 10: [mem 0xf0908000-0xf09083ff]
[    0.626428] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.626433] pci 0000:00:1d.0: PME# disabled
[    0.626458] pci 0000:00:1f.0: [8086:1c49] type 0 class 0x000601
[    0.626574] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    0.626593] pci 0000:00:1f.2: reg 10: [io  0x1858-0x185f]
[    0.626602] pci 0000:00:1f.2: reg 14: [io  0x184c-0x184f]
[    0.626610] pci 0000:00:1f.2: reg 18: [io  0x1850-0x1857]
[    0.626619] pci 0000:00:1f.2: reg 1c: [io  0x1848-0x184b]
[    0.626627] pci 0000:00:1f.2: reg 20: [io  0x1860-0x187f]
[    0.626636] pci 0000:00:1f.2: reg 24: [mem 0xf0909000-0xf09097ff]
[    0.626669] pci 0000:00:1f.2: PME# supported from D3hot
[    0.626673] pci 0000:00:1f.2: PME# disabled
[    0.626692] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    0.626708] pci 0000:00:1f.3: reg 10: [mem 0xf090a000-0xf090a0ff 64bit]
[    0.626730] pci 0000:00:1f.3: reg 20: [io  0x1880-0x189f]
[    0.626803] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.626810] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.626815] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.626822] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.626902] pci 0000:03:00.0: [8086:0084] type 0 class 0x000280
[    0.626944] pci 0000:03:00.0: reg 10: [mem 0xf0500000-0xf0501fff 64bit]
[    0.627118] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.627126] pci 0000:03:00.0: PME# disabled
[    0.631628] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.631635] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.631640] pci 0000:00:1c.1:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.631646] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.631719] pci 0000:04:00.0: [10ec:5209] type 0 class 0x00ff00
[    0.631740] pci 0000:04:00.0: reg 10: [mem 0xf0600000-0xf0600fff]
[    0.631864] pci 0000:04:00.0: supports D1 D2
[    0.631866] pci 0000:04:00.0: PME# supported from D1 D2 D3hot
[    0.631872] pci 0000:04:00.0: PME# disabled
[    0.639615] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.639623] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
[    0.639628] pci 0000:00:1c.2:   bridge window [mem 0xf0600000-0xf06fffff]
[    0.639634] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.639684] pci 0000:00:1c.3: PCI bridge to [bus 05-07]
[    0.639689] pci 0000:00:1c.3:   bridge window [io  0x2000-0x2fff]
[    0.639694] pci 0000:00:1c.3:   bridge window [mem 0xf0400000-0xf04fffff]
[    0.639703] pci 0000:00:1c.3:   bridge window [mem 0xf0c00000-0xf0dfffff 64bit pref]
[    0.639750] pci 0000:00:1c.4: PCI bridge to [bus 08-08]
[    0.639755] pci 0000:00:1c.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.639760] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.639767] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.639836] pci 0000:09:00.0: [10ec:8168] type 0 class 0x000200
[    0.639856] pci 0000:09:00.0: reg 10: [io  0x3000-0x30ff]
[    0.639891] pci 0000:09:00.0: reg 18: [mem 0xf0a04000-0xf0a04fff 64bit pref]
[    0.639913] pci 0000:09:00.0: reg 20: [mem 0xf0a00000-0xf0a03fff 64bit pref]
[    0.639976] pci 0000:09:00.0: supports D1 D2
[    0.639978] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.639984] pci 0000:09:00.0: PME# disabled
[    0.647612] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
[    0.647619] pci 0000:00:1c.5:   bridge window [io  0x3000-0x3fff]
[    0.647624] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.647631] pci 0000:00:1c.5:   bridge window [mem 0xf0a00000-0xf0afffff 64bit pref]
[    0.647666] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.647793] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.647824] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.647854] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.647883] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.647911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.647939] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.648026] \_SB_.PCI0:_OSC invalid UUID
[    0.648027] _OSC request data:1 1e 1f 
[    0.648031]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.650727] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.650774] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.650818] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.650861] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.650907] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.650952] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.650996] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.651039] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.651117] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.651126] vgaarb: loaded
[    0.651128] vgaarb: bridge control possible 0000:00:02.0
[    0.651269] SCSI subsystem initialized
[    0.651325] libata version 3.00 loaded.
[    0.651365] usbcore: registered new interface driver usbfs
[    0.651374] usbcore: registered new interface driver hub
[    0.651400] usbcore: registered new device driver usb
[    0.651467] PCI: Using ACPI for IRQ routing
[    0.651471] PCI: pci_cache_line_size set to 64 bytes
[    0.651559] reserve RAM buffer: 000000000009c400 - 000000000009ffff 
[    0.651562] reserve RAM buffer: 00000000c6a7c000 - 00000000c7ffffff 
[    0.651565] reserve RAM buffer: 00000000c6bec000 - 00000000c7ffffff 
[    0.651568] reserve RAM buffer: 00000000c6c70000 - 00000000c7ffffff 
[    0.651571] reserve RAM buffer: 00000000c6f18000 - 00000000c7ffffff 
[    0.651574] reserve RAM buffer: 00000000c6f6f000 - 00000000c7ffffff 
[    0.651576] reserve RAM buffer: 00000000c6fdf000 - 00000000c7ffffff 
[    0.651578] reserve RAM buffer: 00000000c7000000 - 00000000c7ffffff 
[    0.651580] reserve RAM buffer: 000000012f800000 - 000000012fffffff 
[    0.651661] NetLabel: Initializing
[    0.651664] NetLabel:  domain hash size = 128
[    0.651666] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.651677] NetLabel:  unlabeled traffic allowed by default
[    0.651721] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.651728] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.653743] Switching to clocksource hpet
[    0.655602] Switched to NOHz mode on CPU #0
[    0.655679] Switched to NOHz mode on CPU #3
[    0.655690] Switched to NOHz mode on CPU #2
[    0.655719] Switched to NOHz mode on CPU #1
[    0.658612] AppArmor: AppArmor Filesystem Enabled
[    0.658637] pnp: PnP ACPI init
[    0.658652] ACPI: bus type pnp registered
[    0.658907] pnp 00:00: [bus 00-3e]
[    0.658910] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.658912] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.658913] pnp 00:00: [io  0x0d00-0xffff window]
[    0.658915] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.658917] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.658919] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.658921] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.658923] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.658924] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.658926] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.658928] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.658930] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.658931] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.658933] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.658935] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.658937] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.658938] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.658940] pnp 00:00: [mem 0xd0000000-0xfeafffff window]
[    0.658942] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.658944] pnp 00:00: [mem 0xfeaff000-0xfeb00000 window]
[    0.659003] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.659017] pnp 00:01: [io  0x0000-0x001f]
[    0.659019] pnp 00:01: [io  0x0081-0x0091]
[    0.659020] pnp 00:01: [io  0x0093-0x009f]
[    0.659022] pnp 00:01: [io  0x00c0-0x00df]
[    0.659024] pnp 00:01: [dma 4]
[    0.659040] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.659047] pnp 00:02: [mem 0xff000000-0xffffffff]
[    0.659064] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.659135] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.659152] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.659160] pnp 00:04: [io  0x00f0]
[    0.659170] pnp 00:04: [irq 13]
[    0.659185] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.659195] pnp 00:05: [io  0x002e-0x002f]
[    0.659196] pnp 00:05: [io  0x004e-0x004f]
[    0.659198] pnp 00:05: [io  0x0061]
[    0.659199] pnp 00:05: [io  0x0063]
[    0.659201] pnp 00:05: [io  0x0065]
[    0.659202] pnp 00:05: [io  0x0067]
[    0.659203] pnp 00:05: [io  0x0070]
[    0.659204] pnp 00:05: [io  0x0080]
[    0.659206] pnp 00:05: [io  0x0092]
[    0.659207] pnp 00:05: [io  0x00b2-0x00b3]
[    0.659209] pnp 00:05: [io  0x0680-0x069f]
[    0.659210] pnp 00:05: [io  0x0800-0x080f]
[    0.659212] pnp 00:05: [io  0xffff]
[    0.659213] pnp 00:05: [io  0xffff]
[    0.659214] pnp 00:05: [io  0x0400-0x0453]
[    0.659216] pnp 00:05: [io  0x0458-0x047f]
[    0.659217] pnp 00:05: [io  0x0500-0x057f]
[    0.659219] pnp 00:05: [io  0x1600-0x16fe]
[    0.659220] pnp 00:05: [io  0xfe00]
[    0.659222] pnp 00:05: [io  0x0068]
[    0.659223] pnp 00:05: [io  0x006c]
[    0.659224] pnp 00:05: [io  0x0700-0x070f]
[    0.659265] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.659269] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.659273] system 00:05: [io  0xffff] has been reserved
[    0.659276] system 00:05: [io  0xffff] has been reserved
[    0.659279] system 00:05: [io  0x0400-0x0453] has been reserved
[    0.659282] system 00:05: [io  0x0458-0x047f] has been reserved
[    0.659286] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.659289] system 00:05: [io  0x1600-0x16fe] has been reserved
[    0.659292] system 00:05: [io  0xfe00] has been reserved
[    0.659296] system 00:05: [io  0x0700-0x070f] has been reserved
[    0.659300] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.659307] pnp 00:06: [io  0x0070-0x0077]
[    0.659312] pnp 00:06: [irq 8]
[    0.659327] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.659350] pnp 00:07: [io  0x0454-0x0457]
[    0.659378] system 00:07: [io  0x0454-0x0457] has been reserved
[    0.659383] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.659390] pnp 00:08: [io  0x0060]
[    0.659391] pnp 00:08: [io  0x0064]
[    0.659396] pnp 00:08: [irq 1]
[    0.659413] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.659428] pnp 00:09: [irq 12]
[    0.659445] pnp 00:09: Plug and Play ACPI device, IDs LEN0017 PNP0f13 (active)
[    0.660352] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    0.660374] pnp 00:0a: Plug and Play ACPI device, IDs SMO1200 PNP0c31 (active)
[    0.660416] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
[    0.660417] pnp 00:0b: [mem 0x00000000-0x00007fff]
[    0.660419] pnp 00:0b: [mem 0x00000000-0x00000fff]
[    0.660422] pnp 00:0b: [mem 0x00000000-0x00000fff]
[    0.660424] pnp 00:0b: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.660426] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
[    0.660428] pnp 00:0b: [mem 0xfed90000-0xfed93fff]
[    0.660429] pnp 00:0b: [mem 0xfed40000-0xfed44fff]
[    0.660431] pnp 00:0b: [mem 0xfed45000-0xfed8ffff]
[    0.660432] pnp 00:0b: [mem 0xff000000-0xffffffff]
[    0.660434] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
[    0.660435] pnp 00:0b: [mem 0xfeaff000-0xfeafffff]
[    0.660470] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.660474] system 00:0b: [mem 0x00000000-0x00007fff] could not be reserved
[    0.660478] system 00:0b: [mem 0x00000000-0x00000fff] could not be reserved
[    0.660482] system 00:0b: [mem 0x00000000-0x00000fff] could not be reserved
[    0.660485] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.660489] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.660493] system 00:0b: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.660498] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.660501] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    0.660505] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.660509] system 00:0b: [mem 0xfeaff000-0xfeafffff] has been reserved
[    0.660513] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.661458] pnp: PnP ACPI: found 12 devices
[    0.661462] ACPI: ACPI bus type pnp unregistered
[    0.667007] PCI: max bus depth: 1 pci_try_num: 2
[    0.667065] pci 0000:00:1c.4: BAR 14: assigned [mem 0xe0100000-0xe02fffff]
[    0.667071] pci 0000:00:1c.4: BAR 15: assigned [mem 0xe0300000-0xe04fffff 64bit pref]
[    0.667077] pci 0000:00:1c.4: BAR 13: assigned [io  0x4000-0x4fff]
[    0.667081] pci 0000:00:1c.2: BAR 15: assigned [mem 0xe0500000-0xe06fffff 64bit pref]
[    0.667086] pci 0000:00:1c.2: BAR 13: assigned [io  0x5000-0x5fff]
[    0.667090] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.667093] pci 0000:00:1c.0:   bridge window [io  disabled]
[    0.667100] pci 0000:00:1c.0:   bridge window [mem disabled]
[    0.667105] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    0.667113] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.667116] pci 0000:00:1c.1:   bridge window [io  disabled]
[    0.667123] pci 0000:00:1c.1:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.667128] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    0.667136] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.667141] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
[    0.667148] pci 0000:00:1c.2:   bridge window [mem 0xf0600000-0xf06fffff]
[    0.667154] pci 0000:00:1c.2:   bridge window [mem 0xe0500000-0xe06fffff 64bit pref]
[    0.667162] pci 0000:00:1c.3: PCI bridge to [bus 05-07]
[    0.667166] pci 0000:00:1c.3:   bridge window [io  0x2000-0x2fff]
[    0.667173] pci 0000:00:1c.3:   bridge window [mem 0xf0400000-0xf04fffff]
[    0.667179] pci 0000:00:1c.3:   bridge window [mem 0xf0c00000-0xf0dfffff 64bit pref]
[    0.667188] pci 0000:00:1c.4: PCI bridge to [bus 08-08]
[    0.667192] pci 0000:00:1c.4:   bridge window [io  0x4000-0x4fff]
[    0.667199] pci 0000:00:1c.4:   bridge window [mem 0xe0100000-0xe02fffff]
[    0.667205] pci 0000:00:1c.4:   bridge window [mem 0xe0300000-0xe04fffff 64bit pref]
[    0.667214] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
[    0.667219] pci 0000:00:1c.5:   bridge window [io  0x3000-0x3fff]
[    0.667225] pci 0000:00:1c.5:   bridge window [mem disabled]
[    0.667231] pci 0000:00:1c.5:   bridge window [mem 0xf0a00000-0xf0afffff 64bit pref]
[    0.667255] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.667262] pci 0000:00:1c.0: setting latency timer to 64
[    0.667272] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.667278] pci 0000:00:1c.1: setting latency timer to 64
[    0.667287] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.667293] pci 0000:00:1c.2: setting latency timer to 64
[    0.667303] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.667309] pci 0000:00:1c.3: setting latency timer to 64
[    0.667316] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.667322] pci 0000:00:1c.4: setting latency timer to 64
[    0.667329] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.667334] pci 0000:00:1c.5: setting latency timer to 64
[    0.667339] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.667341] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.667343] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.667344] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.667346] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.667348] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.667350] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.667352] pci_bus 0000:00: resource 11 [mem 0xd0000000-0xfeb00000]
[    0.667354] pci_bus 0000:00: resource 12 [mem 0xfed40000-0xfed44fff]
[    0.667356] pci_bus 0000:03: resource 1 [mem 0xf0500000-0xf05fffff]
[    0.667358] pci_bus 0000:04: resource 0 [io  0x5000-0x5fff]
[    0.667360] pci_bus 0000:04: resource 1 [mem 0xf0600000-0xf06fffff]
[    0.667362] pci_bus 0000:04: resource 2 [mem 0xe0500000-0xe06fffff 64bit pref]
[    0.667364] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
[    0.667366] pci_bus 0000:05: resource 1 [mem 0xf0400000-0xf04fffff]
[    0.667368] pci_bus 0000:05: resource 2 [mem 0xf0c00000-0xf0dfffff 64bit pref]
[    0.667370] pci_bus 0000:08: resource 0 [io  0x4000-0x4fff]
[    0.667371] pci_bus 0000:08: resource 1 [mem 0xe0100000-0xe02fffff]
[    0.667373] pci_bus 0000:08: resource 2 [mem 0xe0300000-0xe04fffff 64bit pref]
[    0.667375] pci_bus 0000:09: resource 0 [io  0x3000-0x3fff]
[    0.667377] pci_bus 0000:09: resource 2 [mem 0xf0a00000-0xf0afffff 64bit pref]
[    0.667402] NET: Registered protocol family 2
[    0.667536] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.668422] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.670339] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.670561] TCP: Hash tables configured (established 524288 bind 65536)
[    0.670565] TCP reno registered
[    0.670575] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.670597] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.670680] NET: Registered protocol family 1
[    0.670694] pci 0000:00:02.0: Boot video device
[    0.670791] PCI: CLS 64 bytes, default 64
[    0.670792] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.670796] Placing 64MB software IO TLB between ffff8800c2a7c000 - ffff8800c6a7c000
[    0.670800] software IO TLB at phys 0xc2a7c000 - 0xc6a7c000
[    0.670816] Simple Boot Flag at 0x36 set to 0x1
[    0.671209] audit: initializing netlink socket (disabled)
[    0.671218] type=2000 audit(1325544542.500:1): initialized
[    0.696489] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.709387] VFS: Disk quotas dquot_6.5.2
[    0.709436] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.709910] fuse init (API version 7.16)
[    0.709977] msgmni has been set to 7577
[    0.710291] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.710319] io scheduler noop registered
[    0.710325] io scheduler deadline registered
[    0.710356] io scheduler cfq registered (default)
[    0.710691] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.710710] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.710744] intel_idle: MWAIT substates: 0x21120
[    0.710746] intel_idle: v0.4 model 0x2A
[    0.710747] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.757005] Freeing initrd memory: 14000k freed
[    0.810502] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.910429] ACPI: AC Adapter [ACAD] (on-line)
[    0.910515] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.912914] ACPI: Lid Switch [LID]
[    0.912946] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.912952] ACPI: Power Button [PWRB]
[    0.912985] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.912990] ACPI: Sleep Button [SLPB]
[    0.913022] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.913026] ACPI: Power Button [PWRF]
[    0.913050] ACPI: acpi_idle yielding to intel_idle
[    0.920716] thermal LNXTHERM:00: registered as thermal_zone0
[    0.920720] ACPI: Thermal Zone [TZ00] (53 C)
[    0.920739] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.920753] ERST: Table is not found!
[    0.920815] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.962268] ACPI: EC: GPE storm detected, transactions will use polling mode
[    1.194011] Linux agpgart interface v0.103
[    1.194082] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.194259] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.195607] agpgart-intel 0000:00:00.0: detected 131072K stolen memory
[    1.195710] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.196467] brd: module loaded
[    1.196814] loop: module loaded
[    1.197124] Fixed MDIO Bus: probed
[    1.197141] PPP generic driver version 2.4.2
[    1.197168] tun: Universal TUN/TAP device driver, 1.6
[    1.197171] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.197225] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.197243] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.197262] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.197266] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.197293] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.197320] ehci_hcd 0000:00:1a.0: debug port 2
[    1.201199] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.201217] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf0907000
[    1.213632] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.213816] hub 1-0:1.0: USB hub found
[    1.213822] hub 1-0:1.0: 3 ports detected
[    1.213879] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.213893] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.213897] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.213923] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.213947] ehci_hcd 0000:00:1d.0: debug port 2
[    1.217822] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.217835] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf0908000
[    1.233622] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.233799] hub 2-0:1.0: USB hub found
[    1.233803] hub 2-0:1.0: 3 ports detected
[    1.233849] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.233858] uhci_hcd: USB Universal Host Controller Interface driver
[    1.233904] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.240601] i8042: Detected active multiplexing controller, rev 1.1
[    1.245150] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.245157] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.245181] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.245200] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.245216] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.245290] mousedev: PS/2 mouse device common for all mice
[    1.245404] rtc_cmos 00:06: RTC can wake from S4
[    1.245494] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.245523] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.245609] device-mapper: uevent: version 1.0.3
[    1.245665] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.245757] cpuidle: using governor ladder
[    1.245898] cpuidle: using governor menu
[    1.245901] EFI Variables Facility v0.08 2004-May-17
[    1.246058] TCP cubic registered
[    1.246150] NET: Registered protocol family 10
[    1.246462] NET: Registered protocol family 17
[    1.246474] Registering the dns_resolver key type
[    1.246546] PM: Hibernation image not present or could not be loaded.
[    1.246557] registered taskstats version 1
[    1.257927]   Magic number: 12:240:855
[    1.258014] rtc_cmos 00:06: setting system clock to 2012-01-02 22:49:03 UTC (1325544543)
[    1.258719] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.258722] EDD information not available.
[    1.259877] Freeing unused kernel memory: 984k freed
[    1.259984] Write protecting the kernel read-only data: 10240k
[    1.260165] Freeing unused kernel memory: 16k freed
[    1.263308] Freeing unused kernel memory: 1396k freed
[    1.274765] udevd[88]: starting version 173
[    1.296329] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.525556] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.617668] ACPI: Battery Slot [BAT1] (battery present)
[    1.658294] hub 1-1:1.0: USB hub found
[    1.658464] hub 1-1:1.0: 6 ports detected
[    1.669473] Refined TSC clocksource calibration: 2294.786 MHz.
[    1.669496] Switching to clocksource tsc
[    1.764544] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.764579] r8169 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.764778] r8169 0000:09:00.0: setting latency timer to 64
[    1.764849] r8169 0000:09:00.0: irq 40 for MSI/MSI-X
[    1.765446] r8169 0000:09:00.0: eth0: RTL8168d/8111d at 0xffffc9000105a000, e8:9a:8f:47:79:a3, XID 083000c0 IRQ 40
[    1.768822] ahci 0000:00:1f.2: version 3.0
[    1.768837] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.768892] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    1.768922] ahci: SSS flag set, parallel bus scan disabled
[    1.769348] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    1.781479] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3b impl SATA mode
[    1.781488] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    1.781496] ahci 0000:00:1f.2: setting latency timer to 64
[    1.813860] scsi0 : ahci
[    1.814006] scsi1 : ahci
[    1.814136] scsi2 : ahci
[    1.814248] scsi3 : ahci
[    1.814365] scsi4 : ahci
[    1.814496] scsi5 : ahci
[    1.901936] hub 2-1:1.0: USB hub found
[    1.902023] hub 2-1:1.0: 6 ports detected
[    1.945432] ata1: SATA max UDMA/133 abar m2048@0xf0909000 port 0xf0909100 irq 41
[    1.945441] ata2: SATA max UDMA/133 abar m2048@0xf0909000 port 0xf0909180 irq 41
[    1.945445] ata3: DUMMY
[    1.945448] ata4: SATA max UDMA/133 abar m2048@0xf0909000 port 0xf0909280 irq 41
[    1.945453] ata5: SATA max UDMA/133 abar m2048@0xf0909000 port 0xf0909300 irq 41
[    1.945457] ata6: SATA max UDMA/133 abar m2048@0xf0909000 port 0xf0909380 irq 41
[    1.973409] usb 1-1.3: new full speed USB device number 3 using ehci_hcd
[    2.137490] usb 1-1.6: new full speed USB device number 4 using ehci_hcd
[    2.265172] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.266548] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    2.266560] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.266580] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.267949] ata1.00: ATA-8: WDC WD3200BEVT-08A23T1, 02.01A02, max UDMA/133
[    2.267967] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.269395] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    2.269407] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.269424] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.270803] ata1.00: configured for UDMA/133
[    2.271016] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-0 02.0 PQ: 0 ANSI: 5
[    2.271153] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.271159] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.271219] sd 0:0:0:0: [sda] Write Protect is off
[    2.271233] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.271259] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.301951]  sda: sda1
[    2.302243] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.305235] usb 2-1.4: new high speed USB device number 3 using ehci_hcd
[    2.589020] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.591137] ata2.00: unexpected _GTF length (8)
[    2.591145] ata2.00: ATAPI: MATSHITADVD-RAM UJ8A0A, SB02, max UDMA/100
[    2.594043] ata2.00: unexpected _GTF length (8)
[    2.594051] ata2.00: configured for UDMA/100
[    2.597878] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ8A0A   SB02 PQ: 0 ANSI: 5
[    2.601173] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.601191] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.601350] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.601405] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.920848] ata4: SATA link down (SStatus 0 SControl 300)
[    3.240684] ata5: SATA link down (SStatus 0 SControl 300)
[    3.560520] ata6: SATA link down (SStatus 0 SControl 300)
[    4.049520] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   76.729694] udevd[348]: starting version 173
[   76.746714] lp: driver loaded but no devices found
[   76.793525] Adding 3903484k swap on /dev/mapper/VG_triton00-swap.  Priority:-1 extents:1 across:3903484k 
[   76.891495] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
[   77.086741] tpm_tis 00:0a: 1.2 TPM (device-id 0x0, rev-id 78)
[   77.086855] Non-volatile memory driver v1.3
[   77.100991] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   77.100994] thinkpad_acpi: http://ibm-acpi.sf.net/
[   77.100996] thinkpad_acpi: ThinkPad BIOS 8GET32WW (1.09 ), EC 8GHT22WW-1.040000
[   77.100998] thinkpad_acpi: Lenovo ThinkPad L420, model 78544VG
[   77.101637] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   77.150212] wmi: Mapper loaded
[   77.154225] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   77.160686] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   77.160986] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   77.160994] mei 0000:00:16.0: setting latency timer to 64
[   77.162098] [drm] Initialized drm 1.1.0 20060810
[   77.168986] rts_pstor: module is from the staging directory, the quality is unknown, you have been warned.
[   77.169797] Initializing Realtek PCIE storage driver...
[   77.169831] rts_pstor 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   77.173644] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   77.173650] i915 0000:00:02.0: setting latency timer to 64
[   77.174688] thinkpad_acpi: radio switch found; radios are enabled
[   77.174704] thinkpad_acpi: possible tablet mode switch found; ThinkPad in laptop mode
[   77.175583] thinkpad_acpi: asked for hotkey mask 0x078dffff, but firmware forced it to 0x008dffff
[   77.175860] Resource length: 0x1000
[   77.175889] Original address: 0xf0600000, remapped address: 0xffffc9000107a000
[   77.175897] pci->irq = 18
[   77.175899] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 18
[   77.175945] rts_pstor 0000:04:00.0: setting latency timer to 64
[   77.175951] scsi6 : SCSI emulation for PCI-Express Mass Storage devices
[   77.179671] cfg80211: Calling CRDA to update world regulatory domain
[   77.207817] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   77.207820] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   77.207885] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   77.207895] iwlagn 0000:03:00.0: setting latency timer to 64
[   77.208124] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   77.212461] Bluetooth: Core ver 2.16
[   77.212482] NET: Registered protocol family 31
[   77.212484] Bluetooth: HCI device and connection manager initialized
[   77.212487] Bluetooth: HCI socket layer initialized
[   77.212488] Bluetooth: L2CAP socket layer initialized
[   77.224247] type=1400 audit(1325544619.500:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=617 comm="apparmor_parser"
[   77.224576] type=1400 audit(1325544619.500:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=617 comm="apparmor_parser"
[   77.224791] type=1400 audit(1325544619.500:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=617 comm="apparmor_parser"
[   77.229141] iwlagn 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   77.229144] iwlagn 0000:03:00.0: Device SKU: 0X9
[   77.229146] iwlagn 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   77.231103] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   77.232716] iwlagn 0000:03:00.0: irq 42 for MSI/MSI-X
[   77.233706] Bluetooth: SCO socket layer initialized
[   77.234043] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   77.237398] usbcore: registered new interface driver btusb
[   77.281541] Linux video capture interface: v2.00
[   77.285188] uvcvideo: Found UVC 1.00 device Integrated Camera (064e:e255)
[   77.285291] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   77.285297] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   77.285299] [drm] Driver supports precise vblank timestamp query.
[   77.285341] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   77.290699] input: Integrated Camera as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input5
[   77.290767] usbcore: registered new interface driver uvcvideo
[   77.290769] USB Video Class driver (v1.1.0)
[   77.320389] cfg80211: World regulatory domain updated:
[   77.320393] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   77.320396] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   77.320398] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   77.320401] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   77.320403] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   77.320405] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   77.378799] rts_pstor: waiting for device to settle before scanning
[   77.383572] iwlagn 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[   77.383680] Registered led device: phy0-led
[   77.383708] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   77.402649] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   77.402711] Registered led device: tpacpi::thinklight
[   77.402727] Registered led device: tpacpi::power
[   77.402739] Registered led device: tpacpi::standby
[   77.402751] Registered led device: tpacpi::thinkvantage
[   77.404814] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   77.582890] fbcon: inteldrmfb (fb0) is primary device
[   77.694564] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   77.694647] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   77.726513] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
[   77.753096] Console: switching to colour frame buffer device 170x48
[   77.755273] fb0: inteldrmfb frame buffer device
[   77.755274] drm: registered panic notifier
[   77.839103] ACPI Warning: _BQC returned an invalid level (20110413/video-473)
[   77.839847] acpi device:38: registered as cooling_device4
[   77.840006] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input7
[   77.840060] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   77.840108] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   77.842386] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   77.842440] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   77.842465] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   78.119972] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd047b3/0xb40000/0xa0000
[   78.119987] serio: Synaptics pass-through port at isa0060/serio4/input0
[   78.148843] EXT4-fs (dm-3): mounted filesystem with ordered data mode. Opts: (null)
[   78.166550] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   78.378025] rts_pstor: device scan complete
[   78.378098] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   78.378123] Bad LUN (0:1)
[   78.378147] scsi: killing requests for dead queue
[   78.395595] hda_codec: ALC269VB: BIOS auto-probing.
[   78.406105] Bad target number (1:0)
[   78.406144] scsi: killing requests for dead queue
[   78.406586] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   78.406712] HDMI status: Pin=6 Presence_Detect=0 ELD_Valid=0
[   78.406837] HDMI status: Pin=7 Presence_Detect=0 ELD_Valid=0
[   78.407078] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   78.407163] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   78.407220] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   78.407412] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   78.407469] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   78.430193] Bad target number (2:0)
[   78.430228] scsi: killing requests for dead queue
[   78.454070] Bad target number (3:0)
[   78.454133] scsi: killing requests for dead queue
[   78.466044] Bad target number (4:0)
[   78.466115] scsi: killing requests for dead queue
[   78.510043] Bad target number (5:0)
[   78.510104] scsi: killing requests for dead queue
[   78.546072] Bad target number (6:0)
[   78.546094] scsi: killing requests for dead queue
[   78.546137] Bad target number (7:0)
[   78.546158] scsi: killing requests for dead queue
[   78.546348] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   78.546460] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   78.731014] type=1400 audit(1325544621.008:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=946 comm="apparmor_parser"
[   78.731082] type=1400 audit(1325544621.008:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=944 comm="apparmor_parser"
[   78.731092] type=1400 audit(1325544621.008:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=945 comm="apparmor_parser"
[   78.731318] type=1400 audit(1325544621.008:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=946 comm="apparmor_parser"
[   78.731505] type=1400 audit(1325544621.008:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=946 comm="apparmor_parser"
[   78.733779] type=1400 audit(1325544621.008:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=949 comm="apparmor_parser"
[   78.734050] type=1400 audit(1325544621.012:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/dhcpd" pid=951 comm="apparmor_parser"
[   79.157178] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   79.210249] r8169 0000:09:00.0: eth0: link down
[   79.210290] r8169 0000:09:00.0: eth0: link down
[   79.210525] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   79.254086] ppdev: user-space parallel port driver
[   79.366588] init: failsafe main process (847) killed by TERM signal
[   79.367214] init: apport pre-start process (1058) terminated with status 1
[   79.375398] init: apport post-stop process (1099) terminated with status 1
[   79.378457] init: gdm main process (1098) killed by TERM signal
[   79.398398] Bluetooth: RFCOMM TTY layer initialized
[   79.398404] Bluetooth: RFCOMM socket layer initialized
[   79.398406] Bluetooth: RFCOMM ver 1.11
[   79.399507] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   79.399510] Bluetooth: BNEP filters: protocol multicast
[   80.118196] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro,commit=0
[   80.120127] EXT4-fs (dm-0): re-mounted. Opts: commit=0
[   80.121503] EXT4-fs (dm-3): re-mounted. Opts: commit=0
[   80.786979] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   81.447626] wlan0: authenticate with 00:24:23:1f:b4:e7 (try 1)
[   81.451728] wlan0: authenticated
[   81.462469] wlan0: associate with 00:24:23:1f:b4:e7 (try 1)
[   81.464999] wlan0: RX AssocResp from 00:24:23:1f:b4:e7 (capab=0x431 status=0 aid=1)
[   81.465003] wlan0: associated
[   81.475177] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   81.581953] r8169 0000:09:00.0: eth0: link up
[   81.582317] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   82.414173] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro,commit=0
[   82.626901] EXT4-fs (dm-0): re-mounted. Opts: commit=0
[   82.796987] EXT4-fs (dm-3): re-mounted. Opts: commit=0
[   84.902633] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   85.151670] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio4/serio5/input/input14
[   92.086812] wlan0: no IPv6 routers present
[   92.582328] eth0: no IPv6 routers present
[  146.193562] cfg80211: All devices are disconnected, going to restore regulatory settings
[  146.193577] cfg80211: Restoring regulatory settings
[  146.193588] cfg80211: Calling CRDA to update world regulatory domain
[  146.200641] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  146.200651] cfg80211: World regulatory domain updated:
[  146.200655] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  146.200663] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  146.200670] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  146.200675] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  146.200681] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  146.200687] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  146.692907] wlan0: authenticate with 00:24:23:1f:b4:e7 (try 1)
[  146.702651] wlan0: authenticated
[  146.704853] wlan0: associate with 00:24:23:1f:b4:e7 (try 1)
[  146.711367] wlan0: RX ReassocResp from 00:24:23:1f:b4:e7 (capab=0x431 status=0 aid=1)
[  146.711369] wlan0: associated
[  147.005646] wlan0: deauthenticated from 00:24:23:1f:b4:e7 (Reason: 15)
[  147.019041] cfg80211: All devices are disconnected, going to restore regulatory settings
[  147.019054] cfg80211: Restoring regulatory settings
[  147.019065] cfg80211: Calling CRDA to update world regulatory domain
[  147.025785] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  147.025797] cfg80211: World regulatory domain updated:
[  147.025803] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  147.025813] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  147.025822] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  147.025831] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  147.025840] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  147.025849] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  147.614006] wlan0: authenticate with 00:24:23:1f:b4:e7 (try 1)
[  147.810349] wlan0: authenticate with 00:24:23:1f:b4:e7 (try 2)
[  148.010152] wlan0: authenticate with 00:24:23:1f:b4:e7 (try 3)
[  148.209926] wlan0: authentication with 00:24:23:1f:b4:e7 timed out
[  153.718990] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 1/3)
[  153.916145] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 2/3)
[  154.115945] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 3/3)
[  154.315729] wlan0: direct probe to 00:24:23:1f:b4:e7 timed out
[  159.791657] wlan0: authenticate with 00:24:23:1f:b4:e7 (try 1)
[  159.794966] wlan0: authenticated
[  159.797375] wlan0: associate with 00:24:23:1f:b4:e7 (try 1)
[  159.801550] wlan0: RX ReassocResp from 00:24:23:1f:b4:e7 (capab=0x431 status=0 aid=1)
[  159.801561] wlan0: associated
[  193.567394] usb 1-1.3: usbfs: process 1731 (fingerprint-hel) did not claim interface 0 before use
[  196.371429] usb 1-1.3: usbfs: process 1737 (fingerprint-hel) did not claim interface 0 before use
[  196.636870] input: fingerprint-helper as /devices/virtual/input/input15
[  312.975706] cfg80211: All devices are disconnected, going to restore regulatory settings
[  312.975721] cfg80211: Restoring regulatory settings
[  312.975732] cfg80211: Calling CRDA to update world regulatory domain
[  312.982598] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  312.982611] cfg80211: World regulatory domain updated:
[  312.982618] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  312.982627] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  312.982633] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  312.982639] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  312.982645] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  312.982651] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  313.483665] wlan0: authenticate with 00:24:23:1f:b4:e7 (try 1)
[  313.682283] wlan0: authenticate with 00:24:23:1f:b4:e7 (try 2)
[  313.882021] wlan0: authenticate with 00:24:23:1f:b4:e7 (try 3)
[  314.081804] wlan0: authentication with 00:24:23:1f:b4:e7 timed out
[  319.624731] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 1/3)
[  319.824036] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 2/3)
[  320.023783] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 3/3)
[  320.223607] wlan0: direct probe to 00:24:23:1f:b4:e7 timed out
[  331.155025] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 1/3)
[  331.352334] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 2/3)
[  331.552133] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 3/3)
[  331.751935] wlan0: direct probe to 00:24:23:1f:b4:e7 timed out
[  353.739451] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 1/3)
[  353.937439] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 2/3)
[  354.137205] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 3/3)
[  354.337028] wlan0: direct probe to 00:24:23:1f:b4:e7 timed out
[  359.847584] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 1/3)
[  360.047251] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 2/3)
[  360.247019] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 3/3)
[  360.446822] wlan0: direct probe to 00:24:23:1f:b4:e7 timed out
[  365.986845] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 1/3)
[  366.185076] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 2/3)
[  366.384817] wlan0: direct probe to 00:24:23:1f:b4:e7 (try 3/3)
[  366.584620] wlan0: direct probe to 00:24:23:1f:b4:e7 timed out
[  372.061213] wlan0: authenticate with 00:24:23:1f:b4:e7 (try 1)
[  372.065127] wlan0: authenticated
[  372.066069] wlan0: associate with 00:24:23:1f:b4:e7 (try 1)
[  372.068765] wlan0: RX ReassocResp from 00:24:23:1f:b4:e7 (capab=0x431 status=0 aid=1)
[  372.068768] wlan0: associated
[  372.362482] wlan0: deauthenticated from 00:24:23:1f:b4:e7 (Reason: 15)
[  372.368794] cfg80211: All devices are disconnected, going to restore regulatory settings
[  372.368807] cfg80211: Restoring regulatory settings
[  372.368819] cfg80211: Calling CRDA to update world regulatory domain
[  372.375595] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  372.375607] cfg80211: World regulatory domain updated:
[  372.375613] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  372.375624] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  372.375634] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  372.375644] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  372.375653] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  372.375662] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  372.966707] wlan0: authenticate with 00:24:23:1f:b4:e7 (try 1)
[  373.165950] wlan0: authenticate with 00:24:23:1f:b4:e7 (try 2)
[  373.365737] wlan0: authenticate with 00:24:23:1f:b4:e7 (try 3)
[  373.565512] wlan0: authentication with 00:24:23:1f:b4:e7 timed out
```

---

### Post by oldfred on 2012-01-02
I always look for large gaps in time which indicate a problem as it is off doing something with issues. Not sure if it is the post before or after a gap that is an issue. 

First is drive ok? What does disk utility show? I only know enough that is should be green under smart status for your drive.
Is cfg80211 your wireless and is it having trouble connecting?
Is the third a fingerprint scanner or more issues with 802.11 set up. Are you on b, g or n and is it having trouble connecting? Have you tried connecting with Ethernet and updating?

> 
[    4.049520] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   76.729694] udevd[348]: starting version 173

[   92.582328] eth0: no IPv6 routers present
[  146.193562] cfg80211: All devices are disconnected, going to restore regulatory settings

[  196.636870] input: fingerprint-helper as /devices/virtual/input/input15
[  312.975706] cfg80211: All devices are disconnected, going to restore regulatory settings


---

### Post by Elktro on 2012-01-02
> **oldfred said:**
> i
First is drive ok? What does disk utility show? I only know enough that is should be green under smart status for your drive.
Is cfg80211 your wireless and is it having trouble connecting?
Is the third a fingerprint scanner or more issues with 802.11 set up. Are you on b, g or n and is it having trouble connecting? Have you tried connecting with Ethernet and updating?

The disk utility says that the disk is healthy (green light).

I have not had major problems with wireless. Only one annoying one. The nm tries continuously to connect even though it fails couple of times and even though I have wired connection.

I don't think it is the wireless. I can switch off the wireless manually, and I still have the booting problem.

These two caught my attention in my dmesg:
[   78.430193] Bad target number (2:0)
[   78.430228] scsi: killing requests for dead queue

What does those mean?

---

### Post by Elktro on 2012-01-02
Found the answer, it is a bug.

I was able to see where the boot got stuck by adding [FONT="Courier New"]GRUB_GFXPAYLOAD_LINUX=text[/FONT] to my /etc/default/grub.

This was what I saw:

```
[    2.157223] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ8A0A   SB02 PQ
: 0 ANSI: 5
[    2.160637] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda
tray
[    2.160746] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.160916] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.176013] usb 2-1.4: new high speed USB device number 3 using ehci_hcd
[    2.479657] ata4: SATA link down (SStatus 0 SControl 300)
[    2.799507] ata5: SATA link down (SStatus 0 SControl 300)
[    3.119337] ata6: SATA link down (SStatus 0 SControl 300)
Begin: Running /scripts/local-premount ... done.
[    3.610778] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts:
(null)
Begin: Running /scripts/local-bottom ... done.
done.
[COLOR="Red"]Begin: Running /scripts/init-bottom[/COLOR] ... udevd[94]: timeout: killing 'watershed s
h -c '/sbin/lvm vgscan; /sbin/lvm vgchange -a y'' [261]

udevd[94]: 'watershed sh -c '/sbin/lvm vgscan; /sbin/lvm vgchange -a y'' [261] t
erminated by signal 9 (Killed)

done.

Ubuntu 11.10 triton tty1

triton login:
```

It got stuck to the row marked red. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818177]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818177")

---

### Post by rootbert on 2012-01-05
Hey there, sorry to bring this up again, it is somewhat off-topic though.

Obviously you were able to get Ubuntu 11.10 up and running on a Thinkpad L420. I also have a L420, and 11.10 will only boot with the nosmp option enabled (guess it is due to a buggy BIOS version).
Could you please post your laptop specs and your BIOS version? Did you install the regular image from ubuntu.com? What Kernel do you use?

So I currently run
Ubuntu 11.10 64 Bit with kernel 3.1.4 (have tried the 3.0), only boots with nosmp boot option

My laptop
Thinkpad L420, BIOS 1.15, ECP 1.08
i5-2540M
Mobile Intel HM65 Express Chipset with HD Graphics
8GB PC3-10600 DDR3-SDRAM 1333MHz SODIMM (2 DIMMs)
500GB HDD @ 7200rpm

Thanks in advance!

---

### Post by oahida on 2012-01-05
i bought [http://penta.com.au/index.php?main_page=product_info&cPath=65_2572_70_109&model=&title=Lenovo-ThinkPad-EDGE-021735M-IN-STORE-Core-i5-470UM-1.33GHz-4GB-250GB13HD-Glossy-BT-Camera-6-Cell--Win-7-Home-Premium-64-Bit-1yr.&products_id=30968](http://penta.com.au/index.php?main_page=product_info&cPath=65_2572_70_109&model=&title=Lenovo-ThinkPad-EDGE-021735M-IN-STORE-Core-i5-470UM-1.33GHz-4GB-250GB13HD-Glossy-BT-Camera-6-Cell--Win-7-Home-Premium-64-Bit-1yr.&products_id=30968)

this lenovo thinkpad

---

