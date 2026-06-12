---
title: "MySQL Error 2002 (HY000)"
date: 2012-03-27
forum: General Help
---

### Post by Hidalgo1231 on 2012-03-27
This has probably been discussed here ad nausem. I have read a couple of threads concerning this, but none of them solved my issue. I desperately need for MySQL to work again. It was working earlier this morning no problems, but now it's not. I haven't installed/uninstalled any additional software (other than MySQL server), nor have I done anything to any config files. I try starting it:

```
mysql -u root -p
```

I get the error message:

```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

I try restarting, and stopping then starting MySQL with:

```
sudo service mysql restart
sudo service mysql stop
sudo service mysql start
```

but I still receive the same error message. I run the command:

```
ps -ef |grep mysql
```

and it returns

```
root      5339  2721  0 16:32 pts/0    00:00:00 grep --color=auto mysql
```

Also, I have noticed that in the directory /var/run/mysqld there is no mysqld.sock. I have tried to find where it might have gone with *whereis mysqld.sock*, but it's nowhere to be found.

I've tried installing/uninstalling mysql-server with apt-get install and apt-get remove, but it didn't help. I have tried purging and reinstalling, and it doesn't help either. Is there a way to just make a new mysqld.sock file and put it in the correct directory? Any advice would be greatly appreciated.

---

### Post by Habitual on 2012-03-27
Did you edit my.cnf recently?

---

### Post by Hidalgo1231 on 2012-03-27
No, I haven't edited that.

---

### Post by Habitual on 2012-03-28
Try reconfigure using 
Terminal > 
```
sudo dpkg-reconfigure mysql-server
```

When it's done, it should start the mysqld process and then try to connect.

---

### Post by Hidalgo1231 on 2012-03-28
Thanks. I tried it and it didn't work. I asked one of my professors about it today and she said it could have something to do with an alias... I'm not sure what that is though.

---

### Post by Hidalgo1231 on 2012-04-03
My MySQL is working again. I think the culprit file was an apache2 my-sites-enabled file with a syntax error in line 1. The file path was:

/etc/apache2/sites-enabled/Csci387

I can't be certain that this was the file, but as soon as I fixed it MySQL would work again.

---

### Post by Habitual on 2012-04-03
+1 and props for fixing it yourself. :)

---

### Post by greenscreen on 2012-05-21
I had similar problem. This post helped:

[http://ubuntuforums.org/showthread.php?t=804021](http://ubuntuforums.org/showthread.php?t=804021)

---

### Post by itmanvn on 2012-05-27
> **greenscreen said:**
> I had similar problem. This post helped:

[http://ubuntuforums.org/showthread.php?t=804021](http://ubuntuforums.org/showthread.php?t=804021)

That thread was not helped me. But this should work::popcorn:
```
sudo apt-get remove apparmor
```

---

