---
title: "PHPMYADMIN Package not showing up"
date: 2006-05-12
forum: General Help
---

### Post by Twenty on 2006-05-12
Every time i put the command into terminal to install phpmyadmin...Can anyone help me fix this or tell me what i need to do?

---

### Post by harisund on 2006-05-12
You will have to enable the universe repository in order to install phpmyadmin. Have you done that? 

And what command are you using to install phpmyadmin?

---

### Post by Twenty on 2006-05-13
Im using sudo apt-get phpmyadmin
How do you get the universal sepositories or w/e?
Thanks for your help :D

---

### Post by harisund on 2006-05-13
To enable Universe and Multiverse see [http://wiki.ubuntu.com/AddingRepositoriesHowto](http://wiki.ubuntu.com/AddingRepositoriesHowto) - Official sources.lists
              here: [http://paste.ubuntu-nl.org/6047](http://paste.ubuntu-nl.org/6047) (Breezy) or [http://paste.ubuntu-nl.org/6666](http://paste.ubuntu-nl.org/6666) (Dapper) see also !easysource

---

### Post by GSX550ES on 2006-05-17
I also have the same problem, sorry but we all have to learn sometimes. I was following the instructions off [https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29](https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29)
The PHP4 link doesn't work on there as well but installed PHP5, so the commands i have entered are

$ sudo apt-get install apache2
$ sudo apt-get install mysql-server
$ sudo apt-get install libapache2-mod-auth-mysql
$ sudo apt-get install php5-mysql
$sudo apt-get install phpmyadmin

This is where I get the error 

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package phpmyadmin

Tried to go in via System, Administration, Synaptic Package Manager

But phpmyadmin is not there, I have updated the list but still nothing, any help would be apprieciated.

---

