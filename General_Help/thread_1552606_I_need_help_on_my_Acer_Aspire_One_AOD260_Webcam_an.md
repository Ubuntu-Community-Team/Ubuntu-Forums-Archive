---
title: "I need help on my Acer Aspire One AOD260 Webcam and Microphone problems"
date: 2010-08-13
forum: General Help
---

### Post by supermario641996 on 2010-08-13
I have a Acer Aspire One AOD260.  It came with Windows 7 Starter so I bought an external USB CD/DVD Drive.  I then install Ubuntu 9.04 on it.  I upgraded to 9.10 witch fixed the wireless card driver.  I then upgraded to 10.04 and that did nothing.  I have a problem with my internal webcam.  Youtube will detect it but it has low frame rate and low resolution. Almost none of the programs run right with the webcam.  With cheese it records sound and a will randomly record then stop witch I mean that it will record with a black screen then normal for less than a second.  My microphone sort of works.  It will only work if i get gnome-alsa mixer and change the bar under the volume bar for capture to the right but then even when it will not record it will have this funky sort of fuzzy clicking noise both with it being able to record and without. :confused:

Stuff you might need to help me is below.
[PHP][/PHP]```
$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

Thanks in advance. :)

---

### Post by lisati on 2010-08-13
Support request not directly relating to forum features: moved to "General Help"

---

### Post by supermario641996 on 2010-08-17
Please somebody help me.  I just need some pointers on were I should go for help.  I have been searching google for an answer, and I get nothing.

---

### Post by no2498 on 2010-08-17
try the cheese help faq's

should help you some

---

### Post by no2498 on 2010-08-17
open a terminal put this in it

dmesg

paste the output here

---

### Post by supermario641996 on 2010-08-17
> **no2498 said:**
> open a terminal put this in it

dmesg

paste the output here
```
$dmesg
 : 0 ANSI: 0 CCS
