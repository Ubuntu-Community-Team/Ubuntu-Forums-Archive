---
title: "Startup Order"
date: 2009-08-13
forum: General Help
---

### Post by 696f6e6963 on 2009-08-13
I have two scripts A and B that start up upon boot (in rc2.d, 3, 4, and 5). However, it appears that B is starting before A - how can I change this?

P.S - I have no GUI, command line only.

---

### Post by zkriesse on 2009-08-13
Check this out. It might help. [http://docstore.mik.ua/orelly/unix2.1/sedawk/appb_01.htm](http://docstore.mik.ua/orelly/unix2.1/sedawk/appb_01.htm)

---

### Post by tgeer43 on 2009-08-13
> **696f6e6963 said:**
> I have two scripts A and B that start up upon boot (in rc2.d, 3, 4, and 5). However, it appears that B is starting before A - how can I change this?The startup scripts in the folders start with S and then a number. The scripts are executed numerically according to this number AFAIK.

Just make sure that script A's filename has a lower number than script B's. ie. S04script_a and S09script_b.

Hope this helps,

tgeer

---

