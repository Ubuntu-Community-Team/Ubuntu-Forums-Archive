---
title: "problem with unity shortcut bar"
date: 2011-10-11
forum: General Help
---

### Post by NeoReaper on 2011-10-11
some how last night i manage to mess up my unity shortcut bar and i haven't been able to fix it.  for some reason all the icons on the bar vanished yet i can still kind of click on them. i can move them around and rearrange them to a certain degree and when i do that sometimes a silhouette of the icon appears with a bar running through it.  i've tried unity reset and unity reset icon but neither command seems to help. i enclosed a screenshot of my unity shortcut bar. any ideas would be appreciated.

---

### Post by vanadium on 2011-10-11
You might also need to reset compiz. Try this:

```

gconftool-2 --recursive-unset /apps/compiz-1
unity --reset

```

---

