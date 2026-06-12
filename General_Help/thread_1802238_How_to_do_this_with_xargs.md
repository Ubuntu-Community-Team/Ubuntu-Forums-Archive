---
title: "How to do this with xargs?"
date: 2011-07-11
forum: General Help
---

### Post by Cuddles McKitten on 2011-07-11
What's the xargs equivalent of:

```
find . -exec cp {} {}.bak \;
```?

My best attempt was ```
find . -print0 | xargs -I file cp file file.bak
``` and it didn't work.  I can't seem to figure out where my syntax is messed up.

EDIT:  Got it!  It was a missing -0.  The full command would be ```
find . -print0 | xargs -0 -I file cp file file.bak
```

---

