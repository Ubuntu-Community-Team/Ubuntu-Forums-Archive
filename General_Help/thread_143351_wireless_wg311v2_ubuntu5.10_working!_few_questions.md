---
title: "wireless wg311v2 ubuntu5.10 working! few questions remaining"
date: 2006-03-12
forum: General Help
---

### Post by tempo500 on 2006-03-12
hi, i finally got it the wireless to work...well being exact ubuntu did after a fresh reinstall. so now that i am conected is it posible to raise the txpower value to 20 dbm? i currently have 15 and could raise the value to 20 while i wasnt connected to the router. now that i am connected i just can lower the value... wg311v2 doesnt suuport more? i am using the command sudo iwconfig wlan0 txpower 100mW. 

second,
the connection stops when the connection is idle, starts again when i use the internet, iwconfig tells me that power managment is off, but it doesnt look like it...

third,

 atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4306136.857000] tx: error 0x20, buf 11! (excessive Tx retries due to either dis tance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpowe r XXX' or 'sens'itivity or 'retry')
[4306149.254000] rx: DUP pkt (seq 53792)!
[4306497.840000] rx: DUP pkt (seq 44512)!
[4306520.505000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4306520.505000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4306520.593000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).

this is the message from dmesg... is that ok? doesnt look that good...
thanx in advanced from a total linux n00b

---

