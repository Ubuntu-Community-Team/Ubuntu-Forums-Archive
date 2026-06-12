---
title: "Howto make parallel compilation of kernel source?"
date: 2010-09-17
forum: General Help
---

### Post by reverse_that on 2010-09-17
Hi all,

My question, as in the subject, is about enabling parallel compilation of kernel source.

I've read that setting the CONCURRENCY_LEVEL environment variable should do that. The problem is that I see only one instance of a running gcc in top, notwithstanding I have set "export CONCURRENCY_LEVEL=5".

What am I missing?

Thanks in advance to anyone who will reply.

fabio

---

### Post by andrewthomas on 2010-09-17
This is the command that I use.

```
fakeroot make-kpkg **-j5** --initrd --revision=20100916.1.0 kernel_image
```The -jX switch is used for the # of jobs.  Use one more than your # of cores.  I have a quad-core cpu thus -j5.  I believe that it is the same as concurrency level but I'm not sure.

---

