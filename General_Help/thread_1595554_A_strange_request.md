---
title: "A strange request"
date: 2010-10-13
forum: General Help
---

### Post by Colo2 on 2010-10-13
Hello

I had an idea for my homeserver, but I don't think it's possible. Maybe someone could tell me how/if I could do it?

I want to make it so that the server runs for, say 20 minutes idle, then goes into a sort of sleep mode. However, I want the server to be woken up out of it's sleep mode by net traffic. For example, if one of the PCs in my network requests to access it's samba shares, it wakes up giving the other PCs full access. 

The server will only shut down if the net traffic/LAN is idle. If no one is transferring files to it, or vice versa, it will NOT shut down.

Is this possible?

Thanks

---

### Post by 3Miro on 2010-10-13
What you need is called "Wake on Lan"

[http://en.wikipedia.org/wiki/Wake-on-LAN](http://en.wikipedia.org/wiki/Wake-on-LAN)

This is the only Ubuntu thread that I found on the subject, it is old (from 2006), however, I think it has been kept up-to-date (last post if very recent).

[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

---

### Post by Colo2 on 2010-10-13
> **3Miro said:**
> What you need is called "Wake on Lan"

[http://en.wikipedia.org/wiki/Wake-on-LAN](http://en.wikipedia.org/wiki/Wake-on-LAN)

This is the only Ubuntu thread that I found on the subject, it is old (from 2006), however, I think it has been kept up-to-date (last post if very recent).

[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

Thank you! it seems perfect :)

---

