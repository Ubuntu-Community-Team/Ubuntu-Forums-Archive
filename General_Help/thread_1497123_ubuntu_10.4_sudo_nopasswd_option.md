---
title: "ubuntu 10.4 sudo nopasswd option?"
date: 2010-05-30
forum: General Help
---

### Post by Wonslung on 2010-05-30
Is there a specific reason this option doesn't work?

I've alwasy set it no problem, but for some reason, it seems to be broken in this release.

```
%sudo ALL=(ALL) NOPASSWD: ALL
```


should allow me to enter commands without a password....it didn't
just to be sure i even explicitly added a line with my user like this:
```
wonslung ALL=(ALL) NOPASSWD: ALL
```

any help would be appreciated.

---

### Post by Wonslung on 2010-05-30
darn...i tried to delete this post, i just found the old forum post regarding this.

i haven't tried the fix yet, but according 
[http://ubuntuforums.org/showthread.php?t=135160](http://ubuntuforums.org/showthread.php?t=135160)


i just need to put it at the end....this is different than FreeBSD which is what i'm used to...sorry for wasting everyone's time (i did search but for some reason i didnt' find this till i did a GOOGLE search instead of a forum search)

---

