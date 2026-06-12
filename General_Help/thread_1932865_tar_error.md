---
title: "tar error"
date: 2012-02-28
forum: General Help
---

### Post by geohei on 2012-02-28
Hi.

I get ...

```
root@vm-99:/usr/src/toolchains# tar xjf Toolchain_mipsel-linux.SSL.tar.bz2 
tar: mipsel-unknown-linux-gnu/mipsel-unknown-linux-gnu/lib/ldscripts: Cannot mkdir: No such file or directory
...
```

I am root.
The . is empty (no space problem).
"tar tjvf" shows the .tar.bz2 archive isn't corrupt.
Google didn't help.

I never hit this problem before.

The .tar.bz2 archive is source code for x-compiling.

Any ideas ... ?!

Thanks!

---

### Post by RegUB on 2012-02-28
Permissions?

---

### Post by geohei on 2012-02-28
1. I am root.
2. Parent directory has 777.

What could possibly be related to a permission problem?

BTW ... another .tar.bz2 archive in the same folder extracts without any problems.

Thanks,

---

### Post by Damascushead on 2012-02-28
misspell filename?

---

### Post by geohei on 2012-02-29
Do you mean the filename after tar or a filename inside the .tar.bz2?
For the former, no it's correct since tar starts and doesn't report that the file doesn't exist.
For the latter, I don't know. I just know that people use this .tar.bz2 and didn't report any problems.

I was expecting an option missing from my side in the tar command?

---

