---
title: "Gzip"
date: 2011-12-01
forum: General Help
---

### Post by mikaelcrocker on 2011-12-01
G'day

So, I'm trying to use gzip in order to zip a file, and then rename it to something else.  I've looked and I haven't found much, perhaps I have not looked enough.  I'm sure it's as simple as using a swtich, but nothing really jumped out at me


Thanks

---

### Post by Dave_L on 2011-12-01
Compress a file using gzip:

```
gzip file123
```

Rename the compressed file:

```
mv file123.gz file456.gz
```

You could also do the same thing like this:

```
gzip -c file123 >file456.gz
```

Does that help?

---

### Post by mikaelcrocker on 2011-12-01
The third option was it.  I was piping and now using standard output, thanks!!

---

