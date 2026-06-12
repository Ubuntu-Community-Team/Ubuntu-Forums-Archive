---
title: "I can't browse my D drive."
date: 2010-01-02
forum: General Help
---

### Post by Rigbonn on 2010-01-02
So, I've installed Ubuntu v9.10 through the Wubi and I can see only the C, E drivers but not the D one (which is, where I have installed the Ubuntu itself and maybe that's why the problem appear).

What should I do?

---

### Post by MooPi on 2010-01-02
Are you able to boot into Ubuntu ? Have you used the Ubuntu partition yet ?

---

### Post by Leppie on 2010-01-02
if you want to access your ubuntu partition from within windows, you will have to install additional software as ubuntu creates an extN filesystem (even within the assigned ntfs partition). However, *accessing linux partitions from within windows isn't really advisable*.

---

### Post by 3rdalbum on 2010-01-02
> **Rigbonn said:**
> So, I've installed Ubuntu v9.10 through the Wubi and I can see only the C, E drivers but not the D one (which is, where I have installed the Ubuntu itself and maybe that's why the problem appear).

What should I do?

The drive that the Ubuntu disk image is stored on is accessible through /host (that is, in your file browser go to Filesystem and then double-click on "host").

That's how Wubi sets things up.

---

### Post by Rigbonn on 2010-01-02
> **3rdalbum said:**
> The drive that the Ubuntu disk image is stored on is accessible through /host (that is, in your file browser go to Filesystem and then double-click on "host").

That's how Wubi sets things up.
Thanks for the help. That's exactly what I've been looking for. Is there any option I can do a shortcut for /host/ to locate it @ desktop? If so, how to?

---

