---
title: "MySQL Error"
date: 2012-07-31
forum: General Help
---

### Post by apejam on 2012-07-31
This is really weird. I developed some php scripts for a class and wanted to test them in windows because that is what the professor will be seeing them in, and I just wanted to make sure they were fine.

I boot into windows, install xampp and test, ok so far so good. I logout to get back to my linux partition and try to view the scripts again and I get this error.

Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Is it possible that the settings in xampp on windows messed up the MySQL on Linux?

any ideas for a fix?

---

### Post by satish_j on 2012-08-01
Is mysql service started?
have you checked telnetting to mysql port(i dont remember its value,may be 3305)?

---

