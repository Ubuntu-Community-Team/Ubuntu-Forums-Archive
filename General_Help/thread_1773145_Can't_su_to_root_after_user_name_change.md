---
title: "Can't su to root after user name change?"
date: 2011-06-01
forum: General Help
---

### Post by the ev on 2011-06-01
I recently changed a user account on my system and now I can't `su` into root. I'm logged in via SSH to a slice on [Slicehost]("http://www.slicehost.com")

I ran this to change my user account:
```

~: usermod -l admin theev

```

Then, logged in as `admin`, I try to run this:
```

~: su
Password: 
su: Authentication failure

```

I know I'm typing in the correct password, because if I use Slicehost's Console for my account and log in as root, the password I type in grants me access.

What's going on? Let me know if you need any additional info to help me with this.

Other info:

```

~: groups
admin

```

```

~: cat /etc/passwd
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
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
dhcp:x:101:102::/nonexistent:/bin/false
syslog:x:102:103::/home/syslog:/bin/false
klog:x:103:104::/home/klog:/bin/false
sshd:x:104:65534::/var/run/sshd:/usr/sbin/nologin
Debian-exim:x:105:109::/var/spool/exim4:/bin/false
postgres:x:106:111:PostgreSQL administrator,,,:/var/lib/postgresql:/bin/bash
ftp:x:107:65534::/home/ftp:/bin/false
splunk:x:1002:1002:Splunk Server:/opt/splunk:/bin/bash
mysql:x:108:112:MySQL Server,,,:/var/lib/mysql:/bin/false
sd-agent:x:109:113:Server Density Agent User,,,:/usr/bin/sd-agent/:/bin/bash
admin:x:1000:1000:Admin,,xxx-xxx-xxxx,:/home/admin:/bin/bash

```

---

