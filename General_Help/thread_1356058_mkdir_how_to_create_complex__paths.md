---
title: "mkdir: how to create complex  paths?"
date: 2009-12-15
forum: General Help
---

### Post by shade5 on 2009-12-15
Hi,

I wonder how to create complex path with mkdir. Im very sure that I did it by

```
mkdir ~/parent/sub1
```

Notice that parent does not existed until yet.

But when I do it now I'm getting

> mkdir: cannot create directory `/home/shade/parent/sub': No such file or directory


I know it is a stupid questions, espceially since I did it in the past with no problems. I hope you can help me.

Thanks.

---

### Post by spiderbatdad on 2009-12-15
check out ```
man mkdir
so
mkdir -p parent/sub1
```
Be aware if you mkdir -p /parent/sub1 this will place the dir in / not /home/user

---

### Post by shade5 on 2009-12-15
Is this feature new?

I got scripts that worked flawless and had no -p.

---

### Post by spiderbatdad on 2009-12-15
For at least 6-7 releases now this has been the method when using mkdir for creating parent directories for sub-directories.

---

