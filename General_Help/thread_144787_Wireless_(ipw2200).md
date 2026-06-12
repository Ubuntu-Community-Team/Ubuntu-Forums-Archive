---
title: "Wireless (ipw2200)"
date: 2006-03-15
forum: General Help
---

### Post by john_markh on 2006-03-15
Hi,
My wireless card (internal card in HP pavilion ze4900) worked until I have updated to newer kernel version.
Since then, I can't connect to any peer.
The problem is with switch button, it seems not to work anymore :
[SIZE="1"]localhost kernel [4294998.379000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
localhost kernel [4294998.379000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
localhost kernel [4294999.220000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
localhost kernel [4294999.220000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
localhost kernel [4294999.820000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
localhost kernel [4294999.820000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
localhost kernel [4295000.381000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
localhost kernel [4295000.381000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
localhost kernel [4295001.699000] ipw2200: failed to send SCAN_ABORT command
localhost kernel [4295002.709000] ipw2200: failed to send CARD_DISABLE command[/SIZE]
I tried to follow different "HOWTO"s to update my driver version successfully, but I still can't switch on the wireless card.

---

### Post by Titus A Duxass on 2006-03-15
Try going back to the old kernel.

---

### Post by john_markh on 2006-03-16
Tried, the same...:-k

---

