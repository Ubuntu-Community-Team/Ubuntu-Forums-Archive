---
title: "Need Help Installing Latest Tar.bz2 of Fireofx"
date: 2012-03-19
forum: General Help
---

### Post by onaridge on 2012-03-19
Can someone walk me through the installation of a tar.bz2 of the latest Firefox please? I have an old one and there is nothing in the software center anymore. I am not sure how to install it and delete the old one.

---

### Post by lovinglinux on 2012-03-20
You can get the latest Firefox by updating your applications through the *Update Manager*.

Alternatively, you can do that from a terminal using:

```
sudo apt-get update
sudo apt-get upgrade
```

The latest version of Firefox is version 11. You can check that from "Firefox Help >> About Firefox" menu.

---

### Post by zombifier25 on 2012-03-20
More info: The .tar.bz2 provided on Firefox's website is pretty much a complete Firefox package. Just extract it and run the "firefox" executable in the folder.
However, I would still recommend installing from the repos. lovinglinux has already provided the instructions.

---

