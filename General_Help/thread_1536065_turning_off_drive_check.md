---
title: "turning off drive check"
date: 2010-07-21
forum: General Help
---

### Post by dog-soldier on 2010-07-21
is there a way to turn off routine drive check?
in running Ubuntu 8.04

---

### Post by oldos2er on 2010-07-21
```
man tune2fs
```

Notice "You should  strongly  consider  the  consequences  of  disabling mount-count-dependent checking entirely." 

Also there is an app here: [https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck) that may be a little easier to use than tune2fs.

---

