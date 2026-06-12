---
title: "purple screen when booting up ubuntu 11.04"
date: 2011-05-08
forum: General Help
---

### Post by eb3ha4el on 2011-05-08
Ubuntu works fine, but
When booting, right after Grub OS selection, Purple screen without ubuntu logo appears for about 3-5 mins without HDD LED flashing. after this 'freeze', same purple screen with logo appears, and it fully loads to ubuntu login screen in about 5 seconds.. 
is this usual?

My spec= 1Ghz CPU, 1GB RAM. Netbook.

any idea why and how to fix this?
please help.
thanks.

---

### Post by Toz on 2011-05-08
Can you please post back the contents of dmesg?

---

### Post by Wim Sturkenboom on 2011-05-08
Boot, when grub menu displays press <esc>. Edit the line with 'nosplash quiet' and remove those two words and you should be able to see where it is spending time.

---

### Post by Doctoxic on 2011-05-08
11.04 boots and works OK but everything is purple for me too

---

### Post by eb3ha4el on 2011-05-08
> **Wim Sturkenboom said:**
> Boot, when grub menu displays press <esc>. Edit the line with 'nosplash quiet' and remove those two words and you should be able to see where it is spending time.



I've done the work, however i dont know what all those text means...



> **Toz said:**
> Can you please post back the contents of dmesg?



how to check contents of dmesg? 
I'm newbie .. :D

---

### Post by RJ12 on 2011-05-08
> **eb3ha4el said:**
> I've done the work, however i dont know what all those text means...







how to check contents of dmesg? 
I'm newbie .. :D

open up a terminal and type "dmesg" (without quotes) it will give you a whole bunch of output, then copy it and paste it here on the forums and use the CODE tags :)

---

### Post by eb3ha4el on 2011-05-08
> **RJ12 said:**
> open up a terminal and type "dmesg" (without quotes) it will give you a whole bunch of output, then copy it and paste it here on the forums and use the CODE tags :)



thanks 

I know how to copy them from terminal in GUI 
by right clicking-copy so on and on... 

but i don't know how to copy when I used Ctrl+Alt+F1 for terminal.
How do you copy messages from that kind of TUI environment???


and can you also let me know what dmesg is about?? 



thanks for help.

---

### Post by Toz on 2011-05-08
dmesg prints out the bootup messages. They are also available in the file /var/log/dmesg. By having a look at these messages, we may be able to pinpoint the source of the problem and offer potential solutions.

If you look at the dmesg file, you will notice that the first field is a time stamp. If it is taking the computer 3-5 minutes to boot, we will only need to look at the first 3-5 minutes. Or alternatively, you should notice a time delay in the file, those lines are of most interest.

---

### Post by eb3ha4el on 2011-05-08
> **Toz said:**
> dmesg prints out the bootup messages. They are also available in the file /var/log/dmesg. By having a look at these messages, we may be able to pinpoint the source of the problem and offer potential solutions.

If you look at the dmesg file, you will notice that the first field is a time stamp. If it is taking the computer 3-5 minutes to boot, we will only need to look at the first 3-5 minutes. Or alternatively, you should notice a time delay in the file, those lines are of most interest.








