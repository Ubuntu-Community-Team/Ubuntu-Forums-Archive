---
title: "MySQL server says &quot;Fail!&quot; on start.  So...now what!"
date: 2010-01-21
forum: General Help
---

### Post by lumix on 2010-01-21
Forgive me; but messages like that make me *grumpy*. No reference to why, or where to check log files...nothing.  After wasting 2 hours trying to find where in the $@!# the log files are, I find /var/log/mysql.err and .log to be empty, and these useless messages in syslog:

```
Jan 21 11:17:48 Atlas kernel: [ 7346.607378] type=1503 audit(1264090668.281:347): operation="open" pid=12293 parent=12292 profile="/usr/sbin
/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan 21 11:17:49 Atlas kernel: [ 7347.628867] type=1503 audit(1264090669.301:348): operation="open" pid=12303 parent=12302 profile="/usr/sbin
/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan 21 11:17:49 Atlas kernel: [ 7347.643913] type=1503 audit(1264090669.321:349): operation="open" pid=12312 parent=12311 profile="/usr/sbin
/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan 21 11:17:49 Atlas /etc/init.d/mysql[12319]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resul
ted in
Jan 21 11:17:49 Atlas /etc/init.d/mysql[12319]: #007/usr/bin/mysqladmin: connect to server at 'localhost' failed
Jan 21 11:17:49 Atlas /etc/init.d/mysql[12319]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
'
Jan 21 11:17:49 Atlas /etc/init.d/mysql[12319]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Jan 21 11:17:49 Atlas /etc/init.d/mysql[12319]:
Jan 21 11:18:05 Atlas kernel: [ 7363.770911] type=1503 audit(1264090685.451:350): operation="open" pid=12511 parent=12510 profile="/usr/sbin
/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan 21 11:18:05 Atlas kernel: [ 7363.792093] type=1503 audit(1264090685.471:351): operation="open" pid=12520 parent=12519 profile="/usr/sbin
/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
```

Why are they meaningless?  Because, no, mysqld.sock does not exist, yet I'd have not the faintest clue where to buy one if given a map.  More google, you say?  Nah, that just says "well create one!"  Good job, that.  I wonder what it should contain?  I dunno.  I suspect nothing at all, but then--why is there a problem in the first place?

Though uname -r says "unknown", I believe I have an AMD64 chipset.  But that wasn't the problem either, since I tried that package, and anyway apt-get seemed to know that.

*Very--grumpy*.

---

### Post by lykwydchykyn on 2010-01-21
Can you give some history here?  Is this a new installation of MySQL?  Did anything procede this failure, like an update or dirty shutdown?

And -- let me get this straight -- you run "uname -r" and it returns "unknown"??  

This sounds bad.

As for creating mysqld.sock, you could always just try:
```

sudo touch /var/run/mysqld/mysqld.sock

```

Though I don't represent that it'll fix the problem.  I thought mysqld made it's own socket on startup.

Are you running apparmor by chance?  Maybe try shutting down apparmor.

---

### Post by lumix on 2010-01-22
The server is a new install with very little on it.  The MySQL failure occurred right from the apt-get install completion on.  Tried rebooting too, just in case.

I did know that touch will create an empty file, but wasn't sure how that would help.  I'm also getting the impression that you did, that mysqld would create the .sock file.

---

### Post by lykwydchykyn on 2010-01-22
What version of Ubuntu?  Which release/variant/architecture?

---

