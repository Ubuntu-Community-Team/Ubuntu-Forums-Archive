---
title: "Grub menu not loading"
date: 2011-01-09
forum: General Help
---

### Post by zuselegacy on 2011-01-09
Iv been running a dual boot ubuntu 9.10 and win xp on my dell inspiron laptop for a few months now without a problem.  But now all of a sudden, sometimes on powering my laptop, the grub menu never shows up. no errors, no messages nothing. however wen i insert my ubuntu disc and choose "load from hard disk", the grub menu shows up and normal bootup ensures. Any idea why this is happening? thanks:)

---

### Post by kimberlite on 2011-01-09
> **zuselegacy said:**
> ... however wen i insert my ubuntu disc and choose "load from hard disk", the grub menu shows up and normal bootup ensures. Any idea why this is happening? thanks:)

Check out BIOS setting: is the hard disk is the first bootable device or your cd drive?

---

### Post by ajgreeny on 2011-01-09
Has there been a grub update recently which may have caused this problem to suddenly appear?  I run 10.04, which has not had any grub changes, but I think I remember reading about something in 9.10, if that is what you have.

---

### Post by zuselegacy on 2011-01-09
i checked my bios settings and hdd is before external drives. and no iv not made any recent changes to the grub.  I also face this problem, after booting ubuntu, after a few minutes, the entire screen gets garbled, display is stuck and the whole system freezes requring me to restart. i use a nvidia geforce card and had recntly installed a driver for it from synaptic. i try using ubuntu live in cd and there's no problem at all.

---

### Post by ajpearson on 2012-01-25
I have the same problem, but only sometimes. I simply turn the laptop of and start again, and then GRUB works.

Would love to know the answer!

---

### Post by drs305 on 2012-01-25
> **ajpearson said:**
> I have the same problem, but only sometimes. I simply turn the laptop of and start again, and then GRUB works.

Would love to know the answer!

If you interrupt the boot Grub leaves a marker that says the boot did not succeed and 'forces' the menu to appear on the next boot. This could be what is happening in your situation, but we really don't have enough information to know for sure. 

If you really want to pursue this I would suggest you start your own thread and provide a bit more details on when it happens and what you see.

---

