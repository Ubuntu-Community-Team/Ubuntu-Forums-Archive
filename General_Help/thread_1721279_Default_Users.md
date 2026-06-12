---
title: "Default Users"
date: 2011-04-04
forum: General Help
---

### Post by systemshq on 2011-04-04
I'm new to Ubuntu and have just set-up a server. I notice that it comes with the following list of users already set-up:-

```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:100:101::/nonexistent:/bin/false
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
sshd:x:103:65534::/var/run/sshd:/usr/sbin/nologin
mysql:x:104:105:MySQL Server,,,:/var/lib/mysql:/bin/false
libuuid:x:105:109::/var/lib/libuuid:/bin/sh
statd:x:106:65534::/var/lib/nfs:/bin/false
postfix:x:107:112::/var/spool/postfix:/bin/false
```

I'm worried about the users which have a shell login e.g. list, backup, news.

Is it necessary to change the password of these default users to be on the safe side? Is it ok to change the default shell of list, backup, news to /bin/false as no-one will ever login under these users?

Many thanks in advance

---

### Post by 3Miro on 2011-04-04
Those are system users, you are no supposed to login as them. If you don't setup a password, you cannot login as that user.

Those users exist so that processes can run as specific user and be restricted in that way. For example sshd would run the ssh server and will not be able to mess things up for mysql.

---

### Post by systemshq on 2011-04-04
That's great - many thanks!

---

