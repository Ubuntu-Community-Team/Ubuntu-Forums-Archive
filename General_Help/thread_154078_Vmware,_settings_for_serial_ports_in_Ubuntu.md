---
title: "Vmware, settings for serial ports in Ubuntu?"
date: 2006-04-02
forum: General Help
---

### Post by speedsix on 2006-04-02
Does anyone have working serial ports running vmware on ubuntu? My XP config file has..
```

serial0.present = "TRUE"
serial0.fileName = "/dev/ttyS1"
serial0.hardwareFlowControl = "TRUE"

```

Am I pointing to the correct /dev/?

---

### Post by MrMozza on 2006-12-30
I have XP as a guest OS (I'm using it for some VWS weather station software).
From my config file (the vmx file):

serial0.present = "TRUE"
serial0.fileName = "/dev/ttyS0"

(Ubuntu Edgy 6.10 fully updated & VMware-server-1.0.1-29996.tar.gz)

But I see the following messages in /var/log/messages which I'm sure is to do with the serial port, I'm still looking for a solution for that...

Dec 30 14:21:20 martyr kernel: [ 2914.751575] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 30 14:21:20 martyr kernel: [ 2914.751579] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 30 14:21:27 martyr kernel: [ 2917.956987] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 30 14:21:27 martyr kernel: [ 2917.956991] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.

---

