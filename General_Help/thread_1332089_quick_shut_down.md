---
title: "quick shut down"
date: 2009-11-20
forum: General Help
---

### Post by shazel on 2009-11-20
how to disable shut down time notification in ubuntu 9.10.
thanks

---

### Post by wilee-nilee on 2009-11-20
Right click on the panel then add to panel then add the shutdown in the menu. This will shut down without the 60 second time out.

---

### Post by shazel on 2009-11-20
thanks dear:popcorn:

---

### Post by lavinog on 2009-11-20
```

gconftool-2 -s '/apps/indicator-session/suppress_logout_restart_shutdown' --type bool true
```

---

