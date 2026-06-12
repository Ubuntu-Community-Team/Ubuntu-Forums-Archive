---
title: "ktorrent does not save my preferences"
date: 2009-09-28
forum: General Help
---

### Post by bruno9779 on 2009-09-28
As the title say.

When I change any preference in Ktorrent it does nor save.

If I press "apply" the button does not grey out as it should. If I press "OK" the window closes, and when I restart Ktorrent I get the default preferences.

I have tried to start ktorrent from CLI, but it is not verbose.

If I sudo ktorrent, then it is verbose and i get:

Error: "/var/tmp/kdecache-bruno" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-brunoigykxZ" is owned by uid 1000 instead of uid 0.
bruno@bruno-box:~$ Error: "/tmp/ksocket-bruno" is owned by uid 1000 instead of uid 0.

now, the preferences can be saved. but only if I reopen ktorrent fom cli.

If i open it with the luncher it gives me the default setup, with my torrents.

If I add gksudo before the command of the launcher, ktorrent opens without my torrents

Thanks

---

### Post by bruno9779 on 2009-09-29
bump

---

### Post by bruno9779 on 2009-09-29
re bump

no replies here or in ktorrent forum....:(

---

### Post by bruno9779 on 2009-09-29
I have been  answered at Ktorrent forum.

I post here the command for reference: 
> 
Your problem is that KT has been run as root, so the config file is now owned by root, and you can't write to it. Don't run KT as root.

To fix it :
```
sudo chown -R bruno:bruno /home/bruno/.kde
```

That will make sure the settings of ktorrent are owned by you again (assuming bruno is your username, if not, replace by your real username)

This post is solved, I wish i knew how to do that

---

