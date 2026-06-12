---
title: "Update manager just killed my system"
date: 2010-06-18
forum: General Help
---

### Post by TheDesertDragon on 2010-06-18
I have no idea what the hell just happened. I opened up my computer this morning, and the update manager ran within Plymouth and removed Evolution (and installed package Evolution-common, which doesn't seem to work), removed laptop-mode, then hung my computer.

After booting into failsafe and reinstalling my display driver, then going back to normal mode after which it finally booted, I can no longer enable desktop effects and the Catalyst Control Centre (I use FGLRX/ATi) no longer works, and when I close the PC, the CAPS LOCK button starts flashing and the system hangs.

I don't even know where to start.:confused:
Can anybody help?

---

### Post by gradinaruvasile on 2010-06-18
Start by posting the computers specs - model name and the output of the commands:

lspci

cat /etc/X11/xorg.conf

dmesg

just after startup.

Reinstall laptop-mode and Evolution. Evolution-common is only a part of Evolution (that, in turn is integrated in the Gnome environment and i am pretty sure it took with it some other packages aswell).
Also, try using the upgrade from the terminal, that way you will clearly see what is going to be removed.

sudo apt-get update && sudo apt-get dselect-upgrade

is the command from the terminal.

---

### Post by dino99 on 2010-06-18
> **TheDesertDragon said:**
> I have no idea what the hell just happened. I opened up my computer this morning, and the update manager ran within Plymouth and removed Evolution (and installed package Evolution-common, which doesn't seem to work), removed laptop-mode, then hung my computer.

After booting into failsafe and reinstalling my display driver, then going back to normal mode after which it finally booted, I can no longer enable desktop effects and the Catalyst Control Centre (I use FGLRX/ATi) no longer works, and when I close the PC, the CAPS LOCK button starts flashing and the system hangs.

I don't even know where to start.:confused:
Can anybody help?

Thats what happen when user blindly apply updates without looking at comments attached, just reinstall the packages beeing removed

---

### Post by TheDesertDragon on 2010-06-18
I just got my display manager back with compositing by going to the laptop-mode website and reinstalling it. My system's now stable again.

Evolution's still gone though but I don't really want it, so if I can get away with not having it, so much the better.

However, now I have no window manager when I first start. Typing "compiz --replace" gets it back though.

Anyway, for mostly debugging purposes or to reveal future problems before they start showing up:

Output of lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
02:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
0e:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

Output of X11 xorg.conf: Remember I repeatedly tried to get my ATI configuration back and finally succeeded, so this might not reveal anuthing bad.
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

EDIT: Ok, got it. Increased terminal lines to infinity! :P Output of dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 (Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=d306be65-f638-4822-aae1-c6edba5eb328 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bdab1000 (usable)
[    0.000000]  BIOS-e820: 00000000bdab1000 - 00000000bdab7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bdab7000 - 00000000bdbb5000 (usable)
[    0.000000]  BIOS-e820: 00000000bdbb5000 - 00000000bdc0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bdc0f000 - 00000000bdd08000 (usable)
[    0.000000]  BIOS-e820: 00000000bdd08000 - 00000000bdf0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bdf0f000 - 00000000bdf18000 (usable)
[    0.000000]  BIOS-e820: 00000000bdf18000 - 00000000bdf1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bdf1f000 - 00000000bdf55000 (usable)
[    0.000000]  BIOS-e820: 00000000bdf55000 - 00000000bdf9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bdf9f000 - 00000000bdfe4000 (usable)
[    0.000000]  BIOS-e820: 00000000bdfe4000 - 00000000bdffd000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bdffd000 - 00000000be000000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbe000 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009d400 (usable)
[    0.000000]  modified: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bdab1000 (usable)
[    0.000000]  modified: 00000000bdab1000 - 00000000bdab7000 (reserved)
[    0.000000]  modified: 00000000bdab7000 - 00000000bdbb5000 (usable)
[    0.000000]  modified: 00000000bdbb5000 - 00000000bdc0f000 (reserved)
[    0.000000]  modified: 00000000bdc0f000 - 00000000bdd08000 (usable)
[    0.000000]  modified: 00000000bdd08000 - 00000000bdf0f000 (reserved)
[    0.000000]  modified: 00000000bdf0f000 - 00000000bdf18000 (usable)
[    0.000000]  modified: 00000000bdf18000 - 00000000bdf1f000 (reserved)
[    0.000000]  modified: 00000000bdf1f000 - 00000000bdf55000 (usable)
[    0.000000]  modified: 00000000bdf55000 - 00000000bdf9f000 (ACPI NVS)
[    0.000000]  modified: 00000000bdf9f000 - 00000000bdfe4000 (usable)
[    0.000000]  modified: 00000000bdfe4000 - 00000000bdffd000 (ACPI data)
[    0.000000]  modified: 00000000bdffd000 - 00000000be000000 (usable)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000be000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00be000000 page 2M
[    0.000000] kernel direct mapping tables up to be000000 @ 8000-c000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ a000-10000
[    0.000000] RAMDISK: 377ee000 - 37fefece
[    0.000000] ACPI: RSDP 00000000000f6ad0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 00000000bdff7287 0007C (v01 PTLTD  ? XSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 00000000bdfe8000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 00000000bdfe9000 05893 (v02 Intel  CANTIGA  06040000 INTL 20060608)
[    0.000000] ACPI: FACS 00000000bdf8efc0 00040
[    0.000000] ACPI: APIC 00000000bdffcd1e 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 00000000bdffcd86 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 00000000bdffcdbe 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: SLIX 00000000bdffcdfa 00176 (v01 Compal JHL00_90 06040000 TBD  00000001)
[    0.000000] ACPI: APIC 00000000bdffcf70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000bdffcfd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: TCPA 00000000bdfef000 00032 (v00                 00000000      00000000)
[    0.000000] ACPI: SSDT 00000000bdfe7000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 00000000bdfe6000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 00000000bdfe5000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [000000000000b000 - 000000000000ffff]
[    0.000000]   bootmap [0000000000010000 -  0000000000037fff] pages 28
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
[    0.000000]   #3 [00377ee000 - 0037fefece]          RAMDISK ==> [00377ee000 - 0037fefece]
[    0.000000]   #4 [000009d400 - 0000100000]    BIOS reserved ==> [000009d400 - 0000100000]
[    0.000000]   #5 [0001a2a000 - 0001a2a065]              BRK ==> [0001a2a000 - 0001a2a065]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]   #7 [000000a000 - 000000b000]          PGTABLE ==> [000000a000 - 000000b000]
[    0.000000] found SMP MP-table at [ffff8800000f6b80] f6b80
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[10] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000bdab1
[    0.000000]     0: 0x000bdab7 -> 0x000bdbb5
[    0.000000]     0: 0x000bdc0f -> 0x000bdd08
[    0.000000]     0: 0x000bdf0f -> 0x000bdf18
[    0.000000]     0: 0x000bdf1f -> 0x000bdf55
[    0.000000]     0: 0x000bdf9f -> 0x000bdfe4
[    0.000000]     0: 0x000bdffd -> 0x000be000
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1039559
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 104 pages reserved
[    0.000000]   DMA zone: 3832 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 759143 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bdab1000 - 00000000bdab7000
[    0.000000] PM: Registered nosave memory: 00000000bdbb5000 - 00000000bdc0f000
[    0.000000] PM: Registered nosave memory: 00000000bdd08000 - 00000000bdf0f000
[    0.000000] PM: Registered nosave memory: 00000000bdf18000 - 00000000bdf1f000
[    0.000000] PM: Registered nosave memory: 00000000bdf55000 - 00000000bdf9f000
[    0.000000] PM: Registered nosave memory: 00000000bdfe4000 - 00000000bdffd000
[    0.000000] PM: Registered nosave memory: 00000000be000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at be000000 (gap: be000000:42000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1021535
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=d306be65-f638-4822-aae1-c6edba5eb328 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 4015828k/5242880k available (5409k kernel code, 1084644k absent, 142408k reserved, 2976k data, 876k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2527.258 MHz processor.
[    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5054.51 BogoMIPS (lpj=25272580)
[    0.010031] Security Framework initialized
[    0.010049] AppArmor: AppArmor initialized
[    0.010365] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.012318] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.013255] Mount-cache hash table entries: 256
[    0.013389] Initializing cgroup subsys ns
[    0.013395] Initializing cgroup subsys cpuacct
[    0.013398] Initializing cgroup subsys memory
[    0.013405] Initializing cgroup subsys devices
[    0.013408] Initializing cgroup subsys freezer
[    0.013409] Initializing cgroup subsys net_cls
[    0.013427] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.013429] CPU: L2 cache: 3072K
[    0.013432] CPU 0/0x0 -> Node 0
[    0.013434] CPU: Physical Processor ID: 0
[    0.013435] CPU: Processor Core ID: 0
[    0.013438] mce: CPU supports 6 MCE banks
[    0.013445] CPU0: Thermal monitoring enabled (TM2)
[    0.013449] using mwait in idle threads.
[    0.013450] Performance Events: Core2 events, Intel PMU driver.
[    0.013456] ... version:                2
[    0.013457] ... bit width:              40
[    0.013458] ... generic registers:      2
[    0.013459] ... value mask:             000000ffffffffff
[    0.013461] ... max period:             000000007fffffff
[    0.013462] ... fixed-purpose events:   3
[    0.013463] ... event mask:             0000000700000003
[    0.016377] ACPI: Core revision 20090903
[    0.029401] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.029406] ftrace: allocating 22518 entries in 89 pages
[    0.030051] Setting APIC routing to flat
[    0.030359] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.138177] CPU0: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz stepping 0a
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.020000] Initializing CPU#1
[    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.020000] CPU: L2 cache: 3072K
[    0.020000] CPU 1/0x1 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 1
[    0.020000] CPU1: Thermal monitoring enabled (TM2)
[    0.290048] CPU1: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz stepping 0a
[    0.290054] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300014] Brought up 2 CPUs
[    0.300016] Total of 2 processors activated (10108.52 BogoMIPS).
[    0.300547] CPU0 attaching sched-domain:
[    0.300550]  domain 0: span 0-1 level MC
[    0.300552]   groups: 0 1
[    0.300557] CPU1 attaching sched-domain:
[    0.300558]  domain 0: span 0-1 level MC
[    0.300560]   groups: 1 0
[    0.300638] devtmpfs: initialized
[    0.300638] regulator: core version 0.5
[    0.300638] Time: 10:08:42  Date: 06/18/10
[    0.300638] NET: Registered protocol family 16
[    0.300638] Trying to unpack rootfs image as initramfs...
[    0.300638] ACPI: bus type pci registered
[    0.300638] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.300638] PCI: Not using MMCONFIG.
[    0.300638] PCI: Using configuration type 1 for base access
[    0.310108] bio: create slab <bio-0> at 0
[    0.310879] ACPI: EC: Look up EC in DSDT
[    0.313818] ACPI: BIOS _OSI(Linux) query ignored
[    0.314355] ACPI: Interpreter enabled
[    0.314358] ACPI: (supports S0 S3 S4 S5)
[    0.314377] ACPI: Using IOAPIC for interrupt routing
[    0.314418] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.350314] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.361312] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.402104] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.402408] ACPI: No dock devices found.
[    0.402819] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.402921] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.402924] pci 0000:00:01.0: PME# disabled
[    0.403008] pci 0000:00:1a.0: reg 20 io port: [0x1800-0x181f]
[    0.403090] pci 0000:00:1a.1: reg 20 io port: [0x1820-0x183f]
[    0.403171] pci 0000:00:1a.2: reg 20 io port: [0x1840-0x185f]
[    0.403257] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf2504800-0xf2504bff]
[    0.403321] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.403325] pci 0000:00:1a.7: PME# disabled
[    0.403373] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf2500000-0xf2503fff]
[    0.403423] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.403427] pci 0000:00:1b.0: PME# disabled
[    0.403500] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.403504] pci 0000:00:1c.0: PME# disabled
[    0.403584] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.403588] pci 0000:00:1c.2: PME# disabled
[    0.403664] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.403668] pci 0000:00:1c.3: PME# disabled
[    0.403745] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.403749] pci 0000:00:1c.4: PME# disabled
[    0.403814] pci 0000:00:1d.0: reg 20 io port: [0x1860-0x187f]
[    0.403895] pci 0000:00:1d.1: reg 20 io port: [0x1880-0x189f]
[    0.403976] pci 0000:00:1d.2: reg 20 io port: [0x18a0-0x18bf]
[    0.404062] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf2504c00-0xf2504fff]
[    0.404126] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.404130] pci 0000:00:1d.7: PME# disabled
[    0.404343] pci 0000:00:1f.2: reg 10 io port: [0x18f0-0x18f7]
[    0.404349] pci 0000:00:1f.2: reg 14 io port: [0x18e4-0x18e7]
[    0.404355] pci 0000:00:1f.2: reg 18 io port: [0x18e8-0x18ef]
[    0.404361] pci 0000:00:1f.2: reg 1c io port: [0x18e0-0x18e3]
[    0.404367] pci 0000:00:1f.2: reg 20 io port: [0x18c0-0x18df]
[    0.404374] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf2504000-0xf25047ff]
[    0.404412] pci 0000:00:1f.2: PME# supported from D3hot
[    0.404416] pci 0000:00:1f.2: PME# disabled
[    0.404450] pci 0000:00:1f.3: reg 10 64bit mmio: [0x000000-0x0000ff]
[    0.404465] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.404522] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.404529] pci 0000:01:00.0: reg 14 io port: [0x2000-0x20ff]
[    0.404536] pci 0000:01:00.0: reg 18 32bit mmio: [0xcfef0000-0xcfefffff]
[    0.404558] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.404585] pci 0000:01:00.0: supports D1 D2
[    0.404627] pci 0000:01:00.1: reg 10 32bit mmio: [0xcfeec000-0xcfeeffff]
[    0.404684] pci 0000:01:00.1: supports D1 D2
[    0.404741] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.404744] pci 0000:00:01.0: bridge 32bit mmio: [0xcfe00000-0xcfefffff]
[    0.404748] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.404797] pci 0000:02:00.0: reg 10 32bit mmio: [0xf2100000-0xf21000ff]
[    0.404847] pci 0000:02:00.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
[    0.404948] pci 0000:02:00.2: reg 10 32bit mmio: [0xf2100400-0xf21004ff]
[    0.405093] pci 0000:02:00.3: reg 10 32bit mmio: [0xf2100800-0xf21008ff]
[    0.405246] pci 0000:00:1c.0: bridge 32bit mmio: [0xf2100000-0xf21fffff]
[    0.405380] pci 0000:0e:00.0: reg 10 64bit mmio: [0xf2200000-0xf2201fff]
[    0.405498] pci 0000:0e:00.0: PME# supported from D0 D3hot D3cold
[    0.405508] pci 0000:0e:00.0: PME# disabled
[    0.405583] pci 0000:00:1c.2: bridge 32bit mmio: [0xf2200000-0xf22fffff]
[    0.405639] pci 0000:14:00.0: reg 10 io port: [0x3000-0x30ff]
[    0.405662] pci 0000:14:00.0: reg 18 64bit mmio pref: [0xf2010000-0xf2010fff]
[    0.405678] pci 0000:14:00.0: reg 20 64bit mmio pref: [0xf2000000-0xf200ffff]
[    0.405687] pci 0000:14:00.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
[    0.405731] pci 0000:14:00.0: supports D1 D2
[    0.405733] pci 0000:14:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.405738] pci 0000:14:00.0: PME# disabled
[    0.405806] pci 0000:00:1c.3: bridge io port: [0x3000-0x3fff]
[    0.405814] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xf2000000-0xf20fffff]
[    0.405862] pci 0000:00:1c.4: bridge io port: [0x4000-0x4fff]
[    0.405866] pci 0000:00:1c.4: bridge 32bit mmio: [0xf4000000-0xf5ffffff]
[    0.405872] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.405929] pci 0000:00:1e.0: transparent bridge
[    0.405969] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.406092] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.406154] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.406284] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.406341] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.406389] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.406446] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.412659] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.412747] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.412832] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.412918] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.413005] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.413091] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.413178] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.413263] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.413363] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.413368] vgaarb: loaded
[    0.413476] SCSI subsystem initialized
[    0.413549] libata version 3.00 loaded.
[    0.413606] usbcore: registered new interface driver usbfs
[    0.413616] usbcore: registered new interface driver hub
[    0.413643] usbcore: registered new device driver usb
[    0.413751] ACPI: WMI: Mapper loaded
[    0.413753] PCI: Using ACPI for IRQ routing
[    0.413984] NetLabel: Initializing
[    0.413985] NetLabel:  domain hash size = 128
[    0.413987] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.413998] NetLabel:  unlabeled traffic allowed by default
[    0.414028] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.414032] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.420130] Switching to clocksource tsc
[    0.421522] AppArmor: AppArmor Filesystem Enabled
[    0.421536] pnp: PnP ACPI init
[    0.421550] ACPI: bus type pnp registered
[    0.440233] pnp: PnP ACPI: found 11 devices
[    0.440236] ACPI: ACPI bus type pnp unregistered
[    0.440250] system 00:03: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.440257] system 00:05: ioport range 0x400-0x47f has been reserved
[    0.440260] system 00:05: ioport range 0x480-0x48f has been reserved
[    0.440262] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.440264] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.440266] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.440268] system 00:05: ioport range 0x1180-0x11ff has been reserved
[    0.440270] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
[    0.440276] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.440278] system 00:09: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.440281] system 00:09: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.440283] system 00:09: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.440285] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.440287] system 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.440290] system 00:09: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.440292] system 00:09: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.445038] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.445041] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.445044] pci 0000:00:01.0:   MEM window: 0xcfe00000-0xcfefffff
[    0.445047] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.445051] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.445054] pci 0000:00:1c.0:   IO window: 0x5000-0x5fff
[    0.445059] pci 0000:00:1c.0:   MEM window: 0xf2100000-0xf21fffff
[    0.445062] pci 0000:00:1c.0:   PREFETCH window: 0xc0000000-0xc01fffff
[    0.445069] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:0e
[    0.445072] pci 0000:00:1c.2:   IO window: 0x6000-0x6fff
[    0.445076] pci 0000:00:1c.2:   MEM window: 0xf2200000-0xf22fffff
[    0.445080] pci 0000:00:1c.2:   PREFETCH window: 0x000000c0200000-0x000000c03fffff
[    0.445087] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:14
[    0.445090] pci 0000:00:1c.3:   IO window: 0x3000-0x3fff
[    0.445095] pci 0000:00:1c.3:   MEM window: 0xc0400000-0xc07fffff
[    0.445098] pci 0000:00:1c.3:   PREFETCH window: 0x000000f2000000-0x000000f20fffff
[    0.445105] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:1a
[    0.445107] pci 0000:00:1c.4:   IO window: 0x4000-0x4fff
[    0.445112] pci 0000:00:1c.4:   MEM window: 0xf4000000-0xf5ffffff
[    0.445116] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.445123] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:26
[    0.445124] pci 0000:00:1e.0:   IO window: disabled
[    0.445129] pci 0000:00:1e.0:   MEM window: disabled
[    0.445133] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.445145]   alloc irq_desc for 16 on node -1
[    0.445147]   alloc kstat_irqs on node -1
[    0.445153] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.445156] pci 0000:00:01.0: setting latency timer to 64
[    0.445164]   alloc irq_desc for 17 on node -1
[    0.445165]   alloc kstat_irqs on node -1
[    0.445167] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.445171] pci 0000:00:1c.0: setting latency timer to 64
[    0.445179]   alloc irq_desc for 18 on node -1
[    0.445180]   alloc kstat_irqs on node -1
[    0.445183] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.445187] pci 0000:00:1c.2: setting latency timer to 64
[    0.445195]   alloc irq_desc for 19 on node -1
[    0.445196]   alloc kstat_irqs on node -1
[    0.445198] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.445203] pci 0000:00:1c.3: setting latency timer to 64
[    0.445211] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.445215] pci 0000:00:1c.4: setting latency timer to 64
[    0.445221] pci 0000:00:1e.0: setting latency timer to 64
[    0.445225] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.445227] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.445229] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.445231] pci_bus 0000:01: resource 1 mem: [0xcfe00000-0xcfefffff]
[    0.445233] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.445235] pci_bus 0000:02: resource 0 io:  [0x5000-0x5fff]
[    0.445237] pci_bus 0000:02: resource 1 mem: [0xf2100000-0xf21fffff]
[    0.445238] pci_bus 0000:02: resource 2 pref mem [0xc0000000-0xc01fffff]
[    0.445240] pci_bus 0000:0e: resource 0 io:  [0x6000-0x6fff]
[    0.445242] pci_bus 0000:0e: resource 1 mem: [0xf2200000-0xf22fffff]
[    0.445244] pci_bus 0000:0e: resource 2 pref mem [0xc0200000-0xc03fffff]
[    0.445246] pci_bus 0000:14: resource 0 io:  [0x3000-0x3fff]
[    0.445247] pci_bus 0000:14: resource 1 mem: [0xc0400000-0xc07fffff]
[    0.445249] pci_bus 0000:14: resource 2 pref mem [0xf2000000-0xf20fffff]
[    0.445251] pci_bus 0000:1a: resource 0 io:  [0x4000-0x4fff]
[    0.445253] pci_bus 0000:1a: resource 1 mem: [0xf4000000-0xf5ffffff]
[    0.445255] pci_bus 0000:1a: resource 2 pref mem [0xf0000000-0xf1ffffff]
[    0.445257] pci_bus 0000:26: resource 3 io:  [0x00-0xffff]
[    0.445259] pci_bus 0000:26: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.445289] NET: Registered protocol family 2
[    0.445434] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.446464] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.450610] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.451119] TCP: Hash tables configured (established 524288 bind 65536)
[    0.451122] TCP reno registered
[    0.451216] NET: Registered protocol family 1
[    0.451379] pci 0000:01:00.0: Boot video device
[    0.451435] Simple Boot Flag at 0x36 set to 0x1
[    0.451598] Scanning for low memory corruption every 60 seconds
[    0.451724] audit: initializing netlink socket (disabled)
[    0.451733] type=2000 audit(1276855721.449:1): initialized
[    0.456073] Freeing initrd memory: 8199k freed
[    0.459644] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.460801] VFS: Disk quotas dquot_6.5.2
[    0.460845] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.461336] fuse init (API version 7.13)
[    0.461401] msgmni has been set to 7859
[    0.461575] alg: No test for stdrng (krng)
[    0.461618] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.461621] io scheduler noop registered
[    0.461622] io scheduler anticipatory registered
[    0.461624] io scheduler deadline registered
[    0.461651] io scheduler cfq registered (default)
[    0.461784]   alloc irq_desc for 24 on node -1
[    0.461785]   alloc kstat_irqs on node -1
[    0.461793] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.461799] pcieport 0000:00:01.0: setting latency timer to 64
[    0.461900]   alloc irq_desc for 25 on node -1
[    0.461901]   alloc kstat_irqs on node -1
[    0.461908] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.461916] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.462035]   alloc irq_desc for 26 on node -1
[    0.462037]   alloc kstat_irqs on node -1
[    0.462043] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.462052] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.462171]   alloc irq_desc for 27 on node -1
[    0.462172]   alloc kstat_irqs on node -1
[    0.462179] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.462187] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.462306]   alloc irq_desc for 28 on node -1
[    0.462307]   alloc kstat_irqs on node -1
[    0.462314] pcieport 0000:00:1c.4: irq 28 for MSI/MSI-X
[    0.462322] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.462406] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.462553] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.462888] ACPI: AC Adapter [ACAD] (off-line)
[    0.462974] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.463008] ACPI: Lid Switch [LID0]
[    0.463045] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.463047] ACPI: Power Button [PWRB]
[    0.463083] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.463085] ACPI: Power Button [PWRF]
[    0.463796] ACPI: SSDT 00000000bdf1ac20 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.464201] ACPI: SSDT 00000000bdf18620 00549 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.466093] Monitor-Mwait will be used to enter C-1 state
[    0.466115] Monitor-Mwait will be used to enter C-2 state
[    0.466135] Monitor-Mwait will be used to enter C-3 state
[    0.466141] Marking TSC unstable due to TSC halts in idle
[    0.466177] Switching to clocksource hpet
[    0.466229] processor LNXCPU:00: registered as cooling_device0
[    0.466630] ACPI: SSDT 00000000bdf19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.466931] ACPI: SSDT 00000000bdf19f20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.467743] processor LNXCPU:01: registered as cooling_device1
[    0.494346] Linux agpgart interface v0.103
[    0.494372] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.495403] brd: module loaded
[    0.495783] loop: module loaded
[    0.495850] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.496154] Fixed MDIO Bus: probed
[    0.496179] PPP generic driver version 2.4.2
[    0.496203] tun: Universal TUN/TAP device driver, 1.6
[    0.496204] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.496271] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.496292] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.496306] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.496309] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.496333] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.496362] ehci_hcd 0000:00:1a.7: debug port 1
[    0.500252] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.500265] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf2504800
[    0.512907] ACPI: Battery Slot [BAT1] (battery present)
[    0.520012] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.520074] usb usb1: configuration #1 chosen from 1 choice
[    0.520097] hub 1-0:1.0: USB hub found
[    0.520103] hub 1-0:1.0: 6 ports detected
[    0.520152]   alloc irq_desc for 23 on node -1
[    0.520153]   alloc kstat_irqs on node -1
[    0.520158] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.520167] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.520169] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.520193] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.520217] ehci_hcd 0000:00:1d.7: debug port 1
[    0.524113] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.524123] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf2504c00
[    0.540011] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.540063] usb usb2: configuration #1 chosen from 1 choice
[    0.540083] hub 2-0:1.0: USB hub found
[    0.540087] hub 2-0:1.0: 6 ports detected
[    0.540134] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.540145] uhci_hcd: USB Universal Host Controller Interface driver
[    0.540160] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.540165] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.540168] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.540196] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.540224] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.540289] usb usb3: configuration #1 chosen from 1 choice
[    0.540312] hub 3-0:1.0: USB hub found
[    0.540319] hub 3-0:1.0: 2 ports detected
[    0.540354]   alloc irq_desc for 21 on node -1
[    0.540355]   alloc kstat_irqs on node -1
[    0.540359] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.540366] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.540369] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.540395] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.540422] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.540490] usb usb4: configuration #1 chosen from 1 choice
[    0.540509] hub 4-0:1.0: USB hub found
[    0.540514] hub 4-0:1.0: 2 ports detected
[    0.540550] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.540555] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.540558] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.540581] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.540602] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001840
[    0.540669] usb usb5: configuration #1 chosen from 1 choice
[    0.540688] hub 5-0:1.0: USB hub found
[    0.540692] hub 5-0:1.0: 2 ports detected
[    0.540730] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.540735] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.540738] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.540769] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.540790] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    0.540859] usb usb6: configuration #1 chosen from 1 choice
[    0.540878] hub 6-0:1.0: USB hub found
[    0.540883] hub 6-0:1.0: 2 ports detected
[    0.540925] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.540930] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.540933] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.540956] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.540977] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    0.541044] usb usb7: configuration #1 chosen from 1 choice
[    0.541062] hub 7-0:1.0: USB hub found
[    0.541067] hub 7-0:1.0: 2 ports detected
[    0.541100] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.541105] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.541108] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.541140] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.541167] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    0.541233] usb usb8: configuration #1 chosen from 1 choice
[    0.541254] hub 8-0:1.0: USB hub found
[    0.541262] hub 8-0:1.0: 2 ports detected
[    0.541337] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.571774] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.571779] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.571870] mice: PS/2 mouse device common for all mice
[    0.572388] rtc_cmos 00:06: RTC can wake from S4
[    0.572418] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.572441] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.572534] device-mapper: uevent: version 1.0.3
[    0.572611] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.572668] device-mapper: multipath: version 1.1.0 loaded
[    0.572670] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.572848] cpuidle: using governor ladder
[    0.572936] cpuidle: using governor menu
[    0.573193] TCP cubic registered
[    0.573288] NET: Registered protocol family 10
[    0.573628] lo: Disabled Privacy Extensions
[    0.573844] NET: Registered protocol family 17
[    0.574449] PM: Resume from disk failed.
[    0.574459] registered taskstats version 1
[    0.575004]   Magic number: 14:475:123
[    0.575031] acpi LNXSYBUS:01: hash matches
[    0.575090] rtc_cmos 00:06: setting system clock to 2010-06-18 10:08:42 UTC (1276855722)
[    0.575092] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.575094] EDD information not available.
[    0.575154] Freeing unused kernel memory: 876k freed
[    0.575399] Write protecting the kernel read-only data: 7680k
[    0.587408] udev: starting version 151
[    0.594146] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.635954] ahci 0000:00:1f.2: version 3.0
[    0.635977] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.636028]   alloc irq_desc for 29 on node -1
[    0.636030]   alloc kstat_irqs on node -1
[    0.636039] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    0.636078] ahci: SSS flag set, parallel bus scan disabled
[    0.636105] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    0.636108] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems 
[    0.636112] ahci 0000:00:1f.2: setting latency timer to 64
[    0.637704] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.637721] r8169 0000:14:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.637759] r8169 0000:14:00.0: setting latency timer to 64
[    0.637804]   alloc irq_desc for 30 on node -1
[    0.637806]   alloc kstat_irqs on node -1
[    0.637818] r8169 0000:14:00.0: irq 30 for MSI/MSI-X
[    0.638261] eth0: RTL8168c/8111c at 0xffffc90000664000, 00:26:22:60:a3:b4, XID 1c4000c0 IRQ 30
[    0.690207] scsi0 : ahci
[    0.690324] scsi1 : ahci
[    0.690371] scsi2 : ahci
[    0.690417] scsi3 : ahci
[    0.690463] scsi4 : ahci
[    0.690519] scsi5 : ahci
[    0.690559] ata1: SATA max UDMA/133 abar m2048@0xf2504000 port 0xf2504100 irq 29
[    0.690562] ata2: SATA max UDMA/133 abar m2048@0xf2504000 port 0xf2504180 irq 29
[    0.690564] ata3: DUMMY
[    0.690565] ata4: DUMMY
[    0.690567] ata5: SATA max UDMA/133 abar m2048@0xf2504000 port 0xf2504300 irq 29
[    0.690569] ata6: SATA max UDMA/133 abar m2048@0xf2504000 port 0xf2504380 irq 29
[    0.860080] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    1.011207] usb 2-2: configuration #1 chosen from 1 choice
[    1.040168] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.085723] ata1.00: ATA-8: ST9320325AS, 0001SDM1, max UDMA/133
[    1.085727] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.087916] ata1.00: configured for UDMA/133
[    1.100140] scsi 0:0:0:0: Direct-Access     ATA      ST9320325AS      0001 PQ: 0 ANSI: 5
[    1.100293] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.100308] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.100350] sd 0:0:0:0: [sda] Write Protect is off
[    1.100352] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.100371] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.100477]  sda: sda1 sda2 < sda5 sda6
[    1.130043] usb 2-3: new high speed USB device using ehci_hcd and address 3
[    1.146179]  sda7 >
[    1.146508] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.324559] usb 2-3: configuration #1 chosen from 1 choice
[    1.850107] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.852753] ata2.00: ATAPI: Slimtype DVD A  DS8A3S, HP51, max UDMA/100, ATAPI AN
[    1.858793] ata2.00: configured for UDMA/100
[    1.883502] scsi 1:0:0:0: CD-ROM            Slimtype DVD A  DS8A3S    HP51 PQ: 0 ANSI: 5
[    1.886931] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda pop-up
[    1.886935] Uniform CD-ROM driver Revision: 3.20
[    1.887043] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.887117] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.230147] ata5: SATA link down (SStatus 0 SControl 300)
[    2.600137] ata6: SATA link down (SStatus 0 SControl 300)
[    8.073653] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   28.048128] udev: starting version 151
[   28.123954] vga16fb: initializing
[   28.123957] vga16fb: mapped to 0xffff8800000a0000
[   28.124007] fb0: VGA16 VGA frame buffer device
[   28.125130] lp: driver loaded but no devices found
[   28.129970] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   28.129974] Disabling lock debugging due to kernel taint
[   28.274883] type=1505 audit(1276848550.194:2):  operation="profile_load" pid=634 name="/sbin/dhclient3"
[   28.275409] type=1505 audit(1276848550.194:3):  operation="profile_load" pid=634 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   28.275693] type=1505 audit(1276848550.194:4):  operation="profile_load" pid=634 name="/usr/lib/connman/scripts/dhclient-script"
[   28.301677] [fglrx] Maximum main memory to use for locked dma buffers: 3768 MBytes.
[   28.301955] [fglrx]   vendor: 1002 device: 9480 count: 1
[   28.302326] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[   28.302342] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.302348] pci 0000:01:00.0: setting latency timer to 64
[   28.302474] [fglrx] Kernel PAT support is enabled
[   28.302491] [fglrx] module loaded - fglrx 8.74.4 [May 27 2010] with 1 minors
[   28.311854] cfg80211: Calling CRDA to update world regulatory domain
[   28.313708] sdhci: Secure Digital Host Controller Interface driver
[   28.313710] sdhci: Copyright(c) Pierre Ossman
[   28.314707] sdhci-pci 0000:02:00.0: SDHCI controller found [197b:2382] (rev 0)
[   28.314729] sdhci-pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.314799] sdhci-pci 0000:02:00.0: setting latency timer to 64
[   28.314837] Registered led device: mmc0::
[   28.314868] mmc0: SDHCI controller on PCI [0000:02:00.0] using ADMA
[   28.314879] sdhci-pci 0000:02:00.2: SDHCI controller found [197b:2381] (rev 0)
[   28.314894] sdhci-pci 0000:02:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.314899] sdhci-pci 0000:02:00.2: Refusing to bind to secondary interface.
[   28.314905] sdhci-pci 0000:02:00.2: PCI INT A disabled
[   28.320862] cfg80211: World regulatory domain updated:
[   28.320864] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   28.320867] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.320870] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.320872] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.320874] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.320876] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.320900] tpm_inf_pnp 00:0a: Found TPM with ID IFX0102
[   28.321746] lirc_dev: IR Remote Control driver registered, major 61 
[   28.322808] jmb38x_ms 0000:02:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.322815] jmb38x_ms 0000:02:00.3: setting latency timer to 64
[   28.323183] lirc_dev: lirc_register_driver: sample_rate: 0
[   28.323275] enecir: unknown ENE chip detected, assuming KB3926D
[   28.323277] enecir: driver support incomplete
[   28.323279] enecir: chip is 0x3926 - 0x00, 0xd2
[   28.323286] enecir: hardware features:
[   28.323288] enecir: learning and tx off, gpio40_learn off, fan_in off
[   28.323290] enecir: driver has been succesfully loaded
[   28.334883] Linux video capture interface: v2.00
[   28.338561] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (064e:a115)
[   28.362769] acpi device:01: registered as cooling_device2
[   28.362896] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input5
[   28.362942] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[   28.376846] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   28.376848] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   28.376959] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   28.376994] iwlagn 0000:0e:00.0: setting latency timer to 64
[   28.377102] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[   28.381939] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/input/input6
[   28.381981] usbcore: registered new interface driver uvcvideo
[   28.381983] USB Video Class driver (v0.1.0)
[   28.436675] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   28.439771]   alloc irq_desc for 31 on node -1
[   28.439773]   alloc kstat_irqs on node -1
[   28.439791] iwlagn 0000:0e:00.0: irq 31 for MSI/MSI-X
[   28.498440] Console: switching to colour frame buffer device 80x30
[   28.508339]   alloc irq_desc for 22 on node -1
[   28.508341]   alloc kstat_irqs on node -1
[   28.508347] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   28.508563] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   28.512780] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   28.667581] hda_codec: ALC268: BIOS auto-probing.
[   28.668103] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   28.675206] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   28.675269] HDA Intel 0000:01:00.1: setting latency timer to 64
[   29.463318] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04711/0xa00000
[   29.496268] iwlagn 0000:0e:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   29.499643] type=1505 audit(1276848551.414:5):  operation="profile_load" pid=916 name="/usr/share/gdm/guest-session/Xsession"
[   29.500966] type=1505 audit(1276848551.424:6):  operation="profile_replace" pid=917 name="/sbin/dhclient3"
[   29.501499] type=1505 audit(1276848551.424:7):  operation="profile_replace" pid=917 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   29.501787] type=1505 audit(1276848551.424:8):  operation="profile_replace" pid=917 name="/usr/lib/connman/scripts/dhclient-script"
[   29.504047] type=1505 audit(1276848551.424:9):  operation="profile_load" pid=918 name="/usr/bin/evince"
[   29.510868] type=1505 audit(1276848551.434:10):  operation="profile_load" pid=918 name="/usr/bin/evince-previewer"
[   29.515034] type=1505 audit(1276848551.434:11):  operation="profile_load" pid=918 name="/usr/bin/evince-thumbnailer"
[   29.524701] iwlagn 0000:0e:00.0: loaded firmware version 8.24.2.12
[   29.559142] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   29.718556] Registered led device: iwl-phy0::radio
[   29.718734] Registered led device: iwl-phy0::assoc
[   29.718954] Registered led device: iwl-phy0::RX
[   29.719253] Registered led device: iwl-phy0::TX
[   29.744257] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.745434] r8169: eth0: link down
[   29.745832] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.902494] ppdev: user-space parallel port driver
[   30.042311]   alloc irq_desc for 32 on node -1
[   30.042313]   alloc kstat_irqs on node -1
[   30.042325] fglrx_pci 0000:01:00.0: irq 32 for MSI/MSI-X
[   30.042801] [fglrx] Firegl kernel thread PID: 1151
[   30.042986] [fglrx] IRQ 32 Enabled
[   30.342579] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   30.503359] [fglrx] Gart USWC size:1228 M.
[   30.503362] [fglrx] Gart cacheable size:487 M.
[   30.503366] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   30.503368] [fglrx] Reserved FB block: Unshared offset:fc27000, size:3d9000 
[   30.503370] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   34.405780] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   40.049375] UDF-fs: Partition marked readonly; forcing readonly mount
[   40.091054] UDF-fs INFO UDF: Mounting volume 'OKAMI', timestamp 2006/09/25 03:35 (1078)
[   41.705811] wlan0: direct probe to AP 00:1c:0e:42:d2:a1 (try 1)
[   41.705834] wlan0: deauthenticating from 00:1c:0e:42:d2:a1 by local choice (reason=3)
[   41.708388] wlan0: direct probe to AP 00:1c:0e:42:b7:41 (try 1)
[   41.900636] wlan0: direct probe to AP 00:1c:0e:42:b7:41 (try 2)
[   41.903784] wlan0: direct probe responded
[   41.903788] wlan0: authenticate with AP 00:1c:0e:42:b7:41 (try 1)
[   42.100058] wlan0: authenticate with AP 00:1c:0e:42:b7:41 (try 2)
[   42.103983] wlan0: authenticated
[   42.104007] wlan0: associate with AP 00:1c:0e:42:b7:41 (try 1)
[   42.107577] wlan0: RX AssocResp from 00:1c:0e:42:b7:41 (capab=0x431 status=0 aid=25)
[   42.107580] wlan0: associated
[   42.110476] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   42.110530] cfg80211: Calling CRDA for country: DK
[   42.112225] cfg80211: Received country IE:
[   42.112227] cfg80211: Regulatory domain: DK
[   42.112228] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   42.112230] 	(2402000 KHz - 2494000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[   42.112232] cfg80211: CRDA thinks this should applied:
[   42.112233] cfg80211: Regulatory domain: DK
[   42.112234] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   42.112236] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   42.112238] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   42.112239] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   42.112241] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   42.112242] cfg80211: We intersect both of these and get:
[   42.112244] cfg80211: Regulatory domain: 98
[   42.112245] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   42.112247] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   42.112250] cfg80211: Leaving channel 5180 MHz intact on phy0 - no rule found in band on Country IE
[   42.112252] cfg80211: Leaving channel 5200 MHz intact on phy0 - no rule found in band on Country IE
[   42.112254] cfg80211: Leaving channel 5220 MHz intact on phy0 - no rule found in band on Country IE
[   42.112256] cfg80211: Leaving channel 5240 MHz intact on phy0 - no rule found in band on Country IE
[   42.112258] cfg80211: Leaving channel 5260 MHz intact on phy0 - no rule found in band on Country IE
[   42.112260] cfg80211: Leaving channel 5280 MHz intact on phy0 - no rule found in band on Country IE
[   42.112262] cfg80211: Leaving channel 5300 MHz intact on phy0 - no rule found in band on Country IE
[   42.112264] cfg80211: Leaving channel 5320 MHz intact on phy0 - no rule found in band on Country IE
[   42.112265] cfg80211: Leaving channel 5500 MHz intact on phy0 - no rule found in band on Country IE
[   42.112267] cfg80211: Leaving channel 5520 MHz intact on phy0 - no rule found in band on Country IE
[   42.112269] cfg80211: Leaving channel 5540 MHz intact on phy0 - no rule found in band on Country IE
[   42.112271] cfg80211: Leaving channel 5560 MHz intact on phy0 - no rule found in band on Country IE
[   42.112273] cfg80211: Leaving channel 5580 MHz intact on phy0 - no rule found in band on Country IE
[   42.112275] cfg80211: Leaving channel 5600 MHz intact on phy0 - no rule found in band on Country IE
[   42.112277] cfg80211: Leaving channel 5620 MHz intact on phy0 - no rule found in band on Country IE
[   42.112278] cfg80211: Leaving channel 5640 MHz intact on phy0 - no rule found in band on Country IE
[   42.112281] cfg80211: Leaving channel 5660 MHz intact on phy0 - no rule found in band on Country IE
[   42.112282] cfg80211: Leaving channel 5680 MHz intact on phy0 - no rule found in band on Country IE
[   42.112284] cfg80211: Leaving channel 5700 MHz intact on phy0 - no rule found in band on Country IE
[   42.112286] cfg80211: Leaving channel 5745 MHz intact on phy0 - no rule found in band on Country IE
[   42.112288] cfg80211: Leaving channel 5765 MHz intact on phy0 - no rule found in band on Country IE
[   42.112290] cfg80211: Leaving channel 5785 MHz intact on phy0 - no rule found in band on Country IE
[   42.112292] cfg80211: Leaving channel 5805 MHz intact on phy0 - no rule found in band on Country IE
[   42.112293] cfg80211: Leaving channel 5825 MHz intact on phy0 - no rule found in band on Country IE
[   42.112297] cfg80211: Current regulatory domain updated by AP to: DK
[   42.112298] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   42.112300] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   52.700086] wlan0: no IPv6 routers present
[   56.482703] wlan0: deauthenticating from 00:1c:0e:42:b7:41 by local choice (reason=3)
[   56.488748] wlan0: deauthenticating from 00:1c:0e:42:b7:41 by local choice (reason=3)
[   56.491408] wlan0: direct probe to AP 00:1c:0e:42:d2:a1 (try 1)
[   56.682596] wlan0: direct probe to AP 00:1c:0e:42:d2:a1 (try 2)
[   56.880141] wlan0: direct probe to AP 00:1c:0e:42:d2:a1 (try 3)
[   56.889983] wlan0: direct probe responded
[   56.889986] wlan0: authenticate with AP 00:1c:0e:42:d2:a1 (try 1)
[   57.080047] wlan0: authenticate with AP 00:1c:0e:42:d2:a1 (try 2)
[   57.085456] wlan0: authenticated
[   57.085476] wlan0: associate with AP 00:1c:0e:42:d2:a1 (try 1)
[   57.108716] wlan0: RX AssocResp from 00:1c:0e:42:d2:a1 (capab=0x431 status=0 aid=14)
[   57.108719] wlan0: associated
[   97.140341] wlan0: deauthenticating from 00:1c:0e:42:d2:a1 by local choice (reason=3)
[  110.144084] wlan0: direct probe to AP 00:1c:0e:42:d2:d1 (try 1)
[  110.157157] wlan0: direct probe responded
[  110.157168] wlan0: authenticate with AP 00:1c:0e:42:d2:d1 (try 1)
[  110.350087] wlan0: authenticate with AP 00:1c:0e:42:d2:d1 (try 2)
[  110.353347] wlan0: authenticated
[  110.353399] wlan0: associate with AP 00:1c:0e:42:d2:d1 (try 1)
[  110.362186] wlan0: RX AssocResp from 00:1c:0e:42:d2:d1 (capab=0x31 status=0 aid=50)
[  110.362194] wlan0: associated
[  239.440122] wlan0: deauthenticating from 00:1c:0e:42:d2:d1 by local choice (reason=3)
[  239.455529] wlan0: direct probe to AP 00:1c:0e:42:d2:d1 (try 1)
[  239.455547] wlan0: deauthenticating from 00:1c:0e:42:d2:d1 by local choice (reason=3)
[  239.459795] wlan0: direct probe to AP 00:1c:0e:42:b7:41 (try 1)
[  239.484469] wlan0: direct probe responded
[  239.484475] wlan0: authenticate with AP 00:1c:0e:42:b7:41 (try 1)
[  239.518264] wlan0: authenticated
[  239.520538] wlan0: associate with AP 00:1c:0e:42:b7:41 (try 1)
[  239.722667] wlan0: associate with AP 00:1c:0e:42:b7:41 (try 2)
[  239.727297] wlan0: RX AssocResp from 00:1c:0e:42:b7:41 (capab=0x431 status=0 aid=25)
[  239.727306] wlan0: associated
[  336.662862] wlan0: deauthenticating from 00:1c:0e:42:b7:41 by local choice (reason=3)
[  336.668081] wlan0: deauthenticating from 00:1c:0e:42:b7:41 by local choice (reason=3)
[  336.672561] wlan0: direct probe to AP 00:1c:0e:42:d2:d1 (try 1)
[  336.872576] wlan0: direct probe to AP 00:1c:0e:42:d2:d1 (try 2)
[  336.882937] wlan0: direct probe responded
[  336.882948] wlan0: authenticate with AP 00:1c:0e:42:d2:d1 (try 1)
[  336.885919] wlan0: authenticated
[  336.885970] wlan0: associate with AP 00:1c:0e:42:d2:d1 (try 1)
[  337.080067] wlan0: associate with AP 00:1c:0e:42:d2:d1 (try 2)
[  337.096299] wlan0: RX AssocResp from 00:1c:0e:42:d2:d1 (capab=0x31 status=0 aid=50)
[  337.096308] wlan0: associated
[  457.512925] wlan0: deauthenticating from 00:1c:0e:42:d2:d1 by local choice (reason=3)
[  457.517599] wlan0: deauthenticating from 00:1c:0e:42:d2:d1 by local choice (reason=3)
[  457.520875] wlan0: direct probe to AP 00:1c:0e:42:b7:41 (try 1)
[  457.710279] wlan0: direct probe to AP 00:1c:0e:42:b7:41 (try 2)
[  457.910079] wlan0: direct probe to AP 00:1c:0e:42:b7:41 (try 3)
[  457.913705] wlan0: direct probe responded
[  457.913716] wlan0: authenticate with AP 00:1c:0e:42:b7:41 (try 1)
[  457.926190] wlan0: authenticated
[  457.926248] wlan0: associate with AP 00:1c:0e:42:b7:41 (try 1)
[  458.120673] wlan0: associate with AP 00:1c:0e:42:b7:41 (try 2)
[  458.128090] wlan0: RX AssocResp from 00:1c:0e:42:b7:41 (capab=0x431 status=0 aid=25)
[  458.128098] wlan0: associated
[  696.332752] wlan0: deauthenticating from 00:1c:0e:42:b7:41 by local choice (reason=3)
[  696.378262] wlan0: deauthenticating from 00:1c:0e:42:b7:41 by local choice (reason=3)
[  696.391197] wlan0: direct probe to AP 00:1c:0e:42:d2:d1 (try 1)
[  696.516466] wlan0: direct probe responded
[  696.516472] wlan0: authenticate with AP 00:1c:0e:42:d2:d1 (try 1)
[  696.710304] wlan0: authenticate with AP 00:1c:0e:42:d2:d1 (try 2)
[  696.713217] wlan0: authenticated
[  696.713270] wlan0: associate with AP 00:1c:0e:42:d2:d1 (try 1)
[  696.731202] wlan0: RX AssocResp from 00:1c:0e:42:d2:d1 (capab=0x31 status=0 aid=50)
[  696.731210] wlan0: associated
[  746.339285] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[  746.526009] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[  746.657390] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[  746.800706] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[  746.873084] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[  746.979981] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[  747.082884] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[  747.193621] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[  747.292360] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[  747.435316] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
[  884.188790] CE: hpet increasing min_delta_ns to 15000 nsec

