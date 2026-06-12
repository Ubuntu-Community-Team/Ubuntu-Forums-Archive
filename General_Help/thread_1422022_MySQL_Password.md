---
title: "MySQL Password"
date: 2010-03-04
forum: General Help
---

### Post by Eightbyte on 2010-03-04
***Can't find the title edit, but this problem is solved***

I have just recently installed MySQL along with Apache and PHP (using 'sudo apt-get install'), and I'm getting this error: ERROR 1045 (28000): access denied for 'skies'@'localhost' (using password: YES) whenever I try to do anything with MySQL.
I've Googled the error and not much has come up besides things that did not help. 
How would one go about resetting the password? I've tried uninstalling via terminal, and when I re-installed the password appeared to be still the same instead of reset. I heard somewhere that the default was blank, but I remember setting a password when I installed it. (one that seems to not work, or I could have mistyped it.)
Also, I'm still a bit new to the whole Linux OS.

Thanks in advance for any help. ;)

---

### Post by n0dix on 2010-03-04
See [this]("http://library.linode.com/databases/mysql/install-mysql-ubuntu-9.10-karmic#using_mysql"), and scroll down.

---

### Post by Eightbyte on 2010-03-05
Will do, denkya.
EDIT:
I put this in:
'dpkg-reconfigure mysql-server-5.1'
And it says it must be run as root, and ALT f2 + gksudo isn't working. Same with ALT f2 sudo.

---

### Post by mcduck on 2010-03-05
> **Eightbyte said:**
> Will do, denkya.
EDIT:
I put this in:
'dpkg-reconfigure mysql-server-5.1'
And it says it must be run as root, and ALT f2 + gksudo isn't working. Same with ALT f2 sudo.

Open a terminal (not Alt-F2) and run "sudo dpkg-reconfigure mysql-server-5.1"

If you get any errors then post them here ("it didn't work" doesn't really tell anything about what didn't work and why).

---

### Post by Eightbyte on 2010-03-05
Ah, that was the problem. Thank you.
But now it's still denying my password even though I just reset it.
I just tried 'mysql -u skies -p' entered my password, and it gave me the same error. Perhaps I go study that page again.

EDIT: trying it with 'mysql -u root -p'
tried
worked
success
Okay! thank you for the help and disregard the above problem ^

---

### Post by jmichelsen on 2010-03-05
Steps to reset mysql password:

First, you're going to want to kill the mysql istance.

```
sudo killall mysqld
```

OR

```
sudo /etc/init.d/mysql stop
```

Then start mysql like this to let it allow you to login without a password, the & sends the daemon to the background so you can run more commands.

```
mysqld --skip-grant-tables &
```

Once its started and running, type:

```
mysql -u root mysql
```

This will get you into mysql as root. once in, type this to change the user password.

```
mysql> UPDATE user SET Password=PASSWORD(‘yourpasswordhere’) WHERE User=’yourusernamehere’;
mysql> FLUSH PRIVILEGES;
```

mysql should confirm that these completed successfully, after that you can exit mysql, kill the running mysqld with ```
killall mysqld
``` and start mysql back up like normal with ```
sudo /etc/init.d/mysql start
```

You should now be able to login as your user with your new password. You can test your new password by logging into mysql on the command line like ```
mysql -u username -p mysql
```

anyway, hope this helps

---

### Post by Eightbyte on 2010-03-05
> **jmichelsen said:**
> Steps to reset mysql password:

First, you're going to want to kill the mysql istance.

```
sudo killall mysqld
```OR

```
sudo /etc/init.d/mysql stop
```Then start mysql like this to let it allow you to login without a password, the & sends the daemon to the background so you can run more commands.

```
mysqld --skip-grant-tables &
```Once its started and running, type:

```
mysql -u root mysql
```This will get you into mysql as root. once in, type this to change the user password.

```
mysql> UPDATE user SET Password=PASSWORD(‘yourpasswordhere’) WHERE User=’yourusernamehere’;
mysql> FLUSH PRIVILEGES;
```mysql should confirm that these completed successfully, after that you can exit mysql, kill the running mysqld with ```
killall mysqld
``` and start mysql back up like normal with ```
sudo /etc/init.d/mysql start
```You should now be able to login as your user with your new password. You can test your new password by logging into mysql on the command line like ```
mysql -u username -p mysql
```anyway, hope this helps

Thank you much, I appreciate it, but I already have it figured out. ;)

---

### Post by DaithiF on 2010-03-05
although the approach above works, [this]("http://code.openark.org/blog/mysql/dangers-of-skip-grant-tables") is the preferred approach:

---

### Post by n0dix on 2010-03-05
If the problem is solved change the title.

---

