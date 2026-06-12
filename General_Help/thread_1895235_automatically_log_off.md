---
title: "automatically log off"
date: 2011-12-14
forum: General Help
---

### Post by nebula12 on 2011-12-14
i have a dell latitude E5420 and ubuntu 11.10. recently, my laptop is automatically logging off unintentionally. it is very annoying cause everything i have done till then, is lost if not yet saved. my laptop is brand new, so it can't be a matter of overheating and i have seen others have the same problem around the net but i haven't found an answer yet..i'm pretty sure it's not a key combination which is causing it, i've checked the shortcuts and it has also happened while no key is pressed ..PLEEEAAASE HELLPP

---

### Post by supercheetah on 2011-12-14
Can you post the output of *dmesg* and */var/log/syslog*?

I'm wondering if perhaps things are being killed by the out-of-memory manager in the kernel.

---

### Post by nebula12 on 2011-12-15
**dmesg:**


[  224.320905] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[  224.336890] PM: Entering mem sleep
[  224.337008] Suspending console(s) (use no_console_suspend to debug)
[  224.341339] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  224.341685] sd 0:0:0:0: [sda] Stopping disk
[  224.383743] ACPI handle has no context!
[  224.383755] sdhci-pci 0000:09:00.1: PCI INT B disabled
[  224.383772] ACPI handle has no context!
[  224.396769] ehci_hcd 0000:00:1d.0: PCI INT A disabled
[  224.448723] ehci_hcd 0000:00:1a.0: PCI INT A disabled
[  224.484986] HDA Intel 0000:00:1b.0: PCI INT A disabled
[  224.500711] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 116.904 msecs
[  224.733137] PM: suspend of drv:sd dev:0:0:0:0 complete after 392.107 msecs
[  224.733171] PM: suspend of drv:scsi dev:target0:0:0 complete after 392.117 msecs
[  224.733193] PM: suspend of drv:scsi dev:host0 complete after 392.121 msecs
[  224.764515] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 380.976 msecs
[  224.764555] PM: suspend of drv: dev:pci0000:00 complete after 380.295 msecs
[  224.764570] PM: suspend of devices complete after 427.738 msecs
[  224.764572] PM: suspend devices took 0.428 seconds
[  224.828503] PM: late suspend of devices complete after 63.968 msecs
[  224.828671] ACPI: Preparing to enter system sleep state S3
[  224.852580] PM: Saving platform NVS memory
[  224.858197] Disabling non-boot CPUs ...
[  224.960342] CPU 1 is now offline
[  225.064258] CPU 2 is now offline
[  225.065079] Broke affinity for irq 16
[  225.168200] CPU 3 is now offline
[  225.168478] Extended CMOS year: 2000
[  225.168729] ACPI: Low-level resume complete
[  225.168775] PM: Restoring platform NVS memory
[  225.169504] Extended CMOS year: 2000
[  225.169548] Enabling non-boot CPUs ...
[  225.169634] Booting Node 0 Processor 1 APIC 0x2
[  225.169635] smpboot cpu 1: start_ip = 95000
[  225.277747] CPU1 is up
[  225.277877] Booting Node 0 Processor 2 APIC 0x1
[  225.277879] smpboot cpu 2: start_ip = 95000
[  225.281074] Switched to NOHz mode on CPU #1
[  225.385633] CPU2 is up
[  225.385804] Booting Node 0 Processor 3 APIC 0x3
[  225.385805] smpboot cpu 3: start_ip = 95000
[  225.388989] Switched to NOHz mode on CPU #2
[  225.493683] CPU3 is up
[  225.496713] ACPI: Waking up from system sleep state S3
[  225.496906] Switched to NOHz mode on CPU #3
[  225.801124] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[  225.801151] mei 0000:00:16.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  225.801167] mei 0000:00:16.0: restoring config space at offset 0x4 (was 0xfedb0004, writing 0xe3d80004)
[  225.801195] ehci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  225.801210] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x4 (was 0x0, writing 0xe3d50000)
[  225.801217] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[  225.804826] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[  225.804848] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0x4, writing 0xe3d40004)
[  225.804854] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  225.804862] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
[  225.804902] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  225.804920] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0xf0, writing 0x200000f0)
[  225.804931] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  225.804937] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  225.804985] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[  225.805003] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0xf0, writing 0x200000f0)
[  225.805014] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  225.805020] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  225.805068] pcieport 0000:00:1c.2: restoring config space at offset 0xf (was 0x300, writing 0x303)
[  225.805092] pcieport 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  225.805099] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  225.805142] pcieport 0000:00:1c.5: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[  225.805158] pcieport 0000:00:1c.5: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  225.805163] pcieport 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  225.805194] pcieport 0000:00:1c.6: restoring config space at offset 0xf (was 0x300, writing 0x303)
[  225.805210] pcieport 0000:00:1c.6: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  225.805216] pcieport 0000:00:1c.6: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  225.805244] ehci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[  225.805260] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x4 (was 0x0, writing 0xe3d30000)
[  225.805267] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[  225.805338] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[  225.805378] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800003)
[  225.805468] iwlagn 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[  225.805507] iwlagn 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xe3c00004)
[  225.805515] iwlagn 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  225.805527] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[  225.805621] firewire_ohci 0000:09:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[  225.805647] firewire_ohci 0000:09:00.0: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[  225.805655] firewire_ohci 0000:09:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[  225.805701] sdhci-pci 0000:09:00.1: restoring config space at offset 0xf (was 0x200, writing 0x203)
[  225.805725] sdhci-pci 0000:09:00.1: restoring config space at offset 0x4 (was 0x0, writing 0xe3b20000)
[  225.805731] sdhci-pci 0000:09:00.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[  225.805739] sdhci-pci 0000:09:00.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[  225.805784] pci 0000:09:00.2: restoring config space at offset 0xf (was 0x300, writing 0x30b)
[  225.805805] pci 0000:09:00.2: restoring config space at offset 0x6 (was 0x0, writing 0xe3b00000)
[  225.805813] pci 0000:09:00.2: restoring config space at offset 0x4 (was 0x0, writing 0xe3b10000)
[  225.805820] pci 0000:09:00.2: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[  225.805827] pci 0000:09:00.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[  225.806051] tg3 0000:0a:00.0: restoring config space at offset 0xf (was 0x1bb, writing 0x103)
[  225.806077] tg3 0000:0a:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xe2000004)
[  225.806086] tg3 0000:0a:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xe2010004)
[  225.806092] tg3 0000:0a:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  225.806100] tg3 0000:0a:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[  225.806251] PM: early resume of devices complete after 5.196 msecs
[  225.806354] i915 0000:00:02.0: setting latency timer to 64
[  225.806369] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  225.806374] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  225.806384] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[  225.806387] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  225.806399] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  225.806409] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[  225.806426] ahci 0000:00:1f.2: setting latency timer to 64
[  225.806465] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[  225.806478] sdhci-pci 0000:09:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[  225.806486] sdhci-pci 0000:09:00.1: setting latency timer to 64
[  225.820726] sd 0:0:0:0: [sda] Starting disk
[  225.860819] firewire_core: skipped bus generations, destroying all nodes
[  225.941839] PM: resume of drv:button dev:PNP0C0D:00 complete after 135.415 msecs
[  225.984626] PM: resume of drv:hub dev:1-1:1.0 complete after 178.008 msecs
[  225.984637] PM: resume of drv: dev:ep_81 complete after 178.004 msecs
[  225.984641] PM: resume of drv:hub dev:2-1:1.0 complete after 177.955 msecs
[  225.984645] PM: resume of drv: dev:ep_00 complete after 177.989 msecs
[  225.984650] PM: resume of drv: dev:ep_81 complete after 177.948 msecs
[  225.984654] PM: resume of drv: dev:ep_00 complete after 177.932 msecs
[  226.004797] tg3 0000:0a:00.0: wake-up capability disabled by ACPI
[  226.004825] tg3 0000:0a:00.0: PME# disabled
[  226.056623] usb 1-1.4: reset high speed USB device number 3 using ehci_hcd
[  226.083386] PM: resume of drv:tg3 dev:0000:0a:00.0 complete after 277.134 msecs
[  226.160585] PM: resume of drv:i915 dev:0000:00:02.0 complete after 354.517 msecs
[  226.164433] ata5: SATA link down (SStatus 0 SControl 300)
[  226.172437] ata6: SATA link down (SStatus 0 SControl 300)
[  226.188420] ata4: SATA link down (SStatus 0 SControl 300)
[  226.188462] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  226.220594] usb 2-1.6: reset full speed USB device number 3 using ehci_hcd
[  226.222466] ata2.00: configured for UDMA/100
[  226.314572] btusb 2-1.6:1.0: no reset_resume for driver btusb?
[  226.314580] btusb 2-1.6:1.1: no reset_resume for driver btusb?
[  226.360294] firewire_core: rediscovered device fw0
[  226.401932] PM: resume of drv:battery dev:PNP0C0A:00 complete after 397.174 msecs
[  226.510450] PM: resume of drv: dev:ep_00 complete after 703.961 msecs
[  226.510467] PM: resume of drv:uvcvideo dev:1-1.4:1.1 complete after 703.998 msecs
[  226.510477] PM: resume of drv:uvcvideo dev:1-1.4:1.0 complete after 704.092 msecs
[  226.510512] PM: resume of drv: dev:ep_87 complete after 704.062 msecs
[  226.528282] PM: resume of drv:thermal dev:LNXTHERM:00 complete after 126.433 msecs
[  226.529143] Extended CMOS year: 2000
[  226.564584] PM: resume of drv:usb dev:2-1.6:1.0 complete after 758.106 msecs
[  226.564619] PM: resume of drv: dev:ep_00 complete after 757.957 msecs
[  226.564629] PM: resume of drv: dev:ep_82 complete after 758.113 msecs
[  226.564637] PM: resume of drv:usb dev:2-1.6:1.3 complete after 757.989 msecs
[  226.564655] PM: resume of drv: dev:ep_81 complete after 758.150 msecs
[  226.564662] PM: resume of drv:usb dev:2-1.6:1.2 complete after 758.065 msecs
[  226.564670] PM: resume of drv: dev:ep_02 complete after 758.140 msecs
[  226.564682] PM: resume of drv:usb dev:2-1.6:1.1 complete after 758.138 msecs
[  226.564712] PM: resume of drv: dev:ep_04 complete after 758.084 msecs
[  226.564720] PM: resume of drv: dev:ep_84 complete after 758.108 msecs
[  226.564749] PM: resume of drv: dev:ep_03 complete after 758.172 msecs
[  226.564756] PM: resume of drv: dev:ep_83 complete after 758.189 msecs
[  227.595314] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  227.995829] ata1.00: ACPI cmd ef/5a:00:00:00:00:a0 (SET FEATURES) succeeded
[  228.315349] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[  228.315675] ata1.00: configured for UDMA/133
[  228.351541] PM: resume of drv:sd dev:0:0:0:0 complete after 2546.651 msecs
[  228.351593] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 1823.800 msecs
[  228.351635] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2546.727 msecs
[  228.498360] PM: resume of devices complete after 2694.215 msecs
[  228.499299] PM: resume devices took 2.696 seconds
[  228.499441] PM: Finishing wakeup.
[  228.499445] Restarting tasks ... done.
[  228.536478] video LNXVIDEO:00: Restoring backlight state
[  228.732007] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[  230.482084] init: anacron main process (2673) killed by TERM signal
[  230.900813] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=600
[  483.503822] tg3 0000:0a:00.0: PME# enabled
[  483.545442] tg3 0000:0a:00.0: wake-up capability enabled by ACPI
[  484.241269] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[  484.571210] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  484.592138] tg3 0000:0a:00.0: irq 46 for MSI/MSI-X
[  484.672598] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  485.568459] init: anacron main process (3367) killed by TERM signal
[  485.739554] PM: Syncing filesystems ... done.
[  485.741127] PM: Preparing system for mem sleep
[  486.058104] Freezing user space processes ... (elapsed 0.01 seconds) done.
[  486.074012] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[  486.089991] PM: Entering mem sleep
[  486.090151] Suspending console(s) (use no_console_suspend to debug)
[  486.108248] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  486.108662] sd 0:0:0:0: [sda] Stopping disk
[  486.149047] ACPI handle has no context!
[  486.149060] sdhci-pci 0000:09:00.1: PCI INT B disabled
[  486.149069] ACPI handle has no context!
[  486.161816] ehci_hcd 0000:00:1a.0: PCI INT A disabled
[  486.161826] ehci_hcd 0000:00:1d.0: PCI INT A disabled
[  486.250023] HDA Intel 0000:00:1b.0: PCI INT A disabled
[  486.265726] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 116.801 msecs
[  486.491076] PM: suspend of drv:sd dev:0:0:0:0 complete after 383.322 msecs
[  486.491121] PM: suspend of drv:scsi dev:target0:0:0 complete after 383.215 msecs
[  486.491142] PM: suspend of drv:scsi dev:host0 complete after 383.124 msecs
[  486.521404] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 372.885 msecs
[  486.521433] PM: suspend of drv: dev:pci0000:00 complete after 372.793 msecs
[  486.521462] PM: suspend of devices complete after 415.999 msecs
[  486.521464] PM: suspend devices took 0.432 seconds
[  486.601333] PM: late suspend of devices complete after 79.968 msecs
[  486.601556] ACPI: Preparing to enter system sleep state S3
[  486.625421] PM: Saving platform NVS memory
[  486.633090] Disabling non-boot CPUs ...
[  486.737097] CPU 1 is now offline
[  486.840975] CPU 2 is now offline
[  486.944831] CPU 3 is now offline
[  486.945154] Extended CMOS year: 2000
[  486.945464] ACPI: Low-level resume complete
[  486.945510] PM: Restoring platform NVS memory
[  486.946244] Extended CMOS year: 2000
[  486.946289] Enabling non-boot CPUs ...
[  486.946374] Booting Node 0 Processor 1 APIC 0x2
[  486.946376] smpboot cpu 1: start_ip = 95000
[  487.054288] CPU1 is up
[  487.054780] Booting Node 0 Processor 2 APIC 0x1
[  487.054782] smpboot cpu 2: start_ip = 95000
[  487.057736] Switched to NOHz mode on CPU #1
[  487.162235] CPU2 is up
[  487.162428] Booting Node 0 Processor 3 APIC 0x3
[  487.162429] smpboot cpu 3: start_ip = 95000
[  487.165594] Switched to NOHz mode on CPU #2
[  487.270064] CPU3 is up
[  487.273108] ACPI: Waking up from system sleep state S3
[  487.273471] Switched to NOHz mode on CPU #3
[  487.577525] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[  487.577551] mei 0000:00:16.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  487.577568] mei 0000:00:16.0: restoring config space at offset 0x4 (was 0xfedb0004, writing 0xe3d80004)
[  487.577595] ehci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  487.577611] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x4 (was 0x0, writing 0xe3d50000)
[  487.577618] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[  487.581217] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[  487.581239] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0x4, writing 0xe3d40004)
[  487.581245] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  487.581254] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
[  487.581290] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  487.581315] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  487.581322] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  487.581371] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[  487.581395] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  487.581403] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  487.581451] pcieport 0000:00:1c.2: restoring config space at offset 0xf (was 0x300, writing 0x303)
[  487.581475] pcieport 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  487.581482] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  487.581524] pcieport 0000:00:1c.5: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[  487.581540] pcieport 0000:00:1c.5: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  487.581545] pcieport 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  487.581576] pcieport 0000:00:1c.6: restoring config space at offset 0xf (was 0x300, writing 0x303)
[  487.581592] pcieport 0000:00:1c.6: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  487.581598] pcieport 0000:00:1c.6: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  487.581626] ehci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[  487.581641] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x4 (was 0x0, writing 0xe3d30000)
[  487.581648] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[  487.581720] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[  487.581761] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800003)
[  487.581850] iwlagn 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[  487.581889] iwlagn 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xe3c00004)
[  487.581898] iwlagn 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  487.581909] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100406)
[  487.581999] firewire_ohci 0000:09:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[  487.582026] firewire_ohci 0000:09:00.0: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[  487.582034] firewire_ohci 0000:09:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[  487.582079] sdhci-pci 0000:09:00.1: restoring config space at offset 0xf (was 0x200, writing 0x203)
[  487.582103] sdhci-pci 0000:09:00.1: restoring config space at offset 0x4 (was 0x0, writing 0xe3b20000)
[  487.582109] sdhci-pci 0000:09:00.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[  487.582117] sdhci-pci 0000:09:00.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[  487.582162] pci 0000:09:00.2: restoring config space at offset 0xf (was 0x300, writing 0x30b)
[  487.582183] pci 0000:09:00.2: restoring config space at offset 0x6 (was 0x0, writing 0xe3b00000)
[  487.582191] pci 0000:09:00.2: restoring config space at offset 0x4 (was 0x0, writing 0xe3b10000)
[  487.582197] pci 0000:09:00.2: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[  487.582205] pci 0000:09:00.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[  487.582427] tg3 0000:0a:00.0: restoring config space at offset 0xf (was 0x1bb, writing 0x103)
[  487.582453] tg3 0000:0a:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xe2000004)
[  487.582462] tg3 0000:0a:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xe2010004)
[  487.582468] tg3 0000:0a:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  487.582477] tg3 0000:0a:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100406)
[  487.582626] PM: early resume of devices complete after 5.173 msecs
[  487.582724] i915 0000:00:02.0: setting latency timer to 64
[  487.582856] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  487.582863] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[  487.582876] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  487.582882] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  487.582896] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  487.582904] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[  487.582935] ahci 0000:00:1f.2: setting latency timer to 64
[  487.582937] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[  487.582988] sdhci-pci 0000:09:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[  487.582995] sdhci-pci 0000:09:00.1: setting latency timer to 64
[  487.597156] sd 0:0:0:0: [sda] Starting disk
[  487.637225] firewire_core: skipped bus generations, destroying all nodes
[  487.760928] PM: resume of drv:hub dev:2-1:1.0 complete after 177.904 msecs
[  487.760932] PM: resume of drv: dev:ep_00 complete after 177.936 msecs
[  487.760943] PM: resume of drv:hub dev:1-1:1.0 complete after 177.956 msecs
[  487.760946] PM: resume of drv: dev:ep_00 complete after 177.907 msecs
[  487.760950] PM: resume of drv: dev:ep_81 complete after 177.919 msecs
[  487.760953] PM: resume of drv: dev:ep_81 complete after 177.964 msecs
[  487.816889] tg3 0000:0a:00.0: wake-up capability disabled by ACPI
[  487.816899] tg3 0000:0a:00.0: PME# disabled
[  487.896451] PM: resume of drv:tg3 dev:0000:0a:00.0 complete after 313.841 msecs
[  487.896553] usb 1-1.4: reset high speed USB device number 3 using ehci_hcd
[  487.896716] PM: resume of drv:button dev:PNP0C0D:00 complete after 314.369 msecs
[  487.924702] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  487.924723] ata6: SATA link down (SStatus 0 SControl 300)
[  487.944662] ata4: SATA link down (SStatus 0 SControl 300)
[  487.948637] ata5: SATA link down (SStatus 0 SControl 300)
[  487.958627] ata2.00: configured for UDMA/100
[  487.996772] PM: resume of drv:i915 dev:0000:00:02.0 complete after 414.606 msecs
[  488.060677] usb 2-1.6: reset full speed USB device number 3 using ehci_hcd
[  488.136411] firewire_core: rediscovered device fw0
[  488.154780] btusb 2-1.6:1.0: no reset_resume for driver btusb?
[  488.154788] btusb 2-1.6:1.1: no reset_resume for driver btusb?
[  488.326578] PM: resume of drv:battery dev:PNP0C0A:00 complete after 393.292 msecs
[  488.350621] PM: resume of drv:uvcvideo dev:1-1.4:1.0 complete after 768.323 msecs
[  488.350641] PM: resume of drv: dev:ep_00 complete after 768.289 msecs
[  488.350664] PM: resume of drv: dev:ep_87 complete after 768.321 msecs
[  488.350675] PM: resume of drv:uvcvideo dev:1-1.4:1.1 complete after 768.317 msecs
[  488.361930] Extended CMOS year: 2000
[  488.404440] PM: resume of drv: dev:ep_00 complete after 822.103 msecs
[  488.404452] PM: resume of drv:usb dev:2-1.6:1.3 complete after 822.106 msecs
[  488.404460] PM: resume of drv:usb dev:2-1.6:1.2 complete after 822.142 msecs
[  488.404468] PM: resume of drv:usb dev:2-1.6:1.1 complete after 822.161 msecs
[  488.404493] PM: resume of drv:usb dev:2-1.6:1.0 complete after 822.207 msecs
[  488.404495] PM: resume of drv: dev:ep_84 complete after 822.174 msecs
[  488.404501] PM: resume of drv: dev:ep_04 complete after 822.179 msecs
[  488.404504] PM: resume of drv: dev:ep_03 complete after 822.190 msecs
[  488.404506] PM: resume of drv: dev:ep_83 complete after 822.198 msecs
[  488.404508] PM: resume of drv: dev:ep_81 complete after 822.217 msecs
[  488.404510] PM: resume of drv: dev:ep_02 complete after 822.211 msecs
[  488.404512] PM: resume of drv: dev:ep_82 complete after 822.218 msecs
[  489.386799] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  489.695166] ata1.00: ACPI cmd ef/5a:00:00:00:00:a0 (SET FEATURES) succeeded
[  489.886879] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[  489.887185] ata1.00: configured for UDMA/133
[  489.925471] PM: resume of drv:sd dev:0:0:0:0 complete after 2345.208 msecs
[  489.925532] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 1565.416 msecs
[  489.925553] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2345.282 msecs
[  490.068644] PM: resume of devices complete after 2489.205 msecs
[  490.069447] PM: resume devices took 2.488 seconds
[  490.069577] PM: Finishing wakeup.
[  490.070085] Restarting tasks ... done.
[  490.114958] video LNXVIDEO:00: Restoring backlight state
[  490.338953] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[  492.007213] init: anacron main process (3705) killed by TERM signal
[  492.595373] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=600
[  512.066709] wlan0: authenticate with 00:17:59:db:5b:10 (try 1)
[  512.070744] wlan0: authenticated
[  512.071389] wlan0: associate with 00:17:59:db:5b:10 (try 1)
[  512.075569] wlan0: RX AssocResp from 00:17:59:db:5b:10 (capab=0x431 status=0 aid=130)
[  512.075579] wlan0: associated
[  512.079291] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  522.591773] wlan0: no IPv6 routers present
[  524.893374] wlan0: deauthenticating from 00:17:59:db:5b:10 by local choice (reason=3)
[  524.909174] cfg80211: All devices are disconnected, going to restore regulatory settings
[  524.909208] cfg80211: Restoring regulatory settings
[  524.909220] cfg80211: Calling CRDA to update world regulatory domain
[  524.927711] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  524.927735] cfg80211: World regulatory domain updated:
[  524.927741] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  524.927752] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  524.927773] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  524.927782] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  524.927791] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  524.927800] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  528.269068] wlan0: authenticate with 00:1c:10:b2:a8:3e (try 1)
[  528.271937] wlan0: authenticated
[  528.308974] wlan0: associate with 00:1c:10:b2:a8:3e (try 1)
[  528.335157] wlan0: RX AssocResp from 00:1c:10:b2:a8:3e (capab=0x421 status=0 aid=13)
[  528.335169] wlan0: associated
[  538.810792] wlan0: no IPv6 routers present


