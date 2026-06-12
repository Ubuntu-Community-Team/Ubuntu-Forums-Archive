---
title: "Bluetooth problem"
date: 2012-03-27
forum: General Help
---

### Post by gayden on 2012-03-27
Hi there ,

each time i try to pair my pc with any mobile it gives me an error code :-
```
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "<string>", line 2, in CreateDevice
  File "/usr/lib/python2.6/dist-packages/blueman/plugins/applet/DBusService.py", line 135, in CreateDevice
    agent = TempAgent(self.Applet.Plugins.StatusIcon, agent_path, time)
  File "/usr/lib/python2.6/dist-packages/blueman/main/applet/BluezAgent.py", line 255, in __init__
    CommonAgent.__init__(self, status_icon, path)
  File "/usr/lib/python2.6/dist-packages/blueman/main/applet/BluezAgent.py", line 52, in __init__
    Agent.__init__(self, path)
  File "/usr/lib/python2.6/dist-packages/blueman/bluez/Agent.py", line 68, in __init__
    dbus.service.Object.__init__(self, dbus.SystemBus(), obj_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 480, in __init__
    self.add_to_connection(conn, object_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 571, in add_to_connection
    self._fallback)
KeyError: "Can't register the object-path handler for '/org/blueman/agent/temp/0013E05AC484': there is already a handler"
```i don't know what's the problem
i'm using backtrack5
and those are my bluetooth card information :-
```
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 00:19:7E:EA:8C:CD  ACL MTU: 1017:8  SCO MTU: 64:8
    UP RUNNING PSCAN ISCAN 
    RX bytes:2793 acl:0 sco:0 events:85 errors:0
    TX bytes:472 acl:0 sco:0 commands:44 errors:0
    Features: 0xff 0xff 0x8d 0xfe 0x9b 0xf9 0x00 0x80
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'USER-PC'
    Class: 0x100100
    Service Classes: Object Transfer
    Device Class: Computer, Uncategorized
    HCI Version: 2.0 (0x3)  Revision: 0x2049
    LMP Version: 2.0 (0x3)  Subversion: 0x4127
    Manufacturer: Broadcom Corporation (15)

```any solutions ?

thanks in advance :)

---

### Post by gayden on 2012-03-27
isn't there any solution for my problem ?

---

### Post by Mark Phelps on 2012-03-27
WOW -- you expect a solution in only 5 hours!  

Show some patience -- we're all volunteers here.

Could be that the ONLY person who can solve this for you is ASLEEP on the other side of the World when you post your question.

---

