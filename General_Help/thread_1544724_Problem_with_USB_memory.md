---
title: "Problem with USB memory"
date: 2010-08-02
forum: General Help
---

### Post by Tantor on 2010-08-02
Hi, I've just installed XUBUNTU 10.04 32 bits on a friend's laptop and I have the following problem.

When I plug a usb stick (pendrive) it doesn't get mounted. I can't mount in manually from a terminal either. After plugging the usb stick I run "sudo fdisk -l" and I can see the hard drive partitions but not the usb stick one. In /dev the corresponing device doesn't show up either. The weird thing is that everything works just fine from the live-cd.

Googling I found a command that provides a temporary fix, but I don't know how to fix it for good. If I plug the usb memory and then type "sudo udevadm trigger", the drive gets automatically mounted. But I have to type the command after plugging the usb stick; it doesn't work if I run the command before.

I really don't know what else to do. Can someone please help me out with this? Below I post the output of the commands
"sudo dmesg | grep usb", "sudo lsusb", "sudo tail /var/log/messages"
before and after plugging an usb stick.

BEFORE PLUGGING THE USB STICK

```
sudo dmesg | grep usb

[    0.246490] usbcore: registered new interface driver usbfs
[    0.246513] usbcore: registered new interface driver hub
[    0.246546] usbcore: registered new device driver usb
[    3.975479] usb usb1: configuration #1 chosen from 1 choice
[    3.975905] usb usb2: configuration #1 chosen from 1 choice
[    3.976246] usb usb3: configuration #1 chosen from 1 choice
[    3.976562] usb usb4: configuration #1 chosen from 1 choice
[    3.976878] usb usb5: confilaptopguration #1 chosen from 1 choice
[   23.337047] usbcore: registered new interface driver ndiswrapper

sudo lsusb

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

sudo tail /var/log/messages
Aug  2 11:58:59 laptop kernel: [   22.994660] ndiswrapper: driver
neti2220 (INPROCOMM,11/04/2004,3.03.11.2004) loaded
Aug  2 11:58:59 laptop kernel: [   22.994937] ndiswrapper
0000:06:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug  2 11:58:59 laptop kernel: [   23.135257] ndiswrapper: using IRQ 17
Aug  2 11:58:59 laptop kernel: [   23.336933] wlan0: ethernet
device 00:11:e2:07:6c:d3 using NDIS driver: neti2220, version:
0x30003, NDIS version: 0x501, vendor: 'NDIS Network Adapter',
17FE:2220.5.conf
Aug  2 11:58:59 laptop kernel: [   23.336957] wlan0: encryption
modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA,
WPA2, WPA2PSK
Aug  2 11:58:59 laptop kernel: [   23.337047] usbcore: registered
new interface driver ndiswrapper
Aug  2 11:58:59 laptop kernel: [   23.353962] ADDRCONF(NETDEV_UP):
wlan0: link is not ready
Aug  2 11:59:27 laptop kernel: [   50.873348] ndiswrapper
(iw_set_auth:1602): invalid cmd 12
Aug  2 11:59:27 laptop kernel: [   50.873358] ndiswrapper
(iw_set_freq:325): setting configuration failed (C0010015)
Aug  2 11:59:27 laptop kernel: [   50.978195]
ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

AFTER PLUGGING THE USB STICK

```
sudo dmesg | grep usb
[    0.246490] usbcore: registered new interface driver usbfs
[    0.246513] usbcore: registered new interface driver hub
[    0.246546] usbcore: registered new device driver usb
[    3.975479] usb usb1: configuration #1 chosen from 1 choice
[    3.975905] usb usb2: configuration #1 chosen from 1 choice
[    3.976246] usb usb3: configuration #1 chosen from 1 choice
[    3.976562] usb usb4: configuration #1 chosen from 1 choice
[    3.976878] usb usb5: configuration #1 chosen from 1 choice
[   23.337047] usbcore: registered new interface driver ndiswrapper
[  371.544072] usb 1-2: new high speed USB device using ehci_hcd and address 2
[  371.688877] usb 1-2: configuration #1 chosen from 1 choice

sudo lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04e8:1623 Samsung Electronics Co., Ltd
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

sudo tail /var/log/messages
Aug  2 11:58:59 laptop kernel: [   23.135257] ndiswrapper: using IRQ 17
Aug  2 11:58:59 laptop kernel: [   23.336933] wlan0: ethernet
device 00:11:e2:07:6c:d3 using NDIS driver: neti2220, version:
0x30003, NDIS version: 0x501, vendor: 'NDIS Network Adapter',
17FE:2220.5.conf
Aug  2 11:58:59 laptop kernel: [   23.336957] wlan0: encryption
modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA,
WPA2, WPA2PSK
Aug  2 11:58:59 laptop kernel: [   23.337047] usbcore: registered
new interface driver ndiswrapper
Aug  2 11:58:59 laptop kernel: [   23.353962] ADDRCONF(NETDEV_UP):
wlan0: link is not ready
Aug  2 11:59:27 laptop kernel: [   50.873348] ndiswrapper
(iw_set_auth:1602): invalid cmd 12
Aug  2 11:59:27 laptop kernel: [   50.873358] ndiswrapper
(iw_set_freq:325): setting configuration failed (C0010015)
Aug  2 11:59:27 laptop kernel: [   50.978195]
ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug  2 12:04:48 laptop kernel: [  371.544072] usb 1-2: new high
speed USB device using ehci_hcd and address 2
Aug  2 12:04:48 laptop kernel: [  371.688877] usb 1-2:
configuration #1 chosen from 1 choice
```

---

