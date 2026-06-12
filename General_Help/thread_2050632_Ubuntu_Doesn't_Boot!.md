---
title: "Ubuntu Doesn't Boot!"
date: 2012-08-31
forum: General Help
---

### Post by pyro.xyz on 2012-08-31
Okay, the problems with my computer are becoming unacceptable, and no one has even tried to help me with them yet. Hibernate works, sure. I STILL NEED TO BOOT FROM A USB BOOTABLE DRIVE, OR ELSE IT STILL WILL NOT BOOT!Now, I have an even worse problem!!! Almost every time I try to turn the computer on, right after it actually powers on, it will power off. Added to my previous problems, that means that I actually needed to turn my computer on 23 times before the operating system was able to boot!!! Also, before that problem started happening, I told you that I need to boot Ubuntu from the flash-drive that I installed it from. And, it seems as if my BIOS has very short term memory loss because I need to open BIOS before it is able to boot. However, I am not always able to actually get to the BIOS, because for about five times of booting, it shows the hp logo, and when that happens, I cannot access the BIOS. Does ANYONE have ANY help, or am I just going to have to be frustrated by this forever?!!?

---

### Post by greatsirkain on 2012-08-31
keep pressing f2 as it boots? Sometimes my Dell splash screen will stay up longer that it should so that's what I do to get to bios. I wouldn't mind knowing the answer to the usb thing, I still have to boot from supergrub2 on a flash drive otherwise a broken installation of windows xp pro boots. Maybe if I installed supergrub2 on the hardisk and edited the boot.config or something?

edit: I thought faulty power supply, if the BIOS is corrupt it might need flashing (seen some programs for ubuntu that claim to be able, but for that yes you would need someone with advanced ubuntu skills). There's plenty of live boot diagnosis tools/rescue disks and OS's that you could use to find out exactly what the problem is and as you don't have a problem booting from usb I suggest you get them all (including the latest firmare for your bios) and dump them onto usb with something like sardu live multiboot that way you always have an avenue to get into and fix your computer once you diagnose the initial power on problems

---

### Post by pyro.xyz on 2012-08-31
Yeah, I tried that, but it still didn't work. I'm going to need someone who has some fairly extensive knowledge of Ubuntu to help me.

---

### Post by gandaran on 2012-08-31
how did you install Ubuntu?
using Wubi (Inside Windows) or on separate partition?
and did you specify a boot partition or just let the installer do the default install?

---

### Post by oldfred on 2012-08-31
Is computer older and BIOS is loosing its memory. Then you may need to change the battery. If a laptop not sure if you can even change battery but on desktops there is a small button battery somewhere.

Post link to BootIfno report that this can create:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by Gordonbp531 on 2012-08-31
> **pyro.xyz said:**
> Almost every time I try to turn the computer on, right after it actually powers on, it will power off. Added to my previous problems, that means that I actually needed to turn my computer on 23 times before the operating system was able to boot!!! 

That sounds to me like a BIOS/hardware problem - maybe you need to sort that out first.
It's also possibly indicative of other hardware problems, which is why you have to boot from a USB drive and not from the internal HDD.
I don't think this is an Ubuntu problem at all....

---

### Post by gman101 on 2012-08-31
I had this problem as well ! At first it only required me to press the power button once to boot, then twice, then three times etc until i had to press the power button like 30 times to boot, this problem was accompanied by a strange hissing sound, do you have any such hissing sound ? 

I solved it by replacing my power supply unit, but if you cannot hear a hissing sound its not likely the power supply unit that is the cause, are you on a laptop or a desktop ? If your comp shuts down just as it begins to boot ubuntu (immediately after the splash screen) it could be caused by your display settings, if you can boot into safe mode i would recommend removing your current graphics drivers and seeing if you can boot up then. If you cant get past the splash screen try shutting your monitor down until you think you have past the splash screen the power the monitor up again!

---

### Post by pyro.xyz on 2012-08-31
Okay, this is the link that was given to me after running boot-repair:

[http://paste.ubuntu.com/1178103/]("http://paste.ubuntu.com/1178103/") Tell me what you think.

---

### Post by Gordonbp531 on 2012-08-31
I still think you've got hardware and/or BIOS problems which is why you are needing to press the power switch many times and can't boot from the HDD.

---

### Post by oldfred on 2012-08-31
I do not see any issues in BootInfo report. 

If while booting it is trying to run fsck and you are not letting it, then it may be a file issue. You could try running e2fsck. But I still think it may be hardware. I might also run the memory test from grub menu. Hold shift from BIOS to get menu.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

---

### Post by pyro.xyz on 2012-09-01
Okay, so whoever suggested trying boot-repair, Thank you very much! ):P I can now see grub when my laptop boots, and SO far, after even hibernating, it works. If I ever have problems with this again, I will be sure to let you know. However, I still think my BIOS is broken. Does any body know how to fix that? My laptop is an HP mini 110 and I can't find any BIOS for Linux for my laptop. Can anyone help with this?

---

