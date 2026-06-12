---
title: "Does the terminal program &quot;locate&quot; search through what the program &quot;tracker&quot; indexes?"
date: 2011-02-02
forum: General Help
---

### Post by s3a on 2011-02-02
Does it? It seems to but I want to be sure.

P.S.
I find that the graphical (Places => Search for files) utility is inferior to locate.

---

### Post by luigi_mb on 2011-02-02
I use beagle, not tracker. I think with beagle it's possible to have it search the locate db. I don't know about the reverse, but you can try the documentation for locate (man locate). 

/luigi

---

### Post by DaithiF on 2011-02-03
No, locate searches a database which is created/updated by the updatedb command.

updatedb is run once per day via a job in cron.daily (see /etc/cron.daily/mlocate)

Note that there are various versions of locate -- on ubuntu mlocate is the variant used, so the locate command is symlinked to mlocate via /etc/alternatives.  And the corresponding updatedb command is updatedb.mlocate.

---

