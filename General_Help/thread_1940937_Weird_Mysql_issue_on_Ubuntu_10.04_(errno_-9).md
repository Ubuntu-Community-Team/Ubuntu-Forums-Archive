---
title: "Weird Mysql issue on Ubuntu 10.04 (errno: -9)"
date: 2012-03-14
forum: General Help
---

### Post by mteppo on 2012-03-14
Just stumbled onto something which may (or may not) be useful if someone else is as stupid as me.
Took me 2 hours to figure out.

Symptoms: I was getting errors like this to one Mysql client log

```
Can't create file '/tmp/#sqlac83_45a50f5_a.frm' (errno: 9)
```

Namely this was MythTV and it caused MythTV not to record anything, but the issue was not MythTV specific.

This issue is more described at:
[http://bugs.mysql.com/bug.php?id=60574](http://bugs.mysql.com/bug.php?id=60574)

perror 9 says:
```
$ perror 9
OS error code   9:  Bad file descriptor

```
So something fishy there. The illogical thing is that it is not with the file /tmp/ but it is with the file permissions of the source file for the query. Most of the time I was fixing perms on /tmp/ but no avail.

So Mysql statement
```
CREATE TEMPORARY TABLE barney LIKE fred;
```
accesses fred.frm file somewhere - mine was in /var/lib/mysql/_DB_NAME_/

The file permissions should look like:
```
-rw-rw---- 1 mysql mysql     8556 2012-03-14 22:21 fred.frm
```

Now I tried to issue chmod - but it did not help.
Finally I noticed that I had confusion (most propably my own doing) in /etc/passwd and /etc/group files - there were overlapping / mixed id's there, namely mysql users group was also assigned to another group.

The funny thing was that this stopped only working when I updated to mysql-server 5.1.61-0ubuntu - before that all was working ok.

So just in case someone else stumbles upon this there is more strict permission checks on this version of Mysql than the previous so you may need to check the permissions.

Ugh.

---

