---
title: "Trouble Starting Python Script Via rc.local"
date: 2012-06-03
forum: General Help
---

### Post by kwikness on 2012-06-03
I have a python daemon process that gets started via rc.local. This same script, with the same permissions, is installed on a few other Ubuntu boxes I have. It runs without trouble on those installations. That is, after restarting the box, the daemon process is running. 

With this particular installation though, the daemon process is not running by the time I log in and check for the existence of the process. The rc.local files between systems are identical (or at least close enough):
```
localaccount@sosms:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

python /var/www/myDaemon/Main.py > /var/log/somelog.txt

exit 0
```The permissions are:```

localaccount@sosms:~$ ls -la /etc/rc.local
-rwxr-xr-x 1 localaccount localaccount 370 Jun  3 11:04 rc.local
```I tested if the rc.local process is getting executed by using this test rc.local:```
localaccount@sosms:/var/log/sosmsd$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo "test" > /home/localaccount/test1
/usr/bin/python /var/www/sosms/sosmsd/Main.py > /var/log/sosmsd/log/log
echo "test" > /home/localaccount/test2

exit 0
localaccount@sosms:/var/log/sosmsd$

```And only the first test file (test1) gets created after restarting the box:
```
localaccount@sosms:~$ ls
test1

```

Why isn't this installation behaving like my other ones? What can I do to fix it?

---

### Post by kwikness on 2012-06-06
I've determined that the Python process is failing because it can't create a connection to MySQL. I logged my output from rc.local like this:
```
/usr/bin/python /var/www/python/Main.py > /var/log/mylog/log/log 2>&1

```

Output after restarting:
```
Traceback (most recent call last):
  File "/var/www/python/Main.py", line 10, in <module>
    queue_handler = QueueHandler.QueueHandler()
  File "/var/www/python/QueueHandler.py", line 19, in __init__
    passwd = 'password123', db = 'test')
_mysql_exceptions.OperationalError: (2002, "Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)")

```

I also put the following in my /etc/rc.local and it printed nothing:
```
ls /var/run/mysqld > /var/log/mylog/log/log 2>&1
```

However, when I run it after I SSH in:
```
localaccount@sosms:~$ ls /var/run/mysqld > /var/log/mylog/log/log 2>&1
localaccount@sosms:~$ cat /var/log/mylog/log/log 
mysqld.pid
mysqld.sock
localaccount@sosms:~$ 

```

Again, when the machine is already up and I SSH in and execute the rc.local script manually, it comes up and runs fine.

Does anyone have some advice?

---

### Post by kwikness on 2012-06-07
bump

---

