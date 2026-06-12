---
title: "Jamu and mysql schema"
date: 2010-01-02
forum: General Help
---

### Post by kempy1000 on 2010-01-02
Hi

I have a small problem with jamu.py

It has been working fine until I updated this morning now I get this error:
```

#CRITICAL - DB speaks schema version 1248, but we speak version 1247

! Warning - MythTV python bindings could not be imported

```
I am using mythtv trunk, and im not sure if this is a bug. But I havent a clue about mysql or this "schema" thing, so was wondering if its just a simple fix.

Thanks
Chris

---

### Post by Guilden_NL on 2010-01-02
I am not familiar with Jamu, other than a quick 2 minutes read from mythtv.org.

What may have happened is that the MySQL database schema was updated but the app is bound to the previous schema and something critical was changed, so the app is now not able to communicate with the database.  OR it could be a bug in MySQL. (Could be a few other things too but these are the first things that come to my mind.)

I remember encountering some bugs a year or two ago that caused inconsistencies between getSchemas and INFORMATION_SCHEMA that would cause apps to throw off error messages like this one.

It's definitely a Jamu issue, I would also see if there is any info on the mythtv.org site.

---

### Post by kempy1000 on 2010-01-02
> **Guilden_NL said:**
> I am not familiar with Jamu, other than a quick 2 minutes read from mythtv.org.

What may have happened is that the MySQL database schema was updated but the app is bound to the previous schema and something critical was changed, so the app is now not able to communicate with the database.  OR it could be a bug in MySQL. (Could be a few other things too but these are the first things that come to my mind.)

I remember encountering some bugs a year or two ago that caused inconsistencies between getSchemas and INFORMATION_SCHEMA that would cause apps to throw off error messages like this one.

It's definitely a Jamu issue, I would also see if there is any info on the mythtv.org site.

Thanks for the detailed reply! Ill look more into it.

---

### Post by eljeffe on 2010-01-02
This is also an issue with mirobridge. Exact same error message.

---

### Post by kempy1000 on 2010-01-03
I think it Is all to do with the rewrite of the python bindings that is going on.

---