```

> 
Thats what happen when user blindly apply updates without looking at comments attached, just reinstall the packages beeing removed 
I did not remove them myself, plymouth just started up and removed them for me and there was nothing I could do to stop it. 
These kinds of errors are the reason why Linux isn't ready for the consumer market. As long as this sort of stuff even happens - heck as long as the package manager may pop up at any time and recommend a partial upgrade that breaks a system, Linux is not ready. It had been nagging me for weeks but I had been brushing me off, and now it just decided to put PC out of its misery apparently. I'm barely able to recover over here.
The big problem here is it may have removed packages I am not aware of. I don't have a list. It just ran through a bunch of scripts and removed stuff, but it moved so fast I only caught laptop-mode and evolution.

---

### Post by gradinaruvasile on 2010-06-18
The laptop-mode package exists in the Ubuntu repos. You should install it from there to ensure you will have it updated.
I also suggest reinstalling evolution - it is a core gnome component and that is bad to have it removed (i hate it too). It has deep dependencies and it just might removed some needed packages.

And how the heck did this happen? The update manager runs automatically before gdm or something?

---

### Post by TheDesertDragon on 2010-06-18
I have marked this thread as solved because my laptop is basically back up and running completely now, but Evolution is still missing, and it cannot be installed due to an issue with existing Evolution packages that didn't go away, aren't broken, and can't be removed without removing nearly the entire OS basically. O.o

And I don't know how this happened. When I started the computer plymouth was shown with the Ubuntu logo as normal and it started posting messages you typically see from aptitude.

I'm assuming it's the updating stuff because as I said the update manager had been starting up on its own for a while and nagged me to do a partial upgrade. Sometimes the update manager just showing up would remove the theme compatability from Nautilus until restart so I just pressed no because I had read of these sorts of incidents.
It coincided with being the first time I did a hard reboot since I installed ATi's FGLRX 10.6 from ati.amd.com.

EDIT:
Also, the author of laptop-mode raised some critique against Ubuntu's versions. He said Ubuntu hasn't updated Laptop-mode since waaaaaay back so they are very outdated and he recommends that I install it via dpkg from his site.

EDIT2:
Output of sudo apt-get install evolution -f
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  evolution: Depends: evolution-common (= 2.28.3-0ubuntu10) but 2.28.3-1ubuntu9~ppa0 is to be installed
E: Broken packages

```

