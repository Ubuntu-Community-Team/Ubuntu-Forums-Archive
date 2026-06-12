---
title: "can't connect to mysql through terminal"
date: 2010-08-01
forum: General Help
---

### Post by MK85 on 2010-08-01
So, I've managed to install xampp on ubuntu and now I want access mysql through the ubuntu terminal. When I try with:

mysql -u root -p

I get:

the application can be found in the following packages
*mysql-client-core-5.1
*mysql-client-5.1
*mysql-cluster-client-5.1
Try: sudo -apt-get install <your chosen package>

But when i use the phpMyAdmin it works fine. So it has to be installed somewhere, right?

Xampp was installed in /opt by default, and the terminal looks for it in /var/run/mysqld/mysqld.sock by default.

I'm wondering if there's a pathvariable you can set so the terminal finds mysql and in that case how to do it.

Thanks!

---

### Post by WorMzy on 2010-08-01
Seems that XAMPP doesn't register it's executables in /usr/bin (or similar), You'll either need to use cd to browse to the executable's location in /opt and run it with "./mysql -p", or create symbolic links to the executables in /usr/bin with "sudo ln -s /path/to/mysql /usr/bin/mysql" and then run it as normal.

---

### Post by MK85 on 2010-08-01
Thank you very much!

You solved all my problems =)

---

### Post by r.mac on 2010-11-26
Hi, I can't find that executable. Can you tell me where I can find it in the /opt folder?

---

### Post by Dave_L on 2010-11-26
In my (rather old version of) XAMPP, it's /opt/lampp/bin/mysql

Also, this command should locate it for you:

$ whereis mysql

---

### Post by r.mac on 2010-11-26
that worked a charm, thanks!

---

