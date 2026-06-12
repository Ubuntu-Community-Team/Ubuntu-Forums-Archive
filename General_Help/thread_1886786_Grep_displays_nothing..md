---
title: "Grep displays nothing."
date: 2011-11-25
forum: General Help
---

### Post by morle on 2011-11-25
Hi,  I'm trying to identify the files inside a directory with certain extension, using ls and grep:[I]
        ls | grep *.ext
[/I]However, it displays nothing.
I've also tried using grep with -E option, yet it displays nothing.

Any idea?
Thanks!

---

### Post by sisco311 on 2011-11-25
Use globs instead of grep and ls:
```
printf '%s\n' *.ext
```

[http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)
[http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)

---

### Post by matt_symes on 2011-11-25
Hi

> **morle said:**
> Hi,  I'm trying to identify the files inside a directory with certain extension, using ls and grep:[I]
        ls | grep *.ext
[/I]However, it displays nothing.
I've also tried using grep with -E option, yet it displays nothing.

Any idea?
Thanks!

No need for the * in the grep

```
ls | grep .ext
```But no need to use grep.

```
ls *.ext
```Kind regards

---

### Post by nothingspecial on 2011-11-25
Because the * means different things to grep and bash

---

### Post by morle on 2011-11-25
Ok! Thanks.

---

