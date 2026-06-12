---
title: "can't update - broken package"
date: 2009-07-15
forum: General Help
---

### Post by boilertnerb on 2009-07-15
9.04 on an intel macbook...

about a week ago, Update Manager prompted me to install a bunch of updates, including an ubuntu security update, as well as a bunch of other lib* updates. i believe i am able to download them all, but when i go to install them, i get this error:

"E: /var/cache/apt/archives/lsb-base_4.0-0ubuntu0.9.04.1_all.deb: trying to overwrite `/etc/lsb-base-logging.sh', which is also in package splashy"

so the update can't finish. and now if i try to go to update again, it says:

"You have 1 broken package on your system!

Use the "Broken" filter to locate it."


Any idea what's causing this, and how to fix it? Thanks in advance.

---

### Post by eBoxNet on 2009-07-15
try this :

System/Administration/Synaptic Package Manager, you should see there a tab called 'Broken'.

---

### Post by boilertnerb on 2009-07-16
that fixed the broken package, but i still cannot install all of the new updates. i continue to get the same error.

---

