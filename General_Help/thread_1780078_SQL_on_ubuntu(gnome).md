---
title: "SQL on ubuntu(gnome)"
date: 2011-06-11
forum: General Help
---

### Post by akarade on 2011-06-11
1-I've installed SQL through snaptyc package manager but when I go into the applications menu, I cannot find any SQL.

2- I would also like to know how to use SQL through opneofficedatabase?

---

### Post by Habitual on 2011-06-11
```
mysql -uroot -p -h localhost
```

In LibreOffice Base, you can access data that is stored in a wide variety of database file formats. LibreOffice Base natively supports some flat file database formats, such as the dBASE format. You can also use LibreOffice Base to connect to external relational databases, such as databases from MySQL or Oracle.
The following database types are read-only types in LibreOffice Base. From within LibreOffice Base it is not possible to change the database structure or to edit, insert, and delete database records for these database types:
Spreadsheet files
Text files
Address book data
Using a Database in LibreOffice
To create a new database file, choose File - New - Database.
The Database Wizard helps you to create a database file and to register a new database within LibreOffice.

The database file contains queries, reports, and forms for the database as well as a link to the database where the records are stored. Formatting information is also stored in the database file.

To open a database file, choose File - Open. In the File type list box, select to view only "Database documents". Select a database document and click Open.

*Substitute LibreOffice for OpenOffice* or whatever that was.

---

