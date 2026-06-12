---
title: "Adding Printer in 11.10"
date: 2011-10-14
forum: General Help
---

### Post by merlinus on 2011-10-14
When I try to add a printer, I get this error message:

FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall.

I have never had such a thing happen with previous versions of ubuntu.  I was always able to add ipp:// etc. to the setup dialog.

What is going on????

---

### Post by crdlb on 2011-10-14
Use system-config-printer. The new printers capplet doesn't have good support for manual configuration yet.

---

### Post by merlinus on 2011-10-14
Thanks!!!

---

### Post by neu5eeCh on 2011-12-16
Trying to install system-config-printer, but can't. Claims that package is missing, obseleted or only available from another source. If I try to uninstall system-config-printer-ghome, apt-get threatens to remove Unity desktop.  WTF Ubuntu?

**Edit:** OK, ALT+F2, then type system-config-printer. What a PITA.

---

