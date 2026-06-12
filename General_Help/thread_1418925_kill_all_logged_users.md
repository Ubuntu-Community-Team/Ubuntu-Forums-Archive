---
title: "kill all logged users?"
date: 2010-03-01
forum: General Help
---

### Post by zuku on 2010-03-01
hi, 
how to kill all logged users to my server (one command to kill all pts sessions)??

---

### Post by falconindy on 2010-03-01
Might be an easier way to do this, but...

```
kill $(ps aux | grep "pts\/[[:digit::]]" | awk '{print $2}')
```

---

### Post by cjhabs on 2010-03-01
I haven't tested this:
for user in `who | awk '{ print $1 }' | uniq`; do skill -STOP -u $user; done

Not really 1 line but close!

---

