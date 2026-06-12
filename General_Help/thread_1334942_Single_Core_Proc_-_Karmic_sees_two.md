---
title: "Single Core Proc - Karmic sees two??"
date: 2009-11-23
forum: General Help
---

### Post by Roasted on 2009-11-23
In system monitor on this computer it comes back as CPU1 and CPU2 on the processor monitor section, suggesting it's seeing a dual core processor.

Although this computer had the option for a dual core processor, it says Pentium 4 HT on the front, and to the best of my knowledge I thought it was a simple P4 single core 3.0ghz chip.

So uh.. what's up with this?

---

### Post by KiraLexi on 2009-11-23
P4 HT was a modified Pentium 4 design that could, under certain circumstances, run two threads concurrently. It appears to the OS as two logical processors.

---

### Post by Ahadiel on 2009-11-23
[http://en.wikipedia.org/wiki/Hyper-threading](http://en.wikipedia.org/wiki/Hyper-threading)

---

### Post by Roasted on 2009-11-23
Ah yeah, that's gotta be what it is. I have an Ubuntu FOG imaging server here at work which is simply a Pentium 4 3.0ghz machine with 1gb of RAM. It's an HP, just like my computer at home, but completely different models.

I'm typing from that other computer now and it too shows up as two CPUs in system monitor. I see now. Thanks guys!

---

### Post by ankspo71 on 2009-11-23
I'm a pentium 4 3.0 user too. I agree with the others. The pentium 4's with hyperthreading enabled will appear as having two processors. This used to be a Celeron computer 2.0 and it used to only show one processor.

---

