---
title: "bzip2 in a pipe"
date: 2012-07-02
forum: General Help
---

### Post by piriton on 2012-07-02
How do I use bzip2 within a pipe ?  Ive tried stuff like this

```

cat file | bzip2 -c -

```

---

### Post by msammels on 2012-07-03
You want to pipe the output of bzip2? You want something like this:

```
bzip2 file.tar.gz > output.txt
```

Obviously, you need to muck around with it, or you'll get no output on screen, but the simple formula is:

```
cmd > output.txt
```

---

