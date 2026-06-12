---
title: "sed help"
date: 2010-09-23
forum: General Help
---

### Post by dillzz on 2010-09-23
I usually don't have a problem with sed, however this fun little line is killing my.  I need to:

Find BELOW:
filter = [ "a/.*/" ]

Replace WITH:
filter = [ "a|^/dev/cciss/.*|", "r/sd.*/", "r/disk.*/", "a/.*/" ]

Thanks!

---

### Post by DaithiF on 2010-09-24
Hi,
```
sed '/filter =/s#\[ "a/.\*/" ]#[ "a|^/dev/cciss/.*|","r/sd.*/", "r/disk.*/","a/.*/" ]#' somefile
```

---

### Post by dillzz on 2010-09-28
DaithiF,

Thank you for the help - worked like a charm, more than appreciated!

-Dillzz

---

