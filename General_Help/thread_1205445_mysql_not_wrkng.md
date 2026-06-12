---
title: "mysql not wrkng"
date: 2009-07-06
forum: General Help
---

### Post by babbar.ankit on 2009-07-06
mysql -u root -p
when i use this command in the terminal it works but

simply if i type 
mysql 
it has error 1045, i can't find any permant soln to prblm
And when i try to install drupal it say no database found.

Please help asap

---

### Post by credobyte on 2009-07-06
1045 means "Access Denied" ( it's users mistake, not mysql "error" ) ! You need to specify username & password to be able to use this command.
Drupal - before installing, you need to create a new database and user ( you should not use root for website databases ).

---

