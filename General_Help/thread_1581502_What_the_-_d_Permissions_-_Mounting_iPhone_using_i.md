---
title: "What the - d??????? Permissions - Mounting iPhone using iFuse"
date: 2010-09-25
forum: General Help
---

### Post by mr_luksom on 2010-09-25
Has anyone ever seen this before:

```
d?????????  ? ?    ?       ?                ? iPhone

```

I'm continuing on a quest to sync my iOS4 iPhone in xubuntu lucid, and the above is what I get after mounting it with iFuse. Unsurprisingly, I can't actually use it after being mounted with permissions like that.

With the iPhone unmounted, an ls -al looks like this

```
drwxrwxrwx  2 root root 4096 2010-09-25 15:51 iPhone
```

Has anyone even seen '?' permissions before?

---

### Post by mr_luksom on 2010-10-03
FYI

This appears to be solved for me using the 1.0.2 libimobiledevice1 release.

There is now a PPA from Paul McEnery, and everything is working fine!

---

