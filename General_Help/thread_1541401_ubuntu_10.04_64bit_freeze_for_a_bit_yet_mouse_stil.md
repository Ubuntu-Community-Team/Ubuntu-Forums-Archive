---
title: "ubuntu 10.04 64bit freeze for a bit yet mouse still move"
date: 2010-07-29
forum: General Help
---

### Post by jcer93705 on 2010-07-29
Hi guys sometime when i'm using the web or so, my computer would stop responding except my mouse and so when i click on something i want to run it wont let me, it doesn't do anything, i cant even click on a link, mouse if i do a right click menu does show but i cant select. Sometime when i click as much as i want, sometime it high light. Man sometime it pisses me off that i power down. What's going on? Hope someone can help solve this.

---

### Post by sourchier on 2010-07-29
What kind of computer are you using? Notebook or PC? Do you have a NVIDIA graphics card? Could you tell use if there is anything using dmesg.

---

### Post by choochoousmc on 2010-07-29
> **jcer93705 said:**
> Hi guys sometime when i'm using the web or so, my computer would stop responding except my mouse and so when i click on something i want to run it wont let me, it doesn't do anything, i cant even click on a link, mouse if i do a right click menu does show but i cant select. Sometime when i click as much as i want, sometime it high light. Man sometime it pisses me off that i power down. What's going on? Hope someone can help solve this.


Do you have a touchpad?
Mine does this too.
I double touch the pad and then system is ok again.
sometimes finger or sleeve just barely touches it and this takes control away from the mouse

---

### Post by jcer93705 on 2010-07-31
> **sourchier said:**
> What kind of computer are you using? Notebook or PC? Do you have a NVIDIA graphics card? Could you tell use if there is anything using dmesg.

