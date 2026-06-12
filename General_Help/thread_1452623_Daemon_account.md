---
title: "Daemon account?"
date: 2010-04-12
forum: General Help
---

### Post by MovingAlong on 2010-04-12
Hi all,

Ubuntu 9.10

I've installed ClamAV daemon, but unfortunately I'm receiving a 'Permission Denied' error. Having read around it appears the likely reason is that the account the daemon is running under doesn't have permission to access the file trying to be scanned - which makes sense.

How could I alter the account the daemon is running under? I'm only using this for some limited testing, so running under my normal account would be fine... although root would also be an option - unless someone wants to tell me different!?! :)

Cheers,
MA

PS. Is there a good link to any article describing more about daemons? - first time I've really encountered them and wouldn't mind some extra background knowledge

**Edit - found a solution which didn't involve changing the user account or file permissions. Documented in the manual pages is the option for --fdpass. I'll leave the question in place for future sessions.**

---

