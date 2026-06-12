---
title: "How to change a process's 'nice' value?"
date: 2009-10-05
forum: General Help
---

### Post by mªrty on 2009-10-05
I'm looking for the file where user permissions are stored. I remember editing it a few months ago so that gnome-system-monitor wouldn't crash when I would edit a process's nice value, but now I'd like to make some links to programs so they can startup with a high priority.

Thanks

---

### Post by dcstar on 2009-10-06
> **mªrty said:**
> I'm looking for the file where user permissions are stored. I remember editing it a few months ago so that gnome-system-monitor wouldn't crash when I would edit a process's nice value, but now I'd like to make some links to programs so they can startup with a high priority.

Thanks

```
man nice
```

---

### Post by mªrty on 2009-10-06
dcstar, thank you, but both
```
man nice
``````
info nice
```
give me the same info. I'm looking for a file that ubuntu checks to see whether a given user has enough permission to run, for example,
```
nice --8 firefox
```

I realize sudo works, but I was hoping someone else knew where the user permissions were stored.

---

