---
title: "Import OOdb to Mysql"
date: 2009-07-25
forum: General Help
---

### Post by jwferk on 2009-07-25
Can anyone tell me how to import an existing OO database to mysql?

I have a large database created in OpenOffice Database.  What I would like to do is import it to Mysql and then use phpmyadmin to search the database.

Since I have recently rebuilt I have the newest versions of php5, phpmyadmin, mysql and OO.

I've also installed the latest JDBC drivers and connectors.

Thanks in advance for any help you can give.

jwferk

---

### Post by jwferk on 2009-07-28
I was finally able to do this in a somewhat brute force manner. Nonetheless, it worked.

1-Open the OO database, select Tables and copy the database table to OO calc spreadsheet.

2 - Save the OO spreadsheet in text.cvs format
3 - Using phpmyadmin, create a new database and create a table in the database that contains all the fields that were originally in the OO db. It is only necessary to enter the field titles (equivalent to column headers in the original OO database). It is important that the field names are exact matches between the original OO db and the new db in Mysql.
4 -select the "import" function for your myphpadmin database.
5- Using the "Browse" function, set the path to the text.cvs copy of the database.
6 - make the following entries on the "import" page:

a. select CSV using LOAD DATA options
b. Check box 'ON' for Replace table data with file
c. in Fields terminated by box type ,
d. in Fields enclosed by box "
e. in Fields escaped by box \
f. in Lines terminated by box auto
g. in Column names box type column name seperated by like
column1,column2,column3
h. check box ON for Use LOCAL keyword.

6 - hit "go" in phpmyadmin

I was able to successfully import a 600 line, 15 field database of Linux command functions that I had created for my own use. It can now be viewed in phpmyadmin in html format and is completely searchable.

---

