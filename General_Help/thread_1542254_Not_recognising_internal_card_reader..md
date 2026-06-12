---
title: "Not recognising internal card reader."
date: 2010-07-30
forum: General Help
---

### Post by ukblacknight on 2010-07-30
My girlfriends laptop (Acer Aspire 5536) has an internal memory card slot, however Ubuntu doesn't seem to be recognising it.

```
tom@maria-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 005: ID 0bda:0159 Realtek Semiconductor Corp. **
Bus 002 Device 002: ID 04f2:b044 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The entry in bold is the memory card reader (lsusb  -v confirms it).  However, there is no entry for the device in fdisk:

```
tom@maria-laptop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1e325cea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275       50881   398460195    7  HPFS/NTFS
/dev/sda3           50882       60801    79682369+   5  Extended
/dev/sda5           50882       51005      995998+  82  Linux swap / Solaris
/dev/sda6           51006       60801    78686338+  83  Linux

```

I **do** have a card plugged in, so idealy it should be auto-mounting the device.  The reader doesn't appear in the disk-utility either.

Any ideas?

Ubuntu 10.04 x64
Acer Aspire 5536

---

### Post by dino99 on 2010-07-30
check this chipset by installing (with synaptic): nictools-nopci and nictools-pci

sudo update-usbids && sudo update-pciids

[http://ubuntuforums.org/showthread.php?t=1083591](http://ubuntuforums.org/showthread.php?t=1083591)

---

### Post by ukblacknight on 2010-07-30
Hasn't seem to have worked I'm afraid.  Maybe this will help a bit:

```
tom@maria-laptop:~$ dmesg | tail -100
[   19.223478] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.550612] EDAC amd64_edac:  Ver: 3.2.0 Jul  5 2010
[   19.550690] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   19.550700] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   19.550702]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   19.550703]  (Note that use of the override may cause unknown side effects.)
[   19.550713] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   19.557863] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8040, revision 0
[   19.564493] acpi device:23: registered as cooling_device2
[   19.564840] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:20/LNXVIDEO:01/input/input6
[   19.564911] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[   19.753157] ath9k 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.753172] ath9k 0000:06:00.0: setting latency timer to 64
[   19.757767] vga16fb: initializing
[   19.757773] vga16fb: mapped to 0xffff8800000a0000
[   19.757852] fb0: VGA16 VGA frame buffer device
[   19.797938] Linux video capture interface: v2.00
[   19.813229] uvcvideo: Found UVC 1.00 device CNF7017 (04f2:b044)
[   19.870119] input: CNF7017 as /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/input/input7
[   19.870186] usbcore: registered new interface driver uvcvideo
[   19.870190] USB Video Class driver (v0.1.0)
[   19.955307] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa44000
[   20.018914] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   20.187350] ath: EEPROM regdomain: 0x65
[   20.187352] ath: EEPROM indicates we should expect a direct regpair map
[   20.187357] ath: Country alpha2 being used: 00
[   20.187359] ath: Regpair used: 0x65
[   20.299759] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   20.299766] Disabling lock debugging due to kernel taint
[   20.376156] [fglrx] Maximum main memory to use for locked dma buffers: 3550 MBytes.
[   20.376185] [fglrx]   vendor: 1002 device: 9612 count: 1
[   20.376541] [fglrx] ioport: bar 1, base 0x9000, size: 0x100
[   20.376566] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   20.376572] pci 0000:01:05.0: setting latency timer to 64
[   20.376935] [fglrx] Kernel PAT support is enabled
[   20.376970] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors
[   20.389546] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   20.390436] Registered led device: ath9k-phy0::radio
[   20.390459] Registered led device: ath9k-phy0::assoc
[   20.390478] Registered led device: ath9k-phy0::tx
[   20.390497] Registered led device: ath9k-phy0::rx
[   20.390511] phy0: Atheros AR9280 MAC/BB Rev:2 AR5133 RF Rev:d0: mem=0xffffc90001940000, irq=17
[   20.542375] Console: switching to colour frame buffer device 80x30
[   20.649819] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[   20.649893] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[   20.649906] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.886716] hda_codec: ALC888: BIOS auto-probing.
[   20.888544] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input9
[   20.908208] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   20.908272] HDA Intel 0000:01:05.1: setting latency timer to 64
[   21.212473] type=1505 audit(1280502177.017:5):  operation="profile_load" pid=1408 name="/usr/share/gdm/guest-session/Xsession"
[   21.214556] type=1505 audit(1280502177.017:6):  operation="profile_replace" pid=1409 name="/sbin/dhclient3"
[   21.214835] type=1505 audit(1280502177.017:7):  operation="profile_replace" pid=1409 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.214994] type=1505 audit(1280502177.017:8):  operation="profile_replace" pid=1409 name="/usr/lib/connman/scripts/dhclient-script"
[   21.219161] type=1505 audit(1280502177.017:9):  operation="profile_load" pid=1410 name="/usr/bin/evince"
[   21.222761] type=1505 audit(1280502177.027:10):  operation="profile_load" pid=1410 name="/usr/bin/evince-previewer"
[   21.224910] type=1505 audit(1280502177.027:11):  operation="profile_load" pid=1410 name="/usr/bin/evince-thumbnailer"
[   21.410252]   alloc irq_desc for 27 on node -1
[   21.410257]   alloc kstat_irqs on node -1
[   21.410276] tg3 0000:03:00.0: irq 27 for MSI/MSI-X
[   21.516572] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.571947] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.174550] [fglrx] ATIF platform detected with notification ID: 0x81
[   22.244409] [fglrx] GART Table is not in FRAME_BUFFER range 
[   22.244771]   alloc irq_desc for 28 on node -1
[   22.244773]   alloc kstat_irqs on node -1
[   22.244788] fglrx_pci 0000:01:05.0: irq 28 for MSI/MSI-X
[   22.245557] [fglrx] Firegl kernel thread PID: 1615
[   22.245903] [fglrx] IRQ 28 Enabled
[   22.581457] ppdev: user-space parallel port driver
[   22.986258] [fglrx] Gart USWC size:1157 M.
[   22.986264] [fglrx] Gart cacheable size:459 M.
[   22.986270] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   22.986273] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   26.239986] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   33.382704] wlan0: deauthenticating from 00:1b:2f:94:cd:f0 by local choice (reason=3)
[   33.384089] wlan0: direct probe to AP 00:1b:2f:94:cd:f0 (try 1)
[   33.387053] wlan0: direct probe responded
[   33.387061] wlan0: authenticate with AP 00:1b:2f:94:cd:f0 (try 1)
[   33.388899] wlan0: authenticated
[   33.397138] wlan0: associate with AP 00:1b:2f:94:cd:f0 (try 1)
[   33.400417] wlan0: RX AssocResp from 00:1b:2f:94:cd:f0 (capab=0x411 status=0 aid=2)
[   33.400422] wlan0: associated
[   33.401236] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   35.069779] UDF-fs: Partition marked readonly; forcing readonly mount
[   35.144024] UDF-fs INFO UDF: Mounting volume 'THE_OC_S1_D2', timestamp 2004/09/01 19:32 (103c)
[   43.790065] wlan0: no IPv6 routers present
[   58.887792] usb 2-6: USB disconnect, address 3
[   79.150088] usb 2-6: new high speed USB device using ehci_hcd and address 4
[   79.312129] usb 2-6: configuration #1 chosen from 1 choice
[   79.317035] scsi5 : SCSI emulation for USB Mass Storage devices
[   79.317189] usb-storage: device found at 4
[   79.317191] usb-storage: waiting for device to settle before scanning
[  127.522881] lo: Disabled Privacy Extensions
[  308.230713] usb 2-6: USB disconnect, address 4
[  308.550175] usb 2-6: new high speed USB device using ehci_hcd and address 5
[  308.712381] usb 2-6: configuration #1 chosen from 1 choice
[  308.722727] scsi6 : SCSI emulation for USB Mass Storage devices
[  308.723408] usb-storage: device found at 5
[  308.723415] usb-storage: waiting for device to settle before scanning

```

It's also worth noting that the same thing is happening with her USB-HDD too.  Her dads USB-HDD works fine, but hers does not, in which case it's exactly the same symptoms are happening.

Also, the SD card works fine in Windows 7 on the same laptop, so I know that the disk is not damaged.

---

### Post by ukblacknight on 2010-07-31
Bump...

---

### Post by ukblacknight on 2010-08-08
Bump.

---

### Post by ukblacknight on 2010-08-10
I nobody able to help on this at all?  I also can't mount external drives either. :(

---