the **/var/log/syslog** gives "Permission denied"

you mean it may be a RAM problem?? but my pc is brand new and i have a 4 GB RAM memory

---

### Post by supercheetah on 2011-12-16
Sorry about being so late to reply.  I've been a little busy.

I'm not seeing anything from dmesg that worries me yet.

In order to view the syslog, you'll need to open it as root, so try the following:

```

gksudo cat /var/log/syslog

```

Also, when you post it here, make sure to wrap it in the [ code ] (no spaces) markups.

---

### Post by nebula12 on 2011-12-17
this is what i took from the syslog:

```
Dec 17 03:02:53 werecat-Latitude-E5420 rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="854" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Dec 17 03:02:54 werecat-Latitude-E5420 anacron[17188]: Job `cron.daily' terminated
Dec 17 03:02:54 werecat-Latitude-E5420 anacron[17188]: Normal exit (1 job run)
Dec 17 03:13:38 werecat-Latitude-E5420 kernel: Kernel logging (proc) stopped.
Dec 17 03:13:38 werecat-Latitude-E5420 rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="854" x-info="http://www.rsyslog.com"] exiting on signal 15.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: imklog 5.8.1, log source = /proc/kmsg started.
Dec 17 11:06:19 werecat-Latitude-E5420 rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="953" x-info="http://www.rsyslog.com"] start
Dec 17 11:06:19 werecat-Latitude-E5420 rsyslogd: rsyslogd's groupid changed to 103
Dec 17 11:06:19 werecat-Latitude-E5420 rsyslogd: rsyslogd's userid changed to 101
Dec 17 11:06:19 werecat-Latitude-E5420 rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Linux version 3.0.0-14-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 (Ubuntu 3.0.0-14.23-generic 3.0.9)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=6ce07dc3-efdb-4e82-95de-616285d8e63c ro quiet splash vt.handoff=7
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] KERNEL supported cpus:
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   Intel GenuineIntel
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   AMD AuthenticAMD
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   Centaur CentaurHauls
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009a800 (usable)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 000000000009a800 - 00000000000a0000 (reserved)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 0000000040200000 - 00000000caa85000 (usable)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 00000000caa85000 - 00000000caac9000 (reserved)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 00000000caac9000 - 00000000cadb7000 (usable)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 00000000cadb7000 - 00000000cade7000 (reserved)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 00000000cade7000 - 00000000cafe7000 (ACPI NVS)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 00000000cafe7000 - 00000000cafff000 (ACPI data)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 00000000cafff000 - 00000000cb000000 (usable)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 00000000cb800000 - 00000000cfa00000 (reserved)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 00000000ffc00000 - 00000000ffc20000 (reserved)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000012f000000 (usable)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] DMI 2.6 present.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] DMI: Dell Inc. Latitude E5420/0H5TG2, BIOS A01 04/20/2011
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] No AGP bridge found
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] last_pfn = 0x12f000 max_arch_pfn = 0x400000000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] MTRR default type: uncachable
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   00000-9FFFF write-back
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   A0000-BFFFF uncachable
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   C0000-FFFFF write-protect
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] MTRR variable ranges enabled:
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   1 base 080000000 mask FC0000000 write-back
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   2 base 0C0000000 mask FF8000000 write-back
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   3 base 0C8000000 mask FFC000000 write-back
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   4 base 0CB000000 mask FFF000000 uncachable
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   5 base 100000000 mask FE0000000 write-back
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   6 base 120000000 mask FF0000000 write-back
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   7 base 12F000000 mask FFF000000 uncachable
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   8 disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   9 disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] original variable MTRRs
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] reg 2, base: 3GB, range: 128MB, type WB
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] reg 3, base: 3200MB, range: 64MB, type WB
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] reg 4, base: 3248MB, range: 16MB, type UC
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] reg 5, base: 4GB, range: 512MB, type WB
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] reg 6, base: 4608MB, range: 256MB, type WB
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] reg 7, base: 4848MB, range: 16MB, type UC
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] total RAM covered: 4000M
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Found optimal setting for mtrr clean up
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  gran_size: 64K 	chunk_size: 32M 	num_reg: 8  	lose cover RAM: 0G
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] New variable MTRRs
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] reg 2, base: 3GB, range: 128MB, type WB
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] reg 3, base: 3200MB, range: 64MB, type WB
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] reg 4, base: 3248MB, range: 16MB, type UC
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] reg 5, base: 4GB, range: 512MB, type WB
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] reg 6, base: 4608MB, range: 256MB, type WB
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] reg 7, base: 4848MB, range: 16MB, type UC
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] e820 update range: 00000000cb000000 - 0000000100000000 (usable) ==> (reserved)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] last_pfn = 0xcb000 max_arch_pfn = 0x400000000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] found SMP MP-table at [ffff8800000f2000] f2000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] initial memory mapped : 0 - 20000000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Base memory trampoline at [ffff880000095000] 95000 size 20480
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cb000000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  0000000000 - 00cb000000 page 2M
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] kernel direct mapping tables up to cb000000 @ 1fffb000-20000000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] init_memory_mapping: 0000000100000000-000000012f000000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  0100000000 - 012f000000 page 2M
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] kernel direct mapping tables up to 12f000000 @ cadb1000-cadb7000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] RAMDISK: 365ae000 - 372cf000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: RSDP 00000000000fe300 00024 (v02 DELL  )
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: XSDT 00000000caffde18 00074 (v01 DELL    CBX3    06222004 MSFT 00010013)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: FACP 00000000caf87d98 000F4 (v04 DELL    CBX3    06222004 MSFT 00010013)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110413/tbfadt-369)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xCAFE4E40/0x00000000CAFE4D40, using 32 (20110413/tbfadt-489)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: DSDT 00000000caf7e018 0864E (v02 INT430 SYSFexxx 00001001 INTL 20090903)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: FACS 00000000cafe4e40 00040
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: APIC 00000000caffcf18 000CC (v02 DELL    CBX3    06222004 MSFT 00010013)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: TCPA 00000000cafe5d18 00032 (v02                 00000000      00000000)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: MCFG 00000000cafe5c98 0003C (v01 DELL   SNDYBRDG 06222004 MSFT 00000097)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: HPET 00000000cafe5c18 00038 (v01 A M I   PCHHPET 06222004 AMI. 00000003)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: BOOT 00000000cafe5b98 00028 (v01 DELL   CBX3     06222004 AMI  00010013)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: SSDT 00000000caf7d818 007C2 (v01  PmRef  Cpu0Ist 00003000 INTL 20090903)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: SSDT 00000000caf7c018 00996 (v01  PmRef    CpuPm 00003000 INTL 20090903)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: DMAR 00000000caf87c18 000E8 (v01 INTEL      SNB  00000001 INTL 00000001)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: SLIC 00000000caf88a18 00176 (v03 DELL    CBX3    06222004 MSFT 00010013)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] No NUMA configuration found
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Faking a node at 0000000000000000-000000012f000000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000012f000000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   NODE_DATA [000000012effb000 - 000000012effffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff88012a600000-ffff88012dffffff] on node 0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Zone PFN ranges:
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   Normal   0x00100000 -> 0x0012f000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Movable zone start PFN for each node
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] early_node_map[7] active PFN ranges
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]     0: 0x00000010 -> 0x0000009a
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]     0: 0x00000100 -> 0x00020000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]     0: 0x00020200 -> 0x00040000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]     0: 0x00040200 -> 0x000caa85
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]     0: 0x000caac9 -> 0x000cadb7
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]     0: 0x000cafff -> 0x000cb000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]     0: 0x00100000 -> 0x0012f000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] On node 0 totalpages: 1022206
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   DMA zone: 5 pages reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   DMA zone: 3917 pages, LIFO batch:0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   DMA32 zone: 811436 pages, LIFO batch:31
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   Normal zone: 2632 pages used for memmap
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000]   Normal zone: 189880 pages, LIFO batch:31
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] SMP: Allowing 16 CPUs, 12 hotplug CPUs
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] nr_irqs_gsi: 40
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 00000000caa85000 - 00000000caac9000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 00000000cadb7000 - 00000000cade7000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 00000000cade7000 - 00000000cafe7000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 00000000cafe7000 - 00000000cafff000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 00000000cb000000 - 00000000cb800000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 00000000cb800000 - 00000000cfa00000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 00000000cfa00000 - 00000000fed1c000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ffc00000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffc20000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc20000 - 0000000100000000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Allocating PCI resources starting at cfa00000 (gap: cfa00000:2f31c000)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:16 nr_node_ids:1
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88012ec00000 s79616 r8192 d22784 u131072
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] pcpu-alloc: s79616 r8192 d22784 u131072 alloc=1*2097152
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1005233
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Policy zone: Normal
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=6ce07dc3-efdb-4e82-95de-616285d8e63c ro quiet splash vt.handoff=7
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Checking aperture...
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] No AGP bridge found
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Queued invalidation will be enabled to support x2apic and Intr-remapping.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Memory: 3934704k/4964352k available (6109k kernel code, 875528k absent, 154120k reserved, 4876k data, 984k init)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Hierarchical RCU implementation.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] NR_IRQS:16640 nr_irqs:808 16
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Extended CMOS year: 2000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] vt handoff: transparent VT on vt#7
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Console: colour dummy device 80x25
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] console [tty0] enabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] allocated 33554432 bytes of page_cgroup
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] hpet clockevent registered
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000000] Fast TSC calibration using PIT
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.004000] Detected 2494.838 MHz processor.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4989.67 BogoMIPS (lpj=9979352)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000006] pid_max: default: 32768 minimum: 301
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000028] Security Framework initialized
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000040] AppArmor: AppArmor initialized
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000041] Yama: becoming mindful.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.000412] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.001260] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.001595] Mount-cache hash table entries: 256
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.001694] Initializing cgroup subsys cpuacct
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.001698] Initializing cgroup subsys memory
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.001704] Initializing cgroup subsys devices
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.001706] Initializing cgroup subsys freezer
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.001707] Initializing cgroup subsys net_cls
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.001709] Initializing cgroup subsys blkio
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.001713] Initializing cgroup subsys perf_event
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.001737] CPU: Physical Processor ID: 0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.001739] CPU: Processor Core ID: 0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.001743] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.001744] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.001747] mce: CPU supports 7 MCE banks
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.001758] CPU0: Thermal monitoring enabled (TM1)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.001765] using mwait in idle threads.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.004004] ACPI: Core revision 20110413
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.009004] ftrace: allocating 25647 entries in 101 pages
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018019] DMAR: Host address width 36
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018022] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018028] IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018030] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018035] IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018036] DMAR: RMRR base: 0x000000cadc6000 end: 0x000000cadd5fff
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018038] DMAR: RMRR base: 0x000000cb800000 end: 0x000000cf9fffff
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018039] DMAR: No ATSR found
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018109] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018110] HPET id 0 under DRHD base 0xfed91000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018111] HPET id 0 under DRHD base 0xfed91000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018112] HPET id 0 under DRHD base 0xfed91000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018113] HPET id 0 under DRHD base 0xfed91000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018115] HPET id 0 under DRHD base 0xfed91000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018116] HPET id 0 under DRHD base 0xfed91000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018117] HPET id 0 under DRHD base 0xfed91000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018118] HPET id 0 under DRHD base 0xfed91000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018299] Enabled IRQ remapping in x2apic mode
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018300] Enabling x2apic
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018301] Enabled x2apic
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018307] Switched APIC routing to cluster x2apic.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.018684] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.058325] CPU0: Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz stepping 07
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.163740] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.163746] ... version:                3
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.163747] ... bit width:              48
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.163748] ... generic registers:      4
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.163749] ... value mask:             0000ffffffffffff
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.163750] ... max period:             000000007fffffff
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.163752] ... fixed-purpose events:   3
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.163753] ... event mask:             000000070000000f
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.164132] Booting Node   0, Processors  #1
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.164134] smpboot cpu 1: start_ip = 95000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.271758]  #2
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.271759] smpboot cpu 2: start_ip = 95000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.379662]  #3
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.379664] smpboot cpu 3: start_ip = 95000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.487425] Brought up 4 CPUs
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.487427] Total of 4 processors activated (19955.00 BogoMIPS).
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.489893] devtmpfs: initialized
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.490006] PM: Registering ACPI NVS region at cade7000 (2097152 bytes)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.490037] Dell Latitude E5420 series board detected. Selecting PCI-method for reboots.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.491209] print_constraints: dummy: 
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.491235] Time: 11:06:04  Date: 12/17/11
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.491264] NET: Registered protocol family 16
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.491344] Trying to unpack rootfs image as initramfs...
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.491358] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.491360] ACPI: bus type pci registered
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.491423] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.491425] PCI: not using MMCONFIG
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.491426] PCI: Using configuration type 1 for base access
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.491432] dmi type 0xB1 record - unknown flag
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.492032] bio: create slab <bio-0> at 0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.493306] ACPI: EC: Look up EC in DSDT
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.527303] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.701236] Freeing initrd memory: 13444k freed
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.711114] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.751305] ACPI: SSDT 00000000cadd7718 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20090903)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.751621] ACPI: Dynamic OEM Table Load:
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.751623] ACPI: SSDT           (null) 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20090903)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.763187] ACPI: SSDT 00000000cadd8a98 00303 (v01  PmRef    ApIst 00003000 INTL 20090903)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.763526] ACPI: Dynamic OEM Table Load:
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.763528] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20090903)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.775055] ACPI: SSDT 00000000cadd6d98 00119 (v01  PmRef    ApCst 00003000 INTL 20090903)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.775368] ACPI: Dynamic OEM Table Load:
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.775370] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20090903)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.858910] ACPI: Interpreter enabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.858913] ACPI: (supports S0 S3 S4 S5)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.858931] ACPI: Using IOAPIC for interrupt routing
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.858949] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    0.859288] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in ACPI motherboard resources
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.410427] ACPI: EC: GPE = 0x10, I/O: command/status = 0x934, data = 0x930
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.434150] ACPI: No dock devices found.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.434152] HEST: Table not found.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.434154] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.434419] \_SB_.PCI0:_OSC invalid UUID
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.434421] _OSC request data:1 8 1f 
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.434424] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.434890] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.434892] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.434894] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.434897] pci_root PNP0A08:00: host bridge window [mem 0xcfa00000-0xfeafffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.434899] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.434908] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.434940] pci 0000:00:02.0: [8086:0126] type 0 class 0x000300
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.434950] pci 0000:00:02.0: reg 10: [mem 0xe1c00000-0xe1ffffff 64bit]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.434956] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.434960] pci 0000:00:02.0: reg 20: [io  0x7000-0x703f]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435008] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435032] pci 0000:00:16.0: reg 10: [mem 0xe3d80000-0xe3d8000f 64bit]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435094] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435098] pci 0000:00:16.0: PME# disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435130] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435151] pci 0000:00:1a.0: reg 10: [mem 0xe3d50000-0xe3d503ff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435223] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435227] pci 0000:00:1a.0: PME# disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435250] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435266] pci 0000:00:1b.0: reg 10: [mem 0xe3d40000-0xe3d43fff 64bit]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435321] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435325] pci 0000:00:1b.0: PME# disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435348] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435448] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435453] pci 0000:00:1c.0: PME# disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435485] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435587] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435593] pci 0000:00:1c.1: PME# disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435626] pci 0000:00:1c.2: [8086:1c14] type 1 class 0x000604
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435725] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435731] pci 0000:00:1c.2: PME# disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435764] pci 0000:00:1c.5: [8086:1c1a] type 1 class 0x000604
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435830] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435834] pci 0000:00:1c.5: PME# disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435858] pci 0000:00:1c.6: [8086:1c1c] type 1 class 0x000604
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435924] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435928] pci 0000:00:1c.6: PME# disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435958] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.435978] pci 0000:00:1d.0: reg 10: [mem 0xe3d30000-0xe3d303ff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436051] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436055] pci 0000:00:1d.0: PME# disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436079] pci 0000:00:1f.0: [8086:1c49] type 0 class 0x000601
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436193] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436212] pci 0000:00:1f.2: reg 10: [io  0x70b0-0x70b7]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436220] pci 0000:00:1f.2: reg 14: [io  0x70a0-0x70a3]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436228] pci 0000:00:1f.2: reg 18: [io  0x7090-0x7097]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436236] pci 0000:00:1f.2: reg 1c: [io  0x7080-0x7083]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436245] pci 0000:00:1f.2: reg 20: [io  0x7060-0x707f]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436253] pci 0000:00:1f.2: reg 24: [mem 0xe3d20000-0xe3d207ff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436285] pci 0000:00:1f.2: PME# supported from D3hot
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436289] pci 0000:00:1f.2: PME# disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436307] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436322] pci 0000:00:1f.3: reg 10: [mem 0xe3d10000-0xe3d100ff 64bit]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436343] pci 0000:00:1f.3: reg 20: [io  0x7040-0x705f]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436440] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436446] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436452] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436461] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436667] pci 0000:02:00.0: [8086:0082] type 0 class 0x000280
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.436814] pci 0000:02:00.0: reg 10: [mem 0xe3c00000-0xe3c01fff 64bit]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.437374] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.437408] pci 0000:02:00.0: PME# disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.437595] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.437599] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.437604] pci 0000:00:1c.1:   bridge window [mem 0xe3c00000-0xe3cfffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.437610] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.437654] pci 0000:00:1c.2: PCI bridge to [bus 03-08]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.437659] pci 0000:00:1c.2:   bridge window [io  0x6000-0x6fff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.437663] pci 0000:00:1c.2:   bridge window [mem 0xe3100000-0xe3afffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.437669] pci 0000:00:1c.2:   bridge window [mem 0xe1100000-0xe1afffff 64bit pref]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.437752] pci 0000:09:00.0: [1217:13f7] type 0 class 0x000c00
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.437784] pci 0000:09:00.0: reg 10: [mem 0xe3b30000-0xe3b30fff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.437985] pci 0000:09:00.0: supports D1 D2
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.437986] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.437994] pci 0000:09:00.0: PME# disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.438074] pci 0000:09:00.1: [1217:8321] type 0 class 0x000805
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.438108] pci 0000:09:00.1: reg 10: [mem 0xe3b20000-0xe3b201ff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.438305] pci 0000:09:00.1: supports D1 D2
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.438306] pci 0000:09:00.1: PME# supported from D0 D1 D2 D3hot D3cold
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.438315] pci 0000:09:00.1: PME# disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.438385] pci 0000:09:00.2: [1217:8331] type 0 class 0x000180
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.438419] pci 0000:09:00.2: reg 10: [mem 0xe3b10000-0xe3b103ff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.438464] pci 0000:09:00.2: reg 18: [mem 0xe3b00000-0xe3b003ff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.438617] pci 0000:09:00.2: supports D1 D2
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.438619] pci 0000:09:00.2: PME# supported from D0 D1 D2 D3hot D3cold
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.438627] pci 0000:09:00.2: PME# disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.438729] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.438734] pci 0000:00:1c.5:   bridge window [io  0xf000-0x0000] (disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.438738] pci 0000:00:1c.5:   bridge window [mem 0xe3b00000-0xe3bfffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.438744] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.438979] pci 0000:0a:00.0: [14e4:1681] type 0 class 0x000200
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439019] pci 0000:0a:00.0: reg 10: [mem 0xe2010000-0xe201ffff 64bit]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439050] pci 0000:0a:00.0: reg 18: [mem 0xe2000000-0xe200ffff 64bit]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439182] pci 0000:0a:00.0: PME# supported from D3hot D3cold
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439190] pci 0000:0a:00.0: PME# disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439244] pci 0000:00:1c.6: PCI bridge to [bus 0a-11]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439248] pci 0000:00:1c.6:   bridge window [io  0x2000-0x5fff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439252] pci 0000:00:1c.6:   bridge window [mem 0xe2000000-0xe30fffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439259] pci 0000:00:1c.6:   bridge window [mem 0xe0000000-0xe10fffff 64bit pref]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439285] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439418] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439447] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439473] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP07._PRT]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439505] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439568] \_SB_.PCI0:_OSC invalid UUID
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439569] _OSC request data:1 1f 1f 
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439573]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439598] \_SB_.PCI0:_OSC invalid UUID
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439599] _OSC request data:1 0 1d 
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439602]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.439603] ACPI _OSC control for PCIe not granted, disabling ASPM
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442077] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442115] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442150] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442188] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442223] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442258] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442293] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 *5 6 7 10 12 14 15)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442327] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442397] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442403] vgaarb: loaded
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442404] vgaarb: bridge control possible 0000:00:02.0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442526] SCSI subsystem initialized
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442570] libata version 3.00 loaded.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442597] usbcore: registered new interface driver usbfs
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442607] usbcore: registered new interface driver hub
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442626] usbcore: registered new device driver usb
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.442686] PCI: Using ACPI for IRQ routing
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.444427] PCI: pci_cache_line_size set to 64 bytes
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.444514] reserve RAM buffer: 000000000009a800 - 000000000009ffff 
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.444516] reserve RAM buffer: 00000000caa85000 - 00000000cbffffff 
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.444519] reserve RAM buffer: 00000000cadb7000 - 00000000cbffffff 
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.444521] reserve RAM buffer: 00000000cb000000 - 00000000cbffffff 
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.444523] reserve RAM buffer: 000000012f000000 - 000000012fffffff 
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.444591] NetLabel: Initializing
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.444593] NetLabel:  domain hash size = 128
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.444594] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.444602] NetLabel:  unlabeled traffic allowed by default
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.444634] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.444639] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.446653] Switching to clocksource hpet
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.450020] Switched to NOHz mode on CPU #0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.450120] Switched to NOHz mode on CPU #1
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.450133] Switched to NOHz mode on CPU #3
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.450169] Switched to NOHz mode on CPU #2
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.450944] AppArmor: AppArmor Filesystem Enabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.450963] pnp: PnP ACPI init
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.450974] ACPI: bus type pnp registered
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451245] pnp 00:00: [bus 00-3e]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451247] pnp 00:00: [io  0x0000-0x0cf7 window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451249] pnp 00:00: [io  0x0cf8-0x0cff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451250] pnp 00:00: [io  0x0d00-0xffff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451252] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451254] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451255] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451257] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451259] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451260] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451262] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451264] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451265] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451267] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451268] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451270] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451272] pnp 00:00: [mem 0x000ec000-0x000effff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451273] pnp 00:00: [mem 0x000f0000-0x000fffff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451275] pnp 00:00: [mem 0xcfa00000-0xfeafffff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451277] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451329] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451341] pnp 00:01: [io  0x0000-0x001f]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451342] pnp 00:01: [io  0x0081-0x0091]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451344] pnp 00:01: [io  0x0093-0x009f]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451345] pnp 00:01: [io  0x00c0-0x00df]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451347] pnp 00:01: [dma 4]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451364] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451371] pnp 00:02: [mem 0xff000000-0xffffffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451384] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451444] pnp 00:03: [mem 0xfed00000-0xfed003ff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451476] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451479] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451487] pnp 00:04: [io  0x00f0]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451499] pnp 00:04: [irq 13]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451515] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451524] pnp 00:05: [io  0x002e-0x002f]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451525] pnp 00:05: [io  0x004e-0x004f]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451526] pnp 00:05: [io  0x0061]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451528] pnp 00:05: [io  0x0063]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451529] pnp 00:05: [io  0x0065]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451530] pnp 00:05: [io  0x0067]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451533] pnp 00:05: [io  0x0070]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451534] pnp 00:05: [io  0x0080]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451535] pnp 00:05: [io  0x0092]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451537] pnp 00:05: [io  0x00b2-0x00b3]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451538] pnp 00:05: [io  0x0680-0x069f]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451539] pnp 00:05: [io  0x1000-0x100f]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451541] pnp 00:05: [io  0xffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451542] pnp 00:05: [io  0xffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451543] pnp 00:05: [io  0x0400-0x047f]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451545] pnp 00:05: [io  0x0500-0x057f]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451546] pnp 00:05: [io  0x164e-0x164f]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451574] system 00:05: [io  0x0680-0x069f] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451576] system 00:05: [io  0x1000-0x100f] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451578] system 00:05: [io  0xffff] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451580] system 00:05: [io  0xffff] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451582] system 00:05: [io  0x0400-0x047f] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451583] system 00:05: [io  0x0500-0x057f] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451585] system 00:05: [io  0x164e-0x164f] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451588] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451594] pnp 00:06: [io  0x0070-0x0077]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451600] pnp 00:06: [irq 8]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451614] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451622] pnp 00:07: [io  0x0060]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451623] pnp 00:07: [io  0x0064]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451628] pnp 00:07: [irq 1]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.451644] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.454908] pnp 00:08: Plug and Play ACPI device, IDs PNP0401 (disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.454921] pnp 00:09: [irq 12]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.454940] pnp 00:09: Plug and Play ACPI device, IDs DLL049b PNP0f13 (active)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455046] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455048] pnp 00:0a: [mem 0xfed10000-0xfed17fff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455049] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455051] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455052] pnp 00:0a: [mem 0xf8000000-0xfbffffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455053] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455055] pnp 00:0a: [mem 0xfed90000-0xfed93fff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455056] pnp 00:0a: [mem 0xfed45000-0xfed8ffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455058] pnp 00:0a: [mem 0xff000000-0xffffffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455059] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455061] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455063] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455099] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455101] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455103] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455105] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455107] system 00:0a: [mem 0xf8000000-0xfbffffff] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455109] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455111] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455113] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455115] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455117] system 00:0a: [mem 0xfee00000-0xfeefffff] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455119] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455178] pnp 00:0b: [irq 23]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.455202] pnp 00:0b: Plug and Play ACPI device, IDs SMO8800 (active)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.478793] pnp 00:0c: [mem 0x20000000-0x201fffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.478797] pnp 00:0c: [mem 0x40000000-0x401fffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.482663] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.482665] system 00:0c: [mem 0x40000000-0x401fffff] has been reserved
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.482668] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.482676] pnp: PnP ACPI: found 13 devices
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.482678] ACPI: ACPI bus type pnp unregistered
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488116] PCI: max bus depth: 1 pci_try_num: 2
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488159] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488161] pci 0000:00:1c.0:   bridge window [io  disabled]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488166] pci 0000:00:1c.0:   bridge window [mem disabled]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488170] pci 0000:00:1c.0:   bridge window [mem pref disabled]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488177] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488178] pci 0000:00:1c.1:   bridge window [io  disabled]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488184] pci 0000:00:1c.1:   bridge window [mem 0xe3c00000-0xe3cfffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488188] pci 0000:00:1c.1:   bridge window [mem pref disabled]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488194] pci 0000:00:1c.2: PCI bridge to [bus 03-08]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488198] pci 0000:00:1c.2:   bridge window [io  0x6000-0x6fff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488203] pci 0000:00:1c.2:   bridge window [mem 0xe3100000-0xe3afffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488208] pci 0000:00:1c.2:   bridge window [mem 0xe1100000-0xe1afffff 64bit pref]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488214] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488216] pci 0000:00:1c.5:   bridge window [io  disabled]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488221] pci 0000:00:1c.5:   bridge window [mem 0xe3b00000-0xe3bfffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488225] pci 0000:00:1c.5:   bridge window [mem pref disabled]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488231] pci 0000:00:1c.6: PCI bridge to [bus 0a-11]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488235] pci 0000:00:1c.6:   bridge window [io  0x2000-0x5fff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488240] pci 0000:00:1c.6:   bridge window [mem 0xe2000000-0xe30fffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488244] pci 0000:00:1c.6:   bridge window [mem 0xe0000000-0xe10fffff 64bit pref]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488264] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488270] pci 0000:00:1c.0: setting latency timer to 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488281] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488286] pci 0000:00:1c.1: setting latency timer to 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488296] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488301] pci 0000:00:1c.2: setting latency timer to 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488308] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488312] pci 0000:00:1c.5: setting latency timer to 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488319] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488323] pci 0000:00:1c.6: setting latency timer to 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488327] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488329] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488330] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488332] pci_bus 0000:00: resource 7 [mem 0xcfa00000-0xfeafffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488334] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488336] pci_bus 0000:02: resource 1 [mem 0xe3c00000-0xe3cfffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488338] pci_bus 0000:03: resource 0 [io  0x6000-0x6fff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488340] pci_bus 0000:03: resource 1 [mem 0xe3100000-0xe3afffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488341] pci_bus 0000:03: resource 2 [mem 0xe1100000-0xe1afffff 64bit pref]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488343] pci_bus 0000:09: resource 1 [mem 0xe3b00000-0xe3bfffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488345] pci_bus 0000:0a: resource 0 [io  0x2000-0x5fff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488347] pci_bus 0000:0a: resource 1 [mem 0xe2000000-0xe30fffff]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488349] pci_bus 0000:0a: resource 2 [mem 0xe0000000-0xe10fffff 64bit pref]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488373] NET: Registered protocol family 2
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.488496] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.489298] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.490509] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.490660] TCP: Hash tables configured (established 524288 bind 65536)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.490662] TCP reno registered
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.490670] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.490688] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.490784] NET: Registered protocol family 1
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.490795] pci 0000:00:02.0: Boot video device
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.490896] PCI: CLS 64 bytes, default 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.490900] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.490902] Placing 64MB software IO TLB between ffff8800c6a85000 - ffff8800caa85000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.490904] software IO TLB at phys 0xc6a85000 - 0xcaa85000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.490918] Simple Boot Flag at 0xf3 set to 0x1
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.491274] audit: initializing netlink socket (disabled)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.491280] type=2000 audit(1324119964.332:1): initialized
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.512939] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.521759] VFS: Disk quotas dquot_6.5.2
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.521806] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.522241] fuse init (API version 7.16)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.522307] msgmni has been set to 7711
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.522614] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.522639] io scheduler noop registered
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.522641] io scheduler deadline registered
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.522669] io scheduler cfq registered (default)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.522957] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.522973] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.523001] intel_idle: MWAIT substates: 0x21120
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.523003] intel_idle: v0.4 model 0x2A
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.523004] intel_idle: lapic_timer_reliable_states 0xffffffff
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.523350] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.523635] ACPI: AC Adapter [AC] (off-line)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.523770] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.524303] ACPI: Lid Switch [LID]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.524360] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.524364] ACPI: Power Button [PBTN]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.524523] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.524526] ACPI: Sleep Button [SBTN]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.524554] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.524557] ACPI: Power Button [PWRF]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.524576] ACPI: acpi_idle yielding to intel_idle
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.694372] thermal LNXTHERM:00: registered as thermal_zone0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.694374] ACPI: Thermal Zone [THM] (25 C)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.694392] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.694402] ERST: Table is not found!
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.694441] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.703964] ACPI: Battery Slot [BAT0] (battery present)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.762453] Linux agpgart interface v0.103
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.762516] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.762640] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.763732] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.763822] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.764564] brd: module loaded
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.764903] loop: module loaded
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.765178] Fixed MDIO Bus: probed
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.765193] PPP generic driver version 2.4.2
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.765218] tun: Universal TUN/TAP device driver, 1.6
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.765219] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.765268] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.765283] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.765300] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.765304] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.765325] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.765348] ehci_hcd 0000:00:1a.0: debug port 2
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.769243] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.769258] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xe3d50000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.782173] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.782299] hub 1-0:1.0: USB hub found
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.782302] hub 1-0:1.0: 2 ports detected
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.782347] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.782358] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.782362] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.782388] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.782408] ehci_hcd 0000:00:1d.0: debug port 2
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.786279] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.786290] ehci_hcd 0000:00:1d.0: irq 17, io mem 0xe3d30000
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.802197] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.802284] hub 2-0:1.0: USB hub found
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.802287] hub 2-0:1.0: 2 ports detected
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.802326] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.802333] uhci_hcd: USB Universal Host Controller Interface driver
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.802375] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.802575] i8042: Warning: Keylock active
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.803752] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.803757] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.803827] mousedev: PS/2 mouse device common for all mice
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.803933] rtc_cmos 00:06: RTC can wake from S4
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.804027] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.804052] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.804124] device-mapper: uevent: version 1.0.3
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.804173] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.804282] cpuidle: using governor ladder
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.804424] cpuidle: using governor menu
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.804426] EFI Variables Facility v0.08 2004-May-17
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.804586] TCP cubic registered
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.804696] NET: Registered protocol family 10
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.804798] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.805149] NET: Registered protocol family 17
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.805158] Registering the dns_resolver key type
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.805221] PM: Hibernation image not present or could not be loaded.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.805232] registered taskstats version 1
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.815012]   Magic number: 7:544:125
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.815051] acpi device:00: hash matches
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.815101] rtc_cmos 00:06: setting system clock to 2011-12-17 11:06:05 UTC (1324119965)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.815755] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.815757] EDD information not available.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.817028] Freeing unused kernel memory: 984k freed
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.817136] Write protecting the kernel read-only data: 10240k
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.817335] Freeing unused kernel memory: 16k freed
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.820735] Freeing unused kernel memory: 1396k freed
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.853148] firewire_ohci 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.853159] firewire_ohci 0000:09:00.0: setting latency timer to 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.854256] ahci 0000:00:1f.2: version 3.0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.854272] ahci 0000:00:1f.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.854337] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.854369] ahci: SSS flag set, parallel bus scan disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.864817] sdhci: Secure Digital Host Controller Interface driver
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.864821] sdhci: Copyright(c) Pierre Ossman
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.866284] tg3.c:v3.119 (May 18, 2011)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.866302] tg3 0000:0a:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.866314] tg3 0000:0a:00.0: setting latency timer to 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.870166] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3b impl SATA mode
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.870171] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.870178] ahci 0000:00:1f.2: setting latency timer to 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.902639] scsi0 : ahci
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.902748] scsi1 : ahci
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.902783] tg3 0000:0a:00.0: eth0: Tigon3 [partno(BCM95761) rev 5761100] (PCI Express) MAC address d0:67:e5:32:66:73
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.902787] tg3 0000:0a:00.0: eth0: attached PHY is 5761 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.902790] tg3 0000:0a:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.902792] tg3 0000:0a:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.902832] scsi2 : ahci
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.902907] scsi3 : ahci
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.902990] scsi4 : ahci
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.903069] scsi5 : ahci
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.903469] ata1: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20100 irq 42
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.903473] ata2: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20180 irq 42
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.903476] ata3: DUMMY
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.903479] ata4: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20280 irq 42
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.903483] ata5: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20300 irq 42
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.903488] ata6: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20380 irq 42
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.906135] firewire_ohci: Register access failure - please notify linux1394-devel@lists.sf.net
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.906181] firewire_ohci: Added fw-ohci device 0000:09:00.0, OHCI v1.10, 8 IR + 8 IT contexts, quirks 0x10
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.906225] sdhci-pci 0000:09:00.1: SDHCI controller found [1217:8321] (rev 5)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.906248] sdhci-pci 0000:09:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.906335] sdhci-pci 0000:09:00.1: Invalid iomem size. You may experience problems.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.906400] sdhci-pci 0000:09:00.1: setting latency timer to 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.906418] mmc0: no vmmc regulator found
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.906443] Registered led device: mmc0::
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    1.906474] mmc0: SDHCI controller on PCI [0000:09:00.1] using DMA
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.093866] usb 1-1: new high speed USB device number 2 using ehci_hcd
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.221698] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.226523] hub 1-1:1.0: USB hub found
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.226594] hub 1-1:1.0: 6 ports detected
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.337548] usb 2-1: new high speed USB device number 2 using ehci_hcd
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.405529] firewire_core: created device fw0: GUID 07364ec1324fc000, S400
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.413269] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.423030] ata1.00: ATA-8: ST9500423AS, 0001DEM1, max UDMA/133
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.423034] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.470098] hub 2-1:1.0: USB hub found
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.470151] hub 2-1:1.0: 6 ports detected
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.489343] Refined TSC clocksource calibration: 2494.333 MHz.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.489348] Switching to clocksource tsc
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.541520] usb 1-1.4: new high speed USB device number 3 using ehci_hcd
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.701511] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.701837] ata1.00: configured for UDMA/133
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.701980] scsi 0:0:0:0: Direct-Access     ATA      ST9500423AS      0001 PQ: 0 ANSI: 5
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.702086] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.702089] sd 0:0:0:0: [sda] 4096-byte physical blocks
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.702129] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.702134] sd 0:0:0:0: [sda] Write Protect is off
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.702137] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.702159] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.770764]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    2.771107] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    3.020570] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    3.033483] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L633J, D500, max UDMA/100
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    3.048569] ata2.00: configured for UDMA/100
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    3.056627] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L633J D500 PQ: 0 ANSI: 5
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    3.066332] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    3.066336] cdrom: Uniform CD-ROM driver Revision: 3.20
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    3.066462] sr 1:0:0:0: Attached scsi CD-ROM sr0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    3.066520] sr 1:0:0:0: Attached scsi generic sg1 type 5
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    3.088826] usb 2-1.6: new full speed USB device number 3 using ehci_hcd
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    3.384195] ata4: SATA link down (SStatus 0 SControl 300)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    3.703782] ata5: SATA link down (SStatus 0 SControl 300)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    4.023368] ata6: SATA link down (SStatus 0 SControl 300)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    4.983662] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    7.159594] Adding 4085756k swap on /dev/sda7.  Priority:-1 extents:1 across:4085756k 
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    8.546334] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    8.637094] lp: driver loaded but no devices found
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    8.789271] wmi: Mapper loaded
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    8.981687] mei: module is from the staging directory, the quality is unknown, you have been warned.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    8.981905] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    8.981911] mei 0000:00:16.0: setting latency timer to 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.009195] cfg80211: Calling CRDA to update world regulatory domain
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.025453] parport_pc 00:08: [io  0x0378-0x037b]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.025469] parport_pc 00:08: [io  0x0278-0x027b]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.025479] parport_pc 00:08: [io  0x03bc-0x03bf]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.025488] parport_pc 00:08: [io  0x0378-0x037b]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.025553] parport_pc 00:08: [irq 7]
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.092185] alps.c: E6 report: 00 00 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.097926] parport_pc 00:08: activated
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.097930] parport_pc 00:08: reported by Plug and Play ACPI
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.098006] parport_pc 00:08: disabled
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.104375] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.119321] alps.c: E7 report: 73 02 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.119663] input: Dell WMI hotkeys as /devices/virtual/input/input5
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.193451] [drm] Initialized drm 1.1.0 20060810
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.446580] Bluetooth: Core ver 2.16
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.446600] NET: Registered protocol family 31
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.446601] Bluetooth: HCI device and connection manager initialized
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.446604] Bluetooth: HCI socket layer initialized
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.446605] Bluetooth: L2CAP socket layer initialized
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.446663] Bluetooth: SCO socket layer initialized
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.563738] alps.c: E6 report: 00 00 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.583634] alps.c: E7 report: 73 02 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.610574] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.610578] i915 0000:00:02.0: setting latency timer to 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.660941] i915 0000:00:02.0: irq 43 for MSI/MSI-X
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.660945] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.660946] [drm] Driver supports precise vblank timestamp query.
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.660970] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.664080] Bluetooth: Generic Bluetooth USB driver ver 0.6
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.664447] usbcore: registered new interface driver btusb
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.667672] ppdev: user-space parallel port driver
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.677940] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.677943] iwlagn: Copyright(c) 2003-2011 Intel Corporation
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.677992] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.678000] iwlagn 0000:02:00.0: setting latency timer to 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.678029] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.694292] iwlagn 0000:02:00.0: device EEPROM VER=0x715, CALIB=0x6
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.694294] iwlagn 0000:02:00.0: Device SKU: 0Xb
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.694296] iwlagn 0000:02:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.694374] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.694460] iwlagn 0000:02:00.0: irq 44 for MSI/MSI-X
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.840080] iwlagn 0000:02:00.0: loaded firmware version 17.168.5.3 build 42301
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.840218] Registered led device: phy0-led
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.840241] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.901048] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.964047] fbcon: inteldrmfb (fb0) is primary device
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.964131] Console: switching to colour frame buffer device 200x56
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.964160] fb0: inteldrmfb frame buffer device
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.964161] drm: registered panic notifier
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [    9.989366] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input6
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.002069] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input7
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.133246] type=1400 audit(1324112773.824:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=757 comm="apparmor_parser"
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.133256] type=1400 audit(1324112773.824:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=660 comm="apparmor_parser"
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.133263] type=1400 audit(1324112773.824:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=718 comm="apparmor_parser"
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.133505] type=1400 audit(1324112773.824:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=757 comm="apparmor_parser"
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.133570] type=1400 audit(1324112773.824:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=660 comm="apparmor_parser"
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.133577] type=1400 audit(1324112773.824:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=718 comm="apparmor_parser"
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.133667] type=1400 audit(1324112773.824:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=757 comm="apparmor_parser"
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.133771] type=1400 audit(1324112773.824:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=660 comm="apparmor_parser"
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.133777] type=1400 audit(1324112773.824:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=718 comm="apparmor_parser"
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.363665] acpi device:36: registered as cooling_device4
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.399624] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.399676] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.423118] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.938688] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.938738] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   10.938756] HDA Intel 0000:00:1b.0: setting latency timer to 64
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.126425] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.126429] cfg80211: World regulatory domain updated:
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.126431] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.126434] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.126436] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.126438] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.126440] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.126443] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.532968] Linux video capture interface: v2.00
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.544176] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_FHD (1bcf:280b)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.565994] input: Laptop_Integrated_Webcam_FHD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input9
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.566094] usbcore: registered new interface driver uvcvideo
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.566096] USB Video Class driver (v1.1.0)
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.614484] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.614610] HDMI status: Pin=6 Presence_Detect=0 ELD_Valid=0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.614735] HDMI status: Pin=7 Presence_Detect=0 ELD_Valid=0
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.614970] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.615026] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.615058] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.615095] input: HDA Intel PCH Mic at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.615129] input: HDA Intel PCH Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.615162] input: HDA Intel PCH Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
Dec 17 11:06:19 werecat-Latitude-E5420 kernel: [   11.615193] input: HDA Intel PCH HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
Dec 17 11:06:20 werecat-Latitude-E5420 kernel: [   17.208969] type=1400 audit(1324112780.908:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=987 comm="apparmor_parser"
Dec 17 11:06:20 werecat-Latitude-E5420 kernel: [   17.209236] type=1400 audit(1324112780.908:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=987 comm="apparmor_parser"
Dec 17 11:06:20 werecat-Latitude-E5420 kernel: [   17.209400] type=1400 audit(1324112780.908:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=987 comm="apparmor_parser"
Dec 17 11:06:21 werecat-Latitude-E5420 modem-manager[994]: <info>  ModemManager (version 0.5) starting...
Dec 17 11:06:21 werecat-Latitude-E5420 kernel: [   17.691641] type=1400 audit(1324112781.392:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=986 comm="apparmor_parser"
Dec 17 11:06:21 werecat-Latitude-E5420 kernel: [   17.790924] type=1400 audit(1324112781.492:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=996 comm="apparmor_parser"
Dec 17 11:06:21 werecat-Latitude-E5420 kernel: [   17.791099] type=1400 audit(1324112781.492:16): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" pid=996 comm="apparmor_parser"
Dec 17 11:06:21 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin Samsung
Dec 17 11:06:21 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin Generic
Dec 17 11:06:21 werecat-Latitude-E5420 kernel: [   17.923194] type=1400 audit(1324112781.624:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1003 comm="apparmor_parser"
Dec 17 11:06:21 werecat-Latitude-E5420 kernel: [   17.923203] type=1400 audit(1324112781.624:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=991 comm="apparmor_parser"
Dec 17 11:06:21 werecat-Latitude-E5420 kernel: [   17.923511] type=1400 audit(1324112781.624:19): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1003 comm="apparmor_parser"
Dec 17 11:06:21 werecat-Latitude-E5420 kernel: [   17.923516] type=1400 audit(1324112781.624:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=991 comm="apparmor_parser"
Dec 17 11:06:21 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin Option High-Speed
Dec 17 11:06:21 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin Gobi
Dec 17 11:06:21 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin Huawei
Dec 17 11:06:21 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin Option
Dec 17 11:06:21 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin AnyData
Dec 17 11:06:21 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin Sierra
Dec 17 11:06:22 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin X22X
Dec 17 11:06:22 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin Novatel
Dec 17 11:06:22 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin Wavecom
Dec 17 11:06:22 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin MotoC
Dec 17 11:06:22 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin ZTE
Dec 17 11:06:22 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin SimTech
Dec 17 11:06:22 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin Nokia
Dec 17 11:06:22 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin Longcheer
Dec 17 11:06:22 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin Linktop
Dec 17 11:06:22 werecat-Latitude-E5420 modem-manager[994]: <info>  Loaded plugin Ericsson MBM
Dec 17 11:06:22 werecat-Latitude-E5420 NetworkManager[1011]: <info> NetworkManager (version 0.9.1.90) is starting...
Dec 17 11:06:22 werecat-Latitude-E5420 NetworkManager[1011]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Dec 17 11:06:22 werecat-Latitude-E5420 avahi-daemon[1024]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Dec 17 11:06:22 werecat-Latitude-E5420 avahi-daemon[1024]: Successfully dropped root privileges.
Dec 17 11:06:22 werecat-Latitude-E5420 avahi-daemon[1024]: avahi-daemon 0.6.30 starting up.
Dec 17 11:06:22 werecat-Latitude-E5420 avahi-daemon[1024]: Successfully called chroot().
Dec 17 11:06:22 werecat-Latitude-E5420 avahi-daemon[1024]: Successfully dropped remaining capabilities.
Dec 17 11:06:22 werecat-Latitude-E5420 avahi-daemon[1024]: Loading service file /services/udisks.service.
Dec 17 11:06:22 werecat-Latitude-E5420 avahi-daemon[1024]: Network interface enumeration completed.
Dec 17 11:06:22 werecat-Latitude-E5420 avahi-daemon[1024]: Registering HINFO record with values 'X86_64'/'LINUX'.
Dec 17 11:06:22 werecat-Latitude-E5420 avahi-daemon[1024]: Server startup complete. Host name is werecat-Latitude-E5420.local. Local service cookie is 4262752382.
Dec 17 11:06:22 werecat-Latitude-E5420 avahi-daemon[1024]: Service "werecat-Latitude-E5420" (/services/udisks.service) successfully established.
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Dec 17 11:06:23 werecat-Latitude-E5420 dbus[980]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Dec 17 11:06:23 werecat-Latitude-E5420 udev-configure-printer: add /module/lp
Dec 17 11:06:23 werecat-Latitude-E5420 udev-configure-printer: Failed to get parent
Dec 17 11:06:23 werecat-Latitude-E5420 polkitd[1037]: started daemon version 0.102 using authority implementation `local' version `0.102'
Dec 17 11:06:23 werecat-Latitude-E5420 dbus[980]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    SCPlugin-Ifupdown: init!
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    SCPlugin-Ifupdown: update_system_hostname
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    SCPluginIfupdown: management mode: unmanaged
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.6/0000:0a:00.0/net/eth0, iface: eth0)
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.6/0000:0a:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    SCPlugin-Ifupdown: end _init.
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    Ifupdown: get unmanaged devices count: 0
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    SCPlugin-Ifupdown: (12545840) ... get_connections.
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    SCPlugin-Ifupdown: (12545840) ... get_connections (managed=false): return empty list.
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    keyfile: parsing AUTh startup ... 
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    keyfile:     read connection 'AUTh startup'
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    keyfile: parsing ATLAS-AUTH ... 
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    keyfile:     read connection 'ATLAS-AUTH'
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    keyfile: parsing NetFasteR IAD (PSTN) ... 
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    keyfile:     read connection 'NetFasteR IAD (PSTN)'
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    keyfile: parsing Thomson1153EE ... 
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    keyfile:     read connection 'Thomson1153EE'
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    keyfile: parsing Nuclear-Lab ... 
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    keyfile:     read connection 'Nuclear-Lab'
Dec 17 11:06:23 werecat-Latitude-E5420 NetworkManager[1011]:    keyfile: parsing eduroam ... 
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]:    keyfile:     read connection 'eduroam'
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]:    Ifupdown: get unmanaged devices count: 0
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> modem-manager is now available
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> found WiFi radio killswitch rfkill3 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/ieee80211/phy0/rfkill3) (driver (unknown))
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/dell-laptop/rfkill/rfkill0) (driver dell-laptop)
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> WiFi enabled by radio killswitch; enabled by state file
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> WWAN enabled by radio killswitch; enabled by state file
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> WiMAX enabled by radio killswitch; enabled by state file
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> Networking is enabled by state file
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3)
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): now managed
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): bringing up device.
Dec 17 11:06:24 werecat-Latitude-E5420 cron[1082]: (CRON) INFO (pidfile fd = 3)
Dec 17 11:06:24 werecat-Latitude-E5420 anacron[1111]: Anacron 2.3 started on 2011-12-17
Dec 17 11:06:24 werecat-Latitude-E5420 acpid: starting up with proc fs
Dec 17 11:06:24 werecat-Latitude-E5420 kernel: [   20.841562] init: failsafe main process (931) killed by TERM signal
Dec 17 11:06:24 werecat-Latitude-E5420 cron[1116]: (CRON) STARTUP (fork ok)
Dec 17 11:06:24 werecat-Latitude-E5420 kernel: [   20.913687] init: apport pre-start process (1071) terminated with status 1
Dec 17 11:06:24 werecat-Latitude-E5420 kernel: [   20.915215] init: apport post-stop process (1119) terminated with status 1
Dec 17 11:06:24 werecat-Latitude-E5420 cron[1116]: (CRON) INFO (Running @reboot jobs)
Dec 17 11:06:24 werecat-Latitude-E5420 anacron[1111]: Normal exit (0 jobs run)
Dec 17 11:06:24 werecat-Latitude-E5420 acpid: 32 rules loaded
Dec 17 11:06:24 werecat-Latitude-E5420 acpid: waiting for events: event logging is off
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): preparing device.
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): deactivating device (reason 'managed') [2]
Dec 17 11:06:24 werecat-Latitude-E5420 dbus[980]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> (eth0): carrier is OFF
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> (eth0): new Ethernet device (driver: 'tg3' ifindex: 2)
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> (eth0): now managed
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> (eth0): bringing up device.
Dec 17 11:06:24 werecat-Latitude-E5420 kernel: [   21.163066] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 17 11:06:24 werecat-Latitude-E5420 kernel: [   21.164730] tg3 0000:0a:00.0: irq 46 for MSI/MSI-X
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> (eth0): preparing device.
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> (eth0): deactivating device (reason 'managed') [2]
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.6/0000:0a:00.0/net/eth0
Dec 17 11:06:24 werecat-Latitude-E5420 NetworkManager[1011]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec 17 11:06:24 werecat-Latitude-E5420 kernel: [   21.257295] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 17 11:06:25 werecat-Latitude-E5420 dbus[980]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Dec 17 11:06:25 werecat-Latitude-E5420 NetworkManager[1011]: <info> wpa_supplicant started
Dec 17 11:06:25 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): supplicant interface state: starting -> ready
Dec 17 11:06:25 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Dec 17 11:06:25 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): supplicant interface state: ready -> inactive
Dec 17 11:06:25 werecat-Latitude-E5420 bluetoothd[1164]: Bluetooth daemon 4.96
Dec 17 11:06:25 werecat-Latitude-E5420 bluetoothd[1164]: Starting SDP server
Dec 17 11:06:25 werecat-Latitude-E5420 kernel: [   22.191182] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Dec 17 11:06:25 werecat-Latitude-E5420 kernel: [   22.191185] Bluetooth: BNEP filters: protocol multicast
Dec 17 11:06:25 werecat-Latitude-E5420 bluetoothd[1164]: Listening for HCI events on hci0
Dec 17 11:06:25 werecat-Latitude-E5420 NetworkManager[1011]: <warn> bluez error getting default adapter: No such adapter
Dec 17 11:06:25 werecat-Latitude-E5420 kernel: [   22.286844] Bluetooth: RFCOMM TTY layer initialized
Dec 17 11:06:25 werecat-Latitude-E5420 kernel: [   22.286849] Bluetooth: RFCOMM socket layer initialized
Dec 17 11:06:25 werecat-Latitude-E5420 kernel: [   22.286851] Bluetooth: RFCOMM ver 1.11
Dec 17 11:06:26 werecat-Latitude-E5420 bluetoothd[1164]: HCI dev 0 up
Dec 17 11:06:26 werecat-Latitude-E5420 acpid: client connected from 1127[0:0]
Dec 17 11:06:26 werecat-Latitude-E5420 acpid: 1 client rule loaded
Dec 17 11:06:26 werecat-Latitude-E5420 bluetoothd[1164]: Adapter /org/bluez/1164/hci0 has been enabled
Dec 17 11:06:26 werecat-Latitude-E5420 kernel: [   23.098181] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
Dec 17 11:06:27 werecat-Latitude-E5420 kernel: [   24.280838] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=600
Dec 17 11:06:28 werecat-Latitude-E5420 dbus[980]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Dec 17 11:06:28 werecat-Latitude-E5420 dbus[980]: [system] Successfully activated service 'org.freedesktop.Accounts'
Dec 17 11:06:28 werecat-Latitude-E5420 accounts-daemon[1307]: started daemon version 0.6.14
Dec 17 11:06:29 werecat-Latitude-E5420 dbus[980]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Dec 17 11:06:29 werecat-Latitude-E5420 dbus[980]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Auto-activating connection 'eduroam'.
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) starting connection 'eduroam'
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0/wireless): connection 'eduroam' has security, and secrets exist.  No new secrets needed.
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Config: added 'ssid' value 'eduroam'
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Config: added 'scan_ssid' value '1'
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Config: added 'key_mgmt' value 'WPA-EAP'
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Config: added 'password' value '<omitted>'
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Config: added 'eap' value 'PEAP'
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Config: added 'fragment_size' value '1300'
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Config: added 'phase2' value 'auth=MSCHAPV2'
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Config: added 'ca_cert' value '/home/werecat/Documents/RootCA.der'
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Config: added 'identity' value 'nsantori@auth.gr'
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Config: added 'bgscan' value 'simple:30:-45:300'
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> Config: set interface ap_scan to 1
Dec 17 11:06:29 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): supplicant interface state: inactive -> scanning
Dec 17 11:06:32 werecat-Latitude-E5420 dbus[980]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Dec 17 11:06:32 werecat-Latitude-E5420 dbus[980]: [system] Successfully activated service 'org.freedesktop.UPower'
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: Trying to authenticate with 00:18:73:31:b2:61 (SSID='eduroam' freq=2437 MHz)
Dec 17 11:06:32 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: Trying to associate with 00:18:73:31:b2:61 (SSID='eduroam' freq=2437 MHz)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.951891] wlan0: authenticate with 00:18:73:31:b2:61 (try 1)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.953695] wlan0: authenticated
Dec 17 11:06:32 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): supplicant interface state: authenticating -> associating
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.990485] wlan0: associate with 00:18:73:31:b2:61 (try 1)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.993824] wlan0: RX AssocResp from 00:18:73:31:b2:61 (capab=0x411 status=0 aid=15)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.993832] wlan0: associated
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: Associated with 00:18:73:31:b2:61
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.996388] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.996444] cfg80211: Calling CRDA for country: GR
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998435] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998438] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998440] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998442] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998443] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998445] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998446] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998448] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998449] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998451] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998452] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998454] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998455] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998457] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998458] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998460] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998461] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998463] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998464] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998466] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998467] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998469] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998470] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998472] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998473] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998475] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998476] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998478] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998479] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998481] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998482] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998484] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998485] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998487] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998488] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998490] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998491] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998493] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998494] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998496] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998497] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998499] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (N/A mBi, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998500] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998502] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998503] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998505] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998506] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998508] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998509] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998511] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998512] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998513] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998515] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998516] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998518] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998519] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998521] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998522] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998524] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998525] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998527] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998528] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998530] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998531] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998533] cfg80211: Disabling freq 5745 MHz
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998534] cfg80211: Disabling freq 5765 MHz
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998535] cfg80211: Disabling freq 5785 MHz
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998536] cfg80211: Disabling freq 5805 MHz
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998537] cfg80211: Disabling freq 5825 MHz
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998539] cfg80211: Regulatory domain changed to country: GR
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998540] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998542] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998543] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998545] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 kernel: [   28.998546] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: CTRL-EVENT-EAP-STARTED EAP authentication started
Dec 17 11:06:32 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): supplicant interface state: associating -> associated
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=13 -> NAK
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: OpenSSL: tls_connection_ca_cert - Failed to load root certificates error:00000000:lib(0):func(0):reason(0)
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: CTRL-EVENT-EAP-PEER-CERT depth=3 subject='/C=GR/O=Hellenic Academic and Research Institutions Cert. Authority/CN=Hellenic Academic and Research Institutions RootCA 2006'
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: CTRL-EVENT-EAP-PEER-CERT depth=2 subject='/C=GR/O=Aristotle University of Thessaloniki/CN=Aristotle University of Thessaloniki Central CA R2/emailAddress=pkiadmin@ccf.auth.gr'
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: CTRL-EVENT-EAP-PEER-CERT depth=1 subject='/C=GR/O=Aristotle University of Thessaloniki/OU=Central Communication Facilities/CN=AUTH Network Operations Center Certification Authority R3/emailAddress=pkiadmin@ccf.auth.gr'
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: CTRL-EVENT-EAP-PEER-CERT depth=0 subject='/C=GR/O=Aristotle University of Thessaloniki/OU=Network Operations Center/CN=radius.auth.gr'
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: EAP-MSCHAPV2: Authentication succeeded
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: EAP-TLV: TLV Result - Success - EAP-TLV/Phase2 Completed
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: WPA: Key negotiation completed with 00:18:73:31:b2:61 [PTK=CCMP GTK=TKIP]
Dec 17 11:06:32 werecat-Latitude-E5420 wpa_supplicant[1130]: CTRL-EVENT-CONNECTED - Connection to 00:18:73:31:b2:61 completed (auth) [id=0 id_str=]
Dec 17 11:06:32 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): supplicant interface state: associated -> completed
Dec 17 11:06:32 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'eduroam'.
Dec 17 11:06:32 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 17 11:06:32 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Dec 17 11:06:32 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 17 11:06:32 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 17 11:06:33 werecat-Latitude-E5420 NetworkManager[1011]: <info> dhclient started with pid 1424
Dec 17 11:06:33 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Beginning IP6 addrconf.
Dec 17 11:06:33 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Dec 17 11:06:33 werecat-Latitude-E5420 dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Dec 17 11:06:33 werecat-Latitude-E5420 dhclient: Copyright 2004-2010 Internet Systems Consortium.
Dec 17 11:06:33 werecat-Latitude-E5420 dhclient: All rights reserved.
Dec 17 11:06:33 werecat-Latitude-E5420 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Dec 17 11:06:33 werecat-Latitude-E5420 dhclient: 
Dec 17 11:06:33 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Dec 17 11:06:33 werecat-Latitude-E5420 dhclient: Listening on LPF/wlan0/a0:88:b4:a1:01:6c
Dec 17 11:06:33 werecat-Latitude-E5420 dhclient: Sending on   LPF/wlan0/a0:88:b4:a1:01:6c
Dec 17 11:06:33 werecat-Latitude-E5420 dhclient: Sending on   Socket/fallback
Dec 17 11:06:33 werecat-Latitude-E5420 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Dec 17 11:06:34 werecat-Latitude-E5420 dhclient: DHCPOFFER of 155.207.102.127 from 155.207.102.101
Dec 17 11:06:34 werecat-Latitude-E5420 dhclient: DHCPREQUEST of 155.207.102.127 on wlan0 to 255.255.255.255 port 67
Dec 17 11:06:34 werecat-Latitude-E5420 dhclient: DHCPACK of 155.207.102.127 from 155.207.102.102
Dec 17 11:06:34 werecat-Latitude-E5420 dhclient: bound to 155.207.102.127 -- renewal in 347 seconds.
Dec 17 11:06:34 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Dec 17 11:06:34 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec 17 11:06:34 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Dec 17 11:06:34 werecat-Latitude-E5420 NetworkManager[1011]: <info>   address 155.207.102.127
Dec 17 11:06:34 werecat-Latitude-E5420 NetworkManager[1011]: <info>   prefix 24 (255.255.255.0)
Dec 17 11:06:34 werecat-Latitude-E5420 NetworkManager[1011]: <info>   gateway 155.207.102.100
Dec 17 11:06:34 werecat-Latitude-E5420 NetworkManager[1011]: <info>   nameserver '155.207.0.31'
Dec 17 11:06:34 werecat-Latitude-E5420 NetworkManager[1011]: <info>   nameserver '155.207.0.32'
Dec 17 11:06:34 werecat-Latitude-E5420 NetworkManager[1011]: <info>   domain name 'pubaccess.auth.gr'
Dec 17 11:06:34 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Dec 17 11:06:34 werecat-Latitude-E5420 avahi-daemon[1024]: Joining mDNS multicast group on interface wlan0.IPv4 with address 155.207.102.127.
Dec 17 11:06:34 werecat-Latitude-E5420 avahi-daemon[1024]: New relevant interface wlan0.IPv4 for mDNS.
Dec 17 11:06:34 werecat-Latitude-E5420 avahi-daemon[1024]: Registering new address record for 155.207.102.127 on wlan0.IPv4.
Dec 17 11:06:34 werecat-Latitude-E5420 avahi-daemon[1024]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::a288:b4ff:fea1:16c.
Dec 17 11:06:34 werecat-Latitude-E5420 avahi-daemon[1024]: New relevant interface wlan0.IPv6 for mDNS.
Dec 17 11:06:34 werecat-Latitude-E5420 avahi-daemon[1024]: Registering new address record for fe80::a288:b4ff:fea1:16c on wlan0.*.
Dec 17 11:06:35 werecat-Latitude-E5420 NetworkManager[1011]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Dec 17 11:06:35 werecat-Latitude-E5420 NetworkManager[1011]: <info> Policy set 'eduroam' (wlan0) as default for IPv4 routing and DNS.
Dec 17 11:06:35 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) successful, device activated.
Dec 17 11:06:35 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Dec 17 11:06:35 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec 17 11:06:35 werecat-Latitude-E5420 dbus[980]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec 17 11:06:35 werecat-Latitude-E5420 dbus[980]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 17 11:06:36 werecat-Latitude-E5420 dbus[980]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Dec 17 11:06:36 werecat-Latitude-E5420 avahi-daemon[1024]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::a288:b4ff:fea1:16c.
Dec 17 11:06:36 werecat-Latitude-E5420 avahi-daemon[1024]: Joining mDNS multicast group on interface wlan0.IPv6 with address 2001:648:2800:102:a288:b4ff:fea1:16c.
Dec 17 11:06:36 werecat-Latitude-E5420 avahi-daemon[1024]: Registering new address record for 2001:648:2800:102:a288:b4ff:fea1:16c on wlan0.*.
Dec 17 11:06:36 werecat-Latitude-E5420 avahi-daemon[1024]: Withdrawing address record for fe80::a288:b4ff:fea1:16c on wlan0.
Dec 17 11:06:36 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Dec 17 11:06:36 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Dec 17 11:06:36 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Dec 17 11:06:37 werecat-Latitude-E5420 dbus[980]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Dec 17 11:06:37 werecat-Latitude-E5420 NetworkManager[1011]: <info> Policy set 'eduroam' (wlan0) as default for IPv4 routing and DNS.
Dec 17 11:06:37 werecat-Latitude-E5420 NetworkManager[1011]: <warn> Failed to add route Object exists
Dec 17 11:06:37 werecat-Latitude-E5420 NetworkManager[1011]: <info> Policy set 'eduroam' (wlan0) as default for IPv6 routing and DNS.
Dec 17 11:06:37 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Dec 17 11:06:37 werecat-Latitude-E5420 NetworkManager[1011]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Dec 17 11:06:37 werecat-Latitude-E5420 dbus[980]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Dec 17 09:06:37 werecat-Latitude-E5420 rtkit-daemon[1546]: Successfully called chroot.
Dec 17 09:06:37 werecat-Latitude-E5420 rtkit-daemon[1546]: Successfully dropped privileges.
Dec 17 09:06:37 werecat-Latitude-E5420 rtkit-daemon[1546]: Successfully limited resources.
Dec 17 09:06:37 werecat-Latitude-E5420 rtkit-daemon[1546]: Running.
Dec 17 09:06:37 werecat-Latitude-E5420 rtkit-daemon[1546]: Canary thread running.
Dec 17 09:06:37 werecat-Latitude-E5420 rtkit-daemon[1546]: Watchdog thread running.
Dec 17 09:06:37 werecat-Latitude-E5420 rtkit-daemon[1546]: Successfully made thread 1544 of process 1544 (n/a) owned by '104' high priority at nice level -11.
Dec 17 09:06:37 werecat-Latitude-E5420 rtkit-daemon[1546]: Supervising 1 threads of 1 processes of 1 users.
Dec 17 11:06:37 werecat-Latitude-E5420 dbus[980]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Dec 17 09:06:39 werecat-Latitude-E5420 rtkit-daemon[1546]: Successfully made thread 1573 of process 1544 (n/a) owned by '104' RT at priority 5.
Dec 17 09:06:39 werecat-Latitude-E5420 rtkit-daemon[1546]: Supervising 2 threads of 1 processes of 1 users.
Dec 17 09:06:39 werecat-Latitude-E5420 rtkit-daemon[1546]: Successfully made thread 1574 of process 1544 (n/a) owned by '104' RT at priority 5.
Dec 17 09:06:39 werecat-Latitude-E5420 rtkit-daemon[1546]: Supervising 3 threads of 1 processes of 1 users.
Dec 17 11:06:39 werecat-Latitude-E5420 kernel: [   35.751137] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=600
Dec 17 11:06:39 werecat-Latitude-E5420 pulseaudio[1544]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Dec 17 11:06:47  pulseaudio[1544]: last message repeated 2 times
Dec 17 11:06:47 werecat-Latitude-E5420 ntpdate[1572]: adjust time server 91.189.94.4 offset -0.250398 sec
Dec 17 11:06:48 werecat-Latitude-E5420 kernel: [   44.779324] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
Dec 17 09:06:56 werecat-Latitude-E5420 rtkit-daemon[1546]: Successfully made thread 1707 of process 1707 (n/a) owned by '1000' high priority at nice level -11.
Dec 17 09:06:56 werecat-Latitude-E5420 rtkit-daemon[1546]: Supervising 4 threads of 2 processes of 2 users.
Dec 17 11:06:57 werecat-Latitude-E5420 gnome-session[1617]: WARNING: Unable to parse command from  'file:///etc/xdg/autostart/synaptiks_init_config.desktop': Key file contains key 'Terminal' which has value that cannot be interpreted.
Dec 17 11:06:57 werecat-Latitude-E5420 gnome-session[1617]: WARNING: Failed to start app: Unable to start application: Key file contains key 'Terminal' which has value that cannot be interpreted.
Dec 17 11:06:57 werecat-Latitude-E5420 gnome-session[1617]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "/usr/bin/touchpad-indicator" (No such file or directory)
Dec 17 11:06:57 werecat-Latitude-E5420 gnome-session[1617]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "docky" (No such file or directory)
Dec 17 09:06:58 werecat-Latitude-E5420 rtkit-daemon[1546]: Successfully made thread 1730 of process 1707 (n/a) owned by '1000' RT at priority 5.
Dec 17 09:06:58 werecat-Latitude-E5420 rtkit-daemon[1546]: Supervising 5 threads of 2 processes of 2 users.
Dec 17 09:06:58 werecat-Latitude-E5420 rtkit-daemon[1546]: Successfully made thread 1731 of process 1707 (n/a) owned by '1000' RT at priority 5.
Dec 17 09:06:58 werecat-Latitude-E5420 rtkit-daemon[1546]: Supervising 6 threads of 2 processes of 2 users.
Dec 17 11:06:58 werecat-Latitude-E5420 pulseaudio[1707]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Dec 17 11:06:58  pulseaudio[1707]: last message repeated 2 times
Dec 17 11:06:58 werecat-Latitude-E5420 dbus[980]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Dec 17 11:06:59 werecat-Latitude-E5420 dbus[980]: [system] Successfully activated service 'org.freedesktop.UDisks'
Dec 17 11:08:06 werecat-Latitude-E5420 dbus[980]: [system] Activating service name='org.debian.apt' (using servicehelper)
Dec 17 11:08:06 werecat-Latitude-E5420 AptDaemon: INFO: Initializing daemon
Dec 17 11:08:06 werecat-Latitude-E5420 dbus[980]: [system] Successfully activated service 'org.debian.apt'
Dec 17 11:08:06 werecat-Latitude-E5420 AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Dec 17 11:08:06 werecat-Latitude-E5420 AptDaemon.Trans: INFO: Simulate was called
Dec 17 11:08:06 werecat-Latitude-E5420 AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/3a13a8f3a5164a4ba29438b6aee5f078
Dec 17 11:08:09 werecat-Latitude-E5420 AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Dec 17 11:09:59 werecat-Latitude-E5420 pulseaudio[2258]: [pulseaudio] main.c: User-configured server at {d1c33a1fbe08cae2647e4d350000000a}unix:/home/werecat/.pulse/d1c33a1fbe08cae2647e4d350000000a-runtime/native, which appears to be local. Probing deeper.
Dec 17 09:09:59 werecat-Latitude-E5420 rtkit-daemon[1546]: Successfully made thread 2261 of process 2261 (n/a) owned by '1000' high priority at nice level -11.
Dec 17 09:09:59 werecat-Latitude-E5420 rtkit-daemon[1546]: Supervising 1 threads of 1 processes of 1 users.
Dec 17 11:09:59 werecat-Latitude-E5420 pulseaudio[2261]: [pulseaudio] pid.c: Stale PID file, overwriting.
Dec 17 11:09:59 werecat-Latitude-E5420 pulseaudio[2261]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Dec 17 11:10:01  pulseaudio[2261]: last message repeated 2 times
Dec 17 09:10:01 werecat-Latitude-E5420 rtkit-daemon[1546]: Successfully made thread 2267 of process 2261 (n/a) owned by '1000' RT at priority 5.
Dec 17 09:10:01 werecat-Latitude-E5420 rtkit-daemon[1546]: Supervising 2 threads of 1 processes of 1 users.
Dec 17 09:10:01 werecat-Latitude-E5420 rtkit-daemon[1546]: Successfully made thread 2268 of process 2261 (n/a) owned by '1000' RT at priority 5.
Dec 17 09:10:01 werecat-Latitude-E5420 rtkit-daemon[1546]: Supervising 3 threads of 1 processes of 1 users.

