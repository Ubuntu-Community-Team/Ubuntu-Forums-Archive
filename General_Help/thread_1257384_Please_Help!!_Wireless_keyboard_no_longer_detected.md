---
title: "Please Help!! Wireless keyboard no longer detected during boot phase!"
date: 2009-09-03
forum: General Help
---

### Post by DylanH on 2009-09-03
This is kind of pressing problem, so it anyone can help me I'd be incredibly grateful.

I accidentally cut power to my desktop when I stepped on the power bar. Now my wireless USB keyboard and mouse are no longer working during the initial BIOS/GRUB boot phase. After 10 seconds the Grub loader starts powering up Linux and THEN my USB keyboard and mouse come to life.

The problem is that I need to get into XP for work. If my keyboard isn't working during the boot phase then I can't select anything from the Grub loader.

This is the first time this has happened in hundreds of boots. I don't know why. My guess is that the power outage reset my BIOS, but who knows. I can't access the BIOS currently for obvious reasons.

Oh and this is the only keyboard I have (no PS/2.)

Any ideas???

---

I just thought of a temporary solution - edit menu.lst and place XP as the default OS so it autoloads that instead of Ubuntu. But I'm still looking for a long-term fix.

---

### Post by Vaphell on 2009-09-03
bios reset is likely, i had similar issues when bios decided to mess things up - i had to recreate configuration to have my keyboard and mouse working.

---

### Post by DylanH on 2009-09-03
Thanks for letting me know. That helps me have a better idea of what the problem is.

I've never heard of a way, but does anyone know if the BIOS can be edited from within Linux?

---

### Post by DylanH on 2009-09-03
No idea how, but it's working again.

For the past hour I tried everything I could think of - changing the batteries, changing USB ports, etc. Randomly now it seems to be fixed. I can't explain why.

If anyone has this problem in the future, good luck! Hopefully it just "works" eventually.

---

