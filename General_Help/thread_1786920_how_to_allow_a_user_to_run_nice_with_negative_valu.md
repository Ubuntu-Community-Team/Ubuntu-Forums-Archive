---
title: "how to allow a user to run nice with negative values"
date: 2011-06-20
forum: General Help
---

### Post by matteosistisette on 2011-06-20
Hi,

I have added this to /etc/security/limits.conf:

```
teo -  nice  -20

```

where teo is the name of my regular user. However, if I try to run some command with:

nice -n -20 somecommand

(or -8 or any negative value for that matter), I still get:

```
nice: cannot set niceness: Permission denied
```

How can I allow user "teo" to run nice and renice with negative nicenesses without sudoing?

Thanks
m.

---

