---
title: "can not install mysql, php5 and apache2 server on ubuntu 10.04"
date: 2010-08-04
forum: General Help
---

### Post by pratyushdeka255 on 2010-08-04
currently I am using Ubuntu 10.04.I want to install mysql, php5 and apache2 server in my machine.  I have tried this-- 

aptitude install mysql-server mysql-client  

But the outcome is

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "mysql-server"
Couldn't find any package whose name or description matched "mysql-client"
Couldn't find any package whose name or description matched "mysql-server"
Couldn't find any package whose name or description matched "mysql-client"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

and also tried to install php5 and apache2 in the same way. But could not install.

Also trid inthis way

apt-get install apache2

But the outcome is

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2


How to proceed??

---

### Post by mcduck on 2010-08-04
First, make sure you have a working network connection. :)

Then run the following commands:

```
sudo apt-get update
sudo tasksel install lamp-server
```

That will give you working setup of Apache, MySQL & PHP.

---

### Post by dragos240 on 2010-08-04
A lot of people forget to do apt-get update, on a fresh install.

---

