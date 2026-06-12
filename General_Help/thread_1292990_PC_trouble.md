---
title: "PC trouble"
date: 2009-10-16
forum: General Help
---

### Post by de_valentin on 2009-10-16
Hi,

Recently I bought some extra ram and a new video card for my pc. And somewhere around that time my computer started acting up. It reboots itself on the most inexplicable moments. For example when its doing nothing. Over time it got only worse, now it doesn't always get to the BIOS-screen and allready restarts.

The problem isn't in Ubuntu since it also happens in XP. Sometimes I play Crysis for 2 hours and nothing happens.

By now I am at a total loss, I've tried everything and nothing worked.


So here are the specs to my machine.

MSI P35 Neo-F ATX motherboard
Intel core 2 Quad Q6600 2,4
Asus ENGTS 250 GPU this used to be a Asus EN 8600 GTS
2x1 GB DDR2 Ram + (new) 2x2 GB DDR2 Ram
1x IDE (Ubuntu 64bit (Ext3) and swap)
1x SATA II 500 GB  (XP 32bit (NTFS) 100 GB + 400 GB (NTFS))
1x SATA II 500 GB (NTFS)

500 Watt (new it used to be 380 Watts) 


Before I put the new video card in I first removed the drivers in both XP
and Ubuntu. Then put in the card and (re)installed the drivers.


Here is what I've tried and checked so far 
1. voltages
2. Check if the ram is in the right slots 
3. back to 2 GB ram
4. only 4 GB of ram
5. Set the BIOS to its default settings


All I can think of is a total and clean install both windows and ubuntu,
where maybe the IDE would be changed for a Solid state drive just for the
operating system.

If there is anything else you want to know just ask.

---

### Post by CharlesA on 2009-10-16
First thing I would check would be if yer PSU is able to cope with the new video card.

Could be straining the PSU causing reboots.

Other then that, run a memtest. Make sure the RAM is ok.

---

### Post by de_valentin on 2009-10-17
Thanks for your reply, I forgot  to mention I already did a memtest I let it run 9 times 0 errors so that wasn't it.

I changed the PSU from 380 watts to 500, that was the first thing I did.

But just to be safe how would I check that?

---

### Post by PrePenguin on 2009-10-17
Well This is a classic symptom of a Power supply failure.. Maybe you acquired a faulty replacement? Did it get worse or any better after PSU replacement. becuase if its doing it before it even boots its either at bios level since that is the first thing read since it is embedded and no drivers etc are loaded. May have a serious IRQ conflict have any other new devices been added lately such as a printer/ USB device etc.? its a hardware or bios level problem.

---

### Post by P4man on 2009-10-17
narrow the problem down by either removing the new RAM or the ew videocard.
Did you connect the power cables to the new videocard? Unlike your old one, it probably requires one or two PCI power plugs, maybe you forgot to connect those?

[IMG]http://www.erodovcdn.com/erodov/reviews/guide/pci-e-connector/pci-e-power-connector-1.jpg[/IMG]

---

### Post by de_valentin on 2009-10-17
@PrePenguin
Changing the Power Supply did not help nor did it make things worse
I checked in windows to see if there were IRQ issues but (according to) windows there aren't any.

@P4man
I've tried without the new ram but no difference
For the GPU I did use one of the PCI-e plugs but there were 2 could I have chosen the wrong one?

---

### Post by P4man on 2009-10-17
> **de_valentin said:**
> 
@P4man
I've tried without the new ram but no difference
For the GPU I did use one of the PCI-e plugs but there were 2 could I have chosen the wrong one?

If there are two connectors on the card, you should connect both. (Although I wouldn't expect any trouble if you aren't stressing the card with games)

---

### Post by de_valentin on 2009-10-17
I can play games for hours without so much as a hiccup, but when its just turned on it might restart after 2 minutes totally random.

@P4mqn
There is only one connector on the video card but 2 on the PSU

---

