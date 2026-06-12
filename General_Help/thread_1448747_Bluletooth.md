---
title: "Bluletooth"
date: 2010-04-07
forum: General Help
---

### Post by nanchu on 2010-04-07
I have installed Ubuntu 9.10. I am able to change the bluetooth dongle name form bluez-gnome interface. However, if i make changes to /etc/bluetooth/main.conf the name does NOT change. I have unistall bluez-gnome but still no luck. mi bluetooth main.conf:

[General]
Name = %h-%d
Class = 0x5a0204
DiscoverableTimeout = 0
ReverseServiceDiscovery = true
NameResolving = true


After applying several system reboot I can not get changes to work.
When i run hciconfig -a i get:

hci0:	Type: USB
	BD Address: 00:1E:58:XX:XX:XX ACL MTU: 1017:8 SCO MTU: 64:0
	UP RUNNING PSCAN 
	RX bytes:2743 acl:0 sco:0 events:61 errors:0
	TX bytes:739 acl:0 sco:0 commands:61 errors:0
	Features: 0xff 0xff 0x8d 0xfe 0x9b 0xf9 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	[COLOR="Magenta"]Name: 'MiDispBl'[/COLOR]
	Class: 0x4a010c
	Service Classes: Networking, Capturing, Telephony
	Device Class: Computer, Laptop
	HCI Ver: 2.0 (0x3) HCI Rev: 0x403d LMP Ver: 2.0 (0x3) LMP Subver: 0x430e
	Manufacturer: Broadcom Corporation (15)

Does any body know where ubuntu is taking this info from?

Thanks in advance,
Nanchu

---

