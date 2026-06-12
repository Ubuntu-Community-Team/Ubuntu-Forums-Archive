---
title: "removing kernel module that is in use"
date: 2012-02-15
forum: General Help
---

### Post by mohsinabbas on 2012-02-15
hi.
any one knows how to remove a module that in use.??
thanks in advance..:-)

---

### Post by aeiah on 2012-02-15
```
sudo rmmod modulename
```
[http://linux.die.net/man/8/rmmod](http://linux.die.net/man/8/rmmod)


if you aren't sure of the full name, you can use lsmod to list modules, perhaps with grep if you have a vague idea
```

lsmod | grep mce

```
will list information about modules with mce in their name (typically windows media center compatible remote controls)

---

