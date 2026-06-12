---
title: "usb not working in my labtop"
date: 2011-04-25
forum: General Help
---

### Post by gretarsson on 2011-04-25
Hi. I have old Hp nx 6125 for my youngest son and it have ubuntu 10.10 on it but after one of this update the usb ports stop working the Hp can not see anything I plug into the usb ports it was working fine before, here is some list.> 
anton@anton:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
anton@anton:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
02:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
02:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
anton@anton:~$ dmesg | tail -n15
[   25.164648] wlan0: associated
[   25.165641] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   26.654505] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 2592.759180] ehci_hcd 0000:00:13.2: port 3 reset error -110
[ 2592.759194] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 2592.868064] usb 1-5: new high speed USB device using ehci_hcd and address 10
[ 2593.008103] usb 1-5: device descriptor read/64, error -71
[ 2593.252049] usb 1-5: device descriptor read/64, error -71
[ 2593.468050] usb 1-5: new high speed USB device using ehci_hcd and address 11
[ 2593.608064] usb 1-5: device descriptor read/64, error -71
[ 2593.852079] usb 1-5: device descriptor read/64, error -71
[ 2594.068072] usb 1-5: new high speed USB device using ehci_hcd and address 12
[ 2594.492057] usb 1-5: device not accepting address 12, error -71
[ 2594.604077] usb 1-5: new high speed USB device using ehci_hcd and address 13
[ 2595.028068] usb 1-5: device not accepting address 13, error -71
anton@anton:~$ 

---