```

---

### Post by supercheetah on 2011-12-17
There doesn't seem to be anything untoward in your syslog.

I'll need you to post the output of ~/.xsession, but you need to do it without logging into your desktop, but rather from a terminal, so first switch to a virtual terminal when at the log in screen (this is after you've been automatically logged out) by pressing *Ctrl+F1*, and then logging in at the prompt for your user name.

Once you've logged in, do the following at the command line that it gives you:

```

cp .xsession xsession_log
exit

```

And once you're done with that, switch back to the graphical log in by pressing *Ctrl+F7*; log in, and post the results here, again in the code mark up.

---

### Post by zeroseven0183 on 2012-01-07
Does this have something to do with this [LightDM bug]("https://bugs.launchpad.net/lightdm/+bug/892485")? Although the main report is that the session crashes to login screen when autologin is enabled and Enter key is pressed.

---

### Post by upuldi on 2012-02-02
Hi

This is what i got from the xsession errors log file. Please have a look and let me know what to do to prevent automatically log off.

```

Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/udoluweera/.profile
Loading resource: /etc/X11/Xresources/x11-common
Loading X session script /etc/X11/Xsession.d/20x11-common_process-args
Loading X session script /etc/X11/Xsession.d/30x11-common_xresources
Loading X session script /etc/X11/Xsession.d/40x11-common_xsessionrc
Loading X session script /etc/X11/Xsession.d/50_check_unity_support
Loading X session script /etc/X11/Xsession.d/50x11-common_determine-startup
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/55gnome-session_gnomerc
Loading X session script /etc/X11/Xsession.d/60x11-common_localhost
Loading X session script /etc/X11/Xsession.d/60x11-common_xdg_path
Loading X session script /etc/X11/Xsession.d/60xdg-user-dirs-update
Loading X session script /etc/X11/Xsession.d/65compiz_profile-on-session
Loading X session script /etc/X11/Xsession.d/70gconfd_path-on-session
Loading X session script /etc/X11/Xsession.d/75dbus_dbus-launch
Loading X session script /etc/X11/Xsession.d/80appmenu
Loading X session script /etc/X11/Xsession.d/80appmenu-gtk3
Loading X session script /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90qt-a11y
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
GNOME_KEYRING_CONTROL=/tmp/keyring-VTXDCd
GNOME_KEYRING_CONTROL=/tmp/keyring-VTXDCd
GPG_AGENT_INFO=/tmp/keyring-VTXDCd/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-VTXDCd
GPG_AGENT_INFO=/tmp/keyring-VTXDCd/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-VTXDCd
GPG_AGENT_INFO=/tmp/keyring-VTXDCd/gpg:0:1
SSH_AUTH_SOCK=/tmp/keyring-VTXDCd/ssh
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done

