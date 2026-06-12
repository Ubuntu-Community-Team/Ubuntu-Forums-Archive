---
title: "ZEN3300E GIG NIC Odd problem"
date: 2006-03-06
forum: General Help
---

### Post by jalm111 on 2006-03-06
I bought this Zonet 10/100/1000 NIC (realtek chip) and an ABS (NW-111-8P) 10/100/1000 switch. When I installed the NIC and booted up the system everything worked fine, the drivers (r8169) worked with no issue and the NIC was pulling an IP (both static and DHCP). I was also able to restart the system as many times as I wanted and the NIC still worked fine.

Once I shut off the system for a prolonged period of time (couple hours) and started it back up the NIC stopped pulling an IP (both static and DHCP). If I take the NIC out and than reinstall it everything works fine again untill I shut the system off for a period of time, than the same exact thing happens.

I also left the system on for a long period of time (week or so) and the NIC was working without a problem during that time untill I shut it off for a period of time, then the same problem occures.

Anyone have any insight on this? I'm thinking about just returning it to NewEgg and getting a better one but I'd like to try and fix this myself first.

I was also not able to sucesfully compile the drivers from realtek's web site (Zonet only offers 2.4.x kernel drivers and I run 2.6.x) and have been using the built in Ubuntu drivers.

System: Ubuntu 5.10 Breezy Badger  2.6 Kernel   Gnome

---

### Post by jalm111 on 2006-03-06
Bump. Anyone?

---

### Post by jalm111 on 2006-03-14
So after some tinkering I pretty much narrowed it down to a hardware problem.

Ordered an ABS network card (same Realtek chipset and same r8169 module) and now everything works fine  :)

Just wanted to post so anyone else with this problem might find this thread helpful.

---

