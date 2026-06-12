---
title: "How to create a new file with a name of the current date &amp; time ?"
date: 2009-07-26
forum: General Help
---

### Post by credobyte on 2009-07-26
```
dainis@credobyte:~$ date
**Sun Jul 26 13:08:25 EEST 2009**

```

How can I create a file, named exactly like it's shown in my example ( *filename = output of the date command* ) ?

---

### Post by sisco311 on 2009-07-26
```
> "$(date)"
```

---

### Post by credobyte on 2009-07-26
> **sisco311 said:**
> ```
> "$(date)"
```

Oh, well - thnx ! Forgot about double-quotes ( tried single-quotes .. made a few smaller files instead of what I was looking for ) :D

---

