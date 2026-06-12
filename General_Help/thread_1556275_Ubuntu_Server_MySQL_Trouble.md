---
title: "Ubuntu Server MySQL Trouble"
date: 2010-08-19
forum: General Help
---

### Post by jaya28inside on 2010-08-19
My mistake...
We already installed everything until i made some changes,

I did change the my.cnf
file which was changing its bind-address ip,
thus, after that i couldn't even connect to mysql again.

So I ended up with many times removing and installing it
both manually (delete folders) or commandly.

I dunno until which part now,
but once I do this

```

apt-get install mysql-server

```

it always got stuck!
hang.

no wonder, I terminate it. CTRL +Z.

And then, i check at 

```

ps aux

```

anyone who access mysql folder, etc... I terminate it via Kill PID.
next, I keep struggling.

I do removing the mysql manually, from 
these locations

/etc/mysql
/etc/init.d/mysql
/var/log/mysql
/var/lib/mysql

all of them are dead now.
And then, :lolflag: I try again, to remove
via 
```

apt-get remove mysql-server

```

and 

```

apt-get remove mysql-common

```

but What I got is,,, stuck. again...
on this line of process...

> 
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  libdbd-mysql-perl libmysqlclient16 mysql-client-5.1 mysql-client-core-5.1
  mysql-common mysql-server-5.1 mysql-server-core-5.1
0 upgraded, 0 newly installed, 7 to remove and 26 not upgraded.
After this operation, 58.0MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 46441 files and directories currently installed.)
Removing mysql-server-5.1 ...



anyone could suggest me which locations again that I need to delete 
first before attempting to either executing remove or install from apt-get command?

*NB: I actually want to post on Server Platform since I'm using Ubuntu Server.But I can not access those section. So I posted here. Sorry guys. Need help. :(

---

### Post by nbkr on 2010-08-19
No problem to see on the output. If ```
sudo apt-get remove mysql-server
``` runs into an error it normally shows an error message. Unfortunately there is no error message in your post, so I assume you just have to wait a bit longer until the removal finishes or shows a real error.

---

### Post by jaya28inside on 2010-08-22
Hmm... nbkr, I hope so.
but, I'm not sure for it.
It just made me mad within more than 15 minutes in hang mode.
gosh, :D I ended it up with closing it with BREAK.


after I restarted the machine. 
And I checked the ps aux,
seems that the mysql was not running at the time machine started up.
Is there any missing thing I need for it, nbkr?

---

### Post by nbkr on 2010-08-23
What does ```
 dpkg -l | grep -i mysql 
``` show?

---

### Post by jaya28inside on 2010-08-23
nbkr,
i thought now is okay...

> 
ii  libdbd-mysql-perl               4.012-1ubuntu1                    A Perl5 da
tabase interface to the MySQL data
ii  libmysqlclient16                5.1.41-3ubuntu12.6                MySQL data
base client library
ii  mysql-client-5.1                5.1.41-3ubuntu12.6                MySQL data
base client binaries
ii  mysql-client-core-5.1           5.1.41-3ubuntu12.6                MySQL data
base core client binaries
ii  mysql-common                    5.1.41-3ubuntu12.6                MySQL data
base common files (e.g. /etc/mysql
ii  mysql-server                    5.1.41-3ubuntu12.6                MySQL data
base server (metapackage depending
ii  mysql-server-5.1                5.1.41-3ubuntu12.6                MySQL data
base server binaries
ii  mysql-server-core-5.1           5.1.41-3ubuntu12.6                MySQL data
base core server files


now another simptomp seems arose,,,
it's slower than ever... 
I tried to connect via SSH through Tunneling (windows)
and yes, of course it's slow now...
is it any /etc/resolve.cnf effect on this?

---

