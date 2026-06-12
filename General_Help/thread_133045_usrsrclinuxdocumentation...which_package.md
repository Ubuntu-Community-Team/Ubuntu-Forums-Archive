---
title: "/usr/src/linux/documentation...which package?"
date: 2006-02-19
forum: General Help
---

### Post by 5-HT on 2006-02-19
Hi, I've come across a few instances where I needed to refer to documentation within /usr/src/linux/documentation.

Problem is that /usr/src/linux/documentation is empty after a default Ubuntu install.

I'm just wondering what I need to download to get that directory?

Would it be kernel-source, kernel-headers, linux tree...etc? 

Thanks for any help

---

### Post by ranf on 2006-02-20
You can either install the full kernel source (package `linux-source-(VERSION)')
or if you just want the documentation install package `linux-doc-2.6.12'.

In the second case the docs are in 
/usr/share/doc/linux-doc-2.6.12/Documentation/

---

### Post by 5-HT on 2006-02-20
[QUOTE=ranf]You can either install the full kernel source (package `linux-source-(VERSION)')
or if you just want the documentation install package `linux-doc-2.6.12'. [/quote]

Beautiful, thanks a lot.

The docs alone should be sufficient, it's nice that you mentioned they'd be in a different directory in that case.

---

