---
title: "Login error - Can't login - Urgent! - System error"
date: 2011-06-02
forum: General Help
---

### Post by ToshNeox on 2011-06-02
Hi. I'm running a server using Xubuntu and I now can't get in. When the computer starts everything is fine. When I try and log in by double-clicking on my user 'server' the screen goes black and reverts to the login screen. Every time I login when the screen goes black I get a list of system events. One that fails is:
"Automatic crash report generation"
  And another failed a couple of times:
"Deferred execution scheduler"

  If anyone can give me any help it would be appreciated as this computer is a server and needs to be fixed ASAP. I can't really afford to do a re-install as I have files on it that are needed. If possible I could put the server hard drive in my normal PC to change the files.

My first post,
Tosh :D

---

### Post by wadkar on 2011-06-02
Couple of options you could try:
1. Try changing your X environment to FailSafe.
2. Hit Alt+Ctrl+F1 (or F2) to get command line access to your system
then you can check syslog or better X.log to see whats the cause for the crash and fix it
3. Use Live CD/Pendrive to access your system for time being (you said ASAP access, this is the fastest)

~$
PS: My first post on Ubuntu Forums too ! :)

---

### Post by ToshNeox on 2011-06-02
I can't start it in FailSafe environment, I'm trying the Live CD now although it takes forever, that or it's crashed O_o. I've got another problem at the moment as my KVM has stopped my mouse from working, even though it works when I switch it to the server. I'm using only the keyboard to get around! Who knew how much we rely upon mice? :D

---

### Post by wadkar on 2011-06-02
LiveCD shouldn't take forever, can post 
# tail /var/log/messages
?

---

### Post by jamesisin on 2011-06-02
Can you ssh into the server?

---

### Post by ToshNeox on 2011-06-03
I can start the computer with the Live CD, but what log files do you guys need? I have no idea. I can get to all the system files.

---

### Post by ToshNeox on 2011-06-03
This is the contents of the syslog file which I just found. Not sure if anything is useful:

