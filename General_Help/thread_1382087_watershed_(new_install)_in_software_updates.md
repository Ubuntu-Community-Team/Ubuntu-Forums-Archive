---
title: "watershed (new install) in software updates"
date: 2010-01-15
forum: General Help
---

### Post by jordilin on 2010-01-15
I just booted up Karmik and the update manager pointed out in "Distribution updates" section a new package called "watershed (New install)" with info: reduce superfluous executions of idempotent command. 
Anyone know what is that package and its purpose? and why software updates suggests to install that new package?

---

### Post by fergus on 2010-01-16
I dug into it a bit and found out cryptsetup now depends on watershed.  watershed is not new, just cryptsetup's dependency on it .  It prevents two things from happening in parallel to prevent data corruption.  shouldn't be a problem.... Hope this helps.

fergus

---

