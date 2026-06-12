---
title: "Virtualbox guest machine can't reach Internet"
date: 2010-02-12
forum: General Help
---

### Post by Objekt on 2010-02-12
I have a Windows XP virtual machine under Virtualbox PUEL 3.1.2.  I have always been able to browse the Web or do anything else I wanted over the network.

Suddenly, the guest XP machine can't reach the Internet any more.  There is no indication of any problem with the network connection.  I checked my router, and the virtual machine is indeed getting assigned an IP address.  So why can't it reach the internet?

Yes, the virtual network adapter is in bridged mode.  It always worked that way before.  I can see local network shares from the virtual XP machine, and even reach the Apache server running on the host OS (Ubuntu 9.10 64-bit).  What happened??

Also possibly significant: Even though the virtual XP machine is detected by the router & assigned an IP address, the printer attached to the virtual XP machine cannot be seen by another Windows machine (a real one, not virtual) on the network.  I never had a problem sharing the printer before.  I have to share it from a virtual Windows XP machine when I'm running Ubuntu because there are no Linux drivers available (it's a Winprinter).

---

### Post by Objekt on 2010-02-14
I "fixed" this by manually entering DNS server addresses instead of selecting "Obtain DNS server addresses automatically" in the virtual machine's network connection settings.  The virtual XP machine can now reach Web sites.

However, I don't consider this a real fix.  Things always worked fine before with the automatic DNS option.  Something else is wrong somewhere.

---

### Post by Objekt on 2010-02-17
Reinstalling NetworkManager seems to have fixed this problem the "good" way - no manual DNS settings on the guest machine required.

---

