---
title: "removeing orphaned packages"
date: 2012-04-27
forum: General Help
---

### Post by johntd on 2012-04-27
when I use the remove orphan package software in ubuntu and check the "show all orphan packages not only those in the Libs section" it comes up with quite a few, is it safe to remove these.

---

### Post by ajgreeny on 2012-04-27
Which software are you using to get rid of these orphan packages?

I have always found that it is necessary to inspect carefully the list and make sure that the removal application you're using is not about to uninstall application that is unnecessary, but is really important and needed by you.

**Take great care!**  If space is not a problem to you it is probably safer to leave well alone, as extra packages take space only, and do not really make a significant difference to system speed.

---

### Post by IWantFroyo on 2012-04-27
+1 to ajgreeny's post. Don't idly remove them.

I would run:
```
sudo apt-get autoremove
```

Inspect the list of what it will uninstall carefully.

---

### Post by johntd on 2012-04-27
many thanks for your time and instruction I will do as you say and leave well alone.

---

