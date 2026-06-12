---
title: "is there a way i can see what was last updated?"
date: 2012-05-25
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-05-25
is there a way i can see what was recently updated in 10.04 64bit
edit silly me i can sort the deb packages in /var/cache/apt/archives by date and see real easy

---

### Post by kc1di on 2012-05-25
> **pqwoerituytrueiwoq said:**
> is there a way i can see what was recently updated in 10.04 64bit
edit silly me i can sort the deb packages in /var/cache/apt/archives by date and see real easy

you can look in the following log file it keeps track of installed packages.

```
 /var/log/dpkg.log 
```

---

### Post by codemaniac on 2012-05-25
Just to add some searches on kc1di's suggestion .
```
grep "\ install\ " /var/log/dpkg.log
```

---

### Post by pqwoerituytrueiwoq on 2012-05-27
> **codemaniac said:**
> Just to add some searches on kc1di's suggestion .
```
grep "\ install\ " /var/log/dpkg.log
```
```
grep "\ upgrade\ " /var/log/dpkg.log
```

---

### Post by dFlyer on 2012-05-27
It can be a long list so you might want to use this:

grep "\ upgrade\ " /var/log/dpkg.log | more

---

