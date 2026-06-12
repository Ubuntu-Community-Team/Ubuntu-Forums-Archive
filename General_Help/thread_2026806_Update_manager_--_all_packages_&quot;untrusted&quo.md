---
title: "Update manager -- all packages &quot;untrusted&quot;"
date: 2012-07-15
forum: General Help
---

### Post by haresear on 2012-07-15
I'm running Ubuntu 12.04 Gnome classic no effects. When I try to install any updates I get an error message to the effect the update would require installing untrusted packages. This happens no matter what packages I select in the update manager window. Is there some problem with authentication? How do I fix it? Thanks for any help.

---

### Post by jmfal on 2012-07-15
It's just legal jargon, I wouldn't worry about it.

---

### Post by haresear on 2012-07-15
The update manager doesn't offer the option to ignore verification, so it refuses to update. I probably can force update via apt-get, but I'd like to fix the update manager.

---

### Post by haresear on 2012-07-15
Okay, I removed (deselected) Recommended Updates in the update manager settings, then reran apt-get update and upgrade, and got no complaint about unverified packages. Apparently if there is one unverifiable package in the list of available update packages, it will throw an unverifiable package error message even if that package is not selected. I'm concluding there must be an unverifiable package in the recommended upgrade package list.

Nevermind -- I restored Recommended Updates in settings, then reloaded, and update manger updated without any error messages. I have no idea what fixed it. The untrusted error was persistent for the past several days.

---