essors (2 cpu cores) (version 2.20.00)
[    1.600863] powernow-k8:    0 : pstate 0 (2200 MHz)
[    1.600865] powernow-k8:    1 : pstate 1 (2000 MHz)
[    1.600867] powernow-k8:    2 : pstate 2 (1500 MHz)
[    1.600868] powernow-k8:    3 : pstate 3 (1100 MHz)
[    1.600870] powernow-k8:    4 : pstate 4 (800 MHz)
[    1.601130] PM: Resume from disk failed.
[    1.601141] registered taskstats version 1
[    1.601432]   Magic number: 2:613:1000
[    1.601467] pnp 00:02: hash matches
[    1.601563] rtc_cmos 00:04: setting system clock to 2010-07-30 18:58:12 UTC (1280516292)
[    1.601565] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.601567] EDD information not available.
[    1.601631] Freeing unused kernel memory: 864k freed
[    1.601853] Write protecting the kernel read-only data: 7524k
[    1.621995] udev: starting version 151
[    1.631173] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.690110] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.692521] ahci 0000:00:11.0: version 3.0
[    1.692536]   alloc irq_desc for 22 on node 0
[    1.692539]   alloc kstat_irqs on node 0
[    1.692546] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.692604]   alloc irq_desc for 28 on node 0
[    1.692605]   alloc kstat_irqs on node 0
[    1.692615] ahci 0000:00:11.0: irq 28 for MSI/MSI-X
[    1.692629] ahci 0000:00:11.0: implemented port map (0x3f) contains more ports than nr_ports (3), using nr_ports
[    1.692631] ahci 0000:00:11.0: forcing PORTS_IMPL to 0x7
[    1.692692] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.692696] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pmp pio slum part ccc sxs 
[    1.695525] scsi0 : ahci
[    1.695706] scsi1 : ahci
[    1.697536] scsi2 : ahci
[    1.697676] ata1: SATA max UDMA/133 abar m1024@0xf2408000 port 0xf2408100 irq 28
[    1.697680] ata2: SATA max UDMA/133 abar m1024@0xf2408000 port 0xf2408180 irq 28
[    1.697684] ata3: SATA max UDMA/133 abar m1024@0xf2408000 port 0xf2408200 irq 28
[    1.698177] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.698372] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.698434] r8169 0000:03:00.0: setting latency timer to 64
[    1.698468]   alloc irq_desc for 29 on node 0
[    1.698470]   alloc kstat_irqs on node 0
[    1.698486] r8169 0000:03:00.0: irq 29 for MSI/MSI-X
[    1.699843] eth0: RTL8102e at 0xffffc90000660000, 00:26:6c:48:4e:ce, XID 04c00000 IRQ 29
[    1.954790] usb 2-1: configuration #1 chosen from 1 choice
[    2.030117] ata1: SATA link down (SStatus 0 SControl 300)
[    2.090104] usb 2-3: new high speed USB device using ehci_hcd and address 3
[    2.210111] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.230110] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.235377] ata3.00: ATAPI: HL-DT-ST DVDRAM GT20F, ET11, max UDMA/133, ATAPI AN
[    2.240832] ata3.00: configured for UDMA/133
[    2.255419] ata2.00: ATA-8: TOSHIBA MK3263GSX, FG020M, max UDMA/100
[    2.255423] ata2.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.256438] ata2.00: configured for UDMA/100
[    2.256542] scsi 1:0:0:0: Direct-Access     ATA      TOSHIBA MK3263GS FG02 PQ: 0 ANSI: 5
[    2.256709] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    2.256774] sd 1:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.256810] sd 1:0:0:0: [sda] Write Protect is off
[    2.256813] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.256831] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.256957]  sda:
[    2.259876] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT20F     ET11 PQ: 0 ANSI: 5
[    2.271248] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.271252] Uniform CD-ROM driver Revision: 3.20
[    2.271383] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.271438] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.309427]  sda1 sda2 < sda5 sda6 >
[    2.354411] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.490824] usb 2-3: configuration #1 chosen from 1 choice
[    2.503694] Initializing USB Mass Storage driver...
[    2.503804] scsi3 : SCSI emulation for USB Mass Storage devices
[    2.503881] usbcore: registered new interface driver usb-storage
[    2.503884] USB Mass Storage support registered.
[    2.503984] usb-storage: device found at 3
[    2.503985] usb-storage: waiting for device to settle before scanning
[    2.820095] usb 3-2: new low speed USB device using ohci_hcd and address 2
[    2.872225] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    2.872230] EXT4-fs (sda5): write access will be enabled during recovery
[    3.018276] usb 3-2: configuration #1 chosen from 1 choice
[    3.029490] usbcore: registered new interface driver hiddev
[    3.034361] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input5
[    3.034452] generic-usb 0003:046D:C00E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:12.0-2/input0
[    3.034476] usbcore: registered new interface driver usbhid
[    3.034478] usbhid: v2.6:USB HID core driver
[    4.335417] EXT4-fs (sda5): orphan cleanup on readonly fs
[    4.335426] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 5120428
[    4.335454] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 5120426
[    4.335504] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 5120263
[    4.335511] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 5120079
[    4.335524] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 5118747
[    4.335536] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 5117928
[    4.335543] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 5117927
[    4.335554] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 5117619
[    4.335563] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 2228774
[    4.335585] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 3148737
[    4.335626] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 3148626
[    4.335639] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 3408060
[    4.335657] EXT4-fs (sda5): 12 orphan inodes deleted
[    4.335659] EXT4-fs (sda5): recovery complete
[    4.585297] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    6.703891] Adding 4742136k swap on /dev/sda6.  Priority:-1 extents:1 across:4742136k 
[    6.976596] udev: starting version 151
[    7.510391] usb-storage: device scan complete
[    7.512887] scsi 3:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    7.513775] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    8.238767] sd 3:0:0:0: [sdb] 7744512 512-byte logical blocks: (3.96 GB/3.69 GiB)
[    8.239518] sd 3:0:0:0: [sdb] Write Protect is off
[    8.239523] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    8.239525] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[    8.242393] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[    8.242430]  sdb: sdb1
[    8.272615] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[    8.272656] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[    8.403074] EDAC MC: Ver: 2.1.0 Jul 25 2010
[    8.461341] EDAC amd64_edac:  Ver: 3.2.0 Jul 25 2010
[    8.461409] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[    8.461417] EDAC amd64: WARNING: ECC is disabled by BIOS. Module will NOT be loaded.
[    8.461419]  Either Enable ECC in the BIOS, or set 'ecc_enable_override'.
[    8.461420]  Also, use of the override can cause unknown side effects.
[    8.461438] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    8.637974] Linux video capture interface: v2.00
[    8.644886] acpi device:02: registered as cooling_device3
[    8.645125] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input6
[    8.645173] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    8.651181] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[    8.651187] shpchp 0000:00:01.0: Cannot reserve MMIO region
[    8.651371] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    8.652765] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.671951] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (064e:d104)
[    8.674556] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input7
[    8.674637] usbcore: registered new interface driver uvcvideo
[    8.674668] USB Video Class driver (v0.1.0)
[    8.993922] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    8.993926] Disabling lock debugging due to kernel taint
[    9.061562] [fglrx] Maximum main memory to use for locked dma buffers: 3550 MBytes.
[    9.061593] [fglrx]   vendor: 1002 device: 9712 count: 1
[    9.061870] [fglrx] ioport: bar 1, base 0x8000, size: 0x100
[    9.061884] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.061888] pci 0000:01:05.0: setting latency timer to 64
[    9.062173] [fglrx] Kernel PAT support is enabled
[    9.062195] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors
[    9.167675] lp: driver loaded but no devices found
[    9.708440] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[    9.780132] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   10.511505] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.511609] HDA Intel 0000:00:14.2: setting latency timer to 64
[   11.054460] hda_codec: ALC272: BIOS auto-probing.
[   11.055998] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input9
[   15.253070] r8169: eth0: link down
[   15.253488] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.933016] [fglrx] ATIF platform detected with notification ID: 0x81
[   19.262139] [fglrx] GART Table is not in FRAME_BUFFER range 
[   19.262293]   alloc irq_desc for 30 on node 0
[   19.262295]   alloc kstat_irqs on node 0
[   19.262302] fglrx_pci 0000:01:05.0: irq 30 for MSI/MSI-X
[   19.262807] [fglrx] Firegl kernel thread PID: 1070
[   19.263088] [fglrx] IRQ 30 Enabled
[   20.359781] [fglrx] Gart USWC size:1157 M.
[   20.359785] [fglrx] Gart cacheable size:459 M.
[   20.359789] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   20.359792] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   21.045127] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   21.045131] vboxdrv: Successfully done.
[   21.045133] vboxdrv: Found 2 processor cores.
[   21.045870] VBoxDrv: dbg - g_abExecMemory=ffffffffa0455ca0
[   21.045895] vboxdrv: fAsync=0 offMin=0x39b offMax=0x748
[   21.046668] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   21.046671] vboxdrv: Successfully loaded version 3.2.6 (interface 0x00140001).
[   23.387325] ppdev: user-space parallel port driver
[   26.410285] ieee80211_crypt: registered algorithm 'NULL'
[   26.410289] ieee80211_crypt: registered algorithm 'TKIP'
[   26.410291] ieee80211_crypt: registered algorithm 'CCMP'
[   26.410293] ieee80211_crypt: registered algorithm 'WEP'
[   26.410295] 
[   26.410295] Linux kernel driver for RTL8192 based WLAN cards
[   26.410297] Copyright (c) 2007-2008, Realsil Wlan
[   26.410377] rtl819xSE 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.410384] rtl819xSE 0000:02:00.0: setting latency timer to 64
[   26.410572] ===============>NIC 8192SE
[   26.411390] Dot11d_Init()
[   26.411403] IRQ 16gen_RefreshLedState first init
[   26.421661] =================> NIC version : C-cut
[   26.421693] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   26.726429] ===>rtl8192_SetWirelessMode(), wireless_mode:0x8, support_mode:0x16
[   26.726432] <===rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   26.736654] ===>ieee80211_start_scan_rsl()
[   26.737171] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.730123] ====================>haha:IPSEnter()
[   28.730129] =========>NicIFDisableNIC()
[   28.730134] PHY_SetRtl8192seRfHalt save BB/RF
[   28.732936] ===========>NicIFEnableNIC()
[   28.739991] gen_RefreshLedState first init
[   28.739994] =================> NIC version : C-cut
[   28.849427] ===>rtl8192_SetWirelessMode(), wireless_mode:0x10, support_mode:0x16
[   28.849429] <===rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   34.740074] ====================>haha:IPSEnter()
[   34.740080] =========>NicIFDisableNIC()
[   34.740086] PHY_SetRtl8192seRfHalt save BB/RF
[   52.103023] =========>r8192_wx_set_scan(): IPSLeave
[   52.103333] ===========>NicIFEnableNIC()
[   52.110401] gen_RefreshLedState first init
[   52.110404] =================> NIC version : C-cut
[   52.219821] ===>rtl8192_SetWirelessMode(), wireless_mode:0x10, support_mode:0x16
[   52.219823] <===rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   54.740098] ====================>haha:IPSEnter()
[   54.740105] =========>NicIFDisableNIC()
[   54.740109] PHY_SetRtl8192seRfHalt save BB/RF
[   58.805428] =========>r8192_wx_set_scan(): IPSLeave
[   58.805740] ===========>NicIFEnableNIC()
[   58.812801] gen_RefreshLedState first init
[   58.812805] =================> NIC version : C-cut
[   58.922264] ===>rtl8192_SetWirelessMode(), wireless_mode:0x10, support_mode:0x16
[   58.922266] <===rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   60.480888] Linking with mywireless,channel:6, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40f
[   60.480893] ============>HTIOTActIsForcedRTSCTS(), 0
[   60.480895] !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!IOTAction = 00060400
[   60.480904] ===>ieee80211_associate_procedure_wq(), chan:6
[   60.480906] ==========>HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[   60.490920] =================>ieee80211_authentication_req():auth->algorithm is 0
[   60.490960] Linking with mywireless,channel:6, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40f
[   60.490967] ============>HTIOTActIsForcedRTSCTS(), 0
[   60.490969] !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!IOTAction = 00060400
[   60.491005] ===>ieee80211_associate_procedure_wq(), chan:6
[   60.491008] ==========>HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[   60.501012] =================>ieee80211_authentication_req():auth->algorithm is 0
[   60.502512] ===>rtl8192_SetWirelessMode(), wireless_mode:0x10, support_mode:0x16
[   60.502516] <===rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   60.506923] #################ieee80211_sta_send_associnfo(), assocreq_ies_len:65,assocresp_ies_len:163
[   60.506977] ===>u4bAcParam:a42b, ===>u4bAcParam:a44f, ===>u4bAcParam:5e4322, ===>u4bAcParam:2f3222, 
[   60.506984] Associated successfully
[   60.506985] ============>normal associate
[   60.506994] Using G rates:108
[   60.506996] Successfully associated, ht enabled
[   60.506998] ==========>HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[   60.517007] !!!!!!!!!!!!!!!!!!!!!!!!!!!IOTRaFunc = 00000000
[   60.517022] ===========rtl8192se_update_ratr_table: ff005
[   60.517023] ===>set to N mode
[   60.518278] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   60.630079] =====>to send ADDBAREQ!!!!!
[   60.637187] ====================>rx ADDBARSP from :00:1c:df:88:c2:15
[   60.672977] ===>DHCP Protocol start tx DHCP pkt src port:68, dest port:67!!
[   60.799909] ========>dm_check_edca_turbo():iot peer is ralink, bssid:00:1c:df:88:c2:15
[   61.000081] =====>to send ADDBAREQ!!!!!
[   61.011814] ====================>rx ADDBARSP from :00:1c:df:88:c2:15
[   62.591505] ====================>rx ADDBAREQ from :00:1c:df:88:c2:15
[   62.591513] =====>to send ADDBARSP
[   71.430068] wlan0: no IPv6 routers present
[   82.372620] ===========rtl8192se_update_ratr_table: ff005
[   82.372623] ===>set to N mode
[   82.377306] ieee80211: can't get TS for RXTS in ieee80211_rx_DELBA().dsf:00:1c:df:88:c2:15 TID:4
[  122.373227] ===========rtl8192se_update_ratr_table: ff005
[  122.373234] ===>set to N mode
[  182.370208] ===========rtl8192se_update_ratr_table: ff005
[  182.370216] ===>set to N mode
[  262.370207] ===========rtl8192se_update_ratr_table: ff005
[  262.370215] ===>set to N mode
[  362.370210] ===========rtl8192se_update_ratr_table: ff005
[  362.370218] ===>set to N mode
[  482.280187] ===========rtl8192se_update_ratr_table: ff005
[  482.280196] ===>set to N mode
[  602.390210] ===========rtl8192se_update_ratr_table: ff005
[  602.390217] ===>set to N mode
[  722.370216] ===========rtl8192se_update_ratr_table: ff005
[  722.370222] ===>set to N mode
[  842.280190] ===========rtl8192se_update_ratr_table: ff005
[  842.280199] ===>set to N mode
[  962.380209] ===========rtl8192se_update_ratr_table: ff005
[  962.380216] ===>set to N mode
[ 1082.390195] ===========rtl8192se_update_ratr_table: ff005
[ 1082.390202] ===>set to N mode
[ 1202.280199] ===========rtl8192se_update_ratr_table: ff005
[ 1202.280208] ===>set to N mode
[ 1322.370210] ===========rtl8192se_update_ratr_table: ff005
[ 1322.370217] ===>set to N mode
[ 1442.380213] ===========rtl8192se_update_ratr_table: ff005
[ 1442.380220] ===>set to N mode
[ 1562.370194] ===========rtl8192se_update_ratr_table: ff005
[ 1562.370201] ===>set to N mode
[ 1682.370214] ===========rtl8192se_update_ratr_table: ff005
[ 1682.370221] ===>set to N mode
[ 1802.290225] ===========rtl8192se_update_ratr_table: ff005
[ 1802.290232] ===>set to N mode
[ 1922.250198] ===========rtl8192se_update_ratr_table: ff005
[ 1922.250205] ===>set to N mode
[ 2042.371903] ===========rtl8192se_update_ratr_table: ff005
[ 2042.371910] ===>set to N mode
[ 2162.270191] ===========rtl8192se_update_ratr_table: ff005
[ 2162.270198] ===>set to N mode
[ 2282.280205] ===========rtl8192se_update_ratr_table: ff005
[ 2282.280212] ===>set to N mode
[ 2402.370209] ===========rtl8192se_update_ratr_table: ff005
[ 2402.370216] ===>set to N mode
[ 2522.250204] ===========rtl8192se_update_ratr_table: ff005
[ 2522.250211] ===>set to N mode
[ 2642.370200] ===========rtl8192se_update_ratr_table: ff005
[ 2642.370207] ===>set to N mode
[ 2762.370209] ===========rtl8192se_update_ratr_table: ff005
[ 2762.370216] ===>set to N mode
[ 2882.250195] ===========rtl8192se_update_ratr_table: ff005
[ 2882.250202] ===>set to N mode
[ 3002.280227] ===========rtl8192se_update_ratr_table: ff005
[ 3002.280234] ===>set to N mode
[ 3099.553484] ====================>rx ADDBAREQ from :00:1c:df:88:c2:15
[ 3099.553496] =====>to send ADDBARSP
[ 3122.362553] ===========rtl8192se_update_ratr_table: ff005
[ 3122.362556] ===>set to N mode
[ 3122.365801] ieee80211: ERR! in GetTs(), TID(8) is not valid
[ 3122.365805] ieee80211: can't get TS for TXTS in ieee80211_rx_DELBA()
[ 3158.971841] ====================>rx ADDBAREQ from :00:1c:df:88:c2:15
[ 3158.971860] =====>to send ADDBARSP
[ 3242.370207] ===========rtl8192se_update_ratr_table: ff005
[ 3242.370215] ===>set to N mode
[ 3242.373316] ieee80211: can't get TS for TXTS in ieee80211_rx_DELBA()
[ 3278.706010] ====================>rx ADDBAREQ from :00:1c:df:88:c2:15
[ 3278.706026] =====>to send ADDBARSP
[ 3362.390178] ===========rtl8192se_update_ratr_table: ff005
[ 3362.390186] ===>set to N mode
[ 3362.393242] ieee80211: ERR! in GetTs(), TID(13) is not valid
[ 3362.393250] ieee80211: can't get TS for TXTS in ieee80211_rx_DELBA()
[ 3482.280193] ===========rtl8192se_update_ratr_table: ff005
[ 3482.280200] ===>set to N mode
[ 3602.370205] ===========rtl8192se_update_ratr_table: ff005
[ 3602.370212] ===>set to N mode
[ 3722.390201] ===========rtl8192se_update_ratr_table: ff005
[ 3722.390208] ===>set to N mode
[ 3842.262698] ===========rtl8192se_update_ratr_table: ff005
[ 3842.262705] ===>set to N mode
[ 3962.370182] ===========rtl8192se_update_ratr_table: ff005
[ 3962.370190] ===>set to N mode
[ 4082.370199] ===========rtl8192se_update_ratr_table: ff005
[ 4082.370206] ===>set to N mode
[ 4202.380164] ===========rtl8192se_update_ratr_table: ff005
[ 4202.380172] ===>set to N mode
[ 4322.310225] ===========rtl8192se_update_ratr_table: ff005
[ 4322.310232] ===>set to N mode
[ 4442.292661] ===========rtl8192se_update_ratr_table: ff005
[ 4442.292668] ===>set to N mode
[ 4562.280224] ===========rtl8192se_update_ratr_table: ff005
[ 4562.280231] ===>set to N mode
[ 4682.370205] ===========rtl8192se_update_ratr_table: ff005
[ 4682.370212] ===>set to N mode
[ 4802.390197] ===========rtl8192se_update_ratr_table: ff005
[ 4802.390204] ===>set to N mode
[ 4922.280218] ===========rtl8192se_update_ratr_table: ff005
[ 4922.280225] ===>set to N mode
[ 5042.370199] ===========rtl8192se_update_ratr_table: ff005
[ 5042.370207] ===>set to N mode
[ 5162.380198] ===========rtl8192se_update_ratr_table: ff005
[ 5162.380207] ===>set to N mode
[ 5282.280215] ===========rtl8192se_update_ratr_table: ff005
[ 5282.280232] ===>set to N mode
[ 5402.380208] ===========rtl8192se_update_ratr_table: ff005
[ 5402.380215] ===>set to N mode
[ 5522.370207] ===========rtl8192se_update_ratr_table: ff005
[ 5522.370214] ===>set to N mode
[ 5642.300234] ===========rtl8192se_update_ratr_table: ff005
[ 5642.300241] ===>set to N mode
[ 5762.290164] ===========rtl8192se_update_ratr_table: ff005
[ 5762.290171] ===>set to N mode
[ 5882.390198] ===========rtl8192se_update_ratr_table: ff005
[ 5882.390207] ===>set to N mode
[ 6002.370332] ===========rtl8192se_update_ratr_table: ff005
[ 6002.370340] ===>set to N mode
[ 6122.370200] ===========rtl8192se_update_ratr_table: ff005
[ 6122.370208] ===>set to N mode
[ 6242.370196] ===========rtl8192se_update_ratr_table: ff005
[ 6242.370205] ===>set to N mode
[ 6362.290166] ===========rtl8192se_update_ratr_table: ff005
[ 6362.290174] ===>set to N mode
[ 6482.390197] ===========rtl8192se_update_ratr_table: ff005
[ 6482.390204] ===>set to N mode
[ 6602.280191] ===========rtl8192se_update_ratr_table: ff005
[ 6602.280198] ===>set to N mode
[ 6722.300225] ===========rtl8192se_update_ratr_table: ff005
[ 6722.300232] ===>set to N mode
[ 6842.300191] ===========rtl8192se_update_ratr_table: ff005
[ 6842.300198] ===>set to N mode
[ 6962.370199] ===========rtl8192se_update_ratr_table: ff005
[ 6962.370207] ===>set to N mode
[ 7082.390194] ===========rtl8192se_update_ratr_table: ff005
[ 7082.390201] ===>set to N mode
[ 7202.370195] ===========rtl8192se_update_ratr_table: ff005
[ 7202.370205] ===>set to N mode
[ 7322.320190] ===========rtl8192se_update_ratr_table: ff005
[ 7322.320197] ===>set to N mode
[ 7442.390199] ===========rtl8192se_update_ratr_table: ff005
[ 7442.390206] ===>set to N mode
[ 7562.370197] ===========rtl8192se_update_ratr_table: ff005
[ 7562.370204] ===>set to N mode
[ 7682.290178] ===========rtl8192se_update_ratr_table: ff005
[ 7682.290188] ===>set to N mode
[ 7802.282683] ===========rtl8192se_update_ratr_table: ff005
[ 7802.282690] ===>set to N mode
[ 7922.380185] ===========rtl8192se_update_ratr_table: ff005
[ 7922.380192] ===>set to N mode
[ 8042.262733] ===========rtl8192se_update_ratr_table: ff005
[ 8042.262740] ===>set to N mode
[ 8162.262731] ===========rtl8192se_update_ratr_table: ff005
[ 8162.262740] ===>set to N mode
[ 8282.280224] ===========rtl8192se_update_ratr_table: ff005
[ 8282.280233] ===>set to N mode
[ 8402.370201] ===========rtl8192se_update_ratr_table: ff005
[ 8402.370208] ===>set to N mode
[ 8522.310218] ===========rtl8192se_update_ratr_table: ff005
[ 8522.310225] ===>set to N mode
[ 8642.380205] ===========rtl8192se_update_ratr_table: ff005
[ 8642.380213] ===>set to N mode
[ 8762.262731] ===========rtl8192se_update_ratr_table: ff005
[ 8762.262738] ===>set to N mode
[ 8882.370199] ===========rtl8192se_update_ratr_table: ff005
[ 8882.370207] ===>set to N mode
[ 8891.351937] ====================>rx ADDBAREQ from :00:1c:df:88:c2:15
[ 8891.351949] =====>to send ADDBARSP
[ 9002.370197] ===========rtl8192se_update_ratr_table: ff005
[ 9002.370206] ===>set to N mode
[ 9002.375830] ieee80211: can't get TS for RXTS in ieee80211_rx_DELBA().dsf:00:1c:df:88:c2:15 TID:5
[ 9122.390195] ===========rtl8192se_update_ratr_table: ff005
[ 9122.390204] ===>set to N mode
[ 9207.432852] npviewer.bin[9566]: segfault at f5867054 ip 00000000f61dd033 sp 00000000ff954670 error 4 in libflashplayer.so[f5e3e000+b04000]
[ 9212.370539] ====================>rx ADDBAREQ from :00:1c:df:88:c2:15
[ 9212.370553] =====>to send ADDBARSP
[ 9252.380199] ===========rtl8192se_update_ratr_table: ff005
[ 9252.380206] ===>set to N mode
[ 9252.383736] ieee80211: ERR! in GetTs(), TID(15) is not valid
[ 9252.383747] ieee80211: can't get TS for RXTS in ieee80211_rx_DELBA().dsf:00:1c:df:88:c2:15 TID:15
[ 9254.064706] ====================>rx ADDBAREQ from :00:1c:df:88:c2:15
[ 9254.064714] =====>to send ADDBARSP
[ 9362.390206] ===========rtl8192se_update_ratr_table: ff005
[ 9362.390213] ===>set to N mode
[ 9362.394290] ieee80211: can't get TS for RXTS in ieee80211_rx_DELBA().dsf:00:1c:df:88:c2:15 TID:6
[ 9375.146014] ====================>rx ADDBAREQ from :00:1c:df:88:c2:15
[ 9375.146027] =====>to send ADDBARSP
[ 9482.370207] ===========rtl8192se_update_ratr_table: ff005
[ 9482.370214] ===>set to N mode
[ 9482.373323] ieee80211: can't get TS for RXTS in ieee80211_rx_DELBA().dsf:00:1c:df:88:c2:15 TID:5
[ 9485.100678] ====================>rx ADDBAREQ from :00:1c:df:88:c2:15
[ 9485.100683] =====>to send ADDBARSP
[ 9602.382822] ===========rtl8192se_update_ratr_table: ff005
[ 9602.382829] ===>set to N mode
[ 9602.385454] ieee80211: ERR! in GetTs(), TID(11) is not valid
[ 9602.385465] ieee80211: can't get TS for RXTS in ieee80211_rx_DELBA().dsf:00:1c:df:88:c2:15 TID:11
[ 9602.484819] ====================>rx ADDBAREQ from :00:1c:df:88:c2:15
[ 9602.484834] =====>to send ADDBARSP
[ 9722.380598] ===========rtl8192se_update_ratr_table: ff005
[ 9722.380605] ===>set to N mode
[ 9722.383999] ieee80211: can't get TS for TXTS in ieee80211_rx_DELBA()

