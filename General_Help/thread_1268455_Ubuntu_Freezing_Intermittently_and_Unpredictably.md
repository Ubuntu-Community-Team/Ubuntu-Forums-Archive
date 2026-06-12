---
title: "Ubuntu Freezing Intermittently and Unpredictably"
date: 2009-09-17
forum: General Help
---

### Post by spartanghost on 2009-09-17
I've just installed the latest version of Ubuntu via wubi on my new desktop.  However, it freezes at seemingly random times, and there doesnt seem to be an obvious cause.  Has anyone else had a similar problem?

Here are the specs of my computer:

AMD Phenom 9600 Quad-Core
Asus M4N78 Pro Motherboard
NVidia GeForce 9400 Video card

Let me know if you need any more information and if so how to obtain it.

Thanks in advance.

---

### Post by QIII on 2009-09-17
I've no experience with Wubi installs, but with a fair understanding of what it is, I'd say it would be hard to differentiate between a problem with Ubuntu itself or Windows.

---

### Post by spartanghost on 2009-09-17
If it helps i've had Windows 7 pro running flawlessly for a couple days, and XP SP3 for a couple weeks before.  A friend thinks it may be the TLB bug on my phenom 9600 popping up. does that sound right?

---

### Post by QIII on 2009-09-17
The TLB problem (not really a "bug", because it is a hardware issue.  There are BIOS and software work arounds that keep it in check... with a performance hit.) was a fairly early problem, and i doubt they've let it continue for the last couple of years since the Phenom has been on the market.

How old is your processor?

---

### Post by P4man on 2009-09-17
its not the TLB bug.
Im guessing its a BIOS and/or IRQ problem

Can you post the output of 

```
cat /proc/interrupts
```?

Make sure your USB isn't sharing an interrupt with anything else. You can try setting your BIOS to disable USB legacy support, enable "plug and play OS". Connect your USB devices to a different port...

---

### Post by spartanghost on 2009-09-17
I bought the processor a couple weeks ago, but it was on sale so i have a feeling they were trying to sell them off.  However, there is no TLB option in my BIOS settings.  I'm not sure what USB has to do with this problem. Could someone explain that please (also the output of that command will coem later, i'm on a different computer now)

---

### Post by P4man on 2009-09-17
> **spartanghost said:**
> I bought the processor a couple weeks ago, but it was on sale so i have a feeling they were trying to sell them off.  However, there is no TLB option in my BIOS settings.  I'm not sure what USB has to do with this problem. Could someone explain that please (also the output of that command will coem later, i'm on a different computer now)

crappy ACPI implementations can end up in having USB and videocard (or sound) share an interrupt, and that may cause freezes. Admittedly, its a long shot, but you wouldn't be the first.

---

### Post by spartanghost on 2009-09-17
This is very frustrating. I've been trying to run the command and i got it once, but it always freezes just before or just after i enter that command!  what exactly should I be looking for in there?

---

