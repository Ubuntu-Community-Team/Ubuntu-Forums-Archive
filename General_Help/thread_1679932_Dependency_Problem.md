---
title: "Dependency Problem"
date: 2011-02-01
forum: General Help
---

### Post by Finalfantasykid on 2011-02-01
I am having problems applying an update from Update Manager.  Upon further investigation, I get this after running: sudo aptitude dist-upgrade

```

The following packages will be upgraded: 
  upstart{b} 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 211kB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  upstart: Breaks: libc6 (< 2.12.1-0ubuntu10.2) but 2.12.1-0ubuntu10.1 is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     upstart [0.6.6-3 (maverick, now)]
```

---

### Post by TeoBigusGeekus on 2011-02-01
Why would you want to upgrade to natty now?

---

### Post by Finalfantasykid on 2011-02-01
I'm not trying to.  I just read somewhere that I can do dist-upgrade to fix these dependency problems.

---

### Post by oldos2er on 2011-02-01
dist-upgrade is something of a misnomer; it's equivalent to full-upgrade. To the OP: I'd go with keeping upstart at its current version for now, and try again in a day or two.

---

### Post by Finalfantasykid on 2011-02-02
Thanks, I tried again today and it worked :D

---

