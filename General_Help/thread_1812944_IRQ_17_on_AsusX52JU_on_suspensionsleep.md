---
title: "IRQ 17 on AsusX52JU on suspension/sleep"
date: 2011-07-27
forum: General Help
---

### Post by AlexSV on 2011-07-27
Hey, I'm running the latest stable version of Ubuntu on an ASUSX52JU laptop i bought recently.

Whenever the laptop goes to suspend or hibernate the following text comes on screen and I have to reboot it to get it to work
[INDENT]
irq 17: nobody cared (try booting with the "irqpoll" option)
handlers:
[<ffffffffa0327ee0>] (ayh_isr+0x0/0x290[ath9k])
Disabling IRQ #17
[/INDENT]

Can anyone interpret this for me and show me the way to getting it fixed. I've done a basic search and I'll I've found out is that IRQ is an interrupt request (which makes sense.)

(+ if anyone is familiar help me find the drivers I need for the inbuilt mic)

---

