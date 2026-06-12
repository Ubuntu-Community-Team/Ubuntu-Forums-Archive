---
title: "Freeze on/before login and touchpad issues"
date: 2011-01-13
forum: General Help
---

### Post by Ziyan Junaideen on 2011-01-13
Hi,

I installed Ubuntu 10.1 (64 bit) in my HP laptop and it looked really cool. But now I am having problems with it.

If I turn off the Touch Pad button, the menus and Windows of Ubuntu will freeze and I will have to restart. I'd even noticed it happen without the touch pad been off.

It also started freezing after the login screen (after I enter my credentials, the screen will disappear and be just like that). Some times the music at start up keep playing in a loop.

Now it even freezes before the login screen. I tried like 10 time in a row and failed. Some how booted once and now I am keeping it without shut down until my exams finish.:(

Wine, TeX, Apache, MySQL, Wine are some of the recently installed programs. I tryed removing Wine, but it didn't do any help.

Any one have any Ideas on what I should do...

---

### Post by amsterdamharu on 2011-01-13
If you have a cabled Internet the first thing you can try is getting into the start menu. When you switch on the computer and press shift (or arrow down key) you will get a menu (not the BIOS settings). In that menu there is an option Ubuntu ... recovery.

Choose that and select dpkg reconfigure.


When it crashes again try to post the (your ubuntu install)var/log/kern.log
You might have to start up from an Ubuntu CD (choose try Ubuntu) then go to the disk/partition where your Ubuntu is installed and find the (your ubuntu install)var/log/kern.log
Copy and paste the content here.

When pasting it here please wrap it in &#91;code] &#91;/code] tags. In other words: &#91;code]Your pasted stuff&#91;/code]

---

### Post by Ziyan Junaideen on 2011-01-14
Thanks for the reply,amsterdamharu. I tried the Repair Package thing, but it didn't work. Got stuck again.

I got the log file, and its massive. I tried posting it here, but there is a 60s time out in the server and fails to load. So I took the log for the last 1.5 hours and it is as follows.

```

Jan 14 14:22:08 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [  505.910195] usb 4-2: new low speed USB device using uhci_hcd and address 2
Jan 14 14:22:09 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [  506.150986] usbcore: registered new interface driver hiddev
Jan 14 14:22:09 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [  506.164034] input: SIGMACH1P U+P Mouse as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input12
Jan 14 14:22:09 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [  506.164297] generic-usb 0003:1C4F:0003.0001: input,hidraw0: USB HID v1.10 Mouse [SIGMACH1P U+P Mouse] on usb-0000:00:1a.1-2/input0
Jan 14 14:22:09 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [  506.164338] usbcore: registered new interface driver usbhid
Jan 14 14:22:09 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [  506.164343] usbhid: USB HID core driver
Jan 14 14:36:02 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: Kernel logging (proc) stopped.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Linux version 2.6.35-24-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 (Ubuntu 2.6.35-24.42-generic 2.6.35.8)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=5a8fd198-0462-4cf9-ae23-14c37362140d ro quiet splash
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fca8000 (usable)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 000000007fca8000 - 000000007fcbf000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 000000007fcbf000 - 000000007fd81000 (usable)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 000000007fd81000 - 000000007fdbf000 (ACPI NVS)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 000000007fdbf000 - 000000007fddf000 (usable)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 000000007fddf000 - 000000007fdf7000 (ACPI data)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 000000007fdf7000 - 000000007fe00000 (usable)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 000000007fe00000 - 0000000080000000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] NX (Execute Disable) protection: active
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] DMI 2.4 present.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] No AGP bridge found
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] last_pfn = 0x7fe00 max_arch_pfn = 0x400000000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] MTRR default type: uncachable
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] MTRR fixed ranges enabled:
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   00000-9FFFF write-back
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   A0000-BFFFF uncachable
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   C0000-FFFFF write-protect
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] MTRR variable ranges enabled:
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   1 base 040000000 mask FC0000000 write-back
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   2 base 0FFE00000 mask FFFE00000 write-protect
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   3 disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   4 disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   5 disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   6 disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] e820 update range: 0000000000001000 - 0000000000010000 (usable) ==> (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] modified physical RAM map:
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 0000000000010000 - 000000000009e000 (usable)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 0000000000100000 - 000000007fca8000 (usable)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 000000007fca8000 - 000000007fcbf000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 000000007fcbf000 - 000000007fd81000 (usable)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 000000007fd81000 - 000000007fdbf000 (ACPI NVS)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 000000007fdbf000 - 000000007fddf000 (usable)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 000000007fddf000 - 000000007fdf7000 (ACPI data)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 000000007fdf7000 - 000000007fe00000 (usable)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 000000007fe00000 - 0000000080000000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000007fe00000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  0000000000 - 007fe00000 page 2M
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] kernel direct mapping tables up to 7fe00000 @ 16000-19000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] RAMDISK: 37570000 - 37ff0000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HPQOEM)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: XSDT 000000007fdf6120 0006C (v01 HPQOEM SLIC-MPC 00000001      01000013)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: FACP 000000007fdf4000 000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: DSDT 000000007fde2000 0D37A (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: FACS 000000007fd8d000 00040
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: DMAR 000000007fdf5000 00040 (v01               ? 00000001      00000000)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: HPET 000000007fdf3000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: APIC 000000007fdf2000 0006C (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: MCFG 000000007fdf1000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: ASF! 000000007fdf0000 000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: SLIC 000000007fde1000 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: BOOT 000000007fde0000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: SSDT 000000007fddf000 00655 (v01  PmRef    CpuPm 00003000 INTL 20051117)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] No NUMA configuration found
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Faking a node at 0000000000000000-000000007fe00000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000007fe00000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   NODE_DATA [0000000001d18200 - 0000000001d1d1ff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880002600000-ffff8800041fffff] on node 0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Zone PFN ranges:
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   Normal   empty
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Movable zone start PFN for each node
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] early_node_map[5] active PFN ranges
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]     0: 0x00000100 -> 0x0007fca8
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]     0: 0x0007fcbf -> 0x0007fd81
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]     0: 0x0007fdbf -> 0x0007fddf
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]     0: 0x0007fdf7 -> 0x0007fe00
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] On node 0 totalpages: 523553
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   DMA zone: 0 pages reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   DMA zone: 3926 pages, LIFO batch:0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   DMA32 zone: 7105 pages used for memmap
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   DMA32 zone: 512466 pages, LIFO batch:31
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] nr_irqs_gsi: 40
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] early_res array is doubled to 64 at [17000 - 177ff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] PM: Registered nosave memory: 000000007fca8000 - 000000007fcbf000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] PM: Registered nosave memory: 000000007fd81000 - 000000007fdbf000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] PM: Registered nosave memory: 000000007fddf000 - 000000007fdf7000
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:78000000)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] early_res array is doubled to 128 at [17800 - 187ff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 516392
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Policy zone: DMA32
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=5a8fd198-0462-4cf9-ae23-14c37362140d ro quiet splash
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Checking aperture...
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] No AGP bridge found
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ------------[ cut here ]------------
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] WARNING: at /build/buildd/linux-2.6.35/drivers/pci/dmar.c:633 warn_invalid_dmar+0x8f/0xa0()
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Hardware name: HP Pavilion dv6 Notebook PC
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Your BIOS is broken; DMAR reported at address 0!
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] BIOS vendor: Hewlett-Packard; Ver: F.36; Product Version: Rev 1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Modules linked in:
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Pid: 0, comm: swapper Not tainted 2.6.35-24-generic #42-Ubuntu
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Call Trace:
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  [<ffffffff8106089f>] warn_slowpath_common+0x7f/0xc0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  [<ffffffff81593e03>] ? _etext+0x0/0x1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  [<ffffffff8106093f>] warn_slowpath_fmt_taint+0x3f/0x50
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  [<ffffffff812eeb0f>] warn_invalid_dmar+0x8f/0xa0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  [<ffffffff81af91e2>] ? __acpi_map_table+0x17/0x19
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  [<ffffffff81b1a0d7>] check_zero_address+0x62/0x11e
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  [<ffffffff8132cbab>] ? acpi_get_table_with_size+0x5a/0xb4
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  [<ffffffff81593e03>] ? _etext+0x0/0x1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  [<ffffffff81b1a1a5>] detect_intel_iommu+0x12/0x69
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  [<ffffffff81af488c>] pci_iommu_alloc+0x1c/0x28
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  [<ffffffff81b03f8f>] mem_init+0x19/0xec
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  [<ffffffff81af2064>] ? trap_init+0x1e2/0x1e9
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  [<ffffffff81aedab4>] start_kernel+0x19e/0x390
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  [<ffffffff81aed341>] x86_64_start_reservations+0x12c/0x130
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]  [<ffffffff81aed43f>] x86_64_start_kernel+0xfa/0x109
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] ---[ end trace a7919e7f17c0a725 ]---
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Disabling lock debugging due to kernel taint
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Subtract (57 early reservations)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #2 [0037570000 - 0037ff0000]         RAMDISK
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #3 [000009e000 - 0000100000]   BIOS reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #4 [0001d18000 - 0001d181f8]             BRK
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #5 [0000010000 - 0000012000]      TRAMPOLINE
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #6 [0000012000 - 0000016000]     ACPI WAKEUP
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #7 [0000016000 - 0000017000]         PGTABLE
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #8 [0001d18200 - 0001d1d200]       NODE_DATA
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #9 [0001d1d200 - 0001d1e200]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #10 [0001d17140 - 0001d172c0]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #11 [000251f000 - 0002520000]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #12 [0002520000 - 0002521000]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #13 [0002600000 - 0004200000]        MEMMAP 0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #14 [0001d172c0 - 0001d17440]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #15 [0001d1e200 - 0001d2a200]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #16 [0001d2b000 - 0001d2c000]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #17 [0001d17440 - 0001d17481]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #18 [0001d174c0 - 0001d17503]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #19 [0001d17540 - 0001d17968]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #20 [0001d17980 - 0001d179e8]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #21 [0001d17a00 - 0001d17a68]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #22 [0001d17a80 - 0001d17ae8]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #23 [0001d17b00 - 0001d17b68]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #24 [0001d17b80 - 0001d17be8]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #25 [0001d17c00 - 0001d17c68]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #26 [0001d17c80 - 0001d17ce8]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #27 [0001d17d00 - 0001d17d68]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #28 [0001d17d80 - 0001d17de8]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #29 [0001d17e00 - 0001d17e68]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #30 [0001d17e80 - 0001d17ee8]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #31 [0001d17f00 - 0001d17f68]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #32 [0001d17f80 - 0001d17fe8]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #33 [0001d2a200 - 0001d2a268]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #34 [0001d2a280 - 0001d2a2e8]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #35 [0001d2a300 - 0001d2a368]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #36 [0001d2a380 - 0001d2a3e8]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #37 [0001d2a400 - 0001d2a468]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #38 [0001d2a480 - 0001d2a4a0]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #39 [0001d2a4c0 - 0001d2a4e0]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #40 [0001d2a500 - 0001d2a520]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #41 [0001d2a540 - 0001d2a560]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #42 [0001d2a580 - 0001d2a5ea]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #43 [0001d2a600 - 0001d2a66a]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #44 [0001e00000 - 0001e1e000]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #45 [0001e80000 - 0001e9e000]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #46 [0001f00000 - 0001f1e000]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #47 [0001f80000 - 0001f9e000]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #48 [0001d2a680 - 0001d2a688]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #49 [0001d2a6c0 - 0001d2a6c8]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #50 [0001d2a700 - 0001d2a710]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #51 [0001d2a740 - 0001d2a760]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #52 [0001d2a780 - 0001d2a8b0]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #53 [0001d2a8c0 - 0001d2a910]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #54 [0001d2a940 - 0001d2a990]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #55 [0001d2c000 - 0001d34000]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000]   #56 [0001d2a9c0 - 0001d2ac00]         BOOTMEM
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Memory: 2040752k/2095104k available (5711k kernel code, 892k absent, 53460k reserved, 5379k data, 908k init)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Hierarchical RCU implementation.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] 	RCU-based detection of stalled CPUs is disabled.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] 	Verbose stalled-CPUs detection is disabled.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] NR_IRQS:4352 nr_irqs:712
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Console: colour VGA+ 80x25
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] console [tty0] enabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] allocated 20971520 bytes of page_cgroup
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] hpet clockevent registered
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Fast TSC calibration using PIT
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.000000] Detected 2260.833 MHz processor.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.010010] Calibrating delay loop (skipped), value calculated using timer frequency.. 4521.66 BogoMIPS (lpj=22608330)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.010014] pid_max: default: 32768 minimum: 301
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.010038] Security Framework initialized
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.010057] AppArmor: AppArmor initialized
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.010059] Yama: becoming mindful.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.010294] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.011384] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.011876] Mount-cache hash table entries: 256
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012009] Initializing cgroup subsys ns
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012014] Initializing cgroup subsys cpuacct
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012017] Initializing cgroup subsys memory
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012025] Initializing cgroup subsys devices
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012027] Initializing cgroup subsys freezer
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012029] Initializing cgroup subsys net_cls
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012058] CPU: Physical Processor ID: 0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012059] CPU: Processor Core ID: 0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012062] mce: CPU supports 6 MCE banks
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012069] CPU0: Thermal monitoring enabled (TM2)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012074] using mwait in idle threads.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012076] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012083] ... version:                2
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012084] ... bit width:              40
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012086] ... generic registers:      2
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012088] ... value mask:             000000ffffffffff
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012089] ... max period:             000000007fffffff
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012091] ... fixed-purpose events:   3
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.012092] ... event mask:             0000000700000003
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.014648] ACPI: Core revision 20100428
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.030011] ftrace: converting mcount calls to 0f 1f 44 00 00
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.030016] ftrace: allocating 22678 entries in 89 pages
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.040065] DMAR: Host address width 36
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.040068] DMAR: DRHD base: 0x00000000000000 flags: 0x1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.040070] DMAR: parse DMAR table failure.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.040073] Setting APIC routing to flat
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.040385] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.140452] CPU0: Intel(R) Core(TM)2 Duo CPU     P7550  @ 2.26GHz stepping 0a
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.150000] Booting Node   0, Processors  #1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.310014] Brought up 2 CPUs
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.310018] Total of 2 processors activated (9043.67 BogoMIPS).
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.310639] devtmpfs: initialized
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.310674] regulator: core version 0.5
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.310700] Time: 14:37:13  Date: 01/14/11
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.310735] NET: Registered protocol family 16
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.310755] Trying to unpack rootfs image as initramfs...
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.310855] ACPI: bus type pci registered
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.310925] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.310928] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.322679] PCI: Using configuration type 1 for base access
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.330112] bio: create slab <bio-0> at 0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.332287] ACPI: EC: Look up EC in DSDT
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.336893] ACPI: BIOS _OSI(Linux) query ignored
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.441349] ACPI: SSDT 000000007fcb4c98 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.441918] ACPI: Dynamic OEM Table Load:
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.441922] ACPI: SSDT (null) 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.442240] ACPI: SSDT 000000007fcb2618 005B3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.442791] ACPI: Dynamic OEM Table Load:
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.442793] ACPI: SSDT (null) 005B3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.443356] ACPI: SSDT 000000007fcb3e18 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.443938] ACPI: Dynamic OEM Table Load:
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.443941] ACPI: SSDT (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.444133] ACPI: SSDT 000000007fcb4f18 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.444695] ACPI: Dynamic OEM Table Load:
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.444698] ACPI: SSDT (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.448557] ACPI: Interpreter enabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.448557] ACPI: (supports S0 S3 S4 S5)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.448557] ACPI: Using IOAPIC for interrupt routing
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.460259] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.460530] ACPI: No dock devices found.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.460533] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.461174] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462182] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462185] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462187] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462191] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xfebfffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462266] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462269] pci 0000:00:01.0: PME# disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462350] pci 0000:00:1a.0: reg 20: [io  0x80e0-0x80ff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462429] pci 0000:00:1a.1: reg 20: [io  0x80c0-0x80df]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462507] pci 0000:00:1a.7: reg 10: [mem 0x9a105c00-0x9a105fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462571] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462576] pci 0000:00:1a.7: PME# disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462617] pci 0000:00:1b.0: reg 10: [mem 0x9a100000-0x9a103fff 64bit]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462668] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462672] pci 0000:00:1b.0: PME# disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462753] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462757] pci 0000:00:1c.0: PME# disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462839] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462843] pci 0000:00:1c.1: PME# disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462927] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.462931] pci 0000:00:1c.3: PME# disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463013] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463017] pci 0000:00:1c.4: PME# disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463102] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463106] pci 0000:00:1c.5: PME# disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463167] pci 0000:00:1d.0: reg 20: [io  0x80a0-0x80bf]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463245] pci 0000:00:1d.1: reg 20: [io  0x8080-0x809f]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463324] pci 0000:00:1d.2: reg 20: [io  0x8060-0x807f]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463404] pci 0000:00:1d.3: reg 20: [io  0x8040-0x805f]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463479] pci 0000:00:1d.7: reg 10: [mem 0x9a105800-0x9a105bff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463543] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463548] pci 0000:00:1d.7: PME# disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463744] pci 0000:00:1f.2: reg 10: [io  0x8108-0x810f]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463751] pci 0000:00:1f.2: reg 14: [io  0x8114-0x8117]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463757] pci 0000:00:1f.2: reg 18: [io  0x8100-0x8107]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463763] pci 0000:00:1f.2: reg 1c: [io  0x8110-0x8113]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463770] pci 0000:00:1f.2: reg 20: [io  0x8020-0x803f]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463777] pci 0000:00:1f.2: reg 24: [mem 0x9a105000-0x9a1057ff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463816] pci 0000:00:1f.2: PME# supported from D3hot
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463820] pci 0000:00:1f.2: PME# disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463854] pci 0000:00:1f.3: reg 10: [mem 0x9a106000-0x9a1060ff 64bit]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463870] pci 0000:00:1f.3: reg 20: [io  0x8000-0x801f]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.463925] pci 0000:00:1f.6: reg 10: [mem 0x9a104000-0x9a104fff 64bit]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464031] pci 0000:01:00.0: reg 10: [mem 0x80000000-0x8fffffff pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464039] pci 0000:01:00.0: reg 14: [io  0x7000-0x70ff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464046] pci 0000:01:00.0: reg 18: [mem 0x9a000000-0x9a00ffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464069] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464097] pci 0000:01:00.0: supports D1 D2
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464133] pci 0000:01:00.1: reg 10: [mem 0x9a010000-0x9a013fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464192] pci 0000:01:00.1: supports D1 D2
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464236] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464239] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464242] pci 0000:00:01.0:   bridge window [mem 0x9a000000-0x9a0fffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464247] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x8fffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464591] pci 0000:02:00.0: reg 10: [mem 0x99000000-0x99003fff 64bit]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464795] pci 0000:02:00.0: supports D1 D2
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464955] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464959] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464963] pci 0000:00:1c.0:   bridge window [mem 0x99000000-0x99ffffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.464971] pci 0000:00:1c.0:   bridge window [mem 0x90000000-0x90ffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465123] pci 0000:03:00.0: reg 10: [io  0x5000-0x50ff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465192] pci 0000:03:00.0: reg 18: [mem 0x91010000-0x91010fff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465241] pci 0000:03:00.0: reg 20: [mem 0x91000000-0x9100ffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465267] pci 0000:03:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465408] pci 0000:03:00.0: supports D1 D2
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465410] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465424] pci 0000:03:00.0: PME# disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465575] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465579] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465583] pci 0000:00:1c.1:   bridge window [mem 0x98000000-0x98ffffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465590] pci 0000:00:1c.1:   bridge window [mem 0x91000000-0x91ffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465640] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465644] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465648] pci 0000:00:1c.3:   bridge window [mem 0x97000000-0x97ffffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465655] pci 0000:00:1c.3:   bridge window [mem 0x92000000-0x92ffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465742] pci 0000:06:00.0: reg 10: [mem 0x96000000-0x960007ff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465754] pci 0000:06:00.0: reg 14: [mem 0x96000d00-0x96000d7f]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465784] pci 0000:06:00.0: reg 20: [mem 0x96000c80-0x96000cff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465795] pci 0000:06:00.0: reg 24: [mem 0x96000c00-0x96000c7f]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.465907] pci 0000:06:00.1: reg 10: [mem 0x96000b00-0x96000bff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.466045] pci 0000:06:00.2: reg 10: [mem 0x96000a00-0x96000aff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.466183] pci 0000:06:00.3: reg 10: [mem 0x96000900-0x960009ff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.466320] pci 0000:06:00.4: reg 10: [mem 0x96000800-0x960008ff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480034] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480040] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480044] pci 0000:00:1c.4:   bridge window [mem 0x96000000-0x96ffffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480052] pci 0000:00:1c.4:   bridge window [mem 0x93000000-0x93ffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480106] pci 0000:00:1c.5: PCI bridge to [bus 07-09]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480110] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480115] pci 0000:00:1c.5:   bridge window [mem 0x95000000-0x95ffffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480122] pci 0000:00:1c.5:   bridge window [mem 0x94000000-0x94ffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480197] pci 0000:00:1e.0: PCI bridge to [bus 0a-0a] (subtractive decode)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480202] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480206] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480213] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480216] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480218] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480221] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480223] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xfebfffff] (subtractive decode)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480275] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480565] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480671] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480845] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.480940] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.481048] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.481142] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.481296] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP6._PRT]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.492963] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.493112] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.493257] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.493400] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.493544] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.493688] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.493835] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.493979] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.494051] HEST: Table is not found!
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.494134] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.494140] vgaarb: loaded
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.494273] SCSI subsystem initialized
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.494357] libata version 3.00 loaded.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.494400] usbcore: registered new interface driver usbfs
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.494413] usbcore: registered new interface driver hub
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.494435] usbcore: registered new device driver usb
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.494642] ACPI: WMI: Mapper loaded
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.494645] PCI: Using ACPI for IRQ routing
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.494648] PCI: pci_cache_line_size set to 64 bytes
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.495182] reserve RAM buffer: 000000000009e000 - 000000000009ffff 
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.495185] reserve RAM buffer: 000000007fca8000 - 000000007fffffff 
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.495188] reserve RAM buffer: 000000007fd81000 - 000000007fffffff 
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.495190] reserve RAM buffer: 000000007fddf000 - 000000007fffffff 
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.495193] reserve RAM buffer: 000000007fe00000 - 000000007fffffff 
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.495274] NetLabel: Initializing
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.495276] NetLabel:  domain hash size = 128
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.495277] NetLabel:  protocols = UNLABELED CIPSOv4
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.495290] NetLabel:  unlabeled traffic allowed by default
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.495321] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.495326] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.495331] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.500030] Switching to clocksource tsc
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.509281] AppArmor: AppArmor Filesystem Enabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.509299] pnp: PnP ACPI init
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.509319] ACPI: bus type pnp registered
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.511987]   alloc irq_desc for 23 on node 0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.511990]   alloc kstat_irqs on node 0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512285] pnp: PnP ACPI: found 12 devices
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512287] ACPI: ACPI bus type pnp unregistered
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512298] system 00:00: [mem 0xf8000000-0xfbffffff] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512304] system 00:02: [io  0x164e-0x164f] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512307] system 00:02: [io  0x0600-0x060f] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512310] system 00:02: [io  0x0610] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512312] system 00:02: [io  0x0800-0x080f] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512315] system 00:02: [io  0x0810-0x0817] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512317] system 00:02: [io  0x0820-0x0823] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512320] system 00:02: [io  0x0400-0x047f] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512322] system 00:02: [io  0x0500-0x053f] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512324] system 00:02: [io  0x0380-0x038e] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512327] system 00:02: [mem 0xf8000000-0xfbffffff] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512330] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512332] system 00:02: [mem 0xfed10000-0xfed13fff] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512335] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512337] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512340] system 00:02: [mem 0xfec00000-0xfec00fff] could not be reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512343] system 00:02: [mem 0xfed20000-0xfed3ffff] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512345] system 00:02: [mem 0xfed40000-0xfed44fff] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512348] system 00:02: [mem 0xfed45000-0xfed8ffff] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.512350] system 00:02: [mem 0xfee00000-0xfee00fff] has been reserved
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518207] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518212] pci 0000:03:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518277] pci 0000:01:00.0: BAR 6: assigned [mem 0x9a020000-0x9a03ffff pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518280] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518283] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518286] pci 0000:00:01.0:   bridge window [mem 0x9a000000-0x9a0fffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518290] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x8fffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518295] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518298] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518303] pci 0000:00:1c.0:   bridge window [mem 0x99000000-0x99ffffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518308] pci 0000:00:1c.0:   bridge window [mem 0x90000000-0x90ffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518315] pci 0000:03:00.0: BAR 6: assigned [mem 0x91020000-0x9102ffff pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518318] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518321] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518326] pci 0000:00:1c.1:   bridge window [mem 0x98000000-0x98ffffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518331] pci 0000:00:1c.1:   bridge window [mem 0x91000000-0x91ffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518338] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518341] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518346] pci 0000:00:1c.3:   bridge window [mem 0x97000000-0x97ffffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518351] pci 0000:00:1c.3:   bridge window [mem 0x92000000-0x92ffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518359] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518362] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518367] pci 0000:00:1c.4:   bridge window [mem 0x96000000-0x96ffffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518372] pci 0000:00:1c.4:   bridge window [mem 0x93000000-0x93ffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518379] pci 0000:00:1c.5: PCI bridge to [bus 07-09]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518382] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518387] pci 0000:00:1c.5:   bridge window [mem 0x95000000-0x95ffffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518392] pci 0000:00:1c.5:   bridge window [mem 0x94000000-0x94ffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518399] pci 0000:00:1e.0: PCI bridge to [bus 0a-0a]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518400] pci 0000:00:1e.0:   bridge window [io  disabled]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518406] pci 0000:00:1e.0:   bridge window [mem disabled]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518410] pci 0000:00:1e.0:   bridge window [mem pref disabled]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518425]   alloc irq_desc for 16 on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518427]   alloc kstat_irqs on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518434] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518438] pci 0000:00:01.0: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518447]   alloc irq_desc for 17 on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518448]   alloc kstat_irqs on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518452] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518456] pci 0000:00:1c.0: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518465] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518469] pci 0000:00:1c.1: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518478]   alloc irq_desc for 19 on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518479]   alloc kstat_irqs on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518482] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518486] pci 0000:00:1c.3: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518495] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518500] pci 0000:00:1c.4: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518508] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518513] pci 0000:00:1c.5: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518520] pci 0000:00:1e.0: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518524] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518526] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518528] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518530] pci_bus 0000:00: resource 7 [mem 0x80000000-0xfebfffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518532] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518534] pci_bus 0000:01: resource 1 [mem 0x9a000000-0x9a0fffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518537] pci_bus 0000:01: resource 2 [mem 0x80000000-0x8fffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518539] pci_bus 0000:02: resource 0 [io  0x6000-0x6fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518541] pci_bus 0000:02: resource 1 [mem 0x99000000-0x99ffffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518543] pci_bus 0000:02: resource 2 [mem 0x90000000-0x90ffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518546] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518548] pci_bus 0000:03: resource 1 [mem 0x98000000-0x98ffffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518550] pci_bus 0000:03: resource 2 [mem 0x91000000-0x91ffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518552] pci_bus 0000:05: resource 0 [io  0x4000-0x4fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518554] pci_bus 0000:05: resource 1 [mem 0x97000000-0x97ffffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518557] pci_bus 0000:05: resource 2 [mem 0x92000000-0x92ffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518559] pci_bus 0000:06: resource 0 [io  0x3000-0x3fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518561] pci_bus 0000:06: resource 1 [mem 0x96000000-0x96ffffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518563] pci_bus 0000:06: resource 2 [mem 0x93000000-0x93ffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518566] pci_bus 0000:07: resource 0 [io  0x2000-0x2fff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518568] pci_bus 0000:07: resource 1 [mem 0x95000000-0x95ffffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518570] pci_bus 0000:07: resource 2 [mem 0x94000000-0x94ffffff 64bit pref]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518572] pci_bus 0000:0a: resource 4 [io  0x0000-0x0cf7]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518574] pci_bus 0000:0a: resource 5 [io  0x0d00-0xffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518576] pci_bus 0000:0a: resource 6 [mem 0x000a0000-0x000bffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518578] pci_bus 0000:0a: resource 7 [mem 0x80000000-0xfebfffff]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518616] NET: Registered protocol family 2
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.518722] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.519404] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.521463] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.522023] TCP: Hash tables configured (established 262144 bind 65536)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.522025] TCP reno registered
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.522033] UDP hash table entries: 1024 (order: 3, 32768 bytes)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.522055] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.522182] NET: Registered protocol family 1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.522566] pci 0000:01:00.0: Boot video device
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.522787] PCI: CLS 64 bytes, default 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.522828] Simple Boot Flag at 0x44 set to 0x1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.523001] Scanning for low memory corruption every 60 seconds
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.523172] audit: initializing netlink socket (disabled)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.523185] type=2000 audit(1295015832.510:1): initialized
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.536546] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.537857] VFS: Disk quotas dquot_6.5.2
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.537911] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.538415] fuse init (API version 7.14)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.538494] msgmni has been set to 3985
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.538732] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.538735] io scheduler noop registered
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.538737] io scheduler deadline registered
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.538771] io scheduler cfq registered (default)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.538883] pcieport 0000:00:01.0: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.538906]   alloc irq_desc for 40 on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.538908]   alloc kstat_irqs on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.538917] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.538986] pcieport 0000:00:1c.0: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539022]   alloc irq_desc for 41 on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539024]   alloc kstat_irqs on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539031] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539113] pcieport 0000:00:1c.1: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539150]   alloc irq_desc for 42 on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539151]   alloc kstat_irqs on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539159] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539241] pcieport 0000:00:1c.3: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539278]   alloc irq_desc for 43 on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539280]   alloc kstat_irqs on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539287] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539368] pcieport 0000:00:1c.4: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539405]   alloc irq_desc for 44 on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539407]   alloc kstat_irqs on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539414] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539498] pcieport 0000:00:1c.5: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539534]   alloc irq_desc for 45 on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539536]   alloc kstat_irqs on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539543] pcieport 0000:00:1c.5: irq 45 for MSI/MSI-X
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539644] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539664] Firmware did not grant requested _OSC control
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539674] Firmware did not grant requested _OSC control
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539683] Firmware did not grant requested _OSC control
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539692] Firmware did not grant requested _OSC control
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539701] Firmware did not grant requested _OSC control
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539709] Firmware did not grant requested _OSC control
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539730] Firmware did not grant requested _OSC control
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539738] Firmware did not grant requested _OSC control
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539747] Firmware did not grant requested _OSC control
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539755] Firmware did not grant requested _OSC control
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539764] Firmware did not grant requested _OSC control
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539772] Firmware did not grant requested _OSC control
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539779] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539876] intel_idle: MWAIT substates: 0x3122220
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.539879] intel_idle: does not run on family 6 model 23
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.540266] ACPI: AC Adapter [ACAD] (on-line)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.540344] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.540349] ACPI: Power Button [PWRB]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.540384] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.540678] ACPI: Lid Switch [LID0]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.540716] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.540720] ACPI: Sleep Button [SLPB]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.540771] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.540774] ACPI: Power Button [PWRF]
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.541251] ACPI: acpi_idle registered with cpuidle
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.548365] Freeing initrd memory: 10752k freed
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.552556] Monitor-Mwait will be used to enter C-1 state
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.552655] Monitor-Mwait will be used to enter C-2 state
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.552676] Monitor-Mwait will be used to enter C-3 state
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.552683] Marking TSC unstable due to TSC halts in idle
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.553095] Switching to clocksource hpet
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.558497] [Firmware Bug]: Invalid critical threshold (0)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.559786] thermal LNXTHERM:01: registered as thermal_zone0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.559794] ACPI: Thermal Zone [TZ01] (58 C)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.559868] ERST: Table is not found!
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.560193] Linux agpgart interface v0.103
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.560220] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.561677] brd: module loaded
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.562213] loop: module loaded
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.562669] Fixed MDIO Bus: probed
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.562699] PPP generic driver version 2.4.2
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.562748] tun: Universal TUN/TAP device driver, 1.6
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.562749] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.562816] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.562867] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.562881] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.562885] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.562913] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.562943] ehci_hcd 0000:00:1a.7: debug port 1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.566826] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.566843] ehci_hcd 0000:00:1a.7: irq 19, io mem 0x9a105c00
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.592837] ACPI: Battery Slot [BAT0] (battery present)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.600012] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.600121] hub 1-0:1.0: USB hub found
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.600125] hub 1-0:1.0: 4 ports detected
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.600194]   alloc irq_desc for 20 on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.600196]   alloc kstat_irqs on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.600203] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.600213] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.600217] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.600245] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.600273] ehci_hcd 0000:00:1d.7: debug port 1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.604152] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.604164] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x9a105800
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630011] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630092] hub 2-0:1.0: USB hub found
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630096] hub 2-0:1.0: 8 ports detected
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630169] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630181] uhci_hcd: USB Universal Host Controller Interface driver
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630232] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630239] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630242] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630272] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630303] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000080e0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630405] hub 3-0:1.0: USB hub found
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630409] hub 3-0:1.0: 2 ports detected
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630467]   alloc irq_desc for 21 on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630469]   alloc kstat_irqs on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630473] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630478] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630482] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630509] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630538] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000080c0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630637] hub 4-0:1.0: USB hub found
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630640] hub 4-0:1.0: 2 ports detected
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630696] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630702] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630705] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630741] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630764] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000080a0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630862] hub 5-0:1.0: USB hub found
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630867] hub 5-0:1.0: 2 ports detected
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630926] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630932] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630935] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630962] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.630985] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00008080
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631080] hub 6-0:1.0: USB hub found
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631084] hub 6-0:1.0: 2 ports detected
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631140] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631145] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631149] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631178] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631201] uhci_hcd 0000:00:1d.2: irq 16, io base 0x00008060
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631305] hub 7-0:1.0: USB hub found
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631309] hub 7-0:1.0: 2 ports detected
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631365]   alloc irq_desc for 18 on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631367]   alloc kstat_irqs on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631371] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631377] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631380] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631407] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631438] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00008040
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631538] hub 8-0:1.0: USB hub found
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631542] hub 8-0:1.0: 2 ports detected
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.631651] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.660581] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.660587] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.660644] mice: PS/2 mouse device common for all mice
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.660772] rtc_cmos 00:04: RTC can wake from S4
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.660802] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.660827] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.660915] device-mapper: uevent: version 1.0.3
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.660983] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.661038] device-mapper: multipath: version 1.1.1 loaded
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.661041] device-mapper: multipath round-robin: version 1.0.0 loaded
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.661219] cpuidle: using governor ladder
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.661970] cpuidle: using governor menu
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.662213] TCP cubic registered
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.662323] NET: Registered protocol family 10
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.662638] lo: Disabled Privacy Extensions
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.662809] NET: Registered protocol family 17
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.663385] PM: Resume from disk failed.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.663396] registered taskstats version 1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.664153]   Magic number: 11:86:637
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.664157] hub 6-0:1.0: hash matches
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.664246] rtc_cmos 00:04: setting system clock to 2011-01-14 14:37:14 UTC (1295015834)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.664249] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.664251] EDD information not available.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.664337] Freeing unused kernel memory: 908k freed
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.664620] Write protecting the kernel read-only data: 10240k
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.664795] Freeing unused kernel memory: 412k freed
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.665053] Freeing unused kernel memory: 1644k freed
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.678825] udev[81]: starting version 163
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.682791] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.738764] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.738807] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.738893] r8169 0000:03:00.0: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.739016]   alloc irq_desc for 46 on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.739018]   alloc kstat_irqs on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.739055] r8169 0000:03:00.0: irq 46 for MSI/MSI-X
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.739513] r8169 0000:03:00.0: eth0: RTL8168c/8111c at 0xffffc90000372000, 00:26:9e:97:b6:a6, XID 1c4000c0 IRQ 46
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.753194] sdhci: Secure Digital Host Controller Interface driver
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.753197] sdhci: Copyright(c) Pierre Ossman
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.755062] sdhci-pci 0000:06:00.1: SDHCI controller found [197b:2382] (rev 0)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.755087] sdhci-pci 0000:06:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.755125] sdhci-pci 0000:06:00.1: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.755155] Registered led device: mmc0::
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.796427] ahci 0000:00:1f.2: version 3.0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.796447] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.796493]   alloc irq_desc for 47 on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.796495]   alloc kstat_irqs on node -1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.796505] ahci 0000:00:1f.2: irq 47 for MSI/MSI-X
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.796555] ahci: SSS flag set, parallel bus scan disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.796586] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.796589] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems sxs 
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.796594] ahci 0000:00:1f.2: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.808492] mmc0: SDHCI controller on PCI [0000:06:00.1] using DMA
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.808512] sdhci-pci 0000:06:00.2: SDHCI controller found [197b:2381] (rev 0)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.808537] sdhci-pci 0000:06:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.808547] sdhci-pci 0000:06:00.2: Refusing to bind to secondary interface.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.808554] sdhci-pci 0000:06:00.2: PCI INT A disabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.808880] firewire_ohci 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.808887] firewire_ohci 0000:06:00.0: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.850180] scsi0 : ahci
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.850299] scsi1 : ahci
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.850363] scsi2 : ahci
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.850430] scsi3 : ahci
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.850501] scsi4 : ahci
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.850569] scsi5 : ahci
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.850758] ata1: SATA max UDMA/133 abar m2048@0x9a105000 port 0x9a105100 irq 47
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.850761] ata2: SATA max UDMA/133 abar m2048@0x9a105000 port 0x9a105180 irq 47
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.850763] ata3: DUMMY
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.850765] ata4: DUMMY
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.850767] ata5: SATA max UDMA/133 abar m2048@0x9a105000 port 0x9a105300 irq 47
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.850770] ata6: SATA max UDMA/133 abar m2048@0x9a105000 port 0x9a105380 irq 47
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    0.961287] firewire_ohci: Added fw-ohci device 0000:06:00.0, OHCI v1.10, 4 IR + 0 IT contexts, quirks 0x0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    1.090054] usb 2-4: new high speed USB device using ehci_hcd and address 3
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    1.401313] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    1.402218] ata1.00: ATA-8: ST9320423AS, 0006HPM1, max UDMA/100
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    1.402222] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    1.403351] ata1.00: configured for UDMA/100
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    1.420183] scsi 0:0:0:0: Direct-Access     ATA      ST9320423AS      0006 PQ: 0 ANSI: 5
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    1.420313] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    1.420381] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    1.420429] sd 0:0:0:0: [sda] Write Protect is off
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    1.420432] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    1.420452] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    1.420577]  sda:
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    1.450100] firewire_core: created device fw0: GUID 00241b000ff9ab01, S400
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    1.466335]  sda1 sda2 sda3 sda4 < sda5 sda6 >
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    1.503132] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    1.670034] usb 4-2: new low speed USB device using uhci_hcd and address 2
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    2.130035] usb 6-1: new full speed USB device using uhci_hcd and address 2
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    2.370038] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    2.374170] ata2.00: ATAPI: hp       DVDRAM GT20L, DC05, max UDMA/100
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    2.379049] ata2.00: configured for UDMA/100
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    2.403222] scsi 1:0:0:0: CD-ROM            hp       DVDRAM GT20L     DC05 PQ: 0 ANSI: 5
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    2.414468] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    2.414472] Uniform CD-ROM driver Revision: 3.20
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    2.414588] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    2.414637] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    2.570055] usb 7-2: new full speed USB device using uhci_hcd and address 2
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    2.761285] ata5: SATA link down (SStatus 0 SControl 300)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    3.130040] ata6: SATA link down (SStatus 0 SControl 300)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    3.153855] usbcore: registered new interface driver hiddev
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    3.166815] input: SIGMACH1P U+P Mouse as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input5
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    3.166914] generic-usb 0003:1C4F:0003.0001: input,hidraw0: USB HID v1.10 Mouse [SIGMACH1P U+P Mouse] on usb-0000:00:1a.1-2/input0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    3.166933] usbcore: registered new interface driver usbhid
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    3.166935] usbhid: USB HID core driver
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [    4.012736] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   16.687019] udev[442]: starting version 163
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   16.725153] Adding 3127292k swap on /dev/sda6.  Priority:-1 extents:1 across:3127292k 
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   16.955458] type=1400 audit(1294996050.783:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=620 comm="apparmor_parser"
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   16.955468] type=1400 audit(1294996050.783:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=638 comm="apparmor_parser"
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   16.956085] type=1400 audit(1294996050.783:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=620 comm="apparmor_parser"
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   16.956097] type=1400 audit(1294996050.783:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=638 comm="apparmor_parser"
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   16.956422] type=1400 audit(1294996050.783:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=620 comm="apparmor_parser"
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   16.956436] type=1400 audit(1294996050.783:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=638 comm="apparmor_parser"
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.153056] Bluetooth: Core ver 2.15
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.153098] NET: Registered protocol family 31
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.153100] Bluetooth: HCI device and connection manager initialized
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.153103] Bluetooth: HCI socket layer initialized
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.223542] input: HP WMI hotkeys as /devices/virtual/input/input6
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.290673] Bluetooth: Generic Bluetooth USB driver ver 0.6
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.290912] usbcore: registered new interface driver btusb
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.302769] lirc_dev: IR Remote Control driver registered, major 249 
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.384226] lp: driver loaded but no devices found
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.454913] Linux video capture interface: v2.00
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.499282] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a127)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.515734] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input7
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.515789] usbcore: registered new interface driver uvcvideo
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.515791] USB Video Class driver (v0.1.0)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.596167] lib80211: common routines for IEEE802.11 drivers
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.596170] lib80211_crypt: registered algorithm 'NULL'
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.691499] lis3lv02d: laptop model unknown, using default axes configuration
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.701458] lis3lv02d: 8 bits sensor found
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.762421] ACPI Error (dswload-0802): [_T_1] Namespace lookup failure, AE_ALREADY_EXISTS
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.762427] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20100428/psloop-231)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.762432] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.PEGP.VGA_.LCD_.GBQC] (Node ffff88007d72e900), AE_ALREADY_EXISTS
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.762443] ACPI: Marking method GBQC as Serialized because of AE_ALREADY_EXISTS error
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.762478] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.PEGP.VGA_.LCD_._BQC] (Node ffff88007d72e8e0), AE_ALREADY_EXISTS
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.762488] ACPI: Marking method _BQC as Serialized because of AE_ALREADY_EXISTS error
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.762527] ACPI Warning: Evaluating _BQC failed (20100428/video-651)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.763002] jmb38x_ms 0000:06:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.763009] jmb38x_ms 0000:06:00.3: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.765550] acpi device:07: registered as cooling_device2
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.766657] ACPI Error (dswload-0802): [_T_1] Namespace lookup failure, AE_ALREADY_EXISTS
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.766663] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20100428/psloop-231)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.766668] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.PEGP.VGA_.LCD1.GBQC] (Node ffff88007d72eb00), AE_ALREADY_EXISTS
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.766678] ACPI: Marking method GBQC as Serialized because of AE_ALREADY_EXISTS error
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.766714] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.PEGP.VGA_.LCD1._BQC] (Node ffff88007d72eae0), AE_ALREADY_EXISTS
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.766724] ACPI: Marking method _BQC as Serialized because of AE_ALREADY_EXISTS error
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.766763] ACPI Warning: Evaluating _BQC failed (20100428/video-651)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.769089] acpi device:09: registered as cooling_device3
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.769622] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input8
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.769696] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.820988] lirc_ene0100: module is from the staging directory, the quality is unknown, you have been warned.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.821620] enecir 00:0a: lirc_dev: driver enecir registered at minor = 0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.821676] enecir: unknown ENE chip detected, assuming KB3926D
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.821678] enecir: driver support incomplete
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.821680] enecir: chip is 0x3926 - 0x00, 0xd2
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.821687] enecir: hardware features:
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.821689] enecir: learning and tx off, gpio40_learn off, fan_in off
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.821691] enecir: driver has been succesfully loaded
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.860093] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input9
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.860206] Registered led device: hp::hddprotect
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   17.860220] lis3lv02d driver loaded.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.221419] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.228660] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.301662] [fglrx] Maximum main memory to use for locked dma buffers: 1879 MBytes.
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.302070] [fglrx]   vendor: 1002 device: 9480 count: 1
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.302709] [fglrx] ioport: bar 1, base 0x7000, size: 0x100
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.302738] pci 0000:01:00.0: power state changed by ACPI to D0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.302749] pci 0000:01:00.0: power state changed by ACPI to D0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.302758] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.302763] pci 0000:01:00.0: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.303024] [fglrx] Kernel PAT support is enabled
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.303044] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.406166] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00000/0x0
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.490034] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.500985] type=1400 audit(1294996052.333:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=973 comm="apparmor_parser"
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.501718] type=1400 audit(1294996052.333:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=974 comm="apparmor_parser"
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.502345] type=1400 audit(1294996052.333:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=974 comm="apparmor_parser"
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.502684] type=1400 audit(1294996052.333:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=974 comm="apparmor_parser"
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.509573] r8169 0000:03:00.0: eth0: link up
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.509585] r8169 0000:03:00.0: eth0: link up
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.527809] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.527822] wl 0000:02:00.0: setting latency timer to 64
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.667784] lib80211_crypt: registered algorithm 'TKIP'
Jan 14 14:37:32 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   18.668094] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
Jan 14 14:37:33 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   19.271956] Bluetooth: L2CAP ver 2.14
Jan 14 14:37:33 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   19.271959] Bluetooth: L2CAP socket layer initialized
Jan 14 14:37:33 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   19.338171] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jan 14 14:37:33 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   19.338174] Bluetooth: BNEP filters: protocol multicast
Jan 14 14:37:33 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   19.619309] Bluetooth: SCO (Voice Link) ver 0.6
Jan 14 14:37:33 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   19.619312] Bluetooth: SCO socket layer initialized
Jan 14 14:37:33 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   19.862838] Bluetooth: RFCOMM TTY layer initialized
Jan 14 14:37:33 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   19.862844] Bluetooth: RFCOMM socket layer initialized
Jan 14 14:37:33 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   19.862846] Bluetooth: RFCOMM ver 1.11
Jan 14 14:37:33 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   19.888219]   alloc irq_desc for 22 on node -1
Jan 14 14:37:33 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   19.888223]   alloc kstat_irqs on node -1
Jan 14 14:37:33 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   19.888230] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jan 14 14:37:33 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   19.888278]   alloc irq_desc for 48 on node -1
Jan 14 14:37:33 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   19.888279]   alloc kstat_irqs on node -1
Jan 14 14:37:33 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   19.888290] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
Jan 14 14:37:33 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   19.888317] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jan 14 14:37:34 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   20.190259] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
Jan 14 14:37:34 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   20.190451] input: HDA Intel Line Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
Jan 14 14:37:34 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   20.193309] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jan 14 14:37:34 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   20.193377]   alloc irq_desc for 49 on node -1
Jan 14 14:37:34 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   20.193379]   alloc kstat_irqs on node -1
Jan 14 14:37:34 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   20.193392] HDA Intel 0000:01:00.1: irq 49 for MSI/MSI-X
Jan 14 14:37:34 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   20.193422] HDA Intel 0000:01:00.1: setting latency timer to 64
Jan 14 14:37:34 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   20.586883] ppdev: user-space parallel port driver
Jan 14 14:37:34 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   21.087998]   alloc irq_desc for 50 on node -1
Jan 14 14:37:34 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   21.088002]   alloc kstat_irqs on node -1
Jan 14 14:37:34 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   21.088014] fglrx_pci 0000:01:00.0: irq 50 for MSI/MSI-X
Jan 14 14:37:34 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   21.088549] [fglrx] Firegl kernel thread PID: 1431
Jan 14 14:37:34 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   21.088736] [fglrx] IRQ 50 Enabled
Jan 14 14:37:35 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   21.768417] [fglrx] Gart USWC size:628 M.
Jan 14 14:37:35 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   21.768420] [fglrx] Gart cacheable size:246 M.
Jan 14 14:37:35 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   21.768425] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Jan 14 14:37:35 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   21.768428] [fglrx] Reserved FB block: Unshared offset:fe07000, size:1f9000 
Jan 14 14:37:35 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   21.768430] [fglrx] Reserved FB block: Unshared offset:3fffb000, size:5000 
Jan 14 14:37:35 ziyanjunaideen-HP-Pavilion-dv6-Notebook-PC kernel: [   21.778230] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0

```

Hope it would be of use.

---

### Post by amsterdamharu on 2011-01-14
I found [this]("https://fedoraproject.org/wiki/Common_F12_bugs#Systems_fail_to_boot.2C_USB_is_not_functional.2C_network_adapter_fails_to_work_.28or_possibly_other_symptoms.29_due_to_imperfect_handling_of_BIOSes_with_broken_IOMMU_handling") related to your "BIOS is broken" message but not sure if it applies to you, do you use the 32 bit version of Ubuntu?
>  If your BIOS has an option for it, enabling virtualization features in the BIOS
Or add *iommu=soft *to your kernel parameters. To do that you have to press arrow down key or shift while you boot to see the boot menu (not the BIOS settings) there are entries like Ubuntu and Ubuntu recovery. Choose the normal Ubuntu one (usually the top one) then press e to edit and replace quiet splash with iommu=soft.

This might also be related to X crashing since you have no input anymore. In that case you should start up with a live CD after the crash and check out (your Ubuntu install)/var/log/Xorg.0.log or the most recenct Xorg????.log you can find.

---

### Post by amsterdamharu on 2011-01-14
Other than that I can't find much other than "ACPI Exception: AE_ALREADY_EXISTS", you might try to add the kernel parameters:

iommu=soft noapic noapci nosplash irqpoll

---

### Post by Ziyan Junaideen on 2011-01-14
What I have is a 64bit Ubuntu and I don't have Virtulisation.

What I did is, I changed 'quiet splash' to iommu=soft. Then the computer is now booting.

If it freeses again, which I hope not, should I add 'noapic noapci nosplash irqpoll' after the new 'iommu=soft' entry?

If not it some thing like the XOrg thing right? Well when it gave prblems the very first days, I was able to boot the system under a low graphics option in the recover menu. But it also faied there after.

Lets see any ways. I booted it like 5 times and seems to be working. I hope its solved.

---

### Post by amsterdamharu on 2011-01-14
There is a way to permanently add these kernel parameters doing the following:

```
sudo nano /etc/default/grub
```

Change
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
With
```
GRUB_CMDLINE_LINUX_DEFAULT="iommu=soft quiet splash"
```
or
```
GRUB_CMDLINE_LINUX_DEFAULT="iommu=soft  noapic noapci nosplash irqpoll
```
Whatever parameters worked best.
Press control +x and y enter to save and exit
 
Then the following command:
```
sudo update-grub
```

---

