---
title: "remove repositories from ubuntu software center"
date: 2010-08-30
forum: General Help
---

### Post by alem189 on 2010-08-30
Okay, so my problem is that I can't get rid of some repositories on the left side of the Ubuntu software center. 

I've gone to Edit > Software Sources and unchecked everything in Other Software, rebooted and still they remain. I then went into /etc/apt/sources.list.d/ and deleted the offending .list files, and they're still there. How do I get rid of them?

---

### Post by zpletan on 2010-08-30
It might be that you still have software installed from some of those, even though you've deleted them.  You might try ppa-purge from [https://launchpad.net/ppa-purge](https://launchpad.net/ppa-purge)

---

### Post by zpletan on 2010-08-30
Duplicate post :)

---

### Post by alem189 on 2010-08-31
This seemed to work -- It outputted a bunch of stuff about downgrading packages and removing lists, but they're still there. Is there any way to remove them manually? It's mainly an aesthetics  thing, so if I've hit a brick wall here, it's not that much of a big deal.

---

### Post by alem189 on 2010-10-15
nvm, fixed on upgrade to maverick

---

