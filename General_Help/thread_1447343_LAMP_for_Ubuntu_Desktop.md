---
title: "LAMP for Ubuntu Desktop?"
date: 2010-04-05
forum: General Help
---

### Post by YongQing on 2010-04-05
I want to test out a LAMP (linux, apache, mysql and php) program called WebERP. But I found out that Ubuntu server only has a command interface and learning the commands would slow me down too much.

Is it possible to get a LAMP program up n running on Ubuntu Desktop? Could anyone please kindly point out the links to tutorials for setting up apache, mysql and php so as to convert my Ubuntu Desktop to a server with a GUI?

---

### Post by Mighty_Joe on 2010-04-05
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by kblft on 2010-04-05
you can try installing xampp for linux

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

note that this will install separately from ubuntu's installers - which makes it ideal for testing

---

### Post by 3rdalbum on 2010-04-05
Usually after installing Ubuntu Server, you would run this command:

```
sudo tasksel install lamp-server
```

to actually turn your Ubuntu Server installation into a LAMP server.

Ubuntu Desktop is virtually the same as Ubuntu Server, but with a GUI; they use the same repositories and same commands. So you can use the 'tasksel' command to install all the LAMP packages on your Ubuntu Desktop system. They will automatically be configured to work in conjunction with eachother, too; that's pretty awesome.

---

### Post by YongQing on 2010-04-06
> **3rdalbum said:**
> Usually after installing Ubuntu Server, you would run this command:

```
sudo tasksel install lamp-server
```

to actually turn your Ubuntu Server installation into a LAMP server.

Ubuntu Desktop is virtually the same as Ubuntu Server, but with a GUI; they use the same repositories and same commands. So you can use the 'tasksel' command to install all the LAMP packages on your Ubuntu Desktop system. They will automatically be configured to work in conjunction with eachother, too; that's pretty awesome.
Yeah I tried that on my Ubuntu Server. But without a GUI, I'm totally lost. If I do that on Ubuntu Desktop, any idea what I should do to get a GUI for the Apache, MySQL? something like a cpanel? Or maybe install a cpanel itself?

---

### Post by lordskid on 2010-04-06
you can install cpanel although I used myPHP.

---

### Post by YongQing on 2010-04-06
how do i install myphp or cpanel?

---

### Post by Oasu4g on 2010-05-12
A good question. I don't seem to see them in the Jaunty repos. That doesn't mean they're not in subsequent releases though.

I am also looking for a GUI to manage my MySQL databases & options. What would be the best one available?

Thanks for any input,

Tim

---

### Post by WorMzy on 2010-05-12
I think the program you're looking for is called phpMyAdmin, not myPHP. ;)

Running 'sudo apt-get install phpmyadmin' in a terminal will install it for you. :)

---

