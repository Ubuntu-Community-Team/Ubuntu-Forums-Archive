---
title: "MySQL Problem"
date: 2005-01-26
forum: General Help
---

### Post by python on 2005-01-26
I have successfully installed MySQL server and all associated packages. When trying to create a sever using 'sql-navigator' (a gui MySQL program), I am prompted to enter a socket to connect to. I have searched and cannot find a '.sock.' file on the system.

What shall I do?!  :-?

---

### Post by machiner on 2005-01-26
Is mysql-server running?

---

### Post by LanceM on 2005-01-26
[QUOTE=machiner]Is mysql-server running?[/QUOTE]
 mysql.socks should be created when the service is started.

code:
mysqld start

---

### Post by python on 2005-01-26
I've got it all sorted out now- thanks!

---

