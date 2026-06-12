---
title: "How do I remove all entries from 'Dates' calendar program?"
date: 2011-05-30
forum: General Help
---

### Post by Rytron on 2011-05-30
Hi.

How do I remove all entries from 'Dates' calendar program?
Is there a hidden folder to delete to reset all settings to default?

Thanks.

---

### Post by hwttdz on 2011-05-30
It looks like dates syncs with evolution, so you'll lose evolution data as well.  But it looks like you:
cd ~/.local/share/evolution
and remove calendar, and possibly tasks as well
and then run
/usr/lib/evolution/2.32/killev
(where you might not be on version 2.32), because it holds something in memory.  Then after you start dates again it should be clean.

---

### Post by Rytron on 2011-05-31
> **hwttdz said:**
> It looks like dates syncs with evolution, so you'll lose evolution data as well.  But it looks like you:
cd ~/.local/share/evolution
and remove calendar, and possibly tasks as well
and then run
/usr/lib/evolution/2.32/killev
(where you might not be on version 2.32), because it holds something in memory.  Then after you start dates again it should be clean.

No joy. :(

```
/usr/lib/evolution/2.32/killev
Could not find Evolution's process ID
rytron@D07:~$ sudo /usr/lib/evolution/2.32/killev
sudo: unable to resolve host D07
[sudo] password for rytron: 
Could not find Evolution's process ID
```

I do notice that if I create an event in 'Dates' and close it; when I relaunch it that event has vanished. Evolution has too much control over Dates.

---

