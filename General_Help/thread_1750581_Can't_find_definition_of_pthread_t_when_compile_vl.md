---
title: "Can't find definition of pthread_t when compile vlc on ubuntu"
date: 2011-05-05
forum: General Help
---

### Post by mjsilverstri on 2011-05-05
Hi,

I am trying to compile vlc under ubuntu 11.04. But some how it can't see the definition of pthread_t. I have already installed 'pthread-stub0-dev'

line 327 is :

```
extern int pthread_create_cancel( pthread_t *thread,
                           const pthread_attr_t *attr,
                           void *( *routine ) ( void* ),
                           void *arg );
```
and here are my errors:

```
In file included from ../config.h:825:0,
                 from pthread_cancel.c:12:
ERROR   : ../include/vlc_fixups.h:327: 45:  expected ')' before '*' token
ERROR   : ../include/vlc_fixups.h:332: 38:  expected ')' before 'thread_id'
ERROR   : ../include/vlc_fixups.h:334: 53:  expected ')' before '*' token
ERROR   : ../include/vlc_fixups.h:336: 58:  expected ')' before '*' token
In file included from ../include/vlc_threads.h:51:0,
                 from ../include/vlc_common.h:494,
```

---