This is funny because it was removed.

---

### Post by gradinaruvasile on 2010-06-18
2.28.3-1ubuntu9~[COLOR="Red"]ppa0[/COLOR] - this means you have some custom PPA installed - id say you find and disable it, this is what broke your system.

It interferes with the normal Ubuntu repositories. You will have problems like this until you remove this PPA.

What is the output of 

cat /etc/apt/sources.list

?

Edit: You have by chance "TSBarnes' Misc. Packages" PPA installed?

---

### Post by TheDesertDragon on 2010-06-18
> **gradinaruvasile said:**
> 2.28.3-1ubuntu9~[COLOR="Red"]ppa0[/COLOR] - this means you have some custom PPA installed - id say you find and disable it, this is what broke your system.

It interferes with the normal Ubuntu repositories. You will have problems like this until you remove this PPA.

What is the output of 

cat /etc/apt/sources.list

?

Edit: You have by chance "TSBarnes' Misc. Packages" PPA installed?

I do.
I don't know how it got there,  but I do.
Should I remove it?

EDIT:
In addition, I seem to have 16 packages installed from it, including several packages related to Evolution.
Have we tracked down the problem?

The packages in question are:
```

evolution-data-server
evolution-data-server-common
gnome-window-applets
libcamel
libebackend
libebook
libecal
libedata-book
libedate-cal
libedataserver
libedataserverui
libegroupwise
libexchange-storage
libgdata-google
libgdata
windowapplets

```

I think what's caused this is me wanting to casually try the new global menu alpha developed by Ubuntu. Installing the basic .deb package, I had no clue that it would cause something like this.

---

