---
title: "Pulling my hair out(whats left of it)"
date: 2010-07-19
forum: General Help
---

### Post by Donalt2010 on 2010-07-19
And im only 27!! Hey guys im practically new round these parts and with Ubuntu as a whole, i managed to install Lucid Lynx onto my desktop, but bought a brand new Msi CR610 laptop today with windows 7 which i totally removed (bad idea)? i dunno. And put Lucid Lynx onto it as a clean install... I managed to get my wifi working after a few reboots. But now trying to get the webcam working on it and not having much luck finding any info on it.. Apparently its called a simple camera as i checked the driver cd just out of curiousity. Bluetooth is working fine aswell... totally baffled:(

donal@donal-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0db0:3801 Micro Star International 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

There doesnt seem to be any hint of a camera there, also installed cheese cam and camera monitor from Ubuntu software centre.

I know theres  alot of very smart people on here so any of your words of wisdom would be very greatfully appreciated, maybe a step by step guide is the best option for a noob like myself.

Regards
Donal

---

### Post by elricscripts on 2010-07-19
This is all i can do to help:[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)


Hope you find a solution.

---

### Post by Donalt2010 on 2010-07-21
After my first post the camera worked, then turned my laptop on earlier and its not working again. Cheesecam is comming up with /dev/video0. 

Thanks for your reply but that only seems to be for usb cameras, as mine is integrated thats irrelevant to me.

Heads fried. Anybody else with any other help please........

Regards
DonalT

---

### Post by davidmohammed on 2010-07-21
if the webcam cant be found as a usb device, it must be part of the hardware devices.


Can you dump the contents of

lspci

here in between code tags in your reply.

...

also have at a look at your system logs (kernel) - dump the contents of the kernel log here in code tags

---

### Post by Donalt2010 on 2010-07-21
Yea its a hardware issue, but for some reason was working then not. I tried the gstreamer-properties thing in terminal and tested linux2 /dev/device0 wasnt found here are the results:

donal@donal-laptop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device "/dev/video0". [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src1:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device "/dev/video0". [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline2/GstV4l2Src:v4l2src2:
system error: No such file or directory]

donal@donal-laptop:~$ ispci
No command 'ispci' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
ispci: command not found
donal@donal-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
donal@donal-laptop:~$ 


Regards
DonalT

---

### Post by davidmohammed on 2010-07-21
...

also have at a look at your system logs (kernel) - dump the contents of the kernel log here in code tags

---

### Post by Donalt2010 on 2010-07-21
Sorry, how do i go about doing that. Thanks.

Regards
DonalT

---

### Post by davidmohammed on 2010-07-21
...

ok sorry - 

administrator - log file viewer

left hand side.  Click on kern.log..
 from the menu - edit select all - and then edit - copy.

Paste the contents here in code tags

---

### Post by Donalt2010 on 2010-07-21
For some reason its stalling when i click on post, to post the kernel.. should i post it one at a time?

Not letting post the kernel one at a time either its timing out.

---

### Post by davidmohammed on 2010-07-21
suggest - click the + next to kern.log.  It will display the days of the week.  Click on the current date log.

Have a look at the log in the right hand side of the screen.  Scroll towards the bottom - you'll notice the time changes.

Highlight the log from the time you last booted to the bottom of the page.  Edit - Copy and the paste into the forum reply.

---

### Post by Donalt2010 on 2010-07-21
Hope this is what you mean:
Jul 21 19:13:32 donal-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Linux version 2.6.32-23-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 (Ubuntu 2.6.32-23.37-generic 2.6.32.15+drm33.5)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] KERNEL supported cpus:
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   Intel GenuineIntel
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   AMD AuthenticAMD
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   NSC Geode by NSC
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   Cyrix CyrixInstead
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   Centaur CentaurHauls
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   Transmeta GenuineTMx86
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   Transmeta TransmetaCPU
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   UMC UMC UMC UMC
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffb0000 (usable)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  BIOS-e820: 00000000cffb0000 - 00000000cffbe000 (ACPI data)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  BIOS-e820: 00000000cffbe000 - 00000000cffe0000 (ACPI NVS)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  BIOS-e820: 00000000cffe0000 - 00000000d0000000 (reserved)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] DMI present.
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] last_pfn = 0xcffb0 max_arch_pfn = 0x100000
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] MTRR default type: uncachable
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] MTRR fixed ranges enabled:
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   00000-9FFFF write-back
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   A0000-EFFFF uncachable
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   F0000-FFFFF write-protect
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] MTRR variable ranges enabled:
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   3 disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   4 disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   5 disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   6 disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   7 disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] TOM2: 0000000130000000 aka 4864M
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] modified physical RAM map:
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  modified: 0000000000100000 - 00000000cffb0000 (usable)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  modified: 00000000cffb0000 - 00000000cffbe000 (ACPI data)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  modified: 00000000cffbe000 - 00000000cffe0000 (ACPI NVS)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  modified: 00000000cffe0000 - 00000000d0000000 (reserved)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] RAMDISK: 37858000 - 37fefb8f
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Allocated new RAMDISK: 008e0000 - 01077b8f
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Move RAMDISK from 0000000037858000 - 0000000037fefb8e to 008e0000 - 01077b8e
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: RSDP 000f96b0 00024 (v02 M S I )
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: XSDT cffb0100 0005C (v01 MSI_NB MEGABOOK 02212010 MSFT 00000097)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: FACP cffb0290 000F4 (v04 M S I  MEGABOOK 02212010 MSFT 00000097)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0000000000000000/1 (20090903/tbfadt-557)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: DSDT cffb05b0 06A3A (v02 MSI    1684     02212010 INTL 20051117)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: FACS cffbe000 00040
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: APIC cffb0390 0005C (v02 M S I  MEGABOOK 02212010 MSFT 00000097)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: MCFG cffb03f0 0003C (v01 M S I  1684     02212010 MSFT 00000097)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: SLIC cffb0430 00176 (v01 MSI_NB MEGABOOK 02212010 MSFT 00000097)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: OEMB cffbe040 00072 (v01 M S I  MEGABOOK 02212010 MSFT 00000097)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: HPET cffba5b0 00038 (v01 M S I  1684     02212010 MSFT 00000097)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: SSDT cffba5f0 003F0 (v01 A M I  POWERNOW 00000001 AMD  00000001)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] 2439MB HIGHMEM available.
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] 887MB LOWMEM available.
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   low ram: 0 - 377fe000
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   #5 [00008dc000 - 00008df183]              BRK ==> [00008dc000 - 00008df183]
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   #7 [00008e0000 - 0001077b8f]      NEW RAMDISK ==> [00008e0000 - 0001077b8f]
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] found SMP MP-table at [c00ff780] ff780
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Zone PFN ranges:
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   HighMem  0x000377fe -> 0x000cffb0
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Movable zone start PFN for each node
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x000cffb0
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] On node 0 totalpages: 851775
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] free_area_init_node: node 0, pgdat c0798760, node_mem_map c1079200
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   HighMem zone: 4880 pages used for memmap
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   HighMem zone: 619682 pages, LIFO batch:31
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Using APIC driver default
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] nr_irqs_gsi: 24
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2f700000)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2c00000 s36056 r0 d21288 u2097152
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 845119
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic root=UUID=91b2ac8c-ff7a-4e32-8d63-ee6fdd006fe8 ro quiet splash
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Initializing CPU#0
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] allocated 17037440 bytes of page_cgroup
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000cffb0)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Memory: 3346032k/3407552k available (4676k kernel code, 60100k reserved, 2118k data, 660k init, 2498248k highmem)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] virtual kernel memory layout:
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]       .data : 0xc0591293 - 0xc07a2e88   (2118 kB)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0591293   (4676 kB)
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Hierarchical RCU implementation.
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Extended CMOS year: 2000
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Console: colour VGA+ 80x25
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] console [tty0] enabled
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] hpet clockevent registered
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   alloc irq_desc for 24 on node 0
Jul 21 19:13:32 donal-laptop kernel: [    0.000000]   alloc kstat_irqs on node 0
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Jul 21 19:13:32 donal-laptop kernel: [    0.000000] Detected 1994.419 MHz processor.
Jul 21 19:13:32 donal-laptop kernel: [    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3988.83 BogoMIPS (lpj=7977676)
Jul 21 19:13:32 donal-laptop kernel: [    0.004019] Security Framework initialized
Jul 21 19:13:32 donal-laptop kernel: [    0.004030] AppArmor: AppArmor initialized
Jul 21 19:13:32 donal-laptop kernel: [    0.004036] Mount-cache hash table entries: 512
Jul 21 19:13:32 donal-laptop kernel: [    0.004133] Initializing cgroup subsys ns
Jul 21 19:13:32 donal-laptop kernel: [    0.004137] Initializing cgroup subsys cpuacct
Jul 21 19:13:32 donal-laptop kernel: [    0.004140] Initializing cgroup subsys memory
Jul 21 19:13:32 donal-laptop kernel: [    0.004146] Initializing cgroup subsys devices
Jul 21 19:13:32 donal-laptop kernel: [    0.004149] Initializing cgroup subsys freezer
Jul 21 19:13:32 donal-laptop kernel: [    0.004151] Initializing cgroup subsys net_cls
Jul 21 19:13:32 donal-laptop kernel: [    0.004165] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 21 19:13:32 donal-laptop kernel: [    0.004168] CPU: L2 Cache: 512K (64 bytes/line)
Jul 21 19:13:32 donal-laptop kernel: [    0.004170] CPU: Physical Processor ID: 0
Jul 21 19:13:32 donal-laptop kernel: [    0.004172] CPU: Processor Core ID: 0
Jul 21 19:13:32 donal-laptop kernel: [    0.004175] mce: CPU supports 6 MCE banks
Jul 21 19:13:32 donal-laptop kernel: [    0.004184] using C1E aware idle routine
Jul 21 19:13:32 donal-laptop kernel: [    0.004190] Performance Events: AMD PMU driver.
Jul 21 19:13:32 donal-laptop kernel: [    0.004195] ... version:                0
Jul 21 19:13:32 donal-laptop kernel: [    0.004197] ... bit width:              48
Jul 21 19:13:32 donal-laptop kernel: [    0.004199] ... generic registers:      4
Jul 21 19:13:32 donal-laptop kernel: [    0.004201] ... value mask:             0000ffffffffffff
Jul 21 19:13:32 donal-laptop kernel: [    0.004203] ... max period:             00007fffffffffff
Jul 21 19:13:32 donal-laptop kernel: [    0.004204] ... fixed-purpose events:   0
Jul 21 19:13:32 donal-laptop kernel: [    0.004206] ... event mask:             000000000000000f
Jul 21 19:13:32 donal-laptop kernel: [    0.004210] Checking 'hlt' instruction... OK.
Jul 21 19:13:32 donal-laptop kernel: [    0.022145] ACPI: Core revision 20090903
Jul 21 19:13:32 donal-laptop kernel: [    0.032008] ftrace: converting mcount calls to 0f 1f 44 00 00
Jul 21 19:13:32 donal-laptop kernel: [    0.032012] ftrace: allocating 21776 entries in 43 pages
Jul 21 19:13:32 donal-laptop kernel: [    0.036109] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 21 19:13:32 donal-laptop kernel: [    0.036452] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 21 19:13:32 donal-laptop kernel: [    0.076434] CPU0: AMD Athlon(tm) II Dual-Core M300 stepping 02
Jul 21 19:13:32 donal-laptop kernel: [    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
Jul 21 19:13:32 donal-laptop kernel: [    0.008000] Initializing CPU#1
Jul 21 19:13:32 donal-laptop kernel: [    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 21 19:13:32 donal-laptop kernel: [    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
Jul 21 19:13:32 donal-laptop kernel: [    0.008000] CPU: Physical Processor ID: 0
Jul 21 19:13:32 donal-laptop kernel: [    0.008000] CPU: Processor Core ID: 1
Jul 21 19:13:32 donal-laptop kernel: [    0.164078] CPU1: AMD Athlon(tm) II Dual-Core M300 stepping 02
Jul 21 19:13:32 donal-laptop kernel: [    0.164123] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jul 21 19:13:32 donal-laptop kernel: [    0.168014] Brought up 2 CPUs
Jul 21 19:13:32 donal-laptop kernel: [    0.168017] Total of 2 processors activated (7977.83 BogoMIPS).
Jul 21 19:13:32 donal-laptop kernel: [    0.168021] System has AMD C1E enabled
Jul 21 19:13:32 donal-laptop kernel: [    0.168046] Switch to broadcast mode on CPU1
Jul 21 19:13:32 donal-laptop kernel: [    0.168207] CPU0 attaching sched-domain:
Jul 21 19:13:32 donal-laptop kernel: [    0.168210]  domain 0: span 0-1 level MC
Jul 21 19:13:32 donal-laptop kernel: [    0.168212]   groups: 0 1
Jul 21 19:13:32 donal-laptop kernel: [    0.168218] CPU1 attaching sched-domain:
Jul 21 19:13:32 donal-laptop kernel: [    0.168220]  domain 0: span 0-1 level MC
Jul 21 19:13:32 donal-laptop kernel: [    0.168222]   groups: 1 0
Jul 21 19:13:32 donal-laptop kernel: [    0.168294] Switch to broadcast mode on CPU0
Jul 21 19:13:32 donal-laptop kernel: [    0.168294] devtmpfs: initialized
Jul 21 19:13:32 donal-laptop kernel: [    0.168294] regulator: core version 0.5
Jul 21 19:13:32 donal-laptop kernel: [    0.168294] Time: 19:13:20  Date: 07/21/10
Jul 21 19:13:32 donal-laptop kernel: [    0.168294] NET: Registered protocol family 16
Jul 21 19:13:32 donal-laptop kernel: [    0.168294] EISA bus registered
Jul 21 19:13:32 donal-laptop kernel: [    0.168294] ACPI: bus type pci registered
Jul 21 19:13:32 donal-laptop kernel: [    0.168294] Trying to unpack rootfs image as initramfs...
Jul 21 19:13:32 donal-laptop kernel: [    0.168304] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jul 21 19:13:32 donal-laptop kernel: [    0.168307] PCI: Not using MMCONFIG.
Jul 21 19:13:32 donal-laptop kernel: [    0.169072] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
Jul 21 19:13:32 donal-laptop kernel: [    0.169074] PCI: Using configuration type 1 for base access
Jul 21 19:13:32 donal-laptop kernel: [    0.169076] PCI: Using configuration type 1 for extended access
Jul 21 19:13:32 donal-laptop kernel: [    0.172158] bio: create slab <bio-0> at 0
Jul 21 19:13:32 donal-laptop kernel: [    0.172992] ACPI: EC: Detected MSI hardware, enabling workarounds.
Jul 21 19:13:32 donal-laptop kernel: [    0.172995] ACPI: EC: Look up EC in DSDT
Jul 21 19:13:32 donal-laptop kernel: [    0.174061] ACPI: Executed 1 blocks of module-level executable AML code
Jul 21 19:13:32 donal-laptop kernel: [    0.177608] ACPI: BIOS _OSI(Linux) query ignored
Jul 21 19:13:32 donal-laptop kernel: [    0.181140] ACPI: Interpreter enabled
Jul 21 19:13:32 donal-laptop kernel: [    0.181150] ACPI: (supports S0 S3 S4 S5)
Jul 21 19:13:32 donal-laptop kernel: [    0.181171] ACPI: Using IOAPIC for interrupt routing
Jul 21 19:13:32 donal-laptop kernel: [    0.181322] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jul 21 19:13:32 donal-laptop kernel: [    0.183531] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Jul 21 19:13:32 donal-laptop kernel: [    0.183533] PCI: Using MMCONFIG for extended config space
Jul 21 19:13:32 donal-laptop kernel: [    0.190433] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
Jul 21 19:13:32 donal-laptop kernel: [    0.190683] ACPI: No dock devices found.
Jul 21 19:13:32 donal-laptop kernel: [    0.191379] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 21 19:13:32 donal-laptop kernel: [    0.191545] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
Jul 21 19:13:32 donal-laptop kernel: [    0.191549] pci 0000:00:04.0: PME# disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.191628] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Jul 21 19:13:32 donal-laptop kernel: [    0.191631] pci 0000:00:06.0: PME# disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.191671] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
Jul 21 19:13:32 donal-laptop kernel: [    0.191674] pci 0000:00:09.0: PME# disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.191769] pci 0000:00:11.0: reg 10 io port: [0xb000-0xb007]
Jul 21 19:13:32 donal-laptop kernel: [    0.191776] pci 0000:00:11.0: reg 14 io port: [0xa000-0xa003]
Jul 21 19:13:32 donal-laptop kernel: [    0.191784] pci 0000:00:11.0: reg 18 io port: [0x9000-0x9007]
Jul 21 19:13:32 donal-laptop kernel: [    0.191791] pci 0000:00:11.0: reg 1c io port: [0x8000-0x8003]
Jul 21 19:13:32 donal-laptop kernel: [    0.191798] pci 0000:00:11.0: reg 20 io port: [0x7000-0x700f]
Jul 21 19:13:32 donal-laptop kernel: [    0.191806] pci 0000:00:11.0: reg 24 32bit mmio: [0xfdbffc00-0xfdbfffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.191859] pci 0000:00:12.0: reg 10 32bit mmio: [0xfdbfe000-0xfdbfefff]
Jul 21 19:13:32 donal-laptop kernel: [    0.191914] pci 0000:00:12.1: reg 10 32bit mmio: [0xfdbfd000-0xfdbfdfff]
Jul 21 19:13:32 donal-laptop kernel: [    0.191988] pci 0000:00:12.2: reg 10 32bit mmio: [0xfdbff800-0xfdbff8ff]
Jul 21 19:13:32 donal-laptop kernel: [    0.192048] pci 0000:00:12.2: supports D1 D2
Jul 21 19:13:32 donal-laptop kernel: [    0.192050] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jul 21 19:13:32 donal-laptop kernel: [    0.192054] pci 0000:00:12.2: PME# disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.192087] pci 0000:00:13.0: reg 10 32bit mmio: [0xfdbfc000-0xfdbfcfff]
Jul 21 19:13:32 donal-laptop kernel: [    0.192162] pci 0000:00:13.2: reg 10 32bit mmio: [0xfdbff400-0xfdbff4ff]
Jul 21 19:13:32 donal-laptop kernel: [    0.192215] pci 0000:00:13.2: supports D1 D2
Jul 21 19:13:32 donal-laptop kernel: [    0.192217] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jul 21 19:13:32 donal-laptop kernel: [    0.192221] pci 0000:00:13.2: PME# disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.192340] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
Jul 21 19:13:32 donal-laptop kernel: [    0.192347] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
Jul 21 19:13:32 donal-laptop kernel: [    0.192354] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
Jul 21 19:13:32 donal-laptop kernel: [    0.192361] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
Jul 21 19:13:32 donal-laptop kernel: [    0.192368] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
Jul 21 19:13:32 donal-laptop kernel: [    0.192438] pci 0000:00:14.2: reg 10 64bit mmio: [0xfdbf8000-0xfdbfbfff]
Jul 21 19:13:32 donal-laptop kernel: [    0.192481] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jul 21 19:13:32 donal-laptop kernel: [    0.192486] pci 0000:00:14.2: PME# disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.192689] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.192693] pci 0000:01:05.0: reg 14 io port: [0xc000-0xc0ff]
Jul 21 19:13:32 donal-laptop kernel: [    0.192697] pci 0000:01:05.0: reg 18 32bit mmio: [0xfddf0000-0xfddfffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.192705] pci 0000:01:05.0: reg 24 32bit mmio: [0xfdc00000-0xfdcfffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.192718] pci 0000:01:05.0: supports D1 D2
Jul 21 19:13:32 donal-laptop kernel: [    0.192737] pci 0000:01:05.1: reg 10 32bit mmio: [0xfdde8000-0xfddebfff]
Jul 21 19:13:32 donal-laptop kernel: [    0.192758] pci 0000:01:05.1: supports D1 D2
Jul 21 19:13:32 donal-laptop kernel: [    0.192833] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
Jul 21 19:13:32 donal-laptop kernel: [    0.192836] pci 0000:00:01.0: bridge 32bit mmio: [0xfdc00000-0xfddfffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.192840] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.192875] pci 0000:02:00.0: reg 10 32bit mmio: [0xfdef0000-0xfdefffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.193013] pci 0000:00:04.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.193051] pci 0000:03:00.0: reg 10 io port: [0xd800-0xd8ff]
Jul 21 19:13:32 donal-laptop kernel: [    0.193066] pci 0000:03:00.0: reg 18 64bit mmio pref: [0xf9fff000-0xf9ffffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.193078] pci 0000:03:00.0: reg 20 64bit mmio pref: [0xf9ff8000-0xf9ffbfff]
Jul 21 19:13:32 donal-laptop kernel: [    0.193085] pci 0000:03:00.0: reg 30 32bit mmio pref: [0xfdfe0000-0xfdffffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.193115] pci 0000:03:00.0: supports D1 D2
Jul 21 19:13:32 donal-laptop kernel: [    0.193117] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 21 19:13:32 donal-laptop kernel: [    0.193121] pci 0000:03:00.0: PME# disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.193182] pci 0000:00:06.0: bridge io port: [0xd000-0xdfff]
Jul 21 19:13:32 donal-laptop kernel: [    0.193186] pci 0000:00:06.0: bridge 32bit mmio: [0xfdf00000-0xfdffffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.193190] pci 0000:00:06.0: bridge 64bit mmio pref: [0xf9f00000-0xf9ffffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.193237] pci 0000:00:09.0: bridge io port: [0xe000-0xefff]
Jul 21 19:13:32 donal-laptop kernel: [    0.193240] pci 0000:00:09.0: bridge 32bit mmio: [0xfe000000-0xfebfffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.193244] pci 0000:00:09.0: bridge 64bit mmio pref: [0xfa000000-0xfcffffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.193302] pci 0000:00:14.4: transparent bridge
Jul 21 19:13:32 donal-laptop kernel: [    0.193325] pci_bus 0000:00: on NUMA node 0
Jul 21 19:13:32 donal-laptop kernel: [    0.193329] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul 21 19:13:32 donal-laptop kernel: [    0.193570] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Jul 21 19:13:32 donal-laptop kernel: [    0.193642] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
Jul 21 19:13:32 donal-laptop kernel: [    0.193704] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
Jul 21 19:13:32 donal-laptop kernel: [    0.193764] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
Jul 21 19:13:32 donal-laptop kernel: [    0.193859] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
Jul 21 19:13:32 donal-laptop kernel: [    0.198960] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Jul 21 19:13:32 donal-laptop kernel: [    0.199106] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Jul 21 19:13:32 donal-laptop kernel: [    0.199255] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Jul 21 19:13:32 donal-laptop kernel: [    0.199440] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Jul 21 19:13:32 donal-laptop kernel: [    0.199627] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Jul 21 19:13:32 donal-laptop kernel: [    0.199735] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Jul 21 19:13:32 donal-laptop kernel: [    0.199919] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Jul 21 19:13:32 donal-laptop kernel: [    0.200111] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Jul 21 19:13:32 donal-laptop kernel: [    0.200259] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
Jul 21 19:13:32 donal-laptop kernel: [    0.200263] vgaarb: loaded
Jul 21 19:13:32 donal-laptop kernel: [    0.200368] SCSI subsystem initialized
Jul 21 19:13:32 donal-laptop kernel: [    0.200447] libata version 3.00 loaded.
Jul 21 19:13:32 donal-laptop kernel: [    0.200505] usbcore: registered new interface driver usbfs
Jul 21 19:13:32 donal-laptop kernel: [    0.200516] usbcore: registered new interface driver hub
Jul 21 19:13:32 donal-laptop kernel: [    0.200541] usbcore: registered new device driver usb
Jul 21 19:13:32 donal-laptop kernel: [    0.200708] ACPI: WMI: Mapper loaded
Jul 21 19:13:32 donal-laptop kernel: [    0.200709] PCI: Using ACPI for IRQ routing
Jul 21 19:13:32 donal-laptop kernel: [    0.200907] NetLabel: Initializing
Jul 21 19:13:32 donal-laptop kernel: [    0.200909] NetLabel:  domain hash size = 128
Jul 21 19:13:32 donal-laptop kernel: [    0.200911] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 21 19:13:32 donal-laptop kernel: [    0.200923] NetLabel:  unlabeled traffic allowed by default
Jul 21 19:13:32 donal-laptop kernel: [    0.200988] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
Jul 21 19:13:32 donal-laptop kernel: [    0.200994] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Jul 21 19:13:32 donal-laptop kernel: [    0.203026] Switching to clocksource tsc
Jul 21 19:13:32 donal-laptop kernel: [    0.203098] AppArmor: AppArmor Filesystem Enabled
Jul 21 19:13:32 donal-laptop kernel: [    0.203098] pnp: PnP ACPI init
Jul 21 19:13:32 donal-laptop kernel: [    0.203098] ACPI: bus type pnp registered
Jul 21 19:13:32 donal-laptop kernel: [    0.204843] pnp: PnP ACPI: found 13 devices
Jul 21 19:13:32 donal-laptop kernel: [    0.204845] ACPI: ACPI bus type pnp unregistered
Jul 21 19:13:32 donal-laptop kernel: [    0.204849] PnPBIOS: Disabled by ACPI PNP
Jul 21 19:13:32 donal-laptop kernel: [    0.204864] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204867] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204874] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204876] system 00:08: ioport range 0x40b-0x40b has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204879] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204882] system 00:08: ioport range 0xc00-0xc01 has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204885] system 00:08: ioport range 0xc14-0xc14 has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204888] system 00:08: ioport range 0xc50-0xc51 has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204890] system 00:08: ioport range 0xc52-0xc52 has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204893] system 00:08: ioport range 0xc6c-0xc6c has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204896] system 00:08: ioport range 0xc6f-0xc6f has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204899] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204901] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204904] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204907] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204910] system 00:08: ioport range 0xcd8-0xcdf has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204913] system 00:08: ioport range 0x800-0x89f has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204915] system 00:08: ioport range 0xb00-0xb0f has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204918] system 00:08: ioport range 0xb20-0xb3f has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204921] system 00:08: ioport range 0x900-0x90f has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204936] system 00:08: ioport range 0x910-0x91f has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204940] system 00:08: ioport range 0xfe00-0xfefe has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204942] system 00:08: ioport range 0xf50-0xf50 has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204946] system 00:08: iomem range 0xffb80000-0xffbfffff has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204950] system 00:08: iomem range 0xfec10000-0xfec1001f has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204956] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204961] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204964] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204967] system 00:0c: iomem range 0x100000-0xcfffffff could not be reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.204970] system 00:0c: iomem range 0xfec00000-0xffffffff could not be reserved
Jul 21 19:13:32 donal-laptop kernel: [    0.239889] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Jul 21 19:13:32 donal-laptop kernel: [    0.239892] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
Jul 21 19:13:32 donal-laptop kernel: [    0.239896] pci 0000:00:01.0:   MEM window: 0xfdc00000-0xfddfffff
Jul 21 19:13:32 donal-laptop kernel: [    0.239899] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Jul 21 19:13:32 donal-laptop kernel: [    0.239904] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
Jul 21 19:13:32 donal-laptop kernel: [    0.239906] pci 0000:00:04.0:   IO window: disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.239909] pci 0000:00:04.0:   MEM window: 0xfde00000-0xfdefffff
Jul 21 19:13:32 donal-laptop kernel: [    0.239912] pci 0000:00:04.0:   PREFETCH window: disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.239916] pci 0000:00:06.0: PCI bridge, secondary bus 0000:03
Jul 21 19:13:32 donal-laptop kernel: [    0.239919] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
Jul 21 19:13:32 donal-laptop kernel: [    0.239922] pci 0000:00:06.0:   MEM window: 0xfdf00000-0xfdffffff
Jul 21 19:13:32 donal-laptop kernel: [    0.239925] pci 0000:00:06.0:   PREFETCH window: 0x000000f9f00000-0x000000f9ffffff
Jul 21 19:13:32 donal-laptop kernel: [    0.239929] pci 0000:00:09.0: PCI bridge, secondary bus 0000:04
Jul 21 19:13:32 donal-laptop kernel: [    0.239932] pci 0000:00:09.0:   IO window: 0xe000-0xefff
Jul 21 19:13:32 donal-laptop kernel: [    0.239935] pci 0000:00:09.0:   MEM window: 0xfe000000-0xfebfffff
Jul 21 19:13:32 donal-laptop kernel: [    0.239938] pci 0000:00:09.0:   PREFETCH window: 0x000000fa000000-0x000000fcffffff
Jul 21 19:13:32 donal-laptop kernel: [    0.239942] pci 0000:00:14.4: PCI bridge, secondary bus 0000:06
Jul 21 19:13:32 donal-laptop kernel: [    0.239944] pci 0000:00:14.4:   IO window: disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.239983] pci 0000:00:14.4:   MEM window: disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.239987] pci 0000:00:14.4:   PREFETCH window: disabled
Jul 21 19:13:32 donal-laptop kernel: [    0.240003]   alloc irq_desc for 16 on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.240005]   alloc kstat_irqs on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.240010] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 21 19:13:32 donal-laptop kernel: [    0.240013] pci 0000:00:04.0: setting latency timer to 64
Jul 21 19:13:32 donal-laptop kernel: [    0.240019]   alloc irq_desc for 18 on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.240020]   alloc kstat_irqs on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.240024] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 21 19:13:32 donal-laptop kernel: [    0.240027] pci 0000:00:06.0: setting latency timer to 64
Jul 21 19:13:32 donal-laptop kernel: [    0.240032]   alloc irq_desc for 17 on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.240034]   alloc kstat_irqs on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.240036] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 21 19:13:32 donal-laptop kernel: [    0.240039] pci 0000:00:09.0: setting latency timer to 64
Jul 21 19:13:32 donal-laptop kernel: [    0.240048] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.240050] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.240053] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
Jul 21 19:13:32 donal-laptop kernel: [    0.240056] pci_bus 0000:01: resource 1 mem: [0xfdc00000-0xfddfffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.240058] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.240061] pci_bus 0000:02: resource 1 mem: [0xfde00000-0xfdefffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.240064] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
Jul 21 19:13:32 donal-laptop kernel: [    0.240066] pci_bus 0000:03: resource 1 mem: [0xfdf00000-0xfdffffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.240069] pci_bus 0000:03: resource 2 pref mem [0xf9f00000-0xf9ffffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.240072] pci_bus 0000:04: resource 0 io:  [0xe000-0xefff]
Jul 21 19:13:32 donal-laptop kernel: [    0.240074] pci_bus 0000:04: resource 1 mem: [0xfe000000-0xfebfffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.240077] pci_bus 0000:04: resource 2 pref mem [0xfa000000-0xfcffffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.240079] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.240082] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
Jul 21 19:13:32 donal-laptop kernel: [    0.240116] NET: Registered protocol family 2
Jul 21 19:13:32 donal-laptop kernel: [    0.240206] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 21 19:13:32 donal-laptop kernel: [    0.240500] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 21 19:13:32 donal-laptop kernel: [    0.241060] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 21 19:13:32 donal-laptop kernel: [    0.241325] TCP: Hash tables configured (established 131072 bind 65536)
Jul 21 19:13:32 donal-laptop kernel: [    0.241327] TCP reno registered
Jul 21 19:13:32 donal-laptop kernel: [    0.241418] NET: Registered protocol family 1
Jul 21 19:13:32 donal-laptop kernel: [    0.325036] pci 0000:01:05.0: Boot video device
Jul 21 19:13:32 donal-laptop kernel: [    0.325226] cpufreq-nforce2: No nForce2 chipset.
Jul 21 19:13:32 donal-laptop kernel: [    0.325249] Scanning for low memory corruption every 60 seconds
Jul 21 19:13:32 donal-laptop kernel: [    0.325344] audit: initializing netlink socket (disabled)
Jul 21 19:13:32 donal-laptop kernel: [    0.325355] type=2000 audit(1279739600.324:1): initialized
Jul 21 19:13:32 donal-laptop kernel: [    0.334406] highmem bounce pool size: 64 pages
Jul 21 19:13:32 donal-laptop kernel: [    0.334411] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jul 21 19:13:32 donal-laptop kernel: [    0.335764] VFS: Disk quotas dquot_6.5.2
Jul 21 19:13:32 donal-laptop kernel: [    0.335816] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 21 19:13:32 donal-laptop kernel: [    0.336332] fuse init (API version 7.13)
Jul 21 19:13:32 donal-laptop kernel: [    0.336408] msgmni has been set to 1657
Jul 21 19:13:32 donal-laptop kernel: [    0.336589] alg: No test for stdrng (krng)
Jul 21 19:13:32 donal-laptop kernel: [    0.336638] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul 21 19:13:32 donal-laptop kernel: [    0.336641] io scheduler noop registered
Jul 21 19:13:32 donal-laptop kernel: [    0.336643] io scheduler anticipatory registered
Jul 21 19:13:32 donal-laptop kernel: [    0.336645] io scheduler deadline registered
Jul 21 19:13:32 donal-laptop kernel: [    0.336685] io scheduler cfq registered (default)
Jul 21 19:13:32 donal-laptop kernel: [    0.336814]   alloc irq_desc for 25 on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.336817]   alloc kstat_irqs on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.336824] pcieport 0000:00:04.0: irq 25 for MSI/MSI-X
Jul 21 19:13:32 donal-laptop kernel: [    0.336830] pcieport 0000:00:04.0: setting latency timer to 64
Jul 21 19:13:32 donal-laptop kernel: [    0.336903]   alloc irq_desc for 26 on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.336905]   alloc kstat_irqs on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.336910] pcieport 0000:00:06.0: irq 26 for MSI/MSI-X
Jul 21 19:13:32 donal-laptop kernel: [    0.336915] pcieport 0000:00:06.0: setting latency timer to 64
Jul 21 19:13:32 donal-laptop kernel: [    0.337001]   alloc irq_desc for 27 on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.337003]   alloc kstat_irqs on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.337007] pcieport 0000:00:09.0: irq 27 for MSI/MSI-X
Jul 21 19:13:32 donal-laptop kernel: [    0.337012] pcieport 0000:00:09.0: setting latency timer to 64
Jul 21 19:13:32 donal-laptop kernel: [    0.337070] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 21 19:13:32 donal-laptop kernel: [    0.337091] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 21 19:13:32 donal-laptop kernel: [    0.337260] ACPI: AC Adapter [ADP1] (off-line)
Jul 21 19:13:32 donal-laptop kernel: [    0.337328] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:18/PNP0C09:00/PNP0C0D:00/input/input0
Jul 21 19:13:32 donal-laptop kernel: [    0.342083] ACPI: Lid Switch [LID0]
Jul 21 19:13:32 donal-laptop kernel: [    0.342122] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:18/PNP0C09:00/PNP0C0E:00/input/input1
Jul 21 19:13:32 donal-laptop kernel: [    0.342125] ACPI: Sleep Button [SLPB]
Jul 21 19:13:32 donal-laptop kernel: [    0.342167] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
Jul 21 19:13:32 donal-laptop kernel: [    0.342170] ACPI: Power Button [PWRB]
Jul 21 19:13:32 donal-laptop kernel: [    0.342207] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jul 21 19:13:32 donal-laptop kernel: [    0.342209] ACPI: Power Button [PWRF]
Jul 21 19:13:32 donal-laptop kernel: [    0.342584] ACPI: processor limited to max C-state 1
Jul 21 19:13:32 donal-laptop kernel: [    0.342605] processor LNXCPU:00: registered as cooling_device0
Jul 21 19:13:32 donal-laptop kernel: [    0.342633] processor LNXCPU:01: registered as cooling_device1
Jul 21 19:13:32 donal-laptop kernel: [    0.354149] thermal LNXTHERM:01: registered as thermal_zone0
Jul 21 19:13:32 donal-laptop kernel: [    0.354155] ACPI: Thermal Zone [THRM] (51 C)
Jul 21 19:13:32 donal-laptop kernel: [    0.355445] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jul 21 19:13:32 donal-laptop kernel: [    0.356568] brd: module loaded
Jul 21 19:13:32 donal-laptop kernel: [    0.356931] loop: module loaded
Jul 21 19:13:32 donal-laptop kernel: [    0.357052] input: Macintosh mouse button emulation as /devices/virtual/input/input4
Jul 21 19:13:32 donal-laptop kernel: [    0.357211] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 21 19:13:32 donal-laptop kernel: [    0.357240] pata_acpi 0000:00:14.1: setting latency timer to 64
Jul 21 19:13:32 donal-laptop kernel: [    0.357514] Fixed MDIO Bus: probed
Jul 21 19:13:32 donal-laptop kernel: [    0.357543] PPP generic driver version 2.4.2
Jul 21 19:13:32 donal-laptop kernel: [    0.357575] tun: Universal TUN/TAP device driver, 1.6
Jul 21 19:13:32 donal-laptop kernel: [    0.357577] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 21 19:13:32 donal-laptop kernel: [    0.357641] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 21 19:13:32 donal-laptop kernel: [    0.357691] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul 21 19:13:32 donal-laptop kernel: [    0.357706] ehci_hcd 0000:00:12.2: EHCI Host Controller
Jul 21 19:13:32 donal-laptop kernel: [    0.357733] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Jul 21 19:13:32 donal-laptop kernel: [    0.357761] ehci_hcd 0000:00:12.2: debug port 1
Jul 21 19:13:32 donal-laptop kernel: [    0.357784] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfdbff800
Jul 21 19:13:32 donal-laptop kernel: [    0.367473] isapnp: Scanning for PnP cards...
Jul 21 19:13:32 donal-laptop kernel: [    0.369686] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jul 21 19:13:32 donal-laptop kernel: [    0.369758] usb usb1: configuration #1 chosen from 1 choice
Jul 21 19:13:32 donal-laptop kernel: [    0.369786] hub 1-0:1.0: USB hub found
Jul 21 19:13:32 donal-laptop kernel: [    0.369792] hub 1-0:1.0: 6 ports detected
Jul 21 19:13:32 donal-laptop kernel: [    0.369880]   alloc irq_desc for 19 on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.369882]   alloc kstat_irqs on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.369887] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 21 19:13:32 donal-laptop kernel: [    0.369899] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jul 21 19:13:32 donal-laptop kernel: [    0.369924] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Jul 21 19:13:32 donal-laptop kernel: [    0.369950] ehci_hcd 0000:00:13.2: debug port 1
Jul 21 19:13:32 donal-laptop kernel: [    0.369969] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfdbff400
Jul 21 19:13:32 donal-laptop kernel: [    0.381627] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jul 21 19:13:32 donal-laptop kernel: [    0.381687] usb usb2: configuration #1 chosen from 1 choice
Jul 21 19:13:32 donal-laptop kernel: [    0.381708] hub 2-0:1.0: USB hub found
Jul 21 19:13:32 donal-laptop kernel: [    0.381714] hub 2-0:1.0: 6 ports detected
Jul 21 19:13:32 donal-laptop kernel: [    0.381798] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 21 19:13:32 donal-laptop kernel: [    0.381854] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 21 19:13:32 donal-laptop kernel: [    0.381865] ohci_hcd 0000:00:12.0: OHCI Host Controller
Jul 21 19:13:32 donal-laptop kernel: [    0.381891] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Jul 21 19:13:32 donal-laptop kernel: [    0.381912] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfdbfe000
Jul 21 19:13:32 donal-laptop kernel: [    0.442178] usb usb3: configuration #1 chosen from 1 choice
Jul 21 19:13:32 donal-laptop kernel: [    0.442207] hub 3-0:1.0: USB hub found
Jul 21 19:13:32 donal-laptop kernel: [    0.442251] hub 3-0:1.0: 3 ports detected
Jul 21 19:13:32 donal-laptop kernel: [    0.442308] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 21 19:13:32 donal-laptop kernel: [    0.442326] ohci_hcd 0000:00:12.1: OHCI Host Controller
Jul 21 19:13:32 donal-laptop kernel: [    0.442366] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Jul 21 19:13:32 donal-laptop kernel: [    0.442423] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfdbfd000
Jul 21 19:13:32 donal-laptop kernel: [    0.487707] Freeing initrd memory: 7774k freed
Jul 21 19:13:32 donal-laptop kernel: [    0.501095] usb usb4: configuration #1 chosen from 1 choice
Jul 21 19:13:32 donal-laptop kernel: [    0.501122] hub 4-0:1.0: USB hub found
Jul 21 19:13:32 donal-laptop kernel: [    0.501142] hub 4-0:1.0: 3 ports detected
Jul 21 19:13:32 donal-laptop kernel: [    0.501199] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 21 19:13:32 donal-laptop kernel: [    0.501216] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 21 19:13:32 donal-laptop kernel: [    0.501249] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Jul 21 19:13:32 donal-laptop kernel: [    0.501321] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfdbfc000
Jul 21 19:13:32 donal-laptop kernel: [    0.561089] usb usb5: configuration #1 chosen from 1 choice
Jul 21 19:13:32 donal-laptop kernel: [    0.561116] hub 5-0:1.0: USB hub found
Jul 21 19:13:32 donal-laptop kernel: [    0.561127] hub 5-0:1.0: 3 ports detected
Jul 21 19:13:32 donal-laptop kernel: [    0.561182] uhci_hcd: USB Universal Host Controller Interface driver
Jul 21 19:13:32 donal-laptop kernel: [    0.561255] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Jul 21 19:13:32 donal-laptop kernel: [    0.580819] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 21 19:13:32 donal-laptop kernel: [    0.580826] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 21 19:13:32 donal-laptop kernel: [    0.580928] mice: PS/2 mouse device common for all mice
Jul 21 19:13:32 donal-laptop kernel: [    0.581752] rtc_cmos 00:03: RTC can wake from S4
Jul 21 19:13:32 donal-laptop kernel: [    0.581788] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jul 21 19:13:32 donal-laptop kernel: [    0.581813] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jul 21 19:13:32 donal-laptop kernel: [    0.581905] device-mapper: uevent: version 1.0.3
Jul 21 19:13:32 donal-laptop kernel: [    0.582006] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Jul 21 19:13:32 donal-laptop kernel: [    0.582061] device-mapper: multipath: version 1.1.0 loaded
Jul 21 19:13:32 donal-laptop kernel: [    0.582063] device-mapper: multipath round-robin: version 1.0.0 loaded
Jul 21 19:13:32 donal-laptop kernel: [    0.582158] EISA: Probing bus 0 at eisa.0
Jul 21 19:13:32 donal-laptop kernel: [    0.582187] Cannot allocate resource for EISA slot 7
Jul 21 19:13:32 donal-laptop kernel: [    0.582190] Cannot allocate resource for EISA slot 8
Jul 21 19:13:32 donal-laptop kernel: [    0.582192] EISA: Detected 0 cards.
Jul 21 19:13:32 donal-laptop kernel: [    0.582249] cpuidle: using governor ladder
Jul 21 19:13:32 donal-laptop kernel: [    0.582251] cpuidle: using governor menu
Jul 21 19:13:32 donal-laptop kernel: [    0.582655] TCP cubic registered
Jul 21 19:13:32 donal-laptop kernel: [    0.582790] NET: Registered protocol family 10
Jul 21 19:13:32 donal-laptop kernel: [    0.583200] lo: Disabled Privacy Extensions
Jul 21 19:13:32 donal-laptop kernel: [    0.583499] NET: Registered protocol family 17
Jul 21 19:13:32 donal-laptop kernel: [    0.583525] powernow-k8: Found 1 AMD Athlon(tm) II Dual-Core M300 processors (2 cpu cores) (version 2.20.00)
Jul 21 19:13:32 donal-laptop kernel: [    0.583560] powernow-k8:    0 : pstate 0 (2000 MHz)
Jul 21 19:13:32 donal-laptop kernel: [    0.583562] powernow-k8:    1 : pstate 1 (1400 MHz)
Jul 21 19:13:32 donal-laptop kernel: [    0.583564] powernow-k8:    2 : pstate 2 (800 MHz)
Jul 21 19:13:32 donal-laptop kernel: [    0.610426] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
Jul 21 19:13:32 donal-laptop kernel: [    0.620345] Using IPI No-Shortcut mode
Jul 21 19:13:32 donal-laptop kernel: [    0.620442] PM: Resume from disk failed.
Jul 21 19:13:32 donal-laptop kernel: [    0.620453] registered taskstats version 1
Jul 21 19:13:32 donal-laptop kernel: [    0.620845]   Magic number: 2:767:243
Jul 21 19:13:32 donal-laptop kernel: [    0.621208] rtc_cmos 00:03: setting system clock to 2010-07-21 19:13:21 UTC (1279739601)
Jul 21 19:13:32 donal-laptop kernel: [    0.621211] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 21 19:13:32 donal-laptop kernel: [    0.621213] EDD information not available.
Jul 21 19:13:32 donal-laptop kernel: [    0.741075] ACPI: Battery Slot [BAT1] (battery present)
Jul 21 19:13:32 donal-laptop kernel: [    0.756214] isapnp: No Plug & Play device found
Jul 21 19:13:32 donal-laptop kernel: [    0.756249] Freeing unused kernel memory: 660k freed
Jul 21 19:13:32 donal-laptop kernel: [    0.756542] Write protecting the kernel text: 4680k
Jul 21 19:13:32 donal-laptop kernel: [    0.756577] Write protecting the kernel read-only data: 1840k
Jul 21 19:13:32 donal-laptop kernel: [    0.775422] udev: starting version 151
Jul 21 19:13:32 donal-laptop kernel: [    0.883915] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul 21 19:13:32 donal-laptop kernel: [    0.883933] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 21 19:13:32 donal-laptop kernel: [    0.883967] r8169 0000:03:00.0: setting latency timer to 64
Jul 21 19:13:32 donal-laptop kernel: [    0.884002]   alloc irq_desc for 28 on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.884004]   alloc kstat_irqs on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.884016] r8169 0000:03:00.0: irq 28 for MSI/MSI-X
Jul 21 19:13:32 donal-laptop kernel: [    0.884627] eth0: RTL8168d/8111d at 0xf8098000, 40:61:86:ad:e4:30, XID 081000c0 IRQ 28
Jul 21 19:13:32 donal-laptop kernel: [    0.900188] scsi0 : pata_atiixp
Jul 21 19:13:32 donal-laptop kernel: [    0.903580] scsi1 : pata_atiixp
Jul 21 19:13:32 donal-laptop kernel: [    0.904949] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Jul 21 19:13:32 donal-laptop kernel: [    0.904952] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Jul 21 19:13:32 donal-laptop kernel: [    0.905272] ahci 0000:00:11.0: version 3.0
Jul 21 19:13:32 donal-laptop kernel: [    0.905288]   alloc irq_desc for 22 on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.905290]   alloc kstat_irqs on node -1
Jul 21 19:13:32 donal-laptop kernel: [    0.905297] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 21 19:13:32 donal-laptop kernel: [    0.905409] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jul 21 19:13:32 donal-laptop kernel: [    0.905413] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc sxs 
Jul 21 19:13:32 donal-laptop kernel: [    0.905811] scsi2 : ahci
Jul 21 19:13:32 donal-laptop kernel: [    0.905976] scsi3 : ahci
Jul 21 19:13:32 donal-laptop kernel: [    0.906057] scsi4 : ahci
Jul 21 19:13:32 donal-laptop kernel: [    0.906141] scsi5 : ahci
Jul 21 19:13:32 donal-laptop kernel: [    0.906323] ata3: SATA max UDMA/133 abar m1024@0xfdbffc00 port 0xfdbffd00 irq 22
Jul 21 19:13:32 donal-laptop kernel: [    0.906327] ata4: SATA max UDMA/133 abar m1024@0xfdbffc00 port 0xfdbffd80 irq 22
Jul 21 19:13:32 donal-laptop kernel: [    0.906330] ata5: SATA max UDMA/133 abar m1024@0xfdbffc00 port 0xfdbffe00 irq 22
Jul 21 19:13:32 donal-laptop kernel: [    0.906334] ata6: SATA max UDMA/133 abar m1024@0xfdbffc00 port 0xfdbffe80 irq 22
Jul 21 19:13:32 donal-laptop kernel: [    1.044271] usb 3-3: new full speed USB device using ohci_hcd and address 2
Jul 21 19:13:32 donal-laptop kernel: [    1.052403] ata1.00: ATAPI: HL-DT-STDVDRAM GT30N, AS02, max UDMA/100
Jul 21 19:13:32 donal-laptop kernel: [    1.068415] ata1.00: configured for UDMA/100
Jul 21 19:13:32 donal-laptop kernel: [    1.071877] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT30N     AS02 PQ: 0 ANSI: 5
Jul 21 19:13:32 donal-laptop kernel: [    1.081004] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jul 21 19:13:32 donal-laptop kernel: [    1.081009] Uniform CD-ROM driver Revision: 3.20
Jul 21 19:13:32 donal-laptop kernel: [    1.081127] sr 0:0:0:0: Attached scsi CD-ROM sr0
Jul 21 19:13:32 donal-laptop kernel: [    1.081187] sr 0:0:0:0: Attached scsi generic sg0 type 5
Jul 21 19:13:32 donal-laptop kernel: [    1.192129] ata6: SATA link down (SStatus 0 SControl 300)
Jul 21 19:13:32 donal-laptop kernel: [    1.192184] ata4: SATA link down (SStatus 0 SControl 300)
Jul 21 19:13:32 donal-laptop kernel: [    1.192211] ata5: SATA link down (SStatus 0 SControl 300)
Jul 21 19:13:32 donal-laptop kernel: [    1.320321] usb 3-3: configuration #1 chosen from 1 choice
Jul 21 19:13:32 donal-laptop kernel: [    1.356118] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 21 19:13:32 donal-laptop kernel: [    1.357409] ata3.00: ATA-8: WDC WD3200BEVT-22A23T0, 01.01A01, max UDMA/133
Jul 21 19:13:32 donal-laptop kernel: [    1.357413] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jul 21 19:13:32 donal-laptop kernel: [    1.358915] ata3.00: configured for UDMA/133
Jul 21 19:13:32 donal-laptop kernel: [    1.372199] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-2 01.0 PQ: 0 ANSI: 5
Jul 21 19:13:32 donal-laptop kernel: [    1.372356] sd 2:0:0:0: Attached scsi generic sg1 type 0
Jul 21 19:13:32 donal-laptop kernel: [    1.372483] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Jul 21 19:13:32 donal-laptop kernel: [    1.372522] sd 2:0:0:0: [sda] Write Protect is off
Jul 21 19:13:32 donal-laptop kernel: [    1.372525] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 21 19:13:32 donal-laptop kernel: [    1.372543] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 21 19:13:32 donal-laptop kernel: [    1.372676]  sda: sda1 sda2 < sda5 >
Jul 21 19:13:32 donal-laptop kernel: [    1.433497] sd 2:0:0:0: [sda] Attached SCSI disk
Jul 21 19:13:32 donal-laptop kernel: [    1.812399] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jul 21 19:13:32 donal-laptop kernel: [   10.676104] udev: starting version 151
Jul 21 19:13:32 donal-laptop kernel: [   10.705422] Adding 9828344k swap on /dev/sda5.  Priority:-1 extents:1 across:9828344k 
Jul 21 19:13:32 donal-laptop kernel: [   10.764151] lp: driver loaded but no devices found
Jul 21 19:13:32 donal-laptop kernel: [   10.792455] acpi device:04: registered as cooling_device2
Jul 21 19:13:32 donal-laptop kernel: [   10.792617] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input6
Jul 21 19:13:32 donal-laptop kernel: [   10.792894] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
Jul 21 19:13:32 donal-laptop kernel: [   11.042181] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
Jul 21 19:13:32 donal-laptop kernel: [   11.042185] shpchp 0000:00:01.0: Cannot reserve MMIO region
Jul 21 19:13:32 donal-laptop kernel: [   11.042280] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 21 19:13:32 donal-laptop kernel: [   11.043035] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Jul 21 19:13:32 donal-laptop kernel: [   11.092444] rt3090sta: module license 'unspecified' taints kernel.
Jul 21 19:13:32 donal-laptop kernel: [   11.092448] Disabling lock debugging due to kernel taint
Jul 21 19:13:32 donal-laptop kernel: [   11.106880] vga16fb: initializing
Jul 21 19:13:32 donal-laptop kernel: [   11.106884] vga16fb: mapped to 0xc00a0000
Jul 21 19:13:32 donal-laptop kernel: [   11.106947] fb0: VGA16 VGA frame buffer device
Jul 21 19:13:32 donal-laptop kernel: [   11.112851] Linux agpgart interface v0.103
Jul 21 19:13:32 donal-laptop kernel: [   11.113320] rt2860 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 21 19:13:32 donal-laptop kernel: [   11.113352] rt2860 0000:02:00.0: setting latency timer to 64
Jul 21 19:13:32 donal-laptop kernel: [   11.113542] 
Jul 21 19:13:32 donal-laptop kernel: [   11.113543] 
Jul 21 19:13:32 donal-laptop kernel: [   11.113544] === pAd = f8a32000, size = 523136 ===
Jul 21 19:13:32 donal-laptop kernel: [   11.113545] 
Jul 21 19:13:32 donal-laptop kernel: [   11.113628] <-- RTMPAllocAdapterBlock, Status=0
Jul 21 19:13:32 donal-laptop kernel: [   11.113631] pAd->CSRBaseAddress =0xf8a20000, csr_addr=0xf8a20000!
Jul 21 19:13:32 donal-laptop kernel: [   11.175737] type=1505 audit(1279736012.051:2):  operation="profile_load" pid=656 name="/sbin/dhclient3"
Jul 21 19:13:32 donal-laptop kernel: [   11.176032] type=1505 audit(1279736012.055:3):  operation="profile_load" pid=656 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 21 19:13:32 donal-laptop kernel: [   11.176184] type=1505 audit(1279736012.055:4):  operation="profile_load" pid=656 name="/usr/lib/connman/scripts/dhclient-script"
Jul 21 19:13:32 donal-laptop kernel: [   11.263953] [fglrx] Maximum main memory to use for locked dma buffers: 3126 MBytes.
Jul 21 19:13:32 donal-laptop kernel: [   11.263988] [fglrx]   vendor: 1002 device: 9712 count: 1
Jul 21 19:13:32 donal-laptop kernel: [   11.264327] [fglrx] ioport: bar 1, base 0xc000, size: 0x100
Jul 21 19:13:32 donal-laptop kernel: [   11.264343] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 21 19:13:32 donal-laptop kernel: [   11.264348] pci 0000:01:05.0: setting latency timer to 64
Jul 21 19:13:32 donal-laptop kernel: [   11.264700] [fglrx] Kernel PAT support is enabled
Jul 21 19:13:32 donal-laptop kernel: [   11.264723] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors
Jul 21 19:13:32 donal-laptop kernel: [   11.269847] Bluetooth: Core ver 2.15
Jul 21 19:13:32 donal-laptop kernel: [   11.269906] NET: Registered protocol family 31
Jul 21 19:13:32 donal-laptop kernel: [   11.269909] Bluetooth: HCI device and connection manager initialized
Jul 21 19:13:32 donal-laptop kernel: [   11.269912] Bluetooth: HCI socket layer initialized
Jul 21 19:13:32 donal-laptop kernel: [   11.311735] Bluetooth: Generic Bluetooth USB driver ver 0.6
Jul 21 19:13:32 donal-laptop kernel: [   11.312241] usbcore: registered new interface driver btusb
Jul 21 19:13:32 donal-laptop kernel: [   11.367928] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 21 19:13:32 donal-laptop kernel: [   11.375336] Console: switching to colour frame buffer device 80x30
Jul 21 19:13:32 donal-laptop kernel: [   11.430387] hda_codec: ALC662 rev1: BIOS auto-probing.
Jul 21 19:13:32 donal-laptop kernel: [   11.431643] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input7
Jul 21 19:13:32 donal-laptop kernel: [   11.437922] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 21 19:13:32 donal-laptop kernel: [   11.437950] HDA Intel 0000:01:05.1: setting latency timer to 64
Jul 21 19:13:32 donal-laptop kernel: [   11.685894] type=1505 audit(1279736012.563:5):  operation="profile_load" pid=801 name="/usr/share/gdm/guest-session/Xsession"
Jul 21 19:13:32 donal-laptop kernel: [   11.687305] type=1505 audit(1279736012.563:6):  operation="profile_replace" pid=802 name="/sbin/dhclient3"
Jul 21 19:13:32 donal-laptop kernel: [   11.687587] type=1505 audit(1279736012.563:7):  operation="profile_replace" pid=802 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 21 19:13:32 donal-laptop kernel: [   11.687743] type=1505 audit(1279736012.563:8):  operation="profile_replace" pid=802 name="/usr/lib/connman/scripts/dhclient-script"
Jul 21 19:13:32 donal-laptop kernel: [   11.690976] type=1505 audit(1279736012.567:9):  operation="profile_load" pid=803 name="/usr/bin/evince"
Jul 21 19:13:32 donal-laptop kernel: [   11.694544] type=1505 audit(1279736012.571:10):  operation="profile_load" pid=803 name="/usr/bin/evince-previewer"
Jul 21 19:13:32 donal-laptop kernel: [   11.698473] type=1505 audit(1279736012.575:11):  operation="profile_load" pid=803 name="/usr/bin/evince-thumbnailer"
Jul 21 19:13:32 donal-laptop kernel: [   11.899669] RX DESC f392b000  size = 2048
Jul 21 19:13:32 donal-laptop kernel: [   11.899862] <-- RTMPAllocTxRxRingMemory, Status=0
Jul 21 19:13:32 donal-laptop kernel: [   12.014458] Key1Str is Invalid key length(0) or Type(0)
Jul 21 19:13:32 donal-laptop kernel: [   12.014481] Key2Str is Invalid key length(0) or Type(0)
Jul 21 19:13:32 donal-laptop kernel: [   12.014503] Key3Str is Invalid key length(0) or Type(0)
Jul 21 19:13:32 donal-laptop kernel: [   12.014525] Key4Str is Invalid key length(0) or Type(0)
Jul 21 19:13:32 donal-laptop kernel: [   12.014888] 1. Phy Mode = 9
Jul 21 19:13:32 donal-laptop kernel: [   12.014890] 2. Phy Mode = 9
Jul 21 19:13:32 donal-laptop kernel: [   12.014892] NVM is Efuse and its size =2d[2d0-2fc] 
Jul 21 19:13:32 donal-laptop kernel: [   12.015712] RTMPSetPhyMode: channel is out of range, use first channel=1 
Jul 21 19:13:32 donal-laptop kernel: [   12.016979] 3. Phy Mode = 9
Jul 21 19:13:32 donal-laptop kernel: [   12.038021] MCS Set = ff 00 00 00 01
Jul 21 19:13:32 donal-laptop kernel: [   12.039270] <==== rt28xx_init, Status=0
Jul 21 19:13:32 donal-laptop kernel: [   12.039331] 0x1300 = 00064300
Jul 21 19:13:32 donal-laptop kernel: [   12.039347]  AUX_CTRL = 0x                             c02
Jul 21 19:13:32 donal-laptop kernel: [   12.039351]  Read AUX_CTRL = 0xc02
Jul 21 19:13:32 donal-laptop kernel: [   12.039353]  Write AUX_CTRL = 0x1c02
Jul 21 19:13:32 donal-laptop kernel: [   12.039356]  OSC_CTRL = 0x3ff11
Jul 21 19:13:32 donal-laptop kernel: [   12.039752] ====> rt30xx Read PowerLevelMode =  0x3.
Jul 21 19:13:32 donal-laptop kernel: [   12.039754] ====> rt30xx F Write 0x83 Command = 0x3.
Jul 21 19:13:32 donal-laptop kernel: [   12.041302] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04711/0x200000
Jul 21 19:13:32 donal-laptop kernel: [   12.043035] r8169: eth0: link down
Jul 21 19:13:32 donal-laptop kernel: [   12.043255] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 21 19:13:32 donal-laptop kernel: [   12.099733] ppdev: user-space parallel port driver
Jul 21 19:13:32 donal-laptop kernel: [   12.114122] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
Jul 21 19:13:33 donal-laptop kernel: [   12.488728] Bluetooth: L2CAP ver 2.14
Jul 21 19:13:33 donal-laptop kernel: [   12.488731] Bluetooth: L2CAP socket layer initialized
Jul 21 19:13:33 donal-laptop kernel: [   12.608808] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul 21 19:13:33 donal-laptop kernel: [   12.608811] Bluetooth: BNEP filters: protocol multicast
Jul 21 19:13:33 donal-laptop kernel: [   12.670590] Bridge firewalling registered
Jul 21 19:13:33 donal-laptop kernel: [   12.706471] Bluetooth: SCO (Voice Link) ver 0.6
Jul 21 19:13:33 donal-laptop kernel: [   12.706474] Bluetooth: SCO socket layer initialized
Jul 21 19:13:33 donal-laptop kernel: [   13.101457] Bluetooth: RFCOMM TTY layer initialized
Jul 21 19:13:33 donal-laptop kernel: [   13.101461] Bluetooth: RFCOMM socket layer initialized
Jul 21 19:13:33 donal-laptop kernel: [   13.101463] Bluetooth: RFCOMM ver 1.11
Jul 21 19:13:34 donal-laptop kernel: [   13.954767] [fglrx] GART Table is not in FRAME_BUFFER range 
Jul 21 19:13:34 donal-laptop kernel: [   13.955103]   alloc irq_desc for 29 on node -1
Jul 21 19:13:34 donal-laptop kernel: [   13.955106]   alloc kstat_irqs on node -1
Jul 21 19:13:34 donal-laptop kernel: [   13.955115] fglrx_pci 0000:01:05.0: irq 29 for MSI/MSI-X
Jul 21 19:13:34 donal-laptop kernel: [   13.955739] [fglrx] Firegl kernel thread PID: 1157
Jul 21 19:13:34 donal-laptop kernel: [   13.956044] [fglrx] IRQ 29 Enabled
Jul 21 19:13:35 donal-laptop kernel: [   14.144445] [fglrx] Gart USWC size:1022 M.
Jul 21 19:13:35 donal-laptop kernel: [   14.144449] [fglrx] Gart cacheable size:405 M.
Jul 21 19:13:35 donal-laptop kernel: [   14.144454] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Jul 21 19:13:35 donal-laptop kernel: [   14.144457] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
Jul 21 19:13:38 donal-laptop kernel: [   17.999826] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Jul 21 19:13:43 donal-laptop kernel: [   22.196052] ra0: no IPv6 routers present
Jul 21 19:13:51 donal-laptop kernel: [   30.473731] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
Jul 21 19:18:18 donal-laptop kernel: [  297.938056] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
Jul 21 19:44:00 donal-laptop kernel: [ 1839.772947] atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
Jul 21 19:44:00 donal-laptop kernel: [ 1839.772958] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
Jul 21 19:44:00 donal-laptop kernel: [ 1839.782835] atkbd.c: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0).
Jul 21 19:44:00 donal-laptop kernel: [ 1839.782843] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.

---

### Post by davidmohammed on 2010-07-21
hmmm...

your usb and pci lists do not show any obvious webcam device that has been connected.

Your kernel log also doesn't show any obvious webcam device recognised by the kernel....

Either your webcam isn't physically connected - or you need to "turn it on" - is there a switch or something on your laptop to switch it on?

I'm curious - you mentioned that your webcam was seen via cheese.  Then you rebooted (?) and then cheese no longer saw the webcam.

When cheese doesn't see the webcam, is there a webcam device mapped? type

ls /dev/video*

in a terminal.

Possibly (or probably), the current lucid kernel doesnt play ball with your webcam.  You could try one of the newest maverick kernels to see if your webcam is recognised better.

---

### Post by Donalt2010 on 2010-07-21
sorry for wasting your time, after reading your last post it was just simply a matter of turning the webcam on by the button, i actually forgot there was a button... I feel like a muppet now. But thanks very much for taking your time to help me. Ill know in future. D'oh!!!!!!!!!!!!!!!!!!!!!

Thanks

Regards
DonalT

---

