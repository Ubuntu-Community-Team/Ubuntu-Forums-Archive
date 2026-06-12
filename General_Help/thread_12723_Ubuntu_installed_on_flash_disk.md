---
title: "Ubuntu installed on flash disk"
date: 2005-01-26
forum: General Help
---

### Post by kerskine on 2005-01-26
Greetings...what would be some of the issues in installing Ubuntu onto flash memory.  At first glance, it could be simply done by putting directories that are "read from mostly" on the flash, leaving directories that tend to be "written to mostly" on spinning media:

[INDENT]/boot - yes
/proc - no
/var - no
/tmp - no
/usr - yes
/home - yes
/opt - yes
(etc.)
[/INDENT]

Is there anything else that should be considered before installing?  Thanks in advance!

---

