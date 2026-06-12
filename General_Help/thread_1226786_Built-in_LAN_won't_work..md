---
title: "Built-in LAN won't work."
date: 2009-07-29
forum: General Help
---

### Post by LinuxFox on 2009-07-29
I don't know if this is the correct forum,  if it is, please move it.  I want to know something about built in LAN port.  Today I had to replace the power supply to my computer, and after replacing it, the built in LAN port I used for the Internet won't work.  On both Ubuntu and Windows XP.

Yesterday, we had a bad storm, and I don't know if it plays a role with this.  I don't know much about motherboards, so I'd just like to know why isn't it working?

Right now I'm on my mother's computer, installing Ubuntu for her and setting stuff up, which is why I'm online now.  Some help please.

---

### Post by MasterNetra on 2009-07-29
It isn't. You want it in the "Networking & Wireless" forum. And did you make sure you where grounded before you started working in the PC? Otherwise if not you could of a small jolt of static electricity, even if you didn't feel it, it can still be strong enough to cause some damage. *May not be a certified tech, but I did have a year of electronics training before switching major*

---

### Post by dragos240 on 2009-07-29
> **masternetra said:**
> it isn't. You want it in the "networking & wireless" forum.
+1

---

### Post by LinuxFox on 2009-07-29
> **MasterNetra said:**
> It isn't. You want it in the "Networking & Wireless" forum.Thanks, I wasn't too sure since it's more of a hardware thing, instead of Ubuntu.  Also it's happening in Windows.

I'll wait until a mod moves this, there's no need to create another one.

---

### Post by MasterNetra on 2009-07-29
lol looks like Mod decided to toss into general help

---

### Post by synapsys on 2009-07-29
If you had a **surge protector** or a **ups**(uninterruptable power supply) between your computer and the wall socket you would not have to worry about storms (power surges). 

You might want to check the simple things first. 

1. Check the led lights near the ethernet port.
2. Swap ethernet cables.
3. Try a different port on the router.
4. Open a terminal window and type:

```
lspci | grep Ethernet 
```and see what comes up.

---

### Post by LinuxFox on 2009-07-30
> **synapsys said:**
> If you had a **surge protector** or a **ups**(uninterruptable power supply) between your computer and the wall socket you would not have to worry about storms (power surges). 

You might want to check the simple things first. 

1. Check the led lights near the ethernet port.
2. Swap ethernet cables.
3. Try a different port on the router.
4. Open a terminal window and type:

```
lspci | grep Ethernet 
```and see what comes up.I checked the cables, the eithernet port's light didn't go on.  When I did terminal code I got this...

```
tailsy@tailsy-desktop:~$ lspci | grep Ethernet
00:0a.0 Ethernet controller: Lite-On Communications Inc LNE100TX [Linksys EtherFast 10/100] (rev 25)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
```VIA eithernet port is the built in LAN one that I've been using.  The other eithernet port is a card that I found in an old machine we had.  That card works as I'm online now.

Being built-in to my motherboard, I can't understand what went wrong.  It was working fine last time I used my computer, it stopped working when I replaced the power supply (the old one won't work anymore).  Should I be concerned over my motherboard?

---

### Post by synapsys on 2009-08-01
That's what it sounds like. Unless you got a weaker power supply than you had before? If the power connection to the motherboard was faulty... Your computer wouldn't boot.... Sometimes you can see burnt spots on the motherboard or blown capacitors but if you can use a network card and it works..... I would 't worry about it.

---

### Post by colin.p on 2009-08-02
I would say that the storm blew out your network port. You're lucky, it usually takes out a lot more than that. Even with a UPS or surge protector, a direct lightning strike will happily travel down the wire right into your house, through the cable or DSL modem and quite easily go through any surge protector right into your computer (whole house surge protection is far better). The best policy is to unplug the ethernet cable from the modem to the router when a storm is detected. 
I also use a cheap router, that usually takes the brunt of the hit and saves the computer, but when you are dealing with a bazillion volts.....

---

### Post by synapsys on 2009-08-03
Direct lightning strike?!?!?! 

...glad I live in california.

---

