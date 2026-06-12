---
title: "Firefox not starting"
date: 2009-12-23
forum: General Help
---

### Post by NadeemMd on 2009-12-23
Hi, i am new to Ubuntu i recently installed Ubuntu 9.10 (karmic kola) i was using Firefox recently i installed opera and firefox stopped working it does not start once i select firefox from application>internet>firefox it says staring firefox and it disappears it does not show any errors tried various methods uninstall and installed thru, ubuntu software centre, synaptic package manager, terminal it does not resolve the issue

---

### Post by Crafty Kisses on 2009-12-23
Try running Firefox through the terminal and post the results here back at the forums. So open a terminal and run:
```
firefox
```

---

### Post by NadeemMd on 2009-12-24
it gives Bus error

---

### Post by Soul-Sing on 2009-12-24
> **NadeemMd said:**
> it gives Bus error

Would you please copy=paste the exact content of the errors?

if you run the rhapsody plugin please remove it, this plugin gives bus errors.

---

### Post by NadeemMd on 2009-12-24
nadeem@MNLT:~$ firefox
Bus error
nadeem@MNLT:~$

---

### Post by Grenage on 2009-12-24
Your best bet is to remove and reinstall firefox via either the GUI package manager, or by the command line:

```
sudo apt-get remove firefox
sudo apt-get install firefox
```

---

### Post by NadeemMd on 2009-12-24
nadeem@MNLT:~$ sudo apt-get remove firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firefox is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.

---

### Post by DeMus on 2009-12-24
> **NadeemMd said:**
> nadeem@MNLT:~$ sudo apt-get remove firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firefox is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.

Open menu Application -> Internet and right-click on firefox. Choose to make a copy of the launcher to the desktop.
Right-click the copied launcher and choose properties.
Look at the line which tells you what command is started.
If it syas firefox-3.5 then in the codes to uninstall and install firefox you also type firefox-3.5

---

### Post by NadeemMd on 2009-12-24
i did uninstalled and installed firefox but it still does not start

---

### Post by Crafty Kisses on 2009-12-24
What are the results the following?
```
dmesg
```

---

