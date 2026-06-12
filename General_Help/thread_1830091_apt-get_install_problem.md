---
title: "apt-get install problem"
date: 2011-08-21
forum: General Help
---

### Post by appz on 2011-08-21
Hello! 

When I try to install, for example phpMyAdmin ( using command sudo apt-get install phpmyadmin ) , ssh console give to me this answe:

```
root@ubuntu:/etc/apache2# apt-get install phpMyAdmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package phpMyAdmin

```A few days ago, this package could be installed, but now it couldn't ...

What can I do? Is a problem with my dedicated server :( ?

EDIT: same problem for apt-get install pure-ftpd on laur account ( not root )

```
laur@ubuntu:~$ sudo apt-get install pure-ftpd
[sudo] password for laur:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package pure-ftpd
laur@ubuntu:~$
```

---

### Post by raja.genupula on 2011-08-21
do update once with 

```
sudo apt-get update
``` in terminal 

and then  try again

---

### Post by appz on 2011-08-21
it works, thank you so much !! :D

---

### Post by raja.genupula on 2011-08-21
hmmm please mark this thread solved man . to do it goto thread tools and click at mark as solved . remember this for everytime , when you got solved your issue.have a nice day .

---

