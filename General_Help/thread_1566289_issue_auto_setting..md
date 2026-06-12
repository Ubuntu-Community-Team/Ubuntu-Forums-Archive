---
title: "issue auto setting."
date: 2010-09-02
forum: General Help
---

### Post by dek8 on 2010-09-02
how do i add like a auto command on launching the os?

every time i boot in my mouse settings changes.. i have to issue a "xset m 0 0" in terminal to get it back... are there any ways to have like a script or some way to issue commands with the os or to have settings stick? tired of putting it back every time i log in.

also the xfce mixer gets reverted to zero volume every time i boot in and i have to up it back every time. :/

---

### Post by dcstar on 2010-09-02
> **dek8 said:**
> how do i add like a auto command on launching the os?

every time i boot in my mouse settings changes.. i have to issue a "xset m 0 0" in terminal to get it back... are there any ways to have like a script or some way to issue commands with the os or to have settings stick? tired of putting it back every time i log in.

For general booting stuff
```
/etc/rc.local
```
For loading the GUI: System-Preferences-Startup Applications

---

### Post by dek8 on 2010-09-02
could you explain a little on how to add for example xset m 0 0 ?
and is it possible to have my xfmixer set at some values i prefer through this? like for example volume at 50.

---

