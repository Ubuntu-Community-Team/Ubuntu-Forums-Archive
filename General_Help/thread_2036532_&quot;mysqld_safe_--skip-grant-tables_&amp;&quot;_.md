---
title: "&quot;mysqld_safe --skip-grant-tables &amp;&quot;   hangs"
date: 2012-08-02
forum: General Help
---

### Post by jiapei100 on 2012-08-02
Hi, all:

I'm trying to reset mysql password, according to the tutorial here [http://rhcelinuxguide.wordpress.com/2008/08/25/mysql-error-1045-28000-access-denied-for-user-rootlocalhost-using-password-yes/]("http://rhcelinuxguide.wordpress.com/2008/08/25/mysql-error-1045-28000-access-denied-for-user-rootlocalhost-using-password-yes/") .


However, as for the first step after stop mysql server, program hangs without progressing:
> pei@pei-GA-870A-UD3:~/mysql$ mysqld_safe --skip-grant-tables &
[2] 30380
pei@pei-GA-870A-UD3:~/mysql$ 120802 01:54:06 mysqld_safe Logging to syslog.
120802 01:54:06 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
120802 01:54:06 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended


Any suggestions please?


Cheers
Pei

---

### Post by Wim Sturkenboom on 2012-08-02
It's not hanging, it's terminated by the looks of it (see the last line). Reason might be that you need root privileges, not sure.

Except for that, don't expect the prompt to come back (unless you press <enter>) ;)

And, don't use guides for RH if you're using Ubuntu; calling for problems. The following might be a better approach: [https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

---

### Post by jiapei100 on 2012-08-02
Hi, Thanks Wim.

Even with root, still hangs.


> root@pei-GA-870A-UD3:/home/pei# 120802 10:45:11 mysqld_safe Logging to syslog.
120802 10:45:11 mysqld_safe A mysqld process already exists




Ok... I just stopped it by "Enter"..And if I move on the next step
```
$ mysql
```

I got the following error message:

> root@pei-GA-870A-UD3:/home/pei# mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
root@pei-GA-870A-UD3:/home/pei# 




> **Wim Sturkenboom said:**
> It's not hanging, it's terminated by the looks of it (see the last line). Reason might be that you need root privileges, not sure.

Except for that, don't expect the prompt to come back (unless you press <enter>) ;)

And, don't use guides for RH if you're using Ubuntu; calling for problems. The following might be a better approach: [https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

---

### Post by Wim Sturkenboom on 2012-08-03
Follow the instructions in the link that I posted. Just checked and they work for 10.04

```

root@pei-GA-870A-UD3:/home/pei# 120802 10:45:11 mysqld_safe Logging to syslog.
120802 10:45:11 mysqld_safe A mysqld process already exists

```
tells you that mysql was already running, so you have to stop it first

> 
Ok... I just stopped it by "Enter"..And if I move on the next step

You did not stop anything

---

### Post by jiapei100 on 2012-08-03
Thanks Wim.
But how to stop it?
Then, the problem might be
```
$ /etc/init.d/mysql stop
```
is not able to stop the mysql service.....
Well, then, how to effectively stop it?



> root@pei-GA-870A-UD3:/home/pei# /etc/init.d/mysql stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mysql
root@pei-GA-870A-UD3:/home/pei# mysqld_safe --skip-grant-tables &
[1] 11455
root@pei-GA-870A-UD3:/home/pei# 120803 10:11:51 mysqld_safe Logging to syslog.
120803 10:11:51 mysqld_safe A mysqld process already exists
^C



Cheers
Pei

---

### Post by Wim Sturkenboom on 2012-08-04
In my case,the instructions did stop the service (although I had the same warning).

After your attempt to stop, run *_ps -ef | grep mysqld_*. You will get 0, 1 or 2 lines. 0 lines means it is stopped, 2 lines means it's still running and 1 line is either the grep command (in which case the service was stopped) or that line is the mysqld service in which case it's not stopped.

If mysqld is not stopped, stop it with the kill command and the pid from the ps command. No system at hand to test, hence no code to show.

PS: Found a way to show
```

wim@aa0:~$ ps -ef |grep vi
wim       1727  1713  0 15:10 pts/0    00:00:00 vi hallo.txt
wim       1747  1732  0 15:10 pts/1    00:00:00 grep vi
wim@aa0:~$ kill 1727
wim@aa0:~$ ps -ef |grep vi
wim       1749  1732  0 15:13 pts/1    00:00:00 grep vi
wim@aa0:~$ 

```
The process is vi instead of mysqld, but the principle is the same.

---

### Post by jiapei100 on 2012-08-04
Hi, Wim:

Thanks for your reply. 
You can see from the following, there is only 1 line when I try
```
$ ps -ef | grep mysqld
```
However, still,
```
mysqld_safe --skip-grant-tables &
```
just keeps hanging....


> pei@pei-GA-870A-UD3:~$ ps -ef | grep mysqld
mysql     1011     1  0 12:16 ?        00:00:01 /usr/sbin/mysqld
pei       4078  2931  0 13:01 pts/0    00:00:00 grep --color=auto mysqld
pei@pei-GA-870A-UD3:~$ sudo /etc/init.d/mysql stop
[sudo] password for pei: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mysql
mysql stop/waiting
pei@pei-GA-870A-UD3:~$ ps -ef | grep mysqld
pei       4094  2931  0 13:01 pts/0    00:00:00 grep --color=auto mysqld
pei@pei-GA-870A-UD3:~$ mysqld_safe --skip-grant-tables &
[1] 4096
pei@pei-GA-870A-UD3:~$ 120804 13:02:51 mysqld_safe Logging to syslog.
120804 13:02:51 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
120804 13:02:51 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended



I've got to press **Enter** in order to stop it.
However, is this **Enter** a must during the whole process?


Cheers
Pei

---

### Post by Wim Sturkenboom on 2012-08-06
First of all, you don't press <enter> to stop it. It is already stopped, but just did not give you the prompt back ;)

The problem is the last line. For some reason mysqld terminates with an error (by the looks of it). Maybe because you don't use the skip-networking option (as described in the earlier link).

Check the following files for what goes wrong.
```

/var/log/mysql.err - MySQL Error log file
/var/log/mysql.log - MySQL log file

```

Also, have a look at post #4 in [this thread](http://ubuntuforums.org/showthread.php?t=1836919) for an alternative approach to reset of passwords; it might work better for you.

---

