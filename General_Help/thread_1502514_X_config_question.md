---
title: "X config question"
date: 2010-06-05
forum: General Help
---

### Post by miststlkr on 2010-06-05
I have my system using two displays on separate X sessions [using the proprietary nvidia drivers if that makes a difference] .  When I boot, I would like to control which session a given program auto-starts in.  My tinkering has failed me, any help/suggestions?

[EDIT] For that matter, is there a way to open a program in the command line and dictate which session it opens in? [/EDIT]

---

### Post by miststlkr on 2010-06-12
Bump?

---

### Post by chayzer on 2010-06-12
```
export DISPLAY=:0.0
```

or 

```
export DISPLAY=:0.1
```

Maybe?

---

### Post by miststlkr on 2010-06-12
*sigh*  so simple once you see it.  Thanks a ton, I beat my head for far too long trying to think of that.   What I ended up doing was running the following from a terminal:

```

mythfrontend -display :0.1

```

I can run that from the monitor and the frontend loads on the TV.  Here's to hoping that changing it in the auto-start config file is just as straight-forward.  Cheers!

---

### Post by chayzer on 2010-06-12
I've beat my own head plenty of times!

---

