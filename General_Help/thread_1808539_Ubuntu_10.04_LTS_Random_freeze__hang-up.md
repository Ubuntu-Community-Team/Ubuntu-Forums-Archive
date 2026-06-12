---
title: "Ubuntu 10.04 LTS Random freeze / hang-up"
date: 2011-07-20
forum: General Help
---

### Post by Flayer1 on 2011-07-20
Hi

I apologize if the solution to my problem already exists, but I've been googling and searching for a solution for about 4 days now, and I've obviosly not found a solution yet.

My problem is that my server randomly hangs. If I remember right it started after an kernel update (can't really remember if it was a kernel update specific, but I did install new updates before this problem occurred), and then I noticed my server was down one day, after that the problems/random freezes continued. And there are no pattern/interval between the freeze ups.

I think that all this started for about 3 weeks ago, so I've never had this problem with Ubuntu 10.04 before. 

At first, I thought the source to my problem was an old IDE which I accidentally left in when installing Ubuntu at the first time, so GRUB was sitting on that one. So I backed up almost all of my data, reinstalled Ubuntu 10.04 (downloaded from the website) but this time without the old IDE drive. Everything seemed to work, had no crashes or freezes. I do have to mention that the same thing happend to the live CD before I removed the old IDE.

But now the fresh install of Ubuntu seems to hang too. And the worst part of this is that I can't really do anything about it to test or look up what may cause the problem, as I have to access it remotely because I'm on vacation right now (I'll have to get my friend over there and restart it).

When the computer hangs it comes inaccessible from the network, can't even see that it is up in my router. But I do know it is running, else it would have been shut off and then started up again and work.

Before I re-installed it, this problem could be reproduced by surfing the web and watching flash videos in either chromium or Firefox.

Oh, and I do know it sounds silly to run a server with the desktop edition installed, but if I don't have any other computer accessible, I use my server instead.

My server specs:

CPU: Intel Core 2 Quad 2.5 GHz
GFX: XFX Nvidia Geforce 8600GT
Mobo: EVGA 750i FTW
RAM: Corsair Dominator 2GB
HDD: Western Digital 500 GB

I also have no special effects nor do I use any proprietary drivers (I did before I re-installed).

Any ideas of what it might be? Is it a bug which came with the updates, like a bug in the kernel?

I've noticed that there actually are alot of threads like mine around here, but none have provided a working solution.

/ Regards Flayer

---

### Post by 2F4U on 2011-07-20
Did you look into the log files (located in /var/log) and see if there is something unusual. As far as I remember, 10.04 still has /var/log/messages, so this would be my personal starting point. The thing is that you should look into it or download it shortly after the machine hung and was restarted. First locate the time of the restart in the file and then look at the messages immediately before the restart.

---

### Post by Flayer1 on 2011-07-20
No, I haven't. But I also can't do it right now :/
As I said in the post, I'm on vacation right now and my friend, who are the only one with a key, just went away for a week. And I can't access my sevrer through SSH, as everything is frozen, even the network and everything is down (on the server, not my LAN).

I will come back at the end of the month with a reply, and hopefully get things resolved when I'm back home.

I do appreciate suggestions on solutions until I get back home tho.

I did just recently looked through another post, which has a link to this page: [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

Under "[B]Non-Symptoms":

[/B]"The caps lock key blinks - this indicates a kernel failure, not X " - This did occur about three times before the freezeups started with the old installation, random interval tho. Just remembered this now.


Thanks for your fast reply, really appreciate it.

---

### Post by no2498 on 2011-07-20
in/on a desk top after you get home 
i start mine in the old kernel like 4 down the list
thats why i dont get rid of them
you can also try its self fix

if i run a few days it usalee fixes its self

---

### Post by Flayer1 on 2011-07-28
I am at home now, sitting on my server. I looked through messages and messages.1, but there was nothing of importance, just some failed ssh logins and it was bloated. I cleaned it up (did a backup first) and hopefully it'll show me anything of importance if/when the server crashes.

So, I installed drivers for my nVidia card, rebooted and opened up VirtualBox, surfed to a heavy flash site and the computer froze.

This is the messages log from /var/log/messages :
```
Jul 28 19:25:30 flayer-server kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jul 28 19:25:30 flayer-server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="941" x-info="http://www.rsyslog.com"] (re)start
Jul 28 19:25:30 flayer-server rsyslogd: rsyslogd's groupid changed to 103
Jul 28 19:25:30 flayer-server rsyslogd: rsyslogd's userid changed to 101
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Linux version 2.6.32-33-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #70-Ubuntu SMP Thu Jul 7 21:13:52 UTC 2011 (Ubuntu 2.6.32-33.70-generic 2.6.32.41+drm33.18)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=8158fd1c-9e52-4dc5-95cb-6a2d7c2bda8c ro quiet splash
Jul 28 19:25:30 flayer-server kernel: [    0.000000] KERNEL supported cpus:
Jul 28 19:25:30 flayer-server kernel: [    0.000000]   Intel GenuineIntel
Jul 28 19:25:30 flayer-server kernel: [    0.000000]   AMD AuthenticAMD
Jul 28 19:25:30 flayer-server kernel: [    0.000000]   Centaur CentaurHauls
Jul 28 19:25:30 flayer-server kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] DMI 2.5 present.
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Jul 28 19:25:30 flayer-server kernel: [    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x400000000
Jul 28 19:25:30 flayer-server kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jul 28 19:25:30 flayer-server kernel: [    0.000000] modified physical RAM map:
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f400 (usable)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  modified: 0000000000100000 - 000000007fee0000 (usable)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  modified: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  modified: 000000007fef0000 - 000000007ff00000 (reserved)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 28 19:25:30 flayer-server kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000007fee0000
Jul 28 19:25:30 flayer-server kernel: [    0.000000] NX (Execute Disable) protection: active
Jul 28 19:25:30 flayer-server kernel: [    0.000000] RAMDISK: 377f5000 - 37fefec4
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: RSDP 00000000000f7d30 00014 (v00 EVGA  )
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: RSDT 000000007fee3000 00034 (v01 EVGA   NVDAACPI 42302E31 NVDA 00000000)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: FACP 000000007fee3080 00074 (v01 EVGA   NVDAACPI 42302E31 NVDA 00000000)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0000000000000000/1 (20090903/tbfadt-557)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: DSDT 000000007fee3100 05470 (v01 EVGA   NVDAACPI 00001000 MSFT 03000000)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: FACS 000000007fee0000 00040
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: HPET 000000007fee8640 00038 (v01 EVGA   NVDAACPI 42302E31 NVDA 00000098)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: MCFG 000000007fee8680 0003C (v01 EVGA   NVDAACPI 42302E31 NVDA 00000000)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: APIC 000000007fee8580 00098 (v01 EVGA   NVDAACPI 42302E31 NVDA 00000000)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] No NUMA configuration found
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Faking a node at 0000000000000000-000000007fee0000
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000007fee0000
Jul 28 19:25:30 flayer-server kernel: [    0.000000]   NODE_DATA [0000000000012000 - 0000000000016fff]
Jul 28 19:25:30 flayer-server kernel: [    0.000000]   bootmap [0000000000017000 -  0000000000026fdf] pages 10
Jul 28 19:25:30 flayer-server kernel: [    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007fee0000]
Jul 28 19:25:30 flayer-server kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jul 28 19:25:30 flayer-server kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Jul 28 19:25:30 flayer-server kernel: [    0.000000]   #2 [0001000000 - 0001a30a64]    TEXT DATA BSS ==> [0001000000 - 0001a30a64]
Jul 28 19:25:30 flayer-server kernel: [    0.000000]   #3 [00377f5000 - 0037fefec4]          RAMDISK ==> [00377f5000 - 0037fefec4]
Jul 28 19:25:30 flayer-server kernel: [    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Jul 28 19:25:30 flayer-server kernel: [    0.000000]   #5 [0001a31000 - 0001a310c7]              BRK ==> [0001a31000 - 0001a310c7]
Jul 28 19:25:30 flayer-server kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Jul 28 19:25:30 flayer-server kernel: [    0.000000] found SMP MP-table at [ffff8800000f3c90] f3c90
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Zone PFN ranges:
Jul 28 19:25:30 flayer-server kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jul 28 19:25:30 flayer-server kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jul 28 19:25:30 flayer-server kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Movable zone start PFN for each node
Jul 28 19:25:30 flayer-server kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul 28 19:25:30 flayer-server kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jul 28 19:25:30 flayer-server kernel: [    0.000000]     0: 0x00000100 -> 0x0007fee0
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x03] enabled)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jul 28 19:25:30 flayer-server kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 28 19:25:30 flayer-server kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Jul 28 19:25:30 flayer-server kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Jul 28 19:25:30 flayer-server kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 28 19:25:30 flayer-server kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jul 28 19:25:30 flayer-server kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:60100000)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 28 19:25:30 flayer-server kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Jul 28 19:25:30 flayer-server kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91864 r8192 d22824 u524288
Jul 28 19:25:30 flayer-server kernel: [    0.000000] pcpu-alloc: s91864 r8192 d22824 u524288 alloc=1*2097152
Jul 28 19:25:30 flayer-server kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 516620
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Policy zone: DMA32
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=8158fd1c-9e52-4dc5-95cb-6a2d7c2bda8c ro quiet splash
Jul 28 19:25:30 flayer-server kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Initializing CPU#0
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Checking aperture...
Jul 28 19:25:30 flayer-server kernel: [    0.000000] No AGP bridge found
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Memory: 2047620k/2096000k available (5412k kernel code, 452k absent, 47928k reserved, 2981k data, 888k init)
Jul 28 19:25:30 flayer-server kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Hierarchical RCU implementation.
Jul 28 19:25:30 flayer-server kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Console: colour VGA+ 80x25
Jul 28 19:25:30 flayer-server kernel: [    0.000000] console [tty0] enabled
Jul 28 19:25:30 flayer-server kernel: [    0.000000] allocated 20971520 bytes of page_cgroup
Jul 28 19:25:30 flayer-server kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Fast TSC calibration using PIT
Jul 28 19:25:30 flayer-server kernel: [    0.000000] Detected 2500.032 MHz processor.
Jul 28 19:25:30 flayer-server kernel: [    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 5000.06 BogoMIPS (lpj=25000320)
Jul 28 19:25:30 flayer-server kernel: [    0.010036] Security Framework initialized
Jul 28 19:25:30 flayer-server kernel: [    0.010061] AppArmor: AppArmor initialized
Jul 28 19:25:30 flayer-server kernel: [    0.010224] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jul 28 19:25:30 flayer-server kernel: [    0.011710] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 28 19:25:30 flayer-server kernel: [    0.012343] Mount-cache hash table entries: 256
Jul 28 19:25:30 flayer-server kernel: [    0.012498] Initializing cgroup subsys ns
Jul 28 19:25:30 flayer-server kernel: [    0.012504] Initializing cgroup subsys cpuacct
Jul 28 19:25:30 flayer-server kernel: [    0.012507] Initializing cgroup subsys memory
Jul 28 19:25:30 flayer-server kernel: [    0.012515] Initializing cgroup subsys devices
Jul 28 19:25:30 flayer-server kernel: [    0.012517] Initializing cgroup subsys freezer
Jul 28 19:25:30 flayer-server kernel: [    0.012519] Initializing cgroup subsys net_cls
Jul 28 19:25:30 flayer-server kernel: [    0.012541] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul 28 19:25:30 flayer-server kernel: [    0.012543] CPU: L2 cache: 3072K
Jul 28 19:25:30 flayer-server kernel: [    0.012546] CPU 0/0x0 -> Node 0
Jul 28 19:25:30 flayer-server kernel: [    0.012548] CPU: Physical Processor ID: 0
Jul 28 19:25:30 flayer-server kernel: [    0.012549] CPU: Processor Core ID: 0
Jul 28 19:25:30 flayer-server kernel: [    0.012552] mce: CPU supports 6 MCE banks
Jul 28 19:25:30 flayer-server kernel: [    0.012560] CPU0: Thermal monitoring enabled (TM1)
Jul 28 19:25:30 flayer-server kernel: [    0.012564] using mwait in idle threads.
Jul 28 19:25:30 flayer-server kernel: [    0.012566] Performance Events: Core2 events, Intel PMU driver.
Jul 28 19:25:30 flayer-server kernel: [    0.012572] ... version:                2
Jul 28 19:25:30 flayer-server kernel: [    0.012573] ... bit width:              40
Jul 28 19:25:30 flayer-server kernel: [    0.012574] ... generic registers:      2
Jul 28 19:25:30 flayer-server kernel: [    0.012575] ... value mask:             000000ffffffffff
Jul 28 19:25:30 flayer-server kernel: [    0.012577] ... max period:             000000007fffffff
Jul 28 19:25:30 flayer-server kernel: [    0.012578] ... fixed-purpose events:   3
Jul 28 19:25:30 flayer-server kernel: [    0.012579] ... event mask:             0000000700000003
Jul 28 19:25:30 flayer-server kernel: [    0.014941] ACPI: Core revision 20090903
Jul 28 19:25:30 flayer-server kernel: [    0.024443] ftrace: converting mcount calls to 0f 1f 44 00 00
Jul 28 19:25:30 flayer-server kernel: [    0.024450] ftrace: allocating 22478 entries in 89 pages
Jul 28 19:25:30 flayer-server kernel: [    0.030060] Setting APIC routing to flat
Jul 28 19:25:30 flayer-server kernel: [    0.030472] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 28 19:25:30 flayer-server kernel: [    0.133794] CPU0: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
Jul 28 19:25:30 flayer-server kernel: [    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
Jul 28 19:25:30 flayer-server kernel: [    0.020000] Initializing CPU#1
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU: L2 cache: 3072K
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU 1/0x1 -> Node 0
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU: Physical Processor ID: 0
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU: Processor Core ID: 1
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU1: Thermal monitoring enabled (TM1)
Jul 28 19:25:30 flayer-server kernel: [    0.290035] CPU1: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
Jul 28 19:25:30 flayer-server kernel: [    0.290041] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jul 28 19:25:30 flayer-server kernel: [    0.300118] Booting processor 2 APIC 0x3 ip 0x6000
Jul 28 19:25:30 flayer-server kernel: [    0.020000] Initializing CPU#2
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU: L2 cache: 3072K
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU 2/0x3 -> Node 0
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU: Physical Processor ID: 0
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU: Processor Core ID: 3
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU2: Thermal monitoring enabled (TM1)
Jul 28 19:25:30 flayer-server kernel: [    0.460056] CPU2: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
Jul 28 19:25:30 flayer-server kernel: [    0.460062] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Jul 28 19:25:30 flayer-server kernel: [    0.470070] Booting processor 3 APIC 0x2 ip 0x6000
Jul 28 19:25:30 flayer-server kernel: [    0.020000] Initializing CPU#3
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU: L2 cache: 3072K
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU 3/0x2 -> Node 0
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU: Physical Processor ID: 0
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU: Processor Core ID: 2
Jul 28 19:25:30 flayer-server kernel: [    0.020000] CPU3: Thermal monitoring enabled (TM1)
Jul 28 19:25:30 flayer-server kernel: [    0.630029] CPU3: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
Jul 28 19:25:30 flayer-server kernel: [    0.630036] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Jul 28 19:25:30 flayer-server kernel: [    0.640012] Brought up 4 CPUs
Jul 28 19:25:30 flayer-server kernel: [    0.640014] Total of 4 processors activated (20000.00 BogoMIPS).
Jul 28 19:25:30 flayer-server kernel: [    0.642025] devtmpfs: initialized
Jul 28 19:25:30 flayer-server kernel: [    0.642025] regulator: core version 0.5
Jul 28 19:25:30 flayer-server kernel: [    0.642025] Time: 17:25:14  Date: 07/28/11
Jul 28 19:25:30 flayer-server kernel: [    0.642025] NET: Registered protocol family 16
Jul 28 19:25:30 flayer-server kernel: [    0.642025] ACPI: bus type pci registered
Jul 28 19:25:30 flayer-server kernel: [    0.642025] Trying to unpack rootfs image as initramfs...
Jul 28 19:25:30 flayer-server kernel: [    0.642025] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jul 28 19:25:30 flayer-server kernel: [    0.642025] PCI: MCFG area at e0000000 reserved in E820
Jul 28 19:25:30 flayer-server kernel: [    0.642976] PCI: Using MMCONFIG at e0000000 - efffffff
Jul 28 19:25:30 flayer-server kernel: [    0.642977] PCI: Using configuration type 1 for base access
Jul 28 19:25:30 flayer-server kernel: [    0.643584] bio: create slab <bio-0> at 0
Jul 28 19:25:30 flayer-server kernel: [    0.653634] ACPI: Interpreter enabled
Jul 28 19:25:30 flayer-server kernel: [    0.653637] ACPI: (supports S0 S1 S3 S4 S5)
Jul 28 19:25:30 flayer-server kernel: [    0.653659] ACPI: Using IOAPIC for interrupt routing
Jul 28 19:25:30 flayer-server kernel: [    0.661370] ACPI: No dock devices found.
Jul 28 19:25:30 flayer-server kernel: [    0.661452] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 28 19:25:30 flayer-server kernel: [    0.662247] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 28 19:25:30 flayer-server kernel: [    0.662250] pci 0000:00:03.0: PME# disabled
Jul 28 19:25:30 flayer-server kernel: [    0.662302] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 28 19:25:30 flayer-server kernel: [    0.662304] pci 0000:00:07.0: PME# disabled
Jul 28 19:25:30 flayer-server kernel: [    0.662577] pci 0000:00:0a.1: PME# supported from D3hot D3cold
Jul 28 19:25:30 flayer-server kernel: [    0.662582] pci 0000:00:0a.1: PME# disabled
Jul 28 19:25:30 flayer-server kernel: [    0.662681] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 28 19:25:30 flayer-server kernel: [    0.662685] pci 0000:00:0b.0: PME# disabled
Jul 28 19:25:30 flayer-server kernel: [    0.662747] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
Jul 28 19:25:30 flayer-server kernel: [    0.662750] pci 0000:00:0b.1: PME# disabled
Jul 28 19:25:30 flayer-server kernel: [    0.663060] pci 0000:00:10.1: PME# supported from D3hot D3cold
Jul 28 19:25:30 flayer-server kernel: [    0.663063] pci 0000:00:10.1: PME# disabled
Jul 28 19:25:30 flayer-server kernel: [    0.663129] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 28 19:25:30 flayer-server kernel: [    0.663132] pci 0000:00:14.0: PME# disabled
Jul 28 19:25:30 flayer-server kernel: [    0.663197] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
Jul 28 19:25:30 flayer-server kernel: [    0.663200] pci 0000:01:00.0: PME# disabled
Jul 28 19:25:30 flayer-server kernel: [    0.663297] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
Jul 28 19:25:30 flayer-server kernel: [    0.663300] pci 0000:02:00.0: PME# disabled
Jul 28 19:25:30 flayer-server kernel: [    0.663348] pci 0000:02:02.0: PME# supported from D0 D3hot D3cold
Jul 28 19:25:30 flayer-server kernel: [    0.663351] pci 0000:02:02.0: PME# disabled
Jul 28 19:25:30 flayer-server kernel: [    0.663701] pci 0000:06:07.0: PME# supported from D0 D1 D2 D3hot
Jul 28 19:25:30 flayer-server kernel: [    0.663705] pci 0000:06:07.0: PME# disabled
Jul 28 19:25:30 flayer-server kernel: [    0.663738] pci 0000:00:10.0: transparent bridge
Jul 28 19:25:30 flayer-server kernel: [    0.729795] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.729919] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.730060] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.730182] ACPI: PCI Interrupt Link [LNK4] (IRQs *5 7 9 10 11 14 15)
Jul 28 19:25:30 flayer-server kernel: [    0.730302] ACPI: PCI Interrupt Link [LNK5] (IRQs *5 7 9 10 11 14 15)
Jul 28 19:25:30 flayer-server kernel: [    0.730423] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.730543] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.730663] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.730783] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
Jul 28 19:25:30 flayer-server kernel: [    0.730902] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.731023] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
Jul 28 19:25:30 flayer-server kernel: [    0.731142] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.731268] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
Jul 28 19:25:30 flayer-server kernel: [    0.731387] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.731506] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.731629] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
Jul 28 19:25:30 flayer-server kernel: [    0.731755] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
Jul 28 19:25:30 flayer-server kernel: [    0.731876] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.731997] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Jul 28 19:25:30 flayer-server kernel: [    0.732122] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
Jul 28 19:25:30 flayer-server kernel: [    0.732278] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.732426] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.732573] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.732721] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
Jul 28 19:25:30 flayer-server kernel: [    0.732870] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
Jul 28 19:25:30 flayer-server kernel: [    0.733017] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.733164] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.733313] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.733467] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
Jul 28 19:25:30 flayer-server kernel: [    0.733617] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.733765] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
Jul 28 19:25:30 flayer-server kernel: [    0.733916] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.734064] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.734212] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22) *0
Jul 28 19:25:30 flayer-server kernel: [    0.734361] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.734510] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22) *0
Jul 28 19:25:30 flayer-server kernel: [    0.734659] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
Jul 28 19:25:30 flayer-server kernel: [    0.734811] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.734966] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
Jul 28 19:25:30 flayer-server kernel: [    0.735114] ACPI: PCI Interrupt Link [APSI] (IRQs 23) *0
Jul 28 19:25:30 flayer-server kernel: [    0.735263] ACPI: PCI Interrupt Link [APSJ] (IRQs 23) *0
Jul 28 19:25:30 flayer-server kernel: [    0.735368] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
Jul 28 19:25:30 flayer-server kernel: [    0.735370] vgaarb: loaded
Jul 28 19:25:30 flayer-server kernel: [    0.735465] SCSI subsystem initialized
Jul 28 19:25:30 flayer-server kernel: [    0.735473] usbcore: registered new interface driver usbfs
Jul 28 19:25:30 flayer-server kernel: [    0.735473] usbcore: registered new interface driver hub
Jul 28 19:25:30 flayer-server kernel: [    0.735575] usbcore: registered new device driver usb
Jul 28 19:25:30 flayer-server kernel: [    0.735575] ACPI: WMI: Mapper loaded
Jul 28 19:25:30 flayer-server kernel: [    0.735575] PCI: Using ACPI for IRQ routing
Jul 28 19:25:30 flayer-server kernel: [    0.735575] NetLabel: Initializing
Jul 28 19:25:30 flayer-server kernel: [    0.735575] NetLabel:  domain hash size = 128
Jul 28 19:25:30 flayer-server kernel: [    0.735575] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 28 19:25:30 flayer-server kernel: [    0.735575] NetLabel:  unlabeled traffic allowed by default
Jul 28 19:25:30 flayer-server kernel: [    0.735575] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Jul 28 19:25:30 flayer-server kernel: [    0.735575] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Jul 28 19:25:30 flayer-server kernel: [    0.735575] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Jul 28 19:25:30 flayer-server kernel: [    0.750071] Switching to clocksource tsc
Jul 28 19:25:30 flayer-server kernel: [    0.751905] AppArmor: AppArmor Filesystem Enabled
Jul 28 19:25:30 flayer-server kernel: [    0.751930] pnp: PnP ACPI init
Jul 28 19:25:30 flayer-server kernel: [    0.751956] ACPI: bus type pnp registered
Jul 28 19:25:30 flayer-server kernel: [    0.755697] pnp: PnP ACPI: found 13 devices
Jul 28 19:25:30 flayer-server kernel: [    0.755699] ACPI: ACPI bus type pnp unregistered
Jul 28 19:25:30 flayer-server kernel: [    0.755711] system 00:01: ioport range 0x1000-0x107f has been reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755713] system 00:01: ioport range 0x1080-0x10ff has been reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755715] system 00:01: ioport range 0x1400-0x147f has been reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755718] system 00:01: ioport range 0x1480-0x14ff has been reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755720] system 00:01: ioport range 0x1800-0x187f has been reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755722] system 00:01: ioport range 0x1880-0x18ff has been reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755727] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755729] system 00:02: ioport range 0x295-0x314 has been reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755731] system 00:02: ioport range 0x880-0x88f has been reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755738] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755743] system 00:0c: iomem range 0xf0000-0xfffff could not be reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755746] system 00:0c: iomem range 0xfeff0000-0xfeff00ff has been reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755748] system 00:0c: iomem range 0x7fee0000-0x7fefffff could not be reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755750] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755753] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755755] system 00:0c: iomem range 0x100000-0x7fedffff could not be reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755757] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755759] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
Jul 28 19:25:30 flayer-server kernel: [    0.755762] system 00:0c: iomem range 0xfeff0000-0xfeff03ff could not be reserved
Jul 28 19:25:30 flayer-server kernel: [    0.760537] pci 0000:02:00.0: PCI bridge, secondary bus 0000:03
Jul 28 19:25:30 flayer-server kernel: [    0.760541] pci 0000:02:00.0:   IO window: 0xe000-0xefff
Jul 28 19:25:30 flayer-server kernel: [    0.760545] pci 0000:02:00.0:   MEM window: 0xda000000-0xddffffff
Jul 28 19:25:30 flayer-server kernel: [    0.760548] pci 0000:02:00.0:   PREFETCH window: 0x000000a0000000-0x000000bfffffff
Jul 28 19:25:30 flayer-server kernel: [    0.760554] pci 0000:02:02.0: PCI bridge, secondary bus 0000:04
Jul 28 19:25:30 flayer-server kernel: [    0.760556] pci 0000:02:02.0:   IO window: disabled
Jul 28 19:25:30 flayer-server kernel: [    0.760559] pci 0000:02:02.0:   MEM window: disabled
Jul 28 19:25:30 flayer-server kernel: [    0.760562] pci 0000:02:02.0:   PREFETCH window: disabled
Jul 28 19:25:30 flayer-server kernel: [    0.760567] pci 0000:01:00.0: PCI bridge, secondary bus 0000:02
Jul 28 19:25:30 flayer-server kernel: [    0.760569] pci 0000:01:00.0:   IO window: 0xe000-0xefff
Jul 28 19:25:30 flayer-server kernel: [    0.760573] pci 0000:01:00.0:   MEM window: 0xda000000-0xddffffff
Jul 28 19:25:30 flayer-server kernel: [    0.760577] pci 0000:01:00.0:   PREFETCH window: 0x000000a0000000-0x000000bfffffff
Jul 28 19:25:30 flayer-server kernel: [    0.760582] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
Jul 28 19:25:30 flayer-server kernel: [    0.760584] pci 0000:00:03.0:   IO window: 0xe000-0xefff
Jul 28 19:25:30 flayer-server kernel: [    0.760586] pci 0000:00:03.0:   MEM window: 0xda000000-0xddffffff
Jul 28 19:25:30 flayer-server kernel: [    0.760589] pci 0000:00:03.0:   PREFETCH window: 0x000000a0000000-0x000000bfffffff
Jul 28 19:25:30 flayer-server kernel: [    0.760593] pci 0000:00:07.0: PCI bridge, secondary bus 0000:05
Jul 28 19:25:30 flayer-server kernel: [    0.760594] pci 0000:00:07.0:   IO window: disabled
Jul 28 19:25:30 flayer-server kernel: [    0.760597] pci 0000:00:07.0:   MEM window: disabled
Jul 28 19:25:30 flayer-server kernel: [    0.760599] pci 0000:00:07.0:   PREFETCH window: disabled
Jul 28 19:25:30 flayer-server kernel: [    0.760602] pci 0000:00:10.0: PCI bridge, secondary bus 0000:06
Jul 28 19:25:30 flayer-server kernel: [    0.760604] pci 0000:00:10.0:   IO window: disabled
Jul 28 19:25:30 flayer-server kernel: [    0.760607] pci 0000:00:10.0:   MEM window: 0xdfe00000-0xdfefffff
Jul 28 19:25:30 flayer-server kernel: [    0.760610] pci 0000:00:10.0:   PREFETCH window: disabled
Jul 28 19:25:30 flayer-server kernel: [    0.760726] NET: Registered protocol family 2
Jul 28 19:25:30 flayer-server kernel: [    0.760846] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Jul 28 19:25:30 flayer-server kernel: [    0.761495] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Jul 28 19:25:30 flayer-server kernel: [    0.764386] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 28 19:25:30 flayer-server kernel: [    0.765176] TCP: Hash tables configured (established 262144 bind 65536)
Jul 28 19:25:30 flayer-server kernel: [    0.765179] TCP reno registered
Jul 28 19:25:30 flayer-server kernel: [    0.765324] NET: Registered protocol family 1
Jul 28 19:25:30 flayer-server kernel: [    0.801326] Freeing initrd memory: 8171k freed
Jul 28 19:25:30 flayer-server kernel: [    1.760011] pci 0000:00:0b.0: OHCI: BIOS handoff failed (BIOS bug?) 00000784
Jul 28 19:25:30 flayer-server kernel: [    3.770006] pci 0000:00:0b.1: EHCI: BIOS handoff failed (BIOS bug?) 01010001
Jul 28 19:25:30 flayer-server kernel: [    3.770575] Scanning for low memory corruption every 60 seconds
Jul 28 19:25:30 flayer-server kernel: [    3.770713] audit: initializing netlink socket (disabled)
Jul 28 19:25:30 flayer-server kernel: [    3.770729] type=2000 audit(1311873916.770:1): initialized
Jul 28 19:25:30 flayer-server kernel: [    3.778806] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jul 28 19:25:30 flayer-server kernel: [    3.780174] VFS: Disk quotas dquot_6.5.2
Jul 28 19:25:30 flayer-server kernel: [    3.780221] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 28 19:25:30 flayer-server kernel: [    3.780760] fuse init (API version 7.13)
Jul 28 19:25:30 flayer-server kernel: [    3.780825] msgmni has been set to 4015
Jul 28 19:25:30 flayer-server kernel: [    3.781213] alg: No test for stdrng (krng)
Jul 28 19:25:30 flayer-server kernel: [    3.781255] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul 28 19:25:30 flayer-server kernel: [    3.781257] io scheduler noop registered
Jul 28 19:25:30 flayer-server kernel: [    3.781259] io scheduler anticipatory registered
Jul 28 19:25:30 flayer-server kernel: [    3.781260] io scheduler deadline registered
Jul 28 19:25:30 flayer-server kernel: [    3.781290] io scheduler cfq registered (default)
Jul 28 19:25:30 flayer-server kernel: [    3.781685] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 28 19:25:30 flayer-server kernel: [    3.781705] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 28 19:25:30 flayer-server kernel: [    3.781811] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jul 28 19:25:30 flayer-server kernel: [    3.781814] ACPI: Power Button [PWRB]
Jul 28 19:25:30 flayer-server kernel: [    3.781866] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jul 28 19:25:30 flayer-server kernel: [    3.781868] ACPI: Power Button [PWRF]
Jul 28 19:25:30 flayer-server kernel: [    3.781917] fan PNP0C0B:00: registered as cooling_device0
Jul 28 19:25:30 flayer-server kernel: [    3.781921] ACPI: Fan [FAN] (on)
Jul 28 19:25:30 flayer-server kernel: [    3.782250] processor LNXCPU:00: registered as cooling_device1
Jul 28 19:25:30 flayer-server kernel: [    3.782282] processor LNXCPU:01: registered as cooling_device2
Jul 28 19:25:30 flayer-server kernel: [    3.782314] processor LNXCPU:02: registered as cooling_device3
Jul 28 19:25:30 flayer-server kernel: [    3.782349] processor LNXCPU:03: registered as cooling_device4
Jul 28 19:25:30 flayer-server kernel: [    3.786145] thermal LNXTHERM:01: registered as thermal_zone0
Jul 28 19:25:30 flayer-server kernel: [    3.786151] ACPI: Thermal Zone [THRM] (40 C)
Jul 28 19:25:30 flayer-server kernel: [    3.787301] Linux agpgart interface v0.103
Jul 28 19:25:30 flayer-server kernel: [    3.787335] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jul 28 19:25:30 flayer-server kernel: [    3.787434] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 28 19:25:30 flayer-server kernel: [    3.787726] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 28 19:25:30 flayer-server kernel: [    3.788579] brd: module loaded
Jul 28 19:25:30 flayer-server kernel: [    3.788968] loop: module loaded
Jul 28 19:25:30 flayer-server kernel: [    3.789030] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jul 28 19:25:30 flayer-server kernel: [    3.789409] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Jul 28 19:25:30 flayer-server kernel: [    3.789419] pata_acpi 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Jul 28 19:25:30 flayer-server kernel: [    3.789439] pata_acpi 0000:00:0e.0: PCI INT A disabled
Jul 28 19:25:30 flayer-server kernel: [    3.789669] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
Jul 28 19:25:30 flayer-server kernel: [    3.789672] pata_acpi 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
Jul 28 19:25:30 flayer-server kernel: [    3.789692] pata_acpi 0000:00:0f.0: PCI INT A disabled
Jul 28 19:25:30 flayer-server kernel: [    3.789926] Fixed MDIO Bus: probed
Jul 28 19:25:30 flayer-server kernel: [    3.789955] PPP generic driver version 2.4.2
Jul 28 19:25:30 flayer-server kernel: [    3.789979] tun: Universal TUN/TAP device driver, 1.6
Jul 28 19:25:30 flayer-server kernel: [    3.789981] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 28 19:25:30 flayer-server kernel: [    3.790052] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 28 19:25:30 flayer-server kernel: [    3.790288] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
Jul 28 19:25:30 flayer-server kernel: [    3.790295] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
Jul 28 19:25:30 flayer-server kernel: [    3.790304] ehci_hcd 0000:00:0b.1: EHCI Host Controller
Jul 28 19:25:30 flayer-server kernel: [    3.790332] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
Jul 28 19:25:30 flayer-server kernel: [    3.790354] ehci_hcd 0000:00:0b.1: debug port 1
Jul 28 19:25:30 flayer-server kernel: [    3.790377] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xdfffe000
Jul 28 19:25:30 flayer-server kernel: [    3.802510] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
Jul 28 19:25:30 flayer-server kernel: [    3.802601] usb usb1: configuration #1 chosen from 1 choice
Jul 28 19:25:30 flayer-server kernel: [    3.802630] hub 1-0:1.0: USB hub found
Jul 28 19:25:30 flayer-server kernel: [    3.802636] hub 1-0:1.0: 8 ports detected
Jul 28 19:25:30 flayer-server kernel: [    3.802685] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 28 19:25:30 flayer-server kernel: [    3.802922] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
Jul 28 19:25:30 flayer-server kernel: [    3.802929] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
Jul 28 19:25:30 flayer-server kernel: [    3.802939] ohci_hcd 0000:00:0b.0: OHCI Host Controller
Jul 28 19:25:30 flayer-server kernel: [    3.802964] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
Jul 28 19:25:30 flayer-server kernel: [    3.802982] ohci_hcd 0000:00:0b.0: irq 21, io mem 0xdffff000
Jul 28 19:25:30 flayer-server kernel: [    3.864570] usb usb2: configuration #1 chosen from 1 choice
Jul 28 19:25:30 flayer-server kernel: [    3.864589] hub 2-0:1.0: USB hub found
Jul 28 19:25:30 flayer-server kernel: [    3.864596] hub 2-0:1.0: 8 ports detected
Jul 28 19:25:30 flayer-server kernel: [    3.864642] uhci_hcd: USB Universal Host Controller Interface driver
Jul 28 19:25:30 flayer-server kernel: [    3.864689] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jul 28 19:25:30 flayer-server kernel: [    3.864691] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jul 28 19:25:30 flayer-server kernel: [    3.865482] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 28 19:25:30 flayer-server kernel: [    3.865555] mice: PS/2 mouse device common for all mice
Jul 28 19:25:30 flayer-server kernel: [    3.865653] rtc_cmos 00:05: RTC can wake from S4
Jul 28 19:25:30 flayer-server kernel: [    3.865682] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Jul 28 19:25:30 flayer-server kernel: [    3.865713] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Jul 28 19:25:30 flayer-server kernel: [    3.865806] device-mapper: uevent: version 1.0.3
Jul 28 19:25:30 flayer-server kernel: [    3.865909] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jul 28 19:25:30 flayer-server kernel: [    3.866143] device-mapper: multipath: version 1.1.0 loaded
Jul 28 19:25:30 flayer-server kernel: [    3.866146] device-mapper: multipath round-robin: version 1.0.0 loaded
Jul 28 19:25:30 flayer-server kernel: [    3.866578] cpuidle: using governor ladder
Jul 28 19:25:30 flayer-server kernel: [    3.866579] cpuidle: using governor menu
Jul 28 19:25:30 flayer-server kernel: [    3.866844] TCP cubic registered
Jul 28 19:25:30 flayer-server kernel: [    3.866963] NET: Registered protocol family 10
Jul 28 19:25:30 flayer-server kernel: [    3.867534] NET: Registered protocol family 17
Jul 28 19:25:30 flayer-server kernel: [    3.867649] registered taskstats version 1
Jul 28 19:25:30 flayer-server kernel: [    3.868024]   Magic number: 3:289:442
Jul 28 19:25:30 flayer-server kernel: [    3.868106] rtc_cmos 00:05: setting system clock to 2011-07-28 17:25:17 UTC (1311873917)
Jul 28 19:25:30 flayer-server kernel: [    3.868113] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 28 19:25:30 flayer-server kernel: [    3.868114] EDD information not available.
Jul 28 19:25:30 flayer-server kernel: [    3.868174] Freeing unused kernel memory: 888k freed
Jul 28 19:25:30 flayer-server kernel: [    3.868424] Write protecting the kernel read-only data: 7688k
Jul 28 19:25:30 flayer-server kernel: [    3.882068] udev: starting version 151
Jul 28 19:25:30 flayer-server kernel: [    3.884986] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jul 28 19:25:30 flayer-server kernel: [    3.940438] scsi0 : pata_amd
Jul 28 19:25:30 flayer-server kernel: [    3.941741] scsi1 : pata_amd
Jul 28 19:25:30 flayer-server kernel: [    3.942359] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfd00 irq 14
Jul 28 19:25:30 flayer-server kernel: [    3.942362] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfd08 irq 15
Jul 28 19:25:30 flayer-server kernel: [    3.942427] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Jul 28 19:25:30 flayer-server kernel: [    3.942430] sata_nv 0000:00:0e.0: Using SWNCQ mode
Jul 28 19:25:30 flayer-server kernel: [    3.944423] scsi2 : sata_nv
Jul 28 19:25:30 flayer-server kernel: [    3.944535] scsi3 : sata_nv
Jul 28 19:25:30 flayer-server kernel: [    3.944631] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
Jul 28 19:25:30 flayer-server kernel: [    3.944648] ohci1394 0000:06:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
Jul 28 19:25:30 flayer-server kernel: [    3.944760] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xf800 irq 23
Jul 28 19:25:30 flayer-server kernel: [    3.944764] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf808 irq 23
Jul 28 19:25:30 flayer-server kernel: [    3.944809] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 28 19:25:30 flayer-server kernel: [    3.945078] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
Jul 28 19:25:30 flayer-server kernel: [    3.945090] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
Jul 28 19:25:30 flayer-server kernel: [    3.956387] FDC 0 is a post-1991 82077
Jul 28 19:25:30 flayer-server kernel: [    4.003799] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[dfeff000-dfeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jul 28 19:25:30 flayer-server kernel: [    4.400008] usb 2-1: new low speed USB device using ohci_hcd and address 2
Jul 28 19:25:30 flayer-server kernel: [    4.430020] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 28 19:25:30 flayer-server kernel: [    4.470984] ata3.00: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
Jul 28 19:25:30 flayer-server kernel: [    4.470987] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul 28 19:25:30 flayer-server kernel: [    4.471073] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:bc:00:25:c2
Jul 28 19:25:30 flayer-server kernel: [    4.471076] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 28 19:25:30 flayer-server kernel: [    4.471099] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
Jul 28 19:25:30 flayer-server kernel: [    4.471101] sata_nv 0000:00:0f.0: Using SWNCQ mode
Jul 28 19:25:30 flayer-server kernel: [    4.471230] scsi4 : sata_nv
Jul 28 19:25:30 flayer-server kernel: [    4.471323] scsi5 : sata_nv
Jul 28 19:25:30 flayer-server kernel: [    4.471473] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xf300 irq 23
Jul 28 19:25:30 flayer-server kernel: [    4.471476] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xf308 irq 23
Jul 28 19:25:30 flayer-server kernel: [    4.510309] ata3.00: configured for UDMA/133
Jul 28 19:25:30 flayer-server kernel: [    4.510422] scsi 2:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Y 80.0 PQ: 0 ANSI: 5
Jul 28 19:25:30 flayer-server kernel: [    4.510591] sd 2:0:0:0: Attached scsi generic sg0 type 0
Jul 28 19:25:30 flayer-server kernel: [    4.510641] sd 2:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Jul 28 19:25:30 flayer-server kernel: [    4.510695] sd 2:0:0:0: [sda] Write Protect is off
Jul 28 19:25:30 flayer-server kernel: [    4.510717] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 28 19:25:30 flayer-server kernel: [    4.510845]  sda: sda1 sda2 < sda5 >
Jul 28 19:25:30 flayer-server kernel: [    4.539855] sd 2:0:0:0: [sda] Attached SCSI disk
Jul 28 19:25:30 flayer-server kernel: [    4.637584] usb 2-1: configuration #1 chosen from 1 choice
Jul 28 19:25:30 flayer-server kernel: [    4.802513] ata5: SATA link down (SStatus 0 SControl 300)
Jul 28 19:25:30 flayer-server kernel: [    4.841263] ata4: SATA link down (SStatus 0 SControl 300)
Jul 28 19:25:30 flayer-server kernel: [    5.170012] ata6: SATA link down (SStatus 0 SControl 300)
Jul 28 19:25:30 flayer-server kernel: [    5.173193] usbcore: registered new interface driver hiddev
Jul 28 19:25:30 flayer-server kernel: [    5.178769] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input4
Jul 28 19:25:30 flayer-server kernel: [    5.178856] generic-usb 0003:045E:0047.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:0b.0-1/input0
Jul 28 19:25:30 flayer-server kernel: [    5.178879] usbcore: registered new interface driver usbhid
Jul 28 19:25:30 flayer-server kernel: [    5.178881] usbhid: v2.6:USB HID core driver
Jul 28 19:25:30 flayer-server kernel: [    5.836682] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jul 28 19:25:30 flayer-server kernel: [   15.518534] udev: starting version 151
Jul 28 19:25:30 flayer-server kernel: [   15.546326] Adding 6022136k swap on /dev/sda5.  Priority:-1 extents:1 across:6022136k 
Jul 28 19:25:30 flayer-server kernel: [   15.570438] ACPI: resource nForce2_smbus [0x1c00-0x1c3f] conflicts with ACPI region SM00 [0x1c00-0x1c05]
Jul 28 19:25:30 flayer-server kernel: [   15.570442] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 28 19:25:30 flayer-server kernel: [   15.570558] i2c i2c-0: nForce2 SMBus adapter at 0x1c80
Jul 28 19:25:30 flayer-server kernel: [   15.572351] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 28 19:25:30 flayer-server kernel: [   15.612330] lp: driver loaded but no devices found
Jul 28 19:25:30 flayer-server kernel: [   15.637135] vga16fb: mapped to 0xffff8800000a0000
Jul 28 19:25:30 flayer-server kernel: [   15.637254] fb0: VGA16 VGA frame buffer device
Jul 28 19:25:30 flayer-server kernel: [   15.657544] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 28 19:25:30 flayer-server kernel: [   15.672260] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Jul 28 19:25:30 flayer-server kernel: [   15.672713] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Jul 28 19:25:30 flayer-server kernel: [   15.672715] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Jul 28 19:25:30 flayer-server kernel: [   15.672716] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Jul 28 19:25:30 flayer-server kernel: [   15.674855] type=1505 audit(1311873929.301:2):  operation="profile_load" pid=692 name="/sbin/dhclient3"
Jul 28 19:25:30 flayer-server kernel: [   15.675427] type=1505 audit(1311873929.301:3):  operation="profile_load" pid=692 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 28 19:25:30 flayer-server kernel: [   15.675737] type=1505 audit(1311873929.301:4):  operation="profile_load" pid=692 name="/usr/lib/connman/scripts/dhclient-script"
Jul 28 19:25:30 flayer-server kernel: [   15.677002] type=1505 audit(1311873929.301:5):  operation="profile_replace" pid=705 name="/sbin/dhclient3"
Jul 28 19:25:30 flayer-server kernel: [   15.678012] type=1505 audit(1311873929.301:6):  operation="profile_replace" pid=705 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 28 19:25:30 flayer-server kernel: [   15.678326] type=1505 audit(1311873929.301:7):  operation="profile_replace" pid=705 name="/usr/lib/connman/scripts/dhclient-script"
Jul 28 19:25:30 flayer-server kernel: [   15.700628] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 28 19:25:30 flayer-server kernel: [   15.727749] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Jul 28 19:25:30 flayer-server kernel: [   15.727754] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
Jul 28 19:25:30 flayer-server kernel: [   15.727756] hda_intel: Disable MSI for Nvidia chipset
Jul 28 19:25:30 flayer-server kernel: [   15.832115] Console: switching to colour frame buffer device 80x30
Jul 28 19:25:30 flayer-server kernel: [   16.530182] nvidia: module license 'NVIDIA' taints kernel.
Jul 28 19:25:30 flayer-server kernel: [   16.530186] Disabling lock debugging due to kernel taint
Jul 28 19:25:30 flayer-server kernel: [   16.601405] type=1505 audit(1311873930.231:8):  operation="profile_load" pid=987 name="/usr/share/gdm/guest-session/Xsession"
Jul 28 19:25:30 flayer-server kernel: [   16.601533] type=1505 audit(1311873930.231:9):  operation="profile_replace" pid=988 name="/sbin/dhclient3"
Jul 28 19:25:30 flayer-server kernel: [   16.602106] type=1505 audit(1311873930.231:10):  operation="profile_replace" pid=988 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 28 19:25:30 flayer-server kernel: [   16.602425] type=1505 audit(1311873930.231:11):  operation="profile_replace" pid=988 name="/usr/lib/connman/scripts/dhclient-script"
Jul 28 19:25:30 flayer-server kernel: [   17.073760] hda_codec: ALC1200: BIOS auto-probing.
Jul 28 19:25:30 flayer-server kernel: [   17.110314] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
Jul 28 19:25:30 flayer-server kernel: [   17.110328] nvidia 0000:03:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
Jul 28 19:25:30 flayer-server kernel: [   17.110340] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jul 28 19:25:30 flayer-server kernel: [   17.110524] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Jul 28 19:25:30 flayer-server kernel: [   17.321003] VBoxDrv: dbg - g_abExecMemory=ffffffffa0e21a20
Jul 28 19:25:30 flayer-server kernel: [   17.321096] vboxdrv: fAsync=0 offMin=0x13b offMax=0x5799
Jul 28 19:25:30 flayer-server kernel: [   17.321419] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jul 28 19:25:31 flayer-server kernel: [   17.449637] ppdev: user-space parallel port driver
Jul 28 19:25:31 flayer-server kernel: [   17.712599] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:10.1/input/input5
Jul 28 19:25:48 flayer-server kernel: [   34.580934] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
Jul 28 19:25:53 flayer-server pulseaudio[1580]: ratelimit.c: 2 events suppressed
```

---

### Post by Flayer1 on 2011-07-28
Have had at least 3 more freezes since the last post, and nothing new in the logs. There is nothing unusual before the freeze-up. It seems like it happens when I use applications like Virtualbox, and as I said earlier, visiting websites with flash.

I ran a Memtest, but it wouldn't find any RAM-issues.
So, I'm starting to think it might be my HDD? It's quite new though, bought it this winter. It's a Western Digital Caviar 1TB.

Any ideas?

---

### Post by Sergius14 on 2011-07-28
Start a Terminal and run

```
sudo uname -a
```

Paste the result.

---

### Post by Flayer1 on 2011-07-28
This is the result from the command:
```
Linux flayer-server 2.6.32-33-generic 
#70-Ubuntu SMP Thu Jul 7 21:13:52 UTC 2011 x86_64 GNU/Linux
```

---

### Post by Sergius14 on 2011-07-28
That's the original 10.04 LTS kernel series.

In your place, I'll give a test to newer kernel.

You can do a backport and upgrade from Synaptic.

```

sudo add-apt-repository ppa:kernel-ppa/ppa 
sudo apt-get update
sudo apt-get install linux-headers-2.6.38-1-generic linux-image-2.6.38-1-generic
```


Or go to this [link]("http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa").

---

### Post by Flayer1 on 2011-07-30
Nope, that didn't solve it either.
But I did test to un-plug my PS/2 keyboard over the night, and had no crash what so ever. I read in a similiar thread that someone had solved it by not using USB to PS/2 converter on his mouse.
Could this be an actual source causing my problems?

---

### Post by Flayer1 on 2011-07-31
Seems like that a PS/2 unit wasn't the problem either, but the computer lasted a lot longer before it froze without it.

---

### Post by tannedin on 2011-08-19
Any new developments on this thread? I have a 10.04.3 dual core AMD opteron server that freezes about 1-3 hours; no network (destination host unreachable from ping) and command line is completely frozen with its black 'screensaver)

---

### Post by Flayer1 on 2011-08-19
Nope. Still have the freezes and unresponsive lock-ups.
When it occurs I have no network or any way of communicating with the server. The only thing I can do is to hard-reboot it.
There's no logs or any information about it either.
I re-installed the server to 11.04, but it's the same symptoms.
I'm almost giving this up, seems like there are no solution.

---

