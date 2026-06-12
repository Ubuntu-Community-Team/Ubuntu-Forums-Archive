---
title: "CD/DVD drive stopped working"
date: 2010-05-16
forum: General Help
---

### Post by klingzw on 2010-05-16
Good evening all, 

My grandparents have been wanting a computer for a long time. About a month ago I built them a computer running ubuntu 10.04 64bit

System specs

Athlon x4 630 @3.2 GHz
4 GB DDR2 800 g.skill ram
MSI 785 motherboard
Sony optical drive (this is the item in question)

I tested the computer at my house for 3 weeks and everything worked smooth as could be.
They took it home (live about 500 miles away) and all worked fine until today. The optical drive seems to not recognize any disk that is inserted!!! However the drive is listed under places>computer as a cd/dvd drive. 

I really hope this is a quick / easy fix as my grandparents were really excited to have a cd/ dvd player, but all of a sudden it has stopped working??

Any suggestions would be really appreciated.

Sincerely,
               klingzw

---

### Post by klingzw on 2010-05-16
One thing I forgot to mention. This problem seemed to arise after installing K3b from software center.

---

### Post by Bucky Ball on 2010-05-16
10.04 is not a good idea for new computer users at it is a baby and there will be probs cropping up on and off for a few months yet.

It could just be that the hardware has died. It will show up, sure, but that doesn't mean that the internals are operational. Bit hard from 500 miles away, but the sure way would be to test in another machine. Someone else will hopefully have some other ideas.

---

### Post by klingzw on 2010-05-17
I really hope that is not the case.. 

Is there anything that could have disabled the CD/DVD drive after installing K3b???

It worked fine saturday, then we installed K3b and after that no media put into the optical drive will work... Have restarted the computer numerous times.


Any suggestions?

---

### Post by Bucky Ball on 2010-05-17
Uninstall K3b would be a start and see if it makes any difference. Open a terminal and try:

```
lspci
```

The optical drive should be on the list there somewhere, just to make sure it is recognised as being in the machine. If not ...

Have there been any updates that may have killed it?

---

### Post by houman001 on 2010-06-02
I'm having the same problem with Ubuntu 9.04
I have K3B installed on my system, and whenever I restart the system with a CD/DVD inserted that will be recognized by the system. Otherwise I won't be able to read a CD/DVD.
I think that something might be wrong with K3B.
I'm gonna test it further and let you know if I discover the root cause of the problem.

---

### Post by Bucky Ball on 2010-06-02
Houman: If you have a cd inserted at boot and your machine is not booting from it, Ubuntu has nothing to do with that. The OS is not happening then. You might want to get into the BIOS and tell your maching to BOOT FROM CD! Sheesh. K3b is not your issue here ...

Try booting with NO cd in the drive.

---

### Post by houman001 on 2010-06-09
Dear Bucky,
As I said, my system ONLY recognizes the CD/DVD that has been in the tray BEFORE booting into Ubuntu. If you get it out and replace it with another one, it won't read it.
I didn't say, NOT BOOTING FROM IT! Please read carefully before responding.

By the way, it seems to be a hardware issue in my case.
Once I changed the SATA port of my DVD drive a couple of days ago, no such incident happened.

Cheers

---

