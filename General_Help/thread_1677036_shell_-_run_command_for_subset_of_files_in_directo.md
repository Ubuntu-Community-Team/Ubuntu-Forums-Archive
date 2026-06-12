---
title: "shell - run command for subset of files in directory"
date: 2011-01-28
forum: General Help
---

### Post by tata_tulen on 2011-01-28
Hi all,

I cannot find the way to run some command for a subset of files in directory - how can I do it?

Thanks for hint!

---

### Post by nothingspecial on 2011-01-28
I'm not sure exactly what you mean but maybe something like

```
for f in * ; do command $f ; done
```

for f assigns the variable $f to all files in the current directory, represented by the *

then the next bit runs that command on all the files.

If you see what I mean.

(I hope this isn`t homework;)

---

### Post by Habitual on 2011-01-28
[http://www.cyberciti.biz/faq/bash-for-loop/](http://www.cyberciti.biz/faq/bash-for-loop/)

---

### Post by tata_tulen on 2011-02-10
Thanks both of you!

---

