---
title: "Cannot change permissions on a mounted truecrypt container"
date: 2010-10-27
forum: General Help
---

### Post by wconstantine on 2010-10-27
> wh1sk3yj4ck@valkyrie:/media$ ls -l
total 44
drwx------ 1 wh1sk3yj4ck wh1sk3yj4ck 40960 2010-10-21 20:38 truecrypt1
wh1sk3yj4ck@valkyrie:/media$ sudo chgrp -R workers truecrypt1
wh1sk3yj4ck@valkyrie:/media$ ls -l
total 44
drwx------ 1 wh1sk3yj4ck wh1sk3yj4ck 40960 2010-10-21 20:38 truecrypt1
wh1sk3yj4ck@valkyrie:/media$

The group owner remains unchanged. Why?

Doesn't work regardless of everything I throw at it.

Edit: Could it be something with the filesystem? The drive is running NTFS!

I tried to change the permissions with chmod o+r truecrypt1. Didn't work either.

---

