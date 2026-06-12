---
title: "Pause of about 30 seconds during boot"
date: 2010-05-03
forum: General Help
---

### Post by G_u_s on 2010-05-03
Hi all,

I'm using a MacBook 2.1 with Lucid.

After i hit Enter in GRUB, there is a message on top of the screen saying "booting up", and it stays there for 20 to 30 seconds. Then everything proceeds normally. I think i caught a message saying that something couldn't be found, but it flashed too rapidly.

Here is an extract of my dmesg. I'm assuming the part between [] is timestamps, and it takes about 40 seconds to go from GRUB to the Login screen, so it fits. Nothing is happening during 32 seconds.

```
[    2.690053] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    2.894315] usb 5-1: configuration #1 chosen from 1 choice
[   35.053835] udev: starting version 151
[   35.059728] Adding 1999992k swap on /dev/sda3.  Priority:-1 extents:1 across:1999992k
```

Also, it seems udev is already being loaded just before that:
```
[    0.874184] udev: starting version 151
```

Any idea? Thank you!

---

### Post by dino99 on 2010-05-03
maybe there is some more info into .xsession-errors or logs too

into /etc/default/grub there is a timer of 10s, can reduce it a little

sudo dpkg --configure -a

---

### Post by G_u_s on 2010-05-03
> **dino99 said:**
> maybe there is some more info into .xsession-errors or logs too

into /etc/default/grub there is a timer of 10s, can reduce it a little

sudo dpkg --configure -a

Hi dino99, thank you for helping!

.xsession-errors indeed displays a few errors, even though I'm not sure whether they are from before or after the update. Pretty sure they're not relevant to the current issue, but it can't hurt to fix them.

It's got a few such errors:
```
gnome-session[1272]: WARNING: Could not launch application '1099ea67a43f635db412599182336898000000023640027.desktop':
```
It seems gnome-session uses an old config file. So i went looking for it, and it seems it was a saved session. I've tried cleaning it up, I'll see how it goes next reboot.

Still nothing on the bigger, badder problem ;)

---

