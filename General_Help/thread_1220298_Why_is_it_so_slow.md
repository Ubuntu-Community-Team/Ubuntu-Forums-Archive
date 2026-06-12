---
title: "Why is it so slow?"
date: 2009-07-22
forum: General Help
---

### Post by avacomputers on 2009-07-22
I have a one week installation of Ubuntu 9.04.
Specs:
Dell Dimension E520
Intel Core 2Duo
4GB Ram
250GB HD (Ubuntu Installed)
320HD External (Storage)
1TB HD Internal (Storage)
I don't have a Graphic Card (No money to buy one)

And Ubuntu seems really slow, especially Compiz Effects. Is there anything I can do without spending money.

---

### Post by rraj.be on 2009-07-22
Why dont you have a swap of 2GiB.  I think it doesnt worth much when you have a 4Gib Of RAM. But it may be a good try.

---

### Post by bnvdarklord on 2009-07-22
I guess i don't have a graphic card = i have an integrated graphic card on the mobo. Most of these cards are crappy, so i guess it cannot handle all the effects. The only free way is to remove all the special effects. The other non-free way is to buy a vga. It doesn't have to be a highend card, you can buy a cheap one  that can handle the effects.

---

### Post by avacomputers on 2009-07-22
> **rraj.be said:**
> Why dont you have a swap of 2GiB.  I think it doesnt worth much when you have a 4Gib Of RAM. But it may be a good try.

What do you mean?

> **bnvdarklord said:**
> I guess i don't have a graphic card = i have an integrated graphic card on the mobo. Most of these cards are crappy, so i guess it cannot handle all the effects. The only free way is to remove all the special effects. The other non-free way is to buy a vga. It doesn't have to be a highend card, you can buy a cheap one  that can handle the effects.

I thought about getting a VGA, just too many bills right now.

---

### Post by chriskin on 2009-07-22
in my opinion , you really have to turn compiz off and enable metacity's compositing.
after all, asking for effects on such a weak card is like asking from an old man to run at the olympics.
try metacity though, you might find it nice (and fast) enough

---

### Post by imtheguru on 2009-07-22
> I don't have a Graphic Card (No money to buy one)

And Ubuntu seems really slow, especially Compiz Effects. Is there anything I can do without spending money.

You've answered your own question. Turn down the graphics settings and the UI will react much quicker.

---

### Post by imtheguru on 2009-07-22
> **rraj.be said:**
> Why dont you have a swap of 2GiB.  I think it doesnt worth much when you have a 4Gib Of RAM. But it may be a good try.This suggestion is completely offtopic and unrelated.

---

### Post by avacomputers on 2009-07-22
> **imtheguru said:**
> This suggestion is completely offtopic and unrelated.

OOPS I created a 2GB Swap.

---

### Post by chriskin on 2009-07-22
it might be slightly offtopic, but it is a good idea to have a swap. 
so no harm done :)

---

### Post by Whiffle on 2009-07-22
Which graphics chipset/card does your computer have?  Even my old laptop can run compiz (Intel GMA915), I would be very surprised if anything newer couldn't run it.

---

### Post by rraj.be on 2009-07-22
i thought he was also running system slower in terms of process to along with the graphic effects. .

---

### Post by chriskin on 2009-07-22
it is also up to how many compiz effects , and what effects, he uses

---

### Post by avacomputers on 2009-07-22
> **Whiffle said:**
> Which graphics chipset/card does your computer have?  Even my old laptop can run compiz (Intel GMA915), I would be very surprised if anything newer couldn't run it.

-display:1 UNCLAIMED
             description: Display controller
             product: 82G965 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0

---

### Post by Whiffle on 2009-07-22
Could you post the output of this command?  I have a theory:

  lspci -nn | grep VGA

---

### Post by avacomputers on 2009-07-22
> **Whiffle said:**
> Could you post the output of this command?  I have a theory:

  lspci -nn | grep VGA

00:02.0 VGA compatible controller [0300]: Intel Corporation 82G965 Integrated Graphics Controller [8086:29a2] (rev 02)

---

### Post by Whiffle on 2009-07-22
Hmm.  My theory is that you may be affected by the intel driver bug that cropped up in the most recent release.  One of the ways to fix that is to roll back the driver to the last version.  According to the link below, yours might not be affected, but if you're willing it may be worth trying.  Theres a howto in the link, and I'd be more than happy to answer questions.

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by Whiffle on 2009-07-22
That said, this might be worth going through:

[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)

---

### Post by avacomputers on 2009-07-22
> **Whiffle said:**
> Hmm.  My theory is that you may be affected by the intel driver bug that cropped up in the most recent release.  One of the ways to fix that is to roll back the driver to the last version.  According to the link below, yours might not be affected, but if you're willing it may be worth trying.  Theres a howto in the link, and I'd be more than happy to answer questions.

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

Will report back.

---

### Post by avacomputers on 2009-07-22
It says I don't have permission to save that.

---

### Post by Whiffle on 2009-07-22
> **avacomputers said:**
> It says I don't have permission to save that.


I assume you're talking about /etc/apt/sources.list

Two ways to do this (depending on whether you prefer using the terminal, or the gui). 

Gui:

System > Administration > Software Sources > Third-Party Software (Tab), click "+ Add".  Then copy paste the two lines there.

Terminal:

gksudo gedit /etc/apt/sources.list 

then copy, paste, and save.


Welcome to the world of Linux permissions :)

---

### Post by XxTrAnzErxX on 2009-07-22
Hmm actually i dont think a new computer with an integrated grafics card should have any issues running Compiz effects. My compute has an integrated Intel R Pro Grafics blah blah, and it works just fine!... i can use most of the effects, including that dam cube haha, but honestly the only time i had problems with ubuntu being slow, was when i tried to enable a certain effect in Compiz, I would also recommend you disable all the extra special effects to see if that could be the issue. Just try it and see how it compares...

---

### Post by avacomputers on 2009-07-22
> **Whiffle said:**
> I assume you're talking about /etc/apt/sources.list

Two ways to do this (depending on whether you prefer using the terminal, or the gui). 

Gui:

System > Administration > Software Sources > Third-Party Software (Tab), click "+ Add".  Then copy paste the two lines there.

Terminal:

gksudo gedit /etc/apt/sources.list 

then copy, paste, and save.


Welcome to the world of Linux permissions :)

Done, Done and Done. I like using the Terminal, but don't know the commands. :confused: I will let you know if I notice a difference.

---

