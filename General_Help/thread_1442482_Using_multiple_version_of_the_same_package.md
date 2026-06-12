---
title: "Using multiple version of the same package"
date: 2010-03-30
forum: General Help
---

### Post by trashofmasters on 2010-03-30
Hi all,

I'll be short and try to point my problem directly.

I recently had to install PHP5.3 package (from *dotdeb.org*), but I had to install a old version of **libtool**(specifically *1.5.26*, from hardy repositories) because php-dev depends on it. Now my Update Manager is complaining about partial upgrades and I thinks that's due the old version of libtool.

I'm looking for a solution that will allow me to have the **libtool1.5.26** just to satisfy the php5-dev dependency and install **libtool2.2.6a-4** for all other packages.

What path do I have to follow to solve this nuisance?

Thanks in advance.

As a side note: I had to install libtool1.5.26 from Hardy repositories because when I tried to install php-dev apt-get was complaining about conflicting dependencies:
```
The following packages have unmet dependencies:
php5-dev: Conflicts: libtool (>= 2.2) but 2.2.*. is to be installed
E: Broken packages 
```

Bye

---

### Post by zvacet on 2010-03-30
I may be wrong,but I don't think you can use two versions of same package at thee time.You have to upgrade to newer version or downgrade to earlier one.

---

### Post by zvacet on 2010-03-30
I may be wrong,but I don't think you can use two versions of same package at the time.You have to upgrade to newer version or downgrade to earlier one.

---