(polkit-gnome-authentication-agent-1:3705): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(polkit-gnome-authentication-agent-1:3705): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(polkit-gnome-authentication-agent-1:3705): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(polkit-gnome-authentication-agent-1:3705): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Initializing bailer options...done
Initializing detection options...done

(canberra-gtk-play:3715): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(canberra-gtk-play:3715): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(canberra-gtk-play:3715): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(canberra-gtk-play:3715): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Initializing composite options...done
** (gnome-fallback-mount-helper:3708): DEBUG: Starting automounting manager
Initializing nautilus-gdu extension
Initializing opengl options...done
** (nautilus:3706): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-open-terminal extension
Initializing decor options...done
Initializing vpswitch options...done
Initializing animation options...done
Starting Dropbox...Initializing resize options...done
Initializing workarounds options...done
(bluetooth-applet:3709): Bluetooth-DEBUG: adding killswitch idx 1 state KILLSWITCH_STATE_SOFT_BLOCKED
(bluetooth-applet:3709): Bluetooth-DEBUG: adding killswitch idx 3 state KILLSWITCH_STATE_HARD_BLOCKED
(bluetooth-applet:3709): Bluetooth-DEBUG: killswitch 1 is KILLSWITCH_STATE_SOFT_BLOCKED
(bluetooth-applet:3709): Bluetooth-DEBUG: killswitch 3 is KILLSWITCH_STATE_HARD_BLOCKED
(bluetooth-applet:3709): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_HARD_BLOCKED
Initializing gnomecompat options...done
(bluetooth-applet:3709): Bluetooth-DEBUG: killswitch 1 is KILLSWITCH_STATE_SOFT_BLOCKED
(bluetooth-applet:3709): Bluetooth-DEBUG: killswitch 3 is KILLSWITCH_STATE_HARD_BLOCKED
(bluetooth-applet:3709): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_HARD_BLOCKED
(bluetooth-applet:3709): Bluetooth-DEBUG: killswitch 1 is KILLSWITCH_STATE_SOFT_BLOCKED
(bluetooth-applet:3709): Bluetooth-DEBUG: killswitch 3 is KILLSWITCH_STATE_HARD_BLOCKED
(bluetooth-applet:3709): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_HARD_BLOCKED
(bluetooth-applet:3709): Bluetooth-DEBUG: killswitch 1 is KILLSWITCH_STATE_SOFT_BLOCKED
(bluetooth-applet:3709): Bluetooth-DEBUG: killswitch 3 is KILLSWITCH_STATE_HARD_BLOCKED
(bluetooth-applet:3709): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_HARD_BLOCKED
Initializing snap options...done
Initializing move options...done
(bluetooth-applet:3709): Bluetooth-DEBUG: killswitch 1 is KILLSWITCH_STATE_SOFT_BLOCKED
(bluetooth-applet:3709): Bluetooth-DEBUG: killswitch 3 is KILLSWITCH_STATE_HARD_BLOCKED
(bluetooth-applet:3709): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_HARD_BLOCKED
Initializing place options...done
Initializing grid options...done
** (gnome-fallback-mount-helper:3708): DEBUG: Found ConsoleKit session at path /org/freedesktop/ConsoleKit/Session4
** (gnome-fallback-mount-helper:3708): DEBUG: ScreenSaver name appeared
Initializing mousepoll options...done
** (gnome-fallback-mount-helper:3708): DEBUG: ConsoleKit session is active 1
** (gnome-fallback-mount-helper:3708): DEBUG: ScreenSaver proxy ready
** (gnome-fallback-mount-helper:3708): DEBUG: Screensaver GetActive() returned 0
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing unitymtgrabhandles options...done
I/O warning : failed to load external entity "/home/udoluweera/.compiz/session/10a9566d77bd7b551e132818547515865700000036150037"
Initializing session options...done
** Message: applet now removed from the notification area
Initializing wall options...done

