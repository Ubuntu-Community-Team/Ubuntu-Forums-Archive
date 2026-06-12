---
title: "Hot laptop?"
date: 2009-09-19
forum: General Help
---

### Post by l3git.h4cker on 2009-09-19
As I use more and more of Ubuntu, I notice that my laptop gets quite hot after prolonged use.
I know how to use CPU Freq. and have been keeping my CPU at 1.00 GHz.
Yet my laptop still seems to get hotter than if I was on my Windows partition - windows seems to keep my CPU running even lower than Ubuntu when idle.

Is there a way to force the CPU to run below 1.00 GHz?
Any other way of keeping the temperature cool?

Thanks in advance.:)

---

### Post by Tipped OuT on 2009-09-19
I don't think you would want anything lower then 1.00 Ghz unless you have a really old CPU.

Make sure your laptop stays ventilated. Don't use it on the rug, your bed, or anything that could block the fans of the laptop.

I can't help you any further until you tell me what CPU it is.

---

### Post by tgalati4 on 2009-09-19
If you have an ATI graphics card, you can turn dynamic clocks on to reduce speed of the GPU.  That can make a big difference.

---

### Post by l3git.h4cker on 2009-09-19
I have an Intel Centrino Duo CPU, and an Integrated Intel Graphics card (not ATI).
Hope that helps...

Also, to be very clear, my laptop has excellent ventilation - it just seems that my Windows OS keeps it cooler (and quieter) then Ubuntu...

---

### Post by blackened on 2009-09-19
What exactly is the make/model? It could be acpi scripts controlling temps/fanspeeds incorrectly.

---

### Post by l3git.h4cker on 2009-09-19
> **blackened said:**
> What exactly is the make/model? It could be acpi scripts controlling temps/fanspeeds incorrectly.

..not sure about what the exact make/model is.
But, where might I find these acpi scripts in Ubuntu?

---

### Post by blackened on 2009-09-20
> **l3git.h4cker said:**
> ..not sure about what the exact make/model is.
But, where might I find these acpi scripts in Ubuntu?

/etc/acpi

---

### Post by l3git.h4cker on 2009-09-20
Ha, so I googled for about a min., and found this:

[https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement)

I scrolled to the bottom, and found 'corrections' to the acpi settings for Ubuntu 8.04
(thats the version I am using now).

Once I tweaked these settings, my laptop instantly began to cool down A LOT.

So for those of you having heat problems, check that link out lol. :popcorn:

~kutos to blackened for helping me out!

---

### Post by Tipped OuT on 2009-09-20
> **l3git.h4cker said:**
> Ha, so I googled for about a min., and found this:

[https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement)

I scrolled to the bottom, and found 'corrections' to the acpi settings for Ubuntu 8.04
(thats the version I am using now).

Once I tweaked these settings, my laptop instantly began to cool down A LOT.

So for those of you having heat problems, check that link out lol. :popcorn:

~kutos to blackened for helping me out!

lol Glad to hear you got it sorted it out.

---

