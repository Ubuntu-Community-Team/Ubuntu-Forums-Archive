---
title: "Update Manager error"
date: 2010-02-11
forum: General Help
---

### Post by CrazySat on 2010-02-11
Hi all,

since from last night I have an error with Update Manager and with shell command
```
sudo apt-get update
``` ... it seems an URL in repositories is not resolved :

```
Failed to fetch http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_US.bz2 
```

so that today I disabled in Software Sources ```
http://dl.google.com/linux/deb/ stable main
```

Are you experiencing same problem and do you think the url is obsolete and should be removed from the list or it can been replaced with different one ?

Thank you.

---

### Post by zvacet on 2010-02-11
It is not something unknown to see language packages make problems from time to time.You can live with it and you can enable that repo,because that will be just temporary inconvenience.

---

### Post by CrazySat on 2010-02-11
Thank you for reply, zvcet

---

