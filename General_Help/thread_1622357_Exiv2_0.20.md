---
title: "Exiv2 0.20"
date: 2010-11-15
forum: General Help
---

### Post by ozzyprv on 2010-11-15
How can I upgrade from Exiv2 0-19 (installed in Maverick) to 0.20?

Thanks

---

### Post by ozzyprv on 2011-01-02
ping!

---

### Post by QLee on 2011-01-02
If you had a .deb for it, you'd have to force the version to install if it isn't in the repos and that version might have dependencies which wouldn't be satisfied with a Maverick install, so then you would have to install all of the dependencies which might end up breaking something about the Maverick install and ending up in what is often referred to as "dependency hell". If someone has backported the version to one for Maverick, then that might work if you trust the backport developer. If there aren't many dependencies, you might have good luck and you'd have to decide if the feature you want is worth the trouble. Or, you could try compiling your own from source code.

---

