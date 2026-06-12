---
title: "Looking for a simple Inventory Control system"
date: 2012-08-23
forum: General Help
---

### Post by tbendubois on 2012-08-23
Hi everyone,

I have been digging around to find an inventory control system for a company I am working with, and I have found things like Django inventory, dot-Project, and SQL-Ledger, but I'm wondering what other options are out there. I have looked at Freecode and did some googling, and I like the idea of the web based platform. We need compatibility for QR and Barcode (RS-232), and really only need the inventory aspect. I liked some of the features of SQL-Ledger, like the ability to assign parts in inventory to a certain product and when we sold one of those products all the inventory items would decrease.

I had trouble getting SQL Ledger installed and same with Django inventory but that might just be me (although Django had an internal error with python)

Have you had a good experience with a program that would be close to what I need? It would be great to get some other opinions.

---

### Post by oldfred on 2012-08-23
This is in synaptic, but I have not used it.

Tryton is a high-level general purpose application platform written in Python
and using PostgreSQL as database engine. It is the core base of a complete
business solution.

---

### Post by tbendubois on 2012-08-23
Thanks for the suggestion! I will look into it and give it a try. It looks like the Tryton demo servers are not functioning at the moment so I will attempt to install it and hopefully I like it!

---

### Post by oldfred on 2012-08-23
It looked like the inventory only module was in synaptic which means you can download directly from Ubuntu. It probably is to get you hooked on the application so you upgrade to a full system, but if all you want is inventory, it seems like it may be worth the experiment.

Being python & PostgreSQL means you should be able to make changes if you want, if you know python and sql queries.

---

### Post by racheljiayou on 2012-09-13
Django is nice

---

