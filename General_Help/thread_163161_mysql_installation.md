---
title: "mysql installation"
date: 2006-04-20
forum: General Help
---

### Post by ampop on 2006-04-20
After mysql installation, I did:
#mysqladmin -u root password my_password

and it appears these message:
"mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'"


And, when I go to the MYSQL Administrator panel, I put:
Server Hostname: localhost
Username: root
(I don't put password)

It appears these message:
"Could not connect to host 'localhost'.
MySQL Error Nr. 1045
Access denied for user 'root'@'localhost' (using password: NO)
Click the 'Ping' button to see if there is a networking problem."

When I do ping, I have communication.


Any idea how to solve this problem?
Thanks!

---

### Post by cgjones on 2006-04-20
You will need to use the password you set when you typed:
```
mysqladmin -u root password my_password
```

---

### Post by dermotti on 2006-04-20
you didnt literly type my_password as your password did you?

If you want your password to be **dragon**, you should type:

**mysqladmin -u root password dragon**

---

### Post by DeadEyes on 2006-04-20
Have you run **mysql_install_db** to set up the grant tables?

---

### Post by ampop on 2006-04-20
The problem begins when I fist time typed:
#mysqladmin -u root password my_password
(I didn't typed my_password, I just don't want that you know my password) :-D

So, I define the password on the fist time I typed the code, right?

I follow the guide: [http://ubuntuguide.org/#installmysqldatabaseserver]("http://ubuntuguide.org/#installmysqldatabaseserver")
Q: How to install MYSQL Database Server?

DeadEyes: I don't know nothing about **mysql_install_db**.

I really need mysql database to run joomla.

I already tried to uninstall mysql using synaptic. But after reinstall, I always have the described error.
How I completely uninstall mysql, and begin again a new right installation?

Thank you for your help. Any more suggestions please.

---

### Post by cgjones on 2006-04-20
Right, typing the following will set the password for the root user on the MySQL database.
```
mysqladmin -u root password *newpassword*
```

I don't think mysql_install_db should be an issue here, because I'm pretty sure that mysqld won't even run without the grant tables being initialized.

Nothing else comes to mind right now, but I'll keep thinking about it and see what I can come up with.

---

### Post by ampop on 2006-04-20
It's solved. I did:

sudo apt-get remove --purge mysql-server
sudo apt-get install mysql-server

And it's fix.

In: ([https://launchpad.net/distros/ubuntu/+ticket/24]("https://launchpad.net/distros/ubuntu/+ticket/24"))

Anyway, I'm very happy with your quickly help.
Thank you.

---

### Post by Nordoelum on 2006-04-21
Will that remove all account data you have stored on the server? In other word, how to reset the whole mysql server.

---

### Post by ampop on 2006-04-21
In my case I haven't any mysql data. But I think that it's better to save SQL data base before do 'sudo apt-get remove --purge mysql-server'.

---

