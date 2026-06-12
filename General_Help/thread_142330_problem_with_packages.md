---
title: "problem with packages"
date: 2006-03-10
forum: General Help
---

### Post by tOpEzz on 2006-03-10
this few day i always encounter this problem when i update my repositories

> deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free

it seen cannot update from the packages, does anybody how to solve this problem.
thanks

p/s: i'm using ubuntu 5.10 breezy badger

---

### Post by Xian on 2006-03-10
Try using this mirror:

```
deb http://cameronbergh.com/mirror/ubuntu/plf/ breezy free non-free
deb-src http://cameronbergh.com/mirror/ubuntu/plf/ breezy free non-free
```

---

### Post by tOpEzz on 2006-03-11
thanks Xian, do you know where can i find the latest repo for breezy badger, soon i'm gonna switch to dapper drake.

---

### Post by akiro.yamamoto on 2006-03-11
You can use this to generate a custom sources.list
[ Ubuntu Source.lists Generator ](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by tOpEzz on 2006-03-11
thanks for the tips akiro.yamamoto.

---