[    0.004662] CPU0: Thermal monitoring enabled (TM2)
[    0.004670] using mwait in idle threads.
[    0.012140] ACPI: Core revision 20110112
[    0.024055] ftrace: allocating 23640 entries in 47 pages
[    0.028104] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028512] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070886] CPU0: Intel(R) Atom(TM) CPU N280   @ 1.66GHz stepping 02
[    0.072003] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.072003] ... version:                3
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] CPU 1 irqstacks, hard=f54ca000 soft=f54cc000
[    0.072003] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.164043] Brought up 2 CPUs
[    0.164052] Total of 2 processors activated (6650.02 BogoMIPS).
[    0.164413] devtmpfs: initialized
[    0.168275] print_constraints: dummy: 
[    0.168321] Time:  1:18:08  Date: 05/09/11
[    0.168408] NET: Registered protocol family 16
[    0.168501] Trying to unpack rootfs image as initramfs...
[    0.168873] EISA bus registered
[    0.168898] ACPI: bus type pci registered
[    0.169127] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.169139] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.169146] PCI: Using MMCONFIG for extended config space
[    0.169152] PCI: Using configuration type 1 for base access
[    0.173414] bio: create slab <bio-0> at 0
[    0.177959] ACPI: EC: Look up EC in DSDT
[    0.186500] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.187926] ACPI: SSDT 3f6d5f7b 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.188997] ACPI: Dynamic OEM Table Load:
[    0.189009] ACPI: SSDT   (null) 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.189605] ACPI: SSDT 3f6d58b7 0063F (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.190586] ACPI: Dynamic OEM Table Load:
[    0.190597] ACPI: SSDT   (null) 0063F (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.191523] ACPI: SSDT 3f6d617e 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.192578] ACPI: Dynamic OEM Table Load:
[    0.192590] ACPI: SSDT   (null) 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.192947] ACPI: SSDT 3f6d5ef6 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.193930] ACPI: Dynamic OEM Table Load:
[    0.193942] ACPI: SSDT   (null) 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.196542] ACPI: Interpreter enabled
[    0.196557] ACPI: (supports S0 S3 S4 S5)
[    0.196627] ACPI: Using IOAPIC for interrupt routing
[    0.254918] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.255422] ACPI: No dock devices found.
[    0.255430] HEST: Table not found.
[    0.255440] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.256583] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.258745] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.258757] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.258766] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.258776] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.258785] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.258794] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.258805] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xfebfffff]
[    0.258843] pci 0000:00:00.0: [8086:27ac] type 0 class 0x000600
[    0.258923] pci 0000:00:02.0: [8086:27ae] type 0 class 0x000300
[    0.258946] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf007ffff]
[    0.258961] pci 0000:00:02.0: reg 14: [io  0x1800-0x1807]
[    0.258975] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.258990] pci 0000:00:02.0: reg 1c: [mem 0xf0200000-0xf023ffff]
[    0.259056] pci 0000:00:02.1: [8086:27a6] type 0 class 0x000380
[    0.259078] pci 0000:00:02.1: reg 10: [mem 0xf0080000-0xf00fffff]
[    0.259232] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.259269] pci 0000:00:1b.0: reg 10: [mem 0xf0440000-0xf0443fff 64bit]
[    0.259382] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.259394] pci 0000:00:1b.0: PME# disabled
[    0.259443] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.259557] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.259568] pci 0000:00:1c.0: PME# disabled
[    0.259620] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.259734] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.259745] pci 0000:00:1c.1: PME# disabled
[    0.259796] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.259911] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.259922] pci 0000:00:1c.2: PME# disabled
[    0.259977] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
[    0.260129] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.260142] pci 0000:00:1c.3: PME# disabled
[    0.260197] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.260275] pci 0000:00:1d.0: reg 20: [io  0x1820-0x183f]
[    0.260340] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.260418] pci 0000:00:1d.1: reg 20: [io  0x1840-0x185f]
[    0.260482] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.260559] pci 0000:00:1d.2: reg 20: [io  0x1860-0x187f]
[    0.260623] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.260700] pci 0000:00:1d.3: reg 20: [io  0x1880-0x189f]
[    0.260797] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.260838] pci 0000:00:1d.7: reg 10: [mem 0xf0444000-0xf04443ff]
[    0.260961] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.260973] pci 0000:00:1d.7: PME# disabled
[    0.261016] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.261136] pci 0000:00:1f.0: [8086:27b9] type 0 class 0x000601
[    0.261266] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.261281] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.261292] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.261303] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 007f)
[    0.261317] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 0068 (mask 0007)
[    0.261378] pci 0000:00:1f.1: [8086:27df] type 0 class 0x000101
[    0.261406] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.261426] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.261447] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.261468] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.261489] pci 0000:00:1f.1: reg 20: [io  0x1810-0x181f]
[    0.261564] pci 0000:00:1f.2: [8086:27c5] type 0 class 0x000106
[    0.261599] pci 0000:00:1f.2: reg 10: [io  0x18c8-0x18cf]
[    0.261620] pci 0000:00:1f.2: reg 14: [io  0x18c0-0x18c3]
[    0.261640] pci 0000:00:1f.2: reg 18: [io  0x18a8-0x18af]
[    0.261661] pci 0000:00:1f.2: reg 1c: [io  0x180c-0x180f]
[    0.261682] pci 0000:00:1f.2: reg 20: [io  0x18b0-0x18bf]
[    0.261705] pci 0000:00:1f.2: reg 24: [mem 0xf0444400-0xf04447ff]
[    0.261767] pci 0000:00:1f.2: PME# supported from D3hot
[    0.261778] pci 0000:00:1f.2: PME# disabled
[    0.261816] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.261901] pci 0000:00:1f.3: reg 20: [io  0x18e0-0x18ff]
[    0.262042] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.262054] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.262067] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.262083] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.262216] pci 0000:03:00.0: [168c:002b] type 0 class 0x000280
[    0.262275] pci 0000:03:00.0: reg 10: [mem 0xf0100000-0xf010ffff 64bit]
[    0.262478] pci 0000:03:00.0: supports D1
[    0.262488] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.262503] pci 0000:03:00.0: PME# disabled
[    0.268094] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.268110] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.268125] pci 0000:00:1c.1:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.268141] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.268321] pci 0000:04:00.0: [10ec:8136] type 0 class 0x000200
[    0.268403] pci 0000:04:00.0: reg 10: [io  0x2000-0x20ff]
[    0.268530] pci 0000:04:00.0: reg 18: [mem 0xf0510000-0xf0510fff 64bit pref]
[    0.268612] pci 0000:04:00.0: reg 20: [mem 0xf0500000-0xf050ffff 64bit pref]
[    0.268664] pci 0000:04:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.268842] pci 0000:04:00.0: supports D1 D2
[    0.268850] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.268872] pci 0000:04:00.0: PME# disabled
[    0.269065] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.269078] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.269091] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.269108] pci 0000:00:1c.2:   bridge window [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.269204] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.269217] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
[    0.269230] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.269246] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.269363] pci 0000:00:1e.0: PCI bridge to [bus 06-06] (subtractive decode)
[    0.269376] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.269389] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.269405] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.269416] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.269426] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.269435] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.269445] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.269455] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.269465] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.269475] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0xfebfffff] (subtractive decode)
[    0.269525] pci_bus 0000:00: on NUMA node 0
[    0.269543] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.270086] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.270264] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.270440] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.270626] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.270886] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.271524]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.289191] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.289373] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.289548] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.289736] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.289917] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.290096] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.290273] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.290449] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.290820] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.290854] vgaarb: loaded
[    0.291685] SCSI subsystem initialized
[    0.291883] libata version 3.00 loaded.
[    0.292111] usbcore: registered new interface driver usbfs
[    0.292163] usbcore: registered new interface driver hub
[    0.292289] usbcore: registered new device driver usb
[    0.292743] wmi: Mapper loaded
[    0.292750] PCI: Using ACPI for IRQ routing
[    0.292760] PCI: pci_cache_line_size set to 64 bytes
[    0.292938] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.292947] reserve RAM buffer: 000000003f6d0000 - 000000003fffffff 
[    0.293310] NetLabel: Initializing
[    0.293317] NetLabel:  domain hash size = 128
[    0.293323] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.293355] NetLabel:  unlabeled traffic allowed by default
[    0.293487] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.293506] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.293521] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.296755] Switching to clocksource hpet
[    0.298322] Switched to NOHz mode on CPU #0
[    0.298420] Switched to NOHz mode on CPU #1
[    0.318676] AppArmor: AppArmor Filesystem Enabled
[    0.318756] pnp: PnP ACPI init
[    0.318810] ACPI: bus type pnp registered
[    0.319999] pnp 00:00: [bus 00-ff]
[    0.320048] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.320058] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.320066] pnp 00:00: [io  0x0d00-0xffff window]
[    0.320075] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.320084] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.320092] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.320101] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.320109] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.320118] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.320126] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.320135] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.320143] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.320151] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.320160] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.320168] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.320177] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.320185] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.320194] pnp 00:00: [mem 0x40000000-0xfebfffff window]
[    0.320202] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.320406] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.320508] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.320517] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.320526] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.320534] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.320541] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.320550] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.320557] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[    0.320565] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
[    0.320721] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.320733] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.320743] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.320753] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.320763] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.320773] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.320783] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.320793] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.320805] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.321550] pnp 00:02: [io  0x0000-0x001f]
[    0.321560] pnp 00:02: [io  0x0081-0x0091]
[    0.321568] pnp 00:02: [io  0x0093-0x009f]
[    0.321575] pnp 00:02: [io  0x00c0-0x00df]
[    0.321583] pnp 00:02: [dma 4]
[    0.321732] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.321970] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.322179] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.322193] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.322240] pnp 00:04: [io  0x00f0]
[    0.322265] pnp 00:04: [irq 13]
[    0.322406] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.322450] pnp 00:05: [io  0x0061]
[    0.322457] pnp 00:05: [io  0x0063]
[    0.322464] pnp 00:05: [io  0x0065]
[    0.322471] pnp 00:05: [io  0x0067]
[    0.322483] pnp 00:05: [io  0x0068]
[    0.322490] pnp 00:05: [io  0x006c]
[    0.322496] pnp 00:05: [io  0x0070]
[    0.322503] pnp 00:05: [io  0x0080]
[    0.322510] pnp 00:05: [io  0x0092]
[    0.322517] pnp 00:05: [io  0x00b2-0x00b3]
[    0.322524] pnp 00:05: [io  0x0800-0x080f]
[    0.322532] pnp 00:05: [io  0x1000-0x107f]
[    0.322539] pnp 00:05: [io  0x1180-0x11bf]
[    0.322546] pnp 00:05: [io  0xfe00]
[    0.322553] pnp 00:05: [io  0xff2c-0xff7f]
[    0.322785] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.322797] system 00:05: [io  0x1000-0x107f] has been reserved
[    0.322808] system 00:05: [io  0x1180-0x11bf] has been reserved
[    0.322817] system 00:05: [io  0xfe00] has been reserved
[    0.322827] system 00:05: [io  0xff2c-0xff7f] has been reserved
[    0.322838] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.322879] pnp 00:06: [io  0x0070-0x0077]
[    0.322898] pnp 00:06: [irq 8]
[    0.323046] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.340172] pnp 00:07: [io  0x0060]
[    0.340182] pnp 00:07: [io  0x0064]
[    0.340208] pnp 00:07: [irq 1]
[    0.340411] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.340457] pnp 00:08: [irq 12]
[    0.340607] pnp 00:08: Plug and Play ACPI device, IDs AUI0311 SYN0700 SYN0002 PNP0f13 (active)
[    0.340716] pnp: PnP ACPI: found 9 devices
[    0.340723] ACPI: ACPI bus type pnp unregistered
[    0.340732] PnPBIOS: Disabled by ACPI PNP
[    0.382640] pci 0000:00:1c.0: BAR 14: assigned [mem 0x40000000-0x401fffff]
[    0.382659] pci 0000:00:1c.0: BAR 15: assigned [mem 0x40200000-0x403fffff 64bit pref]
[    0.382674] pci 0000:00:1c.1: BAR 15: assigned [mem 0x40400000-0x405fffff 64bit pref]
[    0.382687] pci 0000:00:1c.2: BAR 14: assigned [mem 0x40600000-0x409fffff]
[    0.382701] pci 0000:00:1c.3: BAR 14: assigned [mem 0x40a00000-0x40bfffff]
[    0.382715] pci 0000:00:1c.3: BAR 15: assigned [mem 0x40c00000-0x40dfffff 64bit pref]
[    0.382729] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.382741] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
[    0.382753] pci 0000:00:1c.3: BAR 13: assigned [io  0x5000-0x5fff]
[    0.382762] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.382772] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.382786] pci 0000:00:1c.0:   bridge window [mem 0x40000000-0x401fffff]
[    0.382799] pci 0000:00:1c.0:   bridge window [mem 0x40200000-0x403fffff 64bit pref]
[    0.382815] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.382825] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.382839] pci 0000:00:1c.1:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.382851] pci 0000:00:1c.1:   bridge window [mem 0x40400000-0x405fffff 64bit pref]
[    0.382870] pci 0000:04:00.0: BAR 6: assigned [mem 0xf0520000-0xf053ffff pref]
[    0.382880] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.382890] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.382903] pci 0000:00:1c.2:   bridge window [mem 0x40600000-0x409fffff]
[    0.382916] pci 0000:00:1c.2:   bridge window [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.382931] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.382941] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.382955] pci 0000:00:1c.3:   bridge window [mem 0x40a00000-0x40bfffff]
[    0.382967] pci 0000:00:1c.3:   bridge window [mem 0x40c00000-0x40dfffff 64bit pref]
[    0.382983] pci 0000:00:1e.0: PCI bridge to [bus 06-06]
[    0.382990] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.383002] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.383012] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.383069] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.383083] pci 0000:00:1c.0: setting latency timer to 64
[    0.383113] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.383125] pci 0000:00:1c.1: setting latency timer to 64
[    0.383153] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.383165] pci 0000:00:1c.2: setting latency timer to 64
[    0.383193] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.383205] pci 0000:00:1c.3: setting latency timer to 64
[    0.383223] pci 0000:00:1e.0: setting latency timer to 64
[    0.383234] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.383243] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.383253] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.383262] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.383271] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.383280] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.383289] pci_bus 0000:00: resource 10 [mem 0x40000000-0xfebfffff]
[    0.383299] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.383309] pci_bus 0000:02: resource 1 [mem 0x40000000-0x401fffff]
[    0.383319] pci_bus 0000:02: resource 2 [mem 0x40200000-0x403fffff 64bit pref]
[    0.383329] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
[    0.383338] pci_bus 0000:03: resource 1 [mem 0xf0100000-0xf01fffff]
[    0.383347] pci_bus 0000:03: resource 2 [mem 0x40400000-0x405fffff 64bit pref]
[    0.383356] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.383365] pci_bus 0000:04: resource 1 [mem 0x40600000-0x409fffff]
[    0.383374] pci_bus 0000:04: resource 2 [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.383383] pci_bus 0000:05: resource 0 [io  0x5000-0x5fff]
[    0.383392] pci_bus 0000:05: resource 1 [mem 0x40a00000-0x40bfffff]
[    0.383401] pci_bus 0000:05: resource 2 [mem 0x40c00000-0x40dfffff 64bit pref]
[    0.383411] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.383419] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.383428] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.383437] pci_bus 0000:06: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.383446] pci_bus 0000:06: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.383455] pci_bus 0000:06: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.383464] pci_bus 0000:06: resource 10 [mem 0x40000000-0xfebfffff]
[    0.383572] NET: Registered protocol family 2
[    0.383768] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.384659] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.385721] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.386245] TCP: Hash tables configured (established 131072 bind 65536)
[    0.386254] TCP reno registered
[    0.386267] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.386290] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.386634] NET: Registered protocol family 1
[    0.386684] pci 0000:00:02.0: Boot video device
[    0.386894] PCI: CLS 64 bytes, default 64
[    0.386993] Simple Boot Flag at 0x36 set to 0x1
[    0.387621] cpufreq-nforce2: No nForce2 chipset.
[    0.388149] audit: initializing netlink socket (disabled)
[    0.388177] type=2000 audit(1304903888.384:1): initialized
[    0.411993] highmem bounce pool size: 64 pages
[    0.412048] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.418826] VFS: Disk quotas dquot_6.5.2
[    0.419037] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.421682] fuse init (API version 7.16)
[    0.422050] msgmni has been set to 1704
[    0.422883] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.423016] io scheduler noop registered
[    0.423024] io scheduler deadline registered
[    0.423094] io scheduler cfq registered (default)
[    0.423466] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.423561] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.423738] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.423826] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.423983] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.424113] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.424269] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.424350] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.424637] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.424738] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.424921] intel_idle: MWAIT substates: 0x20220
[    0.424939] intel_idle: v0.4 model 0x1C
[    0.424945] intel_idle: lapic_timer_reliable_states 0x2
[    0.424963] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.425501] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.425940] ACPI: AC Adapter [ACAD] (on-line)
[    0.426736] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.426789] ACPI: Lid Switch [LID0]
[    0.426959] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.426973] ACPI: Power Button [PWRB]
[    0.427177] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.427190] ACPI: Power Button [PWRF]
[    0.427756] ACPI: acpi_idle yielding to intel_idle
[    0.460781] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.460954] ERST: Table is not found!
[    0.461178] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.461650] isapnp: Scanning for PnP cards...
[    0.632994] ACPI: Battery Slot [BAT1] (battery present)
[    0.817073] isapnp: No Plug & Play device found
[    0.845646] Freeing initrd memory: 12508k freed
[    0.868601] Linux agpgart interface v0.103
[    0.868766] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    0.868934] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    0.869116] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.869351] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.872588] brd: module loaded
[    0.874125] loop: module loaded
[    0.874380] i2c-core: driver [adp5520] using legacy suspend method
[    0.874386] i2c-core: driver [adp5520] using legacy resume method
[    0.874622] ata_piix 0000:00:1f.1: version 2.13
[    0.874651] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.874714] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.875532] scsi0 : ata_piix
[    0.875798] scsi1 : ata_piix
[    0.876650] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.876657] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.876758] ata2: port disabled. ignoring.
[    0.877745] Fixed MDIO Bus: probed
[    0.877858] PPP generic driver version 2.4.2
[    0.878003] tun: Universal TUN/TAP device driver, 1.6
[    0.878008] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.878229] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.878295] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.878330] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.878338] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.878436] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.878543] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.878562] ehci_hcd 0000:00:1d.7: debug port 1
[    0.882439] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.882478] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0444000
[    0.896070] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.896413] hub 1-0:1.0: USB hub found
[    0.896424] hub 1-0:1.0: 8 ports detected
[    0.896605] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.896645] uhci_hcd: USB Universal Host Controller Interface driver
[    0.896722] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.896737] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.896744] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.896864] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.896961] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    0.897278] hub 2-0:1.0: USB hub found
[    0.897290] hub 2-0:1.0: 2 ports detected
[    0.897441] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.897456] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.897463] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.897570] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.897678] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    0.897994] hub 3-0:1.0: USB hub found
[    0.898005] hub 3-0:1.0: 2 ports detected
[    0.898151] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.898166] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.898173] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.898275] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.900160] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    0.900479] hub 4-0:1.0: USB hub found
[    0.900490] hub 4-0:1.0: 2 ports detected
[    0.900660] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.900675] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.900682] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.900780] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.900884] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    0.901186] hub 5-0:1.0: USB hub found
[    0.901197] hub 5-0:1.0: 2 ports detected
[    0.901458] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.955787] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.955805] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.956159] mousedev: PS/2 mouse device common for all mice
[    0.958421] rtc_cmos 00:06: RTC can wake from S4
[    0.958582] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.958628] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.958876] device-mapper: uevent: version 1.0.3
[    0.959101] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    0.959284] device-mapper: multipath: version 1.2.0 loaded
[    0.959293] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.959521] EISA: Probing bus 0 at eisa.0
[    0.959531] EISA: Cannot allocate resource for mainboard
[    0.959537] Cannot allocate resource for EISA slot 1
[    0.959542] Cannot allocate resource for EISA slot 2
[    0.959548] Cannot allocate resource for EISA slot 3
[    0.959553] Cannot allocate resource for EISA slot 4
[    0.959559] Cannot allocate resource for EISA slot 5
[    0.959564] Cannot allocate resource for EISA slot 6
[    0.959569] Cannot allocate resource for EISA slot 7
[    0.959575] Cannot allocate resource for EISA slot 8
[    0.959579] EISA: Detected 0 cards.
[    0.959886] cpuidle: using governor ladder
[    0.960186] cpuidle: using governor menu
[    0.960829] TCP cubic registered
[    0.961182] NET: Registered protocol family 10
[    0.962418] NET: Registered protocol family 17
[    0.962466] Registering the dns_resolver key type
[    0.963413] Using IPI No-Shortcut mode
[    0.963713] PM: Hibernation image not present or could not be loaded.
[    0.963738] registered taskstats version 1
[    0.964342]   Magic number: 11:43:306
[    0.964394] tty tty35: hash matches
[    0.964496] rtc_cmos 00:06: setting system clock to 2011-05-09 01:18:09 UTC (1304903889)
[    0.964505] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.964509] EDD information not available.
[    1.008811] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.038355] Freeing unused kernel memory: 700k freed
[    1.038821] Write protecting the kernel text: 5192k
[    1.038909] Write protecting the kernel read-only data: 2148k
[    1.095014] <30>udev[67]: starting version 167
[    1.208082] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.335349] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.335445] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.335524] r8169 0000:04:00.0: setting latency timer to 64
[    1.335632] r8169 0000:04:00.0: irq 44 for MSI/MSI-X
[    1.341151] r8169 0000:04:00.0: eth0: RTL8102e at 0xf8022000, 00:26:22:3c:73:da, XID 04c00000 IRQ 44
[    1.461758] ahci 0000:00:1f.2: version 3.0
[    1.461794] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.461912] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.462056] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    1.462069] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.462082] ahci 0000:00:1f.2: setting latency timer to 64
[    1.464777] scsi2 : ahci
[    1.465121] scsi3 : ahci
[    1.465792] scsi4 : ahci
[    1.466125] scsi5 : ahci
[    1.466627] ata3: SATA max UDMA/133 abar m1024@0xf0444400 port 0xf0444500 irq 45
[    1.466637] ata4: DUMMY
[    1.466646] ata5: SATA max UDMA/133 abar m1024@0xf0444400 port 0xf0444600 irq 45
[    1.466653] ata6: DUMMY
[    1.784144] ata5: SATA link down (SStatus 0 SControl 300)
[    1.784217] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.784950] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.884225] ata3.00: ATA-8: TOSHIBA MK2555GSX, FG001M, max UDMA/100
[    1.884237] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.892386] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.896073] ata3.00: configured for UDMA/100
[    1.896384] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK2555GS FG00 PQ: 0 ANSI: 5
[    1.896962] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.896971] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.897256] sd 2:0:0:0: [sda] Write Protect is off
[    1.897266] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.897376] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.947367]  sda: sda1 sda2 sda3 sda4
[    1.948429] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.893677] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[  300.303162] <30>udev[266]: starting version 167
[  300.394951] lp: driver loaded but no devices found
[  300.416054] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro
[  300.859113] type=1400 audit(1304900589.387:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=426 comm="apparmor_parser"
[  300.872240] type=1400 audit(1304900589.403:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=426 comm="apparmor_parser"
[  300.873019] type=1400 audit(1304900589.403:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=426 comm="apparmor_parser"
[  301.128508] Detected Toshiba ACPI Bluetooth device - installing RFKill handler
[  301.132493] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
[  301.201597] acpi device:01: registered as cooling_device2
[  301.202054] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[  301.202380] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[  301.413026] intel_rng: FWH not detected
[  301.423516] r8169 0000:04:00.0: eth0: link down
[  301.426549] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  301.478915] leds_ss4200: no LED devices found
[  301.700819] [drm] Initialized drm 1.1.0 20060810
[  301.844122] usb 5-1: new full speed USB device using uhci_hcd and address 2
[  302.159046] type=1400 audit(1304900590.689:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=587 comm="apparmor_parser"
[  302.160927] type=1400 audit(1304900590.693:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=588 comm="apparmor_parser"
[  302.162072] type=1400 audit(1304900590.693:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=588 comm="apparmor_parser"
[  302.162836] type=1400 audit(1304900590.693:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=588 comm="apparmor_parser"
[  302.217326] type=1400 audit(1304900590.748:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=595 comm="apparmor_parser"
[  302.220761] type=1400 audit(1304900590.752:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=595 comm="apparmor_parser"
[  302.230680] type=1400 audit(1304900590.760:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=596 comm="apparmor_parser"
[  302.236303] cfg80211: Calling CRDA to update world regulatory domain
[  302.444242] Linux video capture interface: v2.00
[  302.609713] uvcvideo: Found UVC 1.00 device USB2.0 UVC WebCam (04f2:b128)
[  302.660351] input: USB2.0 UVC WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input5
[  302.666316] usbcore: registered new interface driver uvcvideo
[  302.666327] USB Video Class driver (v1.0.0)
[  303.370077] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input6
[  303.373752] cfg80211: World regulatory domain updated:
[  303.373762] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  303.373772] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  303.373781] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  303.373790] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  303.373799] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  303.373807] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  303.432319] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input7
[  303.496521] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  303.496538] i915 0000:00:02.0: setting latency timer to 64
[  303.633055] Bluetooth: Core ver 2.15
[  303.633171] NET: Registered protocol family 31
[  303.633177] Bluetooth: HCI device and connection manager initialized
[  303.633185] Bluetooth: HCI socket layer initialized
[  303.651370] Bluetooth: Generic Bluetooth USB driver ver 0.6
[  303.664075] usbcore: registered new interface driver btusb
[  303.702762] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  303.702791] ath9k 0000:03:00.0: setting latency timer to 64
[  303.757295] ath: EEPROM regdomain: 0x65
[  303.757304] ath: EEPROM indicates we should expect a direct regpair map
[  303.757315] ath: Country alpha2 being used: 00
[  303.757320] ath: Regpair used: 0x65
[  303.757331] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  303.757342] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  303.757351] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  303.757360] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  303.757368] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  303.757377] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  303.757385] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  303.757394] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  303.757403] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  303.757413] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  303.757422] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  303.757432] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  303.757440] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  303.757450] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  303.757458] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  303.757468] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  303.757477] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  303.757487] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  303.757495] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  303.757505] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  303.757513] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  303.757522] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  303.757530] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  303.757539] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  303.757548] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  303.757558] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  303.757567] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[  303.767113] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[  303.767123] [drm] Driver supports precise vblank timestamp query.
[  303.787498] Bluetooth: L2CAP ver 2.15
[  303.787506] Bluetooth: L2CAP socket layer initialized
[  303.840454] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  303.840462] Bluetooth: BNEP filters: protocol multicast
[  303.858219] Bluetooth: SCO (Voice Link) ver 0.6
[  303.858227] Bluetooth: SCO socket layer initialized
[  303.866723] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  303.868170] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[  303.868728] [drm] initialized overlay support
[  303.900319] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[  303.904760] Registered led device: ath9k-phy0::radio
[  303.905058] Registered led device: ath9k-phy0::assoc
[  303.905355] Registered led device: ath9k-phy0::tx
[  303.905644] Registered led device: ath9k-phy0::rx
[  303.905669] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8420000, irq=17
[  304.015197] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  304.126089] Console: switching to colour frame buffer device 128x37
[  304.126170] fb0: inteldrmfb frame buffer device
[  304.126177] drm: registered panic notifier
[  304.126628] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[  304.129603] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  304.129732] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[  304.129798] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  304.401461] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[  304.402229] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[  304.996157] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,commit=0
[  305.010051] ppdev: user-space parallel port driver
[  309.065831] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,commit=0
[  323.900752] wlan0: authenticate with 00:26:5a:92:c1:8e (try 1)
[  323.902919] wlan0: authenticated
[  323.902990] wlan0: associate with 00:26:5a:92:c1:8e (try 1)
[  323.913088] wlan0: RX AssocResp from 00:26:5a:92:c1:8e (capab=0x411 status=0 aid=3)
[  323.913100] wlan0: associated
[  323.921197] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  323.922461] cfg80211: Calling CRDA for country: TW
[  323.938865] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  323.938881] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  323.938890] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  323.938901] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  323.938910] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  323.938920] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  323.938929] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  323.938940] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  323.938949] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  323.938960] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  323.938970] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  323.938981] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  323.938991] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  323.939002] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  323.939012] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  323.939022] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  323.939032] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  323.939043] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  323.939053] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  323.939064] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  323.939074] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  323.939085] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  323.939093] cfg80211: Disabling freq 2467 MHz
[  323.939100] cfg80211: Disabling freq 2472 MHz
[  323.939106] cfg80211: Disabling freq 2484 MHz
[  323.939118] cfg80211: Regulatory domain changed to country: TW
[  323.939125] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  323.939136] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  323.939146] cfg80211:     (5270000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  323.939155] cfg80211:     (5735000 KHz - 5815000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  324.224946] Intel AES-NI instructions are not detected.
[  324.250428] padlock_aes: VIA PadLock not detected.
[  334.832057] wlan0: no IPv6 routers present
[ 5764.771881] ptrace of non-child pid 2372 was attempted by: opera (pid 2791)
[ 5764.968398] wlan0: deauthenticating from 00:26:5a:92:c1:8e by local choice (reason=3)
[ 5765.027044] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 5765.027058] cfg80211: Restoring regulatory settings
[ 5765.027073] cfg80211: Calling CRDA to update world regulatory domain
[ 5765.291082] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 5765.291097] cfg80211: World regulatory domain updated:
[ 5765.291101] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 5765.291109] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5765.291116] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5765.291123] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5765.291129] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5765.291136] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6022.821212] wlan0: authenticate with 00:26:5a:92:c1:8e (try 1)
[ 6022.823648] wlan0: authenticated
[ 6022.823719] wlan0: associate with 00:26:5a:92:c1:8e (try 1)
[ 6022.833360] wlan0: RX AssocResp from 00:26:5a:92:c1:8e (capab=0x411 status=0 aid=3)
[ 6022.833372] wlan0: associated
[ 6022.841275] cfg80211: Calling CRDA for country: TW
[ 6022.859046] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 6022.859061] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6022.859072] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 6022.859082] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6022.859091] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 6022.859101] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6022.859110] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 6022.859121] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6022.859130] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 6022.859141] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6022.859150] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 6022.859161] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6022.859171] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 6022.859181] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6022.859191] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 6022.859201] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6022.859211] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 6022.859222] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6022.859232] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 6022.859243] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6022.859252] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 6022.859262] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6022.859270] cfg80211: Disabling freq 2467 MHz
[ 6022.859277] cfg80211: Disabling freq 2472 MHz
[ 6022.859284] cfg80211: Disabling freq 2484 MHz
[ 6022.859295] cfg80211: Regulatory domain changed to country: TW
[ 6022.859301] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 6022.859312] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 6022.859322] cfg80211:     (5270000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 6022.859332] cfg80211:     (5735000 KHz - 5815000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 9131.407342] wlan0: deauthenticating from 00:26:5a:92:c1:8e by local choice (reason=3)
[ 9131.460636] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 9131.460655] cfg80211: Restoring regulatory settings
[ 9131.460717] cfg80211: Calling CRDA to update world regulatory domain
[ 9131.507475] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 9131.507494] cfg80211: World regulatory domain updated:
[ 9131.507501] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 9131.507511] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 9131.507520] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 9131.507530] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 9131.507539] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 9131.507548] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 9201.090808] wlan0: authenticate with 00:26:5a:92:c1:8e (try 1)
[ 9201.096088] wlan0: authenticated
[ 9201.096156] wlan0: associate with 00:26:5a:92:c1:8e (try 1)
[ 9201.105372] wlan0: RX AssocResp from 00:26:5a:92:c1:8e (capab=0x411 status=0 aid=3)
[ 9201.105384] wlan0: associated
[ 9201.114776] cfg80211: Calling CRDA for country: TW
[ 9201.130605] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 9201.130619] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 9201.130628] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 9201.130637] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 9201.130646] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 9201.130656] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 9201.130665] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 9201.130674] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 9201.130683] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 9201.130693] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 9201.130702] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 9201.130712] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 9201.130721] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 9201.130730] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 9201.130739] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 9201.130749] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 9201.130758] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 9201.130768] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 9201.130777] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 9201.130786] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 9201.130795] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 9201.130805] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 9201.130812] cfg80211: Disabling freq 2467 MHz
[ 9201.130819] cfg80211: Disabling freq 2472 MHz
[ 9201.130824] cfg80211: Disabling freq 2484 MHz
[ 9201.130836] cfg80211: Regulatory domain changed to country: TW
[ 9201.130842] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 9201.130852] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 9201.130862] cfg80211:     (5270000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 9201.130872] cfg80211:     (5735000 KHz - 5815000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)




