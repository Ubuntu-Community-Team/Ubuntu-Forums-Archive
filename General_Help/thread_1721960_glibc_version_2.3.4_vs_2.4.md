---
title: "glibc version 2.3.4 vs 2.4"
date: 2011-04-05
forum: General Help
---

### Post by capybara! on 2011-04-05
Hi,

hope someone can help me. I try to install dropbox on a cluster computer, it comes as a precompiled binary for x86.

Trying to run it, it gives me the error:

```
./dropbox: /lib/tls/libc.so.6: version `GLIBC_2.4' not found (required by ./dropbox)
```

glibc is installed in the version 2.3.4 on this machine.
I do have root access to this machine, but I really do not want to mess with the installed version of glibc, since many other users run stuff on the cluster.

So is there maybe a way to install my own glibc 2.4 in my home directory and let dropbox use this library?
Or is there another way to get dropbox running?

Thanks in advance, I'd really appreciate any help!

capybara

---

