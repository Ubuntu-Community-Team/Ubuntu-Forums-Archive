---
title: "Speed to query database"
date: 2010-10-16
forum: General Help
---

### Post by fantastic on 2010-10-16
Right now I have one table with multiple columns in postgresql. As rows increase (right now over 10,000), will querying degrade?

Is it more efficient for me have multiple tables with only two (2) columns and joining them?

I'm expecting more data and I just want to be able to update and query it quicker.

---

### Post by TeoBigusGeekus on 2010-10-16
Index the columns you use in your queries. It will speed up queries.

---

### Post by fantastic on 2010-10-16
> **TeoBigusGeekus said:**
> Index the columns you use in your queries. It will speed up queries.

When I have more rows, say like 250,000 or much more, will it still matter?

---

### Post by junapp on 2010-10-16
> **fantastic said:**
> Right now I have one table with multiple columns in postgresql. As rows increase (right now over 10,000), will querying degrade?

Is it more efficient for me have multiple tables with only two (2) columns and joining them?

I'm expecting more data and I just want to be able to update and query it quicker.

Without seeing your data, knowing the number of users logged at a time etc, reads vs updates/inserts, indexes etc, I would be willing to guess that you'll be better off with the one table, avoiding the multiple joins for redundant tables.

If you haven't heard about third normal form, it might be worth looking up.

It all depends on your data and how you intend to use it.

---

### Post by TeoBigusGeekus on 2010-10-16
Especially when you have more rows.

---

### Post by junapp on 2010-10-16
also depends on how many records you want returned from a single query. How would you define "degrade"?

---

