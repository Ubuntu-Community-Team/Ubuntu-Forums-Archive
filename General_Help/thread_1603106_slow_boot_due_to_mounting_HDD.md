---
title: "slow boot due to mounting HDD"
date: 2010-10-22
forum: General Help
---

### Post by ssalman on 2010-10-22
hi,

I've been noticing that my ubuntu 10.04 takes too long to boot lately, and now that I've upgraded to 10.10 and had the same issue, I took few minutes to investigate. from what I understand from the log files, it looks like my hard drive takes too long to mount, actually 40+ seconds to mount... I've been searching all this morning for people on this forum with the same issue, but I couldn't find any posts.

any idea what's going on and how to fix this? below is the section I mentioned above from my messages log:

```
Oct 22 08:43:22 ubuntu kernel: [    2.076608] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Oct 22 08:43:22 ubuntu kernel: [   49.537272] Adding 2096444k swap on /dev/sda8.  Priority:-1 extents:1 across:2096444k
```

---

### Post by uvaio on 2010-10-27
Same issue here

[    7.900968] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   19.467289] udev[468]: starting version 163

Anyone can help please?

---

### Post by MK567 on 2010-10-27
I have the same problem:

Usingu Ubuntu 10.10
Kernel 2.6.35-22

> 
[1.843858] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
 [2.248155] firewire_core: created device fw0: GUID 00023c01510f72cb, S400
[32.006818] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro 
[32.346683] udev[424]: starting version 163


---

### Post by ssalman on 2010-10-28
So I did some more digging using bootchart (see link _[here]("http://dl.dropbox.com/u/2779156/ubuntu-maverick-20101028-1.png")_), and found that mountall takes about 19 sec, which is still long, but not as long as I initial thought (40+ sec). however I think now there is more to this than just the mount, since it seams everything else is taking longer in the bootchart. 

anyone with similar experience?

---

### Post by winstonschmidt on 2010-10-28
Hi,
I have a similar problem (10.4 and 10.10):

```

[    3.871054] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.012130] firewire_core: created device fw0: GUID 007664e900001fd0, S400
[   25.017125] Adding 5653500k swap on /dev/sda5.  Priority:-1 extents:1 across:5653500k 
[   25.044633] udev[400]: starting version 163

```

I'm open for suggestions....

regards,
ws

---

### Post by matson36 on 2010-12-04
Indeed, I have the same problem here...
I hope there will be a solution for this ;)
```

[    1.944682] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts$
[   29.913944] udev[372]: starting version 163

```

---

### Post by Unabletoload on 2010-12-21
same problem!!
```
[    7.157160] usb 1-1.6: new full speed USB device using ehci_hcd and address 4
[    7.326649] ata6: SATA link down (SStatus 0 SControl 300)
[   13.142610] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   23.526700] udev[300]: starting version 163
[   23.740225] Adding 4296700k swap on /dev/sda6.  Priority:-1 extents:1 across:4296700k 
```here 

i'm using maverick and kernel
[CODE ].6.37-020637rc2-generic #201011160905 SMP Tue Nov 16 09:08:47 UTC 2010 x86_64 GNU/Linux
[/CODE]

my lspci -vv

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
    Subsystem: Sony Corporation Device 9071
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device 9071
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 44
    Region 0: Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Region 2: Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at e080 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Sony Corporation Device 9071
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at f600a000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
    Subsystem: Sony Corporation Device 9071
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f6008000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Sony Corporation Device 9071
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 42
    Region 0: Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f4c00000-f5ffffff
    Prefetchable memory behind bridge: 00000000fe900000-00000000feafffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f3800000-f4bfffff
    Prefetchable memory behind bridge: 00000000fe700000-00000000fe8fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: f2400000-f37fffff
    Prefetchable memory behind bridge: 00000000fe500000-00000000fe6fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: f0400000-f23fffff
    Prefetchable memory behind bridge: 00000000fe300000-00000000fe4fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
    Subsystem: Sony Corporation Device 9071
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at f6007000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=32
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
    Subsystem: Sony Corporation Device 9071
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: Sony Corporation Device 9071
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 41
    Region 0: I/O ports at e070 [size=8]
    Region 1: I/O ports at e060 [size=4]
    Region 2: I/O ports at e050 [size=8]
    Region 3: I/O ports at e040 [size=4]
    Region 4: I/O ports at e020 [size=32]
    Region 5: Memory at f6006000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    Subsystem: Sony Corporation Device 9071
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 4
    Region 0: Memory at f6005000 (64-bit, non-prefetchable) [size=256]
    Region 4: I/O ports at e000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
    Subsystem: Sony Corporation Device 9071
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 0: Memory at f6004000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: intel ips
    Kernel modules: intel_ips

02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 43
    Region 0: Memory at f4c00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

03:00.0 SD Host controller: Ricoh Co Ltd Device e822
    Subsystem: Sony Corporation Device 9071
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at f3802000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

03:00.1 System peripheral: Ricoh Co Ltd Device e230
    Subsystem: Sony Corporation Device 9071
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 4
    Region 0: Memory at f3801000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

