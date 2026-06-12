---
title: "postgresql"
date: 2009-06-26
forum: General Help
---

### Post by babbar.ankit on 2009-06-26
do anyone have experience installing postgresql ...
plz help me out:confused:

---

### Post by cyzak on 2009-06-26
What is the problem exactly?

---

### Post by masux594 on 2009-06-26
Do u need a tutorial to install postgres?

Sysc, A

---

### Post by babbar.ankit on 2009-06-26
I tried installing postgre two ways both failed 
I write the command 
dspace@dspace:~$ sudo apt-get install postgresql[sudo] password for dspace:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package postgresql

---

### Post by cyzak on 2009-06-26
Please go to System > Administration > Software Sources.

And verify that in ubuntu software tab canonical supported Open Source Software check box is chekecd.

---

### Post by SkipCody on 2011-05-12
I am having the same issue. Couldn't find package postgresql

Checked sources.list, Checked  System > Administration > Software Sources. and performed a sudo apt-get update to now avial.

Seems that this is not an issue because very few posts about it. 

BTW I am a new convert to ubuntu and so far so good. 

Any help will be appreciated.

---

### Post by jperelli on 2011-05-12
apt-cache search postgresql
gives you the packages with postgresql

apt-get install postgresql-8.4
installs the DBMS

good luck!

---

