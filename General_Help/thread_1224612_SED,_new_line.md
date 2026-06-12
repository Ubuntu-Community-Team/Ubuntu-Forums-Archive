---
title: "SED, new line"
date: 2009-07-27
forum: General Help
---

### Post by GreenDance on 2009-07-27
Hi, I have a SED line, can I add a new [blank] line above it?, it's on line 21, many thanks

---

### Post by DaithiF on 2009-07-27
You want to add a new line above line 21 in a file, using sed ?

```
sed '21{x;p;x}' somefile   
```
to preview it

add -i flag to actually change the file:
```
sed -i'21{x;p;x} somefile
```

---

