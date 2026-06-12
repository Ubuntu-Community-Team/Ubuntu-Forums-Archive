---
title: "Open Office Base Question"
date: 2009-10-01
forum: General Help
---

### Post by CrusaderAD on 2009-10-01
I'm connecting to a MS SQL Server database through Open Office's Base program using a JDBC driver on Ubuntu. I can connect to the database just fine, but when running queries and opening tables, a lot of the data is blank. I know these fields have data in them. It seems to be the fields with letters in them. The fields that are just integers pull up fine. Any ideas?

---

### Post by CrusaderAD on 2009-10-02
Update: Seems to only be with nvarchar fields.

---

### Post by CrusaderAD on 2009-10-02
Appaerently JDBC doesn't support nvarchar... but it works fine with squirrel SQL and it's using the same driver.

---

### Post by CrusaderAD on 2009-10-05
I also tried the ODBC driver. It connects fine but doesn't let me run any queries.

> The data content could not be loaded.

FreeTDS SQL Server Incorrect Syntax near 'tablename'.

---

### Post by CrusaderAD on 2009-10-05
Apparently you need brackets around the object.

> select * from [tablename]

It needs to run the sql command directly to work.

---

### Post by CrusaderAD on 2009-10-08
The ODBC driver works to run queries but I can't find anyway of updating the data. It doesn't let you edit it. The only way to do so would be to run an update statement which is too time consuming if your changing many rows of data. Oh well, at least squirrel sql works great.

---