### Post by pyro.xyz on 2012-09-01
Actually, now it's still suddenly turning off when it is booting. However, it doesn't ever turn off after a certain point in the boot-up process.

---

### Post by critin on 2012-09-01
> **pyro.xyz said:**
> Actually, now it's still suddenly turning off when it is booting. However, it doesn't ever turn off after a certain point in the boot-up process.

Does it turn off for only a few seconds and then come back on its own, or do you physically restart it with the button?  Sometimes on boot up my monitor button turns off, screen is black and I think it's turned off;  but if I wait a bit it will come back on and continue.

---

### Post by pyro.xyz on 2012-09-01
No, that normally happens anyways. I know when my laptop turns off, because the light on my power button turns off. Also, I used to have to do hard shut-downs (holding the power button down for about five seconds) to turn it off, and it made a distinct kind of beeping/chirping sound. That happens just about every time my laptop turns off on its own during boot.

---

### Post by critin on 2012-09-03
All right.   I left the word 'screen' out.  I thought maybe just the screen was affected and you began the process again thinking the machine had turned off.    :)

---

### Post by oldfred on 2012-09-03
I would look in log files to see if something is reported.

You can use Log File Viewer. I usually look at dmesg first. It is the same info as on the screen when you delete quiet splash on Linux line when booting. While a long list you just need to look for errors, repeats where it is trying to load something and then fails or very long times between entries.

---

