---
title: "Speeding up searches using FIND"
date: 2010-07-19
forum: General Help
---

### Post by FeraTech on 2010-07-19
Does FIND use any indexing at all?

Is there any way to speed up this command when doing searches?

---

### Post by ronnielsen1 on 2010-07-19
Gnome-Do is a great search app. I agree on the find

It should be in the repos

---

### Post by FeraTech on 2010-07-19
The problem is that FIND is built into the system and is used by the apache server when going through the directory structure.

---

### Post by rubylaser on 2010-07-19
The easiest way to limit a find is to limit it's scope by directory, type, etc. For example.

```
find /var/www -type f -name "index.html"
```

I'm not sure if that answers your question or not.

---

