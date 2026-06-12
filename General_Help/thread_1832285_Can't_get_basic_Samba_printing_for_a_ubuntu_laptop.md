---
title: "Can't get basic Samba printing for a ubuntu laptop"
date: 2011-08-24
forum: General Help
---

### Post by silverrope on 2011-08-24
I have Lucid Lynx running on a desktop as a Samba server. The machine has two printers: one is a Brother that uses the driver from the cups database that comes with the ubuntu distribution and the other is a Canon in which I installed the driver from the Canon website. Both printers work and I can see them using lpstat -a.

The client is a Lucid Lynx laptop. The smbbrowser finds the two samba shares. When I connect, the client searches for the drivers; here, I assume it would try to download the drivers from the samba server. Unfortunately, it does not find them and instead it tries to search locally in the cups database which of course raises a problem with the Canon printer.

How do I get the client to use the Samba print server?

---

