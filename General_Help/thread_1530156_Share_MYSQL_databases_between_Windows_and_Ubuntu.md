---
title: "Share MYSQL databases between Windows and Ubuntu"
date: 2010-07-13
forum: General Help
---

### Post by Oded Dwek on 2010-07-13
Hey,

Assuming I have:

- Ubuntu 10.4 and windows 7 dual booted, at same PC, same hard drive (different partition)
- exactly the same mysql version (5.1.0.49 something like that) installed in both OS's.

Is there a way to make linux MYSQL to load the windows MYSQL databases? (so they will be shared).


Thanks :).

---

### Post by sdowney717 on 2010-07-13
as long as it is a mounted drive, and if the mysql server is configured to access that DB, it should work.
normally DB folder is in the data directory of mysql
Linux will respect capitals. I wrote a VB app that uses mysql for windows. 
I then ran the mysql server for linux hosting the database on ubunut and acessed it from another windows box and it was foobared due to table name issues
I ended up making all the tables lowercase names.

---

### Post by satish_j on 2010-07-13
I dont think it is possible...
You can run any one OS at a given time.
Assuming you have booted into Linux,even if the windows drive is mounted,mysql service also needs to be running on windows to access the data files which are on windows filesystem.
mysql services on linux will access data files from linux system only..
BTW,it is really a good question;)

---

### Post by sdowney717 on 2010-07-13
the service can run on ubuntu
the database file can be somewhere outside of the normal location.
reconfigure the server to look for it there
[http://developer.spikesource.com/wiki/index.php/How_to_change_the_mysql_database_location](http://developer.spikesource.com/wiki/index.php/How_to_change_the_mysql_database_location)

---

### Post by Oded Dwek on 2010-07-14
Thanks everyone :)

---

