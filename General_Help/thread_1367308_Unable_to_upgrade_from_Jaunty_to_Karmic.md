---
title: "Unable to upgrade from Jaunty to Karmic"
date: 2009-12-29
forum: General Help
---

### Post by dberg on 2009-12-29
I have searched for a solution but so far haven't found anything.

I am currently running 9.04 and am trying to upgrade to 9.10. The problem is that there is no button to perform the upgrade in Update Manager. I already checked the settings to make sure that it is notifying of new releases. Also, running dist-upgrade does nothing.

Any help or suggestions would be appreciated.

---

### Post by Leppie on 2009-12-29
in a terminal run:
```
$sudo do-release-upgrade
```

---

### Post by dberg on 2009-12-29
That took care of it. Not sure why the upgrade wasn't showing up in manager.

Thank you.

---