By the way it is a Toshiba L505D-GS6000

---

### Post by jcer93705 on 2010-07-31
> **choochoousmc said:**
> Do you have a touchpad?
Mine does this too.
I double touch the pad and then system is ok again.
sometimes finger or sleeve just barely touches it and this takes control away from the mouse

Yes i do actually my touch pad is so sensitive in linux that if i have two fingers hovering above the touch pad by couple mm mouse pointer goes crazy. But when i'm using the computer, it freeze up in a way that i can still move my mouse i try to click something and it wont response unless if i do a right click the menu does pop out but i cant click whats in the menu, i cant click anything. Also my mouse touch pad can detect my palm even if its not touching sometime my pointer would delete some of the words i'm typing. I really have to have my hand high enough from the mouse pad.

---

### Post by jcer93705 on 2010-07-31
> **choochoousmc said:**
> Do you have a touchpad?
Mine does this too.
I double touch the pad and then system is ok again.
sometimes finger or sleeve just barely touches it and this takes control away from the mouse

Also the problem u have my problem is a bit different, when it kindof freeze i cant even use my touch pad. Eventually if i wait it will go back to normal then it would run a bit rough i need to do a system reboot then it works again. 

2 problem i have

1 mouse pad to sensitive and can detect something that is not even touching the mouse pad.

2 Once in a while my pc would go to a point where it seem it is freezed but its not, i just cant click anything only right click will show menu.

---

### Post by sml on 2010-07-31
i have the same freeze problems ..
a) mouse moves
b) can tab around and press enter
c) everything locked otherwise with mouse

occurs on two computers ...
a) macbook 64bit with nvidia chipset & graphics
b) lenovo y650 64bit with nvidia graphics & intel chipset

frequency ... every 4 or 5 hours ... only solution so far is reboot/power-off.

---

### Post by sourchier on 2010-08-09
You have two main problems on your computer.

1. You keep turning off the power button on your computer, rather than doing a graceful shutdown. This is why there is a "EXT4-fs (sda5): orphan cleanup on readonly fs" in your dmesg. You need to run fsck in a read-only mode from the ubuntu live cd.

2. There is a driver error with your wireless. This is why you keep getting messages with your rtl8192se. Also you keep getting problems with the ieee80211. Try updating ubuntu and your bios. If you can't update then try disabling firewire in the bios.

---

