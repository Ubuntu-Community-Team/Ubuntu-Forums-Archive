---
title: "I need help troubleshooting bluetooth problem."
date: 2012-08-04
forum: General Help
---

### Post by 0okami on 2012-08-04
Ok, so im not too familiar with bluetooth but while I was updating/patching some wifi drivers, something went wrong somewhere and now my bluetooth mouse stopped working. It can be seen and added, but the mouse does not move nor click. 

Here's what i'm working with: 
ubuntu 12.04 

```
 
wolfe@inugami:~$ lsusb
Bus 002 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

```

```

wolfe@inugami:~$ hciconfig
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 01:36:05:22:62:D5  ACL MTU: 310:10  SCO MTU: 64:8
	UP RUNNING PSCAN 
	RX bytes:16270 acl:844 sco:0 events:187 errors:0
	TX bytes:1719 acl:43 sco:0 commands:73 errors:0

```

```

wolfe@inugami:~$ hciconfig -a hci0
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 01:36:05:22:62:D5  ACL MTU: 310:10  SCO MTU: 64:8
	UP RUNNING PSCAN 
	RX bytes:16270 acl:844 sco:0 events:187 errors:0
	TX bytes:1719 acl:43 sco:0 commands:73 errors:0
	Features: 0xff 0xff 0x8f 0xfe 0x9b 0xf9 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'inugami-0'
	Class: 0x7e0100
	Service Classes: Networking, Rendering, Capturing, Object Transfer, Audio, Telephony
	Device Class: Computer, Uncategorized
	HCI Version: 2.0 (0x3)  Revision: 0xc5c
	LMP Version: 2.0 (0x3)  Subversion: 0xc5c
	Manufacturer: Cambridge Silicon Radio (10)


```

???

I'm not sure where to start troubleshooting with bluetooth. Any help appreciated.

---

### Post by 0okami on 2012-08-04
here's a few things i've tried...

---

### Post by 0okami on 2012-08-04
continuing

---

### Post by 0okami on 2012-08-04
and more..

---

### Post by 0okami on 2012-08-04
and still no luck. No courser movement, no clicks even though it shows as successful. 

Any advice in how to further troubleshooting is greatly welcome.

---

### Post by 0okami on 2012-08-05
Some more info... 
/var/log/syslog

```
 
Aug  5 17:35:06 inugami bluetoothd[946]: HCI dev 0 down
Aug  5 17:35:06 inugami bluetoothd[946]: Adapter /org/bluez/946/hci0 has been disabled
Aug  5 17:35:06 inugami bluetoothd[946]: HCI dev 0 up
Aug  5 17:35:06 inugami bluetoothd[946]: Adapter /org/bluez/946/hci0 has been enabled
Aug  5 17:35:06 inugami bluetoothd[946]: Inquiry Cancel Failed with status 0x0c
Aug  5 17:35:26 inugami bluetoothd[946]: Discovery session 0xb7902250 with :1.228 activated
Aug  5 17:35:35 inugami bluetoothd[946]: Stopping discovery
Aug  5 17:36:58 inugami sudo: pam_ecryptfs: pam_sm_authenticate: /home/wolfe is already mounted


``` 

Is this something to be concerned about?: 

```

Aug  5 17:35:06 inugami bluetoothd[946]: Inquiry Cancel Failed with status 0x0c

```

---

