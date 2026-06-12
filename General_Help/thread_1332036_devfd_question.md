---
title: "dev/fd question"
date: 2009-11-19
forum: General Help
---

### Post by mo.reina on 2009-11-19
what exactly is going on in this piece of code? what is the role of /dev/fd? i know that /dev/fd/0 is somehow linked to standard input, but that's the extent of my knowledge

```
cat header.txt /dev/fd/0 footer.txt
```

---

### Post by mo.reina on 2009-11-20
ok figured out /dev/fd/0

now i have another related question.  what's the difference between:

```
exec 7<&0
```

and

```
exec 7>&0
```

---

