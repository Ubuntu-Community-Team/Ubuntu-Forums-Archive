---
title: "Is this the sign of a failing hard drive?"
date: 2010-05-04
forum: General Help
---

### Post by false_chicken on 2010-05-04
I upgraded to Lucid yesterday and my computer seems to randomly lock up. I can move the mouse but all of my running programs freeze. Its happens often. When it happens my HDD led is on constantly. And this is in my kernel log:

May  4 16:05:00 jamie-ubuntu kernel: [   35.255113] end_request: I/O error, dev sr0, sector 0
May  4 16:05:00 jamie-ubuntu kernel: [   35.256103] sr 2:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  4 16:05:00 jamie-ubuntu kernel: [   35.256107] sr 2:0:1:0: [sr0] Sense Key : Illegal Request [current] 
May  4 16:05:00 jamie-ubuntu kernel: [   35.256110] sr 2:0:1:0: [sr0] Add. Sense: Logical block address out of range
May  4 16:05:00 jamie-ubuntu kernel: [   35.256114] sr 2:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
May  4 16:05:00 jamie-ubuntu kernel: [   35.256119] end_request: I/O error, dev sr0, sector 0
May  4 16:05:00 jamie-ubuntu kernel: [   35.257107] sr 2:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  4 16:05:00 jamie-ubuntu kernel: [   35.257111] sr 2:0:1:0: [sr0] Sense Key : Illegal Request [current] 
May  4 16:05:00 jamie-ubuntu kernel: [   35.257114] sr 2:0:1:0: [sr0] Add. Sense: Logical block address out of range
May  4 16:05:00 jamie-ubuntu kernel: [   35.257118] sr 2:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
May  4 16:05:00 jamie-ubuntu kernel: [   35.257122] end_request: I/O error, dev sr0, sector 0
May  4 16:05:00 jamie-ubuntu kernel: [   35.286928] psmouse serio1: ID: 10 00 64

Is my drive failing? It only happened when I upgraded.

---

### Post by Usabent on 2010-05-04
> **false_chicken said:**
> I upgraded to Lucid yesterday and my computer seems to randomly lock up. I can move the mouse but all of my running programs freeze. Its happens often. When it happens my HDD led is on constantly. And this is in my kernel log:

May  4 16:05:00 jamie-ubuntu kernel: [   35.255113] end_request: I/O error, dev sr0, sector 0
May  4 16:05:00 jamie-ubuntu kernel: [   35.256103] sr 2:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  4 16:05:00 jamie-ubuntu kernel: [   35.256107] sr 2:0:1:0: [sr0] Sense Key : Illegal Request [current] 
May  4 16:05:00 jamie-ubuntu kernel: [   35.256110] sr 2:0:1:0: [sr0] Add. Sense: Logical block address out of range
May  4 16:05:00 jamie-ubuntu kernel: [   35.256114] sr 2:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
May  4 16:05:00 jamie-ubuntu kernel: [   35.256119] end_request: I/O error, dev sr0, sector 0
May  4 16:05:00 jamie-ubuntu kernel: [   35.257107] sr 2:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  4 16:05:00 jamie-ubuntu kernel: [   35.257111] sr 2:0:1:0: [sr0] Sense Key : Illegal Request [current] 
May  4 16:05:00 jamie-ubuntu kernel: [   35.257114] sr 2:0:1:0: [sr0] Add. Sense: Logical block address out of range
May  4 16:05:00 jamie-ubuntu kernel: [   35.257118] sr 2:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
May  4 16:05:00 jamie-ubuntu kernel: [   35.257122] end_request: I/O error, dev sr0, sector 0
May  4 16:05:00 jamie-ubuntu kernel: [   35.286928] psmouse serio1: ID: 10 00 64

Is my drive failing? It only happened when I upgraded.

I think not because ubuntu 10.04 has lots of bugs it might be A false alarm or the problem is you need to re-install it.

---

### Post by happyhamster on 2010-05-04
/dev/sr0 is a dvd or cd drive.

---

### Post by archimedez on 2010-05-05
I have a similar problem after upgrading. I hope is is just a bug and not the hdd failing. 

No solution as yet.


> **false_chicken said:**
> I upgraded to Lucid yesterday and my computer seems to randomly lock up. I can move the mouse but all of my running programs freeze. Its happens often. When it happens my HDD led is on constantly. And this is in my kernel log:

May  4 16:05:00 jamie-ubuntu kernel: [   35.255113] end_request: I/O error, dev sr0, sector 0
May  4 16:05:00 jamie-ubuntu kernel: [   35.256103] sr 2:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  4 16:05:00 jamie-ubuntu kernel: [   35.256107] sr 2:0:1:0: [sr0] Sense Key : Illegal Request [current] 
May  4 16:05:00 jamie-ubuntu kernel: [   35.256110] sr 2:0:1:0: [sr0] Add. Sense: Logical block address out of range
May  4 16:05:00 jamie-ubuntu kernel: [   35.256114] sr 2:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
May  4 16:05:00 jamie-ubuntu kernel: [   35.256119] end_request: I/O error, dev sr0, sector 0
May  4 16:05:00 jamie-ubuntu kernel: [   35.257107] sr 2:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  4 16:05:00 jamie-ubuntu kernel: [   35.257111] sr 2:0:1:0: [sr0] Sense Key : Illegal Request [current] 
May  4 16:05:00 jamie-ubuntu kernel: [   35.257114] sr 2:0:1:0: [sr0] Add. Sense: Logical block address out of range
May  4 16:05:00 jamie-ubuntu kernel: [   35.257118] sr 2:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
May  4 16:05:00 jamie-ubuntu kernel: [   35.257122] end_request: I/O error, dev sr0, sector 0
May  4 16:05:00 jamie-ubuntu kernel: [   35.286928] psmouse serio1: ID: 10 00 64

Is my drive failing? It only happened when I upgraded.

---

### Post by rnerwein on 2010-05-05
hi
stay cool !
i bet it's a bug - it's on my sons box too ( brand new box with intel i3 - may be this is the problem - with the DVD-RW TSSTcorp  )
ciao

---

