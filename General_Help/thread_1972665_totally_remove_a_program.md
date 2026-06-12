---
title: "totally remove a program"
date: 2012-05-03
forum: General Help
---

### Post by dog-soldier on 2012-05-03
i need to totally remove chrome so i can reinstall it. i messed up some how and now when i go to facebook i cant play any games. i tried to uninstall chrome but when i reinstall it everything is like before.

---

### Post by billyseth on 2012-05-03
apt-get remove --purge chromium-browser (or any package name) should remove all the config files and such.

---

### Post by llamabr on 2012-05-03
You might do a:

```
rm -rf .chrome*
```

too while you're at it.

---

