---
title: "Realtek 8112L Gigabit LAN controller"
date: 2010-07-19
forum: General Help
---

### Post by KonoKanji on 2010-07-19
So my new Computer was workin' fine until one mornin' I lost power to my desktop due to a blackout during an update and my LAN built into my motherboard stop working.  The motherboard claims that it's enabled in the bios but it doesn't show up in my Ubuntu installation nor my XP boot.  It's a ASUS P7P55D motherboard.  Any info would be helpful.  Thanks.  

Note: please excuse any grammatical mistakes that don't make any sense because I am typing this out on an iPod.

---

### Post by cariboo on 2010-07-19
If the nic doesn't show up in Windows or Ubuntu, try resetting the BIOS using the jumper on the motherbaord, to see if that makes a difference.

---

### Post by rubylaser on 2010-07-19
If the BIOS reset doesn't work, which I'm guessing it won't, you probably have a hardware failure.  If that's the case, just pick up a new PCI gigabit NIC card.

---

### Post by kepps03 on 2010-07-19
> **KonoKanji said:**
> So my new Computer was workin' fine until one mornin' I lost power to my desktop due to a blackout during an update and my LAN built into my motherboard stop working.  The motherboard claims that it's enabled in the bios but it doesn't show up in my Ubuntu installation nor my XP boot.  It's a ASUS P7P55D motherboard.  Any info would be helpful.  Thanks.  

Note: please excuse any grammatical mistakes that don't make any sense because I am typing this out on an iPod.


Lost power is key here for me. I think the power lost fried your NIC.

---

### Post by KonoKanji on 2010-07-19
> **cariboo907 said:**
> If the nic doesn't show up in Windows or Ubuntu, try resetting the BIOS using the jumper on the motherbaord, to see if that makes a difference.

So, I popped it open and switched over to the 2,3 jumpers to briefly reset it, popped it back on and the NIC came back to life!  Brilliant.  I would have been so disappointed if the controller had already burnt out on the board I just invested in.
Thanks for the prompt responses, guys.  Much appreciated.

---

### Post by ColonelSammy on 2011-01-24
I had a similar problem, also with an Asus P7P55D motherboard, although I didn't have any power problems.  Clearing the RTC RAM (moving the jumper from pins 1-2 to pins 2-3 also fixed the problem for me.

:D

---

