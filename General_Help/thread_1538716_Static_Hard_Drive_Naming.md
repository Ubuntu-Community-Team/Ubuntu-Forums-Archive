---
title: "Static Hard Drive Naming"
date: 2010-07-25
forum: General Help
---

### Post by cj.surrusco on 2010-07-25
I have 4 SATA hard drives, and they are named sda, sdb, sdc and sdd. My problem is that the drives always randomly switch between these names when I restart my system. It is not really a problem as far as mounting, because I use the UUID option. I'm using the sensors applet to monitor the temps of the hard drives, and I can never tell which one is which, because the drive names are always changing.

Is there any way to have the drives named the same way every time?

Thanks in advance,

CJ

---

### Post by regneva on 2010-07-25
Is the boot sequence fixed in your computer? For me the names on /dev change only when I change the boot sequence or when I physically move the hard drives or change jumper settings.

---

### Post by cj.surrusco on 2010-07-25
> **regneva said:**
> Is the boot sequence fixed in your computer? For me the names on /dev change only when I change the boot sequence or when I physically move the hard drives or change jumper settings.

No, that doesn't seem to be it. I don't have to change anything for it to do this.

Thanks anyway.

---

### Post by cj.surrusco on 2010-08-02
I seemed to have narrowed it down a little bit. One of my drives in connected to a different controller. For some reason, my motherboard has two separate controllers (I think it has to do with the fakeraid).

Anyway, the second controller will sometimes be listed before the first controller, or sometimes after. So the drive will sometimes be mapped at sda, and sometimes at sdd. 

I can't figure out any way to control it...

---

