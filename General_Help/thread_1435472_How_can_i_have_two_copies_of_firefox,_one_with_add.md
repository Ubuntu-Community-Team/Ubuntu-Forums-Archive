---
title: "How can i have two copies of firefox, one with addons and one without?"
date: 2010-03-21
forum: General Help
---

### Post by mag1 on 2010-03-21
Thanks for any help. ;)

---

### Post by phen0m on 2010-03-21
I believe this should work
```
firefox -ProfileManager
```

you can also check out the *firefox -P* switch for making shortcuts.

---

### Post by lovinglinux on 2010-03-21
Close Firefox, then open the Profile Manager with this command:

```
firefox -P
```

Create a new profile with the Profile Manager and start it.

If you want to use both profiles at the same time, then start a new instance of Firefox with:

```
firefox -P -no-remote
```

---

