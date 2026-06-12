---
title: "Jaunty 64 bit: Locks up randomly"
date: 2009-06-30
forum: General Help
---

### Post by donovanh on 2009-06-30
Hi,

I've recently upgraded from 32 bit to 64 bit jaunty, and am finding that the computer locks up approximately once or twice per day. A hard reset is the only option.

I am quite new to ubuntu and don't know where to start looking for possible causes. Any ideas?

D

---

### Post by akakingess on 2009-06-30
> **donovanh said:**
> Hi,

I've recently upgraded from 32 bit to 64 bit jaunty, and am finding that the computer locks up approximately once or twice per day. A hard reset is the only option.

I am quite new to ubuntu and don't know where to start looking for possible causes. Any ideas?

D
Can you give us some more details, such as what you are doing when it locks up, the hardware in your system, etc. I run 64-bit Juanty and have not had one problem, so we need to start narrowing down where the problem exists.
 
akakingess

---

### Post by gergos on 2009-08-22
I am having the same issue with locking up randomly.  I noticed it would mess the screen up when it did so, before totally locking up.  I thought it might have something to do with the graphics driver (nvidia's most recent). I tried to go back to the previous one, and it didn't help.

I noticed that it mostly happens when I open evolution, have a web page up, or try to do more than one thing at a time - which is all day for me!

Its getting VERY annoying that a crash report won't get generated when this happens so that we can look at what is really going on.  The system and kernel logs are clean when I boot back up and check on it. ??? Confused!!:confused:

---

### Post by P4man on 2009-08-22
sounds like a kernel issue.. do the keyboard leds blink when it locks up?
It could be worth trying an older or more recent kernel if you got any in your grub menu. Or install one through synaptic.

---