[ 6095.481508] sd 5:0:0:0: Attached scsi generic sg1 type 0
[ 6095.486472] sd 5:0:0:0: [sdb] 3895296 512-byte logical blocks: (1.99 GB/1.85 GiB)
[ 6095.486910] sd 5:0:0:0: [sdb] Write Protect is off
[ 6095.486920] sd 5:0:0:0: [sdb] Mode Sense: 00 ce 20 00
[ 6095.486927] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 6095.493905] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 6095.493922]  sdb: sdb1
[ 6095.509947] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 6095.509959] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 6156.644805] usb 1-1: USB disconnect, address 5
[ 6318.936111] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 6319.070514] usb 1-1: configuration #1 chosen from 1 choice
[ 6319.071568] scsi6 : SCSI emulation for USB Mass Storage devices
[ 6319.073222] usb-storage: device found at 6
[ 6319.073235] usb-storage: waiting for device to settle before scanning
[ 6324.072356] usb-storage: device scan complete
[ 6324.072929] scsi 6:0:0:0: Direct-Access     Sony     PSP              1.00 PQ: 0 ANSI: 0 CCS
[ 6324.082756] sd 6:0:0:0: Attached scsi generic sg1 type 0
[ 6324.089283] sd 6:0:0:0: [sdb] 3895296 512-byte logical blocks: (1.99 GB/1.85 GiB)
[ 6324.089768] sd 6:0:0:0: [sdb] Write Protect is off
[ 6324.089776] sd 6:0:0:0: [sdb] Mode Sense: 00 ce 20 00
[ 6324.089781] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 6324.092788] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 6324.092805]  sdb: sdb1
[ 6324.099420] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 6324.099438] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 6352.023845] usb 1-1: USB disconnect, address 6
[ 6595.396984] usb 1-1: new high speed USB device using ehci_hcd and address 7
[ 6595.529514] usb 1-1: configuration #1 chosen from 1 choice
[ 6595.536042] scsi7 : SCSI emulation for USB Mass Storage devices
[ 6595.551024] usb-storage: device found at 7
[ 6595.551032] usb-storage: waiting for device to settle before scanning
[ 6600.548930] usb-storage: device scan complete
[ 6600.549604] scsi 7:0:0:0: Direct-Access     Sony     PSP              1.00 PQ: 0 ANSI: 0 CCS
[ 6600.555721] sd 7:0:0:0: Attached scsi generic sg1 type 0
[ 6600.559325] sd 7:0:0:0: [sdb] 3895296 512-byte logical blocks: (1.99 GB/1.85 GiB)
[ 6600.559808] sd 7:0:0:0: [sdb] Write Protect is off
[ 6600.559821] sd 7:0:0:0: [sdb] Mode Sense: 00 ce 20 00
[ 6600.559830] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 6600.563309] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 6600.563326]  sdb: sdb1
[ 6600.569716] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 6600.569733] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 6630.541388] usb 1-1: USB disconnect, address 7
[ 7687.715236] CPU0 attaching NULL sched-domain.
[ 7687.715254] CPU1 attaching NULL sched-domain.
[ 7687.748190] CPU0 attaching sched-domain:
[ 7687.748203]  domain 0: span 0-1 level SIBLING
[ 7687.748213]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[ 7687.748234]   domain 1: span 0-1 level MC
[ 7687.748242]    groups: 0-1 (cpu_power = 1178)
[ 7687.748259] CPU1 attaching sched-domain:
[ 7687.748267]  domain 0: span 0-1 level SIBLING
[ 7687.748276]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[ 7687.748294]   domain 1: span 0-1 level MC
[ 7687.748303]    groups: 0-1 (cpu_power = 1178)
[ 7689.544714] wlan0: deauthenticating from 00:22:3f:7c:0b:ce by local choice (reason=3)
[ 7691.044333] PM: Syncing filesystems ... done.
[ 7691.212069] PM: Preparing system for mem sleep
[ 7691.212076] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 7691.213702] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 7691.213885] PM: Entering mem sleep
[ 7691.213907] Suspending console(s) (use no_console_suspend to debug)
[ 7691.240664] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 7691.240931] sd 0:0:0:0: [sda] Stopping disk
[ 7691.830513] PM: suspend of drv:sd dev:0:0:0:0 complete after 589.855 msecs
[ 7692.280814] PM: suspend of drv:psmouse dev:serio1 complete after 416.732 msecs
[ 7692.384072] PM: suspend of drv:atkbd dev:serio0 complete after 103.230 msecs
[ 7692.386172] ath9k 0000:02:00.0: PCI INT A disabled
[ 7692.400205] atl1c 0000:01:00.0: PCI INT A disabled
[ 7692.464087] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 7692.464103] uhci_hcd 0000:00:1d.3: PCI INT D disabled
[ 7692.464117] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 7692.464131] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 7692.464145] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 7692.569047] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 7692.584078] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 119.911 msecs
[ 7692.640455] PM: suspend of devices complete after 1426.282 msecs
[ 7692.640463] PM: suspend devices took 1.428 seconds
[ 7692.656338] PM: late suspend of devices complete after 15.864 msecs
[ 7692.656393] ACPI: Preparing to enter system sleep state S3
[ 7692.676027] Disabling non-boot CPUs ...
[ 7692.676066] CPU0 attaching NULL sched-domain.
[ 7692.676075] CPU1 attaching NULL sched-domain.
[ 7692.740031] CPU0 attaching NULL sched-domain.
[ 7692.741267] Breaking affinity for irq 12
[ 7692.741288] Breaking affinity for irq 17
[ 7692.741341] Breaking affinity for irq 27
[ 7692.844036] CPU 1 is now offline
[ 7692.844041] SMP alternatives: switching to UP code
[ 7692.850053] Back to C!
[ 7692.850053] CPU0: Thermal monitoring handled by SMI
[ 7692.850053] Enabling non-boot CPUs ...
[ 7692.850053] SMP alternatives: switching to SMP code
[ 7692.855535] Booting processor 1 APIC 0x1 ip 0x6000
[ 7692.849273] Initializing CPU#1
[ 7692.849273] CPU: L1 I cache: 32K, L1 D cache: 24K
[ 7692.849273] CPU: L2 cache: 512K
[ 7692.849273] CPU: Physical Processor ID: 0
[ 7692.849273] CPU: Processor Core ID: 0
[ 7692.849273] CPU1: Thermal monitoring handled by SMI
[ 7692.944130] CPU1: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
[ 7692.944279] CPU0 attaching NULL sched-domain.
[ 7692.972036] CPU0 attaching sched-domain:
[ 7692.972045]  domain 0: span 0-1 level SIBLING
[ 7692.972052]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[ 7692.972066]   domain 1: span 0-1 level MC
[ 7692.972072]    groups: 0-1 (cpu_power = 1178)
[ 7692.972083] CPU1 attaching sched-domain:
[ 7692.972089]  domain 0: span 0-1 level SIBLING
[ 7692.972095]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[ 7692.972108]   domain 1: span 0-1 level MC
[ 7692.972114]    groups: 0-1 (cpu_power = 1178)
[ 7692.976043] CPU1 is up
[ 7692.976211] ACPI: Waking up from system sleep state S3
[ 7692.977130] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[ 7692.977223] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 7692.977238] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 7692.977287] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x1ff)
[ 7692.977309] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x50f15001)
[ 7692.977321] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0x57f05700)
[ 7692.977333] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x5050)
[ 7692.977345] pcieport 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0x10100)
[ 7692.977361] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 7692.977375] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 7692.977445] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x2ff)
[ 7692.977466] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0x51f15101)
[ 7692.977478] pcieport 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0x56f05600)
[ 7692.977490] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0x20000000, writing 0x4040)
[ 7692.977502] pcieport 0000:00:1c.1: restoring config space at offset 0x6 (was 0x0, writing 0x20200)
[ 7692.977518] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 7692.977532] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 7692.977614] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 7692.977667] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 7692.977717] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 7692.977768] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 7692.977823] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x4 (was 0x0, writing 0x58204400)
[ 7692.977839] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[ 7692.977879] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x0, writing 0xff)
[ 7692.978001] ahci 0000:00:1f.2: restoring config space at offset 0x9 (was 0x58200000, writing 0x58204000)
[ 7692.978025] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 7692.978135] atl1c 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 7692.978173] atl1c 0000:01:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 7692.978188] atl1c 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 7692.978269] ath9k 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10a)
[ 7692.978304] ath9k 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0x56000004)
[ 7692.978317] ath9k 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 7692.978331] ath9k 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 7692.978733] PM: early resume of devices complete after 1.758 msecs
[ 7693.804231] PM: resume of drv:battery dev:PNP0C0A:00 complete after 825.232 msecs
[ 7693.877395] i915 0000:00:02.0: setting latency timer to 64
[ 7693.877928] [drm] Big FIFO is enabled
[ 7693.948066] [drm] Big FIFO is enabled
[ 7693.948078] [drm] Big FIFO is enabled
[ 7693.948181] [drm] Big FIFO is enabled
[ 7693.972239] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 7693.972251] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 7693.972296] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 7693.972306] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 7693.972335] usb usb2: root hub lost power or was reset
[ 7693.972364] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 7693.972374] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 7693.972401] usb usb3: root hub lost power or was reset
[ 7693.972443] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 7693.972454] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 7693.972480] usb usb4: root hub lost power or was reset
[ 7693.972508] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[ 7693.972518] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 7693.972545] usb usb5: root hub lost power or was reset
[ 7693.972573] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 7693.972583] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 7693.972624] pci 0000:00:1e.0: setting latency timer to 64
[ 7693.972649] ahci 0000:00:1f.2: setting latency timer to 64
[ 7694.048087] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 7694.204071] PM: resume of drv:usb dev:usb1 complete after 155.460 msecs
[ 7694.292090] ata2: SATA link down (SStatus 0 SControl 300)
[ 7694.452069] PM: resume of drv:usb dev:usb3 complete after 247.962 msecs
[ 7694.568072] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[ 7694.735203] PM: resume of drv:usb dev:1-4 complete after 277.994 msecs
[ 7694.992067] usb 3-1: reset low speed USB device using uhci_hcd and address 2
[ 7695.299128] PM: resume of drv:usb dev:3-1 complete after 563.905 msecs
[ 7695.299188] sd 0:0:0:0: [sda] Starting disk
[ 7695.968077] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 7695.969495] ata1.00: _GTF unexpected object type 0x1
[ 7696.004361] ata1.00: _GTF unexpected object type 0x1
[ 7696.004703] ata1.00: configured for UDMA/133
[ 7696.031570] PM: resume of drv:sd dev:0:0:0:0 complete after 732.380 msecs
[ 7696.036213] PM: resume of devices complete after 3057.435 msecs
[ 7696.036468] PM: resume devices took 3.060 seconds
[ 7696.036547] PM: Finishing wakeup.
[ 7696.036553] Restarting tasks ... done.
[ 7697.036561] atl1c 0000:01:00.0: irq 28 for MSI/MSI-X
[ 7697.037707] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7697.074398] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7697.916938] CPU0 attaching NULL sched-domain.
[ 7697.916950] CPU1 attaching NULL sched-domain.
[ 7697.940206] CPU0 attaching sched-domain:
[ 7697.940219]  domain 0: span 0-1 level SIBLING
[ 7697.940229]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[ 7697.940250]   domain 1: span 0-1 level MC
[ 7697.940259]    groups: 0-1 (cpu_power = 1178)
[ 7697.940277] CPU1 attaching sched-domain:
[ 7697.940284]  domain 0: span 0-1 level SIBLING
[ 7697.940293]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[ 7697.940312]   domain 1: span 0-1 level MC
[ 7697.940320]    groups: 0-1 (cpu_power = 1178)
[ 7703.293994] wlan0: deauthenticating from 00:22:3f:7c:0b:ce by local choice (reason=3)
[ 7703.494160] wlan0: direct probe to AP 00:22:3f:7c:0b:ce (try 1)
[ 7703.501635] wlan0: direct probe responded
[ 7703.501647] wlan0: authenticate with AP 00:22:3f:7c:0b:ce (try 1)
[ 7703.503615] wlan0: authenticated
[ 7703.503661] wlan0: associate with AP 00:22:3f:7c:0b:ce (try 1)
[ 7703.506261] wlan0: RX AssocResp from 00:22:3f:7c:0b:ce (capab=0x431 status=0 aid=2)
[ 7703.506270] wlan0: associated
[ 7703.507054] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7714.332055] wlan0: no IPv6 routers present
[ 8547.449187] CPU0 attaching NULL sched-domain.
[ 8547.449201] CPU1 attaching NULL sched-domain.
[ 8547.472627] CPU0 attaching sched-domain:
[ 8547.472636]  domain 0: span 0-1 level SIBLING
[ 8547.472643]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[ 8547.472655]   domain 1: span 0-1 level MC
[ 8547.472660]    groups: 0-1 (cpu_power = 1178)
[ 8547.472672] CPU1 attaching sched-domain:
[ 8547.472676]  domain 0: span 0-1 level SIBLING
[ 8547.472682]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[ 8547.472693]   domain 1: span 0-1 level MC
[ 8547.472698]    groups: 0-1 (cpu_power = 1178)
[ 8548.728148] usb 3-1: USB disconnect, address 2
[ 8692.134008] CPU0 attaching NULL sched-domain.
[ 8692.134023] CPU1 attaching NULL sched-domain.
[ 8692.160983] CPU0 attaching sched-domain:
[ 8692.160993]  domain 0: span 0-1 level SIBLING
[ 8692.161001]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[ 8692.161018]   domain 1: span 0-1 level MC
[ 8692.161025]    groups: 0-1 (cpu_power = 1178)
[ 8692.161041] CPU1 attaching sched-domain:
[ 8692.161047]  domain 0: span 0-1 level SIBLING
[ 8692.161055]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[ 8692.161071]   domain 1: span 0-1 level MC
[ 8692.161078]    groups: 0-1 (cpu_power = 1178)
[ 8793.656585] usb 3-1: new low speed USB device using uhci_hcd and address 3
[ 8793.832821] usb 3-1: configuration #1 chosen from 1 choice
[ 8793.849253] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input11
[ 8793.849497] generic-usb 0003:046D:C00E.0002: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1/input0
[12438.112768] [drm] Big FIFO is enabled
[12438.188081] [drm] Big FIFO is enabled
[12438.188099] [drm] Big FIFO is enabled
[12438.563503] [drm] Big FIFO is enabled
[12440.684780] [drm] Big FIFO is enabled
[12440.760052] [drm] Big FIFO is enabled
[12440.760072] [drm] Big FIFO is enabled
[12441.176091] [drm] Big FIFO is enabled
[12880.602710] CPU0 attaching NULL sched-domain.
[12880.602724] CPU1 attaching NULL sched-domain.
[12880.636209] CPU0 attaching sched-domain:
[12880.636219]  domain 0: span 0-1 level SIBLING
[12880.636228]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[12880.636245]   domain 1: span 0-1 level MC
[12880.636252]    groups: 0-1 (cpu_power = 1178)
[12880.636267] CPU1 attaching sched-domain:
[12880.636274]  domain 0: span 0-1 level SIBLING
[12880.636281]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[12880.636297]   domain 1: span 0-1 level MC
[12880.636304]    groups: 0-1 (cpu_power = 1178)
[12883.264166] wlan0: deauthenticating from 00:22:3f:7c:0b:ce by local choice (reason=3)
[12885.112910] PM: Syncing filesystems ... done.
[12885.136573] PM: Preparing system for mem sleep
[12885.136583] Freezing user space processes ... (elapsed 0.00 seconds) done.
[12885.138349] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[12885.138536] PM: Entering mem sleep
[12885.138558] Suspending console(s) (use no_console_suspend to debug)
[12885.216160] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[12885.243345] sd 0:0:0:0: [sda] Stopping disk
[12885.831765] PM: suspend of drv:sd dev:0:0:0:0 complete after 615.608 msecs
[12886.261219] PM: suspend of drv:psmouse dev:serio1 complete after 417.135 msecs
[12886.364077] PM: suspend of drv:atkbd dev:serio0 complete after 102.830 msecs
[12886.366917] ath9k 0000:02:00.0: PCI INT A disabled
[12886.444089] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[12886.444106] uhci_hcd 0000:00:1d.3: PCI INT D disabled
[12886.444120] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[12886.444134] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[12886.444147] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[12886.548438] HDA Intel 0000:00:1b.0: PCI INT A disabled
[12886.564071] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 119.902 msecs
[12886.592457] PM: suspend of devices complete after 1453.634 msecs
[12886.592465] PM: suspend devices took 1.456 seconds
[12886.608456] PM: late suspend of devices complete after 15.981 msecs
[12886.608507] ACPI: Preparing to enter system sleep state S3
[12886.624027] Disabling non-boot CPUs ...
[12886.624063] CPU0 attaching NULL sched-domain.
[12886.624071] CPU1 attaching NULL sched-domain.
[12886.688031] CPU0 attaching NULL sched-domain.
[12886.792039] CPU 1 is now offline
[12886.792044] SMP alternatives: switching to UP code
[12886.797915] Back to C!
[12886.797915] CPU0: Thermal monitoring handled by SMI
[12886.797915] Enabling non-boot CPUs ...
[12886.797915] SMP alternatives: switching to SMP code
[12886.803403] Booting processor 1 APIC 0x1 ip 0x6000
[12886.797182] Initializing CPU#1
[12886.797182] CPU: L1 I cache: 32K, L1 D cache: 24K
[12886.797182] CPU: L2 cache: 512K
[12886.797182] CPU: Physical Processor ID: 0
[12886.797182] CPU: Processor Core ID: 0
[12886.797182] CPU1: Thermal monitoring handled by SMI
[12886.892128] CPU1: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
[12886.892239] CPU0 attaching NULL sched-domain.
[12886.920036] CPU0 attaching sched-domain:
[12886.920045]  domain 0: span 0-1 level SIBLING
[12886.920051]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[12886.920066]   domain 1: span 0-1 level MC
[12886.920072]    groups: 0-1 (cpu_power = 1178)
[12886.920083] CPU1 attaching sched-domain:
[12886.920089]  domain 0: span 0-1 level SIBLING
[12886.920095]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[12886.920108]   domain 1: span 0-1 level MC
[12886.920114]    groups: 0-1 (cpu_power = 1178)
[12886.924033] CPU1 is up
[12886.924205] ACPI: Waking up from system sleep state S3
[12886.925125] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[12886.925219] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[12886.925233] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[12886.925283] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x1ff)
[12886.925304] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x50f15001)
[12886.925316] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0x57f05700)
[12886.925328] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x20005050)
[12886.925341] pcieport 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0x10100)
[12886.925356] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[12886.925370] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[12886.925440] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x2ff)
[12886.925461] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0x51f15101)
[12886.925473] pcieport 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0x56f05600)
[12886.925485] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0x20000000, writing 0x20004040)
[12886.925497] pcieport 0000:00:1c.1: restoring config space at offset 0x6 (was 0x0, writing 0x20200)
[12886.925513] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[12886.925527] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[12886.925609] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[12886.925661] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[12886.925711] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[12886.925762] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[12886.925817] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x4 (was 0x0, writing 0x58204400)
[12886.925833] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[12886.925873] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x0, writing 0xff)
[12886.925994] ahci 0000:00:1f.2: restoring config space at offset 0x9 (was 0x58200000, writing 0x58204000)
[12886.926019] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[12886.926128] atl1c 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[12886.926166] atl1c 0000:01:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[12886.926182] atl1c 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[12886.926264] ath9k 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10a)
[12886.926301] ath9k 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0x56000004)
[12886.926313] ath9k 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[12886.926328] ath9k 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[12886.926729] PM: early resume of devices complete after 1.759 msecs
[12887.752230] PM: resume of drv:battery dev:PNP0C0A:00 complete after 825.238 msecs
[12887.825426] i915 0000:00:02.0: setting latency timer to 64
[12887.826356] [drm] Big FIFO is enabled
[12887.896066] [drm] Big FIFO is enabled
[12887.896078] [drm] Big FIFO is enabled
[12887.896212] [drm] Big FIFO is enabled
[12887.920241] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[12887.920253] HDA Intel 0000:00:1b.0: setting latency timer to 64
[12887.920298] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[12887.920308] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[12887.920337] usb usb2: root hub lost power or was reset
[12887.920366] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[12887.920376] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[12887.920403] usb usb3: root hub lost power or was reset
[12887.920446] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[12887.920456] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[12887.920483] usb usb4: root hub lost power or was reset
[12887.920510] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[12887.920520] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[12887.920547] usb usb5: root hub lost power or was reset
[12887.920575] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[12887.920585] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[12887.920627] pci 0000:00:1e.0: setting latency timer to 64
[12887.920652] ahci 0000:00:1f.2: setting latency timer to 64
[12887.996086] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[12888.152070] PM: resume of drv:usb dev:usb1 complete after 155.472 msecs
[12888.240089] ata2: SATA link down (SStatus 0 SControl 300)
[12888.400069] PM: resume of drv:usb dev:usb3 complete after 247.964 msecs
[12888.516072] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[12888.683188] PM: resume of drv:usb dev:1-4 complete after 278.401 msecs
[12888.683230] sd 0:0:0:0: [sda] Starting disk
[12889.972077] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[12889.973574] ata1.00: _GTF unexpected object type 0x1
[12890.002850] ata1.00: _GTF unexpected object type 0x1
[12890.003196] ata1.00: configured for UDMA/133
[12890.030062] PM: resume of drv:sd dev:0:0:0:0 complete after 1346.831 msecs
[12890.292071] usb 3-1: reset low speed USB device using uhci_hcd and address 3
[12890.599134] PM: resume of drv:usb dev:3-1 complete after 564.440 msecs
[12890.599166] PM: resume of devices complete after 3672.393 msecs
[12890.599421] PM: resume devices took 3.672 seconds
[12890.599486] PM: Finishing wakeup.
[12890.599490] Restarting tasks ... done.
[12892.105906] atl1c 0000:01:00.0: irq 28 for MSI/MSI-X
[12892.107231] ADDRCONF(NETDEV_UP): eth0: link is not ready
[12892.162201] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12893.606345] CPU0 attaching NULL sched-domain.
[12893.606361] CPU1 attaching NULL sched-domain.
[12893.632678] CPU0 attaching sched-domain:
[12893.632689]  domain 0: span 0-1 level SIBLING
[12893.632697]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[12893.632714]   domain 1: span 0-1 level MC
[12893.632721]    groups: 0-1 (cpu_power = 1178)
[12893.632737] CPU1 attaching sched-domain:
[12893.632743]  domain 0: span 0-1 level SIBLING
[12893.632750]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[12893.632766]   domain 1: span 0-1 level MC
[12893.632773]    groups: 0-1 (cpu_power = 1178)
[12898.378082] wlan0: deauthenticating from 00:22:3f:7c:0b:ce by local choice (reason=3)
[12898.579555] wlan0: direct probe to AP 00:22:3f:7c:0b:ce (try 1)
[12898.582384] wlan0: direct probe responded
[12898.582396] wlan0: authenticate with AP 00:22:3f:7c:0b:ce (try 1)
[12898.584368] wlan0: authenticated
[12898.584413] wlan0: associate with AP 00:22:3f:7c:0b:ce (try 1)
[12898.587002] wlan0: RX AssocResp from 00:22:3f:7c:0b:ce (capab=0x31 status=0 aid=3)
[12898.587011] wlan0: associated
[12898.587795] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12909.480533] wlan0: no IPv6 routers present

