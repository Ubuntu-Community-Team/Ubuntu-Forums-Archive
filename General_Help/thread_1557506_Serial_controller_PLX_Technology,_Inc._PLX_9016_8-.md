---
title: "Serial controller: PLX Technology, Inc. PLX 9016 8-port"
date: 2010-08-20
forum: General Help
---

### Post by ziotibia81 on 2010-08-20
hi!!

I installed on my server (Ubuntu 10.04) a 8-port serial controller.
In the board there are one chip IT8871F and two TL16C554A.

lspci show:
Serial controller: PLX Technology, Inc. PLX 9016 8-port serial controller

lspci -v
05:03.0 Serial controller: PLX Technology, Inc. PLX 9016 8-port serial controller (rev 01) (prog-if 02)
   Subsystem: Device 544e:0008
   Flags: medium devsel, IRQ 22
   I/O ports at 2500 [size=64]
   I/O ports at 2540 [size=16]
   I/O ports at 2550 [size=16]
   Memory at f9fff000 (32-bit, non-prefetchable) [size=4K]
   Memory at f9ffe000 (32-bit, non-prefetchable) [size=4K]
   Memory at f9ffd000 (32-bit, non-prefetchable) [size=4K]

-x05:03.0 Serial controller: PLX Technology, Inc. PLX 9016 8-port serial controller (rev 01)
00: b5 10 16 90 43 01 80 02 01 02 00 07 00 00 00 00
10: 01 25 00 00 41 25 00 00 51 25 00 00 00 f0 ff f9
20: 00 e0 ff f9 00 d0 ff f9 00 00 00 00 4e 54 08 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 03 01 00 00


I look on dmesg output. There is something about ttyS0 that's serial port embedded on motherboard but nothing about other 8 serial port.....

Someone could help me?
bye

---

### Post by gordintoronto on 2010-08-21
You have not said what you want help with.

---

### Post by ziotibia81 on 2010-08-22
...help to configure system do make working this card...

---

