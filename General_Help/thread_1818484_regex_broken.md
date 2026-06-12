---
title: "regex broken ?"
date: 2011-08-04
forum: General Help
---

### Post by nagileon on 2011-08-04
Hi there

I have a following file:

cat x.csv 
dsadasd,,
,,
,,
,,
aa
bb
cc
dd
,,aa
,,bb
,,cc
,,dd

In Ubuntu:

cat x.csv |grep ^,,$ Gives me no results.

In CentOS:

cat x.csv |grep ^,,$
,,
,,
,,

Why would that be ?

Thanks

---

### Post by Habitual on 2011-08-04
On OpenSUSE 11.4, I get
```

,,
,,
,,

```

but I ran ```
grep ^,,$ x.csv
``` (hint :wink: ) 
grep (GNU grep) 2.7

---

### Post by nothingspecial on 2011-08-05
Can't speak
```

ns@netbook\:~$ cat x.csv
dsadasd,,
,,
,,
,,
aa
bb
cc
dd
,,aa
,,bb
,,cc
,,dd
ns@netbook\:~$ grep ^,,$ x.csv 
,,
,,
,,
ns@netbook\:~$ cat x.csv |grep ^,,$
,,
,,
,,
ns@netbook\:~$ 
```

---

### Post by Habitual on 2011-08-05
nagileon:
You said "Ubuntu" but not the release/version etc...
Terminal > ```
lsb_release -dr
```


My VM of 10.10:
```
lsb_release -dr && grep ^,,$ x.csv
Description:	Ubuntu 10.10
Release:	10.10
,,
,,
,,
```

---

