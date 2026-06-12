---
title: "&quot;Serious errors were found in ...&quot;"
date: 2010-06-09
forum: General Help
---

### Post by spmurphy on 2010-06-09
Clean install of 64 bit 10.04 onto (previously) working hardware.

On boot, sometimes the boot process stops and under the 5 little dots displays a message saying "Serious errors were found in " and then either /var or /home. This screen gives me the option to "I" ignore it, "M" manually fix it or a third option beginning with "S" that I can't remember. I'll update this post next time I reboot. If I select "M" to manually fix it followed by Ctrl-D to end the shell i.e. I didn't attempt to fix whatever is wrong, it boots as if nothing were wrong. Machine works perfectly.

I've rebooted with my live cd and checked the /var and /home with the disk utility and it reports they're both fine, no errors. My root is on an 80 gig intel ssd and /var and /home are both on a 500 gig magnetic. All file systems are ext4 and check out ok from the live cd.

If I had to guess, I'd guess some kind of timing issue due to the intermittent nature. It happens roughly 1 in 3 boots. Boot, stop, "M", Ctrl-D, boots and works perfectly.

Can anyone point me at a log that might have more information as to what it's moaning about i.e. what the "serious errors" are?

I also get a single text line that pops up and disappears before the 5 dot graphic screen about "ureadahead" terminated with 4 (I think, it's awfully quick).

Is there a way to turn off the low-res 5 dot ubuntu screen and get back the old scrolly terminal that told me what it was actually doing when it booted?

Does anyone have any fault finding suggestions?

---

### Post by Peter09 on 2010-06-09
Look in the log files (System->Admin->Logs) and see if there are any messages in Syslog.

---

### Post by spmurphy on 2010-06-09
I'd seen those but there are about 30 and I've no idea what they all represent.

Can you suggest which one(s) I should be looking at?

---

### Post by Peter09 on 2010-06-09
Cut and paste them in here.
 
EDIT: Not sure if you mean 30errors or 30 Logs, look in Syslog first.

---

### Post by spmurphy on 2010-06-09
Ok, I'll start with syslog, thank you. It was 30 log files.

I've just rebooted 3 times and got 2 "Serious error" complaints. The options given are I to ignore, S to skip mounting or M for manual recovery. The third boot it checked the file systems for error - that's the first time it's done that on boot with this version. I remember the routine file system checks after so many reboots with 9.10 but this version has never checked, not once.

I'll have a look at syslog now.

---

### Post by spmurphy on 2010-06-09
the ureadhead error is because ureadahead assumes /var is on root, not it's own partition. i've disabled ureadahead.

syslog from the last "Serious errors" boot:

```
Jun  9 11:14:18 simon-watery kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jun  9 11:14:18 simon-watery rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1081" x-info="http://www.rsyslog.com"] (re)start
Jun  9 11:14:18 simon-watery rsyslogd: rsyslogd's groupid changed to 103
Jun  9 11:14:18 simon-watery rsyslogd: rsyslogd's userid changed to 101
Jun  9 11:14:18 simon-watery rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun  9 11:14:18 simon-watery avahi-daemon[1130]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Jun  9 11:14:18 simon-watery avahi-daemon[1130]: Successfully dropped root privileges.
Jun  9 11:14:18 simon-watery avahi-daemon[1130]: avahi-daemon 0.6.25 starting up.
Jun  9 11:14:18 simon-watery avahi-daemon[1130]: Successfully called chroot().
Jun  9 11:14:18 simon-watery avahi-daemon[1130]: Successfully dropped remaining capabilities.
Jun  9 11:14:18 simon-watery avahi-daemon[1130]: No service file found in /etc/avahi/services.
Jun  9 11:14:18 simon-watery avahi-daemon[1130]: Network interface enumeration completed.
Jun  9 11:14:18 simon-watery avahi-daemon[1130]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun  9 11:14:18 simon-watery avahi-daemon[1130]: Server startup complete. Host name is simon-watery.local. Local service cookie is 3062193817.
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Initializing cgroup subsys cpu
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Linux version 2.6.32-22-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 (Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=f7185e7c-bb4e-414b-b15c-62e18742ea57 ro quiet splash
Jun  9 11:14:18 simon-watery kernel: [    0.000000] KERNEL supported cpus:
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   Intel GenuineIntel
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   AMD AuthenticAMD
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   Centaur CentaurHauls
Jun  9 11:14:18 simon-watery kernel: [    0.000000] BIOS-provided physical RAM map:
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf670000 (usable)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  BIOS-e820: 00000000bf670000 - 00000000bf688000 (ACPI data)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  BIOS-e820: 00000000bf688000 - 00000000bf6dc000 (ACPI NVS)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  BIOS-e820: 00000000bf6dc000 - 00000000bf700000 (reserved)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  BIOS-e820: 00000000bf800000 - 00000000c0000000 (reserved)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000240000000 (usable)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] DMI 2.6 present.
Jun  9 11:14:18 simon-watery kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Jun  9 11:14:18 simon-watery kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] last_pfn = 0x240000 max_arch_pfn = 0x400000000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] MTRR default type: uncachable
Jun  9 11:14:18 simon-watery kernel: [    0.000000] MTRR fixed ranges enabled:
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   00000-9FFFF write-back
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   A0000-BFFFF uncachable
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   C0000-CFFFF write-protect
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   D0000-DFFFF uncachable
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   E0000-E7FFF write-through
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   E8000-FFFFF write-protect
Jun  9 11:14:18 simon-watery kernel: [    0.000000] MTRR variable ranges enabled:
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   0 base 000000000 mask E00000000 write-back
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   1 base 200000000 mask FC0000000 write-back
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   4 disabled
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   5 disabled
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   6 disabled
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   7 disabled
Jun  9 11:14:18 simon-watery kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun  9 11:14:18 simon-watery kernel: [    0.000000] e820 update range: 00000000bff00000 - 0000000100000000 (usable) ==> (reserved)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] last_pfn = 0xbf670 max_arch_pfn = 0x400000000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jun  9 11:14:18 simon-watery kernel: [    0.000000] modified physical RAM map:
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  modified: 0000000000010000 - 000000000009e800 (usable)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  modified: 000000000009e800 - 00000000000a0000 (reserved)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  modified: 0000000000100000 - 00000000bf670000 (usable)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  modified: 00000000bf670000 - 00000000bf688000 (ACPI data)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  modified: 00000000bf688000 - 00000000bf6dc000 (ACPI NVS)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  modified: 00000000bf6dc000 - 00000000bf700000 (reserved)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  modified: 00000000bf800000 - 00000000c0000000 (reserved)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  modified: 0000000100000000 - 0000000240000000 (usable)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bf670000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] NX (Execute Disable) protection: active
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  0000000000 - 00bf600000 page 2M
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  00bf600000 - 00bf670000 page 4k
Jun  9 11:14:18 simon-watery kernel: [    0.000000] kernel direct mapping tables up to bf670000 @ 10000-15000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000240000000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] NX (Execute Disable) protection: active
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  0100000000 - 0240000000 page 2M
Jun  9 11:14:18 simon-watery kernel: [    0.000000] kernel direct mapping tables up to 240000000 @ 13000-1d000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] RAMDISK: 377fe000 - 37fef810
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: RSDP 00000000000fad50 00024 (v02 ACPIAM)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: XSDT 00000000bf670100 0005C (v01 122109 XSDT1805 20091221 MSFT 00000097)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: FACP 00000000bf670290 000F4 (v03 122109 FACP1805 20091221 MSFT 00000097)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: DSDT 00000000bf6704a0 0F151 (v01  A1320 A1320001 00000001 INTL 20060113)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: FACS 00000000bf688000 00040
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: APIC 00000000bf670390 000CC (v01 122109 APIC1805 20091221 MSFT 00000097)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: MCFG 00000000bf670460 0003C (v01 122109 OEMMCFG  20091221 MSFT 00000097)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: OEMB 00000000bf688040 00072 (v01 122109 OEMB1805 20091221 MSFT 00000097)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: HPET 00000000bf67f6a0 00038 (v01 122109 OEMHPET  20091221 MSFT 00000097)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: OSFR 00000000bf67f6e0 000B0 (v01 122109 OEMOSFR  20091221 MSFT 00000097)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: SSDT 00000000bf68ad80 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] No NUMA configuration found
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Faking a node at 0000000000000000-0000000240000000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000240000000
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   NODE_DATA [0000000000018000 - 000000000001cfff]
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   bootmap [000000000001d000 -  0000000000064fff] pages 48
Jun  9 11:14:18 simon-watery kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0240000000]
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   #3 [00377fe000 - 0037fef810]          RAMDISK ==> [00377fe000 - 0037fef810]
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   #4 [000009e800 - 0000100000]    BIOS reserved ==> [000009e800 - 0000100000]
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   #5 [0001a2a000 - 0001a2a2d0]              BRK ==> [0001a2a000 - 0001a2a2d0]
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   #7 [0000013000 - 0000018000]          PGTABLE ==> [0000013000 - 0000018000]
Jun  9 11:14:18 simon-watery kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Jun  9 11:14:18 simon-watery kernel: [    0.000000]  [ffffea0000000000-ffffea0007dfffff] PMD -> [ffff880028600000-ffff88002f5fffff] on node 0
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Zone PFN ranges:
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   Normal   0x00100000 -> 0x00240000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Movable zone start PFN for each node
Jun  9 11:14:18 simon-watery kernel: [    0.000000] early_node_map[3] active PFN ranges
Jun  9 11:14:18 simon-watery kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Jun  9 11:14:18 simon-watery kernel: [    0.000000]     0: 0x00000100 -> 0x000bf670
Jun  9 11:14:18 simon-watery kernel: [    0.000000]     0: 0x00100000 -> 0x00240000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] On node 0 totalpages: 2094590
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   DMA zone: 108 pages reserved
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   DMA zone: 3818 pages, LIFO batch:0
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   DMA32 zone: 765608 pages, LIFO batch:31
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   Normal zone: 17920 pages used for memmap
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   Normal zone: 1292800 pages, LIFO batch:31
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
Jun  9 11:14:18 simon-watery kernel: [    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun  9 11:14:18 simon-watery kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] SMP: Allowing 16 CPUs, 8 hotplug CPUs
Jun  9 11:14:18 simon-watery kernel: [    0.000000] nr_irqs_gsi: 24
Jun  9 11:14:18 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000bf670000 - 00000000bf688000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000bf688000 - 00000000bf6dc000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000bf6dc000 - 00000000bf700000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000bf700000 - 00000000bf800000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000bf800000 - 00000000c0000000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun  9 11:14:18 simon-watery kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:16 nr_node_ids:1
Jun  9 11:14:18 simon-watery kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u131072
Jun  9 11:14:18 simon-watery kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u131072 alloc=1*2097152
Jun  9 11:14:18 simon-watery kernel: [    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2062226
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Policy zone: Normal
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=f7185e7c-bb4e-414b-b15c-62e18742ea57 ro quiet splash
Jun  9 11:14:18 simon-watery kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Initializing CPU#0
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Checking aperture...
Jun  9 11:14:18 simon-watery kernel: [    0.000000] No AGP bridge found
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jun  9 11:14:18 simon-watery kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Memory: 8176920k/9437184k available (5409k kernel code, 1058824k absent, 201440k reserved, 2976k data, 876k init)
Jun  9 11:14:18 simon-watery kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Hierarchical RCU implementation.
Jun  9 11:14:18 simon-watery kernel: [    0.000000] NR_IRQS:4352 nr_irqs:536
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Extended CMOS year: 2000
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Console: colour VGA+ 80x25
Jun  9 11:14:18 simon-watery kernel: [    0.000000] console [tty0] enabled
Jun  9 11:14:18 simon-watery kernel: [    0.000000] allocated 83886080 bytes of page_cgroup
Jun  9 11:14:18 simon-watery kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun  9 11:14:18 simon-watery kernel: [    0.000000] hpet clockevent registered
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   alloc irq_desc for 24 on node 0
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   alloc kstat_irqs on node 0
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   alloc irq_desc for 25 on node 0
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   alloc kstat_irqs on node 0
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   alloc irq_desc for 26 on node 0
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   alloc kstat_irqs on node 0
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   alloc irq_desc for 27 on node 0
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   alloc kstat_irqs on node 0
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   alloc irq_desc for 28 on node 0
Jun  9 11:14:18 simon-watery kernel: [    0.000000]   alloc kstat_irqs on node 0
Jun  9 11:14:18 simon-watery kernel: [    0.000000] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
Jun  9 11:14:18 simon-watery kernel: [    0.000000] Fast TSC calibration using PIT
Jun  9 11:14:18 simon-watery kernel: [    0.010000] Detected 2942.598 MHz processor.
Jun  9 11:14:18 simon-watery kernel: [    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5885.19 BogoMIPS (lpj=29425980)
Jun  9 11:14:18 simon-watery kernel: [    0.000016] Security Framework initialized
Jun  9 11:14:18 simon-watery kernel: [    0.000026] AppArmor: AppArmor initialized
Jun  9 11:14:18 simon-watery kernel: [    0.000473] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Jun  9 11:14:18 simon-watery kernel: [    0.001855] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun  9 11:14:18 simon-watery kernel: [    0.002468] Mount-cache hash table entries: 256
Jun  9 11:14:18 simon-watery kernel: [    0.002628] Initializing cgroup subsys ns
Jun  9 11:14:18 simon-watery kernel: [    0.002630] Initializing cgroup subsys cpuacct
Jun  9 11:14:18 simon-watery kernel: [    0.002633] Initializing cgroup subsys memory
Jun  9 11:14:18 simon-watery kernel: [    0.002637] Initializing cgroup subsys devices
Jun  9 11:14:18 simon-watery kernel: [    0.002639] Initializing cgroup subsys freezer
Jun  9 11:14:18 simon-watery kernel: [    0.002640] Initializing cgroup subsys net_cls
Jun  9 11:14:18 simon-watery kernel: [    0.002652] CPU: Physical Processor ID: 0
Jun  9 11:14:18 simon-watery kernel: [    0.002653] CPU: Processor Core ID: 0
Jun  9 11:14:18 simon-watery kernel: [    0.002655] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun  9 11:14:18 simon-watery kernel: [    0.002657] CPU: L2 cache: 256K
Jun  9 11:14:18 simon-watery kernel: [    0.002658] CPU: L3 cache: 8192K
Jun  9 11:14:18 simon-watery kernel: [    0.002659] CPU 0/0x0 -> Node 0
Jun  9 11:14:18 simon-watery kernel: [    0.002661] mce: CPU supports 9 MCE banks
Jun  9 11:14:18 simon-watery kernel: [    0.002669] CPU0: Thermal monitoring enabled (TM1)
Jun  9 11:14:18 simon-watery kernel: [    0.002672] CPU 0 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6 SHD:8
Jun  9 11:14:18 simon-watery kernel: [    0.002678] using mwait in idle threads.
Jun  9 11:14:18 simon-watery kernel: [    0.002679] Performance Events: Nehalem/Corei7 events, Intel PMU driver.
Jun  9 11:14:18 simon-watery kernel: [    0.002683] ... version:                3
Jun  9 11:14:18 simon-watery kernel: [    0.002684] ... bit width:              48
Jun  9 11:14:18 simon-watery kernel: [    0.002685] ... generic registers:      4
Jun  9 11:14:18 simon-watery kernel: [    0.002686] ... value mask:             0000ffffffffffff
Jun  9 11:14:18 simon-watery kernel: [    0.002687] ... max period:             000000007fffffff
Jun  9 11:14:18 simon-watery kernel: [    0.002688] ... fixed-purpose events:   3
Jun  9 11:14:18 simon-watery kernel: [    0.002689] ... event mask:             000000070000000f
Jun  9 11:14:18 simon-watery kernel: [    0.004239] ACPI: Core revision 20090903
Jun  9 11:14:18 simon-watery kernel: [    0.038086] ftrace: converting mcount calls to 0f 1f 44 00 00
Jun  9 11:14:18 simon-watery kernel: [    0.038090] ftrace: allocating 22518 entries in 89 pages
Jun  9 11:14:18 simon-watery kernel: [    0.043470] Setting APIC routing to physical flat
Jun  9 11:14:18 simon-watery kernel: [    0.043795] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun  9 11:14:18 simon-watery kernel: [    0.143517] CPU0: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
Jun  9 11:14:18 simon-watery kernel: [    0.257902] Booting processor 1 APIC 0x2 ip 0x6000
Jun  9 11:14:18 simon-watery kernel: [    0.268316] Initializing CPU#1
Jun  9 11:14:18 simon-watery kernel: [    0.417360] CPU: Physical Processor ID: 0
Jun  9 11:14:18 simon-watery kernel: [    0.417361] CPU: Processor Core ID: 1
Jun  9 11:14:18 simon-watery kernel: [    0.417362] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun  9 11:14:18 simon-watery kernel: [    0.417363] CPU: L2 cache: 256K
Jun  9 11:14:18 simon-watery kernel: [    0.417364] CPU: L3 cache: 8192K
Jun  9 11:14:18 simon-watery kernel: [    0.417366] CPU 1/0x2 -> Node 0
Jun  9 11:14:18 simon-watery kernel: [    0.417374] CPU1: Thermal monitoring enabled (TM1)
Jun  9 11:14:18 simon-watery kernel: [    0.417376] CPU 1 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Jun  9 11:14:18 simon-watery kernel: [    0.417427] CPU1: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
Jun  9 11:14:18 simon-watery kernel: [    0.417433] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jun  9 11:14:18 simon-watery kernel: [    0.437437] Booting processor 2 APIC 0x4 ip 0x6000
Jun  9 11:14:18 simon-watery kernel: [    0.447740] Initializing CPU#2
Jun  9 11:14:18 simon-watery kernel: [    0.596835] CPU: Physical Processor ID: 0
Jun  9 11:14:18 simon-watery kernel: [    0.596836] CPU: Processor Core ID: 2
Jun  9 11:14:18 simon-watery kernel: [    0.596837] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun  9 11:14:18 simon-watery kernel: [    0.596839] CPU: L2 cache: 256K
Jun  9 11:14:18 simon-watery kernel: [    0.596839] CPU: L3 cache: 8192K
Jun  9 11:14:18 simon-watery kernel: [    0.596841] CPU 2/0x4 -> Node 0
Jun  9 11:14:18 simon-watery kernel: [    0.596849] CPU2: Thermal monitoring enabled (TM1)
Jun  9 11:14:18 simon-watery kernel: [    0.596852] CPU 2 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Jun  9 11:14:18 simon-watery kernel: [    0.596887] CPU2: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
Jun  9 11:14:18 simon-watery kernel: [    0.596893] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Jun  9 11:14:18 simon-watery kernel: [    0.616897] Booting processor 3 APIC 0x6 ip 0x6000
Jun  9 11:14:18 simon-watery kernel: [    0.627199] Initializing CPU#3
Jun  9 11:14:18 simon-watery kernel: [    0.776310] CPU: Physical Processor ID: 0
Jun  9 11:14:18 simon-watery kernel: [    0.776311] CPU: Processor Core ID: 3
Jun  9 11:14:18 simon-watery kernel: [    0.776312] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun  9 11:14:18 simon-watery kernel: [    0.776314] CPU: L2 cache: 256K
Jun  9 11:14:18 simon-watery kernel: [    0.776314] CPU: L3 cache: 8192K
Jun  9 11:14:18 simon-watery kernel: [    0.776316] CPU 3/0x6 -> Node 0
Jun  9 11:14:18 simon-watery kernel: [    0.776324] CPU3: Thermal monitoring enabled (TM1)
Jun  9 11:14:18 simon-watery kernel: [    0.776326] CPU 3 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Jun  9 11:14:18 simon-watery kernel: [    0.776421] CPU3: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
Jun  9 11:14:18 simon-watery kernel: [    0.776427] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Jun  9 11:14:18 simon-watery kernel: [    0.796432] Booting processor 4 APIC 0x1 ip 0x6000
Jun  9 11:14:18 simon-watery kernel: [    0.806735] Initializing CPU#4
Jun  9 11:14:18 simon-watery kernel: [    0.955785] CPU: Physical Processor ID: 0
Jun  9 11:14:18 simon-watery kernel: [    0.955786] CPU: Processor Core ID: 0
Jun  9 11:14:18 simon-watery kernel: [    0.955789] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun  9 11:14:18 simon-watery kernel: [    0.955790] CPU: L2 cache: 256K
Jun  9 11:14:18 simon-watery kernel: [    0.955791] CPU: L3 cache: 8192K
Jun  9 11:14:18 simon-watery kernel: [    0.955793] CPU 4/0x1 -> Node 0
Jun  9 11:14:18 simon-watery kernel: [    0.955802] CPU4: Thermal monitoring enabled (TM1)
Jun  9 11:14:18 simon-watery kernel: [    0.955805] CPU 4 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
Jun  9 11:14:18 simon-watery kernel: [    0.955861] CPU4: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
Jun  9 11:14:18 simon-watery kernel: [    0.955868] checking TSC synchronization [CPU#0 -> CPU#4]: passed.
Jun  9 11:14:18 simon-watery kernel: [    0.975875] Booting processor 5 APIC 0x3 ip 0x6000
Jun  9 11:14:18 simon-watery kernel: [    0.986177] Initializing CPU#5
Jun  9 11:14:18 simon-watery kernel: [    1.135260] CPU: Physical Processor ID: 0
Jun  9 11:14:18 simon-watery kernel: [    1.135261] CPU: Processor Core ID: 1
Jun  9 11:14:18 simon-watery kernel: [    1.135263] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun  9 11:14:18 simon-watery kernel: [    1.135264] CPU: L2 cache: 256K
Jun  9 11:14:18 simon-watery kernel: [    1.135264] CPU: L3 cache: 8192K
Jun  9 11:14:18 simon-watery kernel: [    1.135266] CPU 5/0x3 -> Node 0
Jun  9 11:14:18 simon-watery kernel: [    1.135274] CPU5: Thermal monitoring enabled (TM1)
Jun  9 11:14:18 simon-watery kernel: [    1.135276] CPU 5 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
Jun  9 11:14:18 simon-watery kernel: [    1.135300] CPU5: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
Jun  9 11:14:18 simon-watery kernel: [    1.135306] checking TSC synchronization [CPU#0 -> CPU#5]: passed.
Jun  9 11:14:18 simon-watery kernel: [    1.155313] Booting processor 6 APIC 0x5 ip 0x6000
Jun  9 11:14:18 simon-watery kernel: [    1.165615] Initializing CPU#6
Jun  9 11:14:18 simon-watery kernel: [    1.314735] CPU: Physical Processor ID: 0
Jun  9 11:14:18 simon-watery kernel: [    1.314736] CPU: Processor Core ID: 2
Jun  9 11:14:18 simon-watery kernel: [    1.314738] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun  9 11:14:18 simon-watery kernel: [    1.314739] CPU: L2 cache: 256K
Jun  9 11:14:18 simon-watery kernel: [    1.314739] CPU: L3 cache: 8192K
Jun  9 11:14:18 simon-watery kernel: [    1.314741] CPU 6/0x5 -> Node 0
Jun  9 11:14:18 simon-watery kernel: [    1.314749] CPU6: Thermal monitoring enabled (TM1)
Jun  9 11:14:18 simon-watery kernel: [    1.314751] CPU 6 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
Jun  9 11:14:18 simon-watery kernel: [    1.314838] CPU6: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
Jun  9 11:14:18 simon-watery kernel: [    1.314844] checking TSC synchronization [CPU#0 -> CPU#6]: passed.
Jun  9 11:14:18 simon-watery kernel: [    1.334849] Booting processor 7 APIC 0x7 ip 0x6000
Jun  9 11:14:18 simon-watery kernel: [    1.345152] Initializing CPU#7
Jun  9 11:14:18 simon-watery kernel: [    1.494210] CPU: Physical Processor ID: 0
Jun  9 11:14:18 simon-watery kernel: [    1.494211] CPU: Processor Core ID: 3
Jun  9 11:14:18 simon-watery kernel: [    1.494213] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun  9 11:14:18 simon-watery kernel: [    1.494214] CPU: L2 cache: 256K
Jun  9 11:14:18 simon-watery kernel: [    1.494215] CPU: L3 cache: 8192K
Jun  9 11:14:18 simon-watery kernel: [    1.494216] CPU 7/0x7 -> Node 0
Jun  9 11:14:18 simon-watery kernel: [    1.494224] CPU7: Thermal monitoring enabled (TM1)
Jun  9 11:14:18 simon-watery kernel: [    1.494227] CPU 7 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
Jun  9 11:14:18 simon-watery kernel: [    1.494274] CPU7: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
Jun  9 11:14:18 simon-watery kernel: [    1.494280] checking TSC synchronization [CPU#0 -> CPU#7]: passed.
Jun  9 11:14:18 simon-watery kernel: [    1.514237] Brought up 8 CPUs
Jun  9 11:14:18 simon-watery kernel: [    1.514239] Total of 8 processors activated (47079.10 BogoMIPS).
Jun  9 11:14:18 simon-watery kernel: [    1.517291] CPU0 attaching sched-domain:
Jun  9 11:14:18 simon-watery kernel: [    1.517293]  domain 0: span 0,4 level SIBLING
Jun  9 11:14:18 simon-watery kernel: [    1.517295]   groups: 0 (cpu_power = 589) 4 (cpu_power = 589)
Jun  9 11:14:18 simon-watery kernel: [    1.517298]   domain 1: span 0-7 level MC
Jun  9 11:14:18 simon-watery kernel: [    1.517300]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun  9 11:14:18 simon-watery kernel: [    1.517306] CPU1 attaching sched-domain:
Jun  9 11:14:18 simon-watery kernel: [    1.517308]  domain 0: span 1,5 level SIBLING
Jun  9 11:14:18 simon-watery kernel: [    1.517309]   groups: 1 (cpu_power = 589) 5 (cpu_power = 589)
Jun  9 11:14:18 simon-watery kernel: [    1.517312]   domain 1: span 0-7 level MC
Jun  9 11:14:18 simon-watery kernel: [    1.517313]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun  9 11:14:18 simon-watery kernel: [    1.517319] CPU2 attaching sched-domain:
Jun  9 11:14:18 simon-watery kernel: [    1.517320]  domain 0: span 2,6 level SIBLING
Jun  9 11:14:18 simon-watery kernel: [    1.517321]   groups: 2 (cpu_power = 589) 6 (cpu_power = 589)
Jun  9 11:14:18 simon-watery kernel: [    1.517324]   domain 1: span 0-7 level MC
Jun  9 11:14:18 simon-watery kernel: [    1.517325]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun  9 11:14:18 simon-watery kernel: [    1.517331] CPU3 attaching sched-domain:
Jun  9 11:14:18 simon-watery kernel: [    1.517332]  domain 0: span 3,7 level SIBLING
Jun  9 11:14:18 simon-watery kernel: [    1.517333]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
Jun  9 11:14:18 simon-watery kernel: [    1.517336]   domain 1: span 0-7 level MC
Jun  9 11:14:18 simon-watery kernel: [    1.517337]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun  9 11:14:18 simon-watery kernel: [    1.517343] CPU4 attaching sched-domain:
Jun  9 11:14:18 simon-watery kernel: [    1.517344]  domain 0: span 0,4 level SIBLING
Jun  9 11:14:18 simon-watery kernel: [    1.517345]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
Jun  9 11:14:18 simon-watery kernel: [    1.517348]   domain 1: span 0-7 level MC
Jun  9 11:14:18 simon-watery kernel: [    1.517349]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun  9 11:14:18 simon-watery kernel: [    1.517354] CPU5 attaching sched-domain:
Jun  9 11:14:18 simon-watery kernel: [    1.517356]  domain 0: span 1,5 level SIBLING
Jun  9 11:14:18 simon-watery kernel: [    1.517357]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
Jun  9 11:14:18 simon-watery kernel: [    1.517360]   domain 1: span 0-7 level MC
Jun  9 11:14:18 simon-watery kernel: [    1.517361]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun  9 11:14:18 simon-watery kernel: [    1.517366] CPU6 attaching sched-domain:
Jun  9 11:14:18 simon-watery kernel: [    1.517368]  domain 0: span 2,6 level SIBLING
Jun  9 11:14:18 simon-watery kernel: [    1.517369]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
Jun  9 11:14:18 simon-watery kernel: [    1.517372]   domain 1: span 0-7 level MC
Jun  9 11:14:18 simon-watery kernel: [    1.517373]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun  9 11:14:18 simon-watery kernel: [    1.517378] CPU7 attaching sched-domain:
Jun  9 11:14:18 simon-watery kernel: [    1.517379]  domain 0: span 3,7 level SIBLING
Jun  9 11:14:18 simon-watery kernel: [    1.517381]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
Jun  9 11:14:18 simon-watery kernel: [    1.517384]   domain 1: span 0-7 level MC
Jun  9 11:14:18 simon-watery kernel: [    1.517385]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun  9 11:14:18 simon-watery kernel: [    1.517639] devtmpfs: initialized
Jun  9 11:14:18 simon-watery kernel: [    1.517863] regulator: core version 0.5
Jun  9 11:14:18 simon-watery kernel: [    1.517885] Time: 10:14:08  Date: 06/09/10
Jun  9 11:14:18 simon-watery kernel: [    1.517917] NET: Registered protocol family 16
Jun  9 11:14:18 simon-watery kernel: [    1.517974] Trying to unpack rootfs image as initramfs...
Jun  9 11:14:18 simon-watery kernel: [    1.517993] ACPI: bus type pci registered
Jun  9 11:14:18 simon-watery kernel: [    1.518039] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jun  9 11:14:18 simon-watery kernel: [    1.518040] PCI: Not using MMCONFIG.
Jun  9 11:14:18 simon-watery kernel: [    1.518041] PCI: Using configuration type 1 for base access
Jun  9 11:14:18 simon-watery kernel: [    1.518573] bio: create slab <bio-0> at 0
Jun  9 11:14:18 simon-watery kernel: [    1.519308] ACPI: EC: Look up EC in DSDT
Jun  9 11:14:18 simon-watery kernel: [    1.521340] ACPI: Executed 1 blocks of module-level executable AML code
Jun  9 11:14:18 simon-watery kernel: [    1.531907] ACPI: Interpreter enabled
Jun  9 11:14:18 simon-watery kernel: [    1.531910] ACPI: (supports S0 S1 S3 S4 S5)
Jun  9 11:14:18 simon-watery kernel: [    1.531926] ACPI: Using IOAPIC for interrupt routing
Jun  9 11:14:18 simon-watery kernel: [    1.531968] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jun  9 11:14:18 simon-watery kernel: [    1.533744] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Jun  9 11:14:18 simon-watery kernel: [    1.538362] PCI: Using MMCONFIG at e0000000 - efffffff
Jun  9 11:14:18 simon-watery kernel: [    1.545466] ACPI: No dock devices found.
Jun  9 11:14:18 simon-watery kernel: [    1.545706] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun  9 11:14:18 simon-watery kernel: [    1.545802] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
Jun  9 11:14:18 simon-watery kernel: [    1.545805] pci 0000:00:05.0: PME# disabled
Jun  9 11:14:18 simon-watery kernel: [    1.546040] pci 0000:00:1a.0: reg 10 32bit mmio: [0xf7ffe000-0xf7ffe3ff]
Jun  9 11:14:18 simon-watery kernel: [    1.546088] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Jun  9 11:14:18 simon-watery kernel: [    1.546091] pci 0000:00:1a.0: PME# disabled
Jun  9 11:14:18 simon-watery kernel: [    1.546125] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf7ff8000-0xf7ffbfff]
Jun  9 11:14:18 simon-watery kernel: [    1.546161] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jun  9 11:14:18 simon-watery kernel: [    1.546163] pci 0000:00:1b.0: PME# disabled
Jun  9 11:14:18 simon-watery kernel: [    1.546217] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jun  9 11:14:18 simon-watery kernel: [    1.546220] pci 0000:00:1c.0: PME# disabled
Jun  9 11:14:18 simon-watery kernel: [    1.546276] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Jun  9 11:14:18 simon-watery kernel: [    1.546278] pci 0000:00:1c.4: PME# disabled
Jun  9 11:14:18 simon-watery kernel: [    1.546332] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Jun  9 11:14:18 simon-watery kernel: [    1.546334] pci 0000:00:1c.5: PME# disabled
Jun  9 11:14:18 simon-watery kernel: [    1.546387] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
Jun  9 11:14:18 simon-watery kernel: [    1.546389] pci 0000:00:1c.6: PME# disabled
Jun  9 11:14:18 simon-watery kernel: [    1.546442] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
Jun  9 11:14:18 simon-watery kernel: [    1.546445] pci 0000:00:1c.7: PME# disabled
Jun  9 11:14:18 simon-watery kernel: [    1.546488] pci 0000:00:1d.0: reg 10 32bit mmio: [0xf7ffd000-0xf7ffd3ff]
Jun  9 11:14:18 simon-watery kernel: [    1.546536] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Jun  9 11:14:18 simon-watery kernel: [    1.546539] pci 0000:00:1d.0: PME# disabled
Jun  9 11:14:18 simon-watery kernel: [    1.546699] pci 0000:00:1f.2: reg 10 io port: [0xc880-0xc887]
Jun  9 11:14:18 simon-watery kernel: [    1.546704] pci 0000:00:1f.2: reg 14 io port: [0xc800-0xc803]
Jun  9 11:14:18 simon-watery kernel: [    1.546708] pci 0000:00:1f.2: reg 18 io port: [0xc480-0xc487]
Jun  9 11:14:18 simon-watery kernel: [    1.546712] pci 0000:00:1f.2: reg 1c io port: [0xc400-0xc403]
Jun  9 11:14:18 simon-watery kernel: [    1.546717] pci 0000:00:1f.2: reg 20 io port: [0xc080-0xc09f]
Jun  9 11:14:18 simon-watery kernel: [    1.546721] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf7ff7000-0xf7ff77ff]
Jun  9 11:14:18 simon-watery kernel: [    1.546748] pci 0000:00:1f.2: PME# supported from D3hot
Jun  9 11:14:18 simon-watery kernel: [    1.546750] pci 0000:00:1f.2: PME# disabled
Jun  9 11:14:18 simon-watery kernel: [    1.546774] pci 0000:00:1f.3: reg 10 64bit mmio: [0xf7ffc000-0xf7ffc0ff]
Jun  9 11:14:18 simon-watery kernel: [    1.546785] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
Jun  9 11:14:18 simon-watery kernel: [    1.546824] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
Jun  9 11:14:18 simon-watery kernel: [    1.546831] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
Jun  9 11:14:18 simon-watery kernel: [    1.546838] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
Jun  9 11:14:18 simon-watery kernel: [    1.546843] pci 0000:01:00.0: reg 24 io port: [0xdc00-0xdc7f]
Jun  9 11:14:18 simon-watery kernel: [    1.546847] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfbd80000-0xfbdfffff]
Jun  9 11:14:18 simon-watery kernel: [    1.546888] pci 0000:00:05.0: bridge io port: [0xd000-0xdfff]
Jun  9 11:14:18 simon-watery kernel: [    1.546890] pci 0000:00:05.0: bridge 32bit mmio: [0xf8000000-0xfbdfffff]
Jun  9 11:14:18 simon-watery kernel: [    1.546894] pci 0000:00:05.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
Jun  9 11:14:18 simon-watery kernel: [    1.547109] pci 0000:07:03.0: reg 10 32bit mmio: [0xfbeff800-0xfbefffff]
Jun  9 11:14:18 simon-watery kernel: [    1.547115] pci 0000:07:03.0: reg 14 io port: [0xec00-0xec7f]
Jun  9 11:14:18 simon-watery kernel: [    1.547153] pci 0000:07:03.0: supports D2
Jun  9 11:14:18 simon-watery kernel: [    1.547155] pci 0000:07:03.0: PME# supported from D2 D3hot D3cold
Jun  9 11:14:18 simon-watery kernel: [    1.547158] pci 0000:07:03.0: PME# disabled
Jun  9 11:14:18 simon-watery kernel: [    1.547192] pci 0000:07:04.0: reg 10 io port: [0xe800-0xe8ff]
Jun  9 11:14:18 simon-watery kernel: [    1.547198] pci 0000:07:04.0: reg 14 32bit mmio: [0xfbeff400-0xfbeff4ff]
Jun  9 11:14:18 simon-watery kernel: [    1.547220] pci 0000:07:04.0: reg 30 32bit mmio pref: [0xfbec0000-0xfbedffff]
Jun  9 11:14:18 simon-watery kernel: [    1.547240] pci 0000:07:04.0: supports D1 D2
Jun  9 11:14:18 simon-watery kernel: [    1.547241] pci 0000:07:04.0: PME# supported from D1 D2 D3hot D3cold
Jun  9 11:14:18 simon-watery kernel: [    1.547244] pci 0000:07:04.0: PME# disabled
Jun  9 11:14:18 simon-watery kernel: [    1.547282] pci 0000:00:1e.0: transparent bridge
Jun  9 11:14:18 simon-watery kernel: [    1.547284] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
Jun  9 11:14:18 simon-watery kernel: [    1.547287] pci 0000:00:1e.0: bridge 32bit mmio: [0xfbe00000-0xfbefffff]
Jun  9 11:14:18 simon-watery kernel: [    1.547316] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun  9 11:14:18 simon-watery kernel: [    1.547451] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR1E._PRT]
Jun  9 11:14:18 simon-watery kernel: [    1.547548] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
Jun  9 11:14:18 simon-watery kernel: [    1.547596] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
Jun  9 11:14:18 simon-watery kernel: [    1.547640] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR24._PRT]
Jun  9 11:14:18 simon-watery kernel: [    1.547683] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR25._PRT]
Jun  9 11:14:18 simon-watery kernel: [    1.547726] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR26._PRT]
Jun  9 11:14:18 simon-watery kernel: [    1.547778] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR27._PRT]
Jun  9 11:14:18 simon-watery kernel: [    1.565267] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
Jun  9 11:14:18 simon-watery kernel: [    1.565364] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
Jun  9 11:14:18 simon-watery kernel: [    1.565456] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 *12 14 15)
Jun  9 11:14:18 simon-watery kernel: [    1.565550] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
Jun  9 11:14:18 simon-watery kernel: [    1.565644] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
Jun  9 11:14:18 simon-watery kernel: [    1.565741] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 *15)
Jun  9 11:14:18 simon-watery kernel: [    1.565836] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 7 10 11 12 *14 15)
Jun  9 11:14:18 simon-watery kernel: [    1.565930] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 6 7 10 11 12 14 15)
Jun  9 11:14:18 simon-watery kernel: [    1.566008] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun  9 11:14:18 simon-watery kernel: [    1.566011] vgaarb: loaded
Jun  9 11:14:18 simon-watery kernel: [    1.566074] SCSI subsystem initialized
Jun  9 11:14:18 simon-watery kernel: [    1.566173] libata version 3.00 loaded.
Jun  9 11:14:18 simon-watery kernel: [    1.566218] usbcore: registered new interface driver usbfs
Jun  9 11:14:18 simon-watery kernel: [    1.566225] usbcore: registered new interface driver hub
Jun  9 11:14:18 simon-watery kernel: [    1.566239] usbcore: registered new device driver usb
Jun  9 11:14:18 simon-watery kernel: [    1.566326] ACPI: WMI: Mapper loaded
Jun  9 11:14:18 simon-watery kernel: [    1.566327] PCI: Using ACPI for IRQ routing
Jun  9 11:14:18 simon-watery kernel: [    1.566432] NetLabel: Initializing
Jun  9 11:14:18 simon-watery kernel: [    1.566433] NetLabel:  domain hash size = 128
Jun  9 11:14:18 simon-watery kernel: [    1.566434] NetLabel:  protocols = UNLABELED CIPSOv4
Jun  9 11:14:18 simon-watery kernel: [    1.566444] NetLabel:  unlabeled traffic allowed by default
Jun  9 11:14:18 simon-watery kernel: [    1.566472] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 25, 26, 27, 28, 0
Jun  9 11:14:18 simon-watery kernel: [    1.566477] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Jun  9 11:14:18 simon-watery kernel: [    1.573988] hpet: hpet2 irq 24 for MSI
Jun  9 11:14:18 simon-watery kernel: [    1.574081] hpet: hpet3 irq 25 for MSI
Jun  9 11:14:18 simon-watery kernel: [    1.584036] hpet: hpet4 irq 26 for MSI
Jun  9 11:14:18 simon-watery kernel: [    1.584095] hpet: hpet5 irq 27 for MSI
Jun  9 11:14:18 simon-watery kernel: [    1.594033] hpet: hpet6 irq 28 for MSI
Jun  9 11:14:18 simon-watery kernel: [    1.613949] Switching to clocksource tsc
Jun  9 11:14:18 simon-watery kernel: [    1.615130] AppArmor: AppArmor Filesystem Enabled
Jun  9 11:14:18 simon-watery kernel: [    1.615139] pnp: PnP ACPI init
Jun  9 11:14:18 simon-watery kernel: [    1.615151] ACPI: bus type pnp registered
Jun  9 11:14:18 simon-watery kernel: [    1.617026] pnp: PnP ACPI: found 14 devices
Jun  9 11:14:18 simon-watery kernel: [    1.617028] ACPI: ACPI bus type pnp unregistered
Jun  9 11:14:18 simon-watery kernel: [    1.617035] system 00:01: iomem range 0xfc000000-0xfcffffff has been reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617037] system 00:01: iomem range 0xfd000000-0xfdffffff has been reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617039] system 00:01: iomem range 0xfe000000-0xfebfffff has been reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617041] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617045] system 00:06: ioport range 0x290-0x29f has been reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617049] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617050] system 00:07: ioport range 0x800-0x87f has been reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617052] system 00:07: ioport range 0x500-0x57f has been reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617054] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617056] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617058] system 00:07: iomem range 0xfed40000-0xfed8ffff has been reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617061] system 00:0a: iomem range 0xffc00000-0xffdfffff has been reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617065] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617066] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617069] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617073] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617074] system 00:0d: iomem range 0xc0000-0xcffff has been reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617076] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617078] system 00:0d: iomem range 0x100000-0xbfefffff could not be reserved
Jun  9 11:14:18 simon-watery kernel: [    1.617080] system 00:0d: iomem range 0xfed90000-0xffffffff could not be reserved
Jun  9 11:14:18 simon-watery kernel: [    1.621686] pci 0000:07:04.0: BAR 6: address space collision on of device [0xfbec0000-0xfbedffff]
Jun  9 11:14:18 simon-watery kernel: [    1.621729] pci 0000:00:05.0: PCI bridge, secondary bus 0000:01
Jun  9 11:14:18 simon-watery kernel: [    1.621731] pci 0000:00:05.0:   IO window: 0xd000-0xdfff
Jun  9 11:14:18 simon-watery kernel: [    1.621734] pci 0000:00:05.0:   MEM window: 0xf8000000-0xfbdfffff
Jun  9 11:14:18 simon-watery kernel: [    1.621736] pci 0000:00:05.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Jun  9 11:14:18 simon-watery kernel: [    1.621740] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:06
Jun  9 11:14:18 simon-watery kernel: [    1.621742] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
Jun  9 11:14:18 simon-watery kernel: [    1.621746] pci 0000:00:1c.0:   MEM window: 0xc0000000-0xc01fffff
Jun  9 11:14:18 simon-watery kernel: [    1.621749] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0200000-0x000000c03fffff
Jun  9 11:14:18 simon-watery kernel: [    1.621753] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:05
Jun  9 11:14:18 simon-watery kernel: [    1.621755] pci 0000:00:1c.4:   IO window: 0x2000-0x2fff
Jun  9 11:14:18 simon-watery kernel: [    1.621759] pci 0000:00:1c.4:   MEM window: 0xc0400000-0xc05fffff
Jun  9 11:14:18 simon-watery kernel: [    1.621762] pci 0000:00:1c.4:   PREFETCH window: 0x000000c0600000-0x000000c07fffff
Jun  9 11:14:18 simon-watery kernel: [    1.621767] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:04
Jun  9 11:14:18 simon-watery kernel: [    1.621769] pci 0000:00:1c.5:   IO window: 0x3000-0x3fff
Jun  9 11:14:18 simon-watery kernel: [    1.621772] pci 0000:00:1c.5:   MEM window: 0xc0800000-0xc09fffff
Jun  9 11:14:18 simon-watery kernel: [    1.621775] pci 0000:00:1c.5:   PREFETCH window: 0x000000c0a00000-0x000000c0bfffff
Jun  9 11:14:18 simon-watery kernel: [    1.621780] pci 0000:00:1c.6: PCI bridge, secondary bus 0000:03
Jun  9 11:14:18 simon-watery kernel: [    1.621781] pci 0000:00:1c.6:   IO window: disabled
Jun  9 11:14:18 simon-watery kernel: [    1.621784] pci 0000:00:1c.6:   MEM window: disabled
Jun  9 11:14:18 simon-watery kernel: [    1.621787] pci 0000:00:1c.6:   PREFETCH window: disabled
Jun  9 11:14:18 simon-watery kernel: [    1.621791] pci 0000:00:1c.7: PCI bridge, secondary bus 0000:02
Jun  9 11:14:18 simon-watery kernel: [    1.621792] pci 0000:00:1c.7:   IO window: disabled
Jun  9 11:14:18 simon-watery kernel: [    1.621796] pci 0000:00:1c.7:   MEM window: disabled
Jun  9 11:14:18 simon-watery kernel: [    1.621798] pci 0000:00:1c.7:   PREFETCH window: disabled
Jun  9 11:14:18 simon-watery kernel: [    1.621804] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
Jun  9 11:14:18 simon-watery kernel: [    1.621806] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
Jun  9 11:14:18 simon-watery kernel: [    1.621809] pci 0000:00:1e.0:   MEM window: 0xfbe00000-0xfbefffff
Jun  9 11:14:18 simon-watery kernel: [    1.621812] pci 0000:00:1e.0:   PREFETCH window: 0xc0c00000-0xc0cfffff
Jun  9 11:14:18 simon-watery kernel: [    1.621822]   alloc irq_desc for 16 on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.621824]   alloc kstat_irqs on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.621827] pci 0000:00:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  9 11:14:18 simon-watery kernel: [    1.621830] pci 0000:00:05.0: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    1.621836] pci 0000:00:1c.0: enabling device (0104 -> 0107)
Jun  9 11:14:18 simon-watery kernel: [    1.621838]   alloc irq_desc for 17 on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.621839]   alloc kstat_irqs on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.621842] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun  9 11:14:18 simon-watery kernel: [    1.621845] pci 0000:00:1c.0: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    1.621850] pci 0000:00:1c.4: enabling device (0104 -> 0107)
Jun  9 11:14:18 simon-watery kernel: [    1.621853] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun  9 11:14:18 simon-watery kernel: [    1.621856] pci 0000:00:1c.4: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    1.621861] pci 0000:00:1c.5: enabling device (0104 -> 0107)
Jun  9 11:14:18 simon-watery kernel: [    1.621864] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Jun  9 11:14:18 simon-watery kernel: [    1.621866] pci 0000:00:1c.5: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    1.621872]   alloc irq_desc for 18 on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.621873]   alloc kstat_irqs on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.621875] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun  9 11:14:18 simon-watery kernel: [    1.621878] pci 0000:00:1c.6: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    1.621884]   alloc irq_desc for 19 on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.621885]   alloc kstat_irqs on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.621887] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jun  9 11:14:18 simon-watery kernel: [    1.621890] pci 0000:00:1c.7: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    1.621895] pci 0000:00:1e.0: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    1.621898] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Jun  9 11:14:18 simon-watery kernel: [    1.621899] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Jun  9 11:14:18 simon-watery kernel: [    1.621901] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
Jun  9 11:14:18 simon-watery kernel: [    1.621902] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xfbdfffff]
Jun  9 11:14:18 simon-watery kernel: [    1.621904] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
Jun  9 11:14:18 simon-watery kernel: [    1.621906] pci_bus 0000:06: resource 0 io:  [0x1000-0x1fff]
Jun  9 11:14:18 simon-watery kernel: [    1.621907] pci_bus 0000:06: resource 1 mem: [0xc0000000-0xc01fffff]
Jun  9 11:14:18 simon-watery kernel: [    1.621909] pci_bus 0000:06: resource 2 pref mem [0xc0200000-0xc03fffff]
Jun  9 11:14:18 simon-watery kernel: [    1.621910] pci_bus 0000:05: resource 0 io:  [0x2000-0x2fff]
Jun  9 11:14:18 simon-watery kernel: [    1.621912] pci_bus 0000:05: resource 1 mem: [0xc0400000-0xc05fffff]
Jun  9 11:14:18 simon-watery kernel: [    1.621913] pci_bus 0000:05: resource 2 pref mem [0xc0600000-0xc07fffff]
Jun  9 11:14:18 simon-watery kernel: [    1.621915] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
Jun  9 11:14:18 simon-watery kernel: [    1.621916] pci_bus 0000:04: resource 1 mem: [0xc0800000-0xc09fffff]
Jun  9 11:14:18 simon-watery kernel: [    1.621918] pci_bus 0000:04: resource 2 pref mem [0xc0a00000-0xc0bfffff]
Jun  9 11:14:18 simon-watery kernel: [    1.621919] pci_bus 0000:07: resource 0 io:  [0xe000-0xefff]
Jun  9 11:14:18 simon-watery kernel: [    1.621921] pci_bus 0000:07: resource 1 mem: [0xfbe00000-0xfbefffff]
Jun  9 11:14:18 simon-watery kernel: [    1.621922] pci_bus 0000:07: resource 2 pref mem [0xc0c00000-0xc0cfffff]
Jun  9 11:14:18 simon-watery kernel: [    1.621924] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
Jun  9 11:14:18 simon-watery kernel: [    1.621925] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffffffffffff]
Jun  9 11:14:18 simon-watery kernel: [    1.621947] NET: Registered protocol family 2
Jun  9 11:14:18 simon-watery kernel: [    1.622115] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun  9 11:14:18 simon-watery kernel: [    1.622872] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jun  9 11:14:18 simon-watery kernel: [    1.624960] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun  9 11:14:18 simon-watery kernel: [    1.625213] TCP: Hash tables configured (established 524288 bind 65536)
Jun  9 11:14:18 simon-watery kernel: [    1.625215] TCP reno registered
Jun  9 11:14:18 simon-watery kernel: [    1.625305] NET: Registered protocol family 1
Jun  9 11:14:18 simon-watery kernel: [    1.625369] pci 0000:01:00.0: Boot video device
Jun  9 11:14:18 simon-watery kernel: [    1.625730] Scanning for low memory corruption every 60 seconds
Jun  9 11:14:18 simon-watery kernel: [    1.625803] audit: initializing netlink socket (disabled)
Jun  9 11:14:18 simon-watery kernel: [    1.625811] type=2000 audit(1276078447.439:1): initialized
Jun  9 11:14:18 simon-watery kernel: [    1.632739] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun  9 11:14:18 simon-watery kernel: [    1.633689] VFS: Disk quotas dquot_6.5.2
Jun  9 11:14:18 simon-watery kernel: [    1.633723] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun  9 11:14:18 simon-watery kernel: [    1.634126] fuse init (API version 7.13)
Jun  9 11:14:18 simon-watery kernel: [    1.634178] msgmni has been set to 15970
Jun  9 11:14:18 simon-watery kernel: [    1.634364] alg: No test for stdrng (krng)
Jun  9 11:14:18 simon-watery kernel: [    1.634399] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun  9 11:14:18 simon-watery kernel: [    1.634401] io scheduler noop registered
Jun  9 11:14:18 simon-watery kernel: [    1.634402] io scheduler anticipatory registered
Jun  9 11:14:18 simon-watery kernel: [    1.634403] io scheduler deadline registered
Jun  9 11:14:18 simon-watery kernel: [    1.634426] io scheduler cfq registered (default)
Jun  9 11:14:18 simon-watery kernel: [    1.634511]   alloc irq_desc for 29 on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.634512]   alloc kstat_irqs on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.634518] pcieport 0000:00:05.0: irq 29 for MSI/MSI-X
Jun  9 11:14:18 simon-watery kernel: [    1.634523] pcieport 0000:00:05.0: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    1.634601]   alloc irq_desc for 30 on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.634602]   alloc kstat_irqs on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.634607] pcieport 0000:00:1c.0: irq 30 for MSI/MSI-X
Jun  9 11:14:18 simon-watery kernel: [    1.634613] pcieport 0000:00:1c.0: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    1.634693]   alloc irq_desc for 31 on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.634694]   alloc kstat_irqs on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.634699] pcieport 0000:00:1c.4: irq 31 for MSI/MSI-X
Jun  9 11:14:18 simon-watery kernel: [    1.634705] pcieport 0000:00:1c.4: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    1.634785]   alloc irq_desc for 32 on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.634786]   alloc kstat_irqs on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.634791] pcieport 0000:00:1c.5: irq 32 for MSI/MSI-X
Jun  9 11:14:18 simon-watery kernel: [    1.634797] pcieport 0000:00:1c.5: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    1.634878]   alloc irq_desc for 33 on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.634879]   alloc kstat_irqs on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.634884] pcieport 0000:00:1c.6: irq 33 for MSI/MSI-X
Jun  9 11:14:18 simon-watery kernel: [    1.634890] pcieport 0000:00:1c.6: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    1.634963]   alloc irq_desc for 34 on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.634964]   alloc kstat_irqs on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.634969] pcieport 0000:00:1c.7: irq 34 for MSI/MSI-X
Jun  9 11:14:18 simon-watery kernel: [    1.634975] pcieport 0000:00:1c.7: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    1.635023] Firmware did not grant requested _OSC control
Jun  9 11:14:18 simon-watery kernel: [    1.635025] aer 0000:00:05.0:pcie02: AER service couldn't init device: no _OSC support
Jun  9 11:14:18 simon-watery kernel: [    1.635031] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun  9 11:14:18 simon-watery kernel: [    1.635039] Firmware did not grant requested _OSC control
Jun  9 11:14:18 simon-watery kernel: [    1.635050] Firmware did not grant requested _OSC control
Jun  9 11:14:18 simon-watery kernel: [    1.635059] Firmware did not grant requested _OSC control
Jun  9 11:14:18 simon-watery kernel: [    1.635076] Firmware did not grant requested _OSC control
Jun  9 11:14:18 simon-watery kernel: [    1.635085] Firmware did not grant requested _OSC control
Jun  9 11:14:18 simon-watery kernel: [    1.635094] Firmware did not grant requested _OSC control
Jun  9 11:14:18 simon-watery kernel: [    1.635103] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun  9 11:14:18 simon-watery kernel: [    1.635164] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jun  9 11:14:18 simon-watery kernel: [    1.635166] ACPI: Power Button [PWRB]
Jun  9 11:14:18 simon-watery kernel: [    1.635190] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun  9 11:14:18 simon-watery kernel: [    1.635192] ACPI: Power Button [PWRF]
Jun  9 11:14:18 simon-watery kernel: [    1.636335] ACPI: SSDT 00000000bf6880c0 0265C (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
Jun  9 11:14:18 simon-watery kernel: [    1.636739] ACPI: SSDT 00000000bf68a720 00659 (v01  PmRef  P001Cst 00003001 INTL 20060113)
Jun  9 11:14:18 simon-watery kernel: [    1.637128] Monitor-Mwait will be used to enter C-1 state
Jun  9 11:14:18 simon-watery kernel: [    1.637146] Monitor-Mwait will be used to enter C-2 state
Jun  9 11:14:18 simon-watery kernel: [    1.637162] Monitor-Mwait will be used to enter C-3 state
Jun  9 11:14:18 simon-watery kernel: [    1.637189] processor LNXCPU:00: registered as cooling_device0
Jun  9 11:14:18 simon-watery kernel: [    1.637447] processor LNXCPU:01: registered as cooling_device1
Jun  9 11:14:18 simon-watery kernel: [    1.637695] processor LNXCPU:02: registered as cooling_device2
Jun  9 11:14:18 simon-watery kernel: [    1.637941] processor LNXCPU:03: registered as cooling_device3
Jun  9 11:14:18 simon-watery kernel: [    1.638194] processor LNXCPU:04: registered as cooling_device4
Jun  9 11:14:18 simon-watery kernel: [    1.646783] Freeing initrd memory: 8134k freed
Jun  9 11:14:18 simon-watery kernel: [    1.647814] processor LNXCPU:05: registered as cooling_device5
Jun  9 11:14:18 simon-watery kernel: [    1.648095] processor LNXCPU:06: registered as cooling_device6
Jun  9 11:14:18 simon-watery kernel: [    1.648342] processor LNXCPU:07: registered as cooling_device7
Jun  9 11:14:18 simon-watery kernel: [    1.651204] Linux agpgart interface v0.103
Jun  9 11:14:18 simon-watery kernel: [    1.651223] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jun  9 11:14:18 simon-watery kernel: [    1.652001] brd: module loaded
Jun  9 11:14:18 simon-watery kernel: [    1.652283] loop: module loaded
Jun  9 11:14:18 simon-watery kernel: [    1.652329] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jun  9 11:14:18 simon-watery kernel: [    1.652555] Fixed MDIO Bus: probed
Jun  9 11:14:18 simon-watery kernel: [    1.652574] PPP generic driver version 2.4.2
Jun  9 11:14:18 simon-watery kernel: [    1.652592] tun: Universal TUN/TAP device driver, 1.6
Jun  9 11:14:18 simon-watery kernel: [    1.652593] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun  9 11:14:18 simon-watery kernel: [    1.652634] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun  9 11:14:18 simon-watery kernel: [    1.652648] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  9 11:14:18 simon-watery kernel: [    1.652661] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    1.652664] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Jun  9 11:14:18 simon-watery kernel: [    1.652682] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jun  9 11:14:18 simon-watery kernel: [    1.652704] ehci_hcd 0000:00:1a.0: debug port 2
Jun  9 11:14:18 simon-watery kernel: [    1.656598] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
Jun  9 11:14:18 simon-watery kernel: [    1.656609] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7ffe000
Jun  9 11:14:18 simon-watery kernel: [    1.675146] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Jun  9 11:14:18 simon-watery kernel: [    1.675235] usb usb1: configuration #1 chosen from 1 choice
Jun  9 11:14:18 simon-watery kernel: [    1.675252] hub 1-0:1.0: USB hub found
Jun  9 11:14:18 simon-watery kernel: [    1.675257] hub 1-0:1.0: 2 ports detected
Jun  9 11:14:18 simon-watery kernel: [    1.675287]   alloc irq_desc for 23 on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.675288]   alloc kstat_irqs on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.675292] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun  9 11:14:18 simon-watery kernel: [    1.675300] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    1.675302] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Jun  9 11:14:18 simon-watery kernel: [    1.675323] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jun  9 11:14:18 simon-watery kernel: [    1.675341] ehci_hcd 0000:00:1d.0: debug port 2
Jun  9 11:14:18 simon-watery kernel: [    1.679228] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
Jun  9 11:14:18 simon-watery kernel: [    1.679237] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7ffd000
Jun  9 11:14:18 simon-watery kernel: [    1.695088] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Jun  9 11:14:18 simon-watery kernel: [    1.695170] usb usb2: configuration #1 chosen from 1 choice
Jun  9 11:14:18 simon-watery kernel: [    1.695184] hub 2-0:1.0: USB hub found
Jun  9 11:14:18 simon-watery kernel: [    1.695188] hub 2-0:1.0: 2 ports detected
Jun  9 11:14:18 simon-watery kernel: [    1.695215] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun  9 11:14:18 simon-watery kernel: [    1.695223] uhci_hcd: USB Universal Host Controller Interface driver
Jun  9 11:14:18 simon-watery kernel: [    1.695262] PNP: No PS/2 controller found. Probing ports directly.
Jun  9 11:14:18 simon-watery kernel: [    1.696872] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun  9 11:14:18 simon-watery kernel: [    1.696877] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun  9 11:14:18 simon-watery kernel: [    1.696924] mice: PS/2 mouse device common for all mice
Jun  9 11:14:18 simon-watery kernel: [    1.696980] rtc_cmos 00:03: RTC can wake from S4
Jun  9 11:14:18 simon-watery kernel: [    1.696999] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jun  9 11:14:18 simon-watery kernel: [    1.697022] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jun  9 11:14:18 simon-watery kernel: [    1.697099] device-mapper: uevent: version 1.0.3
Jun  9 11:14:18 simon-watery kernel: [    1.697156] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jun  9 11:14:18 simon-watery kernel: [    1.697244] device-mapper: multipath: version 1.1.0 loaded
Jun  9 11:14:18 simon-watery kernel: [    1.697246] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun  9 11:14:18 simon-watery kernel: [    1.697560] cpuidle: using governor ladder
Jun  9 11:14:18 simon-watery kernel: [    1.697786] cpuidle: using governor menu
Jun  9 11:14:18 simon-watery kernel: [    1.698022] TCP cubic registered
Jun  9 11:14:18 simon-watery kernel: [    1.698099] NET: Registered protocol family 10
Jun  9 11:14:18 simon-watery kernel: [    1.698422] lo: Disabled Privacy Extensions
Jun  9 11:14:18 simon-watery kernel: [    1.698605] NET: Registered protocol family 17
Jun  9 11:14:18 simon-watery kernel: [    1.698626] ------------[ cut here ]------------
Jun  9 11:14:18 simon-watery kernel: [    1.698631] WARNING: at /build/buildd/linux-2.6.32/arch/x86/kernel/hpet.c:392 hpet_next_event+0x7a/0x90()
Jun  9 11:14:18 simon-watery kernel: [    1.698633] Hardware name: System Product Name
Jun  9 11:14:18 simon-watery kernel: [    1.698634] Modules linked in:
Jun  9 11:14:18 simon-watery kernel: [    1.698636] Pid: 0, comm: swapper Not tainted 2.6.32-22-generic #36-Ubuntu
Jun  9 11:14:18 simon-watery kernel: [    1.698638] Call Trace:
Jun  9 11:14:18 simon-watery kernel: [    1.698642]  [<ffffffff81066d0b>] warn_slowpath_common+0x7b/0xc0
Jun  9 11:14:18 simon-watery kernel: [    1.698644]  [<ffffffff81066d64>] warn_slowpath_null+0x14/0x20
Jun  9 11:14:18 simon-watery kernel: [    1.698646]  [<ffffffff810375ca>] hpet_next_event+0x7a/0x90
Jun  9 11:14:18 simon-watery kernel: [    1.698648]  [<ffffffff81037610>] hpet_legacy_next_event+0x10/0x20
Jun  9 11:14:18 simon-watery kernel: [    1.698652]  [<ffffffff81092e24>] clockevents_program_event+0x54/0xa0
Jun  9 11:14:18 simon-watery kernel: [    1.698654]  [<ffffffff81094378>] tick_dev_program_event+0x68/0xd0
Jun  9 11:14:18 simon-watery kernel: [    1.698657]  [<ffffffff81093cae>] tick_broadcast_oneshot_control+0x11e/0x120
Jun  9 11:14:18 simon-watery kernel: [    1.698659]  [<ffffffff810934c0>] tick_notify+0x130/0x200
Jun  9 11:14:18 simon-watery kernel: [    1.698662]  [<ffffffff81543b46>] notifier_call_chain+0x56/0x80
Jun  9 11:14:18 simon-watery kernel: [    1.698666]  [<ffffffff8108a366>] raw_notifier_call_chain+0x16/0x20
Jun  9 11:14:18 simon-watery kernel: [    1.698668]  [<ffffffff81092c47>] clockevents_notify+0x37/0x160
Jun  9 11:14:18 simon-watery kernel: [    1.698671]  [<ffffffff8130ccd5>] lapic_timer_state_broadcast+0x46/0x48
Jun  9 11:14:18 simon-watery kernel: [    1.698673]  [<ffffffff8130d244>] acpi_idle_enter_bm+0x187/0x2be
Jun  9 11:14:18 simon-watery kernel: [    1.698675]  [<ffffffff81543b06>] ? notifier_call_chain+0x16/0x80
Jun  9 11:14:18 simon-watery kernel: [    1.698678]  [<ffffffff81437537>] cpuidle_idle_call+0xa7/0x140
Jun  9 11:14:18 simon-watery kernel: [    1.698682]  [<ffffffff81011e73>] cpu_idle+0xb3/0x110
Jun  9 11:14:18 simon-watery kernel: [    1.698684]  [<ffffffff8153ad7b>] start_secondary+0xa8/0xaa
Jun  9 11:14:18 simon-watery kernel: [    1.698687] ---[ end trace 58841cc3d19f44f2 ]---
Jun  9 11:14:18 simon-watery kernel: [    1.701269] PM: Resume from disk failed.
Jun  9 11:14:18 simon-watery kernel: [    1.701275] registered taskstats version 1
Jun  9 11:14:18 simon-watery kernel: [    1.701552]   Magic number: 14:900:223
Jun  9 11:14:18 simon-watery kernel: [    1.701667] rtc_cmos 00:03: setting system clock to 2010-06-09 10:14:08 UTC (1276078448)
Jun  9 11:14:18 simon-watery kernel: [    1.701674] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun  9 11:14:18 simon-watery kernel: [    1.701676] EDD information not available.
Jun  9 11:14:18 simon-watery kernel: [    1.701711] Freeing unused kernel memory: 876k freed
Jun  9 11:14:18 simon-watery kernel: [    1.701814] Write protecting the kernel read-only data: 7680k
Jun  9 11:14:18 simon-watery kernel: [    1.716966] udev: starting version 151
Jun  9 11:14:18 simon-watery kernel: [    1.739335] ahci 0000:00:1f.2: version 3.0
Jun  9 11:14:18 simon-watery kernel: [    1.739348]   alloc irq_desc for 21 on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.739350]   alloc kstat_irqs on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.739356] ahci 0000:00:1f.2: PCI INT D -> GSI 21 (level, low) -> IRQ 21
Jun  9 11:14:18 simon-watery kernel: [    1.739391]   alloc irq_desc for 35 on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.739393]   alloc kstat_irqs on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.739400] ahci 0000:00:1f.2: irq 35 for MSI/MSI-X
Jun  9 11:14:18 simon-watery kernel: [    1.739429] ahci: SSS flag set, parallel bus scan disabled
Jun  9 11:14:18 simon-watery kernel: [    1.746372] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jun  9 11:14:18 simon-watery kernel: [    1.746383]   alloc irq_desc for 22 on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.746384]   alloc kstat_irqs on node -1
Jun  9 11:14:18 simon-watery kernel: [    1.746387] r8169 0000:07:04.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun  9 11:14:18 simon-watery kernel: [    1.746457] r8169 0000:07:04.0: no PCI Express capability
Jun  9 11:14:18 simon-watery kernel: [    1.746769] eth0: RTL8169sc/8110sc at 0xffffc90000c66400, 90:e6:ba:00:b7:62, XID 18000000 IRQ 22
Jun  9 11:14:18 simon-watery kernel: [    1.750841] ohci1394 0000:07:03.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun  9 11:14:18 simon-watery kernel: [    1.754712] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Jun  9 11:14:18 simon-watery kernel: [    1.754719] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems sxs apst 
Jun  9 11:14:18 simon-watery kernel: [    1.754726] ahci 0000:00:1f.2: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    1.807854] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[fbeff800-fbefffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jun  9 11:14:18 simon-watery kernel: [    1.854756] scsi0 : ahci
Jun  9 11:14:18 simon-watery kernel: [    1.855046] scsi1 : ahci
Jun  9 11:14:18 simon-watery kernel: [    1.855297] scsi2 : ahci
Jun  9 11:14:18 simon-watery kernel: [    1.855512] scsi3 : ahci
Jun  9 11:14:18 simon-watery kernel: [    1.855754] scsi4 : ahci
Jun  9 11:14:18 simon-watery kernel: [    1.856026] scsi5 : ahci
Jun  9 11:14:18 simon-watery kernel: [    1.856194] ata1: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7100 irq 35
Jun  9 11:14:18 simon-watery kernel: [    1.856197] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 35
Jun  9 11:14:18 simon-watery kernel: [    1.856199] ata3: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7200 irq 35
Jun  9 11:14:18 simon-watery kernel: [    1.856200] ata4: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7280 irq 35
Jun  9 11:14:18 simon-watery kernel: [    1.856202] ata5: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7300 irq 35
Jun  9 11:14:18 simon-watery kernel: [    1.856204] ata6: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 35
Jun  9 11:14:18 simon-watery kernel: [    1.995007] usb 1-1: new high speed USB device using ehci_hcd and address 2
Jun  9 11:14:18 simon-watery kernel: [    2.143506] usb 1-1: configuration #1 chosen from 1 choice
Jun  9 11:14:18 simon-watery kernel: [    2.143811] hub 1-1:1.0: USB hub found
Jun  9 11:14:18 simon-watery kernel: [    2.143984] hub 1-1:1.0: 6 ports detected
Jun  9 11:14:18 simon-watery kernel: [    2.264229] usb 2-1: new high speed USB device using ehci_hcd and address 2
Jun  9 11:14:18 simon-watery kernel: [    2.383878] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun  9 11:14:18 simon-watery kernel: [    2.384351] ata1.00: ATA-7: INTEL SSDSA2M080G2GC, 2CV102HD, max UDMA/133
Jun  9 11:14:18 simon-watery kernel: [    2.384356] ata1.00: 156301488 sectors, multi 1: LBA48 NCQ (depth 31/32)
Jun  9 11:14:18 simon-watery kernel: [    2.385051] ata1.00: configured for UDMA/133
Jun  9 11:14:18 simon-watery kernel: [    2.403944] scsi 0:0:0:0: Direct-Access     ATA      INTEL SSDSA2M080 2CV1 PQ: 0 ANSI: 5
Jun  9 11:14:18 simon-watery kernel: [    2.404059] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun  9 11:14:18 simon-watery kernel: [    2.404107] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Jun  9 11:14:18 simon-watery kernel: [    2.404133] sd 0:0:0:0: [sda] Write Protect is off
Jun  9 11:14:18 simon-watery kernel: [    2.404134] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun  9 11:14:18 simon-watery kernel: [    2.404146] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  9 11:14:18 simon-watery kernel: [    2.404215]  sda: sda1
Jun  9 11:14:18 simon-watery kernel: [    2.404839] sd 0:0:0:0: [sda] Attached SCSI disk
Jun  9 11:14:18 simon-watery kernel: [    2.414576] usb 2-1: configuration #1 chosen from 1 choice
Jun  9 11:14:18 simon-watery kernel: [    2.414901] hub 2-1:1.0: USB hub found
Jun  9 11:14:18 simon-watery kernel: [    2.415085] hub 2-1:1.0: 8 ports detected
Jun  9 11:14:18 simon-watery kernel: [    2.691283] usb 2-1.3: new high speed USB device using ehci_hcd and address 3
Jun  9 11:14:18 simon-watery kernel: [    2.801510] usb 2-1.3: configuration #1 chosen from 1 choice
Jun  9 11:14:18 simon-watery kernel: [    2.801743] hub 2-1.3:1.0: USB hub found
Jun  9 11:14:18 simon-watery kernel: [    2.801875] hub 2-1.3:1.0: 2 ports detected
Jun  9 11:14:18 simon-watery kernel: [    2.882586] usb 2-1.4: new low speed USB device using ehci_hcd and address 4
Jun  9 11:14:18 simon-watery kernel: [    3.028975] usb 2-1.4: configuration #1 chosen from 1 choice
Jun  9 11:14:18 simon-watery kernel: [    3.110048] usb 2-1.7: new high speed USB device using ehci_hcd and address 5
Jun  9 11:14:18 simon-watery kernel: [    3.122632] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0000a2df9b]
Jun  9 11:14:18 simon-watery kernel: [    3.221485] usb 2-1.7: configuration #1 chosen from 1 choice
Jun  9 11:14:18 simon-watery kernel: [    3.221919] hub 2-1.7:1.0: USB hub found
Jun  9 11:14:18 simon-watery kernel: [    3.222377] hub 2-1.7:1.0: 4 ports detected
Jun  9 11:14:18 simon-watery kernel: [    3.299502] usb 2-1.8: new low speed USB device using ehci_hcd and address 6
Jun  9 11:14:18 simon-watery kernel: [    3.331114] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun  9 11:14:18 simon-watery kernel: [    3.351773] ata2.00: ATA-8: SAMSUNG HD501LJ, CR100-13, max UDMA7
Jun  9 11:14:18 simon-watery kernel: [    3.351778] ata2.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Jun  9 11:14:18 simon-watery kernel: [    3.353981] ata2.00: configured for UDMA/133
Jun  9 11:14:18 simon-watery kernel: [    3.369218] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
Jun  9 11:14:18 simon-watery kernel: [    3.369337] sd 1:0:0:0: Attached scsi generic sg1 type 0
Jun  9 11:14:18 simon-watery kernel: [    3.369348] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jun  9 11:14:18 simon-watery kernel: [    3.369393] sd 1:0:0:0: [sdb] Write Protect is off
Jun  9 11:14:18 simon-watery kernel: [    3.369395] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jun  9 11:14:18 simon-watery kernel: [    3.369416] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  9 11:14:18 simon-watery kernel: [    3.369478]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 >
Jun  9 11:14:18 simon-watery kernel: [    3.411777] sd 1:0:0:0: [sdb] Attached SCSI disk
Jun  9 11:14:18 simon-watery kernel: [    3.427321] usb 2-1.8: configuration #1 chosen from 1 choice
Jun  9 11:14:18 simon-watery kernel: [    3.431758] usbcore: registered new interface driver hiddev
Jun  9 11:14:18 simon-watery kernel: [    3.508930] usb 2-1.3.1: new high speed USB device using ehci_hcd and address 7
Jun  9 11:14:18 simon-watery kernel: [    3.618905] usb 2-1.3.1: configuration #1 chosen from 1 choice
Jun  9 11:14:18 simon-watery kernel: [    3.619253] hub 2-1.3.1:1.0: USB hub found
Jun  9 11:14:18 simon-watery kernel: [    3.619455] hub 2-1.3.1:1.0: 4 ports detected
Jun  9 11:14:18 simon-watery kernel: [    3.708346] usb 2-1.3.2: new high speed USB device using ehci_hcd and address 8
Jun  9 11:14:18 simon-watery kernel: [    3.718208] ata3: SATA link down (SStatus 0 SControl 300)
Jun  9 11:14:18 simon-watery kernel: [    3.739444] generic-usb 0003:051D:0002.0001: hiddev96,hidraw0: USB HID v1.10 Device [American Power Conversion Back-UPS BR  800 FW:9.o4 .I USB FW:o4 ] on usb-0000:00:1d.0-1.4/input0
Jun  9 11:14:18 simon-watery kernel: [    3.748964] input: daskeyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.0/input/input3
Jun  9 11:14:18 simon-watery kernel: [    3.749006] generic-usb 0003:04D9:2013.0002: input,hidraw1: USB HID v1.10 Keyboard [daskeyboard] on usb-0000:00:1d.0-1.8/input0
Jun  9 11:14:18 simon-watery kernel: [    3.771846] input: daskeyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.1/input/input4
Jun  9 11:14:18 simon-watery kernel: [    3.771886] generic-usb 0003:04D9:2013.0003: input,hidraw2: USB HID v1.10 Device [daskeyboard] on usb-0000:00:1d.0-1.8/input1
Jun  9 11:14:18 simon-watery kernel: [    3.771896] usbcore: registered new interface driver usbhid
Jun  9 11:14:18 simon-watery kernel: [    3.771897] usbhid: v2.6:USB HID core driver
Jun  9 11:14:18 simon-watery kernel: [    3.907597] usb 2-1.3.2: configuration #1 chosen from 1 choice
Jun  9 11:14:18 simon-watery kernel: [    3.912322] Initializing USB Mass Storage driver...
Jun  9 11:14:18 simon-watery kernel: [    3.912664] scsi6 : SCSI emulation for USB Mass Storage devices
Jun  9 11:14:18 simon-watery kernel: [    3.912846] usb-storage: device found at 8
Jun  9 11:14:18 simon-watery kernel: [    3.912850] usb-storage: waiting for device to settle before scanning
Jun  9 11:14:18 simon-watery kernel: [    3.912864] usbcore: registered new interface driver usb-storage
Jun  9 11:14:18 simon-watery kernel: [    3.912869] USB Mass Storage support registered.
Jun  9 11:14:18 simon-watery kernel: [    3.987543] usb 2-1.3.1.1: new low speed USB device using ehci_hcd and address 9
Jun  9 11:14:18 simon-watery kernel: [    4.089037] ata4: SATA link down (SStatus 0 SControl 300)
Jun  9 11:14:18 simon-watery kernel: [    4.102183] usb 2-1.3.1.1: configuration #1 chosen from 1 choice
Jun  9 11:14:18 simon-watery kernel: [    4.104617] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.1/2-1.3.1.1/2-1.3.1.1:1.0/input/input5
Jun  9 11:14:18 simon-watery kernel: [    4.104659] generic-usb 0003:045E:0040.0004: input,hidraw3: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-1.3.1.1/input0
Jun  9 11:14:18 simon-watery kernel: [    4.457964] ata5: SATA link down (SStatus 0 SControl 300)
Jun  9 11:14:18 simon-watery kernel: [    5.403405] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun  9 11:14:18 simon-watery kernel: [    5.406450] ata6.00: ATAPI: PIONEER BD-ROM  BDC-202, 1.01, max UDMA/66
Jun  9 11:14:18 simon-watery kernel: [    5.409754] ata6.00: configured for UDMA/66
Jun  9 11:14:18 simon-watery kernel: [    5.441479] scsi 5:0:0:0: CD-ROM            PIONEER  BD-ROM  BDC-202  1.01 PQ: 0 ANSI: 5
Jun  9 11:14:18 simon-watery kernel: [    5.461013] sr0: scsi3-mmc drive: 32x/32x writer dvd-ram cd/rw xa/form2 cdda tray
Jun  9 11:14:18 simon-watery kernel: [    5.461019] Uniform CD-ROM driver Revision: 3.20
Jun  9 11:14:18 simon-watery kernel: [    5.461138] sr 5:0:0:0: Attached scsi CD-ROM sr0
Jun  9 11:14:18 simon-watery kernel: [    5.461193] sr 5:0:0:0: Attached scsi generic sg2 type 5
Jun  9 11:14:18 simon-watery kernel: [    5.634030] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jun  9 11:14:18 simon-watery kernel: [    5.761614] Adding 15998968k swap on /dev/sdb1.  Priority:-1 extents:1 across:15998968k 
Jun  9 11:14:18 simon-watery kernel: [    5.783079] udev: starting version 151
Jun  9 11:14:18 simon-watery kernel: [    5.807998] vga16fb: initializing
Jun  9 11:14:18 simon-watery kernel: [    5.808001] vga16fb: mapped to 0xffff8800000a0000
Jun  9 11:14:18 simon-watery kernel: [    5.808041] fb0: VGA16 VGA frame buffer device
Jun  9 11:14:18 simon-watery kernel: [    5.817786] lp: driver loaded but no devices found
Jun  9 11:14:18 simon-watery kernel: [    5.911412] nvidia: module license 'NVIDIA' taints kernel.
Jun  9 11:14:18 simon-watery kernel: [    5.911414] Disabling lock debugging due to kernel taint
Jun  9 11:14:18 simon-watery kernel: [    6.138665] type=1505 audit(1276078452.942:2):  operation="profile_load" pid=711 name="/sbin/dhclient3"
Jun  9 11:14:18 simon-watery kernel: [    6.138993] type=1505 audit(1276078452.942:3):  operation="profile_load" pid=711 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jun  9 11:14:18 simon-watery kernel: [    6.139168] type=1505 audit(1276078452.942:4):  operation="profile_load" pid=711 name="/usr/lib/connman/scripts/dhclient-script"
Jun  9 11:14:18 simon-watery kernel: [    6.163029] type=1505 audit(1276078452.972:5):  operation="profile_load" pid=764 name="/usr/sbin/ntpd"
Jun  9 11:14:18 simon-watery kernel: [    6.213877] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun  9 11:14:18 simon-watery kernel: [    6.213978] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    6.336325] EXT4-fs (sdb7): mounted filesystem with ordered data mode
Jun  9 11:14:18 simon-watery kernel: [    6.360656] Console: switching to colour frame buffer device 80x30
Jun  9 11:14:18 simon-watery kernel: [    6.366910] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  9 11:14:18 simon-watery kernel: [    6.366915] nvidia 0000:01:00.0: setting latency timer to 64
Jun  9 11:14:18 simon-watery kernel: [    6.366918] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jun  9 11:14:18 simon-watery kernel: [    6.367049] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.15  Fri Mar 12 00:29:13 PST 2010
Jun  9 11:14:18 simon-watery kernel: [    6.404094] EXT4-fs (sdb5): mounted filesystem with ordered data mode
Jun  9 11:14:18 simon-watery kernel: [    8.899106] usb-storage: device scan complete
Jun  9 11:14:18 simon-watery kernel: [    8.902649] scsi 6:0:0:0: Direct-Access     SMSC     223 U HS-CF      3.60 PQ: 0 ANSI: 0
Jun  9 11:14:18 simon-watery kernel: [    8.906013] scsi 6:0:0:1: Direct-Access     SMSC     223 U HS-MS      3.60 PQ: 0 ANSI: 0
Jun  9 11:14:18 simon-watery kernel: [    8.909127] scsi 6:0:0:2: Direct-Access     SMSC     223 U HS-SM      3.60 PQ: 0 ANSI: 0
Jun  9 11:14:18 simon-watery kernel: [    8.911996] scsi 6:0:0:3: Direct-Access     SMSC     223 U HS-SD/MMC  3.60 PQ: 0 ANSI: 0
Jun  9 11:14:18 simon-watery kernel: [    8.912212] sd 6:0:0:0: Attached scsi generic sg3 type 0
Jun  9 11:14:18 simon-watery kernel: [    8.912298] sd 6:0:0:1: Attached scsi generic sg4 type 0
Jun  9 11:14:18 simon-watery kernel: [    8.912373] sd 6:0:0:2: Attached scsi generic sg5 type 0
Jun  9 11:14:18 simon-watery kernel: [    8.912449] sd 6:0:0:3: Attached scsi generic sg6 type 0
Jun  9 11:14:18 simon-watery kernel: [    9.028731] sd 6:0:0:3: [sdf] Attached SCSI removable disk
Jun  9 11:14:18 simon-watery kernel: [    9.050929] sd 6:0:0:2: [sde] Attached SCSI removable disk
Jun  9 11:14:18 simon-watery kernel: [    9.094457] sd 6:0:0:1: [sdd] Attached SCSI removable disk
Jun  9 11:14:18 simon-watery kernel: [    9.113207] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Jun  9 11:14:18 simon-watery kernel: [   10.316190] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input6
Jun  9 11:14:18 simon-watery kernel: [   12.069396] EXT4-fs (sdb6): mounted filesystem with ordered data mode
Jun  9 11:14:18 simon-watery kernel: [   12.121334] type=1505 audit(1276078458.943:6):  operation="profile_load" pid=1101 name="/usr/share/gdm/guest-session/Xsession"
Jun  9 11:14:18 simon-watery kernel: [   12.122281] type=1505 audit(1276078458.943:7):  operation="profile_replace" pid=1102 name="/sbin/dhclient3"
Jun  9 11:14:18 simon-watery kernel: [   12.122583] type=1505 audit(1276078458.943:8):  operation="profile_replace" pid=1102 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jun  9 11:14:18 simon-watery kernel: [   12.122746] type=1505 audit(1276078458.943:9):  operation="profile_replace" pid=1102 name="/usr/lib/connman/scripts/dhclient-script"
Jun  9 11:14:18 simon-watery kernel: [   12.127459] type=1505 audit(1276078458.953:10):  operation="profile_load" pid=1103 name="/usr/bin/evince"
Jun  9 11:14:18 simon-watery kernel: [   12.131254] type=1505 audit(1276078458.953:11):  operation="profile_load" pid=1103 name="/usr/bin/evince-previewer"
Jun  9 11:14:18 simon-watery kernel: [   12.133649] type=1505 audit(1276078458.953:12):  operation="profile_load" pid=1103 name="/usr/bin/evince-thumbnailer"
Jun  9 11:14:18 simon-watery kernel: [   12.138006] type=1505 audit(1276078458.963:13):  operation="profile_load" pid=1108 name="/usr/lib/cups/backend/cups-pdf"
Jun  9 11:14:18 simon-watery kernel: [   12.138423] type=1505 audit(1276078458.963:14):  operation="profile_load" pid=1108 name="/usr/sbin/cupsd"
Jun  9 11:14:18 simon-watery kernel: [   12.139709] type=1505 audit(1276078458.963:15):  operation="profile_replace" pid=1110 name="/usr/sbin/ntpd"
Jun  9 11:14:19 simon-watery gdm-binary[1115]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jun  9 11:14:19 simon-watery NetworkManager: <info>  starting...
Jun  9 11:14:19 simon-watery NetworkManager: <info>  Trying to start the modem-manager...
Jun  9 11:14:19 simon-watery NetworkManager:    SCPlugin-Ifupdown: init!
Jun  9 11:14:19 simon-watery NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Jun  9 11:14:19 simon-watery NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Jun  9 11:14:19 simon-watery NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:07:04.0/net/eth0, iface: eth0)
Jun  9 11:14:19 simon-watery NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:07:04.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun  9 11:14:19 simon-watery NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun  9 11:14:19 simon-watery NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun  9 11:14:19 simon-watery NetworkManager:    SCPlugin-Ifupdown: end _init.
Jun  9 11:14:19 simon-watery NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun  9 11:14:19 simon-watery NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun  9 11:14:19 simon-watery modem-manager: Loaded plugin Generic
Jun  9 11:14:19 simon-watery NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Jun  9 11:14:19 simon-watery NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Jun  9 11:14:19 simon-watery NetworkManager:    SCPlugin-Ifupdown: (22690080) ... get_connections.
Jun  9 11:14:19 simon-watery NetworkManager:    SCPlugin-Ifupdown: (22690080) ... get_connections (managed=false): return empty list.
Jun  9 11:14:19 simon-watery modem-manager: Loaded plugin ZTE
Jun  9 11:14:19 simon-watery modem-manager: Loaded plugin Huawei
Jun  9 11:14:19 simon-watery modem-manager: Loaded plugin Novatel
Jun  9 11:14:19 simon-watery modem-manager: Loaded plugin Longcheer
Jun  9 11:14:19 simon-watery NetworkManager:    Ifupdown: get unmanaged devices count: 0
Jun  9 11:14:19 simon-watery modem-manager: Loaded plugin Sierra
Jun  9 11:14:19 simon-watery modem-manager: Loaded plugin Gobi
Jun  9 11:14:19 simon-watery NetworkManager: <info>  (eth0): carrier is OFF
Jun  9 11:14:19 simon-watery NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Jun  9 11:14:19 simon-watery NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun  9 11:14:19 simon-watery modem-manager: Loaded plugin Nokia
Jun  9 11:14:19 simon-watery modem-manager: Loaded plugin Option
Jun  9 11:14:19 simon-watery modem-manager: Loaded plugin MotoC
Jun  9 11:14:19 simon-watery modem-manager: Loaded plugin AnyData
Jun  9 11:14:19 simon-watery modem-manager: Loaded plugin Ericsson MBM
Jun  9 11:14:19 simon-watery modem-manager: Loaded plugin Option High-Speed
Jun  9 11:14:19 simon-watery gdm-simple-slave[1204]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jun  9 11:14:19 simon-watery gdm-binary[1115]: WARNING: Unable to find users: no seat-id found
Jun  9 11:14:19 simon-watery NetworkManager: <info>  (eth0): now managed
Jun  9 11:14:19 simon-watery NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jun  9 11:14:19 simon-watery NetworkManager: <info>  (eth0): bringing up device.
Jun  9 11:14:19 simon-watery kernel: [   12.283486] r8169: eth0: link down
Jun  9 11:14:19 simon-watery kernel: [   12.283963] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  9 11:14:19 simon-watery NetworkManager: <info>  (eth0): preparing device.
Jun  9 11:14:19 simon-watery NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jun  9 11:14:19 simon-watery NetworkManager: <info>  modem-manager is now available
Jun  9 11:14:19 simon-watery NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun  9 11:14:19 simon-watery NetworkManager: <info>  Trying to start the supplicant...
Jun  9 11:14:21 simon-watery cron[1249]: (CRON) INFO (pidfile fd = 3)
Jun  9 11:14:21 simon-watery init: apport pre-start process (1244) terminated with status 1
Jun  9 11:14:21 simon-watery acpid: starting up with proc fs
Jun  9 11:14:21 simon-watery anacron[1259]: Anacron 2.3 started on 2010-06-09
Jun  9 11:14:21 simon-watery cron[1262]: (CRON) STARTUP (fork ok)
Jun  9 11:14:21 simon-watery init: apport post-stop process (1261) terminated with status 1
Jun  9 11:14:21 simon-watery cron[1262]: (CRON) INFO (Running @reboot jobs)
Jun  9 11:14:21 simon-watery acpid: 36 rules loaded
Jun  9 11:14:21 simon-watery acpid: waiting for events: event logging is off
Jun  9 11:14:21 simon-watery anacron[1259]: Normal exit (0 jobs run)
Jun  9 11:14:21 simon-watery NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Jun  9 11:14:21 simon-watery NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
Jun  9 11:14:21 simon-watery NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
Jun  9 11:14:21 simon-watery kernel: [   14.328341] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Jun  9 11:14:21 simon-watery kernel: [   14.328343] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
Jun  9 11:14:21 simon-watery kernel: [   14.328344] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
Jun  9 11:14:21 simon-watery kernel: [   14.328345] vboxdrv: the usage of hardware performance counters by
Jun  9 11:14:21 simon-watery kernel: [   14.328345] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
Jun  9 11:14:21 simon-watery kernel: [   14.328348] vboxdrv: Found 8 processor cores.
Jun  9 11:14:21 simon-watery kernel: [   14.328383] VBoxDrv: dbg - g_abExecMemory=ffffffffa0d0da20
Jun  9 11:14:21 simon-watery kernel: [   14.328540] vboxdrv: fAsync=0 offMin=0x24f offMax=0x2903b
Jun  9 11:14:21 simon-watery kernel: [   14.328563] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jun  9 11:14:21 simon-watery kernel: [   14.328564] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
Jun  9 11:14:21 simon-watery kernel: [   14.429324] ppdev: user-space parallel port driver
Jun  9 11:14:21 simon-watery anacron[1424]: Anacron 2.3 started on 2010-06-09
Jun  9 11:14:21 simon-watery anacron[1424]: Normal exit (0 jobs run)
Jun  9 11:14:21 simon-watery kernel: [   14.649635] CPU0 attaching NULL sched-domain.
Jun  9 11:14:21 simon-watery kernel: [   14.649644] CPU1 attaching NULL sched-domain.
Jun  9 11:14:21 simon-watery kernel: [   14.649653] CPU2 attaching NULL sched-domain.
Jun  9 11:14:21 simon-watery kernel: [   14.649659] CPU3 attaching NULL sched-domain.
Jun  9 11:14:21 simon-watery kernel: [   14.649660] CPU4 attaching NULL sched-domain.
Jun  9 11:14:21 simon-watery kernel: [   14.649662] CPU5 attaching NULL sched-domain.
Jun  9 11:14:21 simon-watery kernel: [   14.649665] CPU6 attaching NULL sched-domain.
Jun  9 11:14:21 simon-watery kernel: [   14.649668] CPU7 attaching NULL sched-domain.
Jun  9 11:14:21 simon-watery acpid: client connected from 1212[0:0]
Jun  9 11:14:21 simon-watery acpid: 1 client rule loaded
Jun  9 11:14:21 simon-watery kernel: [   14.806606] CPU0 attaching sched-domain:
Jun  9 11:14:21 simon-watery kernel: [   14.806608]  domain 0: span 0,4 level SIBLING
Jun  9 11:14:21 simon-watery kernel: [   14.806609]   groups: 0 (cpu_power = 589) 4 (cpu_power = 589)
Jun  9 11:14:21 simon-watery kernel: [   14.806612]   domain 1: span 0-7 level MC
Jun  9 11:14:21 simon-watery kernel: [   14.806614]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun  9 11:14:21 simon-watery kernel: [   14.806619] CPU1 attaching sched-domain:
Jun  9 11:14:21 simon-watery kernel: [   14.806620]  domain 0: span 1,5 level SIBLING
Jun  9 11:14:21 simon-watery kernel: [   14.806621]   groups: 1 (cpu_power = 589) 5 (cpu_power = 589)
Jun  9 11:14:21 simon-watery kernel: [   14.806624]   domain 1: span 0-7 level MC
Jun  9 11:14:21 simon-watery kernel: [   14.806625]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun  9 11:14:21 simon-watery kernel: [   14.806629] CPU2 attaching sched-domain:
Jun  9 11:14:21 simon-watery kernel: [   14.806630]  domain 0: span 2,6 level SIBLING
Jun  9 11:14:21 simon-watery kernel: [   14.806631]   groups: 2 (cpu_power = 589) 6 (cpu_power = 589)
Jun  9 11:14:21 simon-watery kernel: [   14.806634]   domain 1: span 0-7 level MC
Jun  9 11:14:21 simon-watery kernel: [   14.806635]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun  9 11:14:21 simon-watery kernel: [   14.806639] CPU3 attaching sched-domain:
Jun  9 11:14:21 simon-watery kernel: [   14.806640]  domain 0: span 3,7 level SIBLING
Jun  9 11:14:21 simon-watery kernel: [   14.806642]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
Jun  9 11:14:21 simon-watery kernel: [   14.806644]   domain 1: span 0-7 level MC
Jun  9 11:14:21 simon-watery kernel: [   14.806645]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun  9 11:14:21 simon-watery kernel: [   14.806650] CPU4 attaching sched-domain:
Jun  9 11:14:21 simon-watery kernel: [   14.806651]  domain 0: span 0,4 level SIBLING
Jun  9 11:14:21 simon-watery kernel: [   14.806652]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
Jun  9 11:14:21 simon-watery kernel: [   14.806654]   domain 1: span 0-7 level MC
Jun  9 11:14:21 simon-watery kernel: [   14.806655]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun  9 11:14:21 simon-watery kernel: [   14.806660] CPU5 attaching sched-domain:
Jun  9 11:14:21 simon-watery kernel: [   14.806661]  domain 0: span 1,5 level SIBLING
Jun  9 11:14:21 simon-watery kernel: [   14.806662]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
Jun  9 11:14:21 simon-watery kernel: [   14.806664]   domain 1: span 0-7 level MC
Jun  9 11:14:21 simon-watery kernel: [   14.806665]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun  9 11:14:21 simon-watery kernel: [   14.806670] CPU6 attaching sched-domain:
Jun  9 11:14:21 simon-watery kernel: [   14.806671]  domain 0: span 2,6 level SIBLING
Jun  9 11:14:21 simon-watery kernel: [   14.806672]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
Jun  9 11:14:21 simon-watery kernel: [   14.806674]   domain 1: span 0-7 level MC
Jun  9 11:14:21 simon-watery kernel: [   14.806675]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun  9 11:14:21 simon-watery kernel: [   14.806680] CPU7 attaching sched-domain:
Jun  9 11:14:21 simon-watery kernel: [   14.806681]  domain 0: span 3,7 level SIBLING
Jun  9 11:14:21 simon-watery kernel: [   14.806682]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
Jun  9 11:14:21 simon-watery kernel: [   14.806684]   domain 1: span 0-7 level MC
Jun  9 11:14:21 simon-watery kernel: [   14.806686]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun  9 11:14:21 simon-watery kernel: [   14.807192] CPU0 attaching NULL sched-domain.
Jun  9 11:14:21 simon-watery kernel: [   14.807194] CPU1 attaching NULL sched-domain.
Jun  9 11:14:21 simon-watery kernel: [   14.807195] CPU2 attaching NULL sched-domain.
Jun  9 11:14:21 simon-watery kernel: [   14.807196] CPU3 attaching NULL sched-domain.
Jun  9 11:14:21 simon-watery kernel: [   14.807197] CPU4 attaching NULL sched-domain.
Jun  9 11:14:21 simon-watery kernel: [   14.807198] CPU5 attaching NULL sched-domain.
Jun  9 11:14:21 simon-watery kernel: [   14.807199] CPU6 attaching NULL sched-domain.
Jun  9 11:14:21 simon-watery kernel: [   14.807200] CPU7 attaching NULL sched-domain.
Jun  9 11:14:21 simon-watery kernel: [   14.956163] CPU0 attaching sched-domain:
Jun  9 11:14:21 simon-watery kernel: [   14.956165]  domain 0: span 0,4 level SIBLING
Jun  9 11:14:21 simon-watery kernel: [   14.956166]   groups: 0 (cpu_power = 589) 4 (cpu_power = 589)
Jun  9 11:14:21 simon-watery kernel: [   14.956169]   domain 1: span 0-7 level MC
Jun  9 11:14:21 simon-watery kernel: [   14.956170]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun  9 11:14:21 simon-watery kernel: [   14.956175] CPU1 attaching sched-domain:
Jun  9 11:14:21 simon-watery kernel: [   14.956176]  domain 0: span 1,5 level SIBLING
Jun  9 11:14:21 simon-watery kernel: [   14.956177]   groups: 1 (cpu_power = 589) 5 (cpu_power = 589)
Jun  9 11:14:21 simon-watery kernel: [   14.956179]   domain 1: span 0-7 level MC
Jun  9 11:14:21 simon-watery kernel: [   14.956180]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun  9 11:14:21 simon-watery kernel: [   14.956185] CPU2 attaching sched-domain:
Jun  9 11:14:21 simon-watery kernel: [   14.956186]  domain 0: span 2,6 level SIBLING
Jun  9 11:14:21 simon-watery kernel: [   14.956187]   groups: 2 (cpu_power = 589) 6 (cpu_power = 589)
Jun  9 11:14:21 simon-watery kernel: [   14.956189]   domain 1: span 0-7 level MC
Jun  9 11:14:21 simon-watery kernel: [   14.956190]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun  9 11:14:21 simon-watery kernel: [   14.956194] CPU3 attaching sched-domain:
Jun  9 11:14:21 simon-watery kernel: [   14.956195]  domain 0: span 3,7 level SIBLING
Jun  9 11:14:21 simon-watery kernel: [   14.956196]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
Jun  9 11:14:21 simon-watery kernel: [   14.956199]   domain 1: span 0-7 level MC
Jun  9 11:14:21 simon-watery kernel: [   14.956200]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun  9 11:14:21 simon-watery kernel: [   14.956204] CPU4 attaching sched-domain:
Jun  9 11:14:21 simon-watery kernel: [   14.956205]  domain 0: span 0,4 level SIBLING
Jun  9 11:14:21 simon-watery kernel: [   14.956206]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
Jun  9 11:14:21 simon-watery kernel: [   14.956208]   domain 1: span 0-7 level MC
Jun  9 11:14:21 simon-watery kernel: [   14.956209]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun  9 11:14:21 simon-watery kernel: [   14.956214] CPU5 attaching sched-domain:
Jun  9 11:14:21 simon-watery kernel: [   14.956215]  domain 0: span 1,5 level SIBLING
Jun  9 11:14:21 simon-watery kernel: [   14.956216]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
Jun  9 11:14:21 simon-watery kernel: [   14.956218]   domain 1: span 0-7 level MC
Jun  9 11:14:21 simon-watery kernel: [   14.956219]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun  9 11:14:21 simon-watery kernel: [   14.956223] CPU6 attaching sched-domain:
Jun  9 11:14:21 simon-watery kernel: [   14.956224]  domain 0: span 2,6 level SIBLING
Jun  9 11:14:21 simon-watery kernel: [   14.956225]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
Jun  9 11:14:21 simon-watery kernel: [   14.956228]   domain 1: span 0-7 level MC
Jun  9 11:14:21 simon-watery kernel: [   14.956229]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun  9 11:14:21 simon-watery kernel: [   14.956233] CPU7 attaching sched-domain:
Jun  9 11:14:21 simon-watery kernel: [   14.956234]  domain 0: span 3,7 level SIBLING
Jun  9 11:14:21 simon-watery kernel: [   14.956235]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
Jun  9 11:14:21 simon-watery kernel: [   14.956237]   domain 1: span 0-7 level MC
Jun  9 11:14:21 simon-watery kernel: [   14.956238]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun  9 11:14:22 simon-watery gdm-session-worker[1487]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jun  9 11:14:22 simon-watery rtkit-daemon[1495]: Sucessfully called chroot.
Jun  9 11:14:22 simon-watery rtkit-daemon[1495]: Sucessfully dropped privileges.
Jun  9 11:14:22 simon-watery rtkit-daemon[1495]: Sucessfully limited resources.
Jun  9 11:14:22 simon-watery rtkit-daemon[1495]: Running.
Jun  9 11:14:22 simon-watery rtkit-daemon[1495]: Watchdog thread running.
Jun  9 11:14:22 simon-watery rtkit-daemon[1495]: Canary thread running.
Jun  9 11:14:22 simon-watery polkitd[1499]: started daemon version 0.96 using authority implementation `local' version `0.96'
Jun  9 11:14:22 simon-watery rtkit-daemon[1495]: Sucessfully made thread 1493 of process 1493 (n/a) owned by '114' high priority at nice level -11.
Jun  9 11:14:22 simon-watery rtkit-daemon[1495]: Supervising 1 threads of 1 processes of 1 users.
Jun  9 11:14:22 simon-watery pulseaudio[1493]: shm.c: shm_open() failed: Permission denied
Jun  9 11:14:22 simon-watery pulseaudio[1493]: core.c: failed to allocate shared memory pool. Falling back to a normal memory pool.
Jun  9 11:14:23 simon-watery gdm-simple-greeter[1484]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Jun  9 11:14:23 simon-watery rtkit-daemon[1495]: Sucessfully made thread 1548 of process 1493 (n/a) owned by '114' RT at priority 5.
Jun  9 11:14:23 simon-watery rtkit-daemon[1495]: Supervising 2 threads of 1 processes of 1 users.
Jun  9 11:14:23 simon-watery anacron[1563]: Anacron 2.3 started on 2010-06-09
Jun  9 11:14:23 simon-watery anacron[1563]: Normal exit (0 jobs run)
Jun  9 11:14:23 simon-watery rtkit-daemon[1495]: Sucessfully made thread 1561 of process 1493 (n/a) owned by '114' RT at priority 5.
Jun  9 11:14:23 simon-watery rtkit-daemon[1495]: Supervising 3 threads of 1 processes of 1 users.
Jun  9 11:14:23 simon-watery kernel: [   16.262029] CPU0 attaching NULL sched-domain.
Jun  9 11:14:23 simon-watery kernel: [   16.262032] CPU1 attaching NULL sched-domain.
Jun  9 11:14:23 simon-watery kernel: [   16.262033] CPU2 attaching NULL sched-domain.
Jun  9 11:14:23 simon-watery kernel: [   16.262034] CPU3 attaching NULL sched-domain.
Jun  9 11:14:23 simon-watery kernel: [   16.262036] CPU4 attaching NULL sched-domain.
Jun  9 11:14:23 simon-watery kernel: [   16.262037] CPU5 attaching NULL sched-domain.
Jun  9 11:14:23 simon-watery kernel: [   16.262038] CPU6 attaching NULL sched-domain.
Jun  9 11:14:23 simon-watery kernel: [   16.262039] CPU7 attaching NULL sched-domain.
Jun  9 11:14:23 simon-watery acpid: client connected from 1587[108:114]
Jun  9 11:14:23 simon-watery acpid: 1 client rule loaded
Jun  9 11:14:23 simon-watery kernel: [   16.353665] CPU0 attaching sched-domain:
Jun  9 11:14:23 simon-watery kernel: [   16.353668]  domain 0: span 0,4 level SIBLING
Jun  9 11:14:23 simon-watery kernel: [   16.353669]   groups: 0 (cpu_power = 589) 4 (cpu_power = 589)
Jun  9 11:14:23 simon-watery kernel: [   16.353672]   domain 1: span 0-7 level MC
Jun  9 11:14:23 simon-watery kernel: [   16.353674]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun  9 11:14:23 simon-watery kernel: [   16.353680] CPU1 attaching sched-domain:
Jun  9 11:14:23 simon-watery kernel: [   16.353681]  domain 0: span 1,5 level SIBLING
Jun  9 11:14:23 simon-watery kernel: [   16.353682]   groups: 1 (cpu_power = 589) 5 (cpu_power = 589)
Jun  9 11:14:23 simon-watery kernel: [   16.353685]   domain 1: span 0-7 level MC
Jun  9 11:14:23 simon-watery kernel: [   16.353686]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun  9 11:14:23 simon-watery kernel: [   16.353691] CPU2 attaching sched-domain:
Jun  9 11:14:23 simon-watery kernel: [   16.353692]  domain 0: span 2,6 level SIBLING
Jun  9 11:14:23 simon-watery kernel: [   16.353693]   groups: 2 (cpu_power = 589) 6 (cpu_power = 589)
Jun  9 11:14:23 simon-watery kernel: [   16.353696]   domain 1: span 0-7 level MC
Jun  9 11:14:23 simon-watery kernel: [   16.353697]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun  9 11:14:23 simon-watery kernel: [   16.353704] CPU3 attaching sched-domain:
Jun  9 11:14:23 simon-watery kernel: [   16.353705]  domain 0: span 3,7 level SIBLING
Jun  9 11:14:23 simon-watery kernel: [   16.353706]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
Jun  9 11:14:23 simon-watery kernel: [   16.353709]   domain 1: span 0-7 level MC
Jun  9 11:14:23 simon-watery kernel: [   16.353710]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun  9 11:14:23 simon-watery kernel: [   16.353714] CPU4 attaching sched-domain:
Jun  9 11:14:23 simon-watery kernel: [   16.353715]  domain 0: span 0,4 level SIBLING
Jun  9 11:14:23 simon-watery kernel: [   16.353716]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
Jun  9 11:14:23 simon-watery kernel: [   16.353719]   domain 1: span 0-7 level MC
Jun  9 11:14:23 simon-watery kernel: [   16.353720]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun  9 11:14:23 simon-watery kernel: [   16.353724] CPU5 attaching sched-domain:
Jun  9 11:14:23 simon-watery kernel: [   16.353725]  domain 0: span 1,5 level SIBLING
Jun  9 11:14:23 simon-watery kernel: [   16.353726]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
Jun  9 11:14:23 simon-watery kernel: [   16.353729]   domain 1: span 0-7 level MC
Jun  9 11:14:23 simon-watery kernel: [   16.353730]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun  9 11:14:23 simon-watery kernel: [   16.353734] CPU6 attaching sched-domain:
Jun  9 11:14:23 simon-watery kernel: [   16.353735]  domain 0: span 2,6 level SIBLING
Jun  9 11:14:23 simon-watery kernel: [   16.353737]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
Jun  9 11:14:23 simon-watery kernel: [   16.353739]   domain 1: span 0-7 level MC
Jun  9 11:14:23 simon-watery kernel: [   16.353740]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun  9 11:14:23 simon-watery kernel: [   16.353745] CPU7 attaching sched-domain:
Jun  9 11:14:23 simon-watery kernel: [   16.353746]  domain 0: span 3,7 level SIBLING
Jun  9 11:14:23 simon-watery kernel: [   16.353747]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
Jun  9 11:14:23 simon-watery kernel: [   16.353749]   domain 1: span 0-7 level MC
Jun  9 11:14:23 simon-watery kernel: [   16.353750]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun  9 11:14:23 simon-watery kernel: [   16.354232] CPU0 attaching NULL sched-domain.
Jun  9 11:14:23 simon-watery kernel: [   16.354234] CPU1 attaching NULL sched-domain.
Jun  9 11:14:23 simon-watery kernel: [   16.354236] CPU2 attaching NULL sched-domain.
Jun  9 11:14:23 simon-watery kernel: [   16.354237] CPU3 attaching NULL sched-domain.
Jun  9 11:14:23 simon-watery kernel: [   16.354238] CPU4 attaching NULL sched-domain.
Jun  9 11:14:23 simon-watery kernel: [   16.354239] CPU5 attaching NULL sched-domain.
Jun  9 11:14:23 simon-watery kernel: [   16.354240] CPU6 attaching NULL sched-domain.
Jun  9 11:14:23 simon-watery kernel: [   16.354241] CPU7 attaching NULL sched-domain.
Jun  9 11:14:23 simon-watery kernel: [   16.433503] CPU0 attaching sched-domain:
Jun  9 11:14:23 simon-watery kernel: [   16.433505]  domain 0: span 0,4 level SIBLING
Jun  9 11:14:23 simon-watery kernel: [   16.433507]   groups: 0 (cpu_power = 589) 4 (cpu_power = 589)
Jun  9 11:14:23 simon-watery kernel: [   16.433509]   domain 1: span 0-7 level MC
Jun  9 11:14:23 simon-watery kernel: [   16.433511]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun  9 11:14:23 simon-watery kernel: [   16.433516] CPU1 attaching sched-domain:
Jun  9 11:14:23 simon-watery kernel: [   16.433517]  domain 0: span 1,5 level SIBLING
Jun  9 11:14:23 simon-watery kernel: [   16.433518]   groups: 1 (cpu_power = 589) 5 (cpu_power = 589)
Jun  9 11:14:23 simon-watery kernel: [   16.433520]   domain 1: span 0-7 level MC
Jun  9 11:14:23 simon-watery kernel: [   16.433521]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun  9 11:14:23 simon-watery kernel: [   16.433526] CPU2 attaching sched-domain:
Jun  9 11:14:23 simon-watery kernel: [   16.433527]  domain 0: span 2,6 level SIBLING
Jun  9 11:14:23 simon-watery kernel: [   16.433528]   groups: 2 (cpu_power = 589) 6 (cpu_power = 589)
Jun  9 11:14:23 simon-watery kernel: [   16.433530]   domain 1: span 0-7 level MC
Jun  9 11:14:23 simon-watery kernel: [   16.433531]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun  9 11:14:23 simon-watery kernel: [   16.433535] CPU3 attaching sched-domain:
Jun  9 11:14:23 simon-watery kernel: [   16.433536]  domain 0: span 3,7 level SIBLING
Jun  9 11:14:23 simon-watery kernel: [   16.433537]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
Jun  9 11:14:23 simon-watery kernel: [   16.433540]   domain 1: span 0-7 level MC
Jun  9 11:14:23 simon-watery kernel: [   16.433541]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun  9 11:14:23 simon-watery kernel: [   16.433545] CPU4 attaching sched-domain:
Jun  9 11:14:23 simon-watery kernel: [   16.433546]  domain 0: span 0,4 level SIBLING
Jun  9 11:14:23 simon-watery kernel: [   16.433547]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
Jun  9 11:14:23 simon-watery kernel: [   16.433549]   domain 1: span 0-7 level MC
Jun  9 11:14:23 simon-watery kernel: [   16.433550]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun  9 11:14:23 simon-watery kernel: [   16.433555] CPU5 attaching sched-domain:
Jun  9 11:14:23 simon-watery kernel: [   16.433556]  domain 0: span 1,5 level SIBLING
Jun  9 11:14:23 simon-watery kernel: [   16.433557]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
Jun  9 11:14:23 simon-watery kernel: [   16.433559]   domain 1: span 0-7 level MC
Jun  9 11:14:23 simon-watery kernel: [   16.433560]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun  9 11:14:23 simon-watery kernel: [   16.433564] CPU6 attaching sched-domain:
Jun  9 11:14:23 simon-watery kernel: [   16.433565]  domain 0: span 2,6 level SIBLING
Jun  9 11:14:23 simon-watery kernel: [   16.433566]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
Jun  9 11:14:23 simon-watery kernel: [   16.433569]   domain 1: span 0-7 level MC
Jun  9 11:14:23 simon-watery kernel: [   16.433570]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun  9 11:14:23 simon-watery kernel: [   16.433574] CPU7 attaching sched-domain:
Jun  9 11:14:23 simon-watery kernel: [   16.433575]  domain 0: span 3,7 level SIBLING
Jun  9 11:14:23 simon-watery kernel: [   16.433576]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
Jun  9 11:14:23 simon-watery kernel: [   16.433578]   domain 1: span 0-7 level MC
Jun  9 11:14:23 simon-watery kernel: [   16.433579]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun  9 11:14:24 simon-watery gdm-session-worker[1487]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jun  9 11:14:30 simon-watery rtkit-daemon[1495]: Sucessfully made thread 1691 of process 1691 (n/a) owned by '1000' high priority at nice level -11.
Jun  9 11:14:30 simon-watery rtkit-daemon[1495]: Supervising 4 threads of 2 processes of 2 users.
Jun  9 11:14:30 simon-watery pulseaudio[1691]: shm.c: shm_open() failed: Permission denied
Jun  9 11:14:30 simon-watery pulseaudio[1691]: core.c: failed to allocate shared memory pool. Falling back to a normal memory pool.
Jun  9 11:14:30 simon-watery rtkit-daemon[1495]: Sucessfully made thread 1705 of process 1691 (n/a) owned by '1000' RT at priority 5.
Jun  9 11:14:30 simon-watery rtkit-daemon[1495]: Supervising 5 threads of 2 processes of 2 users.
Jun  9 11:14:30 simon-watery rtkit-daemon[1495]: Sucessfully made thread 1706 of process 1691 (n/a) owned by '1000' RT at priority 5.
Jun  9 11:14:30 simon-watery rtkit-daemon[1495]: Supervising 6 threads of 2 processes of 2 users.
Jun  9 11:14:30 simon-watery rtkit-daemon[1495]: Sucessfully made thread 1711 of process 1711 (n/a) owned by '1000' high priority at nice level -11.
Jun  9 11:14:30 simon-watery rtkit-daemon[1495]: Supervising 7 threads of 3 processes of 2 users.
Jun  9 11:14:30 simon-watery pulseaudio[1711]: pid.c: Daemon already running.

```

As usual, I pressed "M" then exited the shell without doing anything.

---

### Post by spmurphy on 2010-06-09
There doesn't seem to be anything in that log about the "serious errors".

Presumably it's in a different log. Anyone got any ideas where?

---

### Post by Peter09 on 2010-06-10
try the output of
 
```
dmsg| more
```
 
this is also in the log files - it should show all your boot sequence log messages.

---

### Post by dcstar on 2010-06-10
> **spmurphy said:**
> Clean install of 64 bit 10.04 onto (previously) working hardware.

On boot, sometimes the boot process stops and under the 5 little dots displays a message saying "Serious errors were found in " and then either /var or /home. This screen gives me the option to "I" ignore it, "M" manually fix it or a third option beginning with "S" that I can't remember. I'll update this post next time I reboot. If I select "M" to manually fix it followed by Ctrl-D to end the shell i.e. I didn't attempt to fix whatever is wrong, it boots as if nothing were wrong. Machine works perfectly.

I've rebooted with my live cd and checked the /var and /home with the disk utility and it reports they're both fine, no errors. My root is on an 80 gig intel **ssd** and /var and /home are both on a 500 gig **magnetic**. .........
Does anyone have any fault finding suggestions?

SSDs will give your MB a ready status long before a mechanical disk has spun up, it is possible that the system is booting too quickly off the SSD before the old disk is actually ready.

See if the BIOS HDD delay setting helps in giving the mechanical disk more time to get ready before system boot.

---

### Post by spmurphy on 2010-06-10
Thank you both for the suggestions. I've just rebooted 6 times and no complaints, heh. Sod's law.

Next time it fails, I'll check dmesg. I thought I'd looked at that one, but will check it again next failure.

I'd also considered the performance differences between the SSD and the magnetic but thought it didn't matter as there's a good 8 seconds of BIOS before it starts to boot. Maybe there's a reset after that time that needs a pause? I know squat about the Linux boot process and this BIOS has no options for spin up type delays.

---

### Post by spmurphy on 2010-06-11
Ok, "Serious errors" when I booted tonight.

dmesg output:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 (Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=f7185e7c-bb4e-414b-b15c-62e18742ea57 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf670000 (usable)
[    0.000000]  BIOS-e820: 00000000bf670000 - 00000000bf688000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf688000 - 00000000bf6dc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6dc000 - 00000000bf700000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf800000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000240000000 (usable)
[    0.000000] DMI 2.6 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x240000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-E7FFF write-through
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000bff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbf670 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009e800 (usable)
[    0.000000]  modified: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf670000 (usable)
[    0.000000]  modified: 00000000bf670000 - 00000000bf688000 (ACPI data)
[    0.000000]  modified: 00000000bf688000 - 00000000bf6dc000 (ACPI NVS)
[    0.000000]  modified: 00000000bf6dc000 - 00000000bf700000 (reserved)
[    0.000000]  modified: 00000000bf800000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000240000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf670000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf670000 page 4k
[    0.000000] kernel direct mapping tables up to bf670000 @ 10000-15000
[    0.000000] init_memory_mapping: 0000000100000000-0000000240000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0240000000 page 2M
[    0.000000] kernel direct mapping tables up to 240000000 @ 13000-1d000
[    0.000000] RAMDISK: 377fe000 - 37fef810
[    0.000000] ACPI: RSDP 00000000000fad50 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000bf670100 0005C (v01 122109 XSDT1805 20091221 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bf670290 000F4 (v03 122109 FACP1805 20091221 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bf6704a0 0F151 (v01  A1320 A1320001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000bf688000 00040
[    0.000000] ACPI: APIC 00000000bf670390 000CC (v01 122109 APIC1805 20091221 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bf670460 0003C (v01 122109 OEMMCFG  20091221 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bf688040 00072 (v01 122109 OEMB1805 20091221 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bf67f6a0 00038 (v01 122109 OEMHPET  20091221 MSFT 00000097)
[    0.000000] ACPI: OSFR 00000000bf67f6e0 000B0 (v01 122109 OEMOSFR  20091221 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bf68ad80 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000240000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000240000000
[    0.000000]   NODE_DATA [0000000000018000 - 000000000001cfff]
[    0.000000]   bootmap [000000000001d000 -  0000000000064fff] pages 48
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0240000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
[    0.000000]   #3 [00377fe000 - 0037fef810]          RAMDISK ==> [00377fe000 - 0037fef810]
[    0.000000]   #4 [000009e800 - 0000100000]    BIOS reserved ==> [000009e800 - 0000100000]
[    0.000000]   #5 [0001a2a000 - 0001a2a2d0]              BRK ==> [0001a2a000 - 0001a2a2d0]
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000]   #7 [0000013000 - 0000018000]          PGTABLE ==> [0000013000 - 0000018000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea0007dfffff] PMD -> [ffff880028600000-ffff88002f5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00240000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bf670
[    0.000000]     0: 0x00100000 -> 0x00240000
[    0.000000] On node 0 totalpages: 2094590
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 108 pages reserved
[    0.000000]   DMA zone: 3818 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 765608 pages, LIFO batch:31
[    0.000000]   Normal zone: 17920 pages used for memmap
[    0.000000]   Normal zone: 1292800 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 16 CPUs, 8 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf670000 - 00000000bf688000
[    0.000000] PM: Registered nosave memory: 00000000bf688000 - 00000000bf6dc000
[    0.000000] PM: Registered nosave memory: 00000000bf6dc000 - 00000000bf700000
[    0.000000] PM: Registered nosave memory: 00000000bf700000 - 00000000bf800000
[    0.000000] PM: Registered nosave memory: 00000000bf800000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:16 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u131072
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2062226
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=f7185e7c-bb4e-414b-b15c-62e18742ea57 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 8176920k/9437184k available (5409k kernel code, 1058824k absent, 201440k reserved, 2976k data, 876k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:536
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 83886080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000]   alloc irq_desc for 24 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 25 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 26 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 27 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 28 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2942.281 MHz processor.
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5884.56 BogoMIPS (lpj=29422810)
[    0.000016] Security Framework initialized
[    0.000027] AppArmor: AppArmor initialized
[    0.000475] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.001861] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002475] Mount-cache hash table entries: 256
[    0.002551] Initializing cgroup subsys ns
[    0.002553] Initializing cgroup subsys cpuacct
[    0.002556] Initializing cgroup subsys memory
[    0.002560] Initializing cgroup subsys devices
[    0.002562] Initializing cgroup subsys freezer
[    0.002563] Initializing cgroup subsys net_cls
[    0.002574] CPU: Physical Processor ID: 0
[    0.002575] CPU: Processor Core ID: 0
[    0.002578] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.002579] CPU: L2 cache: 256K
[    0.002580] CPU: L3 cache: 8192K
[    0.002582] CPU 0/0x0 -> Node 0
[    0.002584] mce: CPU supports 9 MCE banks
[    0.002592] CPU0: Thermal monitoring enabled (TM1)
[    0.002595] CPU 0 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6 CMCI:8
[    0.002601] using mwait in idle threads.
[    0.002602] Performance Events: Nehalem/Corei7 events, Intel PMU driver.
[    0.002606] ... version:                3
[    0.002607] ... bit width:              48
[    0.002608] ... generic registers:      4
[    0.002609] ... value mask:             0000ffffffffffff
[    0.002610] ... max period:             000000007fffffff
[    0.002611] ... fixed-purpose events:   3
[    0.002612] ... event mask:             000000070000000f
[    0.004167] ACPI: Core revision 20090903
[    0.038173] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.038177] ftrace: allocating 22518 entries in 89 pages
[    0.043569] Setting APIC routing to physical flat
[    0.043886] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.143885] CPU0: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
[    0.258647] Booting processor 1 APIC 0x2 ip 0x6000
[    0.269087] Initializing CPU#1
[    0.418564] CPU: Physical Processor ID: 0
[    0.418565] CPU: Processor Core ID: 1
[    0.418566] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.418567] CPU: L2 cache: 256K
[    0.418568] CPU: L3 cache: 8192K
[    0.418570] CPU 1/0x2 -> Node 0
[    0.418578] CPU1: Thermal monitoring enabled (TM1)
[    0.418580] CPU 1 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.418605] CPU1: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
[    0.418611] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.438671] Booting processor 2 APIC 0x4 ip 0x6000
[    0.449002] Initializing CPU#2
[    0.598556] CPU: Physical Processor ID: 0
[    0.598557] CPU: Processor Core ID: 2
[    0.598559] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.598560] CPU: L2 cache: 256K
[    0.598560] CPU: L3 cache: 8192K
[    0.598562] CPU 2/0x4 -> Node 0
[    0.598570] CPU2: Thermal monitoring enabled (TM1)
[    0.598573] CPU 2 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.598627] CPU2: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
[    0.598633] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.618693] Booting processor 3 APIC 0x6 ip 0x6000
[    0.629024] Initializing CPU#3
[    0.778548] CPU: Physical Processor ID: 0
[    0.778549] CPU: Processor Core ID: 3
[    0.778551] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.778552] CPU: L2 cache: 256K
[    0.778553] CPU: L3 cache: 8192K
[    0.778554] CPU 3/0x6 -> Node 0
[    0.778563] CPU3: Thermal monitoring enabled (TM1)
[    0.778565] CPU 3 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.778650] CPU3: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
[    0.778655] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.798715] Booting processor 4 APIC 0x1 ip 0x6000
[    0.809047] Initializing CPU#4
[    0.958541] CPU: Physical Processor ID: 0
[    0.958542] CPU: Processor Core ID: 0
[    0.958544] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.958546] CPU: L2 cache: 256K
[    0.958547] CPU: L3 cache: 8192K
[    0.958549] CPU 4/0x1 -> Node 0
[    0.958558] CPU4: Thermal monitoring enabled (TM1)
[    0.958560] CPU 4 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
[    0.958586] CPU4: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
[    0.958593] checking TSC synchronization [CPU#0 -> CPU#4]: passed.
[    0.978655] Booting processor 5 APIC 0x3 ip 0x6000
[    0.988986] Initializing CPU#5
[    1.138533] CPU: Physical Processor ID: 0
[    1.138534] CPU: Processor Core ID: 1
[    1.138536] CPU: L1 I cache: 32K, L1 D cache: 32K
[    1.138537] CPU: L2 cache: 256K
[    1.138537] CPU: L3 cache: 8192K
[    1.138539] CPU 5/0x3 -> Node 0
[    1.138547] CPU5: Thermal monitoring enabled (TM1)
[    1.138549] CPU 5 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
[    1.138654] CPU5: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
[    1.138660] checking TSC synchronization [CPU#0 -> CPU#5]: passed.
[    1.158721] Booting processor 6 APIC 0x5 ip 0x6000
[    1.169052] Initializing CPU#6
[    1.318525] CPU: Physical Processor ID: 0
[    1.318526] CPU: Processor Core ID: 2
[    1.318528] CPU: L1 I cache: 32K, L1 D cache: 32K
[    1.318529] CPU: L2 cache: 256K
[    1.318530] CPU: L3 cache: 8192K
[    1.318531] CPU 6/0x5 -> Node 0
[    1.318539] CPU6: Thermal monitoring enabled (TM1)
[    1.318541] CPU 6 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
[    1.318583] CPU6: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
[    1.318589] checking TSC synchronization [CPU#0 -> CPU#6]: passed.
[    1.338651] Booting processor 7 APIC 0x7 ip 0x6000
[    1.348982] Initializing CPU#7
[    1.498518] CPU: Physical Processor ID: 0
[    1.498518] CPU: Processor Core ID: 3
[    1.498520] CPU: L1 I cache: 32K, L1 D cache: 32K
[    1.498521] CPU: L2 cache: 256K
[    1.498522] CPU: L3 cache: 8192K
[    1.498524] CPU 7/0x7 -> Node 0
[    1.498532] CPU7: Thermal monitoring enabled (TM1)
[    1.498534] CPU 7 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
[    1.498608] CPU7: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
[    1.498613] checking TSC synchronization [CPU#0 -> CPU#7]: passed.
[    1.518627] Brought up 8 CPUs
[    1.518629] Total of 8 processors activated (47078.46 BogoMIPS).
[    1.521683] CPU0 attaching sched-domain:
[    1.521685]  domain 0: span 0,4 level SIBLING
[    1.521687]   groups: 0 (cpu_power = 589) 4 (cpu_power = 589)
[    1.521690]   domain 1: span 0-7 level MC
[    1.521691]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
[    1.521698] CPU1 attaching sched-domain:
[    1.521699]  domain 0: span 1,5 level SIBLING
[    1.521701]   groups: 1 (cpu_power = 589) 5 (cpu_power = 589)
[    1.521704]   domain 1: span 0-7 level MC
[    1.521705]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
[    1.521710] CPU2 attaching sched-domain:
[    1.521711]  domain 0: span 2,6 level SIBLING
[    1.521713]   groups: 2 (cpu_power = 589) 6 (cpu_power = 589)
[    1.521716]   domain 1: span 0-7 level MC
[    1.521717]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
[    1.521722] CPU3 attaching sched-domain:
[    1.521723]  domain 0: span 3,7 level SIBLING
[    1.521725]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
[    1.521728]   domain 1: span 0-7 level MC
[    1.521729]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
[    1.521734] CPU4 attaching sched-domain:
[    1.521735]  domain 0: span 0,4 level SIBLING
[    1.521737]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
[    1.521740]   domain 1: span 0-7 level MC
[    1.521741]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
[    1.521746] CPU5 attaching sched-domain:
[    1.521747]  domain 0: span 1,5 level SIBLING
[    1.521749]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
[    1.521752]   domain 1: span 0-7 level MC
[    1.521753]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
[    1.521758] CPU6 attaching sched-domain:
[    1.521759]  domain 0: span 2,6 level SIBLING
[    1.521761]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
[    1.521764]   domain 1: span 0-7 level MC
[    1.521765]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
[    1.521770] CPU7 attaching sched-domain:
[    1.521771]  domain 0: span 3,7 level SIBLING
[    1.521773]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
[    1.521776]   domain 1: span 0-7 level MC
[    1.521777]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
[    1.522031] devtmpfs: initialized
[    1.522255] regulator: core version 0.5
[    1.522278] Time: 16:53:45  Date: 06/11/10
[    1.522309] NET: Registered protocol family 16
[    1.522366] Trying to unpack rootfs image as initramfs...
[    1.522386] ACPI: bus type pci registered
[    1.522431] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    1.522433] PCI: Not using MMCONFIG.
[    1.522434] PCI: Using configuration type 1 for base access
[    1.522967] bio: create slab <bio-0> at 0
[    1.523707] ACPI: EC: Look up EC in DSDT
[    1.525743] ACPI: Executed 1 blocks of module-level executable AML code
[    1.536345] ACPI: Interpreter enabled
[    1.536348] ACPI: (supports S0 S1 S3 S4 S5)
[    1.536364] ACPI: Using IOAPIC for interrupt routing
[    1.536405] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    1.538187] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    1.542818] PCI: Using MMCONFIG at e0000000 - efffffff
[    1.549941] ACPI: No dock devices found.
[    1.550182] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.550279] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    1.550282] pci 0000:00:05.0: PME# disabled
[    1.550518] pci 0000:00:1a.0: reg 10 32bit mmio: [0xf7ffe000-0xf7ffe3ff]
[    1.550566] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.550569] pci 0000:00:1a.0: PME# disabled
[    1.550603] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf7ff8000-0xf7ffbfff]
[    1.550639] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.550641] pci 0000:00:1b.0: PME# disabled
[    1.550695] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.550698] pci 0000:00:1c.0: PME# disabled
[    1.550754] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.550757] pci 0000:00:1c.4: PME# disabled
[    1.550810] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    1.550813] pci 0000:00:1c.5: PME# disabled
[    1.550865] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    1.550868] pci 0000:00:1c.6: PME# disabled
[    1.550921] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    1.550923] pci 0000:00:1c.7: PME# disabled
[    1.550968] pci 0000:00:1d.0: reg 10 32bit mmio: [0xf7ffd000-0xf7ffd3ff]
[    1.551015] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.551018] pci 0000:00:1d.0: PME# disabled
[    1.551179] pci 0000:00:1f.2: reg 10 io port: [0xc880-0xc887]
[    1.551184] pci 0000:00:1f.2: reg 14 io port: [0xc800-0xc803]
[    1.551188] pci 0000:00:1f.2: reg 18 io port: [0xc480-0xc487]
[    1.551192] pci 0000:00:1f.2: reg 1c io port: [0xc400-0xc403]
[    1.551197] pci 0000:00:1f.2: reg 20 io port: [0xc080-0xc09f]
[    1.551201] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf7ff7000-0xf7ff77ff]
[    1.551228] pci 0000:00:1f.2: PME# supported from D3hot
[    1.551230] pci 0000:00:1f.2: PME# disabled
[    1.551254] pci 0000:00:1f.3: reg 10 64bit mmio: [0xf7ffc000-0xf7ffc0ff]
[    1.551265] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    1.551304] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
[    1.551312] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    1.551319] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
[    1.551323] pci 0000:01:00.0: reg 24 io port: [0xdc00-0xdc7f]
[    1.551327] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfbd80000-0xfbdfffff]
[    1.551368] pci 0000:00:05.0: bridge io port: [0xd000-0xdfff]
[    1.551371] pci 0000:00:05.0: bridge 32bit mmio: [0xf8000000-0xfbdfffff]
[    1.551374] pci 0000:00:05.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    1.551590] pci 0000:07:03.0: reg 10 32bit mmio: [0xfbeff800-0xfbefffff]
[    1.551596] pci 0000:07:03.0: reg 14 io port: [0xec00-0xec7f]
[    1.551635] pci 0000:07:03.0: supports D2
[    1.551636] pci 0000:07:03.0: PME# supported from D2 D3hot D3cold
[    1.551639] pci 0000:07:03.0: PME# disabled
[    1.551674] pci 0000:07:04.0: reg 10 io port: [0xe800-0xe8ff]
[    1.551679] pci 0000:07:04.0: reg 14 32bit mmio: [0xfbeff400-0xfbeff4ff]
[    1.551701] pci 0000:07:04.0: reg 30 32bit mmio pref: [0xfbec0000-0xfbedffff]
[    1.551721] pci 0000:07:04.0: supports D1 D2
[    1.551723] pci 0000:07:04.0: PME# supported from D1 D2 D3hot D3cold
[    1.551726] pci 0000:07:04.0: PME# disabled
[    1.551763] pci 0000:00:1e.0: transparent bridge
[    1.551766] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    1.551769] pci 0000:00:1e.0: bridge 32bit mmio: [0xfbe00000-0xfbefffff]
[    1.551798] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.551935] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR1E._PRT]
[    1.552032] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    1.552080] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    1.552124] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR24._PRT]
[    1.552167] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR25._PRT]
[    1.552211] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR26._PRT]
[    1.552263] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR27._PRT]
[    1.569811] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    1.569908] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    1.570000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 *12 14 15)
[    1.570095] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[    1.570189] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    1.570286] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 *15)
[    1.570380] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 7 10 11 12 *14 15)
[    1.570475] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 6 7 10 11 12 14 15)
[    1.570553] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.570555] vgaarb: loaded
[    1.570619] SCSI subsystem initialized
[    1.570719] libata version 3.00 loaded.
[    1.570764] usbcore: registered new interface driver usbfs
[    1.570771] usbcore: registered new interface driver hub
[    1.570785] usbcore: registered new device driver usb
[    1.570872] ACPI: WMI: Mapper loaded
[    1.570873] PCI: Using ACPI for IRQ routing
[    1.570979] NetLabel: Initializing
[    1.570980] NetLabel:  domain hash size = 128
[    1.570981] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.570990] NetLabel:  unlabeled traffic allowed by default
[    1.571019] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 25, 26, 27, 28, 0
[    1.571023] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.578525] hpet: hpet2 irq 24 for MSI
[    1.578593] hpet: hpet3 irq 25 for MSI
[    1.578619] hpet: hpet4 irq 26 for MSI
[    1.578649] hpet: hpet5 irq 27 for MSI
[    1.588595] hpet: hpet6 irq 28 for MSI
[    1.598627] Switching to clocksource tsc
[    1.599811] AppArmor: AppArmor Filesystem Enabled
[    1.599822] pnp: PnP ACPI init
[    1.599832] ACPI: bus type pnp registered
[    1.601712] pnp: PnP ACPI: found 14 devices
[    1.601714] ACPI: ACPI bus type pnp unregistered
[    1.601721] system 00:01: iomem range 0xfc000000-0xfcffffff has been reserved
[    1.601723] system 00:01: iomem range 0xfd000000-0xfdffffff has been reserved
[    1.601725] system 00:01: iomem range 0xfe000000-0xfebfffff has been reserved
[    1.601727] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    1.601732] system 00:06: ioport range 0x290-0x29f has been reserved
[    1.601735] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    1.601737] system 00:07: ioport range 0x800-0x87f has been reserved
[    1.601739] system 00:07: ioport range 0x500-0x57f has been reserved
[    1.601740] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.601742] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[    1.601744] system 00:07: iomem range 0xfed40000-0xfed8ffff has been reserved
[    1.601748] system 00:0a: iomem range 0xffc00000-0xffdfffff has been reserved
[    1.601751] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    1.601753] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    1.601756] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    1.601759] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    1.601761] system 00:0d: iomem range 0xc0000-0xcffff has been reserved
[    1.601763] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    1.601765] system 00:0d: iomem range 0x100000-0xbfefffff could not be reserved
[    1.601766] system 00:0d: iomem range 0xfed90000-0xffffffff could not be reserved
[    1.606387] pci 0000:07:04.0: BAR 6: address space collision on of device [0xfbec0000-0xfbedffff]
[    1.606431] pci 0000:00:05.0: PCI bridge, secondary bus 0000:01
[    1.606433] pci 0000:00:05.0:   IO window: 0xd000-0xdfff
[    1.606436] pci 0000:00:05.0:   MEM window: 0xf8000000-0xfbdfffff
[    1.606438] pci 0000:00:05.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    1.606442] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:06
[    1.606444] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    1.606448] pci 0000:00:1c.0:   MEM window: 0xc0000000-0xc01fffff
[    1.606451] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0200000-0x000000c03fffff
[    1.606455] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:05
[    1.606458] pci 0000:00:1c.4:   IO window: 0x2000-0x2fff
[    1.606461] pci 0000:00:1c.4:   MEM window: 0xc0400000-0xc05fffff
[    1.606464] pci 0000:00:1c.4:   PREFETCH window: 0x000000c0600000-0x000000c07fffff
[    1.606469] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:04
[    1.606471] pci 0000:00:1c.5:   IO window: 0x3000-0x3fff
[    1.606474] pci 0000:00:1c.5:   MEM window: 0xc0800000-0xc09fffff
[    1.606477] pci 0000:00:1c.5:   PREFETCH window: 0x000000c0a00000-0x000000c0bfffff
[    1.606482] pci 0000:00:1c.6: PCI bridge, secondary bus 0000:03
[    1.606483] pci 0000:00:1c.6:   IO window: disabled
[    1.606487] pci 0000:00:1c.6:   MEM window: disabled
[    1.606489] pci 0000:00:1c.6:   PREFETCH window: disabled
[    1.606494] pci 0000:00:1c.7: PCI bridge, secondary bus 0000:02
[    1.606495] pci 0000:00:1c.7:   IO window: disabled
[    1.606498] pci 0000:00:1c.7:   MEM window: disabled
[    1.606501] pci 0000:00:1c.7:   PREFETCH window: disabled
[    1.606506] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    1.606508] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    1.606511] pci 0000:00:1e.0:   MEM window: 0xfbe00000-0xfbefffff
[    1.606514] pci 0000:00:1e.0:   PREFETCH window: 0xc0c00000-0xc0cfffff
[    1.606525]   alloc irq_desc for 16 on node -1
[    1.606526]   alloc kstat_irqs on node -1
[    1.606530] pci 0000:00:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.606533] pci 0000:00:05.0: setting latency timer to 64
[    1.606538] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    1.606541]   alloc irq_desc for 17 on node -1
[    1.606542]   alloc kstat_irqs on node -1
[    1.606544] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.606547] pci 0000:00:1c.0: setting latency timer to 64
[    1.606553] pci 0000:00:1c.4: enabling device (0104 -> 0107)
[    1.606555] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.606558] pci 0000:00:1c.4: setting latency timer to 64
[    1.606563] pci 0000:00:1c.5: enabling device (0104 -> 0107)
[    1.606566] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.606569] pci 0000:00:1c.5: setting latency timer to 64
[    1.606574]   alloc irq_desc for 18 on node -1
[    1.606575]   alloc kstat_irqs on node -1
[    1.606578] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.606581] pci 0000:00:1c.6: setting latency timer to 64
[    1.606586]   alloc irq_desc for 19 on node -1
[    1.606587]   alloc kstat_irqs on node -1
[    1.606590] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.606593] pci 0000:00:1c.7: setting latency timer to 64
[    1.606597] pci 0000:00:1e.0: setting latency timer to 64
[    1.606600] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    1.606602] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    1.606603] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    1.606605] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xfbdfffff]
[    1.606606] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    1.606608] pci_bus 0000:06: resource 0 io:  [0x1000-0x1fff]
[    1.606609] pci_bus 0000:06: resource 1 mem: [0xc0000000-0xc01fffff]
[    1.606611] pci_bus 0000:06: resource 2 pref mem [0xc0200000-0xc03fffff]
[    1.606613] pci_bus 0000:05: resource 0 io:  [0x2000-0x2fff]
[    1.606614] pci_bus 0000:05: resource 1 mem: [0xc0400000-0xc05fffff]
[    1.606616] pci_bus 0000:05: resource 2 pref mem [0xc0600000-0xc07fffff]
[    1.606617] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
[    1.606619] pci_bus 0000:04: resource 1 mem: [0xc0800000-0xc09fffff]
[    1.606620] pci_bus 0000:04: resource 2 pref mem [0xc0a00000-0xc0bfffff]
[    1.606622] pci_bus 0000:07: resource 0 io:  [0xe000-0xefff]
[    1.606623] pci_bus 0000:07: resource 1 mem: [0xfbe00000-0xfbefffff]
[    1.606625] pci_bus 0000:07: resource 2 pref mem [0xc0c00000-0xc0cfffff]
[    1.606626] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
[    1.606628] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffffffffffff]
[    1.606649] NET: Registered protocol family 2
[    1.606817] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    1.607570] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.609655] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.609910] TCP: Hash tables configured (established 524288 bind 65536)
[    1.609912] TCP reno registered
[    1.609988] NET: Registered protocol family 1
[    1.610051] pci 0000:01:00.0: Boot video device
[    1.610413] Scanning for low memory corruption every 60 seconds
[    1.610486] audit: initializing netlink socket (disabled)
[    1.610494] type=2000 audit(1276275224.419:1): initialized
[    1.617445] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.618385] VFS: Disk quotas dquot_6.5.2
[    1.618419] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.618815] fuse init (API version 7.13)
[    1.618867] msgmni has been set to 15970
[    1.619040] alg: No test for stdrng (krng)
[    1.619076] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.619078] io scheduler noop registered
[    1.619079] io scheduler anticipatory registered
[    1.619080] io scheduler deadline registered
[    1.619103] io scheduler cfq registered (default)
[    1.619188]   alloc irq_desc for 29 on node -1
[    1.619189]   alloc kstat_irqs on node -1
[    1.619195] pcieport 0000:00:05.0: irq 29 for MSI/MSI-X
[    1.619201] pcieport 0000:00:05.0: setting latency timer to 64
[    1.619279]   alloc irq_desc for 30 on node -1
[    1.619280]   alloc kstat_irqs on node -1
[    1.619285] pcieport 0000:00:1c.0: irq 30 for MSI/MSI-X
[    1.619291] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.619371]   alloc irq_desc for 31 on node -1
[    1.619372]   alloc kstat_irqs on node -1
[    1.619377] pcieport 0000:00:1c.4: irq 31 for MSI/MSI-X
[    1.619383] pcieport 0000:00:1c.4: setting latency timer to 64
[    1.619463]   alloc irq_desc for 32 on node -1
[    1.619464]   alloc kstat_irqs on node -1
[    1.619469] pcieport 0000:00:1c.5: irq 32 for MSI/MSI-X
[    1.619475] pcieport 0000:00:1c.5: setting latency timer to 64
[    1.619556]   alloc irq_desc for 33 on node -1
[    1.619557]   alloc kstat_irqs on node -1
[    1.619562] pcieport 0000:00:1c.6: irq 33 for MSI/MSI-X
[    1.619568] pcieport 0000:00:1c.6: setting latency timer to 64
[    1.619642]   alloc irq_desc for 34 on node -1
[    1.619643]   alloc kstat_irqs on node -1
[    1.619648] pcieport 0000:00:1c.7: irq 34 for MSI/MSI-X
[    1.619654] pcieport 0000:00:1c.7: setting latency timer to 64
[    1.619705] Firmware did not grant requested _OSC control
[    1.619707] aer 0000:00:05.0:pcie02: AER service couldn't init device: no _OSC support
[    1.619713] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.619722] Firmware did not grant requested _OSC control
[    1.619733] Firmware did not grant requested _OSC control
[    1.619742] Firmware did not grant requested _OSC control
[    1.619760] Firmware did not grant requested _OSC control
[    1.619769] Firmware did not grant requested _OSC control
[    1.619777] Firmware did not grant requested _OSC control
[    1.619787] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.619849] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.619851] ACPI: Power Button [PWRB]
[    1.619876] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.619878] ACPI: Power Button [PWRF]
[    1.621024] ACPI: SSDT 00000000bf6880c0 0265C (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    1.621432] ACPI: SSDT 00000000bf68a720 00659 (v01  PmRef  P001Cst 00003001 INTL 20060113)
[    1.621817] Monitor-Mwait will be used to enter C-1 state
[    1.621832] Monitor-Mwait will be used to enter C-2 state
[    1.621845] Monitor-Mwait will be used to enter C-3 state
[    1.621871] processor LNXCPU:00: registered as cooling_device0
[    1.622114] processor LNXCPU:01: registered as cooling_device1
[    1.622353] processor LNXCPU:02: registered as cooling_device2
[    1.622594] processor LNXCPU:03: registered as cooling_device3
[    1.622837] processor LNXCPU:04: registered as cooling_device4
[    1.630387] processor LNXCPU:05: registered as cooling_device5
[    1.630626] processor LNXCPU:06: registered as cooling_device6
[    1.630861] processor LNXCPU:07: registered as cooling_device7
[    1.633710] Linux agpgart interface v0.103
[    1.633727] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.634502] brd: module loaded
[    1.634781] loop: module loaded
[    1.634826] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.635046] Fixed MDIO Bus: probed
[    1.635066] PPP generic driver version 2.4.2
[    1.635083] tun: Universal TUN/TAP device driver, 1.6
[    1.635085] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.635126] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.635140] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.635152] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.635154] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.635172] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.635194] ehci_hcd 0000:00:1a.0: debug port 2
[    1.639064] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[    1.639076] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7ffe000
[    1.651546] Freeing initrd memory: 8134k freed
[    1.660935] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.661033] usb usb1: configuration #1 chosen from 1 choice
[    1.661052] hub 1-0:1.0: USB hub found
[    1.661057] hub 1-0:1.0: 2 ports detected
[    1.661093]   alloc irq_desc for 23 on node -1
[    1.661094]   alloc kstat_irqs on node -1
[    1.661099] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.661113] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.661116] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.661139] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.661159] ehci_hcd 0000:00:1d.0: debug port 2
[    1.665032] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[    1.665043] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7ffd000
[    1.690919] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.691002] usb usb2: configuration #1 chosen from 1 choice
[    1.691017] hub 2-0:1.0: USB hub found
[    1.691020] hub 2-0:1.0: 2 ports detected
[    1.691051] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.691059] uhci_hcd: USB Universal Host Controller Interface driver
[    1.691108] PNP: No PS/2 controller found. Probing ports directly.
[    1.692573] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.692577] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.692624] mice: PS/2 mouse device common for all mice
[    1.692680] rtc_cmos 00:03: RTC can wake from S4
[    1.692704] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.692727] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.692805] device-mapper: uevent: version 1.0.3
[    1.692868] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.692955] device-mapper: multipath: version 1.1.0 loaded
[    1.692957] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.693279] cpuidle: using governor ladder
[    1.693509] cpuidle: using governor menu
[    1.693748] TCP cubic registered
[    1.693824] NET: Registered protocol family 10
[    1.694149] lo: Disabled Privacy Extensions
[    1.694331] NET: Registered protocol family 17
[    1.694361] ------------[ cut here ]------------
[    1.694367] WARNING: at /build/buildd/linux-2.6.32/arch/x86/kernel/hpet.c:392 hpet_next_event+0x7a/0x90()
[    1.694368] Hardware name: System Product Name
[    1.694370] Modules linked in:
[    1.694372] Pid: 0, comm: swapper Not tainted 2.6.32-22-generic #36-Ubuntu
[    1.694373] Call Trace:
[    1.694378]  [<ffffffff81066d0b>] warn_slowpath_common+0x7b/0xc0
[    1.694380]  [<ffffffff81066d64>] warn_slowpath_null+0x14/0x20
[    1.694382]  [<ffffffff810375ca>] hpet_next_event+0x7a/0x90
[    1.694384]  [<ffffffff81037610>] hpet_legacy_next_event+0x10/0x20
[    1.694388]  [<ffffffff81092e24>] clockevents_program_event+0x54/0xa0
[    1.694390]  [<ffffffff81094378>] tick_dev_program_event+0x68/0xd0
[    1.694393]  [<ffffffff81093cae>] tick_broadcast_oneshot_control+0x11e/0x120
[    1.694395]  [<ffffffff810934c0>] tick_notify+0x130/0x200
[    1.694399]  [<ffffffff81543b46>] notifier_call_chain+0x56/0x80
[    1.694401]  [<ffffffff8108a366>] raw_notifier_call_chain+0x16/0x20
[    1.694404]  [<ffffffff81092c47>] clockevents_notify+0x37/0x160
[    1.694407]  [<ffffffff8130ccd5>] lapic_timer_state_broadcast+0x46/0x48
[    1.694409]  [<ffffffff8130d244>] acpi_idle_enter_bm+0x187/0x2be
[    1.694411]  [<ffffffff81543b06>] ? notifier_call_chain+0x16/0x80
[    1.694414]  [<ffffffff81437537>] cpuidle_idle_call+0xa7/0x140
[    1.694418]  [<ffffffff81011e73>] cpu_idle+0xb3/0x110
[    1.694420]  [<ffffffff8153ad7b>] start_secondary+0xa8/0xaa
[    1.694423] ---[ end trace 3bd3e2b4cadc7f72 ]---
[    1.697055] PM: Resume from disk failed.
[    1.697061] registered taskstats version 1
[    1.697341]   Magic number: 14:860:893
[    1.697474] rtc_cmos 00:03: setting system clock to 2010-06-11 16:53:45 UTC (1276275225)
[    1.697479] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.697482] EDD information not available.
[    1.697518] Freeing unused kernel memory: 876k freed
[    1.697623] Write protecting the kernel read-only data: 7680k
[    1.711822] udev: starting version 151
[    1.727470] ahci 0000:00:1f.2: version 3.0
[    1.727484]   alloc irq_desc for 21 on node -1
[    1.727486]   alloc kstat_irqs on node -1
[    1.727492] ahci 0000:00:1f.2: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    1.727528]   alloc irq_desc for 35 on node -1
[    1.727530]   alloc kstat_irqs on node -1
[    1.727537] ahci 0000:00:1f.2: irq 35 for MSI/MSI-X
[    1.727568] ahci: SSS flag set, parallel bus scan disabled
[    1.739281] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.739295]   alloc irq_desc for 22 on node -1
[    1.739296]   alloc kstat_irqs on node -1
[    1.739300] r8169 0000:07:04.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.739419] r8169 0000:07:04.0: no PCI Express capability
[    1.739748] eth0: RTL8169sc/8110sc at 0xffffc90000c76400, 90:e6:ba:00:b7:62, XID 18000000 IRQ 22
[    1.740810] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.740812] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems sxs apst 
[    1.740816] ahci 0000:00:1f.2: setting latency timer to 64
[    1.743868] ohci1394 0000:07:03.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.802487] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[fbeff800-fbefffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.841012] scsi0 : ahci
[    1.841264] scsi1 : ahci
[    1.841523] scsi2 : ahci
[    1.841815] scsi3 : ahci
[    1.842119] scsi4 : ahci
[    1.842363] scsi5 : ahci
[    1.842559] ata1: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7100 irq 35
[    1.842561] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 35
[    1.842563] ata3: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7200 irq 35
[    1.842565] ata4: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7280 irq 35
[    1.842567] ata5: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7300 irq 35
[    1.842569] ata6: SATA max UDMA/133 irq_stat 0x00400040, connection status changed
[    1.978885] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.129760] usb 1-1: configuration #1 chosen from 1 choice
[    2.130005] hub 1-1:1.0: USB hub found
[    2.130195] hub 1-1:1.0: 6 ports detected
[    2.248781] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    2.370641] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.371141] ata1.00: ATA-7: INTEL SSDSA2M080G2GC, 2CV102HD, max UDMA/133
[    2.371146] ata1.00: 156301488 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    2.371727] ata1.00: configured for UDMA/133
[    2.390747] scsi 0:0:0:0: Direct-Access     ATA      INTEL SSDSA2M080 2CV1 PQ: 0 ANSI: 5
[    2.390852] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.390908] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    2.390935] sd 0:0:0:0: [sda] Write Protect is off
[    2.390936] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.390948] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.391019]  sda: sda1
[    2.391675] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.409270] usb 2-1: configuration #1 chosen from 1 choice
[    2.409477] hub 2-1:1.0: USB hub found
[    2.409545] hub 2-1:1.0: 8 ports detected
[    2.688990] usb 2-1.3: new high speed USB device using ehci_hcd and address 3
[    2.799178] usb 2-1.3: configuration #1 chosen from 1 choice
[    2.799404] hub 2-1.3:1.0: USB hub found
[    2.799567] hub 2-1.3:1.0: 2 ports detected
[    2.878812] usb 2-1.4: new low speed USB device using ehci_hcd and address 4
[    3.027284] usb 2-1.4: configuration #1 chosen from 1 choice
[    3.108834] usb 2-1.7: new high speed USB device using ehci_hcd and address 5
[    3.118814] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0000a2df9b]
[    3.230585] usb 2-1.7: configuration #1 chosen from 1 choice
[    3.230898] hub 2-1.7:1.0: USB hub found
[    3.231195] hub 2-1.7:1.0: 4 ports detected
[    3.308835] usb 2-1.8: new low speed USB device using ehci_hcd and address 6
[    3.320285] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.341258] ata2.00: ATA-8: SAMSUNG HD501LJ, CR100-13, max UDMA7
[    3.341263] ata2.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    3.343764] ata2.00: configured for UDMA/133
[    3.360362] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[    3.360427] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    3.360463] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.360484] sd 1:0:0:0: [sdb] Write Protect is off
[    3.360486] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.360497] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.360563]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 >
[    3.411405] sd 1:0:0:0: [sdb] Attached SCSI disk
[    3.446916] usb 2-1.8: configuration #1 chosen from 1 choice
[    3.451290] usbcore: registered new interface driver hiddev
[    3.528838] usb 2-1.3.1: new high speed USB device using ehci_hcd and address 7
[    3.639028] usb 2-1.3.1: configuration #1 chosen from 1 choice
[    3.639240] hub 2-1.3.1:1.0: USB hub found
[    3.639297] hub 2-1.3.1:1.0: 4 ports detected
[    3.720526] ata3: SATA link down (SStatus 0 SControl 300)
[    3.721821] usb 2-1.3.2: new high speed USB device using ehci_hcd and address 8
[    3.759758] generic-usb 0003:051D:0002.0001: hiddev96,hidraw0: USB HID v1.10 Device [American Power Conversion Back-UPS BR  800 FW:9.o4 .I USB FW:o4 ] on usb-0000:00:1d.0-1.4/input0
[    3.769423] input: daskeyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.0/input/input3
[    3.769463] generic-usb 0003:04D9:2013.0002: input,hidraw1: USB HID v1.10 Keyboard [daskeyboard] on usb-0000:00:1d.0-1.8/input0
[    3.792398] input: daskeyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.1/input/input4
[    3.792440] generic-usb 0003:04D9:2013.0003: input,hidraw2: USB HID v1.10 Device [daskeyboard] on usb-0000:00:1d.0-1.8/input1
[    3.792450] usbcore: registered new interface driver usbhid
[    3.792451] usbhid: v2.6:USB HID core driver
[    3.918411] usb 2-1.3.2: configuration #1 chosen from 1 choice
[    3.923006] Initializing USB Mass Storage driver...
[    3.923479] scsi6 : SCSI emulation for USB Mass Storage devices
[    3.923845] usbcore: registered new interface driver usb-storage
[    3.923850] usb-storage: device found at 8
[    3.923855] usb-storage: waiting for device to settle before scanning
[    3.923920] USB Mass Storage support registered.
[    3.998829] usb 2-1.3.1.1: new low speed USB device using ehci_hcd and address 9
[    4.078617] ata4: SATA link down (SStatus 0 SControl 300)
[    4.123533] usb 2-1.3.1.1: configuration #1 chosen from 1 choice
[    4.125986] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.1/2-1.3.1.1/2-1.3.1.1:1.0/input/input5
[    4.126034] generic-usb 0003:045E:0040.0004: input,hidraw3: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-1.3.1.1/input0
[    4.450535] ata5: SATA link down (SStatus 0 SControl 300)
[    5.398590] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.401654] ata6.00: ATAPI: PIONEER BD-ROM  BDC-202, 1.01, max UDMA/66
[    5.404915] ata6.00: configured for UDMA/66
[    5.435666] scsi 5:0:0:0: CD-ROM            PIONEER  BD-ROM  BDC-202  1.01 PQ: 0 ANSI: 5
[    5.455281] sr0: scsi3-mmc drive: 32x/32x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.455286] Uniform CD-ROM driver Revision: 3.20
[    5.455407] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    5.455457] sr 5:0:0:0: Attached scsi generic sg2 type 5
[    5.574024] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    5.722185] udev: starting version 151
[    5.740614] Adding 15998968k swap on /dev/sdb1.  Priority:-1 extents:1 across:15998968k 
[    5.752848] vga16fb: initializing
[    5.752851] vga16fb: mapped to 0xffff8800000a0000
[    5.752893] fb0: VGA16 VGA frame buffer device
[    5.782924] lp: driver loaded but no devices found
[    5.829483] nvidia: module license 'NVIDIA' taints kernel.
[    5.829485] Disabling lock debugging due to kernel taint
[    5.871070] type=1505 audit(1276275229.671:2):  operation="profile_load" pid=751 name="/sbin/dhclient3"
[    5.871428] type=1505 audit(1276275229.671:3):  operation="profile_load" pid=751 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    5.871601] type=1505 audit(1276275229.671:4):  operation="profile_load" pid=751 name="/usr/lib/connman/scripts/dhclient-script"
[    5.873186] type=1505 audit(1276275229.671:5):  operation="profile_load" pid=807 name="/usr/sbin/ntpd"
[    6.103067] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    6.103103] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    6.249651] Console: switching to colour frame buffer device 80x30
[    6.295130] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.295136] nvidia 0000:01:00.0: setting latency timer to 64
[    6.295139] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    6.295403] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.15  Fri Mar 12 00:29:13 PST 2010
[    8.926067] usb-storage: device scan complete
[    8.929570] scsi 6:0:0:0: Direct-Access     SMSC     223 U HS-CF      3.60 PQ: 0 ANSI: 0
[    8.932886] scsi 6:0:0:1: Direct-Access     SMSC     223 U HS-MS      3.60 PQ: 0 ANSI: 0
[    8.936249] scsi 6:0:0:2: Direct-Access     SMSC     223 U HS-SM      3.60 PQ: 0 ANSI: 0
[    8.939257] scsi 6:0:0:3: Direct-Access     SMSC     223 U HS-SD/MMC  3.60 PQ: 0 ANSI: 0
[    8.939561] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    8.939626] sd 6:0:0:1: Attached scsi generic sg4 type 0
[    8.939687] sd 6:0:0:2: Attached scsi generic sg5 type 0
[    8.939750] sd 6:0:0:3: Attached scsi generic sg6 type 0
[    9.055046] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[    9.076933] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[    9.105557] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    9.131079] sd 6:0:0:2: [sde] Attached SCSI removable disk
[   10.248435] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input6
[   14.314791] EXT4-fs (sdb6): mounted filesystem with ordered data mode
[   14.411118] EXT4-fs (sdb7): mounted filesystem with ordered data mode
[   14.415973] EXT4-fs (sdb5): mounted filesystem with ordered data mode
[   14.462107] type=1505 audit(1276275238.261:6):  operation="profile_load" pid=1156 name="/usr/share/gdm/guest-session/Xsession"
[   14.463177] type=1505 audit(1276275238.261:7):  operation="profile_replace" pid=1157 name="/sbin/dhclient3"
[   14.463468] type=1505 audit(1276275238.261:8):  operation="profile_replace" pid=1157 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.463626] type=1505 audit(1276275238.261:9):  operation="profile_replace" pid=1157 name="/usr/lib/connman/scripts/dhclient-script"
[   14.468084] type=1505 audit(1276275238.271:10):  operation="profile_load" pid=1158 name="/usr/bin/evince"
[   14.472106] type=1505 audit(1276275238.271:11):  operation="profile_load" pid=1158 name="/usr/bin/evince-previewer"
[   14.474567] type=1505 audit(1276275238.271:12):  operation="profile_load" pid=1158 name="/usr/bin/evince-thumbnailer"
[   14.479428] type=1505 audit(1276275238.281:13):  operation="profile_load" pid=1160 name="/usr/lib/cups/backend/cups-pdf"
[   14.479854] type=1505 audit(1276275238.281:14):  operation="profile_load" pid=1160 name="/usr/sbin/cupsd"
[   14.481178] type=1505 audit(1276275238.281:15):  operation="profile_replace" pid=1162 name="/usr/sbin/ntpd"
[   14.622561] r8169: eth0: link up
[   16.772015] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   16.772017] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   16.772018] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   16.772018] vboxdrv: the usage of hardware performance counters by
[   16.772019] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   16.772021] vboxdrv: Found 8 processor cores.
[   16.772059] VBoxDrv: dbg - g_abExecMemory=ffffffffa0d0fa20
[   16.772278] vboxdrv: fAsync=0 offMin=0x2a1 offMax=0x47747
[   16.772302] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   16.772303] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
[   16.925167] ppdev: user-space parallel port driver
[   17.164002] CPU0 attaching NULL sched-domain.
[   17.164005] CPU1 attaching NULL sched-domain.
[   17.164007] CPU2 attaching NULL sched-domain.
[   17.164008] CPU3 attaching NULL sched-domain.
[   17.164010] CPU4 attaching NULL sched-domain.
[   17.164011] CPU5 attaching NULL sched-domain.
[   17.164012] CPU6 attaching NULL sched-domain.
[   17.164013] CPU7 attaching NULL sched-domain.
[   17.279644] CPU0 attaching sched-domain:
[   17.279646]  domain 0: span 0,4 level SIBLING
[   17.279647]   groups: 0 (cpu_power = 589) 4 (cpu_power = 589)
[   17.279650]   domain 1: span 0-7 level MC
[   17.279651]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
[   17.279657] CPU1 attaching sched-domain:
[   17.279658]  domain 0: span 1,5 level SIBLING
[   17.279659]   groups: 1 (cpu_power = 589) 5 (cpu_power = 589)
[   17.279661]   domain 1: span 0-7 level MC
[   17.279662]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
[   17.279667] CPU2 attaching sched-domain:
[   17.279668]  domain 0: span 2,6 level SIBLING
[   17.279669]   groups: 2 (cpu_power = 589) 6 (cpu_power = 589)
[   17.279671]   domain 1: span 0-7 level MC
[   17.279672]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
[   17.279676] CPU3 attaching sched-domain:
[   17.279677]  domain 0: span 3,7 level SIBLING
[   17.279678]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
[   17.279681]   domain 1: span 0-7 level MC
[   17.279682]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
[   17.279686] CPU4 attaching sched-domain:
[   17.279687]  domain 0: span 0,4 level SIBLING
[   17.279688]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
[   17.279691]   domain 1: span 0-7 level MC
[   17.279692]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
[   17.279696] CPU5 attaching sched-domain:
[   17.279697]  domain 0: span 1,5 level SIBLING
[   17.279698]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
[   17.279700]   domain 1: span 0-7 level MC
[   17.279701]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
[   17.279706] CPU6 attaching sched-domain:
[   17.279707]  domain 0: span 2,6 level SIBLING
[   17.279708]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
[   17.279710]   domain 1: span 0-7 level MC
[   17.279711]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
[   17.279718] CPU7 attaching sched-domain:
[   17.279719]  domain 0: span 3,7 level SIBLING
[   17.279721]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
[   17.279723]   domain 1: span 0-7 level MC
[   17.279724]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
[   17.280278] CPU0 attaching NULL sched-domain.
[   17.280280] CPU1 attaching NULL sched-domain.
[   17.280281] CPU2 attaching NULL sched-domain.
[   17.280282] CPU3 attaching NULL sched-domain.
[   17.280283] CPU4 attaching NULL sched-domain.
[   17.280284] CPU5 attaching NULL sched-domain.
[   17.280285] CPU6 attaching NULL sched-domain.
[   17.280286] CPU7 attaching NULL sched-domain.
[   17.429630] CPU0 attaching sched-domain:
[   17.429632]  domain 0: span 0,4 level SIBLING
[   17.429633]   groups: 0 (cpu_power = 589) 4 (cpu_power = 589)
[   17.429636]   domain 1: span 0-7 level MC
[   17.429637]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
[   17.429642] CPU1 attaching sched-domain:
[   17.429643]  domain 0: span 1,5 level SIBLING
[   17.429644]   groups: 1 (cpu_power = 589) 5 (cpu_power = 589)
[   17.429647]   domain 1: span 0-7 level MC
[   17.429648]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
[   17.429652] CPU2 attaching sched-domain:
[   17.429653]  domain 0: span 2,6 level SIBLING
[   17.429654]   groups: 2 (cpu_power = 589) 6 (cpu_power = 589)
[   17.429657]   domain 1: span 0-7 level MC
[   17.429658]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
[   17.429662] CPU3 attaching sched-domain:
[   17.429663]  domain 0: span 3,7 level SIBLING
[   17.429664]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
[   17.429667]   domain 1: span 0-7 level MC
[   17.429668]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
[   17.429672] CPU4 attaching sched-domain:
[   17.429673]  domain 0: span 0,4 level SIBLING
[   17.429674]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
[   17.429677]   domain 1: span 0-7 level MC
[   17.429678]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
[   17.429682] CPU5 attaching sched-domain:
[   17.429683]  domain 0: span 1,5 level SIBLING
[   17.429685]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
[   17.429687]   domain 1: span 0-7 level MC
[   17.429688]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
[   17.429692] CPU6 attaching sched-domain:
[   17.429693]  domain 0: span 2,6 level SIBLING
[   17.429695]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
[   17.429697]   domain 1: span 0-7 level MC
[   17.429698]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
[   17.429703] CPU7 attaching sched-domain:
[   17.429703]  domain 0: span 3,7 level SIBLING
[   17.429705]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
[   17.429707]   domain 1: span 0-7 level MC
[   17.429708]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
[   18.678423] CPU0 attaching NULL sched-domain.
[   18.678426] CPU1 attaching NULL sched-domain.
[   18.678428] CPU2 attaching NULL sched-domain.
[   18.678429] CPU3 attaching NULL sched-domain.
[   18.678430] CPU4 attaching NULL sched-domain.
[   18.678431] CPU5 attaching NULL sched-domain.
[   18.678432] CPU6 attaching NULL sched-domain.
[   18.678433] CPU7 attaching NULL sched-domain.
[   18.770191] CPU0 attaching sched-domain:
[   18.770193]  domain 0: span 0,4 level SIBLING
[   18.770195]   groups: 0 (cpu_power = 589) 4 (cpu_power = 589)
[   18.770198]   domain 1: span 0-7 level MC
[   18.770199]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
[   18.770205] CPU1 attaching sched-domain:
[   18.770206]  domain 0: span 1,5 level SIBLING
[   18.770208]   groups: 1 (cpu_power = 589) 5 (cpu_power = 589)
[   18.770210]   domain 1: span 0-7 level MC
[   18.770212]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
[   18.770216] CPU2 attaching sched-domain:
[   18.770217]  domain 0: span 2,6 level SIBLING
[   18.770219]   groups: 2 (cpu_power = 589) 6 (cpu_power = 589)
[   18.770221]   domain 1: span 0-7 level MC
[   18.770222]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
[   18.770227] CPU3 attaching sched-domain:
[   18.770228]  domain 0: span 3,7 level SIBLING
[   18.770229]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
[   18.770232]   domain 1: span 0-7 level MC
[   18.770233]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
[   18.770238] CPU4 attaching sched-domain:
[   18.770239]  domain 0: span 0,4 level SIBLING
[   18.770240]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
[   18.770243]   domain 1: span 0-7 level MC
[   18.770244]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
[   18.770249] CPU5 attaching sched-domain:
[   18.770250]  domain 0: span 1,5 level SIBLING
[   18.770251]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
[   18.770254]   domain 1: span 0-7 level MC
[   18.770255]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
[   18.770260] CPU6 attaching sched-domain:
[   18.770261]  domain 0: span 2,6 level SIBLING
[   18.770262]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
[   18.770265]   domain 1: span 0-7 level MC
[   18.770266]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
[   18.770271] CPU7 attaching sched-domain:
[   18.770272]  domain 0: span 3,7 level SIBLING
[   18.770273]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
[   18.770276]   domain 1: span 0-7 level MC
[   18.770277]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
[   18.770741] CPU0 attaching NULL sched-domain.
[   18.770742] CPU1 attaching NULL sched-domain.
[   18.770743] CPU2 attaching NULL sched-domain.
[   18.770744] CPU3 attaching NULL sched-domain.
[   18.770745] CPU4 attaching NULL sched-domain.
[   18.770746] CPU5 attaching NULL sched-domain.
[   18.770747] CPU6 attaching NULL sched-domain.
[   18.770749] CPU7 attaching NULL sched-domain.
[   18.950361] CPU0 attaching sched-domain:
[   18.950363]  domain 0: span 0,4 level SIBLING
[   18.950365]   groups: 0 (cpu_power = 589) 4 (cpu_power = 589)
[   18.950368]   domain 1: span 0-7 level MC
[   18.950369]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
[   18.950374] CPU1 attaching sched-domain:
[   18.950375]  domain 0: span 1,5 level SIBLING
[   18.950376]   groups: 1 (cpu_power = 589) 5 (cpu_power = 589)
[   18.950379]   domain 1: span 0-7 level MC
[   18.950380]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
[   18.950385] CPU2 attaching sched-domain:
[   18.950386]  domain 0: span 2,6 level SIBLING
[   18.950387]   groups: 2 (cpu_power = 589) 6 (cpu_power = 589)
[   18.950389]   domain 1: span 0-7 level MC
[   18.950390]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
[   18.950395] CPU3 attaching sched-domain:
[   18.950396]  domain 0: span 3,7 level SIBLING
[   18.950397]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
[   18.950399]   domain 1: span 0-7 level MC
[   18.950400]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
[   18.950405] CPU4 attaching sched-domain:
[   18.950406]  domain 0: span 0,4 level SIBLING
[   18.950407]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
[   18.950409]   domain 1: span 0-7 level MC
[   18.950410]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
[   18.950415] CPU5 attaching sched-domain:
[   18.950416]  domain 0: span 1,5 level SIBLING
[   18.950417]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
[   18.950420]   domain 1: span 0-7 level MC
[   18.950421]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
[   18.950425] CPU6 attaching sched-domain:
[   18.950426]  domain 0: span 2,6 level SIBLING
[   18.950427]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
[   18.950430]   domain 1: span 0-7 level MC
[   18.950431]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
[   18.950435] CPU7 attaching sched-domain:
[   18.950436]  domain 0: span 3,7 level SIBLING
[   18.950437]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
[   18.950440]   domain 1: span 0-7 level MC
[   18.950441]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
[   25.501935] eth0: no IPv6 routers present
```

corresponding syslog:
```
Jun 11 17:53:58 simon-watery kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jun 11 17:53:58 simon-watery rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1137" x-info="http://www.rsyslog.com"] (re)start
Jun 11 17:53:58 simon-watery rsyslogd: rsyslogd's groupid changed to 103
Jun 11 17:53:58 simon-watery rsyslogd: rsyslogd's userid changed to 101
Jun 11 17:53:58 simon-watery rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun 11 17:53:58 simon-watery avahi-daemon[1190]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Jun 11 17:53:58 simon-watery avahi-daemon[1190]: Successfully dropped root privileges.
Jun 11 17:53:58 simon-watery avahi-daemon[1190]: avahi-daemon 0.6.25 starting up.
Jun 11 17:53:58 simon-watery avahi-daemon[1190]: Successfully called chroot().
Jun 11 17:53:58 simon-watery avahi-daemon[1190]: Successfully dropped remaining capabilities.
Jun 11 17:53:58 simon-watery avahi-daemon[1190]: No service file found in /etc/avahi/services.
Jun 11 17:53:58 simon-watery avahi-daemon[1190]: Network interface enumeration completed.
Jun 11 17:53:58 simon-watery avahi-daemon[1190]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun 11 17:53:58 simon-watery avahi-daemon[1190]: Server startup complete. Host name is simon-watery.local. Local service cookie is 3478267437.
Jun 11 17:53:58 simon-watery NetworkManager: <info>  starting...
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Trying to start the modem-manager...
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Linux version 2.6.32-22-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 (Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=f7185e7c-bb4e-414b-b15c-62e18742ea57 ro quiet splash
Jun 11 17:53:58 simon-watery kernel: [    0.000000] KERNEL supported cpus:
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   Intel GenuineIntel
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   AMD AuthenticAMD
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   Centaur CentaurHauls
Jun 11 17:53:58 simon-watery kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf670000 (usable)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  BIOS-e820: 00000000bf670000 - 00000000bf688000 (ACPI data)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  BIOS-e820: 00000000bf688000 - 00000000bf6dc000 (ACPI NVS)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  BIOS-e820: 00000000bf6dc000 - 00000000bf700000 (reserved)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  BIOS-e820: 00000000bf800000 - 00000000c0000000 (reserved)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000240000000 (usable)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] DMI 2.6 present.
Jun 11 17:53:58 simon-watery kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Jun 11 17:53:58 simon-watery kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] last_pfn = 0x240000 max_arch_pfn = 0x400000000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] MTRR default type: uncachable
Jun 11 17:53:58 simon-watery kernel: [    0.000000] MTRR fixed ranges enabled:
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   00000-9FFFF write-back
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   A0000-BFFFF uncachable
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   C0000-CFFFF write-protect
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   D0000-DFFFF uncachable
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   E0000-E7FFF write-through
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   E8000-FFFFF write-protect
Jun 11 17:53:58 simon-watery kernel: [    0.000000] MTRR variable ranges enabled:
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   0 base 000000000 mask E00000000 write-back
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   1 base 200000000 mask FC0000000 write-back
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   4 disabled
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   5 disabled
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   6 disabled
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   7 disabled
Jun 11 17:53:58 simon-watery kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun 11 17:53:58 simon-watery kernel: [    0.000000] e820 update range: 00000000bff00000 - 0000000100000000 (usable) ==> (reserved)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] last_pfn = 0xbf670 max_arch_pfn = 0x400000000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jun 11 17:53:58 simon-watery kernel: [    0.000000] modified physical RAM map:
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  modified: 0000000000010000 - 000000000009e800 (usable)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  modified: 000000000009e800 - 00000000000a0000 (reserved)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  modified: 0000000000100000 - 00000000bf670000 (usable)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  modified: 00000000bf670000 - 00000000bf688000 (ACPI data)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  modified: 00000000bf688000 - 00000000bf6dc000 (ACPI NVS)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  modified: 00000000bf6dc000 - 00000000bf700000 (reserved)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  modified: 00000000bf800000 - 00000000c0000000 (reserved)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  modified: 0000000100000000 - 0000000240000000 (usable)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bf670000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] NX (Execute Disable) protection: active
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  0000000000 - 00bf600000 page 2M
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  00bf600000 - 00bf670000 page 4k
Jun 11 17:53:58 simon-watery kernel: [    0.000000] kernel direct mapping tables up to bf670000 @ 10000-15000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000240000000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] NX (Execute Disable) protection: active
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  0100000000 - 0240000000 page 2M
Jun 11 17:53:58 simon-watery kernel: [    0.000000] kernel direct mapping tables up to 240000000 @ 13000-1d000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] RAMDISK: 377fe000 - 37fef810
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: RSDP 00000000000fad50 00024 (v02 ACPIAM)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: XSDT 00000000bf670100 0005C (v01 122109 XSDT1805 20091221 MSFT 00000097)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: FACP 00000000bf670290 000F4 (v03 122109 FACP1805 20091221 MSFT 00000097)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: DSDT 00000000bf6704a0 0F151 (v01  A1320 A1320001 00000001 INTL 20060113)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: FACS 00000000bf688000 00040
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: APIC 00000000bf670390 000CC (v01 122109 APIC1805 20091221 MSFT 00000097)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: MCFG 00000000bf670460 0003C (v01 122109 OEMMCFG  20091221 MSFT 00000097)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: OEMB 00000000bf688040 00072 (v01 122109 OEMB1805 20091221 MSFT 00000097)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: HPET 00000000bf67f6a0 00038 (v01 122109 OEMHPET  20091221 MSFT 00000097)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: OSFR 00000000bf67f6e0 000B0 (v01 122109 OEMOSFR  20091221 MSFT 00000097)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: SSDT 00000000bf68ad80 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] No NUMA configuration found
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Faking a node at 0000000000000000-0000000240000000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000240000000
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   NODE_DATA [0000000000018000 - 000000000001cfff]
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   bootmap [000000000001d000 -  0000000000064fff] pages 48
Jun 11 17:53:58 simon-watery kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0240000000]
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   #3 [00377fe000 - 0037fef810]          RAMDISK ==> [00377fe000 - 0037fef810]
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   #4 [000009e800 - 0000100000]    BIOS reserved ==> [000009e800 - 0000100000]
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   #5 [0001a2a000 - 0001a2a2d0]              BRK ==> [0001a2a000 - 0001a2a2d0]
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   #7 [0000013000 - 0000018000]          PGTABLE ==> [0000013000 - 0000018000]
Jun 11 17:53:58 simon-watery kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Jun 11 17:53:58 simon-watery kernel: [    0.000000]  [ffffea0000000000-ffffea0007dfffff] PMD -> [ffff880028600000-ffff88002f5fffff] on node 0
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Zone PFN ranges:
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   Normal   0x00100000 -> 0x00240000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Movable zone start PFN for each node
Jun 11 17:53:58 simon-watery kernel: [    0.000000] early_node_map[3] active PFN ranges
Jun 11 17:53:58 simon-watery kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Jun 11 17:53:58 simon-watery kernel: [    0.000000]     0: 0x00000100 -> 0x000bf670
Jun 11 17:53:58 simon-watery kernel: [    0.000000]     0: 0x00100000 -> 0x00240000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] On node 0 totalpages: 2094590
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   DMA zone: 108 pages reserved
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   DMA zone: 3818 pages, LIFO batch:0
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   DMA32 zone: 765608 pages, LIFO batch:31
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   Normal zone: 17920 pages used for memmap
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   Normal zone: 1292800 pages, LIFO batch:31
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
Jun 11 17:53:58 simon-watery kernel: [    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 11 17:53:58 simon-watery kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] SMP: Allowing 16 CPUs, 8 hotplug CPUs
Jun 11 17:53:58 simon-watery kernel: [    0.000000] nr_irqs_gsi: 24
Jun 11 17:53:58 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000bf670000 - 00000000bf688000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000bf688000 - 00000000bf6dc000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000bf6dc000 - 00000000bf700000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000bf700000 - 00000000bf800000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000bf800000 - 00000000c0000000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun 11 17:53:58 simon-watery kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:16 nr_node_ids:1
Jun 11 17:53:58 simon-watery kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u131072
Jun 11 17:53:58 simon-watery kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u131072 alloc=1*2097152
Jun 11 17:53:58 simon-watery kernel: [    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2062226
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Policy zone: Normal
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=f7185e7c-bb4e-414b-b15c-62e18742ea57 ro quiet splash
Jun 11 17:53:58 simon-watery kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Initializing CPU#0
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Checking aperture...
Jun 11 17:53:58 simon-watery kernel: [    0.000000] No AGP bridge found
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jun 11 17:53:58 simon-watery kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Memory: 8176920k/9437184k available (5409k kernel code, 1058824k absent, 201440k reserved, 2976k data, 876k init)
Jun 11 17:53:58 simon-watery kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Hierarchical RCU implementation.
Jun 11 17:53:58 simon-watery kernel: [    0.000000] NR_IRQS:4352 nr_irqs:536
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Extended CMOS year: 2000
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Console: colour VGA+ 80x25
Jun 11 17:53:58 simon-watery kernel: [    0.000000] console [tty0] enabled
Jun 11 17:53:58 simon-watery kernel: [    0.000000] allocated 83886080 bytes of page_cgroup
Jun 11 17:53:58 simon-watery kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun 11 17:53:58 simon-watery kernel: [    0.000000] hpet clockevent registered
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   alloc irq_desc for 24 on node 0
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   alloc kstat_irqs on node 0
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   alloc irq_desc for 25 on node 0
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   alloc kstat_irqs on node 0
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   alloc irq_desc for 26 on node 0
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   alloc kstat_irqs on node 0
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   alloc irq_desc for 27 on node 0
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   alloc kstat_irqs on node 0
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   alloc irq_desc for 28 on node 0
Jun 11 17:53:58 simon-watery kernel: [    0.000000]   alloc kstat_irqs on node 0
Jun 11 17:53:58 simon-watery kernel: [    0.000000] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
Jun 11 17:53:58 simon-watery kernel: [    0.000000] Fast TSC calibration using PIT
Jun 11 17:53:58 simon-watery kernel: [    0.010000] Detected 2942.281 MHz processor.
Jun 11 17:53:58 simon-watery kernel: [    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5884.56 BogoMIPS (lpj=29422810)
Jun 11 17:53:58 simon-watery kernel: [    0.000016] Security Framework initialized
Jun 11 17:53:58 simon-watery kernel: [    0.000027] AppArmor: AppArmor initialized
Jun 11 17:53:58 simon-watery kernel: [    0.000475] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Jun 11 17:53:58 simon-watery kernel: [    0.001861] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun 11 17:53:58 simon-watery kernel: [    0.002475] Mount-cache hash table entries: 256
Jun 11 17:53:58 simon-watery kernel: [    0.002551] Initializing cgroup subsys ns
Jun 11 17:53:58 simon-watery kernel: [    0.002553] Initializing cgroup subsys cpuacct
Jun 11 17:53:58 simon-watery kernel: [    0.002556] Initializing cgroup subsys memory
Jun 11 17:53:58 simon-watery kernel: [    0.002560] Initializing cgroup subsys devices
Jun 11 17:53:58 simon-watery kernel: [    0.002562] Initializing cgroup subsys freezer
Jun 11 17:53:58 simon-watery kernel: [    0.002563] Initializing cgroup subsys net_cls
Jun 11 17:53:58 simon-watery kernel: [    0.002574] CPU: Physical Processor ID: 0
Jun 11 17:53:58 simon-watery kernel: [    0.002575] CPU: Processor Core ID: 0
Jun 11 17:53:58 simon-watery kernel: [    0.002578] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 11 17:53:58 simon-watery kernel: [    0.002579] CPU: L2 cache: 256K
Jun 11 17:53:58 simon-watery kernel: [    0.002580] CPU: L3 cache: 8192K
Jun 11 17:53:58 simon-watery kernel: [    0.002582] CPU 0/0x0 -> Node 0
Jun 11 17:53:58 simon-watery kernel: [    0.002584] mce: CPU supports 9 MCE banks
Jun 11 17:53:58 simon-watery kernel: [    0.002592] CPU0: Thermal monitoring enabled (TM1)
Jun 11 17:53:58 simon-watery kernel: [    0.002595] CPU 0 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6 CMCI:8
Jun 11 17:53:58 simon-watery kernel: [    0.002601] using mwait in idle threads.
Jun 11 17:53:58 simon-watery kernel: [    0.002602] Performance Events: Nehalem/Corei7 events, Intel PMU driver.
Jun 11 17:53:58 simon-watery kernel: [    0.002606] ... version:                3
Jun 11 17:53:58 simon-watery kernel: [    0.002607] ... bit width:              48
Jun 11 17:53:58 simon-watery kernel: [    0.002608] ... generic registers:      4
Jun 11 17:53:58 simon-watery kernel: [    0.002609] ... value mask:             0000ffffffffffff
Jun 11 17:53:58 simon-watery kernel: [    0.002610] ... max period:             000000007fffffff
Jun 11 17:53:58 simon-watery kernel: [    0.002611] ... fixed-purpose events:   3
Jun 11 17:53:58 simon-watery kernel: [    0.002612] ... event mask:             000000070000000f
Jun 11 17:53:58 simon-watery kernel: [    0.004167] ACPI: Core revision 20090903
Jun 11 17:53:58 simon-watery kernel: [    0.038173] ftrace: converting mcount calls to 0f 1f 44 00 00
Jun 11 17:53:58 simon-watery kernel: [    0.038177] ftrace: allocating 22518 entries in 89 pages
Jun 11 17:53:58 simon-watery kernel: [    0.043569] Setting APIC routing to physical flat
Jun 11 17:53:58 simon-watery kernel: [    0.043886] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 11 17:53:58 simon-watery kernel: [    0.143885] CPU0: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
Jun 11 17:53:58 simon-watery kernel: [    0.258647] Booting processor 1 APIC 0x2 ip 0x6000
Jun 11 17:53:58 simon-watery kernel: [    0.269087] Initializing CPU#1
Jun 11 17:53:58 simon-watery kernel: [    0.418564] CPU: Physical Processor ID: 0
Jun 11 17:53:58 simon-watery kernel: [    0.418565] CPU: Processor Core ID: 1
Jun 11 17:53:58 simon-watery kernel: [    0.418566] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 11 17:53:58 simon-watery kernel: [    0.418567] CPU: L2 cache: 256K
Jun 11 17:53:58 simon-watery kernel: [    0.418568] CPU: L3 cache: 8192K
Jun 11 17:53:58 simon-watery kernel: [    0.418570] CPU 1/0x2 -> Node 0
Jun 11 17:53:58 simon-watery kernel: [    0.418578] CPU1: Thermal monitoring enabled (TM1)
Jun 11 17:53:58 simon-watery kernel: [    0.418580] CPU 1 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Jun 11 17:53:58 simon-watery kernel: [    0.418605] CPU1: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
Jun 11 17:53:58 simon-watery kernel: [    0.418611] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jun 11 17:53:58 simon-watery kernel: [    0.438671] Booting processor 2 APIC 0x4 ip 0x6000
Jun 11 17:53:58 simon-watery kernel: [    0.449002] Initializing CPU#2
Jun 11 17:53:58 simon-watery kernel: [    0.598556] CPU: Physical Processor ID: 0
Jun 11 17:53:58 simon-watery kernel: [    0.598557] CPU: Processor Core ID: 2
Jun 11 17:53:58 simon-watery kernel: [    0.598559] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 11 17:53:58 simon-watery kernel: [    0.598560] CPU: L2 cache: 256K
Jun 11 17:53:58 simon-watery kernel: [    0.598560] CPU: L3 cache: 8192K
Jun 11 17:53:58 simon-watery kernel: [    0.598562] CPU 2/0x4 -> Node 0
Jun 11 17:53:58 simon-watery kernel: [    0.598570] CPU2: Thermal monitoring enabled (TM1)
Jun 11 17:53:58 simon-watery kernel: [    0.598573] CPU 2 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Jun 11 17:53:58 simon-watery kernel: [    0.598627] CPU2: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
Jun 11 17:53:58 simon-watery kernel: [    0.598633] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Jun 11 17:53:58 simon-watery kernel: [    0.618693] Booting processor 3 APIC 0x6 ip 0x6000
Jun 11 17:53:58 simon-watery kernel: [    0.629024] Initializing CPU#3
Jun 11 17:53:58 simon-watery kernel: [    0.778548] CPU: Physical Processor ID: 0
Jun 11 17:53:58 simon-watery kernel: [    0.778549] CPU: Processor Core ID: 3
Jun 11 17:53:58 simon-watery kernel: [    0.778551] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 11 17:53:58 simon-watery kernel: [    0.778552] CPU: L2 cache: 256K
Jun 11 17:53:58 simon-watery kernel: [    0.778553] CPU: L3 cache: 8192K
Jun 11 17:53:58 simon-watery kernel: [    0.778554] CPU 3/0x6 -> Node 0
Jun 11 17:53:58 simon-watery kernel: [    0.778563] CPU3: Thermal monitoring enabled (TM1)
Jun 11 17:53:58 simon-watery kernel: [    0.778565] CPU 3 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Jun 11 17:53:58 simon-watery kernel: [    0.778650] CPU3: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
Jun 11 17:53:58 simon-watery kernel: [    0.778655] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Jun 11 17:53:58 simon-watery kernel: [    0.798715] Booting processor 4 APIC 0x1 ip 0x6000
Jun 11 17:53:58 simon-watery kernel: [    0.809047] Initializing CPU#4
Jun 11 17:53:58 simon-watery kernel: [    0.958541] CPU: Physical Processor ID: 0
Jun 11 17:53:58 simon-watery kernel: [    0.958542] CPU: Processor Core ID: 0
Jun 11 17:53:58 simon-watery kernel: [    0.958544] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 11 17:53:58 simon-watery kernel: [    0.958546] CPU: L2 cache: 256K
Jun 11 17:53:58 simon-watery kernel: [    0.958547] CPU: L3 cache: 8192K
Jun 11 17:53:58 simon-watery kernel: [    0.958549] CPU 4/0x1 -> Node 0
Jun 11 17:53:58 simon-watery kernel: [    0.958558] CPU4: Thermal monitoring enabled (TM1)
Jun 11 17:53:58 simon-watery kernel: [    0.958560] CPU 4 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
Jun 11 17:53:58 simon-watery kernel: [    0.958586] CPU4: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
Jun 11 17:53:58 simon-watery kernel: [    0.958593] checking TSC synchronization [CPU#0 -> CPU#4]: passed.
Jun 11 17:53:58 simon-watery kernel: [    0.978655] Booting processor 5 APIC 0x3 ip 0x6000
Jun 11 17:53:58 simon-watery kernel: [    0.988986] Initializing CPU#5
Jun 11 17:53:58 simon-watery kernel: [    1.138533] CPU: Physical Processor ID: 0
Jun 11 17:53:58 simon-watery kernel: [    1.138534] CPU: Processor Core ID: 1
Jun 11 17:53:58 simon-watery kernel: [    1.138536] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 11 17:53:58 simon-watery kernel: [    1.138537] CPU: L2 cache: 256K
Jun 11 17:53:58 simon-watery kernel: [    1.138537] CPU: L3 cache: 8192K
Jun 11 17:53:58 simon-watery kernel: [    1.138539] CPU 5/0x3 -> Node 0
Jun 11 17:53:58 simon-watery kernel: [    1.138547] CPU5: Thermal monitoring enabled (TM1)
Jun 11 17:53:58 simon-watery kernel: [    1.138549] CPU 5 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
Jun 11 17:53:58 simon-watery kernel: [    1.138654] CPU5: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
Jun 11 17:53:58 simon-watery kernel: [    1.138660] checking TSC synchronization [CPU#0 -> CPU#5]: passed.
Jun 11 17:53:58 simon-watery kernel: [    1.158721] Booting processor 6 APIC 0x5 ip 0x6000
Jun 11 17:53:58 simon-watery kernel: [    1.169052] Initializing CPU#6
Jun 11 17:53:58 simon-watery kernel: [    1.318525] CPU: Physical Processor ID: 0
Jun 11 17:53:58 simon-watery kernel: [    1.318526] CPU: Processor Core ID: 2
Jun 11 17:53:58 simon-watery kernel: [    1.318528] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 11 17:53:58 simon-watery kernel: [    1.318529] CPU: L2 cache: 256K
Jun 11 17:53:58 simon-watery kernel: [    1.318530] CPU: L3 cache: 8192K
Jun 11 17:53:58 simon-watery kernel: [    1.318531] CPU 6/0x5 -> Node 0
Jun 11 17:53:58 simon-watery kernel: [    1.318539] CPU6: Thermal monitoring enabled (TM1)
Jun 11 17:53:58 simon-watery kernel: [    1.318541] CPU 6 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
Jun 11 17:53:58 simon-watery kernel: [    1.318583] CPU6: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
Jun 11 17:53:58 simon-watery kernel: [    1.318589] checking TSC synchronization [CPU#0 -> CPU#6]: passed.
Jun 11 17:53:58 simon-watery kernel: [    1.338651] Booting processor 7 APIC 0x7 ip 0x6000
Jun 11 17:53:58 simon-watery kernel: [    1.348982] Initializing CPU#7
Jun 11 17:53:58 simon-watery kernel: [    1.498518] CPU: Physical Processor ID: 0
Jun 11 17:53:58 simon-watery kernel: [    1.498518] CPU: Processor Core ID: 3
Jun 11 17:53:58 simon-watery kernel: [    1.498520] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 11 17:53:58 simon-watery kernel: [    1.498521] CPU: L2 cache: 256K
Jun 11 17:53:58 simon-watery kernel: [    1.498522] CPU: L3 cache: 8192K
Jun 11 17:53:58 simon-watery kernel: [    1.498524] CPU 7/0x7 -> Node 0
Jun 11 17:53:58 simon-watery kernel: [    1.498532] CPU7: Thermal monitoring enabled (TM1)
Jun 11 17:53:58 simon-watery kernel: [    1.498534] CPU 7 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
Jun 11 17:53:58 simon-watery kernel: [    1.498608] CPU7: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz stepping 05
Jun 11 17:53:58 simon-watery kernel: [    1.498613] checking TSC synchronization [CPU#0 -> CPU#7]: passed.
Jun 11 17:53:58 simon-watery kernel: [    1.518627] Brought up 8 CPUs
Jun 11 17:53:58 simon-watery kernel: [    1.518629] Total of 8 processors activated (47078.46 BogoMIPS).
Jun 11 17:53:58 simon-watery kernel: [    1.521683] CPU0 attaching sched-domain:
Jun 11 17:53:58 simon-watery kernel: [    1.521685]  domain 0: span 0,4 level SIBLING
Jun 11 17:53:58 simon-watery kernel: [    1.521687]   groups: 0 (cpu_power = 589) 4 (cpu_power = 589)
Jun 11 17:53:58 simon-watery kernel: [    1.521690]   domain 1: span 0-7 level MC
Jun 11 17:53:58 simon-watery kernel: [    1.521691]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun 11 17:53:58 simon-watery kernel: [    1.521698] CPU1 attaching sched-domain:
Jun 11 17:53:58 simon-watery kernel: [    1.521699]  domain 0: span 1,5 level SIBLING
Jun 11 17:53:58 simon-watery kernel: [    1.521701]   groups: 1 (cpu_power = 589) 5 (cpu_power = 589)
Jun 11 17:53:58 simon-watery kernel: [    1.521704]   domain 1: span 0-7 level MC
Jun 11 17:53:58 simon-watery kernel: [    1.521705]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun 11 17:53:58 simon-watery kernel: [    1.521710] CPU2 attaching sched-domain:
Jun 11 17:53:58 simon-watery kernel: [    1.521711]  domain 0: span 2,6 level SIBLING
Jun 11 17:53:58 simon-watery kernel: [    1.521713]   groups: 2 (cpu_power = 589) 6 (cpu_power = 589)
Jun 11 17:53:58 simon-watery kernel: [    1.521716]   domain 1: span 0-7 level MC
Jun 11 17:53:58 simon-watery kernel: [    1.521717]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun 11 17:53:58 simon-watery kernel: [    1.521722] CPU3 attaching sched-domain:
Jun 11 17:53:58 simon-watery kernel: [    1.521723]  domain 0: span 3,7 level SIBLING
Jun 11 17:53:58 simon-watery kernel: [    1.521725]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
Jun 11 17:53:58 simon-watery kernel: [    1.521728]   domain 1: span 0-7 level MC
Jun 11 17:53:58 simon-watery kernel: [    1.521729]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun 11 17:53:58 simon-watery kernel: [    1.521734] CPU4 attaching sched-domain:
Jun 11 17:53:58 simon-watery kernel: [    1.521735]  domain 0: span 0,4 level SIBLING
Jun 11 17:53:58 simon-watery kernel: [    1.521737]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
Jun 11 17:53:58 simon-watery kernel: [    1.521740]   domain 1: span 0-7 level MC
Jun 11 17:53:58 simon-watery kernel: [    1.521741]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun 11 17:53:58 simon-watery kernel: [    1.521746] CPU5 attaching sched-domain:
Jun 11 17:53:58 simon-watery kernel: [    1.521747]  domain 0: span 1,5 level SIBLING
Jun 11 17:53:58 simon-watery kernel: [    1.521749]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
Jun 11 17:53:58 simon-watery kernel: [    1.521752]   domain 1: span 0-7 level MC
Jun 11 17:53:58 simon-watery kernel: [    1.521753]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun 11 17:53:58 simon-watery kernel: [    1.521758] CPU6 attaching sched-domain:
Jun 11 17:53:58 simon-watery kernel: [    1.521759]  domain 0: span 2,6 level SIBLING
Jun 11 17:53:58 simon-watery kernel: [    1.521761]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
Jun 11 17:53:58 simon-watery kernel: [    1.521764]   domain 1: span 0-7 level MC
Jun 11 17:53:58 simon-watery kernel: [    1.521765]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun 11 17:53:58 simon-watery kernel: [    1.521770] CPU7 attaching sched-domain:
Jun 11 17:53:58 simon-watery kernel: [    1.521771]  domain 0: span 3,7 level SIBLING
Jun 11 17:53:58 simon-watery kernel: [    1.521773]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
Jun 11 17:53:58 simon-watery kernel: [    1.521776]   domain 1: span 0-7 level MC
Jun 11 17:53:58 simon-watery kernel: [    1.521777]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun 11 17:53:58 simon-watery kernel: [    1.522031] devtmpfs: initialized
Jun 11 17:53:58 simon-watery kernel: [    1.522255] regulator: core version 0.5
Jun 11 17:53:58 simon-watery kernel: [    1.522278] Time: 16:53:45  Date: 06/11/10
Jun 11 17:53:58 simon-watery kernel: [    1.522309] NET: Registered protocol family 16
Jun 11 17:53:58 simon-watery kernel: [    1.522366] Trying to unpack rootfs image as initramfs...
Jun 11 17:53:58 simon-watery kernel: [    1.522386] ACPI: bus type pci registered
Jun 11 17:53:58 simon-watery kernel: [    1.522431] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jun 11 17:53:58 simon-watery kernel: [    1.522433] PCI: Not using MMCONFIG.
Jun 11 17:53:58 simon-watery kernel: [    1.522434] PCI: Using configuration type 1 for base access
Jun 11 17:53:58 simon-watery kernel: [    1.522967] bio: create slab <bio-0> at 0
Jun 11 17:53:58 simon-watery kernel: [    1.523707] ACPI: EC: Look up EC in DSDT
Jun 11 17:53:58 simon-watery kernel: [    1.525743] ACPI: Executed 1 blocks of module-level executable AML code
Jun 11 17:53:58 simon-watery kernel: [    1.536345] ACPI: Interpreter enabled
Jun 11 17:53:58 simon-watery kernel: [    1.536348] ACPI: (supports S0 S1 S3 S4 S5)
Jun 11 17:53:58 simon-watery kernel: [    1.536364] ACPI: Using IOAPIC for interrupt routing
Jun 11 17:53:58 simon-watery kernel: [    1.536405] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jun 11 17:53:58 simon-watery kernel: [    1.538187] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Jun 11 17:53:58 simon-watery kernel: [    1.542818] PCI: Using MMCONFIG at e0000000 - efffffff
Jun 11 17:53:58 simon-watery kernel: [    1.549941] ACPI: No dock devices found.
Jun 11 17:53:58 simon-watery kernel: [    1.550182] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 11 17:53:58 simon-watery kernel: [    1.550279] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
Jun 11 17:53:58 simon-watery kernel: [    1.550282] pci 0000:00:05.0: PME# disabled
Jun 11 17:53:58 simon-watery kernel: [    1.550518] pci 0000:00:1a.0: reg 10 32bit mmio: [0xf7ffe000-0xf7ffe3ff]
Jun 11 17:53:58 simon-watery kernel: [    1.550566] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Jun 11 17:53:58 simon-watery kernel: [    1.550569] pci 0000:00:1a.0: PME# disabled
Jun 11 17:53:58 simon-watery kernel: [    1.550603] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf7ff8000-0xf7ffbfff]
Jun 11 17:53:58 simon-watery kernel: [    1.550639] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jun 11 17:53:58 simon-watery kernel: [    1.550641] pci 0000:00:1b.0: PME# disabled
Jun 11 17:53:58 simon-watery kernel: [    1.550695] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jun 11 17:53:58 simon-watery kernel: [    1.550698] pci 0000:00:1c.0: PME# disabled
Jun 11 17:53:58 simon-watery kernel: [    1.550754] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Jun 11 17:53:58 simon-watery kernel: [    1.550757] pci 0000:00:1c.4: PME# disabled
Jun 11 17:53:58 simon-watery kernel: [    1.550810] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Jun 11 17:53:58 simon-watery kernel: [    1.550813] pci 0000:00:1c.5: PME# disabled
Jun 11 17:53:58 simon-watery kernel: [    1.550865] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
Jun 11 17:53:58 simon-watery kernel: [    1.550868] pci 0000:00:1c.6: PME# disabled
Jun 11 17:53:58 simon-watery kernel: [    1.550921] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
Jun 11 17:53:58 simon-watery kernel: [    1.550923] pci 0000:00:1c.7: PME# disabled
Jun 11 17:53:58 simon-watery kernel: [    1.550968] pci 0000:00:1d.0: reg 10 32bit mmio: [0xf7ffd000-0xf7ffd3ff]
Jun 11 17:53:58 simon-watery kernel: [    1.551015] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Jun 11 17:53:58 simon-watery kernel: [    1.551018] pci 0000:00:1d.0: PME# disabled
Jun 11 17:53:58 simon-watery kernel: [    1.551179] pci 0000:00:1f.2: reg 10 io port: [0xc880-0xc887]
Jun 11 17:53:58 simon-watery kernel: [    1.551184] pci 0000:00:1f.2: reg 14 io port: [0xc800-0xc803]
Jun 11 17:53:58 simon-watery kernel: [    1.551188] pci 0000:00:1f.2: reg 18 io port: [0xc480-0xc487]
Jun 11 17:53:58 simon-watery kernel: [    1.551192] pci 0000:00:1f.2: reg 1c io port: [0xc400-0xc403]
Jun 11 17:53:58 simon-watery kernel: [    1.551197] pci 0000:00:1f.2: reg 20 io port: [0xc080-0xc09f]
Jun 11 17:53:58 simon-watery kernel: [    1.551201] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf7ff7000-0xf7ff77ff]
Jun 11 17:53:58 simon-watery kernel: [    1.551228] pci 0000:00:1f.2: PME# supported from D3hot
Jun 11 17:53:58 simon-watery kernel: [    1.551230] pci 0000:00:1f.2: PME# disabled
Jun 11 17:53:58 simon-watery kernel: [    1.551254] pci 0000:00:1f.3: reg 10 64bit mmio: [0xf7ffc000-0xf7ffc0ff]
Jun 11 17:53:58 simon-watery kernel: [    1.551265] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
Jun 11 17:53:58 simon-watery kernel: [    1.551304] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
Jun 11 17:53:58 simon-watery kernel: [    1.551312] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
Jun 11 17:53:58 simon-watery kernel: [    1.551319] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
Jun 11 17:53:58 simon-watery kernel: [    1.551323] pci 0000:01:00.0: reg 24 io port: [0xdc00-0xdc7f]
Jun 11 17:53:58 simon-watery kernel: [    1.551327] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfbd80000-0xfbdfffff]
Jun 11 17:53:58 simon-watery kernel: [    1.551368] pci 0000:00:05.0: bridge io port: [0xd000-0xdfff]
Jun 11 17:53:58 simon-watery kernel: [    1.551371] pci 0000:00:05.0: bridge 32bit mmio: [0xf8000000-0xfbdfffff]
Jun 11 17:53:58 simon-watery kernel: [    1.551374] pci 0000:00:05.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
Jun 11 17:53:58 simon-watery kernel: [    1.551590] pci 0000:07:03.0: reg 10 32bit mmio: [0xfbeff800-0xfbefffff]
Jun 11 17:53:58 simon-watery kernel: [    1.551596] pci 0000:07:03.0: reg 14 io port: [0xec00-0xec7f]
Jun 11 17:53:58 simon-watery kernel: [    1.551635] pci 0000:07:03.0: supports D2
Jun 11 17:53:58 simon-watery kernel: [    1.551636] pci 0000:07:03.0: PME# supported from D2 D3hot D3cold
Jun 11 17:53:58 simon-watery kernel: [    1.551639] pci 0000:07:03.0: PME# disabled
Jun 11 17:53:58 simon-watery kernel: [    1.551674] pci 0000:07:04.0: reg 10 io port: [0xe800-0xe8ff]
Jun 11 17:53:58 simon-watery kernel: [    1.551679] pci 0000:07:04.0: reg 14 32bit mmio: [0xfbeff400-0xfbeff4ff]
Jun 11 17:53:58 simon-watery kernel: [    1.551701] pci 0000:07:04.0: reg 30 32bit mmio pref: [0xfbec0000-0xfbedffff]
Jun 11 17:53:58 simon-watery kernel: [    1.551721] pci 0000:07:04.0: supports D1 D2
Jun 11 17:53:58 simon-watery kernel: [    1.551723] pci 0000:07:04.0: PME# supported from D1 D2 D3hot D3cold
Jun 11 17:53:58 simon-watery kernel: [    1.551726] pci 0000:07:04.0: PME# disabled
Jun 11 17:53:58 simon-watery kernel: [    1.551763] pci 0000:00:1e.0: transparent bridge
Jun 11 17:53:58 simon-watery kernel: [    1.551766] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
Jun 11 17:53:58 simon-watery kernel: [    1.551769] pci 0000:00:1e.0: bridge 32bit mmio: [0xfbe00000-0xfbefffff]
Jun 11 17:53:58 simon-watery kernel: [    1.551798] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 11 17:53:58 simon-watery kernel: [    1.551935] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR1E._PRT]
Jun 11 17:53:58 simon-watery kernel: [    1.552032] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
Jun 11 17:53:58 simon-watery kernel: [    1.552080] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
Jun 11 17:53:58 simon-watery kernel: [    1.552124] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR24._PRT]
Jun 11 17:53:58 simon-watery kernel: [    1.552167] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR25._PRT]
Jun 11 17:53:58 simon-watery kernel: [    1.552211] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR26._PRT]
Jun 11 17:53:58 simon-watery kernel: [    1.552263] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR27._PRT]
Jun 11 17:53:58 simon-watery kernel: [    1.569811] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
Jun 11 17:53:58 simon-watery kernel: [    1.569908] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
Jun 11 17:53:58 simon-watery kernel: [    1.570000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 *12 14 15)
Jun 11 17:53:58 simon-watery kernel: [    1.570095] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
Jun 11 17:53:58 simon-watery kernel: [    1.570189] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
Jun 11 17:53:58 simon-watery kernel: [    1.570286] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 *15)
Jun 11 17:53:58 simon-watery kernel: [    1.570380] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 7 10 11 12 *14 15)
Jun 11 17:53:58 simon-watery kernel: [    1.570475] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 6 7 10 11 12 14 15)
Jun 11 17:53:58 simon-watery kernel: [    1.570553] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun 11 17:53:58 simon-watery kernel: [    1.570555] vgaarb: loaded
Jun 11 17:53:58 simon-watery kernel: [    1.570619] SCSI subsystem initialized
Jun 11 17:53:58 simon-watery kernel: [    1.570719] libata version 3.00 loaded.
Jun 11 17:53:58 simon-watery kernel: [    1.570764] usbcore: registered new interface driver usbfs
Jun 11 17:53:58 simon-watery kernel: [    1.570771] usbcore: registered new interface driver hub
Jun 11 17:53:58 simon-watery kernel: [    1.570785] usbcore: registered new device driver usb
Jun 11 17:53:58 simon-watery kernel: [    1.570872] ACPI: WMI: Mapper loaded
Jun 11 17:53:58 simon-watery kernel: [    1.570873] PCI: Using ACPI for IRQ routing
Jun 11 17:53:58 simon-watery kernel: [    1.570979] NetLabel: Initializing
Jun 11 17:53:58 simon-watery kernel: [    1.570980] NetLabel:  domain hash size = 128
Jun 11 17:53:58 simon-watery kernel: [    1.570981] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 11 17:53:58 simon-watery kernel: [    1.570990] NetLabel:  unlabeled traffic allowed by default
Jun 11 17:53:58 simon-watery kernel: [    1.571019] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 25, 26, 27, 28, 0
Jun 11 17:53:58 simon-watery kernel: [    1.571023] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Jun 11 17:53:58 simon-watery kernel: [    1.578525] hpet: hpet2 irq 24 for MSI
Jun 11 17:53:58 simon-watery kernel: [    1.578593] hpet: hpet3 irq 25 for MSI
Jun 11 17:53:58 simon-watery kernel: [    1.578619] hpet: hpet4 irq 26 for MSI
Jun 11 17:53:58 simon-watery kernel: [    1.578649] hpet: hpet5 irq 27 for MSI
Jun 11 17:53:58 simon-watery kernel: [    1.588595] hpet: hpet6 irq 28 for MSI
Jun 11 17:53:58 simon-watery kernel: [    1.598627] Switching to clocksource tsc
Jun 11 17:53:58 simon-watery kernel: [    1.599811] AppArmor: AppArmor Filesystem Enabled
Jun 11 17:53:58 simon-watery kernel: [    1.599822] pnp: PnP ACPI init
Jun 11 17:53:58 simon-watery kernel: [    1.599832] ACPI: bus type pnp registered
Jun 11 17:53:58 simon-watery kernel: [    1.601712] pnp: PnP ACPI: found 14 devices
Jun 11 17:53:58 simon-watery kernel: [    1.601714] ACPI: ACPI bus type pnp unregistered
Jun 11 17:53:58 simon-watery kernel: [    1.601721] system 00:01: iomem range 0xfc000000-0xfcffffff has been reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601723] system 00:01: iomem range 0xfd000000-0xfdffffff has been reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601725] system 00:01: iomem range 0xfe000000-0xfebfffff has been reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601727] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601732] system 00:06: ioport range 0x290-0x29f has been reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601735] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601737] system 00:07: ioport range 0x800-0x87f has been reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601739] system 00:07: ioport range 0x500-0x57f has been reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601740] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601742] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601744] system 00:07: iomem range 0xfed40000-0xfed8ffff has been reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601748] system 00:0a: iomem range 0xffc00000-0xffdfffff has been reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601751] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601753] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601756] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601759] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601761] system 00:0d: iomem range 0xc0000-0xcffff has been reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601763] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601765] system 00:0d: iomem range 0x100000-0xbfefffff could not be reserved
Jun 11 17:53:58 simon-watery kernel: [    1.601766] system 00:0d: iomem range 0xfed90000-0xffffffff could not be reserved
Jun 11 17:53:58 simon-watery kernel: [    1.606387] pci 0000:07:04.0: BAR 6: address space collision on of device [0xfbec0000-0xfbedffff]
Jun 11 17:53:58 simon-watery kernel: [    1.606431] pci 0000:00:05.0: PCI bridge, secondary bus 0000:01
Jun 11 17:53:58 simon-watery kernel: [    1.606433] pci 0000:00:05.0:   IO window: 0xd000-0xdfff
Jun 11 17:53:58 simon-watery kernel: [    1.606436] pci 0000:00:05.0:   MEM window: 0xf8000000-0xfbdfffff
Jun 11 17:53:58 simon-watery kernel: [    1.606438] pci 0000:00:05.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Jun 11 17:53:58 simon-watery kernel: [    1.606442] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:06
Jun 11 17:53:58 simon-watery kernel: [    1.606444] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
Jun 11 17:53:58 simon-watery kernel: [    1.606448] pci 0000:00:1c.0:   MEM window: 0xc0000000-0xc01fffff
Jun 11 17:53:58 simon-watery kernel: [    1.606451] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0200000-0x000000c03fffff
Jun 11 17:53:58 simon-watery kernel: [    1.606455] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:05
Jun 11 17:53:58 simon-watery kernel: [    1.606458] pci 0000:00:1c.4:   IO window: 0x2000-0x2fff
Jun 11 17:53:58 simon-watery kernel: [    1.606461] pci 0000:00:1c.4:   MEM window: 0xc0400000-0xc05fffff
Jun 11 17:53:58 simon-watery kernel: [    1.606464] pci 0000:00:1c.4:   PREFETCH window: 0x000000c0600000-0x000000c07fffff
Jun 11 17:53:58 simon-watery kernel: [    1.606469] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:04
Jun 11 17:53:58 simon-watery kernel: [    1.606471] pci 0000:00:1c.5:   IO window: 0x3000-0x3fff
Jun 11 17:53:58 simon-watery kernel: [    1.606474] pci 0000:00:1c.5:   MEM window: 0xc0800000-0xc09fffff
Jun 11 17:53:58 simon-watery kernel: [    1.606477] pci 0000:00:1c.5:   PREFETCH window: 0x000000c0a00000-0x000000c0bfffff
Jun 11 17:53:58 simon-watery kernel: [    1.606482] pci 0000:00:1c.6: PCI bridge, secondary bus 0000:03
Jun 11 17:53:58 simon-watery kernel: [    1.606483] pci 0000:00:1c.6:   IO window: disabled
Jun 11 17:53:58 simon-watery kernel: [    1.606487] pci 0000:00:1c.6:   MEM window: disabled
Jun 11 17:53:58 simon-watery kernel: [    1.606489] pci 0000:00:1c.6:   PREFETCH window: disabled
Jun 11 17:53:58 simon-watery kernel: [    1.606494] pci 0000:00:1c.7: PCI bridge, secondary bus 0000:02
Jun 11 17:53:58 simon-watery kernel: [    1.606495] pci 0000:00:1c.7:   IO window: disabled
Jun 11 17:53:58 simon-watery kernel: [    1.606498] pci 0000:00:1c.7:   MEM window: disabled
Jun 11 17:53:58 simon-watery kernel: [    1.606501] pci 0000:00:1c.7:   PREFETCH window: disabled
Jun 11 17:53:58 simon-watery kernel: [    1.606506] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
Jun 11 17:53:58 simon-watery kernel: [    1.606508] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
Jun 11 17:53:58 simon-watery kernel: [    1.606511] pci 0000:00:1e.0:   MEM window: 0xfbe00000-0xfbefffff
Jun 11 17:53:58 simon-watery kernel: [    1.606514] pci 0000:00:1e.0:   PREFETCH window: 0xc0c00000-0xc0cfffff
Jun 11 17:53:58 simon-watery kernel: [    1.606525]   alloc irq_desc for 16 on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.606526]   alloc kstat_irqs on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.606530] pci 0000:00:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 11 17:53:58 simon-watery kernel: [    1.606533] pci 0000:00:05.0: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    1.606538] pci 0000:00:1c.0: enabling device (0104 -> 0107)
Jun 11 17:53:58 simon-watery kernel: [    1.606541]   alloc irq_desc for 17 on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.606542]   alloc kstat_irqs on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.606544] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 11 17:53:58 simon-watery kernel: [    1.606547] pci 0000:00:1c.0: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    1.606553] pci 0000:00:1c.4: enabling device (0104 -> 0107)
Jun 11 17:53:58 simon-watery kernel: [    1.606555] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 11 17:53:58 simon-watery kernel: [    1.606558] pci 0000:00:1c.4: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    1.606563] pci 0000:00:1c.5: enabling device (0104 -> 0107)
Jun 11 17:53:58 simon-watery kernel: [    1.606566] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Jun 11 17:53:58 simon-watery kernel: [    1.606569] pci 0000:00:1c.5: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    1.606574]   alloc irq_desc for 18 on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.606575]   alloc kstat_irqs on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.606578] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 11 17:53:58 simon-watery kernel: [    1.606581] pci 0000:00:1c.6: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    1.606586]   alloc irq_desc for 19 on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.606587]   alloc kstat_irqs on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.606590] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jun 11 17:53:58 simon-watery kernel: [    1.606593] pci 0000:00:1c.7: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    1.606597] pci 0000:00:1e.0: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    1.606600] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Jun 11 17:53:58 simon-watery kernel: [    1.606602] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Jun 11 17:53:58 simon-watery kernel: [    1.606603] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
Jun 11 17:53:58 simon-watery kernel: [    1.606605] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xfbdfffff]
Jun 11 17:53:58 simon-watery kernel: [    1.606606] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
Jun 11 17:53:58 simon-watery kernel: [    1.606608] pci_bus 0000:06: resource 0 io:  [0x1000-0x1fff]
Jun 11 17:53:58 simon-watery kernel: [    1.606609] pci_bus 0000:06: resource 1 mem: [0xc0000000-0xc01fffff]
Jun 11 17:53:58 simon-watery kernel: [    1.606611] pci_bus 0000:06: resource 2 pref mem [0xc0200000-0xc03fffff]
Jun 11 17:53:58 simon-watery kernel: [    1.606613] pci_bus 0000:05: resource 0 io:  [0x2000-0x2fff]
Jun 11 17:53:58 simon-watery kernel: [    1.606614] pci_bus 0000:05: resource 1 mem: [0xc0400000-0xc05fffff]
Jun 11 17:53:58 simon-watery kernel: [    1.606616] pci_bus 0000:05: resource 2 pref mem [0xc0600000-0xc07fffff]
Jun 11 17:53:58 simon-watery kernel: [    1.606617] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
Jun 11 17:53:58 simon-watery kernel: [    1.606619] pci_bus 0000:04: resource 1 mem: [0xc0800000-0xc09fffff]
Jun 11 17:53:58 simon-watery kernel: [    1.606620] pci_bus 0000:04: resource 2 pref mem [0xc0a00000-0xc0bfffff]
Jun 11 17:53:58 simon-watery kernel: [    1.606622] pci_bus 0000:07: resource 0 io:  [0xe000-0xefff]
Jun 11 17:53:58 simon-watery kernel: [    1.606623] pci_bus 0000:07: resource 1 mem: [0xfbe00000-0xfbefffff]
Jun 11 17:53:58 simon-watery kernel: [    1.606625] pci_bus 0000:07: resource 2 pref mem [0xc0c00000-0xc0cfffff]
Jun 11 17:53:58 simon-watery kernel: [    1.606626] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
Jun 11 17:53:58 simon-watery kernel: [    1.606628] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffffffffffff]
Jun 11 17:53:58 simon-watery kernel: [    1.606649] NET: Registered protocol family 2
Jun 11 17:53:58 simon-watery kernel: [    1.606817] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun 11 17:53:58 simon-watery kernel: [    1.607570] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jun 11 17:53:58 simon-watery kernel: [    1.609655] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun 11 17:53:58 simon-watery kernel: [    1.609910] TCP: Hash tables configured (established 524288 bind 65536)
Jun 11 17:53:58 simon-watery kernel: [    1.609912] TCP reno registered
Jun 11 17:53:58 simon-watery kernel: [    1.609988] NET: Registered protocol family 1
Jun 11 17:53:58 simon-watery kernel: [    1.610051] pci 0000:01:00.0: Boot video device
Jun 11 17:53:58 simon-watery kernel: [    1.610413] Scanning for low memory corruption every 60 seconds
Jun 11 17:53:58 simon-watery kernel: [    1.610486] audit: initializing netlink socket (disabled)
Jun 11 17:53:58 simon-watery kernel: [    1.610494] type=2000 audit(1276275224.419:1): initialized
Jun 11 17:53:58 simon-watery kernel: [    1.617445] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun 11 17:53:58 simon-watery kernel: [    1.618385] VFS: Disk quotas dquot_6.5.2
Jun 11 17:53:58 simon-watery kernel: [    1.618419] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 11 17:53:58 simon-watery kernel: [    1.618815] fuse init (API version 7.13)
Jun 11 17:53:58 simon-watery kernel: [    1.618867] msgmni has been set to 15970
Jun 11 17:53:58 simon-watery kernel: [    1.619040] alg: No test for stdrng (krng)
Jun 11 17:53:58 simon-watery kernel: [    1.619076] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun 11 17:53:58 simon-watery kernel: [    1.619078] io scheduler noop registered
Jun 11 17:53:58 simon-watery kernel: [    1.619079] io scheduler anticipatory registered
Jun 11 17:53:58 simon-watery kernel: [    1.619080] io scheduler deadline registered
Jun 11 17:53:58 simon-watery kernel: [    1.619103] io scheduler cfq registered (default)
Jun 11 17:53:58 simon-watery kernel: [    1.619188]   alloc irq_desc for 29 on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.619189]   alloc kstat_irqs on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.619195] pcieport 0000:00:05.0: irq 29 for MSI/MSI-X
Jun 11 17:53:58 simon-watery kernel: [    1.619201] pcieport 0000:00:05.0: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    1.619279]   alloc irq_desc for 30 on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.619280]   alloc kstat_irqs on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.619285] pcieport 0000:00:1c.0: irq 30 for MSI/MSI-X
Jun 11 17:53:58 simon-watery kernel: [    1.619291] pcieport 0000:00:1c.0: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    1.619371]   alloc irq_desc for 31 on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.619372]   alloc kstat_irqs on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.619377] pcieport 0000:00:1c.4: irq 31 for MSI/MSI-X
Jun 11 17:53:58 simon-watery kernel: [    1.619383] pcieport 0000:00:1c.4: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    1.619463]   alloc irq_desc for 32 on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.619464]   alloc kstat_irqs on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.619469] pcieport 0000:00:1c.5: irq 32 for MSI/MSI-X
Jun 11 17:53:58 simon-watery kernel: [    1.619475] pcieport 0000:00:1c.5: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    1.619556]   alloc irq_desc for 33 on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.619557]   alloc kstat_irqs on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.619562] pcieport 0000:00:1c.6: irq 33 for MSI/MSI-X
Jun 11 17:53:58 simon-watery kernel: [    1.619568] pcieport 0000:00:1c.6: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    1.619642]   alloc irq_desc for 34 on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.619643]   alloc kstat_irqs on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.619648] pcieport 0000:00:1c.7: irq 34 for MSI/MSI-X
Jun 11 17:53:58 simon-watery kernel: [    1.619654] pcieport 0000:00:1c.7: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    1.619705] Firmware did not grant requested _OSC control
Jun 11 17:53:58 simon-watery kernel: [    1.619707] aer 0000:00:05.0:pcie02: AER service couldn't init device: no _OSC support
Jun 11 17:53:58 simon-watery kernel: [    1.619713] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 11 17:53:58 simon-watery kernel: [    1.619722] Firmware did not grant requested _OSC control
Jun 11 17:53:58 simon-watery kernel: [    1.619733] Firmware did not grant requested _OSC control
Jun 11 17:53:58 simon-watery kernel: [    1.619742] Firmware did not grant requested _OSC control
Jun 11 17:53:58 simon-watery kernel: [    1.619760] Firmware did not grant requested _OSC control
Jun 11 17:53:58 simon-watery kernel: [    1.619769] Firmware did not grant requested _OSC control
Jun 11 17:53:58 simon-watery kernel: [    1.619777] Firmware did not grant requested _OSC control
Jun 11 17:53:58 simon-watery kernel: [    1.619787] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 11 17:53:58 simon-watery kernel: [    1.619849] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jun 11 17:53:58 simon-watery kernel: [    1.619851] ACPI: Power Button [PWRB]
Jun 11 17:53:58 simon-watery kernel: [    1.619876] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun 11 17:53:58 simon-watery kernel: [    1.619878] ACPI: Power Button [PWRF]
Jun 11 17:53:58 simon-watery kernel: [    1.621024] ACPI: SSDT 00000000bf6880c0 0265C (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
Jun 11 17:53:58 simon-watery kernel: [    1.621432] ACPI: SSDT 00000000bf68a720 00659 (v01  PmRef  P001Cst 00003001 INTL 20060113)
Jun 11 17:53:58 simon-watery kernel: [    1.621817] Monitor-Mwait will be used to enter C-1 state
Jun 11 17:53:58 simon-watery kernel: [    1.621832] Monitor-Mwait will be used to enter C-2 state
Jun 11 17:53:58 simon-watery kernel: [    1.621845] Monitor-Mwait will be used to enter C-3 state
Jun 11 17:53:58 simon-watery kernel: [    1.621871] processor LNXCPU:00: registered as cooling_device0
Jun 11 17:53:58 simon-watery kernel: [    1.622114] processor LNXCPU:01: registered as cooling_device1
Jun 11 17:53:58 simon-watery kernel: [    1.622353] processor LNXCPU:02: registered as cooling_device2
Jun 11 17:53:58 simon-watery kernel: [    1.622594] processor LNXCPU:03: registered as cooling_device3
Jun 11 17:53:58 simon-watery kernel: [    1.622837] processor LNXCPU:04: registered as cooling_device4
Jun 11 17:53:58 simon-watery kernel: [    1.630387] processor LNXCPU:05: registered as cooling_device5
Jun 11 17:53:58 simon-watery kernel: [    1.630626] processor LNXCPU:06: registered as cooling_device6
Jun 11 17:53:58 simon-watery kernel: [    1.630861] processor LNXCPU:07: registered as cooling_device7
Jun 11 17:53:58 simon-watery kernel: [    1.633710] Linux agpgart interface v0.103
Jun 11 17:53:58 simon-watery kernel: [    1.633727] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jun 11 17:53:58 simon-watery kernel: [    1.634502] brd: module loaded
Jun 11 17:53:58 simon-watery kernel: [    1.634781] loop: module loaded
Jun 11 17:53:58 simon-watery kernel: [    1.634826] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jun 11 17:53:58 simon-watery kernel: [    1.635046] Fixed MDIO Bus: probed
Jun 11 17:53:58 simon-watery kernel: [    1.635066] PPP generic driver version 2.4.2
Jun 11 17:53:58 simon-watery kernel: [    1.635083] tun: Universal TUN/TAP device driver, 1.6
Jun 11 17:53:58 simon-watery kernel: [    1.635085] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun 11 17:53:58 simon-watery kernel: [    1.635126] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 11 17:53:58 simon-watery kernel: [    1.635140] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 11 17:53:58 simon-watery kernel: [    1.635152] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    1.635154] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Jun 11 17:53:58 simon-watery kernel: [    1.635172] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jun 11 17:53:58 simon-watery kernel: [    1.635194] ehci_hcd 0000:00:1a.0: debug port 2
Jun 11 17:53:58 simon-watery kernel: [    1.639064] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
Jun 11 17:53:58 simon-watery kernel: [    1.639076] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7ffe000
Jun 11 17:53:58 simon-watery kernel: [    1.651546] Freeing initrd memory: 8134k freed
Jun 11 17:53:58 simon-watery kernel: [    1.660935] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Jun 11 17:53:58 simon-watery kernel: [    1.661033] usb usb1: configuration #1 chosen from 1 choice
Jun 11 17:53:58 simon-watery kernel: [    1.661052] hub 1-0:1.0: USB hub found
Jun 11 17:53:58 simon-watery kernel: [    1.661057] hub 1-0:1.0: 2 ports detected
Jun 11 17:53:58 simon-watery kernel: [    1.661093]   alloc irq_desc for 23 on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.661094]   alloc kstat_irqs on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.661099] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 11 17:53:58 simon-watery kernel: [    1.661113] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    1.661116] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Jun 11 17:53:58 simon-watery kernel: [    1.661139] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jun 11 17:53:58 simon-watery kernel: [    1.661159] ehci_hcd 0000:00:1d.0: debug port 2
Jun 11 17:53:58 simon-watery kernel: [    1.665032] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
Jun 11 17:53:58 simon-watery kernel: [    1.665043] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7ffd000
Jun 11 17:53:58 simon-watery kernel: [    1.690919] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Jun 11 17:53:58 simon-watery kernel: [    1.691002] usb usb2: configuration #1 chosen from 1 choice
Jun 11 17:53:58 simon-watery kernel: [    1.691017] hub 2-0:1.0: USB hub found
Jun 11 17:53:58 simon-watery kernel: [    1.691020] hub 2-0:1.0: 2 ports detected
Jun 11 17:53:58 simon-watery kernel: [    1.691051] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 11 17:53:58 simon-watery kernel: [    1.691059] uhci_hcd: USB Universal Host Controller Interface driver
Jun 11 17:53:58 simon-watery kernel: [    1.691108] PNP: No PS/2 controller found. Probing ports directly.
Jun 11 17:53:58 simon-watery kernel: [    1.692573] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 11 17:53:58 simon-watery kernel: [    1.692577] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 11 17:53:58 simon-watery kernel: [    1.692624] mice: PS/2 mouse device common for all mice
Jun 11 17:53:58 simon-watery kernel: [    1.692680] rtc_cmos 00:03: RTC can wake from S4
Jun 11 17:53:58 simon-watery kernel: [    1.692704] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jun 11 17:53:58 simon-watery kernel: [    1.692727] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jun 11 17:53:58 simon-watery kernel: [    1.692805] device-mapper: uevent: version 1.0.3
Jun 11 17:53:58 simon-watery kernel: [    1.692868] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jun 11 17:53:58 simon-watery kernel: [    1.692955] device-mapper: multipath: version 1.1.0 loaded
Jun 11 17:53:58 simon-watery kernel: [    1.692957] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun 11 17:53:58 simon-watery kernel: [    1.693279] cpuidle: using governor ladder
Jun 11 17:53:58 simon-watery kernel: [    1.693509] cpuidle: using governor menu
Jun 11 17:53:58 simon-watery kernel: [    1.693748] TCP cubic registered
Jun 11 17:53:58 simon-watery kernel: [    1.693824] NET: Registered protocol family 10
Jun 11 17:53:58 simon-watery kernel: [    1.694149] lo: Disabled Privacy Extensions
Jun 11 17:53:58 simon-watery kernel: [    1.694331] NET: Registered protocol family 17
Jun 11 17:53:58 simon-watery kernel: [    1.694361] ------------[ cut here ]------------
Jun 11 17:53:58 simon-watery kernel: [    1.694367] WARNING: at /build/buildd/linux-2.6.32/arch/x86/kernel/hpet.c:392 hpet_next_event+0x7a/0x90()
Jun 11 17:53:58 simon-watery kernel: [    1.694368] Hardware name: System Product Name
Jun 11 17:53:58 simon-watery kernel: [    1.694370] Modules linked in:
Jun 11 17:53:58 simon-watery kernel: [    1.694372] Pid: 0, comm: swapper Not tainted 2.6.32-22-generic #36-Ubuntu
Jun 11 17:53:58 simon-watery kernel: [    1.694373] Call Trace:
Jun 11 17:53:58 simon-watery kernel: [    1.694378]  [<ffffffff81066d0b>] warn_slowpath_common+0x7b/0xc0
Jun 11 17:53:58 simon-watery kernel: [    1.694380]  [<ffffffff81066d64>] warn_slowpath_null+0x14/0x20
Jun 11 17:53:58 simon-watery kernel: [    1.694382]  [<ffffffff810375ca>] hpet_next_event+0x7a/0x90
Jun 11 17:53:58 simon-watery kernel: [    1.694384]  [<ffffffff81037610>] hpet_legacy_next_event+0x10/0x20
Jun 11 17:53:58 simon-watery kernel: [    1.694388]  [<ffffffff81092e24>] clockevents_program_event+0x54/0xa0
Jun 11 17:53:58 simon-watery kernel: [    1.694390]  [<ffffffff81094378>] tick_dev_program_event+0x68/0xd0
Jun 11 17:53:58 simon-watery kernel: [    1.694393]  [<ffffffff81093cae>] tick_broadcast_oneshot_control+0x11e/0x120
Jun 11 17:53:58 simon-watery kernel: [    1.694395]  [<ffffffff810934c0>] tick_notify+0x130/0x200
Jun 11 17:53:58 simon-watery kernel: [    1.694399]  [<ffffffff81543b46>] notifier_call_chain+0x56/0x80
Jun 11 17:53:58 simon-watery kernel: [    1.694401]  [<ffffffff8108a366>] raw_notifier_call_chain+0x16/0x20
Jun 11 17:53:58 simon-watery kernel: [    1.694404]  [<ffffffff81092c47>] clockevents_notify+0x37/0x160
Jun 11 17:53:58 simon-watery kernel: [    1.694407]  [<ffffffff8130ccd5>] lapic_timer_state_broadcast+0x46/0x48
Jun 11 17:53:58 simon-watery kernel: [    1.694409]  [<ffffffff8130d244>] acpi_idle_enter_bm+0x187/0x2be
Jun 11 17:53:58 simon-watery kernel: [    1.694411]  [<ffffffff81543b06>] ? notifier_call_chain+0x16/0x80
Jun 11 17:53:58 simon-watery kernel: [    1.694414]  [<ffffffff81437537>] cpuidle_idle_call+0xa7/0x140
Jun 11 17:53:58 simon-watery kernel: [    1.694418]  [<ffffffff81011e73>] cpu_idle+0xb3/0x110
Jun 11 17:53:58 simon-watery kernel: [    1.694420]  [<ffffffff8153ad7b>] start_secondary+0xa8/0xaa
Jun 11 17:53:58 simon-watery kernel: [    1.694423] ---[ end trace 3bd3e2b4cadc7f72 ]---
Jun 11 17:53:58 simon-watery kernel: [    1.697055] PM: Resume from disk failed.
Jun 11 17:53:58 simon-watery kernel: [    1.697061] registered taskstats version 1
Jun 11 17:53:58 simon-watery kernel: [    1.697341]   Magic number: 14:860:893
Jun 11 17:53:58 simon-watery kernel: [    1.697474] rtc_cmos 00:03: setting system clock to 2010-06-11 16:53:45 UTC (1276275225)
Jun 11 17:53:58 simon-watery kernel: [    1.697479] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 11 17:53:58 simon-watery kernel: [    1.697482] EDD information not available.
Jun 11 17:53:58 simon-watery kernel: [    1.697518] Freeing unused kernel memory: 876k freed
Jun 11 17:53:58 simon-watery kernel: [    1.697623] Write protecting the kernel read-only data: 7680k
Jun 11 17:53:58 simon-watery kernel: [    1.711822] udev: starting version 151
Jun 11 17:53:58 simon-watery kernel: [    1.727470] ahci 0000:00:1f.2: version 3.0
Jun 11 17:53:58 simon-watery kernel: [    1.727484]   alloc irq_desc for 21 on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.727486]   alloc kstat_irqs on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.727492] ahci 0000:00:1f.2: PCI INT D -> GSI 21 (level, low) -> IRQ 21
Jun 11 17:53:58 simon-watery kernel: [    1.727528]   alloc irq_desc for 35 on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.727530]   alloc kstat_irqs on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.727537] ahci 0000:00:1f.2: irq 35 for MSI/MSI-X
Jun 11 17:53:58 simon-watery kernel: [    1.727568] ahci: SSS flag set, parallel bus scan disabled
Jun 11 17:53:58 simon-watery kernel: [    1.739281] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jun 11 17:53:58 simon-watery kernel: [    1.739295]   alloc irq_desc for 22 on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.739296]   alloc kstat_irqs on node -1
Jun 11 17:53:58 simon-watery kernel: [    1.739300] r8169 0000:07:04.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun 11 17:53:58 simon-watery kernel: [    1.739419] r8169 0000:07:04.0: no PCI Express capability
Jun 11 17:53:58 simon-watery kernel: [    1.739748] eth0: RTL8169sc/8110sc at 0xffffc90000c76400, 90:e6:ba:00:b7:62, XID 18000000 IRQ 22
Jun 11 17:53:58 simon-watery kernel: [    1.740810] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Jun 11 17:53:58 simon-watery kernel: [    1.740812] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems sxs apst 
Jun 11 17:53:58 simon-watery kernel: [    1.740816] ahci 0000:00:1f.2: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    1.743868] ohci1394 0000:07:03.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 11 17:53:58 simon-watery kernel: [    1.802487] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[fbeff800-fbefffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jun 11 17:53:58 simon-watery kernel: [    1.841012] scsi0 : ahci
Jun 11 17:53:58 simon-watery kernel: [    1.841264] scsi1 : ahci
Jun 11 17:53:58 simon-watery kernel: [    1.841523] scsi2 : ahci
Jun 11 17:53:58 simon-watery kernel: [    1.841815] scsi3 : ahci
Jun 11 17:53:58 simon-watery kernel: [    1.842119] scsi4 : ahci
Jun 11 17:53:58 simon-watery kernel: [    1.842363] scsi5 : ahci
Jun 11 17:53:58 simon-watery kernel: [    1.842559] ata1: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7100 irq 35
Jun 11 17:53:58 simon-watery kernel: [    1.842561] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 35
Jun 11 17:53:58 simon-watery kernel: [    1.842563] ata3: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7200 irq 35
Jun 11 17:53:58 simon-watery kernel: [    1.842565] ata4: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7280 irq 35
Jun 11 17:53:58 simon-watery kernel: [    1.842567] ata5: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7300 irq 35
Jun 11 17:53:58 simon-watery kernel: [    1.842569] ata6: SATA max UDMA/133 irq_stat 0x00400040, connection status changed
Jun 11 17:53:58 simon-watery kernel: [    1.978885] usb 1-1: new high speed USB device using ehci_hcd and address 2
Jun 11 17:53:58 simon-watery kernel: [    2.129760] usb 1-1: configuration #1 chosen from 1 choice
Jun 11 17:53:58 simon-watery kernel: [    2.130005] hub 1-1:1.0: USB hub found
Jun 11 17:53:58 simon-watery kernel: [    2.130195] hub 1-1:1.0: 6 ports detected
Jun 11 17:53:58 simon-watery kernel: [    2.248781] usb 2-1: new high speed USB device using ehci_hcd and address 2
Jun 11 17:53:58 simon-watery kernel: [    2.370641] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 11 17:53:58 simon-watery kernel: [    2.371141] ata1.00: ATA-7: INTEL SSDSA2M080G2GC, 2CV102HD, max UDMA/133
Jun 11 17:53:58 simon-watery kernel: [    2.371146] ata1.00: 156301488 sectors, multi 1: LBA48 NCQ (depth 31/32)
Jun 11 17:53:58 simon-watery kernel: [    2.371727] ata1.00: configured for UDMA/133
Jun 11 17:53:58 simon-watery kernel: [    2.390747] scsi 0:0:0:0: Direct-Access     ATA      INTEL SSDSA2M080 2CV1 PQ: 0 ANSI: 5
Jun 11 17:53:58 simon-watery kernel: [    2.390852] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 11 17:53:58 simon-watery kernel: [    2.390908] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Jun 11 17:53:58 simon-watery kernel: [    2.390935] sd 0:0:0:0: [sda] Write Protect is off
Jun 11 17:53:58 simon-watery kernel: [    2.390936] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 11 17:53:58 simon-watery kernel: [    2.390948] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 11 17:53:58 simon-watery kernel: [    2.391019]  sda: sda1
Jun 11 17:53:58 simon-watery kernel: [    2.391675] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 11 17:53:58 simon-watery kernel: [    2.409270] usb 2-1: configuration #1 chosen from 1 choice
Jun 11 17:53:58 simon-watery kernel: [    2.409477] hub 2-1:1.0: USB hub found
Jun 11 17:53:58 simon-watery kernel: [    2.409545] hub 2-1:1.0: 8 ports detected
Jun 11 17:53:58 simon-watery kernel: [    2.688990] usb 2-1.3: new high speed USB device using ehci_hcd and address 3
Jun 11 17:53:58 simon-watery kernel: [    2.799178] usb 2-1.3: configuration #1 chosen from 1 choice
Jun 11 17:53:58 simon-watery kernel: [    2.799404] hub 2-1.3:1.0: USB hub found
Jun 11 17:53:58 simon-watery kernel: [    2.799567] hub 2-1.3:1.0: 2 ports detected
Jun 11 17:53:58 simon-watery kernel: [    2.878812] usb 2-1.4: new low speed USB device using ehci_hcd and address 4
Jun 11 17:53:58 simon-watery kernel: [    3.027284] usb 2-1.4: configuration #1 chosen from 1 choice
Jun 11 17:53:58 simon-watery kernel: [    3.108834] usb 2-1.7: new high speed USB device using ehci_hcd and address 5
Jun 11 17:53:58 simon-watery kernel: [    3.118814] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0000a2df9b]
Jun 11 17:53:58 simon-watery kernel: [    3.230585] usb 2-1.7: configuration #1 chosen from 1 choice
Jun 11 17:53:58 simon-watery kernel: [    3.230898] hub 2-1.7:1.0: USB hub found
Jun 11 17:53:58 simon-watery kernel: [    3.231195] hub 2-1.7:1.0: 4 ports detected
Jun 11 17:53:58 simon-watery kernel: [    3.308835] usb 2-1.8: new low speed USB device using ehci_hcd and address 6
Jun 11 17:53:58 simon-watery kernel: [    3.320285] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 11 17:53:58 simon-watery kernel: [    3.341258] ata2.00: ATA-8: SAMSUNG HD501LJ, CR100-13, max UDMA7
Jun 11 17:53:58 simon-watery kernel: [    3.341263] ata2.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Jun 11 17:53:58 simon-watery kernel: [    3.343764] ata2.00: configured for UDMA/133
Jun 11 17:53:58 simon-watery kernel: [    3.360362] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
Jun 11 17:53:58 simon-watery kernel: [    3.360427] sd 1:0:0:0: Attached scsi generic sg1 type 0
Jun 11 17:53:58 simon-watery kernel: [    3.360463] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jun 11 17:53:58 simon-watery kernel: [    3.360484] sd 1:0:0:0: [sdb] Write Protect is off
Jun 11 17:53:58 simon-watery kernel: [    3.360486] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jun 11 17:53:58 simon-watery kernel: [    3.360497] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 11 17:53:58 simon-watery kernel: [    3.360563]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 >
Jun 11 17:53:58 simon-watery kernel: [    3.411405] sd 1:0:0:0: [sdb] Attached SCSI disk
Jun 11 17:53:58 simon-watery kernel: [    3.446916] usb 2-1.8: configuration #1 chosen from 1 choice
Jun 11 17:53:58 simon-watery kernel: [    3.451290] usbcore: registered new interface driver hiddev
Jun 11 17:53:58 simon-watery kernel: [    3.528838] usb 2-1.3.1: new high speed USB device using ehci_hcd and address 7
Jun 11 17:53:58 simon-watery kernel: [    3.639028] usb 2-1.3.1: configuration #1 chosen from 1 choice
Jun 11 17:53:58 simon-watery kernel: [    3.639240] hub 2-1.3.1:1.0: USB hub found
Jun 11 17:53:58 simon-watery kernel: [    3.639297] hub 2-1.3.1:1.0: 4 ports detected
Jun 11 17:53:58 simon-watery kernel: [    3.720526] ata3: SATA link down (SStatus 0 SControl 300)
Jun 11 17:53:58 simon-watery kernel: [    3.721821] usb 2-1.3.2: new high speed USB device using ehci_hcd and address 8
Jun 11 17:53:58 simon-watery kernel: [    3.759758] generic-usb 0003:051D:0002.0001: hiddev96,hidraw0: USB HID v1.10 Device [American Power Conversion Back-UPS BR  800 FW:9.o4 .I USB FW:o4 ] on usb-0000:00:1d.0-1.4/input0
Jun 11 17:53:58 simon-watery kernel: [    3.769423] input: daskeyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.0/input/input3
Jun 11 17:53:58 simon-watery kernel: [    3.769463] generic-usb 0003:04D9:2013.0002: input,hidraw1: USB HID v1.10 Keyboard [daskeyboard] on usb-0000:00:1d.0-1.8/input0
Jun 11 17:53:58 simon-watery kernel: [    3.792398] input: daskeyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.1/input/input4
Jun 11 17:53:58 simon-watery kernel: [    3.792440] generic-usb 0003:04D9:2013.0003: input,hidraw2: USB HID v1.10 Device [daskeyboard] on usb-0000:00:1d.0-1.8/input1
Jun 11 17:53:58 simon-watery kernel: [    3.792450] usbcore: registered new interface driver usbhid
Jun 11 17:53:58 simon-watery kernel: [    3.792451] usbhid: v2.6:USB HID core driver
Jun 11 17:53:58 simon-watery kernel: [    3.918411] usb 2-1.3.2: configuration #1 chosen from 1 choice
Jun 11 17:53:58 simon-watery kernel: [    3.923006] Initializing USB Mass Storage driver...
Jun 11 17:53:58 simon-watery kernel: [    3.923479] scsi6 : SCSI emulation for USB Mass Storage devices
Jun 11 17:53:58 simon-watery kernel: [    3.923845] usbcore: registered new interface driver usb-storage
Jun 11 17:53:58 simon-watery kernel: [    3.923850] usb-storage: device found at 8
Jun 11 17:53:58 simon-watery kernel: [    3.923855] usb-storage: waiting for device to settle before scanning
Jun 11 17:53:58 simon-watery kernel: [    3.923920] USB Mass Storage support registered.
Jun 11 17:53:58 simon-watery kernel: [    3.998829] usb 2-1.3.1.1: new low speed USB device using ehci_hcd and address 9
Jun 11 17:53:58 simon-watery kernel: [    4.078617] ata4: SATA link down (SStatus 0 SControl 300)
Jun 11 17:53:58 simon-watery kernel: [    4.123533] usb 2-1.3.1.1: configuration #1 chosen from 1 choice
Jun 11 17:53:58 simon-watery kernel: [    4.125986] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.1/2-1.3.1.1/2-1.3.1.1:1.0/input/input5
Jun 11 17:53:58 simon-watery kernel: [    4.126034] generic-usb 0003:045E:0040.0004: input,hidraw3: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-1.3.1.1/input0
Jun 11 17:53:58 simon-watery kernel: [    4.450535] ata5: SATA link down (SStatus 0 SControl 300)
Jun 11 17:53:58 simon-watery kernel: [    5.398590] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 11 17:53:58 simon-watery kernel: [    5.401654] ata6.00: ATAPI: PIONEER BD-ROM  BDC-202, 1.01, max UDMA/66
Jun 11 17:53:58 simon-watery kernel: [    5.404915] ata6.00: configured for UDMA/66
Jun 11 17:53:58 simon-watery kernel: [    5.435666] scsi 5:0:0:0: CD-ROM            PIONEER  BD-ROM  BDC-202  1.01 PQ: 0 ANSI: 5
Jun 11 17:53:58 simon-watery kernel: [    5.455281] sr0: scsi3-mmc drive: 32x/32x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 11 17:53:58 simon-watery kernel: [    5.455286] Uniform CD-ROM driver Revision: 3.20
Jun 11 17:53:58 simon-watery kernel: [    5.455407] sr 5:0:0:0: Attached scsi CD-ROM sr0
Jun 11 17:53:58 simon-watery kernel: [    5.455457] sr 5:0:0:0: Attached scsi generic sg2 type 5
Jun 11 17:53:58 simon-watery kernel: [    5.574024] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jun 11 17:53:58 simon-watery kernel: [    5.722185] udev: starting version 151
Jun 11 17:53:58 simon-watery kernel: [    5.740614] Adding 15998968k swap on /dev/sdb1.  Priority:-1 extents:1 across:15998968k 
Jun 11 17:53:58 simon-watery kernel: [    5.752848] vga16fb: initializing
Jun 11 17:53:58 simon-watery kernel: [    5.752851] vga16fb: mapped to 0xffff8800000a0000
Jun 11 17:53:58 simon-watery kernel: [    5.752893] fb0: VGA16 VGA frame buffer device
Jun 11 17:53:58 simon-watery kernel: [    5.782924] lp: driver loaded but no devices found
Jun 11 17:53:58 simon-watery kernel: [    5.829483] nvidia: module license 'NVIDIA' taints kernel.
Jun 11 17:53:58 simon-watery kernel: [    5.829485] Disabling lock debugging due to kernel taint
Jun 11 17:53:58 simon-watery kernel: [    5.871070] type=1505 audit(1276275229.671:2):  operation="profile_load" pid=751 name="/sbin/dhclient3"
Jun 11 17:53:58 simon-watery kernel: [    5.871428] type=1505 audit(1276275229.671:3):  operation="profile_load" pid=751 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jun 11 17:53:58 simon-watery kernel: [    5.871601] type=1505 audit(1276275229.671:4):  operation="profile_load" pid=751 name="/usr/lib/connman/scripts/dhclient-script"
Jun 11 17:53:58 simon-watery kernel: [    5.873186] type=1505 audit(1276275229.671:5):  operation="profile_load" pid=807 name="/usr/sbin/ntpd"
Jun 11 17:53:58 simon-watery kernel: [    6.103067] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun 11 17:53:58 simon-watery kernel: [    6.103103] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    6.249651] Console: switching to colour frame buffer device 80x30
Jun 11 17:53:58 simon-watery kernel: [    6.295130] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 11 17:53:58 simon-watery kernel: [    6.295136] nvidia 0000:01:00.0: setting latency timer to 64
Jun 11 17:53:58 simon-watery kernel: [    6.295139] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jun 11 17:53:58 simon-watery kernel: [    6.295403] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.15  Fri Mar 12 00:29:13 PST 2010
Jun 11 17:53:58 simon-watery kernel: [    8.926067] usb-storage: device scan complete
Jun 11 17:53:58 simon-watery kernel: [    8.929570] scsi 6:0:0:0: Direct-Access     SMSC     223 U HS-CF      3.60 PQ: 0 ANSI: 0
Jun 11 17:53:58 simon-watery kernel: [    8.932886] scsi 6:0:0:1: Direct-Access     SMSC     223 U HS-MS      3.60 PQ: 0 ANSI: 0
Jun 11 17:53:58 simon-watery kernel: [    8.936249] scsi 6:0:0:2: Direct-Access     SMSC     223 U HS-SM      3.60 PQ: 0 ANSI: 0
Jun 11 17:53:58 simon-watery kernel: [    8.939257] scsi 6:0:0:3: Direct-Access     SMSC     223 U HS-SD/MMC  3.60 PQ: 0 ANSI: 0
Jun 11 17:53:58 simon-watery kernel: [    8.939561] sd 6:0:0:0: Attached scsi generic sg3 type 0
Jun 11 17:53:58 simon-watery kernel: [    8.939626] sd 6:0:0:1: Attached scsi generic sg4 type 0
Jun 11 17:53:58 simon-watery kernel: [    8.939687] sd 6:0:0:2: Attached scsi generic sg5 type 0
Jun 11 17:53:58 simon-watery kernel: [    8.939750] sd 6:0:0:3: Attached scsi generic sg6 type 0
Jun 11 17:53:58 simon-watery kernel: [    9.055046] sd 6:0:0:1: [sdd] Attached SCSI removable disk
Jun 11 17:53:58 simon-watery kernel: [    9.076933] sd 6:0:0:3: [sdf] Attached SCSI removable disk
Jun 11 17:53:58 simon-watery kernel: [    9.105557] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Jun 11 17:53:58 simon-watery kernel: [    9.131079] sd 6:0:0:2: [sde] Attached SCSI removable disk
Jun 11 17:53:58 simon-watery kernel: [   10.248435] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input6
Jun 11 17:53:58 simon-watery kernel: [   14.314791] EXT4-fs (sdb6): mounted filesystem with ordered data mode
Jun 11 17:53:58 simon-watery kernel: [   14.411118] EXT4-fs (sdb7): mounted filesystem with ordered data mode
Jun 11 17:53:58 simon-watery kernel: [   14.415973] EXT4-fs (sdb5): mounted filesystem with ordered data mode
Jun 11 17:53:58 simon-watery kernel: [   14.462107] type=1505 audit(1276275238.261:6):  operation="profile_load" pid=1156 name="/usr/share/gdm/guest-session/Xsession"
Jun 11 17:53:58 simon-watery kernel: [   14.463177] type=1505 audit(1276275238.261:7):  operation="profile_replace" pid=1157 name="/sbin/dhclient3"
Jun 11 17:53:58 simon-watery kernel: [   14.463468] type=1505 audit(1276275238.261:8):  operation="profile_replace" pid=1157 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jun 11 17:53:58 simon-watery kernel: [   14.463626] type=1505 audit(1276275238.261:9):  operation="profile_replace" pid=1157 name="/usr/lib/connman/scripts/dhclient-script"
Jun 11 17:53:58 simon-watery kernel: [   14.468084] type=1505 audit(1276275238.271:10):  operation="profile_load" pid=1158 name="/usr/bin/evince"
Jun 11 17:53:58 simon-watery kernel: [   14.472106] type=1505 audit(1276275238.271:11):  operation="profile_load" pid=1158 name="/usr/bin/evince-previewer"
Jun 11 17:53:58 simon-watery kernel: [   14.474567] type=1505 audit(1276275238.271:12):  operation="profile_load" pid=1158 name="/usr/bin/evince-thumbnailer"
Jun 11 17:53:58 simon-watery kernel: [   14.479428] type=1505 audit(1276275238.281:13):  operation="profile_load" pid=1160 name="/usr/lib/cups/backend/cups-pdf"
Jun 11 17:53:58 simon-watery kernel: [   14.479854] type=1505 audit(1276275238.281:14):  operation="profile_load" pid=1160 name="/usr/sbin/cupsd"
Jun 11 17:53:58 simon-watery kernel: [   14.481178] type=1505 audit(1276275238.281:15):  operation="profile_replace" pid=1162 name="/usr/sbin/ntpd"
Jun 11 17:53:58 simon-watery NetworkManager:    SCPlugin-Ifupdown: init!
Jun 11 17:53:58 simon-watery NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Jun 11 17:53:58 simon-watery NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Jun 11 17:53:58 simon-watery gdm-binary[1185]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jun 11 17:53:58 simon-watery NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:07:04.0/net/eth0, iface: eth0)
Jun 11 17:53:58 simon-watery NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:07:04.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 11 17:53:58 simon-watery NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 11 17:53:58 simon-watery NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 11 17:53:58 simon-watery NetworkManager:    SCPlugin-Ifupdown: end _init.
Jun 11 17:53:58 simon-watery NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 11 17:53:58 simon-watery NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 11 17:53:58 simon-watery NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Jun 11 17:53:58 simon-watery NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Jun 11 17:53:58 simon-watery NetworkManager:    SCPlugin-Ifupdown: (21608736) ... get_connections.
Jun 11 17:53:58 simon-watery NetworkManager:    SCPlugin-Ifupdown: (21608736) ... get_connections (managed=false): return empty list.
Jun 11 17:53:58 simon-watery modem-manager: Loaded plugin Generic
Jun 11 17:53:58 simon-watery modem-manager: Loaded plugin ZTE
Jun 11 17:53:58 simon-watery modem-manager: Loaded plugin Huawei
Jun 11 17:53:58 simon-watery modem-manager: Loaded plugin Novatel
Jun 11 17:53:58 simon-watery modem-manager: Loaded plugin Longcheer
Jun 11 17:53:58 simon-watery modem-manager: Loaded plugin Sierra
Jun 11 17:53:58 simon-watery modem-manager: Loaded plugin Gobi
Jun 11 17:53:58 simon-watery modem-manager: Loaded plugin Nokia
Jun 11 17:53:58 simon-watery modem-manager: Loaded plugin Option
Jun 11 17:53:58 simon-watery modem-manager: Loaded plugin MotoC
Jun 11 17:53:58 simon-watery modem-manager: Loaded plugin AnyData
Jun 11 17:53:58 simon-watery modem-manager: Loaded plugin Ericsson MBM
Jun 11 17:53:58 simon-watery NetworkManager:    Ifupdown: get unmanaged devices count: 0
Jun 11 17:53:58 simon-watery modem-manager: Loaded plugin Option High-Speed
Jun 11 17:53:58 simon-watery NetworkManager: <info>  (eth0): carrier is OFF
Jun 11 17:53:58 simon-watery NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Jun 11 17:53:58 simon-watery NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 11 17:53:58 simon-watery NetworkManager: <info>  (eth0): now managed
Jun 11 17:53:58 simon-watery NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jun 11 17:53:58 simon-watery NetworkManager: <info>  (eth0): bringing up device.
Jun 11 17:53:58 simon-watery NetworkManager: <info>  (eth0): preparing device.
Jun 11 17:53:58 simon-watery NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jun 11 17:53:58 simon-watery NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Jun 11 17:53:58 simon-watery NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Jun 11 17:53:58 simon-watery NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun 11 17:53:58 simon-watery NetworkManager: <info>  modem-manager is now available
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Trying to start the supplicant...
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jun 11 17:53:58 simon-watery NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun 11 17:53:58 simon-watery NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun 11 17:53:58 simon-watery NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jun 11 17:53:58 simon-watery NetworkManager: <info>  dhclient started with pid 1268
Jun 11 17:53:58 simon-watery kernel: [   14.622561] r8169: eth0: link up
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun 11 17:53:58 simon-watery dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jun 11 17:53:58 simon-watery dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jun 11 17:53:58 simon-watery dhclient: All rights reserved.
Jun 11 17:53:58 simon-watery dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun 11 17:53:58 simon-watery dhclient: 
Jun 11 17:53:58 simon-watery gdm-simple-slave[1263]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jun 11 17:53:58 simon-watery gdm-binary[1185]: WARNING: Unable to find users: no seat-id found
Jun 11 17:53:58 simon-watery NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Jun 11 17:53:58 simon-watery dhclient: Listening on LPF/eth0/90:e6:ba:00:b7:62
Jun 11 17:53:58 simon-watery dhclient: Sending on   LPF/eth0/90:e6:ba:00:b7:62
Jun 11 17:53:58 simon-watery dhclient: Sending on   Socket/fallback
Jun 11 17:53:58 simon-watery dhclient: DHCPREQUEST of 192.168.1.64 on eth0 to 255.255.255.255 port 67
Jun 11 17:53:58 simon-watery dhclient: DHCPACK of 192.168.1.64 from 192.168.1.254
Jun 11 17:53:58 simon-watery NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Jun 11 17:53:58 simon-watery dhclient: bound to 192.168.1.64 -- renewal in 37840 seconds.
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jun 11 17:53:58 simon-watery NetworkManager: <info>    address 192.168.1.64
Jun 11 17:53:58 simon-watery NetworkManager: <info>    prefix 24 (255.255.255.0)
Jun 11 17:53:58 simon-watery NetworkManager: <info>    gateway 192.168.1.254
Jun 11 17:53:58 simon-watery NetworkManager: <info>    nameserver '192.168.1.254'
Jun 11 17:53:58 simon-watery NetworkManager: <info>    domain name 'home'
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun 11 17:53:58 simon-watery NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jun 11 17:53:58 simon-watery avahi-daemon[1190]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.64.
Jun 11 17:53:58 simon-watery avahi-daemon[1190]: New relevant interface eth0.IPv4 for mDNS.
Jun 11 17:53:58 simon-watery avahi-daemon[1190]: Registering new address record for 192.168.1.64 on eth0.IPv4.
Jun 11 17:53:59 simon-watery NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jun 11 17:53:59 simon-watery NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jun 11 17:53:59 simon-watery NetworkManager: <info>  Activation (eth0) successful, device activated.
Jun 11 17:53:59 simon-watery NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jun 11 17:54:00 simon-watery ntpdate[1335]: adjust time server 130.88.200.4 offset -0.233672 sec
Jun 11 17:54:00 simon-watery avahi-daemon[1190]: Registering new address record for fe80::92e6:baff:fe00:b762 on eth0.*.
Jun 11 17:54:00 simon-watery ntpd[1362]: ntpd 4.2.4p8@1.1612-o Fri Apr  9 03:13:54 UTC 2010 (1)
Jun 11 17:54:00 simon-watery ntpd[1363]: precision = 1.000 usec
Jun 11 17:54:00 simon-watery ntpd[1363]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Jun 11 17:54:00 simon-watery ntpd[1363]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jun 11 17:54:00 simon-watery ntpd[1363]: Listening on interface #1 wildcard, ::#123 Disabled
Jun 11 17:54:00 simon-watery ntpd[1363]: Listening on interface #2 lo, ::1#123 Enabled
Jun 11 17:54:00 simon-watery ntpd[1363]: Listening on interface #3 eth0, fe80::92e6:baff:fe00:b762#123 Enabled
Jun 11 17:54:00 simon-watery ntpd[1363]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Jun 11 17:54:00 simon-watery ntpd[1363]: Listening on interface #5 eth0, 192.168.1.64#123 Enabled
Jun 11 17:54:00 simon-watery ntpd[1363]: kernel time sync status 2040
Jun 11 17:54:00 simon-watery ntpd[1363]: frequency initialized -77.507 PPM from /var/lib/ntp/ntp.drift
Jun 11 17:54:00 simon-watery init: apport pre-start process (1395) terminated with status 1
Jun 11 17:54:00 simon-watery cron[1400]: (CRON) INFO (pidfile fd = 3)
Jun 11 17:54:00 simon-watery anacron[1411]: Anacron 2.3 started on 2010-06-11
Jun 11 17:54:00 simon-watery acpid: starting up with proc fs
Jun 11 17:54:00 simon-watery cron[1414]: (CRON) STARTUP (fork ok)
Jun 11 17:54:00 simon-watery init: apport post-stop process (1412) terminated with status 1
Jun 11 17:54:00 simon-watery cron[1414]: (CRON) INFO (Running @reboot jobs)
Jun 11 17:54:00 simon-watery acpid: 36 rules loaded
Jun 11 17:54:00 simon-watery acpid: waiting for events: event logging is off
Jun 11 17:54:00 simon-watery anacron[1411]: Will run job `cron.daily' in 5 min.
Jun 11 17:54:00 simon-watery anacron[1411]: Jobs will be executed sequentially
Jun 11 17:54:00 simon-watery kernel: [   16.772015] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Jun 11 17:54:00 simon-watery kernel: [   16.772017] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
Jun 11 17:54:00 simon-watery kernel: [   16.772018] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
Jun 11 17:54:00 simon-watery kernel: [   16.772018] vboxdrv: the usage of hardware performance counters by
Jun 11 17:54:00 simon-watery kernel: [   16.772019] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
Jun 11 17:54:00 simon-watery kernel: [   16.772021] vboxdrv: Found 8 processor cores.
Jun 11 17:54:00 simon-watery kernel: [   16.772059] VBoxDrv: dbg - g_abExecMemory=ffffffffa0d0fa20
Jun 11 17:54:00 simon-watery kernel: [   16.772278] vboxdrv: fAsync=0 offMin=0x2a1 offMax=0x47747
Jun 11 17:54:00 simon-watery kernel: [   16.772302] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jun 11 17:54:00 simon-watery kernel: [   16.772303] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
Jun 11 17:54:00 simon-watery NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Jun 11 17:54:00 simon-watery NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
Jun 11 17:54:00 simon-watery NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
Jun 11 17:54:00 simon-watery kernel: [   16.925167] ppdev: user-space parallel port driver
Jun 11 17:54:00 simon-watery acpid: client connected from 1275[0:0]
Jun 11 17:54:00 simon-watery acpid: 1 client rule loaded
Jun 11 17:54:00 simon-watery kernel: [   17.164002] CPU0 attaching NULL sched-domain.
Jun 11 17:54:00 simon-watery kernel: [   17.164005] CPU1 attaching NULL sched-domain.
Jun 11 17:54:00 simon-watery kernel: [   17.164007] CPU2 attaching NULL sched-domain.
Jun 11 17:54:00 simon-watery kernel: [   17.164008] CPU3 attaching NULL sched-domain.
Jun 11 17:54:00 simon-watery kernel: [   17.164010] CPU4 attaching NULL sched-domain.
Jun 11 17:54:00 simon-watery kernel: [   17.164011] CPU5 attaching NULL sched-domain.
Jun 11 17:54:00 simon-watery kernel: [   17.164012] CPU6 attaching NULL sched-domain.
Jun 11 17:54:00 simon-watery kernel: [   17.164013] CPU7 attaching NULL sched-domain.
Jun 11 17:54:01 simon-watery kernel: [   17.279644] CPU0 attaching sched-domain:
Jun 11 17:54:01 simon-watery kernel: [   17.279646]  domain 0: span 0,4 level SIBLING
Jun 11 17:54:01 simon-watery kernel: [   17.279647]   groups: 0 (cpu_power = 589) 4 (cpu_power = 589)
Jun 11 17:54:01 simon-watery kernel: [   17.279650]   domain 1: span 0-7 level MC
Jun 11 17:54:01 simon-watery kernel: [   17.279651]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun 11 17:54:01 simon-watery kernel: [   17.279657] CPU1 attaching sched-domain:
Jun 11 17:54:01 simon-watery kernel: [   17.279658]  domain 0: span 1,5 level SIBLING
Jun 11 17:54:01 simon-watery kernel: [   17.279659]   groups: 1 (cpu_power = 589) 5 (cpu_power = 589)
Jun 11 17:54:01 simon-watery kernel: [   17.279661]   domain 1: span 0-7 level MC
Jun 11 17:54:01 simon-watery kernel: [   17.279662]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun 11 17:54:01 simon-watery kernel: [   17.279667] CPU2 attaching sched-domain:
Jun 11 17:54:01 simon-watery kernel: [   17.279668]  domain 0: span 2,6 level SIBLING
Jun 11 17:54:01 simon-watery kernel: [   17.279669]   groups: 2 (cpu_power = 589) 6 (cpu_power = 589)
Jun 11 17:54:01 simon-watery kernel: [   17.279671]   domain 1: span 0-7 level MC
Jun 11 17:54:01 simon-watery kernel: [   17.279672]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun 11 17:54:01 simon-watery kernel: [   17.279676] CPU3 attaching sched-domain:
Jun 11 17:54:01 simon-watery kernel: [   17.279677]  domain 0: span 3,7 level SIBLING
Jun 11 17:54:01 simon-watery kernel: [   17.279678]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
Jun 11 17:54:01 simon-watery kernel: [   17.279681]   domain 1: span 0-7 level MC
Jun 11 17:54:01 simon-watery kernel: [   17.279682]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun 11 17:54:01 simon-watery kernel: [   17.279686] CPU4 attaching sched-domain:
Jun 11 17:54:01 simon-watery kernel: [   17.279687]  domain 0: span 0,4 level SIBLING
Jun 11 17:54:01 simon-watery kernel: [   17.279688]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
Jun 11 17:54:01 simon-watery kernel: [   17.279691]   domain 1: span 0-7 level MC
Jun 11 17:54:01 simon-watery kernel: [   17.279692]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun 11 17:54:01 simon-watery kernel: [   17.279696] CPU5 attaching sched-domain:
Jun 11 17:54:01 simon-watery kernel: [   17.279697]  domain 0: span 1,5 level SIBLING
Jun 11 17:54:01 simon-watery kernel: [   17.279698]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
Jun 11 17:54:01 simon-watery kernel: [   17.279700]   domain 1: span 0-7 level MC
Jun 11 17:54:01 simon-watery kernel: [   17.279701]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun 11 17:54:01 simon-watery kernel: [   17.279706] CPU6 attaching sched-domain:
Jun 11 17:54:01 simon-watery kernel: [   17.279707]  domain 0: span 2,6 level SIBLING
Jun 11 17:54:01 simon-watery kernel: [   17.279708]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
Jun 11 17:54:01 simon-watery kernel: [   17.279710]   domain 1: span 0-7 level MC
Jun 11 17:54:01 simon-watery kernel: [   17.279711]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun 11 17:54:01 simon-watery kernel: [   17.279718] CPU7 attaching sched-domain:
Jun 11 17:54:01 simon-watery kernel: [   17.279719]  domain 0: span 3,7 level SIBLING
Jun 11 17:54:01 simon-watery kernel: [   17.279721]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
Jun 11 17:54:01 simon-watery kernel: [   17.279723]   domain 1: span 0-7 level MC
Jun 11 17:54:01 simon-watery kernel: [   17.279724]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun 11 17:54:01 simon-watery kernel: [   17.280278] CPU0 attaching NULL sched-domain.
Jun 11 17:54:01 simon-watery kernel: [   17.280280] CPU1 attaching NULL sched-domain.
Jun 11 17:54:01 simon-watery kernel: [   17.280281] CPU2 attaching NULL sched-domain.
Jun 11 17:54:01 simon-watery kernel: [   17.280282] CPU3 attaching NULL sched-domain.
Jun 11 17:54:01 simon-watery kernel: [   17.280283] CPU4 attaching NULL sched-domain.
Jun 11 17:54:01 simon-watery kernel: [   17.280284] CPU5 attaching NULL sched-domain.
Jun 11 17:54:01 simon-watery kernel: [   17.280285] CPU6 attaching NULL sched-domain.
Jun 11 17:54:01 simon-watery kernel: [   17.280286] CPU7 attaching NULL sched-domain.
Jun 11 17:54:01 simon-watery kernel: [   17.429630] CPU0 attaching sched-domain:
Jun 11 17:54:01 simon-watery kernel: [   17.429632]  domain 0: span 0,4 level SIBLING
Jun 11 17:54:01 simon-watery kernel: [   17.429633]   groups: 0 (cpu_power = 589) 4 (cpu_power = 589)
Jun 11 17:54:01 simon-watery kernel: [   17.429636]   domain 1: span 0-7 level MC
Jun 11 17:54:01 simon-watery kernel: [   17.429637]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun 11 17:54:01 simon-watery kernel: [   17.429642] CPU1 attaching sched-domain:
Jun 11 17:54:01 simon-watery kernel: [   17.429643]  domain 0: span 1,5 level SIBLING
Jun 11 17:54:01 simon-watery kernel: [   17.429644]   groups: 1 (cpu_power = 589) 5 (cpu_power = 589)
Jun 11 17:54:01 simon-watery kernel: [   17.429647]   domain 1: span 0-7 level MC
Jun 11 17:54:01 simon-watery kernel: [   17.429648]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun 11 17:54:01 simon-watery kernel: [   17.429652] CPU2 attaching sched-domain:
Jun 11 17:54:01 simon-watery kernel: [   17.429653]  domain 0: span 2,6 level SIBLING
Jun 11 17:54:01 simon-watery kernel: [   17.429654]   groups: 2 (cpu_power = 589) 6 (cpu_power = 589)
Jun 11 17:54:01 simon-watery kernel: [   17.429657]   domain 1: span 0-7 level MC
Jun 11 17:54:01 simon-watery kernel: [   17.429658]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun 11 17:54:01 simon-watery kernel: [   17.429662] CPU3 attaching sched-domain:
Jun 11 17:54:01 simon-watery kernel: [   17.429663]  domain 0: span 3,7 level SIBLING
Jun 11 17:54:01 simon-watery kernel: [   17.429664]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
Jun 11 17:54:01 simon-watery kernel: [   17.429667]   domain 1: span 0-7 level MC
Jun 11 17:54:01 simon-watery kernel: [   17.429668]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun 11 17:54:01 simon-watery kernel: [   17.429672] CPU4 attaching sched-domain:
Jun 11 17:54:01 simon-watery kernel: [   17.429673]  domain 0: span 0,4 level SIBLING
Jun 11 17:54:01 simon-watery kernel: [   17.429674]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
Jun 11 17:54:01 simon-watery kernel: [   17.429677]   domain 1: span 0-7 level MC
Jun 11 17:54:01 simon-watery kernel: [   17.429678]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun 11 17:54:01 simon-watery kernel: [   17.429682] CPU5 attaching sched-domain:
Jun 11 17:54:01 simon-watery kernel: [   17.429683]  domain 0: span 1,5 level SIBLING
Jun 11 17:54:01 simon-watery kernel: [   17.429685]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
Jun 11 17:54:01 simon-watery kernel: [   17.429687]   domain 1: span 0-7 level MC
Jun 11 17:54:01 simon-watery kernel: [   17.429688]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun 11 17:54:01 simon-watery kernel: [   17.429692] CPU6 attaching sched-domain:
Jun 11 17:54:01 simon-watery kernel: [   17.429693]  domain 0: span 2,6 level SIBLING
Jun 11 17:54:01 simon-watery kernel: [   17.429695]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
Jun 11 17:54:01 simon-watery kernel: [   17.429697]   domain 1: span 0-7 level MC
Jun 11 17:54:01 simon-watery kernel: [   17.429698]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun 11 17:54:01 simon-watery kernel: [   17.429703] CPU7 attaching sched-domain:
Jun 11 17:54:01 simon-watery kernel: [   17.429703]  domain 0: span 3,7 level SIBLING
Jun 11 17:54:01 simon-watery kernel: [   17.429705]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
Jun 11 17:54:01 simon-watery kernel: [   17.429707]   domain 1: span 0-7 level MC
Jun 11 17:54:01 simon-watery kernel: [   17.429708]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun 11 17:54:02 simon-watery gdm-session-worker[1649]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jun 11 17:54:02 simon-watery rtkit-daemon[1657]: Sucessfully called chroot.
Jun 11 17:54:02 simon-watery rtkit-daemon[1657]: Sucessfully dropped privileges.
Jun 11 17:54:02 simon-watery rtkit-daemon[1657]: Sucessfully limited resources.
Jun 11 17:54:02 simon-watery rtkit-daemon[1657]: Running.
Jun 11 17:54:02 simon-watery rtkit-daemon[1657]: Canary thread running.
Jun 11 17:54:02 simon-watery rtkit-daemon[1657]: Watchdog thread running.
Jun 11 17:54:02 simon-watery polkitd[1661]: started daemon version 0.96 using authority implementation `local' version `0.96'
Jun 11 17:54:02 simon-watery rtkit-daemon[1657]: Sucessfully made thread 1655 of process 1655 (n/a) owned by '114' high priority at nice level -11.
Jun 11 17:54:02 simon-watery rtkit-daemon[1657]: Supervising 1 threads of 1 processes of 1 users.
Jun 11 17:54:02 simon-watery pulseaudio[1655]: shm.c: shm_open() failed: Permission denied
Jun 11 17:54:02 simon-watery pulseaudio[1655]: core.c: failed to allocate shared memory pool. Falling back to a normal memory pool.
Jun 11 17:54:02 simon-watery gdm-simple-greeter[1646]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Jun 11 17:54:02 simon-watery rtkit-daemon[1657]: Sucessfully made thread 1709 of process 1655 (n/a) owned by '114' RT at priority 5.
Jun 11 17:54:02 simon-watery rtkit-daemon[1657]: Supervising 2 threads of 1 processes of 1 users.
Jun 11 17:54:02 simon-watery kernel: [   18.678423] CPU0 attaching NULL sched-domain.
Jun 11 17:54:02 simon-watery kernel: [   18.678426] CPU1 attaching NULL sched-domain.
Jun 11 17:54:02 simon-watery kernel: [   18.678428] CPU2 attaching NULL sched-domain.
Jun 11 17:54:02 simon-watery kernel: [   18.678429] CPU3 attaching NULL sched-domain.
Jun 11 17:54:02 simon-watery kernel: [   18.678430] CPU4 attaching NULL sched-domain.
Jun 11 17:54:02 simon-watery kernel: [   18.678431] CPU5 attaching NULL sched-domain.
Jun 11 17:54:02 simon-watery kernel: [   18.678432] CPU6 attaching NULL sched-domain.
Jun 11 17:54:02 simon-watery kernel: [   18.678433] CPU7 attaching NULL sched-domain.
Jun 11 17:54:02 simon-watery rtkit-daemon[1657]: Sucessfully made thread 1728 of process 1655 (n/a) owned by '114' RT at priority 5.
Jun 11 17:54:02 simon-watery rtkit-daemon[1657]: Supervising 3 threads of 1 processes of 1 users.
Jun 11 17:54:02 simon-watery kernel: [   18.770191] CPU0 attaching sched-domain:
Jun 11 17:54:02 simon-watery kernel: [   18.770193]  domain 0: span 0,4 level SIBLING
Jun 11 17:54:02 simon-watery kernel: [   18.770195]   groups: 0 (cpu_power = 589) 4 (cpu_power = 589)
Jun 11 17:54:02 simon-watery kernel: [   18.770198]   domain 1: span 0-7 level MC
Jun 11 17:54:02 simon-watery kernel: [   18.770199]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun 11 17:54:02 simon-watery kernel: [   18.770205] CPU1 attaching sched-domain:
Jun 11 17:54:02 simon-watery kernel: [   18.770206]  domain 0: span 1,5 level SIBLING
Jun 11 17:54:02 simon-watery kernel: [   18.770208]   groups: 1 (cpu_power = 589) 5 (cpu_power = 589)
Jun 11 17:54:02 simon-watery kernel: [   18.770210]   domain 1: span 0-7 level MC
Jun 11 17:54:02 simon-watery kernel: [   18.770212]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun 11 17:54:02 simon-watery kernel: [   18.770216] CPU2 attaching sched-domain:
Jun 11 17:54:02 simon-watery kernel: [   18.770217]  domain 0: span 2,6 level SIBLING
Jun 11 17:54:02 simon-watery kernel: [   18.770219]   groups: 2 (cpu_power = 589) 6 (cpu_power = 589)
Jun 11 17:54:02 simon-watery kernel: [   18.770221]   domain 1: span 0-7 level MC
Jun 11 17:54:02 simon-watery kernel: [   18.770222]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun 11 17:54:02 simon-watery kernel: [   18.770227] CPU3 attaching sched-domain:
Jun 11 17:54:02 simon-watery kernel: [   18.770228]  domain 0: span 3,7 level SIBLING
Jun 11 17:54:02 simon-watery kernel: [   18.770229]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
Jun 11 17:54:02 simon-watery kernel: [   18.770232]   domain 1: span 0-7 level MC
Jun 11 17:54:02 simon-watery kernel: [   18.770233]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun 11 17:54:02 simon-watery kernel: [   18.770238] CPU4 attaching sched-domain:
Jun 11 17:54:02 simon-watery kernel: [   18.770239]  domain 0: span 0,4 level SIBLING
Jun 11 17:54:02 simon-watery kernel: [   18.770240]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
Jun 11 17:54:02 simon-watery kernel: [   18.770243]   domain 1: span 0-7 level MC
Jun 11 17:54:02 simon-watery kernel: [   18.770244]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun 11 17:54:02 simon-watery kernel: [   18.770249] CPU5 attaching sched-domain:
Jun 11 17:54:02 simon-watery kernel: [   18.770250]  domain 0: span 1,5 level SIBLING
Jun 11 17:54:02 simon-watery kernel: [   18.770251]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
Jun 11 17:54:02 simon-watery kernel: [   18.770254]   domain 1: span 0-7 level MC
Jun 11 17:54:02 simon-watery kernel: [   18.770255]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun 11 17:54:02 simon-watery kernel: [   18.770260] CPU6 attaching sched-domain:
Jun 11 17:54:02 simon-watery kernel: [   18.770261]  domain 0: span 2,6 level SIBLING
Jun 11 17:54:02 simon-watery kernel: [   18.770262]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
Jun 11 17:54:02 simon-watery kernel: [   18.770265]   domain 1: span 0-7 level MC
Jun 11 17:54:02 simon-watery kernel: [   18.770266]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun 11 17:54:02 simon-watery kernel: [   18.770271] CPU7 attaching sched-domain:
Jun 11 17:54:02 simon-watery kernel: [   18.770272]  domain 0: span 3,7 level SIBLING
Jun 11 17:54:02 simon-watery kernel: [   18.770273]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
Jun 11 17:54:02 simon-watery kernel: [   18.770276]   domain 1: span 0-7 level MC
Jun 11 17:54:02 simon-watery kernel: [   18.770277]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun 11 17:54:02 simon-watery kernel: [   18.770741] CPU0 attaching NULL sched-domain.
Jun 11 17:54:02 simon-watery kernel: [   18.770742] CPU1 attaching NULL sched-domain.
Jun 11 17:54:02 simon-watery kernel: [   18.770743] CPU2 attaching NULL sched-domain.
Jun 11 17:54:02 simon-watery kernel: [   18.770744] CPU3 attaching NULL sched-domain.
Jun 11 17:54:02 simon-watery kernel: [   18.770745] CPU4 attaching NULL sched-domain.
Jun 11 17:54:02 simon-watery kernel: [   18.770746] CPU5 attaching NULL sched-domain.
Jun 11 17:54:02 simon-watery kernel: [   18.770747] CPU6 attaching NULL sched-domain.
Jun 11 17:54:02 simon-watery kernel: [   18.770749] CPU7 attaching NULL sched-domain.
Jun 11 17:54:02 simon-watery acpid: client connected from 1747[108:114]
Jun 11 17:54:02 simon-watery acpid: 1 client rule loaded
Jun 11 17:54:02 simon-watery kernel: [   18.950361] CPU0 attaching sched-domain:
Jun 11 17:54:02 simon-watery kernel: [   18.950363]  domain 0: span 0,4 level SIBLING
Jun 11 17:54:02 simon-watery kernel: [   18.950365]   groups: 0 (cpu_power = 589) 4 (cpu_power = 589)
Jun 11 17:54:02 simon-watery kernel: [   18.950368]   domain 1: span 0-7 level MC
Jun 11 17:54:02 simon-watery kernel: [   18.950369]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun 11 17:54:02 simon-watery kernel: [   18.950374] CPU1 attaching sched-domain:
Jun 11 17:54:02 simon-watery kernel: [   18.950375]  domain 0: span 1,5 level SIBLING
Jun 11 17:54:02 simon-watery kernel: [   18.950376]   groups: 1 (cpu_power = 589) 5 (cpu_power = 589)
Jun 11 17:54:02 simon-watery kernel: [   18.950379]   domain 1: span 0-7 level MC
Jun 11 17:54:02 simon-watery kernel: [   18.950380]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun 11 17:54:02 simon-watery kernel: [   18.950385] CPU2 attaching sched-domain:
Jun 11 17:54:02 simon-watery kernel: [   18.950386]  domain 0: span 2,6 level SIBLING
Jun 11 17:54:02 simon-watery kernel: [   18.950387]   groups: 2 (cpu_power = 589) 6 (cpu_power = 589)
Jun 11 17:54:02 simon-watery kernel: [   18.950389]   domain 1: span 0-7 level MC
Jun 11 17:54:02 simon-watery kernel: [   18.950390]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun 11 17:54:02 simon-watery kernel: [   18.950395] CPU3 attaching sched-domain:
Jun 11 17:54:02 simon-watery kernel: [   18.950396]  domain 0: span 3,7 level SIBLING
Jun 11 17:54:02 simon-watery kernel: [   18.950397]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
Jun 11 17:54:02 simon-watery kernel: [   18.950399]   domain 1: span 0-7 level MC
Jun 11 17:54:02 simon-watery kernel: [   18.950400]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun 11 17:54:02 simon-watery kernel: [   18.950405] CPU4 attaching sched-domain:
Jun 11 17:54:02 simon-watery kernel: [   18.950406]  domain 0: span 0,4 level SIBLING
Jun 11 17:54:02 simon-watery kernel: [   18.950407]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
Jun 11 17:54:02 simon-watery kernel: [   18.950409]   domain 1: span 0-7 level MC
Jun 11 17:54:02 simon-watery kernel: [   18.950410]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
Jun 11 17:54:02 simon-watery kernel: [   18.950415] CPU5 attaching sched-domain:
Jun 11 17:54:02 simon-watery kernel: [   18.950416]  domain 0: span 1,5 level SIBLING
Jun 11 17:54:02 simon-watery kernel: [   18.950417]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
Jun 11 17:54:02 simon-watery kernel: [   18.950420]   domain 1: span 0-7 level MC
Jun 11 17:54:02 simon-watery kernel: [   18.950421]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
Jun 11 17:54:02 simon-watery kernel: [   18.950425] CPU6 attaching sched-domain:
Jun 11 17:54:02 simon-watery kernel: [   18.950426]  domain 0: span 2,6 level SIBLING
Jun 11 17:54:02 simon-watery kernel: [   18.950427]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
Jun 11 17:54:02 simon-watery kernel: [   18.950430]   domain 1: span 0-7 level MC
Jun 11 17:54:02 simon-watery kernel: [   18.950431]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
Jun 11 17:54:02 simon-watery kernel: [   18.950435] CPU7 attaching sched-domain:
Jun 11 17:54:02 simon-watery kernel: [   18.950436]  domain 0: span 3,7 level SIBLING
Jun 11 17:54:02 simon-watery kernel: [   18.950437]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
Jun 11 17:54:02 simon-watery kernel: [   18.950440]   domain 1: span 0-7 level MC
Jun 11 17:54:02 simon-watery kernel: [   18.950441]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
Jun 11 17:54:03 simon-watery gdm-session-worker[1649]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jun 11 17:54:07 simon-watery rtkit-daemon[1657]: Sucessfully made thread 1851 of process 1851 (n/a) owned by '1000' high priority at nice level -11.
Jun 11 17:54:07 simon-watery rtkit-daemon[1657]: Supervising 4 threads of 2 processes of 2 users.
Jun 11 17:54:07 simon-watery pulseaudio[1851]: shm.c: shm_open() failed: Permission denied
Jun 11 17:54:07 simon-watery pulseaudio[1851]: core.c: failed to allocate shared memory pool. Falling back to a normal memory pool.
Jun 11 17:54:08 simon-watery rtkit-daemon[1657]: Sucessfully made thread 1865 of process 1851 (n/a) owned by '1000' RT at priority 5.
Jun 11 17:54:08 simon-watery rtkit-daemon[1657]: Supervising 5 threads of 2 processes of 2 users.
Jun 11 17:54:08 simon-watery rtkit-daemon[1657]: Sucessfully made thread 1866 of process 1851 (n/a) owned by '1000' RT at priority 5.
Jun 11 17:54:08 simon-watery rtkit-daemon[1657]: Supervising 6 threads of 2 processes of 2 users.
Jun 11 17:54:08 simon-watery rtkit-daemon[1657]: Sucessfully made thread 1871 of process 1871 (n/a) owned by '1000' high priority at nice level -11.
Jun 11 17:54:08 simon-watery rtkit-daemon[1657]: Supervising 7 threads of 3 processes of 2 users.
Jun 11 17:54:08 simon-watery pulseaudio[1871]: pid.c: Daemon already running.
Jun 11 17:54:09 simon-watery kernel: [   25.501935] eth0: no IPv6 routers present
Jun 11 17:55:10 simon-watery AptDaemon: INFO: Initializing daemon
Jun 11 17:58:03 simon-watery pulseaudio[1851]: ratelimit.c: 2 events suppressed
Jun 11 17:58:15 simon-watery ntpd[1363]: synchronized to 130.88.202.49, stratum 2
Jun 11 17:58:15 simon-watery ntpd[1363]: kernel time sync status change 2001
Jun 11 17:59:00 simon-watery anacron[1411]: Job `cron.daily' started
Jun 11 17:59:00 simon-watery anacron[2057]: Updated timestamp for job `cron.daily' to 2010-06-11

```

I still see nothing that points to why it's complaining.

I don't know enough about the linux boot process to work out which piece of it is broken.

---

### Post by spmurphy on 2010-06-11
Is boot.log rewritten *every* boot?

```
swapon: /dev/disk/by-uuid/580f8157-e9dc-426c-9fe6-f92f1b7f7ef3: swapon failed: Device or resource busy

mountall: swapon /dev/disk/by-uuid/580f8157-e9dc-426c-9fe6-f92f1b7f7ef3 [1063] terminated with status 255

mountall: Problem activating swap: /dev/disk/by-uuid/580f8157-e9dc-426c-9fe6-f92f1b7f7ef3

fsck from util-linux-ng 2.17.2

fsck from util-linux-ng 2.17.2

fsck from util-linux-ng 2.17.2

/dev/sdb6: clean, 28/499968 files, 68568/1999872 blocks

/dev/sdb7: clean, 245323/28524544 files, 25233507/114095872 blocks

/dev/sdb5: clean, 9722/499968 files, 343739/1999872 blocks (check after next mount)

```

Going to look at swap...

---

### Post by spmurphy on 2010-06-11
Ok, this is repeatable

```
swapon: /dev/disk/by-uuid/580f8157-e9dc-426c-9fe6-f92f1b7f7ef3: swapon failed: Device or resource busy

mountall: swapon /dev/disk/by-uuid/580f8157-e9dc-426c-9fe6-f92f1b7f7ef3 [1330] terminated with status 255

mountall: Problem activating swap: /dev/disk/by-uuid/580f8157-e9dc-426c-9fe6-f92f1b7f7ef3

fsck from util-linux-ng 2.17.2

/dev/sdb5: clean, 9735/499968 files, 344394/1999872 blocks

```

This particular boot it complained about errors on /var yet the corresponding boot.log above complains about mounting swap?

My swap is the first partition on the magnetic. I have 8 gig physical and 16 gig swap, is that a problem? I could try deleting the swap and recreating it, but I fail to see why it would moan about swap in boot.log but say the problems were with /var on the display.

I've never actually had it fail to boot if I select 'M' for manual intervention then don't actually do *anything* but exit the shell. Presumably after that, it mounts the partitions anyway and boots as normal.

Could this be an incorrect shutdown problem instead? I'm shutting it down from the menu, but that's not to say something isn't shutting down the filesystems correctly.

Any suggestions?

---

### Post by spmurphy on 2010-06-11
Pressing 'M' for manual and checking the filesystem it complained about on the display says no errors.

---

### Post by spmurphy on 2010-06-17
This still happens and I still can't see anything obviously wrong.

Anyone got any suggestions?

---

### Post by MountainX on 2011-12-20
same problem here with 11.10 - exactly the same. I see the error on the screen, but nothing in the logs.

---

