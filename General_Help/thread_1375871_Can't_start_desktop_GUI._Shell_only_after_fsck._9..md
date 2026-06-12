---
title: "Can't start desktop GUI. Shell only after fsck. 9.10"
date: 2010-01-08
forum: General Help
---

### Post by orango on 2010-01-08
I have been running ubuntu 9.10 since its release. Yesterday it upgraded itself at some point. When I restarted the computer this morning, I had a "mount of filesystem failed" error. I read on the forums that I should use the fsck command, so I did. It did some "force rewrites" and "has deleted/unused inode" stuff.

Now I can only login to a shell. I can't get a GUI to start. Any ideas?? Thanks!

---

### Post by %hMa@?b&lt;C on 2010-01-08
what happens when you try from the shell

```
startx
```

?

---

### Post by orango on 2010-01-08
> what happens when you try from the shell startxIt fails to load a bunch of modules, and then I get "fatal error: no screens found"

---

