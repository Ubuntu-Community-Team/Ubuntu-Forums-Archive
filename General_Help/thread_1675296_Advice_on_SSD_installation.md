---
title: "Advice on SSD installation"
date: 2011-01-25
forum: General Help
---

### Post by bouncingwilf on 2011-01-25
Now I realise that there has been quite a lot of advice handed out on the correct setup/installation of SSD'd but I'd get like to harness the collective wisdom of the hardware Guru's on this one as once I set it up, it's a two day journey away to go and put anything right!  
The Scenario: I need to change out a dodgy hard disk on a pal's boat that I believe is beginning to fail ( keeps banging into big lumps of water off SW Ireland) I intend to replace said HD with an SSD which I will pre-configure before I set off to see him and just swap out the drives. Now for stability reasons, I would prefer to pre-load the disk with 10.04 but as I understand it, I need the 2.6.35 kernel to enable trim support.
The PC  generally is in a data logging mode so there are significant quantities of writes but very few re-writes.

Question 1: with modern SSD's - a Corsair F60 in this case - Do I really need trim support? 
Question 2: Can I backport a 2.6.35 kernel to Lucid if required?
Question 3: If I use either 10.04 or 10.10, what extra parameters need to be set to ensure a reasonable lifetime for this disk?

Oh! one other constraint, Internet access in the wilds of West Cork is "Troubled" i.e. I really need to get it right before I set off!.

Many thanks in advance for any advice.

Bouncingwilf.

---

### Post by Smart Viking on 2011-01-25
1/2: No, but it's clearly a benefit, the drive will write faster for longer. You can install a newer kernel as a deb download when the system is installed.

---

