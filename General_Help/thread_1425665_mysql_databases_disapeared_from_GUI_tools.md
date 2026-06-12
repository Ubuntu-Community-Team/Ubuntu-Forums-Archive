---
title: "mysql databases disapeared from GUI tools"
date: 2010-03-09
forum: General Help
---

### Post by sinchan_ on 2010-03-09
hi all

After changing the administrator password only information_schema and test databases are shown in GUI tools (webmin or mysql administrator GUI tool). After the error I restored the password to the old used

if I use mysql in terminal, and use *show databases;* I can see the 7 databases that I have. 

I aslo cannot access to any field using GUI tools (cannot acces to database permissions, or MySQL Server Configuration, host permissions or MySQL system variables). The error is:

DBI connect failed : Access denied for user ''@'localhost' to database 'mysql'

Do you know how to restore the view/access to databases?

---

