---
title: "Using RM- Syntax Error with Filenames Containing &quot;(&quot;"
date: 2012-01-28
forum: General Help
---

### Post by w201 on 2012-01-28
Hey guys- just wondering why RM doesn't work with filenames containing parenthesis and what I can do to make it work.

Thanks!

---

### Post by mutley89 on 2012-01-28
Use quotes:

```
 rm 'some(file)name'
```Or backslash escapes:

```
rm some\(file\)name
```

---

### Post by w201 on 2012-01-28
That did it. Thanks!

---

