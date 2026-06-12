---
title: "Quick Question"
date: 2011-08-10
forum: General Help
---

### Post by Hovercat on 2011-08-10
Is it safe to have a cron job run every day at 12AM to do this:

```
sync && echo 3 > /proc/sys/vm/drop_caches
```

It's a game server that I keep on 24/7. Here is a graph from Monitorix:

[img]http://i.imgur.com/Bu2e6.png[/img]

---

### Post by Hovercat on 2011-08-10
Well? Does anybody know?

---