```
That is really long.  Good luck.:p

---

### Post by supermario641996 on 2010-08-18
If anyone needs any more info about my system will gladly tell you.

---

### Post by no2498 on 2010-08-18
see if you can get this program installed wxcam

read and install all that the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)


myself i like this program

---

### Post by supermario641996 on 2010-08-18
> **no2498 said:**
> see if you can get this program installed wxcam

read and install all that the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)


myself i like this program
Its not just the program with the problem I think its the driver.  The webcam has a uvc driver and I do not not if the driver is install correctly or maby I need gstreamer to mess with the settings.  It records on youtube but with really low resolution.  The only thing I can do with it is take pictures.

---

### Post by supermario641996 on 2010-08-19
If it helps, its runs with the uvc driver.  I have been able to record but its weird.  I open up cheese and record the booth with recordmydesktop but my microphone is still having problems.

---

### Post by no2498 on 2010-08-19
im not good with the mic's only had mine work for a short time

---

### Post by supermario641996 on 2010-08-20
That sucks, did you try alsamixer.  It has extra settings then just in the volume bar.

---

### Post by supermario641996 on 2010-08-30
Does somebody need more information?

---

### Post by no2498 on 2010-08-30
not me i give up on the cam mic just got my master sound slider to work yesterday thanks


you may help the original poster

---

### Post by supermario641996 on 2010-09-02
> **no2498 said:**
> not me i give up on the cam mic just got my master sound slider to work yesterday thanks


you may help the original poster
What do you mean you can help the original poster?  I posted this.

---