That's dmesg. I don't know which unit is used for time there, so i just posted them all. 

By the way, do you know how to copy these if I used Ctrl+Art+F1?
I copied this because I used terminal in GUI, which allowed me to use Mouse pointer to highlight them and copy, but what about TUI environment where there is no mouse pointer?

---

### Post by Toz on 2011-05-09
Looks like the slowdown is with udev. Anything relevant in /var/log/udev?

In the TUI, you can always pipe the results of the command to a file and then copy/paste/attach the file. The command would be:```
dmesg > name_of_file
```

---

### Post by eb3ha4el on 2011-05-09
> **Toz said:**
> Looks like the slowdown is with udev. Anything relevant in /var/log/udev?

In the TUI, you can always pipe the results of the command to a file and then copy/paste/attach the file. The command would be:```
dmesg > name_of_file
```





Fantastic! the command works!
thanks



I can't put all the logs in Udev. 
Page simply goes to time-out.
How can I see what to be relevant?

---

### Post by Toz on 2011-05-09
You can upload /var/log/udev to uploaded.to and post back the link to the file.

After the word KERNEL in the udev log file, is a time stamp. Look for a couple of entries where the time stamps are not close - indicating a delay. This should tell us which device is causing the delay.

Have a look at:
[http://askubuntu.com/questions/39316/slow-boot-after-clean-install-of-natty](http://askubuntu.com/questions/39316/slow-boot-after-clean-install-of-natty) for some suggested fixes.

---

### Post by eb3ha4el on 2011-05-10
> **Toz said:**
> You can upload /var/log/udev to uploaded.to and post back the link to the file.

After the word KERNEL in the udev log file, is a time stamp. Look for a couple of entries where the time stamps are not close - indicating a delay. This should tell us which device is causing the delay.

Have a look at:
[http://askubuntu.com/questions/39316/slow-boot-after-clean-install-of-natty](http://askubuntu.com/questions/39316/slow-boot-after-clean-install-of-natty) for some suggested fixes.




I've gone through udev file, however, I wasn't able to find any distinctive, dramatic gap inbetween although some larger gaps (when compared to others) are there, but too many.

Does this mean that it is because overall capability of my hardware?
This happened when I installed puppy linux before and the forum said that
it might be because I installed it in the last part of partition (My ubuntu is in the last as well) and also because of HDD speed itself. (mine is netbook, and it seems to have 5400 rpm HDD) 

Does this fact make big difference in loading up speed? especially, installing it in the last partition. If it matters a lot, I might have to re-install. 



I also uploaded whole Udev. 
Thank you very much for help Taz. 



[http://uploaded.to/file/u0it9u83](http://uploaded.to/file/u0it9u83)

---

### Post by Toz on 2011-05-10
What make/model is your netbook?

Have you tried the suggestions at: [http://askubuntu.com/questions/39316/slow-boot-after-clean-install-of-natty](http://askubuntu.com/questions/39316/slow-boot-after-clean-install-of-natty) ?
Specifically:
   1. turning off acpi in your bios?
   2. installing cryptsetup and reinstalling ureadahead?

---

### Post by eb3ha4el on 2011-05-10
> **Toz said:**
> What make/model is your netbook?

Have you tried the suggestions at: [http://askubuntu.com/questions/39316/slow-boot-after-clean-install-of-natty](http://askubuntu.com/questions/39316/slow-boot-after-clean-install-of-natty) ?
Specifically:
   1. turning off acpi in your bios?
   2. installing cryptsetup and reinstalling ureadahead?



I'm using Netbook Toshiba NB-200


I tried 2 option before, didn't work.
For first one, I couldn't find ACPI in BIOS. 

Isn't BIOS the one that you can get into when you press F2 or something when booting? I did that, but there was no menu for it. 

I tried this method from other forum to turn off ACPI in Grub, but menu.lst does not display anything.. :(



```

gksudo gedit /boot/grub/menu.lst 

```
then add
```

"acpi=off"
```

to the line that lists your ubuntu install.
Look for the line in menu.lst that says 
 ## ## End Default Options ## 
right after that you should see the line for your install.
 __________________

---

### Post by Toz on 2011-05-10
Actually, editing grub should be done via the /etc/default/grub file then running sudo update-grub afterwards to commit the changes.

However, there is an easier way to test. Here is a link to a document that describes this: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Look for the section that starts "How to temporarily set kernel boot options on an installed OS (not wubi)". In the example there, they are adding the parameter nomodest. Just replace "nomodest" with "acpi=off" and continue with the instructions. 

This will allow you to temporarily boot with acpi=off to see if it solves the problem. If it does, there are further instructions there on how to make the change permanent.

---

### Post by eb3ha4el on 2011-05-11
> **Toz said:**
> Actually, editing grub should be done via the /etc/default/grub file then running sudo update-grub afterwards to commit the changes.

However, there is an easier way to test. Here is a link to a document that describes this: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Look for the section that starts "How to temporarily set kernel boot options on an installed OS (not wubi)". In the example there, they are adding the parameter nomodest. Just replace "nomodest" with "acpi=off" and continue with the instructions. 

This will allow you to temporarily boot with acpi=off to see if it solves the problem. If it does, there are further instructions there on how to make the change permanent.




It works Taz!! :P
HDD works like mad and login screen was loaded within 30 second I guess.

But it brought another problem unfortunately..
screen resolution got lower. 

From System setting > Monitor 
can't change it to higher (there is no option for higher ones)
and it says Monitor: Unknown

It says I'm using 800x600.
After re-boot (which should be set to the original)
booting time got slower but faster than before turning off acpi
(Before the modification: 330s, after modification: 30s, after set to origianl: 110s)

and 1024x600 is working (which is set by default) 




.... going long way.

---

### Post by physicz on 2011-05-11
acpi=off is bad, isn't it?

the boot freeze occurs for me too (so annoying) and is described exactly by this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/774896](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/774896)

here are the relevant lines in my dmesg:
[    1.020456] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[  146.400147] pci 0000:01:05.0: Boot video device

---

### Post by Toz on 2011-05-11
Have a look at: [http://ubuntuforums.org/showthread.php?t=1588579](http://ubuntuforums.org/showthread.php?t=1588579)

Try with the kernel option nohz=off.

---

### Post by eb3ha4el on 2011-05-11
> **Toz said:**
> Have a look at: [http://ubuntuforums.org/showthread.php?t=1588579](http://ubuntuforums.org/showthread.php?t=1588579)

Try with the kernel option nohz=off.



Hi Taz...
Sorry for bothering you again 

but they say I need to add nohz=off by opening a file using

```
#vi /boot/grub/grub.conf
```

but when I do so, Blue mark of ~ <- this 
are just shown, and say Newfile. 
I guess the file does not exist. I tried to find the file
in the directory but it seems it does not exist...



You mean this one, right?
[http://www.linlap.com/wiki/toshiba+nb200](http://www.linlap.com/wiki/toshiba+nb200)

---

### Post by Toz on 2011-05-11
/boot/grub/grub.conf no longer exists in ubuntu. The file you want to edit is /etc/default/grub.

However, you should test it first before committing it permanently. The test it, edit the kernel line in grub as your computer is booting (see the link in my post #16 for a link that gives instructions). If it works with this test, then you can add it permanently.

To add it permanently, make the change to /etc/default/grub and run:```
sudo update-grub
```.

---

### Post by eb3ha4el on 2011-05-12
> **Toz said:**
> /boot/grub/grub.conf no longer exists in ubuntu. The file you want to edit is /etc/default/grub.

However, you should test it first before committing it permanently. The test it, edit the kernel line in grub as your computer is booting (see the link in my post #16 for a link that gives instructions). If it works with this test, then you can add it permanently.

To add it permanently, make the change to /etc/default/grub and run:```
sudo update-grub
```.



Hi Toz
I tried it for temporarily, and it works great
But to change permanently, I did

```
# gedit /etc/default/grub
```

but I don't know where to put nohz=off...
this is the file.
can you help me again one last time?](*,)

I inserted nohz=off as you can see in the file, but having put it in that position
didnt make any change.

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" nohz=off
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by Toz on 2011-05-12
The "nohz=off" parameter should be **inside** the quotes, like this:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nohz=off"
```
Make sure you run:```
sudo update-grub
``` afterwards.

---

### Post by eb3ha4el on 2011-05-12
> **Toz said:**
> The "nohz=off" parameter should be **inside** the quotes, like this:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nohz=off"
```
Make sure you run:```
sudo update-grub
``` afterwards.




T H A N K Y O U V E R Y M U C H T O Z!!!!!!!!!!!!!!!!!!
:P:P:P:P:P:P:P


it works like charming
( at least, so far.... )

thank you again for long long guiding!!

---

