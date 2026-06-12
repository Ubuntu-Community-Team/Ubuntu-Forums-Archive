---
title: "A simple bash tools problem"
date: 2011-01-10
forum: General Help
---

### Post by Solow2010 on 2011-01-10
I have a file "file1",
It contains like
AAA  BBB CCC DDD
each item is separated by "space",
Is there bash tool to convert the file likes
AAA
BBB
CCC
DDD

Thanks a lot.

---

### Post by sisco311 on 2011-01-10
Hi and welcome to the forums!

You can use sed or tr. Is this your homework?

---

### Post by Solow2010 on 2011-01-10
Hehe
It's not my homework
It is my research

---

### Post by sisco311 on 2011-01-10
Did you check out sed?  [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

You need something like:
```
sed 's/ \+/\n/g' filename
```

---

### Post by Solow2010 on 2011-01-11
Thanks for your hint

---

