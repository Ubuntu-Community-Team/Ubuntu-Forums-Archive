---
title: "LOAD DATA into mySQL not loading?"
date: 2009-12-18
forum: General Help
---

### Post by shawn.bordeaux on 2009-12-18
I have a csv file "data.csv" that is stored in the var/lib/mysql/jras_intranet/ folder, that I am trying to load into a mySQL table named "test" the database is named "jras_intranet". For sake of simplicity the "data.csv" file has only two collumns and no headers. The data looks like this;

joe,smith
mike,richards
susan,doe

The table named "test" is setup with these fields;

ID = Primary Field / identity
first_name = varchar(50)
last_name = varchar(70)

So I run the below command from the terminal prompt and once I press enter I get no notices but just an arrow for a cursor like this   >

```

mysql -uroot -p12345 -e "LOAD DATA INFILE 'data.csv' INTO TABLE jras_intranet.test FILEDS TERMINATED BY ',' ENCLOSED BY '"' LINES TERMINATED BY '\n';

```12345 is the root password for the root SQL account which has full access to the jras_intranet database.

I am in desperate need for help in how to properly insert this data. I know I must be doing something wrong.

Thank you and best regards,

Shawn

---

### Post by wojox on 2009-12-18
Try LOAD DATA LOCAL INFILE

---

### Post by shawn.bordeaux on 2009-12-18
Thank you. I've tried that with the same result...

---

### Post by wojox on 2009-12-18
Looks like you forgot the closing ( " ) marks at the end of the command. Should be '\n'";

---

### Post by shawn.bordeaux on 2009-12-18
Thank you! That was part of the problem. The other part is that I was misspelling "FIELDS" - All is good now. Thanks! :)

---

