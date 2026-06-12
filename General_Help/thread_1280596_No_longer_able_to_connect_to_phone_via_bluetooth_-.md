---
title: "No longer able to connect to phone via bluetooth - &quot;connection reset by peer&quot;"
date: 2009-10-02
forum: General Help
---

### Post by tsprout on 2009-10-02
Hi. Please point me in the right direction troubleshooting this issue.
Running 9.04 on DELL Studio 1537, trying to connect to Nokia N73 using Bluetooth icon (Browse files on device...)

Get this message:

[I]Could not display "obex://[00:1B:AF:7F:47:EE]/".
Error: Service search failed (Connection reset by peer)
Please select another viewer and try again.[/I]

Was able to bluetooth to my phone fine about a week ago. System up to date.

I am able to pair with my phone using "Set up new device" on the Bluetooth icon.

My limited trouble shooting, yields:
**sudo hcitool scan** 
```
    00:1B:AF:7F:47:EE    Fusion
```**sudo hciconfig -a**
```
hci0:    Type: USB
    BD Address: 00:22:5F:4B:7C:B0 ACL MTU: 1021:8 SCO MTU: 64:8
    UP RUNNING PSCAN ISCAN 
    RX bytes:4118 acl:2 sco:0 events:166 errors:0
    TX bytes:3363 acl:16 sco:0 commands:101 errors:0
    Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x79 0x83
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'tsprout'
    Class: 0x0a210c
    Service Classes: Networking, Capturing
    Device Class: Computer, Laptop
    HCI Ver: 2.1 (0x4) HCI Rev: 0x51c8 LMP Ver: 2.1 (0x4) LMP Subver: 0x423d
    Manufacturer: Broadcom Corporation (15)
```I was also able to use the device as a Bluetooth modem previously but this is also not working now.

When I run: **rfcomm connect 0** 
I get:
```
Can't connect RFCOMM socket: Connection reset by peer
```Please let me know what else I should be looking for...:confused:

---

