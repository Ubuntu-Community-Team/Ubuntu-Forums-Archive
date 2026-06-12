---
title: "Bluetooth Disabled in 10.10"
date: 2011-02-17
forum: General Help
---

### Post by JelloGirl on 2011-02-17
I have been unable to use Bluetooth since I did a clean install of 10.10. It worked before, so I know I have the hardware. 

The default manager has a button to turn on bluetooth, but it doesn't do anything. I downloaded Blueman but get a message that "Bluez daemon is not running, blue-man manager cannot continue."

I've tried a few different inquiries, but I'm not sure what they mean:

> 
hciconfig
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:16:41:4A:98:B0  ACL MTU: 384:8  SCO MTU: 64:8
	DOWN 
	RX bytes:380 acl:0 sco:0 events:16 errors:0
	TX bytes:64 acl:0 sco:0 commands:16 errors:0

sudo lsusb -v | grep Blue
Bus 003 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
  bDeviceProtocol         1 Bluetooth
  idProduct          0x8103 Wireless 350 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth


> 

hciconfig -a
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:16:41:4A:98:B0  ACL MTU: 384:8  SCO MTU: 64:8
	DOWN 
	RX bytes:380 acl:0 sco:0 events:16 errors:0
	TX bytes:64 acl:0 sco:0 commands:16 errors:0
	Features: 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
	Packet type: DM1 DH1 HV1 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 


> 

cat /var/log/dmesg | grep Blue*
[   20.414919] Bluetooth: Core ver 2.15
[   20.414974] Bluetooth: HCI device and connection manager initialized
[   20.414978] Bluetooth: HCI socket layer initialized
[   20.420717] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   21.759900] Bluetooth: L2CAP ver 2.14
[   21.759905] Bluetooth: L2CAP socket layer initialized
[   21.775108] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.775113] Bluetooth: BNEP filters: protocol multicast
[   21.786621] Bluetooth: SCO (Voice Link) ver 0.6
[   21.786625] Bluetooth: SCO socket layer initialized


> 

hciconfig
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:16:41:4A:98:B0  ACL MTU: 384:8  SCO MTU: 64:8
	DOWN 
	RX bytes:380 acl:0 sco:0 events:16 errors:0
	TX bytes:64 acl:0 sco:0 commands:16 errors:0


---

### Post by quixote on 2011-02-18
Maybe try starting the service from the command line to see if that works. ```
sudo /etc/init.d/bluetooth start
```

---

