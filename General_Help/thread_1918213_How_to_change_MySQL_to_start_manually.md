---
title: "How to change MySQL to start manually?"
date: 2012-01-31
forum: General Help
---

### Post by fredand44 on 2012-01-31
Hello guys!

I got MySQL installed and it start up as a service. 

To save CPU and RAM I wonder if there is a way to force MySQL to only start if I want it to?

I would prefer like this:
sudo /etc/init.d/mysql start

What do you think guys is this a possible?

Best regards
Fredrik

---

### Post by ruffEdgz on 2012-01-31
If there is a service I want to disable at start up, I run the command 'update-rc.d'. For example:
```

sudo update-rc.d mysql disable

```
This will make sure that the service 'mysqld' is disabled in all runlevels. I ran this for the service 'apache2' and this is the output it gave me:
```

update-rc.d: warning: apache2 start runlevel arguments (none) do not match LSB Default-Start values (2 3 4 5)
update-rc.d: warning: apache2 stop runlevel arguments (none) do not match LSB Default-Stop values (0 1 6)
 Disabling system startup links for /etc/init.d/apache2 ...
 Removing any system startup links for /etc/init.d/apache2 ...
   /etc/rc0.d/K09apache2
   /etc/rc1.d/K09apache2
   /etc/rc2.d/S91apache2
   /etc/rc3.d/S91apache2
   /etc/rc4.d/S91apache2
   /etc/rc5.d/S91apache2
   /etc/rc6.d/K09apache2
 Adding system startup for /etc/init.d/apache2 ...
   /etc/rc0.d/K09apache2 -> ../init.d/apache2
   /etc/rc1.d/K09apache2 -> ../init.d/apache2
   /etc/rc6.d/K09apache2 -> ../init.d/apache2
   /etc/rc2.d/K09apache2 -> ../init.d/apache2
   /etc/rc3.d/K09apache2 -> ../init.d/apache2
   /etc/rc4.d/K09apache2 -> ../init.d/apache2
   /etc/rc5.d/K09apache2 -> ../init.d/apache2

```
Now the service 'apache2' will not start in any runlevel.

Hope this helps.

---

### Post by Dngrsone on 2012-01-31
It can be done very simply with this command:

```
sudo update-rc.d -f mysql remove
```

Information on the update-rc.d command can be found [here](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

---

### Post by fredand44 on 2012-02-01
Hello Guys!

Thanks for all replies!

I tested:
sudo update-rc.d mysqld disable
But I got:
update-rc.d: /etc/init.d/mysqld: file does not exist

I also tested: 
sudo update-rc.d -f mysql remove
And got:
Removing any system startup links for /etc/init.d/mysql ...

But after a reboot I still can connect to MySql without strating it manually.

What do you think guys?
Do I miss something?

(The version I got installed is: mysql-server 5.1.58-1ubuntu1)

Best regards
Fredrik

---

### Post by ruffEdgz on 2012-02-01
If you do the following command, does anything come up:
```

ll /etc/rc*.d/ | grep -i "mysql"

```
If something comes up like SXXmysql -> ../init.d/mysql, then my command should work but I misspelled it. I changed it on my previous post but I will repeat it here:
```

sudo update-rc.d mysql disable

```

When you ran the command:
```

sudo update-rc.d -f mysql remove

```
Did anything else come up after the line "Removing any system startup links for /etc/init.d/mysql ..." or was that is? You should have seen something like this after running that command (it might have been different on your system):
```

/etc/rc1.d/S90mysql
/etc/rc2.d/S90mysql
...
ect
...

```

---

### Post by fredand44 on 2012-02-02
Hello again amigos!

I tried:
ll /etc/rc*.d/ | grep -i "mysql"
...but nothing came up (I guess that is good?)

How ever I tried the following twice, I'm pretty sure the out come was the same each time, but something back in my head recall some line that you said the first time I ran it:
If I run it now I just get: 
fredrik@LinuxOne:~$ sudo update-rc.d -f mysql remove
[sudo] password for fredrik:
 Removing any system startup links for /etc/init.d/mysql ...
fredrik@LinuxOne:~$

And the MySQL still answers.

So if you got any idea do not hesitate to ...

Best regards
/Fredrik

---

### Post by Dngrsone on 2012-02-02
How can we tell that mysql is actually running in the background and not being called up as you run the command?

---

### Post by fredand44 on 2012-02-02
Hello guys!

Yes I understand your doubts, but I have checked.
I call mysql through some Java-application.

I checked:
fredrik@LinuxOne:~$ ps -A | grep mys
  898 ?        00:00:24 mysqld

So I guess the process still is on.

To make sure I will restart my computer and run the ps command again!
Back in a minute or two!

/Fredrik

---

### Post by fredand44 on 2012-02-02
Hello again!

I just restarted Ubuntu and run the command:

fredrik@LinuxOne:~$ ps -A | grep mys
  882 ?        00:00:00 mysqld
fredrik@LinuxOne:~$ 

Do we miss something?

Best regards
Fredrik

---

### Post by wojox on 2012-02-02
```
gksudo gedit /etc/init/mysql.conf
```

Look for:
```
start on (net-device-up
          and local-filesystems
	  and runlevel [2345])
stop on runlevel [016]
```

Comment theses lines:
```
#start on (net-device-up
#          and local-filesystems
#	  and runlevel [2345])
stop on runlevel [016]
```

That’s it for the MySQL server. Now you can start it manually using following command:
```
sudo service mysql start
```

---

