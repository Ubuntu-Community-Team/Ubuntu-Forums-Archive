---
title: "Why no LibreOffice Base?"
date: 2012-01-03
forum: General Help
---

### Post by zhaotianwu on 2012-01-03
Hi! Does anyone know why isn't LibreOffice Base shipped with Ubuntu 11.10 by default? Is there any security or other concerns over that? I'm quite surprised since I used it quite heavily under Windows. I do not mind installing it, but would really like to know the reason. Many thanks.

---

### Post by mastablasta on 2012-01-03
it is probably in repositories.
 
everything can't fit on a CD.

---

### Post by sanderd17 on 2012-01-03
Base is not popular as it's not compatible with MS Access, and there are a lot of other, better alternatives such as MySQL, PostgreSQL, SQLite ...

Those alternatives are more scalable, and you can use them with a number of front-ends (including websites via headless servers).

---

### Post by zhaotianwu on 2012-01-03
So it is not because of any technical/security concerns over Base?

---

### Post by sanderd17 on 2012-01-03
> **zhaotianwu said:**
> So it is not because of any technical/security concerns over Base?

If it's in the official repositories, there are no security concerns over it. For the technical concerns, you have to know what you need, Canonical can't do that for you.

---

### Post by zhaotianwu on 2012-01-03
> **sanderd17 said:**
> Base is not popular as it's not compatible with MS Access, and there are a lot of other, better alternatives such as MySQL, PostgreSQL, SQLite ...

Those alternatives are more scalable, and you can use them with a number of front-ends (including websites via headless servers).

 I appreciate your advice, but my application is only for single user and only for desktop use, no internet involved. So MySQL, PostgreSQL seem to be overkill. As for SQLite, although it is very cute and embedded very well in C Programming environment, it is a bit too lagged behind in terms of SQL standard compliance. 

That's why I chose Base (with HSQLDB being the backend): designed for single-user, and more functionality built-in. 

Please feel free to correct me if my reasoning is flawed, and could you please give me some advice if my choice is not the optimal one? I would appreciate it very much. Thanks.

---

### Post by sanderd17 on 2012-01-03
> **zhaotianwu said:**
> I appreciate your advice, but my application is only for single user. So MySQL, PostgreSQL seem to be overkill. As for SQLite, it is very cute and embedded very well in C Programming environment, but it is a bit too lagged behind in terms of SQL standard compliance. That's why I chose Base (with HSQLDB being the backend): Single-user, and more functionality built-in. Could you give me some advice if my choice is not the optimal one? I would appreciate it very much. Thanks.

If it works for you, there is no reason to change it. I only gave a reason why it's not on the CD.

Btw, it has been a long time since I really used OpenOffice.org, and I have never used LibreOffice. So I can't really judge on the quality of their products.

---

