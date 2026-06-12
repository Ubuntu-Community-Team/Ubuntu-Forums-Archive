---
title: "Enviroment variables"
date: 2011-10-03
forum: General Help
---

### Post by clwandling on 2011-10-03
I wanted a system wide environment variable (JAVA_HOME) and so I put it into /etc/environment  but it appears to get set after tomcat6 runs during the boot phase.  Is there a way to set system wide env var during the initial boot phase so that other processes that startup during boot up can see them?

---

### Post by dcstar on 2011-10-04
> **clwandling said:**
> I wanted a system wide environment variable (JAVA_HOME) and so I put it into /etc/environment  but it appears to get set after tomcat6 runs during the boot phase.  Is there a way to set system wide env var during the initial boot phase so that other processes that startup during boot up can see them?

The startup script for the particular process needs that set inside it.

---

