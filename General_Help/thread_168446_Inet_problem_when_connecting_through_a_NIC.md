---
title: "Inet problem when connecting through a NIC"
date: 2006-04-30
forum: General Help
---

### Post by TimR1988 on 2006-04-30
Hi.
I'm having some weird problems with Internet access on Ubuntu 5.10.

My Internet connection is through a router which I'm connected to with a standard ethernet cable.  Ubuntu detected my NIC card fine -- no need for drivers.

Thing is, some things work and some things don't.  Mozilla Firefox works (though for a 1meg connection it feels like 56k) but nothing else does (Gaim, Thunderbird, nothing).

I went into the settings for eth0 and it's obtaining an IP through DHCP.  I have XP on a separate partition and it is also set for DHCP and everything there works fine.

Any ideas why some things are working (albeit slowly) and other things aren't?  I'm thinking of setting eth0 to use a static IP rather than the DHCP.  I assume I need to edit a config file for this.

Thanks in advance for any help with this.  I'm a windows user finally wanting to make the switch to linux :)

---

