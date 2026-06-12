---
title: "SSH not releasing terminal after command is executed."
date: 2010-09-07
forum: General Help
---

### Post by stewartm82 on 2010-09-07
Hello,

When I run the following command from my macbook to my ubuntu server the terminal does not get released. It just sits there until I Control-C the command.

```
ssh user@my-server 'sudo /etc/init.d/nginx start'
```

When i login and then run the command everything works fine.

```

ssh user@my-server
sudo /etc/init.d/nginx start

```

Here is the output highlighting the issue

```

~ $ ssh me@somewhere.com
me@somewhere.com's password: 
Last login: Mon Sep  6 15:18:18 2010 from 
me@somewhere:~$ sudo /etc/init.d/nginx restart
[sudo] password for me: 
Restarting nginx daemon: nginx.
me@somewhere:~$ exit
logout
Connection to somewhere.com closed.
~ $ ssh me@somewhere.com 'sudo /etc/init.d/nginx restart'
me@somewhere.com's password: 
[sudo] password for me:

Restarting nginx daemon: nginx.

```

After the last command executes it just holds there and does nothing. Thanks in advance for any advice you might have.

```

me@somewhere:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"
me@somewhere:~$ 

```

---

### Post by midenok on 2010-10-26
Try redirecting STDOUT to /dev/null

Better inside the script, though 

ssh user@my-server 'sudo /etc/init.d/nginx start > /dev/null'
should also work.

---