### Post by pyro.xyz on 2012-09-03
I have no idea what most of it means, and I don't have a lot of time to just look through thousands of lines, so if any of you want to scan through this, go ahead.
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-29-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 (Ubuntu 3.2.0-29.46-generic-pae 3.2.24)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f43f000 (usable)
[    0.000000]  BIOS-e820: 000000003f43f000 - 000000003f4bf000 (reserved)
[    0.000000]  BIOS-e820: 000000003f4bf000 - 000000003f5bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f5bf000 - 000000003f5f7000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f5f7000 - 000000003f600000 (usable)
[    0.000000]  BIOS-e820: 000000003f600000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Hewlett-Packard HP Mini 110-3100                /148A, BIOS F.13 08/17/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3f600 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFE00000 mask 0FFE00000 write-protect
[    0.000000]   1 base 000000000 mask 0E0000000 write-back
[    0.000000]   2 base 020000000 mask 0E0000000 write-back
[    0.000000]   3 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364f4000 - 37272000
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 3f5f6120 00074 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 3f5f5000 000F4 (v04 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 3f5e6000 0BA96 (v01 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 3f589000 00040
[    0.000000] ACPI: HPET 3f5f4000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 3f5f3000 00078 (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 3f5f2000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 3f5e5000 00176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 3f5e4000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 3f5e3000 004C4 (v02  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 3f5e2000 001F7 (v02  PmRef  Cpu0Tst 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 3f5e1000 00064 (v02  PmRef  Cpu1Tst 00003000 INTL 20051117)
[    0.000000] ACPI: WDAT 3f5e0000 00194 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 122MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0003f600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f43f
[    0.000000]     0: 0x0003f5f7 -> 0x0003f600
[    0.000000] On node 0 totalpages: 259031
[    0.000000] free_area_init_node: node 0, pgdat c1866a40, node_mem_map f740d200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 245 pages used for memmap
[    0.000000]   HighMem zone: 30549 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
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
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f73cf000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257002
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=4b8fc25a-3135-4095-8708-9fae90cfa1f5 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4153088 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0003f600)
[    0.000000] Memory: 998708k/1038336k available (5814k kernel code, 37416k reserved, 2841k data, 740k init, 123176k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1875000 - 0xc192e000   ( 740 kB)
[    0.000000]       .data : 0xc15adb64 - 0xc1874240   (2841 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15adb64   (5814 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f5c0a000 soft=f5c0c000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.805 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.61 BogoMIPS (lpj=6651220)
[    0.004017] pid_max: default: 32768 minimum: 301
[    0.004073] Security Framework initialized
[    0.004113] AppArmor: AppArmor initialized
[    0.004118] Yama: becoming mindful.
[    0.004240] Mount-cache hash table entries: 512
[    0.004516] Initializing cgroup subsys cpuacct
[    0.004532] Initializing cgroup subsys memory
[    0.004551] Initializing cgroup subsys devices
[    0.004557] Initializing cgroup subsys freezer
[    0.004563] Initializing cgroup subsys blkio
[    0.004578] Initializing cgroup subsys perf_event
[    0.008033] Disabled fast string operations
[    0.008042] CPU: Physical Processor ID: 0
[    0.008047] CPU: Processor Core ID: 0
[    0.008054] mce: CPU supports 5 MCE banks
[    0.008066] CPU0: Thermal monitoring handled by SMI
[    0.008075] using mwait in idle threads.
[    0.011883] ACPI: Core revision 20110623
[    0.028030] ftrace: allocating 26545 entries in 52 pages
[    0.032101] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032607] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075129] CPU0: Intel(R) Atom(TM) CPU N455   @ 1.66GHz stepping 0a
[    0.076004] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.076004] ... version:                3
[    0.076004] ... bit width:              40
[    0.076004] ... generic registers:      2
[    0.076004] ... value mask:             000000ffffffffff
[    0.076004] ... max period:             000000007fffffff
[    0.076004] ... fixed-purpose events:   3
[    0.076004] ... event mask:             0000000700000003
[    0.076004] NMI watchdog enabled, takes one hw-pmu counter.
[    0.076004] CPU 1 irqstacks, hard=f5d12000 soft=f5d14000
[    0.076004] Booting Node   0, Processors  #1
[    0.076004] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.008000] Disabled fast string operations
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.164071] NMI watchdog enabled, takes one hw-pmu counter.
[    0.164151] Brought up 2 CPUs
[    0.164160] Total of 2 processors activated (6650.92 BogoMIPS).
[    0.164735] devtmpfs: initialized
[    0.164735] EVM: security.selinux
[    0.164735] EVM: security.SMACK64
[    0.164735] EVM: security.capability
[    0.164735] PM: Registering ACPI NVS region at 3f4bf000 (1048576 bytes)
[    0.168555] print_constraints: dummy: 
[    0.168612] RTC time:  6:02:24, date: 09/03/12
[    0.168706] NET: Registered protocol family 16
[    0.168909] Trying to unpack rootfs image as initramfs...
[    0.169200] EISA bus registered
[    0.169247] ACPI: bus type pci registered
[    0.169491] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.169504] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.169511] PCI: Using MMCONFIG for extended config space
[    0.169518] PCI: Using configuration type 1 for base access
[    0.184335] bio: create slab <bio-0> at 0
[    0.184605] ACPI: Added _OSI(Module Device)
[    0.184614] ACPI: Added _OSI(Processor Device)
[    0.184622] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.184630] ACPI: Added _OSI(Processor Aggregator Device)
[    0.190319] ACPI: EC: Look up EC in DSDT
[    0.196064] ACPI: Executed 1 blocks of module-level executable AML code
[    0.202559] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.203899] ACPI: SSDT 3f494c98 001F7 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.205348] ACPI: Dynamic OEM Table Load:
[    0.205361] ACPI: SSDT   (null) 001F7 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.205791] ACPI: SSDT 3f493e18 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.207167] ACPI: Dynamic OEM Table Load:
[    0.207179] ACPI: SSDT   (null) 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.256997] ACPI: SSDT 3f494f18 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.258392] ACPI: Dynamic OEM Table Load:
[    0.258406] ACPI: SSDT   (null) 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.258814] ACPI: SSDT 3f492f18 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.260207] ACPI: Dynamic OEM Table Load:
[    0.260221] ACPI: SSDT   (null) 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.644670] ACPI: Interpreter enabled
[    0.644696] ACPI: (supports S0 S3 S4 S5)
[    0.644786] ACPI: Using IOAPIC for interrupt routing
[    0.663520] ACPI: Power Resource [FN00] (on)
[    0.664915] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.665431] ACPI: No dock devices found.
[    0.665440] HEST: Table not found.
[    0.665453] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.666859] ACPI Warning: For \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20110623/nspredef-359)
[    0.666887] \_SB_.PCI0:_OSC evaluation returned wrong type
[    0.666893] _OSC request data:1 8 1f 
[    0.666909] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.669278] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.669290] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.669300] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.669312] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xfebfffff]
[    0.669351] pci 0000:00:00.0: [8086:a010] type 0 class 0x000600
[    0.669437] pci 0000:00:02.0: [8086:a011] type 0 class 0x000300
[    0.669460] pci 0000:00:02.0: reg 10: [mem 0x54180000-0x541fffff]
[    0.669475] pci 0000:00:02.0: reg 14: [io  0x30c0-0x30c7]
[    0.669489] pci 0000:00:02.0: reg 18: [mem 0x40000000-0x4fffffff pref]
[    0.669504] pci 0000:00:02.0: reg 1c: [mem 0x54000000-0x540fffff]
[    0.669576] pci 0000:00:02.1: [8086:a012] type 0 class 0x000380
[    0.669596] pci 0000:00:02.1: reg 10: [mem 0x54100000-0x5417ffff]
[    0.669755] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.669793] pci 0000:00:1b.0: reg 10: [mem 0x54200000-0x54203fff 64bit]
[    0.669947] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.669961] pci 0000:00:1b.0: PME# disabled
[    0.670015] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.670172] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.670184] pci 0000:00:1c.0: PME# disabled
[    0.670240] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.670394] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.670406] pci 0000:00:1c.1: PME# disabled
[    0.670467] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.670551] pci 0000:00:1d.0: reg 20: [io  0x3080-0x309f]
[    0.670623] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.670710] pci 0000:00:1d.1: reg 20: [io  0x3060-0x307f]
[    0.670785] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.670869] pci 0000:00:1d.2: reg 20: [io  0x3040-0x305f]
[    0.670942] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.671026] pci 0000:00:1d.3: reg 20: [io  0x3020-0x303f]
[    0.671120] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.671828] pci 0000:00:1d.7: reg 10: [mem 0x54204400-0x542047ff]
[    0.671828] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.671828] pci 0000:00:1d.7: PME# disabled
[    0.671828] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.676098] pci 0000:00:1f.0: [8086:27bc] type 0 class 0x000601
[    0.676312] pci 0000:00:1f.2: [8086:27c1] type 0 class 0x000106
[    0.676351] pci 0000:00:1f.2: reg 10: [io  0x30b8-0x30bf]
[    0.676372] pci 0000:00:1f.2: reg 14: [io  0x30cc-0x30cf]
[    0.676393] pci 0000:00:1f.2: reg 18: [io  0x30b0-0x30b7]
[    0.676415] pci 0000:00:1f.2: reg 1c: [io  0x30c8-0x30cb]
[    0.676436] pci 0000:00:1f.2: reg 20: [io  0x30a0-0x30af]
[    0.676457] pci 0000:00:1f.2: reg 24: [mem 0x54204000-0x542043ff]
[    0.676541] pci 0000:00:1f.2: PME# supported from D3hot
[    0.676552] pci 0000:00:1f.2: PME# disabled
[    0.676601] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.676691] pci 0000:00:1f.3: reg 20: [io  0x3000-0x301f]
[    0.676922] pci 0000:01:00.0: [10ec:8136] type 0 class 0x000200
[    0.677007] pci 0000:01:00.0: reg 10: [io  0x2000-0x20ff]
[    0.677142] pci 0000:01:00.0: reg 18: [mem 0x50004000-0x50004fff 64bit pref]
[    0.677231] pci 0000:01:00.0: reg 20: [mem 0x50000000-0x50003fff 64bit pref]
[    0.677563] pci 0000:01:00.0: supports D1 D2
[    0.677573] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.677606] pci 0000:01:00.0: PME# disabled
[    0.677811] pci 0000:01:00.1: [10ec:5288] type 0 class 0x00ff00
[    0.677898] pci 0000:01:00.1: reg 10: [mem 0x53000000-0x5300ffff]
[    0.678437] pci 0000:01:00.1: supports D1 D2
[    0.678446] pci 0000:01:00.1: PME# supported from D1 D2 D3hot D3cold
[    0.678479] pci 0000:01:00.1: PME# disabled
[    0.678713] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.678727] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.678740] pci 0000:00:1c.0:   bridge window [mem 0x53000000-0x53ffffff]
[    0.678757] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
[    0.678909] pci 0000:02:00.0: [14e4:4727] type 0 class 0x000280
[    0.678966] pci 0000:02:00.0: reg 10: [mem 0x52000000-0x52003fff 64bit]
[    0.679224] pci 0000:02:00.0: supports D1 D2
[    0.679334] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.679347] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    0.679359] pci 0000:00:1c.1:   bridge window [mem 0x52000000-0x52ffffff]
[    0.679376] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
[    0.679501] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.679527] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.679537] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.679547] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.679557] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0xfebfffff] (subtractive decode)
[    0.679594] pci_bus 0000:00: on NUMA node 0
[    0.679610] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.680109] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.680390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.680594] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.681065] ACPI Warning: For \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20110623/nspredef-359)
[    0.681090] \_SB_.PCI0:_OSC evaluation returned wrong type
[    0.681096] _OSC request data:1 1f 1f 
[    0.681112]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.681311] ACPI Warning: For \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20110623/nspredef-359)
[    0.681335] \_SB_.PCI0:_OSC evaluation returned wrong type
[    0.681341] _OSC request data:1 0 1d 
[    0.681355]  pci0000:00: ACPI _OSC request failed (AE_TYPE), returned control mask: 0x1d
[    0.681362] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.690422] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.690649] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.690856] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.691061] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.691264] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.691482] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.691691] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.691902] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.692438] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.692469] vgaarb: loaded
[    0.692475] vgaarb: bridge control possible 0000:00:02.0
[    0.693007] i2c-core: driver [aat2870] using legacy suspend method
[    0.693015] i2c-core: driver [aat2870] using legacy resume method
[    0.693298] SCSI subsystem initialized
[    0.693482] libata version 3.00 loaded.
[    0.693685] usbcore: registered new interface driver usbfs
[    0.693736] usbcore: registered new interface driver hub
[    0.693843] usbcore: registered new device driver usb
[    0.694266] PCI: Using ACPI for IRQ routing
[    0.705089] PCI: pci_cache_line_size set to 64 bytes
[    0.705286] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.705297] reserve RAM buffer: 000000003f43f000 - 000000003fffffff 
[    0.705309] reserve RAM buffer: 000000003f600000 - 000000003fffffff 
[    0.705724] NetLabel: Initializing
[    0.705732] NetLabel:  domain hash size = 128
[    0.705738] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.705772] NetLabel:  unlabeled traffic allowed by default
[    0.705974] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.705988] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.706004] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.712207] Switching to clocksource hpet
[    0.735941] AppArmor: AppArmor Filesystem Enabled
[    0.736074] pnp: PnP ACPI init
[    0.736130] ACPI: bus type pnp registered
[    0.738273] pnp 00:00: [bus 00-ff]
[    0.738286] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.738295] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.738303] pnp 00:00: [io  0x0d00-0xffff window]
[    0.738312] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.738321] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.738335] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.738344] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.738353] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.738362] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.738370] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.738379] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.738388] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.738397] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.738405] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.738414] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.738423] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.738431] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.738440] pnp 00:00: [mem 0x40000000-0xfebfffff window]
[    0.738623] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.739057] pnp 00:01: [io  0x002e-0x002f]
[    0.739067] pnp 00:01: [io  0x004e-0x004f]
[    0.739074] pnp 00:01: [io  0x0061]
[    0.739081] pnp 00:01: [io  0x0070]
[    0.739088] pnp 00:01: [io  0x0080]
[    0.739095] pnp 00:01: [io  0x0092]
[    0.739102] pnp 00:01: [io  0x00b2-0x00b3]
[    0.739110] pnp 00:01: [io  0x0063]
[    0.739117] pnp 00:01: [io  0x0065]
[    0.739124] pnp 00:01: [io  0x0067]
[    0.739131] pnp 00:01: [io  0x0600-0x060f]
[    0.739138] pnp 00:01: [io  0x0610]
[    0.739145] pnp 00:01: [io  0x0800-0x080f]
[    0.739154] pnp 00:01: [io  0x0810-0x0817]
[    0.739162] pnp 00:01: [io  0x0400-0x047f]
[    0.739170] pnp 00:01: [io  0x0500-0x053f]
[    0.739178] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.739186] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.739195] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.739204] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.739213] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.739221] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.739230] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.739454] system 00:01: [io  0x0600-0x060f] has been reserved
[    0.739465] system 00:01: [io  0x0610] has been reserved
[    0.739474] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.739484] system 00:01: [io  0x0810-0x0817] has been reserved
[    0.739494] system 00:01: [io  0x0400-0x047f] has been reserved
[    0.739504] system 00:01: [io  0x0500-0x053f] has been reserved
[    0.739516] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.739526] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.739537] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.739547] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.739558] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.739568] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.739579] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.739591] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.739633] pnp 00:02: [io  0x0000-0x001f]
[    0.739641] pnp 00:02: [io  0x0081-0x0091]
[    0.739649] pnp 00:02: [io  0x0093-0x009f]
[    0.739656] pnp 00:02: [io  0x00c0-0x00df]
[    0.739664] pnp 00:02: [dma 4]
[    0.739769] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.739859] pnp 00:03: [io  0x0070-0x0077]
[    0.739961] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.740232] pnp 00:04: [irq 0 disabled]
[    0.740260] pnp 00:04: [irq 8]
[    0.740269] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.740387] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.740430] pnp 00:05: [io  0x00f0]
[    0.740446] pnp 00:05: [irq 13]
[    0.740559] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.740600] pnp 00:06: [mem 0xff800000-0xffffffff]
[    0.740703] pnp 00:06: Plug and Play ACPI device, IDs INT0800 (active)
[    0.740778] pnp 00:07: [io  0x0060]
[    0.740786] pnp 00:07: [io  0x0064]
[    0.740801] pnp 00:07: [irq 1]
[    0.740912] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.740977] pnp 00:08: [irq 12]
[    0.741091] pnp 00:08: Plug and Play ACPI device, IDs SYN1e33 SYN1e00 SYN0002 PNP0f13 (active)
[    0.741347] pnp: PnP ACPI: found 9 devices
[    0.741354] ACPI: ACPI bus type pnp unregistered
[    0.741364] PnPBIOS: Disabled by ACPI PNP
[    0.783458] PCI: max bus depth: 1 pci_try_num: 2
[    0.783520] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.783532] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.783547] pci 0000:00:1c.0:   bridge window [mem 0x53000000-0x53ffffff]
[    0.783561] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
[    0.783579] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.783591] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    0.783606] pci 0000:00:1c.1:   bridge window [mem 0x52000000-0x52ffffff]
[    0.783620] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
[    0.783638] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.783702] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.783716] pci 0000:00:1c.0: setting latency timer to 64
[    0.783747] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.783760] pci 0000:00:1c.1: setting latency timer to 64
[    0.783778] pci 0000:00:1e.0: setting latency timer to 64
[    0.783790] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.783798] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.783808] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.783817] pci_bus 0000:00: resource 7 [mem 0x40000000-0xfebfffff]
[    0.783826] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.783835] pci_bus 0000:01: resource 1 [mem 0x53000000-0x53ffffff]
[    0.783845] pci_bus 0000:01: resource 2 [mem 0x50000000-0x50ffffff 64bit pref]
[    0.783854] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.783863] pci_bus 0000:02: resource 1 [mem 0x52000000-0x52ffffff]
[    0.783873] pci_bus 0000:02: resource 2 [mem 0x51000000-0x51ffffff 64bit pref]
[    0.783882] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.783891] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.783900] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.783909] pci_bus 0000:03: resource 7 [mem 0x40000000-0xfebfffff]
[    0.784074] NET: Registered protocol family 2
[    0.784290] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.785122] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.786246] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.786821] TCP: Hash tables configured (established 131072 bind 65536)
[    0.786832] TCP reno registered
[    0.786850] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.786879] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.787168] NET: Registered protocol family 1
[    0.787216] pci 0000:00:02.0: Boot video device
[    0.787265] pci 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.787295] pci 0000:00:1d.0: PCI INT A disabled
[    0.787336] pci 0000:00:1d.1: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.787365] pci 0000:00:1d.1: PCI INT C disabled
[    0.787386] pci 0000:00:1d.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.787414] pci 0000:00:1d.2: PCI INT B disabled
[    0.787447] pci 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.787476] pci 0000:00:1d.3: PCI INT D disabled
[    0.787500] pci 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.800115] pci 0000:00:1d.7: PCI INT A disabled
[    0.800194] PCI: CLS 64 bytes, default 64
[    0.800208] Simple Boot Flag at 0x44 set to 0x1
[    0.801333] audit: initializing netlink socket (disabled)
[    0.801362] type=2000 audit(1346652143.796:1): initialized
[    0.863285] Freeing initrd memory: 13816k freed
[    0.863324] highmem bounce pool size: 64 pages
[    0.863340] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.879585] VFS: Disk quotas dquot_6.5.2
[    0.879754] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.881293] fuse init (API version 7.17)
[    0.881564] msgmni has been set to 1737
[    0.882498] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.882567] io scheduler noop registered
[    0.882575] io scheduler deadline registered
[    0.882594] io scheduler cfq registered (default)
[    0.882860] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.882947] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.883086] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.883160] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.883355] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.883427] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.883600] intel_idle: MWAIT substates: 0x20220
[    0.883619] intel_idle: v0.4 model 0x1C
[    0.883623] intel_idle: lapic_timer_reliable_states 0x2
[    0.883629] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.884664] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.885624] ACPI: AC Adapter [AC] (off-line)
[    0.885868] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.885881] ACPI: Power Button [PWRB]
[    0.886002] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.887629] ACPI: Lid Switch [LID0]
[    0.887772] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.887782] ACPI: Power Button [PWRF]
[    0.899452] ACPI Warning: For \_TZ_.THRM._AL0: Return Package has no elements (empty) (20110623/nspredef-463)
[    0.899469] ACPI: [Package] has zero elements (f5e46dc0)
[    0.899475] ACPI: Invalid active0 threshold
[    0.903240] thermal LNXTHERM:00: registered as thermal_zone0
[    0.903247] ACPI: Thermal Zone [THRM] (50 C)
[    0.903301] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.903322] ACPI: Battery Slot [BAT0] (battery present)
[    0.903425] ERST: Table is not found!
[    0.903430] GHES: HEST is not enabled!
[    0.903573] isapnp: Scanning for PnP cards...
[    0.903675] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.949788] ACPI: Battery Slot [BAT0] (battery present)
[    1.258036] isapnp: No Plug & Play device found
[    1.293209] Linux agpgart interface v0.103
[    1.293389] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.293603] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.293872] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.294133] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[    1.298355] brd: module loaded
[    1.300606] loop: module loaded
[    1.300988] ahci 0000:00:1f.2: version 3.0
[    1.301016] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.301114] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.301182] ahci: SSS flag set, parallel bus scan disabled
[    1.301231] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.301240] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pmp pio slum part 
[    1.301250] ahci 0000:00:1f.2: setting latency timer to 64
[    1.302640] scsi0 : ahci
[    1.302895] scsi1 : ahci
[    1.303102] scsi2 : ahci
[    1.303309] scsi3 : ahci
[    1.303782] ata1: SATA max UDMA/133 abar m1024@0x54204000 port 0x54204100 irq 42
[    1.303791] ata2: SATA max UDMA/133 abar m1024@0x54204000 port 0x54204180 irq 42
[    1.303797] ata3: DUMMY
[    1.303801] ata4: DUMMY
[    1.305100] Fixed MDIO Bus: probed
[    1.305177] tun: Universal TUN/TAP device driver, 1.6
[    1.305183] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.305342] PPP generic driver version 2.4.2
[    1.305615] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.305664] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.305714] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.305722] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.305842] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.305880] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.305899] ehci_hcd 0000:00:1d.7: debug port 1
[    1.309796] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.309836] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x54204400
[    1.324037] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.324371] hub 1-0:1.0: USB hub found
[    1.324384] hub 1-0:1.0: 8 ports detected
[    1.324583] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.324622] uhci_hcd: USB Universal Host Controller Interface driver
[    1.324672] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.324691] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.324699] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.324830] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.324873] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00003080
[    1.325214] hub 2-0:1.0: USB hub found
[    1.325227] hub 2-0:1.0: 2 ports detected
[    1.325370] uhci_hcd 0000:00:1d.1: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.325387] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.325394] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.325517] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.325578] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00003060
[    1.325906] hub 3-0:1.0: USB hub found
[    1.325917] hub 3-0:1.0: 2 ports detected
[    1.326054] uhci_hcd 0000:00:1d.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.326070] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.326078] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.326207] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.326270] uhci_hcd 0000:00:1d.2: irq 17, io base 0x00003040
[    1.326615] hub 4-0:1.0: USB hub found
[    1.326627] hub 4-0:1.0: 2 ports detected
[    1.326770] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.326788] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.326795] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.326928] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.326987] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00003020
[    1.327320] hub 5-0:1.0: USB hub found
[    1.327332] hub 5-0:1.0: 2 ports detected
[    1.327613] usbcore: registered new interface driver libusual
[    1.327720] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    1.333038] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.333057] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.333447] mousedev: PS/2 mouse device common for all mice
[    1.333942] rtc_cmos 00:03: RTC can wake from S4
[    1.334153] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.334197] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.334338] device-mapper: uevent: version 1.0.3
[    1.334545] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.334645] EISA: Probing bus 0 at eisa.0
[    1.334651] EISA: Cannot allocate resource for mainboard
[    1.334658] Cannot allocate resource for EISA slot 1
[    1.334664] Cannot allocate resource for EISA slot 2
[    1.334669] Cannot allocate resource for EISA slot 3
[    1.334675] Cannot allocate resource for EISA slot 4
[    1.334680] Cannot allocate resource for EISA slot 5
[    1.334686] Cannot allocate resource for EISA slot 6
[    1.334691] Cannot allocate resource for EISA slot 7
[    1.334697] Cannot allocate resource for EISA slot 8
[    1.334701] EISA: Detected 0 cards.
[    1.334718] cpufreq-nforce2: No nForce2 chipset.
[    1.334916] cpuidle: using governor ladder
[    1.335214] cpuidle: using governor menu
[    1.335219] EFI Variables Facility v0.08 2004-May-17
[    1.335767] TCP cubic registered
[    1.336100] NET: Registered protocol family 10
[    1.337332] NET: Registered protocol family 17
[    1.337345] Registering the dns_resolver key type
[    1.337396] Using IPI No-Shortcut mode
[    1.337780] PM: Hibernation image not present or could not be loaded.
[    1.337807] registered taskstats version 1
[    1.357024]   Magic number: 12:836:12
[    1.357175] rtc_cmos 00:03: setting system clock to 2012-09-03 06:02:25 UTC (1346652145)
[    1.358017] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.358022] EDD information not available.
[    1.462768] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.748080] usb 1-8: new high-speed USB device number 3 using ehci_hcd
[    1.792080] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.801689] ata1.00: unexpected _GTF length (4)
[    1.801876] ata1.00: ATA-8: SAMSUNG HM250HI, 2AC101C4, max UDMA/133
[    1.801890] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.811527] ata1.00: unexpected _GTF length (4)
[    1.811728] ata1.00: configured for UDMA/133
[    1.812062] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM250HI  2AC1 PQ: 0 ANSI: 5
[    1.812416] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.812530] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.812625] sd 0:0:0:0: [sda] Write Protect is off
[    1.812636] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.812723] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.869169]  sda: sda1 sda2 < sda5 >
[    1.870210] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.132084] ata2: SATA link down (SStatus 0 SControl 300)
[    2.132424] Freeing unused kernel memory: 740k freed
[    2.132986] Write protecting the kernel text: 5816k
[    2.133033] Write protecting the kernel read-only data: 2376k
[    2.133040] NX-protecting the kernel data: 4424k
[    2.140148] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[    2.175378] udevd[92]: starting version 175
[    2.408952] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.409037] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.409138] r8169 0000:01:00.0: (unregistered net_device): unknown MAC, using family default
[    2.409179] r8169 0000:01:00.0: setting latency timer to 64
[    2.409435] r8169 0000:01:00.0: irq 43 for MSI/MSI-X
[    2.411460] r8169 0000:01:00.0: eth0: RTL8101e at 0xf8436000, 00:21:cc:5b:69:6c, XID 04000000 IRQ 43
[    2.613832] input: Microsoft LifeChat LX-3000  as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.3/input/input4
[    2.614185] generic-usb 0003:045E:070F.0001: input,hidraw0: USB HID v1.00 Device [Microsoft LifeChat LX-3000 ] on usb-0000:00:1d.1-1/input3
[    2.614252] usbcore: registered new interface driver usbhid
[    2.614260] usbhid: USB HID core driver
[    2.722400] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   15.236808] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.281649] udevd[302]: starting version 175
[   15.368090] lp: driver loaded but no devices found
[   15.380610] Adding 1035260k swap on /dev/sda5.  Priority:-1 extents:1 across:1035260k 
[   15.576773] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.716071] wmi: Mapper loaded
[   15.958975] rts_pstor: module is from the staging directory, the quality is unknown, you have been warned.
[   16.056529] lib80211: common routines for IEEE802.11 drivers
[   16.056540] lib80211_crypt: registered algorithm 'NULL'
[   16.109698] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.109711] Disabling lock debugging due to kernel taint
[   16.188466] Bluetooth: Core ver 2.16
[   16.188681] NET: Registered protocol family 31
[   16.188691] Bluetooth: HCI device and connection manager initialized
[   16.188700] Bluetooth: HCI socket layer initialized
[   16.188707] Bluetooth: L2CAP socket layer initialized
[   16.188730] Bluetooth: SCO socket layer initialized
[   16.216631] type=1400 audit(1346652160.356:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=523 comm="apparmor_parser"
[   16.218297] ppdev: user-space parallel port driver
[   16.220402] type=1400 audit(1346652160.360:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=523 comm="apparmor_parser"
[   16.221241] type=1400 audit(1346652160.360:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=523 comm="apparmor_parser"
[   16.224501] Initializing Realtek PCIE storage driver...
[   16.224591] rts_pstor 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   16.233433] Bluetooth: RFCOMM TTY layer initialized
[   16.233454] Bluetooth: RFCOMM socket layer initialized
[   16.233462] Bluetooth: RFCOMM ver 1.11
[   16.248238] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.248249] Bluetooth: BNEP filters: protocol multicast
[   16.251372] Resource length: 0x10000
[   16.251445] Original address: 0x53000000, remapped address: 0xf8620000
[   16.251460] pci->irq = 17
[   16.251468] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 17
[   16.251522] rts_pstor 0000:01:00.1: setting latency timer to 64
[   16.314191] type=1400 audit(1346652160.452:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=552 comm="apparmor_parser"
[   16.333743] type=1400 audit(1346652160.472:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=552 comm="apparmor_parser"
[   16.540074] scsi4 : SCSI emulation for PCI-Express Mass Storage devices
[   16.573279] [drm] Initialized drm 1.1.0 20060810
[   16.632076] rts_pstor: waiting for device to settle before scanning
[   16.669442] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.669462] wl 0000:02:00.0: setting latency timer to 64
[   16.767882] i915 0000:00:02.0: power state changed by ACPI to D0
[   16.767901] i915 0000:00:02.0: power state changed by ACPI to D0
[   16.767922] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.767935] i915 0000:00:02.0: setting latency timer to 64
[   16.866085] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   16.866102] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   16.866110] [drm] Driver supports precise vblank timestamp query.
[   16.905640] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   16.973268] Linux video capture interface: v2.00
[   16.975381] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b1eb)
[   17.017803] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input5
[   17.018171] usbcore: registered new interface driver uvcvideo
[   17.018180] USB Video Class driver (1.1.1)
[   17.187400] lib80211_crypt: registered algorithm 'TKIP'
[   17.262236] [drm] initialized overlay support
[   17.317579] fbcon: inteldrmfb (fb0) is primary device
[   17.319899] Console: switching to colour frame buffer device 128x37
[   17.320094] fb0: inteldrmfb frame buffer device
[   17.320101] drm: registered panic notifier
[   17.410069] acpi device:21: registered as cooling_device2
[   17.411256] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   17.411574] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   17.411807] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.412736] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.412882] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   17.413035] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   17.414033] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
[   17.506024] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   17.506847] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   17.642290] rts_pstor: device scan complete
[   17.643725] scsi 4:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   17.649696] Bad LUN (0:1)
[   17.650104] Bad target number (1:0)
[   17.651539] Bad target number (2:0)
[   17.652413] Bad target number (3:0)
[   17.653340] Bad target number (4:0)
[   17.654312] Bad target number (5:0)
[   17.655343] Bad target number (6:0)
[   17.656581] Bad target number (7:0)
[   17.658398] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   17.658565] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   17.670818] usbcore: registered new interface driver snd-usb-audio
[   17.719637] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0xa0400
[   17.754493] init: failsafe main process (656) killed by TERM signal
[   17.768900] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   18.124795] input: HP WMI hotkeys as /devices/virtual/input/input10
[   18.205495] type=1400 audit(1346652162.344:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=775 comm="apparmor_parser"
[   18.246793] type=1400 audit(1346652162.384:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=776 comm="apparmor_parser"
[   18.261342] type=1400 audit(1346652162.400:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=776 comm="apparmor_parser"
[   18.262178] type=1400 audit(1346652162.400:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=776 comm="apparmor_parser"
[   18.326689] r8169 0000:01:00.0: eth0: link down
[   18.331766] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.338747] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.362804] type=1400 audit(1346652162.500:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=781 comm="apparmor_parser"

```

---

### Post by oldfred on 2012-09-03
Are you using an external USB hub?

Do you have USB3 ports?

---

### Post by pyro.xyz on 2012-09-03
No, I don't believe that I do have usb3 ports, as long as that is referring to usb3 as opposed to usb2.0 ports. However, I may be mistaken.

---

