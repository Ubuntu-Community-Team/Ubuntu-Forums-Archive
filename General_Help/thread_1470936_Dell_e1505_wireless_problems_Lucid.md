---
title: "Dell e1505 wireless problems Lucid"
date: 2010-05-03
forum: General Help
---

### Post by theotherotherguy on 2010-05-03
OK guys I took the plunge and made a clean install of 10.04 because it sounded cool (and it is, I like it!) and now I'm tied to a wall again :( I've gone through several of the broadcom wireless card tutorials on the forums and the only thing I've managed to get is a lit up wifi light. It's not detecting an active unsecured network several inches away, that has computers up and running on it... I'm perfectly willing to post more details as needed.


lspci -nn results, "0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311  802.11b/g WLAN [14e4:4311] (rev 01)" being the most relevant entry

```
 00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)                                                                       
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)                                                                            
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)                                                                                      
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```

The device is there, so it's *probably* not a fwcutter problem, dang, those are easy enough to fix so no luck.
I searched my log for "wlan" got the following entries

```

2010-05-03 04:53:17    Lappy-9000    NetworkManager       SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:0b:00.0/ssb0:0/net/wlan0, iface: wlan0)
2010-05-03 04:53:17    Lappy-9000    NetworkManager    <info>  (wlan0): now unmanaged
2010-05-03 04:53:17    Lappy-9000    NetworkManager    <info>  (wlan0): device state change: 2 -> 1 (reason 36)
2010-05-03 04:54:33    Lappy-9000    NetworkManager    <info>  Found wlan radio killswitch rfkill1 (at /sys/devices/virtual/rfkill/rfkill1) (driver <unknown>)
2010-05-03 04:54:34    Lappy-9000    NetworkManager       SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:0b:00.0/net/wlan0, iface: wlan0)
2010-05-03 04:54:34    Lappy-9000    kernel    [   21.831515] wlan0: ethernet device 00:18:f3:49:ec:eb using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
2010-05-03 04:54:34    Lappy-9000    kernel    [   21.831612] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
2010-05-03 04:54:34    Lappy-9000    NetworkManager       SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:0b:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
2010-05-03 04:54:34    Lappy-9000    NetworkManager    <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
2010-05-03 04:54:34    Lappy-9000    NetworkManager    <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
2010-05-03 04:54:34    Lappy-9000    NetworkManager    <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
2010-05-03 04:54:34    Lappy-9000    NetworkManager    <info>  (wlan0): now managed
2010-05-03 04:54:34    Lappy-9000    NetworkManager    <info>  (wlan0): device state change: 1 -> 2 (reason 2)
2010-05-03 04:54:34    Lappy-9000    NetworkManager    <info>  (wlan0): bringing up device.
2010-05-03 04:54:34    Lappy-9000    NetworkManager    <info>  (wlan0): deactivating device (reason: 2).

```If I were a guru I'd know what reason 2 was, but I'm still picking up linux from the top. What doesn't help me may help you help me however. Any ideas as to how to undo this, because I'm considering reverting and that would be no fun.

---

### Post by dino99 on 2010-05-03
wifi-radar, wireless-tools, wireless-crda installed ?

apt://linux-backports-modules-wireless-lucid-generic

found this too:

To solve it I simply went to Synaptic Package Manager

Typed &#8220;broadcom&#8221;

Right clicked on &#8220;bcmwl-kernel-source&#8221; and marked it for re-installation

Then went back to the hardware drivers where I could now activate the broadcom driver without any problems!

---

### Post by john newbuntu on 2010-05-03
Let me ask you a dumb question. Does pressing the Fn and F2 key together help?  A post few hours ago had a similar problem and that was the solution.

---

### Post by theotherotherguy on 2010-05-03
I installed the package, It's hanging on "Acquiring IP address (DHCP)"

is the network manager package broken right now?

@John
no help, the hotkey is disabled from BIOS from other attempts to resolve this issue

---

### Post by theotherotherguy on 2010-05-03
I'm trying the driver options you mentioned... if it works that means this problem is solved from a GUI, which on the one hand makes me feel less good about my terminal skills, but on the other hand makes me feel really good for the dev's who finally fixed it up for us.


**UPDATE**

it seems to have done SOMETHING, I'm going to shutdown -r now and see if it helps

**UPDATE***

That did the trick. Thanks for noticing and knowing about what I did not.

---

