---
title: "Prevent mysql starting on boot"
date: 2011-10-16
forum: General Help
---

### Post by endontoddy on 2011-10-16
Hi everyone,

I have mysql-server installed, but would prefer it not be started at boot time (I only need it when doing development work). I can't seem to work out how to tell Ubuntu (11.10) NOT to start it at boot though. I've looked though the /etc/rc*.d directories to no avail. I've tried installing BUM and using that but it already thinks mysql ISN'T started at boot.

Rather confusing! :(

Give a chap a hand?

Thanks!

---

### Post by akakingess on 2011-10-16
When you say that you have it installed, did you install Ubuntu server, or install LAMP, or MySQL manually, or what?  Shorter question:  How was MySQL installed?

---

### Post by endontoddy on 2011-10-16
I mean I installed the mysql-server package myself post-os-installation via apt

---

### Post by akakingess on 2011-10-16
Let me boot into my Ubuntu, but I thought there was a way to tell MySQLd not to start on boot, let me verify and then edit this post. May take a couple of minutes.

---

### Post by endontoddy on 2011-10-18
*BUMP*

Anyone? I'm sure it is something simple!

---

### Post by Dangertux on 2011-10-18
The following can be used to prevent a service from starting at boot time

```

sudo update-rc.d -f mysql remove

```

You can then just start it when needed using

```

sudo /etc/init.d/mysql start

```

hope that helps.

---

### Post by endontoddy on 2011-10-18
Thanks :) but unfortunately that doesn't seem to work. After running that command and rebooting, if I run: 

```
ps aux | grep mysql 
```

I get:```


mysql      876  0.4  2.5 137644 17848 ?        Ssl  20:13   0:00 /usr/sbin/mysqld
```

Rather annoyingly still there. It doesn't seem to exist in the rc*.d directories, where else could a command be auto run at boot from?

---

### Post by Dangertux on 2011-10-18
> **endontoddy said:**
> Thanks :) but unfortunately that doesn't seem to work. After running that command and rebooting, if I run: 

```
ps aux | grep mysql 
```I get:```


mysql      876  0.4  2.5 137644 17848 ?        Ssl  20:13   0:00 /usr/sbin/mysqld
```Rather annoyingly still there. It doesn't seem to exist in the rc*.d directories, where else could a command be auto run at boot from?

It's probably been converted to an upstart job you can stop it from starting automatically via upstart this way

```

sudo nano /etc/init/mysql.conf

```Change the following
```

start on (net-device-up
          and local-filesystems
      and runlevel [2345])
stop on runlevel [016]

```to

```

start on never
stop on runlevel [016]

```Hope that helps.

---

### Post by endontoddy on 2011-10-18
That's done the trick! :D

---

### Post by leodido22 on 2012-05-07
IMHO, a better solution is:

- open a terminal
- log-in as root
- digit:
```
echo manual >> /etc/init/mysql.override
```

here the [source]("http://upstart.ubuntu.com/cookbook/#disabling-a-job-from-automatically-starting").

---

