---
title: "Search files for word"
date: 2011-12-25
forum: General Help
---

### Post by 7cardcha on 2011-12-25
I tried grep but it wouldn't match the way I wanted it to. If the file was this. And I searched for "ll"

```


hellordg  dusengdfbnbjfbn 


```I would want it to match the ll in hellordg. Thank you very much for your help.

---

### Post by papibe on 2011-12-25
grep works in case sensitive mode by default. Try using the option -i to match case insensitive patterns. For example:
```
grep -i ll your_file
```
Merry Christmas.

EDIT: I forgot to put the expression 'll'.

---

### Post by 7cardcha on 2011-12-26
> **papibe said:**
> grep works in case sensitive mode by default. Try using the option -i to match case insensitive patterns. For example:
```
grep -i your_file
```Merry Christmas.

TYVM & Merry Christmas!

---

