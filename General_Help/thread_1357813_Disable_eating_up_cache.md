---
title: "Disable eating up cache"
date: 2009-12-17
forum: General Help
---

### Post by StrangeWill on 2009-12-17
Now I know this is a good feature for Ubuntu, but I run some virtual servers and I don't want them all to eat up all available RAM, but only eat up what they need.


Is there a way to let the system free up more RAM, and only cache things that are more commonly accessed? Being as some virtual machines may share RAM, we'll have issues when they both boot and try to eat up all available RAM (more RAM than the host system has).

---

### Post by dcstar on 2009-12-17
> **StrangeWill said:**
> Now I know this is a good feature for Ubuntu, but I run some virtual servers and I don't want them all to eat up all available RAM, but only eat up what they need.


Is there a way to let the system free up more RAM, and only cache things that are more commonly accessed? Being as some virtual machines may share RAM, we'll have issues when they both boot and try to eat up all available RAM (more RAM than the host system has).

Like any OS, you give them minimal RAM and set them to use paging (swap).

You do this via whatever VM environment you are using, it has nothing to do with the host OS.

---

