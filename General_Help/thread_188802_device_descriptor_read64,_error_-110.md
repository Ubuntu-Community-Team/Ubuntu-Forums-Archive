---
title: "device descriptor read/64, error -110"
date: 2006-06-04
forum: General Help
---

### Post by bkanuka on 2006-06-04
I have tried for days to fix this and I still have no idea what to do.  This seems like an unsolvable problem.

Basically, my usb cd-rom drive doesn't work. It worked under breezy and an update to dapper, but after a fresh install, it doesn't work.
 Well on to the symptoms;  My dmesg:
```
[4295128.721000] usb 3-5: new high speed USB device using ehci_hcd and address 16
[4295128.835000] hub 3-5:1.0: USB hub found
[4295128.835000] hub 3-5:1.0: 3 ports detected
[4295129.270000] usb 3-5.1: new high speed USB device using ehci_hcd and address 17
[4295131.088000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[4295131.088000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4295132.150000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4295132.150000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295132.343000] usb 3-5.1: device descriptor read/64, error -110

```and it kind of repeats the same thing as long as I have the drive plugged in.
Also, strange thing, when the computer starts up with the drive plugged in, it takes a long time for the usb optical mouse light to turn on.  If I unplug the drive durring startup, the usb mouse light goes on right away.
I am really frustrated so just give me any leads you can.

---

### Post by bkanuka on 2006-06-05
Sorry to push it, but I'd really like a cd drive.

---

### Post by bkanuka on 2006-06-08
anyone?

---

### Post by bkanuka on 2006-06-10
works.  I have no idea why. maybe it's becuase I plugged in USB for the drive before the drive's power supply, but I don't want to unplug it again to find out.

---

### Post by enopepsoo on 2006-06-10
[QUOTE=bkanuka]works.  I have no idea why. maybe it's becuase I plugged in USB for the drive before the drive's power supply, but I don't want to unplug it again to find out.[/QUOTE]

I am happy we could help you out with that one. :p

---

