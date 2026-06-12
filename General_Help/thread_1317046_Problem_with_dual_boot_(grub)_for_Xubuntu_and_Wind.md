---
title: "Problem with dual boot (grub) for Xubuntu and Windows XP"
date: 2009-11-06
forum: General Help
---

### Post by tomsax on 2009-11-06
I had Windows XP set up on my laptop.  I installed Xubuntu to dual boot but when it enters grub I can't use the arrow keys to choose Windows XP.  If I just wait it will go into Xubunto on the timer but if I press an up or down arrow it will then get blocked.  No response from any key and I have to turn it off at power.

I tried again reintalling windows XP again on half the drive leaving the other half free, then reintalling Xubuntu on the other half, but same problem.

I don't know if I can reintall grub in Xubuntu or whether there is another fix.  

Any ideas?

Tom

---

### Post by undecim on 2009-11-06
Did you install Xubuntu 9.10 or an earlier version? 9.10 uses a different version of Grub

---

### Post by tomsax on 2009-11-06
Yes, it was the latest one 9.10.  Should I try a previous version of Xubuntu.  I thought the latest would be the best but maybe it has some issues to be ironed out!

---

### Post by undecim on 2009-11-06
If you log into Xubuntu, you should be able to get the old version of Grub by running the command "sudo aptitude install grub" in a terminal.

I'm not sure, but I think it will give you the option at that time to choose either Grub or Grub2 as your boot loader. Just make sure that you choose Grub.

EDIT: Actually, just tested this on my machine... installing Grub replaces Grub2

---

### Post by pqwoerituytrueiwoq on 2009-11-06
if you have a copy of an old cd/iso you can boot it 
open a terminal
type 
sudo grub
root (hd0,1)
setup (hd0)
quit
sudo reboot

NOTE i assumed xubuntu is on the second partition of your 1st hard drive 
im not sure how to change teh default os in the new gub

---

### Post by undecim on 2009-11-06
> **pqwoerituytrueiwoq said:**
> if you have a copy of an old cd/iso you can boot it 
open a terminal
type 
sudo grub
root (hd0,1)
setup (hd0)
quit
sudo reboot

NOTE i assumed xubuntu is on the second partition of your 1st hard drive 
im not sure how to change teh default os in the new gub

That's a bad idea. First of all, it won't fix anything, because its not a corrupted grub install, because the problem persisted after reinstallation. Second, if you install the Grub 1 MBR where Grub 2 is already installed, Grub 1 won't have its configuration files.

---

### Post by ranch hand on 2009-11-06
If you go to grub-legacy you should take a look at the link in my sig.

There is a link there to a "How To" on that procedure.  There are a couple of pitfalls you want to avoid.

---

### Post by tomsax on 2009-11-06
> **undecim said:**
> If you log into Xubuntu, you should be able to get the old version of Grub by running the command "sudo aptitude install grub" in a terminal.

I'm not sure, but I think it will give you the option at that time to choose either Grub or Grub2 as your boot loader. Just make sure that you choose Grub.

EDIT: Actually, just tested this on my machine... installing Grub replaces Grub2

I ran the command but I got the same. I also ran the command from Terminal after booting from the live CD and it was the same.

I think I will try the last version of Xubuntu. I have an old CD of a version from a year ago but there seems some doubt above whether installing from that and using another grub would work or not.

By the way the version I installed again called itself grub not grub2 and there was no choice of any other.

I'll wait some minutes before installing another CD.  I'm sorry but I find these sort of glitches frustrating.

---

### Post by tomsax on 2009-11-06
> **ranch hand said:**
> If you go to grub-legacy you should take a look at the link in my sig.

There is a link there to a "How To" on that procedure.  There are a couple of pitfalls you want to avoid.

Thanks for all the suggestions guys.  

I tried update-grub but that didn't work. I'm trying the older version of Xubuntu now.  Hope I don't have the same problem.

---

### Post by tomsax on 2009-11-11
Just an update:  installed the last version and it was no problem with dual boot.

---

