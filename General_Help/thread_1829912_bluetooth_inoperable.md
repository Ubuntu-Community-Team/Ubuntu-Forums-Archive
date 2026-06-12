---
title: "bluetooth inoperable"
date: 2011-08-20
forum: General Help
---

### Post by quequotion on 2011-08-20
I can't use any bluetooth devices.

I can't manage my bluetooth adapter.

It's plugged in and it works.

```
sudo hciconfig dev
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:1B:DC:0F:E6:FB  ACL MTU: 310:10  SCO MTU: 64:8
	UP RUNNING 
	RX bytes:382 acl:0 sco:0 events:14 errors:0
	TX bytes:44 acl:0 sco:0 commands:13 errors:0

```

Any time I try to use bluetooth however,
```
The name org.bluez was not provided by any .service files
```

I've tried restarting bluetooth.

I've tried removing gnome-bluetooth and installing blueman to no avail.

The Unity bluetooth indicator only has a switch for bluetooth ON or OFF which is apparently meaningless.

---

### Post by quequotion on 2011-08-21
Issue resolved.

I reinstalled bluez and rebooted.

Don't know exactly why, but things are mostly working now.

---

