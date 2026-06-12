---
title: "How to backup gnome gui in ubuntu server"
date: 2012-08-24
forum: General Help
---

### Post by rxlord on 2012-08-24
Hi alli installed ubuntu server on my computer then i installed gui in it using command :- sudo apt-get install ubuntu-desktopnow i want to re-install ubuntu server.i just wanna know is there any way to backup the gui.it downloads 400mb files and my net is slow.so i wanna make a backup of the gui so that i dont have to download the gui files again after i re-install ubuntu-server.

---

### Post by Cheesemill on 2012-08-24
If you are going to install Ubuntu Server and then install the ubuntu-desktop package on it you may as well just install the desktop version of Ubuntu to start with, you end up with exactly the same system.

But as to your question, you should be able to back up the .deb files found in /var/apt/cache/ and then restore them to the new installation before installing ubuntu-desktop.

---

### Post by rxlord on 2012-08-25
Ok i made a backup of /var/cache/apt/ folder in my flash drive and i have re-installed ubuntu server and i have copied the backed up folder & files to /var/cache/apt folder.now what command i should use to install ubuntu desktopwithout downloading the files again. i think if i use apt-get install ubuntu-desktop then it will    re-download and replace the existing files

---

### Post by Cheesemill on 2012-08-25
```
sudo apt-get install ubuntu-desktop
```

---

### Post by rxlord on 2012-08-25
hey whenever i enter my pendrive in which the backed up files are it shows
Assuming drive cache:write trough
no caching mode page present
assuming drive cache:write trough
no caching mode page present 
assuming drive cache: write trough
and its stuck here only.
plz help

---

### Post by Rexilion on 2012-08-25
Does

```
fdisk -l
```

show a new sd* device? Without GUI, you have to mount device with the 'mount' command and unmount with the 'umount' (sic) command.

---

### Post by rxlord on 2012-08-25
did all the things successfully.
Last question
whenever i click on the wireless icon on top it doesnt shows any wireless networks.

---

### Post by Rexilion on 2012-08-25
Here we go again :) . Please post the output of:

```
lspci -v
dmesg
nm-tool
ls /lib/firmware
```

at [www.pastebin.com](www.pastebin.com) and post the link here please.

---

### Post by rxlord on 2012-08-25
i have solved the usb error
i have installed gui in ubuntu server
now when i click on wireless icon on above no networks show up on it.

---

### Post by Rexilion on 2012-08-25
> **rxlord said:**
> i have solved the usb error
i have installed gui in ubuntu server
now when i click on wireless icon on above no networks show up on it.

Yes, and the above mentioned commands will aid us (me) in diagnosing your problem.

---

### Post by rxlord on 2012-08-26
result of 
lspci -v:-
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Lenovo Device 3800
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=09 <?>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 3801
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d4200000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at d4300000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Lenovo Device 3801
    Flags: bus master, fast devsel, latency 0
    Memory at d4280000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Lenovo Device 3837
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at d4340000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d2000000-d3ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo Device 3803
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: d4000000-d40fffff
    Prefetchable memory behind bridge: 0000000084400000-00000000845fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo Device 3804
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 84000000-841fffff
    Prefetchable memory behind bridge: 0000000084200000-00000000843fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo Device 3805
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Lenovo Device 3807
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Lenovo Device 3808
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Lenovo Device 3809
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Lenovo Device 380a
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 380b
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d4544000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=09, sec-latency=32
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d4100000-d41fffff
    Prefetchable memory behind bridge: 0000000080000000-0000000083ffffff
    Capabilities: [50] Subsystem: Lenovo Device 380c

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Lenovo Device 380d
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02) (prog-if 80 [Master])
    Subsystem: Lenovo Device 3835
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 18b0 [size=16]
    Capabilities: [70] Power Management version 2
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Lenovo Device 380f
    Flags: medium devsel, IRQ 10
    I/O ports at 18c0 [size=32]
    Kernel modules: i2c-i801

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at d4000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-19-d2-ff-ff-ad-5a-57
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Lenovo Device 3827
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at 3000 [size=256]
    Memory at d4100000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
    Subsystem: Lenovo Device 3828
    Flags: bus master, medium devsel, latency 168, IRQ 16
    Memory at 88000000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
    Memory window 0: 80000000-83fff000 (prefetchable)
    Memory window 1: 8c000000-8ffff000
    I/O window 0: 00003800-000038ff
    I/O window 1: 00003400-000034ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
    Subsystem: Lenovo Device 3829
    Flags: bus master, medium devsel, latency 64, IRQ 22
    Memory at d4100800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

05:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
    Subsystem: Lenovo Device 382a
    Flags: bus master, medium devsel, latency 64, IRQ 22
    Memory at d4100400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

05:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
    Subsystem: Lenovo Device 382c
    Flags: medium devsel, IRQ 23
    Memory at d4101400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: r592
    Kernel modules: r592

05:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
    Subsystem: Lenovo Device 382d
    Flags: medium devsel, IRQ 23
    Memory at d4101800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: r852
    Kernel modules: r852

```
rsult of nm-tool
```

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:02:3F:EB:93:C3

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             unmanaged
  Default:           no
  HW Address:        00:19:D2:AD:5A:57

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


```result of ls /lib/firmware
```
3.2.0-23-generic-pae         matrox
3com                 mrvl
acenic                 mts_cdma.fw
adaptec                 mts_edge.fw
advansys             mts_gsm.fw
agere_ap_fw.bin             mts_mt9234mu.fw
agere_sta_fw.bin         mts_mt9234zba.fw
aic94xx-seq.fw             mwl8335_duplex.fw
ar3k                 mwl8k
ar7010_1_1.fw             myri10ge_ethp_z8e.dat
ar7010.fw             myri10ge_eth_z8e.dat
ar9170-1.fw             myri10ge_rss_ethp_z8e.dat
ar9170-2.fw             myri10ge_rss_eth_z8e.dat
ar9170.fw             myricom
ar9271.fw             NPE-B
asihpi                 NPE-C
ath3k-1.fw             ositech
ath6k                 phanfw.bin
atmel_at76c502_3com.bin      ql2100_fw.bin
atmel_at76c502.bin         ql2200_fw.bin
atmel_at76c502d.bin         ql2300_fw.bin
atmel_at76c502e.bin         ql2322_fw.bin
atmel_at76c504_2958.bin      ql2400_fw.bin
atmel_at76c504a_2958.bin     ql2500_fw.bin
atmel_at76c504.bin         qlogic
atmel_at76c506.bin         r128
atmsar11.fw             radeon
av7110                 rt2561.bin
bnx2                 rt2561s.bin
bnx2x                 rt2661.bin
brcm                 rt2860.bin
carl9170-1.fw             rt2870.bin
cis                 rt3070.bin
cpia2                 rt3071.bin
cxgb3                 rt3090.bin
cxgb4                 rt73.bin
dabusb                 RTL8192E
dsp56k                 RTL8192SE
dvb-fe-xc5000-1.6.114.fw     rtl_nic
dvb-usb-dib0700-1.20.fw      rtlwifi
dvb-usb-terratec-h5-drxk.fw  s2250.fw
e100                 s2250_loader.fw
ea                 sb16
edgeport             scripts
emi26                 slicoss
emi62                 sun
ene-ub6250             sxg
ess                 TDA7706_OM_v2.5.1_boot.txt
f2255usb.bin             TDA7706_OM_v3.0.2_boot.txt
GPL-3                 tehuti
hp                 ti_3410.fw
htc_7010.fw             ti_5052.fw
htc_9271.fw             ti-connectivity
i2400m-fw-usb-1.4.sbcf         tigon
i2400m-fw-usb-1.5.sbcf         tlg2300_firmware.bin
i6050-fw-usb-1.5.sbcf         tr_smctr.bin
intelliport2.bin         ttusb-budget
ipw2100-1.3.fw             ueagle-atm
ipw2100-1.3-i.fw         usbdux
ipw2100-1.3-p.fw         usbduxfast_firmware.bin
ipw2200-bss.fw             usbdux_firmware.bin
ipw2200-ibss.fw             usbduxsigma_firmware.bin
ipw2200-sniffer.fw         v4l-cx231xx-avcore-01.fw
isci                 v4l-cx23418-apu.fw
iwlwifi-1000-5.ucode         v4l-cx23418-cpu.fw
iwlwifi-100-5.ucode         v4l-cx23418-dig.fw
iwlwifi-105-6.ucode         v4l-cx2341x-dec.fw
iwlwifi-135-6.ucode         v4l-cx2341x-enc.fw
iwlwifi-2000-6.ucode         v4l-cx2341x-init.mpg
iwlwifi-2030-6.ucode         v4l-cx23885-avcore-01.fw
iwlwifi-3945-2.ucode         v4l-cx23885-enc.fw
iwlwifi-4965-2.ucode         v4l-cx25840.fw
iwlwifi-5000-5.ucode         v4l-pvrusb2-24xxx-01.fw
iwlwifi-5150-2.ucode         v4l-pvrusb2-29xxx-01.fw
iwlwifi-6000-4.ucode         vicam
iwlwifi-6000g2a-5.ucode      vntwusb.fw
iwlwifi-6000g2b-6.ucode      vxge
iwlwifi-6050-5.ucode         WHENCE.ubuntu
kaweth                 whiteheat.fw
keyspan                 whiteheat_loader.fw
keyspan_pda             yam
korg                 yamaha
lbtf_usb.bin             zd1201-ap.fw
lgs8g75.fw             zd1201.fw
libertas             zd1211

