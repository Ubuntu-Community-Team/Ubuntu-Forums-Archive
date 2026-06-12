---
title: "Can't APT-GET/Update or USC"
date: 2012-06-02
forum: General Help
---

### Post by Colo2 on 2012-06-02
Whats happened to my PC? :s

I can't sudo apt-get install anything, it just freezes at 

> Building dependency tree... 0%

I can't open update manager, it crashes and closes.

I can't open ubuntu software centre, it crashes and it closes itself.

any ideas what's wrong? :S

Tom

---

### Post by kc1di on 2012-06-02
you can try this in a terminal

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update 
```

---

### Post by Colo2 on 2012-06-02
Thank you, fixed :)

---

