---
title: "MySQL on Ubuntu Server"
date: 2010-08-13
forum: General Help
---

### Post by zombie_ on 2010-08-13
Hello everyone, 

I would like to know how I can use the MySQL that already installed, on  Ubuntu server?

I can categorize my question into three questions. 

- How I can start MySQL?
- How I can add a data base host?. 

On Ubuntu itself I just use mysql -u root and it works but not on the server!

Thanks in advance,

---

### Post by surfer on 2010-08-13
```
mysql -u root
```
should work when you are logged in locally on the server... what is the error message?

once logged in you have to [grant permissions]("http://dev.mysql.com/doc/refman/5.1/en/adding-users.html") to users.

---

### Post by zombie_ on 2010-08-13
mysql -u root gives me: 

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

Even when I do 

mysql -u root -p whatever

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)


I used these commands on my username and as a root.

---

### Post by zombie_ on 2010-08-13
> **surfer said:**
> ```
mysql -u root
```
should work when you are logged in locally on the server... what is the error message?

once logged in you have to [grant permissions]("http://dev.mysql.com/doc/refman/5.1/en/adding-users.html") to users.
mysql -u root gives me: 

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

Even when I do 

mysql -u root -p whatever

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)


I used these commands on my username and as a root.

---

### Post by surfer on 2010-08-13
try:

```
mysql -u root -p
```

and just hit enter at the password prompt. if i remember correctly, you can not supply a password with -p, you'd have to write

```
mysql -u root --password="thepassword"
```

---

### Post by zombie_ on 2010-08-13
> **surfer said:**
> try:

```
mysql -u root -p
```

and just hit enter at the password prompt. if i remember correctly, you can not supply a password with -p, you'd have to write

```
mysql -u root --password="thepassword"
```
The error still the same. 

I assume I need to change something from my.cnf file inside mysql directory. I did not uncomment anything from the file.
Any idea on that one?

---

### Post by surfer on 2010-08-13
did you try [this]("http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/")? or [this]("http://www.ubuntugeek.com/reset-the-root-password-on-mysql.html")?

---

### Post by zombie_ on 2010-08-13
> **surfer said:**
> did you try [this]("http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/")? or [this]("http://www.ubuntugeek.com/reset-the-root-password-on-mysql.html")?
The first solution actually worked!
I can now go and use MySQL with mysql -u root -p and then enter my password!.

Cheers

---

