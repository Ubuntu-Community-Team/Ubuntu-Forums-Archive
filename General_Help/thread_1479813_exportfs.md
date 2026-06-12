---
title: "exportfs"
date: 2010-05-11
forum: General Help
---

### Post by metro23man on 2010-05-11
What happened to the map_static option in the exportfs file?  Is there another way to map user ID's between different systems.

I'm trying to use autofs to access my files and directories on different systems.  Unfortunately I have different UID's on each of these systems which leads to access problems?

Can anybody please point me in the right direction?  Is there a simple way to configure the systems to allow access?

Thanks

---

### Post by rnerwein on 2010-05-11
hi
beleave me - the only way to handle different UIDs and GIDs on different systems is to use
LDAP or NIS. every think else will be a "Ticket to Hell" in the future.
ciao

---