(bzr-notify:3710): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bzr-notify:3710): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bzr-notify:3710): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bzr-notify:3710): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Initializing ezoom options...done
** (nm-applet:3704): DEBUG: old state indicates that this was not a disconnect 0
Initializing fade options...done
Initializing scale options...done
** Message: using fallback from indicator to GtkStatusIcon
No LSB modules are available.
Initializing nautilus-dropbox 0.6.8

Screen geometry changed:
   0x0x1366x768

unity-panel-service: no process found

(dropbox:3734): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(dropbox:3734): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(dropbox:3734): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(dropbox:3734): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Done!
Initializing unityshell options...done
Starting unity-window-decorator
compiz (core) - Warn: no exact match for ConfigureNotify on 0x120011b!
compiz (core) - Warn: expected the following changes:
compiz (core) - Warn: sibling: 0x427e99
compiz (core) - Warn: instead got:
compiz (core) - Warn: x: 0
compiz (core) - Warn: y: 0
compiz (core) - Warn: width: 1366
compiz (core) - Warn: height: 768
compiz (core) - Warn: above: 0
compiz (core) - Warn: this should never happen. you should probably file a bug about this.

(unity-window-decorator:3873): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(unity-window-decorator:3873): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(unity-window-decorator:3873): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(unity-window-decorator:3873): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
DEBUG 2012-02-02 17:54:37 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1366 h=768
** Message: moving back from GtkStatusIcon to indicator
Xlib.protocol.request.QueryExtension
Xlib.protocol.request.QueryExtension
sys:1: Warning: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Setting Update "main_menu_key"
Setting Update "run_key"
** (process:3956): DEBUG: Telepathy Indicator started
WARN  2012-02-02 17:54:42 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2012-02-02 17:54:42 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2012-02-02 17:54:42 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2012-02-02 17:54:42 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2012-02-02 17:54:42 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-02-02 17:54:42 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-02-02 17:54:42 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-02-02 17:54:42 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-02-02 17:54:43 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2012-02-02 17:54:43 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory

** (process:4111): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

(applet.py:4177): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(applet.py:4177): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(applet.py:4177): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(applet.py:4177): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(chromium-browser:4378): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(chromium-browser:4378): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(chromium-browser:4378): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(chromium-browser:4378): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gimp-2.7:4532): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gimp-2.7:4532): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gimp-2.7:4532): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gimp-2.7:4532): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
This is a development version of GIMP.  Debug messages may appear here.

WARN  2012-02-02 17:56:21 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(file-jpeg:4569): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(file-jpeg:4569): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(file-jpeg:4569): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(file-jpeg:4569): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
jpeg-load: found EXIF block (7686 bytes)
While parsing XMP metadata:
Error: No XMP packet found
lcms: skipping conversion because profiles seem to be equal:
 sRGB IEC61966-2.1
 sRGB built-in
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

/usr/lib/python2.7/dist-packages/gi/types.py:43: Warning: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
  return info.invoke(*args, **kwargs)
WARN  2012-02-02 17:58:13 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `(null)'
** (deja-dup-monitor:4557): DEBUG: monitor.vala:221: Automatic backups disabled.  Not scheduling a backup.

(script-fu:4543): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(script-fu:4543): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(script-fu:4543): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(script-fu:4543): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:3679): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

WARN  2012-02-02 18:00:27 glib.gdk <unknown>:0 compiz: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nm-applet:3704): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0"
      after 1826 requests (1826 known processed) with 0 events remaining.

(bluetooth-applet:3709): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(touchpad-indicator.py:3713): Gdk-WARNING **: touchpad-indicator.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

gnome-session[3615]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gdu-notification-daemon:4031): Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

(gnome-fallback-mount-helper:3708): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

dropbox: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
bzr-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
unity-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(gnome-terminal:4037): Gdk-WARNING **: gnome-terminal: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.


(nautilus:3706): Gdk-WARNING **: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(update-notifier:4342): Gdk-WARNING **: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

[4378:4378:1626397113:ERROR:browser_main_gtk.cc(75)] X IO Error detected

(eog:4586): Gdk-WARNING **: eog: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
gimp-2.7: Fatal IO error 104 (Connection reset by peer) on X server :0.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

(script-fu:4543): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
t.__init__, (self, ) + args, keys)
  File "/usr/lib/pymodules/python2.7/Xlib/protocol/rq.py", line 1428, in __init__
    self.reply()
  File "/usr/lib/pymodules/python2.7/Xlib/protocol/rq.py", line 1440, in reply
    self._display.send_and_recv(request = self._serial)
  File "/usr/lib/pymodules/python2.7/Xlib/protocol/display.py", line 544, in send_and_recv
    raise self.socket_error
ConnectionClosedError: Display connection closed by server


```

