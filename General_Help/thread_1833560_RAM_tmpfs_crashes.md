---
title: "RAM tmpfs crashes?"
date: 2011-08-26
forum: General Help
---

### Post by SlugSlug on 2011-08-26
I've added more ram to my box and read adding /tmp to ram can speed things up so I added

```
tmpfs /tmp tmpfs defaults,noexec,nosuid 0 0
```

to fstab and experienced random crashes every few hours (by crashes I mean complete freeze ups)

anyone know why?

as a side question is it safe to use /dev/shm ? I was toying with loading game server files in there with a 5min crontab rsyncing them back to disk

---

### Post by raja.genupula on 2011-08-26
[http://www.redhat.com/archives/nahant-list/2007-June/msg00151.html](http://www.redhat.com/archives/nahant-list/2007-June/msg00151.html)


[http://forums.debian.net/viewtopic.php?t=16450](http://forums.debian.net/viewtopic.php?t=16450)

---