### Post by NadeemMd on 2009-12-25
[    1.092745] Bluetooth: L2CAP ver 2.13
[    1.092747] Bluetooth: L2CAP socket layer initialized
[    1.092750] Bluetooth: SCO (Voice Link) ver 0.6
[    1.092752] Bluetooth: SCO socket layer initialized
[    1.092794] Bluetooth: RFCOMM TTY layer initialized
[    1.092798] Bluetooth: RFCOMM socket layer initialized
[    1.092800] Bluetooth: RFCOMM ver 1.11
[    1.093050] Using IPI No-Shortcut mode
[    1.093114] PM: Resume from disk failed.
[    1.093128] registered taskstats version 1
[    1.093250]   Magic number: 5:484:905
[    1.093336] rtc_cmos 00:06: setting system clock to 2009-12-25 21:53:53 UTC (1261778033)
[    1.093340] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.093342] EDD information not available.
[    1.095217] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.228977] ata2.00: ATAPI: SONY DVD+/-RW DW-D56A, PDS3, max UDMA/33
[    1.229436] ata1.00: ATA-6: FUJITSU MHV2060AH, 00000096, max UDMA/100
[    1.229439] ata1.00: 117210240 sectors, multi 8: LBA 
[    1.229454] ata1.00: applying bridge limits
[    1.244738] ata2.00: configured for UDMA/33
[    1.245159] ata1.00: configured for UDMA/100
[    1.245305] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2060A 0000 PQ: 0 ANSI: 5
[    1.245434] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.245476] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.245530] sd 0:0:0:0: [sda] Write Protect is off
[    1.245534] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.245561] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.245696]  sda:
[    1.246442] scsi 1:0:0:0: CD-ROM            SONY     DVD+-RW DW-D56A  PDS3 PQ: 0 ANSI: 5
[    1.249437] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.249441] Uniform CD-ROM driver Revision: 3.20
[    1.249520] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.249565] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.273515]  sda2 < sda5 sda6 sda7 >
[    1.286099] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.286116] Freeing unused kernel memory: 540k freed
[    1.286459] Write protecting the kernel text: 4568k
[    1.286500] Write protecting the kernel read-only data: 1836k
[    1.441319] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:22/input/input5
[    1.441373] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.441430] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434
[    1.441501] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:27/input/input6
[    1.441527] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[    1.469798] Linux agpgart interface v0.103
[    1.473814] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[    1.474479] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.515138] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.515289] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.598442] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
[    1.602889] ohci1394 0000:02:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.634677] [drm] Initialized drm 1.1.0 20060810
[    1.651214] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.651221] i915 0000:00:02.0: setting latency timer to 64
[    1.656024] Clocksource tsc unstable (delta = -122524071 ns)
[    1.657072] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[dfdf7800-dfdf7fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.657447] b44 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.760187] integrated sync not supported
[    1.837658] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    1.837682] b44.c:v2.0
[    1.865393] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:12:3f:1d:bb:79
[    2.615313] [drm] DAC-6: set mode 640x480 0
[    2.809319] integrated sync not supported
[    2.876684] [drm] TV-16: set mode NTSC 480i 0
[    3.013742] [drm] fb0: inteldrmfb frame buffer device
[    3.013753] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.089713] render error detected, EIR: 0x00000010
[    3.089716] page table error
[    3.089718]   PGTBL_ER: 0x00000100
[    3.089721] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[    3.089728] render error detected, EIR: 0x00000010
[    3.089730] page table error
[    3.089732]   PGTBL_ER: 0x00000100
[    3.097624] [drm] LVDS-8: set mode 1024x768 19
[    3.369910] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[464fc0003c5ed830]
[    3.406549] Console: switching to colour frame buffer device 128x48
[    3.684301] PM: Starting manual resume from disk
[    3.684306] PM: Resume from partition 8:6
[    3.684308] PM: Checking hibernation image.
[    3.684497] PM: Resume from disk failed.
[    3.687277] EXT4-fs (sda7): INFO: recovery required on readonly filesystem
[    3.687281] EXT4-fs (sda7): write access will be enabled during recovery
[    3.720736] EXT4-fs (sda7): barriers enabled
[    6.174058] kjournald2 starting: pid 382, dev sda7:8, commit interval 5 seconds
[    6.174080] EXT4-fs (sda7): delayed allocation enabled
[    6.174084] EXT4-fs: file extents enabled
[    6.174181] EXT4-fs: mballoc enabled
[    6.174197] EXT4-fs (sda7): orphan cleanup on readonly fs
[    6.174206] EXT4-fs (sda7): ext4_orphan_cleanup: deleting unreferenced inode 198443
[    6.174282] EXT4-fs (sda7): ext4_orphan_cleanup: deleting unreferenced inode 198430
[    6.174298] EXT4-fs (sda7): 2 orphan inodes deleted
[    6.174301] EXT4-fs (sda7): recovery complete
[    6.504722] EXT4-fs (sda7): mounted filesystem with ordered data mode
[    7.384160] type=1505 audit(1261778039.790:2): operation="profile_load" pid=405 name=/usr/share/gdm/guest-session/Xsession
[    7.386738] type=1505 audit(1261778039.790:3): operation="profile_load" pid=406 name=/sbin/dhclient3
[    7.387464] type=1505 audit(1261778039.790:4): operation="profile_load" pid=406 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.387860] type=1505 audit(1261778039.790:5): operation="profile_load" pid=406 name=/usr/lib/connman/scripts/dhclient-script
[    7.458368] type=1505 audit(1261778039.863:6): operation="profile_load" pid=407 name=/usr/bin/evince
[    7.470376] type=1505 audit(1261778039.874:7): operation="profile_load" pid=407 name=/usr/bin/evince-previewer
[    7.477347] type=1505 audit(1261778039.882:8): operation="profile_load" pid=407 name=/usr/bin/evince-thumbnailer
[    7.498471] type=1505 audit(1261778039.902:9): operation="profile_load" pid=409 name=/usr/lib/cups/backend/cups-pdf
[    7.499348] type=1505 audit(1261778039.902:10): operation="profile_load" pid=409 name=/usr/sbin/cupsd
[    7.502063] type=1505 audit(1261778039.906:11): operation="profile_load" pid=410 name=/usr/sbin/tcpdump
[   18.464344] Adding 995924k swap on /dev/sda6.  Priority:-1 extents:1 across:995924k 
[   18.495786] udev: starting version 147
[   18.539518] lp: driver loaded but no devices found
[   18.688981] EXT4-fs (sda7): internal journal on sda7:8
[   18.695238] intel_rng: FWH not detected
[   18.783502] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:01af]
[   18.783528] yenta_cardbus 0000:02:01.0: Using CSCINT to route CSC interrupts to PCI
[   18.783531] yenta_cardbus 0000:02:01.0: Routing CardBus interrupts to PCI
[   18.783538] yenta_cardbus 0000:02:01.0: TI: mfunc 0x01001022, devctl 0x64
[   18.787881] parport_pc 00:0c: reported by Plug and Play ACPI
[   18.787947] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   18.874505] cfg80211: Calling CRDA to update world regulatory domain
[   18.931833] cfg80211: World regulatory domain updated:
[   18.931837] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.931841] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.931844] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.931847] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.931851] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.931854] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.939165] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   18.945636] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   18.955407] lp0: using parport0 (interrupt-driven).
[   18.970973] ppdev: user-space parallel port driver
[   19.015731] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.025490] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0c78, PCI irq 19
[   19.025496] yenta_cardbus 0000:02:01.0: Socket status: 30000006
[   19.025501] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   19.025510] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0xdfd00000 - 0xdfdfffff
[   19.025515] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[   19.057144] dell-wmi: No known WMI GUID found
[   19.239866] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.239903] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   19.263460] phy0: Selected rate control algorithm 'minstrel'
[   19.264244] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   19.357009] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.397451] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   19.399127] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   19.399824] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   19.400441] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   19.401217] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   19.419438] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7
[   19.436470] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   19.439614] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   19.496242] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   19.508971] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   19.527004] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   19.633520] type=1505 audit(1261758252.038:12): operation="profile_replace" pid=949 name=/usr/share/gdm/guest-session/Xsession
[   19.635133] type=1505 audit(1261758252.038:13): operation="profile_replace" pid=950 name=/sbin/dhclient3
[   19.635863] type=1505 audit(1261758252.038:14): operation="profile_replace" pid=950 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   19.640274] type=1505 audit(1261758252.046:15): operation="profile_replace" pid=950 name=/usr/lib/connman/scripts/dhclient-script
[   19.644669] type=1505 audit(1261758252.050:16): operation="profile_replace" pid=952 name=/usr/bin/evince
[   19.659850] type=1505 audit(1261758252.062:17): operation="profile_replace" pid=952 name=/usr/bin/evince-previewer
[   19.678538] type=1505 audit(1261758252.082:18): operation="profile_replace" pid=952 name=/usr/bin/evince-thumbnailer
[   19.696147] type=1505 audit(1261758252.102:19): operation="profile_replace" pid=971 name=/usr/lib/cups/backend/cups-pdf
[   19.697011] type=1505 audit(1261758252.102:20): operation="profile_replace" pid=971 name=/usr/sbin/cupsd
[   19.700625] type=1505 audit(1261758252.106:21): operation="profile_replace" pid=975 name=/usr/sbin/tcpdump
[   19.728333] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   19.784712] Registered led device: b43-phy0::tx
[   19.784736] Registered led device: b43-phy0::rx
[   19.784757] Registered led device: b43-phy0::radio
[   19.785170] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.188137] intel8x0_measure_ac97_clock: measured 55447 usecs (2671 samples)
[   20.188143] intel8x0: clocking to 48000
[   20.648276] [drm] DAC-6: set mode 640x480 0
[   20.867521] [drm] DAC-6: set mode 640x480 0
[   21.093083] integrated sync not supported
[   21.180921] [drm] TV-16: set mode NTSC 480i 0
[   21.419724] [drm] TV-16: set mode NTSC 480i 0
[   21.715459] [drm] DAC-6: set mode 640x480 0
[   21.891507] [drm] DAC-6: set mode 640x480 0
[   22.113452] integrated sync not supported
[   22.226360] [drm] TV-16: set mode NTSC 480i 0
[   22.415492] [drm] TV-16: set mode NTSC 480i 0
[   22.601041] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   22.601046] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hwardware performance
[   22.601048] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   22.601050] vboxdrv: the usage of hardware performance counters by
[   22.601051] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   22.601056] vboxdrv: Found 1 processor cores.
[   22.601188] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   22.601191] vboxdrv: Successfully loaded version 3.0.12 (interface 0x00110000).
[   24.814430] [drm] DAC-6: set mode 640x480 0
[   24.945823] [drm] DAC-6: set mode 640x480 0
[   25.121576] integrated sync not supported
[   25.207296] [drm] TV-16: set mode NTSC 480i 0
[   25.374244] [drm] TV-16: set mode NTSC 480i 0
[   25.753876] [drm] DAC-6: set mode 640x480 0
[   25.911269] [drm] DAC-6: set mode 640x480 0
[   26.085753] integrated sync not supported
[   26.169313] [drm] TV-16: set mode NTSC 480i 0
[   26.335375] [drm] TV-16: set mode NTSC 480i 0
[   26.542960] [drm] DAC-6: set mode 640x480 0
[   26.677897] [drm] DAC-6: set mode 640x480 0
[   26.852356] integrated sync not supported
[   26.935358] [drm] TV-16: set mode NTSC 480i 0
[   27.100618] [drm] TV-16: set mode NTSC 480i 0
[   28.344368] wlan0: authenticate with AP 00:1c:df:d0:97:12
[   28.345834] wlan0: authenticated
[   28.345837] wlan0: associate with AP 00:1c:df:d0:97:12
[   28.349619] wlan0: RX AssocResp from 00:1c:df:d0:97:12 (capab=0x411 status=0 aid=1)
[   28.349625] wlan0: associated
[   28.350503] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   28.624561] padlock: VIA PadLock not detected.
[   39.224023] wlan0: no IPv6 routers present
[   48.214884] [drm] DAC-6: set mode 640x480 0
[   48.359752] [drm] DAC-6: set mode 640x480 0
[   48.534128] integrated sync not supported
[   48.617528] [drm] TV-16: set mode NTSC 480i 0
[   48.798433] [drm] TV-16: set mode NTSC 480i 0
[   48.985995] [drm] DAC-6: set mode 640x480 0
[   49.167538] [drm] DAC-6: set mode 640x480 0
[   49.345985] integrated sync not supported
[   49.429952] [drm] TV-16: set mode NTSC 480i 0
[   49.609777] [drm] TV-16: set mode NTSC 480i 0
[   49.804516] [drm] DAC-6: set mode 640x480 0
[   49.939258] [drm] DAC-6: set mode 640x480 0
[   50.115562] integrated sync not supported
[   50.202183] [drm] TV-16: set mode NTSC 480i 0
[   50.376715] [drm] TV-16: set mode NTSC 480i 0
[   99.444385] atkbd.c: Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0).
[   99.444392] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.
[ 1094.290256] b44: eth0: powering down PHY
[ 1094.494840] wlan0: deauthenticating by local choice (reason=3)
[ 1094.970186] PM: Marking nosave pages: 0000000000002000 - 0000000000006000
[ 1094.970191] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[ 1094.970195] PM: Basic memory bitmaps created
[ 1094.970197] PM: Syncing filesystems ... done.
[ 1095.276743] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 1095.278071] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 1095.278139] PM: Shrinking memory... done (48789 pages freed)
[ 1098.569736] PM: Freed 195156 kbytes in 3.29 seconds (59.31 MB/s)
[ 1098.569739] Suspending console(s) (use no_console_suspend to debug)
[ 1098.772161] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 1098.772507] ACPI handle has no context!
[ 1098.773802] parport_pc 00:0c: disabled
[ 1098.775019] serial 00:0b: disabled
[ 1098.775081] b43-pci-bridge 0000:02:03.0: PCI INT A disabled
[ 1098.775157] ACPI handle has no context!
[ 1098.788204] b44 0000:02:00.0: PCI INT A disabled
[ 1098.788210] ACPI handle has no context!
[ 1098.804335] ata_piix 0000:00:1f.2: PCI INT B disabled
[ 1098.804536] Intel ICH 0000:00:1e.2: PCI INT A disabled
[ 1098.817736] ACPI: Preparing to enter system sleep state S4
[ 1098.818341] PM: Saving platform NVS memory
[ 1098.818425] Disabling non-boot CPUs ...
[ 1098.818568] PM: Creating hibernation image: 
[ 1098.820020] PM: Need to copy 58937 pages
[ 1098.820020] PM: Normal pages needed: 58937 + 1024 + 14, available pages: 69940
[ 1098.820020] PM: Restoring platform NVS memory
[ 1098.820020] CPU0: Thermal LVT vector (0xfa) already installed
[ 1098.820020] ACPI: Waking up from system sleep state S4
[ 1099.510689] ehci_hcd 0000:00:1d.7: PME# disabled
[ 1099.510714] pci 0000:00:1e.0: restoring config space at offset 0x6 (was 0x20030200, writing 0x20060200)
[ 1099.510759] Intel ICH 0000:00:1e.2: restoring config space at offset 0x1 (was 0x2900007, writing 0x2900003)
[ 1099.510863] ata_piix 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b80001, writing 0x2b80005)
[ 1099.510935] b44 0000:02:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 1099.510959] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xf (was 0x74001ff, writing 0x5c001ff)
[ 1099.510985] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x3 (was 0x824010, writing 0x82a808)
[ 1099.511199] ACPI: \_SB_.PCI0.PCIE.GDCK - docking
[ 1101.108033] ohci1394 0000:02:01.2: restoring config space at offset 0xf (was 0x4020200, writing 0x4020209)
[ 1101.108061] ohci1394 0000:02:01.2: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 1101.108069] ohci1394 0000:02:01.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100116)
[ 1101.108108] b43-pci-bridge 0000:02:03.0: restoring config space at offset 0x1 (was 0x102, writing 0x106)
[ 1101.112018] acpi PNP0C15:00: parent device:28 should not be sleeping
[ 1101.389198] i915 0000:00:02.0: setting latency timer to 64
[ 1101.389583] render error detected, EIR: 0x00000010
[ 1101.389586] page table error
[ 1101.389587]   PGTBL_ER: 0x00000100
[ 1101.389591] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[ 1101.389602] render error detected, EIR: 0x00000010
[ 1101.389604] page table error
[ 1101.389606]   PGTBL_ER: 0x00000100
[ 1101.907987] [drm] LVDS-8: set mode 1024x768 19
[ 1102.767795] pci 0000:00:02.1: PME# disabled
[ 1102.767803] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 1102.767841] usb usb2: root hub lost power or was reset
[ 1102.767862] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 1102.767899] usb usb3: root hub lost power or was reset
[ 1102.767918] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 1102.767955] usb usb4: root hub lost power or was reset
[ 1102.767973] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 1102.768004] usb usb5: root hub lost power or was reset
[ 1102.768040] ehci_hcd 0000:00:1d.7: PME# disabled
[ 1102.768045] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 1102.768050] usb usb1: root hub lost power or was reset
[ 1102.771928] ehci_hcd 0000:00:1d.7: debug port 1
[ 1102.771935] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[ 1102.771947] pci 0000:00:1e.0: setting latency timer to 64
[ 1102.771958] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1102.771965] Intel ICH 0000:00:1e.2: setting latency timer to 64
[ 1103.781725] pci 0000:00:1e.3: PME# disabled
[ 1103.781735] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 1103.781740] ata_piix 0000:00:1f.2: setting latency timer to 64
[ 1103.781903] b44 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1103.781922] ata1.00: _GTF evaluation failed (AE 0x1001)
[ 1103.856186] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[dfdf7800-dfdf7fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[ 1103.856218] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1103.891705] serial 00:0b: activated
[ 1103.915650] parport_pc 00:0c: activated
[ 1103.952523] ata2.00: configured for UDMA/33
[ 1103.960810] ata1.00: configured for UDMA/100
[ 1104.149216] sd 0:0:0:0: [sda] Starting disk
[ 1104.248334] PM: Image restored successfully.
[ 1104.266047] Restarting tasks ... done.
[ 1104.284299] PM: Basic memory bitmaps freed
[ 1104.376035] usb 1-2: new high speed USB device using ehci_hcd and address 2
[ 1104.508481] usb 1-2: configuration #1 chosen from 1 choice
[ 1104.508649] hub 1-2:1.0: USB hub found
[ 1104.508739] hub 1-2:1.0: 4 ports detected
[ 1110.210846] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1110.372208] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1110.412915] Registered led device: b43-phy0::tx
[ 1110.412957] Registered led device: b43-phy0::rx
[ 1110.412997] Registered led device: b43-phy0::radio
[ 1110.413442] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1115.790543] wlan0: authenticate with AP 00:1c:df:d0:97:12
[ 1115.797708] wlan0: authenticated
[ 1115.797715] wlan0: associate with AP 00:1c:df:d0:97:12
[ 1115.800705] wlan0: RX AssocResp from 00:1c:df:d0:97:12 (capab=0x411 status=0 aid=1)
[ 1115.800714] wlan0: associated
[ 1115.801934] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1126.668173] wlan0: no IPv6 routers present
[ 2095.750375] [drm] DAC-6: set mode 640x480 0
[ 2095.880684] [drm] DAC-6: set mode 640x480 0
[ 2096.090158] integrated sync not supported
[ 2096.174845] [drm] TV-16: set mode NTSC 480i 0
[ 2096.349910] [drm] TV-16: set mode NTSC 480i 0
[ 3419.188186] usb 4-1: new full speed USB device using uhci_hcd and address 2
[ 3419.380479] usb 4-1: configuration #3 chosen from 1 choice
[ 3419.877678] cdc_wdm 4-1:3.7: cdc-wdm0: USB WDM device
[ 3419.877716] usbcore: registered new interface driver cdc_wdm
[ 3419.899514] cdc_acm 4-1:3.1: ttyACM0: USB ACM device
[ 3419.903673] cdc_acm 4-1:3.3: ttyACM1: USB ACM device
[ 3419.905306] usbcore: registered new interface driver cdc_acm
[ 3419.905311] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[ 3420.008385] cdc_ether: probe of 4-1:3.8 failed with error -71
[ 3420.008423] usbcore: registered new interface driver cdc_ether
[ 3420.123230] tty_port_close_start: tty->count = 1 port count = 0.
[ 3420.139452] tty_port_close_start: tty->count = 1 port count = 0.
[ 3420.245738] usb 4-1: USB disconnect, address 2
[ 3420.246836] uhci_hcd 0000:00:1d.2: dma_pool_free buffer-2048, d4d4c000/14d4c000 (bad dma)
[ 3420.741598] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 3421.620078] usb 4-1: new full speed USB device using uhci_hcd and address 3
[ 3421.809405] usb 4-1: configuration #3 chosen from 1 choice
[ 3421.839245] cdc_acm 4-1:3.1: ttyACM0: USB ACM device
[ 3421.847340] cdc_acm 4-1:3.3: ttyACM1: USB ACM device
[ 3421.860526] cdc_wdm 4-1:3.7: cdc-wdm0: USB WDM device
[ 3421.872868] usb0: register 'cdc_ether' at usb-0000:00:1d.2-1, CDC Ethernet Device, 02:80:37:fb:02:00
[ 3432.448174] usb0: no IPv6 routers present
[ 3799.528222] usb 4-1: USB disconnect, address 3
[ 3799.531303] uhci_hcd 0000:00:1d.2: dma_pool_free buffer-2048, d4d4ce80/14d4ce80 (bad dma)
[ 3799.531400] usb0: unregister 'cdc_ether' usb-0000:00:1d.2-1, CDC Ethernet Device
[ 3800.152205] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 3801.044209] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 3801.340061] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 3802.592209] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 3803.720211] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 4101.828194] usb 4-1: new full speed USB device using uhci_hcd and address 4
[ 4101.936226] hub 4-0:1.0: unable to enumerate USB device on port 1
[ 4110.976079] hub 4-0:1.0: unable to enumerate USB device on port 1
[ 4111.752050] usb 4-1: new full speed USB device using uhci_hcd and address 6
[ 4111.982451] usb 4-1: configuration #3 chosen from 1 choice
[ 4111.998756] cdc_acm 4-1:3.1: ttyACM0: USB ACM device
[ 4112.006738] cdc_acm 4-1:3.3: ttyACM1: USB ACM device
[ 4112.024143] cdc_wdm 4-1:3.7: cdc-wdm0: USB WDM device
[ 4112.044488] usb0: register 'cdc_ether' at usb-0000:00:1d.2-1, CDC Ethernet Device, 02:80:37:fb:02:00
[ 4122.484169] usb0: no IPv6 routers present
[ 4154.324194] usb 1-7: new high speed USB device using ehci_hcd and address 14
[ 4154.459465] usb 1-7: configuration #1 chosen from 1 choice
[ 4171.364831] usb 1-7: USB disconnect, address 14
[ 4289.080224] usb 4-1: USB disconnect, address 6
[ 4289.083292] uhci_hcd 0000:00:1d.2: dma_pool_free buffer-2048, d4d4ce00/14d4ce00 (bad dma)
[ 4289.083390] usb0: unregister 'cdc_ether' usb-0000:00:1d.2-1, CDC Ethernet Device
[ 4379.816053] usb 1-7: new high speed USB device using ehci_hcd and address 15
[ 4379.951161] usb 1-7: configuration #1 chosen from 1 choice
[ 4400.835538] usb 1-7: USB disconnect, address 15
[ 4417.444206] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 4423.068207] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 4429.992203] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 4430.232051] usb 1-7: new high speed USB device using ehci_hcd and address 19
[ 4430.367153] usb 1-7: configuration #1 chosen from 1 choice
[ 4435.448076] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 4438.468204] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 4443.244209] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 4445.780072] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 4447.396061] hub 4-0:1.0: unable to enumerate USB device on port 1
[ 4447.696591] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 4449.680056] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 4452.836050] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 4453.568118] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 4454.142290] hub 4-0:1.0: unable to enumerate USB device on port 1
[ 4454.968795] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 4455.264095] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 4455.736059] usb 4-1: new full speed USB device using uhci_hcd and address 9
[ 4455.804135] hub 4-0:1.0: unable to enumerate USB device on port 1
[ 4456.788213] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 4457.776199] usb 4-1: new full speed USB device using uhci_hcd and address 10
[ 4458.005736] usb 4-1: configuration #3 chosen from 1 choice
[ 4458.022020] cdc_acm 4-1:3.1: ttyACM0: USB ACM device
[ 4458.034574] cdc_acm 4-1:3.3: ttyACM1: USB ACM device
[ 4458.056883] cdc_wdm 4-1:3.7: cdc-wdm0: USB WDM device
[ 4458.072837] usb0: register 'cdc_ether' at usb-0000:00:1d.2-1, CDC Ethernet Device, 02:80:37:fb:02:00
[ 4459.208205] usb 4-1: USB disconnect, address 10
[ 4459.213374] uhci_hcd 0000:00:1d.2: dma_pool_free buffer-2048, d4d4cd80/14d4cd80 (bad dma)
[ 4459.213486] usb0: unregister 'cdc_ether' usb-0000:00:1d.2-1, CDC Ethernet Device
[ 4470.720198] usb 4-1: new full speed USB device using uhci_hcd and address 11
[ 4470.844192] usb 4-1: device descriptor read/64, error -71
[ 4471.068192] usb 4-1: device descriptor read/64, error -71
[ 4471.285105] usb 4-1: new full speed USB device using uhci_hcd and address 12
[ 4471.408191] usb 4-1: device descriptor read/64, error -71
[ 4471.640208] usb 4-1: device descriptor read/64, error -71
[ 4471.912193] usb 4-1: new full speed USB device using uhci_hcd and address 13
[ 4472.324115] usb 4-1: device not accepting address 13, error -71
[ 4472.436192] usb 4-1: new full speed USB device using uhci_hcd and address 14
[ 4472.852177] usb 4-1: device not accepting address 14, error -71
[ 4472.852212] hub 4-0:1.0: unable to enumerate USB device on port 1
[ 4504.340031] usb 4-1: new full speed USB device using uhci_hcd and address 15
[ 4504.468037] usb 4-1: device descriptor read/64, error -71
[ 4504.700026] usb 4-1: device descriptor read/64, error -71
[ 4504.925920] usb 4-1: new full speed USB device using uhci_hcd and address 16
[ 4505.064033] usb 4-1: device descriptor read/64, error -71
[ 4505.312031] usb 4-1: device descriptor read/64, error -71
[ 4505.536045] usb 4-1: new full speed USB device using uhci_hcd and address 17
[ 4505.968021] usb 4-1: device not accepting address 17, error -71
[ 4506.080042] usb 4-1: new full speed USB device using uhci_hcd and address 18
[ 4506.504518] usb 4-1: device not accepting address 18, error -71
[ 4506.504549] hub 4-0:1.0: unable to enumerate USB device on port 1

---

### Post by zaki-chao on 2009-12-25
remove it and set up new..:P

---

### Post by NadeemMd on 2009-12-25
remove? firefox, i did that it doesnot work

---

### Post by NadeemMd on 2009-12-25
how to reinstall ubuntu without loosing the data

---

### Post by HectorG on 2009-12-28
I am also having the same problem. seems to have come after an update. I have also tried uninstalling and reinstalling various times with no progress.

even get the bus error with safe-mode

I also tried deleting my profile but still nothing.

---

### Post by HectorG on 2009-12-29
Whoever hasn't gotten their firefox to work yet I found a way to get it to work. I hope it works for you as well... 

I couldnt get it to work with "sudo apt-get --remove firefox" but the following did work!

*************************************************************************************

System -> Synaptic Package Manager-> 

On the quick search type firefox and select everything related to firefox you can find. In my case I just had the regular firefox 3.5.6+nobinonly-0ubuntu0.9.10.1

make sure you select it and right click. 

select mark for complete uninstall and click apply. (it will select a couple of other packages to uninstall like ubufox ...

when its done reinstall it through the synaptic the same way you uninstalled it. 

Good Luck

---

