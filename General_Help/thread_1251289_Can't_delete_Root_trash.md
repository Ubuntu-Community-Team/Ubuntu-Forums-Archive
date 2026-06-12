---
title: "Can't delete Root trash?"
date: 2009-08-27
forum: General Help
---

### Post by Bruce M. on 2009-08-27
Hi Folks,

Everywhere I look it says root's trash is in:

```
/root/.local/share/Trash/
```

Not for me - it doesn't exist, but Conky is telling me I have 12K in trash, and the trash bin is empty.

Any help?

Thanks
Bruce

---

### Post by Gen2ly on 2009-08-27
Hmm, your trash directory might be different????  Try .Trash.  Otherwise su 2 root (su -) and remove manually:

```
rm /root/.local/share/Trash/* # or
rm /root/.Trash/*
```

---

### Post by uylug on 2009-08-27
I don't get it? The screenshot you posted says you're logged in as root, therefore you're seeing the root trash, which makes sense.

---

### Post by Bruce M. on 2009-08-30
> **uylug said:**
> I don't get it? The screenshot you posted says you're logged in as root, therefore you're seeing the root trash, which makes sense.

No it says I'm using Thunar as root looking in:
```
/root/.local/share/
```
and there is NO - **/Trash** directory there, just an /Application directory.

So how can there be 20K trash in a non-existent directory?

Have a nice day
Bruce

---

