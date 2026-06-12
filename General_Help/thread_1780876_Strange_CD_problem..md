---
title: "Strange CD problem."
date: 2011-06-12
forum: General Help
---

### Post by zozza on 2011-06-12
Hello,

I put a blank CD (Verbatim CD-R) into my external CD drive using 10.04 LTS.

Dmesg shows:

[ 255.950512] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 255.950527] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current]
[ 255.950542] sr 3:0:0:0: [sr0] Add. Sense: Logical block address out of range
[ 255.950558] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 255.950589] end_request: I/O error, dev sr0, sector 0

When I go to /media there are no directories that could be the CD-ROM.  I therefore cannot 'see' the CD (which is blank btw). 

I then went into XP. Windows Explorer could see the blank CD. I then wrote to it.

I then went back into Ubuntu. Now when I put the CD into the external drive Dmesg shows:

[97.594505] ISO 9660 Extensions: Microsoft Joliet Level 3
[97.674629] ISO 9660 Extensions: RRIP_1991A

When I go to /media I see the name of the CD.

Why will XP and Ubuntu see the CD with information on it but only XP can see the blank CD?

Any ideas? Thanks.

---

### Post by ajgreeny on 2011-06-12
Because until it is burned, there is nothing on the disk for linux to see, though it should appear in the left hand pane of nautilus.

Everything in linux is a file, no file means nothing to see.

---

