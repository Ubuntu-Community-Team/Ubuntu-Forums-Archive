---
title: "Brightness of laptop in Ubuntu"
date: 2010-07-07
forum: General Help
---

### Post by Ryantoss on 2010-07-07
Hello everybody

I have a 6735b laptop from HP

This is my problem

1. In windows: whenever you unplug your A/C power ==> brightness of laptop will be reduced. This brightness will return after you replug your A/C.

2. In Ubuntu 10.04: The brightness of my laptop in Ubuntu will reduce when i unplug. But they **_will not_** return 100% of brightness when i replug. In fact they will just back about 80% of normal. Thus whatever i do with my configure in brightness 80% will be my new maximum brightness.

100% of brightness only return after i restart my laptop, this is extremely annoy for me T_T.

Any help is extremely welcome :D

---

### Post by Ryantoss on 2010-07-07
Plzzzzzzzzzzzzzzzz, anyone can help me #-o

---

### Post by JoelOl75 on 2010-07-07
Not sure of your HP, but Dell settings are in the BIOS.  Maybe go into your BIOS and Disable any brightness changes and let Ubuntus power management deal with it.

---

### Post by pschroth on 2010-07-08
Welcome on board. Here the same on an hp 6830s. I have tried almost everything to solve this bug. The workaround is to switch of the fglrx driver and use the screenbrightness applet.

---

### Post by Ryantoss on 2010-07-09
> **pschroth said:**
> Welcome on board. Here the same on an hp 6830s. I have tried almost everything to solve this bug. The workaround is to switch of the fglrx driver and use the screenbrightness applet.

Could you provide some more detail, i googgling for flgrx. What does it mean.

---

### Post by Ryantoss on 2010-07-09
Yayyyyyyyyyyyyyyyyyyyy

I found a beautiful solution for this problem.

Turning of ATI driver will not be a good choice.

These things are what you need to do.

1. Go to ATI and take a lastest official driver. For eg, my ATI Catylyst Center was 10.04, i take the newest 10.06 and done.

2. Go to ubuntu official website and take a open-source free driver of ATI.

---

### Post by pschroth on 2010-07-09
Yes that works for me also. Thanks.. Now using 10.04 great..

---

