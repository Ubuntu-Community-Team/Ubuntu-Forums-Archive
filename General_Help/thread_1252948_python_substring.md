---
title: "python substring"
date: 2009-08-29
forum: General Help
---

### Post by krishna1650 on 2009-08-29
hi all, i want to know is there any to know whether a string is a substring of another string in python. for example 'ta' is a substring of 'natataa'. the main problem is 'ta' is not fixed, it will be given as input, so it may be 'na'. so i need a function like strstr provided in c.

thank you.

---

### Post by Bachstelze on 2009-08-29
You can use find(). The fact that the string to search for is given as input is irrelevant.

---

### Post by krishna1650 on 2009-08-31
> **HymnToLife said:**
> You can use find(). The fact that the string to search for is given as input is irrelevant.

thank you, for your reply. can you give some example or any source, where i will get some examples.

thank you.

---

### Post by The Cog on 2009-08-31
```
a = "fish and chips and salt and vinegar"
b = "hip"
offset = a.find(b)
if offset >= 0:
    print b, "is at location", offset, "in", a
else:
    a, "doesn't contain", b
```
find() returns -1 if not found.

---

