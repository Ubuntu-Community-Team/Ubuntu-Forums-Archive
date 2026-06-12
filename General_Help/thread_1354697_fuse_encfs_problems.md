---
title: "fuse encfs problems"
date: 2009-12-14
forum: General Help
---

### Post by syphodias on 2009-12-14
im trying to run encfs on my ubuntu 9.10 box. I have some problems:

installed encfs and added my user to fuse group. Logged out and in.

tryed

```
encfs /home/davide/source /home/davide/target
```

both folder exist and have been created by my user.

first problem:

```
fusermount: failed to open /etc/fuse.conf: Permission denied
```

solved with

```
sudo chmod a+rwx /etc/fuse.conf
```

and uncommenting user_allow_other in that file.

i don't know why it worked, i checked and fuse.conf belongs to fuse group..


now the real problem.

```
fusermount: failed to access mountpoint /home/davide/target: Permission denied 
```


ideas?

---

### Post by syphodias on 2009-12-14
sorry i was very dumb, this thread can be removed. 

No real problems present.

---

