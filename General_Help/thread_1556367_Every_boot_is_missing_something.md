---
title: "Every boot is missing something"
date: 2010-08-19
forum: General Help
---

### Post by X5-655 on 2010-08-19
Ok, I have tollerated Ubuntu long enough, if I don't get this fixed I am going back to Windows, because this is ridiculous..

Everytime I boot, there's something missing from the gnome panel..  Literally, sometimes it's the bluetooth icon, sometimes (more than not), my name, IM status, and power buttons don't load at the top right, and sometimes the networking icon don't load..  Just empty spots where they should be..  Right clicking just yields gnome panel preferences or add a panel, not the preferences of the item that should be there..

One time when I booted, all windows had no borders, and everything loaded in the top right, like Compiz decided not to actually load..

I'm getting tired of crap like this.  EVERY damn boot, something is missing or didn't load, and I have to reboot.  It's starting to feel like my car, sometimes when it starts, it just don't run right..

It's been doing this since a fresh install too, and my laptop is perfectly fine, I've done a stress test diagnostics, RAM, CPU, everything passed with flying colors.

Ubuntu 10.04 64-bit, everything updated..

If this don't get fixed, I swear I'm going back to Windows..  Linux should be matured enough by now to not have silly little bugs like this.

---

### Post by X5-655 on 2010-08-19
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/515139](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/515139)

---

### Post by X5-655 on 2010-08-20
Bump 2..

---

### Post by ScarletWyvern on 2010-08-20
Obvious solution: don't use GNOME.

---

### Post by QIII on 2010-08-20
GNOME has worked fine for me for years on things from Fedora to  OpenSolaris.  This is something particular to the OP's machine, and he  needs an answer, not a brush off.

X5-665 -- 

There may be some useful information in /var/log/messages or /var/log/syslog.  You can also use dmesg in the terminal.

Reboot and look at what has been logged for that boot.  See if there are  errors indicating that things you expect to start are not.

It might be worth while to C&P some of the text between code tags so others have a chance to look at it and advise.

---

### Post by HeadHunter00 on 2010-08-20
This problem happens to me every now and then when I newly install any linux distro with gnome. So, what I do is make another panel, move the apps from the old panel to the new panel, and then delete the old panel. Or, sometimes you just need to refresh your desktop using Ctrl+alt+f1 and then ctrl+alt+f7(or f8 ). I hope that helped.

---

### Post by HeadHunter00 on 2010-08-20
Or, you can just use the kde-panel instead of gnome by changing the panel in gconf-editor.
Run gconf-editor using terminal or alt+f2.
Go to Desktop->Gnome->Session->Required_components and then change the panel from gnome-panel to kde-panel. That way you will still be using gnome with kde panel. Oh btw, be sure to install kubuntu from synaptics package manager.
And btw, it doesnt have to be kde-panel. you can also use xfce-panel, which is a lot lighter than kde. But again, then you have to install xubuntu from synaptics.

---

### Post by X5-655 on 2010-08-20
This is going to be a very long post.  I tried to just attach the txt files but 65kB is too large..

