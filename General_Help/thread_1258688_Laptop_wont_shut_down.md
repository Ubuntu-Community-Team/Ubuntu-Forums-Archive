---
title: "Laptop wont shut down"
date: 2009-09-05
forum: General Help
---

### Post by xiodene on 2009-09-05
I recently got a new laptop, ran vista on it for a week before i got around to installing  Ubuntu so i know it was working fine.

I installed 8.04 and it wont shut down? it gets to the splash screen, the status bar goes all the way to 0 then that screen just stays there and i have to press and hold th power button.
I upgraded to 9.04 last night and it does almost the same thing, goes to the splash screen, status bar empties but then the screen goes blank and i get a message in the top corned reading "[   253.912524] Power down]" and it just stays there.

Any ideas guys??

I have tried the force ascii thing and tried disableing wireless before shutting down but it has not helped.

Any help would be much appreciated

Matt

---

### Post by P4man on 2009-09-05
> **xiodene said:**
> I
I have tried the force ascii thing 

you mean force acpi?
Shutting down is an ACPI function. It seems like its not working on your laptop. You can either check if ACPI is enabled in your bios, or perhaps check if there is a bios update available for your machine. What laptop do you have?

---

### Post by xiodene on 2009-09-05
Oops yes i meant ACPI, I have a ASUS X59GLseries laptop.
Il go check to see if their is a bios update. How do i go about checking the bios to see is acpi in enabled?

Thanks

---

### Post by P4man on 2009-09-05
It seems there is a bug in the current kernel handling your ACPI bios:

[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/366200](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/366200)

The good news is that apparently its solved in the upstream kernel (2.6.30).

You could give it a try, but its not released yet, therefore not supported, and it may give you some trouble with video drivers. Nothing that can't be fixed, but just warning you, you may have to remove your videodrivers in the current kernel, then reinstall with the new one.

Or you can wait a bit until its released for jaunty, as its annoying perhaps, but not exactly critical.

---

### Post by xiodene on 2009-09-05
Thnks so much mate, i think il wait untill its released properly. as you say, its not critical.

Thankyou!

---

### Post by Kryzzalid on 2009-09-05
Hi, I have about the same problem since i reinstalled ubuntu 9.04 (64-bit). When i shut down my laptop (pavilion zv6150ea) the screen goes black with a part of a log written i believe. And to shut it down completely i have to press the power button. Here is what is an example of it is written:

[ 1041.872010] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 1041.872010] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 1041.872010] Process usplash (pid: 19551, threadinfo ffff8800764a6000, task ffff8800690facc0)
[ 1041.872010] Stack:
[ 1041.872010]  ffffe20001660d80 0000000000400000 ffff8800761bb7f8 000ffffffffc0000
[ 1041.872010]  ffffffffc0000000 0000000040400000 0000000000400000 ffff88006e57d218
[ 1041.872010]  ffff8800764a7da8 ffffffff802396aa ffff88006e57dbd0 ffff8800682389c0
[ 1041.872010] Call Trace:
[ 1041.872010]  [<ffffffff802396aa>] phys_mem_access_prot_allowed+0xba/0x170
[ 1041.872010]  [<ffffffff80489ed7>] mmap_mem+0x87/0x150
[ 1041.872010]  [<ffffffff802cb12d>] mmap_region+0x23d/0x630
[ 1041.872010]  [<ffffffff802cb9f4>] do_mmap_pgoff+0x3e4/0x410
[ 1041.872010]  [<ffffffff802177d6>] sys_mmap+0x106/0x130
[ 1041.872010]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
[ 1041.872010] Code: 00 49 89 d0 48 8b 55 c8 4c 89 ee 48 c7 c7 d8 fd 7e 80 31 c0 45 31 e4 e8 4e 2c 46 00 e9 68 fc ff ff 66 2e 0f 1f 84 00 00 00 00 00 <0f> 0b eb fe 0f 1f 40 00 48 8b 7d d0 4c 89 fa 48 89 de e8 f9 f7 
[ 1041.872010] RIP  [<ffffffff80239290>] reserve_memtype+0x3f0/0x640
[ 1041.872010]  RSP <ffff8800764a7d18>
[ 1041.876640] ---[ end trace a4f0c8a3d4a57af1 ]---

It's a part of the kern.log and the values change. Any opinion on that?

---

### Post by P4man on 2009-09-05
im sorry, thats Chinese to me :D perhaps you can attach the full log and maybe there is something in there that makes sense to a mere human (and not a  kernel developer :) )

---

### Post by Kryzzalid on 2009-09-06
I don't use ubuntu for that long. So, i don't have any idea of what it could mean. But here is the whole kern.log from boot to shutdown:

Sep  5 21:58:46 Akatsuki kernel: Inspecting /boot/System.map-2.6.28-15-generic
Sep  5 21:58:46 Akatsuki kernel: Cannot find map file.
Sep  5 21:58:46 Akatsuki kernel: Loaded 57337 symbols from 59 modules.
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] Initializing cgroup subsys cpu
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] Linux version 2.6.28-15-generic (buildd@yellow) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 (Ubuntu 2.6.28-15.49-generic)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] Command line: root=UUID=2a90dfc7-e381-4528-a3df-561b2443b726 ro quiet splash 
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] KERNEL supported cpus:
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   Intel GenuineIntel
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   AMD AuthenticAMD
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   Centaur CentaurHauls
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] BIOS-provided physical RAM map:
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000077ef0000 (usable)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  BIOS-e820: 0000000077ef0000 - 0000000077eff000 (ACPI data)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  BIOS-e820: 0000000077eff000 - 0000000077f00000 (ACPI NVS)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  BIOS-e820: 0000000077f00000 - 0000000080000000 (reserved)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] DMI present.
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] last_pfn = 0x77ef0 max_arch_pfn = 0x3ffffffff
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] Scanning 2 areas for low memory corruption
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] modified physical RAM map:
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  modified: 0000000000006000 - 0000000000008000 (usable)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  modified: 0000000000008000 - 0000000000010000 (reserved)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  modified: 00000000000d0000 - 0000000000100000 (reserved)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  modified: 0000000000100000 - 0000000077ef0000 (usable)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  modified: 0000000077ef0000 - 0000000077eff000 (ACPI data)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  modified: 0000000077eff000 - 0000000077f00000 (ACPI NVS)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  modified: 0000000077f00000 - 0000000080000000 (reserved)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] init_memory_mapping: 0000000000000000-0000000077ef0000
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  0000000000 - 0077e00000 page 2M
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  0077e00000 - 0077ef0000 page 4k
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] kernel direct mapping tables up to 77ef0000 @ 10000-14000
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] last_map_addr: 77ef0000 end: 77ef0000
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] RAMDISK: 37859000 - 37fefbd6
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] ACPI: RSDP 000F7DF0, 0014 (r0 PTLTD )
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] ACPI: RSDT 77EF9524, 0034 (r1 PTLTD    RSDT    6040000  LTP        0)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] ACPI: FACP 77EFEE31, 0074 (r1 HP     Piranha   6040000 ATI     F4240)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] ACPI: DSDT 77EF9558, 58D9 (r1     HP     3085  6040000 MSFT  100000E)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] ACPI: FACS 77EFFFC0, 0040
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] ACPI: MCFG 77EFEEA5, 003C (r1 ATI    Piranha   6040000 LOHR       5F)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] ACPI: SSDT 77EFEEE1, 00CF (r1 PTLTD  POWERNOW  6040000  LTP        1)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] ACPI: APIC 77EFEFB0, 0050 (r1 PTLTD  ^I APIC    6040000  LTP        0)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] (6 early reservations) ==> bootmem [0000000000 - 0077ef0000]
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   #2 [0000200000 - 0000b7bbb0]    TEXT DATA BSS ==> [0000200000 - 0000b7bbb0]
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   #3 [0037859000 - 0037fefbd6]          RAMDISK ==> [0037859000 - 0037fefbd6]
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] found SMP MP-table at [ffff8800000f7e20] 000f7e20
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]  [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] Zone PFN ranges:
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] Movable zone start PFN for each node
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] early_node_map[4] active PFN ranges
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]     0: 0x00000006 -> 0x00000008
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]     0: 0x00000010 -> 0x00000092
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]     0: 0x00000100 -> 0x00077ef0
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] On node 0 totalpages: 491125
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   DMA zone: 2530 pages reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   DMA zone: 1387 pages, LIFO batch:0
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   DMA32 zone: 6661 pages used for memmap
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   DMA32 zone: 480491 pages, LIFO batch:31
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Sep  5 21:58:46 Akatsuki kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] SB4X0 revision 0x10
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] Ignoring ACPI timer override.
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 0, address 0xfec00000, GSI 0-23
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] PM: Registered nosave memory: 0000000000008000 - 0000000000010000
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 481878
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] Kernel command line: root=UUID=2a90dfc7-e381-4528-a3df-561b2443b726 ro quiet splash 
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] Initializing CPU#0
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] Fast TSC calibration using PIT
Sep  5 21:58:46 Akatsuki kernel: [    0.000000] Detected 1989.599 MHz processor.
Sep  5 21:58:46 Akatsuki kernel: [    0.004000] Console: colour VGA+ 80x25
Sep  5 21:58:46 Akatsuki kernel: [    0.004000] console [tty0] enabled
Sep  5 21:58:46 Akatsuki kernel: [    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Sep  5 21:58:46 Akatsuki kernel: [    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Sep  5 21:58:46 Akatsuki kernel: [    0.004000] allocated 19660800 bytes of page_cgroup
Sep  5 21:58:46 Akatsuki kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
Sep  5 21:58:46 Akatsuki kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
Sep  5 21:58:46 Akatsuki kernel: [    0.004000] Checking aperture...
Sep  5 21:58:46 Akatsuki kernel: [    0.004000] No AGP bridge found
Sep  5 21:58:46 Akatsuki kernel: [    0.004000] Node 0: aperture @ 7586000000 size 32 MB
Sep  5 21:58:46 Akatsuki kernel: [    0.004000] Aperture beyond 4GB. Ignoring.
Sep  5 21:58:46 Akatsuki kernel: [    0.004000] Memory: 1895168k/1964992k available (4749k kernel code, 492k absent, 68648k reserved, 2523k data, 532k init)
Sep  5 21:58:46 Akatsuki kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Sep  5 21:58:46 Akatsuki kernel: [    0.004015] Calibrating delay loop (skipped), value calculated using timer frequency.. 3979.19 BogoMIPS (lpj=7958396)
Sep  5 21:58:46 Akatsuki kernel: [    0.004046] Security Framework initialized
Sep  5 21:58:46 Akatsuki kernel: [    0.004062] SELinux:  Disabled at boot.
Sep  5 21:58:46 Akatsuki kernel: [    0.004087] AppArmor: AppArmor initialized
Sep  5 21:58:46 Akatsuki kernel: [    0.004097] Mount-cache hash table entries: 256
Sep  5 21:58:46 Akatsuki kernel: [    0.004297] Initializing cgroup subsys ns
Sep  5 21:58:46 Akatsuki kernel: [    0.004301] Initializing cgroup subsys cpuacct
Sep  5 21:58:46 Akatsuki kernel: [    0.004304] Initializing cgroup subsys memory
Sep  5 21:58:46 Akatsuki kernel: [    0.004308] Initializing cgroup subsys freezer
Sep  5 21:58:46 Akatsuki kernel: [    0.004325] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep  5 21:58:46 Akatsuki kernel: [    0.004327] CPU: L2 Cache: 512K (64 bytes/line)
Sep  5 21:58:46 Akatsuki kernel: [    0.004329] tseg: 0077f00000
Sep  5 21:58:46 Akatsuki kernel: [    0.004348] SMP alternatives: switching to UP code
Sep  5 21:58:46 Akatsuki kernel: [    0.123881] Freeing SMP alternatives: 37k freed
Sep  5 21:58:46 Akatsuki kernel: [    0.124720] ACPI: Core revision 20080926
Sep  5 21:58:46 Akatsuki kernel: [    0.126850] ACPI: Checking initramfs for custom DSDT
Sep  5 21:58:46 Akatsuki kernel: [    0.420064] Setting APIC routing to flat
Sep  5 21:58:46 Akatsuki kernel: [    0.420560] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
Sep  5 21:58:46 Akatsuki kernel: [    0.462872] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 00
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] Brought up 1 CPUs
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] Total of 1 processors activated (3979.19 BogoMIPS).
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] CPU0 attaching NULL sched-domain.
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] net_namespace: 1400 bytes
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] Booting paravirtualized kernel on bare hardware
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] Time: 18:58:24  Date: 09/05/09
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] regulator: core version 0.5
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] NET: Registered protocol family 16
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] node 0 link 0: io port [1000, fffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] TOM: 0000000080000000 aka 2048M
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] node 0 link 0: mmio [d0000000, fff8ffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] node 0 link 0: mmio [c0000000, cfffffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] node 0 link 0: mmio [a0000, bffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] node 0 link 0: mmio [80000000, bfffffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] bus: [00,ff] on node 0 link 0
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] bus: 00 index 0 io port: [0, ffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] bus: 00 index 1 mmio: [80000000, fcffffffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] bus: 00 index 2 mmio: [a0000, bffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] ACPI: bus type pci registered
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Sep  5 21:58:46 Akatsuki kernel: [    0.464001] PCI: MCFG area at e0000000 reserved in E820
Sep  5 21:58:46 Akatsuki kernel: [    0.475759] PCI: Using MMCONFIG at e0000000 - efffffff
Sep  5 21:58:46 Akatsuki kernel: [    0.475762] PCI: Using configuration type 1 for base access
Sep  5 21:58:46 Akatsuki kernel: [    0.476986] ACPI: EC: Look up EC in DSDT
Sep  5 21:58:46 Akatsuki kernel: [    0.479562] ACPI: Interpreter enabled
Sep  5 21:58:46 Akatsuki kernel: [    0.479565] ACPI: (supports S0 S3 S4 S5)
Sep  5 21:58:46 Akatsuki kernel: [    0.479581] ACPI: Using IOAPIC for interrupt routing
Sep  5 21:58:46 Akatsuki kernel: [    0.482559] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep  5 21:58:46 Akatsuki kernel: [    0.552426] ACPI: EC: GPE = 0x1a, I/O: command/status = 0x66, data = 0x62
Sep  5 21:58:46 Akatsuki kernel: [    0.552428] ACPI: EC: driver started in interrupt mode
Sep  5 21:58:46 Akatsuki kernel: [    0.552518] ACPI: No dock devices found.
Sep  5 21:58:46 Akatsuki kernel: [    0.552526] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep  5 21:58:46 Akatsuki kernel: [    0.552610] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
Sep  5 21:58:46 Akatsuki kernel: [    0.552613] pci 0000:00:04.0: PME# disabled
Sep  5 21:58:46 Akatsuki kernel: [    0.552676] pci 0000:00:13.0: reg 10 32bit mmio: [0xb0000000-0xb0000fff]
Sep  5 21:58:46 Akatsuki kernel: [    0.552766] pci 0000:00:13.1: reg 10 32bit mmio: [0xb0001000-0xb0001fff]
Sep  5 21:58:46 Akatsuki kernel: [    0.552863] pci 0000:00:13.2: reg 10 32bit mmio: [0xb0002000-0xb0002fff]
Sep  5 21:58:46 Akatsuki kernel: [    0.552911] pci 0000:00:13.2: supports D1 D2
Sep  5 21:58:46 Akatsuki kernel: [    0.552912] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Sep  5 21:58:46 Akatsuki kernel: [    0.552917] pci 0000:00:13.2: PME# disabled
Sep  5 21:58:46 Akatsuki kernel: [    0.552968] pci 0000:00:14.0: reg 10 io port: [0x8400-0x840f]
Sep  5 21:58:46 Akatsuki kernel: [    0.552976] pci 0000:00:14.0: reg 14 32bit mmio: [0xb0003000-0xb00033ff]
Sep  5 21:58:46 Akatsuki kernel: [    0.553010] HPET not enabled in BIOS. You might try hpet=force boot option
Sep  5 21:58:46 Akatsuki kernel: [    0.553059] pci 0000:00:14.1: reg 10 io port: [0x1f0-0x1f7]
Sep  5 21:58:46 Akatsuki kernel: [    0.553067] pci 0000:00:14.1: reg 14 io port: [0x3f4-0x3f7]
Sep  5 21:58:46 Akatsuki kernel: [    0.553074] pci 0000:00:14.1: reg 18 io port: [0x170-0x177]
Sep  5 21:58:46 Akatsuki kernel: [    0.553082] pci 0000:00:14.1: reg 1c io port: [0x374-0x377]
Sep  5 21:58:46 Akatsuki kernel: [    0.553090] pci 0000:00:14.1: reg 20 io port: [0x8410-0x841f]
Sep  5 21:58:46 Akatsuki kernel: [    0.553251] pci 0000:00:14.5: reg 10 32bit mmio: [0xb0003400-0xb00034ff]
Sep  5 21:58:46 Akatsuki kernel: [    0.553338] pci 0000:00:14.6: reg 10 32bit mmio: [0xb0003800-0xb00038ff]
Sep  5 21:58:46 Akatsuki kernel: [    0.553465] pci 0000:01:05.0: reg 10 32bit mmio: [0xc0000000-0xcfffffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.553468] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
Sep  5 21:58:46 Akatsuki kernel: [    0.553472] pci 0000:01:05.0: reg 18 32bit mmio: [0xb0100000-0xb010ffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.553479] pci 0000:01:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.553484] pci 0000:01:05.0: supports D1 D2
Sep  5 21:58:46 Akatsuki kernel: [    0.553496] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
Sep  5 21:58:46 Akatsuki kernel: [    0.553499] pci 0000:00:01.0: bridge 32bit mmio: [0xb0100000-0xb01fffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.553502] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.556050] pci 0000:00:04.0: bridge io port: [0x00-0xfff]
Sep  5 21:58:46 Akatsuki kernel: [    0.556053] pci 0000:00:04.0: bridge 32bit mmio: [0x000000-0x0fffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.556106] pci 0000:03:00.0: reg 10 32bit mmio: [0xb0208000-0xb02087ff]
Sep  5 21:58:46 Akatsuki kernel: [    0.556116] pci 0000:03:00.0: reg 14 32bit mmio: [0xb0200000-0xb0203fff]
Sep  5 21:58:46 Akatsuki kernel: [    0.556169] pci 0000:03:00.0: supports D1 D2
Sep  5 21:58:46 Akatsuki kernel: [    0.556170] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
Sep  5 21:58:46 Akatsuki kernel: [    0.556176] pci 0000:03:00.0: PME# disabled
Sep  5 21:58:46 Akatsuki kernel: [    0.556212] pci 0000:03:02.0: reg 10 32bit mmio: [0xb0204000-0xb0205fff]
Sep  5 21:58:46 Akatsuki kernel: [    0.556312] pci 0000:03:04.0: reg 10 32bit mmio: [0xb0209000-0xb0209fff]
Sep  5 21:58:46 Akatsuki kernel: [    0.556326] pci 0000:03:04.0: supports D1 D2
Sep  5 21:58:46 Akatsuki kernel: [    0.556328] pci 0000:03:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep  5 21:58:46 Akatsuki kernel: [    0.556334] pci 0000:03:04.0: PME# disabled
Sep  5 21:58:46 Akatsuki kernel: [    0.556391] pci 0000:03:04.3: reg 10 32bit mmio: [0xb0206000-0xb0207fff]
Sep  5 21:58:46 Akatsuki kernel: [    0.556449] pci 0000:03:04.3: supports D1 D2
Sep  5 21:58:46 Akatsuki kernel: [    0.556451] pci 0000:03:04.3: PME# supported from D0 D1 D2 D3hot
Sep  5 21:58:46 Akatsuki kernel: [    0.556456] pci 0000:03:04.3: PME# disabled
Sep  5 21:58:46 Akatsuki kernel: [    0.556509] pci 0000:03:04.4: reg 10 32bit mmio: [0xb020a000-0xb020a0ff]
Sep  5 21:58:46 Akatsuki kernel: [    0.556518] pci 0000:03:04.4: reg 14 32bit mmio: [0xb0208c00-0xb0208cff]
Sep  5 21:58:46 Akatsuki kernel: [    0.556528] pci 0000:03:04.4: reg 18 32bit mmio: [0xb0208800-0xb02088ff]
Sep  5 21:58:46 Akatsuki kernel: [    0.556571] pci 0000:03:04.4: supports D1 D2
Sep  5 21:58:46 Akatsuki kernel: [    0.556573] pci 0000:03:04.4: PME# supported from D0 D1 D2 D3hot
Sep  5 21:58:46 Akatsuki kernel: [    0.556578] pci 0000:03:04.4: PME# disabled
Sep  5 21:58:46 Akatsuki kernel: [    0.556638] pci 0000:03:06.0: reg 10 io port: [0xa000-0xa0ff]
Sep  5 21:58:46 Akatsuki kernel: [    0.556648] pci 0000:03:06.0: reg 14 32bit mmio: [0xb020a400-0xb020a4ff]
Sep  5 21:58:46 Akatsuki kernel: [    0.556698] pci 0000:03:06.0: supports D1 D2
Sep  5 21:58:46 Akatsuki kernel: [    0.556700] pci 0000:03:06.0: PME# supported from D1 D2 D3hot D3cold
Sep  5 21:58:46 Akatsuki kernel: [    0.556705] pci 0000:03:06.0: PME# disabled
Sep  5 21:58:46 Akatsuki kernel: [    0.556762] pci 0000:00:14.4: transparent bridge
Sep  5 21:58:46 Akatsuki kernel: [    0.556769] pci 0000:00:14.4: bridge io port: [0xa000-0xafff]
Sep  5 21:58:46 Akatsuki kernel: [    0.556774] pci 0000:00:14.4: bridge 32bit mmio: [0xb0200000-0xb02fffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.556813] bus 00 -> node 0
Sep  5 21:58:46 Akatsuki kernel: [    0.556818] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Sep  5 21:58:46 Akatsuki kernel: [    0.556967] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
Sep  5 21:58:46 Akatsuki kernel: [    0.557081] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Sep  5 21:58:46 Akatsuki kernel: [    0.557244] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Sep  5 21:58:46 Akatsuki kernel: [    0.558883] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
Sep  5 21:58:46 Akatsuki kernel: [    0.558990] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
Sep  5 21:58:46 Akatsuki kernel: [    0.559097] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
Sep  5 21:58:46 Akatsuki kernel: [    0.560033] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
Sep  5 21:58:46 Akatsuki kernel: [    0.560138] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
Sep  5 21:58:46 Akatsuki kernel: [    0.560243] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
Sep  5 21:58:46 Akatsuki kernel: [    0.560349] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
Sep  5 21:58:46 Akatsuki kernel: [    0.560454] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
Sep  5 21:58:46 Akatsuki kernel: [    0.560576] ACPI: WMI: Mapper loaded
Sep  5 21:58:46 Akatsuki kernel: [    0.560803] SCSI subsystem initialized
Sep  5 21:58:46 Akatsuki kernel: [    0.560847] libata version 3.00 loaded.
Sep  5 21:58:46 Akatsuki kernel: [    0.560894] usbcore: registered new interface driver usbfs
Sep  5 21:58:46 Akatsuki kernel: [    0.560910] usbcore: registered new interface driver hub
Sep  5 21:58:46 Akatsuki kernel: [    0.560942] usbcore: registered new device driver usb
Sep  5 21:58:46 Akatsuki kernel: [    0.561051] PCI: Using ACPI for IRQ routing
Sep  5 21:58:46 Akatsuki kernel: [    0.561057] pci 0000:00:04.0: BAR 7: can't allocate resource
Sep  5 21:58:46 Akatsuki kernel: [    0.561058] pci 0000:00:04.0: BAR 8: can't allocate resource
Sep  5 21:58:46 Akatsuki kernel: [    0.572009] Bluetooth: Core ver 2.13
Sep  5 21:58:46 Akatsuki kernel: [    0.572059] NET: Registered protocol family 31
Sep  5 21:58:46 Akatsuki kernel: [    0.572061] Bluetooth: HCI device and connection manager initialized
Sep  5 21:58:46 Akatsuki kernel: [    0.572064] Bluetooth: HCI socket layer initialized
Sep  5 21:58:46 Akatsuki kernel: [    0.572066] NET: Registered protocol family 8
Sep  5 21:58:46 Akatsuki kernel: [    0.572068] NET: Registered protocol family 20
Sep  5 21:58:46 Akatsuki kernel: [    0.572079] NetLabel: Initializing
Sep  5 21:58:46 Akatsuki kernel: [    0.572080] NetLabel:  domain hash size = 128
Sep  5 21:58:46 Akatsuki kernel: [    0.572082] NetLabel:  protocols = UNLABELED CIPSOv4
Sep  5 21:58:46 Akatsuki kernel: [    0.572099] NetLabel:  unlabeled traffic allowed by default
Sep  5 21:58:46 Akatsuki kernel: [    0.572334] AppArmor: AppArmor Filesystem Enabled
Sep  5 21:58:46 Akatsuki kernel: [    0.584007] pnp: PnP ACPI init
Sep  5 21:58:46 Akatsuki kernel: [    0.584019] ACPI: bus type pnp registered
Sep  5 21:58:46 Akatsuki kernel: [    0.585543] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:01:05.0 BAR 6 (0x0-0x1ffff), disabling
Sep  5 21:58:46 Akatsuki kernel: [    0.633166] pnp: PnP ACPI: found 10 devices
Sep  5 21:58:46 Akatsuki kernel: [    0.633168] ACPI: ACPI bus type pnp unregistered
Sep  5 21:58:46 Akatsuki kernel: [    0.633177] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633180] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633182] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633189] system 00:08: ioport range 0x1080-0x1080 has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633191] system 00:08: ioport range 0x220-0x22f has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633194] system 00:08: ioport range 0x40b-0x40b has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633196] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633198] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633200] system 00:08: ioport range 0x530-0x537 has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633203] system 00:08: ioport range 0x870-0x87f has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633205] system 00:08: ioport range 0xc00-0xc01 has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633207] system 00:08: ioport range 0xc14-0xc14 has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633209] system 00:08: ioport range 0xc50-0xc52 has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633217] system 00:08: ioport range 0xc6c-0xc6c has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633219] system 00:08: ioport range 0xc6f-0xc6f has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633221] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633224] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633226] system 00:08: ioport range 0xcd8-0xcdf has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633228] system 00:08: ioport range 0x8000-0x805f has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633231] system 00:08: ioport range 0xf40-0xf47 has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633233] system 00:08: ioport range 0x280-0x293 has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633238] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633240] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.633243] system 00:09: iomem range 0xe0000000-0xe03fffff has been reserved
Sep  5 21:58:46 Akatsuki kernel: [    0.637933] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Sep  5 21:58:46 Akatsuki kernel: [    0.637935] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
Sep  5 21:58:46 Akatsuki kernel: [    0.637939] pci 0000:00:01.0:   MEM window: 0xb0100000-0xb01fffff
Sep  5 21:58:46 Akatsuki kernel: [    0.637942] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
Sep  5 21:58:46 Akatsuki kernel: [    0.637945] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
Sep  5 21:58:46 Akatsuki kernel: [    0.637947] pci 0000:00:04.0:   IO window: disabled
Sep  5 21:58:46 Akatsuki kernel: [    0.637949] pci 0000:00:04.0:   MEM window: disabled
Sep  5 21:58:46 Akatsuki kernel: [    0.637951] pci 0000:00:04.0:   PREFETCH window: disabled
Sep  5 21:58:46 Akatsuki kernel: [    0.637957] pci 0000:03:04.0: CardBus bridge, secondary bus 0000:04
Sep  5 21:58:46 Akatsuki kernel: [    0.637959] pci 0000:03:04.0:   IO window: 0x00a400-0x00a4ff
Sep  5 21:58:46 Akatsuki kernel: [    0.637964] pci 0000:03:04.0:   IO window: 0x00a800-0x00a8ff
Sep  5 21:58:46 Akatsuki kernel: [    0.637970] pci 0000:03:04.0:   PREFETCH window: 0x88000000-0x8bffffff
Sep  5 21:58:46 Akatsuki kernel: [    0.637975] pci 0000:03:04.0:   MEM window: 0x8c000000-0x8fffffff
Sep  5 21:58:46 Akatsuki kernel: [    0.637981] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
Sep  5 21:58:46 Akatsuki kernel: [    0.637984] pci 0000:00:14.4:   IO window: 0xa000-0xafff
Sep  5 21:58:46 Akatsuki kernel: [    0.637991] pci 0000:00:14.4:   MEM window: 0xb0200000-0xb02fffff
Sep  5 21:58:46 Akatsuki kernel: [    0.637995] pci 0000:00:14.4:   PREFETCH window: 0x00000088000000-0x0000008bffffff
Sep  5 21:58:46 Akatsuki kernel: [    0.638012] pci 0000:00:04.0: setting latency timer to 64
Sep  5 21:58:46 Akatsuki kernel: [    0.638030] pci 0000:03:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Sep  5 21:58:46 Akatsuki kernel: [    0.638038] bus: 00 index 0 io port: [0x00-0xffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.638040] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.638042] bus: 01 index 0 io port: [0x9000-0x9fff]
Sep  5 21:58:46 Akatsuki kernel: [    0.638043] bus: 01 index 1 mmio: [0xb0100000-0xb01fffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.638045] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.638047] bus: 01 index 3 mmio: [0x0-0x0]
Sep  5 21:58:46 Akatsuki kernel: [    0.638049] bus: 02 index 0 mmio: [0x0-0xfff]
Sep  5 21:58:46 Akatsuki kernel: [    0.638050] bus: 02 index 1 mmio: [0x0-0xfffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.638052] bus: 02 index 2 mmio: [0x0-0x0]
Sep  5 21:58:46 Akatsuki kernel: [    0.638053] bus: 02 index 3 mmio: [0x0-0x0]
Sep  5 21:58:46 Akatsuki kernel: [    0.638055] bus: 03 index 0 io port: [0xa000-0xafff]
Sep  5 21:58:46 Akatsuki kernel: [    0.638057] bus: 03 index 1 mmio: [0xb0200000-0xb02fffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.638059] bus: 03 index 2 mmio: [0x88000000-0x8bffffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.638061] bus: 03 index 3 io port: [0x00-0xffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.638062] bus: 03 index 4 mmio: [0x000000-0xffffffffffffffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.638064] bus: 04 index 0 io port: [0xa400-0xa4ff]
Sep  5 21:58:46 Akatsuki kernel: [    0.638066] bus: 04 index 1 io port: [0xa800-0xa8ff]
Sep  5 21:58:46 Akatsuki kernel: [    0.638068] bus: 04 index 2 mmio: [0x88000000-0x8bffffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.638070] bus: 04 index 3 mmio: [0x8c000000-0x8fffffff]
Sep  5 21:58:46 Akatsuki kernel: [    0.638081] NET: Registered protocol family 2
Sep  5 21:58:46 Akatsuki kernel: [    0.672070] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Sep  5 21:58:46 Akatsuki kernel: [    0.672881] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Sep  5 21:58:46 Akatsuki kernel: [    0.677867] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Sep  5 21:58:46 Akatsuki kernel: [    0.679103] TCP: Hash tables configured (established 262144 bind 65536)
Sep  5 21:58:46 Akatsuki kernel: [    0.679107] TCP reno registered
Sep  5 21:58:46 Akatsuki kernel: [    0.688131] NET: Registered protocol family 1
Sep  5 21:58:46 Akatsuki kernel: [    0.688276] checking if image is initramfs... it is
Sep  5 21:58:46 Akatsuki kernel: [    1.140102] Switched to high resolution mode on CPU 0
Sep  5 21:58:46 Akatsuki kernel: [    1.299538] Freeing initrd memory: 7770k freed
Sep  5 21:58:46 Akatsuki kernel: [    1.309034] audit: initializing netlink socket (disabled)
Sep  5 21:58:46 Akatsuki kernel: [    1.309053] type=2000 audit(1252177103.308:1): initialized
Sep  5 21:58:46 Akatsuki kernel: [    1.317256] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Sep  5 21:58:46 Akatsuki kernel: [    1.318438] VFS: Disk quotas dquot_6.5.1
Sep  5 21:58:46 Akatsuki kernel: [    1.318490] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Sep  5 21:58:46 Akatsuki kernel: [    1.319036] fuse init (API version 7.10)
Sep  5 21:58:46 Akatsuki kernel: [    1.319108] msgmni has been set to 3718
Sep  5 21:58:46 Akatsuki kernel: [    1.319281] alg: No test for stdrng (krng)
Sep  5 21:58:46 Akatsuki kernel: [    1.319292] io scheduler noop registered
Sep  5 21:58:46 Akatsuki kernel: [    1.319293] io scheduler anticipatory registered
Sep  5 21:58:46 Akatsuki kernel: [    1.319295] io scheduler deadline registered
Sep  5 21:58:46 Akatsuki kernel: [    1.319332] io scheduler cfq registered (default)
Sep  5 21:58:46 Akatsuki kernel: [    1.319340] pci 0000:00:00.0: MSI quirk detected; MSI disabled
Sep  5 21:58:46 Akatsuki kernel: [    1.319410] pci 0000:01:05.0: Boot video device
Sep  5 21:58:46 Akatsuki kernel: [    1.319496] pcieport-driver 0000:00:04.0: setting latency timer to 64
Sep  5 21:58:46 Akatsuki kernel: [    1.319514] pcieport-driver 0000:00:04.0: found MSI capability
Sep  5 21:58:46 Akatsuki kernel: [    1.319518] pci_express 0000:00:04.0:pcie00: allocate port service
Sep  5 21:58:46 Akatsuki kernel: [    1.319530] pci_express 0000:00:04.0:pcie01: allocate port service
Sep  5 21:58:46 Akatsuki kernel: [    1.369176] aer 0000:00:04.0:pcie01: AER service couldn't init device: no _OSC support
Sep  5 21:58:46 Akatsuki kernel: [    1.369187] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  5 21:58:46 Akatsuki kernel: [    1.369195] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Sep  5 21:58:46 Akatsuki kernel: [    1.375246] ACPI: AC Adapter [ACAD] (on-line)
Sep  5 21:58:46 Akatsuki kernel: [    1.632083] ACPI: Battery Slot [BAT1] (battery present)
Sep  5 21:58:46 Akatsuki kernel: [    1.632153] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Sep  5 21:58:46 Akatsuki kernel: [    1.632156] ACPI: Power Button (FF) [PWRF]
Sep  5 21:58:46 Akatsuki kernel: [    1.632198] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Sep  5 21:58:46 Akatsuki kernel: [    1.632249] ACPI: Lid Switch [LID]
Sep  5 21:58:46 Akatsuki kernel: [    1.632293] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
Sep  5 21:58:46 Akatsuki kernel: [    1.632295] ACPI: Power Button (CM) [PWRB]
Sep  5 21:58:46 Akatsuki kernel: [    1.632470] processor ACPI_CPU:00: registered as cooling_device0
Sep  5 21:58:46 Akatsuki kernel: [    1.632473] ACPI: Processor [CPU0] (supports 8 throttling states)
Sep  5 21:58:46 Akatsuki kernel: [    1.685099] thermal LNXTHERM:01: registered as thermal_zone0
Sep  5 21:58:46 Akatsuki kernel: [    1.701024] ACPI: Thermal Zone [THRM] (44 C)
Sep  5 21:58:46 Akatsuki kernel: [    1.724167] Linux agpgart interface v0.103
Sep  5 21:58:46 Akatsuki kernel: [    1.724176] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Sep  5 21:58:46 Akatsuki kernel: [    1.724435] serial 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Sep  5 21:58:46 Akatsuki kernel: [    1.724443] serial 0000:00:14.6: PCI INT B disabled
Sep  5 21:58:46 Akatsuki kernel: [    1.725097] brd: module loaded
Sep  5 21:58:46 Akatsuki kernel: [    1.725402] loop: module loaded
Sep  5 21:58:46 Akatsuki kernel: [    1.725473] Fixed MDIO Bus: probed
Sep  5 21:58:46 Akatsuki kernel: [    1.725479] PPP generic driver version 2.4.2
Sep  5 21:58:46 Akatsuki kernel: [    1.725552] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Sep  5 21:58:46 Akatsuki kernel: [    1.725582] Driver 'sd' needs updating - please use bus_type methods
Sep  5 21:58:46 Akatsuki kernel: [    1.725590] Driver 'sr' needs updating - please use bus_type methods
Sep  5 21:58:46 Akatsuki kernel: [    1.725830] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep  5 21:58:46 Akatsuki kernel: [    1.725887] pata_atiixp 0000:00:14.1: setting latency timer to 64
Sep  5 21:58:46 Akatsuki kernel: [    1.726023] scsi0 : pata_atiixp
Sep  5 21:58:46 Akatsuki kernel: [    1.726143] scsi1 : pata_atiixp
Sep  5 21:58:46 Akatsuki kernel: [    1.727372] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
Sep  5 21:58:46 Akatsuki kernel: [    1.727375] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
Sep  5 21:58:46 Akatsuki kernel: [    1.888564] ata1.00: ATA-6: ST9808210A, 3.02, max UDMA/100
Sep  5 21:58:46 Akatsuki kernel: [    1.888566] ata1.00: 156301488 sectors, multi 16: LBA48 
Sep  5 21:58:46 Akatsuki kernel: [    1.904507] ata1.00: configured for UDMA/100
Sep  5 21:58:46 Akatsuki kernel: [    2.084589] ata2.00: ATAPI: TOSHIBA CD/DVDW SD-R6472, TU51, max UDMA/33
Sep  5 21:58:46 Akatsuki kernel: [    2.100579] ata2.00: configured for UDMA/33
Sep  5 21:58:46 Akatsuki kernel: [    2.101160] isa bounce pool size: 16 pages
Sep  5 21:58:46 Akatsuki kernel: [    2.101255] scsi 0:0:0:0: Direct-Access     ATA      ST9808210A       3.02 PQ: 0 ANSI: 5
Sep  5 21:58:46 Akatsuki kernel: [    2.101347] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
Sep  5 21:58:46 Akatsuki kernel: [    2.101364] sd 0:0:0:0: [sda] Write Protect is off
Sep  5 21:58:46 Akatsuki kernel: [    2.101366] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep  5 21:58:46 Akatsuki kernel: [    2.101389] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  5 21:58:46 Akatsuki kernel: [    2.101468] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
Sep  5 21:58:46 Akatsuki kernel: [    2.101481] sd 0:0:0:0: [sda] Write Protect is off
Sep  5 21:58:46 Akatsuki kernel: [    2.101483] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep  5 21:58:46 Akatsuki kernel: [    2.101505] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  5 21:58:46 Akatsuki kernel: [    2.101509]  sda: sda1 sda2 < sda5 sda6 >
Sep  5 21:58:46 Akatsuki kernel: [    2.134974] sd 0:0:0:0: [sda] Attached SCSI disk
Sep  5 21:58:46 Akatsuki kernel: [    2.135030] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep  5 21:58:46 Akatsuki kernel: [    2.139092] scsi 1:0:0:0: CD-ROM            TOSHIBA  CD/DVDW SD-R6472 TU51 PQ: 0 ANSI: 5
Sep  5 21:58:46 Akatsuki kernel: [    2.145317] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Sep  5 21:58:46 Akatsuki kernel: [    2.145320] Uniform CD-ROM driver Revision: 3.20
Sep  5 21:58:46 Akatsuki kernel: [    2.145406] sr 1:0:0:0: Attached scsi CD-ROM sr0
Sep  5 21:58:46 Akatsuki kernel: [    2.145437] sr 1:0:0:0: Attached scsi generic sg1 type 5
Sep  5 21:58:46 Akatsuki kernel: [    2.145803] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Sep  5 21:58:46 Akatsuki kernel: [    2.145832] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Sep  5 21:58:46 Akatsuki kernel: [    2.145865] ehci_hcd 0000:00:13.2: EHCI Host Controller
Sep  5 21:58:46 Akatsuki kernel: [    2.145928] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
Sep  5 21:58:46 Akatsuki kernel: [    2.146008] ehci_hcd 0000:00:13.2: irq 19, io mem 0xb0002000
Sep  5 21:58:46 Akatsuki kernel: [    2.156007] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Sep  5 21:58:46 Akatsuki kernel: [    2.156088] usb usb1: configuration #1 chosen from 1 choice
Sep  5 21:58:46 Akatsuki kernel: [    2.156125] hub 1-0:1.0: USB hub found
Sep  5 21:58:46 Akatsuki kernel: [    2.156135] hub 1-0:1.0: 8 ports detected
Sep  5 21:58:46 Akatsuki kernel: [    2.156251] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep  5 21:58:46 Akatsuki kernel: [    2.156263] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Sep  5 21:58:46 Akatsuki kernel: [    2.156274] ohci_hcd 0000:00:13.0: OHCI Host Controller
Sep  5 21:58:46 Akatsuki kernel: [    2.156318] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
Sep  5 21:58:46 Akatsuki kernel: [    2.156336] ohci_hcd 0000:00:13.0: irq 19, io mem 0xb0000000
Sep  5 21:58:46 Akatsuki kernel: [    2.216052] usb usb2: configuration #1 chosen from 1 choice
Sep  5 21:58:46 Akatsuki kernel: [    2.216072] hub 2-0:1.0: USB hub found
Sep  5 21:58:46 Akatsuki kernel: [    2.216084] hub 2-0:1.0: 4 ports detected
Sep  5 21:58:46 Akatsuki kernel: [    2.216167] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Sep  5 21:58:46 Akatsuki kernel: [    2.216181] ohci_hcd 0000:00:13.1: OHCI Host Controller
Sep  5 21:58:46 Akatsuki kernel: [    2.216220] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
Sep  5 21:58:46 Akatsuki kernel: [    2.216237] ohci_hcd 0000:00:13.1: irq 19, io mem 0xb0001000
Sep  5 21:58:46 Akatsuki kernel: [    2.276049] usb usb3: configuration #1 chosen from 1 choice
Sep  5 21:58:46 Akatsuki kernel: [    2.276069] hub 3-0:1.0: USB hub found
Sep  5 21:58:46 Akatsuki kernel: [    2.276081] hub 3-0:1.0: 4 ports detected
Sep  5 21:58:46 Akatsuki kernel: [    2.276162] uhci_hcd: USB Universal Host Controller Interface driver
Sep  5 21:58:46 Akatsuki kernel: [    2.276244] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Sep  5 21:58:46 Akatsuki kernel: [    2.284260] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  5 21:58:46 Akatsuki kernel: [    2.284265] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep  5 21:58:46 Akatsuki kernel: [    2.296033] mice: PS/2 mouse device common for all mice
Sep  5 21:58:46 Akatsuki kernel: [    2.344058] rtc_cmos 00:04: RTC can wake from S4
Sep  5 21:58:46 Akatsuki kernel: [    2.344098] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Sep  5 21:58:46 Akatsuki kernel: [    2.344127] rtc0: alarms up to one month, 114 bytes nvram
Sep  5 21:58:46 Akatsuki kernel: [    2.344187] device-mapper: uevent: version 1.0.3
Sep  5 21:58:46 Akatsuki kernel: [    2.344312] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
Sep  5 21:58:46 Akatsuki kernel: [    2.344359] device-mapper: multipath: version 1.0.5 loaded
Sep  5 21:58:46 Akatsuki kernel: [    2.344362] device-mapper: multipath round-robin: version 1.0.0 loaded
Sep  5 21:58:46 Akatsuki kernel: [    2.344432] cpuidle: using governor ladder
Sep  5 21:58:46 Akatsuki kernel: [    2.344433] cpuidle: using governor menu
Sep  5 21:58:46 Akatsuki kernel: [    2.344859] TCP cubic registered
Sep  5 21:58:46 Akatsuki kernel: [    2.344925] NET: Registered protocol family 10
Sep  5 21:58:46 Akatsuki kernel: [    2.345289] lo: Disabled Privacy Extensions
Sep  5 21:58:46 Akatsuki kernel: [    2.345546] NET: Registered protocol family 17
Sep  5 21:58:46 Akatsuki kernel: [    2.345567] Bluetooth: L2CAP ver 2.11
Sep  5 21:58:46 Akatsuki kernel: [    2.345568] Bluetooth: L2CAP socket layer initialized
Sep  5 21:58:46 Akatsuki kernel: [    2.345571] Bluetooth: SCO (Voice Link) ver 0.6
Sep  5 21:58:46 Akatsuki kernel: [    2.345572] Bluetooth: SCO socket layer initialized
Sep  5 21:58:46 Akatsuki kernel: [    2.345605] Bluetooth: RFCOMM socket layer initialized
Sep  5 21:58:46 Akatsuki kernel: [    2.345613] Bluetooth: RFCOMM TTY layer initialized
Sep  5 21:58:46 Akatsuki kernel: [    2.345614] Bluetooth: RFCOMM ver 1.10
Sep  5 21:58:46 Akatsuki kernel: [    2.345632] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)
Sep  5 21:58:46 Akatsuki kernel: [    2.345678] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x2
Sep  5 21:58:46 Akatsuki kernel: [    2.345680] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6
Sep  5 21:58:46 Akatsuki kernel: [    2.345682] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x10
Sep  5 21:58:46 Akatsuki kernel: [    2.345804] registered taskstats version 1
Sep  5 21:58:46 Akatsuki kernel: [    2.345952]   Magic number: 9:744:998
Sep  5 21:58:46 Akatsuki kernel: [    2.346009] pnp 00:00: hash matches
Sep  5 21:58:46 Akatsuki kernel: [    2.346060] rtc_cmos 00:04: setting system clock to 2009-09-05 18:58:26 UTC (1252177106)
Sep  5 21:58:46 Akatsuki kernel: [    2.346063] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep  5 21:58:46 Akatsuki kernel: [    2.346064] EDD information not available.
Sep  5 21:58:46 Akatsuki kernel: [    2.346108] Freeing unused kernel memory: 532k freed
Sep  5 21:58:46 Akatsuki kernel: [    2.346553] Write protecting the kernel read-only data: 6688k
Sep  5 21:58:46 Akatsuki kernel: [    2.350239] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Sep  5 21:58:46 Akatsuki kernel: [    2.540032] usb 1-4: new high speed USB device using ehci_hcd and address 3
Sep  5 21:58:46 Akatsuki kernel: [    2.699751] usb 1-4: configuration #1 chosen from 1 choice
Sep  5 21:58:46 Akatsuki kernel: [    2.811280] ohci1394 0000:03:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Sep  5 21:58:46 Akatsuki kernel: [    2.861095] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[b0208000-b02087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Sep  5 21:58:46 Akatsuki kernel: [    2.863682] usb 1-5: new high speed USB device using ehci_hcd and address 4
Sep  5 21:58:46 Akatsuki kernel: [    2.876923] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Sep  5 21:58:46 Akatsuki kernel: [    2.888924] b43-pci-bridge 0000:03:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Sep  5 21:58:46 Akatsuki kernel: [    2.892602] ssb: Sonics Silicon Backplane found on PCI device 0000:03:02.0
Sep  5 21:58:46 Akatsuki kernel: [    2.892911] 8139cp 0000:03:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Sep  5 21:58:46 Akatsuki kernel: [    2.895309] 8139too Fast Ethernet driver 0.9.28
Sep  5 21:58:46 Akatsuki kernel: [    2.895367] 8139too 0000:03:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Sep  5 21:58:46 Akatsuki kernel: [    2.896872] eth0: RealTek RTL8139 at 0xa000, 00:0f:b0:74:01:e3, IRQ 22
Sep  5 21:58:46 Akatsuki kernel: [    2.896874] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Sep  5 21:58:46 Akatsuki kernel: [    3.016084] usb 1-5: configuration #1 chosen from 1 choice
Sep  5 21:58:46 Akatsuki kernel: [    3.224270] Initializing USB Mass Storage driver...
Sep  5 21:58:46 Akatsuki kernel: [    3.226191] scsi2 : SCSI emulation for USB Mass Storage devices
Sep  5 21:58:46 Akatsuki kernel: [    3.227247] usb-storage: device found at 3
Sep  5 21:58:46 Akatsuki kernel: [    3.227251] usb-storage: waiting for device to settle before scanning
Sep  5 21:58:46 Akatsuki kernel: [    3.227644] scsi3 : SCSI emulation for USB Mass Storage devices
Sep  5 21:58:46 Akatsuki kernel: [    3.228707] usbcore: registered new interface driver usb-storage
Sep  5 21:58:46 Akatsuki kernel: [    3.228712] USB Mass Storage support registered.
Sep  5 21:58:46 Akatsuki kernel: [    3.229025] usb-storage: device found at 4
Sep  5 21:58:46 Akatsuki kernel: [    3.229027] usb-storage: waiting for device to settle before scanning
Sep  5 21:58:46 Akatsuki kernel: [    3.284084] PM: Starting manual resume from disk
Sep  5 21:58:46 Akatsuki kernel: [    3.284088] PM: Resume from partition 8:6
Sep  5 21:58:46 Akatsuki kernel: [    3.284090] PM: Checking hibernation image.
Sep  5 21:58:46 Akatsuki kernel: [    3.284295] PM: Resume from disk failed.
Sep  5 21:58:46 Akatsuki kernel: [    3.287000] EXT3-fs: INFO: recovery required on readonly filesystem.
Sep  5 21:58:46 Akatsuki kernel: [    3.287004] EXT3-fs: write access will be enabled during recovery.
Sep  5 21:58:46 Akatsuki kernel: [    3.432015] usb 2-1: new low speed USB device using ohci_hcd and address 2
Sep  5 21:58:46 Akatsuki kernel: [    3.644615] usb 2-1: configuration #1 chosen from 1 choice
Sep  5 21:58:46 Akatsuki kernel: [    3.652774] usbcore: registered new interface driver hiddev
Sep  5 21:58:46 Akatsuki kernel: [    3.656810] input: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0 as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input5
Sep  5 21:58:46 Akatsuki kernel: [    3.688127] generic-usb 0003:045E:007D.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0] on usb-0000:00:13.0-1/input0
Sep  5 21:58:46 Akatsuki kernel: [    3.688245] usbcore: registered new interface driver usbhid
Sep  5 21:58:46 Akatsuki kernel: [    3.688248] usbhid: v2.6:USB HID core driver
Sep  5 21:58:46 Akatsuki kernel: [    3.948011] usb 2-4: new full speed USB device using ohci_hcd and address 3
Sep  5 21:58:46 Akatsuki kernel: [    4.159649] usb 2-4: configuration #1 chosen from 1 choice
Sep  5 21:58:46 Akatsuki kernel: [    4.160924] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[573f020072c74079]
Sep  5 21:58:46 Akatsuki kernel: [    7.033171] kjournald starting.  Commit interval 5 seconds
Sep  5 21:58:46 Akatsuki kernel: [    7.033194] EXT3-fs: recovery complete.
Sep  5 21:58:46 Akatsuki kernel: [    7.033666] EXT3-fs: mounted filesystem with ordered data mode.
Sep  5 21:58:46 Akatsuki kernel: [    8.224921] usb-storage: device scan complete
Sep  5 21:58:46 Akatsuki kernel: [    8.225997] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
Sep  5 21:58:46 Akatsuki kernel: [    8.226962] sd 2:0:0:0: [sdb] 15646720 512-byte hardware sectors: (8.01 GB/7.46 GiB)
Sep  5 21:58:46 Akatsuki kernel: [    8.227461] sd 2:0:0:0: [sdb] Write Protect is off
Sep  5 21:58:46 Akatsuki kernel: [    8.227464] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
Sep  5 21:58:46 Akatsuki kernel: [    8.227466] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Sep  5 21:58:46 Akatsuki kernel: [    8.228230] usb-storage: device scan complete
Sep  5 21:58:46 Akatsuki kernel: [    8.229089] sd 2:0:0:0: [sdb] 15646720 512-byte hardware sectors: (8.01 GB/7.46 GiB)
Sep  5 21:58:46 Akatsuki kernel: [    8.229594] sd 2:0:0:0: [sdb] Write Protect is off
Sep  5 21:58:46 Akatsuki kernel: [    8.229596] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
Sep  5 21:58:46 Akatsuki kernel: [    8.229598] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Sep  5 21:58:46 Akatsuki kernel: [    8.229601]  sdb: sdb1
Sep  5 21:58:46 Akatsuki kernel: [    8.230454] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Sep  5 21:58:46 Akatsuki kernel: [    8.230518] sd 2:0:0:0: Attached scsi generic sg2 type 0
Sep  5 21:58:46 Akatsuki kernel: [    8.265151] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-E40L  SE02 PQ: 0 ANSI: 0
Sep  5 21:58:46 Akatsuki kernel: [    8.282134] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Sep  5 21:58:46 Akatsuki kernel: [    8.282269] sr 3:0:0:0: Attached scsi CD-ROM sr1
Sep  5 21:58:46 Akatsuki kernel: [    8.282339] sr 3:0:0:0: Attached scsi generic sg3 type 5
Sep  5 21:58:46 Akatsuki kernel: [   13.823844] udev: starting version 141
Sep  5 21:58:46 Akatsuki kernel: [   14.133627] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:12/device:13/input/input6
Sep  5 21:58:46 Akatsuki kernel: [   14.158728] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  5 21:58:46 Akatsuki kernel: [   14.164197] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Sep  5 21:58:46 Akatsuki kernel: [   14.210158] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
Sep  5 21:58:46 Akatsuki kernel: [   14.231190] Bluetooth: Generic Bluetooth USB driver ver 0.3
Sep  5 21:58:46 Akatsuki kernel: [   14.231324] usbcore: registered new interface driver btusb
Sep  5 21:58:46 Akatsuki kernel: [   14.569095] yenta_cardbus 0000:03:04.0: CardBus bridge found [103c:3085]
Sep  5 21:58:46 Akatsuki kernel: [   14.569124] yenta_cardbus 0000:03:04.0: Enabling burst memory read transactions
Sep  5 21:58:46 Akatsuki kernel: [   14.569131] yenta_cardbus 0000:03:04.0: Using INTVAL to route CSC interrupts to PCI
Sep  5 21:58:46 Akatsuki kernel: [   14.569134] yenta_cardbus 0000:03:04.0: Routing CardBus interrupts to ISA
Sep  5 21:58:46 Akatsuki kernel: [   14.569140] yenta_cardbus 0000:03:04.0: TI: mfunc 0x00aa1b22, devctl 0x64
Sep  5 21:58:46 Akatsuki kernel: [   14.801367] yenta_cardbus 0000:03:04.0: ISA IRQ mask 0x0ef8, PCI irq 20
Sep  5 21:58:46 Akatsuki kernel: [   14.801374] yenta_cardbus 0000:03:04.0: Socket status: 30000006
Sep  5 21:58:46 Akatsuki kernel: [   14.801378] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
Sep  5 21:58:46 Akatsuki kernel: [   14.801388] yenta_cardbus 0000:03:04.0: pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
Sep  5 21:58:46 Akatsuki kernel: [   14.801392] yenta_cardbus 0000:03:04.0: pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
Sep  5 21:58:46 Akatsuki kernel: [   14.801395] yenta_cardbus 0000:03:04.0: pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
Sep  5 21:58:46 Akatsuki kernel: [   14.874119] sdhci: Secure Digital Host Controller Interface driver
Sep  5 21:58:46 Akatsuki kernel: [   14.874123] sdhci: Copyright(c) Pierre Ossman
Sep  5 21:58:46 Akatsuki kernel: [   14.876940] sdhci-pci 0000:03:04.4: SDHCI controller found [104c:8034] (rev 0)
Sep  5 21:58:46 Akatsuki kernel: [   14.876968] sdhci-pci 0000:03:04.4: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Sep  5 21:58:46 Akatsuki kernel: [   14.877116] mmc0: SDHCI controller on PCI [0000:03:04.4] using PIO
Sep  5 21:58:46 Akatsuki kernel: [   14.877176] mmc1: SDHCI controller on PCI [0000:03:04.4] using PIO
Sep  5 21:58:46 Akatsuki kernel: [   14.877234] mmc2: SDHCI controller on PCI [0000:03:04.4] using PIO
Sep  5 21:58:46 Akatsuki kernel: [   14.914092] input: PC Speaker as /devices/platform/pcspkr/input/input7
Sep  5 21:58:46 Akatsuki kernel: [   14.960117] cfg80211: Calling CRDA to update world regulatory domain
Sep  5 21:58:46 Akatsuki kernel: [   15.005372] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Sep  5 21:58:46 Akatsuki kernel: [   15.084299] cfg80211: World regulatory domain updated:
Sep  5 21:58:46 Akatsuki kernel: [   15.084304] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep  5 21:58:46 Akatsuki kernel: [   15.084307] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  5 21:58:46 Akatsuki kernel: [   15.084309] ^I(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep  5 21:58:46 Akatsuki kernel: [   15.084311] ^I(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep  5 21:58:46 Akatsuki kernel: [   15.084313] ^I(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  5 21:58:46 Akatsuki kernel: [   15.084315] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  5 21:58:46 Akatsuki kernel: [   15.166750] tifm_7xx1 0000:03:04.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Sep  5 21:58:46 Akatsuki kernel: [   15.410494] b43-phy0: Broadcom 4306 WLAN found
Sep  5 21:58:46 Akatsuki kernel: [   15.464906] phy0: Selected rate control algorithm 'pid'
Sep  5 21:58:46 Akatsuki kernel: [   15.671621] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Sep  5 21:58:46 Akatsuki kernel: [   15.698829] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
Sep  5 21:58:46 Akatsuki kernel: [   15.780038] MC'97 0 converters and GPIO not ready (0x1)
Sep  5 21:58:46 Akatsuki kernel: [   15.781648] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Sep  5 21:58:46 Akatsuki kernel: [   15.814927] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x23a0b1, caps: 0xa04713/0x200000
Sep  5 21:58:46 Akatsuki kernel: [   15.862562] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
Sep  5 21:58:46 Akatsuki kernel: [   16.102200] lp: driver loaded but no devices found
Sep  5 21:58:46 Akatsuki kernel: [   16.452911] Adding 2144604k swap on /dev/sda6.  Priority:-1 extents:1 across:2144604k
Sep  5 21:58:46 Akatsuki kernel: [   17.056347] EXT3 FS on sda1, internal journal
Sep  5 21:58:46 Akatsuki kernel: [   20.491219] kjournald starting.  Commit interval 5 seconds
Sep  5 21:58:46 Akatsuki kernel: [   20.492181] EXT3 FS on sda5, internal journal
Sep  5 21:58:46 Akatsuki kernel: [   20.492187] EXT3-fs: mounted filesystem with ordered data mode.
Sep  5 21:58:46 Akatsuki kernel: [   21.002182] type=1505 audit(1252177125.153:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2529
Sep  5 21:58:46 Akatsuki kernel: [   21.056029] type=1505 audit(1252177125.205:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2533
Sep  5 21:58:46 Akatsuki kernel: [   21.056263] type=1505 audit(1252177125.209:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2533
Sep  5 21:58:46 Akatsuki kernel: [   21.056323] type=1505 audit(1252177125.209:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2533
Sep  5 21:58:46 Akatsuki kernel: [   21.056380] type=1505 audit(1252177125.209:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2533
Sep  5 21:58:46 Akatsuki kernel: [   21.112187] type=1505 audit(1252177125.265:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2538
Sep  5 21:58:46 Akatsuki kernel: [   21.261335] type=1505 audit(1252177125.413:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2542
Sep  5 21:58:46 Akatsuki kernel: [   21.261633] type=1505 audit(1252177125.413:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2542
Sep  5 21:58:46 Akatsuki kernel: [   21.297139] type=1505 audit(1252177125.449:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2546
Sep  5 21:58:50 Akatsuki kernel: [   26.017660] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Sep  5 21:58:50 Akatsuki kernel: [   26.017664] Bluetooth: BNEP filters: protocol multicast
Sep  5 21:58:50 Akatsuki kernel: [   26.045459] Bridge firewalling registered
Sep  5 21:58:51 Akatsuki kernel: [   27.086996] pci 0000:01:05.0: power state changed by ACPI to D0
Sep  5 21:58:51 Akatsuki kernel: [   27.087008] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Sep  5 21:58:51 Akatsuki kernel: [   27.332893] ppdev: user-space parallel port driver
Sep  5 21:58:51 Akatsuki kernel: [   27.369360] [drm] Initialized drm 1.1.0 20060810
Sep  5 21:58:52 Akatsuki kernel: [   27.441406] [drm] Initialized radeon 1.29.0 20080528 on minor 0
Sep  5 21:58:52 Akatsuki kernel: [   28.301336] [drm] Setting GART location based on new memory map
Sep  5 21:58:52 Akatsuki kernel: [   28.301736] [drm] Loading R300 Microcode
Sep  5 21:58:52 Akatsuki kernel: [   28.301756] [drm] Num pipes: 1
Sep  5 21:58:52 Akatsuki kernel: [   28.301762] [drm] writeback test succeeded in 1 usecs
Sep  5 21:58:55 Akatsuki kernel: [   30.847440] eth0: link down
Sep  5 21:58:55 Akatsuki kernel: [   30.848082] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep  5 21:58:55 Akatsuki kernel: [   30.944231] input: b43-phy0 as /devices/virtual/input/input9
Sep  5 21:58:55 Akatsuki kernel: [   31.012036] b43 ssb0:0: firmware: requesting b43/ucode5.fw
Sep  5 21:58:55 Akatsuki kernel: [   31.137791] b43 ssb0:0: firmware: requesting b43/pcm5.fw
Sep  5 21:58:55 Akatsuki kernel: [   31.139975] hci_cmd_task: hci0 command tx timeout
Sep  5 21:58:55 Akatsuki kernel: [   31.209364] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
Sep  5 21:58:55 Akatsuki kernel: [   31.295446] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
Sep  5 21:58:55 Akatsuki kernel: [   31.432029] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Sep  5 21:58:55 Akatsuki kernel: [   31.494259] Registered led device: b43-phy0::tx
Sep  5 21:58:55 Akatsuki kernel: [   31.494281] Registered led device: b43-phy0::rx
Sep  5 21:58:55 Akatsuki kernel: [   31.494303] Registered led device: b43-phy0::radio
Sep  5 21:58:55 Akatsuki kernel: [   31.512033] b43-phy0: Radio turned on by software
Sep  5 21:58:55 Akatsuki kernel: [   31.512645] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep  5 21:58:57 Akatsuki kernel: [   33.720959] warning: `pulseaudio' uses 32-bit capabilities (legacy support in use)
Sep  5 21:59:31 Akatsuki kernel: [   67.760508] wlan0: authenticate with AP 00:1a:9f:c9:fd:30
Sep  5 21:59:31 Akatsuki kernel: [   67.763229] wlan0: authenticated
Sep  5 21:59:31 Akatsuki kernel: [   67.763231] wlan0: associate with AP 00:1a:9f:c9:fd:30
Sep  5 21:59:31 Akatsuki kernel: [   67.768252] wlan0: RX AssocResp from 00:1a:9f:c9:fd:30 (capab=0x471 status=0 aid=1)
Sep  5 21:59:31 Akatsuki kernel: [   67.768256] wlan0: associated
Sep  5 21:59:31 Akatsuki kernel: [   67.771161] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Sep  5 21:59:42 Akatsuki kernel: [   77.892007] wlan0: no IPv6 routers present
Sep  5 15:56:52 Akatsuki kernel: [   89.044108] Marking TSC unstable due to cpufreq changes
Sep  5 15:56:53 Akatsuki kernel: [   89.616029] Clocksource tsc unstable (delta = -250013288 ns)
Sep  5 20:21:15 Akatsuki kernel: [15952.227110] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Sep  5 22:03:39 Akatsuki kernel: [22096.317476] [drm] Num pipes: 1
Sep  5 22:03:39 Akatsuki kernel: [22096.375761] mtrr: MTRR 2 not used
Sep  5 22:03:40 Akatsuki kernel: [22096.769713] ------------[ cut here ]------------
Sep  5 22:03:40 Akatsuki kernel: [22096.769762] kernel BUG at /build/buildd/linux-2.6.28/arch/x86/mm/pat.c:298!
Sep  5 22:03:40 Akatsuki kernel: [22096.769806] invalid opcode: 0000 [#1] SMP 
Sep  5 22:03:40 Akatsuki kernel: [22096.769919] last sysfs file: /sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/PNP0C0A:00/power_supply/BAT1/charge_full
Sep  5 22:03:40 Akatsuki kernel: [22096.769969] Dumping ftrace buffer:
Sep  5 22:03:40 Akatsuki kernel: [22096.770010]    (ftrace buffer empty)
Sep  5 22:03:40 Akatsuki kernel: [22096.770050] CPU 0 
Sep  5 22:03:40 Akatsuki kernel: [22096.770124] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat rfkill_input binfmt_misc radeon drm ppdev bridge stp bnep lp parport joydev arc4 snd_atiixp snd_atiixp_modem ecb snd_ac97_codec snd_pcm_oss snd_mixer_oss ac97_bus snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi b43 snd_seq_midi_event snd_seq snd_timer snd_seq_device mac80211 pcmcia snd tifm_7xx1 soundcore snd_page_alloc cfg80211 psmouse k8temp pcspkr sdhci_pci sdhci tifm_core yenta_socket rsrc_nonstatic pcmcia_core led_class input_polldev serio_raw btusb i2c_piix4 shpchp video output usbhid usb_storage 8139too 8139cp mii ohci1394 ssb ieee1394 fbcon tileblit font bitblit softcursor
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] Pid: 15733, comm: usplash Not tainted 2.6.28-15-generic #49-Ubuntu
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] RIP: 0010:[<ffffffff80239290>]  [<ffffffff80239290>] reserve_memtype+0x3f0/0x640
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] RSP: 0018:ffff88006d4b9d18  EFLAGS: 00010286
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] RAX: 0000000040400000 RBX: 000ffffffffc0000 RCX: ffff88006d4b9d78
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] RDX: ffffffffffffffff RSI: 0000000000400000 RDI: ffffffffc0000000
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] RBP: ffff88006d4b9d58 R08: 0000000000000000 R09: ffff88006d42ae70
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] R10: ffff88004e8abb28 R11: 0000000000003206 R12: ffffffffc0000000
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] R13: ffffffffc0000000 R14: ffffffffffffffff R15: ffff88006d4b9d78
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] FS:  00007f790053e6f0(0000) GS:ffffffff80a9a000(0000) knlGS:00000000f7cf96c0
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] CR2: 00007f79000d94af CR3: 0000000075cda000 CR4: 00000000000006a0
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] Process usplash (pid: 15733, threadinfo ffff88006d4b8000, task ffff8800761b2cc0)
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] Stack:
Sep  5 22:03:40 Akatsuki kernel: [22096.772014]  ffffe200019f2f58 0000000000400000 ffff880075cda7f0 000ffffffffc0000
Sep  5 22:03:40 Akatsuki kernel: [22096.772014]  ffffffffc0000000 0000000040400000 0000000000400000 ffff88006d42ae90
Sep  5 22:03:40 Akatsuki kernel: [22096.772014]  ffff88006d4b9da8 ffffffff802396aa ffff88006d42a5e8 ffff8800601e3740
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] Call Trace:
Sep  5 22:03:40 Akatsuki kernel: [22096.772014]  [<ffffffff802396aa>] phys_mem_access_prot_allowed+0xba/0x170
Sep  5 22:03:40 Akatsuki kernel: [22096.772014]  [<ffffffff8048ac27>] mmap_mem+0x87/0x150
Sep  5 22:03:40 Akatsuki kernel: [22096.772014]  [<ffffffff802cb45d>] mmap_region+0x23d/0x630
Sep  5 22:03:40 Akatsuki kernel: [22096.772014]  [<ffffffff802cbd24>] do_mmap_pgoff+0x3e4/0x410
Sep  5 22:03:40 Akatsuki kernel: [22096.772014]  [<ffffffff802177d6>] sys_mmap+0x106/0x130
Sep  5 22:03:40 Akatsuki kernel: [22096.772014]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] Code: 00 49 89 d0 48 8b 55 c8 4c 89 ee 48 c7 c7 b8 ba 7e 80 31 c0 45 31 e4 e8 1e ff 45 00 e9 68 fc ff ff 66 2e 0f 1f 84 00 00 00 00 00 <0f> 0b eb fe 0f 1f 40 00 48 8b 7d d0 4c 89 fa 48 89 de e8 f9 f7 
Sep  5 22:03:40 Akatsuki kernel: [22096.772014] RIP  [<ffffffff80239290>] reserve_memtype+0x3f0/0x640
Sep  5 22:03:40 Akatsuki kernel: [22096.772014]  RSP <ffff88006d4b9d18>
Sep  5 22:03:40 Akatsuki kernel: [22096.777232] ---[ end trace 5a40003c43053f88 ]---

Thank you:)

---

### Post by P4man on 2009-09-06
First of all, please attach such a long file to your post, or at least enclose it in "code" tags, so the thread remains browsable :)

Here, this seems to be your problem:

> Sep 5 22:03:40 Akatsuki kernel: [22096.769762] kernel BUG at /build/buildd/linux-2.6.28/arch/x86/mm/pat.c:298!
Sep 5 22:03:40 Akatsuki kernel: [22096.769806] invalid opcode: 0000 [#1] SMP 

It has been reported by 1 other person as far as i can find:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407652)

You may want to register for launchpad and confirm the bug for your system.
Not much else I can think off. Perhaps check if there is a newer bios for your system?

---

### Post by Kryzzalid on 2009-09-06
Thanks for the reply:) I didn't know that I could attach code. I learnt something new today;) I guess the error comes from the 64-bits version. Because before i had ubuntu 32-bit 8.10 that i updated to 9.10. But when i reinstall from a 9.10 cd i got the 64-bits version. Anyway, i guess there ain't much i can do.

---

