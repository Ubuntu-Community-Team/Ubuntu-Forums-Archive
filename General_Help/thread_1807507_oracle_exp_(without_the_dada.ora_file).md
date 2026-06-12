---
title: "oracle exp (without the dada.ora file)"
date: 2011-07-19
forum: General Help
---

### Post by mikejonesey on 2011-07-19
**unable to get the oracle exp utility to work on remote servers...**

okey dokes, to connect to a remote oracle db from sqlplus i use somthing along the lines;
```
sqlplus -L user/pass@"(conection string locating db which replaces the ora file which i don't think unix based systems have?)"
```cool that works;

now to use exp i'm trying somthing along the same lines;
```
exp usr/pas@"(dada)"
```But to no avail, who's used the exp utitlity on a unix based system to connect to a remote oracle server (local connect is fine with exp)?

i guess it's all about replacing the tsnames.ora file in the command but can't seen to get syntax right on the exp util...

---

### Post by mikejonesey on 2011-07-19
resolved this by just setting up the connection in the tnsnames.ora then using;

```
exp usr/pass@LINKNAME
```

(linkname defines in ora file :) )

---

