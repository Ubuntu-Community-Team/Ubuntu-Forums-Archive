---
title: "Why does Ubuntu ignore Windows file permissions?"
date: 2012-01-30
forum: General Help
---

### Post by zander x on 2012-01-30
Hello all,

I have a question that needs a thorough answer. Why does Ubuntu ignore Windows file permissions?

I'm not complaining about it, in fact I thank the Flying Spaghetti Monster for this. I recently had to recover data from a Win 7 HD and Windows simply would not allow me to copy the data due to its "file permissions" (no matter what I did, I got "access denied"). When I put the HD in a converter and booted into Ubuntu, it came right up. It took 4 hours, but I was able to copy the files. I need to explain, in depth, why this worked.

Thanks guys!

---

### Post by Vaphell on 2012-01-30
there is not much to say. Windows recognizes ntfs permissions as his own and honors them, while they are incompatible with linux permission structure and the system completely ignores them.

---

### Post by 2F4U on 2012-01-30
Windows and Linux implement permissions in a completely different way. On top of this comes, that comes that Microsoft technology is proprietary and often not publicly documented.

---

### Post by zander x on 2012-01-31
Thanks guys! Those are good enough answers for me!

---

