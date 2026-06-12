---
title: "Updater won't install updates"
date: 2010-12-20
forum: General Help
---

### Post by FacesComix on 2010-12-20
Hey all, Recently update manager stopped updating.

whenever somenew updates get released it pops up saying that there are updates and when I hit "Install Updates" it gives me an error

> Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

[QUOTE]icedtea-6-jre-cacao icedtea6-plugin libc-bin libc-dev-bin libc6 libc6-dev openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib ubuntu-docs[/QUOTE]

help!

---

### Post by FacesComix on 2010-12-21
Bump...

---

### Post by sikander3786 on 2010-12-21
From Software Center > Edit > Software Sources, change your Download Server to Main and try update/install again.

If there are still some errors, from Applications > Accessories > Terminal, post the complete output of this command.

```
sudo apt-get update
```

---