```
Jun  3 09:54:40 ubuntu kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jun  3 09:54:40 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="1089" x-info="http://www.rsyslog.com"] (re)start
Jun  3 09:54:40 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Jun  3 09:54:40 ubuntu rsyslogd: rsyslogd's userid changed to 101
Jun  3 09:54:40 ubuntu rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Command line: file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
Jun  3 09:54:40 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Jun  3 09:54:40 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jun  3 09:54:40 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jun  3 09:54:40 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jun  3 09:54:40 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6e0000 (usable)
Jun  3 09:54:40 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007f6e0000 - 000000007f6ed000 (ACPI data)
Jun  3 09:54:40 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007f6ed000 - 000000007f700000 (ACPI NVS)
Jun  3 09:54:40 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
Jun  3 09:54:40 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00000 (reserved)
Jun  3 09:54:40 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
Jun  3 09:54:40 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Jun  3 09:54:40 ubuntu kernel: [    0.000000] DMI present.
Jun  3 09:54:40 ubuntu kernel: [    0.000000] DMI: FUJITSU SIEMENS ESPRIMO P           /D2151-A1, BIOS 5.00 R1.10.2151.A1               05/08/2006
Jun  3 09:54:40 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] No AGP bridge found
Jun  3 09:54:40 ubuntu kernel: [    0.000000] last_pfn = 0x7f6e0 max_arch_pfn = 0x400000000
Jun  3 09:54:40 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Jun  3 09:54:40 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   C0000-C7FFF write-protect
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   C8000-E3FFF uncachable
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   E4000-FFFFF write-protect
Jun  3 09:54:40 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   1 base 07F700000 mask FFFF00000 uncachable
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   2 base 07F800000 mask FFF800000 uncachable
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   3 disabled
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   4 disabled
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   5 disabled
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   6 disabled
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   7 disabled
Jun  3 09:54:40 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun  3 09:54:40 ubuntu kernel: [    0.000000] found SMP MP-table at [ffff8800000f75a0] f75a0
Jun  3 09:54:40 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jun  3 09:54:40 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000007f6e0000
Jun  3 09:54:40 ubuntu kernel: [    0.000000]  0000000000 - 007f600000 page 2M
Jun  3 09:54:40 ubuntu kernel: [    0.000000]  007f600000 - 007f6e0000 page 4k
Jun  3 09:54:40 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 7f6e0000 @ 1fffc000-20000000
Jun  3 09:54:40 ubuntu kernel: [    0.000000] RAMDISK: 7e9a0000 - 7f6e0000
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: RSDP 00000000000f7600 00024 (v02 PTLTD )
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: XSDT 000000007f6e84b6 0005C (v01 PTLTD  ? XSDT   00050000  LTP 00000000)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: FACP 000000007f6e8586 000F4 (v03 FSC             00050000      000F4240)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: DSDT 000000007f6e867a 0453F (v01 FSC    D2151    00050000 MSFT 02000002)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: FACS 000000007f6edfc0 00040
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: ASF! 000000007f6ecbb9 00085 (v16 OEMID  OEMTBL   00050000 PTL  00000001)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: SSDT 000000007f6ecc3e 0017C (v01 FSC    EISTCPU0 00050000  CSF 00000001)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: SSDT 000000007f6ecdba 0017C (v01 FSC    EISTCPU1 00050000  CSF 00000001)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: MCFG 000000007f6ecf36 00040 (v01 PTLTD    MCFG   00050000  LTP 00000000)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: APIC 000000007f6ecf76 00062 (v01 FSC    ? APIC   00050000  CSF 00000000)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: BOOT 000000007f6ecfd8 00028 (v01 PTLTD  $SBFTBL$ 00050000  LTP 00000001)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun  3 09:54:40 ubuntu kernel: [    0.000000] No NUMA configuration found
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Faking a node at 0000000000000000-000000007f6e0000
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000007f6e0000
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   NODE_DATA [000000007e99b000 - 000000007e99ffff]
Jun  3 09:54:40 ubuntu kernel: [    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff88007c000000-ffff88007dbfffff] on node 0
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Zone PFN ranges:
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   Normal   empty
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Jun  3 09:54:40 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Jun  3 09:54:40 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jun  3 09:54:40 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0007f6e0
Jun  3 09:54:40 ubuntu kernel: [    0.000000] On node 0 totalpages: 521839
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   DMA zone: 6 pages reserved
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   DMA zone: 3921 pages, LIFO batch:0
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   DMA32 zone: 7081 pages used for memmap
Jun  3 09:54:40 ubuntu kernel: [    0.000000]   DMA32 zone: 510775 pages, LIFO batch:31
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xf008
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun  3 09:54:40 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun  3 09:54:40 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun  3 09:54:40 ubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Jun  3 09:54:40 ubuntu kernel: [    0.000000] nr_irqs_gsi: 40
Jun  3 09:54:40 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun  3 09:54:40 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jun  3 09:54:40 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ec00000)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun  3 09:54:40 ubuntu kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
Jun  3 09:54:40 ubuntu kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007e600000 s84416 r8192 d22080 u1048576
Jun  3 09:54:40 ubuntu kernel: [    0.000000] pcpu-alloc: s84416 r8192 d22080 u1048576 alloc=1*2097152
Jun  3 09:54:40 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 514696
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Policy zone: DMA32
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Kernel command line: file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
Jun  3 09:54:40 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Checking aperture...
Jun  3 09:54:40 ubuntu kernel: [    0.000000] No AGP bridge found
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Memory: 2031424k/2087808k available (5940k kernel code, 452k absent, 55932k reserved, 5017k data, 956k init)
Jun  3 09:54:40 ubuntu kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Jun  3 09:54:40 ubuntu kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jun  3 09:54:40 ubuntu kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Jun  3 09:54:40 ubuntu kernel: [    0.000000] NR_IRQS:16640 nr_irqs:512 16
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Extended CMOS year: 2000
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Jun  3 09:54:40 ubuntu kernel: [    0.000000] console [tty0] enabled
Jun  3 09:54:40 ubuntu kernel: [    0.000000] allocated 20971520 bytes of page_cgroup
Jun  3 09:54:40 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Jun  3 09:54:40 ubuntu kernel: [    0.000000] Detected 3391.669 MHz processor.
Jun  3 09:54:40 ubuntu kernel: [    0.020005] Calibrating delay loop (skipped), value calculated using timer frequency.. 6783.33 BogoMIPS (lpj=33916690)
Jun  3 09:54:40 ubuntu kernel: [    0.020010] pid_max: default: 32768 minimum: 301
Jun  3 09:54:40 ubuntu kernel: [    0.020043] Security Framework initialized
Jun  3 09:54:40 ubuntu kernel: [    0.020070] AppArmor: AppArmor initialized
Jun  3 09:54:40 ubuntu kernel: [    0.020072] Yama: becoming mindful.
Jun  3 09:54:40 ubuntu kernel: [    0.020555] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun  3 09:54:40 ubuntu kernel: [    0.021695] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jun  3 09:54:40 ubuntu kernel: [    0.022275] Mount-cache hash table entries: 256
Jun  3 09:54:40 ubuntu kernel: [    0.022457] Initializing cgroup subsys ns
Jun  3 09:54:40 ubuntu kernel: [    0.022464] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
Jun  3 09:54:40 ubuntu kernel: [    0.022467] Initializing cgroup subsys cpuacct
Jun  3 09:54:40 ubuntu kernel: [    0.022472] Initializing cgroup subsys memory
Jun  3 09:54:40 ubuntu kernel: [    0.022482] Initializing cgroup subsys devices
Jun  3 09:54:40 ubuntu kernel: [    0.022485] Initializing cgroup subsys freezer
Jun  3 09:54:40 ubuntu kernel: [    0.022487] Initializing cgroup subsys net_cls
Jun  3 09:54:40 ubuntu kernel: [    0.022490] Initializing cgroup subsys blkio
Jun  3 09:54:40 ubuntu kernel: [    0.022542] CPU: Physical Processor ID: 0
Jun  3 09:54:40 ubuntu kernel: [    0.022545] CPU: Processor Core ID: 0
Jun  3 09:54:40 ubuntu kernel: [    0.022548] mce: CPU supports 4 MCE banks
Jun  3 09:54:40 ubuntu kernel: [    0.022561] CPU0: Thermal monitoring enabled (TM1)
Jun  3 09:54:40 ubuntu kernel: [    0.022567] using mwait in idle threads.
Jun  3 09:54:40 ubuntu kernel: [    0.031426] ACPI: Core revision 20110112
Jun  3 09:54:40 ubuntu kernel: [    0.035546] ftrace: allocating 24314 entries in 96 pages
Jun  3 09:54:40 ubuntu kernel: [    0.040080] Setting APIC routing to flat
Jun  3 09:54:40 ubuntu kernel: [    0.040398] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun  3 09:54:40 ubuntu kernel: [    0.140437] CPU0: Intel(R) Pentium(R) D CPU 3.40GHz stepping 04
Jun  3 09:54:40 ubuntu kernel: [    0.150000] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
Jun  3 09:54:40 ubuntu kernel: [    0.150000] ... version:                0
Jun  3 09:54:40 ubuntu kernel: [    0.150000] ... bit width:              40
Jun  3 09:54:40 ubuntu kernel: [    0.150000] ... generic registers:      18
Jun  3 09:54:40 ubuntu kernel: [    0.150000] ... value mask:             000000ffffffffff
Jun  3 09:54:40 ubuntu kernel: [    0.150000] ... max period:             0000007fffffffff
Jun  3 09:54:40 ubuntu kernel: [    0.150000] ... fixed-purpose events:   0
Jun  3 09:54:40 ubuntu kernel: [    0.150000] ... event mask:             000000000003ffff
Jun  3 09:54:40 ubuntu kernel: [    0.150000] Booting Node   0, Processors  #1 Ok.
Jun  3 09:54:40 ubuntu kernel: [    0.310019] Brought up 2 CPUs
Jun  3 09:54:40 ubuntu kernel: [    0.310025] Total of 2 processors activated (13566.73 BogoMIPS).
Jun  3 09:54:40 ubuntu kernel: [    0.310655] devtmpfs: initialized
Jun  3 09:54:40 ubuntu kernel: [    0.311116] print_constraints: dummy: 
Jun  3 09:54:40 ubuntu kernel: [    0.311145] Time:  9:52:41  Date: 06/03/11
Jun  3 09:54:40 ubuntu kernel: [    0.311197] NET: Registered protocol family 16
Jun  3 09:54:40 ubuntu kernel: [    0.311300] Trying to unpack rootfs image as initramfs...
Jun  3 09:54:40 ubuntu kernel: [    1.310287] ACPI: bus type pci registered
Jun  3 09:54:40 ubuntu kernel: [    1.310358] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xd0000000-0xdfffffff] (base 0xd0000000)
Jun  3 09:54:40 ubuntu kernel: [    1.310362] PCI: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub with MMCONFIG support
Jun  3 09:54:40 ubuntu kernel: [    1.310368] PCI: not using MMCONFIG
Jun  3 09:54:40 ubuntu kernel: [    1.310371] PCI: Using configuration type 1 for base access
Jun  3 09:54:40 ubuntu kernel: [    1.311575] bio: create slab <bio-0> at 0
Jun  3 09:54:40 ubuntu kernel: [    1.312688] ACPI: EC: Look up EC in DSDT
Jun  3 09:54:40 ubuntu kernel: [    1.315801] ACPI: Interpreter enabled
Jun  3 09:54:40 ubuntu kernel: [    1.315805] ACPI: (supports S0 S1 S3 S4 S5)
Jun  3 09:54:40 ubuntu kernel: [    1.315832] ACPI: Using IOAPIC for interrupt routing
Jun  3 09:54:40 ubuntu kernel: [    1.321162] ACPI: No dock devices found.
Jun  3 09:54:40 ubuntu kernel: [    1.321166] HEST: Table not found.
Jun  3 09:54:40 ubuntu kernel: [    1.321170] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Jun  3 09:54:40 ubuntu kernel: [    1.321293] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jun  3 09:54:40 ubuntu kernel: [    1.321531] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Jun  3 09:54:40 ubuntu kernel: [    1.321536] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
Jun  3 09:54:40 ubuntu kernel: [    1.321539] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Jun  3 09:54:40 ubuntu kernel: [    1.321542] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000dffff] (ignored)
Jun  3 09:54:40 ubuntu kernel: [    1.321545] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xcfffffff] (ignored)
Jun  3 09:54:40 ubuntu kernel: [    1.321548] pci_root PNP0A08:00: host bridge window [mem 0xe0000000-0xfebfffff] (ignored)
Jun  3 09:54:40 ubuntu kernel: [    1.321551] pci_root PNP0A08:00: host bridge window [mem 0xfed00000-0xfedfffff] (ignored)
Jun  3 09:54:40 ubuntu kernel: [    1.321554] pci_root PNP0A08:00: host bridge window [mem 0xfef00000-0xffafffff] (ignored)
Jun  3 09:54:40 ubuntu kernel: [    1.321557] pci_root PNP0A08:00: host bridge window [mem 0xffc00000-0xffefffff] (ignored)
Jun  3 09:54:40 ubuntu kernel: [    1.321571] pci 0000:00:00.0: [8086:2770] type 0 class 0x000600
Jun  3 09:54:40 ubuntu kernel: [    1.321621] pci 0000:00:02.0: [8086:2772] type 0 class 0x000300
Jun  3 09:54:40 ubuntu kernel: [    1.321634] pci 0000:00:02.0: reg 10: [mem 0xf0080000-0xf00fffff]
Jun  3 09:54:40 ubuntu kernel: [    1.321641] pci 0000:00:02.0: reg 14: [io  0x2000-0x2007]
Jun  3 09:54:40 ubuntu kernel: [    1.321650] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff pref]
Jun  3 09:54:40 ubuntu kernel: [    1.321657] pci 0000:00:02.0: reg 1c: [mem 0xf0040000-0xf007ffff]
Jun  3 09:54:40 ubuntu kernel: [    1.321731] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
Jun  3 09:54:40 ubuntu kernel: [    1.321749] pci 0000:00:1b.0: reg 10: [mem 0xf0000000-0xf0003fff 64bit]
Jun  3 09:54:40 ubuntu kernel: [    1.321811] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jun  3 09:54:40 ubuntu kernel: [    1.321816] pci 0000:00:1b.0: PME# disabled
Jun  3 09:54:40 ubuntu kernel: [    1.321838] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
Jun  3 09:54:40 ubuntu kernel: [    1.321902] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jun  3 09:54:40 ubuntu kernel: [    1.321907] pci 0000:00:1c.0: PME# disabled
Jun  3 09:54:40 ubuntu kernel: [    1.321929] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
Jun  3 09:54:40 ubuntu kernel: [    1.321993] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jun  3 09:54:40 ubuntu kernel: [    1.321997] pci 0000:00:1c.1: PME# disabled
Jun  3 09:54:40 ubuntu kernel: [    1.322020] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
Jun  3 09:54:40 ubuntu kernel: [    1.322081] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jun  3 09:54:40 ubuntu kernel: [    1.322085] pci 0000:00:1c.2: PME# disabled
Jun  3 09:54:40 ubuntu kernel: [    1.322112] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
Jun  3 09:54:40 ubuntu kernel: [    1.322176] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jun  3 09:54:40 ubuntu kernel: [    1.322180] pci 0000:00:1c.3: PME# disabled
Jun  3 09:54:40 ubuntu kernel: [    1.322206] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
Jun  3 09:54:40 ubuntu kernel: [    1.322253] pci 0000:00:1d.0: reg 20: [io  0x2400-0x241f]
Jun  3 09:54:40 ubuntu kernel: [    1.322288] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
Jun  3 09:54:40 ubuntu kernel: [    1.322333] pci 0000:00:1d.1: reg 20: [io  0x2800-0x281f]
Jun  3 09:54:40 ubuntu kernel: [    1.322367] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
Jun  3 09:54:40 ubuntu kernel: [    1.322412] pci 0000:00:1d.2: reg 20: [io  0x2c00-0x2c1f]
Jun  3 09:54:40 ubuntu kernel: [    1.322445] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
Jun  3 09:54:40 ubuntu kernel: [    1.322489] pci 0000:00:1d.3: reg 20: [io  0x3000-0x301f]
Jun  3 09:54:40 ubuntu kernel: [    1.322530] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
Jun  3 09:54:40 ubuntu kernel: [    1.322550] pci 0000:00:1d.7: reg 10: [mem 0xf0004000-0xf00043ff]
Jun  3 09:54:40 ubuntu kernel: [    1.322622] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jun  3 09:54:40 ubuntu kernel: [    1.322627] pci 0000:00:1d.7: PME# disabled
Jun  3 09:54:40 ubuntu kernel: [    1.322644] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
Jun  3 09:54:40 ubuntu kernel: [    1.322709] pci 0000:00:1f.0: [8086:27b8] type 0 class 0x000601
Jun  3 09:54:40 ubuntu kernel: [    1.322802] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
Jun  3 09:54:40 ubuntu kernel: [    1.322811] pci 0000:00:1f.0: quirk: [io  0xf000-0xf07f] claimed by ICH6 ACPI/GPIO/TCO
Jun  3 09:54:40 ubuntu kernel: [    1.322818] pci 0000:00:1f.0: quirk: [io  0xf180-0xf1bf] claimed by ICH6 GPIO
Jun  3 09:54:40 ubuntu kernel: [    1.322822] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 00ff)
Jun  3 09:54:40 ubuntu kernel: [    1.322868] pci 0000:00:1f.2: [8086:27c0] type 0 class 0x000101
Jun  3 09:54:40 ubuntu kernel: [    1.322885] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
Jun  3 09:54:40 ubuntu kernel: [    1.322894] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
Jun  3 09:54:40 ubuntu kernel: [    1.322903] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
Jun  3 09:54:40 ubuntu kernel: [    1.322912] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
Jun  3 09:54:40 ubuntu kernel: [    1.322921] pci 0000:00:1f.2: reg 20: [io  0x3800-0x380f]
Jun  3 09:54:40 ubuntu kernel: [    1.322954] pci 0000:00:1f.2: PME# supported from D3hot
Jun  3 09:54:40 ubuntu kernel: [    1.322958] pci 0000:00:1f.2: PME# disabled
Jun  3 09:54:40 ubuntu kernel: [    1.322974] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
Jun  3 09:54:40 ubuntu kernel: [    1.323029] pci 0000:00:1f.3: reg 20: [io  0x3400-0x341f]
Jun  3 09:54:40 ubuntu kernel: [    1.323111] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
Jun  3 09:54:40 ubuntu kernel: [    1.323116] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
Jun  3 09:54:40 ubuntu kernel: [    1.323121] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jun  3 09:54:40 ubuntu kernel: [    1.323128] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jun  3 09:54:40 ubuntu kernel: [    1.323196] pci 0000:05:00.0: [14e4:1677] type 0 class 0x000200
Jun  3 09:54:40 ubuntu kernel: [    1.323221] pci 0000:05:00.0: reg 10: [mem 0xf0100000-0xf010ffff 64bit]
Jun  3 09:54:40 ubuntu kernel: [    1.323323] pci 0000:05:00.0: PME# supported from D3hot D3cold
Jun  3 09:54:40 ubuntu kernel: [    1.323328] pci 0000:05:00.0: PME# disabled
Jun  3 09:54:40 ubuntu kernel: [    1.323341] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Jun  3 09:54:40 ubuntu kernel: [    1.323357] pci 0000:00:1c.1: PCI bridge to [bus 05-05]
Jun  3 09:54:40 ubuntu kernel: [    1.323361] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
Jun  3 09:54:40 ubuntu kernel: [    1.323366] pci 0000:00:1c.1:   bridge window [mem 0xf0100000-0xf01fffff]
Jun  3 09:54:40 ubuntu kernel: [    1.323373] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jun  3 09:54:40 ubuntu kernel: [    1.323420] pci 0000:00:1c.2: PCI bridge to [bus 07-07]
Jun  3 09:54:40 ubuntu kernel: [    1.323424] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
Jun  3 09:54:40 ubuntu kernel: [    1.323429] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jun  3 09:54:40 ubuntu kernel: [    1.323436] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jun  3 09:54:40 ubuntu kernel: [    1.323481] pci 0000:00:1c.3: PCI bridge to [bus 09-09]
Jun  3 09:54:40 ubuntu kernel: [    1.323486] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
Jun  3 09:54:40 ubuntu kernel: [    1.323491] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jun  3 09:54:40 ubuntu kernel: [    1.323497] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jun  3 09:54:40 ubuntu kernel: [    1.323566] pci 0000:00:1e.0: PCI bridge to [bus 0b-0b] (subtractive decode)
Jun  3 09:54:40 ubuntu kernel: [    1.323571] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
Jun  3 09:54:40 ubuntu kernel: [    1.323576] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jun  3 09:54:40 ubuntu kernel: [    1.323582] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jun  3 09:54:40 ubuntu kernel: [    1.323586] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Jun  3 09:54:40 ubuntu kernel: [    1.323589] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
Jun  3 09:54:40 ubuntu kernel: [    1.323617] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun  3 09:54:40 ubuntu kernel: [    1.323782] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXB._PRT]
Jun  3 09:54:40 ubuntu kernel: [    1.323841] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXC._PRT]
Jun  3 09:54:40 ubuntu kernel: [    1.323899] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXD._PRT]
Jun  3 09:54:40 ubuntu kernel: [    1.323956] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXE._PRT]
Jun  3 09:54:40 ubuntu kernel: [    1.324035] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIH._PRT]
Jun  3 09:54:40 ubuntu kernel: [    1.328211] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Jun  3 09:54:40 ubuntu kernel: [    1.328294] ACPI: PCI Interrupt Link [LNKB] (IRQs 9 10 *11)
Jun  3 09:54:40 ubuntu kernel: [    1.328374] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
Jun  3 09:54:40 ubuntu kernel: [    1.328453] ACPI: PCI Interrupt Link [LNKD] (IRQs *9 10 11)
Jun  3 09:54:40 ubuntu kernel: [    1.328534] ACPI: PCI Interrupt Link [LNKE] (IRQs *9 10 11)
Jun  3 09:54:40 ubuntu kernel: [    1.328618] ACPI: PCI Interrupt Link [LNKF] (IRQs 9 10 11) *5
Jun  3 09:54:40 ubuntu kernel: [    1.328698] ACPI: PCI Interrupt Link [LNKG] (IRQs 9 *10 11)
Jun  3 09:54:40 ubuntu kernel: [    1.328779] ACPI: PCI Interrupt Link [LNKH] (IRQs 9 10 *11)
Jun  3 09:54:40 ubuntu kernel: [    1.328916] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jun  3 09:54:40 ubuntu kernel: [    1.328931] vgaarb: loaded
Jun  3 09:54:40 ubuntu kernel: [    1.329171] SCSI subsystem initialized
Jun  3 09:54:40 ubuntu kernel: [    1.329232] libata version 3.00 loaded.
Jun  3 09:54:40 ubuntu kernel: [    1.329298] usbcore: registered new interface driver usbfs
Jun  3 09:54:40 ubuntu kernel: [    1.329313] usbcore: registered new interface driver hub
Jun  3 09:54:40 ubuntu kernel: [    1.329349] usbcore: registered new device driver usb
Jun  3 09:54:40 ubuntu kernel: [    1.329490] wmi: Mapper loaded
Jun  3 09:54:40 ubuntu kernel: [    1.329493] PCI: Using ACPI for IRQ routing
Jun  3 09:54:40 ubuntu kernel: [    1.329496] PCI: pci_cache_line_size set to 64 bytes
Jun  3 09:54:40 ubuntu kernel: [    1.329572] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
Jun  3 09:54:40 ubuntu kernel: [    1.329575] reserve RAM buffer: 000000007f6e0000 - 000000007fffffff 
Jun  3 09:54:40 ubuntu kernel: [    1.329701] NetLabel: Initializing
Jun  3 09:54:40 ubuntu kernel: [    1.329704] NetLabel:  domain hash size = 128
Jun  3 09:54:40 ubuntu kernel: [    1.329705] NetLabel:  protocols = UNLABELED CIPSOv4
Jun  3 09:54:40 ubuntu kernel: [    1.329720] NetLabel:  unlabeled traffic allowed by default
Jun  3 09:54:40 ubuntu kernel: [    1.329834] hpet clockevent registered
Jun  3 09:54:40 ubuntu kernel: [    1.329839] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Jun  3 09:54:40 ubuntu kernel: [    1.329844] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun  3 09:54:40 ubuntu kernel: [    1.329849] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Jun  3 09:54:40 ubuntu kernel: [    2.960130] Switching to clocksource hpet
Jun  3 09:54:40 ubuntu kernel: [    2.969813] Switched to NOHz mode on CPU #0
Jun  3 09:54:40 ubuntu kernel: [    2.969876] Switched to NOHz mode on CPU #1
Jun  3 09:54:40 ubuntu kernel: [    2.970596] AppArmor: AppArmor Filesystem Enabled
Jun  3 09:54:40 ubuntu kernel: [    2.970640] pnp: PnP ACPI init
Jun  3 09:54:40 ubuntu kernel: [    2.970667] ACPI: bus type pnp registered
Jun  3 09:54:40 ubuntu kernel: [    2.970850] pnp 00:00: [bus 00-ff]
Jun  3 09:54:40 ubuntu kernel: [    2.970855] pnp 00:00: [io  0x0000-0x0cf7 window]
Jun  3 09:54:40 ubuntu kernel: [    2.970858] pnp 00:00: [io  0x0d00-0xffff window]
Jun  3 09:54:40 ubuntu kernel: [    2.970860] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jun  3 09:54:40 ubuntu kernel: [    2.970863] pnp 00:00: [mem 0x000c8000-0x000dffff window]
Jun  3 09:54:40 ubuntu kernel: [    2.970866] pnp 00:00: [mem 0x80000000-0xcfffffff window]
Jun  3 09:54:40 ubuntu kernel: [    2.970868] pnp 00:00: [mem 0xe0000000-0xfebfffff window]
Jun  3 09:54:40 ubuntu kernel: [    2.970871] pnp 00:00: [mem 0xfed00000-0xfedfffff window]
Jun  3 09:54:40 ubuntu kernel: [    2.970874] pnp 00:00: [mem 0xfef00000-0xffafffff window]
Jun  3 09:54:40 ubuntu kernel: [    2.970876] pnp 00:00: [mem 0xffc00000-0xffefffff window]
Jun  3 09:54:40 ubuntu kernel: [    2.970879] pnp 00:00: [io  0x0cf8-0x0cff]
Jun  3 09:54:40 ubuntu kernel: [    2.970961] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Jun  3 09:54:40 ubuntu kernel: [    2.971063] pnp 00:01: [io  0x0cb0-0x0cbb]
Jun  3 09:54:40 ubuntu kernel: [    2.971144] system 00:01: [io  0x0cb0-0x0cbb] has been reserved
Jun  3 09:54:40 ubuntu kernel: [    2.971149] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
Jun  3 09:54:40 ubuntu kernel: [    2.971339] pnp 00:02: [mem 0xffb00000-0xffbfffff]
Jun  3 09:54:40 ubuntu kernel: [    2.971385] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
Jun  3 09:54:40 ubuntu kernel: [    2.971524] pnp 00:03: [io  0x0010-0x001f]
Jun  3 09:54:40 ubuntu kernel: [    2.971528] pnp 00:03: [io  0x0022-0x002d]
Jun  3 09:54:40 ubuntu kernel: [    2.971530] pnp 00:03: [io  0x0030-0x003f]
Jun  3 09:54:40 ubuntu kernel: [    2.971532] pnp 00:03: [io  0x0050-0x0053]
Jun  3 09:54:40 ubuntu kernel: [    2.971534] pnp 00:03: [io  0x0062-0x0063]
Jun  3 09:54:40 ubuntu kernel: [    2.971536] pnp 00:03: [io  0x0065-0x006f]
Jun  3 09:54:40 ubuntu kernel: [    2.971544] pnp 00:03: [io  0x0074-0x007f]
Jun  3 09:54:40 ubuntu kernel: [    2.971546] pnp 00:03: [io  0x0090-0x009f]
Jun  3 09:54:40 ubuntu kernel: [    2.971548] pnp 00:03: [io  0x00a2-0x00b1]
Jun  3 09:54:40 ubuntu kernel: [    2.971550] pnp 00:03: [io  0x00b2-0x00b3]
Jun  3 09:54:40 ubuntu kernel: [    2.971553] pnp 00:03: [io  0x00b4-0x00bf]
Jun  3 09:54:40 ubuntu kernel: [    2.971555] pnp 00:03: [io  0x00ec-0x00ef]
Jun  3 09:54:40 ubuntu kernel: [    2.971557] pnp 00:03: [io  0x0072-0x0073]
Jun  3 09:54:40 ubuntu kernel: [    2.971559] pnp 00:03: [io  0x002e-0x002f]
Jun  3 09:54:40 ubuntu kernel: [    2.971562] pnp 00:03: [io  0x04d0-0x04d1]
Jun  3 09:54:40 ubuntu kernel: [    2.971564] pnp 00:03: [io  0xf000-0xf07f]
Jun  3 09:54:40 ubuntu kernel: [    2.971568] pnp 00:03: [io  0xf100-0xf10f]
Jun  3 09:54:40 ubuntu kernel: [    2.971570] pnp 00:03: [io  0xf180-0xf1bf]
Jun  3 09:54:40 ubuntu kernel: [    2.971572] pnp 00:03: [io  0x0800-0x087f]
Jun  3 09:54:40 ubuntu kernel: [    2.971574] pnp 00:03: [io  0xf820-0xf82f]
Jun  3 09:54:40 ubuntu kernel: [    2.971577] pnp 00:03: [io  0xfe00]
Jun  3 09:54:40 ubuntu kernel: [    2.971579] pnp 00:03: [mem 0xfec00000-0xfecfffff]
Jun  3 09:54:40 ubuntu kernel: [    2.971581] pnp 00:03: [mem 0xfee00000-0xfeefffff]
Jun  3 09:54:40 ubuntu kernel: [    2.971583] pnp 00:03: [mem 0xfed1c000-0xfed1ffff]
Jun  3 09:54:40 ubuntu kernel: [    2.971586] pnp 00:03: [mem 0xfed13000-0xfed13fff]
Jun  3 09:54:40 ubuntu kernel: [    2.971588] pnp 00:03: [mem 0xfed14000-0xfed17fff]
Jun  3 09:54:40 ubuntu kernel: [    2.971590] pnp 00:03: [mem 0xfed18000-0xfed18fff]
Jun  3 09:54:40 ubuntu kernel: [    2.971592] pnp 00:03: [mem 0xfed19000-0xfed19fff]
Jun  3 09:54:40 ubuntu kernel: [    2.971595] pnp 00:03: [mem 0xd0000000-0xdfffffff]
Jun  3 09:54:40 ubuntu kernel: [    2.971677] system 00:03: [io  0x04d0-0x04d1] has been reserved
Jun  3 09:54:40 ubuntu kernel: [    2.971681] system 00:03: [io  0xf000-0xf07f] has been reserved
Jun  3 09:54:40 ubuntu kernel: [    2.971684] system 00:03: [io  0xf100-0xf10f] has been reserved
Jun  3 09:54:40 ubuntu kernel: [    2.971687] system 00:03: [io  0xf180-0xf1bf] has been reserved
Jun  3 09:54:40 ubuntu kernel: [    2.971690] system 00:03: [io  0x0800-0x087f] has been reserved
Jun  3 09:54:40 ubuntu kernel: [    2.971692] system 00:03: [io  0xf820-0xf82f] has been reserved
Jun  3 09:54:40 ubuntu kernel: [    2.971695] system 00:03: [io  0xfe00] has been reserved
Jun  3 09:54:40 ubuntu kernel: [    2.971705] system 00:03: [mem 0xfec00000-0xfecfffff] could not be reserved
Jun  3 09:54:40 ubuntu kernel: [    2.971709] system 00:03: [mem 0xfee00000-0xfeefffff] has been reserved
Jun  3 09:54:40 ubuntu kernel: [    2.971712] system 00:03: [mem 0xfed1c000-0xfed1ffff] has been reserved
Jun  3 09:54:40 ubuntu kernel: [    2.971715] system 00:03: [mem 0xfed13000-0xfed13fff] has been reserved
Jun  3 09:54:40 ubuntu kernel: [    2.971718] system 00:03: [mem 0xfed14000-0xfed17fff] has been reserved
Jun  3 09:54:40 ubuntu kernel: [    2.971721] system 00:03: [mem 0xfed18000-0xfed18fff] has been reserved
Jun  3 09:54:40 ubuntu kernel: [    2.971725] system 00:03: [mem 0xfed19000-0xfed19fff] has been reserved
Jun  3 09:54:40 ubuntu kernel: [    2.971728] system 00:03: [mem 0xd0000000-0xdfffffff] has been reserved
Jun  3 09:54:40 ubuntu kernel: [    2.971732] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun  3 09:54:40 ubuntu kernel: [    2.971750] pnp 00:04: [io  0x0000-0x000f]
Jun  3 09:54:40 ubuntu kernel: [    2.971753] pnp 00:04: [io  0x0080-0x008f]
Jun  3 09:54:40 ubuntu kernel: [    2.971755] pnp 00:04: [io  0x00c0-0x00df]
Jun  3 09:54:40 ubuntu kernel: [    2.971758] pnp 00:04: [dma 4]
Jun  3 09:54:40 ubuntu kernel: [    2.971810] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
Jun  3 09:54:40 ubuntu kernel: [    2.971831] pnp 00:05: [io  0x0070-0x0071]
Jun  3 09:54:40 ubuntu kernel: [    2.971850] pnp 00:05: [irq 8]
Jun  3 09:54:40 ubuntu kernel: [    2.971897] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
Jun  3 09:54:40 ubuntu kernel: [    2.971925] pnp 00:06: [io  0x00f0-0x00fe]
Jun  3 09:54:40 ubuntu kernel: [    2.971932] pnp 00:06: [irq 13]
Jun  3 09:54:40 ubuntu kernel: [    2.971989] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Jun  3 09:54:40 ubuntu kernel: [    2.972005] pnp 00:07: [io  0x0061]
Jun  3 09:54:40 ubuntu kernel: [    2.972053] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
Jun  3 09:54:40 ubuntu kernel: [    2.972136] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (disabled)
Jun  3 09:54:40 ubuntu kernel: [    2.972187] pnp 00:09: [io  0x0060]
Jun  3 09:54:40 ubuntu kernel: [    2.972190] pnp 00:09: [io  0x0064]
Jun  3 09:54:40 ubuntu kernel: [    2.972197] pnp 00:09: [irq 1]
Jun  3 09:54:40 ubuntu kernel: [    2.972246] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
Jun  3 09:54:40 ubuntu kernel: [    2.972343] pnp 00:0a: [irq 12]
Jun  3 09:54:40 ubuntu kernel: [    2.972399] pnp 00:0a: Plug and Play ACPI device, IDs PNP0f13 (active)
Jun  3 09:54:40 ubuntu kernel: [    2.972481] pnp 00:0b: [io  0x03f0-0x03f5]
Jun  3 09:54:40 ubuntu kernel: [    2.972484] pnp 00:0b: [io  0x03f7]
Jun  3 09:54:40 ubuntu kernel: [    2.972486] pnp 00:0b: [dma 2]
Jun  3 09:54:40 ubuntu kernel: [    2.972493] pnp 00:0b: [irq 6]
Jun  3 09:54:40 ubuntu kernel: [    2.972564] pnp 00:0b: Plug and Play ACPI device, IDs PNP0700 (active)
Jun  3 09:54:40 ubuntu kernel: [    2.972887] pnp 00:0c: [io  0x0378-0x037f]
Jun  3 09:54:40 ubuntu kernel: [    2.972890] pnp 00:0c: [io  0x0778-0x077f]
Jun  3 09:54:40 ubuntu kernel: [    2.972898] pnp 00:0c: [irq 7]
Jun  3 09:54:40 ubuntu kernel: [    2.972900] pnp 00:0c: [dma 3]
Jun  3 09:54:40 ubuntu kernel: [    2.972973] pnp 00:0c: Plug and Play ACPI device, IDs PNP0401 (active)
Jun  3 09:54:40 ubuntu kernel: [    2.973151] pnp 00:0d: [io  0x03f8-0x03ff]
Jun  3 09:54:40 ubuntu kernel: [    2.973158] pnp 00:0d: [irq 4]
Jun  3 09:54:40 ubuntu kernel: [    2.973232] pnp 00:0d: Plug and Play ACPI device, IDs PNP0501 (active)
Jun  3 09:54:40 ubuntu kernel: [    2.973283] pnp: PnP ACPI: found 14 devices
Jun  3 09:54:40 ubuntu kernel: [    2.973286] ACPI: ACPI bus type pnp unregistered
Jun  3 09:54:40 ubuntu kernel: [    2.980472] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x801fffff]
Jun  3 09:54:40 ubuntu kernel: [    2.980477] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
Jun  3 09:54:40 ubuntu kernel: [    2.980481] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
Jun  3 09:54:40 ubuntu kernel: [    2.980486] pci 0000:00:1c.2: BAR 14: assigned [mem 0x80600000-0x807fffff]
Jun  3 09:54:40 ubuntu kernel: [    2.980490] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80800000-0x809fffff 64bit pref]
Jun  3 09:54:40 ubuntu kernel: [    2.980494] pci 0000:00:1c.3: BAR 14: assigned [mem 0x80a00000-0x80bfffff]
Jun  3 09:54:40 ubuntu kernel: [    2.980498] pci 0000:00:1c.3: BAR 15: assigned [mem 0x80c00000-0x80dfffff 64bit pref]
Jun  3 09:54:40 ubuntu kernel: [    2.980502] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
Jun  3 09:54:40 ubuntu kernel: [    2.980505] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
Jun  3 09:54:40 ubuntu kernel: [    2.980509] pci 0000:00:1c.2: BAR 13: assigned [io  0x5000-0x5fff]
Jun  3 09:54:40 ubuntu kernel: [    2.980512] pci 0000:00:1c.3: BAR 13: assigned [io  0x6000-0x6fff]
Jun  3 09:54:40 ubuntu kernel: [    2.980515] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
Jun  3 09:54:40 ubuntu kernel: [    2.980519] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
Jun  3 09:54:40 ubuntu kernel: [    2.980525] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff]
Jun  3 09:54:40 ubuntu kernel: [    2.980530] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
Jun  3 09:54:40 ubuntu kernel: [    2.980539] pci 0000:00:1c.1: PCI bridge to [bus 05-05]
Jun  3 09:54:40 ubuntu kernel: [    2.980543] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
Jun  3 09:54:40 ubuntu kernel: [    2.980549] pci 0000:00:1c.1:   bridge window [mem 0xf0100000-0xf01fffff]
Jun  3 09:54:40 ubuntu kernel: [    2.980555] pci 0000:00:1c.1:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
Jun  3 09:54:40 ubuntu kernel: [    2.980562] pci 0000:00:1c.2: PCI bridge to [bus 07-07]
Jun  3 09:54:40 ubuntu kernel: [    2.980566] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
Jun  3 09:54:40 ubuntu kernel: [    2.980572] pci 0000:00:1c.2:   bridge window [mem 0x80600000-0x807fffff]
Jun  3 09:54:40 ubuntu kernel: [    2.980577] pci 0000:00:1c.2:   bridge window [mem 0x80800000-0x809fffff 64bit pref]
Jun  3 09:54:40 ubuntu kernel: [    2.980585] pci 0000:00:1c.3: PCI bridge to [bus 09-09]
Jun  3 09:54:40 ubuntu kernel: [    2.980588] pci 0000:00:1c.3:   bridge window [io  0x6000-0x6fff]
Jun  3 09:54:40 ubuntu kernel: [    2.980595] pci 0000:00:1c.3:   bridge window [mem 0x80a00000-0x80bfffff]
Jun  3 09:54:40 ubuntu kernel: [    2.980601] pci 0000:00:1c.3:   bridge window [mem 0x80c00000-0x80dfffff 64bit pref]
Jun  3 09:54:40 ubuntu kernel: [    2.980609] pci 0000:00:1e.0: PCI bridge to [bus 0b-0b]
Jun  3 09:54:40 ubuntu kernel: [    2.980611] pci 0000:00:1e.0:   bridge window [io  disabled]
Jun  3 09:54:40 ubuntu kernel: [    2.980617] pci 0000:00:1e.0:   bridge window [mem disabled]
Jun  3 09:54:40 ubuntu kernel: [    2.980621] pci 0000:00:1e.0:   bridge window [mem pref disabled]
Jun  3 09:54:40 ubuntu kernel: [    2.980636] pci 0000:00:1c.0: enabling device (0000 -> 0003)
Jun  3 09:54:40 ubuntu kernel: [    2.980653] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun  3 09:54:40 ubuntu kernel: [    2.980660] pci 0000:00:1c.0: setting latency timer to 64
Jun  3 09:54:40 ubuntu kernel: [    2.980674] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Jun  3 09:54:40 ubuntu kernel: [    2.980680] pci 0000:00:1c.1: setting latency timer to 64
Jun  3 09:54:40 ubuntu kernel: [    2.980687] pci 0000:00:1c.2: enabling device (0000 -> 0003)
Jun  3 09:54:40 ubuntu kernel: [    2.980697] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun  3 09:54:40 ubuntu kernel: [    2.980703] pci 0000:00:1c.2: setting latency timer to 64
Jun  3 09:54:40 ubuntu kernel: [    2.980711] pci 0000:00:1c.3: enabling device (0000 -> 0003)
Jun  3 09:54:40 ubuntu kernel: [    2.980721] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jun  3 09:54:40 ubuntu kernel: [    2.980728] pci 0000:00:1c.3: setting latency timer to 64
Jun  3 09:54:40 ubuntu kernel: [    2.980737] pci 0000:00:1e.0: setting latency timer to 64
Jun  3 09:54:40 ubuntu kernel: [    2.980742] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
Jun  3 09:54:40 ubuntu kernel: [    2.980745] pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]
Jun  3 09:54:40 ubuntu kernel: [    2.980748] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
Jun  3 09:54:40 ubuntu kernel: [    2.980751] pci_bus 0000:03: resource 1 [mem 0x80000000-0x801fffff]
Jun  3 09:54:40 ubuntu kernel: [    2.980754] pci_bus 0000:03: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
Jun  3 09:54:40 ubuntu kernel: [    2.980757] pci_bus 0000:05: resource 0 [io  0x4000-0x4fff]
Jun  3 09:54:40 ubuntu kernel: [    2.980759] pci_bus 0000:05: resource 1 [mem 0xf0100000-0xf01fffff]
Jun  3 09:54:40 ubuntu kernel: [    2.980762] pci_bus 0000:05: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
Jun  3 09:54:40 ubuntu kernel: [    2.980765] pci_bus 0000:07: resource 0 [io  0x5000-0x5fff]
Jun  3 09:54:40 ubuntu kernel: [    2.980767] pci_bus 0000:07: resource 1 [mem 0x80600000-0x807fffff]
Jun  3 09:54:40 ubuntu kernel: [    2.980770] pci_bus 0000:07: resource 2 [mem 0x80800000-0x809fffff 64bit pref]
Jun  3 09:54:40 ubuntu kernel: [    2.980773] pci_bus 0000:09: resource 0 [io  0x6000-0x6fff]
Jun  3 09:54:40 ubuntu kernel: [    2.980776] pci_bus 0000:09: resource 1 [mem 0x80a00000-0x80bfffff]
Jun  3 09:54:40 ubuntu kernel: [    2.980778] pci_bus 0000:09: resource 2 [mem 0x80c00000-0x80dfffff 64bit pref]
Jun  3 09:54:40 ubuntu kernel: [    2.980781] pci_bus 0000:0b: resource 4 [io  0x0000-0xffff]
Jun  3 09:54:40 ubuntu kernel: [    2.980784] pci_bus 0000:0b: resource 5 [mem 0x00000000-0xfffffffff]
Jun  3 09:54:40 ubuntu kernel: [    2.980840] NET: Registered protocol family 2
Jun  3 09:54:40 ubuntu kernel: [    2.981055] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Jun  3 09:54:40 ubuntu kernel: [    2.982652] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Jun  3 09:54:40 ubuntu kernel: [    2.985715] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun  3 09:54:40 ubuntu kernel: [    2.986571] TCP: Hash tables configured (established 262144 bind 65536)
Jun  3 09:54:40 ubuntu kernel: [    2.986573] TCP reno registered
Jun  3 09:54:40 ubuntu kernel: [    2.986589] UDP hash table entries: 1024 (order: 3, 32768 bytes)
Jun  3 09:54:40 ubuntu kernel: [    2.986635] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
Jun  3 09:54:40 ubuntu kernel: [    2.986821] NET: Registered protocol family 1
Jun  3 09:54:40 ubuntu kernel: [    2.986854] pci 0000:00:02.0: Boot video device
Jun  3 09:54:40 ubuntu kernel: [    4.290496] Freeing initrd memory: 13568k freed
Jun  3 09:54:40 ubuntu kernel: [    4.980022] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
Jun  3 09:54:40 ubuntu kernel: [    4.980059] PCI: CLS 32 bytes, default 64
Jun  3 09:54:40 ubuntu kernel: [    4.980125] Simple Boot Flag at 0x69 set to 0x1
Jun  3 09:54:40 ubuntu kernel: [    4.980514] audit: initializing netlink socket (disabled)
Jun  3 09:54:40 ubuntu kernel: [    4.980531] type=2000 audit(1307094764.980:1): initialized
Jun  3 09:54:40 ubuntu kernel: [    4.993681] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun  3 09:54:40 ubuntu kernel: [    4.996146] VFS: Disk quotas dquot_6.5.2
Jun  3 09:54:40 ubuntu kernel: [    4.996220] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun  3 09:54:40 ubuntu kernel: [    4.997166] fuse init (API version 7.16)
Jun  3 09:54:40 ubuntu kernel: [    4.997326] msgmni has been set to 3994
Jun  3 09:54:40 ubuntu kernel: [    4.997737] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun  3 09:54:40 ubuntu kernel: [    4.997793] io scheduler noop registered
Jun  3 09:54:40 ubuntu kernel: [    4.997796] io scheduler deadline registered
Jun  3 09:54:40 ubuntu kernel: [    4.997879] io scheduler cfq registered (default)
Jun  3 09:54:40 ubuntu kernel: [    4.998232] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun  3 09:54:40 ubuntu kernel: [    4.998261] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun  3 09:54:40 ubuntu kernel: [    4.998434] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jun  3 09:54:40 ubuntu kernel: [    4.998441] ACPI: Power Button [PWRB]
Jun  3 09:54:40 ubuntu kernel: [    4.998508] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun  3 09:54:40 ubuntu kernel: [    4.998513] ACPI: Power Button [PWRF]
Jun  3 09:54:40 ubuntu kernel: [    4.998678] ACPI: acpi_idle registered with cpuidle
Jun  3 09:54:40 ubuntu kernel: [    5.000286] ERST: Table is not found!
Jun  3 09:54:40 ubuntu kernel: [    5.000360] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jun  3 09:54:40 ubuntu kernel: [    5.020946] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun  3 09:54:40 ubuntu kernel: [    5.450834] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun  3 09:54:40 ubuntu kernel: [    5.460311] Linux agpgart interface v0.103
Jun  3 09:54:40 ubuntu kernel: [    5.460385] agpgart-intel 0000:00:00.0: Intel 945G Chipset
Jun  3 09:54:40 ubuntu kernel: [    5.460482] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
Jun  3 09:54:40 ubuntu kernel: [    5.461286] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
Jun  3 09:54:40 ubuntu kernel: [    5.461477] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Jun  3 09:54:40 ubuntu kernel: [    5.462959] brd: module loaded
Jun  3 09:54:40 ubuntu kernel: [    5.463646] loop: module loaded
Jun  3 09:54:40 ubuntu kernel: [    5.463768] i2c-core: driver [adp5520] using legacy suspend method
Jun  3 09:54:40 ubuntu kernel: [    5.463770] i2c-core: driver [adp5520] using legacy resume method
Jun  3 09:54:40 ubuntu kernel: [    5.463895] ata_piix 0000:00:1f.2: version 2.13
Jun  3 09:54:40 ubuntu kernel: [    5.463910] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun  3 09:54:40 ubuntu kernel: [    5.463917] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Jun  3 09:54:40 ubuntu kernel: [    5.620035] ata_piix 0000:00:1f.2: setting latency timer to 64
Jun  3 09:54:40 ubuntu kernel: [    5.620503] scsi0 : ata_piix
Jun  3 09:54:40 ubuntu kernel: [    5.620652] scsi1 : ata_piix
Jun  3 09:54:40 ubuntu kernel: [    5.621351] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3800 irq 14
Jun  3 09:54:40 ubuntu kernel: [    5.621354] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x3808 irq 15
Jun  3 09:54:40 ubuntu kernel: [    5.621848] Fixed MDIO Bus: probed
Jun  3 09:54:40 ubuntu kernel: [    5.621890] PPP generic driver version 2.4.2
Jun  3 09:54:40 ubuntu kernel: [    5.621943] tun: Universal TUN/TAP device driver, 1.6
Jun  3 09:54:40 ubuntu kernel: [    5.621945] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun  3 09:54:40 ubuntu kernel: [    5.622057] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun  3 09:54:40 ubuntu kernel: [    5.622086] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun  3 09:54:40 ubuntu kernel: [    5.622104] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jun  3 09:54:40 ubuntu kernel: [    5.622108] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jun  3 09:54:40 ubuntu kernel: [    5.622158] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jun  3 09:54:40 ubuntu kernel: [    5.630081] ehci_hcd 0000:00:1d.7: using broken periodic workaround
Jun  3 09:54:40 ubuntu kernel: [    5.633950] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Jun  3 09:54:40 ubuntu kernel: [    5.633975] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0004000
Jun  3 09:54:40 ubuntu kernel: [    5.650020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jun  3 09:54:40 ubuntu kernel: [    5.650201] hub 1-0:1.0: USB hub found
Jun  3 09:54:40 ubuntu kernel: [    5.650207] hub 1-0:1.0: 8 ports detected
Jun  3 09:54:40 ubuntu kernel: [    5.650306] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun  3 09:54:40 ubuntu kernel: [    5.650322] uhci_hcd: USB Universal Host Controller Interface driver
Jun  3 09:54:40 ubuntu kernel: [    5.650388] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun  3 09:54:40 ubuntu kernel: [    5.650395] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jun  3 09:54:40 ubuntu kernel: [    5.650399] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jun  3 09:54:40 ubuntu kernel: [    5.650444] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jun  3 09:54:40 ubuntu kernel: [    5.660065] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00002400
Jun  3 09:54:40 ubuntu kernel: [    5.660239] hub 2-0:1.0: USB hub found
Jun  3 09:54:40 ubuntu kernel: [    5.660246] hub 2-0:1.0: 2 ports detected
Jun  3 09:54:40 ubuntu kernel: [    5.660332] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Jun  3 09:54:40 ubuntu kernel: [    5.660339] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jun  3 09:54:40 ubuntu kernel: [    5.660343] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jun  3 09:54:40 ubuntu kernel: [    5.660386] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jun  3 09:54:40 ubuntu kernel: [    5.660443] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00002800
Jun  3 09:54:40 ubuntu kernel: [    5.660601] hub 3-0:1.0: USB hub found
Jun  3 09:54:40 ubuntu kernel: [    5.660607] hub 3-0:1.0: 2 ports detected
Jun  3 09:54:40 ubuntu kernel: [    5.660688] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
Jun  3 09:54:40 ubuntu kernel: [    5.660696] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jun  3 09:54:40 ubuntu kernel: [    5.660700] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jun  3 09:54:40 ubuntu kernel: [    5.660747] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jun  3 09:54:40 ubuntu kernel: [    5.670074] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00002c00
Jun  3 09:54:40 ubuntu kernel: [    5.670245] hub 4-0:1.0: USB hub found
Jun  3 09:54:40 ubuntu kernel: [    5.670251] hub 4-0:1.0: 2 ports detected
Jun  3 09:54:40 ubuntu kernel: [    5.670342] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 20 (level, low) -> IRQ 20
Jun  3 09:54:40 ubuntu kernel: [    5.670349] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Jun  3 09:54:40 ubuntu kernel: [    5.670352] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jun  3 09:54:40 ubuntu kernel: [    5.670396] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Jun  3 09:54:40 ubuntu kernel: [    5.670450] uhci_hcd 0000:00:1d.3: irq 20, io base 0x00003000
Jun  3 09:54:40 ubuntu kernel: [    5.670603] hub 5-0:1.0: USB hub found
Jun  3 09:54:40 ubuntu kernel: [    5.670614] hub 5-0:1.0: 2 ports detected
Jun  3 09:54:40 ubuntu kernel: [    5.680097] i8042: PNP: PS/2 Controller [PNP0303:KEYB,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jun  3 09:54:40 ubuntu kernel: [    5.682617] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun  3 09:54:40 ubuntu kernel: [    5.682628] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun  3 09:54:40 ubuntu kernel: [    5.682841] mousedev: PS/2 mouse device common for all mice
Jun  3 09:54:40 ubuntu kernel: [    5.683010] rtc_cmos 00:05: RTC can wake from S4
Jun  3 09:54:40 ubuntu kernel: [    5.683101] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Jun  3 09:54:40 ubuntu kernel: [    5.683128] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jun  3 09:54:40 ubuntu kernel: [    5.683289] device-mapper: uevent: version 1.0.3
Jun  3 09:54:40 ubuntu kernel: [    5.683389] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
Jun  3 09:54:40 ubuntu kernel: [    5.683500] device-mapper: multipath: version 1.2.0 loaded
Jun  3 09:54:40 ubuntu kernel: [    5.683503] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun  3 09:54:40 ubuntu kernel: [    5.683676] cpuidle: using governor ladder
Jun  3 09:54:40 ubuntu kernel: [    5.683680] cpuidle: using governor menu
Jun  3 09:54:40 ubuntu kernel: [    5.684050] TCP cubic registered
Jun  3 09:54:40 ubuntu kernel: [    5.684211] NET: Registered protocol family 10
Jun  3 09:54:40 ubuntu kernel: [    5.684845] NET: Registered protocol family 17
Jun  3 09:54:40 ubuntu kernel: [    5.684867] Registering the dns_resolver key type
Jun  3 09:54:40 ubuntu kernel: [    5.685706] PM: Hibernation image not present or could not be loaded.
Jun  3 09:54:40 ubuntu kernel: [    5.685722] registered taskstats version 1
Jun  3 09:54:40 ubuntu kernel: [    5.685958]   Magic number: 15:515:878
Jun  3 09:54:40 ubuntu kernel: [    5.686048] rtc_cmos 00:05: setting system clock to 2011-06-03 09:52:46 UTC (1307094766)
Jun  3 09:54:40 ubuntu kernel: [    5.686052] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun  3 09:54:40 ubuntu kernel: [    5.686054] EDD information not available.
Jun  3 09:54:40 ubuntu kernel: [    5.705441] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
Jun  3 09:54:40 ubuntu kernel: [    5.800485] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-H10N, JH04, max UDMA/33
Jun  3 09:54:40 ubuntu kernel: [    5.840195] ata2.00: configured for UDMA/33
Jun  3 09:54:40 ubuntu kernel: [    5.848967] ata1.00: ATA-7: ST3808110AS, 3.AAE, max UDMA/133
Jun  3 09:54:40 ubuntu kernel: [    5.848973] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun  3 09:54:40 ubuntu kernel: [    5.932267] ata1.00: configured for UDMA/133
Jun  3 09:54:40 ubuntu kernel: [    5.932413] scsi 0:0:0:0: Direct-Access     ATA      ST3808110AS      3.AA PQ: 0 ANSI: 5
Jun  3 09:54:40 ubuntu kernel: [    5.932597] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun  3 09:54:40 ubuntu kernel: [    5.932704] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Jun  3 09:54:40 ubuntu kernel: [    5.932839] sd 0:0:0:0: [sda] Write Protect is off
Jun  3 09:54:40 ubuntu kernel: [    5.932842] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun  3 09:54:40 ubuntu kernel: [    5.932874] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  3 09:54:40 ubuntu kernel: [    5.936324] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10N  JH04 PQ: 0 ANSI: 5
Jun  3 09:54:40 ubuntu kernel: [    5.940471] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
Jun  3 09:54:40 ubuntu kernel: [    5.940477] cdrom: Uniform CD-ROM driver Revision: 3.20
Jun  3 09:54:40 ubuntu kernel: [    5.940602] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jun  3 09:54:40 ubuntu kernel: [    5.940675] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jun  3 09:54:40 ubuntu kernel: [    5.980028] Refined TSC clocksource calibration: 3391.588 MHz.
Jun  3 09:54:40 ubuntu kernel: [    5.980033] Switching to clocksource tsc
Jun  3 09:54:40 ubuntu kernel: [    6.009124]  sda: sda1 sda2 < sda5 >
Jun  3 09:54:40 ubuntu kernel: [    6.009468] sd 0:0:0:0: [sda] Attached SCSI disk
Jun  3 09:54:40 ubuntu kernel: [    6.011609] Freeing unused kernel memory: 956k freed
Jun  3 09:54:40 ubuntu kernel: [    6.012057] Write protecting the kernel read-only data: 10240k
Jun  3 09:54:40 ubuntu kernel: [    6.012953] Freeing unused kernel memory: 184k freed
Jun  3 09:54:40 ubuntu kernel: [    6.018791] Freeing unused kernel memory: 1444k freed
Jun  3 09:54:40 ubuntu kernel: [    6.053791] <30>udev[72]: starting version 167
Jun  3 09:54:40 ubuntu kernel: [    6.176541] [drm] Initialized drm 1.1.0 20060810
Jun  3 09:54:40 ubuntu kernel: [    6.206737] Floppy drive(s): fd0 is 1.44M
Jun  3 09:54:40 ubuntu kernel: [    6.212935] tg3.c:v3.116 (December 3, 2010)
Jun  3 09:54:40 ubuntu kernel: [    6.212952] tg3 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun  3 09:54:40 ubuntu kernel: [    6.212962] tg3 0000:05:00.0: setting latency timer to 64
Jun  3 09:54:40 ubuntu kernel: [    6.224296] FDC 0 is a post-1991 82077
Jun  3 09:54:40 ubuntu kernel: [    6.241429] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  3 09:54:40 ubuntu kernel: [    6.241436] i915 0000:00:02.0: setting latency timer to 64
Jun  3 09:54:40 ubuntu kernel: [    6.289168] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jun  3 09:54:40 ubuntu kernel: [    6.289172] [drm] Driver supports precise vblank timestamp query.
Jun  3 09:54:40 ubuntu kernel: [    6.294234] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Jun  3 09:54:40 ubuntu kernel: [    6.294597] [drm] initialized overlay support
Jun  3 09:54:40 ubuntu kernel: [    6.352804] Console: switching to colour frame buffer device 128x48
Jun  3 09:54:40 ubuntu kernel: [    6.355444] fb0: inteldrmfb frame buffer device
Jun  3 09:54:40 ubuntu kernel: [    6.355446] drm: registered panic notifier
Jun  3 09:54:40 ubuntu kernel: [    6.355556] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jun  3 09:54:40 ubuntu kernel: [    6.405402] tg3 0000:05:00.0: eth0: Tigon3 [partno(BCM95751) rev 4001] (PCI Express) MAC address 00:30:05:ce:60:ae
Jun  3 09:54:40 ubuntu kernel: [    6.405408] tg3 0000:05:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
Jun  3 09:54:40 ubuntu kernel: [    6.405412] tg3 0000:05:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Jun  3 09:54:40 ubuntu kernel: [    6.405415] tg3 0000:05:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Jun  3 09:54:40 ubuntu kernel: [   10.207546] Btrfs loaded
Jun  3 09:54:40 ubuntu kernel: [   10.218308] xor: automatically using best checksumming function: generic_sse
Jun  3 09:54:40 ubuntu kernel: [   10.260010]    generic_sse:  5175.200 MB/sec
Jun  3 09:54:40 ubuntu kernel: [   10.260012] xor: using function: generic_sse (5175.200 MB/sec)
Jun  3 09:54:40 ubuntu kernel: [   10.267647] device-mapper: dm-raid45: initialized v0.2594b
Jun  3 09:54:40 ubuntu kernel: [   10.386870] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun  3 09:54:40 ubuntu kernel: [   16.300431] ISO 9660 Extensions: Microsoft Joliet Level 3
Jun  3 09:54:40 ubuntu kernel: [   16.362989] ISO 9660 Extensions: RRIP_1991A
Jun  3 09:54:40 ubuntu kernel: [   16.917205] aufs 2.1-standalone.tree-38-rcN-20110207
Jun  3 09:54:40 ubuntu kernel: [   17.064312] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Jun  3 09:54:40 ubuntu kernel: [  119.581860] <30>udev[1120]: starting version 167
Jun  3 09:54:43 ubuntu avahi-daemon[1326]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Jun  3 09:54:43 ubuntu avahi-daemon[1326]: Successfully dropped root privileges.
Jun  3 09:54:43 ubuntu avahi-daemon[1326]: avahi-daemon 0.6.30 starting up.
Jun  3 09:54:44 ubuntu avahi-daemon[1326]: Successfully called chroot().
Jun  3 09:54:44 ubuntu avahi-daemon[1326]: Successfully dropped remaining capabilities.
Jun  3 09:54:44 ubuntu init: ubiquity main process (1328) terminated with status 1
Jun  3 09:54:44 ubuntu avahi-daemon[1329]: chroot.c: open() failed: No such file or directory
Jun  3 09:54:44 ubuntu avahi-daemon[1326]: Failed to open /etc/resolv.conf: Invalid argument
Jun  3 09:54:45 ubuntu avahi-daemon[1326]: Loading service file /services/udisks.service.
Jun  3 09:54:45 ubuntu avahi-daemon[1326]: Network interface enumeration completed.
Jun  3 09:54:45 ubuntu avahi-daemon[1326]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun  3 09:54:45 ubuntu avahi-daemon[1326]: Server startup complete. Host name is ubuntu.local. Local service cookie is 1711807196.
Jun  3 09:54:45 ubuntu avahi-daemon[1326]: Service "ubuntu" (/services/udisks.service) successfully established.
Jun  3 09:54:50 ubuntu NetworkManager[1396]: <info> NetworkManager (version 0.8.3.998) is starting...
Jun  3 09:54:50 ubuntu NetworkManager[1396]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jun  3 09:54:52 ubuntu NetworkManager[1396]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jun  3 09:54:52 ubuntu NetworkManager[1396]: <info> trying to start the modem manager...
Jun  3 09:54:53 ubuntu kernel: [  133.123254] intel_rng: FWH not detected
Jun  3 09:54:53 ubuntu kernel: [  133.128221] parport_pc 00:0c: reported by Plug and Play ACPI
Jun  3 09:54:53 ubuntu kernel: [  133.128282] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jun  3 09:54:54 ubuntu kernel: [  134.035561] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input3
Jun  3 09:54:55 ubuntu kernel: [  134.368287] leds_ss4200: no LED devices found
Jun  3 09:54:56 ubuntu polkitd[1499]: started daemon version 0.101 using authority implementation `local' version `0.101'
Jun  3 09:54:56 ubuntu modem-manager[1491]: <info>  ModemManager (version 0.4) starting...
Jun  3 09:54:56 ubuntu NetworkManager[1396]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun  3 09:54:56 ubuntu modem-manager[1491]: <info>  Loaded plugin AnyData
Jun  3 09:54:56 ubuntu modem-manager[1491]: <info>  Loaded plugin Generic
Jun  3 09:54:56 ubuntu modem-manager[1491]: <info>  Loaded plugin Gobi
Jun  3 09:54:56 ubuntu modem-manager[1491]: <info>  Loaded plugin Option High-Speed
Jun  3 09:54:56 ubuntu NetworkManager[1396]:    SCPlugin-Ifupdown: init!
Jun  3 09:54:56 ubuntu NetworkManager[1396]:    SCPlugin-Ifupdown: update_system_hostname
Jun  3 09:54:56 ubuntu NetworkManager[1396]:    SCPluginIfupdown: management mode: unmanaged
Jun  3 09:54:56 ubuntu NetworkManager[1396]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:05:00.0/net/eth0, iface: eth0)
Jun  3 09:54:56 ubuntu NetworkManager[1396]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:05:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun  3 09:54:56 ubuntu NetworkManager[1396]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun  3 09:54:56 ubuntu NetworkManager[1396]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun  3 09:54:56 ubuntu NetworkManager[1396]:    SCPlugin-Ifupdown: end _init.
Jun  3 09:54:56 ubuntu NetworkManager[1396]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun  3 09:54:57 ubuntu modem-manager[1491]: <info>  Loaded plugin Huawei
Jun  3 09:54:57 ubuntu modem-manager[1491]: <info>  Loaded plugin Linktop
Jun  3 09:54:58 ubuntu kernel: [  137.224359] ppdev: user-space parallel port driver
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun  3 09:54:58 ubuntu NetworkManager[1396]:    Ifupdown: get unmanaged devices count: 0
Jun  3 09:54:58 ubuntu NetworkManager[1396]:    SCPlugin-Ifupdown: (31613296) ... get_connections.
Jun  3 09:54:58 ubuntu NetworkManager[1396]:    SCPlugin-Ifupdown: (31613296) ... get_connections (managed=false): return empty list.
Jun  3 09:54:58 ubuntu NetworkManager[1396]:    Ifupdown: get unmanaged devices count: 0
Jun  3 09:54:58 ubuntu modem-manager[1491]: <info>  Loaded plugin Longcheer
Jun  3 09:54:58 ubuntu modem-manager[1491]: <info>  Loaded plugin Ericsson MBM
Jun  3 09:54:58 ubuntu modem-manager[1491]: <info>  Loaded plugin MotoC
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <info> Networking is enabled by state file
Jun  3 09:54:58 ubuntu modem-manager[1491]: <info>  Loaded plugin Nokia
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <info> (eth0): carrier is OFF
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <info> (eth0): new Ethernet device (driver: 'tg3' ifindex: 2)
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <info> (eth0): now managed
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <info> (eth0): bringing up device.
Jun  3 09:54:58 ubuntu kernel: [  137.555382] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <info> (eth0): preparing device.
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <info> (eth0): deactivating device (reason: 2).
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:05:00.0/net/eth0
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <info> modem-manager is now available
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun  3 09:54:58 ubuntu NetworkManager[1396]: <info> Trying to start the supplicant...
Jun  3 09:54:59 ubuntu modem-manager[1491]: <info>  Loaded plugin Novatel
Jun  3 09:54:59 ubuntu modem-manager[1491]: <info>  Loaded plugin Option
Jun  3 09:54:59 ubuntu modem-manager[1491]: <info>  Loaded plugin Sierra
Jun  3 09:54:59 ubuntu modem-manager[1491]: <info>  Loaded plugin SimTech
Jun  3 09:54:59 ubuntu gdm-binary[1336]: WARNING: Unable to find users: no seat-id found
Jun  3 09:55:00 ubuntu modem-manager[1491]: <info>  Loaded plugin X22X
Jun  3 09:55:00 ubuntu modem-manager[1491]: <info>  Loaded plugin ZTE
Jun  3 09:55:03 ubuntu cron[1671]: (CRON) INFO (pidfile fd = 3)
Jun  3 09:55:04 ubuntu acpid: starting up with proc fs
Jun  3 09:55:04 ubuntu cron[1717]: (CRON) STARTUP (fork ok)
Jun  3 09:55:06 ubuntu cron[1717]: (CRON) INFO (Running @reboot jobs)
Jun  3 09:55:06 ubuntu acpid: 32 rules loaded
Jun  3 09:55:06 ubuntu acpid: waiting for events: event logging is off
Jun  3 09:55:10 ubuntu kernel: [  150.138680] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun  3 09:55:10 ubuntu kernel: [  150.138814] HDA Intel 0000:00:1b.0: irq 40 for MSI/MSI-X
Jun  3 09:55:10 ubuntu kernel: [  150.138851] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jun  3 09:55:15 ubuntu NetworkManager[1396]: <info> (eth0): carrier now ON (device state 2)
Jun  3 09:55:15 ubuntu NetworkManager[1396]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Jun  3 09:55:16 ubuntu NetworkManager[1396]: <info> Activation (eth0) starting connection 'Auto eth0'
Jun  3 09:55:16 ubuntu NetworkManager[1396]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Jun  3 09:55:16 ubuntu NetworkManager[1396]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 09:55:16 ubuntu NetworkManager[1396]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun  3 09:55:16 ubuntu NetworkManager[1396]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 09:55:16 ubuntu NetworkManager[1396]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun  3 09:55:16 ubuntu NetworkManager[1396]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun  3 09:55:16 ubuntu NetworkManager[1396]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Jun  3 09:55:16 ubuntu NetworkManager[1396]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun  3 09:55:16 ubuntu NetworkManager[1396]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  3 09:55:16 ubuntu NetworkManager[1396]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun  3 09:55:16 ubuntu NetworkManager[1396]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun  3 09:55:16 ubuntu NetworkManager[1396]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jun  3 09:55:16 ubuntu NetworkManager[1396]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun  3 09:55:16 ubuntu kernel: [  155.185202] tg3 0000:05:00.0: eth0: Link is up at 100 Mbps, full duplex
Jun  3 09:55:16 ubuntu kernel: [  155.185207] tg3 0000:05:00.0: eth0: Flow control is on for TX and on for RX
Jun  3 09:55:16 ubuntu kernel: [  155.185440] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun  3 09:55:17 ubuntu NetworkManager[1396]: <info> dhclient started with pid 2080
Jun  3 09:55:17 ubuntu NetworkManager[1396]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun  3 09:55:17 ubuntu avahi-daemon[1326]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::230:5ff:fece:60ae.
Jun  3 09:55:17 ubuntu avahi-daemon[1326]: New relevant interface eth0.IPv6 for mDNS.
Jun  3 09:55:17 ubuntu avahi-daemon[1326]: Registering new address record for fe80::230:5ff:fece:60ae on eth0.*.
Jun  3 09:55:20 ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Jun  3 09:55:20 ubuntu dhclient: Copyright 2004-2010 Internet Systems Consortium.
Jun  3 09:55:20 ubuntu dhclient: All rights reserved.
Jun  3 09:55:20 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun  3 09:55:20 ubuntu dhclient: 
Jun  3 09:55:20 ubuntu acpid: client connected from 1675[0:0]
Jun  3 09:55:20 ubuntu acpid: 1 client rule loaded
Jun  3 09:55:21 ubuntu NetworkManager[1396]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun  3 09:55:21 ubuntu dhclient: Listening on LPF/eth0/00:30:05:ce:60:ae
Jun  3 09:55:21 ubuntu dhclient: Sending on   LPF/eth0/00:30:05:ce:60:ae
Jun  3 09:55:21 ubuntu dhclient: Sending on   Socket/fallback
Jun  3 09:55:21 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jun  3 09:55:21 ubuntu dhclient: DHCPOFFER of 192.168.0.8 from 192.168.0.1
Jun  3 09:55:21 ubuntu dhclient: DHCPREQUEST of 192.168.0.8 on eth0 to 255.255.255.255 port 67
Jun  3 09:55:22 ubuntu dhclient: DHCPACK of 192.168.0.8 from 192.168.0.1
Jun  3 09:55:22 ubuntu dhclient: bound to 192.168.0.8 -- renewal in 1406 seconds.
Jun  3 09:55:22 ubuntu NetworkManager[1396]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jun  3 09:55:22 ubuntu NetworkManager[1396]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun  3 09:55:22 ubuntu NetworkManager[1396]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jun  3 09:55:22 ubuntu NetworkManager[1396]: <info>   address 192.168.0.8
Jun  3 09:55:22 ubuntu NetworkManager[1396]: <info>   prefix 24 (255.255.255.0)
Jun  3 09:55:22 ubuntu NetworkManager[1396]: <info>   gateway 192.168.0.1
Jun  3 09:55:22 ubuntu NetworkManager[1396]: <info>   nameserver '194.168.4.100'
Jun  3 09:55:22 ubuntu NetworkManager[1396]: <info>   nameserver '194.168.8.100'
Jun  3 09:55:22 ubuntu NetworkManager[1396]: <info> Scheduling stage 5
Jun  3 09:55:22 ubuntu NetworkManager[1396]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun  3 09:55:22 ubuntu NetworkManager[1396]: <info> Done scheduling stage 5
Jun  3 09:55:22 ubuntu NetworkManager[1396]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun  3 09:55:22 ubuntu NetworkManager[1396]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jun  3 09:55:22 ubuntu avahi-daemon[1326]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.8.
Jun  3 09:55:22 ubuntu avahi-daemon[1326]: New relevant interface eth0.IPv4 for mDNS.
Jun  3 09:55:22 ubuntu avahi-daemon[1326]: Registering new address record for 192.168.0.8 on eth0.IPv4.
Jun  3 09:55:23 ubuntu NetworkManager[1396]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Jun  3 09:55:23 ubuntu NetworkManager[1396]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jun  3 09:55:23 ubuntu NetworkManager[1396]: <info> Activation (eth0) successful, device activated.
Jun  3 09:55:23 ubuntu NetworkManager[1396]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jun  3 09:55:24 ubuntu kernel: [  163.322192] lp0: using parport0 (interrupt-driven).
Jun  3 09:55:26 ubuntu kernel: [  165.770035] eth0: no IPv6 routers present
Jun  3 09:55:30 ubuntu udev-configure-printer: add /devices/pnp0/00:0c/printer/lp0
Jun  3 09:55:30 ubuntu udev-configure-printer: Failed to get parent
Jun  3 09:55:30 ubuntu udev-configure-printer: add /module/lp
Jun  3 09:55:30 ubuntu udev-configure-printer: Failed to get parent
Jun  3 09:55:41 ubuntu gdm-session-worker[2354]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jun  3 09:55:48 ubuntu ntpdate[2282]: adjust time server 91.189.94.4 offset -0.051245 sec
Jun  3 09:56:17 ubuntu rtkit-daemon[3095]: Successfully called chroot.
Jun  3 09:56:17 ubuntu rtkit-daemon[3095]: Successfully dropped privileges.
Jun  3 09:56:17 ubuntu rtkit-daemon[3095]: Successfully limited resources.
Jun  3 09:56:17 ubuntu rtkit-daemon[3095]: Running.
Jun  3 09:56:17 ubuntu rtkit-daemon[3095]: Watchdog thread running.
Jun  3 09:56:17 ubuntu rtkit-daemon[3095]: Canary thread running.
Jun  3 09:56:18 ubuntu rtkit-daemon[3095]: Successfully made thread 3093 of process 3093 (n/a) owned by '999' high priority at nice level -11.
Jun  3 09:56:18 ubuntu rtkit-daemon[3095]: Supervising 1 threads of 1 processes of 1 users.
Jun  3 09:56:27 ubuntu rtkit-daemon[3095]: Successfully made thread 3147 of process 3093 (n/a) owned by '999' RT at priority 5.
Jun  3 09:56:27 ubuntu rtkit-daemon[3095]: Supervising 2 threads of 1 processes of 1 users.
Jun  3 09:56:27 ubuntu rtkit-daemon[3095]: Successfully made thread 3152 of process 3093 (n/a) owned by '999' RT at priority 5.
Jun  3 09:56:27 ubuntu rtkit-daemon[3095]: Supervising 3 threads of 1 processes of 1 users.
Jun  3 09:57:23 ubuntu kernel: [  282.556799] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)

```

---

### Post by Toz on 2011-06-03
> Jun  3 09:54:59 ubuntu gdm-binary[1336]: WARNING: Unable to find users: no seat-id found

Can you post back the contents of:```
/var/log/gdm/:0-greeter.log	
```and
```
~/.xsession-errors
~/.xsession-errors.old
```

Also, boot the server again, Ctrl-Alt-F1 to get to console, login, then issue ```
/etc/init.d/gdm restart
```and try again. If still no luck, Ctrl-Alt-F1 and post back any error messages that might exist.

[https://bugs.launchpad.net/ubuntu/+source/gnupg2/+bug/766574]("https://bugs.launchpad.net/ubuntu/+source/gnupg2/+bug/766574")

---

### Post by ToshNeox on 2011-06-03
Okay well at the moment I'm re-installing it. Keeping software and user files. If that doesn't work, I will do what you said and post the contents of the files and use certain commands. :D

---

### Post by ToshNeox on 2011-06-03
It seems to be working fine now. I think there's a glitch with the 'Log me in automatically' thing. That's when I had this problem, I made the system log me in automatically.

---

