---
title: "/var/crash/*.crash rights"
date: 2010-02-27
forum: General Help
---

### Post by dino99 on 2010-02-27
i'm having problem reporting some silent crashes as they are own by root. Looking at /var/crash i've found 11 crashes that have not been automaticaly reported by apport, and 6 of them are own by root, so when i double click on them to report, i cant because i'm not the owner.

That seem curious to me: every crash about linux-image or _usr_sbin or _usr_share are locked; but _usr_lib or _usr_bin are not.

---

### Post by rnerwein on 2010-02-27
> **dino99 said:**
> i'm having problem reporting some silent crashes as they are own by root. Looking at /var/crash i've found 11 crashes that have not been automaticaly reported by apport, and 6 of them are own by root, so when i double click on them to report, i cant because i'm not the owner.

That seem curious to me: every crash about linux-image or _usr_sbin or _usr_share are locked; but _usr_lib or _usr_bin are not.

hi
i'll say that the core files, when made by root e.g. system core, it is absolute nessary that it can only read by the owner of program where it comes from. can you emagine whats all inside in those core files ( espacially in system cores ) !
see also: man apport-bug

on the oter way - are the core files which are owned by root may be comes from commands where the "s" bit is set ? this should be an explanation for me.
ciao

---

### Post by dino99 on 2010-02-27
> **rnerwein said:**
> hi
i'll say that the core files, when made by root e.g. system core, it is absolute nessary that it can only read by the owner of program where it comes from. can you emagine whats all inside in those core files ( espacially in system cores ) !
see also: man apport-bug

on the oter way - are the core files which are owned by root may be comes from commands where the "s" bit is set ? this should be an explanation for me.
ciao

maybe you have missed something; i'm talking about silent crashes, they don't have to be root owned.

---

