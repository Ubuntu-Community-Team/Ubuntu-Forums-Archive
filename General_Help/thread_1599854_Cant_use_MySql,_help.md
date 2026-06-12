---
title: "Cant use MySql, help"
date: 2010-10-18
forum: General Help
---

### Post by Lancro on 2010-10-18
Im using apache2 with mysql, php, phpmyadmin, you know, lamp, I have installed all using a tutorial from this forums, but when I try to install a phpBB3 forum It tells me that I havent permisions, I have loaded the console and typed mysql, this is the error it returns...

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

So I cant use it, I need help with how I have access to mysql to create the databases for phpBB3, to set a user and to set a password...

Thanks

---

### Post by WorMzy on 2010-10-18
Have you set up mySQL?

Open a terminal and run
```
sudo mysql_secure_installation
```

and follow the instructions.

---

### Post by Lancro on 2010-10-18
Thanks!!, now I have another problem with the installation of phpBB3, the database, I am suposed to create it, I thought it was created by the installer, now the error in phpBB3 installation is...

[B]Could not connect to the database, see error message below.
Unknown database 'phpbb3'

[/B]**[COLOR=Black]t[/COLOR]**[B][FONT=Arial][COLOR=Black]hats the database name I want for my database, how I create a database for phpBB3 or phpnuke (I will install this one too, so lets prevent).
[/COLOR][/FONT][/B]
**[FONT=Arial][COLOR=Black]Thanks.[/COLOR][/FONT]**

---

### Post by Lancro on 2010-10-18
Solved with phpmyadmin, thanks.

---

