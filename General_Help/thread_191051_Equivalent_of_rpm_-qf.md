---
title: "Equivalent of rpm -qf"
date: 2006-06-07
forum: General Help
---

### Post by caldevil on 2006-06-07
In fedora and other rpm distribution when I wanted to see which package a file *foobar* belongs to I used to give the following command

rpm -qf foobar

I want to know what is the equivalent of the above command in ubuntu?

---

### Post by adwait on 2006-06-07
I think its
```
dpkg -S <filename>
```

---

### Post by caldevil on 2006-06-07
thanks. Now when I look at help page for dpkg I can find an entry for  this, somehow I missed it when I was looking at it before.

---