```result of dmesg
```
[    0.577087] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    0.577107] pci 0000:00:1c.1:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.577125] pci 0000:00:1c.1:   bridge window [mem 0x84400000-0x845fffff 64bit pref]
[    0.577150] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.577164] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.577183] pci 0000:00:1c.2:   bridge window [mem 0x84000000-0x841fffff]
[    0.577202] pci 0000:00:1c.2:   bridge window [mem 0x84200000-0x843fffff 64bit pref]
[    0.577236] pci 0000:05:04.0: BAR 0: assigned [mem 0x88000000-0x88000fff]
[    0.577256] pci 0000:05:04.0: BAR 0: set to [mem 0x88000000-0x88000fff] (PCI address [0x88000000-0x88000fff])
[    0.577280] pci 0000:05:04.0: BAR 16: assigned [mem 0x8c000000-0x8fffffff]
[    0.577296] pci 0000:05:04.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.577313] pci 0000:05:04.0: BAR 14: assigned [io  0x3400-0x34ff]
[    0.577327] pci 0000:05:04.0: BAR 13: assigned [io  0x3800-0x38ff]
[    0.577340] pci 0000:05:04.0: CardBus bridge to [bus 06-09]
[    0.577353] pci 0000:05:04.0:   bridge window [io  0x3800-0x38ff]
[    0.577371] pci 0000:05:04.0:   bridge window [io  0x3400-0x34ff]
[    0.577389] pci 0000:05:04.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.577410] pci 0000:05:04.0:   bridge window [mem 0x8c000000-0x8fffffff]
[    0.577428] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.577443] pci 0000:00:1e.0:   bridge window [io  0x3000-0x3fff]
[    0.577462] pci 0000:00:1e.0:   bridge window [mem 0xd4100000-0xd41fffff]
[    0.577480] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.577543] pci 0000:00:1c.0: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.577563] pci 0000:00:1c.0: setting latency timer to 64
[    0.577590] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.577608] pci 0000:00:1c.1: setting latency timer to 64
[    0.577633] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.577651] pci 0000:00:1c.2: setting latency timer to 64
[    0.577666] pci 0000:00:1e.0: enabling device (0004 -> 0007)
[    0.577686] pci 0000:00:1e.0: setting latency timer to 64
[    0.577703] pci 0000:05:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.577724] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.577731] pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]
[    0.577739] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.577746] pci_bus 0000:02: resource 1 [mem 0xd2000000-0xd3ffffff]
[    0.577754] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.577762] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
[    0.577768] pci_bus 0000:03: resource 1 [mem 0xd4000000-0xd40fffff]
[    0.577776] pci_bus 0000:03: resource 2 [mem 0x84400000-0x845fffff 64bit pref]
[    0.577783] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    0.577790] pci_bus 0000:04: resource 1 [mem 0x84000000-0x841fffff]
[    0.577797] pci_bus 0000:04: resource 2 [mem 0x84200000-0x843fffff 64bit pref]
[    0.577805] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.577812] pci_bus 0000:05: resource 1 [mem 0xd4100000-0xd41fffff]
[    0.577819] pci_bus 0000:05: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.577826] pci_bus 0000:05: resource 4 [io  0x0000-0xffff]
[    0.577833] pci_bus 0000:05: resource 5 [mem 0x00000000-0xfffffffff]
[    0.577840] pci_bus 0000:06: resource 0 [io  0x3800-0x38ff]
[    0.577847] pci_bus 0000:06: resource 1 [io  0x3400-0x34ff]
[    0.577854] pci_bus 0000:06: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.577861] pci_bus 0000:06: resource 3 [mem 0x8c000000-0x8fffffff]
[    0.577970] NET: Registered protocol family 2
[    0.578172] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.578799] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.579698] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.580190] TCP: Hash tables configured (established 131072 bind 65536)
[    0.580204] TCP reno registered
[    0.580218] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.580244] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.580440] NET: Registered protocol family 1
[    0.580490] pci 0000:00:02.0: Boot video device
[    0.580563] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.580601] pci 0000:00:1d.0: PCI INT A disabled
[    0.580626] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.580662] pci 0000:00:1d.1: PCI INT B disabled
[    0.580686] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.580721] pci 0000:00:1d.2: PCI INT C disabled
[    0.580745] pci 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.580780] pci 0000:00:1d.3: PCI INT D disabled
[    0.580807] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.580871] pci 0000:00:1d.7: PCI INT A disabled
[    0.580932] PCI: CLS mismatch (64 != 32), using 64 bytes
[    0.580958] Simple Boot Flag at 0x36 set to 0x1
[    0.581860] audit: initializing netlink socket (disabled)
[    0.581889] type=2000 audit(1345986236.576:1): initialized
[    0.651472] highmem bounce pool size: 64 pages
[    0.651496] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.668859] VFS: Disk quotas dquot_6.5.2
[    0.669063] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.670683] fuse init (API version 7.17)
[    0.670976] msgmni has been set to 1686
[    0.671860] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.671947] io scheduler noop registered
[    0.671960] io scheduler deadline registered
[    0.671987] io scheduler cfq registered (default)
[    0.672361] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.672465] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.672628] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.672722] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.672882] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.672976] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.673210] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.673291] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.673497] intel_idle: MWAIT substates: 0x22220
[    0.673503] intel_idle: does not run on family 6 model 15
[    0.688056] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.704081] ACPI: AC Adapter [ACAD] (off-line)
[    0.704392] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.704450] ACPI: Lid Switch [LID0]
[    0.704588] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.704611] ACPI: Power Button [PWRB]
[    0.704743] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.704763] ACPI: Sleep Button [SLPB]
[    0.704922] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.704943] ACPI: Power Button [PWRF]
[    0.720327] Monitor-Mwait will be used to enter C-1 state
[    0.724702] Monitor-Mwait will be used to enter C-2 state
[    0.725485] Monitor-Mwait will be used to enter C-3 state
[    0.725504] Marking TSC unstable due to TSC halts in idle
[    0.725544] ACPI: acpi_idle registered with cpuidle
[    0.824165] thermal LNXTHERM:00: registered as thermal_zone0
[    0.824187] ACPI: Thermal Zone [TZ00] (34 C)
[    0.824290] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.824331] ACPI: Battery Slot [BAT1] (battery present)
[    0.824419] ERST: Table is not found!
[    0.824429] GHES: HEST is not enabled!
[    0.824671] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.825157] isapnp: Scanning for PnP cards...
[    1.007545] Freeing initrd memory: 13796k freed
[    1.080983] ACPI: Battery Slot [BAT1] (battery present)
[    1.180108] isapnp: No Plug & Play device found
[    1.237279] Linux agpgart interface v0.103
[    1.237558] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    1.237774] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    1.239081] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.239363] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.244063] brd: module loaded
[    1.246485] loop: module loaded
[    1.246975] ata_piix 0000:00:1f.2: version 2.13
[    1.247006] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.247028] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.400056] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.400941] scsi0 : ata_piix
[    1.401195] scsi1 : ata_piix
[    1.402967] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    1.402985] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    1.404195] Fixed MDIO Bus: probed
[    1.404269] tun: Universal TUN/TAP device driver, 1.6
[    1.404282] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.404445] PPP generic driver version 2.4.2
[    1.404760] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.404813] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.404856] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.404866] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.405023] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.405071] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.405101] ehci_hcd 0000:00:1d.7: debug port 1
[    1.409004] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.409044] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd4544000
[    1.424038] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.424411] hub 1-0:1.0: USB hub found
[    1.424430] hub 1-0:1.0: 8 ports detected
[    1.424673] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.424723] uhci_hcd: USB Universal Host Controller Interface driver
[    1.424774] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.424800] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.424809] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.424943] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.424999] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.425374] hub 2-0:1.0: USB hub found
[    1.425393] hub 2-0:1.0: 2 ports detected
[    1.425589] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.425615] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.425624] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.425769] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.425846] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.426209] hub 3-0:1.0: USB hub found
[    1.426227] hub 3-0:1.0: 2 ports detected
[    1.426416] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.426442] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.426451] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.426590] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.426671] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.427033] hub 4-0:1.0: USB hub found
[    1.427051] hub 4-0:1.0: 2 ports detected
[    1.427246] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.427272] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.427281] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.427419] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.427497] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.427863] hub 5-0:1.0: USB hub found
[    1.427881] hub 5-0:1.0: 2 ports detected
[    1.428243] usbcore: registered new interface driver libusual
[    1.428413] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.434755] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.435086] mousedev: PS/2 mouse device common for all mice
[    1.556590] rtc_cmos 00:08: RTC can wake from S4
[    1.556836] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.556893] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.557057] device-mapper: uevent: version 1.0.3
[    1.557275] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.557389] EISA: Probing bus 0 at eisa.0
[    1.557408] Cannot allocate resource for EISA slot 1
[    1.557421] Cannot allocate resource for EISA slot 2
[    1.557433] Cannot allocate resource for EISA slot 3
[    1.557444] Cannot allocate resource for EISA slot 4
[    1.557456] Cannot allocate resource for EISA slot 5
[    1.557490] EISA: Detected 0 cards.
[    1.557518] cpufreq-nforce2: No nForce2 chipset.
[    1.557710] cpuidle: using governor ladder
[    1.958449] i8042: Can't write CTR while closing KBD port
[    1.958664] cpuidle: using governor menu
[    1.958680] EFI Variables Facility v0.08 2004-May-17
[    1.959450] TCP cubic registered
[    1.959809] NET: Registered protocol family 10
[    1.960945] ata2.00: ATAPI: MATSHITADVD-RAM UJ-85JS, FYX4, max UDMA/66
[    1.960965] ata2.00: limited to UDMA/33 due to 40-wire cable
[    1.961126] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC70P, max UDMA/100
[    1.961142] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.962652] NET: Registered protocol family 17
[    1.962701] Registering the dns_resolver key type
[    1.962757] Using IPI No-Shortcut mode
[    1.963013] PM: Hibernation image not present or could not be loaded.
[    1.963042] registered taskstats version 1
[    1.985708]   Magic number: 8:856:79
[    2.855340] rtc_cmos 00:08: setting system clock to 2012-08-26 13:03:58 UTC (1345986238)
[    2.855435] i8042: Can't reactivate KBD port
[    2.856654] ata1.00: configured for UDMA/100
[    2.856856] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.856864] EDD information not available.
[    2.856897] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[    2.857116] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.857194] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.857214] sd 0:0:0:0: [sda] Write Protect is off
[    2.857224] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.857279] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.864500] ata2.00: configured for UDMA/33
[    2.867206] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-85JS  FYX4 PQ: 0 ANSI: 5
[    2.869568] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    2.869586] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.869879] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.870034] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.886855]  sda: sda1 sda2 sda3 < sda5 >
[    2.887793] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.887923] Freeing unused kernel memory: 740k freed
[    2.888364] Write protecting the kernel text: 5828k
[    2.888400] Write protecting the kernel read-only data: 2376k
[    2.888406] NX-protecting the kernel data: 4412k
[    2.912314] udevd[95]: starting version 175
[    3.045105] sdhci: Secure Digital Host Controller Interface driver
[    3.045118] sdhci: Copyright(c) Pierre Ossman
[    3.045527] sdhci-pci 0000:05:06.1: SDHCI controller found [1180:0822] (rev 19)
[    3.045549] sdhci-pci 0000:05:06.1: enabling device (0000 -> 0002)
[    3.045577] sdhci-pci 0000:05:06.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.046014] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.046615] sdhci-pci 0000:05:06.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    3.046634] sdhci-pci 0000:05:06.1: setting latency timer to 64
[    3.046665] mmc0: no vmmc regulator found
[    3.047704] Registered led device: mmc0::
[    3.068903] mmc0: SDHCI controller on PCI [0000:05:06.1] using DMA
[    3.068949] 8139cp 0000:05:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.069036] firewire_ohci 0000:05:06.0: enabling device (0000 -> 0002)
[    3.069054] firewire_ohci 0000:05:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.069070] firewire_ohci 0000:05:06.0: setting latency timer to 64
[    3.069639] 8139too: 8139too Fast Ethernet driver 0.9.28
[    3.132126] firewire_ohci: Added fw-ohci device 0000:05:06.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    3.132272] 8139too 0000:05:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.132317] 8139too 0000:05:01.0: setting latency timer to 64
[    3.133913] 8139too 0000:05:01.0: eth0: RealTek RTL8139 at 0x3000, 00:02:3f:eb:93:c3, IRQ 21
[    3.177277] usb 1-4: new high-speed USB device number 3 using ehci_hcd
[    3.386112] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    3.632390] firewire_core: created device fw0: GUID 00023f72a6400310, S400
[    3.820092] usb 1-6: new high-speed USB device number 4 using ehci_hcd
[    4.200065] usb 2-2: new full-speed USB device number 2 using uhci_hcd
[   25.284158] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.312475] udevd[442]: starting version 175
[   25.348683] lp: driver loaded but no devices found
[   25.387080] wmi: Mapper loaded
[   25.449378] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   25.468845] input: Ideapad extra buttons as /devices/platform/ideapad/input/input4
[   25.507958] intel_rng: FWH not detected
[   25.536142] leds_ss4200: no LED devices found
[   25.546891] cfg80211: Calling CRDA to update world regulatory domain
[   25.604638] r592 0000:05:06.2: enabling device (0000 -> 0002)
[   25.604652] r592 0000:05:06.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[   25.604664] r592 0000:05:06.2: setting latency timer to 64
[   25.608514] r592: driver successfully loaded
[   25.609630] yenta_cardbus 0000:05:04.0: CardBus bridge found [17aa:3828]
[   25.609661] yenta_cardbus 0000:05:04.0: Using CSCINT to route CSC interrupts to PCI
[   25.609665] yenta_cardbus 0000:05:04.0: Routing CardBus interrupts to PCI
[   25.609673] yenta_cardbus 0000:05:04.0: TI: mfunc 0x01111c12, devctl 0x44
[   25.610062] Bluetooth: Core ver 2.16
[   25.610133] NET: Registered protocol family 31
[   25.610136] Bluetooth: HCI device and connection manager initialized
[   25.610141] Bluetooth: HCI socket layer initialized
[   25.610144] Bluetooth: L2CAP socket layer initialized
[   25.610152] Bluetooth: SCO socket layer initialized
[   25.610620] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   25.635132] Linux video capture interface: v2.00
[   25.636226] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b008)
[   25.636524] usbcore: registered new interface driver btusb
[   25.636630] acpi device:05: registered as cooling_device2
[   25.636790] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input5
[   25.638182] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   25.644317] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input6
[   25.644506] usbcore: registered new interface driver uvcvideo
[   25.644510] USB Video Class driver (1.1.1)
[   25.647522] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   25.647526] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   25.647626] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   25.647643] iwl3945 0000:03:00.0: setting latency timer to 64
[   25.648570] ideapad_laptop: timeout in read_ec_cmd
[   25.701634] [drm] Initialized drm 1.1.0 20060810
[   25.703896] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   25.703903] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   25.704155] iwl3945 0000:03:00.0: irq 43 for MSI/MSI-X
[   25.715604] Registered led device: phy0-led
[   25.715653] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   25.732211] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.732220] i915 0000:00:02.0: setting latency timer to 64
[   25.734776] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   25.790919] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   25.790924] [drm] Driver supports precise vblank timestamp query.
[   25.845456] yenta_cardbus 0000:05:04.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   25.845463] yenta_cardbus 0000:05:04.0: Socket status: 30000006
[   25.845469] pci_bus 0000:05: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   25.847263] yenta_cardbus 0000:05:04.0: pcmcia: parent PCI bridge window: [io  0x3000-0x3fff]
[   25.847269] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff
[   25.854799] yenta_cardbus 0000:05:04.0: pcmcia: parent PCI bridge window: [mem 0xd4100000-0xd41fffff]
[   25.854806] pcmcia_socket pcmcia_socket0: cs: memory probe 0xd4100000-0xd41fffff: excluding 0xd4100000-0xd410ffff
[   25.854830] yenta_cardbus 0000:05:04.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
[   25.854835] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
[   25.859357] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.859362] Bluetooth: BNEP filters: protocol multicast
[   25.863328] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   25.865038] Bluetooth: RFCOMM TTY layer initialized
[   25.865045] Bluetooth: RFCOMM socket layer initialized
[   25.865048] Bluetooth: RFCOMM ver 1.11
[   25.976657] r852 0000:05:06.3: enabling device (0000 -> 0002)
[   25.976671] r852 0000:05:06.3: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[   25.976682] r852 0000:05:06.3: setting latency timer to 64
[   25.979792] r852: Non dma capable device detected, dma disabled
[   25.979811] r852: driver loaded successfully
[   25.981001] ppdev: user-space parallel port driver
[   25.999474] type=1400 audit(1345966462.508:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=716 comm="apparmor_parser"
[   26.000195] type=1400 audit(1345966462.512:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=716 comm="apparmor_parser"
[   26.000537] type=1400 audit(1345966462.512:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=716 comm="apparmor_parser"
[   26.029145] type=1400 audit(1345966462.540:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=731 comm="apparmor_parser"
[   26.029885] type=1400 audit(1345966462.540:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=731 comm="apparmor_parser"
[   26.206939] [drm] initialized overlay support
[   26.223783] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   26.223790] cfg80211: World regulatory domain updated:
[   26.223793] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   26.223797] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.223801] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.223805] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.223855] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.223859] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.269781] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   26.271898] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   26.272798] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   26.273513] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   26.274301] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xfffff
[   26.274347] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   26.274392] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   26.274432] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   26.357654] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   26.369670] fbcon: inteldrmfb (fb0) is primary device
[   26.428181] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.604238] Console: switching to colour frame buffer device 160x50
[   26.609818] fb0: inteldrmfb frame buffer device
[   26.609820] drm: registered panic notifier
[   26.609892] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   26.609964] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   26.610132] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   26.610175] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   26.649876] hda_codec: ALC262: BIOS auto-probing.
[   26.659993] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   26.660360] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   28.792266] wlan0: authenticate with 00:23:f8:36:4a:bf (try 1)
[   28.794199] wlan0: authenticated
[   28.797730] wlan0: associate with 00:23:f8:36:4a:bf (try 1)
[   28.801252] wlan0: RX AssocResp from 00:23:f8:36:4a:bf (capab=0x431 status=0 aid=1)
[   28.801260] wlan0: associated
[   28.803147] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   39.424055] wlan0: no IPv6 routers present
[   52.201483] init: failsafe main process (778) killed by TERM signal
[   52.291243] type=1400 audit(1345966488.800:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1144 comm="apparmor_parser"
[   52.291864] type=1400 audit(1345966488.800:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1144 comm="apparmor_parser"
[   52.292291] type=1400 audit(1345966488.804:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1144 comm="apparmor_parser"
[   52.294576] type=1400 audit(1345966488.804:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1143 comm="apparmor_parser"
[   52.310097] 8139too 0000:05:01.0: eth0: link down
[   52.310450] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.311359] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.314431] type=1400 audit(1345966488.824:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1145 comm="apparmor_parser"
[   52.315992] type=1400 audit(1345966488.824:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/libvirt/virt-aa-helper" pid=1147 comm="apparmor_parser"
[   52.324324] type=1400 audit(1345966488.836:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=1145 comm="apparmor_parser"
[   52.325611] type=1400 audit(1345966488.836:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1149 comm="apparmor_parser"
[   52.326050] type=1400 audit(1345966488.836:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=1145 comm="apparmor_parser"
[   52.326361] type=1400 audit(1345966488.836:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1149 comm="apparmor_parser"
[   52.827757] Bridge firewalling registered
[   52.899664] ip_tables: (C) 2000-2006 Netfilter Core Team
[   52.947861] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   52.972406] ADDRCONF(NETDEV_UP): virbr0: link is not ready
[   53.600118] init: plymouth-upstart-bridge main process (670) killed by TERM signal
[   53.942493] postgres (1475): /proc/1475/oom_adj is deprecated, please use /proc/1475/oom_score_adj instead.
[   54.146522] Ebtables v2.0 registered
[   54.169390] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   55.356804] init: anacron main process (1239) killed by TERM signal
[   57.841479] init: plymouth-stop pre-start process (2001) terminated with status 1
[   83.656165] usb 4-1: new low-speed USB device number 2 using uhci_hcd
[   83.973060] input: 2.4G RX as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input9
[   83.973284] generic-usb 0003:04F3:00A4.0001: input,hidraw0: USB HID v1.10 Keyboard [2.4G RX] on usb-0000:00:1d.2-1/input0
[   83.973311] usbcore: registered new interface driver usbhid
[   83.973314] usbhid: USB HID core driver
[   91.656215] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input10
```

---

### Post by Rexilion on 2012-08-26
I see in your dmesg output:

> [   28.792266] wlan0: authenticate with 00:23:f8:36:4a:bf (try 1)
[   28.794199] wlan0: authenticated
[   28.797730] wlan0: associate with 00:23:f8:36:4a:bf (try 1)
[   28.801252] wlan0: RX AssocResp from 00:23:f8:36:4a:bf (capab=0x431 status=0 aid=1)
[   28.801260] wlan0: associated

So your wireless works properly. Since it succesfully associates.

I see in your nm-tool output:

> - Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             unmanaged

Network-manager is not touching it since you configured the card elsewhere in the system, hence network-manager ignores it.

I guess you need to look at /etc/network/interfaces ?

---

### Post by rxlord on 2012-08-26
what i have to look at network/interfaces 
im new just installed ubuntu this week
i dont know anything about ubuntu

---

### Post by rxlord on 2012-08-26
i solved the wireless networks not showing up problem.
and now i am posting the solution here :-
to make wirelss networks show up in wireless icon on to just type in terminal
sudo nano /etc/network/interfaces        and comment all the lines under " # The primary network interface "
like this 
```
 # The primary network interface
#auto wlan0
#iface wlan0 inet dhcp
    # wireless-* options are implemented by the wireless-tools package
#    wireless-mode managed
#    wireless-essid wireless SSID
#    wireless-key1 wireless password 
```

thanks for the ubuntu community to help 
the best communitu thumbs up for you :D
i feel like a rockstart :guitar:

---

