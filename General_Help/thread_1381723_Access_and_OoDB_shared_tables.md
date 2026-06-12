---
title: "Access and OoDB shared tables"
date: 2010-01-15
forum: General Help
---

### Post by cyblance on 2010-01-15
Any help please? 
I am migrating a few of the company's boxes to ubuntu (open Office data). A few of the remote machines are still using access. My questions are:
1.  Is it possible to get a single platform to hold tables that both access and OoDB can read and write too?
2. Which - if any - of these would be the most stable?
3. Is this even possible?

---

### Post by cyblance on 2010-08-02
Ever get the feeling you're talking to yourself?

---

### Post by oldfred on 2010-08-02
You could use any sql database. I used pervasive, then MS sql server for files in Access. Access has a tool to update from Access to MS sql server but I have not updated to MySQL or postgreSQL. Corporate was windows only and I have not needed Access at home. You then use ODBC to link your tables into Access. Sometimes a few things have to be modified as the tables may not be exactly the same. I also used queries to replace tables in some cases.

[http://blog.moybella.net/2007/03/10/converting-microsoft-access-mdb-into-csv-or-mysql-in-linux/](http://blog.moybella.net/2007/03/10/converting-microsoft-access-mdb-into-csv-or-mysql-in-linux/)
To get the list of tables, you run the following command:
    mdb-tables database.mdb
You can then get a CSV version for each table using:
    mdb-export database.mdb table_name
You can also convert the mdb into a format required by MySQL. First you must get the put the table schema into the database using the following command:
    mdb-schema database.mdb | mysql -u username -p database_name
You then import each table by running:
    mdb-export -I database.mdb table_name | sed -e 's/)$/)\;/' | mysql -u username -p database_name
Sed is required as mdb-export doesn't put a semi-colon at the end of each insert statement,  which MySQL definately doesn't like.
After running this, you can now be rid of the horror that are Access MDB files :)

---

### Post by cyblance on 2010-08-04
Thanks for this - will let you know if I win.

---

### Post by cyblance on 2011-12-05
Great all sorted.

As suggested - converted all my tables to CSV and exported them to MySql which now runs as the backend.  Serious tweaking needed for date, currency and other formats which was great because the tables are now more robust.

Started off using Knoda to quickly rewrite the forms.  But soon moved to OpenOffice Base for all the form and report work.  OOoBase or me (most likely the latter) is a little clumsy when querying MySql but works.

Imported all of the queries which worked with minimal tweaking and voila up and running.  Sorry I didn't mark this as solved sooner.

Thanks for the help.

---

### Post by oldfred on 2011-12-05
Glad that worked, hope it did not take all this time to complete it.:)

---

### Post by cyblance on 2011-12-05
lol - very nearly. Just threw caution to the wind and switched - the increase in system startup time and data access speed made up for the "this things not working" issues. Big learning curve.

---