### Post by G_u_s on 2010-05-05
Help anyone? =(

---

### Post by duncanmc on 2010-05-07
I get the same problem. Any solutions?

---

### Post by duncanmc on 2010-05-07
This is the dmesg output

```


kernel: imklog 4.2.0, log source = /proc/kmsg started. 
rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="815" x-info="http://www.rsyslog.com"] (re)start 
rsyslogd: rsyslogd's groupid changed to 102 
rsyslogd: rsyslogd's userid changed to 101 
kernel: [ 0.000000] Initializing cgroup subsys cpuset 
kernel: [ 0.000000] Initializing cgroup subsys cpu 
kernel: [ 0.000000] Linux version 2.6.32-22-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2) 
kernel: [ 0.000000] Command line: root=UUID=122093b1-b281-42b8-9a35-6b70bad47b2c ro quiet splash 
kernel: [ 0.000000] KERNEL supported cpus: 
kernel: [ 0.000000] Intel GenuineIntel 
kernel: [ 0.000000] AMD AuthenticAMD 
kernel: [ 0.000000] Centaur CentaurHauls 
kernel: [ 0.000000] BIOS-provided physical RAM map: 
kernel: [ 0.000000] BIOS-e820: 0 0 000000000009fc00 (usable) 
kernel: [ 0.000000] BIOS-e820: 000000000009fc00 0 00000000000a0000 (reserved) 
kernel: [ 0.000000] BIOS-e820: 00000000000e0000 0 100000 (reserved) 
kernel: [ 0.000000] BIOS-e820: 100000 0 000000007faa0000 (usable) 
kernel: [ 0.000000] BIOS-e820: 000000007faa0000 0 000000007fb74000 (ACPI NVS) 
kernel: [ 0.000000] BIOS-e820: 000000007fb74000 0 000000007fc00000 (ACPI data) 
kernel: [ 0.000000] BIOS-e820: 000000007fc00000 0 80000000 (reserved) 
kernel: [ 0.000000] BIOS-e820: 00000000ffe00000 0 100000000 (reserved) 
kernel: [ 0.000000] BIOS-e820: 100000000 0 480000000 (usable) 
kernel: [ 0.000000] DMI 2.4 present. 
kernel: [ 0.000000] last_pfn = 0x480000 max_arch_pfn = 0x400000000 
kernel: [ 0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106 
kernel: [ 0.000000] ------------[ cut here ]------------ 
kernel: [ 0.000000] WARNING: at /build/buildd/linux-2.6.32/arch/x86/kernel/cpu/mtrr/generic.c:467 generic_get_mtrr+0x11e/0x140() 
kernel: [ 0.000000] Hardware name: MacPro2,1 
kernel: [ 0.000000] mtrr: your BIOS has set up an incorrect mask, fixing it up. 
kernel: [ 0.000000] Modules linked in: 
kernel: [ 0.000000] Pid: 0, comm: swapper Not tainted 2.6.32-22-generic #33-Ubuntu 
kernel: [ 0.000000] Call Trace: 
kernel: [ 0.000000] [<ffffffff81066d0b>] warn_slowpath_common+0x7b/0xc0 
kernel: [ 0.000000] [<ffffffff81066db1>] warn_slowpath_fmt+0x41/0x50 
kernel: [ 0.000000] [<ffffffff81028ebe>] generic_get_mtrr+0x11e/0x140 
kernel: [ 0.000000] [<ffffffff8185310f>] mtrr_trim_uncached_memory+0x91/0x309 
kernel: [ 0.000000] [<ffffffff818520c6>] ? mtrr_bp_init+0x1ab/0x1d2 
kernel: [ 0.000000] [<ffffffff8184e848>] setup_arch+0x3d6/0x6eb 
kernel: [ 0.000000] [<ffffffff8153e110>] ? printk+0x41/0x49 
kernel: [ 0.000000] [<ffffffff81849b2e>] start_kernel+0xca/0x371 
kernel: [ 0.000000] [<ffffffff8184933a>] x86_64_start_reservations+0x125/0x129 
kernel: [ 0.000000] [<ffffffff81849438>] x86_64_start_kernel+0xfa/0x109 
kernel: [ 0.000000] ---[ end trace a7919e7f17c0a725 ]--- 
kernel: [ 0.000000] last_pfn = 0x7faa0 max_arch_pfn = 0x400000000 
kernel: [ 0.000000] Scanning 1 areas for low memory corruption 
kernel: [ 0.000000] modified physical RAM map: 
kernel: [ 0.000000] modified: 0 0 1000 (usable) 
kernel: [ 0.000000] modified: 1000 0 6000 (reserved) 
kernel: [ 0.000000] modified: 6000 0 000000000009fc00 (usable) 
kernel: [ 0.000000] modified: 000000000009fc00 0 00000000000a0000 (reserved) 
kernel: [ 0.000000] modified: 00000000000e0000 0 100000 (reserved) 
kernel: [ 0.000000] modified: 100000 0 000000007faa0000 (usable) 
kernel: [ 0.000000] modified: 000000007faa0000 0 000000007fb74000 (ACPI NVS) 
kernel: [ 0.000000] modified: 000000007fb74000 0 000000007fc00000 (ACPI data) 
kernel: [ 0.000000] modified: 000000007fc00000 0 80000000 (reserved) 
kernel: [ 0.000000] modified: 00000000ffe00000 0 100000000 (reserved) 
kernel: [ 0.000000] modified: 100000000 0 480000000 (usable) 
kernel: [ 0.000000] init_memory_mapping: 0000000000000000-000000007faa0000 
kernel: [ 0.000000] NX (Execute Disable) protection: active 
kernel: [ 0.000000] init_memory_mapping: 0000000100000000-0000000480000000 
kernel: [ 0.000000] NX (Execute Disable) protection: active 
kernel: [ 0.000000] RAMDISK: 377ff000 0 37fef653 
kernel: [ 0.000000] ACPI: RSDP 00000000000fe020 24 (v02 APPLE ) 
kernel: [ 0.000000] ACPI: XSDT 000000007fbb31c0 000EC (v01 APPLE Apple00 0000007F 01000013) 
kernel: [ 0.000000] ACPI: ECDT 000000007fbb1000 53 (v01 APPLE Apple00 1 Loki 0000005F) 
kernel: [ 0.000000] ACPI: FACP 000000007fbaf000 000F4 (v04 APPLE Apple00 0000007F Loki 0000005F) 
kernel: [ 0.000000] ACPI: DSDT 000000007fba6000 0480E (v01 APPLE Apple00 20001 Loki 0000005F) 
kernel: [ 0.000000] ACPI: FACS 000000007faa3000 40 
kernel: [ 0.000000] ACPI: HPET 000000007fbae000 38 (v01 APPLE Apple00 1 Loki 0000005F) 
kernel: [ 0.000000] ACPI: APIC 000000007fbac000 000BC (v02 APPLE Apple00 0 Loki 0000005F) 
kernel: [ 0.000000] ACPI: MCFG 000000007fbab000 0003C (v01 APPLE Apple00 1 Loki 0000005F) 
kernel: [ 0.000000] ACPI: SSDT 000000007fba5000 0008E (v01 PmRef Cpu0Cst 3001 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fba4000 30 (v01 PmRef Cpu0Ist 3000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fba3000 47 (v01 PmRef Cpu1Cst 3000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fba2000 30 (v01 PmRef Cpu1Ist 3000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fba1000 47 (v01 PmRef Cpu2Cst 3000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fba0000 30 (v01 PmRef Cpu2Ist 3000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fb9f000 47 (v01 PmRef Cpu3Cst 3000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fb9e000 30 (v01 PmRef Cpu3Ist 3000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fb9d000 47 (v01 PmRef Cpu4Cst 3000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fb9c000 30 (v01 PmRef Cpu4Ist 3000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fb9b000 47 (v01 PmRef Cpu5Cst 3000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fb9a000 30 (v01 PmRef Cpu5Ist 3000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fb99000 47 (v01 PmRef Cpu6Cst 3000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fb98000 30 (v01 PmRef Cpu6Ist 3000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fb97000 47 (v01 PmRef Cpu7Cst 3000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fb96000 30 (v01 PmRef Cpu7Ist 3000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fb95000 00CEC (v01 PmRef CpuPm 3000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fb8f000 0057B (v01 PCIRef Pci16118 1000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fb94000 892 (v01 SataRe SataPri 1000 INTL 20050309) 
kernel: [ 0.000000] ACPI: SSDT 000000007fb93000 005F4 (v01 SataRe SataSec 1000 INTL 20050309) 
kernel: [ 0.000000] No NUMA configuration found 
kernel: [ 0.000000] Faking a node at 0000000000000000-0000000480000000 
kernel: [ 0.000000] Bootmem setup node 0 0000000000000000-0000000480000000 
kernel: [ 0.000000] NODE_DATA [0000000000018000 0 000000000001cfff] 
kernel: [ 0.000000] bootmap [0000000000100000 0 000000000018ffff] pages 90 
kernel: [ 0.000000] (8 early reservations) Err:510 bootmem [0000000000 0 0480000000] 
kernel: [ 0.000000] #0 [0000000000 0 0000001000] BIOS data page Err:510 [0000000000 0 0000001000] 
kernel: [ 0.000000] #1 [0000006000 0 0000008000] TRAMPOLINE Err:510 [0000006000 0 0000008000] 
kernel: [ 0.000000] #2 [0001000000 0 0001a29e64] TEXT DATA BSS Err:510 [0001000000 0 0001a29e64] 
kernel: [ 0.000000] #3 [00377ff000 0 0037fef653] RAMDISK Err:510 [00377ff000 0 0037fef653] 
kernel: [ 0.000000] #4 [000009fc00 0 0000100000] BIOS reserved Err:510 [000009fc00 0 0000100000] 
kernel: [ 0.000000] #5 [0001a2a000 0 0001a2a211] BRK Err:510 [0001a2a000 0 0001a2a211] 
kernel: [ 0.000000] #6 [0000008000 0 000000a000] PGTABLE Err:510 [0000008000 0 000000a000] 
kernel: [ 0.000000] #7 [000000a000 0 0000018000] PGTABLE Err:510 [000000a000 0 0000018000] 
kernel: [ 0.000000] found SMP MP-table at [ffff8800000fec60] fec60 
kernel: [ 0.000000] Zone PFN ranges: 
kernel: [ 0.000000] DMA 0x00000000 -> 0x00001000 
kernel: [ 0.000000] DMA32 0x00001000 -> 0x00100000 
kernel: [ 0.000000] Normal 0x00100000 -> 0x00480000 
kernel: [ 0.000000] Movable zone start PFN for each node 
kernel: [ 0.000000] early_node_map[4] active PFN ranges 
kernel: [ 0.000000] 0: 0x00000000 -> 0x00000001 
kernel: [ 0.000000] 0: 0x00000006 -> 0x0000009f 
kernel: [ 0.000000] 0: 0x00000100 -> 0x0007faa0 
kernel: [ 0.000000] 0: 0x00100000 -> 0x00480000 
kernel: [ 0.000000] ACPI: PM-Timer IO Port: 0x408 
kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled) 
kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled) 
kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x03] enabled) 
kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled) 
kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] enabled) 
kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] enabled) 
kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] enabled) 
kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] enabled) 
kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high level lint[0x1]) 
kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high level lint[0x1]) 
kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high level lint[0x1]) 
kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high level lint[0x1]) 
kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high level lint[0x1]) 
kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high level lint[0x1]) 
kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high level lint[0x1]) 
kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high level lint[0x1]) 
kernel: [ 0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0]) 
kernel: [ 0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23 
kernel: [ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
kernel: [ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
kernel: [ 0.000000] Using ACPI (MADT) for SMP configuration information 
kernel: [ 0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000 
kernel: [ 0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs 
kernel: [ 0.000000] PM: Registered nosave memory: 1000 0 6000 
kernel: [ 0.000000] PM: Registered nosave memory: 000000000009f000 0 00000000000a0000 
kernel: [ 0.000000] PM: Registered nosave memory: 00000000000a0000 0 00000000000e0000 
kernel: [ 0.000000] PM: Registered nosave memory: 00000000000e0000 0 100000 
kernel: [ 0.000000] PM: Registered nosave memory: 000000007faa0000 0 000000007fb74000 
kernel: [ 0.000000] PM: Registered nosave memory: 000000007fb74000 0 000000007fc00000 
kernel: [ 0.000000] PM: Registered nosave memory: 000000007fc00000 0 80000000 
kernel: [ 0.000000] PM: Registered nosave memory: 80000000 0 00000000ffe00000 
kernel: [ 0.000000] PM: Registered nosave memory: 00000000ffe00000 0 100000000 
kernel: [ 0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7fe00000) 
kernel: [ 0.000000] Booting paravirtualized kernel on bare hardware 
kernel: [ 0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1 
kernel: [ 0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u262144 
kernel: [ 0.000000] pcpu-alloc: s91544 r8192 d23144 u262144 alloc=1*2097152 
kernel: [ 0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
kernel: [ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 4128199 
kernel: [ 0.000000] Policy zone: Normal 
kernel: [ 0.000000] Kernel command line: root=UUID=122093b1-b281-42b8-9a35-6b70bad47b2c ro quiet splash 
kernel: [ 0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes) 
kernel: [ 0.000000] Initializing CPU#0 
kernel: [ 0.000000] Checking aperture... 
kernel: [ 0.000000] No AGP bridge found 
kernel: [ 0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB) 
kernel: [ 0.000000] Placing 64MB software IO TLB between ffff880020000000 0 ffff880024000000 
kernel: [ 0.000000] software IO TLB at phys 0x20000000 0 0x24000000 
kernel: [ 0.000000] Memory: 16456088k/18874368k available (5409k kernel code, 2103064k absent, 315216k reserved, 2976k data, 876k init) 
kernel: [ 0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1 
kernel: [ 0.000000] Hierarchical RCU implementation. 
kernel: [ 0.000000] NR_IRQS:4352 nr_irqs:472 
kernel: [ 0.000000] Extended CMOS year: 2000 
kernel: [ 0.000000] Console: colour VGA+ 80x25 
kernel: [ 0.000000] console [tty0] enabled 
kernel: [ 0.000000] allocated 167772160 bytes of page_cgroup 
kernel: [ 0.000000] please try cgroup_disable=memory' option if you don't want memory cgroups 
kernel: [ 0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer 
kernel: [ 0.000000] Fast TSC calibration using PIT 
kernel: [ 0.000000] Detected 2992.089 MHz processor. 
kernel: [ 0.010006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5984.17 BogoMIPS (lpj=29920890) 
kernel: [ 0.010032] Security Framework initialized 
kernel: [ 0.010051] AppArmor: AppArmor initialized 
kernel: [ 0.011184] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes) 
kernel: [ 0.019224] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes) 
kernel: [ 0.023123] Mount-cache hash table entries: 256 
kernel: [ 0.023279] Initializing cgroup subsys ns 
kernel: [ 0.023283] Initializing cgroup subsys cpuacct 
kernel: [ 0.023286] Initializing cgroup subsys memory 
kernel: [ 0.023293] Initializing cgroup subsys devices 
kernel: [ 0.023295] Initializing cgroup subsys freezer 
kernel: [ 0.023297] Initializing cgroup subsys net_cls 
kernel: [ 0.023318] CPU: L1 I cache: 32K, L1 D cache: 32K 
kernel: [ 0.023319] CPU: L2 cache: 4096K 
kernel: [ 0.023322] CPU 0/0x0 -> Node 0 
kernel: [ 0.023324] CPU: Physical Processor ID: 0 
kernel: [ 0.023325] CPU: Processor Core ID: 0 
kernel: [ 0.023327] mce: CPU supports 6 MCE banks 
kernel: [ 0.023334] CPU0: Thermal monitoring enabled (TM2) 
kernel: [ 0.023338] using mwait in idle threads. 
kernel: [ 0.023339] Performance Events: Core2 events, Intel PMU driver. 
kernel: [ 0.023344] ... version: 2 
kernel: [ 0.023345] ... bit width: 40 
kernel: [ 0.023346] ... generic registers: 2 
kernel: [ 0.023347] ... value mask: 000000ffffffffff 
kernel: [ 0.023348] ... max period: 000000007fffffff 
kernel: [ 0.023349] ... fixed-purpose events: 3 
kernel: [ 0.023350] ... event mask: 700000003 
kernel: [ 0.025763] ACPI: Core revision 20090903 
kernel: [ 0.038009] ftrace: converting mcount calls to 0f 1f 44 0 0 
kernel: [ 0.038013] ftrace: allocating 22518 entries in 89 pages 
kernel: [ 0.040062] Setting APIC routing to flat 
kernel: [ 0.040369] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1 
kernel: [ 0.145880] CPU0: Intel(R) Xeon(R) CPU X5365 @ 3.00GHz stepping 0b 
kernel: [ 0.150000] Booting processor 1 APIC 0x1 ip 0x6000 
kernel: [ 0.020000] Initializing CPU#1 
kernel: [ 0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K 
kernel: [ 0.020000] CPU: L2 cache: 4096K 
kernel: [ 0.020000] CPU 1/0x1 -> Node 0 
kernel: [ 0.020000] CPU: Physical Processor ID: 0 
kernel: [ 0.020000] CPU: Processor Core ID: 1 
kernel: [ 0.020000] CPU1: Thermal monitoring enabled (TM2) 
kernel: [ 0.300034] CPU1: Intel(R) Xeon(R) CPU X5365 @ 3.00GHz stepping 0b 
kernel: [ 0.300040] checking TSC synchronization [CPU#0 -> CPU#1]: passed. 
kernel: [ 0.310121] Booting processor 2 APIC 0x3 ip 0x6000 
kernel: [ 0.020000] Initializing CPU#2 
kernel: [ 0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K 
kernel: [ 0.020000] CPU: L2 cache: 4096K 
kernel: [ 0.020000] CPU 2/0x3 -> Node 0 
kernel: [ 0.020000] CPU: Physical Processor ID: 0 
kernel: [ 0.020000] CPU: Processor Core ID: 3 
kernel: [ 0.020000] CPU2: Thermal monitoring enabled (TM2) 
kernel: [ 0.470081] CPU2: Intel(R) Xeon(R) CPU X5365 @ 3.00GHz stepping 0b 
kernel: [ 0.470086] checking TSC synchronization [CPU#0 -> CPU#2]: passed. 
kernel: [ 0.480076] Booting processor 3 APIC 0x2 ip 0x6000 
kernel: [ 0.020000] Initializing CPU#3 
kernel: [ 0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K 
kernel: [ 0.020000] CPU: L2 cache: 4096K 
kernel: [ 0.020000] CPU 3/0x2 -> Node 0 
kernel: [ 0.020000] CPU: Physical Processor ID: 0 
kernel: [ 0.020000] CPU: Processor Core ID: 2 
kernel: [ 0.020000] CPU3: Thermal monitoring enabled (TM2) 
kernel: [ 0.640034] CPU3: Intel(R) Xeon(R) CPU X5365 @ 3.00GHz stepping 0b 
kernel: [ 0.640039] checking TSC synchronization [CPU#0 -> CPU#3]: passed. 
kernel: [ 0.650069] Booting processor 4 APIC 0x4 ip 0x6000 
kernel: [ 0.020000] Initializing CPU#4 
kernel: [ 0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K 
kernel: [ 0.020000] CPU: L2 cache: 4096K 
kernel: [ 0.020000] CPU 4/0x4 -> Node 0 
kernel: [ 0.020000] CPU: Physical Processor ID: 1 
kernel: [ 0.020000] CPU: Processor Core ID: 0 
kernel: [ 0.020000] CPU4: Thermal monitoring enabled (TM2) 
kernel: [ 0.810083] CPU4: Intel(R) Xeon(R) CPU X5365 @ 3.00GHz stepping 0b 
kernel: [ 0.810088] checking TSC synchronization [CPU#0 -> CPU#4]: passed. 
kernel: [ 0.820069] Booting processor 5 APIC 0x5 ip 0x6000 
kernel: [ 0.020000] Initializing CPU#5 
kernel: [ 0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K 
kernel: [ 0.020000] CPU: L2 cache: 4096K 
kernel: [ 0.020000] CPU 5/0x5 -> Node 0 
kernel: [ 0.020000] CPU: Physical Processor ID: 1 
kernel: [ 0.020000] CPU: Processor Core ID: 1 
kernel: [ 0.020000] CPU5: Thermal monitoring enabled (TM2) 
kernel: [ 0.980030] CPU5: Intel(R) Xeon(R) CPU X5365 @ 3.00GHz stepping 0b 
kernel: [ 0.980036] checking TSC synchronization [CPU#0 -> CPU#5]: passed. 
kernel: [ 0.990067] Booting processor 6 APIC 0x6 ip 0x6000 
kernel: [ 0.020000] Initializing CPU#6 
kernel: [ 0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K 
kernel: [ 0.020000] CPU: L2 cache: 4096K 
kernel: [ 0.020000] CPU 6/0x6 -> Node 0 
kernel: [ 0.020000] CPU: Physical Processor ID: 1 
kernel: [ 0.020000] CPU: Processor Core ID: 2 
kernel: [ 0.020000] CPU6: Thermal monitoring enabled (TM2) 
kernel: [ 1.150074] CPU6: Intel(R) Xeon(R) CPU X5365 @ 3.00GHz stepping 0b 
kernel: [ 1.150080] checking TSC synchronization [CPU#0 -> CPU#6]: passed. 
kernel: [ 1.160071] Booting processor 7 APIC 0x7 ip 0x6000 
kernel: [ 0.020000] Initializing CPU#7 
kernel: [ 0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K 
kernel: [ 0.020000] CPU: L2 cache: 4096K 
kernel: [ 0.020000] CPU 7/0x7 -> Node 0 
kernel: [ 0.020000] CPU: Physical Processor ID: 1 
kernel: [ 0.020000] CPU: Processor Core ID: 3 
kernel: [ 0.020000] CPU7: Thermal monitoring enabled (TM2) 
kernel: [ 1.320123] CPU7: Intel(R) Xeon(R) CPU X5365 @ 3.00GHz stepping 0b 
kernel: [ 1.320129] checking TSC synchronization [CPU#0 -> CPU#7]: passed. 
kernel: [ 1.330010] Brought up 8 CPUs 
kernel: [ 1.330012] Total of 8 processors activated (47879.67 BogoMIPS). 
kernel: [ 1.333705] devtmpfs: initialized 
kernel: [ 1.333705] regulator: core version 0.5 
kernel: [ 1.333705] Time: 21:27:21 Date: 05/07/10 
kernel: [ 1.333705] NET: Registered protocol family 16 
kernel: [ 1.333705] ACPI: bus type pci registered 
kernel: [ 1.333705] Trying to unpack rootfs image as initramfs... 
kernel: [ 1.333705] PCI: MCFG configuration 0: base d0000000 segment 0 buses 0 0 255 
kernel: [ 1.333705] PCI: Not using MMCONFIG. 
kernel: [ 1.333705] PCI: Using configuration type 1 for base access 
kernel: [ 1.333705] bio: create slab <bio-0> at 0 
kernel: [ 1.333705] ACPI: EC: EC description table is found, configuring boot EC 
kernel: [ 1.361401] ACPI: BIOS _OSI(Linux) query ignored 
kernel: [ 1.460590] ACPI: Interpreter enabled 
kernel: [ 1.460593] ACPI: (supports S0 S1 S3 S4 S5) 
kernel: [ 1.460611] ACPI: BIOS offers _GTS 
kernel: [ 1.460612] ACPI: If "acpi.gts=1" improves suspend, please notify linux-acpi@vger.kernel.org 
kernel: [ 1.460614] ACPI: Using IOAPIC for interrupt routing 
kernel: [ 1.460648] PCI: MCFG configuration 0: base d0000000 segment 0 buses 0 0 255 
kernel: [ 1.461016] PCI: MCFG area at d0000000 reserved in ACPI motherboard resources 
kernel: [ 1.465846] PCI: Using MMCONFIG at d0000000 0 dfffffff 
kernel: [ 1.465814] Freeing initrd memory: 8129k freed 
kernel: [ 1.468903] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62 
kernel: [ 1.469144] ACPI: No dock devices found. 
kernel: [ 1.469940] ACPI: PCI Root Bridge [PCI0] (0000:00) 
kernel: [ 1.470020] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold 
kernel: [ 1.470023] pci 0000:00:00.0: PME# disabled 
kernel: [ 1.470069] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold 
kernel: [ 1.470072] pci 0000:00:02.0: PME# disabled 
kernel: [ 1.470104] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold 
kernel: [ 1.470106] pci 0000:00:03.0: PME# disabled 
kernel: [ 1.470149] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold 
kernel: [ 1.470152] pci 0000:00:04.0: PME# disabled 
kernel: [ 1.470179] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold 
kernel: [ 1.470182] pci 0000:00:05.0: PME# disabled 
kernel: [ 1.470209] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold 
kernel: [ 1.470212] pci 0000:00:06.0: PME# disabled 
kernel: [ 1.470243] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold 
kernel: [ 1.470245] pci 0000:00:07.0: PME# disabled 
kernel: [ 1.470292] pci 0000:00:08.0: PME# supported from D0 D3hot D3cold 
kernel: [ 1.470294] pci 0000:00:08.0: PME# disabled 
kernel: [ 1.470544] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold 
kernel: [ 1.470547] pci 0000:00:1b.0: PME# disabled 
kernel: [ 1.470605] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold 
kernel: [ 1.470608] pci 0000:00:1c.0: PME# disabled 
kernel: [ 1.470666] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold 
kernel: [ 1.470669] pci 0000:00:1c.1: PME# disabled 
kernel: [ 1.470729] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold 
kernel: [ 1.470732] pci 0000:00:1c.2: PME# disabled 
kernel: [ 1.470790] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold 
kernel: [ 1.470793] pci 0000:00:1c.3: PME# disabled 
kernel: [ 1.471066] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold 
kernel: [ 1.471069] pci 0000:00:1d.7: PME# disabled 
kernel: [ 1.471293] pci 0000:00:1f.2: PME# supported from D3hot 
kernel: [ 1.471296] pci 0000:00:1f.2: PME# disabled 
kernel: [ 1.471405] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold 
kernel: [ 1.471408] pci 0000:01:00.0: PME# disabled 
kernel: [ 1.471510] pci 0000:01:00.3: PME# supported from D0 D3hot D3cold 
kernel: [ 1.471512] pci 0000:01:00.3: PME# disabled 
kernel: [ 1.471602] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold 
kernel: [ 1.471605] pci 0000:02:00.0: PME# disabled 
kernel: [ 1.471657] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold 
kernel: [ 1.471660] pci 0000:02:01.0: PME# disabled 
kernel: [ 1.471709] pci 0000:02:02.0: PME# supported from D0 D3hot D3cold 
kernel: [ 1.471712] pci 0000:02:02.0: PME# disabled 
kernel: [ 1.471907] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold 
kernel: [ 1.471910] pci 0000:05:00.0: PME# disabled 
kernel: [ 1.472005] pci 0000:05:00.1: PME# supported from D0 D3hot D3cold 
kernel: [ 1.472008] pci 0000:05:00.1: PME# disabled 
kernel: [ 1.472603] pci 0000:10:0b.0: PME# supported from D0 D1 D2 D3hot 
kernel: [ 1.472607] pci 0000:10:0b.0: PME# disabled 
kernel: [ 1.472636] pci 0000:00:1e.0: transparent bridge 
kernel: [ 1.478640] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 7 9 10 *11) 
kernel: [ 1.478726] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7 9 10 11) *3 
kernel: [ 1.478809] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 7 9 *10 11) 
kernel: [ 1.478893] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 *9 10 11) 
kernel: [ 1.478975] ACPI: PCI Interrupt Link [LNKE] (IRQs *5 7 9 10 11) 
kernel: [ 1.479058] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 7 9 10 *11) 
kernel: [ 1.479141] ACPI: PCI Interrupt Link [LNKG] (IRQs 5 7 9 10 11) *0, disabled. 
kernel: [ 1.479228] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 7 9 *10 11) 
kernel: [ 1.479326] vgaarb: device added: PCI:0000:08:00.0,decodes=io+mem,owns=io+mem,locks=none 
kernel: [ 1.479329] vgaarb: loaded 
kernel: [ 1.479414] SCSI subsystem initialized 
kernel: [ 1.479455] usbcore: registered new interface driver usbfs 
kernel: [ 1.479455] usbcore: registered new interface driver hub 
kernel: [ 1.479455] usbcore: registered new device driver usb 
kernel: [ 1.480003] ACPI: WMI: Mapper loaded 
kernel: [ 1.480005] PCI: Using ACPI for IRQ routing 
kernel: [ 1.480224] NetLabel: Initializing 
kernel: [ 1.480226] NetLabel: domain hash size = 128 
kernel: [ 1.480228] NetLabel: protocols = UNLABELED CIPSOv4 
kernel: [ 1.480253] NetLabel: unlabeled traffic allowed by default 
kernel: [ 1.480308] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0 
kernel: [ 1.480312] hpet0: 3 comparators, 64-bit 14.31818 MHz counter 
kernel: [ 1.530009] Switching to clocksource tsc 
kernel: [ 1.531796] AppArmor: AppArmor Filesystem Enabled 
kernel: [ 1.531820] pnp: PnP ACPI init 
kernel: [ 1.531840] ACPI: bus type pnp registered 
kernel: [ 1.533260] pnp: PnP ACPI: found 10 devices 
kernel: [ 1.533261] ACPI: ACPI bus type pnp unregistered 
kernel: [ 1.533272] system 00:01: iomem range 0xd0000000-0xdfffffff has been reserved 
kernel: [ 1.533275] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved 
kernel: [ 1.533277] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved 
kernel: [ 1.533279] system 00:01: iomem range 0xfec00000-0xfecfffff could not be reserved 
kernel: [ 1.533281] system 00:01: iomem range 0xfee00000-0xfeefffff has been reserved 
kernel: [ 1.533283] system 00:01: iomem range 0xfe700000-0xfe7003ff has been reserved 
kernel: [ 1.533285] system 00:01: iomem range 0xfe600000-0xfe6fffff has been reserved 
kernel: [ 1.533287] system 00:01: iomem range 0xfe000000-0xfe01ffff has been reserved 
kernel: [ 1.533294] system 00:08: ioport range 0x320-0x37f has been reserved 
kernel: [ 1.533296] system 00:08: ioport range 0x400-0x47f has been reserved 
kernel: [ 1.533297] system 00:08: ioport range 0x500-0x53f has been reserved 
kernel: [ 1.533299] system 00:08: ioport range 0x872-0x875 has been reserved 
kernel: [ 1.538051] pci 0000:02:01.0: BAR 14: can't allocate mem resource [0xf2d00000-0xf2cfffff] 
kernel: [ 1.538054] pci 0000:02:01.0: BAR 13: can't allocate I/O resource [0x3000-0x2fff] 
kernel: [ 1.538056] pci 0000:02:00.0: PCI bridge, secondary bus 0000:03 
kernel: [ 1.538058] pci 0000:02:00.0: IO window: disabled 
kernel: [ 1.538061] pci 0000:02:00.0: MEM window: disabled 
kernel: [ 1.538064] pci 0000:02:00.0: PREFETCH window: disabled 
kernel: [ 1.538068] pci 0000:02:01.0: PCI bridge, secondary bus 0000:04 
kernel: [ 1.538069] pci 0000:02:01.0: IO window: disabled 
kernel: [ 1.538073] pci 0000:02:01.0: MEM window: disabled 
kernel: [ 1.538076] pci 0000:02:01.0: PREFETCH window: 0x00000080000000-0x000000801fffff 
kernel: [ 1.538081] pci 0000:02:02.0: PCI bridge, secondary bus 0000:05 
kernel: [ 1.538083] pci 0000:02:02.0: IO window: 0x2000-0x2fff 
kernel: [ 1.538087] pci 0000:02:02.0: MEM window: 0xf2400000-0xf2cfffff 
kernel: [ 1.538090] pci 0000:02:02.0: PREFETCH window: disabled 
kernel: [ 1.538095] pci 0000:01:00.0: PCI bridge, secondary bus 0000:02 
kernel: [ 1.538097] pci 0000:01:00.0: IO window: 0x2000-0x2fff 
kernel: [ 1.538100] pci 0000:01:00.0: MEM window: 0xf2400000-0xf2cfffff 
kernel: [ 1.538103] pci 0000:01:00.0: PREFETCH window: 0x00000080000000-0x000000801fffff 
kernel: [ 1.538108] pci 0000:01:00.3: PCI bridge, secondary bus 0000:06 
kernel: [ 1.538109] pci 0000:01:00.3: IO window: disabled 
kernel: [ 1.538112] pci 0000:01:00.3: MEM window: disabled 
kernel: [ 1.538115] pci 0000:01:00.3: PREFETCH window: disabled 
kernel: [ 1.538119] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01 
kernel: [ 1.538121] pci 0000:00:02.0: IO window: 0x2000-0x2fff 
kernel: [ 1.538124] pci 0000:00:02.0: MEM window: 0xf2400000-0xf2dfffff 
kernel: [ 1.538126] pci 0000:00:02.0: PREFETCH window: 0x00000080000000-0x000000801fffff 
kernel: [ 1.538130] pci 0000:00:03.0: not setting up bridge for bus 0000:07 
kernel: [ 1.538131] pci 0000:00:04.0: PCI bridge, secondary bus 0000:08 
kernel: [ 1.538133] pci 0000:00:04.0: IO window: 0x1000-0x1fff 
kernel: [ 1.538136] pci 0000:00:04.0: MEM window: 0xf0000000-0xf20fffff 
kernel: [ 1.538139] pci 0000:00:04.0: PREFETCH window: 0x000000e0000000-0x000000efffffff 
kernel: [ 1.538142] pci 0000:00:05.0: not setting up bridge for bus 0000:09 
kernel: [ 1.538144] pci 0000:00:06.0: not setting up bridge for bus 0000:0a 
kernel: [ 1.538145] pci 0000:00:07.0: not setting up bridge for bus 0000:0b 
kernel: [ 1.538147] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0c 
kernel: [ 1.538149] pci 0000:00:1c.0: IO window: 0x4000-0x4fff 
kernel: [ 1.538153] pci 0000:00:1c.0: MEM window: 0x80200000-0x803fffff 
kernel: [ 1.538156] pci 0000:00:1c.0: PREFETCH window: 0x00000080400000-0x000000805fffff 
kernel: [ 1.538161] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0d 
kernel: [ 1.538163] pci 0000:00:1c.1: IO window: 0x5000-0x5fff 
kernel: [ 1.538166] pci 0000:00:1c.1: MEM window: 0x80600000-0x807fffff 
kernel: [ 1.538169] pci 0000:00:1c.1: PREFETCH window: 0x00000080800000-0x000000809fffff 
kernel: [ 1.538174] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:0e 
kernel: [ 1.538176] pci 0000:00:1c.2: IO window: 0x6000-0x6fff 
kernel: [ 1.538180] pci 0000:00:1c.2: MEM window: 0x80a00000-0x80bfffff 
kernel: [ 1.538183] pci 0000:00:1c.2: PREFETCH window: 0x00000080c00000-0x00000080dfffff 
kernel: [ 1.538188] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0f 
kernel: [ 1.538190] pci 0000:00:1c.3: IO window: 0x7000-0x7fff 
kernel: [ 1.538194] pci 0000:00:1c.3: MEM window: 0x80e00000-0x80ffffff 
kernel: [ 1.538197] pci 0000:00:1c.3: PREFETCH window: 0x00000081000000-0x000000811fffff 
kernel: [ 1.538201] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:10 
kernel: [ 1.538203] pci 0000:00:1e.0: IO window: disabled 
kernel: [ 1.538206] pci 0000:00:1e.0: MEM window: 0xf2e00000-0xf2efffff 
kernel: [ 1.538209] pci 0000:00:1e.0: PREFETCH window: disabled 
kernel: [ 1.538227] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
kernel: [ 1.538237] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
kernel: [ 1.538246] pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
kernel: [ 1.538258] pci 0000:02:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
kernel: [ 1.538270] pci 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
kernel: [ 1.538290] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
kernel: [ 1.538314] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
kernel: [ 1.538324] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16 
kernel: [ 1.538333] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18 
kernel: [ 1.538345] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19 
kernel: [ 1.538415] pci 0000:00:1e.0: power state changed by ACPI to D0 
kernel: [ 1.538501] NET: Registered protocol family 2 
kernel: [ 1.538843] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes) 
kernel: [ 1.540893] TCP established hash table entries: 524288 (order: 11, 8388608 bytes) 
kernel: [ 1.544822] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes) 
kernel: [ 1.545308] TCP: Hash tables configured (established 524288 bind 65536) 
kernel: [ 1.545310] TCP reno registered 
kernel: [ 1.545451] NET: Registered protocol family 1 
kernel: [ 1.545561] pci 0000:00:1f.0: rerouting interrupts for [8086:2670] 
kernel: [ 1.546068] Scanning for low memory corruption every 60 seconds 
kernel: [ 1.546194] audit: initializing netlink socket (disabled) 
kernel: [ 1.546204] type=2000 audit(1273267640.541:1): initialized 
kernel: [ 1.553847] HugeTLB registered 2 MB page size, pre-allocated 0 pages 
kernel: [ 1.555212] VFS: Disk quotas dquot_6.5.2 
kernel: [ 1.555278] Dquot-cache hash table entries: 512 (order 0, 4096 bytes) 
kernel: [ 1.555766] fuse init (API version 7.13) 
kernel: [ 1.555849] msgmni has been set to 32156 
kernel: [ 1.556386] alg: No test for stdrng (krng) 
kernel: [ 1.556438] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253) 
kernel: [ 1.556441] io scheduler noop registered 
kernel: [ 1.556443] io scheduler anticipatory registered 
kernel: [ 1.556444] io scheduler deadline registered 
kernel: [ 1.556470] io scheduler cfq registered (default) 
kernel: [ 1.557773] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
kernel: [ 1.557887] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
kernel: [ 1.557979] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0 
kernel: [ 1.557982] ACPI: Power Button [PWRB] 
kernel: [ 1.558015] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1 
kernel: [ 1.558017] ACPI: Power Button [PWRF] 
kernel: [ 1.558609] processor LNXCPU:00: registered as cooling_device0 
kernel: [ 1.559020] processor LNXCPU:01: registered as cooling_device1 
kernel: [ 1.559430] processor LNXCPU:02: registered as cooling_device2 
kernel: [ 1.559845] processor LNXCPU:03: registered as cooling_device3 
kernel: [ 1.560255] processor LNXCPU:04: registered as cooling_device4 
kernel: [ 1.560676] processor LNXCPU:05: registered as cooling_device5 
kernel: [ 1.561103] processor LNXCPU:06: registered as cooling_device6 
kernel: [ 1.561510] processor LNXCPU:07: registered as cooling_device7 
kernel: [ 1.562393] ACPI: SBS HC: EC = 0xffff88046e5e3a80, offset = 0x20, query_bit = 0x10 
kernel: [ 1.563459] Linux agpgart interface v0.103 
kernel: [ 1.563486] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled 
kernel: [ 1.564464] brd: module loaded 
kernel: [ 1.564809] loop: module loaded 
kernel: [ 1.564866] input: Macintosh mouse button emulation as /devices/virtual/input/input2 
kernel: [ 1.564951] ata_piix 0000:00:1f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
kernel: [ 1.565063] scsi0 : ata_piix 
kernel: [ 1.565151] scsi1 : ata_piix 
kernel: [ 1.565870] ata1: PATA max UDMA/100 cmd 0x30e8 ctl 0x30fc bmdma 0x30c0 irq 20 
kernel: [ 1.565872] ata2: PATA max UDMA/100 cmd 0x30e0 ctl 0x30f8 bmdma 0x30c8 irq 20 
kernel: [ 1.565899] ata_piix 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21 
kernel: [ 1.565903] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ] 
kernel: [ 1.566013] scsi2 : ata_piix 
kernel: [ 1.566096] scsi3 : ata_piix 
kernel: [ 1.566865] ata3: SATA max UDMA/133 cmd 0x30d8 ctl 0x30f4 bmdma 0x3020 irq 21 
kernel: [ 1.566867] ata4: SATA max UDMA/133 cmd 0x30d0 ctl 0x30f0 bmdma 0x3028 irq 21 
kernel: [ 1.567134] Fixed MDIO Bus: probed 
kernel: [ 1.567159] PPP generic driver version 2.4.2 
kernel: [ 1.567188] tun: Universal TUN/TAP device driver, 1.6 
kernel: [ 1.567189] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
kernel: [ 1.567242] ehci_hcd: USB 2 Enhanced' Host Controller (EHCI) Driver 
kernel: [ 1.567258] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
kernel: [ 1.567281] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
kernel: [ 1.567303] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1 
kernel: [ 1.567334] ehci_hcd 0000:00:1d.7: debug port 1 
kernel: [ 1.571235] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf2f04800 
kernel: [ 1.593780] ehci_hcd 0000:00:1d.7: USB 2 started, EHCI 1 
kernel: [ 1.593877] usb usb1: configuration #1 chosen from 1 choice 
kernel: [ 1.593914] hub 1-0:1.0: USB hub found 
kernel: [ 1.593922] hub 1-0:1.0: 8 ports detected 
kernel: [ 1.593984] ohci_hcd: USB 1.1 Open' Host Controller (OHCI) Driver 
kernel: [ 1.593995] uhci_hcd: USB Universal Host Controller Interface driver 
kernel: [ 1.594011] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
kernel: [ 1.594018] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
kernel: [ 1.594044] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2 
kernel: [ 1.594067] uhci_hcd 0000:00:1d.0: irq 19, io base 0x000030a0 
kernel: [ 1.594127] usb usb2: configuration #1 chosen from 1 choice 
kernel: [ 1.594146] hub 2-0:1.0: USB hub found 
kernel: [ 1.594151] hub 2-0:1.0: 2 ports detected 
kernel: [ 1.594182] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20 
kernel: [ 1.594189] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
kernel: [ 1.594217] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3 
kernel: [ 1.594236] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00003080 
kernel: [ 1.594299] usb usb3: configuration #1 chosen from 1 choice 
kernel: [ 1.594319] hub 3-0:1.0: USB hub found 
kernel: [ 1.594323] hub 3-0:1.0: 2 ports detected 
kernel: [ 1.594354] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21 
kernel: [ 1.594360] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
kernel: [ 1.594387] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4 
kernel: [ 1.594407] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00003060 
kernel: [ 1.594470] usb usb4: configuration #1 chosen from 1 choice 
kernel: [ 1.594487] hub 4-0:1.0: USB hub found 
kernel: [ 1.594491] hub 4-0:1.0: 2 ports detected 
kernel: [ 1.594529] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 22 (level, low) -> IRQ 22 
kernel: [ 1.594536] uhci_hcd 0000:00:1d.3: UHCI Host Controller 
kernel: [ 1.594559] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5 
kernel: [ 1.594583] uhci_hcd 0000:00:1d.3: irq 22, io base 0x00003040 
kernel: [ 1.594644] usb usb5: configuration #1 chosen from 1 choice 
kernel: [ 1.594661] hub 5-0:1.0: USB hub found 
kernel: [ 1.594665] hub 5-0:1.0: 2 ports detected 
kernel: [ 1.594732] PNP: No PS/2 controller found. Probing ports directly. 
kernel: [ 1.595634] mice: PS/2 mouse device common for all mice 
kernel: [ 1.595717] rtc_cmos 00:07: RTC can wake from S4 
kernel: [ 1.595742] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0 
kernel: [ 1.595764] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs 
kernel: [ 1.595846] device-mapper: uevent: version 1.0.3 
kernel: [ 1.595981] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com 
kernel: [ 1.596296] device-mapper: multipath: version 1.1.0 loaded 
kernel: [ 1.596299] device-mapper: multipath round-robin: version 1.0.0 loaded 
kernel: [ 1.596968] cpuidle: using governor ladder 
kernel: [ 1.596971] cpuidle: using governor menu 
kernel: [ 1.597227] TCP cubic registered 
kernel: [ 1.597313] NET: Registered protocol family 10 
kernel: [ 1.597682] lo: Disabled Privacy Extensions 
kernel: [ 1.597877] NET: Registered protocol family 17 
kernel: [ 1.597998] registered taskstats version 1 
kernel: [ 1.598466] Magic number: 10:672:499 
kernel: [ 1.598470] misc pktcdvd: hash matches 
kernel: [ 1.598543] rtc_cmos 00:07: setting system clock to 2010-05-07 21:27:21 UTC (1273267641) 
kernel: [ 1.598545] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
kernel: [ 1.598546] EDD information not available. 
kernel: [ 1.750332] ata1.00: ATAPI: OPTIARC DVD RW AD-7170A, 1.N8, max UDMA/66 
kernel: [ 1.767679] ata4.00: ATA-8: ST31500341AS, CC1G, max UDMA/133 
kernel: [ 1.767683] ata4.00: 2930277168 sectors, multi 0: LBA48 NCQ (depth 0/32) 
kernel: [ 1.781430] ata3.00: ATA-7: ST3500630AS P, 3.BTH, max UDMA/133 
kernel: [ 1.781433] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32) 
kernel: [ 1.790231] ata1.00: configured for UDMA/66 
kernel: [ 1.791495] scsi 0:0:0:0: CD-ROM OPTIARC DVD RW AD-7170A 1.N8 PQ: 0 ANSI: 5 
kernel: [ 1.805457] sr0: scsi3-mmc drive: 32x/32x writer dvd-ram cd/rw xa/form2 cdda tray 
kernel: [ 1.805461] Uniform CD-ROM driver Revision: 3.2 
kernel: [ 1.805697] sr 0:0:0:0: Attached scsi generic sg0 type 5 
kernel: [ 1.860119] ata4.00: configured for UDMA/133 
kernel: [ 1.873067] ata3.00: configured for UDMA/133 
kernel: [ 1.873146] scsi 2:0:0:0: Direct-Access ATA ST3500630AS P 3.BT PQ: 0 ANSI: 5 
kernel: [ 1.873336] sd 2:0:0:0: Attached scsi generic sg1 type 0 
kernel: [ 1.873351] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB) 
kernel: [ 1.873413] sd 2:0:0:0: [sda] Write Protect is off 
kernel: [ 1.873443] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
kernel: [ 1.873493] scsi 3:0:0:0: Direct-Access ATA ST31500341AS CC1G PQ: 0 ANSI: 5 
kernel: [ 1.873608] sda: 
kernel: [ 1.873630] sd 3:0:0:0: [sdb] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB) 
kernel: [ 1.873661] sd 3:0:0:0: Attached scsi generic sg2 type 0 
kernel: [ 1.873735] sd 3:0:0:0: [sdb] Write Protect is off 
kernel: [ 1.873755] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
kernel: [ 1.873880] sdb: sdb1 
kernel: [ 1.883789] sd 3:0:0:0: [sdb] Attached SCSI disk 
kernel: [ 1.934133] sda1 sda2 sda3 sda4 
kernel: [ 1.934374] sd 2:0:0:0: [sda] Attached SCSI disk 
kernel: [ 1.934405] Freeing unused kernel memory: 876k freed 
kernel: [ 1.934737] Write protecting the kernel read-only data: 7680k 
kernel: [ 1.950224] udev: starting version 151 
kernel: [ 1.967827] e1000e: Intel(R) PRO/1000 Network Driver 0 1.0.2-k2 
kernel: [ 1.967831] e1000e: Copyright (c) 1999-2008 Intel Corporation. 
kernel: [ 1.967910] e1000e 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
kernel: [ 1.985148] ohci1394 0000:10:0b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
kernel: [ 2.043617] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16] MMIO=[f2e04000-f2e047ff] Max Packet=[4096] IR/IT contexts=[4/8] 
kernel: [ 2.093063] 0000:05:00.0: eth0: (PCI Express:2.5GB/s:Width x4) 00:1d:4f:44:d6:78 
kernel: [ 2.093066] 0000:05:00.0: eth0: Intel(R) PRO/1000 Network Connection 
kernel: [ 2.093143] 0000:05:00.0: eth0: MAC: 5, PHY: 5, PBA No: 3070ff-0ff 
kernel: [ 2.093181] e1000e 0000:05:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
kernel: [ 2.201280] usb 2-1: new low speed USB device using uhci_hcd and address 2 
kernel: [ 2.223514] 0000:05:00.1: eth1: (PCI Express:2.5GB/s:Width x4) 00:1d:4f:44:d6:79 
kernel: [ 2.223516] 0000:05:00.1: eth1: Intel(R) PRO/1000 Network Connection 
kernel: [ 2.223593] 0000:05:00.1: eth1: MAC: 5, PHY: 5, PBA No: 3070ff-0ff 
kernel: [ 2.242118] EXT3-fs: INFO: recovery required on readonly filesystem. 
kernel: [ 2.242121] EXT3-fs: write access will be enabled during recovery. 
kernel: [ 2.420323] usb 2-1: configuration #1 chosen from 1 choice 
kernel: [ 2.462962] usbcore: registered new interface driver hiddev 
kernel: [ 2.494526] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3 
kernel: [ 2.494607] generic-usb 0003:413C:2105.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1/input0 
kernel: [ 2.494632] usbcore: registered new interface driver usbhid 
kernel: [ 2.494634] usbhid: v2.6:USB HID core driver 
kernel: [ 2.730044] usb 2-2: new low speed USB device using uhci_hcd and address 3 
kernel: [ 2.825838] kjournald starting. Commit interval 5 seconds 
kernel: [ 2.825848] EXT3-fs: recovery complete. 
kernel: [ 2.829817] EXT3-fs: mounted filesystem with ordered data mode. 
kernel: [ 2.911389] usb 2-2: configuration #1 chosen from 1 choice 
kernel: [ 2.930590] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4 
kernel: [ 2.930674] generic-usb 0003:046D:C01D.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2/input0 
kernel: [ 31.524332] udev: starting version 151 
kernel: [ 31.675164] type=1505 audit(1273235271.573:2): operation="profile_load" pid=523 name="/sbin/dhclient3" 
kernel: [ 31.675621] type=1505 audit(1273235271.573:3): operation="profile_load" pid=523 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
kernel: [ 31.675867] type=1505 audit(1273235271.573:4): operation="profile_load" pid=523 name="/usr/lib/connman/scripts/dhclient-script" 
kernel: [ 31.802914] ADDRCONF(NETDEV_UP): eth0: link is not ready 
kernel: [ 32.015976] EXT3 FS on sda3, internal journal 
kernel: [ 32.254558] type=1505 audit(1273235272.151:5): operation="profile_replace" pid=858 name="/sbin/dhclient3" 
kernel: [ 32.255026] type=1505 audit(1273235272.151:6): operation="profile_replace" pid=858 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
kernel: [ 32.255276] type=1505 audit(1273235272.151:7): operation="profile_replace" pid=858 name="/usr/lib/connman/scripts/dhclient-script" 
kernel: [ 32.259111] lp: driver loaded but no devices found 
kernel: [ 32.365419] ADDRCONF(NETDEV_UP): eth1: link is not ready 
kernel: [ 32.508972] applesmc: Apple MacPro2 detected: 
kernel: [ 32.508975] applesmc: 0 Model without accelerometer 
kernel: [ 32.508976] applesmc: 0 Model without light sensors and backlight 
kernel: [ 32.508978] applesmc: 0 Model with 35 temperature sensors 
kernel: [ 32.509040] applesmc: device successfully initialized. 
kernel: [ 32.509833] applesmc: 4 fans found. 
kernel: [ 32.509905] applesmc: driver successfully loaded. 
kernel: [ 32.635738] type=1505 audit(1273235272.535:8): operation="profile_load" pid=872 name="/usr/lib/cups/backend/cups-pdf" 
kernel: [ 32.636287] type=1505 audit(1273235272.535:9): operation="profile_load" pid=872 name="/usr/sbin/cupsd" 
kernel: [ 32.638149] type=1505 audit(1273235272.535:10): operation="profile_load" pid=873 name="/usr/sbin/mysqld-akonadi" 
kernel: [ 32.639523] type=1505 audit(1273235272.535:11): operation="profile_load" pid=874 name="/usr/sbin/tcpdump" 
kernel: [ 32.887850] intel_rng: FWH not detected 
kernel: [ 32.939869] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
kernel: [ 33.037725] vga16fb: mapped to 0xffff8800000a0000 
kernel: [ 33.037803] fb0: VGA16 VGA frame buffer device 
kernel: [ 33.826872] nvidia: module license NVIDIA' taints kernel. 
kernel: [ 33.826877] Disabling lock debugging due to kernel taint 
kernel: [ 34.105941] dca service started, version 1.12.1 
kernel: [ 34.137188] ioatdma: Intel(R) QuickData Technology Driver 4 
kernel: [ 34.137254] ioatdma 0000:00:08.0: can't derive routing for PCI INT A 
kernel: [ 34.137256] ioatdma 0000:00:08.0: PCI INT A: no GSI 
kernel: [ 34.293084] coretemp coretemp.0: Using relative temperature scale! 
kernel: [ 34.293142] coretemp coretemp.1: Using relative temperature scale! 
kernel: [ 34.293234] coretemp coretemp.2: Using relative temperature scale! 
kernel: [ 34.293270] coretemp coretemp.3: Using relative temperature scale! 
kernel: [ 34.293319] coretemp coretemp.4: Using relative temperature scale! 
kernel: [ 34.293367] coretemp coretemp.5: Using relative temperature scale! 
kernel: [ 34.293599] coretemp coretemp.6: Using relative temperature scale! 
kernel: [ 34.293682] coretemp coretemp.7: Using relative temperature scale! 
kernel: [ 34.348184] nvidia 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
kernel: [ 34.348196] vgaarb: device changed decodes: PCI:0000:08:00.0,olddecodes=io+mem,decodes=none:owns=io+mem 
kernel: [ 34.348395] NVRM: loading NVIDIA UNIX x86_64 Kernel Module 195.36.15 Fri Mar 12 00:29:13 PST 2010 
kernel: [ 34.433253] EDAC MC: Ver: 2.1.0 Apr 28 2010 
kernel: [ 34.445576] EDAC MC0: Giving out device to i5000_edac.c' I5000': DEV 0000:00:10.0 
kernel: [ 34.445595] EDAC PCI0: Giving out device to module i5000_edac' controller EDAC PCI controller': DEV 0000:00:10.0' (POLLED) 
kernel: [ 34.451163] Console: switching to colour frame buffer device 80x30 
kernel: [ 34.867975] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX 
kernel: [ 34.871746] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
kernel: [ 35.469280] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23 
kernel: [ 35.844255] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5 
dhcdbd: Started up. 
kernel: [ 38.920129] ppdev: user-space parallel port driver 
kernel: [ 46.294115] Adding 7999992k swap on /swapfile. Priority:-1 extents:2018 across:8161476k 
python: hp-systray[1996]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting. 
 

```

---

### Post by G_u_s on 2010-05-12
Anyone at all, please?

---

### Post by bville09 on 2010-05-12
Yeah, I get the same kinda thing before plymouth flashes up (except it's just a single blinking cursor against a black screen, no words, no status, kinda like the old black screens of death you'd get with Windows) - I think is just normal behavior, as it happens across all of my computers (except my powermac, which displays an "acpi length error" or something for a while, can't quite remember).

All up it takes roughly fourty seconds from post to login, with the plymouth screen appearing for like a split second in between that (after the blinking cursor, though).

It's as if the computer is loading files in the background, but just ignores them, or doesn't display any output for them. I don't know. Anyway, the dmesg output looks the same as mine (differences in i/o, though). It's interesting that I don't get the "booting up" message though.

Honestly though, most people don't experience the sub-ten second boot anyway (unless they've got a bleeding edge pc or a mid-range mac, or even a low-end sdd). If you ask me, i'd say the computer is doing what it's telling, it's just "booting up".

Sorry I can't be of anymore help.

edit: is that an extract of the dmesg output, or the entire thing?

---

### Post by G_u_s on 2010-05-12
Thank you for your answer!

It is only an extract of the dmesg, i could output the entire thing, but I was afraid it might contain personal info.

I'm also attaching my "bootchart", in case it helps to determine whether it's normal or problematic behaviour (click the image for full size):
[[img]http://i.imagehost.org/t/0606/Augustin-lucid-20100512-5.jpg[/img]](http://i.imagehost.org/view/0606/Augustin-lucid-20100512-5)

I'm not necessarily after a 10-second bootup; honestly, 10 or 30 is pretty much the same, but it really bothers me that it just stands there seemingly doing nothing. That and my display problems (see [http://ubuntuforums.org/showthread.php?t=1468647](http://ubuntuforums.org/showthread.php?t=1468647) and [http://ubuntuforums.org/showthread.php?t=1461210](http://ubuntuforums.org/showthread.php?t=1461210)) are the only things that really prevent me from fully enjoying this new distro =)

---

### Post by bville09 on 2010-05-12
> **G_u_s said:**
> Thank you for your answer!

It is only an extract of the dmesg, i could output the entire thing, but I was afraid it might contain personal info.

It's best not to post it, then. What you posted would be the only relevant part of it, anyway.

It is kind of a hassle that it just "sits there" but I think it is actually doing something, just not telling you (kinda like a text boot, but without the output - if that even makes sense), or loading files in the backgrounnd. I did get a similar (although unrelated) problem, that happened because the computer was waiting for the hard drive to spin up (but this was on a really ancient computer), this one could be related to hardware. I think, as long as it doesn't affect the actual operating system, or any of your files, it should be fine to leave as is.

I'll take a look at your other problems, and see what I can do about them.

edit: a quick glance at the bootchart, and I'd say that was right. it is loading these things, just not telling you. :) (unless I missed something important there)

---

### Post by duncanmc on 2010-05-12
I posted the full dmesg.
I am using a powerful mac pro with 8 cores. Previous version of ubuntu was booting much faster.

---

### Post by jocko on 2010-05-12
> **G_u_s said:**
> Thank you for your answer!

It is only an extract of the dmesg, i could output the entire thing, but I was afraid it might contain personal info.

I'm also attaching my "bootchart", in case it helps to determine whether it's normal or problematic behaviour (click the image for full size):
[[IMG]http://i.imagehost.org/t/0606/Augustin-lucid-20100512-5.jpg[/IMG]]("http://i.imagehost.org/view/0606/Augustin-lucid-20100512-5")

I'm not necessarily after a 10-second bootup; honestly, 10 or 30 is pretty much the same, but it really bothers me that it just stands there seemingly doing nothing. That and my display problems (see [http://ubuntuforums.org/showthread.php?t=1468647](http://ubuntuforums.org/showthread.php?t=1468647) and [http://ubuntuforums.org/showthread.php?t=1461210](http://ubuntuforums.org/showthread.php?t=1461210)) are the only things that really prevent me from fully enjoying this new distro =)
One thing that seems a little bit off in your bootchart is that ureadahead doesn't seem to do anything. If ureadahead doesn't do it's job, boot will be quite a bit slower. But I can see no 30s pause anywhere in the bootchart, so I think your dmesg just doesn't report everything.

---

### Post by duncanmc on 2010-05-13
Now I applied the latest ubuntu updates. Boot speed improved by 15 seconds!

---

### Post by G_u_s on 2010-05-20
> **jocko said:**
> One thing that seems a little bit off in your bootchart is that ureadahead doesn't seem to do anything. If ureadahead doesn't do it's job, boot will be quite a bit slower. But I can see no 30s pause anywhere in the bootchart, so I think your dmesg just doesn't report everything.

Thank you for your help, jocko. I'll try to check if ureadahead does its magic, just in case.

Many thanks (and sorry for taking so long to answer!) =)

(I'm not sure I should mark the thread as "SOLVED" though, at least not yet.)

---

