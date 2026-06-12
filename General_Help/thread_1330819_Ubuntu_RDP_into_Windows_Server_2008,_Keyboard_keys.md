---
title: "Ubuntu RDP into Windows Server 2008, Keyboard keys not working"
date: 2009-11-18
forum: General Help
---

### Post by shirubia on 2009-11-18
Hi all,

So I'm using Ubuntu 9.04 to Remote Desktop into a Windows Server 2008 R2. during my RDP session, when I try to use certain keys on my keyboard they don't show up on Windows. 

The following keys dont work: @, :, / (turns into a 7), }, { 

I run RDP through the terminal: rdesktop 192.xxx.xxx.xxx -k -f etc etc

Anyone run into the same issue? Also, for some reason my mouse turns black?!?

Any help is much appreciated!

---

### Post by dcstar on 2009-11-18
> **shirubia said:**
> Hi all,

So I'm using Ubuntu 9.04 to Remote Desktop into a Windows Server 2008 R2. during my RDP session, when I try to use certain keys on my keyboard they don't show up on Windows. 

The following keys dont work: @, :, / (turns into a 7), }, { 

I run RDP through the terminal: rdesktop 192.xxx.xxx.xxx -k -f etc etc

Anyone run into the same issue? Also, for some reason my mouse turns black?!?

Any help is much appreciated!

Microsoft continually muck around with the RDP protocol to patch up security holes that are exposed in it, they probably have made more changes that the client is now incompatible with.

---

### Post by shirubia on 2009-11-19
> **dcstar said:**
> Microsoft continually muck around with the RDP protocol to patch up security holes that are exposed in it, they probably have made more changes that the client is now incompatible with.

Dang so no quick configuration fix?

---

