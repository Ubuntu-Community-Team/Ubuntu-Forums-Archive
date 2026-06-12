---
title: "postfix issue"
date: 2011-04-26
forum: General Help
---

### Post by CNM on 2011-04-26
Hi ,

i am getting this postfix error in the maillog :

Apr 26 13:20:23 localhost postfix/qmgr[3976]: warning: connect to transport local: Connection refused

anyone faced that before ?

Thanks :)

---

### Post by websavages on 2011-04-26
what does 

```
netstat -tna | grep -i listen
```

say?

Cheers ws

---

### Post by CNM on 2011-04-26
> **websavages said:**
> what does 

```
netstat -tna | grep -i listen
```say?

Cheers ws

it gives 

tcp        0      0 0.0.0.0:867                 0.0.0.0:*                   LISTEN      
tcp        0      0 127.0.0.1:3310              0.0.0.0:*                   LISTEN      
tcp        0      0 0.0.0.0:111                 0.0.0.0:*                   LISTEN      
tcp        0      0 127.0.0.1:631               0.0.0.0:*                   LISTEN      
tcp        0      0 0.0.0.0:25                  0.0.0.0:*                   LISTEN      
tcp        0      0 :::22                       :::*                        LISTEN

---