---

### Post by upuldi on 2012-02-04
This is what i got today.

```
Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/udoluweera/.profile
Loading resource: /etc/X11/Xresources/x11-common
Loading X session script /etc/X11/Xsession.d/20x11-common_process-args
Loading X session script /etc/X11/Xsession.d/30x11-common_xresources
Loading X session script /etc/X11/Xsession.d/40x11-common_xsessionrc
Loading X session script /etc/X11/Xsession.d/50_check_unity_support
Loading X session script /etc/X11/Xsession.d/50x11-common_determine-startup
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/55gnome-session_gnomerc
Loading X session script /etc/X11/Xsession.d/60x11-common_localhost
Loading X session script /etc/X11/Xsession.d/60x11-common_xdg_path
Loading X session script /etc/X11/Xsession.d/60xdg-user-dirs-update
Loading X session script /etc/X11/Xsession.d/65compiz_profile-on-session
Loading X session script /etc/X11/Xsession.d/70gconfd_path-on-session
Loading X session script /etc/X11/Xsession.d/75dbus_dbus-launch
Loading X session script /etc/X11/Xsession.d/80appmenu
Loading X session script /etc/X11/Xsession.d/80appmenu-gtk3
Loading X session script /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90qt-a11y
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
GNOME_KEYRING_CONTROL=/tmp/keyring-c22J0f
GNOME_KEYRING_CONTROL=/tmp/keyring-c22J0f
GPG_AGENT_INFO=/tmp/keyring-c22J0f/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-c22J0f
GPG_AGENT_INFO=/tmp/keyring-c22J0f/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-c22J0f
GPG_AGENT_INFO=/tmp/keyring-c22J0f/gpg:0:1
SSH_AUTH_SOCK=/tmp/keyring-c22J0f/ssh
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
** (gnome-fallback-mount-helper:1687): DEBUG: Starting automounting manager
Initializing nautilus-gdu extension
** (nautilus:1684): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-open-terminal extension
(bluetooth-applet:1688): Bluetooth-DEBUG: adding killswitch idx 2 state KILLSWITCH_STATE_HARD_BLOCKED
(bluetooth-applet:1688): Bluetooth-DEBUG: adding killswitch idx 3 state KILLSWITCH_STATE_SOFT_BLOCKED
(bluetooth-applet:1688): Bluetooth-DEBUG: killswitch 2 is KILLSWITCH_STATE_HARD_BLOCKED
(bluetooth-applet:1688): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_HARD_BLOCKED

(polkit-gnome-authentication-agent-1:1683): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(polkit-gnome-authentication-agent-1:1683): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(polkit-gnome-authentication-agent-1:1683): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(polkit-gnome-authentication-agent-1:1683): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(canberra-gtk-play:1707): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(canberra-gtk-play:1707): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
(bluetooth-applet:1688): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_HARD_BLOCKED
(bluetooth-applet:1688): Bluetooth-DEBUG: killswitch 2 is KILLSWITCH_STATE_HARD_BLOCKED
(bluetooth-applet:1688): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_HARD_BLOCKED

(canberra-gtk-play:1707): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(canberra-gtk-play:1707): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
(bluetooth-applet:1688): Bluetooth-DEBUG: killswitch 2 is KILLSWITCH_STATE_HARD_BLOCKED
(bluetooth-applet:1688): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_HARD_BLOCKED
Initializing detection options...done
Initializing composite options...done

(bzr-notify:1689): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bzr-notify:1689): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bzr-notify:1689): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bzr-notify:1689): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Starting Dropbox...Initializing opengl options...done
Initializing decor options...done
Dropbox isn't running!
Done!
** (gnome-fallback-mount-helper:1687): DEBUG: Found ConsoleKit session at path /org/freedesktop/ConsoleKit/Session2
** (gnome-fallback-mount-helper:1687): DEBUG: ScreenSaver name appeared
** (gnome-fallback-mount-helper:1687): DEBUG: ConsoleKit session is active 1
** (gnome-fallback-mount-helper:1687): DEBUG: ScreenSaver proxy ready
** Message: applet now removed from the notification area
** (gnome-fallback-mount-helper:1687): DEBUG: Screensaver GetActive() returned 0
Initializing vpswitch options...done
Initializing animation options...done
** (nm-applet:1682): DEBUG: old state indicates that this was not a disconnect 0
Initializing resize options...done
Initializing workarounds options...done
Initializing gnomecompat options...done
Initializing snap options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing mousepoll options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing unitymtgrabhandles options...done
I/O warning : failed to load external entity "/home/udoluweera/.compiz/session/10f80dfdb457f287bd132836565743006800000015940037"
Initializing session options...done
Initializing wall options...done
** Message: using fallback from indicator to GtkStatusIcon
Initializing ezoom options...done
Initializing fade options...done
Initializing scale options...done
Initializing nautilus-dropbox 0.6.8

Screen geometry changed:
   0x0x1366x768

unity-panel-service: no process found

(dropbox:1723): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(dropbox:1723): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(dropbox:1723): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(dropbox:1723): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
No LSB modules are available.
sys:1: Warning: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Initializing unityshell options...done
Starting unity-window-decorator

(unity-window-decorator:1857): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(unity-window-decorator:1857): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(unity-window-decorator:1857): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(unity-window-decorator:1857): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
DEBUG 2012-02-04 19:57:40 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1366 h=768
** Message: moving back from GtkStatusIcon to indicator
Setting Update "main_menu_key"
Setting Update "run_key"
Xlib.protocol.request.QueryExtension
Xlib.protocol.request.QueryExtension
** (process:1935): DEBUG: Telepathy Indicator started
WARN  2012-02-04 19:58:05 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2012-02-04 19:58:05 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2012-02-04 19:58:05 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2012-02-04 19:58:05 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2012-02-04 19:58:06 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-02-04 19:58:06 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-02-04 19:58:06 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-02-04 19:58:06 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-02-04 19:58:07 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory
WARN  2012-02-04 19:58:07 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory

(applet.py:2032): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(applet.py:2032): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(applet.py:2032): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(applet.py:2032): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(update-manager:2068): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:2068): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:2068): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:2068): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:2068): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:2068): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(thunderbird-bin:2107): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunderbird-bin:2107): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunderbird-bin:2107): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunderbird-bin:2107): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
** (process:1952): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(gnome-settings-daemon:1656): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

gnome-session[1594]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

WARN  2012-02-04 20:00:03 glib.gdk <unknown>:0 compiz: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nm-applet:1682): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

dropbox: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

(gnome-terminal:2125): Gdk-WARNING **: gnome-terminal: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

unity-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(update-notifier:2038): Gdk-WARNING **: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nautilus:1684): Gdk-WARNING **: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

bzr-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

(gnome-fallback-mount-helper:1687): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 552, in __bootstrap_inner
    self.run()
  File "/usr/share/touchpad-indicator/listenkbd.py", line 156, in run
    self.record_dpy.record_enable_context(self.ctx, self.key_press)
  File "/usr/lib/pymodules/python2.7/Xlib/ext/record.py", line 238, in enable_context
    context = context)
  File "/usr/lib/pymodules/python2.7/Xlib/ext/record.py", line 215, in __init__
    apply(rq.ReplyRequest.__init__, (self, ) + args, keys)
  File "/usr/lib/pymodules/python2.7/Xlib/protocol/rq.py", line 1428, in __init__
    self.reply()
  File "/usr/lib/pymodules/python2.7/Xlib/protocol/rq.py", line 1440, in reply
    self._display.send_and_recv(request = self._serial)
  File "/usr/lib/pymodules/python2.7/Xlib/protocol/display.py", line 544, in send_and_recv
    raise self.socket_error
ConnectionClosedError: Display connection closed by server

g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

** (process:1952): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
** (process:1952): DEBUG: zeitgeist-datahub.vala:58: Zeitgeist-daemon disappeared from the bus, exitting...
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
```

---

