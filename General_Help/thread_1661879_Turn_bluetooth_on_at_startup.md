---
title: "Turn bluetooth on at startup?"
date: 2011-01-07
forum: General Help
---

### Post by davavanstone on 2011-01-07
Hi, im unable to turn bluetooth on at startup, i have to use the applet every time and click enable, any ideas on how to do this via terminal so i can do it on boot?

---

### Post by cgroza on 2011-01-07
Go to System>Preferences>Startup Applications  and there is an option called Bluetooth Manager or something like that. Make sure its ticked.

---

### Post by davavanstone on 2011-01-07
Thanks, but the applet loads, (the boxes are ticked) the the bluetooth is always turned off after a reboot. 
I have tried invoking it by "service bluetooth start" of which the service is already loaded but the bluetooth is not turned on if you get what i mean.  
Is is a dongle so there is no function key to turn it on that way.

EDIT:
More info
Hciconfig hcio up returns:
boxee@Boxee:~$ hciconfig hci0 up
Can't init device hci0: Permission denied (13)
and
boxee@Boxee:~$ sudo hciconfig hci0 up
Can't init device hci0: Operation not possible due to RF-kill (132)

---

### Post by davavanstone on 2011-01-07
Solved

boxee@Boxee:~$ rfkill unblock all
boxee@Boxee:~$ sudo hciconfig hci0 up

---

### Post by MaikoID on 2011-07-19
Hi, I've had the same problem of rfkill now I'm having timeout problems have you ever had any of these problems ?

```
root@maiko-cce-lin:~# hciconfig -a dev
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:1F:81:00:01:1C  ACL MTU: 1021:4  SCO MTU: 180:1
	DOWN 
	RX bytes:330 acl:0 sco:0 events:8 errors:0
	TX bytes:24 acl:0 sco:0 commands:29 errors:21
	Features: 0xff 0x3e 0x09 0x76 0x80 0x01 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: 
	Link mode: SLAVE ACCEPT 

```

```
root@maiko-cce-lin:~# hciconfig hci0 reset
Can't init device hci0: Connection timed out (110)
```

I'm looking for a solution since last week and I can't find one. 

```
root@maiko-cce-lin:~# lsusb | grep Blue
Bus 001 Device 007: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

```

```
root@maiko-cce-lin:~# hcitool dev
Devices:

```

bye

---

