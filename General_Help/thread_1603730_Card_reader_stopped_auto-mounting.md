---
title: "Card reader stopped auto-mounting"
date: 2010-10-23
forum: General Help
---

### Post by Yappix on 2010-10-23
I have a card reader (you know for those SD cards, etc), previously it was auto-mounting the card as soon as it is inserted (Nautilus would pop up), after that it was auto-mounting only once in a few attempts, now it doesn't mount at all. Lights on the device light up, when I insert the card.

Occasionally it still mounts. But very rarely.

/var/log/messages either adds this:

> kernel: [224291.360707] Info fld=0x0
kernel: [224291.360709] sd 8:0:0:0: [sdf] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
kernel: [224291.360715] sd 8:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
kernel: [224291.362076] sd 8:0:0:0: [sdf] Device not ready
kernel: [224291.362079] sd 8:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
kernel: [224291.362083] sd 8:0:0:0: [sdf] Sense Key : Not Ready [current] 

(a lot of these)

or instead this (if it mounts successfully):

> kernel: [224397.796195]  sdf: sdf1

Ubuntu 10.04 LTS, Gnome

Any ideas where to start searching for the problem?

---

