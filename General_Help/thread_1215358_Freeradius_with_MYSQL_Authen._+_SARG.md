---
title: "Freeradius with MYSQL Authen. + SARG"
date: 2009-07-17
forum: General Help
---

### Post by Jarr0d on 2009-07-17
I have a freeradius server using mysql database for authentication. It is on the same server as a Dansguardian/Squid proxy server. I use SARG to view the reports of internet usage, currently this is reporting by IP address. Is it possible for me to have it log by the username from the MYSQL db?

---

### Post by Jarr0d on 2009-07-30
I resolved this by pointing SARG to the squid access logs, instead of the DansGuardian access logs.
I had it looking at the DG logs for a proxy built I had built.

---

