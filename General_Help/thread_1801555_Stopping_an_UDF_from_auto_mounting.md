---
title: "Stopping an UDF from auto mounting?"
date: 2011-07-10
forum: General Help
---

### Post by BeaverDono on 2011-07-10
I have one of those lovely Western Digital external hard drives and it seems to have an UDF "partition" on the hard drive itself. I cannot format it, remove it from the hard drive itself, or  disabling the UDF seems to be a no go once its popped into a Linux distribution of any kind.

So my question is, is it possible to stop the UDF from even auto mounting at all?

System
Ubuntu 10.10 Maverick Meerkat

**EDITED:**
Giving a bit more of a follow up as I work on this situation. 
- Since an UDF has no UUID #, no dice with using /etc/fstab
- Cannot use an autorun feature

---

### Post by BeaverDono on 2011-07-11
Seems like it is impossible to prevent the UDF from auto mounting. I am probably going to have to take this a step further and remove the UDF forcefully. I am keeping this thread open for now until I (or someone else) resolves this issue.

---

### Post by pqwoerituytrueiwoq on 2011-07-11
can creating a new partition table get rid of it? (under device in gparted)
be sure **not** to do that on the** wrong** disk
backup everything on the target drive you want to keep or you will loose it

---