Syslog
```
Aug 20 16:52:01 brandon-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="817" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Aug 20 16:52:14 brandon-laptop anacron[1034]: Job `cron.daily' terminated
Aug 20 16:52:14 brandon-laptop anacron[1034]: Normal exit (1 job run)
Aug 20 17:17:01 brandon-laptop CRON[2858]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 20 17:40:21 brandon-laptop kernel: [ 5054.217840] ALSA hda_intel.c:1670: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Aug 20 17:40:21 brandon-laptop kernel: [ 5054.217856] ALSA hda_codec.c:1225: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
Aug 20 17:40:21 brandon-laptop kernel: [ 5054.217860] ALSA hda_codec.c:1225: hda_codec_setup_stream: NID=0x11, stream=0x5, channel=0, format=0x4011
Aug 20 17:40:21 brandon-laptop kernel: [ 5054.217896] ALSA hda_intel.c:1670: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Aug 20 17:40:21 brandon-laptop kernel: [ 5054.217906] ALSA hda_codec.c:1225: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
Aug 20 17:40:21 brandon-laptop kernel: [ 5054.217910] ALSA hda_codec.c:1225: hda_codec_setup_stream: NID=0x11, stream=0x5, channel=0, format=0x4011
```

Messages
```
Aug 20 16:16:23 brandon-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Aug 20 16:16:23 brandon-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="817" x-info="http://www.rsyslog.com"] (re)start
Aug 20 16:16:23 brandon-laptop rsyslogd: rsyslogd's groupid changed to 103
Aug 20 16:16:23 brandon-laptop rsyslogd: rsyslogd's userid changed to 101
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 (Ubuntu 2.6.32-24.41-generic 2.6.32.15+drm33.5)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=43ae0c2a-a07c-4304-9b11-66cf8be28d65 ro vga=758 quiet splash
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] KERNEL supported cpus:
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]   Intel GenuineIntel
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]   AMD AuthenticAMD
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]   Centaur CentaurHauls
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000de50e000 (usable)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 00000000de50e000 - 00000000de70e000 (ACPI NVS)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 00000000de70e000 - 00000000dfd94000 (usable)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 00000000dfd94000 - 00000000dfdbf000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 00000000dfdbf000 - 00000000dfe92000 (usable)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 00000000dfe92000 - 00000000dfebf000 (ACPI NVS)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 00000000dfebf000 - 00000000dfee4000 (usable)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 00000000dfee4000 - 00000000dfef7000 (ACPI data)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 00000000dfef7000 - 00000000dff00000 (usable)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 00000000f7000000 - 00000000f8000000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb01000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000110000000 (usable)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] DMI 2.6 present.
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] last_pfn = 0x110000 max_arch_pfn = 0x400000000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] last_pfn = 0xdff00 max_arch_pfn = 0x400000000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] modified physical RAM map:
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 0000000000100000 - 00000000de50e000 (usable)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 00000000de50e000 - 00000000de70e000 (ACPI NVS)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 00000000de70e000 - 00000000dfd94000 (usable)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 00000000dfd94000 - 00000000dfdbf000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 00000000dfdbf000 - 00000000dfe92000 (usable)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 00000000dfe92000 - 00000000dfebf000 (ACPI NVS)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 00000000dfebf000 - 00000000dfee4000 (usable)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 00000000dfee4000 - 00000000dfef7000 (ACPI data)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 00000000dfef7000 - 00000000dff00000 (usable)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 00000000f7000000 - 00000000f8000000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 00000000feb00000 - 00000000feb01000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]  modified: 0000000100000000 - 0000000110000000 (usable)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Using GB pages for direct mapping
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000dff00000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] NX (Execute Disable) protection: active
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000110000000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] NX (Execute Disable) protection: active
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] RAMDISK: 377b1000 - 37fef8de
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HP    )
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: XSDT 00000000dfef6120 0005C (v01 HPQOEM SLIC-MPC 00000003      01000013)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: FACP 00000000dfef5000 000F4 (v04 HP     363F     00000003 MSFT 01000013)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: DSDT 00000000dfee8000 092FF (v01 HP     363F     F0000000 MSFT 01000013)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: FACS 00000000dfe9b000 00040
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: HPET 00000000dfef4000 00038 (v01 HP     363F     00000001 MSFT 01000013)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: APIC 00000000dfef3000 00068 (v02 HP     363F     00000001 MSFT 01000013)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: MCFG 00000000dfef2000 0003C (v01 HP     363F     00000001 MSFT 01000013)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: BOOT 00000000dfee7000 00028 (v01 HP     363F     00000001 MSFT 01000013)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: SLIC 00000000dfee6000 00176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: SSDT 00000000dfee4000 00386 (v01 AMD    PowerNow 00000001 AMD  00000001)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] No NUMA configuration found
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Faking a node at 0000000000000000-0000000110000000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000110000000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]   NODE_DATA [000000000000b000 - 000000000000ffff]
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]   bootmap [0000000000010000 -  0000000000031fff] pages 22
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0110000000]
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]   #2 [0001000000 - 0001a2fe64]    TEXT DATA BSS ==> [0001000000 - 0001a2fe64]
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]   #3 [00377b1000 - 0037fef8de]          RAMDISK ==> [00377b1000 - 0037fef8de]
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]   #5 [0001a30000 - 0001a3025e]              BRK ==> [0001a30000 - 0001a3025e]
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]   #7 [000000a000 - 000000b000]          PGTABLE ==> [000000a000 - 000000b000]
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Zone PFN ranges:
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]   Normal   0x00100000 -> 0x00110000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Movable zone start PFN for each node
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] early_node_map[8] active PFN ranges
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x000de50e
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]     0: 0x000de70e -> 0x000dfd94
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]     0: 0x000dfdbf -> 0x000dfe92
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]     0: 0x000dfebf -> 0x000dfee4
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]     0: 0x000dfef7 -> 0x000dff00
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000]     0: 0x00100000 -> 0x00110000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000de50e000 - 00000000de70e000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000dfd94000 - 00000000dfdbf000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000dfe92000 - 00000000dfebf000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000dfee4000 - 00000000dfef7000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000dff00000 - 00000000f7000000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000f7000000 - 00000000f8000000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000feb00000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb01000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000feb01000 - 00000000fec00000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Allocating PCI resources starting at dff00000 (gap: dff00000:17100000)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u1048576
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 966729
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Policy zone: Normal
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=43ae0c2a-a07c-4304-9b11-66cf8be28d65 ro vga=758 quiet splash
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Initializing CPU#0
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Checking aperture...
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] No AGP bridge found
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Node 0: aperture @ fc7c000000 size 32 MB
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] This costs you 64 MB of RAM
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Memory: 3788060k/4456448k available (5422k kernel code, 528196k absent, 140192k reserved, 2979k data, 880k init)
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Hierarchical RCU implementation.
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] NR_IRQS:4352 nr_irqs:424
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Console: colour VGA+ 80x25
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] console [tty0] enabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] allocated 39321600 bytes of page_cgroup
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Aug 20 16:16:23 brandon-laptop kernel: [    0.000000] Detected 1994.663 MHz processor.
Aug 20 16:16:23 brandon-laptop kernel: [    0.020005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.32 BogoMIPS (lpj=19946600)
Aug 20 16:16:23 brandon-laptop kernel: [    0.020025] Security Framework initialized
Aug 20 16:16:23 brandon-laptop kernel: [    0.020038] AppArmor: AppArmor initialized
Aug 20 16:16:23 brandon-laptop kernel: [    0.020381] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Aug 20 16:16:23 brandon-laptop kernel: [    0.021855] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Aug 20 16:16:23 brandon-laptop kernel: [    0.022521] Mount-cache hash table entries: 256
Aug 20 16:16:23 brandon-laptop kernel: [    0.022638] Initializing cgroup subsys ns
Aug 20 16:16:23 brandon-laptop kernel: [    0.022642] Initializing cgroup subsys cpuacct
Aug 20 16:16:23 brandon-laptop kernel: [    0.022646] Initializing cgroup subsys memory
Aug 20 16:16:23 brandon-laptop kernel: [    0.022654] Initializing cgroup subsys devices
Aug 20 16:16:23 brandon-laptop kernel: [    0.022656] Initializing cgroup subsys freezer
Aug 20 16:16:23 brandon-laptop kernel: [    0.022659] Initializing cgroup subsys net_cls
Aug 20 16:16:23 brandon-laptop kernel: [    0.022676] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Aug 20 16:16:23 brandon-laptop kernel: [    0.022678] CPU: L2 Cache: 512K (64 bytes/line)
Aug 20 16:16:23 brandon-laptop kernel: [    0.022681] CPU 0/0x0 -> Node 0
Aug 20 16:16:23 brandon-laptop kernel: [    0.022686] CPU: Physical Processor ID: 0
Aug 20 16:16:23 brandon-laptop kernel: [    0.022688] CPU: Processor Core ID: 0
Aug 20 16:16:23 brandon-laptop kernel: [    0.022690] mce: CPU supports 6 MCE banks
Aug 20 16:16:23 brandon-laptop kernel: [    0.022700] using C1E aware idle routine
Aug 20 16:16:23 brandon-laptop kernel: [    0.022702] Performance Events: AMD PMU driver.
Aug 20 16:16:23 brandon-laptop kernel: [    0.022707] ... version:                0
Aug 20 16:16:23 brandon-laptop kernel: [    0.022708] ... bit width:              48
Aug 20 16:16:23 brandon-laptop kernel: [    0.022710] ... generic registers:      4
Aug 20 16:16:23 brandon-laptop kernel: [    0.022712] ... value mask:             0000ffffffffffff
Aug 20 16:16:23 brandon-laptop kernel: [    0.022714] ... max period:             00007fffffffffff
Aug 20 16:16:23 brandon-laptop kernel: [    0.022716] ... fixed-purpose events:   0
Aug 20 16:16:23 brandon-laptop kernel: [    0.022717] ... event mask:             000000000000000f
Aug 20 16:16:23 brandon-laptop kernel: [    0.024404] ACPI: Core revision 20090903
Aug 20 16:16:23 brandon-laptop kernel: [    0.040009] ftrace: converting mcount calls to 0f 1f 44 00 00
Aug 20 16:16:23 brandon-laptop kernel: [    0.040014] ftrace: allocating 22527 entries in 89 pages
Aug 20 16:16:23 brandon-laptop kernel: [    0.046750] Setting APIC routing to flat
Aug 20 16:16:23 brandon-laptop kernel: [    0.047124] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 20 16:16:23 brandon-laptop kernel: [    0.149386] CPU0: AMD Athlon(tm) II Dual-Core M300 stepping 02
Aug 20 16:16:23 brandon-laptop kernel: [    0.150000] Booting processor 1 APIC 0x1 ip 0x6000
Aug 20 16:16:23 brandon-laptop kernel: [    0.030000] Initializing CPU#1
Aug 20 16:16:23 brandon-laptop kernel: [    0.030000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Aug 20 16:16:23 brandon-laptop kernel: [    0.030000] CPU: L2 Cache: 512K (64 bytes/line)
Aug 20 16:16:23 brandon-laptop kernel: [    0.030000] CPU 1/0x1 -> Node 0
Aug 20 16:16:23 brandon-laptop kernel: [    0.030000] CPU: Physical Processor ID: 0
Aug 20 16:16:23 brandon-laptop kernel: [    0.030000] CPU: Processor Core ID: 1
Aug 20 16:16:23 brandon-laptop kernel: [    0.300101] CPU1: AMD Athlon(tm) II Dual-Core M300 stepping 02
Aug 20 16:16:23 brandon-laptop kernel: [    0.300109] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug 20 16:16:23 brandon-laptop kernel: [    0.310012] Brought up 2 CPUs
Aug 20 16:16:23 brandon-laptop kernel: [    0.310015] Total of 2 processors activated (7979.28 BogoMIPS).
Aug 20 16:16:23 brandon-laptop kernel: [    0.310021] System has AMD C1E enabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.310034] Switch to broadcast mode on CPU1
Aug 20 16:16:23 brandon-laptop kernel: [    0.310274] Switch to broadcast mode on CPU0
Aug 20 16:16:23 brandon-laptop kernel: [    0.310274] devtmpfs: initialized
Aug 20 16:16:23 brandon-laptop kernel: [    0.310274] regulator: core version 0.5
Aug 20 16:16:23 brandon-laptop kernel: [    0.310274] Time: 16:16:07  Date: 08/20/10
Aug 20 16:16:23 brandon-laptop kernel: [    0.310274] NET: Registered protocol family 16
Aug 20 16:16:23 brandon-laptop kernel: [    0.310274] TOM: 00000000e0000000 aka 3584M
Aug 20 16:16:23 brandon-laptop kernel: [    0.310274] Trying to unpack rootfs image as initramfs...
Aug 20 16:16:23 brandon-laptop kernel: [    0.310274] 
Aug 20 16:16:23 brandon-laptop kernel: [    0.310274] TOM2: 0000000120000000 aka 4608M
Aug 20 16:16:23 brandon-laptop kernel: [    0.310274] ACPI: bus type pci registered
Aug 20 16:16:23 brandon-laptop kernel: [    0.310403] PCI: MCFG configuration 0: base f7000000 segment 0 buses 0 - 15
Aug 20 16:16:23 brandon-laptop kernel: [    0.310406] PCI: MCFG area at f7000000 reserved in E820
Aug 20 16:16:23 brandon-laptop kernel: [    0.311514] PCI: Using MMCONFIG at f7000000 - f7ffffff
Aug 20 16:16:23 brandon-laptop kernel: [    0.311516] PCI: Using configuration type 1 for base access
Aug 20 16:16:23 brandon-laptop kernel: [    0.311540] mtrr: your CPUs had inconsistent fixed MTRR settings
Aug 20 16:16:23 brandon-laptop kernel: [    0.311542] mtrr: probably your BIOS does not setup all CPUs.
Aug 20 16:16:23 brandon-laptop kernel: [    0.311543] mtrr: corrected configuration.
Aug 20 16:16:23 brandon-laptop kernel: [    0.320170] bio: create slab <bio-0> at 0
Aug 20 16:16:23 brandon-laptop kernel: [    0.322147] ACPI: Executed 1 blocks of module-level executable AML code
Aug 20 16:16:23 brandon-laptop kernel: [    0.325436] ACPI: BIOS _OSI(Linux) query ignored
Aug 20 16:16:23 brandon-laptop kernel: [    0.330137] ACPI: Interpreter enabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.330137] ACPI: (supports S0 S3 S4 S5)
Aug 20 16:16:23 brandon-laptop kernel: [    0.330152] ACPI: Using IOAPIC for interrupt routing
Aug 20 16:16:23 brandon-laptop kernel: [    0.340521] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
Aug 20 16:16:23 brandon-laptop kernel: [    0.340787] ACPI: No dock devices found.
Aug 20 16:16:23 brandon-laptop kernel: [    0.341778] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 20 16:16:23 brandon-laptop kernel: [    0.341982] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
Aug 20 16:16:23 brandon-laptop kernel: [    0.341986] pci 0000:00:05.0: PME# disabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.342025] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Aug 20 16:16:23 brandon-laptop kernel: [    0.342027] pci 0000:00:06.0: PME# disabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.342389] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Aug 20 16:16:23 brandon-laptop kernel: [    0.342393] pci 0000:00:12.2: PME# disabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.342608] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Aug 20 16:16:23 brandon-laptop kernel: [    0.342612] pci 0000:00:13.2: PME# disabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.342779] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Aug 20 16:16:23 brandon-laptop kernel: [    0.342783] pci 0000:00:14.2: PME# disabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.343270] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
Aug 20 16:16:23 brandon-laptop kernel: [    0.343274] pci 0000:02:00.0: PME# disabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.343455] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 20 16:16:23 brandon-laptop kernel: [    0.343459] pci 0000:03:00.0: PME# disabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.343614] pci 0000:00:14.4: transparent bridge
Aug 20 16:16:23 brandon-laptop kernel: [    0.354828] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Aug 20 16:16:23 brandon-laptop kernel: [    0.355015] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Aug 20 16:16:23 brandon-laptop kernel: [    0.355269] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Aug 20 16:16:23 brandon-laptop kernel: [    0.355522] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Aug 20 16:16:23 brandon-laptop kernel: [    0.355754] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Aug 20 16:16:23 brandon-laptop kernel: [    0.355869] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Aug 20 16:16:23 brandon-laptop kernel: [    0.356051] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Aug 20 16:16:23 brandon-laptop kernel: [    0.356304] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Aug 20 16:16:23 brandon-laptop kernel: [    0.356492] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
Aug 20 16:16:23 brandon-laptop kernel: [    0.356496] vgaarb: loaded
Aug 20 16:16:23 brandon-laptop kernel: [    0.356599] SCSI subsystem initialized
Aug 20 16:16:23 brandon-laptop kernel: [    0.356746] usbcore: registered new interface driver usbfs
Aug 20 16:16:23 brandon-laptop kernel: [    0.356757] usbcore: registered new interface driver hub
Aug 20 16:16:23 brandon-laptop kernel: [    0.356779] usbcore: registered new device driver usb
Aug 20 16:16:23 brandon-laptop kernel: [    0.356928] ACPI: WMI: Mapper loaded
Aug 20 16:16:23 brandon-laptop kernel: [    0.356930] PCI: Using ACPI for IRQ routing
Aug 20 16:16:23 brandon-laptop kernel: [    0.357133] NetLabel: Initializing
Aug 20 16:16:23 brandon-laptop kernel: [    0.357135] NetLabel:  domain hash size = 128
Aug 20 16:16:23 brandon-laptop kernel: [    0.357137] NetLabel:  protocols = UNLABELED CIPSOv4
Aug 20 16:16:23 brandon-laptop kernel: [    0.357150] NetLabel:  unlabeled traffic allowed by default
Aug 20 16:16:23 brandon-laptop kernel: [    0.357253] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
Aug 20 16:16:23 brandon-laptop kernel: [    0.357259] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Aug 20 16:16:23 brandon-laptop kernel: [    0.359292] Switching to clocksource tsc
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] AppArmor: AppArmor Filesystem Enabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] pnp: PnP ACPI init
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] ACPI: bus type pnp registered
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] pnp: PnP ACPI: found 11 devices
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] ACPI: ACPI bus type pnp unregistered
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:01: iomem range 0xf7000000-0xf7ffffff has been reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:09: ioport range 0x400-0x4cf has been reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:09: ioport range 0x4d6-0x4d6 has been reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:09: ioport range 0x680-0x6ff has been reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:09: ioport range 0x77a-0x77a has been reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:09: ioport range 0xc00-0xc01 has been reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:09: ioport range 0xc14-0xc14 has been reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:09: ioport range 0xc50-0xc52 has been reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:09: ioport range 0xc6c-0xc6c has been reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:09: ioport range 0xc6f-0xc6f has been reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:09: ioport range 0xcd0-0xcdb has been reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:09: ioport range 0x380-0x387 has been reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359434] system 00:0a: iomem range 0xffe00000-0xffffffff has been reserved
Aug 20 16:16:23 brandon-laptop kernel: [    0.359833] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Aug 20 16:16:23 brandon-laptop kernel: [    0.359836] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
Aug 20 16:16:23 brandon-laptop kernel: [    0.359839] pci 0000:00:01.0:   MEM window: 0xf0200000-0xf03fffff
Aug 20 16:16:23 brandon-laptop kernel: [    0.359842] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
Aug 20 16:16:23 brandon-laptop kernel: [    0.359847] pci 0000:00:05.0: PCI bridge, secondary bus 0000:02
Aug 20 16:16:23 brandon-laptop kernel: [    0.359849] pci 0000:00:05.0:   IO window: disabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.359852] pci 0000:00:05.0:   MEM window: 0xf0100000-0xf01fffff
Aug 20 16:16:23 brandon-laptop kernel: [    0.359854] pci 0000:00:05.0:   PREFETCH window: disabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.359859] pci 0000:00:06.0: PCI bridge, secondary bus 0000:03
Aug 20 16:16:23 brandon-laptop kernel: [    0.359862] pci 0000:00:06.0:   IO window: 0x2000-0x2fff
Aug 20 16:16:23 brandon-laptop kernel: [    0.359865] pci 0000:00:06.0:   MEM window: 0xf0500000-0xf05fffff
Aug 20 16:16:23 brandon-laptop kernel: [    0.359868] pci 0000:00:06.0:   PREFETCH window: 0x000000f0000000-0x000000f00fffff
Aug 20 16:16:23 brandon-laptop kernel: [    0.359872] pci 0000:00:14.4: PCI bridge, secondary bus 0000:04
Aug 20 16:16:23 brandon-laptop kernel: [    0.359874] pci 0000:00:14.4:   IO window: disabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.359944] pci 0000:00:14.4:   MEM window: disabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.359948] pci 0000:00:14.4:   PREFETCH window: disabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.359975] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 20 16:16:23 brandon-laptop kernel: [    0.359988] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug 20 16:16:23 brandon-laptop kernel: [    0.360063] NET: Registered protocol family 2
Aug 20 16:16:23 brandon-laptop kernel: [    0.360221] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 20 16:16:23 brandon-laptop kernel: [    0.361359] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Aug 20 16:16:23 brandon-laptop kernel: [    0.364326] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Aug 20 16:16:23 brandon-laptop kernel: [    0.364691] TCP: Hash tables configured (established 524288 bind 65536)
Aug 20 16:16:23 brandon-laptop kernel: [    0.364695] TCP reno registered
Aug 20 16:16:23 brandon-laptop kernel: [    0.364786] NET: Registered protocol family 1
Aug 20 16:16:23 brandon-laptop kernel: [    0.520961] PCI-DMA: Disabling AGP.
Aug 20 16:16:23 brandon-laptop kernel: [    0.521046] PCI-DMA: aperture base @ 20000000 size 65536 KB
Aug 20 16:16:23 brandon-laptop kernel: [    0.521048] PCI-DMA: using GART IOMMU.
Aug 20 16:16:23 brandon-laptop kernel: [    0.521051] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Aug 20 16:16:23 brandon-laptop kernel: [    0.522494] Simple Boot Flag at 0x44 set to 0x1
Aug 20 16:16:23 brandon-laptop kernel: [    0.522677] Scanning for low memory corruption every 60 seconds
Aug 20 16:16:23 brandon-laptop kernel: [    0.522805] audit: initializing netlink socket (disabled)
Aug 20 16:16:23 brandon-laptop kernel: [    0.522816] type=2000 audit(1282320967.520:1): initialized
Aug 20 16:16:23 brandon-laptop kernel: [    0.531785] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Aug 20 16:16:23 brandon-laptop kernel: [    0.533016] VFS: Disk quotas dquot_6.5.2
Aug 20 16:16:23 brandon-laptop kernel: [    0.533071] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Aug 20 16:16:23 brandon-laptop kernel: [    0.533634] fuse init (API version 7.13)
Aug 20 16:16:23 brandon-laptop kernel: [    0.533708] msgmni has been set to 7398
Aug 20 16:16:23 brandon-laptop kernel: [    0.533910] alg: No test for stdrng (krng)
Aug 20 16:16:23 brandon-laptop kernel: [    0.533960] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug 20 16:16:23 brandon-laptop kernel: [    0.533964] io scheduler noop registered
Aug 20 16:16:23 brandon-laptop kernel: [    0.533965] io scheduler anticipatory registered
Aug 20 16:16:23 brandon-laptop kernel: [    0.533967] io scheduler deadline registered
Aug 20 16:16:23 brandon-laptop kernel: [    0.533998] io scheduler cfq registered (default)
Aug 20 16:16:23 brandon-laptop kernel: [    0.534365] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 20 16:16:23 brandon-laptop kernel: [    0.534385] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug 20 16:16:23 brandon-laptop kernel: [    0.535022] ACPI: AC Adapter [ACAD] (on-line)
Aug 20 16:16:23 brandon-laptop kernel: [    0.535081] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Aug 20 16:16:23 brandon-laptop kernel: [    0.535085] ACPI: Power Button [PWRB]
Aug 20 16:16:23 brandon-laptop kernel: [    0.535127] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
Aug 20 16:16:23 brandon-laptop kernel: [    0.535129] ACPI: Sleep Button [SLPB]
Aug 20 16:16:23 brandon-laptop kernel: [    0.535180] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
Aug 20 16:16:23 brandon-laptop kernel: [    0.535691] ACPI: Lid Switch [LID]
Aug 20 16:16:23 brandon-laptop kernel: [    0.535758] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Aug 20 16:16:23 brandon-laptop kernel: [    0.535762] ACPI: Power Button [PWRF]
Aug 20 16:16:23 brandon-laptop kernel: [    0.536166] ACPI: processor limited to max C-state 1
Aug 20 16:16:23 brandon-laptop kernel: [    0.536196] processor LNXCPU:00: registered as cooling_device0
Aug 20 16:16:23 brandon-laptop kernel: [    0.536229] processor LNXCPU:01: registered as cooling_device1
Aug 20 16:16:23 brandon-laptop kernel: [    0.539390] ACPI Exception: AE_OK, No or invalid critical threshold (20090903/thermal-386)
Aug 20 16:16:23 brandon-laptop kernel: [    0.540799] Linux agpgart interface v0.103
Aug 20 16:16:23 brandon-laptop kernel: [    0.540832] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Aug 20 16:16:23 brandon-laptop kernel: [    0.541926] brd: module loaded
Aug 20 16:16:23 brandon-laptop kernel: [    0.542307] loop: module loaded
Aug 20 16:16:23 brandon-laptop kernel: [    0.542393] input: Macintosh mouse button emulation as /devices/virtual/input/input4
Aug 20 16:16:23 brandon-laptop kernel: [    0.542768] Fixed MDIO Bus: probed
Aug 20 16:16:23 brandon-laptop kernel: [    0.542797] PPP generic driver version 2.4.2
Aug 20 16:16:23 brandon-laptop kernel: [    0.542825] tun: Universal TUN/TAP device driver, 1.6
Aug 20 16:16:23 brandon-laptop kernel: [    0.542827] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug 20 16:16:23 brandon-laptop kernel: [    0.542901] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 20 16:16:23 brandon-laptop kernel: [    0.543105] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug 20 16:16:23 brandon-laptop kernel: [    0.543138] ehci_hcd 0000:00:12.2: EHCI Host Controller
Aug 20 16:16:23 brandon-laptop kernel: [    0.543169] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Aug 20 16:16:23 brandon-laptop kernel: [    0.543207] ehci_hcd 0000:00:12.2: debug port 1
Aug 20 16:16:23 brandon-laptop kernel: [    0.543229] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf0408500
Aug 20 16:16:23 brandon-laptop kernel: [    0.560671] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Aug 20 16:16:23 brandon-laptop kernel: [    0.560790] usb usb1: configuration #1 chosen from 1 choice
Aug 20 16:16:23 brandon-laptop kernel: [    0.560816] hub 1-0:1.0: USB hub found
Aug 20 16:16:23 brandon-laptop kernel: [    0.560824] hub 1-0:1.0: 6 ports detected
Aug 20 16:16:23 brandon-laptop kernel: [    0.561084] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 20 16:16:23 brandon-laptop kernel: [    0.561117] ehci_hcd 0000:00:13.2: EHCI Host Controller
Aug 20 16:16:23 brandon-laptop kernel: [    0.561158] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Aug 20 16:16:23 brandon-laptop kernel: [    0.561246] ehci_hcd 0000:00:13.2: debug port 1
Aug 20 16:16:23 brandon-laptop kernel: [    0.561267] ehci_hcd 0000:00:13.2: irq 19, io mem 0xf0408400
Aug 20 16:16:23 brandon-laptop kernel: [    0.562933] ACPI: Battery Slot [BAT0] (battery present)
Aug 20 16:16:23 brandon-laptop kernel: [    0.580714] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Aug 20 16:16:23 brandon-laptop kernel: [    0.580824] usb usb2: configuration #1 chosen from 1 choice
Aug 20 16:16:23 brandon-laptop kernel: [    0.580850] hub 2-0:1.0: USB hub found
Aug 20 16:16:23 brandon-laptop kernel: [    0.580859] hub 2-0:1.0: 6 ports detected
Aug 20 16:16:23 brandon-laptop kernel: [    0.581005] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 20 16:16:23 brandon-laptop kernel: [    0.581140] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 20 16:16:23 brandon-laptop kernel: [    0.581166] ohci_hcd 0000:00:12.0: OHCI Host Controller
Aug 20 16:16:23 brandon-laptop kernel: [    0.581199] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Aug 20 16:16:23 brandon-laptop kernel: [    0.581304] ohci_hcd 0000:00:12.0: irq 16, io mem 0xf0407000
Aug 20 16:16:23 brandon-laptop kernel: [    0.585544] Freeing initrd memory: 8442k freed
Aug 20 16:16:23 brandon-laptop kernel: [    0.644791] usb usb3: configuration #1 chosen from 1 choice
Aug 20 16:16:23 brandon-laptop kernel: [    0.644817] hub 3-0:1.0: USB hub found
Aug 20 16:16:23 brandon-laptop kernel: [    0.644892] hub 3-0:1.0: 3 ports detected
Aug 20 16:16:23 brandon-laptop kernel: [    0.645065] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 20 16:16:23 brandon-laptop kernel: [    0.645090] ohci_hcd 0000:00:12.1: OHCI Host Controller
Aug 20 16:16:23 brandon-laptop kernel: [    0.645123] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Aug 20 16:16:23 brandon-laptop kernel: [    0.645146] ohci_hcd 0000:00:12.1: irq 16, io mem 0xf0406000
Aug 20 16:16:23 brandon-laptop kernel: [    0.704795] usb usb4: configuration #1 chosen from 1 choice
Aug 20 16:16:23 brandon-laptop kernel: [    0.704821] hub 4-0:1.0: USB hub found
Aug 20 16:16:23 brandon-laptop kernel: [    0.704896] hub 4-0:1.0: 3 ports detected
Aug 20 16:16:23 brandon-laptop kernel: [    0.705068] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug 20 16:16:23 brandon-laptop kernel: [    0.705095] ohci_hcd 0000:00:13.0: OHCI Host Controller
Aug 20 16:16:23 brandon-laptop kernel: [    0.705129] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Aug 20 16:16:23 brandon-laptop kernel: [    0.705233] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf0405000
Aug 20 16:16:23 brandon-laptop kernel: [    0.764825] usb usb5: configuration #1 chosen from 1 choice
Aug 20 16:16:23 brandon-laptop kernel: [    0.764850] hub 5-0:1.0: USB hub found
Aug 20 16:16:23 brandon-laptop kernel: [    0.764925] hub 5-0:1.0: 3 ports detected
Aug 20 16:16:23 brandon-laptop kernel: [    0.765094] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug 20 16:16:23 brandon-laptop kernel: [    0.765120] ohci_hcd 0000:00:13.1: OHCI Host Controller
Aug 20 16:16:23 brandon-laptop kernel: [    0.765159] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Aug 20 16:16:23 brandon-laptop kernel: [    0.765249] ohci_hcd 0000:00:13.1: irq 18, io mem 0xf0404000
Aug 20 16:16:23 brandon-laptop kernel: [    0.824880] usb usb6: configuration #1 chosen from 1 choice
Aug 20 16:16:23 brandon-laptop kernel: [    0.824905] hub 6-0:1.0: USB hub found
Aug 20 16:16:23 brandon-laptop kernel: [    0.824980] hub 6-0:1.0: 3 ports detected
Aug 20 16:16:23 brandon-laptop kernel: [    0.825046] uhci_hcd: USB Universal Host Controller Interface driver
Aug 20 16:16:23 brandon-laptop kernel: [    0.825117] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 20 16:16:23 brandon-laptop kernel: [    0.842734] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 20 16:16:23 brandon-laptop kernel: [    0.842739] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 20 16:16:23 brandon-laptop kernel: [    0.842845] mice: PS/2 mouse device common for all mice
Aug 20 16:16:23 brandon-laptop kernel: [    0.844073] rtc_cmos 00:05: RTC can wake from S4
Aug 20 16:16:23 brandon-laptop kernel: [    0.844108] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Aug 20 16:16:23 brandon-laptop kernel: [    0.844132] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
Aug 20 16:16:23 brandon-laptop kernel: [    0.844241] device-mapper: uevent: version 1.0.3
Aug 20 16:16:23 brandon-laptop kernel: [    0.844357] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Aug 20 16:16:23 brandon-laptop kernel: [    0.844449] device-mapper: multipath: version 1.1.0 loaded
Aug 20 16:16:23 brandon-laptop kernel: [    0.844452] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug 20 16:16:23 brandon-laptop kernel: [    0.844624] cpuidle: using governor ladder
Aug 20 16:16:23 brandon-laptop kernel: [    0.844626] cpuidle: using governor menu
Aug 20 16:16:23 brandon-laptop kernel: [    0.844948] TCP cubic registered
Aug 20 16:16:23 brandon-laptop kernel: [    0.845060] NET: Registered protocol family 10
Aug 20 16:16:23 brandon-laptop kernel: [    0.845465] lo: Disabled Privacy Extensions
Aug 20 16:16:23 brandon-laptop kernel: [    0.845724] NET: Registered protocol family 17
Aug 20 16:16:23 brandon-laptop kernel: [    0.845769] powernow-k8: Found 1 AMD Athlon(tm) II Dual-Core M300 processors (2 cpu cores) (version 2.20.00)
Aug 20 16:16:23 brandon-laptop kernel: [    0.845811] powernow-k8:    0 : pstate 0 (2000 MHz)
Aug 20 16:16:23 brandon-laptop kernel: [    0.845813] powernow-k8:    1 : pstate 1 (1400 MHz)
Aug 20 16:16:23 brandon-laptop kernel: [    0.845815] powernow-k8:    2 : pstate 2 (800 MHz)
Aug 20 16:16:23 brandon-laptop kernel: [    0.846079] registered taskstats version 1
Aug 20 16:16:23 brandon-laptop kernel: [    0.846453]   Magic number: 6:930:287
Aug 20 16:16:23 brandon-laptop kernel: [    0.846480] tty tty20: hash matches
Aug 20 16:16:23 brandon-laptop kernel: [    0.846606] rtc_cmos 00:05: setting system clock to 2010-08-20 16:16:08 UTC (1282320968)
Aug 20 16:16:23 brandon-laptop kernel: [    0.846609] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 20 16:16:23 brandon-laptop kernel: [    0.846611] EDD information not available.
Aug 20 16:16:23 brandon-laptop kernel: [    0.846679] Freeing unused kernel memory: 880k freed
Aug 20 16:16:23 brandon-laptop kernel: [    0.846926] Write protecting the kernel read-only data: 7696k
Aug 20 16:16:23 brandon-laptop kernel: [    0.860588] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
Aug 20 16:16:23 brandon-laptop kernel: [    0.870115] udev: starting version 151
Aug 20 16:16:23 brandon-laptop kernel: [    0.969542] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Aug 20 16:16:23 brandon-laptop kernel: [    0.969617] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug 20 16:16:23 brandon-laptop kernel: [    0.970439] eth0: RTL8102e at 0xffffc90000678000, 00:26:9e:50:79:4d, XID 04c00000 IRQ 27
Aug 20 16:16:23 brandon-laptop kernel: [    0.976406] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 20 16:16:23 brandon-laptop kernel: [    0.976589] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Aug 20 16:16:23 brandon-laptop kernel: [    0.976594] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
Aug 20 16:16:23 brandon-laptop kernel: [    0.983844] scsi0 : ahci
Aug 20 16:16:23 brandon-laptop kernel: [    0.987983] scsi1 : ahci
Aug 20 16:16:23 brandon-laptop kernel: [    0.988123] ata1: SATA max UDMA/133 abar m1024@0xf0408000 port 0xf0408100 irq 22
Aug 20 16:16:23 brandon-laptop kernel: [    0.988127] ata2: SATA max UDMA/133 abar m1024@0xf0408000 port 0xf0408180 irq 22
Aug 20 16:16:23 brandon-laptop kernel: [    1.000768] usb 1-3: new high speed USB device using ehci_hcd and address 3
Aug 20 16:16:23 brandon-laptop kernel: [    1.165797] usb 1-3: configuration #1 chosen from 1 choice
Aug 20 16:16:23 brandon-laptop kernel: [    1.480154] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 20 16:16:23 brandon-laptop kernel: [    1.490146] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 20 16:16:23 brandon-laptop kernel: [    1.490172] usb 3-1: new full speed USB device using ohci_hcd and address 2
Aug 20 16:16:23 brandon-laptop kernel: [    1.490924] ata1.00: ATA-8: TOSHIBA MK2555GSX, FG002C, max UDMA/100
Aug 20 16:16:23 brandon-laptop kernel: [    1.490928] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Aug 20 16:16:23 brandon-laptop kernel: [    1.491914] ata1.00: configured for UDMA/100
Aug 20 16:16:23 brandon-laptop kernel: [    1.498089] ata2.00: ATAPI: hp       CDDVDW TS-L633M, 0301, max UDMA/100, ATAPI AN
Aug 20 16:16:23 brandon-laptop kernel: [    1.510252] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK2555GS FG00 PQ: 0 ANSI: 5
Aug 20 16:16:23 brandon-laptop kernel: [    1.510411] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug 20 16:16:23 brandon-laptop kernel: [    1.510598] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Aug 20 16:16:23 brandon-laptop kernel: [    1.510635] sd 0:0:0:0: [sda] Write Protect is off
Aug 20 16:16:23 brandon-laptop kernel: [    1.510657] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 20 16:16:23 brandon-laptop kernel: [    1.510764]  sda:
Aug 20 16:16:23 brandon-laptop kernel: [    1.517859] ata2.00: configured for UDMA/100
Aug 20 16:16:23 brandon-laptop kernel: [    1.536484] scsi 1:0:0:0: CD-ROM            hp       CDDVDW TS-L633M  0301 PQ: 0 ANSI: 5
Aug 20 16:16:23 brandon-laptop kernel: [    1.551896] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 20 16:16:23 brandon-laptop kernel: [    1.551901] Uniform CD-ROM driver Revision: 3.20
Aug 20 16:16:23 brandon-laptop kernel: [    1.552098] sr 1:0:0:0: Attached scsi generic sg1 type 5
Aug 20 16:16:23 brandon-laptop kernel: [    1.579969]  sda1 < sda5 sda6 > sda3 sda4
Aug 20 16:16:23 brandon-laptop kernel: [    1.623267] sd 0:0:0:0: [sda] Attached SCSI disk
Aug 20 16:16:23 brandon-laptop kernel: [    1.687054] usb 3-1: configuration #1 chosen from 1 choice
Aug 20 16:16:23 brandon-laptop kernel: [    1.689002] hub 3-1:1.0: USB hub found
Aug 20 16:16:23 brandon-laptop kernel: [    1.690940] hub 3-1:1.0: 3 ports detected
Aug 20 16:16:23 brandon-laptop kernel: [    1.990983] usb 3-1.1: new full speed USB device using ohci_hcd and address 3
Aug 20 16:16:23 brandon-laptop kernel: [    2.111110] usb 3-1.1: configuration #1 chosen from 1 choice
Aug 20 16:16:23 brandon-laptop kernel: [    2.122479] usbcore: registered new interface driver hiddev
Aug 20 16:16:23 brandon-laptop kernel: [    2.126240] input: HID 0a5c:4502 as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input6
Aug 20 16:16:23 brandon-laptop kernel: [    2.126323] generic-usb 0003:0A5C:4502.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 0a5c:4502] on usb-0000:00:12.0-1.1/input0
Aug 20 16:16:23 brandon-laptop kernel: [    2.126348] usbcore: registered new interface driver usbhid
Aug 20 16:16:23 brandon-laptop kernel: [    2.126350] usbhid: v2.6:USB HID core driver
Aug 20 16:16:23 brandon-laptop kernel: [    2.191011] usb 3-1.2: new full speed USB device using ohci_hcd and address 4
Aug 20 16:16:23 brandon-laptop kernel: [    2.311144] usb 3-1.2: configuration #1 chosen from 1 choice
Aug 20 16:16:23 brandon-laptop kernel: [    2.319319] input: HID 0a5c:4503 as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1.2/3-1.2:1.0/input/input7
Aug 20 16:16:23 brandon-laptop kernel: [    2.319414] generic-usb 0003:0A5C:4503.0002: input,hidraw1: USB HID v1.11 Mouse [HID 0a5c:4503] on usb-0000:00:12.0-1.2/input0
Aug 20 16:16:23 brandon-laptop kernel: [    2.401034] usb 3-1.3: new full speed USB device using ohci_hcd and address 5
Aug 20 16:16:23 brandon-laptop kernel: [    2.405367] EXT4-fs (sda5): mounted filesystem with ordered data mode
Aug 20 16:16:23 brandon-laptop kernel: [    2.529162] usb 3-1.3: configuration #1 chosen from 1 choice
Aug 20 16:16:23 brandon-laptop kernel: [   14.442872] udev: starting version 151
Aug 20 16:16:23 brandon-laptop kernel: [   14.520092] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 20 16:16:23 brandon-laptop kernel: [   14.537217] Adding 9377784k swap on /dev/sda6.  Priority:-1 extents:1 across:9377784k 
Aug 20 16:16:23 brandon-laptop kernel: [   14.551773] lp: driver loaded but no devices found
Aug 20 16:16:23 brandon-laptop kernel: [   14.654783] Linux video capture interface: v2.00
Aug 20 16:16:23 brandon-laptop kernel: [   14.657690] uvcvideo: Found UVC 1.00 device HP Webcam-101 (064e:a102)
Aug 20 16:16:23 brandon-laptop kernel: [   14.658320] EDAC MC: Ver: 2.1.0 Aug 19 2010
Aug 20 16:16:23 brandon-laptop kernel: [   14.660203] vga16fb: mapped to 0xffff8800000a0000
Aug 20 16:16:23 brandon-laptop kernel: [   14.660290] fb0: VGA16 VGA frame buffer device
Aug 20 16:16:23 brandon-laptop kernel: [   14.666310] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Aug 20 16:16:23 brandon-laptop kernel: [   14.666315] Disabling lock debugging due to kernel taint
Aug 20 16:16:23 brandon-laptop kernel: [   14.722332] cfg80211: Calling CRDA to update world regulatory domain
Aug 20 16:16:23 brandon-laptop kernel: [   14.722361] ACPI: resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SMBI [0x000b00-0x000b0f]
Aug 20 16:16:23 brandon-laptop kernel: [   14.722363] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Aug 20 16:16:23 brandon-laptop kernel: [   14.724783] acpi device:03: registered as cooling_device2
Aug 20 16:16:23 brandon-laptop kernel: [   14.724929] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input8
Aug 20 16:16:23 brandon-laptop kernel: [   14.724987] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Aug 20 16:16:23 brandon-laptop kernel: [   14.733060] input: HP Webcam-101 as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/input/input9
Aug 20 16:16:23 brandon-laptop kernel: [   14.733123] usbcore: registered new interface driver uvcvideo
Aug 20 16:16:23 brandon-laptop kernel: [   14.733126] USB Video Class driver (v0.1.0)
Aug 20 16:16:23 brandon-laptop kernel: [   14.784677] type=1505 audit(1282335382.435:2):  operation="profile_load" pid=648 name="/sbin/dhclient3"
Aug 20 16:16:23 brandon-laptop kernel: [   14.784953] type=1505 audit(1282335382.435:3):  operation="profile_load" pid=648 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug 20 16:16:23 brandon-laptop kernel: [   14.785107] type=1505 audit(1282335382.435:4):  operation="profile_load" pid=648 name="/usr/lib/connman/scripts/dhclient-script"
Aug 20 16:16:23 brandon-laptop kernel: [   14.820353] cfg80211: World regulatory domain updated:
Aug 20 16:16:23 brandon-laptop kernel: [   14.820357] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 20 16:16:23 brandon-laptop kernel: [   14.820360] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 20 16:16:23 brandon-laptop kernel: [   14.820363] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 20 16:16:23 brandon-laptop kernel: [   14.820365] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 20 16:16:23 brandon-laptop kernel: [   14.820368] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 20 16:16:23 brandon-laptop kernel: [   14.820370] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 20 16:16:23 brandon-laptop kernel: [   14.846343] Bluetooth: Core ver 2.15
Aug 20 16:16:23 brandon-laptop kernel: [   14.846463] [fglrx] Maximum main memory to use for locked dma buffers: 3550 MBytes.
Aug 20 16:16:23 brandon-laptop kernel: [   14.846506] [fglrx]   vendor: 1002 device: 9712 count: 1
Aug 20 16:16:23 brandon-laptop kernel: [   14.846816] [fglrx] ioport: bar 1, base 0x3000, size: 0x100
Aug 20 16:16:23 brandon-laptop kernel: [   14.846844] pci 0000:01:05.0: power state changed by ACPI to D0
Aug 20 16:16:23 brandon-laptop kernel: [   14.846851] pci 0000:01:05.0: power state changed by ACPI to D0
Aug 20 16:16:23 brandon-laptop kernel: [   14.846859] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug 20 16:16:23 brandon-laptop kernel: [   14.847171] [fglrx] Kernel PAT support is enabled
Aug 20 16:16:23 brandon-laptop kernel: [   14.847195] [fglrx] module loaded - fglrx 8.75.5 [Jun 29 2010] with 1 minors
Aug 20 16:16:23 brandon-laptop kernel: [   14.852920] NET: Registered protocol family 31
Aug 20 16:16:23 brandon-laptop kernel: [   14.852923] Bluetooth: HCI device and connection manager initialized
Aug 20 16:16:23 brandon-laptop kernel: [   14.852926] Bluetooth: HCI socket layer initialized
Aug 20 16:16:23 brandon-laptop kernel: [   14.854762] Bluetooth: Generic Bluetooth USB driver ver 0.6
Aug 20 16:16:23 brandon-laptop kernel: [   14.854880] usbcore: registered new interface driver btusb
Aug 20 16:16:23 brandon-laptop kernel: [   14.873453] EDAC amd64_edac:  Ver: 3.2.0 Aug 19 2010
Aug 20 16:16:23 brandon-laptop kernel: [   14.924235] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
Aug 20 16:16:23 brandon-laptop kernel: [   14.924246] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Aug 20 16:16:23 brandon-laptop kernel: [   14.924248]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Aug 20 16:16:23 brandon-laptop kernel: [   14.924249]  (Note that use of the override may cause unknown side effects.)
Aug 20 16:16:23 brandon-laptop kernel: [   14.924284] amd64_edac: probe of 0000:00:18.2 failed with error -22
Aug 20 16:16:23 brandon-laptop kernel: [   14.931432] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 20 16:16:23 brandon-laptop kernel: [   14.984500] Console: switching to colour frame buffer device 80x30
Aug 20 16:16:23 brandon-laptop kernel: [   14.993487] Registered led device: ath9k-phy0::radio
Aug 20 16:16:23 brandon-laptop kernel: [   14.993503] Registered led device: ath9k-phy0::assoc
Aug 20 16:16:23 brandon-laptop kernel: [   14.993517] Registered led device: ath9k-phy0::tx
Aug 20 16:16:23 brandon-laptop kernel: [   14.993530] Registered led device: ath9k-phy0::rx
Aug 20 16:16:23 brandon-laptop kernel: [   14.993543] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xffffc90002a40000, irq=17
Aug 20 16:16:23 brandon-laptop kernel: [   15.683435] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00000
Aug 20 16:16:23 brandon-laptop kernel: [   15.752790] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
Aug 20 16:16:23 brandon-laptop kernel: [   15.892748] type=1505 audit(1282335383.543:5):  operation="profile_load" pid=859 name="/usr/share/gdm/guest-session/Xsession"
Aug 20 16:16:23 brandon-laptop kernel: [   15.894276] type=1505 audit(1282335383.543:6):  operation="profile_replace" pid=860 name="/sbin/dhclient3"
Aug 20 16:16:23 brandon-laptop kernel: [   15.894601] type=1505 audit(1282335383.543:7):  operation="profile_replace" pid=860 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug 20 16:16:23 brandon-laptop kernel: [   15.894762] type=1505 audit(1282335383.543:8):  operation="profile_replace" pid=860 name="/usr/lib/connman/scripts/dhclient-script"
Aug 20 16:16:23 brandon-laptop kernel: [   15.897889] type=1505 audit(1282335383.543:9):  operation="profile_load" pid=861 name="/usr/bin/evince"
Aug 20 16:16:23 brandon-laptop kernel: [   15.901643] type=1505 audit(1282335383.553:10):  operation="profile_load" pid=861 name="/usr/bin/evince-previewer"
Aug 20 16:16:23 brandon-laptop kernel: [   15.903980] type=1505 audit(1282335383.553:11):  operation="profile_load" pid=861 name="/usr/bin/evince-thumbnailer"
Aug 20 16:16:23 brandon-laptop kernel: [   15.930725] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 20 16:16:23 brandon-laptop kernel: [   15.952254] r8169: eth0: link down
Aug 20 16:16:23 brandon-laptop kernel: [   15.952800] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 20 16:16:23 brandon-laptop kernel: [   16.299493] [fglrx] GART Table is not in FRAME_BUFFER range 
Aug 20 16:16:23 brandon-laptop kernel: [   16.300490] [fglrx] Firegl kernel thread PID: 968
Aug 20 16:16:23 brandon-laptop kernel: [   16.300789] [fglrx] IRQ 28 Enabled
Aug 20 16:16:24 brandon-laptop kernel: [   16.424397] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 20 16:16:24 brandon-laptop kernel: [   16.603489] ALSA patch_sigmatel.c:5565: hda_codec: 92HD75B2X5: BIOS auto-probing.
Aug 20 16:16:24 brandon-laptop kernel: [   16.604070] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input11
Aug 20 16:16:24 brandon-laptop kernel: [   16.640422] input: HDA ATI SB Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
Aug 20 16:16:24 brandon-laptop kernel: [   16.640512] input: HDA ATI SB HP Out at Ext Rear Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input13
Aug 20 16:16:24 brandon-laptop kernel: [   16.669020] VBoxDrv: dbg - g_abExecMemory=ffffffffa0519ca0
Aug 20 16:16:24 brandon-laptop kernel: [   16.669053] vboxdrv: fAsync=0 offMin=0x3c7 offMax=0x208f
Aug 20 16:16:24 brandon-laptop kernel: [   16.672281] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Aug 20 16:16:24 brandon-laptop kernel: [   16.698449] [fglrx] Gart USWC size:1160 M.
Aug 20 16:16:24 brandon-laptop kernel: [   16.698453] [fglrx] Gart cacheable size:459 M.
Aug 20 16:16:24 brandon-laptop kernel: [   16.698459] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Aug 20 16:16:24 brandon-laptop kernel: [   16.698462] [fglrx] Reserved FB block: Unshared offset:14ffb000, size:5000 
Aug 20 16:16:24 brandon-laptop kernel: [   16.963927] Bluetooth: L2CAP ver 2.14
Aug 20 16:16:24 brandon-laptop kernel: [   16.963930] Bluetooth: L2CAP socket layer initialized
Aug 20 16:16:24 brandon-laptop kernel: [   16.969339] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug 20 16:16:24 brandon-laptop kernel: [   16.969342] Bluetooth: BNEP filters: protocol multicast
Aug 20 16:16:24 brandon-laptop kernel: [   16.988129] Bridge firewalling registered
Aug 20 16:16:24 brandon-laptop kernel: [   16.999507] Bluetooth: SCO (Voice Link) ver 0.6
Aug 20 16:16:24 brandon-laptop kernel: [   16.999511] Bluetooth: SCO socket layer initialized
Aug 20 16:16:24 brandon-laptop kernel: [   17.011987] usb 3-1.1: input irq status -75  received
Aug 20 16:16:24 brandon-laptop kernel: [   17.027987] usb 3-1.1: input irq status -75  received
Aug 20 16:16:24 brandon-laptop kernel: [   17.030630] ppdev: user-space parallel port driver
Aug 20 16:16:24 brandon-laptop kernel: [   17.043995] usb 3-1.1: input irq status -75  received
Aug 20 16:16:24 brandon-laptop kernel: [   17.059991] usb 3-1.1: input irq status -75  received
Aug 20 16:16:24 brandon-laptop kernel: [   17.151776] Bluetooth: RFCOMM TTY layer initialized
Aug 20 16:16:24 brandon-laptop kernel: [   17.151781] Bluetooth: RFCOMM socket layer initialized
Aug 20 16:16:24 brandon-laptop kernel: [   17.151783] Bluetooth: RFCOMM ver 1.11
Aug 20 16:16:33 brandon-laptop kernel: [   26.052717] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 20 16:17:44 brandon-laptop kernel: [   97.929971] __ratelimit: 9 callbacks suppressed
Aug 20 16:17:44 brandon-laptop kernel: [   97.929977] python[1427]: segfault at 7ff2fe2ec190 ip 00007ff2fe2ec190 sp 00007fff555ad0d8 error 15 in libQtGui.so.4.6.2[7ff2fe2d9000+3f000]
Aug 20 16:17:46 brandon-laptop kernel: [   99.273826] [fglrx] IRQ 28 Disabled
Aug 20 16:17:46 brandon-laptop kernel: [   99.715904] [fglrx] GART Table is not in FRAME_BUFFER range 
Aug 20 16:17:46 brandon-laptop kernel: [   99.716728] [fglrx] Firegl kernel thread PID: 1802
Aug 20 16:17:46 brandon-laptop kernel: [   99.717024] [fglrx] IRQ 28 Enabled
Aug 20 16:17:46 brandon-laptop kernel: [   99.905809] [fglrx] Gart USWC size:1160 M.
Aug 20 16:17:46 brandon-laptop kernel: [   99.905813] [fglrx] Gart cacheable size:459 M.
Aug 20 16:17:46 brandon-laptop kernel: [   99.905818] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Aug 20 16:17:46 brandon-laptop kernel: [   99.905822] [fglrx] Reserved FB block: Unshared offset:14ffb000, size:5000 
Aug 20 16:52:01 brandon-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="817" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
```

---

### Post by QIII on 2010-08-20
Can you give us some hardware information?  What version of the fglrx driver are you using?  I didn't see anything there that jumped out in my lap (I'll look more closely if I get the chance), so I don't know what else I can suggest.

I'm not saying it isn't a bug, but it is not happening to me or to many, many other users, so it is not generalized.  It may be something that occurs with some particular hardware configuration.  In any case, it does need to be addressed.

By the way, the bug reported on launchpad will not likely be dealt with as is.  It is marked as incomplete.  That means there is not enough information provided for anyone to work on it.

I think you are having a problem specifically with gnome-panel rather than GNOME in general.

Search launchpad first for a complete bug report.  If there is one, add your "this affects me too".  

If you do not find one, click ALT+F2.  In the box, type "ubuntu-bug gnome-panel"  (not sure if "gnome-panel" will work.  If that doesn't work, just report "gnome".)

That will collect and generate all the files the developers need to address the bug. On the launchpad page, add some reasonable text describing the behavior you are seeing -- what you do, what you expect and what actually happens.

Be civil.  You catch more flies with honey than with vinegar.  If the developers have a choice between someone's nasty message and another asking for help politely, which do you think they will choose to look at first?

---

### Post by X5-655 on 2010-08-20
Well I'm already on the verge of going back to Windows 7 on this laptop.

I'll try the bug reporter.  I use the latest fglrx driver ATI has available to download..  It did it before, with the latest offered by Ubuntu..

Laptop:
AMD Athlon II M300 Dual Core 2GHz
4GB RAM, 250GB Hard Drive
ATI Radeon 4200

---

### Post by ScarletWyvern on 2010-08-20
Seriously.

Just because GNOME  or gnome-panel aren't working for you, don't blow off Linux all together.

Install something else like Kubuntu or Crunchbang, or just install a different desktop environment on your current install.

---

### Post by X5-655 on 2010-08-21
> **ScarletWyvern said:**
> Seriously.

Just because GNOME  or gnome-panel aren't working for you, don't blow off Linux all together.

Install something else like Kubuntu or Crunchbang, or just install a different desktop environment on your current install.
There's MANY other issues that are turning me away, and the fact that I just can't get any help from anyone on them.

Here's a list of bugs I have, all at a fresh install:
1. Sleep Mode don't work..  It goes to sleep, and won't wake up..  I have to pull the battery because holding down the power button while it turns off, EFI never turns back on to post and never boots.  Windows doesn't have this issue.

2. This gnome panel bug, and I refuse to use anything other than Gnome, because I'm all about a GUI looking nice, and Gnome looks nice to me.

3.  FGLRX have problems with tearing.  Games don't seem to have it, but the desktop does, including DVD's and anything else..  NOTHING worked, and nearly everyone else with FGLRX has this problem..  Proprietary driver is the only driver that gives me OpenGL.

4.  Mouse cursors won't change if you use Compiz.  The workaround is way too much and shouldn't have to be done, I'm all about software that don't need hacking to work right.

Quite a bit more than this gnome panel bug, but it's just all added up for me.  Sleep mode and FGLRX tearing are the biggest problem for me, and honestly, Windows 7 Aero just looks better to me, especially with Firefox 4..  I'm seriously possibly reformatting tomorrow and going back to Windows.

---

### Post by QIII on 2010-08-21
That is, of course, the power of choice.  And there should be no ill will from this community if you make that choice.

The very legitimate difficulties you have had point to something that needs to be fixed.  

Perhaps you might be persuaded to reinstall Windows, install Ubuntu again as a dual boot and then help us sort this out?

---

### Post by X5-655 on 2010-08-21
All the bugs I reported though are bugs others have reported though..  And the fact they all occur on fresh installs for me point to a bug in the distro..

I really don't have the time or patience to figure it out..  I'm still tinkering with linux though right now..  I may stay a little longer, but I am missing Windows 7..

---

### Post by HeadHunter00 on 2010-08-21
> **QIII said:**
> Can you give us some hardware information?  What version of the fglrx driver are you using?  I didn't see anything there that jumped out in my lap (I'll look more closely if I get the chance), so I don't know what else I can suggest.

I'm not saying it isn't a bug, but it is not happening to me or to many, many other users, so it is not generalized.  It may be something that occurs with some particular hardware configuration.  In any case, it does need to be addressed.

By the way, the bug reported on launchpad will not likely be dealt with as is.  It is marked as incomplete.  That means there is not enough information provided for anyone to work on it.

I think you are having a problem specifically with gnome-panel rather than GNOME in general.

Search launchpad first for a complete bug report.  If there is one, add your "this affects me too".  

If you do not find one, click ALT+F2.  In the box, type "ubuntu-bug gnome-panel"  (not sure if "gnome-panel" will work.  If that doesn't work, just report "gnome".)

That will collect and generate all the files the developers need to address the bug. On the launchpad page, add some reasonable text describing the behavior you are seeing -- what you do, what you expect and what actually happens.

Be civil.  You catch more flies with honey than with vinegar.  If the developers have a choice between someone's nasty message and another asking for help politely, which do you think they will choose to look at first?
It isn't a hardware issue. Trust me. Happens on all three, intel, ati, and nvidia. But a common bug. Although strange thing is that this happens a lot less in ubuntu 10.04. hmmmmm... maybe, it's the driver version. Did you try using the x-swat repository? maybe that's what solved my problem. Add This to your software sources and then update**: ppa:ubuntu-x-swat/x-updates**

---

### Post by HeadHunter00 on 2010-08-21
Although, this may be disloyal to ubuntu, but you can try using arch linux. Its a minimalistic distro in which you start out with no GUI, but you can build that up. Be sure to follow this guide, or you will get really messed up: [http://wiki.archlinux.org/index.php/Beginners%27_Guide]("http://wiki.archlinux.org/index.php/Beginners%27_Guide")
Stay with arch linux for a while and then you will start realizing how linux works. Basically, it's like a boot camp. Remember though, linux is different from windblows. If you need any help, ask me. BTW, here's one gud advice for you. Co-operate more. You are just whining.

---

### Post by HeadHunter00 on 2010-08-21
> **X5-655 said:**
> There's MANY other issues that are turning me away, and the fact that I just can't get any help from anyone on them.

Here's a list of bugs I have, all at a fresh install:
1. Sleep Mode don't work..  It goes to sleep, and won't wake up..  I have to pull the battery because holding down the power button while it turns off, EFI never turns back on to post and never boots.  Windows doesn't have this issue.

2. This gnome panel bug, and I refuse to use anything other than Gnome, because I'm all about a GUI looking nice, and Gnome looks nice to me.

3.  FGLRX have problems with tearing.  Games don't seem to have it, but the desktop does, including DVD's and anything else..  NOTHING worked, and nearly everyone else with FGLRX has this problem..  Proprietary driver is the only driver that gives me OpenGL.

4.  Mouse cursors won't change if you use Compiz.  The workaround is way too much and shouldn't have to be done, I'm all about software that don't need hacking to work right.

Quite a bit more than this gnome panel bug, but it's just all added up for me.  Sleep mode and FGLRX tearing are the biggest problem for me, and honestly, Windows 7 Aero just looks better to me, especially with Firefox 4..  I'm seriously possibly reformatting tomorrow and going back to Windows.
1. In linux, you have to press the power button to get out of the sleep state. Plus if you get stuck, you can always press ctrl+alt+f1 and then use this command: sudo killall gnome-screensaver
2. KDE looks way nicer, different colours, but hey, you can change that. After all customizability is what linux is all about. Gnome is for people who like the mac interface, like me.
3. Why not use catalyst? Get rid of fglrx from synaptics and install catalyst.
4. Easy fix. Just use this command: sudo gedit /usr/share/icons/default/index.theme and then change the name to whatever cursor you want. Or, since you can't or don't want to "hack", I made a shell script for you.

So, you're fond of aero eh? yah then you should use kde, it has a windows 7 feel. Plus, if you want you can use this to make kde look exactly like win7 [http://kde-look.org/content/show.php/Vistar7+-+Windows+7+Transformation+Pack?content=104232&PHPSESSID=f3c10decb7c33928ce413f9dd8914f87](http://kde-look.org/content/show.php/Vistar7+-+Windows+7+Transformation+Pack?content=104232&PHPSESSID=f3c10decb7c33928ce413f9dd8914f87)
Instructions to install this are right on the page.

---

### Post by X5-655 on 2010-08-21
> **HeadHunter00 said:**
> 1. In linux, you have to press the power button to get out of the sleep state. Plus if you get stuck, you can always press ctrl+alt+f1 and then use this command: sudo killall gnome-screensaver
2. KDE looks way nicer, different colours, but hey, you can change that. After all customizability is what linux is all about. Gnome is for people who like the mac interface, like me.
3. Why not use catalyst? Get rid of fglrx from synaptics and install catalyst.
4. Easy fix. Just use this command: sudo gedit /usr/share/icons/default/index.theme and then change the name to whatever cursor you want. Or, since you can't or don't want to "hack", I made a shell script for you.

So, you're fond of aero eh? yah then you should use kde, it has a windows 7 feel. Plus, if you want you can use this to make kde look exactly like win7 [http://kde-look.org/content/show.php/Vistar7+-+Windows+7+Transformation+Pack?content=104232&PHPSESSID=f3c10decb7c33928ce413f9dd8914f87](http://kde-look.org/content/show.php/Vistar7+-+Windows+7+Transformation+Pack?content=104232&PHPSESSID=f3c10decb7c33928ce413f9dd8914f87)
Instructions to install this are right on the page.
1.  You didn't understand, the laptop gets STUCK getting out of sleep.  Do a Google, it's a common problem.  And to get out of sleep is more of a BIOS thing, which for mine it's the power button anyway.  You can't throw it any commands because the keyboard is never waken up either (no response to ANYTHING).

2.  If I wanted KDE I would have used Kubuntu but I wanted Gnome.  KDE still feels too ugly for me.

3.  What?  Isn't FGLRX Catalyst Control Center?  If your talking about the Open Source driver, I think I already said the Open Source Driver doesn't work, has no OpenGL and I can't do anything.

4.  Thanks.

---

### Post by HeadHunter00 on 2010-08-21
> **X5-655 said:**
> 1.  You didn't understand, the laptop gets STUCK getting out of sleep.  Do a Google, it's a common problem.  And to get out of sleep is more of a BIOS thing, which for mine it's the power button anyway.  You can't throw it any commands because the keyboard is never waken up either (no response to ANYTHING).

2.  If I wanted KDE I would have used Kubuntu but I wanted Gnome.  KDE still feels too ugly for me.

3.  What?  Isn't FGLRX Catalyst Control Center?  If your talking about the Open Source driver, I think I already said the Open Source Driver doesn't work, has no OpenGL and I can't do anything.

4.  Thanks.
1. Oh ok. I will look into it. I looked into it and found this link. There seems to be some sort of script that fixes the problem [http://ubuntuforums.org/showthread.php?t=1281130](http://ubuntuforums.org/showthread.php?t=1281130) Also, if this doesn't work, I will try making you a shell script that kills gnome-screensaver and then respawns it once, you are back.
2. Try the hack, eh? Makes KDE look exactly like windows 7.
3. FGLRX is the opensource driver. Catalyst is the official ati proprietary driver, not a control center. BTW, use the x-swat repository. Also, ati doesn't have gud support in linux. So, if thats the reson you switch, I can understand.
4. No problem, mate.

---

### Post by Quackers on 2010-08-21
During my various OS installs I have come across some of your problems.
In the case of sleep/hibernate problems it seems to me to be often caused by smbios needing to be changed. The DSDT (part of bios) is also commonly the cause of many problems and is often because it has been poorly written by the hardware manufacturer (HP seem to be the worst offender). When installing Mac OS X I had to make alterations to the DSDT.aml just to get sound working. In the same installation as soon as I got my graphics card recognised the screen went black. This is because the way Sony laptops speak to their screens, and at the moment this problem is insurmountable, so vesa is the only way I can get a display. That means no fancy visual effects, but I have to accept that. Tearing and artefacts is usually a graphics driver or framebuffer issue.
Have you tried running Ubuntu without the current ATI driver, just as a test? Does anything work better then?
You can change some of the features in Power Management, have a look at that.

---

### Post by dino99 on 2010-08-21
if you want to stay out of troubles, dont use third party and untrusted ppa, and dont run ati/nvidia command, only use genuine ubuntu repo and for graphic driver you can add x-swat ppa to your synaptic repo

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

as actual kernels directly deals with X, remove xorg.conf, as many issues are due to an old xorg config

---

### Post by X5-655 on 2010-08-21
> **dino99 said:**
> if you want to stay out of troubles, dont use third party and untrusted ppa, and dont run ati/nvidia command, only use genuine ubuntu repo and for graphic driver you can add x-swat ppa to your synaptic repo

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

as actual kernels directly deals with X, remove xorg.conf, as many issues are due to an old xorg config
But then I loose OpenGL..  I said this many MANY times now..  So I'm supposed to loose OpenGL just to be "genuine"?

---

### Post by HeadHunter00 on 2010-08-21
How will you lose opengl? I don't understand. Your graphics card has opengl enabled by default. Maybe you should compile your the latest kernel and tell it to reconfigure X. But, if don't have time, then you can use kernelcheck from here: [http://ubuntuforums.org/showpost.php?p=9133861&postcount=500](http://ubuntuforums.org/showpost.php?p=9133861&postcount=500)
Using kernelcheck, compile the kernel using custom compilation and enable reconfigure x server option. After the kernel has been compiled, do this: 1. cd /boot 2. sudo mkinitramfs -o initrd.img-2.6.35.3-candela 2.6.35.3-candela 3. sudo update-grub

---

### Post by X5-655 on 2010-08-21
Whenever I use any other ATI driver other than FGLRX, OpenGL apps load with just a white window and no picture..  OpenGL just doesn't exist on my graphics chip other than FGLRX.

ATI Radeon Mobility 4200..

---

### Post by QIII on 2010-08-21
> **HeadHunter00 said:**
> It isn't a hardware issue. Trust me. Happens on all three, intel, ati, and nvidia. 

We haven't established that it is even GPU related, actually.  I said "hardware configuration".   That is somewhat more complex than looking at one particular component.  Furthermore, I did not say that is what it was.  I suggested that as a possibility.  If that is the problem, that is this occurs with a particular hardware configuration, then it may still be a "bug" in that some consideration in the code was overlooked.

As for "common": how do you define that?  Any use of this forum or launchpad as a measure of frequency of occurrence is doomed by bias.

If we see 100 or even 1000 complaints, it is easy to jump to the conclusion that it is "common".   The problem, however, is that those who* do not* encounter this issue *do not* come to this forum to complain that they *do not *have the problem and they *do not* report that they *do not *have the problem on launchpad. 

Since we know neither how many Ubuntu users there are nor how many actually have this problem, we cannot say whether or not it is common.

If 1000 people encounter this problem and there are 5,000,000 users, then the incidence of this problem is 1 per 5000.  Is that common?  (That doesn't mean that it doesn't suck in any particular person's case.  I suffer from a rare disease, but the fact that it is rare does not make it suck any less *for me*!)

The important thing is not whether this is a "common" problem, but that someone IS having the problem and would like it to be fixed.

Failing that, any user has every right to be exasperated and find an OS that does work for him.  There's nothing at all wrong with that.  He should use what works.

However, I do wish you would take at least a fraction of your time, X5-655, however little that is, and dual boot to let us know how things are going and whether we can resolve this issue.  That is really how the user effects the final product in this community.

---

### Post by X5-655 on 2010-08-22
Ok, trying KDE.

Lets fix THIS bug.

[http://img.photobucket.com/albums/v395/Evilweredragon/error-1.png](http://img.photobucket.com/albums/v395/Evilweredragon/error-1.png)

I have internet connectivity..

Also, another bug is that I keep getting asked a KWallet thing for a password at every login..  Annoying!

---

### Post by X5-655 on 2010-08-22
The most important bug being the update not found.

I found a workaround for the password at login, make the kwallet password blank..  NOT secure, but the only thing that worked.

---

### Post by X5-655 on 2010-08-22
Ok so the sleep mode bug STILL affects KDE..  Goes to sleep, doesn't wake..  This problem has been widely reported, especially for laptops..

Thing is, in Gnome, I have to right click on the network icon to enable networking, cause for some reason, after the sleep bug, it's disabled.  Well in KDE, guess what, nowhere to be found is this enable option, so it just says Networking disabled, and "Unmanaged"..  I had to go BACK into Gnome.

Screw this..  Try all you want to keep me on Linux, but it's still not matured enough yet to be used daily..

---

### Post by brr872002 on 2010-08-22
> **X5-655 said:**
> Ok so the sleep mode bug STILL affects KDE..  Goes to sleep, doesn't wake..  This problem has been widely reported, especially for laptops..

Thing is, in Gnome, I have to right click on the network icon to enable networking, cause for some reason, after the sleep bug, it's disabled.  Well in KDE, guess what, nowhere to be found is this enable option, so it just says Networking disabled, and "Unmanaged"..  I had to go BACK into Gnome.

Screw this..  Try all you want to keep me on Linux, but it's still not matured enough yet to be used daily..

something gone wrong in system configuration " Maturity comes after practice child never starts running after his first step" .Try to reinstall from scratch ,Don't for get to backup important files. I formated my HDD 10 time when  Started using RH 7.00 2001 PIII 500 mHZ

!!!!!! Linux Geek Redhat 7.7.2 8. fedora core  to fedora 10. !!!!!!!!! p4 2.66 Ghz 1GB RAM MULTIBOOT 8.04 LTS 10.4 LTS. WINDOWS 7 FEDORA 12!!!!!!!!!!!!!!!!!!!!!111

---

### Post by X5-655 on 2010-08-23
But it IS a fresh install!  How can it be so screwed up from the start?  Linux has been around for FAR enough to have matured..  I mean come on, it's horrible..

Even the LIVE CD crashes on sleep mode the same way!!

Oh, and when I switched to KDM, when logging out, the whole login screen is corrupted.  I'm in NO way dealing with it..  Windows 7 disc is being placed in the drive as I type this.

---

### Post by X5-655 on 2010-08-23
Ok well it turns out my HP recovery disc isn't working, and am stuck with this linux mess.

So I'll give you guys one chance to fix atleast this logout corruption bug.  If this bug can be fixed I'll stay with Linux some more..

Steps to reproduce it:  Install Kubuntu ontop of Ubuntu, switch from GDM to KDM, and viola, logout from KDE is corrupted.

If I use GDM to login to KDE, there's no way to shut down the laptop, literally..  No shutdown button..

---

### Post by X5-655 on 2010-08-23
See?  Only with KDM..

IT DOES THIS ON THE LIVE CD!!  So please don't anyone say it's a configuration file problem.

Cold Boot Login:
[IMG]http://img.photobucket.com/albums/v395/Evilweredragon/Screenshot2010-08-23at122943PM.png[/IMG]

Logon Off After Logging On:
[IMG]http://img.photobucket.com/albums/v395/Evilweredragon/Screenshot2010-08-23at123158PM.png[/IMG]

The Logon Screen Now:
[img]http://img.photobucket.com/albums/v395/Evilweredragon/Screenshot2010-08-23at123209PM.png[/img]

My Desktop When I Log Back In:
[IMG]http://img.photobucket.com/albums/v395/Evilweredragon/Screenshot2010-08-23at123457PM.png[/IMG]

Control+Alt F2 yields an ok looking terminal screen.  Going back to Control+Alt F7 brings the graphical corruption again.

---

### Post by X5-655 on 2010-08-23
HP Recovery Kit on order.

Go ahead guys, one last chance.  Help me fix this logout glitch, or I will be reinstalling Windows when the HP recovery kit arrives.

MANY MANY MANY bugs, and all you guys so far was point fingers and give no true solution, except one guy who did help me switch mouse cursors.

---

### Post by X5-655 on 2010-08-23
Ok, AuroraOS will be my selected OS when it becomes a stable release.

Debian worked fine in sleep mode, but Ubuntu doesn't, and Aurora is more debian based, so it'll probably work.

I don't dis the linux kernel, it's rock solid, but I do dis the distro.

---

### Post by brr872002 on 2010-08-23
The problem is with graphic card, Pl. try this ,
[http://www.x.org/wiki/radeonBuildHowTo](http://www.x.org/wiki/radeonBuildHowTo)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/569372](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/569372)

Use alternate install insted of liveCd
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by X5-655 on 2010-08-23
I actually gave up with KDE, I found it rather slow, too slow for my tastes..  But what I did find was how to enhance Gnome and it looks super "sexy" for a lack of a better word, right now.

Only ONE problem remains:  I can NOT resume from sleep mode.  I made a bug report here:  [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/621593](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/621593)

That's the last and only remaining bug I have left..

My GUI setup:  [http://img.photobucket.com/albums/v395/Evilweredragon/gnomesetup.png](http://img.photobucket.com/albums/v395/Evilweredragon/gnomesetup.png)

Honestly, I love this look FAR better than my Mac or Windows 7..  So if we can nail this ACPI bug, i'll be happy and contempt with Linux..

---

### Post by brr872002 on 2010-08-24
You try to google it 
[https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement)
[https://launchpad.net/ubuntu/+source/acpi-support/0.136.1](https://launchpad.net/ubuntu/+source/acpi-support/0.136.1)

---

### Post by X5-655 on 2010-08-24
Already running those packages.  And don't think for a second I didn't Google this..  That's why I resorted to asking.

But seriously, I'm finding the debian community more helpful than Ubuntu, and I don't even have a true debian distro!

---

