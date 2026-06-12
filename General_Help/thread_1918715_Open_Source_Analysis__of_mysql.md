---
title: "Open Source Analysis  of mysql"
date: 2012-02-01
forum: General Help
---

### Post by 0000_soldier on 2012-02-01
Hey,

Is OS software written to run on a server available to import mysql scripts to manipulate the data in graphs etc?

thanx

---

### Post by cavh on 2012-02-01
You're going to have to be more precise to get an answer on this. Do you have a graphing package already or are you looking for one which has MySQL support?

---

### Post by 0000_soldier on 2012-02-02
ok say i have a recoreded details of a client fitness after a track run  and i want to display the time vs heart rate is thier a program writen in java that could maybey do this?

---

### Post by cavh on 2012-02-02
You don't need Java for this - you could just use LibreOffice Calc or another spreadsheet program. Java is overkill. See screenshot attached.

---

### Post by 0000_soldier on 2012-02-10
The data will be in the format of a .sql script thou?

---

### Post by Rafterman414 on 2012-02-10
Are you looking for a program to display the information or to generate the SQL script for you? Making a SQL script for this to input the data should be pretty easy. For example,

```
INSERT INTO table_fitness (id, name, time, heartrate)
VALUES (1, 'Jeff', 15, 101);

commit;
```If you don't really have a need to use a SQL database then it would probably be easiest to do this in LibreOffice Calc, unless you have other relational tables for each person and the fitness data is just a subset of the data. I can't really think of any program that displays the data you enter and then create a SQL script. Usually it is the other way around and that you enter the data or create the script to enter the data and that display is generate from the information stored in the database. 

If you are looking for a program that can generate insert scripts from information already in a database then SquirrelSQL can do that. That is useful for moving data from one table to another or migrating sets of data from one db to another.

---

### Post by 0000_soldier on 2012-02-10
No, i want the .sql script to be interpreted by a program into a graph:

.sql data collected -> (process) -> graph

---

### Post by Rafterman414 on 2012-02-10
> **0000_soldier said:**
> No, i want the .sql script to be interpreted by a program into a graph:

.sql data collected -> (process) -> graph

Ahh ok I understand, unfortunately I am not aware of any graphing programs that extract data from the .sql script and graph it. I guess you could write a shell script that will extract the data from the Values part of the .sql script and place them into a .csv file. For example using sed and awk the shell script will look in the .sql script text file for any line that starts with Values and then parse those values into another document, pretty much removing the SQL statements and just giving you the values, from there you can use LibreOffice to graph it. Shell scripting is not my thing so I won't be able to tell you how to write the shell script.

---

