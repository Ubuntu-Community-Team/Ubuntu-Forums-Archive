---
title: "modify firefox places.sqlit"
date: 2010-05-19
forum: General Help
---

### Post by jmitn on 2010-05-19
Im interested in modifying the times a site was visited in ubuntu 10 firefox 3 any help?

---

### Post by lovinglinux on 2010-05-19
Use [SQLite Manager](https://addons.mozilla.org/en-US/firefox/addon/5817) extension.

Make a copy of places.sqlite for editing, since you probably won't be able to change the one in your profile while using Firefox. A backup copy is also recommended. After applying the changes, close Firefox and copy the modified places.sqlite file back to your FF profile folder.

---

