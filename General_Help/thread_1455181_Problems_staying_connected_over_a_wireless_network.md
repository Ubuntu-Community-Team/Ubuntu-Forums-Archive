---
title: "Problems staying connected over a wireless network (Compaq CQ61))"
date: 2010-04-15
forum: General Help
---

### Post by ninjaaron on 2010-04-15
My old Laptop broke (also an ubuntu machine), so I just got a new one. It's a really cheap Compaq, but more than enough for my simple needs, and the service plan was good, so I got it.

Anyway, The wi-fi at my home network has been really crappy since then. I remain connected to the router, but the service mysteriously disappears after it's been on a while. Occasionally disconnecting and reconnecting helps, but usually not. Restarting the machine helps most of the time, but this invariably happens after being on for a while (usually less than thirty minutes. Sometimes much less). It's not a network problem, because everyone else stays connected. It also doesn't happen on my Windows partition. It is infuriating. I would almost just prefer to stay in Windows all the time since everything is working great over there (better flash support, internet works, Open Office even boots faster, oddly enough).

Anyway most of my disk is already partitioned to Ubuntu, and I still want to believe. Just help me get my internets working right.

P.S. Someone else is graciously allowing me to use their service, so I can't go around making demands about network protocols or anything like that. I need to make it work from inside the OS.

---

### Post by 2hot6ft2 on 2010-04-15
It would be more help to know what wifi adapter you have.
Open a terminal
Applications > Accessories > Terminal
and run

If internal PCI
```
lspci
```
That's LSPCI in lower case, and post the results.

If it's a USB adapter
```
lsusb
```
That's LSUSB in lower case, and post the results.

---

