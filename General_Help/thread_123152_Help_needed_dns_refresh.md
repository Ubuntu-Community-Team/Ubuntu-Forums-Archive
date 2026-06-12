---
title: "Help needed: dns refresh?"
date: 2006-01-29
forum: General Help
---

### Post by kverde on 2006-01-29
An IP address changed to a website that I use for work.  For some reason, Ubuntu keeps resolving the name to the OLD ip.  I dual boot into windows and the name resolves properly to the new IP.  Its been over 24 hours since the change, but it still resolves to the wrong (old) IP.

Any tips on how to refresh or flush the local dns cache (if that is what the problem is)?

Thanks for the help!

---

### Post by dcstar on 2006-01-29
[QUOTE=kverde]An IP address changed to a website that I use for work.  For some reason, Ubuntu keeps resolving the name to the OLD ip.  I dual boot into windows and the name resolves properly to the new IP.  Its been over 24 hours since the change, but it still resolves to the wrong (old) IP.

Any tips on how to refresh or flush the local dns cache (if that is what the problem is)?

Thanks for the help![/QUOTE]
What DNS server does the Ubuntu system use (cat /etc/resolv.conf) compared to Windows?

---

### Post by kverde on 2006-01-29
Well, it finally started going to the correct address.  I feel like it was caching it somewhere, but all is good now.  Thanks for the reply.

---

