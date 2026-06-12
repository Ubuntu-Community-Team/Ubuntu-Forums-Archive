---
title: "problem in installing mysql"
date: 2011-03-08
forum: General Help
---

### Post by nishant29 on 2011-03-08
i am unable to find from where i have to install mySql i didnt get any software listing in software center which can fulfil as 
mySql command prompt.

plz help me out

---

### Post by new_tolinux on 2011-03-08
I don't know for sure where it's in the software-center, but this should do the trick:

```
sudo apt-get install mysql-server-5.1
```

---

### Post by vivek.pandey on 2011-03-08
try this on terminal type mysql
it will list you mysql packages then
sudo apt-get install packagename
else go to synaptic and quick search mysql

---

### Post by nishant29 on 2011-03-08
> **neo_aryan said:**
> try this on terminal type mysql
it will list you mysql packages then
sudo apt-get install packagename
else go to synaptic and quick search mysql

this is not working.
and i am doing some project related to database conncectivty i had install net beans for coding and i have to use mysql database for backend.
in software center there are lots of package i had install few of them but i am not able to get command prompt form where i can execute my database query

---

### Post by vivek.pandey on 2011-03-08
> **nishant29 said:**
> this is not working.
and i am doing some project related to database conncectivty i had install net beans for coding and i have to use mysql database for backend.
in software center there are lots of package i had install few of them but i am not able to get command prompt form where i can execute my database query

what didnt work ? i mean you are getting an error message?

---

### Post by nishant29 on 2011-03-08
> **neo_aryan said:**
> what didnt work ? i mean you are getting an error message?
nishant@ubuntu:~$ mysql
ERROR 1045 (28000): Access denied for user 'nishant'@'localhost' (using password: NO)
nishant@ubuntu:~$

displaying above error message

---

### Post by lykeion on 2011-03-08
You have to login to mysql prompt as root user (password is empty):
```
mysql -u root
```
Then you should create a new root password, a database and a new user with exclusive rights to the db.

Read more about it here (it's doc for installing LAMP, but the MySQL section is relevant anyway):
[https://help.ubuntu.com/community/ApacheMySQLPHP#After%20installing%20MySQL](https://help.ubuntu.com/community/ApacheMySQLPHP#After%20installing%20MySQL)

---

### Post by vivek.pandey on 2011-03-08
the error it shows mysql is already installed
on terminal type this mysql -u root -p
then it will ask your password and then mysql will be started.

---