03:00.4 SD Host controller: Ricoh Co Ltd Device e822
    Subsystem: Sony Corporation Device 9071
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin C routed to IRQ 19
    Region 0: Memory at f3800000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8059 PCI-E Gigabit Ethernet Controller (rev 11)
    Subsystem: Sony Corporation Device 9071
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 40
    Region 0: Memory at f2420000 (64-bit, non-prefetchable) [size=16K]
    Region 2: I/O ports at b000 [size=256]
    Expansion ROM at f2400000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Sony Corporation Device 9071
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Sony Corporation Device 9071
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Sony Corporation Device 9071
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Sony Corporation Device 9071
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Sony Corporation Device 9071
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Sony Corporation Device 9071
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
```

any hint??

---

### Post by &lt;mike&gt; on 2010-12-29
I have a similar problem; I am not sure if it's mounting the fs or starting udev which is taking so long, but if someone could help me find out I'd appreciate it!

dmesg shows:

```

...
[    2.715618] Uniform CD-ROM driver Revision: 3.20
[    2.715783] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.715871] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.715981] ata4: port disabled. ignoring.
[    3.528234] kjournald starting.  Commit interval 5 seconds
[    3.528254] EXT3-fs: mounted filesystem with ordered data mode.
[   50.620215] udev: starting version 151
[   50.829441] lp: driver loaded but no devices found
[   50.917913] acpi device:22: registered as cooling_device2
[   50.918114] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   50.918191] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   51.019969] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   51.061798] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   51.061828] i2c i2c-1: nForce2 SMBus adapter at 0x3000
...

```
(full file attached...)

---

### Post by hhoyt on 2010-12-30
Are you sure it is the mount ? I think mode NULL just means you took the default on fstab.

One thing that can lengthen things is if ureadahead is not working.
If it shows in bootlog above mountall, it should be working ok. Else,
Do you have /var/lib/ureadahead/pack ? If so, delete it:
sudo rm /var/lib/ureadahead/pack and then 
sudo reboot
(force rebuild of the pack file used by ureadahead)

/var/lib/ureadadhead/pack should now be rebuilt if all is ok.

File /etc/init/ureadahead.conf needs to exist. If you delete/rename it, my experience has been a reinstall of ureadahead will not rebuild it.

Anything in /var/log/boot.log ?

Howie

---

### Post by ssalman on 2011-01-14
Thanks Howie! I think you struck the main cause.

after I deleted the ureadahead pack I got a much better boot time
```
[    2.072181] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    5.309136] Adding 2096444k swap on /dev/sda8.  Priority:-1 extents:1 across:2096444k 
[    7.159446] udev[326]: starting version 163
```but after the second reboot the boot time increased once more, but not to the previous very high levels
```
[    2.049643] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   25.729924] udev[317]: starting version 163
```any ideas why ureadahead is not cooperating?

thanks.

---

### Post by noa097 on 2011-01-19
i am suffering from the same problem
```
[    2.013860] fb0: VESA VGA frame buffer device
[    2.261312] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[   17.067186] Adding 538140k swap on /dev/sdb6.  Priority:-1 extents:1 across:538140k 
[   17.570902] udev[458]: starting version 163
```

I deleted the /var/lib/ureadadhead/pack, as hhoyt mentioned, but it did not rebuild after rebooting. Is that a problem?

---

### Post by noa097 on 2011-01-19
i am suffering from the same problem
```
[    2.013860] fb0: VESA VGA frame buffer device
[    2.261312] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[   17.067186] Adding 538140k swap on /dev/sdb6.  Priority:-1 extents:1 across:538140k 
[   17.570902] udev[458]: starting version 163
```

I deleted the /var/lib/ureadadhead/pack, as hhoyt mentioned, but it did not rebuild after rebooting. Is that a problem?

---

### Post by claretsfan on 2011-02-04
Hi all

I've had a similar problem with ureadahead, but it seems to have been solved in post 4 here:

[http://ubuntuforums.org/showthread.php?p=10426741&posted=1#post10426741](http://ubuntuforums.org/showthread.php?p=10426741&posted=1#post10426741)

Hope it helps you too

---

### Post by claretsfan on 2011-02-04
I spoke too soon.  Problem back after a few reboots.

---

### Post by ylam on 2011-05-21
Hi guys,
[FONT=Verdana]
Did a fresh installation of Natty (11.04) and am getting the same problem, except the delay is 5+ minutes (!!). I'm dual-booting with Windows 7. Here's part of the dmesg log: 
  

[/FONT][FONT=Verdana][ 28.989223] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[/FONT]   [FONT=Verdana][ 305.166041] Adding 3178492k swap on /dev/sda6. Priority:-1 extents:1 across:3178492k 
[/FONT]   [FONT=Verdana][ 305.169951] <30>udev[265]: starting version 167
[/FONT]   [FONT=Verdana][ 305.268165] lp: driver loaded but no devices found
[/FONT]   [FONT=Verdana][ 305.403739] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr


Any ideas on what else to try? Also, besides the delay between secs 28 and 305, is it normal to have it remount afterwards??[/FONT]     [FONT=Verdana]
[/FONT] 
Thanks!

---

### Post by uvaio on 2011-05-22
upgrade to Natty did not change anything for me as well

[    5.457445] generic-usb 0003:05AC:820B.0007: input,hidraw6: USB HID v1.11 Mouse [HID 05ac:820b] on usb-0000:00:06.0-6.3/input0
[    7.847261] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   22.909247] <30>udev[432]: starting version 167
[   22.938942] lp: driver loaded but no devices found

---

