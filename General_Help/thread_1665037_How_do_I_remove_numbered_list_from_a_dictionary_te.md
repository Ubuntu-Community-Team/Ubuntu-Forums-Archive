---
title: "How do I remove numbered list from a dictionary text file?"
date: 2011-01-11
forum: General Help
---

### Post by inverser on 2011-01-11
Source:

```
2343 test1
4838 test2
3243 test3
8998 test4
2343 12345
```Output:

```

test1
test2
test3
test4
12345
```What is the best tool to accomplish this? Thank you for your help.

---

### Post by sisco311 on 2011-01-11
awk:
```
awk '{print $2}' filename
```

---

### Post by inverser on 2011-01-11
> **sisco311 said:**
> awk:
```
awk '{print $2}' filename
```
Perfecto. Thank you.

---

