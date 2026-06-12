---
title: "ORACLE -&gt; Nothing happens when clicking on &quot;Start Database&quot;"
date: 2011-01-14
forum: General Help
---

### Post by micael3000 on 2011-01-14
Hello,

I've installed Oracle XE yesterday (forcing architecture, cause i am using amd64), it was working fine until i reboot my computer.

At the beginning i wasn't able to start because i was getting an error:
- "Operation failed. my_user is not a member of 'dba' group."

So, i went to System -> Administration -> Users and Groups -> Manage Groups -> (selected 'dba') -> Properties, and checked my user.

But now, when i click on "Start Database", the cursor stay 'waiting' and after some time it goes back to the pointer and nothing happens. On "Run SQL Command Line" i get "SP2-0640: Not connected" and in "Go To Database Homepage":
- "Firefox can't establish a connection to the server at 127.0.0.1:1234"

(When installing i chose port 1234)


Now i cant uninstall it (I've installed it through dpkg for forcing architecture, and opening the .deb package i don't get the "uninstall" button)

What can I do? Have anyone had this issue before?

Thanks in advance.

---

### Post by Waappu on 2011-01-15
Hi,

Problem is probably that dba group can not write listener log.
You can start database and listener from terminal
```

sudo /etc/init.d/oracle-xe start

```

Or try add write permission to log file and see if it help
```

sudo chmod g+w /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log

```

---

### Post by micael3000 on 2011-01-15
sudo /etc/init.d/oracle-xe start

It don't work :/

Nothing happens. Terminal executes the command without any errors or messages, and oracle is still down...

---

### Post by Waappu on 2011-01-16
Hi,

Oracle XE is only for 32bit os. So it might you missing some package.

But try this and post results:
Open SQLplus in terminal
```

sqlplus '/as sysdba'

```
run
```

startup

```
Post what is printed.
If database starts OK, then start listener
```

$ORACLE_HOME/bin/lsnrctl start

```
and check listener status and post result
```

$ORACLE_HOME/bin/lsnrctl status

```

---

### Post by micael3000 on 2011-01-17
content removed.

---

### Post by micael3000 on 2011-01-17
content removed.

---

### Post by micael3000 on 2011-01-17
content removed.

---

### Post by micael3000 on 2011-01-17
```
my_user@my_laptop:~/Desktop$ sqlplus '/as sysdba'
sqlplus: command not found
```


As i said, when i first installed it everything was ok, so, i don't believe there are packages missing...

I opened the "Run SQL Command" in Oracle menu (Applications -> Oracle Database 10g Express Edition) and typed "startup": ORA-01031: insufficient privileges.
Then i dragged it to desktop and there was a "Run SQL Command.desktop". I opened it in gedit and copied the path from Exec. In terminal i did: sudo *path*. The Oracle Terminal Console opened and i typed again startup... The same error: insufficient privileges.


;/


```
my_user@my_laptop:~/Desktop$ $ORACLE_HOME/bin/lsnrctl start
bash: /bin/lsnrctl: No such file or directory
```

---

### Post by Waappu on 2011-01-17
Hi,

You have not set enviroment variables.
Add to your .bashrc at last lines
```

ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
PATH=$PATH:$ORACLE_HOME/bin
export ORACLE_HOME
export ORACLE_SID=XE

export PATH

```

Logout and back in.
Then run what I did post in my previous post

BTW, what instructions you have follow to install ?
Have you select that database is not started automatically on boot?
That generates these kind problems

---

### Post by micael3000 on 2011-01-17
```
my_user@my_laptop:~$ sqlplus '/as sysdba'

SQL*Plus: Release 10.2.0.1.0 - Production on Mon Jan 17 10:10:43 2011

Copyright (c) 1982, 2005, Oracle.  All rights reserved.

Connected.
SQL> startup
ORA-01081: cannot start already-running ORACLE - shut it down first
SQL> shutdown immediate
ORA-24324: service handle not initialized
ORA-24323: value not allowed
ORA-01090: shutdown in progress - connection is not permitted
SQL> startup
ORA-01031: insufficient privileges
SQL> 
```However, Oracle isn't up. When i open its website (on  localhost) i have a message that firefox couldn't connect to the host...

Then i tried to run the ```
$ORACLE_HOME/bin/lsnrctl start
``````
my_user@my_laptop:~$ $ORACLE_HOME/bin/lsnrctl start

LSNRCTL for Linux: Version 10.2.0.1.0 - Production on 17-JAN-2011 10:14:10

Copyright (c) 1991, 2005, Oracle.  All rights reserved.

Starting /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/tnslsnr: please wait...

TNSLSNR for Linux: Version 10.2.0.1.0 - Production
System parameter file is /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/admin/listener.ora
Log messages written to /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log
Error listening on: (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC_FOR_XE)))
TNS-12555: TNS:permission denied
 TNS-12560: TNS:protocol adapter error
  TNS-00525: Insufficient privilege for operation
   Linux Error: 1: Operation not permitted

Listener failed to start. See the error message(s) above...
```I have  executed the command ```
sudo chmod g+w  /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log
```:s

--------edit---------

I dont remember what guide i have followed, sorry...
Yes, database is not starting automatically. :)

---

### Post by Waappu on 2011-01-17
Hi,

Hmm. I do not know what is wrong.

Try set that database is started on boot.
```

sudo nano /etc/default/oracle-xe

```

And change quite begin on file row
```

ORACLE_DBENABLED=flase

```
to
```

ORACLE_DBENABLED=true

```

Boot PC and see does database work.
Note, when you boot there might be delay before listener register connection.
So wait few min before you try open database home

---

### Post by micael3000 on 2011-01-17
Its now working!

Thanks a lot for helping so fast :D

---

### Post by Waappu on 2011-01-17
Hi,

Good.

It is best keep setting that database is started on boot.
That way database is also closed probebly when you shutdown PC and prevent possible data entry losts.
Of course boot is bit slower this way.

---

