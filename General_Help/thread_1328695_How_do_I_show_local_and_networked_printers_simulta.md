---
title: "How do I show local and networked printers simultaneously?"
date: 2009-11-16
forum: General Help
---

### Post by dfrossar on 2009-11-16
I'm helping configure printers in an environment in which Linux users receive a list of printers (and automatically receive drivers) from a Linux print server specified in their local /etc/cups/client.conf line, something like:

ServerName server.Domain.EDU

My problem: When client.conf exists, users see only those network printers. No matter what I configure on the local machine with CUPS, only the printers on the server appear when users try to print.

When client.conf is deleted, the printers specified in the local CUPS settings reappear.

I have tried manually installing each of the network printers manually, specifying the server name and printer queue but for some reason that doesn't work. The only "solution" I've found is to install each of those printers to print directly to the printer, bypassing the server, via IPP. Not an ideal solution from a management perspective. (And, of course, if a printer is changed, the user won't automatically get new drivers.)

My main question: Is there a line of text, a trick of some kind, that would allow a user to configure Ubuntu (8.04 in this case) to see both the server's list of printers and those printers configured locally in CUPS at the same time?

---

